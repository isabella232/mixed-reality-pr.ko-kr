---
title: 추적 서비스 손실
description: MRTK의 LostTracking Service에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144521"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="185b6-104">추적 시각화 손실</span><span class="sxs-lookup"><span data-stu-id="185b6-104">Lost tracking visualization</span></span>

![추적 손실](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="185b6-106">손실 된 추적 확장 서비스는 손실 된 추적 상태에 대 한 HoloLens 셸 스타일 애니메이션 시각적 표시를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="185b6-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="185b6-107">손실 된 추적 확장을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="185b6-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="185b6-108">MRTK 프로필에서 손실 된 **추적 서비스** 를 확장에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="185b6-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="185b6-109">**LostTrackingVisualPrefab** 을 포함 하는 **DefaultLostTrackingServiceProfile** 을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="185b6-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
