---
title: Unity의 공간 매핑
description: Unity 혼합 현실 앱에서 사용자를 중심으로 실제 기 하 도형에서 렌더링 및 충돌을 사용 하 고 관리 하는 방법을 알아봅니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 매핑, 렌더러, collider, 메시, 검색, 구성 요소, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: e2ef6ac43e81ff2b8e66a4bd197ea41c198a1626
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105549953"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="3090e-104">Unity의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="3090e-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="3090e-105">[공간 매핑을](../../design/spatial-mapping.md) 사용 하면 HoloLens 장치 주변의 화면을 나타내는 삼각형 메시를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="3090e-106">Placement, 폐색 및 room 분석에 surface 데이터를 사용 하 여 Unity 프로젝트에 집중 교육의 추가 백신를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="3090e-107">Unity에는 다음과 같은 방법으로 개발자에 게 노출 되는 공간 매핑에 대 한 완벽 한 지원이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="3090e-108">공간 매핑 구성 요소는 MixedRealityToolkit에서 사용할 수 있으며 공간 매핑을 시작 하기 위한 편리 하 고 빠른 경로를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="3090e-109">모든 권한을 제공 하 고 보다 정교한 응용 프로그램 관련 사용자 지정을 가능 하 게 하는 하위 수준 공간 매핑 Api</span><span class="sxs-lookup"><span data-stu-id="3090e-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="3090e-110">앱에서 공간 매핑을 사용 하려면 Appxmanifest.xml에 spatialPerception 기능을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="3090e-111">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="3090e-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3090e-112"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="3090e-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3090e-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (첫 번째 gen)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3090e-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3090e-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3090e-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3090e-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="3090e-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3090e-116">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="3090e-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="3090e-117">✔️</span><span class="sxs-lookup"><span data-stu-id="3090e-117">✔️</span></span></td>
        <td><span data-ttu-id="3090e-118">✔️</span><span class="sxs-lookup"><span data-stu-id="3090e-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="3090e-119">SpatialPerception 기능 설정</span><span class="sxs-lookup"><span data-stu-id="3090e-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="3090e-120">앱이 공간 매핑 데이터를 사용 하도록 하려면 SpatialPerception 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="3090e-121">SpatialPerception 기능을 사용 하도록 설정 하는 방법:</span><span class="sxs-lookup"><span data-stu-id="3090e-121">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="3090e-122">Unity 편집기에서 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > 플레이어)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="3090e-123">**"Windows 스토어"** 탭에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="3090e-124">" **게시 설정"** 을 확장 하 고 " **기능"** 목록에서 **"SpatialPerception"** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="3090e-125">Unity 프로젝트를 Visual Studio 솔루션으로 이미 내보낸 경우에는 새 폴더로 내보내거나 [Visual studio의 appxmanifest.xml에서이 기능](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)을 수동으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="3090e-126">공간 매핑에는 10.0.10586.0 이상의 MaxVersionTested 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="3090e-127">Visual Studio의 솔루션 탐색기에서 appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 를 선택 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="3090e-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="3090e-128">**Targetdevicefamily** 를 지정 하 고 **MaxVersionTested = "10.0.10240.0"** 를 **MaxVersionTested = "10.0.10586.0"** 로 변경 하는 줄을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="3090e-129">Appxmanifest.xml를 **저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="3090e-130">Unity의 기본 제공 공간 매핑 구성 요소 시작</span><span class="sxs-lookup"><span data-stu-id="3090e-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="3090e-131">Unity는 앱, **공간 매핑 렌더러** 및 **공간 매핑 Collider** 에 공간 매핑을 쉽게 추가 하기 위한 두 가지 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="3090e-132">공간 매핑 렌더러</span><span class="sxs-lookup"><span data-stu-id="3090e-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="3090e-133">공간 매핑 렌더러를 사용 하면 공간 매핑 메시를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity의 공간 매핑 렌더러](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="3090e-135">공간 매핑 Collider</span><span class="sxs-lookup"><span data-stu-id="3090e-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="3090e-136">공간 매핑 Collider는 공간 매핑 메시를 사용 하 여 물리학 등의 holographic 콘텐츠 (또는 문자) 조작을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity의 공간 매핑 Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="3090e-138">기본 제공 공간 매핑 구성 요소 사용</span><span class="sxs-lookup"><span data-stu-id="3090e-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="3090e-139">실제 화면을 시각화 하 고 상호 작용 하려는 경우 두 구성 요소를 모두 앱에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="3090e-140">Unity 앱에서 이러한 두 구성 요소를 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-140">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="3090e-141">공간 표면 메시를 검색할 영역의 가운데에 있는 GameObject를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="3090e-142">검사기 창에서 **구성 요소**  >  **XR**  >  **공간 매핑 Collider** 또는 **공간 매핑 렌더러** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="3090e-143">이러한 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="3090e-144">기본 제공 공간 매핑 구성 요소 이상</span><span class="sxs-lookup"><span data-stu-id="3090e-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="3090e-145">이러한 구성 요소를 사용 하면 쉽게 끌어서 놓기를 통해 공간 매핑을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="3090e-146">자세히 알아보려면 다음 두 가지 주요 경로를 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-146">When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="3090e-147">낮은 수준의 메시 처리를 수행 하려면 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3090e-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="3090e-148">높은 수준의 메시 분석을 수행 하려면 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>의 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3090e-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="3090e-149">하위 수준 Unity 공간 매핑 API 사용</span><span class="sxs-lookup"><span data-stu-id="3090e-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="3090e-150">공간 매핑 렌더러 및 공간 매핑 Collider components 제품 보다 더 많은 제어가 필요한 경우 하위 수준 공간 매핑 Api를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="3090e-151">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="3090e-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="3090e-152">**유형**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="3090e-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="3090e-153">다음 섹션에서는 공간 매핑 Api를 사용 하는 응용 프로그램에 대 한 제안 된 흐름에 대해 설명 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="3090e-154">SurfaceObserver 설정</span><span class="sxs-lookup"><span data-stu-id="3090e-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="3090e-155">공간 매핑 데이터가 필요한 각 응용 프로그램 정의 공간 영역에 대해 하나의 SurfaceObserver 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="3090e-156">SetSurfaceObserver 개체가 SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox 또는 Set지 수를 호출 하 여 데이터를 제공할 공간 영역을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="3090e-157">나중에 이러한 메서드 중 하나를 다시 호출 하 여 공간 영역을 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="3090e-158">SurfaceObserver ()를 호출 하는 경우 공간 매핑 시스템에 새 정보가 있는 SurfaceObserver의 공간 영역에 있는 각 공간 표면의 처리기를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="3090e-159">이 처리기는 하나의 공간 표면의를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="3090e-160">화면 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="3090e-160">Handling Surface Changes</span></span>

