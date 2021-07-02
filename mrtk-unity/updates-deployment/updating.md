---
title: 이전 버전에서 업데이트
description: MRTK의 하위 버전에서 마이그레이션에 대한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175105"
---
# <a name="updating-from-earlier-versions"></a>이전 버전에서 업데이트

- [새 버전의 MRTK로 업그레이드](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 ~ 2.4.0](#updating-230-to-240)
- [2.2.0 ~ 2.3.0](#updating-220-to-230)
- [2.1.0 ~ 2.2.0](#updating-210-to-220)
- [2.0.0 ~ 2.1.0](#updating-200-to-210)
- [RC2에서 2.0.0으로](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>현재 버전 찾기 

다음 지침에 따라 현재 사용 중인 MRTK 버전을 파악합니다.

1. Unity에서 MRTK 프로젝트 열기
2. Project 창에서 "MixedRealityToolkit" 폴더로 이동합니다.
3. "Version"이라는 파일을 엽니다.

위의 파일 및 폴더가 없으면 최신 버전의 MRTK에 있는 것입니다. 이 경우 다음을 시도합니다.

1. "Mixed Reality Toolkit Foundation" 폴더로 이동합니다.
2. "package.js켜기"를 클릭하여 Unity에서 미리 보기를 보거나 텍스트 편집기를 사용하여 엽니다.
3. "version:"이라는 단어가 있는 줄을 찾습니다. 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>새 버전의 MRTK로 업그레이드

*MRTK 업데이트를 받은 후 [마이그레이션 도구를](../features/tools/migration-window.md) 실행하여* 사용되지 않은 구성 요소에서 자동 수정 및 업그레이드하고 주요 변경 내용에 맞게 조정하는 것이 좋습니다. 마이그레이션 도구는 **도구** 패키지의 일부입니다.

아래 지침에서는 2.4.0에서 2.5.0으로 업그레이드 경로를 설명합니다. 프로젝트가 2.3.0 이하인 경우 [버전 간](#updating-230-to-240) 변경 내용을 읽어 업그레이드 경로를 이해하거나 이전 [릴리스의 지침을](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) 읽어 버전별 업그레이드를 수행합니다.

### <a name="mixed-reality-feature-tool"></a>Mixed Reality Feature Tool
MRTK를 최신 버전 MRTK로 업그레이드하는 가장 쉬운 방법은 [Mixed Reality 기능 도구를](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 사용하여 최신 패키지를 다운로드하고 Unity 프로젝트에 직접 로드하는 것입니다.

프로젝트에서 이전에 Unity 자산(.unitypackage) 파일을 사용한 경우 [다음 지침을 참조하세요.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool) 

### <a name="unity-asset-unitypackage-files"></a>Unity 자산(.unitypackage) 파일

또 다른 업그레이드 경로는 MRTK Unity 패키지를 수동으로 다운로드하여 프로젝트에 적용하는 것입니다. 아래 단계를 참조하세요.

1. 업그레이드 단계의 어느 지점에서나 스네그를 적중하는 경우 현재 프로젝트의 복사본을 저장합니다.
1. Unity 닫기
1. *Assets* 폴더 내에서 .meta 파일과 함께 다음 **MRTK** 폴더를 삭제합니다(프로젝트에 나열된 폴더가 모두 없을 수 있음).
    - MRTK/Core
    - MRTK/예제
    - MRTK/확장
    - MRTK/공급자
    - MRTK/SDK
    - MRTK/서비스
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > MRTK 셰이더를 수정한 경우 MRTK/StandardAssets 폴더를 삭제하기 전에 로컬 백업을 만듭니다.
    - MRTK/도구
    > [!IMPORTANT]
    > **MixedRealityToolkit.Generated** 폴더 또는 해당 .meta 파일을 삭제하지 마십시오.
1. **라이브러리** 폴더 삭제
    > [!IMPORTANT]
    > Unity Collab과 같은 일부 Unity 도구는 라이브러리 폴더에 구성 정보를 저장합니다. 이 작업을 수행하는 도구를 사용하는 경우 먼저 삭제하기 전에 라이브러리에서 도구의 데이터 폴더를 복사한 다음 라이브러리를 다시 생성한 후 복원합니다.
1. Unity에서 프로젝트 다시 열기
1. 새 Unity 패키지 가져오기
    - Foundation - _이 패키지를 먼저 가져오기_
    - 도구
    - (선택 사항) 확장
    > [!NOTE]
    > 추가 확장이 설치된 경우 다시 가져와야 할 수 있습니다.
    - (선택 사항) 예제
1. Unity를 닫고 **Library** 폴더를 삭제합니다(아래 참고를 먼저 읽어보세요!). 이 단계는 Unity에서 자산 데이터베이스를 새로 고치고 기존 사용자 지정 프로필을 조정하도록 강제하는 데 필요합니다.
1. Unity를 시작하고 프로젝트의 각 장면에 대해
    - 계층에서 **MixedRealityToolkit** 및 **MixedRealityPlayspace(있는 경우)를** 삭제합니다. 그러면 기본 카메라가 삭제되지만 다음 단계에서 다시 만들어집니다. 주 카메라의 속성을 수동으로 변경한 경우 새 카메라가 만들어지면 수동으로 다시 적용해야 합니다.
    - **MixedRealityToolkit -> 장면에 추가 및 구성을** 선택합니다.
    - **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles(한** 번만 수행) 선택 - 사용자 지정 할당 입력 작업을 그대로 유지하면서 업데이트된 축 및 데이터로 사용자 지정 컨트롤러 매핑 프로필을 업데이트합니다.
1. 마이그레이션 [도구를](../features/tools/migration-window.md) 실행하고 *전체 Project* 도구를 실행하여 모든 코드가 최신 코드로 업데이트되었는지 확인합니다.
   마이그레이션 창에는 각각 자체 실행해야 하는 다양한 마이그레이션 처리기가 포함되어 있습니다. 이 단계에는 다음이 포함됩니다.
   - 마이그레이션 처리기 선택 드롭다운에서 첫 번째 **마이그레이션 처리기를 선택합니다.**
   - "전체 Project" 단추를 클릭합니다.
   - "마이그레이션할 전체 프로젝트 추가" 단추를 클릭합니다(마이그레이션할 개체에 대한 전체 프로젝트를 검색함).
   - 마이그레이션 가능한 개체가 있는 경우 사용하도록 설정해야 하는 "마이그레이션" 단추를 클릭합니다.
   - 드롭다운 내의 각 마이그레이션 처리기에 대해 이전 세 단계를 반복합니다.
     (향후 릴리스에서 이 마이그레이션 프로세스를 간소화하기 위해 수행할 수 있는 작업을 다루는 이 [문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) 참조하세요.)

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Unity 자산 파일에서 Mixed Reality 기능 도구로 전환

Unity 자산 파일에서 Mixed Reality 기능 도구 패키지로 전환하면 다음과 같은 여러 가지 이점이 있습니다.

- 보다 쉽게 업데이트
- 컴파일 시간 단축
- Visual Studio 솔루션의 프로젝트 감소

를 Mixed Reality 기능 도구 사용으로 변경하려면 일회성 수동 단계 집합이 필요합니다.

1. 현재 프로젝트의 복사본을 저장합니다.
1. Unity 닫기
1. *Assets* 폴더 내에서 .meta 파일과 함께 다음 **MRTK** 폴더를 삭제합니다(프로젝트에 나열된 폴더가 모두 없을 수 있음).
    - MRTK/Core
    - MRTK/예제
    - MRTK/확장
    - MRTK/공급자
    - MRTK/SDK
    - MRTK/서비스
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > MRTK 셰이더를 수정한 경우 MRTK/StandardAssets 폴더를 삭제하기 전에 로컬 백업을 만듭니다.
    - MRTK/도구
    > [!IMPORTANT]
    > **MixedRealityToolkit.Generated** 폴더 또는 해당 .meta 파일을 삭제하지 마십시오.
1. **라이브러리** 폴더 삭제
    > [!IMPORTANT]
    > Unity Collab과 같은 일부 Unity 도구는 라이브러리 폴더에 구성 정보를 저장합니다. 이 작업을 수행하는 도구를 사용하는 경우 먼저 삭제하기 전에 라이브러리에서 도구의 데이터 폴더를 복사한 다음 라이브러리를 다시 생성한 후 복원합니다.
1. Unity에서 프로젝트 다시 열기

이전 단계가 수행되면 [Mixed Reality 기능 도구를](#mixed-reality-feature-tool) 실행하고 원하는 버전의 Mixed Reality Toolkit 가져옵니다.

## <a name="updating-230-to-240"></a>2.3.0에서 2.4.0으로 업데이트

[폴더 이름 바꾸기](#folder-renames-in-240) 
 [API 변경 내용](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>2.4.0에서 폴더 이름 바꾸기

MixedRealityToolkit 폴더의 이름이 변경되고 버전 2.4의 공통 계층 구조로 이동되었습니다. 애플리케이션이 MRTK 리소스에 하드 코딩된 경로를 사용하는 경우 다음 표에 따라 업데이트해야 합니다.

| 이전 폴더 | 새 폴더 |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit.Examples | MRTK/예제 |
| MixedRealityToolkit.Extensions | MRTK/확장 |
| MixedRealityToolkit.Providers | MRTK/공급자 |
| MixedRealityToolkit.SDK | MRTK/SDK |
| MixedRealityToolkit.Services | MRTK/서비스 |
| MixedRealityToolkit.Tests | MRTK/테스트 |
| MixedRealityToolkit.Tools | MRTK/도구 |

> [!IMPORTANT]
> 에는 `MixedRealityToolkit.Generated` 고객이 생성한 파일이 포함되어 있으며 변경되지 않은 상태로 유지됩니다.

### <a name="eye-gaze-setup-in-240"></a>2.4.0의 시선 응시 설정

이 버전의 MRTK는 시선 응시 설정에 필요한 단계를 수정합니다. _'IsEyeTrackingEnabled'_ 확인란은 입력 포인터 프로필의 응시 설정에서 찾을 수 있습니다. 이 확인란을 선택하면 시선 기반 응시가 활성화된 다음, 기본 머리 기반 응시가 사용됩니다.

이러한 변경 내용 및 시선 추적 설정에 대한 전체 지침에 대한 자세한 내용은 [시선 추적](../features/input/eye-tracking/eye-tracking-basic-setup.md) 문서를 참조하세요.

### <a name="eye-gaze-pointer-behavior-in-240"></a>2.4.0의 시선 응시 포인터 동작

시선 응시 기본 포인터 동작이 머리 응시 기본 포인터 동작과 일치하도록 수정되었습니다. 시선 응시 포인터는 손을 감지하면 자동으로 표시되지 않습니다. "선택"이라고 말하면 시선 응시 포인터가 다시 표시됩니다.

응시 및 손 설정에 대한 세부 정보는 [눈과 손](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 문서에서 찾을 수 있습니다.

### <a name="api-changes-in-240"></a>2.4.0의 API 변경 내용

**사용자 지정 컨트롤러 클래스**

사용자 지정 컨트롤러 클래스는 이전에 를 정의해야 `SetupDefaultInteractions(Handedness)` 했습니다. 이 메서드는 2.4에서 사용되지 않습니다. 2.4에서는 손수 매개 변수가 컨트롤러 클래스의 고유 전달과 중복되었기 때문에 사용되지 않습니다. 새 메서드에 매개 변수가 없습니다. 또한 많은 컨트롤러 클래스가 동일한 `AssignControllerMappings(DefaultInteractions);` 방식()으로 정의되었으므로 전체 호출이 로 리팩터화되어 `BaseController` 필요 대신 선택적 재정의를 수행했습니다.

**시선 응시 속성**

`UseEyeTracking`구현의 속성 `GazeProvider` 이름이 로 `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` 바뀌었습니다.

이전에 이 작업을 한 경우...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

지금 이 작업을 수행합니다...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**WindowsApiChecker 속성**

다음 WindowsApiChecker 속성은 사용되지 않는 것으로 표시되었습니다. 또는 `IsMethodAvailable` 을 `IsPropertyAvailable` `IsTypeAvailable` 사용하세요.

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

향후 API 계약 버전에 대해 WindowsApiChecker에 속성을 추가할 계획은 없습니다.

**GltfMeshPrimitiveAttributes 읽기 전용**

설정 가능한 데 사용된 gltf 메시 기본 특성은 이제 읽기 전용입니다. 해당 값은 deserialized될 때 한 번 설정됩니다.

### <a name="custom-button-icon-migration"></a>사용자 지정 단추 아이콘 마이그레이션

이전에는 사용자 지정 단추 아이콘을 사용하여 단추의 쿼드 렌더러에 새 재질을 할당해야 했습니다. 더 이상 필요하지 않으며 사용자 지정 아이콘 질감을 IconSet으로 이동하는 것이 좋습니다. 기존 사용자 지정 재질 및 아이콘이 유지됩니다. 그러나 업그레이드할 때까지는 최적 상태가 되지 않습니다.
프로젝트의 모든 단추에 있는 자산을 새 권장 형식으로 업그레이드하려면 ButtonConfigHelperMigrationHandler를 사용합니다.
(Mixed Reality Toolkit -> 유틸리티 -> 마이그레이션 창 -> 마이그레이션 처리기 선택 -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)

![업그레이드 창 대화](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

마이그레이션 중에 설정된 기본 아이콘에 아이콘이 없으면 MixedRealityToolkit.Generated/CustomIconSets에 사용자 지정 아이콘 집합이 만들어집니다. 대화 상자는 이 작업을 수행했음을 나타냅니다.

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>2.2.0에서 2.3.0으로 업데이트

- [API 변경 내용](#api-changes-in-230)

### <a name="api-changes-in-230"></a>2.3.0의 API 변경 내용

**ControllerPoseSynchronizer**

프라이빗 ControllerPoseSynchronizer.handedness 필드는 사용되지 않는 것으로 표시되었습니다. 필드가 클래스 외부에 표시되지 않기 때문에 애플리케이션에 미치는 영향을 최소화해야 합니다.

공용 ControllerPoseSynchronizer.Handedness 속성의 setter가 제거되었습니다([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**Unity용 MSBuild**

이 버전의 MRTK는 이전 릴리스보다 최신 버전의 Unity용 MSBuild 사용합니다. 프로젝트를 로드하는 동안 이전 버전이 Unity 패키지 관리자 매니페스트에 나열되면 Unity에 MSBuild 사용 옵션이 선택된 구성 대화 상자가 나타납니다. 를 적용하면 업그레이드가 수행됩니다.

**ScriptingUtilities**

ScriptingUtilities 클래스는 사용되지 않는 것으로 표시되었으며 Microsoft.MixedReality에서 ScriptUtilities로 대체되었습니다. Toolkit. Editor.Utilities 어셈블리. 새 클래스는 이전 동작을 구체화하고 스크립팅 정의 제거에 대한 지원을 추가합니다.

기존 코드는 버전 2.3.0에서 계속 작동하지만 새 클래스로 업데이트하는 것이 좋습니다.

**ShellHandRayPointer**

ShellHandRayPointer 클래스의 lineRendererSelected 및 lineRendererNoTarget 멤버가 각각 lineMaterialSelected 및 lineMaterialNoTarget(#6863 )으로 대체되었습니다.[](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)

lineRendererSelected 및/또는 lineRendererNoTarget을 lineMaterialNoTarget으로 바꾸어 컴파일 오류를 해결하세요.

**공간 관찰자 StartupBehavior**

클래스를 기반으로 구축된 공간 `BaseSpatialObserver` 관찰자는 이제 다시 사용하도록 설정할 때 StartupBehavior의 값을 적용합니다([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

이 수정 사항을 활용하기 위해 변경할 필요가 없습니다.

**PressableButton을 사용하도록 업데이트된 UX 컨트롤 프리팹**

다음 프리팹은 이제 근거리 상호 작용을 위해 TouchHandler 대신 PressableButton 구성 요소를 사용하고 있습니다([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)).

- AnimationButton
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

이 변경으로 인해 애플리케이션 코드를 업데이트해야 할 수 있습니다.

**WindowsMixedRealityUtilities 네임스페이스**

WindowsMixedRealityUtilities의 네임스페이스가 Microsoft.MixedReality에서 변경되었습니다. Toolkit. Microsoft.MixedReality에 대한 WindowsMixedReality.Input. Toolkit. WindowsMixedReality([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

컴파일 오류를 해결하려면 #using 문을 업데이트하세요.

## <a name="updating-210-to-220"></a>2.1.0에서 2.2.0으로 업데이트

- [API 변경 내용](#api-changes-in-220)

### <a name="api-changes-in-220"></a>2.2.0의 API 변경 내용

**IMixedRealityBoundarySystem.Contains**

이 메서드는 이전에 Unity에서 정의한 특정 실험적 열거형을 사용했습니다. 이제 Unity 열거형과 동일한 MRTK 정의 열거형을 받습니다. 이 변경은 Unity의 향후 경계 API에 대한 MRTK를 준비하는 데 도움이 됩니다.

**MixedRealityServiceProfileAttribute**

프로필 지원 요구 사항을 더 잘 설명하기 위해 MixedRealityServiceProfileAttribute가 업데이트되어 제외된 형식의 선택적 컬렉션을 추가했습니다. 이 변경의 일부로 ServiceType 속성이 Type에서 Type[]으로 변경되고 RequiredTypes로 이름이 변경되었습니다.

두 번째 속성인 ExcludedTypes도 추가되었습니다.

## <a name="updating-200-to-210"></a>2.0.0에서 2.1.0으로 업데이트

- [API 변경 내용](#api-changes-in-210)
- [프로필 변경 내용](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>2.1.0의 API 변경 내용

**BaseNearInteractionTouchable**

`BaseNearInteractionTouchable`메서드를 가상으로 표시하도록 가 `OnValidate` 수정되었습니다. (예: `BaseNearInteractionTouchable` )를 확장하는 `NearInteractionTouchableUnityUI` 클래스가 이 변경 사항을 반영하도록 업데이트되었습니다.

**ColliderNearInteractionTouchable**

`ColliderNearInteractionTouchable` 클래스는 사용되지 않습니다. 를 사용하도록 코드 참조를 `BaseNearInteractionTouchable` 업데이트하세요.

**IMixedRealityMouseDeviceManager**

**_추가됨_**

`IMixedRealityMouseDeviceManager``CursorSpeed`및 `WheelSpeed` 속성이 추가되었습니다. 이러한 속성을 사용하면 애플리케이션에서 커서와 휠의 속도를 각각 조정하는 승수 값을 지정할 수 있습니다.

이는 주요 변경이며 기존 마우스 디바이스 관리자 구현을 수정해야 합니다.

>[!NOTE]
>이 변경 내용은 버전 2.0.0과 호환되지 않습니다.

**_사용되지 않음_**

`MouseInputProfile`속성은 사용되지 않는 것으로 표시되었으며 이후 버전의 Microsoft Mixed Reality Toolkit 제거됩니다. 애플리케이션 코드는 더 이상이 속성을 사용 하지 않는 것이 좋습니다.

**상호 작용 가능**

다음 메서드 및 속성은 더 이상 사용되지 않으며 이후 버전의 Microsoft Mixed Reality Toolkit 제거될 예정입니다. 권장 사항은 사용되지 않는 특성에 포함되고 콘솔에 표시되는 지침에 따라 애플리케이션 코드를 업데이트하는 것입니다.

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

`NearInteractionTouchableSurface`클래스가 추가되었으며 이제 및 의 기본 클래스로 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 사용됩니다.

### <a name="profile-changes-in-210"></a>2.1.0의 프로필 변경 내용

**손 추적 프로필**

손 메시 및 공동 시각화에는 이제 별도의 편집기와 플레이어 설정이 있습니다. 이러한 시각화를 로 설정하도록 손 추적 프로필이 업데이트되었습니다. Nothing, Everything, Editor 또는 Player.

![손 시각화 모드](../release-notes/images/HandTrackingVisualizationModes.png)

사용자 지정 손 추적 프로필은 버전 2.1.0에서 올바르게 작동하도록 업데이트해야 할 수 있습니다.

>[!NOTE]
>이 변경 내용은 버전 2.0.0과 호환되지 않습니다.

**입력 시뮬레이션 프로필**

입력 시뮬레이션 시스템이 업그레이드되어 입력 시뮬레이션 프로필의 몇 가지 설정이 변경되었습니다. 일부 변경 내용은 자동으로 마이그레이션할 수 없으며 사용자는 프로필이 기본값을 사용하고 있음을 확인할 수 있습니다.

1. 프로필의 모든 KeyCode 및 마우스 단추 바인딩은 `KeyBinding` 바인딩 형식(키 또는 마우스)과 실제 바인딩 코드(각각 KeyCode 또는 마우스 단추 번호)를 저장하는 제네릭 구조체로 대체되었습니다. 구조체에는 통합된 표시를 허용하고 큰 드롭다운 목록에서 선택하는 대신 해당 키를 눌러 키 바인딩을 신속하게 설정하는 "자동 바인딩" 도구를 제공하는 자체 검사기가 있습니다.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` 은 이전에 `MouseLookButton` 열거형에 로 `InputSimulationMouseButton.Focused` 포함되었으므로 이제는 별도의 옵션입니다. 사용하도록 설정하면 단추를 해제한 후 이스케이프 키를 누를 때까지 카메라가 마우스로 계속 회전합니다.
1. `HandDepthMultiplier` 입력 시뮬레이션에 대한 일부 변경 내용을 수용하기 위해 기본값이 0.1에서 0.03으로 감소되었습니다. 스크롤할 때 카메라가 너무 빨리 이동하면 이 값을 낮추어 보세요.
1. 손을 회전하기 위한 키가 제거되었으며, 이제 마우스를 통해 손 회전도 제어됩니다. `HandRotateButton`왼쪽/오른쪽 조작 키(LShift/Space)와 함께 (Ctrl)을 보유하면 손 회전이 가능합니다.
1. 새 축 "UpDown"이 입력 축 목록에 도입되었습니다. 이렇게 하면 세로로 카메라의 이동이 제어되고, 기본적으로 Q/E 키와 컨트롤러 트리거 단추가 사용됩니다.

이러한 변경 내용에 대한 자세한 내용은 [입력 시뮬레이션 서비스](../features/input-simulation/input-simulation-service.md) 문서를 참조하세요.

**마우스 데이터 공급자 프로필**

새 및 속성을 노출하도록 마우스 데이터 공급자 프로필이 `CursorSpeed` `WheelSpeed` 업데이트되었습니다. 기존 사용자 지정 프로필에는 자동으로 기본값이 제공됩니다. 프로필이 저장되면 이러한 새 값이 유지됩니다.

**컨트롤러 매핑 프로필**

일부 축 및 입력 형식은 2.1.0, 특히 OpenVR 플랫폼과 관련하여 업데이트되었습니다. 업그레이드할 때 **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles를** 선택해야 합니다. 이렇게 하면 사용자 지정 할당 입력 작업을 그대로 유지하면서 사용자 지정 컨트롤러 매핑 프로필이 업데이트된 축 및 데이터로 업데이트됩니다.

## <a name="updating-rc2-to-200"></a>RC2를 2.0.0으로 업데이트

Microsoft Mixed Reality Toolkit RC2 및 2.0.0 릴리스 사이에 기존 프로젝트에 영향을 미칠 수 있는 변경 내용이 있었습니다. 이 문서에서는 이러한 변경 내용과 프로젝트를 2.0.0 릴리스로 업데이트하는 방법을 설명합니다.

- [API 변경 내용](#api-changes-in-200)
- [어셈블리 이름 변경](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>2.0.0의 API 변경 내용

RC2 릴리스 이후 기존 프로젝트를 중단시키는 일부 API를 포함하여 많은 API 변경이 있었습니다. 다음 섹션에서는 RC2 및 2.0.0 릴리스 간에 발생한 변경 내용에 대해 설명합니다.

**MixedRealityToolkit**

MixedRealityToolkit 개체의 다음 공용 속성은 더 이상 사용되지 않습니다.

- `RegisteredMixedRealityServices` 에 등록된 확장 서비스 및 데이터 공급자의 컬렉션이 더 이상 포함되지 않습니다.

확장 서비스에 액세스하려면 를 `MixedRealityServiceRegistry.TryGetService<T>` 사용합니다. 데이터 공급자에 액세스하려면 서비스 인스턴스를 로 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 캐스팅하고 `GetDataProvider<T>` 를 사용합니다.

다음 사용되지 않은 속성에 대해 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 또는 를 대신 사용합니다. [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)클래스는 개체에 있는 정적 시스템 접근자(예: BoundarySystem)를 `MixedRealityToolkit` 대체합니다.

>[!IMPORTANT]
>`MixedRealityToolkit`시스템 접근자는 버전 2.0.0에서 더 이상 사용되지 않으며 MRTK의 이후 릴리스에서 제거될 예정입니다.

다음 코드 예제에서는 이전 및 새 패턴을 보여 줍니다.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

새 CoreSystem 클래스를 사용하면 다른 서비스 등록 기관(예: 실험적 서비스 관리자 중 하나)을 사용하도록 애플리케이션을 변경하는 경우 애플리케이션 코드를 업데이트할 필요가 없습니다.

**IMixedRealityRaycastProvider**

IMixedRealityRaycastProvider가 추가되면서 입력 시스템 구성 프로필이 변경되었습니다. 사용자 지정 프로필이 있는 경우 애플리케이션을 실행할 때 다음 이미지에 오류가 발생할 수 있습니다.

![Raycast 공급자 1 선택](../release-notes/images/UnableToRegisterRaycastProvider.png)

이 문제를 해결하려면 IMixedRealityRaycastProvider 인스턴스를 입력 시스템 프로필에 추가하세요.

![Raycast 공급자 2 선택](../release-notes/images/SelectRaycastProvider.png)

**이벤트 시스템**

- `IMixedRealityEventSystem`이전 API 메서드 `Register` 및 는 사용되지 않는 것으로 `Unregister` 표시되었습니다. 이전 버전과의 호환성을 위해 유지됩니다.
- `InputSystemGlobalListener` 가 사용되지 않는 것으로 표시되었습니다. 해당 기능은 변경되지 않았습니다.
- `BaseInputHandler` 기본 클래스가 에서 로 `InputSystemGlobalListener` `InputSystemGlobalHandlerListener` 변경되었습니다. 이는 의 하위 항목에 대한 주요 `BaseInputHandler` 변경입니다.

**_변경의 동기 부여_**

이전 이벤트 시스템 `Register` API로 `Unregister` 인해 런타임에 여러 문제가 발생할 수 있습니다. 주요 원인은 다음과 같습니다.

- 구성 요소가 전역 이벤트에 등록하는 경우 *모든* 형식의 전역 입력 이벤트를 받습니다.
- 개체의 구성 요소 중 하나가 전역 입력 이벤트를 등록하는 경우 이 개체의 모든 구성 요소는 *모든* 형식의 전역 입력 이벤트를 받습니다.
- 동일한 개체의 두 구성 요소가 전역 이벤트에 등록되고 한 구성 요소가 런타임에서 비활성화된 경우 두 번째 구성 요소는 전역 이벤트 수신을 중지합니다.

새 API `RegisterHandler` 및 `UnregisterHandler` :

- 전역적으로 수신 대기해야 하는 입력 이벤트와 포커스를 기반으로 해야 하는 입력 이벤트에 대한 명시적 및 세부적인 제어를 제공합니다.
- 동일한 개체의 여러 구성 요소가 서로 독립적으로 전역 이벤트를 수신 대기할 수 있도록 허용합니다.

**_마이그레이션 방법_**

- 이전에 API를 호출한 경우 `Register` / `Unregister` 이러한 호출을 에 대한 호출로 `RegisterHandler` / `UnregisterHandler` 대체합니다. 제네릭 매개 변수로 구현하는 처리기 인터페이스를 사용합니다. 여러 인터페이스를 구현하고 그 중 여러 인터페이스가 전역 입력 이벤트를 수신 대기하는 경우 를 `RegisterHandler` 여러 번 호출합니다.
- 에서 상속한 경우 `InputSystemGlobalListener` 상속을 로 `InputSystemGlobalHandlerListener` 변경합니다. `RegisterHandlers`메서드를 구현하고 `UnregisterHandlers` 추상화합니다. 구현 `inputSystem.RegisterHandler` 호출에서 ( `inputSystem.UnregisterHandler` ) 전역 이벤트를 수신 대기 하려는 모든 처리기 인터페이스에 등록 합니다.
- 에서 상속된 경우 `BaseInputHandler` 및 `RegisterHandlers` `UnregisterHandlers` 추상 메서드를 구현합니다(의 경우와 `InputSystemGlobalListener` 동일).

**_마이그레이션 예제_**

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

IMixedRealitySpatialAwarenessSystem 및 IMixedRealitySpatialAwarenessObserver 인터페이스는 아래에 설명된 대로 여러 가지 주요 변경 내용을 수행했습니다.

**_변경_**

사용법을 더 잘 설명하기 위해 다음 메서드의 이름이 바뀌었습니다.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 은 사용을 명확히 하기 위해 로 이름이 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 변경되었습니다.

**_추가_**

고객 피드백에 따라 이전에 관찰된 공간 인식 데이터를 쉽게 제거할 수 있는 지원이 추가되었습니다.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**해결기**

일부 해결기 구성 요소 및 SolverHandler 관리자 클래스는 다양한 버그를 수정하고 보다 직관적인 사용을 위해 변경되었습니다.

**_SolverHandler_**

- 클래스는 더 이상 에서 확장되지 않습니다. `ControllerFinder`
- `TrackedObjectToReference` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `TrackedTargetType`
- `TrackedObjectType` 는 왼쪽 & 오른쪽 컨트롤러 값을 더 이상 사용되지 않습니다. 대신 또는 값을 사용하고 `MotionController` `HandJoint` 새 속성을 `TrackedHandedness` 업데이트하여 추적을 왼쪽 또는 오른쪽 컨트롤러로 제한합니다.

**_Inbetween_**

- `TrackedObjectForSecondTransform` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` 는 제거되었습니다. 해결기를 업데이트하려면 공용 속성(즉, `SecondTrackedObjectType`)

**_SurfaceM_**

- `MaxDistance` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `MaxRaycastDistance`
- `CloseDistance` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `ClosestDistance`
- `RaycastDirectionMode`의 기본값은 이제 `TrackedTargetForward` 추적된 대상 변환의 방향으로 광선 캐스트를 변환하는 입니다.
- `OrientationMode`열거형 값 `Vertical` 및 의 이름이 각각 및 로 `Full` 변경되었습니다. `TrackedTarget` `SurfaceNormal`
- `KeepOrientationVertical` 연결된 GameObject의 방향이 세로로 유지되는지 여부를 제어하기 위해 public 속성이 추가되었습니다.

**단추**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 이제 `DistanceSpaceMode` 속성이 `Local` 기본값으로 로 설정됩니다. 이렇게 하면 계속 누를 수 있는 동안 단추의 크기를 조정합니다.

**클리핑 구**

ClippingSphere 인터페이스가 ClippingBox 및 ClippingPlane에 있는 API를 미러하도록 변경되었습니다.

이제 ClippingSphere의 Radius 속성이 변환 배율에 따라 암시적으로 계산됩니다. 개발자는 검사기에서 ClippingSphere의 반지름을 지정해야 합니다. 반경을 변경하려면 변환의 변환 배율만 정상적으로 업데이트하면 됩니다.

**NearInteractionTouchable 및인스턴스**

- NearInteractionTouchable은 더 이상 터치하는 Unity UI 캔버스를 처리하지 않습니다. 이제 Unity UI 터치 가능에 NearInteractionTouchableUnityUI 클래스를 사용해야 합니다.
- ColliderNearInteractionTouchable은 충돌체를 기반으로 하는 터치 가능한 새 기본 클래스입니다. 즉, NearInteractionTouchableUnityUI를 제외한 모든 터치 가능 클래스입니다.
- BaseNearInteractionTouchable.DistFront가 이동되고 Rename이 표시되어,이 거리이며, 이 거리이며, 이 거리와는 다른 TouchAble과 상호 작용할 수 있습니다. 이전에는 각 터치 가능 개체의 최대 상호 작용 거리가 있었지만, 이제는 최적화를 향상할 수 있도록 하여 을(를) 에 정의했습니다.
- BaseNearInteractionTouchable.DistBack의 이름이Resreshold로 바뀌었습니다. 이렇게 하면 사용자 표시가 DebounceThreshold에 해당한다는 것을 알 수 있습니다. Touchable은Resreshold가 교차될 때 활성화되고 DebounceThreshold가 교차될 때 해제됩니다.

**ReadOnlyAttribute**

`Microsoft.MixedReality.Toolkit`네임스페이스가 , 및 에 `ReadOnlyAttribute` 추가되었습니다. `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute`

**PointerClickHandler**

`PointerClickHandler` 클래스는 사용되지 않습니다. `PointerHandler`대신 을 사용해야 하며, 동일한 기능을 제공합니다.

**HoloLens 클릭하여 지원**

HoloLens 클릭하여 컨트롤러 매핑이 처리되지 않은 에서 처리되지 않은 로 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 변경되었습니다. 이를 고려하기 위해 ControllerMapping 프로필을 처음 열 때 자동 업데이트 관리자가 실행됩니다. 이 일회성 마이그레이션 단계를 트리거하려면 2.0.0으로 업그레이드한 후 사용자 지정 프로필을 한 번 이상 여세요.

**InteractableHighlight**

`InteractableHighlight` 클래스는 사용되지 않습니다. `InteractableOnFocus` `FocusInteractableStates` 클래스와 자산을 대신 사용해야 합니다. 에 대한 새 자산을 만들려면 `Theme` 프로젝트 창을 마우스 오른쪽 `InteractableOnFocus` 단추로 클릭하고 상호 작용 가능한 테마 Mixed Reality Toolkit   >    >    >  *만들기를* 선택합니다.

**HandInteractionPanZoom**

`HandInteractionPanZoom` 은 입력 구성 요소가 아니어도 UI 네임스페이스로 이동되었습니다. `HandPanEventData` 도 이 네임스페이스로 이동되었으며 다른 UI 이벤트 데이터와 일치하도록 간소화되었습니다.

### <a name="assembly-name-changes-in-200"></a>2.0.0에서 어셈블리 이름 변경

2.0.0 릴리스에서는 모든 공식 Mixed Reality Toolkit 어셈블리 이름과 관련 어셈블리 정의(.asmdef) 파일이 다음 패턴에 맞게 업데이트되었습니다.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

일부 경우에는 콘텐츠의 더 나은 통합을 만들기 위해 여러 어셈블리가 병합되었습니다. 프로젝트에서 사용자 지정 .asmdef 파일을 사용하는 경우 업데이트가 필요할 수 있습니다.

다음 표에서는 RC2 .asmdef 파일 이름이 2.0.0 릴리스에 매핑하는 방법을 설명합니다. 모든 어셈블리 이름은 .asmdef 파일 이름과 일치합니다.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft.MixedReality. Toolkit.asmdef |
| MixedRealityToolkit.Core.BuildAndDeploy.asmdef | Microsoft.MixedReality. Toolkit. Editor.BuildAndDeploy.asmdef |
| MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef | 제거된 경우 Microsoft.MixedReality를 사용합니다. Toolkit. Editor.Utilities.asmdef |
| MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef | Microsoft.MixedReality. Toolkit. Editor.ClassExtensions.asmdef
| MixedRealityToolkit.Core.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Editor.Inspectors.asmdef |
| MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef | Microsoft.MixedReality. Toolkit. Editor.ServiceInspectors.asmdef |
| MixedRealityToolkit.Core.UtilitiesAsync.asmdef | Microsoft.MixedReality. Toolkit. Async.asmdef |
| MixedRealityToolkit.Core.Utilities.Editor.asmdef | Microsoft.MixedReality. Toolkit. Editor.Utilities.asmdef |
| MixedRealityToolkit.Utilities.Gltf.asmdef | Microsoft.MixedReality. Toolkit. Gltf.asmdef |
| MixedRealityToolkit.Utilities.Gltf.Importers.asmdef | Microsoft.MixedReality. Toolkit. Gltf.Importers.asmdef |

**MixedRealityToolkit.Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Providers.OpenVR.asmdef | Microsoft.MixedReality. Toolkit. Providers.OpenVR.asmdef |
| MixedRealityToolkit.Providers.WindowsMixedReality.asmdef | Microsoft.MixedReality. Toolkit. Providers.WindowsMixedReality.asmdef |
| MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef | Microsoft.MixedReality. Toolkit. Providers.WindowsVoiceInput.asmdef |

**MixedRealityToolkit.Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Services.BoundarySystem.asmdef | Microsoft.MixedReality. Toolkit. Services.BoundarySystem.asmdef |
| MixedRealityToolkit.Services.CameraSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.CameraSystem.asmdef |
| MixedRealityToolkit.Services.DiagnosticsSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.DiagnosticsSystem.asmdef |
| MixedRealityToolkit.Services.InputSimulation.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSimulation.asmdef |
| MixedRealityToolkit.Services.InputSimulation.Editor.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSimulation.Editor.asmdef |
| MixedRealityToolkit.Services.InputSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSystem.asmdef |
| MixedRealityToolkit.Services.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Services.InputSystem.Editor.asmdef |
| MixedRealityToolkit.Services.SceneSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.SceneSystem.asmdef |
| MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.SpatialAwarenessSystem.asmdef |
| MixedRealityToolkit.Services.TeleportSystem.asmdef | Microsoft.MixedReality. Toolkit. Services.TeleportSystem.asmdef |

**MixedRealityToolkit.SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.SDK.asmdef | Microsoft.MixedReality. Toolkit. SDK.asmdef |
| MixedRealityToolkit.SDK.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Sdk. Inspectors.asmdef |

**MixedRealityToolkit.Examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Examples.asmdef | Microsoft.MixedReality. Toolkit. Examples.asmdef |
| MixedRealityToolkit.Examples.Demos.Gltf.asmdef | Microsoft.MixedReality. Toolkit. Demos.Gltf.asmdef |
| MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Demos.StandardShader.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef | Microsoft.MixedReality. Toolkit. Demos.InspectorFields.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef | Microsoft.MixedReality. Toolkit. Demos.InspectorFields.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef | Microsoft.MixedReality. Toolkit. Demos.UX.Interactables.asmdef |
