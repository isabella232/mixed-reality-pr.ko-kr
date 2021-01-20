---
title: 헤드 게이즈(head-gaze) 및 드웰(dwell)
description: 일반적인 시나리오 및 디자인 원칙을 포함 하 여 헤드 응시 및 지속 입력 모델의 개요를 시작 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: 혼합 현실, 응시, 지속, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, ux, 지침, 목록 뷰
ms.openlocfilehash: e70536b7247153979b8650ba1f5bcbe1a7cd08af
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582200"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="49d03-104">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="49d03-104">Head-gaze and dwell</span></span>

<span data-ttu-id="49d03-105">손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="49d03-106">제스처와 같은 음성 명령은 특정 상황(예: 과도하게 소리가 큰 상황)에서 불안정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="49d03-107">또한 음성을 사용하여 컴퓨터를 제어하는 것이 전체적으로 일반적이지는 않지만 보편화되고 있는 것은 확실합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="49d03-108">헤드 게이즈(head-gaze) 및 드웰(dwell)은 HoloLens에서 헤드업 및 핸즈프리 작업을 수행하기에 가장 친숙하고 마스터하기 편한 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="49d03-109">또한 헤드 게이즈(head-gaze) 및 드웰(dwell)은 운영 환경에서 소음 간섭이나 무음 제약과 상관없이 100% 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="49d03-110">시나리오</span><span class="sxs-lookup"><span data-stu-id="49d03-110">Scenarios</span></span>

<span data-ttu-id="49d03-111">헤드-응시 및 유지는 사용자가 다른 작업을 사용 하는 시나리오에서 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="49d03-112">이 기능은 음성이 100% 안정적이 아니거나 환경 또는 소셜 제약 조건으로 인해 사용할 수 있는 경우에도 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="49d03-113">HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="49d03-114">엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="49d03-115">차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="49d03-116">헤드-응시 및 유지를 통해 HoloLens를 사용 하는 사람은 자신의 워크플로를 중단 하지 않고 자신 들이 참조 자료를 안전 하 게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="49d03-117">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="49d03-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="49d03-118"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="49d03-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="49d03-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="49d03-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="49d03-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="49d03-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="49d03-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="49d03-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="49d03-122">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="49d03-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="49d03-123">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="49d03-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="49d03-124">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="49d03-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="49d03-125">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="49d03-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="49d03-126">디자인 원칙</span><span class="sxs-lookup"><span data-stu-id="49d03-126">Design principles</span></span>

<span data-ttu-id="49d03-127">**“과도한 응시” 방지**</span><span class="sxs-lookup"><span data-stu-id="49d03-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="49d03-128">헤드 게이즈(head-gaze) 및 드웰(dwell)에는 직관적인 시각 피드백이 필요하지만 피드백이 너무 많으면 불안정한 상태를 유발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="49d03-129">사용자 의견을 통해 사용자에 게 대상에 대 한 정보를 알려 주지만 자신의 의도에 대해 자동 선택을 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="49d03-130">텍스트, 아이콘 및 레이블을 읽을 때를 선택 하기 전에 사용자에 게 정보를 입력할 수 있는 시간을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="49d03-131">**최적의 속도 구하기**</span><span class="sxs-lookup"><span data-stu-id="49d03-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="49d03-132">드웰(dwell) 상호 작용은 탐색의 영향력에 따라 타이머가 다를 수 있습니다. 사용 빈도가 높은 함수는 일반적으로 채우기 시간이 빠른 것이 유용하고 중대한 함수는 채우기 시간이 긴 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="49d03-133">채우기 효과를 사용하여 타이머를 표시하면, 채우기 색상의 애니메이션 곡선이 채우기 시간이 빠른 느낌에 긍정적인 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="49d03-134">빠른/중간/느린 채우기 속도 재정의 중에서 사용자가 결정할 수 있도록 고려하는 것이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="49d03-135">**요요 효과 절대 금지**</span><span class="sxs-lookup"><span data-stu-id="49d03-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="49d03-136">Yo – yo 효과는 콘텐츠 배치 및 헤드-응시 컨트롤이 반복적으로 조회를 수행 하는 경우 발생 하는 불쾌 한 헤드 이동 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="49d03-137">예를 들어 목록의 맨 아래에 있는 헤드-응시 및 유지 단추를 사용 하 여 탐색을 시작 하 고, 결과를 조회 하 고, 유지 하는 등의 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="49d03-138">결과적으로 발생 하는 패턴은 불편 하므로, 더 작은 앞뒤로 필요로 하는 중앙 위치에 탐색 컨트롤을 배치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="49d03-139">효과를 바탕으로 지속 단추를 배치 하는 것은 편안 하 게 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="49d03-140">초</span><span class="sxs-lookup"><span data-stu-id="49d03-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="49d03-141">UX 지침 및 모범 사례</span><span class="sxs-lookup"><span data-stu-id="49d03-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="49d03-142">대상 크기</span><span class="sxs-lookup"><span data-stu-id="49d03-142">Target sizes</span></span>

