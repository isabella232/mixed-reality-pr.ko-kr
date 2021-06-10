---
title: ExperienceSettings
description: MRTK에 대 한 다양 한 환경 설정에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647893"
---
# <a name="experience-settings"></a><span data-ttu-id="40818-104">환경 설정</span><span class="sxs-lookup"><span data-stu-id="40818-104">Experience Settings</span></span>

<span data-ttu-id="40818-105">혼합 현실에 대 한 UI를 만드는 문제 중 하나는 다양 한 환경에서 정렬 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="40818-106">MRTK를 사용 하면 `Target Experience Scale` 장면에 대해 및를 설정할 수 있습니다 `Content Offset` . 그러면 다음을 수행 하 여 대상 배율에 맞게 적절히 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="40818-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="40818-107">혼합 현실 장면 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="40818-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="40818-108">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="40818-108">Boundary System</span></span>

  ![MRTK 구성 프로필의 경험 설정](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="40818-110">대상 환경 크기 조정</span><span class="sxs-lookup"><span data-stu-id="40818-110">Target Experience Scale</span></span>

<span data-ttu-id="40818-111">**대상 환경 규모** 는 환경을 디자인 하는 환경을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40818-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="40818-112">다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-112">It can take on the following values.</span></span>

* <span data-ttu-id="40818-113">*OrientationOnly* -헤드셋 방향만 활용 하 고 무게를 맞춘 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="40818-114">좌표계 원점이 헤드 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="40818-115">*장착* 됨-를 사용 하도록 설계 된 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="40818-116">좌표계 원점이 바닥 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="40818-117">고정 *-고정* 된 용도로 설계 된 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="40818-118">좌표계 원점이 바닥 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="40818-119">*대화방* -실내에서의 이동을 지원 하도록 설계 된 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="40818-120">좌표계 원점이 바닥 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="40818-121">*세계* -실제 세계를 활용 하 고 이동 하도록 설계 된 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="40818-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="40818-122">좌표계 원점이 헤드 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40818-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="40818-123">콘텐츠 오프셋</span><span class="sxs-lookup"><span data-stu-id="40818-123">Content Offset</span></span>

<span data-ttu-id="40818-124">이 매개 변수는 **맞춤 유형이** **환경 크기에 맞게** 설정 된 경우 혼합 된 현실을 포함 하는 [혼합 된 항목](scene-content.md) 의 높이를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40818-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>