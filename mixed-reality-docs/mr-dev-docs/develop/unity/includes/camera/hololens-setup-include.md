---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636321"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

이 단계별 [자습서](../../tutorials/mr-learning-base-01.md) 에 따라 Unity 프로젝트에서 Mixed Reality Toolkit을 추가 하 고 자동으로 구성 합니다. 또한 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스에서 Unity를 사용 하 여 직접 작업 하 고 **대상 규모** 를 **세계** 로 설정할 수 있습니다.

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

HoloLens 응용 프로그램에 대해 앵커 및 Arsession/Arsession에서 더 잘 작동 하는 [Arsession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) 을 사용할 수 있습니다.

![계층의 AR 세션](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> AR 세션 및 관련 기능에는 AR Foundation이 설치 되어 있어야 합니다.

ARSession을 사용 하지 않고 카메라 변경 내용을 수동으로 적용할 수 있습니다.

1. **계층** 패널에서 **주 카메라** 를 선택 합니다.
1. **검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.

   ![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)  
   *Unity의 검사기 창에 있는 카메라*

1. **기본 카메라** 에 **TrackedPoseDriver** 추가

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. **계층** 패널에서 **주 카메라** 를 선택 합니다.
1. **검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.

   ![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)  
   *Unity의 검사기 창에 있는 카메라*

1. **Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.
1. **Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.
1. **지원 되는 가상 현실** 선택

기본 카메라 개체는 자동으로 카메라로 태그를 지정 하므로 Unity는 모든 이동 및 이동을 이동 합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject 포함 되지만 설정이 제대로 적용 되지 않을 수 있습니다.