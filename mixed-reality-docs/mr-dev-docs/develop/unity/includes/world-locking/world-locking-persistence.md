---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528780"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="68aa1-101">세계 잠금 도구 (권장)</span><span class="sxs-lookup"><span data-stu-id="68aa1-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="68aa1-102">기본적으로 세계 잠금 도구는 전체 세션에서 실제 세계를 기준으로 Unity의 좌표계를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="68aa1-103">즉, 응용 프로그램을 종료 하 고 다시 실행 한 후에도 홀로그램이 물리적 환경에서 동일 하 게 표시 되도록 하기 위해 홀로그램은 동일한 포즈를 다시 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Unity 검사기의 세계 잠금 컨텍스트 구성 요소](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="68aa1-105">응용 프로그램에 더 세밀 하 게 제어 해야 하는 경우 검사기에서 **자동 저장** 및 **자동 로드** 를 사용 하지 않도록 설정 하 고, [설명서의 지 속성 섹션](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)에 설명 된 대로 스크립트에서 지 속성을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="68aa1-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="68aa1-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="68aa1-107">**XRAnchorStore** 이라는 추가 API를 사용 하면 세션 간에 앵커가 지속 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="68aa1-108">XRAnchorStore는 장치에 저장 된 앵커를 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="68aa1-109">Unity 장면의 **Aranchors** 에서 앵커를 유지 하거나, 저장소에서 새 **aranchors** 로 로드 하거나, 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="68aa1-110">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="68aa1-111">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="68aa1-112">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="68aa1-112">Namespaces</span></span>

<span data-ttu-id="68aa1-113">**Unity 2020 및 OpenXR**:</span><span class="sxs-lookup"><span data-stu-id="68aa1-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="68aa1-114">또는 **Unity 2019/2020 + WINDOWS XR 플러그 인**:</span><span class="sxs-lookup"><span data-stu-id="68aa1-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="68aa1-115">public 메서드</span><span class="sxs-lookup"><span data-stu-id="68aa1-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="68aa1-116">앵커 저장소 참조 가져오기</span><span class="sxs-lookup"><span data-stu-id="68aa1-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="68aa1-117">**Unity 2020 및 OpenXR** 를 사용 하 여 XRAnchorStore를 로드 하려면 XRAnchorSubsystem의 ARAnchorManager 하위 시스템에 확장 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="68aa1-118">**Unity 2019/2020 및 WINDOWS XR 플러그** 인을 사용 하 여 XRAnchorStore를 로드 하려면 XRReferencePointSubsystem (unity 2019) 또는 XRAnchorSubsystem (unity 2020)의 확장 메서드 (ARReferencePointManager/ARAnchorManager의 하위 시스템)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="68aa1-119">앵커 저장소 로드</span><span class="sxs-lookup"><span data-stu-id="68aa1-119">Loading an anchor store</span></span>

<span data-ttu-id="68aa1-120">**Unity 2020 및 OpenXR** 에서 앵커 저장소를 로드 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서이 저장소에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="68aa1-121">또는 **Unity 2019/2020 및 WINDOWS XR 플러그** 인을 사용 하 여 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="68aa1-122">앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR 플러그 인 샘플 장면](../../openxr-getting-started.md#hololens-2-samples)에서 앵커-> 앵커 샘플 GameObject 및 AnchorsSample 스크립트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="68aa1-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](../../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="68aa1-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="68aa1-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="68aa1-126">**WorldAnchorStore** 는 응용 프로그램의 여러 인스턴스에서 holograms 특정 실제 위치에 유지 되는 holographic 환경을 만드는 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="68aa1-127">사용자는 언제 든 지 개별 holograms을 고정 하 고, 나중에 앱의 여러 사용에 대 한 동일한 지점에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="68aa1-128">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="68aa1-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="68aa1-129">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="68aa1-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="68aa1-130">WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="68aa1-131">실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="68aa1-132">일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="68aa1-133">이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="68aa1-134">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="68aa1-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="68aa1-135">세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 ID를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="68aa1-136">해당 ID에서 전 세계 앵커 로드</span><span class="sxs-lookup"><span data-stu-id="68aa1-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="68aa1-137">이후 세션에 대해 holograms를 저장 하려면:</span><span class="sxs-lookup"><span data-stu-id="68aa1-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="68aa1-138">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="68aa1-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="68aa1-139">ID를 지정 하 여 전 세계 앵커 저장</span><span class="sxs-lookup"><span data-stu-id="68aa1-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="68aa1-140">ID와 함께 세계 앵커와 관련 된 앱 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="68aa1-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="68aa1-141">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="68aa1-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="68aa1-142">작업을 수행할 준비가 된 시기를 알 수 있도록 WorldAnchorStore에 대 한 참조를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="68aa1-143">비동기 호출 이므로 시작 하는 즉시 다음을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="68aa1-144">이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="68aa1-145">이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="68aa1-146">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="68aa1-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="68aa1-147">저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="68aa1-148">참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="68aa1-149">이전 저장을 삭제 한 후 새 저장을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="68aa1-150">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="68aa1-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="68aa1-151">로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-151">And to load:</span></span>

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

<span data-ttu-id="68aa1-152">저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="68aa1-153">기존 앵커 열거</span><span class="sxs-lookup"><span data-stu-id="68aa1-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="68aa1-154">이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="68aa1-155">여러 장치에 대 한 holograms 유지</span><span class="sxs-lookup"><span data-stu-id="68aa1-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="68aa1-156"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 해당 장치가 동시에 함께 제공 되지 않는 경우에도 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="68aa1-157">클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="68aa1-158">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="68aa1-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="68aa1-159">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68aa1-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
