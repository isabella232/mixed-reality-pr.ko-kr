---
title: Unity의 좌표계
description: Unity에서 착석, 대기, 방 크기 조정 및 세계 규모의 혼합 현실 환경을 빌드하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 좌표계, 공간 좌표계, 방향 전용, 좌표 크기 조정, 고정 배율, 방 크기 조정, 세계 크기 조정, 360도, 착석형, 서 있는, 방, 세계, 규모, 위치, 방향, Unity, 앵커, 공간 앵커, 세계 앵커, 세계 잠금, 세계 잠금, 신체 잠금, 신체 잠금, 추적 손실, 위치 가능성, 경계, 최신, 혼합 현실 헤드셋, Windows 혼합 현실 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 3372b9bd259202145fd658e225a36d2125f4a86d01eb90bc765b65918540db8b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203585"
---
# <a name="coordinate-systems-in-unity"></a>Unity의 좌표계

Windows Mixed Reality 방향 전용 및 착석 크기 조정 앱에서 실내 크기 조정 앱을 통해 다양한 환경 규모에서 앱을 지원합니다. HoloLens 사용자가 5미터를 넘어 건물 전체 층을 탐색할 수 있는 세계적 규모의 앱을 빌드할 수 있습니다.

Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 [좌표계를](../../design/coordinate-systems.md) 이해하고 앱이 대상으로 지정할 환경 크기를 선택하는 것입니다.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>방향 전용 또는 착석 규모 환경 빌드

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDevice*

**방향 전용** 또는 **좌표 크기 조정 환경을** 빌드하려면 Unity를 고정 추적 공간 형식으로 설정해야 합니다. 고정 추적 공간은 Unity의 세계 좌표계를 설정하여 [고정 참조 프레임을](../../design/coordinate-systems.md#spatial-coordinate-systems)추적합니다. 고정 추적 모드에서는 앱이 시작되면 카메라의 기본 위치 바로 앞에 배치된 콘텐츠(정방향은 -Z)가 사용자 앞에 표시됩니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**네임스페이스:** *UnityEngine.XR*<br>
**형식:** *InputTracking*

360도 비디오 뷰어와 같은 순수 **방향 전용 환경의** 경우(위치 헤드 업데이트로 인해 현상이 악화되는 경우) XR을 설정할 수 [있습니다. InputTracking.disablePositionalTracking을](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true로:

```cs
InputTracking.disablePositionalTracking = true;
```

**사용자용 크기 조정 환경의** 경우 사용자가 나중에 착석 원점이 될 수 있도록 XR을 호출할 수 [있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>스케일 업 또는 실내 규모 환경 구축

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDevice*

서 **있는 규모** 또는 **방 규모 환경의** 경우 층을 기준으로 콘텐츠를 배치해야 합니다. 첫 번째 실행 중에 설정된 사용자의 정의된 층 수준 원점 및 선택적 방 경계를 나타내는 **[공간 단계](../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 사용하여 사용자의 층을 추론합니다.

Unity가 바닥 수준에서 해당 세계 좌표계와 함께 작동하도록 하려면 Unity가 RoomScale 추적 공간 형식을 사용하고 있는지 설정하고 테스트할 수 있습니다.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* SetTrackingSpaceType이 true를 반환하는 경우 Unity는 세계 좌표계를 성공적으로 전환하여 [참조의 스테이지 프레임을](../../design/coordinate-systems.md#spatial-coordinate-systems)추적합니다.
* SetTrackingSpaceType이 false를 반환하는 경우 Unity는 사용자가 환경에서 층을 설정하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다. 잘못된 반환 값은 일반적이지 않지만, 스테이지가 다른 공간에 설정되고 사용자가 새 스테이지를 설정하지 않고 디바이스를 현재 공간으로 이동하는 경우 발생할 수 있습니다.

앱이 RoomScale 추적 공간 유형을 성공적으로 설정하면 y=0 평면에 배치된 콘텐츠가 층으로 표시됩니다. 0, 0, 0의 원점은 사용자가 방 설치 중에 깔고 있는 층의 특정 위치이며, -Z는 설치하는 동안의 정방향 방향을 나타냅니다.

**네임스페이스:** *UnityEngine.Experimental.XR*<br>
**유형:** *경계*

그런 다음 스크립트 코드에서 UnityEngine.Experimental.XR.Boundary 형식의 TryGetGeometry 메서드를 호출하여 경계 다각형을 가져올 수 있으며, 경계 형식은 TrackedArea입니다. 사용자가 경계를 정의한 경우(꼭짓점 목록을 다시 가져올 경우) 사용자가 만든 장면을 둘러 볼 수 있는 **공간 규모 환경을** 사용자에게 제공하는 것이 안전합니다.

> [!NOTE]
> 시스템은 사용자가 경계에 접근하면 자동으로 경계를 렌더링합니다. 앱은 경계 자체를 렌더링하기 위해 이 다각형을 사용할 필요가 없습니다. 그러나 사용자가 원격 보고 없이 해당 개체에 물리적으로 연결할 수 있도록 이 경계 다각형을 사용하여 장면 개체의 레이아웃을 지정할 수 있습니다.

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>세계적 규모의 환경 구축

**네임스페이스:** *UnityEngine.XR.WSA*<br>
**유형:** *WorldAnchor*

사용자가 5미터를 초과하여 배회할 수 있는 HoloLens 진정한 **세계적 규모의 환경의** 경우 공간 규모 경험에 사용되는 기술 이외에 새로운 기술이 필요합니다. 사용자가 얼마나 멀리 로밍했는지에 관계없이 실제 세계에서 홀로그램 클러스터를 정확하게 잠그는 [공간 앵커를](../../design/coordinate-systems.md#spatial-anchors) 만든 다음, [이후 세션에서 홀로그램을 다시 찾는](../../design/coordinate-systems.md#spatial-anchor-persistence)것이 한 가지 핵심 기술입니다.

Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가하여 공간 앵커를 만듭니다.

### <a name="adding-a-world-anchor"></a>World Anchor 추가

세계 앵커를 추가하려면 <WorldAnchor> 실제 세계에서 앵커하려는 변환을 사용하여 게임 개체에서 AddComponent()를 호출합니다.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

이것으로 끝입니다. 이 게임 개체는 이제 실제 세계의 현재 위치에 고정됩니다. Unity 세계 좌표는 시간이 지남에 따라 약간 조정되어 물리적 맞춤을 확인할 수 있습니다. [지속성을](persistence-in-unity.md) 사용하여 향후 앱 세션에서 이 고정된 위치를 다시 찾습니다.

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

## <a name="sharing-anchors-across-devices"></a>디바이스 간에 앵커 공유

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 사용하여 로컬 WorldAnchor에서 지속형 클라우드 앵커를 만듭니다. 그러면 앱이 여러 HoloLens, iOS 및 Android 디바이스에서 찾을 수 있습니다.  여러 디바이스에서 공통 공간 앵커를 공유하면 각 사용자는 동일한 물리적 위치에서 해당 앵커를 기준으로 렌더링된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

Unity에서 공유 환경 빌드를 시작하려면 5분 Azure Spatial Anchors Unity 빠른 시작을 사용해 <a href="/azure/spatial-anchors/unity-overview" target="_blank">보세요.</a>

Azure Spatial Anchors 사용하여 실행하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity 에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 검사점 여정을 수행하는 경우 Mixed Reality 핵심 구성 요소에 대해 탐색해야 합니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [응시](gaze-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [환경 크기 조정](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [공간 단계](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [Unity의 지속성](persistence-in-unity.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity용 Azure Spatial Anchors SDK</a>