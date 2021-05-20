---
title: 장면 이해
description: SDK, 기능 및 일반적인 사용 시나리오를 비롯 하 여 HoloLens에 대 한 장면 이해를 통해 개발 하는 방법에 대해 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 폐색, SDK
ms.openlocfilehash: dd54be85ed71c3359408c02914470e97ab42b90e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196398"
---
# <a name="scene-understanding"></a><span data-ttu-id="edcf7-104">장면 이해</span><span class="sxs-lookup"><span data-stu-id="edcf7-104">Scene understanding</span></span>

<span data-ttu-id="edcf7-105">장면 이해는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조적인 고급 환경 표현을 포함 하는 혼합 현실 개발자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="edcf7-106">장면 이해는 매우 정확 하지만 구조화 되지 않은 [공간 매핑과](spatial-mapping.md) 새로운 AI 기반 런타임과 같이 기존의 혼합 현실 런타임의 강력한 기능을 결합 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-106">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="edcf7-107">이러한 기술을 결합 하 여 장면 이해는 Unity 또는 ARKit/Arkit와 같은 프레임 워크에서 사용한 것과 유사한 3D 환경의 표현을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="edcf7-108">장면 이해 진입점은 새 장면을 계산 하기 위해 응용 프로그램에서 호출 하는 장면 관찰자로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="edcf7-109">현재이 기술은 3 가지 고유 하지만 관련 개체 범주를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-109">Today, the technology can generate 3 distinct but related object categories:</span></span>

* <span data-ttu-id="edcf7-110">간단 하지 않고 평면 대화방 구조를 유추 하는 간소화 된 watertight 환경 망</span><span class="sxs-lookup"><span data-stu-id="edcf7-110">Simplified watertight environment meshes that infer the planar room structure without clutter</span></span>
* <span data-ttu-id="edcf7-111">Quads를 호출 하는 배치를 위한 평면 영역</span><span class="sxs-lookup"><span data-stu-id="edcf7-111">Plane regions for placement that we call Quads</span></span>
* <span data-ttu-id="edcf7-112">노출 되는 Quads/Watertight 데이터에 맞는 [공간 매핑](spatial-mapping.md) 메시의 스냅숏입니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-112">A snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface</span></span>

![공간 매핑 메시, 레이블이 지정 된 평면 표면, watertight 메시](images/SUScenarios.png)

<span data-ttu-id="edcf7-114">이 문서는 시나리오 개요를 제공 하 고 장면 이해 및 공간 매핑 공유의 관계를 명확 하 게 설명 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-114">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span> <span data-ttu-id="edcf7-115">진행 중인 장면 이해를 확인 하려는 경우 아래 **Holograms-공간 인식** 비디오 데모 디자인을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="edcf7-115">If you'd like to see Scene Understanding in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="edcf7-116">*이 비디오는 "디자인 Holograms" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드 하 고 활용해 보세요.*</span><span class="sxs-lookup"><span data-stu-id="edcf7-116">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="edcf7-117">장면 이해로 개발</span><span class="sxs-lookup"><span data-stu-id="edcf7-117">Developing with Scene Understanding</span></span>

<span data-ttu-id="edcf7-118">이 문서에서는 런타임 및 개념을 이해 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-118">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="edcf7-119">Scene Understanding을 사용하여 개발하는 방법에 대한 설명서를 찾는 경우 다음 문서에 관심이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-119">If you're looking for documentation on how to develop with Scene Understanding, you may be interested in the following articles:</span></span>

