---
title: 입력 시스템 데이터 공급자 만들기
description: MRTK에서 입력 시스템 및 데이터 공급자를 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281927"
---
# <a name="creating-an-input-system-data-provider"></a>입력 시스템 데이터 공급자 만들기

Mixed Reality Toolkit 입력 시스템은 입력 디바이스 지원을 사용하도록 설정하는 데 사용할 수 있는 시스템입니다. 새 하드웨어 플랫폼에 대한 지원을 추가하려면 사용자 지정 입력 데이터 공급자가 필요할 수 있습니다.

이 문서에서는 입력 시스템에 대해 디바이스 관리자라고도 하는 사용자 지정 데이터 공급자를 만드는 방법을 설명합니다. 여기에 표시된 예제 코드는 에서 온 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 것입니다.

> 이 예제에 사용된 전체 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.

## <a name="namespace-and-folder-structure"></a>네임스페이스 및 폴더 구조

데이터 공급자는 타사 추가 기능 또는 Microsoft Mixed Reality Toolkit 일부로 배포할 수 있습니다. MRTK에 새 데이터 공급자를 제출하는 승인 프로세스는 사례별로 다르며 초기 제안 시 전달됩니다.

> [!Important]
> 입력 시스템 데이터 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출되는 경우 네임스페이스는 Microsoft.MixedReality로 시작해야 **합니다.** Toolkit(예: Microsoft.MixedReality.Toolkit. WindowsMixedReality) 및 코드는 MRTK/공급자(예: MRTK/Providers/WindowsMixedReality) 아래의 폴더에 있어야 합니다.

### <a name="namespace"></a>네임스페이스

데이터 공급자는 잠재적인 이름 충돌을 완화하기 위해 네임스페이스가 있어야 합니다. 네임스페이스에는 다음 구성 요소가 포함되는 것이 좋습니다.

- 회사 이름
- 기능 영역

예를 들어 Contoso 회사에서 만든 입력 데이터 공급자는 "Contoso.MixedReality"일 수 있습니다. Toolkit. 입력"을 입력합니다.

### <a name="recommended-folder-structure"></a>권장 폴더 구조

다음 이미지와 같이 데이터 공급자의 소스 코드를 폴더 계층 구조에 배치하는 것이 좋습니다.

![폴더 구조의 예](../images/input/ExampleProviderFolderStructure.png)

ContosoInput에 데이터 공급자의 구현이 포함된 경우 Editor 폴더에는 검사기(및 다른 Unity 편집기 관련 코드)가 포함되고 Textures 폴더에는 지원되는 컨트롤러의 이미지가 포함되고 Profiles에는 미리 만들어진 프로필이 하나 이상 포함되어 있습니다.

> [!Note]
> 몇 가지 일반적인 컨트롤러 이미지는 MixedRealityToolkit\StandardAssets\Textures 폴더에서 찾을 수 있습니다.

## <a name="implement-the-data-provider"></a>데이터 공급자 구현

### <a name="specify-interface-andor-base-class-inheritance"></a>인터페이스 및/또는 기본 클래스 상속 지정

