---
title: Unreal의 로컬 Spatial Anchors
description: Unreal의 공간 앵커 사용 가이드
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 앵커
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702180"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="8518c-104">Unreal의 로컬 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8518c-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="8518c-105">개요</span><span class="sxs-lookup"><span data-stu-id="8518c-105">Overview</span></span>

<span data-ttu-id="8518c-106">공간 앵커는 애플리케이션 세션 사이의 실제 공간에서 홀로그램을 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="8518c-107">이는 Unreal을 통해 **ARPin** 으로 표시되며 향후 세션에 로드될 HoloLens의 앵커 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="8518c-108">로컬 앵커는 인터넷에 연결되어 있지 않은 경우 대비책으로 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8518c-109">로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="8518c-110">Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](unreal-azure-spatial-anchors.md) 통합 과정을 안내하는 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8518c-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="8518c-111">로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="8518c-112">앵커 저장소 확인</span><span class="sxs-lookup"><span data-stu-id="8518c-112">Checking the anchor store</span></span>

<span data-ttu-id="8518c-113">앵커를 저장하거나 로드하기 전에 먼저 앵커 저장소가 준비되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="8518c-114">앵커 저장소가 준비되기 전에는 HoloLens 앵커 함수의 호출에 성공하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Spatial Anchors 저장소 준비](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="8518c-116">앵커 저장</span><span class="sxs-lookup"><span data-stu-id="8518c-116">Saving anchors</span></span>

<span data-ttu-id="8518c-117">세계에 고정해야 하는 구성 요소가 애플리케이션에 있으면 다음 순서에 따라 앵커 저장소에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Spatial Anchors 저장](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="8518c-119">상세 구분:</span><span class="sxs-lookup"><span data-stu-id="8518c-119">Breaking this down:</span></span>
1. <span data-ttu-id="8518c-120">알려진 위치에 행위자를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="8518c-121">행위자의 클래스를 기준으로 해당 위치와 이름을 사용하여 **ARPin** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="8518c-122">**ARPin** 에 행위자를 추가하고 HoloLens 앵커 저장소에 핀을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="8518c-123">선택한 앵커 이름은 고유해야 하며 이 예제에서는 현재 타임스탬프를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="8518c-124">앵커가 앵커 저장소에 성공적으로 저장된 경우, **시스템 > 맵 관리자 > 디바이스에 저장된 앵커 파일** 에서 해당 항목을 HoloLens 장치 포털에서 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device** .</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="8518c-125">앵커 로드</span><span class="sxs-lookup"><span data-stu-id="8518c-125">Loading anchors</span></span>

<span data-ttu-id="8518c-126">애플리케이션이 시작되면 다음 청사진을 사용하여 구성 요소를 앵커 위치에 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Spatial Anchors 로드](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="8518c-128">상세 구분:</span><span class="sxs-lookup"><span data-stu-id="8518c-128">Breaking this down:</span></span>
1. <span data-ttu-id="8518c-129">앵커 저장소의 모든 앵커에 대해 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="8518c-130">ID에서 행위자를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="8518c-131">해당 행위자를 앵커 저장소에서 **ARPin** 에 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="8518c-132">앵커는 홀로그램이 저장된 위치를 기준으로 홀로그램 위치를 다시 설정하는 것을 담당하므로 행위자를 ID에 생성하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="8518c-133">여기에 추가된 변환은 앵커에 오프셋을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="8518c-134">앵커 ID는 앵커의 저장된 이름에 따라 다른 행위자가 생성될 수 있도록 쿼리되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="8518c-135">앵커 제거</span><span class="sxs-lookup"><span data-stu-id="8518c-135">Removing anchors</span></span> 

<span data-ttu-id="8518c-136">앵커 작업을 마치면 **WMRAnchor 저장소에서 ARPin 제거** 및 **WMRAnchor 저장소 모든 ARPin 제거** 구성 요소를 통해 개별 앵커 또는 전체 앵커 저장소를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Spatial Anchors 제거](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="8518c-138">공간 앵커가 아직 베타 버전이므로 업데이트된 정보 및 기능을 다시 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8518c-139">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="8518c-139">Next Development Checkpoint</span></span>

<span data-ttu-id="8518c-140">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 MRTK 핵심 구성 요소를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8518c-141">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-141">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="8518c-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8518c-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="8518c-143">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8518c-144">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="8518c-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="8518c-145">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8518c-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8518c-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8518c-146">See also</span></span>
* [<span data-ttu-id="8518c-147">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8518c-147">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="8518c-148">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="8518c-148">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="8518c-149">좌표계</span><span class="sxs-lookup"><span data-stu-id="8518c-149">Coordinate systems</span></span>](../../design/coordinate-systems.md)
