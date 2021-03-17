---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603398"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="6ebae-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="6ebae-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="6ebae-102">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="6ebae-103">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="6ebae-104">XRAnchorStore를 로드 하기 위해 플러그 인은 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="6ebae-105">이 확장 메서드를 사용 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="6ebae-106">앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR Plugin 샘플 장면의](../openxr-getting-started.md#hololens-2-samples)앵커-> 앵커 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ebae-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="6ebae-109">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="6ebae-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="6ebae-110">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="6ebae-111">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="6ebae-112">XRAnchorStore를 로드 하기 위해 플러그 인은 XRReferencePointSubsystem (Unity 2019) 또는 XRAnchorSubsystem (Unity 2020), ARReferencePointManager/ARAnchorManager의 하위 시스템에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="6ebae-113">이 확장 메서드를 사용 하려면 Unity 2019에 대해 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="6ebae-114">또는 Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="6ebae-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="6ebae-115">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="6ebae-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="6ebae-116">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="6ebae-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="6ebae-117">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="6ebae-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="6ebae-118">WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="6ebae-119">실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="6ebae-120">일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="6ebae-121">이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="6ebae-122">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="6ebae-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="6ebae-123">세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 ID를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="6ebae-124">해당 ID에서 전 세계 앵커 로드</span><span class="sxs-lookup"><span data-stu-id="6ebae-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="6ebae-125">이후 세션에 대해 holograms를 저장 하려면:</span><span class="sxs-lookup"><span data-stu-id="6ebae-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="6ebae-126">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="6ebae-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="6ebae-127">ID를 지정 하 여 전 세계 앵커 저장</span><span class="sxs-lookup"><span data-stu-id="6ebae-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="6ebae-128">ID와 함께 세계 앵커와 관련 된 앱 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="6ebae-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="6ebae-129">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="6ebae-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="6ebae-130">작업을 수행할 준비가 된 시기를 알 수 있도록 WorldAnchorStore에 대 한 참조를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="6ebae-131">비동기 호출 이므로 시작 하는 즉시 다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="6ebae-132">이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="6ebae-133">이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="6ebae-134">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="6ebae-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="6ebae-135">저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="6ebae-136">참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="6ebae-137">이전 저장을 삭제 한 후 새 저장을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="6ebae-138">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="6ebae-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="6ebae-139">로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-139">And to load:</span></span>

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

<span data-ttu-id="6ebae-140">저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="6ebae-141">기존 앵커 열거</span><span class="sxs-lookup"><span data-stu-id="6ebae-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="6ebae-142">이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="6ebae-143">세계 최고 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="6ebae-143">Building a world-scale experience</span></span>

<span data-ttu-id="6ebae-144">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="6ebae-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="6ebae-145">**유형:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="6ebae-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="6ebae-146">사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="6ebae-147">사용할 수 있는 한 가지 핵심 기술은 holograms의 클러스터를 물리적 환경에서 정확 [하 게 배치 하 여](../../../design/coordinate-systems.md#spatial-anchors) 사용자가 로밍 하는 거리에 관계 없이 [해당 holograms를 다시 찾는](../../../design/coordinate-systems.md#spatial-anchor-persistence)것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="6ebae-148">Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="6ebae-149">세계 앵커 추가</span><span class="sxs-lookup"><span data-stu-id="6ebae-149">Adding a World Anchor</span></span>

<span data-ttu-id="6ebae-150">세계 앵커를 추가 하려면 `AddComponent<WorldAnchor>()` 실제 지역에서 고정 하려는 변환을 사용 하 여 game 개체에 대해를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="6ebae-151">정말 간단하죠.</span><span class="sxs-lookup"><span data-stu-id="6ebae-151">That's it!</span></span> <span data-ttu-id="6ebae-152">이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="6ebae-153">이후 앱 세션에서이 앵커 된 위치를 다시 찾으려면 [세계 앵커 로드](#loading-a-worldanchor) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ebae-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="6ebae-154">세계 앵커 제거</span><span class="sxs-lookup"><span data-stu-id="6ebae-154">Removing a World Anchor</span></span>

<span data-ttu-id="6ebae-155">GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="6ebae-156">GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="6ebae-157">세계 고정 GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="6ebae-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="6ebae-158">GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="6ebae-159">GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="6ebae-160">세계 앵커 구성 요소 DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="6ebae-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="6ebae-161">GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="6ebae-161">Move the GameObject</span></span>
3. <span data-ttu-id="6ebae-162">GameObject에 새 세계 앵커 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="6ebae-163">Locatability 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="6ebae-163">Handling Locatability Changes</span></span>

<span data-ttu-id="6ebae-164">WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="6ebae-165">이 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="6ebae-166">이는 앱이 실행 되는 동안에도 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-166">This also can change while an app is running.</span></span> <span data-ttu-id="6ebae-167">Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="6ebae-168">Locatability 변경 내용에 대 한 알림이 표시 되는 경우:</span><span class="sxs-lookup"><span data-stu-id="6ebae-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="6ebae-169">OnTrackingChanged 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="6ebae-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="6ebae-170">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-170">Handle the event</span></span>

<span data-ttu-id="6ebae-171">**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="6ebae-172">그런 다음 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="6ebae-173">경우에 따라 앵커가 즉시 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="6ebae-174">이 경우 AddComponent ()가 반환 되 면 앵커의이 isLocated 속성은 true로 설정 됩니다 <WorldAnchor> .</span><span class="sxs-lookup"><span data-stu-id="6ebae-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="6ebae-175">따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="6ebae-176">깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="6ebae-177">여러 장치에 대 한 holograms 유지</span><span class="sxs-lookup"><span data-stu-id="6ebae-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="6ebae-178"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 해당 장치가 동시에 함께 제공 되지 않는 경우에도 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="6ebae-179">클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="6ebae-180">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6ebae-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="6ebae-181">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ebae-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