모든 입력 시스템 데이터 공급자는 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 입력 시스템에 필요한 최소 기능을 지정하는 인터페이스를 구현해야 합니다. MRTK 기초에는 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 이 필수 기능의 기본 구현을 제공하는 클래스가 포함되어 있습니다. Unity의 UInput 클래스를 기반으로 하는 디바이스의 경우 [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 클래스를 기본 클래스로 사용할 수 있습니다.

> [!Note]
> `BaseInputDeviceManager`및 `UnityJoystickManager` 클래스는 필요한 `IMixedRealityInputDeviceManager` 구현을 제공합니다.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` 사용 되는 `WindowsMixedRealityDeviceManager` 입력된 기능 집합에 대 한 지원을 제공 함을 나타내기 위해 특히, 굴절형 손, 응시 제스처 음성 손 및 모션 컨트롤러입니다.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>MixedRealityDataProvider 특성 적용

입력 시스템 데이터 공급자를 만드는 주요 단계는 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 특성을 클래스에 적용하는 것입니다. 이 단계에서는 입력 시스템 프로필에서 선택할 때 공급자에 대한 기본 프로필 및 플랫폼을 설정할 수 있습니다.

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

클래스가 정의되면 다음 단계는 인터페이스의 구현을 제공하는 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 것입니다.

> [!Note]
> `BaseInputDeviceManager`클래스를 통해 `BaseService` 클래스는 메서드에 대한 빈 구현만 `IMixedRealityDataProvider` 제공합니다. 이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.

데이터 공급자가 구현해야 하는 메서드는 다음과 같습니다.

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>데이터 공급자 논리 구현

다음 단계는 지원되는 컨트롤러를 포함하여 입력 디바이스를 관리하기 위한 논리를 추가하는 것입니다.

### <a name="implement-the-controller-classes"></a>컨트롤러 클래스 구현

 예제를 `WindowsMixedRealityDeviceManager` 정의 하 고 다음 컨트롤러 클래스를 구현 합니다.

> 이러한 각 클래스의 소스 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> 일부 디바이스 관리자는 여러 컨트롤러 유형을 지원하지 않습니다.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>MixedRealityController 특성 적용

다음으로 특성을 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 클래스에 적용합니다. 이 특성은 컨트롤러의 유형(예: 굴절된 손), 손수(예: 왼쪽 또는 오른쪽) 및 선택적 컨트롤러 이미지를 지정합니다.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>상호 작용 매핑 구성

다음 단계는 컨트롤러에서 지원하는 상호 작용 매핑 집합을 정의하는 것입니다. Unity의 Input 클래스를 통해 데이터를 수신하는 디바이스의 경우 [컨트롤러 매핑 도구는](../tools/controller-mapping-tool.md) 상호 작용에 할당할 올바른 축 및 단추 매핑을 확인하는 데 유용한 리소스입니다.

다음 예제는 `GenericOpenVRController` MRTK/Providers/OpenVR 폴더에 있는 클래스에서 약어로 표시됩니다.

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
>[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)클래스는 Unity 입력 축 및 단추 정의에 대한 기호 상수를 제공합니다.

### <a name="raise-notification-events"></a>알림 이벤트 발생

애플리케이션이 사용자의 입력에 응답할 수 있도록 데이터 공급자는 및 인터페이스에 정의된 컨트롤러 상태 변경에 해당하는 알림 이벤트를 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 발생합니다.

디지털(단추) 형식 컨트롤의 경우 OnInputDown 및 OnInputUp 이벤트를 발생합니다.

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

아날로그 컨트롤(예: 터치 패드 위치)의 경우 InputChanged 이벤트가 발생해야 합니다.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Unity Profiler 계측 추가

성능은 혼합 현실 애플리케이션에서 매우 중요합니다. 모든 구성 요소는 애플리케이션이 고려해야 하는 약간의 오버헤드를 추가합니다. 이를 위해 모든 입력 데이터 공급자는 내부 루프 및 자주 활용되는 코드 경로에 Unity Profiler 계측을 포함하는 것이 중요합니다.

사용자 지정 공급자를 계측할 때 MRTK에서 사용하는 패턴을 구현하는 것이 좋습니다.

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
> 프로파일러 표식 식별에 사용되는 이름은 임의로 지정됩니다. MRTK는 다음 패턴을 사용합니다.
>
> "[product] className.methodName - 선택적 참고"
>
> 사용자 지정 데이터 공급자는 추적을 분석할 때 특정 구성 요소 및 메서드의 식별을 간소화하기 위해 유사한 패턴을 따르는 것이 좋습니다.

## <a name="create-the-profile-and-inspector"></a>프로필 및 검사기 만들기

Mixed Reality Toolkit 데이터 공급자는 프로필을 사용하여 [구성됩니다.](../profiles/profiles.md)

추가 구성 옵션이 있는 데이터 공급자(예: [InputSimulationService)는](../input-simulation/input-simulation-service.md)고객이 애플리케이션의 요구에 가장 적합하게 동작을 수정할 수 있도록 프로필 및 검사기를 만들어야 합니다.

> 이 섹션의 예제에 대한 전체 코드는 MRTK에서 찾을 수 있습니다. Services/InputSimulation 폴더.

### <a name="define-the-profile"></a>프로필 정의

프로필 콘텐츠는 관찰자의 액세스 가능한 속성(예: 업데이트 간격)을 미러해야 합니다. 각 인터페이스에 정의된 모든 사용자 구성 가능 속성은 프로필에 포함되어야 합니다.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

`CreateAssetMenu`특성은 프로필 클래스에 적용하여 고객이 프로필 만들기 > 자산 > Mixed Reality Toolkit > 프로필 메뉴를 사용하여 **프로필 인스턴스를 만들** 수 있도록 합니다.

### <a name="implement-the-inspector"></a>검사기 구현

프로필 검사자는 프로필 콘텐츠를 구성하고 보기 위한 사용자 인터페이스입니다. 각 프로필 검사기는 ['BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 클래스를 확장해야 합니다.

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`특성은 검사자가 적용되는 자산 유형을 Unity에 알릴 수 있습니다.

## <a name="create-assembly-definitions"></a>어셈블리 정의 만들기

Mixed Reality Toolkit 어셈블리 정의([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용하여 구성 요소 간의 의존성을 지정하고 Unity를 통해 컴파일 시간을 단축합니다.

모든 데이터 공급자 및 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.

이전 예제에서 [폴더 구조를](#recommended-folder-structure) 사용하면 ContosoInput 데이터 공급자에 대한 두 개의 .asmdef 파일이 있습니다.

첫 번째 어셈블리 정의는 데이터 공급자에 대한 것입니다. 이 예제에서는 ContosoInput이라고 하며 예제의 ContosoInput 폴더에 있습니다.
이 어셈블리 정의는 Microsoft.MixedReality에 대한 종속성을 지정해야 합니다. Toolkit 및 해당 어셈블리가 의존하는 다른 어셈블리입니다.

ContosoInputEditor 어셈블리 정의는 프로필 검사자와 편집기별 코드를 지정합니다. 이 파일은 편집기 코드의 루트 폴더에 있어야 합니다. 이 예제에서 파일은 ContosoInput\Editor 폴더에 있습니다. 이 어셈블리 정의에는 ContosoInput 어셈블리에 대한 참조도 포함됩니다.

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>데이터 공급자 등록

데이터 공급자를 만든 후에는 입력 시스템에 등록하고 애플리케이션에서 사용할 수 있습니다.

![등록된 입력 시스템 데이터 공급자](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>패키징 및 배포

타사 구성 요소로 배포되는 데이터 공급자에는 패키징 및 배포에 대한 구체적인 세부 정보가 개발자의 기본 설정으로 남아 있습니다. 가장 일반적인 솔루션은 .unitypackage를 생성하고 Unity 자산 저장소를 통해 배포하는 것입니다.

데이터 공급자가 제출되고 Microsoft Mixed Reality Toolkit 패키지의 일부로 수락되면 Microsoft MRTK 팀은 이를 MRTK 제품의 일부로 패키지하고 배포합니다.

## <a name="see-also"></a>참조

- [입력 시스템](overview.md)
- [`BaseInputDeviceManager` 클래스](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [컨트롤러 매핑 도구](../tools/controller-mapping-tool.md)
