---
title: 상호 작용 가능한 개체
description: 혼합 현실 애플리케이션에서 이벤트를 트리거하고, 시각 신호를 제공하고, 개체와 상호 작용하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, 컨트롤, 상호 작용, 큐, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 오디오
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110213"
---
# <a name="interactable-object"></a><span data-ttu-id="5a122-104">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="5a122-104">Interactable object</span></span>

![상호 작용 가능한 개체](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="5a122-106">단추는 오랫동안 2D 추상 세계에서 이벤트를 트리거하는 데 사용된 메타포입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="5a122-107">3차원 혼합 현실 세계에서는 더 이상 이 추상화 세계로 제한할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="5a122-108">이벤트를 트리거하는 **상호 작용 가능한 개체일** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="5a122-109">상호 작용 가능한 개체는 테이블의 커피 잔에서 중간 계단의 풍선에 이르기까지 모든 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="5a122-110">대화 UI와 같은 특정 상황에서는 여전히 기존 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="5a122-111">단추의 시각적 표현은 컨텍스트에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="5a122-112">상호 작용 가능한 개체의 중요한 속성</span><span class="sxs-lookup"><span data-stu-id="5a122-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="5a122-113">시각 신호</span><span class="sxs-lookup"><span data-stu-id="5a122-113">Visual cues</span></span>

<span data-ttu-id="5a122-114">시각 신호는 시각 인식 중에 눈에서 수신되고 시각적 시스템에서 처리되는 광원의 센서 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="5a122-115">시각적 개체 시스템은 많은 종, 특히 인간에서 주로 적용되므로 시각 신호는 세계를 인식하는 방식에서 정보의 큰 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="5a122-116">홀로그램 개체는 혼합 현실의 실제 환경과 혼합되므로 상호 작용할 수 있는 개체를 이해하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="5a122-117">사용자 환경의 상호 작용 가능한 개체의 경우 각 입력 상태에 대해 차별화된 시각적 신호를 제공하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="5a122-118">이렇게 하면 사용자가 상호 작용 가능한 환경의 일부를 이해하고 일관된 상호 작용 방법을 사용하여 사용자가 안심할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="5a122-119">원거리 상호 작용</span><span class="sxs-lookup"><span data-stu-id="5a122-119">Far interactions</span></span>

<span data-ttu-id="5a122-120">사용자가 응시, 손 광선 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음 세 가지 입력 상태에 대해 서로 다른 시각 신호를 갖는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5a122-121">![기본 상태의 상호 작용 가능한 개체](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="5a122-122">**기본(관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="5a122-123">개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-123">Default idle state of the object.</span></span>
    <span data-ttu-id="5a122-124">커서가 개체에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-124">The cursor isn't on the object.</span></span> <span data-ttu-id="5a122-125">손은 감지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5a122-126">![대상 및 가리키기 상태의 상호 작용 가능한 개체](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="5a122-127">**대상 지정(가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="5a122-128">개체가 응시 커서, 손가락 근접 또는 모션 컨트롤러의 포인터를 대상으로 하는 경우</span><span class="sxs-lookup"><span data-stu-id="5a122-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="5a122-129">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-129">The cursor is on the object.</span></span> <span data-ttu-id="5a122-130">손은 감지되고 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5a122-131">![누른 상태의 상호 작용 가능한 개체](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="5a122-132">**누른 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-132">**Pressed state**</span></span><br>
        <span data-ttu-id="5a122-133">에어 탭 제스처를 통해 개체를 누르면 손가락으로 누르거나 모션 컨트롤러의 선택 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="5a122-134">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-134">The cursor is on the object.</span></span> <span data-ttu-id="5a122-135">손을 감지하고, 에어 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="5a122-136">강조 표시 또는 크기 조정과 같은 기술을 사용하여 사용자의 입력 상태에 대한 시각적 신호를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="5a122-137">혼합 현실에서는 시작 메뉴 앱 바 단추를 통해 다양한 입력 상태를 시각화하는 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="5a122-138">이러한 상태는 **홀로그램 단추** 에서 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5a122-139">![기본 상태의 홀로그램 단추](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="5a122-140">**기본(관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5a122-141">![대상 및 가리키기 상태의 홀로그램 단추](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="5a122-142">**대상 지정(가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5a122-143">![누른 상태의 홀로그램 단추](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="5a122-144">**누른 상태**</span><span class="sxs-lookup"><span data-stu-id="5a122-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="5a122-145">가까운 상호 작용(직접)</span><span class="sxs-lookup"><span data-stu-id="5a122-145">Near interactions (direct)</span></span> 

<span data-ttu-id="5a122-146">HoloLens 2 개체와 상호 작용할 수 있는 굴절형 손 추적 입력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="5a122-147">능동적 피드백과 완벽한 깊이 인식이 없으면 개체에서 얼마나 멀리 떨어져 있는지 또는 터치하고 있는지 여부를 알기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="5a122-148">개체의 상태, 특히 해당 개체를 기반으로 하는 손의 상태를 전달하기에 충분한 시각적 신호를 제공하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="5a122-149">시각적 피드백을 사용하여 다음 상태를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="5a122-150">**기본값(관찰)**: 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="5a122-151">**마우스로 가리키기:** 손을 홀로그램 근처에 있을 때 홀로그램을 대상으로 하는 손을 전달하도록 시각적 개체를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="5a122-152">**거리 및 상호 작용 지점:** 손에서 홀로그램에 접근하면 피드백이 디자인되어 프로젝션된 상호 작용 지점과 손가락이 얼마나 멀리 떨어져 있는지를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="5a122-153">**연락처 시작:** 터치가 발생했음을 전달하도록 시각적 개체(밝게, 색)를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="5a122-154">**이해:** 개체를 파악할 때 시각적 개체(밝게, 색) 변경</span><span class="sxs-lookup"><span data-stu-id="5a122-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="5a122-155">**연락처 종료:** 터치가 종료되면 시각적 개체(밝게, 색) 변경</span><span class="sxs-lookup"><span data-stu-id="5a122-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="5a122-156">![가리키기(원거리)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="5a122-157">**가리키기(원거리)**</span><span class="sxs-lookup"><span data-stu-id="5a122-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="5a122-158">손의 근접성을 기준으로 강조 표시</span><span class="sxs-lookup"><span data-stu-id="5a122-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5a122-159">![가리키기(가까이)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="5a122-160">**가리키기(가까이)**</span><span class="sxs-lookup"><span data-stu-id="5a122-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="5a122-161">손까지의 거리를 기준으로 크기 변경을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="5a122-162">![터치/누르기](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="5a122-163">**터치/누르기**</span><span class="sxs-lookup"><span data-stu-id="5a122-163">**Touch / press**</span></span><br>
        <span data-ttu-id="5a122-164">시각적 개체 및 오디오 피드백.</span><span class="sxs-lookup"><span data-stu-id="5a122-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5a122-165">![파악](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="5a122-166">**파악**</span><span class="sxs-lookup"><span data-stu-id="5a122-166">**Grasp**</span></span><br>
        <span data-ttu-id="5a122-167">시각적 개체 및 오디오 피드백.</span><span class="sxs-lookup"><span data-stu-id="5a122-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="5a122-168">[HoloLens 2 단추는](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 다양한 입력 상호 작용 상태를 시각화하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-168">A [button on HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5a122-169">![기본값](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="5a122-170">**기본값**</span><span class="sxs-lookup"><span data-stu-id="5a122-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5a122-171">![가리키기](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="5a122-172">**가리키기**</span><span class="sxs-lookup"><span data-stu-id="5a122-172">**Hover**</span></span><br>
        <span data-ttu-id="5a122-173">근접 기반 조명 효과를 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="5a122-174">![터치](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="5a122-175">**터치**</span><span class="sxs-lookup"><span data-stu-id="5a122-175">**Touch**</span></span><br>
        <span data-ttu-id="5a122-176">잔물결 효과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5a122-177">![작업 방법](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="5a122-178">**눌러**</span><span class="sxs-lookup"><span data-stu-id="5a122-178">**Press**</span></span><br>
        <span data-ttu-id="5a122-179">앞면판을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="5a122-180">HoloLens 2 "링" 시각 신호</span><span class="sxs-lookup"><span data-stu-id="5a122-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="5a122-181">HoloLens 2 사용자의 깊이 인식에 도움이 될 수 있는 추가 시각 신호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="5a122-182">손끝이 개체에 가까워지면 손끝 근처의 링이 나타나고 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="5a122-183">링은 누른 상태에 도달하면 결국 점으로 수렴됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="5a122-184">이 시각적 어패던스는 사용자가 개체에서 얼마나 멀리 떨어져 있는지 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="5a122-185">*비디오 루프: 경계 상자에 대한 근접성을 기반으로 하는 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="5a122-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5a122-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="5a122-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="5a122-187">![손 근접도에 대한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="5a122-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="5a122-188">오디오 큐</span><span class="sxs-lookup"><span data-stu-id="5a122-188">Audio cues</span></span>

<span data-ttu-id="5a122-189">직접 손 상호 작용을 위해 적절한 오디오 피드백은 사용자 환경을 크게 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="5a122-190">오디오 피드백을 사용하여 다음 신호를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="5a122-191">**연락처 시작: 터치가** 시작될 때 소리 재생</span><span class="sxs-lookup"><span data-stu-id="5a122-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="5a122-192">**연락처 끝:** 터치 엔드에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="5a122-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="5a122-193">**잡기 시작: 잡기가** 시작될 때 소리를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="5a122-194">**잡기 끝: 잡기가** 끝날 때 소리를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="5a122-195">음성 명령</span><span class="sxs-lookup"><span data-stu-id="5a122-195">Voice commanding</span></span><br>
        <span data-ttu-id="5a122-196">상호 작용 가능한 개체의 경우 대체 상호 작용 옵션을 지원하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="5a122-197">기본적으로 상호 작용 가능한 모든 개체에 [대해 음성 명령을](../out-of-scope/voice-design.md) 지원하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="5a122-198">검색 가능성을 개선하기 위해 가리키기 상태 중에 도구 설명도 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="5a122-199">*이미지: 음성 명령에 대한 도구 설명*</span><span class="sxs-lookup"><span data-stu-id="5a122-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![음성 명령](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="5a122-201">크기 조정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a122-201">Sizing recommendations</span></span>

<span data-ttu-id="5a122-202">상호 작용 가능한 모든 개체를 쉽게 터치할 수 있도록 하려면 상호 작용 가능한 가 사용자로부터의 거리를 기준으로 최소 크기를 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="5a122-203">시각적 각도는 종종 시각적 호의 각도로 측정됩니다. 시각적 각도는 사용자의 눈과 개체 사이의 거리를 기반으로 하며 일정하게 유지되지만, 대상의 물리적 크기는 사용자와의 거리가 변경됨에 따라 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="5a122-204">사용자와의 거리를 기준으로 개체의 필요한 물리적 크기를 확인하려면 [이](https://elvers.us/perception/visualAngle/)와 같은 시각적 각도 계산기를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="5a122-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="5a122-205">다음은 상호 작용 가능한 콘텐츠의 최소 크기에 대한 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="5a122-206">직접 손 조작을 위한 대상 크기</span><span class="sxs-lookup"><span data-stu-id="5a122-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="5a122-207">거리</span><span class="sxs-lookup"><span data-stu-id="5a122-207">Distance</span></span> | <span data-ttu-id="5a122-208">시야각</span><span class="sxs-lookup"><span data-stu-id="5a122-208">Viewing angle</span></span> | <span data-ttu-id="5a122-209">크기</span><span class="sxs-lookup"><span data-stu-id="5a122-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="5a122-210">45cm</span><span class="sxs-lookup"><span data-stu-id="5a122-210">45 cm</span></span>  | <span data-ttu-id="5a122-211">2°보다 작지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-211">no smaller than 2°</span></span> | <span data-ttu-id="5a122-212">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="5a122-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="5a122-213">![직접 손 조작을 위한 대상 크기](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="5a122-214">*직접 손 조작을 위한 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="5a122-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="5a122-215">단추의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="5a122-215">Target size for buttons</span></span>

<span data-ttu-id="5a122-216">직접 상호 작용을 위한 단추를 만들 때 아이콘과 일부 텍스트를 포함할 충분한 공간이 있는지 확인하기 위해 최소 크기가 3.2 x 3.2 cm보다 큰 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="5a122-217">거리</span><span class="sxs-lookup"><span data-stu-id="5a122-217">Distance</span></span> | <span data-ttu-id="5a122-218">최소 크기</span><span class="sxs-lookup"><span data-stu-id="5a122-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="5a122-219">45cm</span><span class="sxs-lookup"><span data-stu-id="5a122-219">45 cm</span></span>  | <span data-ttu-id="5a122-220">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="5a122-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="5a122-221">![단추의 대상 크기](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="5a122-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="5a122-222">*단추의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="5a122-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="5a122-223">손 광선 또는 응시 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="5a122-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="5a122-224">거리</span><span class="sxs-lookup"><span data-stu-id="5a122-224">Distance</span></span> | <span data-ttu-id="5a122-225">시야각</span><span class="sxs-lookup"><span data-stu-id="5a122-225">Viewing angle</span></span> | <span data-ttu-id="5a122-226">크기</span><span class="sxs-lookup"><span data-stu-id="5a122-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="5a122-227">2m</span><span class="sxs-lookup"><span data-stu-id="5a122-227">2 m</span></span>  | <span data-ttu-id="5a122-228">1°보다 작지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-228">no smaller than 1°</span></span> | <span data-ttu-id="5a122-229">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="5a122-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="5a122-230">![손 광선 또는 응시 상호 작용의 대상 크기](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="5a122-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="5a122-231">*손 광선 또는 응시 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="5a122-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="5a122-232">Unity용 MRTK(Mixed Reality Toolkit)의 상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="5a122-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="5a122-233">**[MRTK에서](https://github.com/Microsoft/MixedRealityToolkit-Unity)** [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 스크립트를 사용하여 개체가 다양한 유형의 입력 상호 작용 상태에 응답하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="5a122-234">색, 크기, 재질 및 셰이더와 같은 개체 속성을 제어하여 시각적 상태를 정의할 수 있는 다양한 유형의 테마를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="5a122-235">상호 작용 가능</span><span class="sxs-lookup"><span data-stu-id="5a122-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="5a122-236">Button</span><span class="sxs-lookup"><span data-stu-id="5a122-236">Button</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="5a122-237">손 상호 작용 예제 장면</span><span class="sxs-lookup"><span data-stu-id="5a122-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="5a122-238">MixedRealityToolkit의 표준 셰이더에서는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 광원과** 같은 다양한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5a122-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="5a122-239">MRTK 표준 세이더</span><span class="sxs-lookup"><span data-stu-id="5a122-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="5a122-240">참조</span><span class="sxs-lookup"><span data-stu-id="5a122-240">See also</span></span>

* [<span data-ttu-id="5a122-241">커서</span><span class="sxs-lookup"><span data-stu-id="5a122-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5a122-242">손 광선</span><span class="sxs-lookup"><span data-stu-id="5a122-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5a122-243">Button</span><span class="sxs-lookup"><span data-stu-id="5a122-243">Button</span></span>](button.md)
* [<span data-ttu-id="5a122-244">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="5a122-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5a122-245">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="5a122-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5a122-246">조작</span><span class="sxs-lookup"><span data-stu-id="5a122-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5a122-247">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="5a122-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5a122-248">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="5a122-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5a122-249">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="5a122-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5a122-250">음성 명령</span><span class="sxs-lookup"><span data-stu-id="5a122-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5a122-251">키보드</span><span class="sxs-lookup"><span data-stu-id="5a122-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5a122-252">Tooltip</span><span class="sxs-lookup"><span data-stu-id="5a122-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5a122-253">슬레이트</span><span class="sxs-lookup"><span data-stu-id="5a122-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="5a122-254">슬라이더</span><span class="sxs-lookup"><span data-stu-id="5a122-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="5a122-255">셰이더</span><span class="sxs-lookup"><span data-stu-id="5a122-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="5a122-256">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="5a122-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5a122-257">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="5a122-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5a122-258">표면 자성</span><span class="sxs-lookup"><span data-stu-id="5a122-258">Surface magnetism</span></span>](surface-magnetism.md)