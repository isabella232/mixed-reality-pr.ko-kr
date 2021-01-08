---
title: 장면 이해
description: SDK, 기능 및 일반적인 사용 시나리오를 비롯 하 여 HoloLens에 대 한 장면 이해를 통해 개발 하는 방법에 대해 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 폐색, SDK
ms.openlocfilehash: c4485c5501300d6ca629f4e587fde1f88eea7ea5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008873"
---
# <a name="scene-understanding"></a><span data-ttu-id="01ebc-104">장면 이해</span><span class="sxs-lookup"><span data-stu-id="01ebc-104">Scene understanding</span></span>

<span data-ttu-id="01ebc-105">장면 이해는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조적인 고급 환경 표현을 포함 하는 혼합 현실 개발자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="01ebc-106">장면 이해는 매우 정확 하지만 구조화 되지 않은 [공간 매핑과](spatial-mapping.md) 새로운 AI 기반 런타임과 같이 기존의 혼합 현실 런타임의 강력한 기능을 결합 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-106">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="01ebc-107">이러한 기술을 결합 하 여 장면 이해는 Unity 또는 ARKit/Arkit와 같은 프레임 워크에서 사용한 것과 유사한 3D 환경의 표현을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="01ebc-108">장면 이해 진입점은 새 장면을 계산 하기 위해 응용 프로그램에서 호출 하는 장면 관찰자로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="01ebc-109">현재이 기술은 3 가지 고유 하지만 관련 개체 범주를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-109">Today, the technology can generate 3 distinct but related object categories:</span></span> 

* <span data-ttu-id="01ebc-110">간단 하지 않고 평면 대화방 구조를 유추 하는 간소화 된 watertight 환경 망</span><span class="sxs-lookup"><span data-stu-id="01ebc-110">Simplified watertight environment meshes that infer the planar room structure without clutter</span></span>
* <span data-ttu-id="01ebc-111">Quads를 호출 하는 배치를 위한 평면 영역</span><span class="sxs-lookup"><span data-stu-id="01ebc-111">Plane regions for placement that we call Quads</span></span>
* <span data-ttu-id="01ebc-112">노출 되는 Quads/Watertight 데이터에 맞는 [공간 매핑](spatial-mapping.md) 메시의 스냅숏입니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-112">A snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface</span></span>

![공간 매핑 메시, 레이블이 지정 된 평면 표면, watertight 메시](images/SUScenarios.png)

<span data-ttu-id="01ebc-114">이 문서는 시나리오 개요를 제공 하 고 장면 이해 및 공간 매핑 공유의 관계를 명확 하 게 설명 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-114">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="01ebc-115">장면 이해로 개발</span><span class="sxs-lookup"><span data-stu-id="01ebc-115">Developing with Scene Understanding</span></span>

<span data-ttu-id="01ebc-116">이 문서에서는 런타임 및 개념을 이해 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-116">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="01ebc-117">장면 이해를 통해 개발 하는 방법에 대 한 설명서를 찾으려는 경우 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="01ebc-117">If you're looking for documentation on how to develop with Scene Understanding, you may be interested in the following articles:</span></span>

