---
title: Holographic 디스플레이용 콘텐츠 디자인
description: HoloLens 디바이스의 홀로그램 디스플레이에 대한 디자인 지침 및 모범 사례에 대해 알아봅니다.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 디자인, 홀로그램 디스플레이, 콘텐츠 디자인, 어두운 테마, 밝은 테마, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 디자인, 픽셀
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600322"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="c4427-104">Holographic 디스플레이용 콘텐츠 디자인</span><span class="sxs-lookup"><span data-stu-id="c4427-104">Designing content for holographic display</span></span>

![Ulnar 측면 손 위치](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="c4427-106">홀로그램 디스플레이에 대한 콘텐츠를 디자인할 때 최상의 환경을 달성하기 위해 고려해야 하는 몇 가지 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="c4427-107">아래에 몇 가지 권장 사항이 나와 있으며 [색, 광원 및 재질](color-light-and-materials.md) 페이지에서 홀로그램 디스플레이의 특징에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="c4427-108">큰 표면에서 밝은 색의 문제</span><span class="sxs-lookup"><span data-stu-id="c4427-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="c4427-109">HoloLens 경험 연구 및 테스트에 따라 디스플레이의 큰 영역에서 밝은 색을 사용하면 다음과 같은 몇 가지 문제가 발생할 수 있음을 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="c4427-110">**눈의 안과**</span><span class="sxs-lookup"><span data-stu-id="c4427-110">**Eye fatigue**</span></span> 

<span data-ttu-id="c4427-111">홀로그램 표시는 가감기이므로 밝은 색의 홀로그램은 더 많은 광원을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="c4427-112">디스플레이의 큰 영역에 있는 밝고 단색으로 인해 사용자의 시선이 쉽게 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="c4427-113">**손 폐색**</span><span class="sxs-lookup"><span data-stu-id="c4427-113">**Hand occlusion**</span></span> 

<span data-ttu-id="c4427-114">밝은 색은 개체와 직접 상호 작용할 때 사용자가 손을 보기 어렵게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="c4427-115">사용자는 손을 볼 수 없으므로 손/손가락과 대상 표면 사이의 깊이/거리를 인식하기가 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="c4427-116">손가락 커서는 이 문제를 보정하는 데 도움이 되지만 밝은 흰색 표면에서는 여전히 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="c4427-117">![색 및 손 폐색 ](images/color_handocclusion.jpg)
 *밝은 색 콘텐츠 백플레이트에서 손을 보기 어렵습니다.*</span><span class="sxs-lookup"><span data-stu-id="c4427-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="c4427-118">**색 균일성**</span><span class="sxs-lookup"><span data-stu-id="c4427-118">**Color uniformity**</span></span>

<span data-ttu-id="c4427-119">홀로그램 디스플레이의 특성으로 인해 디스플레이의 큰 밝은 영역은 blotlot이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="c4427-120">어두운 색 구성표를 사용하면 이 문제를 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="c4427-121">색 선택에 대한 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="c4427-121">Design guidelines for color choices</span></span>

<span data-ttu-id="c4427-122">**UI 배경에 어두운 색 사용**</span><span class="sxs-lookup"><span data-stu-id="c4427-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="c4427-123">어두운 색 구성표를 사용하면 눈의 집중을 최소화하고 직접 손 조작에 대한 신뢰도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="c4427-124">![콘텐츠 배경에 사용되는 어두운 색의 예 콘텐츠 ](images/color_dark_examples.jpg)
 *배경에 사용되는 어두운 색의 예*</span><span class="sxs-lookup"><span data-stu-id="c4427-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="c4427-125">**세미볼트 또는 굵은 글꼴 두께 사용**</span><span class="sxs-lookup"><span data-stu-id="c4427-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="c4427-126">HoloLens를 사용하면 환경이 멋진 고해상도 텍스트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="c4427-127">그러나 세로 스트로크가 작은 글꼴 크기로 지터링할 수 있으므로 밝게 또는 반광과 같은 씬 글꼴 두께를 방지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="c4427-128">![굵게 또는 반굵은 글꼴 두께(위쪽 패널)는 가독성을 ](images/color_font_examples.jpg)
 *향상시키거나 굵게 또는 반굵게 글꼴 두께(위쪽 패널)를 개선하여 가독성을 향상시킵니다.*</span><span class="sxs-lookup"><span data-stu-id="c4427-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="c4427-129">**MRTK의 HolographicBackplate 재질 사용**</span><span class="sxs-lookup"><span data-stu-id="c4427-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="c4427-130">HolographicBackplate 재질은 HoloLens 셸의 여러 UI 패널에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="c4427-131">해당 기능 중 하나는 패널에 따라 위치를 이동할 때 사용자에게 표시되는 재정의 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="c4427-132">백플래트 색은 미리 정의된 스펙트럼에서 약간 이동하며, 콘텐츠 가독성을 방해하지 않고 매력적인 동적 시각적 효과를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="c4427-133">이러한 미묘한 색 변화로 사소한 색 불규칙도를 보정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="c4427-134">투명 또는 반투명 UI 백플래트 문제</span><span class="sxs-lookup"><span data-stu-id="c4427-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="c4427-135">![투명한 UI 예제 투명 ](images/color_transparent_examples.jpg)
 *UI 백플레이트 예*</span><span class="sxs-lookup"><span data-stu-id="c4427-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="c4427-136">**시각적 복잡성 및 접근성**</span><span class="sxs-lookup"><span data-stu-id="c4427-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="c4427-137">홀로그램 개체는 실제 환경과 혼합되므로 투명 또는 반투명 창의 콘텐츠 또는 UI 가독성이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="c4427-138">또한 투명 홀로그램 개체가 서로 위에 오버레이되는 경우 혼동되는 깊이로 인해 사용자가 상호 작용하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="c4427-139">**성능**</span><span class="sxs-lookup"><span data-stu-id="c4427-139">**Performance**</span></span>

<span data-ttu-id="c4427-140">투명 또는 반투명 개체가 올바르게 렌더링하려면 백그라운드에 있는 개체와 정렬하고 혼합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="c4427-141">투명 개체 정렬에는 CPU 비용이 적고 혼합 시 상당한 GPU 비용이 듭니다. GPU가 z 선별(즉, 선별)을 통해 숨겨진 표면 제거를 수행할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="c4427-142">깊이 테스트).</span><span class="sxs-lookup"><span data-stu-id="c4427-142">depth testing).</span></span> <span data-ttu-id="c4427-143">숨겨진 표면 제거를 허용하지 않을 경우 최종 렌더링된 픽셀에 필요한 작업 수가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="c4427-144">이로 인해 더 많은 압력 채우기 속도 제약 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="c4427-145">**깊이 LSR 기술의 홀로그램 안정성 문제**</span><span class="sxs-lookup"><span data-stu-id="c4427-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="c4427-146">홀로그램 다시 프로젝션 또는 홀로그램 안정성을 개선하기 위해 애플리케이션은 렌더링된 모든 프레임에 대해 깊이 버퍼를 시스템에 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="c4427-147">다시 프로젝션에 깊이 버퍼를 사용하는 경우 렌더링된 모든 픽셀에 해당하는 깊이의 깊이 버퍼를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="c4427-148">깊이 값이 있는 모든 픽셀에는 색 값도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="c4427-149">위의 지침을 따르지 않으면 유효한 깊이 정보가 없는 렌더링된 이미지의 영역이 종종 파동과 같은 왜곡으로 표시되는 아티팩트 생성 방식으로 다시 프로젝션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="c4427-150">투명 요소에 대한 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="c4427-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="c4427-151">**불투명 UI 배경 사용**</span><span class="sxs-lookup"><span data-stu-id="c4427-151">**Use opaque UI background**</span></span>

