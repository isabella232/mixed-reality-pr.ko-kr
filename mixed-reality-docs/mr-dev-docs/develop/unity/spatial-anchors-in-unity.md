---
title: Unity의 세계 잠금 및 공간 앵커
description: Unity mixed reality 응용 프로그램에서 세계 잠금 도구 및 공간 앵커를 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, 공간 앵커, 앵커 저장소, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 세계 잠금 도구, holograms
ms.openlocfilehash: 4fc982244a766bb34f15b356d608f2aad18f7a88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528805"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a><span data-ttu-id="f31d4-104">Unity의 세계 잠금 및 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="f31d4-104">World locking and spatial anchors in Unity</span></span>

![세계 잠금 도구 주인공 이미지](images/wlt-img-01.jpeg)

<span data-ttu-id="f31d4-106">Holograms을 준비 하 고, 이동 하거나, 다른 holograms를 기준으로 하는 경우에는 혼합 현실 응용 프로그램을 만드는 과정에서 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-106">Getting your holograms to stay in place, move with you, or in some cases position themselves relative to other holograms is a big part of creating Mixed Reality applications.</span></span> <span data-ttu-id="f31d4-107">이 문서에서는 세계 잠금 도구를 사용 하는 권장 솔루션을 안내 하지만 Unity 프로젝트에서 공간 앵커를 수동으로 설정 하는 방법에 대해서도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-107">This article will take you through our recommended solution using World Locking Tools, but we'll also cover manually setting up spatial anchors in your Unity projects.</span></span> <span data-ttu-id="f31d4-108">코드로 이동 하기 전에 Unity가 자체 엔진에서 좌표 공간 및 앵커를 처리 하는 방법을 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-108">Before we jump into any code, it's important to understand how Unity handles coordinate space and anchors in its own engine.</span></span>

## <a name="world-scale-coordinate-systems"></a><span data-ttu-id="f31d4-109">세계 확장 좌표계</span><span class="sxs-lookup"><span data-stu-id="f31d4-109">World-scale coordinate systems</span></span>

<span data-ttu-id="f31d4-110">오늘날 게임, 데이터 시각화 앱 또는 가상 현실 앱을 작성할 때 일반적인 방법은 다른 모든 좌표가 안정적으로 다시 매핑될 수 있는 하나의 절대 **좌표계** 를 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-110">Today, when writing games, data visualization apps, or virtual reality apps, the typical approach is to establish one absolute **world coordinate system** that all other coordinates can reliably map back to.</span></span> <span data-ttu-id="f31d4-111">해당 환경에서 항상 해당 세계의 두 개체 간의 관계를 정의 하는 안정적인 변환을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-111">In that environment, you can always find a stable transform that defines a relationship between any two objects in that world.</span></span> <span data-ttu-id="f31d4-112">이러한 개체를 이동 하지 않은 경우에는 상대 변환이 항상 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-112">If you didn't move those objects, their relative transforms would always remain the same.</span></span> <span data-ttu-id="f31d4-113">이러한 종류의 글로벌 좌표계는 모든 기 하 도형을 미리 알고 있는 순수한 가상 세계를 렌더링 하는 경우 쉽게 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-113">This kind of global coordinate system is easy to get right when rendering a purely virtual world where you know all of the geometry in advance.</span></span> <span data-ttu-id="f31d4-114">현재 공간 규모의 VR 응용 프로그램은 일반적으로 바닥의 원점을 사용 하 여 이러한 종류의 절대 공간 크기 조정 좌표계를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-114">Room-scale VR apps today typically establish this kind of absolute room-scale coordinate system with its origin on the floor.</span></span>

<span data-ttu-id="f31d4-115">이와 대조적으로, HoloLens와 같은 작업할 혼합 현실 장치에는 전 세계의 전체 건물에서 많은 미터를 이동 하는 동안 사용자의 업무에 대 한 지식을 지속적으로 조정 하는 동적 센서 기반 이해가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-115">In contrast, an untethered mixed reality device such as HoloLens has a dynamic sensor-driven understanding of the world, continuously adjusting its knowledge over time of the user's surroundings as they walk many meters across an entire floor of a building.</span></span> <span data-ttu-id="f31d4-116">전 세계 규모의 환경에서 모든 holograms을 naive 고정 좌표계에 배치 하는 경우 해당 holograms는 전 세계 또는 서로를 기준으로 하 여 유동에 따라 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-116">In a world-scale experience, if you placed all your holograms in a naive rigid coordinate system, those holograms would end up drifting over time, either based on the world or relative to each other.</span></span>

