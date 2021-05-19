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
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="1efec-104">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="1efec-104">Creating an input system data provider</span></span>

<span data-ttu-id="1efec-105">Mixed Reality Toolkit 입력 시스템은 입력 장치 지원을 사용 하기 위한 확장 가능한 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="1efec-106">새 하드웨어 플랫폼에 대 한 지원을 추가 하려면 사용자 지정 입력 데이터 공급자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="1efec-107">이 문서에서는 입력 시스템에 대해 장치 관리자 라고도 하는 사용자 지정 데이터 공급자를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="1efec-108">여기에 표시 된 예제 코드는에서 가져온 것입니다 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="1efec-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="1efec-109">이 예제에서 사용 되는 전체 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="1efec-110">네임 스페이스 및 폴더 구조</span><span class="sxs-lookup"><span data-stu-id="1efec-110">Namespace and folder structure</span></span>

<span data-ttu-id="1efec-111">데이터 공급자는 타사 추가 기능 또는 Microsoft Mixed Reality 도구 키트의 일부로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="1efec-112">새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="1efec-113">입력 시스템 데이터 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출 되는 경우 네임 스페이스는 MixedReality (예: MixedReality)로 시작 **해야** 하 고 코드는 mrtk/providers (예: Mrtk/providers/WindowsMixedReality) 아래에 있는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="1efec-114">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-114">Namespace</span></span>

<span data-ttu-id="1efec-115">데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="1efec-116">네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="1efec-117">회사 이름</span><span class="sxs-lookup"><span data-stu-id="1efec-117">Company name</span></span>
- <span data-ttu-id="1efec-118">기능 영역</span><span class="sxs-lookup"><span data-stu-id="1efec-118">Feature area</span></span>

<span data-ttu-id="1efec-119">예를 들어 Contoso 회사에서 만든 입력 데이터 공급자는 "MixedReality" 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="1efec-120">권장 폴더 구조</span><span class="sxs-lookup"><span data-stu-id="1efec-120">Recommended folder structure</span></span>

