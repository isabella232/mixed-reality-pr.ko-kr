---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719704"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="3321a-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="3321a-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="3321a-102">**XRAnchorStore** 이라는 추가 API를 사용 하면 세션 간에 앵커가 지속 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="3321a-103">XRAnchorStore는 장치에 저장 된 앵커를 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="3321a-104">Unity 장면의 **Aranchors** 에서 앵커를 유지 하거나, 저장소에서 새 **aranchors** 로 로드 하거나, 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="3321a-105">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="3321a-106">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
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
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="3321a-107">XRAnchorStore를 로드 하기 위해 플러그 인은 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="3321a-108">이 확장 메서드를 사용 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="3321a-109">앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR 플러그 인 샘플 장면](../openxr-getting-started.md#hololens-2-samples)에서 앵커-> 앵커 샘플 GameObject 및 AnchorsSample 스크립트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="3321a-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="3321a-112">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="3321a-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="3321a-113">**XRAnchorStore** 라는 API를 사용 하면 세션 간에 앵커가 지속 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="3321a-114">XRAnchorStore는 장치에 저장 된 앵커를 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="3321a-115">Unity 장면의 **Aranchors** 에서 앵커를 유지 하거나, 저장소에서 새 **aranchors** 로 로드 하거나, 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="3321a-116">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="3321a-117">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
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

<span data-ttu-id="3321a-118">XRAnchorStore를 로드 하기 위해 플러그 인은 XRReferencePointSubsystem (Unity 2019) 또는 XRAnchorSubsystem (Unity 2020), ARReferencePointManager/ARAnchorManager의 하위 시스템에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="3321a-119">이 확장 메서드를 사용 하려면 Unity 2019에 대해 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="3321a-120">또는 Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="3321a-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="3321a-121">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="3321a-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="3321a-122">**WorldAnchorStore** 는 응용 프로그램의 여러 인스턴스에서 holograms 특정 실제 위치에 유지 되는 holographic 환경을 만드는 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="3321a-123">사용자는 언제 든 지 개별 holograms을 고정 하 고, 나중에 앱의 여러 사용에 대 한 동일한 지점에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="3321a-124">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="3321a-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="3321a-125">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="3321a-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="3321a-126">WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="3321a-127">실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="3321a-128">일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="3321a-129">이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="3321a-130">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="3321a-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="3321a-131">세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 ID를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="3321a-132">해당 ID에서 전 세계 앵커 로드</span><span class="sxs-lookup"><span data-stu-id="3321a-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="3321a-133">이후 세션에 대해 holograms를 저장 하려면:</span><span class="sxs-lookup"><span data-stu-id="3321a-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="3321a-134">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="3321a-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="3321a-135">ID를 지정 하 여 전 세계 앵커 저장</span><span class="sxs-lookup"><span data-stu-id="3321a-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="3321a-136">ID와 함께 세계 앵커와 관련 된 앱 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="3321a-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="3321a-137">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="3321a-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="3321a-138">작업을 수행할 준비가 된 시기를 알 수 있도록 WorldAnchorStore에 대 한 참조를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="3321a-139">비동기 호출 이므로 시작 하는 즉시 다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="3321a-140">이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="3321a-141">이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="3321a-142">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="3321a-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="3321a-143">저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="3321a-144">참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="3321a-145">이전 저장을 삭제 한 후 새 저장을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="3321a-146">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="3321a-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="3321a-147">로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-147">And to load:</span></span>

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

<span data-ttu-id="3321a-148">저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="3321a-149">기존 앵커 열거</span><span class="sxs-lookup"><span data-stu-id="3321a-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="3321a-150">이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="3321a-151">여러 장치에 대 한 holograms 유지</span><span class="sxs-lookup"><span data-stu-id="3321a-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="3321a-152"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 해당 장치가 동시에 함께 제공 되지 않는 경우에도 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="3321a-153">클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="3321a-154">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="3321a-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="3321a-155">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3321a-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