<span data-ttu-id="49d03-143">쉽게 액세스할 수 있도록 헤드 응시 및 유지 대상은 편안 하 게 볼 수 있을 만큼 충분히 커야 하며 지정 된 시간 동안 대상에서 한 개의 헤드를 보유 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="49d03-144">가장 편안한 환경을 구현 하기 위해 최소 대상 크기인 2도를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="49d03-145">시각적 피드백</span><span class="sxs-lookup"><span data-stu-id="49d03-145">Visual feedback</span></span>

<span data-ttu-id="49d03-146">드웰(dwell) 타이머를 나타내기 위해 방사형 채우기를 사용하는 경우에는 단추 가운데에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="49d03-147">일관된 응답이 서로 다른 단추의 모두 다른 방향보다는 덜 혼란스럽습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="49d03-148">이 규칙은 방향 상호 작용 (예: nav up/down/left/right 등)의 경우 손상 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="49d03-149">예를 들어, Microsoft Dynamics 365 가이드의 경우 예외적으로 다음/뒤로가 왼쪽에서 오른쪽으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="49d03-150">단추를 설정/해제 하는 등의 경우에는 바깥쪽에서 방사형 채우기를 반전 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="49d03-151">단추 누르기와 반대되는 느낌은 유지하기 좋은 시각 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="49d03-152">점진적 공개</span><span class="sxs-lookup"><span data-stu-id="49d03-152">Progressive disclosure</span></span>

<span data-ttu-id="49d03-153">점진적인 공개란 상호 작용의 각 단계에 해당하는 세부 정보만 표시하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="49d03-154">유지의 경우 유지 대상이 강조 표시에서 표시 됩니다 (예: 목록 컨트롤).</span><span class="sxs-lookup"><span data-stu-id="49d03-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="49d03-155">너무 큰 대상</span><span class="sxs-lookup"><span data-stu-id="49d03-155">Oversized targets</span></span>

