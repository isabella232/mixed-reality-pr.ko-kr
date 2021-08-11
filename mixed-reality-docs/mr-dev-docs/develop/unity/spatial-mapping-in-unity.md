---
title: Unity의 공간 매핑
description: Unity 혼합 현실 앱에서 사용자를 중심으로 실제 기 하 도형에서 렌더링 및 충돌을 사용 하 고 관리 하는 방법을 알아봅니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 매핑, 렌더러, collider, 메시, 스캔, 구성 요소, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, 혼합 현실 Toolkit
ms.openlocfilehash: 4c8d0598898b4717a624562340918f968bd26f1fcde72258907e4fce73bd8489
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223108"
---
# <a name="spatial-mapping-in-unity"></a>Unity의 공간 매핑

[공간 매핑을](../../design/spatial-mapping.md) 사용 하면 HoloLens 장치 주위에서 화면을 나타내는 삼각형 메시를 검색할 수 있습니다. Placement, 폐색 및 room 분석에 surface 데이터를 사용 하 여 Unity 프로젝트에 집중 교육의 추가 백신를 제공할 수 있습니다.

Unity에는 다음과 같은 방법으로 개발자에 게 노출 되는 공간 매핑에 대 한 완벽 한 지원이 포함 되어 있습니다.

1. 공간 매핑 구성 요소는 MixedRealityToolkit에서 사용할 수 있으며 공간 매핑을 시작 하기 위한 편리 하 고 빠른 경로를 제공 합니다.
2. 모든 권한을 제공 하 고 보다 정교한 응용 프로그램 관련 사용자 지정을 가능 하 게 하는 하위 수준 공간 매핑 Api

앱에서 공간 매핑을 사용 하려면 Appxmanifest.xml에 spatialPerception 기능을 설정 해야 합니다.

## <a name="device-support"></a>디바이스 지원

