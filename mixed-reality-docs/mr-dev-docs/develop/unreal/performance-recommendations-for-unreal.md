---
title: Unreal을 사용하기 위한 권장 성능
description: 권장 Unreal 프로젝트 설정을 사용하여 혼합 현실 앱을 최대한 활용하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583062"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="b05da-104">Unreal을 사용하기 위한 권장 성능</span><span class="sxs-lookup"><span data-stu-id="b05da-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="b05da-105">Unreal Engine에는 [혼합 현실에 대한 성능 권장 사항](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)에 설명된 내용을 기반으로 앱 성능을 향상시킬 수 있는 여러 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="b05da-106">계속하기 전에 애플리케이션 병목, 혼합 현실 앱 분석 및 프로파일링, 일반 성능 수정 사항을 확인해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="b05da-107">권장 Unreal 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b05da-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="b05da-108">**편집 > 프로젝트 설정** 에서 다음의 각 설정을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="b05da-109">모바일 VR 렌더러 사용:</span><span class="sxs-lookup"><span data-stu-id="b05da-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="b05da-110">**프로젝트** 섹션으로 스크롤하고 **대상 하드웨어** 를 선택한 다음, 대상 플랫폼을 **모바일/태블릿** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![모바일 대상 설정](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="b05da-112">전방 렌더러 사용:</span><span class="sxs-lookup"><span data-stu-id="b05da-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="b05da-113">전방 렌더러는 개별적으로 끌 수 있는 기능의 수가 많기 때문에 기본 지연 렌더링 파이프라인보다 혼합 현실에 훨씬 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="b05da-114">자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![전방 렌더링](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="b05da-116">모바일 다중 보기 사용:</span><span class="sxs-lookup"><span data-stu-id="b05da-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="b05da-117">**엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **VR** 섹션을 확장하고 **인스턴스 스테레오** 와 **모바일 다중 뷰** 를 모두 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="b05da-118">모바일 HDR를 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-118">Mobile HDR should be unchecked.</span></span>

![VR 렌더링 설정](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="b05da-120">**[OpenXR만]** **기본값** 또는 **D3D12** 가 **기본 RHI** 로 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="b05da-121">추가 렌더링 패스를 수행하는 플랫폼으로 인해 **D3D11** 을 선택하면 성능에 부정적인 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="b05da-122">**D3D12** 는 추가 렌더링 패스를 피하는 것 외에도 렌더링 성능 향상을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![기본 RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="b05da-124">꼭짓점 Fogging 비활성화:</span><span class="sxs-lookup"><span data-stu-id="b05da-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="b05da-125">꼭짓점 fogging 다각형의 각 꼭짓점에 포그 계산을 적용한 다음, 다각형의 표면 전체에 결과를 보간합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="b05da-126">게임에서 안개를 사용하지 않는 경우 꼭짓점 Fogging을 비활성화하여 음영 성능을 높이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![꼭짓점 fogging 옵션](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="b05da-128">폐색 고르기 사용 안 함:</span><span class="sxs-lookup"><span data-stu-id="b05da-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="b05da-129">**엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **고르기** 섹션을 확장하고 **폐색 고르기** 를 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="b05da-130">렌더링되는 자세한 장면에 폐색 고르기가 필요한 경우 **엔진 > 렌더링** 에서 **소프트웨어 폐색 고르기 지원** 을 사용하도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="b05da-131">Unreal이 CPU에서 작동하며, HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="b05da-132">모바일 디바이스에서 GPU에 대한 폐색 고르기 속도가 느립니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="b05da-133">일반적으로 GPU는 주로 렌더링에 관여하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="b05da-134">폐색이 성능에 도움이 된다고 생각되면 대신 소프트웨어 폐색을 사용하도록 설정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="b05da-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="b05da-135">많은 수의 그리기 호출로 인해 CPU가 이미 바인딩된 경우 소프트웨어 폐색을 사용하도록 설정하면 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![폐색 고르기 사용 안 함](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="b05da-137">사용자 지정 깊이-스텐실 비활성화 패스:</span><span class="sxs-lookup"><span data-stu-id="b05da-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="b05da-138">사용자 지정 깊이-스텐실을 비활성화하려면 추가 패스가 필요합니다. 즉, 속도가 느립니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="b05da-139">반투명도는 Unreal에서도 느립니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="b05da-140">자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![깊이 스텐실](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="b05da-142">중첩된 섀도 맵 축소:</span><span class="sxs-lookup"><span data-stu-id="b05da-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="b05da-143">섀도 맵의 수를 줄이면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="b05da-144">일반적으로 눈에 보이는 품질 손실이 없는 한 속성을 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![중첩된 섀도 맵](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="b05da-146">선택적 설정</span><span class="sxs-lookup"><span data-stu-id="b05da-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="b05da-147">다음 설정을 사용하면 성능을 향상시킬 수 있지만 특정 기능을 사용하지 않도록 설정하는 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="b05da-148">해당 기능이 필요하지 않는 경우에만 이 설정을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="b05da-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="b05da-149">모바일 셰이더 순열 감소</span><span class="sxs-lookup"><span data-stu-id="b05da-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="b05da-150">조명이 카메라와 별개로 이동하지 않는 경우 속성 값을 안전하게 0으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="b05da-151">기본 장점은 Unreal이 여러 셰이더 순열을 제거하여 셰이더 컴파일의 속도를 높일 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b05da-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![모바일 셰이더 순열 감소](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="b05da-153">참조</span><span class="sxs-lookup"><span data-stu-id="b05da-153">See also</span></span>

* [<span data-ttu-id="b05da-154">Unreal 엔진 모바일 성능 지침</span><span class="sxs-lookup"><span data-stu-id="b05da-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)