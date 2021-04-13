---
title: 커서
description: 대상 벡터의 커서 또는 표시기는 사용자에 대 한 지속적인 피드백을 제공 하 여 HoloLens의 용도에 대 한 정보를 파악할 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (첫 번째 gen), HoloLens 2, 혼합 현실, 커서, 대상 지정, 응시, 제스처, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 광선, 입력
ms.openlocfilehash: 744e75f4212046b7c237a6c6634a4980e9148b0e
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300088"
---
# <a name="cursors"></a><span data-ttu-id="34062-104">커서</span><span class="sxs-lookup"><span data-stu-id="34062-104">Cursors</span></span>

![커서](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="34062-106">커서는 지정 된 시간에 헤드셋에서 사용자의 현재 포커스를 인식 하는 위치에 따라 지속적인 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="34062-107">커서 피드백에는 가상 환경에서 입력에 응답 하는 영역, 홀로그램 또는 점이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="34062-108">커서는 장치가 사용자의 주의를 이해 하는 데 사용 되는 디지털 표현인 경우에도 사용자의 의도를 확인 하는 것과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="34062-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="34062-109">또한 커서 피드백을 통해 사용자는 필요한 시스템 응답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="34062-110">피드백을 사용 하 여 장치에 대 한 사용자의 자신을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="34062-111">**손가락, 광선** 및 **헤드-응시** 의 세 가지 종류의 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="34062-112">이러한 포인팅 커서는 HoloLens, HoloLens 2 및 모던 헤드셋에서 다른 입력 소프트웨어나 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="34062-113">다음은 각 유형의 헤드셋 및 상호 작용 모델에 사용할 커서 유형에 대 한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="34062-114">Mixed Reality Toolkit (MRTK)에서 끌어서 놓기 커서 모듈을 만들어 올바른 포인팅 환경을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="34062-115">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="34062-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="34062-116"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="34062-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="34062-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="34062-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="34062-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="34062-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="34062-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="34062-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="34062-120">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="34062-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="34062-121">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="34062-122">레이 커서</span><span class="sxs-lookup"><span data-stu-id="34062-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="34062-123">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-123">✔️</span></span></td>
        <td><span data-ttu-id="34062-124">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="34062-125">헤드-응시 커서</span><span class="sxs-lookup"><span data-stu-id="34062-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="34062-126">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-126">✔️</span></span></td>
        <td><span data-ttu-id="34062-127">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-127">✔️</span></span></td>
        <td><span data-ttu-id="34062-128">✔️</span><span class="sxs-lookup"><span data-stu-id="34062-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="34062-129">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="34062-129">Finger cursor</span></span>

<span data-ttu-id="34062-130">핑거 커서는 "[손으로 직접 조작](direct-manipulation.md)" 상호 작용 모드를 향상 시키기 위해 HoloLens 2 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="34062-131">손가락을 가리키는 위치를 더 잘 이해 하기 위해 두 인덱스 손가락의 팁에 링을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="34062-132">링 크기는 손가락이 ui 표면에 근접 하는 점을 기반으로 하며, 손가락이 UI에 닿을 때 작은 점으로 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="34062-133">손가락에 가까울수록 링이 더 작습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="34062-134">![손가락 커서](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="34062-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="34062-135">**손가락 커서 1의 시각적 피드백 상태** : 링이 점으로 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="34062-136">2: 링이 표면과 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="34062-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="34062-137">3: 링이 손가락 벡터에 수직 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="34062-138">4: 링 없음</span><span class="sxs-lookup"><span data-stu-id="34062-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="34062-139">레이 커서</span><span class="sxs-lookup"><span data-stu-id="34062-139">Ray cursor</span></span>

<span data-ttu-id="34062-140">광선 커서는 먼 곳의 끝에 연결 하 여 손을 벗어난 개체를 조작할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="34062-141">몰입 형 헤드셋에서 광선은 동작 컨트롤러에서 시작 하 여 점 커서에서 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="34062-142">HoloLens 2에서는 이러한 동작 컨트롤러 광선의 멘 탈 모델을 적용 하 고 직접 조작에 사용 되는 손가락 커서와 일치 하는 고리 모양의 커서에서 끝을 palms에서 시작 하는 손으로 디자인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="34062-143">![레이 커서 컨트롤러](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="34062-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="34062-144">**동작 컨트롤러의 레이 커서**</span><span class="sxs-lookup"><span data-stu-id="34062-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="34062-145">![레이 커서 손 모양](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="34062-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="34062-146">**바늘의 레이 커서**</span><span class="sxs-lookup"><span data-stu-id="34062-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="34062-147">헤드-응시 커서</span><span class="sxs-lookup"><span data-stu-id="34062-147">Head-gaze cursor</span></span>

<span data-ttu-id="34062-148">헤드-응시 커서는 헤드의 위치와 회전을 사용 하는 보이지 않는 헤드 응시 벡터의 끝에 연결 되는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="34062-149">작업을 실행 하기 위해이 포인팅 커서는 공중 탭, 음성 명령, 지속 및 단추 누름과 같은 다양 한 커밋 입력과 쌍을 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="34062-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="34062-150">HoloLens 2에서 헤드-응시는 공기 탭과 far 광선 간의 상호 작용 충돌을 발생 시킬 수 있으므로 공중 탭이 아닌 모든 커밋 입력과 가장 잘 페어링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="34062-151">![헤드 응시 커서 손 모양](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="34062-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="34062-152">**헤드-손 모양 제스처를 사용 하 여 커서 이동**</span><span class="sxs-lookup"><span data-stu-id="34062-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="34062-153">![헤드 응시 커서 음성](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="34062-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="34062-154">**헤드-음성 명령으로 커서를 응시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="34062-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="34062-155">커서 사용자 지정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="34062-155">Cursor customization recommendations</span></span>

<span data-ttu-id="34062-156">커서 피드백 동작 및 모양을 사용자 지정 하려는 경우 다음 몇 가지 디자인 권장 사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34062-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="34062-157">커서 배율</span><span class="sxs-lookup"><span data-stu-id="34062-157">Cursor scale</span></span>

* <span data-ttu-id="34062-158">사용자가 쉽게 콘텐츠를 조작 하 고 볼 수 있도록 커서는 사용 가능한 대상 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="34062-159">사용자가 만드는 환경에 따라 사용자가 볼 때 커서의 크기를 조정 하는 것도 중요 한 고려 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="34062-160">예를 들어 사용자가 더 이상 사용자의 경험을 볼 때 커서가 너무 작아 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="34062-161">커서의 크기를 조정 하는 경우 유기적 느낌을 제공 하기 위해 크기가 조정 될 때 소프트 애니메이션을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="34062-162">방해 하지 않는지 콘텐츠를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-162">Avoid obstructing content.</span></span> <span data-ttu-id="34062-163">Holograms는 환경을 기억 하 고 커서를 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="34062-164">Directionless cursor 셰이프</span><span class="sxs-lookup"><span data-stu-id="34062-164">Directionless cursor shape</span></span>

* <span data-ttu-id="34062-165">하나의 오른쪽 커서 셰이프도 있지만 torus 같은 directionless 셰이프를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="34062-166">특정 방향 (예: 기존 화살표 커서)을 가리키는 커서는 사용자에 게 항상 표시 되는 것으로 혼동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="34062-167">이에 대 한 예외는 커서를 사용 하 여 사용자에 게 상호 작용 명령을 전달 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="34062-168">예를 들어 혼합 현실 OS에서 holograms 크기를 조정 하는 경우 커서는 손을 이동 하 여 홀로그램 크기를 조정 하는 방법을 사용자에 게 지시 하는 화살표를 일시적으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="34062-169">모양 및 느낌</span><span class="sxs-lookup"><span data-stu-id="34062-169">Look and feel</span></span>

* <span data-ttu-id="34062-170">도넛형 또는 torus 모양의 커서는 많은 응용 프로그램에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="34062-171">사용자가 만드는 환경을 가장 잘 나타내는 색과 모양을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="34062-172">커서는 특히 [색 구분](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="34062-173">분산 된 불투명도가 있는 작은 커서는 시각적 계층 구조를 dominating 않고 정보를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="34062-174">콘텐츠를 액세스가 방해 하 고 작업에서 방해 수 있으므로 커서 뒤에 그림자 또는 하이라이트를 사용 하는 것이 cognizant 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="34062-175">커서는 앱의 표면에 맞추고 hug 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="34062-176">사용자는 시스템에서 원하는 위치를 볼 수 있을 뿐만 아니라 시스템에서 주변을 인식 하 고 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="34062-177">예를 들어 Mixed Reality OS의 커서는 사용자가 홀로그램에 직접 표시 하지 않는 경우에도 전 세계의 이해를 목표로 하는 사용자의 표면에 맞춰 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="34062-178">자기적으로 사용자에 게 가까이 있는 대화형 요소로 커서를 잠그면 사용자가 선택 작업을 사용할 때 해당 요소와 상호 작용 하는 확신을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="34062-179">시각적 신호</span><span class="sxs-lookup"><span data-stu-id="34062-179">Visual cues</span></span>

* <span data-ttu-id="34062-180">환경을 단일 홀로그램에 집중 하는 경우 해당 홀로그램에서 볼 때 커서는 홀로그램 및 변경 셰이프만 정렬 하 고 hug 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="34062-181">이는 사용자에 게 홀로그램 작업을 수행할 수 있고 사용자가이를 조작할 수 있음을 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="34062-182">응용 프로그램에서 공간 매핑을 사용 하는 경우 커서가 표시 하는 모든 표면에 커서를 맞추고 hug 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="34062-183">그러면 HoloLens를 사용 하는 사용자에 게 피드백을 제공 하 고 응용 프로그램에서 해당 공간을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="34062-184">이를 통해 강화는 진정한 세계 이며 실제 및 가상 간의 차이를 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="34062-185">보기에 holograms 또는 표면이 없을 때 커서에서 수행 해야 하는 작업을 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="34062-186">사용자 앞의 미리 정해진 거리에 배치 하는 것은 한 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="34062-187">가능한 작업</span><span class="sxs-lookup"><span data-stu-id="34062-187">Possible actions</span></span>

* <span data-ttu-id="34062-188">커서는 여러 아이콘으로 표시 되어 홀로그램에서 크기 조정 또는 회전과 같이 수행할 수 있는 작업을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="34062-189">사용자에 게 무언가가 있음을 의미 하는 경우에만 커서에 추가 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="34062-190">그렇지 않으면 사용자가 상태를 변경 하거나 커서를 혼동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="34062-191">입력 상태</span><span class="sxs-lookup"><span data-stu-id="34062-191">Input state</span></span>

* <span data-ttu-id="34062-192">커서를 사용 하 여 사용자의 입력 상태나 의도를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="34062-193">예를 들어 사용자에 게 시스템 상태를 확인 하 고 응용 프로그램에서 사용자에 게 조치를 취할 준비가 되었음을 알리는 아이콘을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="34062-194">또한 시스템에서 일시 정지 된 색 변경을 통해 음성 명령을 수신 하는 사용자를 표시 하는 커서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="34062-195">다음 커서 상태를 다양 한 방법으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="34062-196">상태 시스템 처럼 커서를 모델링 하 여 이러한 다양 한 상태를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="34062-197">예:</span><span class="sxs-lookup"><span data-stu-id="34062-197">For example:</span></span>
    * <span data-ttu-id="34062-198">유휴 상태는 기본 커서를 표시 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="34062-199">준비 상태는 사용자가 준비 위치에서 사용자 손을 검색 한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="34062-200">상호 작용 상태는 사용자가 특정 상호 작용을 수행 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="34062-201">가능한 작업 상태 또는 가리키기 상태는 홀로그램에서 수행할 수 있는 가능한 작업을 전달 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="34062-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="34062-202">또한 다양 한 상태를 검색할 때 다양 한 아트 자산을 표시 하는 스킨 가능 방식으로 이러한 상태를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="34062-203">"커서를 사용 하지 않음"으로 이동</span><span class="sxs-lookup"><span data-stu-id="34062-203">Going "cursor-free"</span></span>

<span data-ttu-id="34062-204">집중 교육의 의미는 환경의 주요 구성 요소이 고,에 대 한 상호 작용을 가리키는 경우 (응시 및 제스처를 통해) 뛰어난 정밀도가 필요 하지 않은 경우 커서를 사용 하지 않고 디자인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="34062-205">시스템은 여전히 커서의 일반적인 요구 사항을 충족 해야 합니다. 사용자에 게 시스템의 포인팅에 대 한 지속적인 피드백을 제공 하 고 사용자가 시스템에 대 한 사용자를 전달 하도록 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34062-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="34062-206">이는 다른 눈에 띄는 상태를 변경 하 여 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="34062-207">Unity 용 MRTK (Mixed Reality Toolkit)의 커서</span><span class="sxs-lookup"><span data-stu-id="34062-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="34062-208">기본적으로 [Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 셸 시스템 커서와 동일한 시각적 상태를 가진 커서 Prefab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors))를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="34062-209">MRTK 입력 프로필의 포인터 아래에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="34062-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="34062-210">사용자 환경에 맞게이 커서를 바꾸거나 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34062-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="34062-211">아이 추적 입력 환경에서 MRTK는 혼란을 최소화 하기 위해 미묘한 시각적 개체를 포함 하는 EyeGazeCursor를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34062-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="34062-212">MRTK - 포인터 프로필</span><span class="sxs-lookup"><span data-stu-id="34062-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="34062-213">MRTK - 입력 시스템</span><span class="sxs-lookup"><span data-stu-id="34062-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="34062-214">MRTK - 포인터</span><span class="sxs-lookup"><span data-stu-id="34062-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="34062-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34062-215">See also</span></span>

* [<span data-ttu-id="34062-216">제스처</span><span class="sxs-lookup"><span data-stu-id="34062-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="34062-217">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="34062-217">Head-gaze and commit</span></span>](gaze-and-commit.md)