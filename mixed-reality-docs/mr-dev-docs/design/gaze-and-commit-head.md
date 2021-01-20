---
title: 헤드 게이즈(head-gaze) 및 커밋
description: 대상 크기 조정, 배치 및 안정화를 포함 하 여 헤드-응시 및 커밋 입력 모델을 시작 합니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 대상 지정, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 대상, 포커스, 다듬기
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582286"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="cfc1b-104">헤드 게이즈(head-gaze) 및 커밋</span><span class="sxs-lookup"><span data-stu-id="cfc1b-104">Head-gaze and commit</span></span>

<span data-ttu-id="cfc1b-105">_헤드-응시 및 커밋은_ 사용자의 방향으로 개체를 대상으로 지정 하는 [응시 및 커밋](gaze-and-commit.md) 입력 모델의 특별 한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="cfc1b-106">손 제스처 air 탭 또는 "선택" 음성 명령과 같은 보조 입력을 사용 하 여 대상에서 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="cfc1b-107">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="cfc1b-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cfc1b-108"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="cfc1b-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="cfc1b-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="cfc1b-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="cfc1b-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="cfc1b-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="cfc1b-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="cfc1b-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cfc1b-112">헤드 게이즈(head-gaze) 및 커밋</span><span class="sxs-lookup"><span data-stu-id="cfc1b-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="cfc1b-113">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="cfc1b-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cfc1b-114">✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</span><span class="sxs-lookup"><span data-stu-id="cfc1b-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="cfc1b-115">➕ 대체 옵션</span><span class="sxs-lookup"><span data-stu-id="cfc1b-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="cfc1b-116">대상 크기 조정 및 피드백</span><span class="sxs-lookup"><span data-stu-id="cfc1b-116">Target sizing and feedback</span></span>

