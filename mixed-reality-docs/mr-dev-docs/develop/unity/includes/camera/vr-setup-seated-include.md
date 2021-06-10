---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748459"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Unity용 MRTK의 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용하고 **대상 눈금을** **Seated로** 설정합니다.

![MRTK 설정 창](../../images/mrtk-target-scale.png)

MRTK는 재생 영역 및 카메라의 위치를 자동으로 처리해야 하지만 다음을 다시 확인하는 것이 좋습니다.

![MRTK 플레이스페이스](../../images/mrtk-playspace.png)

1. **Hierarchy** 패널에서 **MixedRealityPlayspace** GameObject를 확장하고 **Main Camera** 자식 개체를 찾습니다.
2. **검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** **(X: 0, Y: 0, Z: 0)으로** 변경합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정합니다. 하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출합니다.

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

Unity의 [XRig 를 작업합니다.](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)

![계층 구조의 XR 조작](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Windows 스토어 플레이어 **설정의 기타 설정** **섹션으로** 이동합니다.
2. 이전 버전의 Unity에서 **Windows Holographic으로** 나열될 수 있는 디바이스로 **Windows Mixed Reality** 선택합니다.
3. **가상 현실 지원 선택**

Main Camera 개체는 자동으로 카메라로 태그가 지정되므로 Unity는 모든 이동 및 변환을 수행합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함하지만 아래 설정이 제대로 적용되지 않은 주 카메라 GameObject가 계층 구조에 포함됩니다.

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDevice*

**방향 전용** 또는 **좌표 크기 조정 환경을** 빌드하려면 Unity를 고정 추적 공간 형식으로 설정해야 합니다. 고정 추적 공간은 Unity의 세계 좌표계를 설정하여 [고정 참조 프레임을](../../../../design/coordinate-systems.md#spatial-coordinate-systems)추적합니다. 고정 추적 모드에서는 앱이 시작되면 카메라의 기본 위치 바로 앞에 배치된 콘텐츠(정방향은 -Z)가 사용자 앞에 표시됩니다.

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

[착석 규모 환경을](../../../../design/coordinate-systems.md)빌드하는 경우 XR을 호출하여 사용자의 현재 헤드 위치에서 Unity의 권역을 더 최근에 만들 수 **[있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 메서드.