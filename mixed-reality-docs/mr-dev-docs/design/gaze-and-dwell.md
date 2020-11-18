---
title: 응시 및 유지
description: (눈/헤드) 응시 및 지속 입력 모델의 일반적인 개요
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 지속, 상호 작용, 디자인, 눈 추적, 헤드 추적, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d47401b65f7d62e1fe59655c42efe72ac68acfc6
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702199"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="864cc-104">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="864cc-104">Gaze and dwell</span></span>

<span data-ttu-id="864cc-105">손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="864cc-106">예를 들어 과도 하 게 큰 조건에서 음성 명령은 특정 컨텍스트에서 안정적이 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="864cc-107">응시 및 유지는 HoloLens에서 실습 작업을 수행할 수 있는 친숙 하 고 간편한 마스터 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="864cc-108">또한 응시 및 유지는 운영 환경에서 노이즈 간섭 또는 대기 제약 조건과 무관 한 좋은 대체 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="864cc-109">여기서는 두 가지 변형 _,_ 즉 [헤드-응시 및](gaze-and-dwell-head.md) 유지와 [눈에 잘](gaze-and-dwell-eyes.md)해 서 유지를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="864cc-110">시나리오</span><span class="sxs-lookup"><span data-stu-id="864cc-110">Scenarios</span></span>

<span data-ttu-id="864cc-111">사용자가 다른 작업을 사용 중이 고, 환경 또는 소셜 제약 조건으로 인해 음성이 100% 안정적이 지 않거나 사용 가능 하지 않은 시나리오에서 뛰어나지만을 응시 하 고 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span>
<span data-ttu-id="864cc-112">HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="864cc-113">엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="864cc-114">차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="864cc-115">응시 및 유지를 사용 하면 HoloLens를 사용 하는 사용자가 워크플로를 중단 하지 않고 자신에 게 해당 참조 자료를 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="864cc-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="864cc-116">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="864cc-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="864cc-117"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="864cc-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="864cc-118"><a href="../hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="864cc-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="864cc-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="864cc-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="864cc-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="864cc-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="864cc-121">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="864cc-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="864cc-122">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="864cc-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="864cc-123">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="864cc-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="864cc-124">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="864cc-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="864cc-125">시선 응시 및 유지(dwell)</span><span class="sxs-lookup"><span data-stu-id="864cc-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="864cc-126">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="864cc-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="864cc-127">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="864cc-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="864cc-128">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="864cc-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="864cc-129">참조</span><span class="sxs-lookup"><span data-stu-id="864cc-129">See also</span></span>
* [<span data-ttu-id="864cc-130">시선 기반 상호 작용</span><span class="sxs-lookup"><span data-stu-id="864cc-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="864cc-131">HoloLens 2의 시선 추적</span><span class="sxs-lookup"><span data-stu-id="864cc-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="864cc-132">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="864cc-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="864cc-133">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="864cc-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="864cc-134">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="864cc-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="864cc-135">손 - 가리키기 및 커밋</span><span class="sxs-lookup"><span data-stu-id="864cc-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="864cc-136">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="864cc-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="864cc-137">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="864cc-137">Voice input</span></span>](voice-input.md)
