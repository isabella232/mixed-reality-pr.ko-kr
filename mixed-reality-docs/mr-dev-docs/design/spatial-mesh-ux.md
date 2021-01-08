---
title: 공간 메시 시각화
description: MRTK의 공간 메시 시각화를 사용 하 여 디자인 지침 및 물리적 환경 이해에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 혼합 현실, HoloLens, UI 컨트롤, 상호 작용, ui, ux, UX 디자인, 공간 UI, 공간 상호 작용, 3D UI, 3D UX, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0f9cdc218c6fe54b8892c39a6a76f023e203d334
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009923"
---
# <a name="spatial-mesh"></a><span data-ttu-id="44fec-104">공간 메시</span><span class="sxs-lookup"><span data-stu-id="44fec-104">Spatial mesh</span></span>

![공간 메시](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="44fec-106">사용자는 장치에서 공간 메시 시각화를 통해 물리적 환경을 인식 하 고 이해 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="44fec-107">적절 한 공간 메시 시각화는 공간 컨텍스트를 제공 하는 동시에 매력적인 및 마법 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="44fec-108">디자인 지침</span><span class="sxs-lookup"><span data-stu-id="44fec-108">Design guideline</span></span>

<span data-ttu-id="44fec-109">사용자가 콘텐츠를 집중적으로 사용 하 고 상호 작용할 수 있도록 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="44fec-110">배경에서 공간 메시의 연속 시각화는 혼란을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="44fec-111">초기 실행에서 한 번만 또는 사용자가 공간을 대상으로 하 여 환경 메시를 표시 하려는 경우에만 환경을 시각화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="44fec-112">혼합 현실 포털에서이 동작을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="44fec-113">Unity 용 MRTK (Mixed Reality Toolkit)의 공간 메시 시각화</span><span class="sxs-lookup"><span data-stu-id="44fec-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="44fec-114">MRTK는 공간 메시 시각화에 대 한 여러 자료를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="44fec-115">**MRTK_Wireframe, MRTK_Wireframe**: 기본 정적 공간 메시 재질: 애니메이션 없이 메시 윤곽선을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="44fec-116">이 자료는 전체 공간 메시 기 하 도형을 표시 하기 때문에 디버깅 목적으로 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="44fec-117">그러나 프로덕션에는 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="44fec-118">**MRTK_SurfaceReconstruction.** 대만:이 자료는 공간 메시에 애니메이션 된 펄스 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="44fec-119">이 자료를 사용 하 여 특정 순간 이나 사용자의 공중 탭 입력에서 환경을 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44fec-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="44fec-120">예제는 **PulseShaderExamples** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44fec-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="44fec-121">자세한 내용은 [Mrtk-공간 인식](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 및 [Mrtk-펄스 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44fec-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="44fec-122">참조</span><span class="sxs-lookup"><span data-stu-id="44fec-122">See also</span></span>

* [<span data-ttu-id="44fec-123">커서</span><span class="sxs-lookup"><span data-stu-id="44fec-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="44fec-124">손 광선</span><span class="sxs-lookup"><span data-stu-id="44fec-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="44fec-125">Button</span><span class="sxs-lookup"><span data-stu-id="44fec-125">Button</span></span>](button.md)
* [<span data-ttu-id="44fec-126">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="44fec-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="44fec-127">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="44fec-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="44fec-128">조작</span><span class="sxs-lookup"><span data-stu-id="44fec-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="44fec-129">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="44fec-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="44fec-130">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="44fec-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="44fec-131">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="44fec-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="44fec-132">음성 명령</span><span class="sxs-lookup"><span data-stu-id="44fec-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="44fec-133">키보드</span><span class="sxs-lookup"><span data-stu-id="44fec-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="44fec-134">Tooltip</span><span class="sxs-lookup"><span data-stu-id="44fec-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="44fec-135">슬레이트</span><span class="sxs-lookup"><span data-stu-id="44fec-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="44fec-136">슬라이더</span><span class="sxs-lookup"><span data-stu-id="44fec-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="44fec-137">셰이더</span><span class="sxs-lookup"><span data-stu-id="44fec-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="44fec-138">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="44fec-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="44fec-139">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="44fec-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="44fec-140">표면 자성</span><span class="sxs-lookup"><span data-stu-id="44fec-140">Surface magnetism</span></span>](surface-magnetism.md)
