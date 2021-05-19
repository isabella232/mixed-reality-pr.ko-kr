---
title: 공간 인식 Data Provider 만들기
description: MRTK에서 사용자 지정 데이터 공급자를 만드는 방법을 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145156"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="40544-104">공간 인식 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="40544-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="40544-105">공간 인식 시스템은 응용 프로그램에 실제 환경에 대 한 데이터를 제공 하기 위한 확장 가능한 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="40544-106">새 하드웨어 플랫폼에 대 한 지원을 추가 하거나 새로운 형식의 공간 인식 데이터를 추가 하려면 사용자 지정 데이터 공급자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="40544-107">이 문서에서는 공간 인식 시스템에 대해 공간 관찰자 라고도 하는 [사용자 지정 데이터 공급자](../../architecture/systems-extensions-providers.md)를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="40544-108">여기에 표시 된 예제 코드는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [편집기에서 3d 메시 데이터를 로드 하](spatial-object-mesh-observer.md)는 데 유용 하 게 사용할 수 있는 클래스 구현에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="40544-109">이 예제에서 사용 되는 전체 소스 코드는 폴더에 있습니다 `Assets/MRTK/Providers/ObjectMeshObserver` .</span><span class="sxs-lookup"><span data-stu-id="40544-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="40544-110">네임 스페이스 및 폴더 구조</span><span class="sxs-lookup"><span data-stu-id="40544-110">Namespace and folder structure</span></span>

<span data-ttu-id="40544-111">데이터 공급자는 다음 두 가지 방법 중 하나로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="40544-112">타사 추가 기능</span><span class="sxs-lookup"><span data-stu-id="40544-112">Third party add-ons</span></span>
1. <span data-ttu-id="40544-113">Microsoft Mixed Reality Toolkit의 일부</span><span class="sxs-lookup"><span data-stu-id="40544-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="40544-114">새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="40544-115">새 [ *기능 요청* 유형 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)를 만들어 제안을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="40544-116">타사 추가 기능</span><span class="sxs-lookup"><span data-stu-id="40544-116">Third party add-on</span></span>

<span data-ttu-id="40544-117">**네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="40544-117">**Namespace**</span></span>

<span data-ttu-id="40544-118">데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="40544-119">네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="40544-120">추가 기능을 생성 하는 회사 이름</span><span class="sxs-lookup"><span data-stu-id="40544-120">Company name producing the add-on</span></span>
- <span data-ttu-id="40544-121">기능 영역</span><span class="sxs-lookup"><span data-stu-id="40544-121">Feature area</span></span>

<span data-ttu-id="40544-122">예를 들어 Contoso 회사에서 만들고 제공 하는 공간 인식 데이터 공급자는 *"MixedReality"* 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="40544-123">**폴더 구조**</span><span class="sxs-lookup"><span data-stu-id="40544-123">**Folder structure**</span></span>