<span data-ttu-id="c4427-152">기본적으로 투명 또는 반투명 개체는 적절한 혼합을 허용하기 위해 깊이를 작성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="c4427-153">이 문제를 완화하는 방법은 불투명 개체 사용, 불투명 개체(예: 불투명 백플래트 앞에 반투명 단추) 가까이 표시, 반투명 개체가 깊이를 쓰도록 강제 적용(모든 시나리오에 적용되지 않음) 또는 프레임 끝에 깊이 값만 기여하는 프록시 개체 렌더링 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="c4427-154">MRTK-Unity 내의 솔루션: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="c4427-154">Solutions within MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="c4427-155">단색 및 불투명 백플레이트를 사용하여 가독성 및 상호 작용 신뢰도를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="c4427-156">**영향을 받는 픽셀 수 최소화**</span><span class="sxs-lookup"><span data-stu-id="c4427-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="c4427-157">프로젝트에서 투명 개체를 사용해야 하는 경우 영향을 받는 픽셀 수를 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="c4427-158">예를 들어 개체가 가감 효과와 같은 특정 조건에서만 표시되는 경우 가감 색을 검은색으로 설정하는 대신 완전히 보이지 않을 때 개체를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="c4427-159">알파 마스크가 있는 쿼드를 사용하여 만든 간단한 2D 도형의 경우 불투명 셰이더를 사용하여 셰이프의 메시 표현을 대신 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c4427-160">Unity용 MRTK(Mixed Reality Toolkit)의 어두운 UI 예제</span><span class="sxs-lookup"><span data-stu-id="c4427-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="c4427-161">**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 어두운 색 구성표를 기반으로 하는 많은 UI 구성표 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c4427-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="c4427-162">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="c4427-162">Near Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="c4427-163">대화 상자</span><span class="sxs-lookup"><span data-stu-id="c4427-163">Dialog</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="c4427-164">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="c4427-164">Hand Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="c4427-165">참조</span><span class="sxs-lookup"><span data-stu-id="c4427-165">See also</span></span>

* [<span data-ttu-id="c4427-166">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="c4427-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="c4427-167">커서</span><span class="sxs-lookup"><span data-stu-id="c4427-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c4427-168">손 광선</span><span class="sxs-lookup"><span data-stu-id="c4427-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c4427-169">Button</span><span class="sxs-lookup"><span data-stu-id="c4427-169">Button</span></span>](button.md)
* [<span data-ttu-id="c4427-170">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="c4427-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c4427-171">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="c4427-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c4427-172">조작</span><span class="sxs-lookup"><span data-stu-id="c4427-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c4427-173">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="c4427-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c4427-174">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="c4427-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c4427-175">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="c4427-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c4427-176">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c4427-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c4427-177">키보드</span><span class="sxs-lookup"><span data-stu-id="c4427-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c4427-178">Tooltip</span><span class="sxs-lookup"><span data-stu-id="c4427-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c4427-179">슬레이트</span><span class="sxs-lookup"><span data-stu-id="c4427-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="c4427-180">슬라이더</span><span class="sxs-lookup"><span data-stu-id="c4427-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="c4427-181">셰이더</span><span class="sxs-lookup"><span data-stu-id="c4427-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="c4427-182">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="c4427-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c4427-183">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="c4427-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c4427-184">표면 자성</span><span class="sxs-lookup"><span data-stu-id="c4427-184">Surface magnetism</span></span>](surface-magnetism.md)