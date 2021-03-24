---
title: 손으로 가리키고 커밋
description: 혼합 현실 애플리케이션에서 제스처 지원을 위한 포인트 및 커밋 입력 모델의 기본 사항에 대해 알아봅니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 상호 작용, 디자인, HoloLens, 손, 원거리, 가리키고 커밋, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 손 광선, 개체 조작, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 8196b67f103bae346ba4da065ee6045ff231b004
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759869"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="db643-104">손으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="db643-104">Point and commit with hands</span></span>

![커서](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="db643-106">손으로 가리키고 커밋은 멀리 떨어져 있는 2D 콘텐츠 및 3D 개체를 겨냥하고, 선택하고, 조작할 수 있는 입력 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="db643-107">“원거리” 상호 작용 기법은 인간이 실제 세상과 자연스럽게 상호 작용하는 방식이 아니므로 혼합 현실에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="db643-108">예를 들어, 슈퍼 영웅 영화인 *엑스맨* 에서 등장 인물 [매그니토](https://en.wikipedia.org/wiki/Magneto_(comics))는 멀리 떨어져 있는 물체를 손으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="db643-109">이것은 사람이 실제로 할 수 있는 일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="db643-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="db643-110">HoloLens(AR)와 Mixed Reality(MR) 모두에서 실제 세계의 물리적 제약 조건을 없애기 위해 사용자에게 이러한 마법 같은 힘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="db643-111">재미있는 홀로그램 환경일 뿐만 아니라 사용자 상호 작용을 보다 효과적이고 효율적으로 만들어 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db643-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="db643-112">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="db643-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="db643-113"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="db643-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="db643-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="db643-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="db643-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="db643-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="db643-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="db643-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="db643-117">손으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="db643-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="db643-118">❌ 지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="db643-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="db643-119">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="db643-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="db643-120">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="db643-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="db643-121">_"손으로 가리키고 커밋"_ 은 새로운 연결형 손 추적 시스템을 사용하는 새로운 기능 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="db643-122">이 입력 모델은 모션 컨트롤러를 사용한 몰입형 헤드셋의 기본 입력 모델이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="db643-123">손 광선</span><span class="sxs-lookup"><span data-stu-id="db643-123">Hand rays</span></span>

<span data-ttu-id="db643-124">HoloLens 2에서 사용자의 손바닥 중앙에서 나오는 손 레이를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="db643-125">이 레이는 손의 연장선으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="db643-126">도넛 모양의 커서가 레이 끝에 연결되어 레이가 대상 개체와 교차하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db643-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="db643-127">그런 다음, 커서가 닿는 개체는 손에서 제스처 명령을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="db643-128">엄지손가락과 집게손가락을 통해 기본적인 제스처 명령이 트리거되면서 에어 탭 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="db643-129">손 레이를 사용하여 가리키고 에어 탭을 사용하여 커밋함으로써, 사용자는 단추 또는 하이퍼링크를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="db643-130">좀 더 복잡한 제스처의 경우, 떨어진 위치에서 웹 콘텐츠를 탐색하고 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="db643-131">손 레이의 시각적 디자인은 아래 설명된 것처럼 이러한 가리키고 커밋 상태에도 대응해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="db643-132">![손 광선 가리키기](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="db643-133">**가리키는 상태**</span><span class="sxs-lookup"><span data-stu-id="db643-133">**Pointing state**</span></span><br>
        <span data-ttu-id="db643-134">*가리키기* 상태에서 레이는 대시이고 커서는 도넛 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db643-135">![손 광선 커밋](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="db643-136">**커밋 상태**</span><span class="sxs-lookup"><span data-stu-id="db643-136">**Commit state**</span></span><br>
        <span data-ttu-id="db643-137">*커밋* 상태에서 레이는 실선으로 바뀌고 커서는 점으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="db643-138">근거리 및 원거리 간 전환</span><span class="sxs-lookup"><span data-stu-id="db643-138">Transition between near and far</span></span>

<span data-ttu-id="db643-139">"집게손가락으로 가리키기"와 같은 특정 제스처를 사용하여 광선을 전달하는 대신 사용자의 손바닥 중앙에서 광선이 발사되도록 설계했습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="db643-140">이러한 방식으로 손가락을 모아서 잡기 같은 더 섬세한 제스처를 위한 Five Fingers를 발표하고 예약했습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="db643-141">이 디자인에서는 근거리 및 원거리 상호 작용 모두에 동일한 손 제스처를 사용하는 한 가지 심리 모델만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db643-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="db643-142">즉, 다른 거리에 있는 개체를 조작하는 데 동일한 잡기 제스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="db643-143">레이 호출은 다음과 같이 자동으로 진행되며 근접성을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="db643-144">![근거리 조작](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="db643-145">**근거리 조작**</span><span class="sxs-lookup"><span data-stu-id="db643-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="db643-146">개체가 팔을 뻗어 닿을 수 있는 거리(약 50cm) 안에 있는 경우 근거리 상호 작용을 위해 레이가 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db643-147">![원거리 조작](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="db643-148">**원거리 조작**</span><span class="sxs-lookup"><span data-stu-id="db643-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="db643-149">개체가 50cm보다 더 멀리 떨어져 있으면 레이가 켜집니다.</span><span class="sxs-lookup"><span data-stu-id="db643-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="db643-150">이러한 전환은 원활하고 매끄럽게 진행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="db643-151">2D 슬레이트 상호 작용</span><span class="sxs-lookup"><span data-stu-id="db643-151">2D slate interaction</span></span>

<span data-ttu-id="db643-152">2D 슬레이트는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 홀로그램 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="db643-153">2D 슬레이트와 먼 거리에서 상호 작용할 경우의 기본적인 개념은 손 광선을 사용하여 타깃팅하고 에어 탭을 사용하여 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="db643-154">손 레이로 타기팅한 후에는 에어 탭을 수행하여 하이퍼링크 또는 단추를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="db643-155">한 손으로 “에어 탭하고 끌기”를 수행하여 슬레이트 콘텐츠를 위아래로 스크롤할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="db643-156">두 손으로 에어 탭을 수행하고 끄는 상대적 동작으로 슬레이트 콘텐츠를 확대 및 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="db643-157">손 레이가 모서리와 가장자리를 직접 향하게 하면 가장 가까운 조작 어포던스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="db643-158">“잡기 및 끌기” 조작 어포던스에서 사용자는 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="db643-159">2D 슬레이트의 맨 위에 있는 홀로바를 잡아서 끌면 전체 슬레이트를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="db643-160">![2D 슬레이트 상호 작용 클릭](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="db643-161">**클릭**</span><span class="sxs-lookup"><span data-stu-id="db643-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-162">![2D 슬레이트 상호 작용 스크롤](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="db643-163">**스크롤**</span><span class="sxs-lookup"><span data-stu-id="db643-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-164">![2D 슬레이트 상호 작용 확대/축소](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="db643-165">**확대/축소**</span><span class="sxs-lookup"><span data-stu-id="db643-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="db643-166">**2D 슬레이트 조작의 경우**</span><span class="sxs-lookup"><span data-stu-id="db643-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="db643-167">사용자는 모서리 또는 가장자리를 손 레이로 가리켜 가장 가까운 조작 어포던스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="db643-168">사용자는 어포던스에 조작 제스처를 적용하여 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="db643-169">2D 슬레이트의 맨 위에 있는 홀로바에 조작 제스처를 적용하여 전체 슬레이트를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="db643-170">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="db643-170">3D object manipulation</span></span>

<span data-ttu-id="db643-171">직접 조작에서 사용자는 어포던스 기반 조작 및 비어포던스 기반 조작의 두 가지 방법으로 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="db643-172">가리키기 및 커밋 모델에서 사용자는 손 광선을 통해 정확히 동일한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="db643-173">추가 학습이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="db643-174">어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="db643-174">Affordance-based manipulation</span></span>

<span data-ttu-id="db643-175">사용자는 손 광선을 사용하여 경계 상자 및 조작 어포던스를 가리키고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="db643-176">사용자는 경계 상자에 조작 제스처를 적용하여 전체 개체를 이동하고, 가장자리 어포던스를 적용하여 회전하고, 모서리 어포던스를 적용하여 균일하게 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="db643-177">![3D 개체 조작 원거리 이동](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="db643-178">**이동**</span><span class="sxs-lookup"><span data-stu-id="db643-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-179">![3D 개체 조작 원거리 회전](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="db643-180">**회전**</span><span class="sxs-lookup"><span data-stu-id="db643-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-181">![3D 개체 조작 원거리 배율](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="db643-182">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="db643-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="db643-183">비어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="db643-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="db643-184">사용자가 직접 손 광선으로 가리켜 경계 상자를 표시한 다음, 조작 제스처를 직접 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="db643-185">한 손을 사용할 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="db643-186">두 손을 사용할 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="db643-187">직관적 제스처</span><span class="sxs-lookup"><span data-stu-id="db643-187">Instinctual gestures</span></span>

<span data-ttu-id="db643-188">가리키고 커밋을 위한 직관적 제스처 개념은 [손을 사용한 직접 조작](direct-manipulation.md)의 개념과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="db643-189">사용자가 3D 개체에 대해 수행해야 하는 제스처는 UI 어포던스의 디자인에 따라 유도됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="db643-190">예를 들어, 사용자는 다섯 손가락을 모두 사용해서 더 큰 개체를 잡을 수도 있지만, 작은 제어점이 사용자가 엄지손가락과 집게손가락을 모으도록 유도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="db643-191">![직관적 제스처 원거리 소형 개체](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="db643-192">**소형 개체**</span><span class="sxs-lookup"><span data-stu-id="db643-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-193">![직관적 제스처 원거리 중형 개체](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="db643-194">**중형 개체**</span><span class="sxs-lookup"><span data-stu-id="db643-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="db643-195">![직관적 제스처 원거리 대형 개체](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="db643-196">**대형 개체**</span><span class="sxs-lookup"><span data-stu-id="db643-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="db643-197">손과 6 DoF 컨트롤러 간의 대칭 디자인</span><span class="sxs-lookup"><span data-stu-id="db643-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="db643-198">Mixed Reality 포털(MRP)에 원거리 상호 작용을 위한 가리키고 커밋이라는 개념이 만들어지고 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db643-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="db643-199">이 시나리오에서 사용자가 몰입형 헤드셋을 쓰고 모션 컨트롤러를 통해 3D 개체와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="db643-200">모션 컨트롤러는 멀리 떨어진 개체를 가리키고 조작하기 위해 레이를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db643-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="db643-201">다른 작업을 추가로 커밋하기 위한 단추가 컨트롤러에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="db643-202">광선의 상호 작용 모델을 적용하고 양손에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="db643-203">이 대칭 디자인에서 MRP에 친숙한 사용자는 HoloLens 2를 사용할 때 먼 거리 가리키기 및 조작을 위해 다른 상호 작용 모델을 학습할 필요가 없으며, 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="db643-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="db643-204">![컨트롤러 사용 광선의 대칭 디자인](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="db643-205">**컨트롤러 광선**</span><span class="sxs-lookup"><span data-stu-id="db643-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db643-206">![손을 사용한 광선의 대칭 디자인](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="db643-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="db643-207">**손 광선**</span><span class="sxs-lookup"><span data-stu-id="db643-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="db643-208">Unity용 MRTK(Mixed Reality Toolkit)의 손 광선</span><span class="sxs-lookup"><span data-stu-id="db643-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="db643-209">기본적으로 MRTK는 셸의 시스템 손 광선과 동일한 시각적 상태의 손 광선 prefab([DefaultControllerPointer. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db643-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="db643-210">MRTK 입력 프로필의 포인터 아래에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="db643-211">몰입형 헤드셋에서 동일한 광선이 모션 컨트롤러에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db643-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="db643-212">MRTK - 포인터 프로필</span><span class="sxs-lookup"><span data-stu-id="db643-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="db643-213">MRTK - 입력 시스템</span><span class="sxs-lookup"><span data-stu-id="db643-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="db643-214">MRTK - 포인터</span><span class="sxs-lookup"><span data-stu-id="db643-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="db643-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db643-215">See also</span></span>
* [<span data-ttu-id="db643-216">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="db643-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="db643-217">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="db643-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="db643-218">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="db643-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="db643-219">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="db643-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="db643-220">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="db643-220">Instinctual interactions</span></span>](interaction-fundamentals.md)