[<span data-ttu-id="01ebc-118">장면 이해 SDK 개요</span><span class="sxs-lookup"><span data-stu-id="01ebc-118">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="01ebc-119">샘플 GitHub 사이트에서 장면 이해 샘플 앱을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-119">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="01ebc-120">장면 이해 샘플</span><span class="sxs-lookup"><span data-stu-id="01ebc-120">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="01ebc-121">장치를 사용 하지 않고 장면 이해를 시도 하기 위해 샘플 장면에 액세스 하려는 경우 샘플 자산 폴더에는 장면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-121">If you don't have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="01ebc-122">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="01ebc-122">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="01ebc-123">SDK)</span><span class="sxs-lookup"><span data-stu-id="01ebc-123">SDK</span></span>

<span data-ttu-id="01ebc-124">장면 이해를 사용 하 여 개발 하는 방법에 대 한 자세한 내용은 [SDK 이해 SDK 개요](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="01ebc-124">If you're looking for specific details on developing with Scene Understanding, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>

### <a name="sample"></a><span data-ttu-id="01ebc-125">샘플</span><span class="sxs-lookup"><span data-stu-id="01ebc-125">Sample</span></span>

## <a name="device-support"></a><span data-ttu-id="01ebc-126">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="01ebc-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="01ebc-127"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="01ebc-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="01ebc-128"><a href="../hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="01ebc-128"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="01ebc-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="01ebc-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="01ebc-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="01ebc-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="01ebc-131">장면 이해</span><span class="sxs-lookup"><span data-stu-id="01ebc-131">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="01ebc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="01ebc-132">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="01ebc-133">일반 시나리오</span><span class="sxs-lookup"><span data-stu-id="01ebc-133">Common usage scenarios</span></span>

<span data-ttu-id="01ebc-134">![일반적인 공간 매핑 사용 시나리오의 그림: 배치, 폐색, 물리 및 탐색](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01ebc-134">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="01ebc-135">*일반적인 공간 매핑 사용 시나리오: 배치, 폐색, 물리 및 탐색.*</span><span class="sxs-lookup"><span data-stu-id="01ebc-135">*Common spatial mapping usage scenarios: placement, occlusion, physics, and navigation.*</span></span>

<br>

<span data-ttu-id="01ebc-136">Environmentally 인식 응용 프로그램에 대 한 핵심 시나리오의 대부분은 공간 매핑과 장면 이해를 통해 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-136">Many of the core scenarios for environmentally aware applications can be addressed by both Spatial mapping and Scene understanding.</span></span> <span data-ttu-id="01ebc-137">이러한 핵심 시나리오에는 placement, 폐색, 물리학 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-137">These core scenarios include placement, occlusion, physics, and so on.</span></span> <span data-ttu-id="01ebc-138">장면 이해와 공간 매핑의 핵심 차이점은 최대 정확성과 구조 및 단순성의 대기 시간에 대 한 균형입니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-138">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="01ebc-139">응용 프로그램에 사용자만 액세스할 수 있는 가장 낮은 대기 시간 및 메시 삼각형이 필요한 경우 공간 매핑을 직접 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-139">If your application requires the lowest-latency possible and mesh triangles that only you'll want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="01ebc-140">더 높은 수준의 처리를 수행 하는 경우 기능 상위 집합을 제공 해야 하므로 장면 이해 모델로 전환 하는 것을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-140">If you're doing higher-level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="01ebc-141">장면 이해에서는 공간 매핑 메시의 스냅숏을 표현의 일부로 제공 하기 때문에 항상 가장 완전 하 고 정확한 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-141">You'll always have access to the most complete and accurate spatial mapping data possible because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation.</span></span>

<span data-ttu-id="01ebc-142">다음 섹션에서는 새 장면 이해 SDK의 컨텍스트에서 핵심 공간 매핑 시나리오를 다시 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-142">The following sections revisit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="01ebc-143">배치</span><span class="sxs-lookup"><span data-stu-id="01ebc-143">Placement</span></span>

<span data-ttu-id="01ebc-144">장면 이해에서는 배치 시나리오를 간소화 하도록 설계 된 새 구문을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-144">Scene understanding provides new constructs designed to simplify placement scenarios.</span></span> <span data-ttu-id="01ebc-145">장면은 holograms을 배치할 수 있는 플랫 표면을 설명 하는 SceneQuads 라는 기본 형식을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-145">A scene can compute primitives called SceneQuads, which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="01ebc-146">SceneQuads는 배치를 중심으로 디자인 되었으며 2D 표면을 설명 하 고 해당 화면에 배치 하기 위한 API를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-146">SceneQuads have been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="01ebc-147">이전에는 삼각형 메시를 사용 하 여 배치 작업을 수행할 때 쿼드의 모든 영역을 검색 하 고 구멍 채우기/사후 처리를 수행 하 여 개체 배치를 위한 좋은 위치를 확인 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-147">Previously, when using the triangle mesh to do placement, one had to scan all areas of the quad and do hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="01ebc-148">장면 이해 런타임은 스캔 되지 않은 쿼드 영역을 유추 하 고 표면에 속하지 않는 영역을 무효화 하므로 항상 Quads에는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-148">This isn't always necessary with Quads, as the Scene understanding runtime infers which quad areas weren't scanned, and invalidate areas that aren't part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="01ebc-149">![유추를 사용 하지 않도록 설정 하 고, 스캔 한 영역에 대 한 배치 영역을 SceneQuads 합니다.](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="01ebc-149">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="01ebc-150">**이미지 #1** -유추가 사용 하지 않도록 설정 된 SceneQuads, 스캔 한 영역에 대 한 배치 영역 캡처</span><span class="sxs-lookup"><span data-stu-id="01ebc-150">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="01ebc-151">![유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="01ebc-151">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="01ebc-152">**이미지 #2** -유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-152">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="01ebc-153">응용 프로그램에서 2D 또는 3D holograms를 환경의 고정 구조에 배치 하려는 경우 배치를 위한 SceneQuads의 단순성과 편의성은 [공간 매핑](spatial-mapping.md) 메시에서이 정보를 계산 하는 것 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-153">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="01ebc-154">이 항목에 대 한 자세한 내용은 [장면 이해 SDK 참조](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="01ebc-154">For more information on this topic, see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="01ebc-155">**참고** 공간 매핑 메시에 의존 하는 레거시 배치 코드의 경우 EnableWorldMesh 설정을 설정 하 여 SceneQuads와 함께 공간 매핑 메시를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-155">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="01ebc-156">장면 이해 API가 응용 프로그램의 대기 시간 요구 사항에 맞지 않는 경우 [공간 매핑 api](spatial-mapping.md#placement)를 계속 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-156">If Scene understanding API doesn't satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="01ebc-157">폐색</span><span class="sxs-lookup"><span data-stu-id="01ebc-157">Occlusion</span></span>

<span data-ttu-id="01ebc-158">[공간 매핑 폐색](spatial-mapping.md#occlusion) 환경의 실시간 상태를 캡처하는 가장 낮은 방법으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-158">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="01ebc-159">이는 매우 동적인 장면에서 폐색을 제공 하는 데 유용할 수 있지만 여러 가지 이유로 폐색에 대 한 장면 이해를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-159">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="01ebc-160">장면 이해로 생성 된 공간 매핑 메시를 사용 하는 경우 로컬 캐시에 저장 되지 않으며 인식 Api에서 사용할 수 없는 공간 매핑에서 데이터를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-160">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that wouldn't be stored in the local cache and isn't available from the perception APIs.</span></span> <span data-ttu-id="01ebc-161">Watertight 메시와 함께 폐색에 대 한 공간 매핑을 사용 하면 특히 검색 되지 않은 room 구조가 추가 가치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-161">Using Spatial Mapping for occlusion alongside watertight meshes will provide extra value, specifically completion of unscanned room structure.</span></span>

<span data-ttu-id="01ebc-162">요구 사항에 따라 장면 이해의 대기 시간이 길어질 수 있는 경우 응용 프로그램 개발자는 장면 이해 watertight 메시를 사용 하 고 한꺼번에에서 평면 표현을 사용 하는 공간 매핑 메시를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-162">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="01ebc-163">이렇게 하면 간소화 된 watertight 폐색이 가장 현실적인 폐색 지도를 제공 하는 보다 정교한 nonplanar 기 하 도형으로 결혼 하는 "세계 최고의" 시나리오를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-163">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="01ebc-164">Physics</span><span class="sxs-lookup"><span data-stu-id="01ebc-164">Physics</span></span>

<span data-ttu-id="01ebc-165">장면 이해는 공간 매핑 메시가 적용 하는 물리의 많은 제한 사항을 해결 하기 위해 의미 체계를 사용 하 여 공간을 분해 하는 watertight 메시를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-165">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="01ebc-166">Watertight 구조체를 사용 하면 물리학 광선 캐스팅이 항상 적중 되며, 의미 체계 분해를 통해 실내 탐색을 위한 탐색 메시를 보다 간단 하 게 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-166">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="01ebc-167">[폐색](#occlusion)에 대 한 섹션에 설명 된 대로 EnableSceneObjectMeshes 및 EnableWorldMesh를 사용 하 여 장면을 만들면 실제로 완전히 완료 된 메시가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-167">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="01ebc-168">환경 메시의 watertight 속성을 통해 적중 테스트는 적중 횟수 테스트에 실패 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-168">The watertight property of the environment mesh prevents hit tests from failing to hit surfaces.</span></span> <span data-ttu-id="01ebc-169">메시 데이터를 사용 하 여 물리학은 방 구조만이 아니라 장면의 모든 개체와 상호 작용 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-169">The mesh data will ensure physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="01ebc-170">탐색</span><span class="sxs-lookup"><span data-stu-id="01ebc-170">Navigation</span></span>

<span data-ttu-id="01ebc-171">의미 체계 클래스로 분해 된 평면 메시는 탐색 및 경로 계획에 이상적인 구문이 며 [공간 매핑 탐색](spatial-mapping.md#navigation) 개요에 설명 된 많은 문제를 감속 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-171">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="01ebc-172">장면에서 계산 된 SceneMesh 개체는 노출 될 수 있는 표면으로 nav 메시를 생성할 수 있도록 표면 유형에 의해 구성 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-172">The SceneMesh objects computed in the scene are de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="01ebc-173">간단한 구조를 기반으로 하기 때문에 Unity와 같은 3d 엔진의 동적 탐색-메시 생성은 실시간 요구 사항에 따라 realistic 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-173">Because of the floor structures' simplicity, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="01ebc-174">정확한 탐색을 생성 하는 메시는 현재 사후 처리가 필요 합니다. 즉, 탐색이 복잡 한/테이블을 통해 전달 되지 않도록 응용 프로그램에서 바닥에 계속 occluders 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-174">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation doesn't pass through clutter/tables and so on.</span></span> <span data-ttu-id="01ebc-175">이를 수행 하는 가장 정확한 방법은 세계 메시 데이터를 프로젝션 하는 것입니다 .이 데이터는 장면이 EnableWorldMesh 플래그를 사용 하 여 계산 되는 경우에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-175">The most accurate way to accomplish this is to project the world mesh data, which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="01ebc-176">시각화</span><span class="sxs-lookup"><span data-stu-id="01ebc-176">Visualization</span></span>

<span data-ttu-id="01ebc-177">[공간 매핑 시각화](spatial-mapping.md#visualization) 를 사용 하 여 환경에 대 한 실시간 피드백을 제공할 수 있지만, 평면 및 watertight 개체의 단순성은 더 많은 성능과 시각적 품질을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-177">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="01ebc-178">공간 매핑을 사용 하 여 설명 하는 그림자 프로젝션 및 접지 기술은 Quads 또는 planar watertight 메시에서 제공 되는 평면 표면에서 투영 된 경우 더 보기 편 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-178">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="01ebc-179">이는 장면에서 추론을 수행 하기 때문에 철저 한 사전 검사가 최적이 아닌 환경/시나리오에서 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-179">This is especially true for environments/scenarios where thorough pre-scanning isn't optimal because the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="01ebc-180">또한 공간 매핑에서 반환 된 총 표면 수는 내부 공간 캐시에 의해 제한 되는 반면 장면 이해의 공간 매핑 메시 버전은 캐시 되지 않은 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-180">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh can access spatial mapping data that isn't cached.</span></span> <span data-ttu-id="01ebc-181">이로 인해 시각화 또는 추가 메시 처리를 위해 장면 이해는 단일 공간 보다 큰 공간에 대 한 메시 표현을 캡처하는 데 더 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-181">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="01ebc-182">EnableWorldMesh를 사용 하 여 반환 되는 세계 메시는 전체에 걸쳐 일관 된 세부 수준을 가지 며,이는 와이어 프레임으로 렌더링 되는 경우 더 많은 보기 편 시각화를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ebc-182">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="01ebc-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01ebc-183">See Also</span></span>

* [<span data-ttu-id="01ebc-184">장면 이해 SDK</span><span class="sxs-lookup"><span data-stu-id="01ebc-184">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="01ebc-185">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="01ebc-185">Spatial mapping</span></span>](spatial-mapping.md)
