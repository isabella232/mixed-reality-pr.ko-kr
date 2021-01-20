---
title: 응시 및 유지
description: 혼합 현실 응용 프로그램의 눈 및 헤드 응시 및 유지 입력 모델에 대 한 일반적인 개요를 확인 하세요.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 지속, 상호 작용, 디자인, 눈 추적, 헤드 추적, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582131"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="acc4e-104">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="acc4e-104">Gaze and dwell</span></span>

<span data-ttu-id="acc4e-105">손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="acc4e-106">예를 들어 과도 하 게 큰 조건에서 음성 명령은 특정 컨텍스트에서 안정적이 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="acc4e-107">응시 및 유지는 HoloLens에서 실습 작업을 수행할 수 있는 친숙 하 고 간편한 마스터 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="acc4e-108">또한 응시 및 유지는 운영 환경에서 노이즈 간섭 또는 대기 제약 조건과 무관 한 좋은 대체 (fallback)입니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="acc4e-109">여기서는 두 가지 변형 _,_ 즉 [헤드-응시 및](gaze-and-dwell-head.md) 유지와 [눈에 잘](gaze-and-dwell-eyes.md)해 서 유지를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="acc4e-110">시나리오</span><span class="sxs-lookup"><span data-stu-id="acc4e-110">Scenarios</span></span>

<span data-ttu-id="acc4e-111">사용자가 다른 작업을 사용 중이 고, 환경 또는 소셜 제약 조건으로 인해 음성이 100% 안정적이 지 않거나 사용 가능 하지 않은 시나리오에서 뛰어나지만을 응시 하 고 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="acc4e-112">HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="acc4e-113">엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="acc4e-114">차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="acc4e-115">응시 및 유지를 사용 하면 HoloLens를 사용 하는 사용자가 워크플로를 중단 하지 않고 자신에 게 해당 참조 자료를 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc4e-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="acc4e-116">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="acc4e-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="acc4e-117"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="acc4e-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="acc4e-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="acc4e-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="acc4e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="acc4e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="acc4e-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="acc4e-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="acc4e-121">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="acc4e-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="acc4e-122">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="acc4e-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="acc4e-123">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="acc4e-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="acc4e-124">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="acc4e-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="acc4e-125">시선 응시 및 유지(dwell)</span><span class="sxs-lookup"><span data-stu-id="acc4e-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="acc4e-126">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="acc4e-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="acc4e-127">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="acc4e-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="acc4e-128">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="acc4e-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="acc4e-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acc4e-129">See also</span></span>

* [<span data-ttu-id="acc4e-130">시선 기반 상호 작용</span><span class="sxs-lookup"><span data-stu-id="acc4e-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="acc4e-131">HoloLens 2의 시선 추적</span><span class="sxs-lookup"><span data-stu-id="acc4e-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="acc4e-132">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="acc4e-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="acc4e-133">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="acc4e-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="acc4e-134">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="acc4e-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="acc4e-135">손 - 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="acc4e-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="acc4e-136">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="acc4e-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="acc4e-137">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="acc4e-137">Voice input</span></span>](voice-input.md)