<span data-ttu-id="f31d4-117">예를 들어 헤드셋은 현재 전 세계의 두 위치를 4 미터 떨어진 것으로 생각 하 고, 나중에이에 대 한 이해를 구체화 하 여 위치는 실제로 3.9 미터 떨어져 있음을 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-117">For example, the headset may currently believe two locations in the world to be 4 meters apart, and then later refine that understanding, learning that the locations are in fact 3.9 meters apart.</span></span> <span data-ttu-id="f31d4-118">이러한 holograms 처음에 하나의 고정 좌표계에 4 미터 떨어진 위치에 배치 된 경우 그 중 하나는 항상 실제 세계에서 0.1 미터를 벗어나 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-118">If those holograms had initially been placed 4 meters apart in a single rigid coordinate system, one of them would then always appear 0.1 meters off from the real world.</span></span>

<span data-ttu-id="f31d4-119">사용자가 mobile 인 경우 실제 환경에서 홀로그램의 위치를 유지 하기 위해 Unity에 **공간 앵커** 를 수동으로 배치할 수 있습니다. 그러나이 sacrifices 가상 환경 내에서 자체 일관성을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-119">You can manually place **spatial anchors** in Unity to maintain a hologram's position in the physical world when the user is mobile - however, this sacrifices the self-consistency within the virtual world.</span></span> <span data-ttu-id="f31d4-120">다른 앵커는 서로 관련 하 여 지속적으로 이동 하며, 전역 좌표 공간도 이동 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-120">Different anchors are constantly moving in relation to one another, and are also moving through the global coordinate space.</span></span> <span data-ttu-id="f31d4-121">이 시나리오에서 레이아웃 같은 간단한 작업은 어렵고 물리 시뮬레이션 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-121">In this scenario, simple tasks like layout become difficult and physics simulation problematic.</span></span>

<span data-ttu-id="f31d4-122">**세계 잠금 도구** 는 사용자가 이동 하는 동안 가상 장면 전체에 분산 된 공간 앵커의 내부 공급을 사용 하 여 단일 고정 좌표계를 안정화 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-122">**World Locking Tools** gets you the best of both worlds, stabilizing a single rigid coordinate system using an internal supply of spatial anchors spread throughout the virtual scene as the user moves around.</span></span> <span data-ttu-id="f31d4-123">도구는 카메라의 좌표와 각 프레임의 공간 앵커를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-123">The tools analyze the coordinates of the camera and those spatial anchors every frame.</span></span> <span data-ttu-id="f31d4-124">사용자 헤드의 좌표에 대 한 수정을 보정 하기 위해 전 세계 모든 항목의 좌표를 변경 하는 대신,이 도구는 헤드의 좌표를 대신 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-124">Instead of changing the coordinates of everything in the world to compensate for the corrections in the coordinates of the user's head, the tools just fix the head's coordinates instead.</span></span>

## <a name="choosing-your-world-locking-approach"></a><span data-ttu-id="f31d4-125">전 세계 잠금 방법 선택</span><span class="sxs-lookup"><span data-stu-id="f31d4-125">Choosing your world locking approach</span></span>

* <span data-ttu-id="f31d4-126">모든 홀로그램 위치 지정 요구 사항에 대해 **세계 잠금 도구** 를 사용 **하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="f31d4-126">**Our recommendation** is to use **World Locking Tools** for all your hologram positioning needs.</span></span> 
    * <span data-ttu-id="f31d4-127">세계 잠금 도구는 가상 및 실제 표식 간에 눈에 띄는 불일치를 최소화 하는 안정 된 좌표계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-127">World Locking Tools provides a stable coordinate system that minimizes the visible inconsistencies between virtual and real world markers.</span></span> <span data-ttu-id="f31d4-128">또 다른 방법으로, 그룹 자체의 개별 앵커를 사용 하 여 각 개체 그룹을 잠그지 않고 고정 공유 풀을 사용 하 여 전체 장면을 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-128">Put another way, it world-locks the entire scene with a shared pool of anchors, rather than locking each group of objects with the group's own individual anchor.</span></span>
