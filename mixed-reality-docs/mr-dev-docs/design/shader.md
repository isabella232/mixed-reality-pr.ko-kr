---
title: 셰이더
description: 혼합 현실 도구 키트 표준 셰이더가 혼합 현실 앱에서 holograms와 함께 사용할 수 있는 다양 한 유형의 시각적 효과를 제공 하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux, 셰이더, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 시각적 효과
ms.openlocfilehash: 4bf8205ac9dfbd22a0deb9ffe796fd4e33a96f89
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300388"
---
# <a name="shader"></a><span data-ttu-id="f3f42-104">셰이더</span><span class="sxs-lookup"><span data-stu-id="f3f42-104">Shader</span></span>

![셰이더](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="f3f42-106">Holographic 개체는 실제 환경에서 물리적 개체와 혼합 되므로 사용자에 게 시각적 신호를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f42-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="f3f42-107">Mixed Reality Toolkit 표준 셰이더는 holograms와 함께 사용할 다양 한 형식의 시각적 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f42-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="f3f42-108">음영 시스템은 단일의 유연한 셰이더를 사용 하 여 Unity의 표준 셰이더에 유사한 시각적 개체를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f42-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="f3f42-109">셰이더는 [흐름 설계 시스템 원칙](https://www.microsoft.com/design/fluent/#/) 을 구현 하 고 혼합 현실 장치에 대 한 성능을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f42-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="f3f42-110">MRTK (Mixed Reality Toolkit) 표준 셰이더를 사용 하는 시각적 효과의 예</span><span class="sxs-lookup"><span data-stu-id="f3f42-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="f3f42-111">![이동](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3f42-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="f3f42-112">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="f3f42-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f3f42-113">![회전](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3f42-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="f3f42-114">**테두리 라이트**</span><span class="sxs-lookup"><span data-stu-id="f3f42-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="f3f42-115">Unity 용 MRTK의 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="f3f42-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="f3f42-116">MRTK-표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="f3f42-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="f3f42-117">참조</span><span class="sxs-lookup"><span data-stu-id="f3f42-117">See also</span></span>

* [<span data-ttu-id="f3f42-118">커서</span><span class="sxs-lookup"><span data-stu-id="f3f42-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f3f42-119">손 광선</span><span class="sxs-lookup"><span data-stu-id="f3f42-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f3f42-120">Button</span><span class="sxs-lookup"><span data-stu-id="f3f42-120">Button</span></span>](button.md)
* [<span data-ttu-id="f3f42-121">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="f3f42-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f3f42-122">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="f3f42-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f3f42-123">조작</span><span class="sxs-lookup"><span data-stu-id="f3f42-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f3f42-124">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="f3f42-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f3f42-125">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="f3f42-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f3f42-126">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="f3f42-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f3f42-127">음성 명령</span><span class="sxs-lookup"><span data-stu-id="f3f42-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f3f42-128">키보드</span><span class="sxs-lookup"><span data-stu-id="f3f42-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f3f42-129">Tooltip</span><span class="sxs-lookup"><span data-stu-id="f3f42-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f3f42-130">슬레이트</span><span class="sxs-lookup"><span data-stu-id="f3f42-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="f3f42-131">슬라이더</span><span class="sxs-lookup"><span data-stu-id="f3f42-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="f3f42-132">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="f3f42-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f3f42-133">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="f3f42-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f3f42-134">표면 자성</span><span class="sxs-lookup"><span data-stu-id="f3f42-134">Surface magnetism</span></span>](surface-magnetism.md)
