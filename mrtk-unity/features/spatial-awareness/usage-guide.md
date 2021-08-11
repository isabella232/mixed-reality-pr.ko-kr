---
title: UsingGuide
description: 에서는 공간 인식 시스템을 프로그래밍 방식으로 구성하는 주요 메커니즘 및 API를 설명합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204125"
---
# <a name="configuring-mesh-observers-via-code"></a>코드를 통해 메시 관찰자 구성

이 문서에서는 [공간 인식 시스템](spatial-awareness-getting-started.md) 및 관련 Mesh *Observer* 데이터 공급자를 프로그래밍 방식으로 구성하는 몇 가지 주요 메커니즘 및 API에 대해 설명합니다.

## <a name="accessing-mesh-observers"></a>메시 관찰자 액세스

인터페이스를 구현하는 Mesh Observer 클래스는 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 공간 인식 시스템에 플랫폼별 메시 데이터를 제공합니다. 공간 인식 프로필에서 여러 관찰자를 구성할 수 있습니다.

공간 인식 시스템의 데이터 공급자에 액세스하는 것은 대부분 다른 Mixed Reality Toolkit 서비스와 동일합니다. API를 통해 액세스하려면 공간 인식 서비스를 인터페이스로 캐스팅해야 합니다. [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) `GetDataProvider<T>` 그러면 런타임에 Mesh Observer 개체에 직접 액세스하는 데 활용할 수 있습니다.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`도우미는 아래와 같이 이 액세스 패턴을 간소화합니다.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>메시 관찰 시작 및 중지

공간 인식 시스템을 처리할 때 가장 일반적인 작업 중 하나는 런타임에 기능을 동적으로 해제/켜는 것입니다. 이 작업은 및 API를 통해 관찰자별로 [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) 수행됩니다.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

이 코드 기능은 공간 인식 시스템을 통해 직접 액세스를 통해 간소화할 수도 있습니다.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>모든 메시 관찰 시작 및 중지

일반적으로 애플리케이션에서 모든 메시 관찰을 시작/중지하는 것이 편리합니다. 이는 유용한 공간 인식 시스템 API 및 를 통해 달성할 수 [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) 있습니다.

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>메시 열거 및 액세스

관찰자별로 메시에 액세스한 다음, API를 통해 메시 관찰자에게 알려진 메시를 열거할 수 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 있습니다.

편집기에서 실행하는 경우 를 사용하여 개체를 자산 파일에 저장할 수 [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) `Mesh` 있습니다.

디바이스에서 실행하는 경우 데이터를 모델 파일 형식으로 직렬화하는 데 사용할 수 있는 많은 커뮤니티 및 저장소 플러그 `MeshFilter` 인이 있습니다([OBJ 예제](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>공간 메시 표시 및 숨기기

아래 샘플 코드를 사용하여 프로그래밍 방식으로 메시를 숨기/표시할 수 있습니다.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>메시 관찰 이벤트 등록

구성 요소는 를 구현한 `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` 다음 공간 인식 시스템에 등록하여 메시 관찰 이벤트를 받을 수 있습니다.

`DemoSpatialMeshHandler`(Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) 스크립트는 Mesh Observer 이벤트를 수신 대기하기 위한 유용한 예제 및 시작점입니다.

이는 *DemoSpatialMeshHandler* 스크립트 및 Mesh Observation 이벤트 수신 대기의 간단한 예입니다.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>추가 정보

- [공간 인식 시작](spatial-awareness-getting-started.md)
- [공간 인식 메시 관찰자 구성](configuring-spatial-awareness-mesh-observer.md)
- [공간 인식 API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
