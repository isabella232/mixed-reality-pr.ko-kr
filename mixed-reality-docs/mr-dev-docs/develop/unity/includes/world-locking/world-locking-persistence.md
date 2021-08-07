---
ms.openlocfilehash: ad45cf8df4e51d17533c8e57b9ffe67738676d2af5398dd320cc86be469d5803
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208891"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools(권장)](#tab/wlt)

기본적으로 World Locking Tools는 세션 전체에서 실제 세계를 기준으로 Unity의 좌표계를 복원합니다. 즉, 애플리케이션을 종료하고 다시 실행한 후 홀로그램이 실제 세계에서 동일한 위치에 나타나도록 하려면 홀로그램이 동일한 자세만 다시 가져야 합니다.

![Unity 검사기에서 세계 잠금 컨텍스트 구성 요소](../../images/world-locking-tools-img-02.png)

애플리케이션에 더 세부적인 제어가 필요한 경우 검사기에서 **자동 저장** 및 **자동 로드를** 사용하지 않도록 설정하고 [설명서의 지속성 섹션에](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)설명된 대로 스크립트에서 관리되는 지속성을 사용할 수 있습니다.

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

**XRAnchorStore라는** 추가 API를 사용하면 세션 간에 앵커를 유지할 수 있습니다. XRAnchorStore는 디바이스에 저장된 앵커의 표현입니다. 앵커는 Unity 장면의 **ARAnchors에서** 유지되거나, 스토리지에서 새 **ARAnchors로** 로드되거나, 스토리지에서 삭제될 수 있습니다.

> [!NOTE]
> 이러한 앵커는 동일한 디바이스에 저장되고 로드됩니다. 디바이스 간 앵커 스토리지는 향후 릴리스에서 Azure Spatial Anchors 통해 지원될 예정입니다.

### <a name="namespaces"></a>네임스페이스

**Unity 2020 및 OpenXR의** 경우: 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

또는 **Unity 2019/2020 + Windows XR 플러그 인:** 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>public 메서드

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

### <a name="getting-an-anchor-store-reference"></a>앵커 저장소 참조 얻기 

**Unity 2020 및 OpenXR을** 사용하여 XRAnchorStore를 로드하려면 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에서 확장 메서드를 사용합니다.

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

**Unity 2019/2020 및 Windows XR 플러그 인을** 사용하여 XRAnchorStore를 로드하려면 ARReferencePointManager/ARAnchorManager의 하위 시스템인 XRReferencePointSubsystem(Unity 2019) 또는 XRAnchorSubsystem(Unity 2020)에서 확장 메서드를 사용합니다.

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>앵커 저장소 로드

**Unity 2020 및 OpenXR에서** 앵커 저장소를 로드하려면 다음과 같이 ARAnchorManager의 하위 시스템으로부터 앵커 저장소에 액세스합니다.

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

또는 **Unity 2019/2020 및 Windows XR 플러그 인:**

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

앵커 유지/비지속성의 전체 예제를 보려면 Mixed Reality [OpenXR 플러그 인 샘플 장면에서](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)앵커 -> Anchors 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인하세요.

![앵커 샘플이 강조 표시된 Unity 편집기에서 열린 계층 구조 패널의 스크린샷](../../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시된 Unity 편집기에서 열린 검사기 패널의 스크린샷](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore는** 홀로그램이 애플리케이션의 인스턴스에서 특정 실제 위치에 유지되는 홀로그램 환경을 만드는 핵심입니다. 그런 다음, 사용자는 원하는 위치에 개별 홀로그램을 고정하고 나중에 앱의 여러 용도에 대해 동일한 지점에서 찾을 수 있습니다.

**네임스페이스:** *UnityEngine.XR.WSA.Persistence*<br>
**클래스:** *WorldAnchorStore*

WorldAnchorStore를 사용하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다. 세션 간에 홀로그램을 실제로 유지하려면 특정 세계 앵커를 사용하는 GameObject를 별도로 추적해야 합니다. 종종 세계 앵커를 사용하여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용하여 자식 홀로그램을 고정하는 것이 타당합니다.

이전 세션에서 홀로그램을 로드하려면 다음을 수행합니다.

1. WorldAnchorStore를 얻습니다.
2. 세계 앵커의 ID를 제공하는 세계 앵커와 관련된 앱 데이터 로드
3. ID에서 세계 앵커 로드

향후 세션에 대해 홀로그램을 저장하려면 다음을 수행합니다.

1. WorldAnchorStore를 얻습니다.
2. ID를 지정하여 세계 앵커 저장
3. ID와 함께 세계 앵커와 관련된 앱 데이터 저장

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore 받기

작업을 수행할 준비가 되면 알 수 있도록 WorldAnchorStore에 대한 참조를 유지하려고 합니다. 비동기 호출이므로 시작하는 즉시 다음을 호출하려고 합니다.

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

이 경우 StoreLoaded는 WorldAnchorStore가 로드를 완료한 경우에 대한 처리기입니다.

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

이제 특정 World Anchors를 저장하고 로드하는 데 사용할 WorldAnchorStore에 대한 참조가 있습니다.

### <a name="saving-a-worldanchor"></a>WorldAnchor 저장

저장하려면 저장하려는 이름을 지정하고 저장하려는 경우 이전에 얻은 WorldAnchor에 전달하기만 하면됩니다. 참고: 동일한 문자열에 두 개의 앵커를 저장하려고 하면 실패합니다(저장소. 저장하면 false가 반환됩니다.) 새 저장을 저장하기 전에 이전 저장을 삭제합니다.

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

### <a name="loading-a-worldanchor"></a>WorldAnchor 로드

로드하려면 다음을 수행합니다.

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

저장소를 사용할 수도 있습니다. Delete() - 이전에 저장하고 저장한 앵커를 제거합니다. 이전에 저장된 모든 데이터를 제거하려면 Clear()를 선택합니다.

### <a name="enumerating-existing-anchors"></a>기존 앵커 열거

이전에 저장된 앵커를 검색하려면 GetAllIds를 호출합니다.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>여러 디바이스에 대한 홀로그램 유지

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 사용하여 로컬 WorldAnchor에서 지속성 클라우드 앵커를 만들 수 있습니다. 그러면 해당 디바이스가 동시에 함께 표시되지 않더라도 앱이 여러 HoloLens, iOS 및 Android 디바이스에서 찾을 수 있습니다.  클라우드 앵커는 영구적이므로 시간이 지남에 따라 여러 디바이스에서 동일한 물리적 위치에서 해당 앵커를 기준으로 렌더링된 콘텐츠를 볼 수 있습니다.

Unity에서 공유 환경 빌드를 시작하려면 5분 Azure Spatial Anchors Unity 빠른 시작을 사용해 <a href="/azure/spatial-anchors/unity-overview" target="_blank">보세요.</a>

Azure Spatial Anchors 실행하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.