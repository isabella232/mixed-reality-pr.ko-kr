---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636385"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용 하 여 Unity에서 MRTK를 사용 하 고 **대상 크기** 를 방 **또는 서** 로 설정 합니다. 

![MRTK 설정 창](../../images/mrtk-target-scale.png)

MRTK는 플레이 공간 및 카메라의 위치를 자동으로 처리 해야 하지만 두 번 확인 하는 것이 좋습니다.

![MRTK playspace](../../images/mrtk-playspace.png)

1. **계층** 패널에서 **MixedRealityPlayspace** GameObject를 확장 하 고 **기본 카메라** 자식 개체를 찾습니다.
2. **검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[Xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정 합니다. 하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출 합니다.

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

Unity의 [Xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)를 사용 하 여 작업 합니다.

![계층의 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. **Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.
2. **Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.
3. **지원 되는 가상 현실** 선택

기본 카메라 개체는 자동으로 카메라로 태그를 지정 하므로 Unity는 모든 이동 및 이동을 이동 합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject가 포함 되지만, 아래에는 설정이 제대로 적용 되지 않습니다.

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdevice*

**대규모 또는** **공간 규모의 경험** 을 위해 바닥을 기준으로 콘텐츠를 넣어야 합니다. 사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다.

Unity가 최고 좌표계로 작동 하는지 확인 하기 위해 RoomScale 추적 공간 유형을 사용 하 여 Unity를 설정 하 고 테스트할 수 있습니다.

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

* SetTrackingSpaceType가 true를 반환 하는 경우 Unity는 세계 좌표계를 정상적으로 전환 하 여 [참조의 스테이지 프레임](../../../../design/coordinate-systems.md#spatial-coordinate-systems)을 추적 했습니다.
* SetTrackingSpaceType가 false를 반환 하는 경우 Unity는 사용자의 환경에서 바닥을 설정 하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다. False 반환 값은 일반적이 지 않지만 다른 방에 단계를 설정 하 고 사용자가 새 단계를 설정 하지 않은 상태에서 현재 대화방으로 장치를 이동 하는 경우 발생할 수 있습니다.

앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다. 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 구현