<span data-ttu-id="40544-124">다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![폴더 구조의 예](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="40544-126">*ContosoSpatialAwareness* 폴더에 데이터 공급자의 구현이 포함된 경우 *Editor* 폴더에는 검사기(및 다른 Unity 편집기 관련 코드)가 포함되고 *Profiles* 폴더에는 미리 만들어진 프로필 스크립팅 가능 개체가 하나 이상 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="40544-127">MRTK 제출</span><span class="sxs-lookup"><span data-stu-id="40544-127">MRTK submission</span></span>

<span data-ttu-id="40544-128">**네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="40544-128">**Namespace**</span></span>

<span data-ttu-id="40544-129">공간 인식 시스템 데이터 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출되는 경우 네임스페이스는 Microsoft.MixedReality.Toolkit(예: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver)로* 시작해야 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="40544-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="40544-130">및 코드는 MRTK/Providers(예: *MRTK/Providers/ObjectMeshObserver) 아래의* 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="40544-131">**폴더 구조**</span><span class="sxs-lookup"><span data-stu-id="40544-131">**Folder structure**</span></span>

<span data-ttu-id="40544-132">모든 코드는 MRTK/Providers(예: MRTK/Providers/ObjectMeshObserver) 아래의 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="40544-133">공간 데이터 개체 정의</span><span class="sxs-lookup"><span data-stu-id="40544-133">Define the spatial data object</span></span>

<span data-ttu-id="40544-134">공간 인식 데이터 공급자를 만드는 첫 번째 단계는 애플리케이션에 제공할 데이터 형식(예: 메시 또는 평면)을 결정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="40544-135">모든 공간 데이터 개체는 인터페이스를 구현해야 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="40544-136">Mixed Reality 도구 키트 기반은 새 데이터 공급자에서 사용하거나 확장할 수 있는 다음과 같은 공간 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="40544-137">데이터 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="40544-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="40544-138">인터페이스 및/또는 기본 클래스 상속 지정</span><span class="sxs-lookup"><span data-stu-id="40544-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="40544-139">모든 공간 인식 데이터 공급자는 공간 인식 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 시스템에 필요한 최소 기능을 지정하는 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="40544-140">MRTK 기초에는 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 이 필수 기능의 기본 구현을 제공하는 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="40544-141">[`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)인터페이스는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 클래스에서 SpatialAwarenessMesh 기능에 대한 지원을 제공한다는 것을 나타내기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="40544-142">MixedRealityDataProvider 특성 적용</span><span class="sxs-lookup"><span data-stu-id="40544-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="40544-143">공간 인식 데이터 공급자를 만드는 주요 단계는 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 특성을 클래스에 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="40544-144">이 단계에서는 공간 인식 프로필 및 이름, 폴더 경로 등에서 선택한 경우 데이터 공급자에 대한 기본 프로필 및 플랫폼을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="40544-145">IMixedRealityDataProvider 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="40544-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="40544-146">클래스가 정의되면 다음 단계는 인터페이스의 구현을 제공하는 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="40544-147">[`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)클래스를 통해 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 클래스는 메서드에 대한 빈 구현만 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="40544-148">이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="40544-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="40544-149">데이터 공급자가 구현해야 하는 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="40544-150">데이터 공급자 논리 구현</span><span class="sxs-lookup"><span data-stu-id="40544-150">Implement the data provider logic</span></span>

<span data-ttu-id="40544-151">다음 단계는 특정 데이터 공급자 인터페이스(예: )를 구현하여 데이터 공급자의 논리를 추가하는 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="40544-152">데이터 공급자의 이 부분은 일반적으로 플랫폼별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="40544-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="40544-153">관찰 변경 알림</span><span class="sxs-lookup"><span data-stu-id="40544-153">Observation change notifications</span></span>

<span data-ttu-id="40544-154">애플리케이션이 디바이스의 환경 이해 변경에 응답할 수 있도록 데이터 공급자는 인터페이스에 정의된 대로 알림 이벤트를 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="40544-155">예제의 다음 코드에서는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 메시 데이터가 추가되면 및 이벤트가 발생되는 것을 보여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="40544-156">[`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) `OnObservationUpdated` 3D 모델이 한 번만 로드되므로 클래스는 이벤트를 발생시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="40544-157">구현을 클래스 관찰 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 된 메시에 대 한 이벤트를 발생 하는 예제를 제공 `OnObservationUpdated` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="40544-158">Unity Profiler 계측 추가</span><span class="sxs-lookup"><span data-stu-id="40544-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="40544-159">성능은 혼합 현실 애플리케이션에서 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="40544-160">모든 구성 요소는 애플리케이션이 고려해야 하는 약간의 오버헤드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="40544-161">이를 위해 모든 공간 인식 데이터 공급자는 내부 루프 및 자주 활용되는 코드 경로에 Unity Profiler 계측을 포함하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="40544-162">사용자 지정 공급자를 계측할 때 MRTK에서 사용하는 패턴을 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="40544-163">프로파일러 표식 식별에 사용되는 이름은 임의로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="40544-164">MRTK는 다음 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="40544-165">"[product] className. methodName-선택 사항</span><span class="sxs-lookup"><span data-stu-id="40544-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="40544-166">사용자 지정 데이터 공급자는 추적을 분석할 때 특정 구성 요소 및 메서드를 쉽게 식별할 수 있도록 비슷한 패턴을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="40544-167">프로필 및 검사기 만들기</span><span class="sxs-lookup"><span data-stu-id="40544-167">Create the profile and inspector</span></span>

<span data-ttu-id="40544-168">혼합 현실 도구 키트에서 데이터 공급자는 [프로필](../profiles/profiles.md)을 사용 하 여 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="40544-169">프로필 정의</span><span class="sxs-lookup"><span data-stu-id="40544-169">Define the profile</span></span>

<span data-ttu-id="40544-170">프로필 콘텐츠는 데이터 공급자의 액세스 가능 속성 (예: 업데이트 간격)을 미러링합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="40544-171">각 인터페이스에 정의 된 모든 사용자 구성 가능 속성은 프로필에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="40544-172">기본 클래스는 새 데이터 공급자가 기존 공급자를 확장 하는 경우에 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="40544-173">예를 들어는를 [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 확장 [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 하 여 고객이 환경 데이터로 사용할 3d 모델을 제공할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="40544-174">`CreateAssetMenu`특성을 프로필 클래스에 적용 하 여 고객이 asset   >    >  **Mixed Reality 도구 키트**  >  **프로필** 만들기 메뉴를 사용 하 여 프로필 인스턴스를 만들 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="40544-175">검사기 구현</span><span class="sxs-lookup"><span data-stu-id="40544-175">Implement the inspector</span></span>

<span data-ttu-id="40544-176">프로필 검사기는 프로필 내용을 구성 하 고 볼 수 있는 사용자 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="40544-177">각 프로필 검사자는 클래스를 확장 해야 합니다 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .</span><span class="sxs-lookup"><span data-stu-id="40544-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="40544-178">`CustomEditor`특성은 검사기가 적용 되는 자산의 유형을 Unity에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40544-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="40544-179">어셈블리 정의 만들기</span><span class="sxs-lookup"><span data-stu-id="40544-179">Create assembly definition(s)</span></span>

<span data-ttu-id="40544-180">Mixed Reality Toolkit에서는 어셈블리 정의 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용 하 여 구성 요소 간의 종속성을 지정 하 고 컴파일 시간을 단축 하는 Unity를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="40544-181">모든 데이터 공급자와 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="40544-182">이전 예제에서 [폴더 구조](#namespace-and-folder-structure) 를 사용 하는 경우 ContosoSpatialAwareness 데이터 공급자에 대 한 두 개의. asmdef 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="40544-183">첫 번째 어셈블리 정의는 데이터 공급자에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="40544-184">이 예에서는 ContosoSpatialAwareness 라고 하 고 예제의 *ContosoSpatialAwareness* 폴더에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="40544-185">이 어셈블리 정의는 Microsoft.MixedReality.Toolkit 및 해당 어셈블리가 종속된 다른 어셈블리에 대한 종속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="40544-186">ContosoInputEditor 어셈블리 정의는 프로필 검사자와 편집기별 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="40544-187">이 파일은 편집기 코드의 루트 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="40544-188">이 예제에서 파일은 *ContosoSpatialAwareness\Editor 폴더에* 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="40544-189">이 어셈블리 정의에는 ContosoSpatialAwareness 어셈블리에 대한 참조도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40544-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="40544-190">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="40544-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="40544-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="40544-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="40544-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="40544-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="40544-193">데이터 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="40544-193">Register the data provider</span></span>

<span data-ttu-id="40544-194">데이터 공급자를 만든 후에는 애플리케이션에서 사용할 공간 인식 시스템에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![공간 개체 메시 관찰자 선택](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="40544-196">패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="40544-196">Packaging and distribution</span></span>

<span data-ttu-id="40544-197">타사 구성 요소로 배포되는 데이터 공급자에는 패키징 및 배포에 대한 구체적인 세부 정보가 개발자의 기본 설정으로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40544-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="40544-198">가장 일반적인 솔루션은 .unitypackage를 생성하고 Unity 자산 저장소를 통해 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40544-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="40544-199">Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출하고 수락하는 경우 Microsoft MRTK 팀은 이를 MRTK 제품의 일부로 패키지하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="40544-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="40544-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40544-200">See also</span></span>

- [<span data-ttu-id="40544-201">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="40544-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="40544-202">`IMixedRealitySpatialAwarenessObject` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40544-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="40544-203">`BaseSpatialAwarenessObject` 클래스</span><span class="sxs-lookup"><span data-stu-id="40544-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="40544-204">`SpatialAwarenessMeshObject` 클래스</span><span class="sxs-lookup"><span data-stu-id="40544-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="40544-205">`SpatialAwarenessPlanarObject` 클래스</span><span class="sxs-lookup"><span data-stu-id="40544-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="40544-206">`IMixedRealitySpatialAwarenessObserver` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40544-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="40544-207">`BaseSpatialObserver` 클래스</span><span class="sxs-lookup"><span data-stu-id="40544-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="40544-208">`IMixedRealitySpatialAwarenessMeshObserver` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40544-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="40544-209">`IMixedRealityDataProvider` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40544-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="40544-210">`IMixedRealityCapabilityCheck` 인터페이스</span><span class="sxs-lookup"><span data-stu-id="40544-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
