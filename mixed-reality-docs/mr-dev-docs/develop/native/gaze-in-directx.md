---
title: DirectX의 헤드 및 눈 응시
description: 네이티브 DirectX 앱의 머리 응시 및 시선 추적에서 광선 캐스팅 데이터를 요청, 사용 및 압축 해제하는 방법을 알아봅니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 시선 응시, 헤드 게이즈, 헤드 추적, 시선 추적, directx, 입력, 홀로그램, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193212"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>DirectX의 헤드 응시 및 시선 응시 입력

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 API와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OpenXR API](openxr-getting-started.md)** 를 사용하는 것이 좋습니다.

Windows Mixed Reality 시선 및 머리 응시 입력은 사용자가 보고 있는 내용을 결정하는 데 사용됩니다. 데이터를 사용하여 [헤드 응시 및 커밋과](../../design/gaze-and-commit.md)같은 기본 입력 모델을 구동하고 다양한 상호 작용 형식에 대한 컨텍스트를 제공할 수 있습니다. API를 통해 사용할 수 있는 응시 벡터에는 머리 응시와 시선 응시의 두 가지 유형이 있습니다.  둘 다 원점과 방향을 가진 3차원 광선으로 제공됩니다. 그런 다음, 애플리케이션은 장면 또는 실제 세계로 광선 캐스팅하고 사용자가 대상으로 하는 대상을 결정할 수 있습니다.

**머리 응시는** 사용자의 머리가 가리키는 방향을 나타냅니다. 헤드 응시는 디바이스 자체의 위치와 앞으로 방향으로, 위치는 두 디스플레이 사이의 중심점으로 간주합니다. 헤드 응시는 모든 Mixed Reality 디바이스에서 사용할 수 있습니다.

**시선 응시는** 사용자의 시선이 보고 있는 방향을 나타냅니다. 원점은 사용자의 눈 사이에 있습니다.  시선 추적 시스템을 포함하는 Mixed Reality 디바이스에서 사용할 수 있습니다.

[SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 통해 헤드 및 눈에 광선 모두에 액세스할 수 있습니다. [SpatialPointerPose::TryGetAtTimestamp를](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 호출하여 지정된 타임스탬프 및 [좌표계](coordinate-systems-in-directx.md)에서 새 SpatialPointerPose 개체를 받습니다. 이 SpatialPointerPose에는 헤드 응시 원점과 방향이 포함됩니다. 또한 시선 추적을 사용할 수 있는 경우 시선 응시 원점과 방향을 포함합니다.

### <a name="device-support"></a>디바이스 지원

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>기능</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>헤드 게이즈(head-gaze)</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>시선 응시</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>헤드 응시 사용

헤드 응시에 액세스하려면  [SpatialPointerPose::TryGetAtTimestamp를](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 호출하여 새 SpatialPointerPose 개체를 수신합니다. 다음 매개 변수를 전달합니다.
 - 헤드 응시에 사용할 좌표계를 나타내는 [SpatialCoordinateSystem입니다.](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 이 값은 다음 코드에서 *coordinateSystem* 변수로 표시됩니다. 자세한 내용은 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드를 참조하세요.
 - 요청된 머리 자세의 정확한 시간을 나타내는 [타임스탬프입니다.](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)  일반적으로 현재 프레임이 표시되는 시간에 해당하는 타임스탬프를 사용합니다. 현재 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)을 통해 액세스할 수 있는 [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체에서 이 예측 표시 타임스탬프를 얻을 수 있습니다.  이 HolographicFramePrediction 개체는 다음 코드에서 *예측* 변수로 표시됩니다.

 유효한 SpatialPointerPose가 있으면 머리 위치와 앞으로 방향에 속성으로 액세스할 수 있습니다.  다음 코드는 액세스하는 방법을 보여줍니다.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>시선 응시 사용

사용자가 시선 응시 입력을 사용하려면 각 사용자가 디바이스를 처음 사용할 때 [시선 추적 사용자 보정을](/hololens/hololens-calibration) 거쳐야 합니다. 시선 응시 API는 머리 응시와 비슷합니다.
장면에 대해 광선 캐스팅할 수 있는 광선 원점과 방향을 제공하는 동일한 [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 사용합니다.  유일한 차이점은 시선 추적을 사용하기 전에 명시적으로 사용하도록 설정해야 한다는 것입니다.
1. 앱에서 시선 추적을 사용할 수 있는 사용자 권한을 요청합니다.
2. 패키지 매니페스트에서 "응시 입력" 기능을 사용하도록 설정합니다.

### <a name="requesting-access-to-eye-gaze-input"></a>시선 응시 입력에 대한 액세스 요청

앱이 시작되면 [EyePose::RequestAccessAsync를](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 호출하여 시선 추적에 대한 액세스를 요청합니다. 필요한 경우 시스템에서 사용자에게 메시지를 표시하고 액세스 권한이 부여되면 [GazeInputAccessStatus::Allowed를](/uwp/api/windows.ui.input.gazeinputaccessstatus) 반환합니다. 비동기 호출이므로 약간의 추가 관리가 필요합니다. 다음 예제에서는 분리된 std::thread를 스핀업하여 결과를 기다립니다. 이 결과는 *m_isEyeTrackingEnabled* 라는 멤버 변수에 저장됩니다.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
분리된 스레드를 시작하는 것은 비동기 호출을 처리하는 한 가지 옵션일 뿐입니다. C++/WinRT에서 지원하는 새로운 [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수도 있습니다.
사용자 권한을 요청하는 또 다른 예제는 다음과 같습니다.
-   EyePose::IsSupported()를 사용하면 애플리케이션에서 시선 추적기가 있는 경우에만 권한 대화 상자를 트리거할 수 있습니다.
-   GazeInputAccessStatus m_gazeInputAccessStatus. 이는 권한 프롬프트가 반복해서 표시되지 않도록 하기 위한 것입니다.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>*응시 입력* 기능 선언

*솔루션 탐색기* appxmanifest 파일을 두 번 클릭합니다.  그런 *다음, 기능* 섹션으로 이동하여 *응시 입력* 기능을 확인합니다. 

![응시 입력 기능](images/gaze-input-capability.png)

그러면 appxmanifest 파일의 *패키지* 섹션에 다음 줄이 추가됩니다.
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>시선 응시 광선 받기

ET에 대한 액세스 권한을 받으면 프레임마다 시선 응시 광선을 자유롭게 볼 수 있습니다.
헤드 응시와 마찬가지로 원하는 타임스탬프 및 좌표계로 [SpatialPointerPose::TryGetAtTimestamp를](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 호출하여 [SpatialPointerPose를](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 얻습니다. SpatialPointerPose는 [Eyes](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성을 통해 [EyesPose](/uwp/api/windows.perception.people.eyespose) 개체를 포함합니다. 시선 추적을 사용하는 경우에만 null이 아닌 것입니다. 이 위치에서 [EyePose::IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)를 호출하여 디바이스의 사용자에게 시선 추적 보정이 있는지 확인할 수 있습니다.  다음으로, [Gaze](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 속성을 사용하여 시선 응시 위치와 방향을 포함하는 [SpatialRay를](/uwp/api/windows.perception.spatial.spatialray) 얻습니다. Gaze 속성은 경우에 따라 null일 수 있으므로 이를 확인해야 합니다. 이는 보정된 사용자가 일시적으로 눈가를 닫는 경우에 발생할 수 있습니다.

다음 코드는 시선 응시 광선에 액세스하는 방법을 보여줍니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>시선 추적을 사용할 수 없는 경우 대체

[시선 추적 디자인 문서에서](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)설명한 것처럼 디자이너와 개발자는 모두 시선 추적 데이터를 사용할 수 없는 인스턴스를 알고 있어야 합니다.

데이터를 사용할 수 없는 다양한 이유가 있습니다.
* 보정되지 않는 사용자
* 사용자가 시선 추적 데이터에 대한 앱 액세스를 거부했습니다.
* HoloLens visor 또는 사용자의 시선이 폐색된 십자선과 같은 일시적인 간섭 

일부 API는 이 문서에서 이미 언급되었지만, 다음에서는 시선 추적을 빠른 참조로 사용할 수 있음을 감지하는 방법에 대한 요약을 제공합니다. 

* 시스템에서 시선 추적을 지원하는지 확인합니다. 다음 *메서드를* [호출합니다. Windows. Perception.People.EyesPose.IsSupported()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* 사용자가 보정되어 있는지 확인합니다. 다음 *속성을* 호출합니다. [Windows. Perception.People.EyesPose.IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* 사용자가 자신의 시선 추적 데이터를 사용할 수 있는 권한을 앱에 부여했는지 확인합니다. 현재 _'GazeInputAccessStatus'_ 를 검색합니다. 이 작업을 수행하는 방법에 대한 예제는 응시 입력 에 [대한 액세스 요청에서](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)설명합니다. 

또한 수신된 시선 추적 데이터 업데이트 간에 시간 초과를 추가하고, 그렇지 않으면 아래 설명된 대로 머리 응시로 대체하여 시선 추적 데이터가 부실하지 않은지 확인할 수도 있습니다.   
자세한 내용은 [대체 디자인 고려 사항을](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) 방문하세요.

<br>

## <a name="correlating-gaze-with-other-inputs"></a>응시와 다른 입력의 상관 관계

경우에 따라 과거의 이벤트에 해당하는 [SpatialPointerPose가](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 필요할 수 있습니다. 예를 들어 사용자가 에어 탭을 수행하는 경우 앱에서 보고 있는 내용을 알고 싶을 수 있습니다. 이를 위해 시스템 입력 처리와 표시 시간 간의 대기 시간으로 인해 예측된 프레임 시간과 함께 [SpatialPointerPose::TryGetAtTimestamp를](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 사용하면 정확하지 않을 수 있습니다. 또한 대상 지정에 시선 응시를 사용하는 경우 커밋 작업을 완료하기 전에도 시선이 이동하는 경향이 있습니다. 간단한 에어 탭에서는 문제가 되지 않지만 긴 음성 명령을 빠른 시선 이동과 결합할 때 더 중요해집니다. 이 시나리오를 처리하는 한 가지 방법은 입력 이벤트에 해당하는 기록 타임스탬프를 사용하여  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)를 추가로 호출하는 것입니다.  

그러나 SpatialInteractionManager를 통해 라우팅되는 입력의 경우 더 쉬운 메서드가 있습니다. [SpatialInteractionSourceState에는](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 자체 [TryGetAtTimestamp 함수가 있습니다.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 이를 호출 하면 추측 하지 않고 완벽 하 게 상호 관련 된 [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 제공 됩니다. SpatialInteractionSourceStates로 작업 하는 방법에 대 한 자세한 내용은 DirectX 설명서 [에서 직접 및 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 를 참조 하세요.

<br>

## <a name="calibration"></a>보정

눈 추적을 정확 하 게 수행 하려면 각 사용자가 [눈 추적 사용자 보정](/hololens/hololens-calibration)을 진행 해야 합니다. 이를 통해 장치는 사용자에 게 더 편안 하 고 높은 품질의 시청 환경을 제공 하 고 동시에 정확한 시각 추적을 보장 합니다. 개발자는 사용자 보정을 관리 하기 위해 최종 작업을 수행할 필요가 없습니다. 시스템은 다음과 같은 상황에서 사용자에 게 장치를 보정할 것인지 묻는 메시지를 표시 합니다.
* 사용자가 처음으로 장치를 사용하는 중
* 사용자가 이전에 보정 프로세스에서 옵트아웃함
* 사용자가 마지막으로 장치를 사용했을 때 보정 프로세스에 실패함

개발자는 눈 추적 데이터를 사용할 수 없는 사용자를 적절 하 게 지원 해야 합니다. [HoloLens 2의 시각 추적](../../design/eye-tracking.md)에서 대체 솔루션에 대 한 고려 사항에 대해 자세히 알아보세요.

<br>

## <a name="see-also"></a>추가 정보

* [조정](/hololens/hololens-calibration)
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
* [눈-HoloLens 2에 응시](../../design/eye-tracking.md)
* [입력 모델 응시 및 커밋](../../design/gaze-and-commit.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)