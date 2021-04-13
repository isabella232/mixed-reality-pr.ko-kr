---
title: 단추
description: 혼합 현실 기본 구성 요소 중 하나인 단추를 사용 하 여 즉각적인 작업을 트리거하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 단추
ms.openlocfilehash: 177ccfc1c07df9a9523c9ed6733d3da61bdb7921
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299758"
---
# <a name="button"></a><span data-ttu-id="497fc-104">단추</span><span class="sxs-lookup"><span data-stu-id="497fc-104">Button</span></span>

![단추](images/UX_Hero_Button.jpg)

<span data-ttu-id="497fc-106">사용자는 단추를 사용 하 여 혼합 현실 환경에서 즉각적인 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497fc-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="497fc-107">HoloLens 2에서 단추에는 사용자와의 상호 작용 신뢰도를 높이는 데 도움이 되는 시각적 신호 및 affordances 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497fc-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="497fc-108">![근접 조명 효과가 표시 된 단추](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="497fc-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="497fc-109">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="497fc-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="497fc-110">![포커스 강조 표시 효과가 표시 된 단추 선택](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="497fc-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="497fc-111">**포커스 강조 표시**</span><span class="sxs-lookup"><span data-stu-id="497fc-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="497fc-112">![압축 케이지 효과를 표시 하 여 단추 누름](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="497fc-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="497fc-113">**케이지 압축**</span><span class="sxs-lookup"><span data-stu-id="497fc-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="497fc-114">![트리거 펄스 효과가 표시 된 단추를 누르는 중임](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="497fc-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="497fc-115">**펄스 on 트리거**</span><span class="sxs-lookup"><span data-stu-id="497fc-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="497fc-116">Unity 용 MRTK (Mixed Reality Toolkit)의 단추</span><span class="sxs-lookup"><span data-stu-id="497fc-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="497fc-117">**[Unity 용 Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 hololens 2 및 hololens (첫 번째 gen)의 셸 스타일 단추를 비롯 한 다양 한 유형의 단추 prefabs을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="497fc-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="497fc-118">HoloLens 2 단추 prefab에는 사용자 신뢰도를 개선 하는 데 도움이 되는 몇 가지 상세 affordances 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497fc-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="497fc-119">근접 기반 강조 표시</span><span class="sxs-lookup"><span data-stu-id="497fc-119">Proximity-based highlight</span></span>
* <span data-ttu-id="497fc-120">전면 케이지 압축</span><span class="sxs-lookup"><span data-stu-id="497fc-120">Compressing front cage</span></span>
* <span data-ttu-id="497fc-121">트리거의 펄스 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="497fc-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="497fc-122">자세한 지침 및 사용자 지정 예제를 보려면 [Mrtk 단추](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="497fc-122">Check out the [MRTK - Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="497fc-123">참조</span><span class="sxs-lookup"><span data-stu-id="497fc-123">See also</span></span>

* [<span data-ttu-id="497fc-124">커서</span><span class="sxs-lookup"><span data-stu-id="497fc-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="497fc-125">손 광선</span><span class="sxs-lookup"><span data-stu-id="497fc-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="497fc-126">Button</span><span class="sxs-lookup"><span data-stu-id="497fc-126">Button</span></span>](button.md)
* [<span data-ttu-id="497fc-127">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="497fc-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="497fc-128">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="497fc-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="497fc-129">조작</span><span class="sxs-lookup"><span data-stu-id="497fc-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="497fc-130">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="497fc-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="497fc-131">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="497fc-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="497fc-132">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="497fc-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="497fc-133">음성 명령</span><span class="sxs-lookup"><span data-stu-id="497fc-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="497fc-134">키보드</span><span class="sxs-lookup"><span data-stu-id="497fc-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="497fc-135">Tooltip</span><span class="sxs-lookup"><span data-stu-id="497fc-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="497fc-136">슬레이트</span><span class="sxs-lookup"><span data-stu-id="497fc-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="497fc-137">슬라이더</span><span class="sxs-lookup"><span data-stu-id="497fc-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="497fc-138">셰이더</span><span class="sxs-lookup"><span data-stu-id="497fc-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="497fc-139">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="497fc-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="497fc-140">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="497fc-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="497fc-141">표면 자성</span><span class="sxs-lookup"><span data-stu-id="497fc-141">Surface magnetism</span></span>](surface-magnetism.md)
