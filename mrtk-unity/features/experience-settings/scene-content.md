---
title: SceneContent
description: Mixed Reality 장면 콘텐츠 구성 요소에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647915"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="e8811-104">혼합 현실 장면 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e8811-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="e8811-105">장면에 MRTK를 추가 하면 `MixedRealitySceneContent` gameobject 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="e8811-106">이 개체는 다양 한 환경에서 적절 하 게 확장할 수 있도록 혼합 현실 콘텐츠를 저장 하 고 인스턴스화하는 전용 장소 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="e8811-107">Gameobject에는 **맞춤 형식** 매개 변수를 통해 구성할 수 있는 동일한 **MixedRealitySceneContent** monobehavior가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="e8811-108">이 매개 변수는 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="e8811-109">*AlignWithExperienceScale* -구성 프로필의 [경험 설정](experience-settings.md) 에 설정 된 **대상 환경 규모** 및 **콘텐츠 오프셋** 을 기준으로 콘텐츠를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="e8811-110">*AlignWithHeadHeight* -기본 카메라의 위치인 사용자 헤드의 y 위치에 콘텐츠를 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="e8811-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![편집기에서 만든 혼합 현실 장면 콘텐츠 개체](../images/experience-settings/MixedRealitySceneContent.png)