---
title: 업데이트
description: 낮은 버전의 MRTK에서 마이그레이션하는 방법에 대 한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742239"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>Microsoft Mixed Reality Toolkit 업데이트

- [새 버전의 MRTK로 업그레이드](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 2.4.0](#updating-230-to-240)
- [2.2.0 2.3.0](#updating-220-to-230)
- [2.1.0 2.2.0](#updating-210-to-220)
- [2.0.0 2.1.0](#updating-200-to-210)
- [2.0.0에 대 한 RC2](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>현재 버전 찾기 

현재 사용 중인 MRTK의 버전을 확인 하려면 다음 지침을 따르세요.

1. Unity에서 MRTK 프로젝트 열기
2. 프로젝트 창에서 "MixedRealityToolkit" 폴더로 이동 합니다.
3. "버전" 이라는 파일을 엽니다.

위의 파일과 폴더가 존재 하지 않는 경우 새 버전의 MRTK가 있습니다. 이 경우 다음을 시도 합니다.

1. "Mixed Reality Toolkit Foundation" 폴더로 이동 합니다.
2. Unity의 미리 보기를 보거나 텍스트 편집기를 사용 하 여 열려면 "package.json"을 클릭 하세요.
3. "버전:" 이라는 단어를 사용 하 여 줄을 찾습니다. 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>새 버전의 MRTK로 업그레이드

*MRTK 업데이트를 가져온 후 [](../features/tools/migration-window.md)* 에는 더 이상 사용 되지 않는 구성 요소에서 자동으로 수정 하 고 업그레이드 하 여 주요 변경 내용을 조정 하는 방법으로 마이그레이션 도구를 실행 하는 것이 좋습니다. 마이그레이션 도구는 **도구** 패키지의 일부입니다.

아래 지침에서는 2.4.0 to 2.5.0 upgrade 경로에 대해 설명 합니다. 프로젝트가 2.3.0 또는 이전 버전인 경우 버전 [간](#updating-230-to-240) 변경 내용을 참조 하 여 업그레이드 경로를 이해 하거나, 버전에 따라 업그레이드를 수행 하는 이전 [릴리스의 지침](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) 을 읽으십시오.

### <a name="mixed-reality-feature-tool"></a>Mixed Reality Feature Tool
MRTK를 최신 버전으로 업그레이드 하는 가장 쉬운 방법은 [혼합 현실 기능 도구](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 를 사용 하 여 최신 패키지를 다운로드 하 고 Unity 프로젝트에 직접 로드 하는 것입니다.

이전에 프로젝트에서 Unity asset (. unitypackage) 파일을 사용한 경우에는 [다음 지침](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)을 참조 하세요. 

### <a name="unity-asset-unitypackage-files"></a>Unity 자산 (. unitypackage) 파일

다른 업그레이드 경로는 MRTK Unity 패키지를 수동으로 다운로드 하 여 프로젝트에 적용 하는 것입니다. 다음 단계를 참조 하세요.

1. 업그레이드 단계의 어느 시점에서 든 모든 snags 적중 하는 경우 현재 프로젝트의 복사본을 저장 합니다.
1. Unity 닫기
1. *자산* 폴더 내에서 다음 **mrtk** 폴더를 해당 .xml 파일과 함께 삭제 합니다. 프로젝트에 나열 된 모든 폴더가 없을 수 있습니다.
    - MRTK/Core
    - MRTK/예제
    - MRTK/Extensions
    - MRTK/공급자
    - MRTK/SDK
    - MRTK/서비스
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > MRTK 셰이더가 수정 된 경우 MRTK/StandardAssets 폴더를 삭제 하기 전에 로컬 백업을 만듭니다.
    - MRTK/Tools
    > [!IMPORTANT]
    > **MixedRealityToolkit** 폴더 또는 해당. i a 파일을 삭제 하지 마십시오.
1. **라이브러리** 폴더를 삭제 합니다.
    > [!IMPORTANT]
    > Unity Collab와 같은 일부 Unity 도구는 구성 정보를 라이브러리 폴더에 저장 합니다. 이를 수행 하는 도구를 사용 하는 경우 먼저 라이브러리에서 도구의 데이터 폴더를 복사한 후 라이브러리를 다시 생성 한 후에 복원 합니다.
1. Unity에서 프로젝트를 다시 엽니다.
1. 새 unity 패키지 가져오기
    - 파운데이션- _이 패키지를 먼저 가져옵니다_ .
    - 도구
    - 필드 확장할
    > [!NOTE]
    > 추가 확장을 설치한 경우 다시 가져와야 할 수 있습니다.
    - 필드 예와
1. Unity를 닫고 **라이브러리** 폴더를 삭제 합니다 (아래 노트를 먼저 읽으십시오!). 이 단계는 Unity가 asset 데이터베이스를 새로 고치고 기존 사용자 지정 프로필을 조정 하도록 강제 하는 데 필요 합니다.
1. Unity를 시작 하 고 프로젝트의 각 장면에 대해
    - 계층에서 **MixedRealityToolkit** 및 **MixedRealityPlayspace**(있는 경우)를 삭제 합니다. 그러면 주 카메라가 삭제 되지만 다음 단계에서는 다시 생성 됩니다. 기본 카메라의 속성을 수동으로 변경한 경우에는 새 카메라를 만든 후 수동으로 다시 적용 해야 합니다.
    - **MixedRealityToolkit-> 선택 하 여 장면에 추가 및 구성**
    - **> MixedRealityToolkit 유틸리티-> 업데이트-> 컨트롤러 매핑 프로필** (한 번만 수행 해야 함)을 선택 합니다. 이렇게 하면 사용자 지정 된 입력 동작을 그대로 유지 하면서 업데이트 된 축 및 데이터를 사용 하 여 사용자 지정 컨트롤러 매핑 프로필을 업데이트 합니다.
1. [마이그레이션 도구](../features/tools/migration-window.md) 를 실행 하 고 *전체 프로젝트* 에서 도구를 실행 하 여 모든 코드가 최신 버전으로 업데이트 되었는지 확인 합니다.
   마이그레이션 창에는 각각 자체에서 실행 되어야 하는 여러 마이그레이션 처리기가 포함 되어 있습니다. 이 단계에는 다음이 포함 됩니다.
   - **마이그레이션 처리기 선택** 드롭다운에서 첫 번째 마이그레이션 처리기를 선택 합니다.
   - "전체 프로젝트" 단추를 클릭 합니다.
   - "마이그레이션을 위한 전체 프로젝트 추가" 단추를 클릭 합니다 .이 단추를 클릭 하면 마이그레이션할 개체에 대 한 전체 프로젝트를 검색 합니다.
   - Migrateable 개체가 발견 된 경우 사용 하도록 설정 해야 하는 "마이그레이션" 단추를 클릭 합니다.
   - 드롭다운 내의 각 마이그레이션 처리기에 대해 앞의 세 단계를 반복 합니다.
     이후 릴리스에서이 마이그레이션 프로세스를 간소화 하기 위해 수행할 수 있는 작업을 설명 하는 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) 를 참조 하세요.

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Unity 자산 파일에서 혼합 현실 기능 도구로 전환

Unity 자산 파일에서 혼합 현실 기능 도구 패키지로 전환 하면 다음과 같은 여러 가지 이점이 있습니다.

- 간편한 업데이트
- 컴파일 시간 단축
- Visual Studio 솔루션의 프로젝트 수 감소

혼합 현실 기능 도구를 사용 하도록 변경 하려면 일회성 수동 단계가 필요 합니다.

1. 현재 프로젝트의 복사본을 저장 합니다.
1. Unity 닫기
1. *자산* 폴더 내에서 다음 **mrtk** 폴더를 해당 .xml 파일과 함께 삭제 합니다. 프로젝트에 나열 된 모든 폴더가 없을 수 있습니다.
    - MRTK/Core
    - MRTK/예제
    - MRTK/Extensions
    - MRTK/공급자
    - MRTK/SDK
    - MRTK/서비스
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > MRTK 셰이더가 수정 된 경우 MRTK/StandardAssets 폴더를 삭제 하기 전에 로컬 백업을 만듭니다.
    - MRTK/Tools
    > [!IMPORTANT]
    > **MixedRealityToolkit** 폴더 또는 해당. i a 파일을 삭제 하지 마십시오.
1. **라이브러리** 폴더를 삭제 합니다.
    > [!IMPORTANT]
    > Unity Collab와 같은 일부 Unity 도구는 구성 정보를 라이브러리 폴더에 저장 합니다. 이를 수행 하는 도구를 사용 하는 경우 먼저 라이브러리에서 도구의 데이터 폴더를 복사한 후 라이브러리를 다시 생성 한 후에 복원 합니다.
1. Unity에서 프로젝트를 다시 엽니다.

이전 단계를 수행한 후 [혼합 현실 기능 도구](#mixed-reality-feature-tool) 를 실행 하 고 Mixed reality Toolkit의 원하는 버전을 가져옵니다.

## <a name="updating-230-to-240"></a>2.3.0를 2.4.0로 업데이트 하는 중

[폴더 이름 바꾸기](#folder-renames-in-240) 
 [API 변경](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>2.4.0에서 폴더 이름 바꾸기

MixedRealityToolkit 폴더의 이름이 변경 되 고 버전 2.4에서 공용 계층으로 이동 되었습니다. 응용 프로그램에서 MRTK 리소스에 하드 코드 된 경로를 사용 하는 경우 다음 테이블에 따라 업데이트 해야 합니다.

| 이전 폴더 | 새 폴더 |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit | MRTK/예제 |
| MixedRealityToolkit | MRTK/Extensions |
| MixedRealityToolkit | MRTK/공급자 |
| MixedRealityToolkit | MRTK/SDK |
| MixedRealityToolkit | MRTK/서비스 |
| MixedRealityToolkit | MRTK/테스트 |
| MixedRealityToolkit | MRTK/Tools |

> [!IMPORTANT]
> 는 `MixedRealityToolkit.Generated` 고객이 생성 한 파일을 포함 하며 변경 되지 않은 상태로 유지 됩니다.

### <a name="eye-gaze-setup-in-240"></a>2.4.0의 눈 응시 설정

이 버전의 MRTK는 눈동자를 설정 하는 데 필요한 단계를 수정 합니다. _' IsEyeTrackingEnabled '_ 확인란은 입력 포인터 프로필의 응시 설정에서 찾을 수 있습니다. 이 확인란을 선택 하면 기본 head 기반 응시를 사용 하는 대신 눈에 맞는 응시를 사용할 수 있습니다.

이러한 변경 내용에 대 한 자세한 내용 및 눈 추적 설정에 대 한 전체 지침은 [눈 추적](../features/input/eye-tracking/eye-tracking-basic-setup.md) 문서를 참조 하세요.

### <a name="eye-gaze-pointer-behavior-in-240"></a>2.4.0의 아이 응시 포인터 동작

아이 응시 기본 포인터 동작은 헤드 응시 기본 포인터 동작과 일치 하도록 수정 되었습니다. 손이 감지 되 면 눈에 주목 하는 포인터가 자동으로 표시 되지 않습니다. "선택"을 말한 후 눈에 띄는 포인터가 다시 표시 됩니다.

응시 및 직접에 대 한 자세한 내용은 [눈동자 및 실습](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 문서에서 찾을 수 있습니다.

### <a name="api-changes-in-240"></a>2.4.0의 API 변경 내용

**사용자 지정 컨트롤러 클래스**

사용자 지정 컨트롤러 클래스는 이전에를 정의 해야 했습니다 `SetupDefaultInteractions(Handedness)` . 이 메서드는 사용 하는 매개 변수가 컨트롤러 클래스의 자체 사용과 중복 되기 때문에 2.4에서 사용 되지 않습니다. 새 메서드에 매개 변수가 없습니다. 또한 다 수의 컨트롤러 클래스는 동일한 방식으로 정의 `AssignControllerMappings(DefaultInteractions);` 되므로 () 전체 호출이로 리팩터링 되었으며 `BaseController` 필요 하지 않고 선택적인 재정의를 만들었습니다.

**아이 응시 속성**

`UseEyeTracking` `GazeProvider` 의 구현에서 속성이 `IMixedRealityEyeGazeProvider` 로 바뀌었습니다 `IsEyeTrackingEnabled` .

이전에 수행한 경우

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

지금이 작업 수행 ...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**WindowsApiChecker 속성**

다음 WindowsApiChecker 속성은 사용 되지 않는 것으로 표시 되었습니다. `IsMethodAvailable`, 또는를 사용 하세요 `IsPropertyAvailable` `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

이후 API 계약 버전의 WindowsApiChecker에는 속성을 추가할 계획이 없습니다.

**GltfMeshPrimitiveAttributes 읽기 전용**

설정 가능 하 게 하는 데 사용 되는, 이제는 읽기 전용입니다. 해당 값은 deserialize 될 때 한 번 설정 됩니다.

### <a name="custom-button-icon-migration"></a>사용자 지정 단추 아이콘 마이그레이션

이전 사용자 지정 단추 아이콘은 단추의 쿼드 렌더러에 새 재질을 할당 하는 데 필요 합니다. 이는 더 이상 필요 하지 않으며 사용자 지정 아이콘 질감을 IconSet 이동 하는 것이 좋습니다. 기존 사용자 지정 자료 및 아이콘은 유지 됩니다. 그러나 업그레이드 될 때까지 최적화가 더 낮습니다.
프로젝트의 모든 단추에 대 한 자산을 새 권장 형식으로 업그레이드 하려면 ButtonConfigHelperMigrationHandler를 사용 합니다.
(혼합 현실 도구 키트-> 유틸리티-> 마이그레이션 창-> 마이그레이션 처리기 선택-> MixedReality)

![업그레이드 창 대화 상자](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

마이그레이션 중에 기본 아이콘 집합에 아이콘이 없으면 사용자 지정 아이콘 집합이 MixedRealityToolkit/CustomIconSets에 생성 됩니다. 이 작업이 수행 되었음을 나타내는 대화 상자가 나타납니다.

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>2.2.0를 2.3.0로 업데이트 하는 중

- [API 변경 내용](#api-changes-in-230)

### <a name="api-changes-in-230"></a>2.3.0의 API 변경 내용

**ControllerPoseSynchronizer**

비공개 ControllerPoseSynchronizer 필드는 사용 되지 않는 것으로 표시 되었습니다. 이는 필드가 클래스 외부에 표시 되지 않기 때문에 응용 프로그램에 대 한 영향을 최소화 해야 합니다.

Public ControllerPoseSynchronizer 속성의 setter가 제거 되었습니다 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**Unity 용 MSBuild**

이 버전의 MRTK는 이전 릴리스 보다 최신 버전의 Unity 용 MSBuild를 사용 합니다. 프로젝트를 로드 하는 동안 Unity 패키지 관리자 매니페스트에 이전 버전이 나열 되어 있으면 Unity에 MSBuild 사용 옵션을 선택 하 여 구성 대화 상자가 표시 됩니다. 를 적용 하면 업그레이드가 수행 됩니다.

**ScriptingUtilities**

ScriptingUtilities 클래스는 사용 되지 않는 것으로 표시 되었으며 MixedReality 어셈블리에서 ScriptUtilities로 대체 되었습니다. 새 클래스는 이전 동작을 구체화 하 고 스크립팅 정의 제거에 대 한 지원을 추가 합니다.

기존 코드는 버전 2.3.0에서 계속 작동 하지만 새 클래스로 업데이트 하는 것이 좋습니다.

**ShellHandRayPointer**

ShellHandRayPointer 클래스의 lineRendererSelected 및 lineRendererNoTarget 멤버는 각각 lineMaterialSelected 및 lineMaterialNoTarget로 대체 되었습니다 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

컴파일 오류를 해결 하려면 lineRendererSelected를 lineMaterialSelected 및/또는 lineRendererNoTarget와 lineMaterialNoTarget로 바꾸세요.

**공간 관찰자 StartupBehavior**

이제 클래스를 기반으로 하는 공간 관찰자가 `BaseSpatialObserver` 다시 활성화 될 때 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) startupbehavior 값을 적용 합니다.

이 픽스를 활용 하는 데 필요한 변경 사항은 없습니다.

**UX 컨트롤 prefabs가 보도를 사용 하도록 업데이트 되었습니다.**

다음 prefabs는 거의 상호 작용 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))에 TouchHandler 대신 보도 Sablebutton 구성 요소를 사용 하 고 있습니다.

- 애니메이션 단추
- 단추
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

이 변경으로 인해 응용 프로그램 코드를 업데이트 해야 할 수 있습니다.

**WindowsMixedRealityUtilities 네임 스페이스**

WindowsMixedRealityUtilities의 네임 스페이스는 MixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989))로 변경 되었습니다 (영문).

컴파일 오류를 해결 하려면 #using 문을 업데이트 하세요.

## <a name="updating-210-to-220"></a>2.1.0를 2.2.0로 업데이트 하는 중

- [API 변경 내용](#api-changes-in-220)

### <a name="api-changes-in-220"></a>2.2.0의 API 변경 내용

**IMixedRealityBoundarySystem**

이 메서드는 이전에 특정 Unity 정의 실험적 열거형에서 수행 되었습니다. 이제 Unity 열거와 동일한 MRTK 정의 열거형을 사용 합니다. 이렇게 변경 하면 Unity의 이후 경계 Api에 대해 MRTK를 준비할 수 있습니다.

**MixedRealityServiceProfileAttribute**

프로필을 지 원하는 데 필요한 요구 사항을 더 잘 설명 하기 위해 MixedRealityServiceProfileAttribute은 제외 된 형식의 선택적 컬렉션을 추가 하도록 업데이트 되었습니다. 이 변경의 일부로 ServiceType 속성이 형식에서 형식 []으로 변경 되 고 이름이 RequiredTypes로 변경 되었습니다.

두 번째 속성인 ExcludedTypes도 추가 되었습니다.

## <a name="updating-200-to-210"></a>2.0.0를 2.1.0로 업데이트 하는 중

- [API 변경 내용](#api-changes-in-210)
- [프로필 변경](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>2.1.0의 API 변경 내용

**BaseNearInteractionTouchable**

`BaseNearInteractionTouchable`가 메서드를 가상으로 표시 하도록 수정 되었습니다 `OnValidate` . 를 확장 하는 클래스 `BaseNearInteractionTouchable` (예: `NearInteractionTouchableUnityUI` )가이 변경 내용을 반영 하도록 업데이트 되었습니다.

**ColliderNearInteractionTouchable**

`ColliderNearInteractionTouchable` 클래스는 사용되지 않습니다. 사용할 코드 참조를 업데이트 하십시오 `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_강화_**

`IMixedRealityMouseDeviceManager``CursorSpeed`및 속성을 추가 했습니다 `WheelSpeed` . 이러한 속성을 사용 하면 응용 프로그램에서 커서 및 휠의 속도를 각각 조정 하는 승수 값을 지정할 수 있습니다.

이는 주요 변경 내용 이며 기존 마우스 장치 관리자 구현을 수정 해야 합니다.

>[!NOTE]
>이 변경 내용은 이전 버전과 호환 되지 않습니다. 2.0.0.

**_Mapi_**

`MouseInputProfile`속성은 더 이상 사용 되지 않는 것으로 표시 되었으며 이후 버전의 Microsoft Mixed Reality Toolkit에서 제거 될 예정입니다. 응용 프로그램 코드에서이 속성을 더 이상 사용 하지 않는 것이 좋습니다.

**상호 작용 가능**

다음 메서드 및 속성은 더 이상 사용 되지 않으며 Microsoft Mixed Reality Toolkit의 이후 버전에서 제거 될 예정입니다. 사용 되지 않는 특성에 포함 되 고 콘솔에 표시 되는 지침에 따라 응용 프로그램 코드를 업데이트 하는 것이 좋습니다.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

`NearInteractionTouchableSurface`클래스가 추가 되었으며 이제 및의 기본 클래스로 사용 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 됩니다.

### <a name="profile-changes-in-210"></a>2.1.0의 프로필 변경 내용

**수동 추적 프로필**

손 모양 메시 및 조인트 시각화에는 이제 별도의 편집기 및 플레이어 설정이 있습니다. 이 시각화를로 설정할 수 있도록 손 추적 프로필이 업데이트 되었습니다. 아무 것도, 모든 편집기 또는 플레이어입니다.

![수동 시각화 모드](../release-notes/images/HandTrackingVisualizationModes.png)

사용자 지정 수동 추적 프로필은 버전 2.1.0에서 제대로 작동 하도록 업데이트 해야 할 수 있습니다.

>[!NOTE]
>이 변경 내용은 이전 버전과 호환 되지 않습니다. 2.0.0.

**입력 시뮬레이션 프로필**

입력 시뮬레이션 시스템이 업그레이드 되어 입력 시뮬레이션 프로필에서 몇 가지 설정이 변경 되었습니다. 일부 변경 내용은 자동으로 마이그레이션되지 않으며, 사용자가 프로필의 기본값 사용을 확인할 수 있습니다.

1. 프로필의 모든 KeyCode 및 마우스 단추 바인딩은 `KeyBinding` 바인딩 형식 (키 또는 마우스) 뿐만 아니라 실제 바인딩 코드 (각각 KeyCode 또는 마우스 단추 번호)를 저장 하는 제네릭 구조체로 대체 되었습니다. 구조체에는 통합 표시를 허용 하는 자체 inspector가 있으며, 큰 드롭다운 목록에서 선택 하는 대신 각 키를 눌러 키 바인딩을 신속 하 게 설정 하는 "자동 바인딩" 도구를 제공 합니다.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` 는 이전에 `MouseLookButton` 와 같이 열거형에 포함 되었지만 `InputSimulationMouseButton.Focused` 이제는 별도의 옵션입니다. 사용 하도록 설정 되 면 카메라는 단추를 놓은 후에도 esc 키를 누를 때까지 마우스를 계속 회전 합니다.
1. `HandDepthMultiplier` 입력 시뮬레이션의 일부 변경 내용을 수용할 수 있도록 기본값은 0.1에서 0.03로 낮아졌습니다. 스크롤할 때 카메라가 너무 빨리 이동 하는 경우이 값을 낮추어 보세요.
1. 회전 하는 데 사용할 키가 제거 되었습니다. 이제 직접 회전이 제어 됩니다. `HandRotateButton`왼쪽/오른쪽 조작 키 (LShift/Space)와 함께 (Ctrl)를 누르고 있으면 직접 회전이 가능 합니다.
1. 새 축 "스핀"가 입력 축 목록에 도입 되었습니다. 이는 세로에서 카메라 이동 및 컨트롤러 트리거 단추 뿐만 아니라 Q/E 키에 대 한 기본값을 제어 합니다.

이러한 변경 내용에 대 한 자세한 내용은 [입력 시뮬레이션 서비스](../features/input-simulation/input-simulation-service.md) 문서를 참조 하세요.

**마우스 데이터 공급자 프로필**

마우스 데이터 공급자 프로필이 새 및 속성을 노출 하도록 업데이트 되었습니다 `CursorSpeed` `WheelSpeed` . 기존 사용자 지정 프로필의 기본값은 자동으로 제공 됩니다. 프로필을 저장 하면 이러한 새 값이 유지 됩니다.

**컨트롤러 매핑 프로필**

일부 축 및 입력 유형은 2.1.0에서 업데이트 되었으며, 특히 OpenVR 플랫폼을 중심으로 합니다. 업그레이드할 때 **MixedRealityToolkit-> 유틸리티-> 업데이트-> 컨트롤러 매핑 프로필** 을 선택 하십시오. 이렇게 하면 사용자 지정 된 입력 동작을 그대로 유지 하면서 업데이트 된 축 및 데이터를 사용 하 여 사용자 지정 컨트롤러 매핑 프로필을 업데이트 합니다.

## <a name="updating-rc2-to-200"></a>2.0.0에 RC2 업데이트

Microsoft Mixed Reality Toolkit의 RC2 및 2.0.0 릴리스 사이에 기존 프로젝트에 영향을 줄 수 있는 변경 내용이 적용 되었습니다. 이 문서에서는 이러한 변경 내용과 프로젝트를 2.0.0 릴리스에 업데이트 하는 방법을 설명 합니다.

- [API 변경 내용](#api-changes-in-200)
- [어셈블리 이름 변경](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>2.0.0의 API 변경 내용

R c 2의 릴리스 이후 기존 프로젝트를 중단할 수 있는 몇 가지 API 변경 내용이 있습니다. 다음 섹션에서는 RC2 및 2.0.0 릴리스 간에 발생 한 변경 사항을 설명 합니다.

**MixedRealityToolkit**

MixedRealityToolkit 개체의 다음 공용 속성은 더 이상 사용 되지 않습니다.

- `RegisteredMixedRealityServices` 에는 더 이상 등록 된 확장 서비스 및 데이터 공급자의 컬렉션이 포함 되지 않습니다.

확장 서비스에 액세스 하려면를 사용 `MixedRealityServiceRegistry.TryGetService<T>` 합니다. 데이터 공급자에 액세스 하려면 서비스 인스턴스를로 캐스팅 하 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 고를 사용 `GetDataProvider<T>` 합니다.

다음의 사용 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 되지 않는 속성 대신 또는를 사용 합니다.

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)클래스는 개체에 있는 정적 시스템 접근자 (예: BoundarySystem)를 대체 합니다 `MixedRealityToolkit` .

>[!IMPORTANT]
>`MixedRealityToolkit`시스템 접근자는 버전 2.0.0에서 더 이상 사용 되지 않으며 MRTK의 이후 릴리스에서 제거 될 예정입니다.

다음 코드 예제에서는 이전 패턴과 새 패턴을 보여 줍니다.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

새 CoreSystem 클래스를 사용 하면 다른 서비스 등록자 (예: 실험적 서비스 관리자 중 하나)를 사용 하도록 응용 프로그램을 변경 하는 경우 응용 프로그램 코드를 업데이트할 필요가 없습니다.

**IMixedRealityRaycastProvider**

IMixedRealityRaycastProvider 추가 하 여 입력 시스템 구성 프로필이 변경 되었습니다. 사용자 지정 프로필이 있는 경우 응용 프로그램을 실행할 때 다음 이미지에 오류가 표시 될 수 있습니다.

![Raycast 공급자 1 선택](../release-notes/images/UnableToRegisterRaycastProvider.png)

이러한 문제를 해결 하려면 입력 시스템 프로필에 IMixedRealityRaycastProvider 인스턴스를 추가 하세요.

![Raycast 공급자 2 선택](../release-notes/images/SelectRaycastProvider.png)

**이벤트 시스템**

- `IMixedRealityEventSystem`이전 API 메서드 `Register` 및는 `Unregister` 사용 되지 않는 것으로 표시 되었습니다. 이전 버전과의 호환성을 위해 유지 됩니다.
- `InputSystemGlobalListener` 사용 되지 않는 것으로 표시 되었습니다. 해당 기능이 변경 되지 않았습니다.
- `BaseInputHandler` 기본 클래스가에서로 변경 되었습니다 `InputSystemGlobalListener` `InputSystemGlobalHandlerListener` . 이는의 모든 하위 항목에 대 한 주요 변경 내용입니다 `BaseInputHandler` .

**_변경 내용 뒤의 동기_**

이전 이벤트 시스템 API를 `Register` 통해 `Unregister` 런타임 시 여러 문제가 발생할 수 있습니다. 주는 다음과 같습니다.

- 구성 요소가 전역 이벤트를 등록 하는 경우 *모든* 형식의 전역 입력 이벤트를 수신 합니다.
- 개체의 구성 요소 중 하나가 전역 입력 이벤트를 등록 하는 경우이 개체의 모든 구성 요소는 *모든* 형식의 전역 입력 이벤트를 수신 합니다.
- 동일한 개체에 있는 두 구성 요소가 전역 이벤트에 등록 된 다음 런타임에 비활성화 되는 경우 두 번째 구성 요소는 글로벌 이벤트 수신을 중지 합니다.

새 API `RegisterHandler` 및 `UnregisterHandler` :

- 지정 된 입력 이벤트를 전역적으로 수신 해야 하는 명확 하 고 세부적인 제어를 제공 하며,이를 중심으로 사용 해야 합니다.
- 동일한 개체의 여러 구성 요소가 전역 이벤트를 서로 독립적으로 수신할 수 있습니다.

**_마이그레이션 방법_**

- `Register` / `Unregister` 이전에 API를 호출한 경우이 호출을 호출로 바꿉니다 `RegisterHandler` / `UnregisterHandler` . 제네릭 매개 변수로 구현 하는 처리기 인터페이스를 사용 합니다. 여러 인터페이스를 구현 하 고 여러 인터페이스에서 전역 입력 이벤트를 수신 하는 경우 `RegisterHandler` 여러 번 호출 합니다.
- 에서 상속 된 경우 `InputSystemGlobalListener` 상속을로 변경 `InputSystemGlobalHandlerListener` 합니다. `RegisterHandlers`및 `UnregisterHandlers` 추상 메서드를 구현 합니다. 구현 호출 `inputSystem.RegisterHandler` ()에서 `inputSystem.UnregisterHandler` 전역 이벤트를 수신 하려는 모든 처리기 인터페이스에 등록 합니다.
- 에서 상속 된 경우 `BaseInputHandler` `RegisterHandlers` 및 추상 메서드를 구현 `UnregisterHandlers` 합니다 .의 경우와 동일 `InputSystemGlobalListener` 합니다.

**_마이그레이션의 예_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**공간 인식**

IMixedRealitySpatialAwarenessSystem 및 IMixedRealitySpatialAwarenessObserver 인터페이스는 아래에 설명 된 대로 여러 가지 주요 변경 내용을 수행 했습니다.

**_변경_**

다음 메서드는 사용에 대 한 더 나은 설명을 위해 이름이 변경 되었습니다.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 의 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 사용법을 명확 하 게 하기 위해 이름이로 바뀌었습니다.

**_추가_**

사용자 의견을 바탕으로 이전에 관찰 된 공간 인식 데이터를 쉽게 제거할 수 있는 지원이 추가 되었습니다.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**해결기**

일부 해 찾기 구성 요소 및 SolverHandler manager 클래스는 다양 한 버그를 수정 하 고 보다 직관적인 사용을 위해 변경 되었습니다.

**_SolverHandler_**

- 클래스가 더 이상에서 확장 되지 않습니다. `ControllerFinder`
- `TrackedObjectToReference` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `TrackedTargetType`
- `TrackedObjectType` 지지 left & right controller values입니다. 대신 또는 값을 사용 하 `MotionController` `HandJoint` 고 새 속성을 업데이트 `TrackedHandedness` 하 여 추적을 왼쪽 또는 오른쪽 컨트롤러로 제한 합니다.

**_를_**

- `TrackedObjectForSecondTransform` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` 는 제거되었습니다. 해 찾기를 업데이트 하려면 공용 속성 (즉, `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `MaxRaycastDistance`
- `CloseDistance` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `ClosestDistance`
- 이제의 기본값 `RaycastDirectionMode` 은 `TrackedTargetForward` 추적 대상 변환 방향의 raycasts를 전달 하는 것입니다.
- `OrientationMode` 열거형 값 `Vertical` 및 `Full` 은 `TrackedTarget` 각각 및로 이름이 변경 되었습니다 `SurfaceNormal` .
- `KeepOrientationVertical` 연결 된 GameObject의 방향이 세로로 유지 되는지 여부를 제어 하기 위해 public 속성이 추가 되었습니다.

**단추**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 이제 `DistanceSpaceMode` 속성을 기본값으로 설정 했습니다 `Local` . 이를 통해 단추의 크기를 조정할 수 있습니다 (pressable).

**자르기 구**

ClippingSphere 인터페이스가 ClippingBox 및 ClippingPlane에 있는 Api를 반영 하도록 변경 되었습니다.

ClippingSphere의 Radius 속성은 이제 변환 배율에 따라 암시적으로 계산 됩니다. 개발자가 검사기에서 ClippingSphere의 반지름을 지정 해야 합니다. Radius를 변경 하려는 경우 일반적인 방법으로 변환의 변환 배율을 업데이트 하면 됩니다.

**NearInteractionTouchable 및 PokePointer**

- NearInteractionTouchable는 Unity UI 캔버스를 더 이상 접촉 하지 않습니다. NearInteractionTouchableUnityUI 클래스는 이제 Unity UI touchables에 사용 해야 합니다.
- ColliderNearInteractionTouchable는 colliders을 기반으로 하는 touchables의 새로운 기본 클래스입니다. 즉, NearInteractionTouchableUnityUI을 제외한 모든 touchable입니다.
- BaseNearInteractionTouchable 이동 되었으며 PokePointer로 이름이 변경 되었습니다. TouchableDistance이 거리 이며 PokePointer가 touchables와 상호 작용할 수 있는 거리입니다. 이전에는 각 touchable 자체의 최대 상호 작용 거리가 있지만 이제 PokePointer에 정의 되어 더 나은 최적화를 허용 합니다.
- BaseNearInteractionTouchable가 PokeThreshold로 이름이 변경 되었습니다. 그러면 PokeThreshold가 DebounceThreshold에 해당 하는 것을 알 수 있습니다. Touchable는 PokeThreshold가 교차 될 때 활성화 되 고 DebounceThreshold가 교차할 때 릴리스됩니다.

**ReadOnlyAttribute**

`Microsoft.MixedReality.Toolkit`네임 스페이스는, 및에 추가 되었습니다 `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .

**Pointer클릭 처리기**

`PointerClickHandler` 클래스는 사용되지 않습니다. `PointerHandler`대신를 사용 해야 합니다 .이는 동일한 기능을 제공 합니다.

**HoloLens clicker 지원**

HoloLens clicker의 컨트롤러 매핑이 unhanded 되지 않도록 변경 되었습니다 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) . 이를 고려 하 여 ControllerMapping 프로필을 처음 열 때 자동 업데이트 프로그램이 실행 됩니다. 이 일회성 마이그레이션 단계를 트리거하기 위해 2.0.0로 업그레이드 한 후에는 한 번 이상 사용자 지정 프로필을 열어 보세요.

**InteractableHighlight 표시**

`InteractableHighlight` 클래스는 사용되지 않습니다. `InteractableOnFocus`클래스 및 `FocusInteractableStates` 자산을 대신 사용 해야 합니다. `Theme`에 대 한 새 자산을 만들려면 `InteractableOnFocus` 프로젝트 창을 마우스 오른쪽 단추로 클릭 하 고   >  *Mixed Reality Toolkit*  >  *Interactable*  >  *테마* 만들기를 선택 합니다.

**HandInteractionPanZoom**

`HandInteractionPanZoom` 입력 구성 요소가 아닌 UI 네임 스페이스로 이동 되었습니다. `HandPanEventData` 도이 네임 스페이스로 이동 되었으며 다른 UI 이벤트 데이터와 일치 하도록 간소화 되었습니다.

### <a name="assembly-name-changes-in-200"></a>2.0.0의 어셈블리 이름 변경

2.0.0 릴리스에서는 공식의 모든 공식 Reality Toolkit 어셈블리 이름 및 연결 된 어셈블리 정의 (. asmdef) 파일이 다음 패턴에 맞게 업데이트 되었습니다.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

일부 경우에는 여러 어셈블리가 병합 되어 해당 콘텐츠의 더 나은 unity를 만들었습니다. 프로젝트에서 사용자 지정. asmdef 파일을 사용 하는 경우 업데이트가 필요할 수 있습니다.

다음 표에서는 2.0.0 릴리스에 대 한 RC2 파일 이름을 매핑하는 방법에 대해 설명 합니다. 모든 어셈블리 이름은. asmdef 파일 이름과 일치 합니다.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit | MixedReality입니다. |
| MixedRealityToolkit. asmdef | MixedReality. a s t. n a m e. |
| MixedRealityToolkit. c s t. | 제거 됨, MixedReality를 사용 합니다. |
| MixedRealityToolkit. EditorClassExtensions (영문) | MixedReality. ClassExtensions. asmdef
| MixedRealityToolkit를 정의 합니다. | MixedReality. m a t. |
| MixedRealityToolkit를 정의 합니다. | MixedReality. b a s e. |
| MixedRealityToolkit. UtilitiesAsync | MixedReality (영문). |
| MixedRealityToolkit (영문). | MixedReality. a s t. |
| MixedRealityToolkit. asmdef | MixedReality. asmdef |
| MixedRealityToolkit. asmdef | MixedReality. c s t. m a t. |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit을 제공 합니다. | MixedReality. c s t. a s e. |
| MixedRealityToolkit. WindowsMixedReality. | MixedReality. WindowsMixedReality.. |
| MixedRealityToolkit. WindowsVoiceInput. | MixedReality. WindowsVoiceInput.. |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. BoundarySystem | MixedReality. BoundarySystem (영문) |
| MixedRealityToolkit. CameraSystem | MixedReality. CameraSystem (영문) |
| MixedRealityToolkit. DiagnosticsSystem | MixedReality. DiagnosticsSystem (영문) |
| MixedRealityToolkit. asmdef | MixedReality (영문). asmdef |
| MixedRealityToolkit. n a m e. | MixedReality. c o m a s. |
| MixedRealityToolkit. n a m e. | MixedReality. n a m e. |
| MixedRealityToolkit입니다. | MixedReality. c o m. n a m e. |
| MixedRealityToolkit. SceneSystem | MixedReality. SceneSystem (영문) |
| MixedRealityToolkit. SpatialAwarenessSystem | MixedReality. SpatialAwarenessSystem (영문) |
| MixedRealityToolkit. TeleportSystem | MixedReality. TeleportSystem (영문) |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. | MixedReality (영문). |
| MixedRealityToolkit입니다. | MixedReality. a s e. |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. asmdef | MixedReality. asmdef |
| MixedRealityToolkit를 정의 합니다. | MixedReality. c. c. c. |
| MixedRealityToolkit.. m a t. | MixedReality.. m a t e. |
| MixedRealityToolkit. InspectorFields. asmdef | MixedReality. InspectorFields (영문) |
| MixedRealityToolkit. InspectorFields. m a t. | MixedReality. InspectorFields. m a t. |
| MixedRealityToolkit (영문). asmdef | MixedReality. a s t. a s t. |