* <span data-ttu-id="f31d4-129">**OpenXR 또는 WINDOWS XR 플러그 인을 사용 하는 Unity 2019/2020의** 경우 **ARAnchorManager** 를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-129">**For Unity 2019/2020 using OpenXR or the Windows XR Plugin**, you need to use **ARAnchorManager**</span></span>
* <span data-ttu-id="f31d4-130">**이전 Unity 버전 또는 WSA 프로젝트의** 경우 **WorldAnchor** 를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-130">**For older Unity versions or WSA** projects, you need to use **WorldAnchor**</span></span>

## <a name="setting-up-world-locking"></a><span data-ttu-id="f31d4-131">세계 잠금 설정</span><span class="sxs-lookup"><span data-stu-id="f31d4-131">Setting up world locking</span></span> 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a><span data-ttu-id="f31d4-132">지속적인 세계 잠금</span><span class="sxs-lookup"><span data-stu-id="f31d4-132">Persistent world locking</span></span>

<span data-ttu-id="f31d4-133">공간 앵커는 응용 프로그램 세션 간에 실제 공간에 holograms를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-133">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="f31d4-134">HoloLens의 앵커 저장소에 저장 한 후에는 서로 다른 세션에서 검색 하 고 로드할 수 있으며 인터넷에 연결 되지 않은 경우 이상적인 대체입니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-134">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f31d4-135">로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-135">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="f31d4-136">Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors) 통합 과정을 안내하는 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f31d4-136">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="f31d4-137">로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-137">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a><span data-ttu-id="f31d4-138">좌표 공간 공유</span><span class="sxs-lookup"><span data-stu-id="f31d4-138">Sharing coordinate spaces</span></span> 

<span data-ttu-id="f31d4-139">세계에서 잠긴 좌표 공간을 공유 하려면 포괄적인 [공유 환경 설명서](shared-experiences-in-unity.md)를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="f31d4-139">If you want to share a world locked coordinate space, check out our comprehensive [shared experience documentation](shared-experiences-in-unity.md).</span></span>

<span data-ttu-id="f31d4-140">Azure 공간 앵커는 아직 세계 잠금 도구 내에서 직접 지원 되지 않으므로 공유 환경에서는 공간 앵커를 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-140">Note that Azure Spatial Anchors is not yet supported directly within World Locking Tools, and so shared experiences will require you to manually create spatial anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f31d4-141">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="f31d4-141">Next Development Checkpoint</span></span>

<span data-ttu-id="f31d4-142">앞서 설명한 Unity 개발 검사점 경험을 팔로 사용할 경우 혼합 현실 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-142">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="f31d4-143">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-143">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f31d4-144">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f31d4-144">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="f31d4-145">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-145">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f31d4-146">공유 환경</span><span class="sxs-lookup"><span data-stu-id="f31d4-146">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f31d4-147">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f31d4-147">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f31d4-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f31d4-148">See Also</span></span>
* [<span data-ttu-id="f31d4-149">세계 잠금 도구 소개</span><span class="sxs-lookup"><span data-stu-id="f31d4-149">World Locking Tools introduction</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [<span data-ttu-id="f31d4-150">빠른 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="f31d4-150">Quickstart guides</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [<span data-ttu-id="f31d4-151">자습서</span><span class="sxs-lookup"><span data-stu-id="f31d4-151">Tutorials</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [<span data-ttu-id="f31d4-152">샘플</span><span class="sxs-lookup"><span data-stu-id="f31d4-152">Samples</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [<span data-ttu-id="f31d4-153">공간 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="f31d4-153">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="f31d4-154"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="f31d4-154"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="f31d4-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="f31d4-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="f31d4-156">환경 크기 조정</span><span class="sxs-lookup"><span data-stu-id="f31d4-156">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="f31d4-157">공간 스테이지</span><span class="sxs-lookup"><span data-stu-id="f31d4-157">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="f31d4-158">Unity의 손실 추적</span><span class="sxs-lookup"><span data-stu-id="f31d4-158">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="f31d4-159">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f31d4-159">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="f31d4-160">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="f31d4-160">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