<span data-ttu-id="49d03-156">드웰(dwell) 지역은 Microsoft Dynamics 365 가이드의 뒤로 단추처럼, 사용하기 쉽도록 비활성 아이콘보다 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="49d03-157">피드백 지연으로 인한 깜박임 방지</span><span class="sxs-lookup"><span data-stu-id="49d03-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="49d03-158">다른 사람이 드웰(dwell) 대상을 지나칠 때 깜박이지 않도록, 시각 피드백을 시작하기 전에 짧은 지연을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="49d03-159">자주 상호 작용 하는 단추의 경우 응용 프로그램이 반응 하지 않도록 짧은 지연 시간을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="49d03-160">자주 상호 작용 하는 단추의 경우 twitchy 인터페이스를 방지 하는 데 시간이 더 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="49d03-161">UI 패턴</span><span class="sxs-lookup"><span data-stu-id="49d03-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="49d03-162">높은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="49d03-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="49d03-163">높은 빈도 단추는 응용 프로그램 전체에서 일반적으로 사용 되는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="49d03-164">Microsoft Dynamics 365 가이드의 다음 및 뒤로 단추가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="49d03-165">**권장 사항**</span><span class="sxs-lookup"><span data-stu-id="49d03-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="49d03-166">높은 빈도 단추가 크고, head-응시로 더 쉽게 적중 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="49d03-167">인체 공학 덕분을 방지 하려면 눈에 가까운 높이를 유지 하세요.</span><span class="sxs-lookup"><span data-stu-id="49d03-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="49d03-168">*이미지: Microsoft Dynamics 365 가이드 다음 단추*</span><span class="sxs-lookup"><span data-stu-id="49d03-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 다음 단추](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="49d03-170">낮은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="49d03-170">Low frequency buttons</span></span>

<span data-ttu-id="49d03-171">빈도가 낮은 단추는 응용 프로그램 전체에서 정기적으로 상호 작용 하지 않는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="49d03-172">설정 메뉴에 액세스하는 단추 또는 모든 작업을 지우는 단추가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="49d03-173">이러한 단추는 우발적인 활성화를 피하기 위해 빈번한 헤드 게이즈(head-gaze) 경로에서 멀리 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="49d03-174">확인</span><span class="sxs-lookup"><span data-stu-id="49d03-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="49d03-175">작업의 요금 청구, 작업 삭제 또는 긴 프로세스 시작과 같은 심각한 영향을 주는 경우 개인이 단추를 선택 하는 것을 확인 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="49d03-176">**권장 사항**</span><span class="sxs-lookup"><span data-stu-id="49d03-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="49d03-177">주요 단추의 선택을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="49d03-178">선택 강조 표시와 동시에 드웰(dwell) 대상을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="49d03-179">보조 단추의 경우 헤드 게이즈(head-gaze) 시 드웰(dwell) 대상을 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="49d03-180">*이미지: Microsoft Dynamics 365 가이드 확인 대화 상자*</span><span class="sxs-lookup"><span data-stu-id="49d03-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 확인 대화 상자](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="49d03-182">토글 단추</span><span class="sxs-lookup"><span data-stu-id="49d03-182">Toggle buttons</span></span>

<span data-ttu-id="49d03-183">토글 단추를 사용하려면 다소 미묘한 논리가 제대로 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="49d03-184">설정/해제 단추를 활성화 하 고 활성화 하는 경우 단추를 종료 하 고를 반환 하 여 유지 논리를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="49d03-185">가능한 단추가 활성 상태와 비활성 상태를 명확 하 게 유지 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="49d03-186">목록 보기</span><span class="sxs-lookup"><span data-stu-id="49d03-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="49d03-187">목록 뷰는 헤드-응시 및 지속 입력에 대 한 특정 챌린지를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="49d03-188">사용자는 유지 목표를 tiptoe 해야 하는 것과 같은 느낌 없이 콘텐츠를 스캔할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="49d03-189">**권장 사항**</span><span class="sxs-lookup"><span data-stu-id="49d03-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="49d03-190">헤드 gazed 때 전체 행을 강조 표시 하 되, head-응시가 특정 유지 목표에 있지 않으면 유지를 시작 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="49d03-191">시각적 노이즈를 줄이기 위해 행이 강조 표시 된 경우에만 유지 대상을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="49d03-192">유지 대상의 위치와 명확 하 게 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="49d03-193">반복적인 UI를 방지 하기 위해 모든 유지 대상을 한 번에 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="49d03-194">가능한 한 자주 같은 패턴을 재사용 하 여 UX를 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="49d03-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="49d03-195">*이미지: Microsoft Dynamics 365 가이드 목록*</span><span class="sxs-lookup"><span data-stu-id="49d03-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 목록](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="49d03-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49d03-197">See also</span></span>

* [<span data-ttu-id="49d03-198">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="49d03-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="49d03-199">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="49d03-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="49d03-200">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="49d03-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="49d03-201">손 - 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="49d03-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="49d03-202">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="49d03-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="49d03-203">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="49d03-203">Voice input</span></span>](voice-input.md)