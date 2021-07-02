---
title: 장면 콘텐츠 Mixed Reality
description: Mixed Reality 장면 콘텐츠 구성 요소에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177342"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="7a101-104">장면 콘텐츠 Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7a101-104">Mixed Reality scene content</span></span>

<span data-ttu-id="7a101-105">장면에 MRTK를 추가하면 `MixedRealitySceneContent` gameobject가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="7a101-106">이 개체는 다양한 환경 간에 적절하게 크기가 조정되도록 Mixed Reality 콘텐츠를 배치하고 인스턴스화하기 위한 전용 위치 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="7a101-107">gameobject에는 **맞춤 형식** 매개 변수를 통해 구성할 수 있는 동일한 **MixedRealitySceneContent** monobehavior가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="7a101-108">이 매개 변수는 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="7a101-109">*AlignWithExperienceScale* - 구성 프로필의 **Experience** [설정](experience-settings.md) 설정된 대상 환경 크기 조정 및 **콘텐츠 오프셋에** 따라 콘텐츠를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="7a101-110">*AlignWithHeadHeight* - 콘텐츠를 주 카메라의 위치인 사용자 머리의 y 위치에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="7a101-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![편집기에서 만든 장면 콘텐츠 개체 Mixed Reality](../images/experience-settings/MixedRealitySceneContent.png)