[<span data-ttu-id="edcf7-120">Scene Understanding SDK 개요</span><span class="sxs-lookup"><span data-stu-id="edcf7-120">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="edcf7-121">샘플 GitHub 사이트에서 Scene Understanding 샘플 앱을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-121">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="edcf7-122">장면 이해 샘플</span><span class="sxs-lookup"><span data-stu-id="edcf7-122">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="edcf7-123">디바이스가 없고 장면 이해를 사용해 볼 샘플 장면에 액세스하려는 경우 샘플 자산 폴더에 다음과 같은 장면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-123">If you don't have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="edcf7-124">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="edcf7-124">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="edcf7-125">SDK)</span><span class="sxs-lookup"><span data-stu-id="edcf7-125">SDK</span></span>

<span data-ttu-id="edcf7-126">Scene Understanding을 통해 개발하는 데 대한 구체적인 세부 정보를 찾고 있는 경우 [Scene Understanding SDK 개요](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="edcf7-126">If you're looking for specific details on developing with Scene Understanding, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>

### <a name="sample"></a><span data-ttu-id="edcf7-127">샘플</span><span class="sxs-lookup"><span data-stu-id="edcf7-127">Sample</span></span>

## <a name="device-support"></a><span data-ttu-id="edcf7-128">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="edcf7-128">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="edcf7-129"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="edcf7-129"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="edcf7-130"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="edcf7-130"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="edcf7-131"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="edcf7-131"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="edcf7-132"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="edcf7-132"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="edcf7-133">장면 이해</span><span class="sxs-lookup"><span data-stu-id="edcf7-133">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="edcf7-134">✔️</span><span class="sxs-lookup"><span data-stu-id="edcf7-134">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="edcf7-135">일반 시나리오</span><span class="sxs-lookup"><span data-stu-id="edcf7-135">Common usage scenarios</span></span>

<span data-ttu-id="edcf7-136">![일반적인 공간 매핑 사용 시나리오의 그림: 배치, 폐색, 물리학 및 탐색](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="edcf7-136">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="edcf7-137">*일반적인 공간 매핑 사용 시나리오: 배치, 폐색, 물리학 및 탐색.*</span><span class="sxs-lookup"><span data-stu-id="edcf7-137">*Common spatial mapping usage scenarios: placement, occlusion, physics, and navigation.*</span></span>

<br>

<span data-ttu-id="edcf7-138">환경 인식 애플리케이션에 대한 많은 핵심 시나리오는 공간 매핑 및 장면 이해를 통해 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-138">Many of the core scenarios for environmentally aware applications can be addressed by both Spatial mapping and Scene understanding.</span></span> <span data-ttu-id="edcf7-139">이러한 핵심 시나리오에는 배치, 폐색, 물리학 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-139">These core scenarios include placement, occlusion, physics, and so on.</span></span> <span data-ttu-id="edcf7-140">장면 이해와 공간 매핑의 핵심 차이점은 최대 정확도와 구조 및 단순성의 대기 시간을 절충하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-140">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="edcf7-141">애플리케이션에 가장 낮은 대기 시간이 필요하고 액세스하려는 메시 삼각형이 필요한 경우 공간 매핑을 직접 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-141">If your application requires the lowest-latency possible and mesh triangles that only you'll want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="edcf7-142">더 높은 수준의 처리를 수행하는 경우 기능 상위 집합을 제공해야 하며 장면 이해 모델로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-142">If you're doing higher-level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="edcf7-143">장면 이해는 공간 매핑 메시의 스냅샷을 표현의 일부로 제공하므로 항상 가능한 가장 완전하고 정확한 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-143">You'll always have access to the most complete and accurate spatial mapping data possible because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation.</span></span>

<span data-ttu-id="edcf7-144">다음 섹션에서는 새로운 Scene understanding SDK의 컨텍스트에서 핵심 공간 매핑 시나리오를 다시 방문합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-144">The following sections revisit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="edcf7-145">배치</span><span class="sxs-lookup"><span data-stu-id="edcf7-145">Placement</span></span>

<span data-ttu-id="edcf7-146">장면 이해는 배치 시나리오를 간소화하도록 설계된 새로운 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-146">Scene understanding provides new constructs designed to simplify placement scenarios.</span></span> <span data-ttu-id="edcf7-147">장면에서는 홀로그램을 배치할 수 있는 평면 표면을 설명하는 SceneQuads라는 기본형을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-147">A scene can compute primitives called SceneQuads, which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="edcf7-148">SceneQuads는 배치를 중심으로 디자인 되었으며 2D 표면을 설명 하 고 해당 화면에 배치 하기 위한 API를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-148">SceneQuads have been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="edcf7-149">이전에는 삼각형 메시를 사용 하 여 배치 작업을 수행할 때 쿼드의 모든 영역을 검색 하 고 구멍 채우기/사후 처리를 수행 하 여 개체 배치를 위한 좋은 위치를 확인 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-149">Previously, when using the triangle mesh to do placement, one had to scan all areas of the quad and do hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="edcf7-150">장면 이해 런타임은 스캔 되지 않은 쿼드 영역을 유추 하 고 표면에 속하지 않는 영역을 무효화 하므로 항상 Quads에는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-150">This isn't always necessary with Quads, as the Scene understanding runtime infers which quad areas weren't scanned, and invalidate areas that aren't part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="edcf7-151">![유추를 사용 하지 않도록 설정 하 고, 스캔 한 영역에 대 한 배치 영역을 SceneQuads 합니다.](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="edcf7-151">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="edcf7-152">**이미지 #1** -유추가 사용 하지 않도록 설정 된 SceneQuads, 스캔 한 영역에 대 한 배치 영역 캡처</span><span class="sxs-lookup"><span data-stu-id="edcf7-152">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="edcf7-153">![유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="edcf7-153">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="edcf7-154">**이미지 #2** -유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-154">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="edcf7-155">응용 프로그램에서 2D 또는 3D holograms를 환경의 고정 구조에 배치 하려는 경우 배치를 위한 SceneQuads의 단순성과 편의성은 [공간 매핑](spatial-mapping.md) 메시에서이 정보를 계산 하는 것 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-155">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="edcf7-156">이 항목에 대 한 자세한 내용은 [장면 이해 SDK 참조](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="edcf7-156">For more information on this topic, see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="edcf7-157">**참고** 공간 매핑 메시에 의존 하는 레거시 배치 코드의 경우 EnableWorldMesh 설정을 설정 하 여 SceneQuads와 함께 공간 매핑 메시를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-157">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="edcf7-158">장면 이해 API가 응용 프로그램의 대기 시간 요구 사항에 맞지 않는 경우 [공간 매핑 api](spatial-mapping.md#placement)를 계속 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-158">If Scene understanding API doesn't satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="edcf7-159">폐색</span><span class="sxs-lookup"><span data-stu-id="edcf7-159">Occlusion</span></span>

<span data-ttu-id="edcf7-160">[공간 매핑 폐색](spatial-mapping.md#occlusion) 환경의 실시간 상태를 캡처하는 가장 낮은 방법으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-160">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="edcf7-161">이는 매우 동적인 장면에서 폐색을 제공 하는 데 유용할 수 있지만 여러 가지 이유로 폐색에 대 한 장면 이해를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-161">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="edcf7-162">장면 이해로 생성 된 공간 매핑 메시를 사용 하는 경우 로컬 캐시에 저장 되지 않으며 인식 Api에서 사용할 수 없는 공간 매핑에서 데이터를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-162">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that wouldn't be stored in the local cache and isn't available from the perception APIs.</span></span> <span data-ttu-id="edcf7-163">폐색에 공간 매핑을 watertight 메시와 함께 사용하면 추가 값, 특히 스캐닝되지 않은 공간 구조의 완성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-163">Using Spatial Mapping for occlusion alongside watertight meshes will provide extra value, specifically completion of unscanned room structure.</span></span>

<span data-ttu-id="edcf7-164">요구 사항으로 장면 이해의 대기 시간이 늘어날 수 있는 경우 애플리케이션 개발자는 장면 이해 watertight 메시 및 평면 표현과 함께 공간 매핑 메시를 함께 사용하는 것을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-164">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="edcf7-165">이렇게 하면 가능한 가장 현실적인 폐색 맵을 제공하는 더 미세한 비 평면 기하 도형으로 간소화된 watertight 폐색이 고갈되는 "두 세계 모두의 최상" 시나리오가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-165">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="edcf7-166">Physics</span><span class="sxs-lookup"><span data-stu-id="edcf7-166">Physics</span></span>

<span data-ttu-id="edcf7-167">장면 이해는 공간 매핑 메시가 적용되는 물리학에 대한 많은 제한 사항을 해결하기 위해 의미 체계를 사용하여 공간을 분해하는 watertight 메시를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-167">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="edcf7-168">Watertight 구조는 물리학 광선 캐스트가 항상 적중되도록 하고, 의미 체계 분해를 통해 실내 탐색을 위해 탐색 메시를 더 간단하게 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-168">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="edcf7-169">[폐색](#occlusion)섹션에 설명된 대로 EnableSceneObjectMeshes 및 EnableWorldMesh를 사용하여 장면을 만들면 가능한 가장 물리적으로 완전한 메시가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-169">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="edcf7-170">환경 메시의 watertight 속성은 적중 테스트가 적중 표면에 실패하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-170">The watertight property of the environment mesh prevents hit tests from failing to hit surfaces.</span></span> <span data-ttu-id="edcf7-171">메시 데이터는 물리학이 공간 구조뿐만 아니라 장면의 모든 개체와 상호 작용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-171">The mesh data will ensure physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="edcf7-172">탐색</span><span class="sxs-lookup"><span data-stu-id="edcf7-172">Navigation</span></span>

<span data-ttu-id="edcf7-173">의미 체계 클래스에 의해 분해되는 평면 메시는 탐색 및 경로 계획에 이상적인 구문이며 공간 [매핑 탐색](spatial-mapping.md#navigation) 개요에 설명된 많은 문제를 완화합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-173">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="edcf7-174">장면에서 계산된 SceneMesh 개체는 탐색 메시 생성이 탐색 메시 생성이 탐색할 수 있는 표면으로 제한되도록 표면 형식으로 구성 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-174">The SceneMesh objects computed in the scene are de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="edcf7-175">바닥 구조의 단순성으로 인해 Unity와 같은 3d 엔진의 동적 탐색 메시 생성은 실시간 요구 사항에 따라 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-175">Because of the floor structures' simplicity, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="edcf7-176">정확한 탐색 메시를 생성하려면 현재 사후 처리가 필요합니다. 즉, 애플리케이션은 탐색이 복잡한/테이블을 통과하지 않도록 여전히 폐색을 바닥으로 프로젝션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-176">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation doesn't pass through clutter/tables and so on.</span></span> <span data-ttu-id="edcf7-177">이를 수행 하는 가장 정확한 방법은 세계 메시 데이터를 프로젝션 하는 것입니다 .이 데이터는 장면이 EnableWorldMesh 플래그를 사용 하 여 계산 되는 경우에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-177">The most accurate way to accomplish this is to project the world mesh data, which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="edcf7-178">시각화</span><span class="sxs-lookup"><span data-stu-id="edcf7-178">Visualization</span></span>

<span data-ttu-id="edcf7-179">[공간 매핑 시각화](spatial-mapping.md#visualization) 를 사용 하 여 환경에 대 한 실시간 피드백을 제공할 수 있지만, 평면 및 watertight 개체의 단순성은 더 많은 성능과 시각적 품질을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-179">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="edcf7-180">공간 매핑을 사용 하 여 설명 하는 그림자 프로젝션 및 접지 기술은 Quads 또는 planar watertight 메시에서 제공 되는 평면 표면에서 투영 된 경우 더 보기 편 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-180">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="edcf7-181">이는 장면에서 추론을 수행 하기 때문에 철저 한 사전 검사가 최적이 아닌 환경/시나리오에서 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-181">This is especially true for environments/scenarios where thorough pre-scanning isn't optimal because the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="edcf7-182">또한 공간 매핑에서 반환 된 총 표면 수는 내부 공간 캐시에 의해 제한 되는 반면 장면 이해의 공간 매핑 메시 버전은 캐시 되지 않은 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-182">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh can access spatial mapping data that isn't cached.</span></span> <span data-ttu-id="edcf7-183">이로 인해 시각화 또는 추가 메시 처리를 위해 장면 이해는 단일 공간 보다 큰 공간에 대 한 메시 표현을 캡처하는 데 더 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-183">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="edcf7-184">EnableWorldMesh를 사용 하 여 반환 되는 세계 메시는 전체에 걸쳐 일관 된 세부 수준을 가지 며,이는 와이어 프레임으로 렌더링 되는 경우 더 많은 보기 편 시각화를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edcf7-184">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="edcf7-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="edcf7-185">See Also</span></span>

* [<span data-ttu-id="edcf7-186">장면 이해 SDK</span><span class="sxs-lookup"><span data-stu-id="edcf7-186">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="edcf7-187">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="edcf7-187">Spatial mapping</span></span>](spatial-mapping.md)