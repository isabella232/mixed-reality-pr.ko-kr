---
title: 입력 데이터 공급자 만들기
description: MRTK에서 입력 시스템 및 데이터 공급자를 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144076"
---
# <a name="creating-an-input-system-data-provider"></a>입력 시스템 데이터 공급자 만들기

Mixed Reality Toolkit 입력 시스템은 입력 장치 지원을 사용 하기 위한 확장 가능한 시스템입니다. 새 하드웨어 플랫폼에 대 한 지원을 추가 하려면 사용자 지정 입력 데이터 공급자가 필요할 수 있습니다.

이 문서에서는 입력 시스템에 대해 장치 관리자 라고도 하는 사용자 지정 데이터 공급자를 만드는 방법을 설명 합니다. 여기에 표시 된 예제 코드는에서 가져온 것입니다 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> 이 예제에서 사용 되는 전체 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.

## <a name="namespace-and-folder-structure"></a>네임 스페이스 및 폴더 구조

데이터 공급자는 타사 추가 기능 또는 Microsoft Mixed Reality 도구 키트의 일부로 배포할 수 있습니다. 새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다.

> [!Important]
> 입력 시스템 데이터 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출 되는 경우 네임 스페이스는 MixedReality (예: MixedReality)로 시작 **해야** 하 고 코드는 mrtk/providers (예: Mrtk/providers/WindowsMixedReality) 아래에 있는 폴더에 있어야 합니다.

### <a name="namespace"></a>네임스페이스

데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다. 네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.

- 회사 이름
- 기능 영역

예를 들어 Contoso 회사에서 만든 입력 데이터 공급자는 "MixedReality" 일 수 있습니다.

### <a name="recommended-folder-structure"></a>권장 폴더 구조

다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.

![폴더 구조의 예](../images/input/ExampleProviderFolderStructure.png)

여기서 ContosoInput에는 데이터 공급자의 구현이 포함 되 고 편집기 폴더에는 검사기 (및 기타 Unity 편집기 관련 코드)가 포함 되며, 텍스처 폴더에는 지원 되는 컨트롤러의 이미지가 포함 되 고, 프로필에는 하나 이상의 미리 구성 된 프로필이 포함 됩니다.

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

> `IMixedRealityCapabilityCheck` 사용 되는 `WindowsMixedRealityDeviceManager` 입력된 기능 집합에 대 한 지원을 제공 함을 나타내기 위해 특히, 굴절된 손, 응시 제스처 음성 손 및 모션 컨트롤러입니다.

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

혼합 현실 응용 프로그램에서 성능이 중요 합니다. 모든 구성 요소는 응용 프로그램을 고려해 야 하는 몇 가지 오버 헤드를 추가 합니다. 이를 위해 모든 입력 데이터 공급자는 내부 루프 및 자주 활용되는 코드 경로에 Unity Profiler 계측을 포함하는 것이 중요합니다.

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

Mixed Reality 도구 키트에서 데이터 공급자는 프로필을 사용하여 [구성됩니다.](../profiles/profiles.md)

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

`CreateAssetMenu`특성은 프로필 클래스에 적용하여 고객이 > 자산 만들기 > Mixed Reality 도구 키트 > 프로필 메뉴를 사용하여 프로필 인스턴스를 만들 수 있도록 할 수 **있습니다.**

### <a name="implement-the-inspector"></a>검사기 구현

프로필 검사자는 프로필 콘텐츠를 구성하고 보기 위한 사용자 인터페이스입니다. 각 프로필 검사기는 ['BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 클래스를 확장해야 합니다.

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`특성은 검사자가 적용되는 자산 유형을 Unity에 알릴 수 있습니다.

## <a name="create-assembly-definitions"></a>어셈블리 정의 만들기

Mixed Reality 도구 키트는 어셈블리 정의([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용하여 구성 요소 간의 의존성을 지정하고 Unity를 통해 컴파일 시간을 단축합니다.

모든 데이터 공급자와 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.

이전 예제에서 [폴더 구조](#recommended-folder-structure) 를 사용 하는 경우 ContosoInput 데이터 공급자에 대 한 두 개의. asmdef 파일이 있습니다.

첫 번째 어셈블리 정의는 데이터 공급자에 대 한 것입니다. 이 예에서는 ContosoInput 라고 하 고 예제의 ContosoInput 폴더에 배치 됩니다.
이 어셈블리 정의는 MixedReality에 대 한 종속성과이 도구 키트가 종속 된 다른 모든 어셈블리를 지정 해야 합니다.

ContosoInputEditor 어셈블리 정의는 프로필 검사자 및 모든 편집기 관련 코드를 지정 합니다. 이 파일은 편집기 코드의 루트 폴더에 있어야 합니다. 이 예제에서 파일은 ContosoInput\Editor 폴더에 있습니다. 이 어셈블리 정의에는 ContosoInput 어셈블리에 대 한 참조 및가 포함 됩니다.

- MixedReality
- MixedReality. 검사기
- MixedReality. 유틸리티

## <a name="register-the-data-provider"></a>데이터 공급자 등록

데이터 공급자를 만든 후에는 입력 시스템에 등록 하 고 응용 프로그램에서 사용할 수 있습니다.

![등록 된 입력 시스템 데이터 공급자](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>패키징 및 배포

타사 구성 요소로 배포 되는 데이터 공급자에는 개발자의 기본 설정에 대 한 패키징 및 배포에 대 한 구체적인 정보가 있습니다. 가장 일반적인 해결책은 unitypackage를 생성 하 고 Unity Asset Store를 통해 배포 하는 것입니다.

Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출 하 고 수락한 경우 Microsoft MRTK 팀은 MRTK 제품의 일부로 패키지 하 고 배포 합니다.

## <a name="see-also"></a>참고 항목

- [입력 시스템](overview.md)
- [`BaseInputDeviceManager` 클래스](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` 인터페이스](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [컨트롤러 매핑 도구](../tools/controller-mapping-tool.md)
