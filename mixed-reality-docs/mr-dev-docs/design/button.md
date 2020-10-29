---
title: 단추
description: 단추를 사용하면 즉각적인 작업을 트리거할 수 있습니다. 혼합 현실에서 가장 기본적인 구성 요소 중 하나입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 150edca67e0115ab6f06165974c00266155765c2
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686208"
---
# <a name="button"></a><span data-ttu-id="67e4d-105">단추</span><span class="sxs-lookup"><span data-stu-id="67e4d-105">Button</span></span>

![단추](images/UX_Hero_Button.jpg)

<span data-ttu-id="67e4d-107">단추를 사용하면 즉각적인 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-107">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="67e4d-108">혼합 현실에서 가장 기본적인 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-108">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="67e4d-109">HoloLens 2에서 단추에는 사용자의 상호 작용 신뢰도를 높이기 위한 많은 시각적 신호 및 affordances 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-109">In HoloLens 2, a button has many visual cues and affordances to increase the user's interaction confidence.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="67e4d-110">![이동](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="67e4d-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="67e4d-111">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="67e4d-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="67e4d-112">![회전](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="67e4d-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="67e4d-113">**포커스 강조 표시**</span><span class="sxs-lookup"><span data-stu-id="67e4d-113">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="67e4d-114">![이동](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="67e4d-114">![Move](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="67e4d-115">**케이지 압축**</span><span class="sxs-lookup"><span data-stu-id="67e4d-115">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="67e4d-116">![회전](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="67e4d-116">![Rotate](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="67e4d-117">**펄스 on 트리거**</span><span class="sxs-lookup"><span data-stu-id="67e4d-117">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="67e4d-118">Unity 용 MRTK (Mixed Reality Toolkit)의 단추</span><span class="sxs-lookup"><span data-stu-id="67e4d-118">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="67e4d-119">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 다양 한 형식의 단추 prefabs 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-119">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="67e4d-120">HoloLens 2 및 HoloLens (첫 번째 gen) 및 사용자 지정 된 예제에 대 한 셸 스타일 단추를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-120">You can find shell-style buttons for HoloLens 2 and HoloLens (1st gen) as well as customized examples.</span></span> <span data-ttu-id="67e4d-121">HoloLens 2 단추 prefab에는 사용자의 신뢰도를 개선 하는 데 도움이 되는 다양 한 affordances가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-121">HoloLens 2 button prefab contains a lot of detailed affordances that help improve the user's confidence.</span></span> <span data-ttu-id="67e4d-122">여기에는 근접 기반 강조 표시, 앞면 케이지 압축 및 트리거의 펄스 효과가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67e4d-122">It includes proximity-based highlight, compressing front cage, and a pulse effect on trigger.</span></span>

* [<span data-ttu-id="67e4d-123">MRTK-단추</span><span class="sxs-lookup"><span data-stu-id="67e4d-123">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="67e4d-124">참조</span><span class="sxs-lookup"><span data-stu-id="67e4d-124">See also</span></span>

* [<span data-ttu-id="67e4d-125">커서</span><span class="sxs-lookup"><span data-stu-id="67e4d-125">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="67e4d-126">손 광선</span><span class="sxs-lookup"><span data-stu-id="67e4d-126">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="67e4d-127">Button</span><span class="sxs-lookup"><span data-stu-id="67e4d-127">Button</span></span>](button.md)
* [<span data-ttu-id="67e4d-128">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="67e4d-128">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="67e4d-129">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="67e4d-129">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="67e4d-130">조작</span><span class="sxs-lookup"><span data-stu-id="67e4d-130">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="67e4d-131">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="67e4d-131">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="67e4d-132">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="67e4d-132">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="67e4d-133">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="67e4d-133">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="67e4d-134">음성 명령</span><span class="sxs-lookup"><span data-stu-id="67e4d-134">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="67e4d-135">키보드</span><span class="sxs-lookup"><span data-stu-id="67e4d-135">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="67e4d-136">Tooltip</span><span class="sxs-lookup"><span data-stu-id="67e4d-136">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="67e4d-137">슬레이트</span><span class="sxs-lookup"><span data-stu-id="67e4d-137">Slate</span></span>](slate.md)
* [<span data-ttu-id="67e4d-138">슬라이더</span><span class="sxs-lookup"><span data-stu-id="67e4d-138">Slider</span></span>](slider.md)
* [<span data-ttu-id="67e4d-139">셰이더</span><span class="sxs-lookup"><span data-stu-id="67e4d-139">Shader</span></span>](shader.md)
* [<span data-ttu-id="67e4d-140">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="67e4d-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="67e4d-141">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="67e4d-141">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="67e4d-142">표면 자성</span><span class="sxs-lookup"><span data-stu-id="67e4d-142">Surface magnetism</span></span>](surface-magnetism.md)
