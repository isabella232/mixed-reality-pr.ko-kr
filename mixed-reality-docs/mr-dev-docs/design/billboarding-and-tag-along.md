---
title: 빌보딩 및 태그얼롱
description: 혼합 현실 애플리케이션에서 사용자를 상대하도록 항상 지향하는 개체를 사용하는 방법을 알아봅니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 스트래핑, 태그 따라, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600342"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="0d79a-104">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="0d79a-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="0d79a-105">가장이란?</span><span class="sxs-lookup"><span data-stu-id="0d79a-105">What is billboarding?</span></span>

<span data-ttu-id="0d79a-106">복습은 혼합 현실의 개체에 적용할 수 있는 동작 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="0d79a-107">싱이 있는 개체는 항상 사용자를 향하도록 방향을 정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="0d79a-108">텍스트 및 메뉴 시스템은 일반적인 사용 사례로, 사용자의 환경에 배치된 정적 개체(세계 잠금)는 사용자가 이동할 때 가려지거나 읽을 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="0d79a-109">래핑이 활성화된 개체는 사용자 환경에서 자유롭게 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="0d79a-110">디자인 고려 사항에 따라 단일 축으로 제한될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="0d79a-111">다른 개체에 너무 가까이 배치하거나 HoloLens에서 스캔된 표면을 너무 가깝게 배치하면 비추는 개체가 자신을 잘라내거나 폐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="0d79a-112">이를 방지하려면 축에서 회전할 때 개체가 생성할 수 있는 총 공간을 생각해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="0d79a-113">태그가란?</span><span class="sxs-lookup"><span data-stu-id="0d79a-113">What is a tag-along?</span></span>

<span data-ttu-id="0d79a-114">태그는 홀로그램에 추가할 수 있는 동작 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="0d79a-115">태그 따라 개체는 사용자가 편안하게 상호 작용할 수 있는 범위에 유지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="0d79a-116">![HoloLens 핀 패널은 태그가 함께 작동하는 방식의 좋은 예입니다.](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d79a-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="0d79a-117">*HoloLens 시작 메뉴 태그 따라 동작의 좋은 예입니다.*</span><span class="sxs-lookup"><span data-stu-id="0d79a-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="0d79a-118">태그 따라 개체에는 동작 방식을 미세 조정할 수 있는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="0d79a-119">사용자가 환경을 이동하는 동안 콘텐츠는 사용자의 시야 안이나 외부에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="0d79a-120">이동하면 콘텐츠가 보기의 가장자리 쪽으로 밀어 사용자의 주변을 유지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="0d79a-121">사용자가 이동하는 빈도에 따라 콘텐츠가 일시적으로 보기에서 벗어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="0d79a-122">사용자가 태그 따라 개체를 응시할 때 더 완벽하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="0d79a-123">콘텐츠는 항상 "한눈에 보기"라고 생각하므로 사용자는 콘텐츠의 방향을 절대 잊어버리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="0d79a-124">추가 매개 변수는 태그와 함께 개체가 밴드에 의해 사용자의 헤드에 연결된 느낌을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="0d79a-125">가속 또는 감속을 강화하면 개체에 가중치가 부여되어 물리적으로 더 많은 느낌을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="0d79a-126">이 봄 동작은 태그가 작동하는 방식에 대한 정확한 멘탈 모델을 작성하는 데 도움이 되는 어패던스입니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="0d79a-127">오디오는 사용자가 태그 따라 모드에서 개체가 있는 경우에 대한 다른 신호를 제공하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="0d79a-128">오디오는 이동 속도를 강화해야 합니다. 빠른 헤드 턴이 더 눈에 띄는 음향 효과를 제공해야 하는 반면, 자연스러운 속도로 복습하는 경우 오디오 효과를 최소화하거나 전혀 영향을 미치지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="0d79a-129">실제로 헤드 잠금된 콘텐츠와 마찬가지로 태그를 따라 이동한 개체는 사용자의 보기에서 너무 많이 이동하거나 너무 많이 움직이면 너무 많이 또는 움갈리게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="0d79a-130">사용자가 주변을 둘러본 후 빠르게 중지하면 해당 감지는 중지되었다고 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="0d79a-131">이들의 균형은 머리의 회전이 중지되고 비전이 전 세계의 회전을 중지한다는 것을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="0d79a-132">그러나 사용자가 중지되었을 때 태그가 계속 이동하면 인식이 혼동될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0d79a-133">Unity용 MRTK(Mixed Reality Toolkit)의 스트리밍 및 태그</span><span class="sxs-lookup"><span data-stu-id="0d79a-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="0d79a-134">**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 스트링 및 태그 따라 동작에 대한 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="0d79a-135">Object.cs 스크립트를 개체에 할당하여 동작을 추가하고 개체가 항상 사용자를 향하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="0d79a-136">태그 따라 동작을 추가하려면 RadialView.cs 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="0d79a-137">lerping time, distance 및 degree와 같은 다양한 옵션을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d79a-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="0d79a-138">MRTK - 방사형 뷰 해결기</span><span class="sxs-lookup"><span data-stu-id="0d79a-138">MRTK - Radial View Solver</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="0d79a-139">MRTK - 스크립트</span><span class="sxs-lookup"><span data-stu-id="0d79a-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="0d79a-140">참조</span><span class="sxs-lookup"><span data-stu-id="0d79a-140">See also</span></span>

* [<span data-ttu-id="0d79a-141">커서</span><span class="sxs-lookup"><span data-stu-id="0d79a-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0d79a-142">손 광선</span><span class="sxs-lookup"><span data-stu-id="0d79a-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="0d79a-143">Button</span><span class="sxs-lookup"><span data-stu-id="0d79a-143">Button</span></span>](button.md)
* [<span data-ttu-id="0d79a-144">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="0d79a-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0d79a-145">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="0d79a-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="0d79a-146">조작</span><span class="sxs-lookup"><span data-stu-id="0d79a-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0d79a-147">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="0d79a-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="0d79a-148">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="0d79a-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="0d79a-149">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="0d79a-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="0d79a-150">음성 명령</span><span class="sxs-lookup"><span data-stu-id="0d79a-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="0d79a-151">키보드</span><span class="sxs-lookup"><span data-stu-id="0d79a-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="0d79a-152">Tooltip</span><span class="sxs-lookup"><span data-stu-id="0d79a-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="0d79a-153">슬레이트</span><span class="sxs-lookup"><span data-stu-id="0d79a-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="0d79a-154">슬라이더</span><span class="sxs-lookup"><span data-stu-id="0d79a-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="0d79a-155">셰이더</span><span class="sxs-lookup"><span data-stu-id="0d79a-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="0d79a-156">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="0d79a-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="0d79a-157">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="0d79a-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="0d79a-158">표면 자성</span><span class="sxs-lookup"><span data-stu-id="0d79a-158">Surface magnetism</span></span>](surface-magnetism.md)