<span data-ttu-id="cfc1b-117">헤드 응시 벡터는 세밀 하 게 대상 지정에 사용할 수 있도록 반복적으로 표시 되었지만 큰 대상을 확보 하는 데 가장 적합 한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="cfc1b-118">최소 대상 크기인 1 ~ 1.5도를 사용 하면 대부분의 시나리오에서 성공적인 사용자 작업을 허용 하지만, 3도의 대상은 속도가 더 높을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="cfc1b-119">사용자가 대상으로 하는 크기는 3D 요소에도 효과적으로 사용할 수 있는 2D 영역입니다. 어떤 프로젝션이 가능 영역 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="cfc1b-120">요소가 "활성" (사용자가 대상으로 하는) 인 두드러진 몇 가지 큐를 제공 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="cfc1b-121">여기에는 표시 되는 "가리키기" 효과, 오디오 하이라이트 또는 클릭 또는 요소와 커서의 처리가 같은 내용이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="cfc1b-122">![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cfc1b-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="cfc1b-123">*2 미터 거리의 최적 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="cfc1b-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="cfc1b-124">![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cfc1b-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="cfc1b-125">*응시 대상 개체를 강조 표시한 예*</span><span class="sxs-lookup"><span data-stu-id="cfc1b-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="cfc1b-126">대상 배치</span><span class="sxs-lookup"><span data-stu-id="cfc1b-126">Target placement</span></span>

<span data-ttu-id="cfc1b-127">사용자는 종종 보기의 필드에 너무 많거나 낮은 UI 요소를 찾지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="cfc1b-128">대부분의 주의가 가장 중요 한 영역에서 가장 중요 한 부분을 차지 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="cfc1b-129">대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="cfc1b-130">사용자가 언제 든 지 상대적으로 작은 시각적 영역에 초점을 맞출 수 있는 경향이 있으므로 (attentional의 비전 원뿔 약 10도), 사용자가 응시를 영역 전체로 이동할 때 UI 요소를 개념적으로 관련 된 수준까지 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="cfc1b-131">UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="cfc1b-132">![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cfc1b-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="cfc1b-133">*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*</span><span class="sxs-lookup"><span data-stu-id="cfc1b-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="cfc1b-134">타기팅 동작 개선</span><span class="sxs-lookup"><span data-stu-id="cfc1b-134">Improving targeting behaviors</span></span>

<span data-ttu-id="cfc1b-135">특정 항목을 대상으로 지정 하는 사용자 의도를 결정 하거나 긴밀 하 게 사용할 수 있는 경우, 정확히 대상으로 지정 된 것 처럼 거의 누락 된 상호 작용 시도를 허용 하면 도움이 될 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="cfc1b-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="cfc1b-136">다음은 혼합 현실 환경에서 통합할 수 있는 성공적인 몇 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="cfc1b-137">헤드 게이즈(head-gaze) 안정화("중력 우물")</span><span class="sxs-lookup"><span data-stu-id="cfc1b-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="cfc1b-138">이는 대부분의 시간 동안 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="cfc1b-139">이 기술은 사용자가 이동 및 말하기 동작으로 인해 이동 하는 것과 같은 자연 스런 head 및 목 jitter을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="cfc1b-140">가장 가까운 링크 알고리즘</span><span class="sxs-lookup"><span data-stu-id="cfc1b-140">Closest link algorithms</span></span>

<span data-ttu-id="cfc1b-141">이러한 알고리즘은 스파스 대화형 콘텐츠가 있는 영역에서 가장 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="cfc1b-142">사용자가 상호 작용 하려고 했던 항목을 결정할 수 있을 확률이 높은 경우 특정 수준의 의도를 가정 하 여 대상 기능을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="cfc1b-143">배경 및 postdating 작업</span><span class="sxs-lookup"><span data-stu-id="cfc1b-143">Backdating and postdating actions</span></span>

<span data-ttu-id="cfc1b-144">이 메커니즘은 속도가 필요한 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="cfc1b-145">사용자가 고속 대상 지정 및 활성화 연습을 통해 이동 하는 경우 몇 가지 의도를 가정 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="cfc1b-146">또한 사용자가 탭을 약간 전후에 초점을 맞춘 대상에 대 한 작업을 수행 하는 데 유용 합니다 (초기 테스트에서 50 밀리초 이전/후에 적용 됨).</span><span class="sxs-lookup"><span data-stu-id="cfc1b-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="cfc1b-147">다듬기</span><span class="sxs-lookup"><span data-stu-id="cfc1b-147">Smoothing</span></span>

<span data-ttu-id="cfc1b-148">이 메커니즘은 자연 스러운 헤드 이동 특성으로 인해 pathing 이동 하 여 약간의 지터와 wobbles를 줄이는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="cfc1b-149">Pathing 동작을 매끄럽게 하는 경우 시간이 지남에 따라 부드러운 이동의 크기와 거리를 매끄럽게 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="cfc1b-150">자성</span><span class="sxs-lookup"><span data-stu-id="cfc1b-150">Magnetism</span></span>

<span data-ttu-id="cfc1b-151">이 메커니즘은 가장 근접 한 링크 알고리즘의 보다 일반적인 버전으로 간주할 수 있습니다. 즉, 사용자가 대화형 레이아웃에 대 한 몇 가지 정보를 사용 하 여 사용자 의도를 보다 효과적으로 활용할 수 있으므로 대상에 커서를 그리거나 단순히 hitboxes를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="cfc1b-152">이는 작은 대상에 대해 강력 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="cfc1b-153">포커스 고착</span><span class="sxs-lookup"><span data-stu-id="cfc1b-153">Focus stickiness</span></span>

<span data-ttu-id="cfc1b-154">에서 제공 하는 근처 대화형 요소를 결정 하는 경우 포커스에 포커스를 지정 하면 현재 포커스가 있는 요소에 대 한 바이어스가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="cfc1b-155">이렇게 하면 자연 노이즈가 있는 두 요소 간의 중간점에서 부동 상태에 있는 경우 비정상적인 포커스 전환 동작을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfc1b-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfc1b-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfc1b-156">See also</span></span>

* [<span data-ttu-id="cfc1b-157">시선 기반 상호 작용</span><span class="sxs-lookup"><span data-stu-id="cfc1b-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="cfc1b-158">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="cfc1b-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="cfc1b-159">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="cfc1b-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cfc1b-160">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="cfc1b-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="cfc1b-161">손 - 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="cfc1b-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="cfc1b-162">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="cfc1b-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="cfc1b-163">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="cfc1b-163">Voice input</span></span>](voice-input.md)