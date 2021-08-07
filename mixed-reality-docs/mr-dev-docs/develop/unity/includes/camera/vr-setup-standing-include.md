---
ms.openlocfilehash: 47dfba0fe2b64e3b7e03ae62af3de1e1e24bd70b8b1e7e6b2cb40995428dbda2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212320"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Unity용 MRTK의 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용하고 **대상 눈금을** **Room** 또는 **Standing** 로 설정합니다.

![MRTK 설정 창](../../images/mrtk-target-scale.png)

MRTK는 재생 영역 및 카메라의 위치를 자동으로 처리해야 하지만 다음을 다시 확인하는 것이 좋습니다.

![MRTK 플레이스페이스](../../images/mrtk-playspace.png)

1. **Hierarchy** 패널에서 **MixedRealityPlayspace** GameObject를 확장하고 **Main Camera** 자식 개체를 찾습니다.
2. **검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** **(X: 0, Y: 0, Z: 0)으로** 변경합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정합니다. 하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출합니다.

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

Unity의 [XRig 를 작업합니다.](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)

![계층 구조의 XR 조작](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Windows **Store Player 설정** **기타** 설정 섹션으로 이동합니다.
2. Windows Mixed Reality **디바이스로** 선택합니다. 이 디바이스는 이전 버전의 Unity에서 **Windows Holographic으로** 나열될 수 있습니다.
3. **가상 현실 지원 선택**

Main Camera 개체는 자동으로 카메라로 태그가 지정되므로 Unity는 모든 이동 및 변환을 수행합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함하지만 아래 설정이 제대로 적용되지 않은 주 카메라 GameObject가 계층 구조에 포함됩니다.

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDevice*

서 **있는 규모** 또는 **방 규모 환경의** 경우 바닥과 상대적인 콘텐츠를 배치해야 합니다. 첫 번째 실행 중에 설정된 사용자의 정의된 층 수준 원점 및 선택적 방 경계를 나타내는 **[공간 단계](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 사용하여 사용자의 층을 추론합니다.

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

* SetTrackingSpaceType이 true를 반환하는 경우 Unity는 세계 좌표계를 성공적으로 전환하여 [참조의 스테이지 프레임을](../../../../design/coordinate-systems.md#spatial-coordinate-systems)추적합니다.
* SetTrackingSpaceType이 false를 반환하는 경우 Unity는 사용자가 환경에서 층을 설정하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다. 잘못된 반환 값은 일반적이지 않지만, 스테이지가 다른 공간에 설정되고 사용자가 새 스테이지를 설정하지 않고 디바이스를 현재 공간으로 이동하는 경우 발생할 수 있습니다.

앱이 RoomScale 추적 공간 유형을 성공적으로 설정하면 y=0 평면에 배치된 콘텐츠가 층으로 표시됩니다. 0, 0, 0의 원점은 사용자가 방 설치 중에 깔고 있는 층의 특정 위치이며, -Z는 설치하는 동안의 정방향 방향을 나타냅니다.