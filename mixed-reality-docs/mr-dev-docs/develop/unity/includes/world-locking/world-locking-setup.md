---
ms.openlocfilehash: 047a77259d78ba8ea68002a5142080971900e305
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244315"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools(권장)](#tab/wlt)

새 Mixed Reality 기능 도구를 사용하여 World Locking Tools를 설치하는 것이 좋습니다. 아래 링크에서 Mixed Reality 기능 도구를 다운로드했으면 **World Locking Tools** 섹션에서 최신 버전의 **WLT Core를** 선택합니다.

![World Locking Tools가 선택된 Mixed Reality 기능 도구 기능 선택 창](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [MR 기능 도구를 사용하여 World Locking Tools 설치](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>자동화된 설정

프로젝트를 진행할 준비가 되면 Mixed Reality > World Locking Tools 에서 장면 구성 **유틸리티를 실행합니다.**

![Mixed Reality Toolkit 메뉴가 선택된 Unity 편집기](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> 장면 구성 유틸리티는 언제든지 다시 실행될 수 있습니다. 예를 들어 AR 대상이 레거시에서 XR SDK로 변경된 경우 다시 실행해야 합니다. 장면을 이미 제대로 구성한 경우 유틸리티를 실행해도 아무 효과가 없습니다.

### <a name="visualizers"></a>시각화 도우미

초기 개발 중에 시각화 도우미를 추가하면 WLT가 제대로 설정되고 작동하는지 확인하는 데 도움이 될 수 있습니다. 프로덕션 성능을 위해 또는 어떤 이유로든 더 이상 필요하지 않은 경우 시각화 도우미 제거 유틸리티를 사용하여 제거할 수 있습니다. 시각화 도우미에 대한 자세한 내용은 [도구 설명서](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)에서 확인할 수 있습니다.

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본 앵커 기능을 제공합니다. ARFoundation의 ARAnchors에 대한 기본 사항 알아보려면 [AR Anchor Manager에 대한 ARFoundation Manual(ARFoundation Manual for ARFoundation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)Manager)을 방문하세요. 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>세계적 규모의 환경 구축

**네임스페이스:** *UnityEngine.XR.WSA*<br>
**유형:** *WorldAnchor*

사용자가 5미터를 초과하여 배회할 수 있는 HoloLens 진정한 **세계적 규모의 환경의** 경우 공간 규모 경험에 사용되는 기술 외에 새로운 기술이 필요합니다. 사용자가 얼마나 멀리 로밍했는지에 관계없이 실제 세계에서 홀로그램 클러스터를 정확하게 잠그는 [공간 앵커를](../../../../design/coordinate-systems.md#spatial-anchors) 만든 다음, [이후 세션에서 홀로그램을 다시 찾는](../../../../design/coordinate-systems.md#spatial-anchor-persistence)것이 한 가지 핵심 기술입니다.

Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가하여 공간 앵커를 만듭니다.

### <a name="adding-a-world-anchor"></a>World Anchor 추가

세계 앵커를 추가하려면 `AddComponent<WorldAnchor>()` 실제 세계에서 앵커하려는 변환을 사용하여 게임 개체에 대해 를 호출합니다.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

이것으로 끝입니다. 이제 이 게임 개체가 실제 세계의 현재 위치에 고정됩니다. Unity 세계 좌표가 시간이 지남에 따라 약간 조정되어 물리적 맞춤을 확인할 수 있습니다. 향후 앱 세션에서 이 앵커 위치를 다시 찾으려면 [세계 앵커 로드를](#loading-a-worldanchor) 참조합니다.

### <a name="removing-a-world-anchor"></a>World Anchor 제거

GameObject를 실제 세계 위치에 더 이상 잠그지 않고 이 프레임을 이동하지 않으려면 World Anchor 구성 요소에서 Destroy를 호출하면 됩니다.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

GameObject 이 프레임을 이동하려면 DestroyImmediate를 대신 호출해야 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>World Anchored GameObject 이동

World Anchor가 있는 동안에는 GameObject를 이동할 수 없습니다. GameObject 이 프레임을 이동해야 하는 경우 다음을 수행해야 합니다.

1. DestroyImmediate the World Anchor component
2. GameObject 이동
3. GameObject에 새 World Anchor 구성 요소를 추가합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>찾기 기능 변경 처리

WorldAnchor는 한 시점에 실제 세계에서 찾기가 불가능할 수 있습니다. 이 경우 Unity는 앵커된 개체의 변환을 업데이트하지 않습니다. 앱이 실행되는 동안에도 변경이 가능합니다. 위치 변경을 처리하지 못하면 개체가 전 세계의 올바른 물리적 위치에 나타나지 않습니다.

찾기 기능 변경에 대한 알림을 받도록 하려면 다음을 수행합니다.

1. OnTrackingChanged 이벤트 구독
2. 이벤트 처리

**OnTrackingChanged** 이벤트는 기본 공간 앵커가 찾기 가능한 상태와 위치 불가 상태 간에 변경될 때마다 호출됩니다.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

그런 다음 이벤트를 처리합니다.

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

앵커가 즉시 배치되는 경우도 있습니다. 이 경우 AddComponent()가 반환될 때 앵커의 isLocated 속성이 true로 <WorldAnchor> 설정됩니다. 따라서 OnTrackingChanged 이벤트는 트리거되지 않습니다. 클린 패턴은 앵커를 연결한 후 초기 IsLocated 상태로 OnTrackingChanged 처리기를 호출하는 것입니다.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```