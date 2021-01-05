---
title: 단추
description: 혼합 현실 기본 구성 요소 중 하나인 단추를 사용 하 여 즉각적인 작업을 트리거하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 단추
ms.openlocfilehash: b4e8388c4e3ea855c191cbdfc06621018274ff86
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847588"
---
# <a name="button"></a><span data-ttu-id="8e24e-104">단추</span><span class="sxs-lookup"><span data-stu-id="8e24e-104">Button</span></span>

![단추](images/UX_Hero_Button.jpg)

<span data-ttu-id="8e24e-106">사용자는 단추를 사용 하 여 혼합 현실 환경에서 즉각적인 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e24e-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="8e24e-107">HoloLens 2에서 단추에는 사용자와의 상호 작용 신뢰도를 높이는 데 도움이 되는 시각적 신호 및 affordances 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e24e-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8e24e-108">![근접 조명 효과가 표시 된 단추](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8e24e-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="8e24e-109">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="8e24e-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8e24e-110">![포커스 강조 표시 효과가 표시 된 단추 선택](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8e24e-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="8e24e-111">**포커스 강조 표시**</span><span class="sxs-lookup"><span data-stu-id="8e24e-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8e24e-112">![압축 케이지 효과를 표시 하 여 단추 누름](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="8e24e-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="8e24e-113">**케이지 압축**</span><span class="sxs-lookup"><span data-stu-id="8e24e-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8e24e-114">![트리거 펄스 효과가 표시 된 단추를 누르는 중임](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="8e24e-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="8e24e-115">**펄스 on 트리거**</span><span class="sxs-lookup"><span data-stu-id="8e24e-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="8e24e-116">Unity 용 MRTK (Mixed Reality Toolkit)의 단추</span><span class="sxs-lookup"><span data-stu-id="8e24e-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="8e24e-117">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 hololens 2 및 hololens (첫 번째 gen)의 셸 스타일 단추를 포함 하 여 다양 한 유형의 단추 prefabs 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e24e-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="8e24e-118">HoloLens 2 단추 prefab에는 사용자 신뢰도를 개선 하는 데 도움이 되는 몇 가지 상세 affordances 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e24e-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="8e24e-119">근접 기반 강조 표시</span><span class="sxs-lookup"><span data-stu-id="8e24e-119">Proximity-based highlight</span></span>
* <span data-ttu-id="8e24e-120">전면 케이지 압축</span><span class="sxs-lookup"><span data-stu-id="8e24e-120">Compressing front cage</span></span>
* <span data-ttu-id="8e24e-121">트리거의 펄스 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="8e24e-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="8e24e-122">자세한 지침 및 사용자 지정 예제를 보려면 [Mrtk 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e24e-122">Check out the [MRTK - Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="8e24e-123">추가 정보</span><span class="sxs-lookup"><span data-stu-id="8e24e-123">See also</span></span>

* [<span data-ttu-id="8e24e-124">커서</span><span class="sxs-lookup"><span data-stu-id="8e24e-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8e24e-125">손 광선</span><span class="sxs-lookup"><span data-stu-id="8e24e-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8e24e-126">Button</span><span class="sxs-lookup"><span data-stu-id="8e24e-126">Button</span></span>](button.md)
* [<span data-ttu-id="8e24e-127">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="8e24e-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8e24e-128">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="8e24e-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8e24e-129">조작</span><span class="sxs-lookup"><span data-stu-id="8e24e-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8e24e-130">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="8e24e-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8e24e-131">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="8e24e-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8e24e-132">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="8e24e-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8e24e-133">음성 명령</span><span class="sxs-lookup"><span data-stu-id="8e24e-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8e24e-134">키보드</span><span class="sxs-lookup"><span data-stu-id="8e24e-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8e24e-135">Tooltip</span><span class="sxs-lookup"><span data-stu-id="8e24e-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8e24e-136">슬레이트</span><span class="sxs-lookup"><span data-stu-id="8e24e-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="8e24e-137">슬라이더</span><span class="sxs-lookup"><span data-stu-id="8e24e-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="8e24e-138">셰이더</span><span class="sxs-lookup"><span data-stu-id="8e24e-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="8e24e-139">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="8e24e-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8e24e-140">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="8e24e-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8e24e-141">표면 자성</span><span class="sxs-lookup"><span data-stu-id="8e24e-141">Surface magnetism</span></span>](surface-magnetism.md)
