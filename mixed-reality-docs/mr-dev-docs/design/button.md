---
title: 단추
description: 혼합 현실의 기본 구성 요소 중 하나인 단추를 사용하여 즉각적인 작업을 트리거하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, 컨트롤, 상호 작용, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 단추
ms.openlocfilehash: ddad8b23950bddd03dd4024497c212d1cc950fb0
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600372"
---
# <a name="button"></a><span data-ttu-id="6dc84-104">단추</span><span class="sxs-lookup"><span data-stu-id="6dc84-104">Button</span></span>

![단추](images/UX_Hero_Button.jpg)

<span data-ttu-id="6dc84-106">단추를 사용하면 혼합 현실 환경의 즉각적인 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dc84-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="6dc84-107">HoloLens 2 단추에는 사용자와의 상호 작용 신뢰도를 높이는 데 도움이 되는 시각 신호와 어조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dc84-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="6dc84-108">![근접 광원 효과가 표시된 단추](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6dc84-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="6dc84-109">**근접 광원**</span><span class="sxs-lookup"><span data-stu-id="6dc84-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6dc84-110">![포커스 강조 효과와 함께 선택된 단추](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6dc84-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="6dc84-111">**포커스 강조 표시**</span><span class="sxs-lookup"><span data-stu-id="6dc84-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="6dc84-112">![압축 압축 효과가 표시된 단추를 누르고 있습니다.](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="6dc84-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="6dc84-113">**압축 압축**</span><span class="sxs-lookup"><span data-stu-id="6dc84-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6dc84-114">![트리거 펄스 효과가 표시된 단추를 누르고 있습니다.](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="6dc84-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="6dc84-115">**트리거의 펄스**</span><span class="sxs-lookup"><span data-stu-id="6dc84-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="6dc84-116">Unity용 MRTK(Mixed Reality Toolkit)의 단추</span><span class="sxs-lookup"><span data-stu-id="6dc84-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6dc84-117">**[Unity용 MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** HoloLens 2 및 HoloLens(1세대)용 셸 스타일 단추를 포함하여 다양한 유형의 단추 프리팹을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6dc84-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="6dc84-118">HoloLens 2 단추 프리팹에는 사용자 신뢰도를 향상시키는 데 도움이 되는 몇 가지 자세한 어포던스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dc84-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="6dc84-119">근접 기반 강조 표시</span><span class="sxs-lookup"><span data-stu-id="6dc84-119">Proximity-based highlight</span></span>
* <span data-ttu-id="6dc84-120">전면 압축</span><span class="sxs-lookup"><span data-stu-id="6dc84-120">Compressing front cage</span></span>
* <span data-ttu-id="6dc84-121">트리거에 대한 펄스 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="6dc84-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="6dc84-122">자세한 지침 및 사용자 지정 예제는 [MRTK - 단추를](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6dc84-122">Check out the [MRTK - Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="6dc84-123">참조</span><span class="sxs-lookup"><span data-stu-id="6dc84-123">See also</span></span>

* [<span data-ttu-id="6dc84-124">커서</span><span class="sxs-lookup"><span data-stu-id="6dc84-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6dc84-125">손 광선</span><span class="sxs-lookup"><span data-stu-id="6dc84-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6dc84-126">Button</span><span class="sxs-lookup"><span data-stu-id="6dc84-126">Button</span></span>](button.md)
* [<span data-ttu-id="6dc84-127">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="6dc84-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6dc84-128">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="6dc84-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6dc84-129">조작</span><span class="sxs-lookup"><span data-stu-id="6dc84-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6dc84-130">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="6dc84-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6dc84-131">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="6dc84-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6dc84-132">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="6dc84-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6dc84-133">음성 명령</span><span class="sxs-lookup"><span data-stu-id="6dc84-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6dc84-134">키보드</span><span class="sxs-lookup"><span data-stu-id="6dc84-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6dc84-135">Tooltip</span><span class="sxs-lookup"><span data-stu-id="6dc84-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6dc84-136">슬레이트</span><span class="sxs-lookup"><span data-stu-id="6dc84-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="6dc84-137">슬라이더</span><span class="sxs-lookup"><span data-stu-id="6dc84-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="6dc84-138">셰이더</span><span class="sxs-lookup"><span data-stu-id="6dc84-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="6dc84-139">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="6dc84-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6dc84-140">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="6dc84-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6dc84-141">표면 자성</span><span class="sxs-lookup"><span data-stu-id="6dc84-141">Surface magnetism</span></span>](surface-magnetism.md)