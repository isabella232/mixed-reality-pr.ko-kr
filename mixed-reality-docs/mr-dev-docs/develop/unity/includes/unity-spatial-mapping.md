---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905716"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>공간 인식 시스템

MRTK의 [공간 인식 시작](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 가이드에서 다양 한 공간 메시 관찰자를 설정 하는 방법에 대 한 정보를 확인 합니다.

장치 관찰자에 대 한 자세한 내용은 [장치에 대 한 메시 관찰자 구성](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) 가이드를 참조 하세요.

장면 이해 관찰자에 대 한 자세한 내용은 관찰자의 [관찰자 이해](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) 가이드를 참조 하세요.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

Unity의 ARFoundation은 공간 메시의 기본 제공 가상화를 위한 ARMeshManager 구성 요소를 제공 합니다. 사용에 대 한 자세한 내용은 [Unity 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) 를 참조 하세요.

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Unity의 [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) 직접 작업 하는 경우 사용에 대 한 자세한 내용은 [unity 설명서](https://docs.unity3d.com/Manual/xrsdk-meshing.html) 를 참조 하세요.

## <a name="windows-xr-plugin"></a>Windows XR 플러그 인

Windows XR 플러그 인은 경계 구를 설정 하거나 기본 플랫폼 메시 표현에 액세스 하는 등의 XRMeshSubsystem를 구성 하는 몇 가지 추가 확장 메서드를 제공 합니다. 이러한 다른 모든 확장 프로그램은 [Unity 설명서에서](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)찾을 수 있습니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity의 기본 제공 공간 매핑 구성 요소 시작

Unity는 앱, **공간 매핑 렌더러** 및 **공간 매핑 Collider** 에 공간 매핑을 쉽게 추가 하기 위한 두 가지 구성 요소를 제공 합니다.

### <a name="spatial-mapping-renderer"></a>공간 매핑 렌더러

공간 매핑 렌더러를 사용 하면 공간 매핑 메시를 시각화할 수 있습니다.

![Unity의 공간 매핑 렌더러](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>공간 매핑 Collider

공간 매핑 Collider는 공간 매핑 메시를 사용 하 여 물리학 등의 holographic 콘텐츠 (또는 문자) 조작을 허용 합니다.

![Unity의 공간 매핑 Collider](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 사용

실제 화면을 시각화 하 고 상호 작용 하려는 경우 두 구성 요소를 모두 앱에 추가할 수 있습니다.

Unity 앱에서 이러한 두 구성 요소를 사용 하려면 다음을 수행 합니다.

1. 공간 표면 메시를 검색할 영역의 가운데에 있는 GameObject를 선택 합니다.
2. 검사기 창에서 **구성 요소**  >  **XR**  >  **공간 매핑 Collider**   또는 **공간 매핑 렌더러** 를 추가 합니다.

이러한 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>에서 확인할 수 있습니다.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 이상

이러한 구성 요소를 사용 하면 쉽게 끌어서 놓기를 통해 공간 매핑을 시작할 수 있습니다. 자세히 알아보려면 다음 두 가지 주요 경로를 살펴볼 수 있습니다.

* 낮은 수준의 메시 처리를 수행 하려면 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 하세요.
* 높은 수준의 메시 분석을 수행 하려면 [MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)의 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요.

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

SetvstststvstvstvstvstvstvSurfaceObserver, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox 또는 setv을 호출 하 여 각 개체가 데이터를 제공 하는 공간 지역을 지정 이러한 메서드 중 하나를 다시 호출 하 여 나중에 공간 영역을 다시 정의할 수 있습니다.

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

을 처리 하는 몇 가지 주요 사례가 있습니다 .이는 동일한 코드 경로를 사용 하 고 제거할 수 있습니다.

* 추가 되 고 업데이트 된 경우에는 사전에서이 메시를 나타내는 GameObject를 추가 하거나 가져옵니다. 필요한 구성 요소를 사용 하 여 SurfaceData 구조체를 만든 다음 RequestMeshDataAsync를 호출 하 여 GameObject를 메시 데이터로 채운 다음 장면에 배치 합니다.
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

OnDataReady 처리기는 SurfaceData 개체를 수신 합니다. 포함 하는 WorldAnchor, MeshFilter 및 (선택 사항) MeshCollider 개체는 연결 된 공간 표면의 최신 상태를 반영 합니다. 필요에 따라 MeshFilter 개체의 메시 멤버에 액세스 하 여 메시 데이터를 분석 및/또는 [처리](../../../design/spatial-mapping.md#mesh-processing) 합니다. 최신 메시를 사용 하 여 공간 표면을 렌더링 하 고 (선택 사항) 물리 충돌과 raycasts에 사용 합니다. SurfaceData의 내용이 null이 아닌지 확인 하는 것이 중요 합니다.

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
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
