---
title: 추적 서비스 손실
description: MRTK의 LostTracking Service에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176224"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="80114-104">추적 서비스 손실</span><span class="sxs-lookup"><span data-stu-id="80114-104">Lost tracking service</span></span>

![추적 손실](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="80114-106">손실 된 추적 확장 서비스는 손실 된 추적 상태에 대 한 HoloLens 셸 스타일 애니메이션 시각적 표시를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80114-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="80114-107">손실 된 추적 확장을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="80114-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="80114-108">MRTK 프로필에서 손실 된 **추적 서비스** 를 확장에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80114-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="80114-109">**LostTrackingVisualPrefab** 을 포함 하는 **DefaultLostTrackingServiceProfile** 을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="80114-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
