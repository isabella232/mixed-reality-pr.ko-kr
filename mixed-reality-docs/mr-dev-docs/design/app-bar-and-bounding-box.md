---
title: 경계 상자 및 앱 바
description: 앱 바는 홀로그램 경계의 아래쪽 가장자리에 표시되는 일련의 단추를 포함하는 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 앱 바, 경계 상자, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110094"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="cfd15-104">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="cfd15-104">Bounding box and App bar</span></span>
<span data-ttu-id="cfd15-105">![경계는 Mixed Reality 개체 조작을 위한 표준 인터페이스입니다.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="cfd15-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="cfd15-106">경계 상자란?</span><span class="sxs-lookup"><span data-stu-id="cfd15-106">What is the Bounding box?</span></span>

<span data-ttu-id="cfd15-107">경계는 Mixed Reality 개체 조작을 위한 표준 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="cfd15-108">이 기능은 사용자에게 개체가 현재 조정 가능한 시각적 신호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="cfd15-109">HoloLens 2 경계 상자는 직접 손 조작과 함께 작동하며 사용자의 손가락 근접에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="cfd15-110">사용자가 개체와의 거리를 인식하는 데 도움이 되는 시각적 피드백을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="cfd15-111">개체 크기 조정</span><span class="sxs-lookup"><span data-stu-id="cfd15-111">Scaling an object</span></span><br>
        <span data-ttu-id="cfd15-112">경계 상자의 모서리는 개체의 크기를 조정하는 데 사용할 수 있음을 사용자에게 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="cfd15-113">핸들은 배율 조정을 위해 널리 이해된 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="cfd15-114">이 시각 신호는 조정 모드 외부에서 표시되지 않더라도 개체의 전체 영역을 사용자에게 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="cfd15-115">이 기능이 없으면 다른 개체 또는 표면에 스냅된 개체가 주위에 공백이 있어서는 안 되는 것처럼 동작하는 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="cfd15-116">*비디오 루프: 경계 상자를 통해 개체 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="cfd15-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cfd15-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cfd15-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="cfd15-118">![경계 상자를 통해 개체 크기를 조정하는 HoloLens의 관점](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="cfd15-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="cfd15-119">개체 회전</span><span class="sxs-lookup"><span data-stu-id="cfd15-119">Rotating an object</span></span><br>
        <span data-ttu-id="cfd15-120">경계 상자의 가장자리에 있는 세로 사각형 어조도 회전 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="cfd15-121">이렇게 하면 사용자가 배치된 홀로그램을 더 세부적으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="cfd15-122">조정하고 크기를 조정할 수 있을 뿐만 아니라 이제도 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="cfd15-123">*비디오 루프: 경계 상자를 통해 개체 회전*</span><span class="sxs-lookup"><span data-stu-id="cfd15-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cfd15-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cfd15-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="cfd15-125">![경계 상자를 통해 개체를 회전하는 HoloLens 지점 보기](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="cfd15-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="cfd15-126">HoloLens 2 손 근접도에 대한 시각적 피드백</span><span class="sxs-lookup"><span data-stu-id="cfd15-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="cfd15-127">HoloLens 2 사용자의 깊이 인식에 도움이 될 수 있는 추가 시각 신호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="cfd15-128">손끝이 개체에 가까워지면 손끝 근처의 링이 나타나고 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="cfd15-129">링은 누른 상태에 도달하면 결국 점으로 수렴됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="cfd15-130">이 시각적 어패던스는 사용자가 개체에서 얼마나 멀리 떨어져 있는지 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="cfd15-131">*비디오 루프: 경계 상자에 대한 근접성을 기반으로 하는 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="cfd15-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cfd15-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cfd15-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="cfd15-133">![손 근접도에 대한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="cfd15-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="cfd15-134">**Unity 앱 개발의 경우 [Mixed Reality Toolkit-Unity의 경계 상자를 참조하세요.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span><span class="sxs-lookup"><span data-stu-id="cfd15-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="cfd15-135">앱 표시줄이란?</span><span class="sxs-lookup"><span data-stu-id="cfd15-135">What is the App bar?</span></span>

<span data-ttu-id="cfd15-136">앱 바는 홀로그램 경계의 아래쪽 가장자리에 표시되는 일련의 단추를 포함하는 개체 수준 메뉴입니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="cfd15-137">이 패턴은 일반적으로 사용자가 홀로그램을 제거하고 조정할 수 있도록 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="cfd15-138">앱 바는 주로 사용자 환경에서 배치된 개체를 관리하는 방법으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="cfd15-139">경계 상자와 결합된 사용자는 혼합 현실에서 개체가 지향되는 위치와 방법을 완전히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="cfd15-140">앱 표시줄이 사용자를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="cfd15-141">이 패턴은 세계에서 잠긴 개체와 함께 사용되므로 사용자가 개체를 이동할 때 앱 표시줄은 항상 사용자와 가장 가까운 개체 쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="cfd15-142">기술적으로는 그렇지 않지만 이 기능은 효과적으로 동일한 결과를 달성합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="cfd15-143">사용자 환경의 다른 위치에서 사용할 수 있는 기능을 차단하거나 차단할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="cfd15-144">*비디오 루프: 홀로그램을 둘러보면 앱 바가 다음과 같이 진행됩니다.*</span><span class="sxs-lookup"><span data-stu-id="cfd15-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cfd15-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cfd15-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="cfd15-146">![홀로그램을 둘러 들이고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-146">![Walking around a hologram.</span></span> <span data-ttu-id="cfd15-147">앱 표시줄은 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="cfd15-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="cfd15-148">Unity용 MRTK(Mixed Reality Toolkit)의 경계 상자</span><span class="sxs-lookup"><span data-stu-id="cfd15-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="cfd15-149">**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 경계 상자 및 앱 표시줄에 대한 스크립트와 프리팹을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="cfd15-150">BoundingBox.cs 스크립트를 개체에 할당하여 경계 상자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd15-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="cfd15-151">MRTK - 경계 상자</span><span class="sxs-lookup"><span data-stu-id="cfd15-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="cfd15-152">참조</span><span class="sxs-lookup"><span data-stu-id="cfd15-152">See also</span></span>

* [<span data-ttu-id="cfd15-153">커서</span><span class="sxs-lookup"><span data-stu-id="cfd15-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="cfd15-154">손 광선</span><span class="sxs-lookup"><span data-stu-id="cfd15-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="cfd15-155">Button</span><span class="sxs-lookup"><span data-stu-id="cfd15-155">Button</span></span>](button.md)
* [<span data-ttu-id="cfd15-156">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="cfd15-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="cfd15-157">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="cfd15-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="cfd15-158">조작</span><span class="sxs-lookup"><span data-stu-id="cfd15-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cfd15-159">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="cfd15-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="cfd15-160">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="cfd15-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="cfd15-161">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="cfd15-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="cfd15-162">음성 명령</span><span class="sxs-lookup"><span data-stu-id="cfd15-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="cfd15-163">키보드</span><span class="sxs-lookup"><span data-stu-id="cfd15-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="cfd15-164">Tooltip</span><span class="sxs-lookup"><span data-stu-id="cfd15-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="cfd15-165">슬레이트</span><span class="sxs-lookup"><span data-stu-id="cfd15-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="cfd15-166">슬라이더</span><span class="sxs-lookup"><span data-stu-id="cfd15-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="cfd15-167">셰이더</span><span class="sxs-lookup"><span data-stu-id="cfd15-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="cfd15-168">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="cfd15-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="cfd15-169">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="cfd15-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="cfd15-170">표면 자성</span><span class="sxs-lookup"><span data-stu-id="cfd15-170">Surface magnetism</span></span>](surface-magnetism.md)