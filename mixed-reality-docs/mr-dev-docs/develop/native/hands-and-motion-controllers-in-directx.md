---
title: DirectX의 헤드 및 모션 컨트롤러
description: 기본 DirectX 앱에서 직접 추적 및 동작 컨트롤러를 사용 하기 위한 개발자 가이드를 시작 합니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 손, 동작 컨트롤러, directx, 입력, holograms, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210962"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX의 헤드 및 모션 컨트롤러

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OPENXR API](openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.

Windows Mixed Reality에서 직접 및 [동작 컨트롤러](../../design/motion-controllers.md) 입력은 Windows에 있는 공간 입력 api를 통해 처리 됩니다 [. U. 입력. 공간](/uwp/api/windows.ui.input.spatial) 네임 스페이스입니다. 이를 통해 바늘 및 모션 컨트롤러에서 같은 방식으로 **Select** 와 같은 일반적인 동작을 쉽게 처리할 수 있습니다.

## <a name="getting-started"></a>시작

Windows Mixed Reality에서 공간 입력에 액세스 하려면 SpatialInteractionManager 인터페이스를 사용 하 여 시작 합니다.  일반적으로 앱을 시작 하는 동안  [SpatialInteractionManager:: GetForCurrentView](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)를 호출 하 여이 인터페이스에 액세스할 수 있습니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager의 작업은 입력의 원본을 나타내는 [SpatialInteractionSources](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)에 대 한 액세스를 제공 하는 것입니다.  시스템에서 사용할 수 있는 SpatialInteractionSources에는 세 가지 종류가 있습니다.
* 사용자의 검색 된 **손을 나타냅니다.** 직접 원본은 HoloLens의 기본 제스처부터 HoloLens 2에 대 한 전체에 대 한 직접 추적에 이르는 다양 한 장치 기반 기능을 제공 합니다. 
* **컨트롤러** 는 페어링된 동작 컨트롤러를 나타냅니다. 동작 컨트롤러는 Select triggers, Menu button, 터치 패드 및 thumbsticks와 같은 다양 한 기능을 제공할 수 있습니다.
* **음성** 은 사용자의 음성 인식 시스템 검색 키워드를 나타냅니다. 예를 들어이 소스는 사용자가 "선택" 이라고 표시 될 때마다 Select 누르기 및 릴리스를 삽입 합니다.

원본에 대 한 프레임당 데이터는  [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 인터페이스로 표시 됩니다. 응용 프로그램에서 이벤트 기반 또는 폴링 기반 모델을 사용 하는지 여부에 따라이 데이터에 액세스 하는 두 가지 방법이 있습니다.

### <a name="event-driven-input"></a>이벤트 기반 입력
SpatialInteractionManager는 앱이 수신할 수 있는 많은 이벤트를 제공 합니다.  [Sourcepressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased 및 [sourcepressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)를 비롯 한 몇 가지 예가 있습니다.

예를 들어 다음 코드는 MyApp:: OnSourcePressed 이벤트 처리기를 Source눌린 이벤트로 후크합니다.  이를 통해 앱은 모든 유형의 상호 작용 소스에서 누름을 검색할 수 있습니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

이 누름 이벤트는 키가 발생 했을 때 해당 SpatialInteractionSourceState 함께 비동기적으로 앱에 전송 됩니다. 앱 또는 게임 엔진에서 즉시 처리를 시작 하거나 입력 처리 루틴에서 이벤트 데이터를 큐에 대기 시킬 수 있습니다. 다음은 선택 단추가 눌러져 있는지 여부를 확인 하는 SourcePressed 이벤트에 대 한 이벤트 처리기 함수입니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

위의 코드는 장치의 기본 작업에 해당 하는 ' Select ' 누르기만 확인 합니다. 예를 들어 HoloLens 이동 하거나 이동 컨트롤러에서 트리거를 당겨 이동 합니다.  ' Select ' 누름은 대상으로 하는 홀로그램을 활성화 하는 사용자의 의도를 나타냅니다.  SourcePressed 이벤트는 다양 한 단추 및 제스처에 대해 발생 하며, SpatialInteractionSource의 다른 속성을 검사 하 여 해당 사례를 테스트할 수 있습니다.

### <a name="polling-based-input"></a>폴링 기반 입력
또한 SpatialInteractionManager를 사용 하 여 모든 프레임의 현재 상태를 폴링할 수 있습니다.  이렇게 하려면 [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 모든 프레임을 호출 합니다.  이 함수는 모든 활성 [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)에 대해 하나의 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 를 포함 하는 배열을 반환 합니다. 즉, 각 활성 동작 컨트롤러에 대해 하나씩, 추적 된 각 항목에 대해 하나씩, ' select ' 명령이 최근에 재생 된 경우 음성을 위한 하나를 의미 합니다. 그런 다음 각 SpatialInteractionSourceState의 속성을 검사 하 여 입력을 응용 프로그램에 추가할 수 있습니다. 

다음은 폴링 방법을 사용 하 여 ' select ' 작업을 확인 하는 방법의 예입니다. *예측* 변수는 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)에서 가져올 수 있는 [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체를 나타냅니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

각 SpatialInteractionSource에는 새 원본을 식별 하 고 기존 소스와 프레임 간에 상관 관계를 지정 하는 데 사용할 수 있는 ID가 있습니다.  시계를 떠날 때마다 새 ID가 제공 되지만, 컨트롤러 Id는 세션 기간 동안 정적 상태로 유지 됩니다.  [Sourcedetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) 와 같은 SpatialInteractionManager의 이벤트를 사용 하 여 장치 [](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)보기를 시작 하거나 떠날 때 또는 동작 컨트롤러를 설정/해제 하거나 페어링된 경우에 반응할 수 있습니다.

### <a name="predicted-vs-historical-poses"></a>예측 및 기록 포즈
GetDetectedSourcesAtTimestamp에 timestamp 매개 변수가 있습니다. 이를 통해 예측 또는 기록 되는 상태 및 포즈 데이터를 요청 하 여 다른 입력 소스와 공간 상호 작용의 상관 관계를 지정할 수 있습니다. 예를 들어 현재 프레임에서 손으로의 위치를 렌더링할 때 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)에서 제공 하는 예측 타임 스탬프를 전달할 수 있습니다. 이를 통해 시스템은 렌더링 된 프레임 출력과 긴밀 하 게 일치 하는 손 위치를 전달 하 여 인식 대기 시간을 최소화 합니다.

그러나 이러한 예측 된 포즈는 상호 작용 소스를 대상으로 지정 하기 위한 이상적인 포인팅 광선을 생성 하지 않습니다. 예를 들어 동작 컨트롤러 단추를 누르면 해당 이벤트에서 운영 체제에 대 한 Bluetooth까지 버블링 하는 데 최대 20 밀리초가 걸릴 수 있습니다. 마찬가지로 사용자가 손 제스처를 수행한 후에는 시스템에서 제스처를 검색 한 후 앱에서 해당 제스처를 폴링하기 전에 몇 시간이 경과할 수 있습니다. 앱이 상태 변경에 대해 폴링하는 시간에 따라 이전에 실제로 발생 한 상호 작용을 대상으로 하는 데 사용 되는 헤드와 손을 사용 합니다. 현재 HolographicFrame의 타임 스탬프를 GetDetectedSourcesAtTimestamp에 전달 하 여 대상으로 지정 하는 경우에는 프레임이 표시 될 때이를 대상 광선으로 전달 하는 것이 좋습니다 .이는 나중에 20 밀리초를 초과할 수 있습니다. 이 향후 포즈는 상호 작용 원본을 *렌더링* 하는 데 유용 하지만 과거에 사용자의 대상 지정이 복합어 상호 작용을 *대상으로 지정* 하는 데 시간 문제가 발생 합니다.

다행히 [Sourcepressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased 및 [sourcepressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) 이벤트는 각 입력 이벤트와 연결 된 기록 [상태](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 를 제공 합니다.  여기에는이 이벤트와 상관 관계를 위해 다른 Api에 전달할 수 있는 기록 [타임 스탬프](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) 와 함께 [TryGetPointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)를 통해 사용할 수 있는 기록 헤드 및 직접 포즈가 포함 됩니다.

그러면 각 프레임 및 컨트롤러를 사용 하 여 렌더링 하 고 대상을 지정할 때 다음과 같은 모범 사례가 발생 합니다.
* 각 프레임의 **수동/컨트롤러 렌더링** 의 경우 앱은 현재 프레임의 photon 시간에 각 상호 작용 소스의 **앞으로 예측** 된 포즈를 **폴링합니다** .  [HolographicFrame:: CurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)제공 하는 예측 타임 스탬프를 전달 하 여 각 프레임 [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 를 호출 하 여 모든 상호 작용 소스에 대해 폴링할 수 있습니다.
* 보도 나 릴리스를 대상으로 하는 **직접/컨트롤러를 대상** 으로 하는 경우 앱은 해당 이벤트에 대 한 **기록** 헤드 또는 핸드 포즈를 기반으로 하는 raycasting 나 눌린/릴리스 **이벤트** 를 처리 해야 합니다. [Sourcepressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) 또는 [SourceReleased](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 이벤트를 처리 하 고, 이벤트 인수에서 [State](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 속성을 가져온 다음, [TryGetPointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 메서드를 호출 하 여이 대상 광선을 가져옵니다.

## <a name="cross-device-input-properties"></a>장치 간 입력 속성
SpatialInteractionSource API는 다양 한 기능을 갖춘 컨트롤러 및 핸드 추적 시스템을 지원 합니다. 이러한 기능 중 몇 가지는 장치 유형 간에 공통적으로 제공 됩니다. 예를 들어 직접 추적 및 동작 컨트롤러는 모두 ' select ' 작업과 3D 위치를 제공 합니다. 가능 하면 API는 이러한 일반적인 기능을 SpatialInteractionSource의 동일한 속성에 매핑합니다.  이를 통해 응용 프로그램은 다양 한 입력 형식을 보다 쉽게 지원할 수 있습니다. 다음 표에서는 지원 되는 속성과 이러한 속성이 입력 형식에서 비교 되는 방식을 설명 합니다.

| 속성 | Description | HoloLens (첫 번째 gen) 제스처 | 동작 컨트롤러 | 트레일러 식|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**손**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 오른쪽 또는 왼쪽/컨트롤러입니다. | 지원되지 않음 | 지원됨 | 지원 여부 |
| [SpatialInteractionSourceState::**Isselectpressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 기본 단추의 현재 상태입니다. | 공기 탭 | 트리거 | 완화 공기 탭 (수직으로) |
| [SpatialInteractionSourceState::**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 잡기 단추의 현재 상태입니다. | 지원되지 않음 | 잡기 단추 | 손가락으로 나 폐쇄 |
| [SpatialInteractionSourceState::**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 메뉴 단추의 현재 상태입니다.    | 지원되지 않음 | 메뉴 단추 | 지원되지 않음 |
| [SpatialInteractionSourceLocation::**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 컨트롤러에서 손 모양 또는 그립 위치의 XYZ 위치입니다. | 팜 위치 | 그립 포즈 위치 | 팜 위치 |
| [SpatialInteractionSourceLocation::**Orientation**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 컨트롤러에서 손 또는 그립 자세의 방향을 나타내는 쿼터니언입니다. | 지원되지 않음 | 그립 자세 방향 | 손만 방향 |
| [SpatialPointerInteractionSourcePose::**Position**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 포인팅 광선의 원점입니다. | 지원되지 않음 | 지원됨 | 지원 여부 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 포인팅 광선의 방향입니다. | 지원되지 않음 | 지원됨 | 지원 여부 |

위의 속성 중 일부는 일부 디바이스에서 사용할 수 없으며 API는 이를 테스트하는 방법을 제공합니다. 예를 들어 [SpatialInteractionSource::IsGraspSupported](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) 속성을 검사하여 소스가 파악 작업을 제공하는지 여부를 확인할 수 있습니다.

### <a name="grip-pose-vs-pointing-pose"></a>그립 자세와 포인팅 자세

Windows Mixed Reality 다양한 폼 팩터에서 모션 컨트롤러를 지원합니다.  또한 설명된 손 추적 시스템도 지원합니다.  이러한 모든 시스템은 손 위치와 앱이 사용자의 손에서 개체를 가리키거나 렌더링하는 데 사용해야 하는 자연스러운 "앞으로" 방향 간에 서로 다른 관계를 갖습니다.  이 모든 것을 지원하기 위해 손 추적 및 모션 컨트롤러 모두에 제공되는 두 가지 유형의 3D 자세가 있습니다.  첫 번째는 사용자의 손 위치를 나타내는 그립 자세입니다.  두 번째는 사용자의 손이나 컨트롤러에서 발생하는 포인팅 광선을 나타내는 포인팅 자세입니다. 따라서 **사용자의 손이나** 사용자의 손을 잡고 **있는** 개체(예: 난소 또는 총)를 렌더링하려면 그립 자세를 사용합니다. 컨트롤러 또는 손에서 광선캐스트하려는 경우(예: 사용자가 **UI를 가리키는 경우) 포인팅 자세를 사용합니다.

[SpatialInteractionSourceState::P roperties::TryGetLocation(...)](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)을 통해 **그립 자세에** 액세스할 수 있습니다. 다음과 같이 정의됩니다.
* **그립 위치:** 컨트롤러를 자연스럽게 보유할 때의 손만 중심으로, 그립 내의 위치를 가운데에 맞도록 왼쪽 또는 오른쪽으로 조정됩니다.
* **그립 방향의 오른쪽 축:** 손을 완전히 열어 플랫 5 손가락 자세를 형성하면 손끝에 정상인 광선(왼쪽 손끝에서 앞으로, 오른쪽 손끝에서 뒤로)입니다.
* **그립 방향의 앞으로 축:** 손을 부분적으로 닫을 때(컨트롤러를 보유하는 것처럼) 엄지 손가락이 아닌 손가락으로 형성된 선을 통해 "앞으로" 가리키는 광선입니다.
* **그립 방향의 Up 축:** 오른쪽 및 앞으로 정의에 암시된 Up 축입니다.

[SpatialInteractionSourceState::P roperties::TryGetLocation(...)::SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) 또는 [SpatialInteractionSourceState::TryGetPointerPose(...)::TryGetInteractionSourcePose](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)를 통해 **포인터 자세에** 액세스할 수 있습니다.

## <a name="controller-specific-input-properties"></a>컨트롤러별 입력 속성
컨트롤러의 경우 SpatialInteractionSource에는 추가 기능이 있는 컨트롤러 속성이 있습니다.
* **HasThumbstick:** true이면 컨트롤러에 엄지스틱이 있습니다. SpatialInteractionSourceState의 [ControllerProperties](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 속성을 검사하여 thumbstick x 및 y 값(ThumbstickX 및 ThumbstickY)과 누름 상태(IsThumbstickPressed)를 획득합니다.
* **HasTouchpad:** true이면 컨트롤러에 터치 패드가 있습니다. SpatialInteractionSourceState의 ControllerProperties 속성을 검사하여 터치 패드 x 및 y 값(TouchpadX 및 TouchpadY)을 획득하고, 사용자가 패드를 터치하고 있는지(IsTouchpadTouched) 터치 패드를 누르고 있는지(IsTouchpadPressed) 확인합니다.
* **SimpleHapticsController:** 컨트롤러에 대한 SimpleHapticsController API를 사용하면 컨트롤러의 haptics 기능을 검사할 수 있으며 틱 피드백을 제어할 수도 있습니다.

터치 패드 및 썸틱의 범위는 두 축(아래쪽에서 위쪽, 왼쪽에서 오른쪽으로)에 대해 -1~1입니다. SpatialInteractionSourceState::SelectPressedValue 속성을 사용하여 액세스되는 아날로그 트리거의 범위는 0~1입니다. 값 1은 IsSelectPressed가 true와 같은 상관 관계를 맺습니다. 다른 모든 값은 IsSelectPressed가 false와 같은 상관 관계가 있습니다.

## <a name="articulated-hand-tracking"></a>굴절형 손 추적
Windows Mixed Reality API는 HoloLens 2 등과 같이 연속된 손 추적을 완전히 지원합니다. 연결 손 추적을 사용하여 애플리케이션에서 직접 조작 및 지점 및 커밋 입력 모델을 구현할 수 있습니다. 또한 완전한 사용자 지정 상호 작용을 제작하는 데 사용할 수도 있습니다.

### <a name="hand-skeleton"></a>손 구조
굴절형 손 추적은 다양한 유형의 상호 작용을 가능하게 하는 25개의 공동 구조체를 제공합니다.  스켈레톤은 인덱스/중간/링/작은 손가락에 대한 5개의 조인트, 엄지 손가락에 대한 4개의 조인트 및 1개의 성합을 제공합니다.  조인은 계층 구조의 기반 역할을 합니다. 다음 그림에서는 구조의 레이아웃을 보여 줍니다.

![손 구조](images/hand-skeleton.png)

대부분의 경우 각 조인은 나타내는 을 기준으로 이름이 지정됩니다.  모든 공동에 두 개의 차이가 있으므로 해당 위치의 자식 에 따라 각 공동의 이름을 지정하는 규칙을 사용합니다.  자식 추가로 정의됩니다.  예를 들어 "Index Proximal" 조인에는 인덱스 프록시 의 시작 위치와 해당 배의 방향이 포함됩니다.  이 파일에는 분의 끝 위치가 포함되지 않습니다.  필요한 경우 계층 구조의 다음 공동인 "인덱스 중간" 조인에서 얻을 수 있습니다.

시스템은 25개의 계층적 조인트 외에도 손만 조인을 제공합니다.  손만은 일반적으로 스큐릿 구조의 일부로 간주되지 않습니다. 손의 전반적인 위치와 방향을 쉽게 확인할 수 있는 편리한 방법으로만 제공됩니다.

각 공동에 대해 다음 정보가 제공됩니다.

| Name | Description |
|--- |--- |
|위치 | 요청된 좌표계에서 사용할 수 있는 조인의 3D 위치입니다. |
|방향 | 요청된 좌표계에서 사용할 수 있는 3D 방향입니다. |
|반지름 | 스킨의 공동 위치에 있는 표면까지의 거리입니다. 손가락 너비를 사용하는 직접 상호 작용 또는 시각화를 조정하는 데 유용합니다. |
|정확도 | 시스템이 이 공동의 정보에 대해 얼마나 확신하는지에 대한 힌트를 제공합니다. |

[SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)의 함수를 통해 손 구조 데이터에 액세스할 수 있습니다.  함수를 [TryGetHandPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)라고 하며 [HandPose](/uwp/api/windows.perception.people.handpose)라는 개체를 반환합니다.  원본이 굴절된 손을 지원하지 않는 경우 이 함수는 null을 반환합니다.  HandPose가 있으면 관심 있는 공동의 이름으로 [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)를 호출하여 현재 공동 데이터를 얻을 수 있습니다.  데이터는 [JointPose](/uwp/api/windows.perception.people.jointpose) 구조체로 반환됩니다.  다음 코드는 인덱스 손가락 팁의 위치를 가져옵니다. *currentState* 변수는 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)의 인스턴스를 나타냅니다.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>손 메시

굴절형 손 추적 API를 사용하면 완전히 변형 가능한 삼각형 손 메시를 사용할 수 있습니다.  이 메시는 손 구조와 함께 실시간으로 변형할 수 있으며 시각화 및 고급 물리학 기술에 유용합니다.  손 메시에 액세스하려면 먼저 [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)에서 [TryCreateHandMeshObserverAsync를](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) 호출하여 [HandMeshObserver](/uwp/api/windows.perception.people.handmeshobserver) 개체를 만들어야 합니다.  이 작업은 원본당 한 번만 수행해야 하며, 일반적으로 처음 볼 때 수행하면 됩니다.  즉, 이 함수를 호출하여 손에서 FOV에 들어갈 때마다 HandMeshObserver 개체를 만듭니다.  이 함수는 비동기 함수이므로 여기서는 약간의 동시성을 처리해야 합니다.  사용 가능하면 [GetT trianglegleIndices](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)를 호출하여 삼각형 인덱스 버퍼에 대해 HandMeshObserver 개체에 요청할 수 있습니다.  인덱스는 프레임을 통해 변경되지 않으므로 이를 한 번 받아 원본의 수명 동안 캐시할 수 있습니다.  인덱스는 시계 방향으로 구불구불한 순서로 제공됩니다.

다음 코드는 분리된 std::thread를 스핀업하여 메시 관찰자를 만들고 메시 관찰자를 사용할 수 있게 되면 인덱스 버퍼를 추출합니다.  추적된 손을 나타내는 [SpatialInteractionSourceState의](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 인스턴스인 *currentState라는* 변수에서 시작합니다.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
분리된 스레드를 시작하는 것은 비동기 호출을 처리하는 한 가지 옵션일 뿐입니다.  또는 C++/WinRT에서 지원하는 새로운 [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수 있습니다.

HandMeshObserver 개체가 있으면 해당 SpatialInteractionSource가 활성 상태인 기간 동안 개체를 유지해야 합니다.  그런 다음, 각 프레임에서 [GetVertexStateForPose를](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) 호출하고 꼭짓점이 원하는 자세를 나타내는 [HandPose](/uwp/api/windows.perception.people.handpose) 인스턴스를 전달하여 손을 나타내는 최신 꼭짓점 버퍼를 요청할 수 있습니다.  버퍼의 각 꼭짓점은 위치와 표준입니다.  다음은 손 메시의 현재 꼭짓점 집합을 얻는 방법의 예입니다.  이전과 마찬가지로 *currentState* 변수는 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)의 인스턴스를 나타냅니다.

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

스켈레톤 조인과 달리 손 메시 API에서는 꼭짓점의 좌표계를 지정할 수 없습니다.  대신 [HandMeshVertexState는](/uwp/api/windows.perception.people.handmeshvertexstate) 꼭짓점이 제공되는 좌표계를 지정합니다.  그런 다음 [TryGetTransformTo를](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 호출하고 원하는 좌표계를 지정하여 메시 변환을 얻을 수 있습니다.  꼭짓점을 사용할 때마다 이 메시 변환을 사용해야 합니다.  이 방법은 특히 렌더링 목적으로만 메시를 사용하는 경우 CPU 오버헤드를 줄입니다.

## <a name="gaze-and-commit-composite-gestures"></a>응시 및 커밋 복합 제스처
응시 및 커밋 입력 모델, 특히 HoloLens(1세대)를 사용하는 애플리케이션의 경우 공간 입력 API는 'select' 이벤트 위에 빌드된 복합 제스처를 사용하도록 설정하는 데 사용할 수 있는 선택적 [SpatialGestureRecognizer를](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) 제공합니다.  SpatialInteractionManager에서 홀로그램의 SpatialGestureRecognizer로 상호 작용을 라우팅하여 앱은 누르기 및 해제를 수동으로 처리할 필요 없이 손, 음성 및 공간 입력 디바이스에서 탭, 홀드, 조작 및 탐색 이벤트를 균일하게 감지할 수 있습니다.

SpatialGestureRecognizer는 요청하는 제스처 집합 간의 최소 명확성만 수행합니다. 예를 들어 탭만 요청하면 사용자가 원하는 한 손가락을 누를 수 있으며 탭이 계속 발생합니다. 탭 및 길게를 모두 요청하는 경우 손가락을 누른 채 약 1초 후에 제스처가 홀드(Hold)로 승격되고 탭이 더 이상 발생하지 않습니다.

SpatialGestureRecognizer를 사용하려면 SpatialInteractionManager의 [InteractionDetected](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) 이벤트를 처리하고 해당 이벤트에 노출된 SpatialPointerPose를 잡습니다. 이 자세에서 사용자의 머리 응시 광선을 사용하여 사용자 주위의 홀로그램 및 표면 메시와 교차하여 사용자가 상호 작용하려는 내용을 확인합니다. 그런 다음 CaptureInteraction [메서드를](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) 사용하여 이벤트 인수의 SpatialInteraction을 대상 홀로그램의 SpatialGestureRecognizer로 라우팅합니다. 이렇게 하면 생성 시 해당 인식기에서 설정된 [SpatialGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) 또는 [TrySetGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer)에 따라 상호 작용을 해석하기 시작합니다.

HoloLens(1세대)에서 상호 작용 및 제스처는 손의 위치에서 렌더링하거나 상호 작용하는 대신 사용자의 머리 응시에서 대상을 파생시켜야 합니다. 조작이 시작되면 조작 또는 탐색 제스처와 마찬가지로 손의 상대 동작을 사용하여 제스처를 제어할 수 있습니다.

## <a name="see-also"></a>추가 정보
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [직접 조작 입력 모델](../../design/direct-manipulation.md)
* [지점 및 커밋 입력 모델](../../design/point-and-commit.md)
* [응시 및 커밋 입력 모델](../../design/gaze-and-commit.md)
* [모션 컨트롤러](../../design/motion-controllers.md)