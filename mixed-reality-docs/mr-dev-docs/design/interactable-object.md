---
title: 상호 작용 가능한 개체
description: 단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, 큐, ui, ux, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 오디오
ms.openlocfilehash: fb7004c22602683e4edb1e38784cac5c0b7479c4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847858"
---
# <a name="interactable-object"></a><span data-ttu-id="52b9e-105">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="52b9e-105">Interactable object</span></span>

![Interactible 개체](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="52b9e-107">단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="52b9e-108">3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="52b9e-109">모든 항목은 이벤트를 트리거하는 **interactable 개체** 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="52b9e-110">Interactable 개체는 테이블의 커피에서 midair의 풍선에 이르기까지 모든 것이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-110">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="52b9e-111">대화 상자 UI에서와 같은 특정 상황에서는 여전히 기존 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="52b9e-112">단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-112">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="52b9e-113">Interactable 개체의 중요 한 속성</span><span class="sxs-lookup"><span data-stu-id="52b9e-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="52b9e-114">시각적 신호</span><span class="sxs-lookup"><span data-stu-id="52b9e-114">Visual cues</span></span>

<span data-ttu-id="52b9e-115">시각적 표시는 빛에서 받은 신호를 토대로 하 고 시각적 개체에 의해 시각적 표시를 통해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-115">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="52b9e-116">시각적 시스템은 다양 한 정보, 특히 사람에 게 중요 한 것 이므로 시각적 신호는 전 세계의 정보에 대 한 많은 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="52b9e-117">Holographic 개체는 혼합 현실에서 실제 환경과 혼합 되므로 상호 작용할 수 있는 개체를 이해 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="52b9e-118">사용자 환경에서 interactable 개체의 경우 각 입력 상태에 대해 차별화 된 시각적 표시를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-118">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="52b9e-119">이렇게 하면 사용자가 interactable 하는 환경 부분을 이해 하 고 일관 된 상호 작용 방법을 사용 하 여 사용자를 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="52b9e-120">먼 상호 작용</span><span class="sxs-lookup"><span data-stu-id="52b9e-120">Far interactions</span></span>

<span data-ttu-id="52b9e-121">사용자가 응시, 손 모양 및 동작 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음과 같은 세 입력 상태에 대해 서로 다른 시각적 신호를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="52b9e-122">![interactibleobject-기본값](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="52b9e-123">**기본 (관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="52b9e-124">개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-124">Default idle state of the object.</span></span>
    <span data-ttu-id="52b9e-125">커서가 개체에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-125">The cursor isn't on the object.</span></span> <span data-ttu-id="52b9e-126">직접 검색 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-126">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="52b9e-127">![interactibleobject-상태-대상](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="52b9e-128">**대상 (가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="52b9e-129">개체가 응시 커서, 손가락 근접 또는 동작 컨트롤러의 포인터를 대상으로 하는 경우</span><span class="sxs-lookup"><span data-stu-id="52b9e-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="52b9e-130">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-130">The cursor is on the object.</span></span> <span data-ttu-id="52b9e-131">준비가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="52b9e-132">![interactibleobject-상태-누름](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="52b9e-133">**누름 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-133">**Pressed state**</span></span><br>
        <span data-ttu-id="52b9e-134">공기 탭 제스처를 사용 하 여 개체를 누르면 손가락을 누르거나 동작 컨트롤러의 선택 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="52b9e-135">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-135">The cursor is on the object.</span></span> <span data-ttu-id="52b9e-136">손으로 검색 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="52b9e-137">강조 표시 또는 크기 조정과 같은 기술을 사용 하 여 사용자의 입력 상태를 시각적으로 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="52b9e-138">혼합 현실에서는 시작 메뉴와 앱 바 단추를 사용 하 여 다양 한 입력 상태를 시각화 하는 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-138">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="52b9e-139">**Holographic 단추** 에서 이러한 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-139">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="52b9e-140">![interactibleobject-기본값](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="52b9e-141">**기본 (관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="52b9e-142">![interactibleobject-상태-대상](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="52b9e-143">**대상 (가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="52b9e-144">![interactibleobject-상태-누름](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="52b9e-145">**누름 상태**</span><span class="sxs-lookup"><span data-stu-id="52b9e-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="52b9e-146">거의 상호 작용 (직접)</span><span class="sxs-lookup"><span data-stu-id="52b9e-146">Near interactions (direct)</span></span> 

<span data-ttu-id="52b9e-147">HoloLens 2는 개체와 상호 작용할 수 있도록 하는 트레일러 추적 입력을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-147">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="52b9e-148">사용자 의견을 햅 하 고 완벽 하 게 인식 하지 못하는 경우 개체에서 얼마나 멀리 떨어져 있는지 또는 터치 하 고 있는지를 알려 주는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-148">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="52b9e-149">개체 상태를 전달 하는 데 충분 한 시각적 신호를 제공 하는 것이 중요 합니다. 특히 해당 개체를 기반으로 하는 사용자의 상태를 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-149">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="52b9e-150">시각적 피드백을 사용 하 여 다음 상태를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-150">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="52b9e-151">**Default (관찰)**: 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="52b9e-152">**가리키기**: 손을 홀로그램 근처에 있으면 시각적 개체를 대상으로 하 여 홀로그램을 대상으로 하는 통신으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="52b9e-153">**거리 및 상호 작용 지점**: 홀로그램은 홀로그램 이며, 프로젝션 된 상호 작용 지점을 전달 하 고, 개체에서 손가락으로 얼마나 떨어져 있는지에 대 한 피드백을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="52b9e-154">**연락처 시작**: 터치가 발생 했음을 알리기 위해 시각적 개체 (광원, 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="52b9e-155">**Grasped**: 개체가 Grasped 경우 시각적 개체 (광원, 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="52b9e-156">**연락처 끝**: 터치가 종료 되 면 시각적 개체 (밝은 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="52b9e-157">![가리키기 (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="52b9e-158">**가리키기 (Far)**</span><span class="sxs-lookup"><span data-stu-id="52b9e-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="52b9e-159">손 모양에 따라 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="52b9e-160">![가리키기 (근처)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="52b9e-161">**가리키기 (근처)**</span><span class="sxs-lookup"><span data-stu-id="52b9e-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="52b9e-162">강조 표시 크기는 손 거리에 따라 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="52b9e-163">![터치/누르기](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="52b9e-164">**터치/누르기**</span><span class="sxs-lookup"><span data-stu-id="52b9e-164">**Touch / press**</span></span><br>
        <span data-ttu-id="52b9e-165">시각적 개체와 오디오 피드백</span><span class="sxs-lookup"><span data-stu-id="52b9e-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="52b9e-166">![잡습니다](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="52b9e-167">**잡습니다**</span><span class="sxs-lookup"><span data-stu-id="52b9e-167">**Grasp**</span></span><br>
        <span data-ttu-id="52b9e-168">시각적 개체와 오디오 피드백</span><span class="sxs-lookup"><span data-stu-id="52b9e-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="52b9e-169">[HoloLens 2의 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 는 서로 다른 입력 상호 작용 상태를 시각화 하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="52b9e-170">![기본값](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="52b9e-171">**기본값**</span><span class="sxs-lookup"><span data-stu-id="52b9e-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="52b9e-172">![가리키기](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="52b9e-173">**가리키기**</span><span class="sxs-lookup"><span data-stu-id="52b9e-173">**Hover**</span></span><br>
        <span data-ttu-id="52b9e-174">근접 기반 조명 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="52b9e-175">![터치](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="52b9e-176">**터치**</span><span class="sxs-lookup"><span data-stu-id="52b9e-176">**Touch**</span></span><br>
        <span data-ttu-id="52b9e-177">Ripple 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="52b9e-178">![작업 방법](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="52b9e-179">**작업 방법**</span><span class="sxs-lookup"><span data-stu-id="52b9e-179">**Press**</span></span><br>
        <span data-ttu-id="52b9e-180">프런트 판을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="52b9e-181">HoloLens 2의 "링" 시각 신호</span><span class="sxs-lookup"><span data-stu-id="52b9e-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="52b9e-182">HoloLens 2에는 사용자가 깊이를 인식 하는 데 도움이 될 수 있는 추가적인 시각적 표시 큐가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-182">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="52b9e-183">Fingertip 근처의 링은 개체에 가까울수록 fingertip가 위쪽으로 표시 되 고 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="52b9e-184">누름 상태에 도달 하면 링이 결국 점으로 수렴.</span><span class="sxs-lookup"><span data-stu-id="52b9e-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="52b9e-185">이 시각적 affordance는 사용자가 개체에서 얼마나 떨어져 있는지 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="52b9e-186">*비디오 루프: 경계 상자에 근접 한 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="52b9e-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="52b9e-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="52b9e-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="52b9e-188">![근접 한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="52b9e-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="52b9e-189">오디오 신호</span><span class="sxs-lookup"><span data-stu-id="52b9e-189">Audio cues</span></span>

<span data-ttu-id="52b9e-190">직접 상호 작용을 위해 적절 한 오디오 피드백을 통해 사용자 환경을 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="52b9e-191">오디오 피드백을 사용 하 여 다음 큐를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-191">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="52b9e-192">**연락처 시작**: 터치 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="52b9e-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="52b9e-193">**연락처 끝**: 터치 엔드에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="52b9e-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="52b9e-194">**시작**: 잡기 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="52b9e-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="52b9e-195">**잡기 종료**: 잡기 종료 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="52b9e-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="52b9e-196">음성 명령</span><span class="sxs-lookup"><span data-stu-id="52b9e-196">Voice commanding</span></span><br>
        <span data-ttu-id="52b9e-197">Interactable 개체의 경우 대체 상호 작용 옵션을 지 원하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-197">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="52b9e-198">기본적으로 interactable 되는 모든 개체에 대해 [음성 명령](../out-of-scope/voice-design.md) 지원을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-198">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="52b9e-199">검색 가능성을 향상 시키기 위해 가리키기 상태에서 도구 설명을 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="52b9e-200">*Image: 음성 명령에 대 한 도구 설명*</span><span class="sxs-lookup"><span data-stu-id="52b9e-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![음성 명령](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="52b9e-202">크기 조정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="52b9e-202">Sizing recommendations</span></span> 

<span data-ttu-id="52b9e-203">모든 interactable 개체의 작업을 쉽게 수행할 수 있도록 하려면 사용자에 게 배치 된 거리를 기준으로 interactable가 최소 크기를 충족 하는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-203">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="52b9e-204">시각적 각도는 종종 시각적 호의 각도로 측정 됩니다. 시각적 각도는 사용자의 눈동자와 개체 간의 거리를 기준으로 하며 일정 하 게 유지 되 고, 대상의 실제 크기는 사용자의 거리가 변경 될 때 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-204">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="52b9e-205">사용자의 거리를 기준으로 개체의 필요한 실제 크기를 확인 하려면 [다음과 같은 시각적](https://elvers.us/perception/visualAngle/)각도 계산기를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="52b9e-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="52b9e-206">다음은 interactable 콘텐츠의 최소 크기에 대 한 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="52b9e-207">직접 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="52b9e-208">거리</span><span class="sxs-lookup"><span data-stu-id="52b9e-208">Distance</span></span> | <span data-ttu-id="52b9e-209">시야각</span><span class="sxs-lookup"><span data-stu-id="52b9e-209">Viewing angle</span></span> | <span data-ttu-id="52b9e-210">크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="52b9e-211">45 cm</span><span class="sxs-lookup"><span data-stu-id="52b9e-211">45 cm</span></span>  | <span data-ttu-id="52b9e-212">2 ° 미만</span><span class="sxs-lookup"><span data-stu-id="52b9e-212">no smaller than 2°</span></span> | <span data-ttu-id="52b9e-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="52b9e-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="52b9e-214">![직접 상호 작용의 대상 크기](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="52b9e-215">*직접 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="52b9e-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="52b9e-216">단추의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-216">Target size for buttons</span></span>

<span data-ttu-id="52b9e-217">직접 상호 작용에 대 한 단추를 만들 때 아이콘 및 잠재적으로 일부 텍스트를 포함할 수 있는 충분 한 공간이 있도록 최소 크기인 3.2 x 3.2 cm을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="52b9e-218">거리</span><span class="sxs-lookup"><span data-stu-id="52b9e-218">Distance</span></span> | <span data-ttu-id="52b9e-219">최소 크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="52b9e-220">45 cm</span><span class="sxs-lookup"><span data-stu-id="52b9e-220">45 cm</span></span>  | <span data-ttu-id="52b9e-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="52b9e-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="52b9e-222">![단추의 대상 크기](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="52b9e-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="52b9e-223">*단추의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="52b9e-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="52b9e-224">핸드 레이 또는 응시 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="52b9e-225">거리</span><span class="sxs-lookup"><span data-stu-id="52b9e-225">Distance</span></span> | <span data-ttu-id="52b9e-226">시야각</span><span class="sxs-lookup"><span data-stu-id="52b9e-226">Viewing angle</span></span> | <span data-ttu-id="52b9e-227">크기</span><span class="sxs-lookup"><span data-stu-id="52b9e-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="52b9e-228">2 m</span><span class="sxs-lookup"><span data-stu-id="52b9e-228">2 m</span></span>  | <span data-ttu-id="52b9e-229">1 ° 보다 작음</span><span class="sxs-lookup"><span data-stu-id="52b9e-229">no smaller than 1°</span></span> | <span data-ttu-id="52b9e-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="52b9e-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="52b9e-231">![핸드 레이 또는 응시 상호 작용의 대상 크기](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="52b9e-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="52b9e-232">*핸드 레이 또는 응시 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="52b9e-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="52b9e-233">Unity 용 MRTK (Mixed Reality Toolkit)의 Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="52b9e-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="52b9e-234">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 에서는 [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 스크립트를 사용 하 여 개체를 다양 한 유형의 입력 상호 작용 상태에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="52b9e-235">색, 크기, 재질, 셰이더 등의 개체 속성을 제어 하 여 시각적 상태를 정의할 수 있도록 하는 다양 한 형식의 테마를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-235">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="52b9e-236">Interactable</span><span class="sxs-lookup"><span data-stu-id="52b9e-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="52b9e-237">단추</span><span class="sxs-lookup"><span data-stu-id="52b9e-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="52b9e-238">직접 상호 작용 예제 장면</span><span class="sxs-lookup"><span data-stu-id="52b9e-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="52b9e-239">MixedRealityToolkit의 표준 셰이더는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 조명** 과 같은 다양 한 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b9e-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="52b9e-240">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="52b9e-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="52b9e-241">추가 정보</span><span class="sxs-lookup"><span data-stu-id="52b9e-241">See also</span></span>

* [<span data-ttu-id="52b9e-242">커서</span><span class="sxs-lookup"><span data-stu-id="52b9e-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="52b9e-243">손 광선</span><span class="sxs-lookup"><span data-stu-id="52b9e-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="52b9e-244">Button</span><span class="sxs-lookup"><span data-stu-id="52b9e-244">Button</span></span>](button.md)
* [<span data-ttu-id="52b9e-245">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="52b9e-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="52b9e-246">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="52b9e-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="52b9e-247">조작</span><span class="sxs-lookup"><span data-stu-id="52b9e-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="52b9e-248">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="52b9e-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="52b9e-249">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="52b9e-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="52b9e-250">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="52b9e-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="52b9e-251">음성 명령</span><span class="sxs-lookup"><span data-stu-id="52b9e-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="52b9e-252">키보드</span><span class="sxs-lookup"><span data-stu-id="52b9e-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="52b9e-253">Tooltip</span><span class="sxs-lookup"><span data-stu-id="52b9e-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="52b9e-254">슬레이트</span><span class="sxs-lookup"><span data-stu-id="52b9e-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="52b9e-255">슬라이더</span><span class="sxs-lookup"><span data-stu-id="52b9e-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="52b9e-256">셰이더</span><span class="sxs-lookup"><span data-stu-id="52b9e-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="52b9e-257">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="52b9e-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="52b9e-258">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="52b9e-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="52b9e-259">표면 자성</span><span class="sxs-lookup"><span data-stu-id="52b9e-259">Surface magnetism</span></span>](surface-magnetism.md)