<span data-ttu-id="1efec-121">다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![폴더 구조의 예](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="1efec-123">여기서 ContosoInput에는 데이터 공급자의 구현이 포함 되 고 편집기 폴더에는 검사기 (및 기타 Unity 편집기 관련 코드)가 포함 되며, 텍스처 폴더에는 지원 되는 컨트롤러의 이미지가 포함 되 고, 프로필에는 하나 이상의 미리 구성 된 프로필이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="1efec-124">몇 가지 일반적인 컨트롤러 이미지는 MixedRealityToolkit\StandardAssets\Textures 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="1efec-125">데이터 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="1efec-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="1efec-126">인터페이스 및/또는 기본 클래스 상속 지정</span><span class="sxs-lookup"><span data-stu-id="1efec-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="1efec-127">모든 입력 시스템 데이터 공급자는 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 입력 시스템에 필요한 최소 기능을 지정하는 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="1efec-128">MRTK 기초에는 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 이 필수 기능의 기본 구현을 제공하는 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="1efec-129">Unity의 UInput 클래스를 기반으로 하는 디바이스의 경우 [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 클래스를 기본 클래스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="1efec-130">`BaseInputDeviceManager`및 `UnityJoystickManager` 클래스는 필요한 `IMixedRealityInputDeviceManager` 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="1efec-131">`IMixedRealityCapabilityCheck` 사용 되는 `WindowsMixedRealityDeviceManager` 입력된 기능 집합에 대 한 지원을 제공 함을 나타내기 위해 특히, 굴절된 손, 응시 제스처 음성 손 및 모션 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="1efec-132">MixedRealityDataProvider 특성 적용</span><span class="sxs-lookup"><span data-stu-id="1efec-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="1efec-133">입력 시스템 데이터 공급자를 만드는 주요 단계는 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 특성을 클래스에 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="1efec-134">이 단계에서는 입력 시스템 프로필에서 선택할 때 공급자에 대한 기본 프로필 및 플랫폼을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="1efec-135">IMixedRealityDataProvider 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="1efec-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="1efec-136">클래스가 정의되면 다음 단계는 인터페이스의 구현을 제공하는 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="1efec-137">`BaseInputDeviceManager`클래스를 통해 `BaseService` 클래스는 메서드에 대한 빈 구현만 `IMixedRealityDataProvider` 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="1efec-138">이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="1efec-139">데이터 공급자가 구현해야 하는 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="1efec-140">데이터 공급자 논리 구현</span><span class="sxs-lookup"><span data-stu-id="1efec-140">Implement the data provider logic</span></span>

<span data-ttu-id="1efec-141">다음 단계는 지원되는 컨트롤러를 포함하여 입력 디바이스를 관리하기 위한 논리를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="1efec-142">컨트롤러 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="1efec-142">Implement the controller classes</span></span>

 <span data-ttu-id="1efec-143">예제를 `WindowsMixedRealityDeviceManager` 정의 하 고 다음 컨트롤러 클래스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="1efec-144">이러한 각 클래스에 대 한 소스 코드는 MRTK/Providers/WindowsMixedReality 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="1efec-145">WindowsMixedRealityArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="1efec-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="1efec-146">WindowsMixedRealityController</span><span class="sxs-lookup"><span data-stu-id="1efec-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="1efec-147">WindowsMixedRealityGGVHand</span><span class="sxs-lookup"><span data-stu-id="1efec-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="1efec-148">일부 장치 관리자는 여러 컨트롤러 유형을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="1efec-149">MixedRealityController 특성 적용</span><span class="sxs-lookup"><span data-stu-id="1efec-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="1efec-150">그런 다음 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 클래스에 특성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="1efec-151">이 특성은 컨트롤러 유형 (예: 트레일러 식), 손 모양 (예: 왼쪽 또는 오른쪽) 및 선택적 컨트롤러 이미지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="1efec-152">상호 작용 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="1efec-152">Configure the interaction mappings</span></span>

<span data-ttu-id="1efec-153">다음 단계는 컨트롤러에서 지 원하는 상호 작용 매핑 집합을 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="1efec-154">Unity의 입력 클래스를 통해 데이터를 수신 하는 장치의 경우 [컨트롤러 매핑 도구](../tools/controller-mapping-tool.md) 는 상호 작용에 할당할 올바른 축 및 단추 매핑을 확인 하는 데 유용한 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="1efec-155">다음 예제는 `GenericOpenVRController` MRTK/Providers/OpenVR 폴더에 있는 클래스에서 간략하게 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

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
><span data-ttu-id="1efec-156">[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)클래스는 Unity 입력 축 및 단추 정의에 대 한 기호화 된 상수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="1efec-157">알림 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="1efec-157">Raise notification events</span></span>

<span data-ttu-id="1efec-158">응용 프로그램이 사용자의 입력에 응답할 수 있도록 하기 위해 데이터 공급자는 및 인터페이스에 정의 된 대로 컨트롤러 상태 변경에 해당 하는 알림 이벤트를 발생 시킵니다 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) .</span><span class="sxs-lookup"><span data-stu-id="1efec-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="1efec-159">디지털 (단추) 형식 컨트롤의 경우 OnInputDown 및 Oninputdown 이벤트를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

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

<span data-ttu-id="1efec-160">아날로그 컨트롤 (예: 터치 패드 위치)의 경우 InputChanged 이벤트가 발생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="1efec-161">Unity 프로파일러 계측 추가</span><span class="sxs-lookup"><span data-stu-id="1efec-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="1efec-162">혼합 현실 응용 프로그램에서 성능이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="1efec-163">모든 구성 요소는 응용 프로그램을 고려해 야 하는 몇 가지 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="1efec-164">이를 위해 모든 입력 데이터 공급자는 내부 루프 및 자주 활용되는 코드 경로에 Unity Profiler 계측을 포함하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="1efec-165">사용자 지정 공급자를 계측할 때 MRTK에서 사용하는 패턴을 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

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
> <span data-ttu-id="1efec-166">프로파일러 표식 식별에 사용되는 이름은 임의로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="1efec-167">MRTK는 다음 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="1efec-168">"[product] className.methodName - 선택적 참고"</span><span class="sxs-lookup"><span data-stu-id="1efec-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="1efec-169">사용자 지정 데이터 공급자는 추적을 분석할 때 특정 구성 요소 및 메서드의 식별을 간소화하기 위해 유사한 패턴을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="1efec-170">프로필 및 검사기 만들기</span><span class="sxs-lookup"><span data-stu-id="1efec-170">Create the profile and inspector</span></span>

<span data-ttu-id="1efec-171">Mixed Reality 도구 키트에서 데이터 공급자는 프로필을 사용하여 [구성됩니다.](../profiles/profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1efec-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="1efec-172">추가 구성 옵션이 있는 데이터 공급자(예: [InputSimulationService)는](../input-simulation/input-simulation-service.md)고객이 애플리케이션의 요구에 가장 적합하게 동작을 수정할 수 있도록 프로필 및 검사기를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="1efec-173">이 섹션의 예제에 대한 전체 코드는 MRTK에서 찾을 수 있습니다. Services/InputSimulation 폴더.</span><span class="sxs-lookup"><span data-stu-id="1efec-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="1efec-174">프로필 정의</span><span class="sxs-lookup"><span data-stu-id="1efec-174">Define the profile</span></span>

<span data-ttu-id="1efec-175">프로필 콘텐츠는 관찰자의 액세스 가능한 속성(예: 업데이트 간격)을 미러해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="1efec-176">각 인터페이스에 정의된 모든 사용자 구성 가능 속성은 프로필에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="1efec-177">`CreateAssetMenu`특성은 프로필 클래스에 적용하여 고객이 > 자산 만들기 > Mixed Reality 도구 키트 > 프로필 메뉴를 사용하여 프로필 인스턴스를 만들 수 있도록 할 수 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="1efec-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="1efec-178">검사기 구현</span><span class="sxs-lookup"><span data-stu-id="1efec-178">Implement the inspector</span></span>

<span data-ttu-id="1efec-179">프로필 검사자는 프로필 콘텐츠를 구성하고 보기 위한 사용자 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="1efec-180">각 프로필 검사기는 ['BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 클래스를 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="1efec-181">`CustomEditor`특성은 검사자가 적용되는 자산 유형을 Unity에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="1efec-182">어셈블리 정의 만들기</span><span class="sxs-lookup"><span data-stu-id="1efec-182">Create assembly definition(s)</span></span>

<span data-ttu-id="1efec-183">Mixed Reality 도구 키트는 어셈블리 정의([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용하여 구성 요소 간의 의존성을 지정하고 Unity를 통해 컴파일 시간을 단축합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="1efec-184">모든 데이터 공급자와 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="1efec-185">이전 예제에서 [폴더 구조](#recommended-folder-structure) 를 사용 하는 경우 ContosoInput 데이터 공급자에 대 한 두 개의. asmdef 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="1efec-186">첫 번째 어셈블리 정의는 데이터 공급자에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="1efec-187">이 예에서는 ContosoInput 라고 하 고 예제의 ContosoInput 폴더에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="1efec-188">이 어셈블리 정의는 MixedReality에 대 한 종속성과이 도구 키트가 종속 된 다른 모든 어셈블리를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="1efec-189">ContosoInputEditor 어셈블리 정의는 프로필 검사자 및 모든 편집기 관련 코드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="1efec-190">이 파일은 편집기 코드의 루트 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="1efec-191">이 예제에서 파일은 ContosoInput\Editor 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="1efec-192">이 어셈블리 정의에는 ContosoInput 어셈블리에 대 한 참조 및가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="1efec-193">MixedReality</span><span class="sxs-lookup"><span data-stu-id="1efec-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="1efec-194">MixedReality. 검사기</span><span class="sxs-lookup"><span data-stu-id="1efec-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="1efec-195">MixedReality. 유틸리티</span><span class="sxs-lookup"><span data-stu-id="1efec-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="1efec-196">데이터 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="1efec-196">Register the data provider</span></span>

<span data-ttu-id="1efec-197">데이터 공급자를 만든 후에는 입력 시스템에 등록 하 고 응용 프로그램에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![등록 된 입력 시스템 데이터 공급자](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="1efec-199">패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="1efec-199">Packaging and distribution</span></span>

<span data-ttu-id="1efec-200">타사 구성 요소로 배포 되는 데이터 공급자에는 개발자의 기본 설정에 대 한 패키징 및 배포에 대 한 구체적인 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="1efec-201">가장 일반적인 해결책은 unitypackage를 생성 하 고 Unity Asset Store를 통해 배포 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="1efec-202">Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출 하 고 수락한 경우 Microsoft MRTK 팀은 MRTK 제품의 일부로 패키지 하 고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efec-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="1efec-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1efec-203">See also</span></span>

- [<span data-ttu-id="1efec-204">입력 시스템</span><span class="sxs-lookup"><span data-stu-id="1efec-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="1efec-205">`BaseInputDeviceManager` 클래스</span><span class="sxs-lookup"><span data-stu-id="1efec-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="1efec-206">`IMixedRealityInputDeviceManager` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="1efec-207">`IMixedRealityInputHandler` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="1efec-208">`IMixedRealityInputHandler<T>` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="1efec-209">`IMixedRealityDataProvider` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="1efec-210">`IMixedRealityCapabilityCheck` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1efec-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="1efec-211">컨트롤러 매핑 도구</span><span class="sxs-lookup"><span data-stu-id="1efec-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
