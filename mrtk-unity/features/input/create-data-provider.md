---
title: 입력 시스템 데이터 공급자 만들기
description: MRTK에서 입력 시스템 및 데이터 공급자를 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 391aa477bb09fa2dec2b3bcb26bad813c715ee03eeb0dc03dcbc9048ae318295
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223994"
---
# <a name="creating-an-input-system-data-provider"></a>입력 시스템 데이터 공급자 만들기

혼합 현실 Toolkit 입력 시스템은 입력 장치 지원을 사용 하기 위한 확장 가능한 시스템입니다. 새 하드웨어 플랫폼에 대 한 지원을 추가 하려면 사용자 지정 입력 데이터 공급자가 필요할 수 있습니다.

이 문서에서는 입력 시스템에 대해 장치 관리자 라고도 하는 사용자 지정 데이터 공급자를 만드는 방법을 설명 합니다. 여기에 표시 된 예제 코드는에서 가져온 것입니다 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> 이 예제에서 사용 되는 전체 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.

## <a name="namespace-and-folder-structure"></a>네임 스페이스 및 폴더 구조

데이터 공급자는 타사 추가 기능 또는 Microsoft Mixed Reality Toolkit 일부로 배포할 수 있습니다. 새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다.

> [!Important]
> 입력 시스템 데이터 공급자가 [혼합 현실 Toolkit 리포지토리로](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출 되는 경우 네임 스페이스는 MixedReality로 시작 **해야** 합니다. Toolkit (예: MixedReality. Toolkit. WindowsMixedReality) 및 코드는 MRTK/Providers 아래에 있는 폴더 (예: MRTK/Providers/WindowsMixedReality)에 있어야 합니다.

### <a name="namespace"></a>네임스페이스

데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다. 네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.

- 회사 이름
- 기능 영역

예를 들어 Contoso 회사에서 만든 입력 데이터 공급자는 "MixedReality" 일 수 있습니다. Toolkit. 입력 ".

### <a name="recommended-folder-structure"></a>권장 폴더 구조

다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.

![폴더 구조의 예](../images/input/ExampleProviderFolderStructure.png)

여기서 ContosoInput에는 데이터 공급자의 구현이 포함 되 고 편집기 폴더에는 검사기 (및 기타 Unity 편집기 관련 코드)가 포함 되며, 텍스처 폴더에는 지원 되는 컨트롤러의 이미지가 포함 되 고, 프로필에는 하나 이상의 미리 구성 된 프로필이 포함 됩니다.

> [!Note]
> 일부 일반적인 컨트롤러 이미지는 MixedRealityToolkit\StandardAssets\Textures 폴더에서 찾을 수 있습니다.

## <a name="implement-the-data-provider"></a>데이터 공급자 구현

### <a name="specify-interface-andor-base-class-inheritance"></a>인터페이스 및/또는 기본 클래스 상속 지정

모든 입력 시스템 데이터 공급자는 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 입력 시스템에 필요한 최소한의 기능을 지정 하는 인터페이스를 구현 해야 합니다. MRTK foundation에는 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 이 필수 기능의 기본 구현을 제공 하는 클래스가 포함 되어 있습니다. Unity의 UInput 클래스를 기반으로 하는 장치의 경우 [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 클래스를 기본 클래스로 사용할 수 있습니다.

> [!Note]
> `BaseInputDeviceManager`및 `UnityJoystickManager` 클래스는 필요한 구현을 제공 `IMixedRealityInputDeviceManager` 합니다.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` 는에서 `WindowsMixedRealityDeviceManager` 입력 기능 집합을 지원 함을 나타내는 데 사용 됩니다 (특히, 구분 하지 않는 방식, 응시 제스처-음성 및 동작 컨트롤러).

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>MixedRealityDataProvider 특성 적용

입력 시스템 데이터 공급자를 만드는 핵심 단계는 특성을 클래스에 적용 하는 것입니다 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) . 이 단계에서는 입력 시스템 프로필에서 선택 하는 경우 공급자에 대 한 기본 프로필 및 플랫폼을 설정할 수 있습니다.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>IMixedRealityDataProvider 메서드 구현

클래스가 정의 되 면 다음 단계는 인터페이스의 구현을 제공 하는 것입니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .

> [!Note]
> 클래스를 `BaseInputDeviceManager` 통해 클래스는 `BaseService` 메서드에 대해 빈 구현만 제공 `IMixedRealityDataProvider` 합니다. 이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.

데이터 공급자에 의해 구현 되어야 하는 메서드는 다음과 같습니다.

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>데이터 공급자 논리 구현

다음 단계는 지원할 컨트롤러를 포함 하 여 입력 장치를 관리 하는 논리를 추가 하는 것입니다.

### <a name="implement-the-controller-classes"></a>컨트롤러 클래스 구현

 의 예제에서는 `WindowsMixedRealityDeviceManager` 다음 컨트롤러 클래스를 정의 하 고 구현 합니다.

> 이러한 각 클래스에 대 한 소스 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.

- WindowsMixedRealityArticulatedHand
- WindowsMixedRealityController
- WindowsMixedRealityGGVHand

> [!Note]
> 일부 장치 관리자는 여러 컨트롤러 유형을 지원 하지 않습니다.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>MixedRealityController 특성 적용

그런 다음 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 클래스에 특성을 적용 합니다. 이 특성은 컨트롤러 유형 (예: 트레일러 식), 손 모양 (예: 왼쪽 또는 오른쪽) 및 선택적 컨트롤러 이미지를 지정 합니다.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>상호 작용 매핑 구성

다음 단계는 컨트롤러에서 지 원하는 상호 작용 매핑 집합을 정의 하는 것입니다. Unity의 입력 클래스를 통해 데이터를 수신 하는 장치의 경우 [컨트롤러 매핑 도구](../tools/controller-mapping-tool.md) 는 상호 작용에 할당할 올바른 축 및 단추 매핑을 확인 하는 데 유용한 리소스입니다.

다음 예제는 `GenericOpenVRController` MRTK/Providers/OpenVR 폴더에 있는 클래스에서 간략하게 나와 있습니다.

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)클래스는 Unity 입력 축 및 단추 정의에 대 한 기호화 된 상수를 제공 합니다.

### <a name="raise-notification-events"></a>알림 이벤트 발생

응용 프로그램이 사용자의 입력에 응답할 수 있도록 하기 위해 데이터 공급자는 및 인터페이스에 정의 된 대로 컨트롤러 상태 변경에 해당 하는 알림 이벤트를 발생 시킵니다 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) .

디지털 (단추) 형식 컨트롤의 경우 OnInputDown 및 Oninputdown 이벤트를 발생 시킵니다.

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

아날로그 컨트롤 (예: 터치 패드 위치)의 경우 InputChanged 이벤트가 발생 해야 합니다.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Unity 프로파일러 계측 추가

혼합 현실 응용 프로그램에서 성능이 중요 합니다. 모든 구성 요소는 응용 프로그램을 고려해 야 하는 몇 가지 오버 헤드를 추가 합니다. 이를 위해 모든 입력 데이터 공급자는 내부 루프 및 자주 사용 되는 코드 경로에서 Unity Profiler 계측을 포함 하는 것이 중요 합니다.

사용자 지정 공급자를 계측할 때 MRTK에서 사용한 패턴을 구현 하는 것이 좋습니다.

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> 프로파일러 표식을 식별 하는 데 사용 되는 이름은 임의로 지정 됩니다. MRTK는 다음 패턴을 사용 합니다.
>
> "[product] className. methodName-선택 사항
>
> 사용자 지정 데이터 공급자는 추적을 분석할 때 특정 구성 요소 및 메서드를 쉽게 식별할 수 있도록 비슷한 패턴을 따르는 것이 좋습니다.

## <a name="create-the-profile-and-inspector"></a>프로필 및 검사기 만들기

혼합 현실 Toolkit에서 데이터 공급자는 [프로필](../profiles/profiles.md)을 사용 하 여 구성 됩니다.

추가 구성 옵션 (예: [InputSimulationService](../input-simulation/input-simulation-service.md))을 포함 하는 데이터 공급자는 고객이 응용 프로그램의 요구 사항에 가장 적합 한 방식으로 동작을 수정할 수 있도록 프로필 및 검사기를 만들어야 합니다.

> 이 섹션의 예제에 대 한 전체 코드는 MRTK에서 찾을 수 있습니다. Services/InputSimulation 폴더.

### <a name="define-the-profile"></a>프로필 정의

프로필 콘텐츠는 관찰자의 액세스 가능 속성 (예: 업데이트 간격)을 미러링합니다. 각 인터페이스에 정의 된 모든 사용자 구성 가능 속성은 프로필에 포함 되어야 합니다.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

`CreateAssetMenu`특성을 profile 클래스에 적용 하면 고객이 **> 자산 만들기 > Mixed Reality Toolkit > 프로필** 메뉴를 사용 하 여 프로필 인스턴스를 만들 수 있습니다.

### <a name="implement-the-inspector"></a>검사기 구현

프로필 검사기는 프로필 내용을 구성 하 고 볼 수 있는 사용자 인터페이스입니다. 각 프로필 검사자는 [' BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 클래스를 확장 해야 합니다.

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`특성은 검사기가 적용 되는 자산의 유형을 Unity에 알려 줍니다.

## <a name="create-assembly-definitions"></a>어셈블리 정의 만들기

혼합 현실에서는 어셈블리 정의 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용 하 여 구성 요소 간의 종속성을 지정 하 고 컴파일 시간을 단축 하는 Unity를 지원할 Toolkit.

모든 데이터 공급자와 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.

이전 예제에서 [폴더 구조](#recommended-folder-structure) 를 사용 하는 경우 ContosoInput 데이터 공급자에 대 한 두 개의. asmdef 파일이 있습니다.

첫 번째 어셈블리 정의는 데이터 공급자에 대 한 것입니다. 이 예에서는 ContosoInput 라고 하 고 예제의 ContosoInput 폴더에 배치 됩니다.
이 어셈블리 정의는 MixedReality에 대 한 종속성을 지정 해야 합니다. Toolkit 및 해당 어셈블리가 종속 된 다른 어셈블리

ContosoInputEditor 어셈블리 정의는 프로필 검사자 및 모든 편집기 관련 코드를 지정 합니다. 이 파일은 편집기 코드의 루트 폴더에 있어야 합니다. 이 예제에서 파일은 ContosoInput\Editor 폴더에 있습니다. 이 어셈블리 정의에는 ContosoInput 어셈블리에 대 한 참조 및가 포함 됩니다.

- MixedReality. Toolkit
- MixedReality. Toolkit. 편집기. 검사기
- MixedReality. Toolkit. 편집기. 유틸리티

## <a name="register-the-data-provider"></a>데이터 공급자 등록

데이터 공급자를 만든 후에는 입력 시스템에 등록 하 고 응용 프로그램에서 사용할 수 있습니다.

![등록 된 입력 시스템 데이터 공급자](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>패키징 및 배포

타사 구성 요소로 배포 되는 데이터 공급자에는 개발자의 기본 설정에 대 한 패키징 및 배포에 대 한 구체적인 정보가 있습니다. 가장 일반적인 해결책은 unitypackage를 생성 하 고 Unity Asset Store를 통해 배포 하는 것입니다.

microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출 하 고 수락한 경우 microsoft mrtk 팀은 mrtk 제품의 일부로 패키지 하 고 배포 합니다.

## <a name="see-also"></a>추가 정보

- [입력 시스템](overview.md)
- [`BaseInputDeviceManager` 클래스](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` 감열재](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` 감열재](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` 감열재](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` 감열재](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 감열재](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [컨트롤러 매핑 도구](../tools/controller-mapping-tool.md)
