---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636378"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Unity 용 MRTK의 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용 하 고 **대상 소수 자릿수** 를 **다음** 으로 설정 합니다.

![MRTK 설정 창](../../images/mrtk-target-scale.png)

MRTK는 플레이 공간 및 카메라의 위치를 자동으로 처리 해야 하지만 두 번 확인 하는 것이 좋습니다.

![MRTK playspace](../../images/mrtk-playspace.png)

1. **계층** 패널에서 **MixedRealityPlayspace** GameObject를 확장 하 고 **기본 카메라** 자식 개체를 찾습니다.
2. **검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[Xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정 합니다. 하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출 합니다.

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
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

**방향 전용** 또는 통합 된 **환경을** 구축 하려면 Unity를 고정 된 추적 공간 형식으로 설정 해야 합니다. 고정 된 추적 공간에서는 Unity의 세계 좌표 시스템을 설정 하 여 [고정 된 참조 프레임](../../../../design/coordinate-systems.md#spatial-coordinate-systems)을 추적 합니다. 고정 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**네임 스페이스:** *UNITYENGINE. XR*<br>
**형식:** *inputtracking*

360도 비디오 뷰어 (위치 헤드 업데이트에서 환상 효과를 ruin)와 같은 순수한 **방향 전용 환경** 에서는 XR를 설정할 수 있습니다 [. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 을 true로 설정 합니다.

```cs
InputTracking.disablePositionalTracking = true;
```

사용자가 나중에 연결 된 원본을 recenter 할 수 있도록 하는 **확장 된 환경의** 경우 XR를 호출할 수 있습니다 [. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:

```cs
InputTracking.Recenter();
```

통합 된 [환경을](../../../../design/coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**