<span data-ttu-id="3090e-161">처리 하는 몇 가지 주요 사례가 있으며, 동일한 코드 경로를 사용 하 고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>
* <span data-ttu-id="3090e-162">추가 되 고 업데이트 된 경우에는 사전에서이 메시를 나타내는 GameObject를 추가 하거나 가져오고, 필요한 구성 요소를 사용 하 여 SurfaceData 구조체를 만든 다음, RequestMeshDataAsync를 호출 하 여 GameObject을 망상 데이터와 장면의 위치로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="3090e-163">제거 된 경우에는이 메시를 나타내는 GameObject를 사전에서 제거 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="3090e-164">데이터 처리 준비 완료</span><span class="sxs-lookup"><span data-stu-id="3090e-164">Handling Data Ready</span></span>

<span data-ttu-id="3090e-165">OnDataReady 처리기는 SurfaceData 개체를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="3090e-166">포함 하는 WorldAnchor, MeshFilter 및 (선택 사항) MeshCollider 개체는 연결 된 공간 표면의 최신 상태를 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="3090e-167">필요에 따라 MeshFilter 개체의 메시 멤버에 액세스 하 여 메시 데이터를 분석 및/또는 [처리](../../design/spatial-mapping.md#mesh-processing) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="3090e-168">최신 메시를 사용 하 여 공간 표면을 렌더링 하 고 (선택 사항) 물리 충돌과 raycasts에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="3090e-169">SurfaceData의 내용이 null이 아닌지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="3090e-170">업데이트 처리 시작</span><span class="sxs-lookup"><span data-stu-id="3090e-170">Start processing on updates</span></span>

<span data-ttu-id="3090e-171">SurfaceObserver ()는 모든 프레임이 아니라 지연 시 호출 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="3090e-172">상위 수준 메시 분석: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="3090e-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="3090e-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> 는 Unity의 holographic api를 기반으로 하는 holographic 개발용 유틸리티 코드의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="3090e-174">공간 이해</span><span class="sxs-lookup"><span data-stu-id="3090e-174">Spatial Understanding</span></span>

<span data-ttu-id="3090e-175">실제 세계에 holograms을 배치할 때 공간 매핑의 메시 및 surface 평면을 넘어 이동 하는 것이 좋은 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-175">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="3090e-176">배치가 procedurally 되 면 더 높은 수준의 환경 이해를 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="3090e-177">일반적으로 바닥, 천장 및 벽에 대 한 결정을 내려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="3090e-178">또한 배치 제약 조건 집합에 대해 최적화 하 여 holographic 개체에 가장 적합 한 물리적 위치를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-178">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="3090e-179">젊은 Conker 및 조각을 개발 하는 동안 Asobo 스튜디오는 방 고 지 해를 개발 하 여이 문제를 해결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-179">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="3090e-180">이러한 각 게임에는 게임 관련 요구 사항이 있지만 공유 되는 핵심 공간을 이해 하는 기술이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-180">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="3090e-181">HoloToolkit SpatialUnderstanding 라이브러리는이 기술을 캡슐화 하 여 벽에서 빈 공간을 신속 하 게 찾고, 최대값에 개체를 배치 하 고, 문자를 놓을 수 있는 개체를 배치 하 고, 수많은 기타 공간을 이해 하는 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="3090e-182">모든 소스 코드가 포함 되어 있으므로 요구 사항에 맞게 사용자 지정 하 고 커뮤니티의 개선 사항을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="3090e-183">C + + 해 찾기에 대 한 코드는 UWP dll로 래핑되어 MixedRealityToolkit 내에 포함 된 prefab의 drop을 사용 하 여 Unity에 노출 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="3090e-184">모듈 이해</span><span class="sxs-lookup"><span data-stu-id="3090e-184">Understanding Modules</span></span>

<span data-ttu-id="3090e-185">모듈에 의해 노출 되는 세 가지 기본 인터페이스에는 단순 화면 및 공간 쿼리를 위한 토폴로지, 개체 검색을 위한 모양, 개체 집합의 제약 조건 기반 배치를 위한 개체 배치 해 찾기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="3090e-186">아래에서는 이러한 각 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-186">Each of these is described below.</span></span> <span data-ttu-id="3090e-187">세 가지 기본 모듈 인터페이스 외에도, 광선 캐스팅 인터페이스를 사용 하 여 태그가 지정 된 서피스 형식을 검색 하 고 사용자 지정 watertight playspace 메시를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="3090e-188">광선 캐스팅</span><span class="sxs-lookup"><span data-stu-id="3090e-188">Ray Casting</span></span>

<span data-ttu-id="3090e-189">방 검색을 완료 한 후에는 층, 천장 및 벽 같은 표면에 대 한 레이블이 내부적으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-189">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="3090e-190">"PlayspaceRaycast" 함수는 광선이 알려진 표면과 충돌 하는 경우를 반환 하 고, 해당 하는 경우에는 "RaycastResult" 형식으로 해당 화면에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="3090e-191">내부적으로 raycast는 playspace의 계산 된 8 센티미터 제곱 voxel 표현에 대해 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-191">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="3090e-192">각 voxel에는 처리 된 토폴로지 데이터 (즉, surfels)를 포함 하는 surface 요소 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="3090e-193">교차 된 voxel 셀에 포함 된 surfels는 토폴로지 정보를 조회 하는 데 사용 되는 가장 일치 하는 항목과 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-193">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="3090e-194">이 토폴로지 데이터에는 "SurfaceTypes" 열거형의 형식으로 반환 된 레이블 및 교차 된 표면의 노출 영역이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="3090e-195">Unity 샘플에서 커서는 각 프레임을 비춥니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="3090e-196">먼저, Unity의 colliders에 대해 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="3090e-197">두 번째는 모듈의 세계 표현에 대해 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="3090e-198">마지막으로 UI 요소를 다시 한 번 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-198">And finally, again UI elements.</span></span> <span data-ttu-id="3090e-199">이 응용 프로그램에서 UI는 우선 순위, 그 다음으로 이해 결과, 마지막으로 Unity의 colliders를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="3090e-200">SurfaceType은 커서 옆에 텍스트로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="3090e-201">![표면 형식의 레이블이 커서 옆에 표시 됩니다.](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3090e-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="3090e-202">*표면 형식의 레이블이 커서 옆에 표시 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="3090e-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="3090e-203">토폴로지 쿼리</span><span class="sxs-lookup"><span data-stu-id="3090e-203">Topology Queries</span></span>

<span data-ttu-id="3090e-204">DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="3090e-205">위에서 언급 한 것 처럼 대부분의 데이터는 voxel 볼륨 내에 포함 된 surfels 내에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="3090e-206">또한 "PlaySpaceInfos" 구조체를 사용 하 여 전 세계 맞춤 (아래에 자세히 설명), 층 및 천장 높이를 포함 하 여 playspace에 대 한 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="3090e-207">추론은 바닥, 천장 및 벽을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="3090e-208">예를 들어 1-m2 노출 영역을 포함 하는 가장 크거나 가장 작은 가로 표면은 바닥으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-208">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span> 

> [!NOTE]
> <span data-ttu-id="3090e-209">검색 프로세스 중에 카메라 경로도이 프로세스에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-209">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="3090e-210">토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합은 dll을 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="3090e-211">노출 된 토폴로지 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="3090e-212">각 쿼리에는 쿼리 유형과 관련 된 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="3090e-213">다음 예에서는 사용자가 원하는 볼륨의 최소 높이 & 너비, 바닥의 최소 배치 높이 및 볼륨 앞에 있는 최소 여유 공간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="3090e-214">모든 측정이 미터 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="3090e-215">이러한 각 쿼리는 미리 할당 된 "TopologyResult" 구조체 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="3090e-216">"LocationCount" 매개 변수는 전달 된 배열의 길이를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="3090e-217">반환 값은 반환 된 위치 수를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="3090e-218">이 숫자는 전달 된 "locationCount" 매개 변수 보다 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="3090e-219">"TopologyResult"에는 반환 된 볼륨의 중심 위치, 방향 (예: 일반) 및 찾은 공간의 크기가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="3090e-220">Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-220">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="3090e-221">샘플에서는 이러한 각 쿼리에 대 한 매개 변수를 적절 한 값으로 하드 코드 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="3090e-222">더 많은 예제는 샘플 코드의 SpaceVisualizer를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3090e-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="3090e-223">셰이프 쿼리</span><span class="sxs-lookup"><span data-stu-id="3090e-223">Shape Queries</span></span>

<span data-ttu-id="3090e-224">Dll에서 shape analyzer ("ShapeAnalyzer_W")는 토폴로지 분석기를 사용 하 여 사용자가 정의한 사용자 지정 셰이프와 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-224">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="3090e-225">Unity 샘플은 셰이프 집합을 정의 하 고 셰이프 탭 내의 앱 내 쿼리 메뉴를 통해 결과를 제공 합니다. 사용자는 자신의 개체 셰이프 쿼리를 정의 하 고 응용 프로그램에 필요한 대로 해당 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="3090e-226">셰이프 분석은 가로 표면 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-226">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="3090e-227">예를 들어, 소파는 평평한 좌석 표면 및 소파 위쪽의 평면에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="3090e-228">셰이프 쿼리는 두 개의 서피스가 정렬 되 고 연결 된 특정 크기, 높이 및 가로 세로 막대의 두 표면을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="3090e-229">Api 용어를 사용 하 여 소파와 후면 위쪽은 셰이프 구성 요소 이며 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="3090e-230">Unity 샘플 (ShapeDefinition)에 정의 된 "sittable" 개체에 대 한 예제 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="3090e-231">각 셰이프 쿼리는 각각 구성 요소 제약 조건 집합과 구성 요소 간의 종속성을 나열 하는 셰이프 제약 조건 집합을 포함 하는 셰이프 구성 요소 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="3090e-232">이 예에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함 되 고 구성 요소 간의 모양 제약 조건 (구성 요소 하나만 있는 경우)이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-232">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="3090e-233">이와 대조적으로, 소파 셰이프에는 두 개의 셰이프 구성 요소와 4 개의 셰이프 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="3090e-234">구성 요소는 사용자의 구성 요소 목록에서 인덱스로 식별 됩니다 (이 예제에서는 0 및 1).</span><span class="sxs-lookup"><span data-stu-id="3090e-234">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="3090e-235">래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들기 위해 Unity 모듈에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="3090e-236">구성 요소 및 모양 제약 조건의 전체 목록은 "ShapeComponentConstraint"의 "SpatialUnderstandingDll" 및 "ShapeConstraint" 구조체에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="3090e-237">![이 화면에서 사각형 모양을 찾았습니다.](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3090e-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="3090e-238">*이 화면에서 사각형 모양을 찾았습니다.*</span><span class="sxs-lookup"><span data-stu-id="3090e-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="3090e-239">개체 배치 해 찾기</span><span class="sxs-lookup"><span data-stu-id="3090e-239">Object Placement Solver</span></span>

<span data-ttu-id="3090e-240">개체 배치 해결 기를 사용 하 여 개체를 배치할 실제 방에 있는 이상적인 위치를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="3090e-241">개체 규칙과 제약 조건이 지정 된 경우 가장 적합 한 위치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="3090e-242">또한 개체 쿼리는 "Solver_RemoveObject" 또는 "Solver_RemoveAllObjects" 호출을 통해 개체가 제거 될 때까지 지속 되어 제한 된 다중 개체 배치를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="3090e-243">개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="3090e-244">쿼리를 실행 하려면 다음 API를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-244">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="3090e-245">이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="3090e-246">C # 래퍼는 생성 도우미 함수를 제공 하 여 규칙 및 제약 조건 생성을 용이 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="3090e-247">배치 정의에는 쿼리 유형 즉, 다음 중 하나를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-247">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="3090e-248">각 배치 형식에는 해당 형식에 고유한 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="3090e-249">"ObjectPlacementDefinition" 구조체에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="3090e-250">예를 들어 바닥에서 개체를 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="3090e-251">공용 정적 ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) 배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="3090e-252">규칙을 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-252">Rules cannot be violated.</span></span> <span data-ttu-id="3090e-253">그러면 형식 및 규칙을 충족 하는 가능한 배치 위치가 최적의 배치 위치를 선택 하기 위해 제약 조건 집합에 대해 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="3090e-254">제공 된 정적 생성 함수를 통해 각 규칙 및 제약 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="3090e-255">아래에는 규칙 및 제약 조건 생성 함수 예제가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="3090e-256">아래 개체 배치 쿼리는 이전에 배치 된 다른 개체와 실내 가운데 근처에서 절반 측정기 큐브를 표면의 가장자리에 배치 하는 위치를 찾고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="3090e-257">성공 하면 배치 위치, 차원 및 방향을 포함 하는 "ObjectPlacementResult" 구조가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="3090e-258">또한 배치가 배치 된 개체의 내부 목록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="3090e-259">이후 배치 쿼리에서는이 개체를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="3090e-260">Unity 샘플의 "LevelSolver 찾기 .cs" 파일에는 더 많은 예제 쿼리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="3090e-261">![개체 배치 결과](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3090e-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="3090e-262">*그림 3: 파란 상자에 카메라 위치 규칙을 사용 하 여 바닥 쿼리를 수행 하는 세 위치의 결과*</span><span class="sxs-lookup"><span data-stu-id="3090e-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="3090e-263">수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치를 해결 하는 경우에는 먼저 필요에 따라 공간을 찾을 수 있는 확률을 최대화 하기 위해 필수적인 개체와 큼 개체를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="3090e-264">배치 순서는 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-264">Placement order is important.</span></span> <span data-ttu-id="3090e-265">개체 배치를 찾을 수 없는 경우 제한 된 구성으로 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="3090e-266">여러 방 구성에서 기능을 지원 하려면 대체 (fallback) 구성 집합이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="3090e-267">대화방 스캔 프로세스</span><span class="sxs-lookup"><span data-stu-id="3090e-267">Room Scanning Process</span></span>

<span data-ttu-id="3090e-268">HoloLens에서 제공 하는 공간 매핑 솔루션은 문제 공간의 전체 영역에 대 한 요구 사항을 충족 하기에 충분히 제네릭으로 설계 되었지만 공간 파악 모듈은 두 가지 특정 게임의 요구 사항을 지원 하도록 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="3090e-269">해당 솔루션은 아래에 요약 된 특정 프로세스 및 가정 집합을 중심으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="3090e-270">사용자 기반 플레이 공간 "그리기"-검사 단계 중에 사용자가 재생 속도를 이동 하 고 표시 하 여 영역을 효과적으로 그려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="3090e-271">생성 된 메시는이 단계에서 사용자 의견을 제공 하는 데 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="3090e-272">실내 홈 또는 office 설정 – 쿼리 함수는 직각으로 평면 및 벽 주위에 디자인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="3090e-273">소프트 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-273">This is a soft limitation.</span></span> <span data-ttu-id="3090e-274">그러나 검사 단계 중에 주 축 분석을 완료 하 여 주 및 보조 축을 따라 메시 공간 분할을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="3090e-275">포함 된 SpatialUnderstanding 파일은 검사 단계 프로세스를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="3090e-276">다음 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-276">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="3090e-277">"SpatialUnderstanding" 동작으로 구동 되는 검색 흐름은 InitScan을 호출한 다음 각 프레임을 UpdateScan 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="3090e-278">통계 쿼리가 적절 한 검사를 보고 하면 사용자는 요청을 눌러 RequestFinish를 호출 하 여 검사 단계의 끝을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="3090e-279">UpdateScan는 해당 반환 값이 dll 처리를 완료 했음을 나타내는 경우에만 계속 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-279">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="3090e-280">메시 이해</span><span class="sxs-lookup"><span data-stu-id="3090e-280">Understanding Mesh</span></span>

<span data-ttu-id="3090e-281">Dll 이해는 내부적으로 playspace를 8 센티미터 크기의 voxel 큐브 그리드로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-281">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="3090e-282">검색의 초기 부분에서 주 구성 요소 분석을 완료 하 여 방의 축을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="3090e-283">내부적으로 이러한 축에 맞춰진 voxel 공간을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="3090e-284">메시는 거의 매 초 마다 voxel 볼륨에서 isosurface를 추출 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="3090e-285">![Voxel 볼륨에서 생성 된 메시 생성](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="3090e-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="3090e-286">*Voxel 볼륨에서 생성 된 메시 생성*</span><span class="sxs-lookup"><span data-stu-id="3090e-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3090e-287">문제 해결</span><span class="sxs-lookup"><span data-stu-id="3090e-287">Troubleshooting</span></span>
* <span data-ttu-id="3090e-288">[SpatialPerception](#setting-the-spatialperception-capability) 기능을 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="3090e-289">추적이 손실 되 면 다음 OnSurfaceChanged 이벤트는 모든 메시를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="3090e-290">Mixed Reality Toolkit의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="3090e-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="3090e-291">Mixed Reality Toolkit v 2에서 공간 매핑을 사용 하는 방법에 대 한 자세한 내용은 MRTK docs의 <a href="/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">공간 인식 섹션</a> 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3090e-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3090e-292">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="3090e-292">Next Development Checkpoint</span></span>

<span data-ttu-id="3090e-293">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-293">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="3090e-294">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-294">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3090e-295">Text</span><span class="sxs-lookup"><span data-stu-id="3090e-295">Text</span></span>](text-in-unity.md)

<span data-ttu-id="3090e-296">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-296">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3090e-297">공유 환경</span><span class="sxs-lookup"><span data-stu-id="3090e-297">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="3090e-298">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3090e-298">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3090e-299">참조</span><span class="sxs-lookup"><span data-stu-id="3090e-299">See also</span></span>
* [<span data-ttu-id="3090e-300">좌표계</span><span class="sxs-lookup"><span data-stu-id="3090e-300">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="3090e-301">Unity의 좌표계</span><span class="sxs-lookup"><span data-stu-id="3090e-301">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="3090e-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="3090e-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="3090e-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="3090e-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="3090e-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="3090e-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="3090e-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. 범위</a></span><span class="sxs-lookup"><span data-stu-id="3090e-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>