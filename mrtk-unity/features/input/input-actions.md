---
title: 입력 작업
description: MRTK에서 입력 작업을 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, InputActions,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176815"
---
# <a name="input-actions"></a><span data-ttu-id="57805-104">입력 작업</span><span class="sxs-lookup"><span data-stu-id="57805-104">Input actions</span></span>

<span data-ttu-id="57805-105">[**입력 작업은**](input-actions.md) 입력을 생성하는 특정 입력 소스에서 애플리케이션 논리를 격리하는 데 도움이 되는 원시 입력에 대한 추상화입니다.</span><span class="sxs-lookup"><span data-stu-id="57805-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="57805-106">예를 들어 *선택* 작업을 정의하고 마우스 왼쪽 단추, 게임 패드의 단추 및 6 DOF 컨트롤러의 트리거에 매핑하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="57805-107">그런 다음 애플리케이션 논리가 생성할 수 있는 모든 다른 입력을 인식하는 대신 입력 *선택* 작업 이벤트를 수신 대기하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="57805-108">입력 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="57805-108">Creating an input action</span></span>

<span data-ttu-id="57805-109">입력 작업은 **입력 작업 프로필에서** 구성되며, Mixed Reality Toolkit 구성 요소의 *입력 시스템 프로필* 내에서 작업 이름과 매핑할 수 있는 입력 형식(축 *제약 조건)을* 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="57805-110">축 **제약** 조건 에 가장 일반적으로 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="57805-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="57805-111">축 제약 조건</span><span class="sxs-lookup"><span data-stu-id="57805-111">Axis Constraint</span></span> | <span data-ttu-id="57805-112">Description</span><span class="sxs-lookup"><span data-stu-id="57805-112">Description</span></span>
--- | ---
<span data-ttu-id="57805-113">디지털</span><span class="sxs-lookup"><span data-stu-id="57805-113">Digital</span></span> | <span data-ttu-id="57805-114">게임 패드 또는 마우스의 이진 단추와 같은 입력 켜기/끄기</span><span class="sxs-lookup"><span data-stu-id="57805-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="57805-115">단일 축</span><span class="sxs-lookup"><span data-stu-id="57805-115">Single Axis</span></span> | <span data-ttu-id="57805-116">게임 패드의 아날로그 트리거와 같은 단일 축 아날로그 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="57805-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="57805-117">이중 축</span><span class="sxs-lookup"><span data-stu-id="57805-117">Dual Axis</span></span> | <span data-ttu-id="57805-118">엄지스틱과 같은 이중 축 아날로그 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="57805-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="57805-119">Six Dof</span><span class="sxs-lookup"><span data-stu-id="57805-119">Six Dof</span></span> | <span data-ttu-id="57805-120">3D는 6개의 DOF 컨트롤러에서 생성된 것과 같이 변환 및 회전이 있는 자세를 취합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="57805-121">에서 전체 목록을 찾을 수 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="57805-122">작업에 입력 매핑</span><span class="sxs-lookup"><span data-stu-id="57805-122">Mapping input to actions</span></span>

<span data-ttu-id="57805-123">입력을 및 작업에 매핑하는 방법은 입력 원본의 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="57805-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="57805-124">컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="57805-124">Controller input</span></span>

<span data-ttu-id="57805-125">입력 시스템 프로필 에서 **컨트롤러 입력 매핑** *프로필* 로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="57805-126">지원되는 모든 컨트롤러 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="57805-127">구성하려는 컨트롤러를 선택하면 모든 컨트롤러 입력과 함께 대화 상자 창이 표시되어 각 컨트롤러에 대한 작업을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="57805-128">음성 입력</span><span class="sxs-lookup"><span data-stu-id="57805-128">Speech input</span></span>

<span data-ttu-id="57805-129">음성 **명령 프로필** 의 *입력 시스템 프로필* 아래에서 현재 정의된 음성 명령 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="57805-130">작업 중 하나를 작업에 매핑하려면 작업 *드롭다운에서* 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="57805-131">제스처 입력</span><span class="sxs-lookup"><span data-stu-id="57805-131">Gesture input</span></span>

<span data-ttu-id="57805-132">입력 시스템 **프로필 아래의 제스처** *프로필에는* 정의된 모든 제스처가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="57805-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="57805-133">작업 드롭다운에서 선택하여 각 *작업을 작업에* 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="57805-134">입력 작업 처리</span><span class="sxs-lookup"><span data-stu-id="57805-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="57805-135">현재 *디지털* 형식의 입력 작업만 이 섹션에 설명된 메서드를 사용하여 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="57805-136">다른 작업 유형의 경우 해당 입력에 대한 이벤트를 직접 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="57805-137">예를 들어 컨트롤러 입력에 매핑된 6개의 DOF 작업을 처리하려면 T = 와 함께 를 사용해야 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 합니다.</span><span class="sxs-lookup"><span data-stu-id="57805-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="57805-138">입력 작업을 처리하는 가장 쉬운 방법은 스크립트를 사용하는 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="57805-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="57805-139">이를 통해 수신 대기하려는 작업을 정의하고 Unity 이벤트를 사용하여 시작된 작업 및 종료된 이벤트에 대응할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="57805-140">더 많은 제어를 원하는 경우 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 스크립트에서 직접 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57805-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="57805-141">처리기 인터페이스를 통한 이벤트 처리에 대한 자세한 내용은 [**입력**](input-events.md) 이벤트 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57805-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="57805-142">예</span><span class="sxs-lookup"><span data-stu-id="57805-142">Examples</span></span>

<span data-ttu-id="57805-143">`MRTK/Examples/Demos/Input/Scenes/InputActions`작업을 만들고, 컨트롤러, 음성 및 제스처 입력에 매핑하고, 이를 사용하여 명령에서 개체를 회전하는 방법을 보여주는 예제 장면을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57805-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
