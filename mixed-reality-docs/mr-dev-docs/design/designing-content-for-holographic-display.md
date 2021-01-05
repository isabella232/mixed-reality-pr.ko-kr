---
title: Holographic 디스플레이용 콘텐츠 디자인
description: Holographic 표시에 대 한 디자인 지침 및 모범 사례를 알아봅니다.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 디자인, holographic 표시, 콘텐츠 디자인, 어두운 테마, 밝은 테마, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 디자인, 픽셀
ms.openlocfilehash: 4a95f5df50a600035d9127c73f86a5d8be5e7131
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847992"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="019a6-104">Holographic 디스플레이용 콘텐츠 디자인</span><span class="sxs-lookup"><span data-stu-id="019a6-104">Designing content for holographic display</span></span>

![Ulnar 사이드 위치](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="019a6-106">Holographic에 대 한 콘텐츠를 디자인할 때 최상의 환경을 달성 하기 위해 고려해 야 하는 몇 가지 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="019a6-107">아래 권장 사항 중 일부를 나열 하 고 [색, 조명 및 자료](color-light-and-materials.md) 페이지에서 holographic 디스플레이의 특징에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="019a6-108">넓은 표면에서 밝은 색을 사용 하는 문제</span><span class="sxs-lookup"><span data-stu-id="019a6-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="019a6-109">HoloLens 경험 연구 및 테스트에 따라 디스플레이의 많은 영역에서 밝은 색을 사용 하면 여러 가지 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="019a6-110">**아이 피로**</span><span class="sxs-lookup"><span data-stu-id="019a6-110">**Eye fatigue**</span></span> 

<span data-ttu-id="019a6-111">Holographic display는 가감 되므로 밝은 색의 holograms는 더 밝은 색을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="019a6-112">밝은 영역에서 단색을 사용 하면 사용자에 게 눈에 피로 쉽게 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="019a6-113">**손 폐색**</span><span class="sxs-lookup"><span data-stu-id="019a6-113">**Hand occlusion**</span></span> 

<span data-ttu-id="019a6-114">밝은 색을 사용 하면 개체와 직접 상호 작용할 때 사용자가 손을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="019a6-115">사용자가 손을 볼 수 없기 때문에 손 모양/손가락 간의 깊이/거리를 대상 화면으로 인식 하기가 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="019a6-116">손가락 커서는이 문제를 보정 하는 데 도움이 되지만 밝은 흰색 표면에서는 여전히 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="019a6-117">![색 및 손 폐색는 ](images/color_handocclusion.jpg)
 *밝은 색이 지정 된 콘텐츠 backplate에서 손 모양 보기*</span><span class="sxs-lookup"><span data-stu-id="019a6-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="019a6-118">**색 균일성**</span><span class="sxs-lookup"><span data-stu-id="019a6-118">**Color uniformity**</span></span>

<span data-ttu-id="019a6-119">Holographic 디스플레이의 특징으로 인해 디스플레이의 밝은 영역이 blotchy 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="019a6-120">짙은 색 구성표를 사용 하면이 문제를 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="019a6-121">색 선택에 대 한 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="019a6-121">Design guidelines for color choices</span></span>

<span data-ttu-id="019a6-122">**UI 배경에 짙은 색 사용**</span><span class="sxs-lookup"><span data-stu-id="019a6-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="019a6-123">진한 색 구성표를 사용 하 여 눈 피로 최소화 하 고 직접 상호 작용에 대 한 신뢰도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="019a6-124">![콘텐츠 배경에 ](images/color_dark_examples.jpg)
 *사용 되는 짙은 색의* 콘텐츠 배경 예제에 사용 되는 짙은 색의 예</span><span class="sxs-lookup"><span data-stu-id="019a6-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="019a6-125">**Semibold 또는 굵은 글꼴 두께 사용**</span><span class="sxs-lookup"><span data-stu-id="019a6-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="019a6-126">HoloLens를 사용 하면 경험을 통해 멋진 고해상도 텍스트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="019a6-127">그러나 세로 스트로크가 작은 글꼴 크기로 지터 될 수 있으므로 밝은 글꼴 가중치 (예: 밝은 글꼴 또는 반투명)를 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="019a6-128">![굵게 또는 반 굵은 글꼴 두께 (위쪽 패널)는 ](images/color_font_examples.jpg)
 *굵은 글꼴 또는 반투명 글꼴 두께 (위쪽 패널)를 개선 하 여 가독성을 향상 시킵니다* .</span><span class="sxs-lookup"><span data-stu-id="019a6-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="019a6-129">**MRTK의 HolographicBackplate 재질 사용**</span><span class="sxs-lookup"><span data-stu-id="019a6-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="019a6-130">HolographicBackplate 재질은 HoloLens 셸에서 여러 UI 패널에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="019a6-131">이러한 기능 중 하나는 패널을 기준으로 위치를 이동할 때 사용자에 게 표시 되는 iridescence 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="019a6-132">배경 플레이트 색은 미리 정의 된 스펙트럼에서 조금씩 이동 하 여 콘텐츠 가독성을 방해 하지 않고 뛰어난 동적 시각적 효과를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="019a6-133">이러한 미세한 이동 색은 보조 색 탐지할을 보정 하는 데도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="019a6-134">투명 또는 반투명 UI 백 판금 관련 챌린지</span><span class="sxs-lookup"><span data-stu-id="019a6-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="019a6-135">![투명 한 UI 예제 ](images/color_transparent_examples.jpg)
 *투명 한 ui 백 판의 예*</span><span class="sxs-lookup"><span data-stu-id="019a6-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="019a6-136">**시각적 복잡성 및 접근성**</span><span class="sxs-lookup"><span data-stu-id="019a6-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="019a6-137">Holographic 개체는 물리적 환경에 혼합 되므로 투명 하거나 투명 한 창의 콘텐츠나 UI 가독성이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="019a6-138">또한 투명 한 개체 들이 서로 위에 중첩 된 경우에는 사용자가 혼동을 holographic 때문에 상호 작용 하기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="019a6-139">**성능**</span><span class="sxs-lookup"><span data-stu-id="019a6-139">**Performance**</span></span>

<span data-ttu-id="019a6-140">투명 하거나 투명 한 개체가 올바르게 렌더링 되려면 백그라운드에 있는 개체와 정렬 하 고 혼합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="019a6-141">투명 개체의 정렬에는 CPU 비용이 적당 하 고, 혼합을 사용 하면 GPU에서 고르기 (즉,</span><span class="sxs-lookup"><span data-stu-id="019a6-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="019a6-142">수준 테스트).</span><span class="sxs-lookup"><span data-stu-id="019a6-142">depth testing).</span></span> <span data-ttu-id="019a6-143">숨겨진 표면 제거를 허용 하지 않으면 렌더링 된 최종 픽셀에 필요한 작업 수가 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="019a6-144">그러면 더 많은 압력 채우기 빈도 제약 조건이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="019a6-145">**깊이 LSR 기술에서 홀로그램 안정성 문제**</span><span class="sxs-lookup"><span data-stu-id="019a6-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="019a6-146">Holographic reprojection 또는 홀로그램 안정성을 향상 시키기 위해 응용 프로그램은 렌더링 된 모든 프레임에 대 한 깊이 버퍼를 시스템에 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="019a6-147">Reprojection에 깊이 버퍼를 사용 하는 경우 모든 색으로 렌더링 된 픽셀에 해당 하는 깊이 버퍼를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="019a6-148">깊이 값이 있는 모든 픽셀에도 색 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="019a6-149">위의 지침을 따르지 않는 경우에는 유효한 깊이 정보가 없는 렌더링 된 이미지 영역이 아티팩트를 생성 하는 방식으로 다시 프로젝션 될 수 있으며,이는 물결 모양의 왜곡으로 표시 되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="019a6-150">투명 한 요소에 대 한 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="019a6-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="019a6-151">**불투명 UI 배경 사용**</span><span class="sxs-lookup"><span data-stu-id="019a6-151">**Use opaque UI background**</span></span>

<span data-ttu-id="019a6-152">투명 하거나 투명 한 개체는 기본적으로 적절 한 혼합을 위해 깊이를 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="019a6-153">이러한 문제를 완화 하는 방법으로는 불투명 한 개체를 사용 하 여 투명 한 개체를 불투명 한 개체 (예: 불투명 한 판 앞의 반투명 단추)에 가깝게 표시 하거나 투명 한 개체를 사용 하 여 깊이 (모든 시나리오에서 적용 되지 않음)를 적용 하거나, 프레임의 끝에 깊이 값을 적용 하는 프록시 개체를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="019a6-154">MRTK-Unity의 솔루션: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="019a6-154">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="019a6-155">단색 및 불투명 백 판을 사용 하 여 가독성 및 상호 작용 신뢰도를 안전 하 게 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="019a6-156">**영향을 받는 픽셀 수 최소화**</span><span class="sxs-lookup"><span data-stu-id="019a6-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="019a6-157">프로젝트에서 투명 개체를 사용 해야 하는 경우 영향을 받는 픽셀 수를 최소화 하십시오.</span><span class="sxs-lookup"><span data-stu-id="019a6-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="019a6-158">예를 들어, 개체가 특정 조건 에서만 표시 되는 경우 (예: 가산적 네온 효과) 개체가 완전히 표시 되지 않는 경우 (추가 색을 검정으로 설정 하는 대신) 개체를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="019a6-159">알파 마스크를 사용 하 여 쿼드를 사용 하 여 만든 간단한 2D 모양의 경우 불투명 셰이더를 사용 하 여 모양의 망상 표시를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="019a6-160">Unity 용 MRTK (Mixed Reality Toolkit)의 어두운 UI 예제</span><span class="sxs-lookup"><span data-stu-id="019a6-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="019a6-161">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 짙은 색 체계를 기반으로 다양 한 UI 빌딩 블록 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="019a6-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="019a6-162">메뉴 근처</span><span class="sxs-lookup"><span data-stu-id="019a6-162">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="019a6-163">대화 상자</span><span class="sxs-lookup"><span data-stu-id="019a6-163">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="019a6-164">손 모양 메뉴</span><span class="sxs-lookup"><span data-stu-id="019a6-164">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="019a6-165">추가 정보</span><span class="sxs-lookup"><span data-stu-id="019a6-165">See also</span></span>

* [<span data-ttu-id="019a6-166">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="019a6-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="019a6-167">커서</span><span class="sxs-lookup"><span data-stu-id="019a6-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="019a6-168">손 광선</span><span class="sxs-lookup"><span data-stu-id="019a6-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="019a6-169">Button</span><span class="sxs-lookup"><span data-stu-id="019a6-169">Button</span></span>](button.md)
* [<span data-ttu-id="019a6-170">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="019a6-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="019a6-171">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="019a6-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="019a6-172">조작</span><span class="sxs-lookup"><span data-stu-id="019a6-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="019a6-173">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="019a6-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="019a6-174">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="019a6-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="019a6-175">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="019a6-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="019a6-176">음성 명령</span><span class="sxs-lookup"><span data-stu-id="019a6-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="019a6-177">키보드</span><span class="sxs-lookup"><span data-stu-id="019a6-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="019a6-178">Tooltip</span><span class="sxs-lookup"><span data-stu-id="019a6-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="019a6-179">슬레이트</span><span class="sxs-lookup"><span data-stu-id="019a6-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="019a6-180">슬라이더</span><span class="sxs-lookup"><span data-stu-id="019a6-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="019a6-181">셰이더</span><span class="sxs-lookup"><span data-stu-id="019a6-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="019a6-182">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="019a6-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="019a6-183">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="019a6-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="019a6-184">표면 자성</span><span class="sxs-lookup"><span data-stu-id="019a6-184">Surface magnetism</span></span>](surface-magnetism.md)
