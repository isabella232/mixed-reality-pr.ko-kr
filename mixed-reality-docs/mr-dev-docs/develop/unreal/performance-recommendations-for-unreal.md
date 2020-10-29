---
title: Unreal을 사용하기 위한 권장 성능
description: Unreal의 혼합 현실 앱에 대한 최적의 성능을 위한 권장 사항
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699289"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="1ea28-104">Unreal을 사용하기 위한 권장 성능</span><span class="sxs-lookup"><span data-stu-id="1ea28-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="1ea28-105">개요</span><span class="sxs-lookup"><span data-stu-id="1ea28-105">Overview</span></span>

<span data-ttu-id="1ea28-106">이 문서에서는 [혼합 현실에 대한 성능 추천 사항](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unreal Engine 특정 기능에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="1ea28-107">계속하기 전에 애플리케이션 병목, 혼합 현실 앱 분석 및 프로파일링, 일반 성능 수정 사항을 확인해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="1ea28-108">권장 Unreal 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="1ea28-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="1ea28-109">**편집 > 프로젝트 설정** 에서 다음의 각 설정을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="1ea28-110">모바일 VR 렌더러 사용:</span><span class="sxs-lookup"><span data-stu-id="1ea28-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="1ea28-111">**프로젝트** 섹션으로 스크롤하고 **대상 하드웨어** 를 선택한 다음, 대상 플랫폼을 **모바일/태블릿** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![모바일 대상 설정](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="1ea28-113">전방 렌더러 사용:</span><span class="sxs-lookup"><span data-stu-id="1ea28-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="1ea28-114">이 기능은 기본 지연 렌더링 파이프라인보다 Mixed Reality에서 훨씬 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="1ea28-115">이는 주로 개별적으로 해제할 수 있는 기능 수로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="1ea28-116">자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![전방 렌더링](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="1ea28-118">꼭짓점 Fogging 비활성화:</span><span class="sxs-lookup"><span data-stu-id="1ea28-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="1ea28-119">꼭짓점 fogging 다각형의 각 꼭짓점에 포그 계산을 적용한 다음, 다각형의 표면 전체에 결과를 보간합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="1ea28-120">게임에서 포그를 사용하지 않는 경우 이 설정을 선택하여 포그를 사용하지 않도록 설정하여 음영 처리 성능을 향상시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![꼭짓점 fogging 옵션](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="1ea28-122">폐색 고르기 사용 안 함:</span><span class="sxs-lookup"><span data-stu-id="1ea28-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="1ea28-123">**엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **고르기** 섹션을 확장하고 **폐색 고르기** 를 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="1ea28-124">렌더링되는 자세한 장면에 폐색 고르기가 필요한 경우 **엔진 > 렌더링** 에서 **소프트웨어 폐색 고르기 지원** 을 사용하도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="1ea28-125">이렇게 하면 Unreal이 CPU에서 작동하며, HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="1ea28-126">모바일 디바이스에서 GPU에 대한 폐색 고르기 속도가 느립니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="1ea28-127">일반적으로 GPU는 주로 렌더링에 관여하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="1ea28-128">폐색이 성능에 도움이 된다고 생각되면 대신 소프트웨어 폐색을 사용하도록 설정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="1ea28-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="1ea28-129">많은 수의 그리기 호출로 인해 CPU가 이미 바인딩된 경우 소프트웨어 폐색을 사용하도록 설정하면 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![폐색 고르기 사용 안 함](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="1ea28-131">깊이 스텐실 사용 안 함:</span><span class="sxs-lookup"><span data-stu-id="1ea28-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="1ea28-132">이 기능 추가 패스가 필요하므로 속도가 느립니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="1ea28-133">반투명도는 Unreal에서도 느립니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="1ea28-134">자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![깊이 스텐실](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="1ea28-136">모바일 다중 보기 사용:</span><span class="sxs-lookup"><span data-stu-id="1ea28-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="1ea28-137">**엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **VR** 섹션을 확장하고 **인스턴스 스테레오** 와 **모바일 다중 뷰** 를 모두 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="1ea28-138">모바일 HDR를 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-138">Mobile HDR should be unchecked.</span></span>

![VR 렌더링 설정](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="1ea28-140">중첩된 섀도 맵 축소:</span><span class="sxs-lookup"><span data-stu-id="1ea28-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="1ea28-141">섀도 맵의 수를 줄이면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="1ea28-142">일반적으로 품질이 저하되지 않는 한 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![중첩된 섀도 맵](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="1ea28-144">선택적 설정</span><span class="sxs-lookup"><span data-stu-id="1ea28-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="1ea28-145">다음 설정을 사용하면 성능을 향상시킬 수 있지만 특정 기능을 사용하지 않도록 설정하는 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="1ea28-146">해당 기능이 필요하지 않는 경우에만 이 설정을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1ea28-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="1ea28-147">모바일 셰이더 순열 감소</span><span class="sxs-lookup"><span data-stu-id="1ea28-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="1ea28-148">조명이 카메라와 별개로 이동하지 않는 경우 이 값을 0으로 안전하게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="1ea28-149">기본 장점은 Unreal이 여러 셰이더 순열을 제거하여 셰이더 컴파일의 속도를 높일 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea28-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![모바일 셰이더 순열 감소](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="1ea28-151">참조</span><span class="sxs-lookup"><span data-stu-id="1ea28-151">See also</span></span>
* [<span data-ttu-id="1ea28-152">Unreal 엔진 모바일 성능 지침</span><span class="sxs-lookup"><span data-stu-id="1ea28-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)