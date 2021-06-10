---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110350010"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="4fb09-101">World Locking Tools(권장)</span><span class="sxs-lookup"><span data-stu-id="4fb09-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="4fb09-102">기본적으로 World Locking Tools는 세션 전체에서 실제 세계를 기준으로 Unity의 좌표계를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="4fb09-103">즉, 홀로그램이 애플리케이션을 종료하고 다시 실행한 후 실제 세계에서 동일한 위치에 나타나도록 하려면 홀로그램이 동일한 자세만 다시 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Unity 검사기에서 세계 잠금 컨텍스트 구성 요소](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="4fb09-105">애플리케이션에 더 세부적인 제어가 필요한 경우 검사기에서 **자동 저장** 및 **자동 로드를** 사용하지 않도록 설정하고 [설명서의 지속성 섹션에](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)설명된 대로 스크립트에서 관리되는 지속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="4fb09-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="4fb09-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="4fb09-107">**XRAnchorStore라는** 추가 API를 사용하면 세션 간에 앵커를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="4fb09-108">XRAnchorStore는 디바이스에 저장된 앵커의 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="4fb09-109">앵커는 Unity 장면의 **ARAnchors에서** 유지되거나, 스토리지에서 새 **ARAnchors로** 로드되거나, 스토리지에서 삭제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="4fb09-110">이러한 앵커는 동일한 디바이스에 저장되고 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="4fb09-111">디바이스 간 앵커 스토리지는 향후 릴리스에서 Azure Spatial Anchors 통해 지원될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="4fb09-112">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="4fb09-112">Namespaces</span></span>

<span data-ttu-id="4fb09-113">**Unity 2020 및 OpenXR의** 경우:</span><span class="sxs-lookup"><span data-stu-id="4fb09-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="4fb09-114">또는 **Unity 2019/2020 + Windows XR 플러그 인:**</span><span class="sxs-lookup"><span data-stu-id="4fb09-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="4fb09-115">public 메서드</span><span class="sxs-lookup"><span data-stu-id="4fb09-115">Public methods</span></span>

```cs 
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="4fb09-116">앵커 저장소 참조 얻기</span><span class="sxs-lookup"><span data-stu-id="4fb09-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="4fb09-117">**Unity 2020 및 OpenXR을** 사용하여 XRAnchorStore를 로드하려면 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에서 확장 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="4fb09-118">**Unity 2019/2020 및 Windows XR 플러그 인을** 사용하여 XRAnchorStore를 로드하려면 ARReferencePointManager/ARAnchorManager의 하위 시스템인 XRReferencePointSubsystem(Unity 2019) 또는 XRAnchorSubsystem(Unity 2020)에서 확장 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="4fb09-119">앵커 저장소 로드</span><span class="sxs-lookup"><span data-stu-id="4fb09-119">Loading an anchor store</span></span>

<span data-ttu-id="4fb09-120">**Unity 2020 및 OpenXR에서** 앵커 저장소를 로드하려면 다음과 같이 ARAnchorManager의 하위 시스템으로부터 앵커 저장소에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="4fb09-121">또는 **Unity 2019/2020 및 Windows XR 플러그 인:**</span><span class="sxs-lookup"><span data-stu-id="4fb09-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="4fb09-122">앵커 유지/비지속성의 전체 예제를 보려면 Mixed Reality [OpenXR 플러그 인 샘플 장면에서](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2)앵커 -> Anchors 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="4fb09-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2):</span></span>

![앵커 샘플이 강조 표시된 Unity 편집기에서 열린 계층 구조 패널의 스크린샷](../../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시된 Unity 편집기에서 열린 검사기 패널의 스크린샷](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="4fb09-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="4fb09-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="4fb09-126">**WorldAnchorStore는** 홀로그램이 애플리케이션 인스턴스에서 특정 실제 위치에 유지되는 홀로그램 환경을 만드는 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="4fb09-127">그런 다음, 사용자는 원하는 위치에 개별 홀로그램을 고정하고 나중에 앱의 여러 용도에 대해 동일한 지점에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="4fb09-128">**네임스페이스:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="4fb09-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="4fb09-129">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="4fb09-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="4fb09-130">WorldAnchorStore를 사용하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="4fb09-131">세션 간에 홀로그램을 실제로 유지하려면 특정 세계 앵커를 사용하는 GameObjects를 별도로 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="4fb09-132">종종 세계 앵커를 사용하여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용하여 자식 홀로그램을 고정하는 것이 타당합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="4fb09-133">이전 세션에서 홀로그램을 로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="4fb09-134">WorldAnchorStore를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="4fb09-135">세계 앵커의 ID를 제공하는 세계 앵커와 관련된 앱 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="4fb09-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="4fb09-136">ID에서 세계 앵커 로드</span><span class="sxs-lookup"><span data-stu-id="4fb09-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="4fb09-137">향후 세션에 대해 홀로그램을 저장하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="4fb09-138">WorldAnchorStore를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="4fb09-139">ID를 지정하여 세계 앵커 저장</span><span class="sxs-lookup"><span data-stu-id="4fb09-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="4fb09-140">ID와 함께 세계 앵커와 관련된 앱 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="4fb09-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="4fb09-141">WorldAnchorStore 얻기</span><span class="sxs-lookup"><span data-stu-id="4fb09-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="4fb09-142">작업을 수행할 준비가 되면 알 수 있도록 WorldAnchorStore에 대한 참조를 유지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="4fb09-143">비동기 호출이므로 시작하는 즉시 다음을 호출하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="4fb09-144">이 경우 StoreLoaded는 WorldAnchorStore가 로드를 완료한 경우에 대한 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="4fb09-145">이제 특정 World Anchors를 저장하고 로드하는 데 사용할 WorldAnchorStore에 대한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="4fb09-146">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="4fb09-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="4fb09-147">저장하려면 저장하려는 이름을 지정하고 저장하려는 경우 이전에 얻은 WorldAnchor에 전달하기만 하면됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="4fb09-148">참고: 동일한 문자열에 두 개의 앵커를 저장하려고 하면 실패합니다(저장소. 저장하면 false가 반환됩니다.)</span><span class="sxs-lookup"><span data-stu-id="4fb09-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="4fb09-149">새 저장을 저장하기 전에 이전 저장을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-149">Delete the previous save before saving the new one:</span></span>

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="4fb09-150">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="4fb09-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="4fb09-151">로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-151">And to load:</span></span>

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

<span data-ttu-id="4fb09-152">저장소를 사용할 수도 있습니다. Delete() - 이전에 저장하고 저장한 앵커를 제거합니다. 이전에 저장된 모든 데이터를 제거하려면 Clear()를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="4fb09-153">기존 앵커 열거</span><span class="sxs-lookup"><span data-stu-id="4fb09-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="4fb09-154">이전에 저장된 앵커를 검색하려면 GetAllIds를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="4fb09-155">여러 디바이스에 대한 홀로그램 유지</span><span class="sxs-lookup"><span data-stu-id="4fb09-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="4fb09-156"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 사용하여 로컬 WorldAnchor에서 지속형 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, iOS 및 Android 디바이스에서 찾을 수 있습니다( 해당 디바이스가 동시에 함께 표시되지 않더라도).</span><span class="sxs-lookup"><span data-stu-id="4fb09-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="4fb09-157">클라우드 앵커는 영구적이므로 시간이 지남에 따라 여러 디바이스에서 동일한 물리적 위치에서 해당 앵커를 기준으로 렌더링된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="4fb09-158">Unity에서 공유 환경 빌드를 시작하려면 5분 Azure Spatial Anchors Unity 빠른 시작을 사용해 <a href="/azure/spatial-anchors/unity-overview" target="_blank">보세요.</a></span><span class="sxs-lookup"><span data-stu-id="4fb09-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="4fb09-159">Azure Spatial Anchors 사용하여 실행하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity 에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb09-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
