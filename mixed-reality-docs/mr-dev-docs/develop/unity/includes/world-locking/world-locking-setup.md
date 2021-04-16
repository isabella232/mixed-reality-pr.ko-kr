---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528761"
---
# <a name="world-locking-tools-recommended"></a>[세계 잠금 도구 (권장)](#tab/wlt)

새 혼합 현실 기능 도구를 사용 하 여 세계 잠금 도구를 설치 하는 것이 좋습니다. 아래 링크에서 Mixed Reality 기능 도구를 다운로드 한 후에는 **세계 잠금 도구** 섹션에서 최신 버전의 **WLT Core** 를 선택 합니다.

![전역 잠금 도구를 선택 하 여 혼합 현실 기능 도구 기능 선택 창](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [MR 기능 도구를 사용 하 여 세계 잠금 도구 설치](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>자동 설치

프로젝트를 사용할 준비가 되 면 **혼합 현실 도구 키트 > 유틸리티 > 세계 잠금 도구** 에서 장면 구성 유틸리티를 실행 합니다.

![혼합 현실 도구 키트 메뉴가 선택 된 Unity 편집기](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> 장면 구성 유틸리티는 언제 든 지 다시 실행할 수 있습니다. 예를 들어 AR 대상이 레거시에서 XR SDK로 변경 된 경우 다시 실행 해야 합니다. 장면이 이미 올바르게 구성 된 경우 유틸리티를 실행 해도 아무런 효과가 없습니다.

### <a name="visualizers"></a>시각화 도우미

초기 개발 중에 시각화 도우미를 추가 하는 것이 WLT가 설치 되어 제대로 작동 하는지 확인 하는 데 도움이 될 수 있습니다. 프로덕션 성능에 대해 제거할 수 있으며, 어떤 이유로 든 더 이상 필요 하지 않은 경우에는 시각화 도우미 제거 유틸리티를 사용 합니다. 시각화 도우미에 대 한 자세한 내용은 [도구 설명서](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)에서 찾을 수 있습니다.

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다. Aranchors의 ARAnchors에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 Aranchors 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요. 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>세계 최고 규모 환경 구축

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형:** *WorldAnchor*

사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다. 사용할 수 있는 한 가지 핵심 기술은 holograms의 클러스터를 물리적 환경에서 정확 [하 게 배치 하 여](../../../../design/coordinate-systems.md#spatial-anchors) 사용자가 로밍 하는 거리에 관계 없이 [해당 holograms를 다시 찾는](../../../../design/coordinate-systems.md#spatial-anchor-persistence)것입니다.

Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.

### <a name="adding-a-world-anchor"></a>세계 앵커 추가

세계 앵커를 추가 하려면 `AddComponent<WorldAnchor>()` 실제 지역에서 고정 하려는 변환을 사용 하 여 game 개체에 대해를 호출 합니다.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

이것으로 끝입니다. 이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다. 이후 앱 세션에서이 앵커 된 위치를 다시 찾으려면 [세계 앵커 로드](#loading-a-worldanchor) 를 참조 하세요.

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