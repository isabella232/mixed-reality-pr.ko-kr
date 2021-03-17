---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603398"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> 이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다. 장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.

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

XRAnchorStore를 로드 하기 위해 플러그 인은 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에 확장 메서드를 제공 합니다.

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

이 확장 메서드를 사용 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR Plugin 샘플 장면의](../openxr-getting-started.md#hololens-2-samples)앵커-> 앵커 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인 하세요.

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](../images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 플러그 인](#tab/winxr)

> [!NOTE]
> 이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다. 장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.

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

XRAnchorStore를 로드 하기 위해 플러그 인은 XRReferencePointSubsystem (Unity 2019) 또는 XRAnchorSubsystem (Unity 2020), ARReferencePointManager/ARAnchorManager의 하위 시스템에 확장 메서드를 제공 합니다.

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

이 확장 메서드를 사용 하려면 Unity 2019에 대해 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

또는 Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

**네임 스페이스:** *UNITYENGINE. XR*<br>
**클래스:** *WorldAnchorStore*

WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다. 실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다. 일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.

이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.

1. WorldAnchorStore 가져오기
2. 세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 ID를 제공 합니다.
3. 해당 ID에서 전 세계 앵커 로드

이후 세션에 대해 holograms를 저장 하려면:

1. WorldAnchorStore 가져오기
2. ID를 지정 하 여 전 세계 앵커 저장
3. ID와 함께 세계 앵커와 관련 된 앱 데이터 저장

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore 가져오기

작업을 수행할 준비가 된 시기를 알 수 있도록 WorldAnchorStore에 대 한 참조를 유지 하려고 합니다. 비동기 호출 이므로 시작 하는 즉시 다음을 호출 합니다.

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.

### <a name="saving-a-worldanchor"></a>WorldAnchor 저장

저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다. 참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다. 이전 저장을 삭제 한 후 새 저장을 저장 합니다.

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

로드 하려면 다음을 수행 합니다.

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

저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.

### <a name="enumerating-existing-anchors"></a>기존 앵커 열거

이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a>세계 최고 규모 환경 구축

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형:** *WorldAnchor*

사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다. 사용할 수 있는 한 가지 핵심 기술은 holograms의 클러스터를 물리적 환경에서 정확 [하 게 배치 하 여](../../../design/coordinate-systems.md#spatial-anchors) 사용자가 로밍 하는 거리에 관계 없이 [해당 holograms를 다시 찾는](../../../design/coordinate-systems.md#spatial-anchor-persistence)것입니다.

Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.

### <a name="adding-a-world-anchor"></a>세계 앵커 추가

세계 앵커를 추가 하려면 `AddComponent<WorldAnchor>()` 실제 지역에서 고정 하려는 변환을 사용 하 여 game 개체에 대해를 호출 합니다.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

정말 간단하죠. 이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다. 이후 앱 세션에서이 앵커 된 위치를 다시 찾으려면 [세계 앵커 로드](#loading-a-worldanchor) 를 참조 하세요.

### <a name="removing-a-world-anchor"></a>세계 앵커 제거

GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>세계 고정 GameObject 이동

GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다. GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.

1. 세계 앵커 구성 요소 DestroyImmediate
2. GameObject 이동
3. GameObject에 새 세계 앵커 구성 요소를 추가 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability 변경 내용 처리

WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다. 이 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다. 이는 앱이 실행 되는 동안에도 변경 될 수 있습니다. Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.

Locatability 변경 내용에 대 한 알림이 표시 되는 경우:

1. OnTrackingChanged 이벤트 구독
2. 이벤트를 처리 합니다.

**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

그런 다음 이벤트를 처리 합니다.

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

경우에 따라 앵커가 즉시 배치 됩니다. 이 경우 AddComponent ()가 반환 되 면 앵커의이 isLocated 속성은 true로 설정 됩니다 <WorldAnchor> . 따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다. 깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>여러 장치에 대 한 holograms 유지

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 해당 장치가 동시에 함께 제공 되지 않는 경우에도 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.  클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.