| 기능 | [HoloLens (첫 번째 gen)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [몰입형 헤드셋](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| 공간 매핑 | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 기능 설정

앱이 공간 매핑 데이터를 사용 하도록 하려면 SpatialPerception 기능을 사용 하도록 설정 해야 합니다.

SpatialPerception 기능을 사용 하도록 설정 하는 방법:

1. Unity 편집기에서 **"플레이어 설정"** 창 (편집 > Project 설정 > 플레이어)을 엽니다.
2. **"Windows 저장소"** 탭에서 선택 합니다.
3. " **설정 게시"** 를 확장 하 고 " **기능"** 목록에서 **"SpatialPerception"** 기능을 확인 합니다.

> [!NOTE]
> Unity 프로젝트를 Visual Studio 솔루션으로 이미 내보낸 경우에는 새 폴더로 내보내거나 [Visual Studio appxmanifest.xml에서이 기능](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)을 수동으로 설정 해야 합니다.

공간 매핑에는 10.0.10586.0 이상의 MaxVersionTested 필요 합니다.

1. Visual Studio에서 솔루션 탐색기의 appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 를 선택 **합니다.**
2. **Targetdevicefamily** 를 지정 하 고 **MaxVersionTested = "10.0.10240.0"** 를 **MaxVersionTested = "10.0.10586.0"** 로 변경 하는 줄을 찾습니다.
3. Appxmanifest.xml를 **저장** 합니다.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity의 기본 제공 공간 매핑 구성 요소 시작

Unity는 앱, **공간 매핑 렌더러** 및 **공간 매핑 Collider** 에 공간 매핑을 쉽게 추가 하기 위한 두 가지 구성 요소를 제공 합니다.

### <a name="spatial-mapping-renderer"></a>공간 매핑 렌더러

공간 매핑 렌더러를 사용 하면 공간 매핑 메시를 시각화할 수 있습니다.

![Unity의 공간 매핑 렌더러](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>공간 매핑 Collider

공간 매핑 Collider는 공간 매핑 메시를 사용 하 여 물리학 등의 holographic 콘텐츠 (또는 문자) 조작을 허용 합니다.

![Unity의 공간 매핑 Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 사용

실제 화면을 시각화 하 고 상호 작용 하려는 경우 두 구성 요소를 모두 앱에 추가할 수 있습니다.

Unity 앱에서 이러한 두 구성 요소를 사용 하려면 다음을 수행 합니다.

1. 공간 표면 메시를 검색할 영역의 가운데에 있는 GameObject를 선택 합니다.
2. 검사기 창에서 **구성 요소**  >  **XR**  >  **공간 매핑 Collider** 또는 **공간 매핑 렌더러** 를 추가 합니다.

이러한 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>에서 확인할 수 있습니다.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 이상

이러한 구성 요소를 사용 하면 쉽게 끌어서 놓기를 통해 공간 매핑을 시작할 수 있습니다.  자세히 알아보려면 다음 두 가지 주요 경로를 살펴볼 수 있습니다.

* 낮은 수준의 메시 처리를 수행 하려면 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 하세요.
* 높은 수준의 메시 분석을 수행 하려면 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>의 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>하위 수준 Unity 공간 매핑 API 사용

공간 매핑 렌더러 및 공간 매핑 Collider components 제품 보다 더 많은 제어가 필요한 경우 하위 수준 공간 매핑 Api를 사용 합니다.

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

다음 섹션에서는 공간 매핑 Api를 사용 하는 응용 프로그램에 대 한 제안 된 흐름에 대해 설명 했습니다.

### <a name="set-up-the-surfaceobservers"></a>SurfaceObserver 설정

공간 매핑 데이터가 필요한 각 응용 프로그램 정의 공간 영역에 대해 하나의 SurfaceObserver 개체를 인스턴스화합니다.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

SetSurfaceObserver 개체가 SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox 또는 Set지 수를 호출 하 여 데이터를 제공할 공간 영역을 지정 합니다. 나중에 이러한 메서드 중 하나를 다시 호출 하 여 공간 영역을 다시 정의할 수 있습니다.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

SurfaceObserver ()를 호출 하는 경우 공간 매핑 시스템에 새 정보가 있는 SurfaceObserver의 공간 영역에 있는 각 공간 표면의 처리기를 제공 해야 합니다. 이 처리기는 하나의 공간 표면의를 수신 합니다.

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>화면 변경 내용 처리

처리 하는 몇 가지 주요 사례가 있으며, 동일한 코드 경로를 사용 하 고 제거할 수 있습니다.

* 추가 되 고 업데이트 된 경우에는 사전에서이 메시를 나타내는 GameObject를 추가 하거나 가져오고, 필요한 구성 요소를 사용 하 여 SurfaceData 구조체를 만든 다음, RequestMeshDataAsync를 호출 하 여 GameObject을 망상 데이터와 장면의 위치로 채웁니다.
* 제거 된 경우에는이 메시를 나타내는 GameObject를 사전에서 제거 하 고 삭제 합니다.

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
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
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

### <a name="handling-data-ready"></a>데이터 처리 준비 완료

OnDataReady 처리기는 SurfaceData 개체를 수신 합니다. 포함 하는 WorldAnchor, MeshFilter 및 (선택 사항) MeshCollider 개체는 연결 된 공간 표면의 최신 상태를 반영 합니다. 필요에 따라 MeshFilter 개체의 메시 멤버에 액세스 하 여 메시 데이터를 분석 및/또는 [처리](../../design/spatial-mapping.md#mesh-processing) 합니다. 최신 메시를 사용 하 여 공간 표면을 렌더링 하 고 (선택 사항) 물리 충돌과 raycasts에 사용 합니다. SurfaceData의 내용이 null이 아닌지 확인 하는 것이 중요 합니다.

### <a name="start-processing-on-updates"></a>업데이트 처리 시작

SurfaceObserver ()는 모든 프레임이 아니라 지연 시 호출 되어야 합니다.

```cs
void Start ()
{
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

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>상위 수준 메시 분석: 공간 이해

> [!CAUTION]
> 공간 이해는 [장면 이해](../../design/scene-understanding.md)를 위해 더 이상 사용 되지 않습니다.

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> 는 Unity의 holographic api를 기반으로 하는 holographic 개발용 유틸리티 코드의 컬렉션입니다.

### <a name="spatial-understanding"></a>공간 이해

실제 세계에 holograms을 배치할 때 공간 매핑의 메시 및 surface 평면을 넘어 이동 하는 것이 좋은 경우가 많습니다. 배치가 procedurally 되 면 더 높은 수준의 환경 이해를 수행 하는 것이 좋습니다. 일반적으로 바닥, 천장 및 벽에 대 한 결정을 내려야 합니다. 또한 배치 제약 조건 집합에 대해 최적화 하 여 holographic 개체에 가장 적합 한 물리적 위치를 결정할 수 있습니다.

젊은 Conker 및 조각을 개발 하는 동안 Asobo 스튜디오는 방 고 지 해를 개발 하 여이 문제를 해결 했습니다. 이러한 각 게임에는 게임 관련 요구 사항이 있지만 공유 되는 핵심 공간을 이해 하는 기술이 있습니다. HoloToolkit SpatialUnderstanding 라이브러리는이 기술을 캡슐화 하 여 벽에서 빈 공간을 신속 하 게 찾고, 최대값에 개체를 배치 하 고, 문자를 놓을 수 있는 개체를 배치 하 고, 수많은 기타 공간을 이해 하는 쿼리를 수행할 수 있습니다.

모든 소스 코드가 포함 되어 있으므로 요구 사항에 맞게 사용자 지정 하 고 커뮤니티의 개선 사항을 공유할 수 있습니다. C + + 해 찾기에 대 한 코드는 UWP dll로 래핑되어 MixedRealityToolkit 내에 포함 된 prefab의 drop을 사용 하 여 Unity에 노출 되었습니다.

### <a name="understanding-modules"></a>모듈 이해

모듈에 의해 노출 되는 세 가지 기본 인터페이스에는 단순 화면 및 공간 쿼리를 위한 토폴로지, 개체 검색을 위한 모양, 개체 집합의 제약 조건 기반 배치를 위한 개체 배치 해 찾기가 있습니다. 아래에서는 이러한 각 방법에 대해 설명합니다. 세 가지 기본 모듈 인터페이스 외에도, 광선 캐스팅 인터페이스를 사용 하 여 태그가 지정 된 서피스 형식을 검색 하 고 사용자 지정 watertight playspace 메시를 복사할 수 있습니다.

### <a name="ray-casting"></a>광선 캐스팅

방 검색을 완료 한 후에는 층, 천장 및 벽 같은 표면에 대 한 레이블이 내부적으로 생성 됩니다. 함수는 광선이 `PlayspaceRaycast` 알려진 표면과 충돌 하는 경우를 반환 하 고, 해당 하는 경우의 형태로 해당 화면에 대 한 정보를 반환 합니다 `RaycastResult` .

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

내부적으로 raycast는 playspace의 계산 된 8 센티미터 제곱 voxel 표현에 대해 계산 됩니다. 각 voxel에는 처리 된 토폴로지 데이터 (즉, surfels)를 포함 하는 surface 요소 집합이 포함 되어 있습니다. 교차 된 voxel 셀에 포함 된 surfels는 토폴로지 정보를 조회 하는 데 사용 되는 가장 일치 하는 항목과 비교 됩니다. 이 토폴로지 데이터에는 "SurfaceTypes" 열거형의 형식으로 반환 된 레이블 및 교차 된 표면의 노출 영역이 포함 됩니다.

Unity 샘플에서 커서는 각 프레임을 비춥니다. 먼저, Unity의 colliders에 대해 합니다. 두 번째는 모듈의 세계 표현에 대해 이해 합니다. 마지막으로 UI 요소를 다시 한 번 더 합니다. 이 응용 프로그램에서 UI는 우선 순위, 그 다음으로 이해 결과, 마지막으로 Unity의 colliders를 가져옵니다. SurfaceType은 커서 옆에 있는 텍스트로 보고됩니다.

![표면 유형은 커서 옆에 레이블이 지정됩니다.](images/su-raycastresults-300px.jpg)<br>
*표면 유형은 커서 옆에 레이블이 지정됩니다.*

### <a name="topology-queries"></a>토폴로지 쿼리

DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리합니다. 위에서 설명한 것처럼 대부분의 데이터는 복셀 볼륨 내에 포함된 파셸 내에 저장됩니다. 또한 "PlaySpaceInfos" 구조는 세계 맞춤(아래의 자세한 내용), 바닥 및 최대 높이를 포함하여 플레이스페이스에 대한 정보를 저장하는 데 사용됩니다. 추론은 바닥, 최면 및 벽 결정에 사용됩니다. 예를 들어 1m2보다 큰 가장 크고 가장 낮은 가로 표면은 바닥으로 간주됩니다.

> [!NOTE]
> 검색 프로세스 중에 카메라 경로도 이 프로세스에 사용됩니다.

토폴로지 관리자가 노출하는 쿼리의 하위 집합은 dll을 통해 노출됩니다. 노출된 토폴로지 쿼리는 다음과 같습니다.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

각 쿼리에는 쿼리 유형에 한정된 매개 변수 집합이 있습니다. 다음 예제에서 사용자는 원하는 볼륨의 최소 높이 & 너비, 바닥 위의 최소 배치 높이 및 볼륨 앞의 최소 제한량을 지정합니다. 모든 측정값은 미터 단위입니다.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

이러한 각 쿼리는 "TopologyResult" 구조체의 미리 할당된 배열을 취합니다. "locationCount" 매개 변수는 전달된 배열의 길이를 지정합니다. 반환 값은 반환된 위치의 수를 보고합니다. 이 숫자는 전달된 "locationCount" 매개 변수보다 크지 않습니다.

"TopologyResult"에는 반환된 볼륨의 중심 위치, 방향(즉, 보통) 및 찾은 공간의 크기가 포함됩니다.

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
> Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결됩니다. 샘플에서는 이러한 각 쿼리에 대한 매개 변수를 적절한 값으로 하드 코딩합니다. 자세한 예제는 샘플 코드의 SpaceVisualizer.cs를 참조하세요.

### <a name="shape-queries"></a>셰이프 쿼리

dll에서 도형 분석기("ShapeAnalyzer_W")는 토폴로지 분석기를 사용하여 사용자가 정의한 사용자 지정 셰이프와 일치합니다. Unity 샘플은 셰이프 집합을 정의하고 셰이프 탭 내의 앱 내 쿼리 메뉴를 통해 결과를 노출합니다. 사용자가 자신의 개체 셰이프 쿼리를 정의하고 애플리케이션에서 필요에 따라 해당 쿼리를 사용할 수 있도록 하기 위한 것입니다.

셰이프 분석은 가로 표면에서만 작동합니다. 예를 들어, 평상시 표면과 평면 상단의 후면에 의해 정의되는 경우를 예로 들어 보겠습니다. 셰이프 쿼리는 두 표면이 정렬되고 연결된 특정 크기, 높이 및 가로 세로 범위의 두 표면을 찾습니다. API 용어를 사용하면 couch seat 및 back top은 셰이프 구성 요소이고 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.

Unity 샘플(ShapeDefinition.cs)에서 "sittable" 개체에 대해 정의된 예제 쿼리는 다음과 같습니다.

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

각 셰이프 쿼리는 구성 요소 간의 의존도를 나열하는 일련의 구성 요소 제약 조건 및 셰이프 제약 조건 집합이 있는 셰이프 구성 요소 집합으로 정의됩니다. 이 예제에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함되며 구성 요소 간에 셰이프 제약 조건이 없습니다(하나의 구성 요소만 있기 때문에).

반면, couch 셰이프에는 두 개의 셰이프 구성 요소와 4개의 셰이프 제약 조건이 있습니다. 구성 요소는 사용자의 구성 요소 목록에서 해당 인덱스로 식별됩니다(이 예제에서는 0과 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들 수 있는 Unity 모듈에서 제공됩니다. 구성 요소 및 셰이프 제약 조건의 전체 목록은 "ShapeComponentConstraint" 및 "ShapeConstraint" 구조체 내의 "SpatialUnderstandingDll.cs"에서 찾을 수 있습니다.

![사각형 모양이 이 화면에 있습니다.](images/su-shapequery-300px.jpg)<br>
*사각형 모양이 이 화면에 있습니다.*

### <a name="object-placement-solver"></a>개체 배치 해결기

개체 배치 해결기를 사용하여 개체를 배치할 실제 공간의 이상적인 위치를 식별할 수 있습니다. 해결기에서 개체 규칙 및 제약 조건이 지정된 경우 가장 적합한 위치를 찾습니다. 또한 개체 쿼리는 "Solver_RemoveObject" 또는 "Solver_RemoveAllObjects" 호출을 통해 개체가 제거될 때까지 유지되어 제한된 다중 개체 배치를 허용합니다. 개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성됩니다. 쿼리를 실행하려면 다음 API를 사용합니다.

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

이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 가져옵니다. C# 래퍼는 규칙 및 제약 조건을 쉽게 만들 수 있는 구조 도우미 함수를 제공합니다. 배치 정의에는 쿼리 형식, 즉 다음 중 하나가 포함됩니다.

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

각 배치 형식에는 형식에 고유한 매개 변수 집합이 있습니다. "ObjectPlacementDefinition" 구조체에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함되어 있습니다. 예를 들어 개체를 층으로 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 형식 및 규칙을 충족하는 가능한 배치 위치는 최적의 배치 위치를 선택하기 위해 제약 조건 집합에 대해 최적화됩니다. 제공된 정적 생성 함수에서 각 규칙 및 제약 조건을 만들 수 있습니다. 예제 규칙 및 제약 조건 구성 함수가 아래에 제공됩니다.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

아래 개체 배치 쿼리는 이전에 배치된 다른 개체와는 다른 공간의 중심 부근에서 반 미터 큐브를 표면 가장자리에 배치할 위치를 찾습니다.

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

성공하면 배치 위치, 차원 및 방향을 포함하는 "ObjectPlacementResult" 구조체가 반환됩니다. 또한 배치된 개체의 dll 내부 목록에 배치가 추가됩니다. 후속 배치 쿼리는 이 개체를 고려합니다. Unity 샘플의 "LevelSolver.cs" 파일에는 더 많은 예제 쿼리가 포함되어 있습니다.

![개체 배치 결과](images/su-objectplacement-1000px.jpg)<br>
*그림 3: 파란색 상자는 카메라 위치 규칙에서 벗어난 바닥 쿼리의 3개 위치 결과*

수준 또는 애플리케이션 시나리오에 필요한 여러 개체의 배치 위치를 해결하는 경우 먼저 공백을 찾을 수 있는 확률을 최대화하기 위해 필수 및 대형 개체를 해결합니다. 배치 순서가 중요합니다. 개체 배치를 찾을 수 없는 경우 덜 제한된 구성을 시도합니다. 대체 구성 집합을 갖는 것은 여러 실내 구성에서 기능을 지원하는 데 중요합니다.

### <a name="room-scanning-process"></a>실내 검색 프로세스

HoloLens 제공하는 공간 매핑 솔루션은 전체 문제 공간 영역의 요구 사항을 충족할 만큼 충분히 일반적이도록 설계되었지만 공간 이해 모듈은 두 가지 특정 게임의 요구를 지원하도록 빌드되었습니다. 솔루션은 특정 프로세스와 가정 집합을 중심으로 구성되며 아래에 요약되어 있습니다.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

사용자 기반 플레이스페이스 "그리기" – 스캔 단계에서 사용자는 재생 속도를 이동하고 둘러보며 포함해야 하는 영역을 효과적으로 그렸습니다. 생성된 메시는 이 단계에서 사용자 피드백을 제공하는 데 중요합니다. 실내 홈 또는 사무실 설정 – 쿼리 함수는 직각으로 평면 표면과 벽 주위에 설계되었습니다. 소프트 제한 사항입니다. 그러나 검색 단계 중에 주 축과 보조 축을 따라 메시 공간을 최적화하기 위해 기본 축 분석이 완료됩니다. 포함된 SpatialUnderstanding.cs 파일은 검사 단계 프로세스를 관리합니다. 다음 함수를 호출합니다.

```txt
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

"SpatialUnderstanding" 동작에 의해 구동되는 검색 흐름은 InitScan을 호출한 다음, UpdateScan 각 프레임을 호출합니다. 통계 쿼리가 적절한 검사를 보고하면 사용자는 RequestFinish를 호출하여 검사 단계의 끝을 나타내는 airtap을 할 수 있습니다. UpdateScan은 해당 반환 값이 dll이 처리를 완료했음을 나타내기 전까지 계속 호출됩니다.

### <a name="understanding-mesh"></a>메시 이해

이해 dll은 내부적으로 플레이스페이스를 8cm 크기의 복셀 큐브 그리드로 저장합니다. 검사의 초기 부분에서는 기본 구성 요소 분석을 완료하여 방의 축을 확인합니다. 내부적으로 이러한 축에 맞춰진 복셀 공간을 저장합니다. 메시는 복셀 볼륨에서 isosurface를 추출하여 약 1초마다 생성됩니다.

![복셀 볼륨에서 생성된 메시 생성](images/su-custommesh.jpg)<br>
*복셀 볼륨에서 생성된 메시 생성*

## <a name="troubleshooting"></a>문제 해결

* [SpatialPerception](#setting-the-spatialperception-capability) 기능을 설정해야 합니다.
* 추적이 손실되면 다음 OnSurfaceChanged 이벤트가 모든 메시를 제거합니다.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit 공간 매핑

Mixed Reality Toolkit 공간 매핑 사용에 대한 자세한 내용은 MRTK 문서의 [공간 인식 섹션을](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 참조하세요.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 따라가는 경우 MRTK 핵심 구성 요소에 대해 알아보세요. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [좌표계](../../design/coordinate-systems.md)
* [Unity의 좌표계](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
