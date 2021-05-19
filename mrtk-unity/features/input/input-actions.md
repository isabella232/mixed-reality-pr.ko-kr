---
title: 입력 작업
description: MRTK에서 입력 작업을 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144154"
---
# <a name="input-actions"></a><span data-ttu-id="04f15-104">입력 작업</span><span class="sxs-lookup"><span data-stu-id="04f15-104">Input actions</span></span>

<span data-ttu-id="04f15-105">[**입력 작업은**](input-actions.md) 입력을 생성하는 특정 입력 소스에서 애플리케이션 논리를 격리하는 데 도움이 되는 원시 입력에 대한 추상화입니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="04f15-106">예를 들어 *선택* 작업을 정의하고 마우스 왼쪽 단추, 게임 패드의 단추 및 6 DOF 컨트롤러의 트리거에 매핑하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="04f15-107">그런 다음 애플리케이션 논리가 생성할 수 있는 모든 다른 입력을 인식하는 대신 입력 *작업 선택* 이벤트를 수신 대기하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="04f15-108">입력 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="04f15-108">Creating an input action</span></span>

<span data-ttu-id="04f15-109">입력 작업은 **입력 작업 프로필에서** 구성되며, Mixed Reality 도구 키트 구성 요소의 *입력 시스템 프로필* 내에서 작업 이름과 매핑할 수 있는 입력 유형(축 *제약 조건)을* 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="04f15-110">축 **제약** 조건 에 가장 일반적으로 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="04f15-111">축 제약 조건</span><span class="sxs-lookup"><span data-stu-id="04f15-111">Axis Constraint</span></span> | <span data-ttu-id="04f15-112">설명</span><span class="sxs-lookup"><span data-stu-id="04f15-112">Description</span></span>
--- | ---
<span data-ttu-id="04f15-113">디지털</span><span class="sxs-lookup"><span data-stu-id="04f15-113">Digital</span></span> | <span data-ttu-id="04f15-114">게임 패드 또는 마우스의 이진 단추와 같은 입력 켜기/끄기</span><span class="sxs-lookup"><span data-stu-id="04f15-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="04f15-115">단일 축</span><span class="sxs-lookup"><span data-stu-id="04f15-115">Single Axis</span></span> | <span data-ttu-id="04f15-116">게임 패드의 아날로그 트리거와 같은 단일 축 아날로그 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="04f15-117">이중 축</span><span class="sxs-lookup"><span data-stu-id="04f15-117">Dual Axis</span></span> | <span data-ttu-id="04f15-118">엄지스틱과 같은 이중 축 아날로그 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="04f15-119">Six Dof</span><span class="sxs-lookup"><span data-stu-id="04f15-119">Six Dof</span></span> | <span data-ttu-id="04f15-120">3D는 6개의 DOF 컨트롤러에서 생성된 것과 같이 변환 및 회전이 있는 자세를 취합니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="04f15-121">에서 전체 목록을 찾을 수 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="04f15-122">작업에 입력 매핑</span><span class="sxs-lookup"><span data-stu-id="04f15-122">Mapping input to actions</span></span>

<span data-ttu-id="04f15-123">입력을 및 작업에 매핑하는 방법은 입력 원본의 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="04f15-124">컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="04f15-124">Controller input</span></span>

<span data-ttu-id="04f15-125">*입력 시스템 프로필* 아래의 **컨트롤러 입력 매핑 프로필** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="04f15-126">여기에서 지원 되는 모든 컨트롤러의 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="04f15-127">구성 하려는 항목을 선택 하면 모든 컨트롤러 입력에 대해 대화 상자 창이 표시 되므로 각 사용자에 대 한 작업을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="04f15-128">음성 입력</span><span class="sxs-lookup"><span data-stu-id="04f15-128">Speech input</span></span>

<span data-ttu-id="04f15-129">**음성 명령 프로필** 의 *입력 시스템 프로필* 에 현재 정의 된 음성 명령 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="04f15-130">이러한 작업 중 하나를 작업에 매핑하려면 *작업* 드롭다운에서 선택 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="04f15-131">제스처 입력</span><span class="sxs-lookup"><span data-stu-id="04f15-131">Gesture input</span></span>

<span data-ttu-id="04f15-132">*입력 시스템 프로필* 에 있는 **제스처 프로필** 에는 정의 된 모든 제스처가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="04f15-133">*작업* 드롭다운에서 각 작업을 선택 하 여 작업에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="04f15-134">입력 동작 처리</span><span class="sxs-lookup"><span data-stu-id="04f15-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="04f15-135">현재 *디지털* 형식의 입력 동작만이 섹션에 설명 된 방법을 사용 하 여 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="04f15-136">다른 동작 유형의 경우에는 대신 해당 입력에 대 한 이벤트를 직접 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="04f15-137">예를 들어 컨트롤러 입력에 매핑된 6 DOF 동작을 처리 하려면 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T =와 함께를 사용 해야 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="04f15-138">입력 작업을 처리 하는 가장 쉬운 방법은 스크립트를 사용 하는 것입니다 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) .</span><span class="sxs-lookup"><span data-stu-id="04f15-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="04f15-139">이를 통해 수행 하려는 작업을 정의 하 고 Unity 이벤트를 사용 하 여 작업 시작 됨 및 종료 이벤트에 대응할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="04f15-140">더 많은 제어를 원하는 경우 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 스크립트에서 직접 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f15-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="04f15-141">처리기 인터페이스를 통한 이벤트 처리에 대 한 자세한 내용은 [**입력 이벤트**](input-events.md) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04f15-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="04f15-142">예</span><span class="sxs-lookup"><span data-stu-id="04f15-142">Examples</span></span>

<span data-ttu-id="04f15-143">`MRTK/Examples/Demos/Input/Scenes/InputActions`작업을 만들고, 컨트롤러, 음성 및 제스처 입력을 매핑하고, 명령에서 개체를 회전 하는 데 사용 하는 방법을 보여 주는 예제 장면을 보려면를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04f15-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
