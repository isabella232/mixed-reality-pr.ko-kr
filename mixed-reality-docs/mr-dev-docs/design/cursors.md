---
title: 커서
description: 커서 또는 대상 벡터의 표시기는 사용자가 HoloLens가 의도에 대해 이해하는 내용을 이해할 수 있도록 지속적인 피드백을 제공합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens(1세대), HoloLens 2, Mixed Reality, 커서, 대상 지정, 응시, 제스처, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 광선, 입력
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600382"
---
# <a name="cursors"></a><span data-ttu-id="a584b-104">커서</span><span class="sxs-lookup"><span data-stu-id="a584b-104">Cursors</span></span>

![커서](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="a584b-106">커서는 헤드셋에서 사용자가 현재 포커스가 지정된 시간에 있다고 생각하는 위치에 따라 지속적인 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="a584b-107">커서 피드백에는 입력에 응답하는 가상 환경의 영역, 홀로그램 또는 지점이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="a584b-108">커서는 디바이스가 사용자의 주의를 이해하는 위치에 대한 디지털 표현이지만 사용자의 의도를 결정하는 것과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="a584b-109">또한 커서 피드백을 통해 사용자는 예상할 시스템 응답을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="a584b-110">피드백을 사용하여 디바이스에 의도를 전달하여 사용자 신뢰도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="a584b-111">**커서에는 손가락, 광선** 및 **머리 응시의** 세 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="a584b-112">이러한 포인팅 커서는 HoloLens, HoloLens 2 및 몰입형 헤드셋에서 다양한 입력 형식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="a584b-113">다음은 각 유형의 헤드셋 및 상호 작용 모델에 사용할 커서 유형에 대한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="a584b-114">MRTK(Mixed Reality 도구 키트)에서는 올바른 포인팅 환경을 빌드하는 데 도움이 되는 끌어서 놓기 커서 모듈을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="a584b-115">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="a584b-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a584b-116"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="a584b-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a584b-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a584b-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a584b-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a584b-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a584b-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="a584b-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a584b-120">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a584b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="a584b-122">광선 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a584b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-123">✔️</span></span></td>
        <td><span data-ttu-id="a584b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a584b-125">머리 응시 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="a584b-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-126">✔️</span></span></td>
        <td><span data-ttu-id="a584b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-127">✔️</span></span></td>
        <td><span data-ttu-id="a584b-128">✔️</span><span class="sxs-lookup"><span data-stu-id="a584b-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="a584b-129">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-129">Finger cursor</span></span>

<span data-ttu-id="a584b-130">손가락 커서는["손으로 직접 조작"](direct-manipulation.md)상호 작용 모드를 향상시키기 위해 HoloLens 2 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="a584b-131">손가락이 가리키는 위치를 더 잘 이해하기 위해 두 인덱스 손가락의 팁에 링을 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="a584b-132">링 크기는 손가락이 UI 화면에 근접한 것을 기반으로 하며, 손가락이 UI를 터치할 때 작은 점으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="a584b-133">손가락이 가까울수록 링이 작습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="a584b-134">![손가락 커서](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="a584b-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="a584b-135">**손가락 커서의 시각적 피드백 상태** 1: 링이 점으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="a584b-136">2: 링이 표면에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="a584b-137">3: 링이 손가락 벡터에 수직입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="a584b-138">4: 링이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="a584b-139">광선 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-139">Ray cursor</span></span>

<span data-ttu-id="a584b-140">광선 커서는 원거리 포인팅 광선의 끝에 연결되어 실습을 벗어나는 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="a584b-141">몰입형 헤드셋에서 광선은 모션 컨트롤러에서 꺼내고 점 커서로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="a584b-142">HoloLens 2 이러한 모션 컨트롤러 광선의 멘탈 모델을 적용하고 손끝에서 시작되고 직접 조작에 사용되는 손가락 커서와 일치하는 링 모양의 커서로 끝나는 손 광선을 디자인했습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a584b-143">![광선 커서 컨트롤러](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="a584b-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="a584b-144">**모션 컨트롤러의 광선 커서**</span><span class="sxs-lookup"><span data-stu-id="a584b-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a584b-145">![광선 커서 손](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="a584b-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a584b-146">**손의 광선 커서**</span><span class="sxs-lookup"><span data-stu-id="a584b-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="a584b-147">머리 응시 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-147">Head-gaze cursor</span></span>

<span data-ttu-id="a584b-148">머리 응시 커서는 머리의 위치와 회전을 사용하여 가리킨 보이지 않는 머리 응시 벡터의 끝에 연결되는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="a584b-149">작업을 실행하기 위해 이 포인팅 커서는 에어 탭, 음성 명령, 대기 및 단추 누르기와 같은 다양한 커밋 입력과 쌍을 이루어 드립니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="a584b-150">HoloLens 2 머리 응시는 에어 탭과 원거리 손 광선 간의 상호 작용 충돌이 있기 때문에 에어 탭이 아닌 커밋 입력과 가장 잘 쌍을 이루게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a584b-151">![머리 응시 커서 손](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="a584b-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a584b-152">**손 제스처를 가진 머리 응시 커서**</span><span class="sxs-lookup"><span data-stu-id="a584b-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a584b-153">![머리 응시 커서 음성](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="a584b-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="a584b-154">**음성 명령을 통해 머리 응시 커서**</span><span class="sxs-lookup"><span data-stu-id="a584b-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="a584b-155">커서 사용자 지정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="a584b-155">Cursor customization recommendations</span></span>

<span data-ttu-id="a584b-156">커서 피드백 동작 및 모양을 사용자 지정하려는 경우 몇 가지 디자인 권장 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="a584b-157">커서 배율</span><span class="sxs-lookup"><span data-stu-id="a584b-157">Cursor scale</span></span>

* <span data-ttu-id="a584b-158">커서는 사용 가능한 대상보다 크지 않아야 하며, 사용자가 콘텐츠를 쉽게 조작하고 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="a584b-159">만든 경험에 따라 사용자가 둘러 볼 때 커서 크기를 조정하는 것도 중요한 고려 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="a584b-160">예를 들어 사용자가 환경을 더 자세히 살펴보고 커서가 너무 작아서 손실되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="a584b-161">커서의 크기를 조정하는 경우 크기가 조정됨에 따라 소프트 애니메이션을 적용하여 유기적인 느낌을 주는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="a584b-162">콘텐츠를 방해하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-162">Avoid obstructing content.</span></span> <span data-ttu-id="a584b-163">홀로그램은 환경을 기억하기 쉽게 만들고 커서를 제거하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="a584b-164">방향 없는 커서 모양</span><span class="sxs-lookup"><span data-stu-id="a584b-164">Directionless cursor shape</span></span>

* <span data-ttu-id="a584b-165">오른쪽 커서 모양은 하나도 없지만 torus와 같은 방향 없는 도형을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="a584b-166">어떤 방향(예: 기존 화살표 커서)을 가리키는 커서는 사용자가 항상 그런 방식으로 보이도록 혼동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="a584b-167">커서를 사용하여 상호 작용 명령을 사용자에게 전달하는 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="a584b-168">예를 들어 Mixed Reality OS에서 홀로그램 크기를 조정하는 경우 커서에는 홀로그램 크기를 조정하기 위해 손을 이동하는 방법을 사용자에게 지시하는 화살표가 일시적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="a584b-169">모양과 느낌</span><span class="sxs-lookup"><span data-stu-id="a584b-169">Look and feel</span></span>

* <span data-ttu-id="a584b-170">도넛형 또는 torus 모양의 커서는 많은 애플리케이션에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="a584b-171">만드는 환경을 가장 잘 나타내는 색과 모양을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="a584b-172">커서는 색 [구분이](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)특히 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="a584b-173">불투명도가 균형이 조정된 작은 커서는 시각적 계층 구조를 분산하지 않고 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="a584b-174">커서 뒤에 그림자 또는 강조 표시를 사용하면 콘텐츠를 방해하고 당면한 작업에 방해가 될 수 있기 때문에 인식할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="a584b-175">커서는 앱의 표면에 맞춰지고 곱해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="a584b-176">사용자는 시스템에서 보고 있는 위치를 볼 수 있을 뿐만 아니라 시스템이 주변을 알고 있다는 느낌을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="a584b-177">예를 들어 Mixed Reality OS의 커서는 사용자의 세계 표면에 맞춰져 사용자가 홀로그램을 직접 보고 있지 않더라도 세계를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="a584b-178">커서를 사용자에게 가까이 있을 때 대화형 요소에 자기적으로 잠그면 사용자가 선택 작업을 사용할 때 해당 요소와 상호 작용할 수 있다는 확신을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="a584b-179">시각 신호</span><span class="sxs-lookup"><span data-stu-id="a584b-179">Visual cues</span></span>

* <span data-ttu-id="a584b-180">환경이 단일 홀로그램에 초점을 맞춘 경우 커서는 홀로그램을 비울 때 해당 홀로그램에 맞춰서 마우스를 맞추고 모양을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="a584b-181">이렇게 하면 홀로그램이 실행 가능하고 상호 작용할 수 있음을 사용자에게 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="a584b-182">애플리케이션에서 공간 매핑을 사용하는 경우 커서가 표시되는 모든 표면을 정렬하고 클리핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="a584b-183">이를 통해 HoloLens와 애플리케이션에서 공간을 볼 수 있다는 피드백을 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="a584b-184">이렇게 하면 홀로그램이 실제와 세계에 있다는 사실이 강화되고 실제와 가상 간의 격차를 해소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="a584b-185">보기에 홀로그램 또는 표면이 없을 때 커서가 수행해야 하는 작업을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="a584b-186">사용자 앞에 미리 결정된 거리에 배치하는 것이 한 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="a584b-187">가능한 작업</span><span class="sxs-lookup"><span data-stu-id="a584b-187">Possible actions</span></span>

* <span data-ttu-id="a584b-188">커서는 크기 조정 또는 회전과 같이 홀로그램이 수행할 수 있는 가능한 작업을 전달하기 위해 다른 아이콘으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="a584b-189">커서가 사용자에게 의미가 있는 경우에만 커서에 추가 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="a584b-190">그렇지 않으면 사용자가 상태 변경을 알아차리지 못하거나 커서가 혼동될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="a584b-191">입력 상태</span><span class="sxs-lookup"><span data-stu-id="a584b-191">Input state</span></span>

* <span data-ttu-id="a584b-192">커서를 사용하여 사용자의 입력 상태 또는 의도를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="a584b-193">예를 들어 시스템에 손 상태가 표시되고 애플리케이션이 조치를 취할 준비가 되었다는 것을 사용자에게 알리는 아이콘을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="a584b-194">커서를 사용하여 사용자에게 음성 명령이 잠시 색 변경을 통해 시스템에서 들은 것을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="a584b-195">다음 커서 상태는 다양한 방법으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="a584b-196">상태 시스템처럼 커서를 모델링하여 이러한 다양한 상태를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="a584b-197">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-197">For example:</span></span>
    * <span data-ttu-id="a584b-198">유휴 상태는 기본 커서를 표시하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="a584b-199">준비 상태는 준비 위치에서 사용자의 손을 감지한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="a584b-200">상호 작용 상태는 사용자가 특정 상호 작용을 수행하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="a584b-201">가능한 작업 상태 또는 가리키기 상태는 홀로그램에서 수행할 수 있는 가능한 작업을 전달 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="a584b-202">또한 다양 한 상태를 검색할 때 다양 한 아트 자산을 표시 하는 스킨 가능 방식으로 이러한 상태를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="a584b-203">"커서를 사용 하지 않음"으로 이동</span><span class="sxs-lookup"><span data-stu-id="a584b-203">Going "cursor-free"</span></span>

<span data-ttu-id="a584b-204">집중 교육의 의미는 환경의 주요 구성 요소이 고,에 대 한 상호 작용을 가리키는 경우 (응시 및 제스처를 통해) 뛰어난 정밀도가 필요 하지 않은 경우 커서를 사용 하지 않고 디자인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="a584b-205">시스템은 여전히 커서의 일반적인 요구 사항을 충족 해야 합니다. 사용자에 게 시스템의 포인팅에 대 한 지속적인 피드백을 제공 하 고 사용자가 시스템에 대 한 사용자를 전달 하도록 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="a584b-206">이는 다른 눈에 띄는 상태를 변경 하 여 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a584b-207">Unity 용 MRTK (Mixed Reality Toolkit)의 커서</span><span class="sxs-lookup"><span data-stu-id="a584b-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="a584b-208">기본적으로 [Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 셸 시스템 커서와 동일한 시각적 상태를 가진 커서 Prefab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors))를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="a584b-209">MRTK 입력 프로필의 포인터 아래에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="a584b-210">사용자 환경에 맞게이 커서를 바꾸거나 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="a584b-211">아이 추적 입력 환경에서 MRTK는 혼란을 최소화 하기 위해 미묘한 시각적 개체를 포함 하는 EyeGazeCursor를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a584b-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="a584b-212">MRTK - 포인터 프로필</span><span class="sxs-lookup"><span data-stu-id="a584b-212">MRTK - Pointer profile</span></span>](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="a584b-213">MRTK - 입력 시스템</span><span class="sxs-lookup"><span data-stu-id="a584b-213">MRTK - Input system</span></span>](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="a584b-214">MRTK - 포인터</span><span class="sxs-lookup"><span data-stu-id="a584b-214">MRTK - Pointers</span></span>](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="a584b-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a584b-215">See also</span></span>

* [<span data-ttu-id="a584b-216">제스처</span><span class="sxs-lookup"><span data-stu-id="a584b-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a584b-217">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="a584b-217">Head-gaze and commit</span></span>](gaze-and-commit.md)