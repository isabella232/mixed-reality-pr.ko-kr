---
title: 시작 제스처
description: 시작 제스처를 사용 하 여 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 시작 메뉴를 호출 하는 방법에 대해 알아봅니다.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, 제스처, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 블 룸
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583233"
---
# <a name="start-gesture"></a><span data-ttu-id="aa323-104">시작 제스처</span><span class="sxs-lookup"><span data-stu-id="aa323-104">Start gesture</span></span>

<span data-ttu-id="aa323-105">시작 제스처는 시작 메뉴를 호출 하는 데 사용 되는 손 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="aa323-106">이는 키보드에서 Windows 키를 누르는 것과 동일한 기능입니다. Xbox의 Xbox 버튼 또는 모던 헤드셋 동작 컨트롤러의 Windows 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="aa323-107">상호 작용을 디자인할 때 충돌을 방지 하기 위해 각 혼합 현실 장치에서 예약 된 시스템 제스처에 특히 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa323-108">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="aa323-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aa323-109"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="aa323-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="aa323-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa323-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="aa323-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="aa323-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="aa323-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa323-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="aa323-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="aa323-113">Bloom</span></span></td>
        <td><span data-ttu-id="aa323-114">✔️</span><span class="sxs-lookup"><span data-stu-id="aa323-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="aa323-115">손목 단추</span><span class="sxs-lookup"><span data-stu-id="aa323-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="aa323-116">✔️</span><span class="sxs-lookup"><span data-stu-id="aa323-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="aa323-117">아이 응시 및 야자수</span><span class="sxs-lookup"><span data-stu-id="aa323-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="aa323-118">✔️</span><span class="sxs-lookup"><span data-stu-id="aa323-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="aa323-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="aa323-119">Bloom</span></span>

<span data-ttu-id="aa323-120">"블 룸"는 모방 (꽃 벚꽃)의 기호화 된 제스처로 시작 메뉴를 HoloLens (첫 번째 gen)로 표시 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="aa323-121">Footed 상호 작용, 사용 편의성 및 신속 하 게 회수할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="aa323-122">제스처를 사용 하려면 야자나무를 함께 사용 하 여 손을 놓고 손가락을 확산 시켜 손을 여세요.</span><span class="sxs-lookup"><span data-stu-id="aa323-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="aa323-123">![블 룸 닫기](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="aa323-124">**1 단계: 쉽게 함께 팜 강화**</span><span class="sxs-lookup"><span data-stu-id="aa323-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aa323-125">![블 룸 열기](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="aa323-126">**2 단계: 간편 하 게 확산 된 팜**</span><span class="sxs-lookup"><span data-stu-id="aa323-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="aa323-127">시작 제스처</span><span class="sxs-lookup"><span data-stu-id="aa323-127">Start gesture</span></span>

<span data-ttu-id="aa323-128">HoloLens 2에서는 블 룸 제스처를 사용자에 게 더 많은 instinctual 인 가상 손목 단추로 대체 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="aa323-129">사용자가 손목 단추를 표시 하 여 쉽게 접근 하 고 다른 손으로 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="aa323-130">![손목 단추 준비 완료](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="aa323-131">**1 단계: 손목 단추를 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="aa323-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aa323-132">![손목 단추 누르기](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="aa323-133">**2 단계: 손목 단추 누르기**</span><span class="sxs-lookup"><span data-stu-id="aa323-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="aa323-134">단방향 시작 제스처</span><span class="sxs-lookup"><span data-stu-id="aa323-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa323-135">한 번의 시작 제스처를 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="aa323-136">2019 년 11 월 업데이트 (빌드 18363.1039) 이상으로 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="aa323-137">눈동자 추적이 제대로 작동 하도록 장치에서 눈동자를 보정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="aa323-138">표시 될 때 시작 아이콘 주위에 orbiting 점이 표시 되지 않는 경우 눈은 장치에서 보정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="aa323-139">한 번만 사용 하 여 시작 제스처를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="aa323-140">사용자를 향한 손을 잡고 내부 손목 **시작 아이콘** 을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="aa323-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="aa323-141">**아이콘을 눈에 유지 하면서** 엄지 단추와 인덱스 손가락을 함께 손가락으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa323-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="aa323-142">![손목 단추 준비 완료](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="aa323-143">**1 단계: 손목 단추를 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="aa323-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aa323-144">![손목 단추 손가락으로](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="aa323-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="aa323-145">**2 단계: 단추를 누른 후 손가락으로 이동**</span><span class="sxs-lookup"><span data-stu-id="aa323-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="aa323-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa323-146">See also</span></span>

* [<span data-ttu-id="aa323-147">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="aa323-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="aa323-148">눈-응시</span><span class="sxs-lookup"><span data-stu-id="aa323-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="aa323-149">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="aa323-149">Voice input</span></span>](voice-input.md)