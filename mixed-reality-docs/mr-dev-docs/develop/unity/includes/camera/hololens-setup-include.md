---
ms.openlocfilehash: 78596197af6c2e7c329e7a7c99281f8debee13b973a212709f5be1ec34e04eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212297"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

이 [단계별 자습서에](../../tutorials/mr-learning-base-01.md) 따라 Unity 프로젝트에서 Mixed Reality Toolkit 추가하고 자동으로 구성합니다. Unity용 MRTK의 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 직접 작업하고 **대상 배율** 을 **World로** 설정할 수도 있습니다.

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

앵커 및 ARKit/ARCore에서 더 잘 작동하는 HoloLens 애플리케이션에 [ARSession을](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) 사용할 수 있습니다.

![계층 구조의 AR 세션](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> AR 세션 및 관련 기능에는 AR Foundation이 설치되어 있어야 합니다.

ARSession을 사용하지 않고 카메라 변경 내용을 수동으로 적용할 수도 있습니다.

1. 계층 패널에서 **주 카메라를** **선택합니다.**
1. **검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** **(X: 0, Y: 0, Z: 0)으로** 변경합니다.

   ![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)  
   *Unity의 검사기 창에 있는 카메라*

1. **기본 카메라에** **TrackedPoseDriver** 추가

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 계층 패널에서 **주 카메라를** **선택합니다.**
1. **검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** **(X: 0, Y: 0, Z: 0)으로** 변경합니다.

   ![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)  
   *Unity의 검사기 창에 있는 카메라*

1. Windows **Store Player 설정** **기타** 설정 섹션으로 이동합니다.
1. Windows Mixed Reality **디바이스로** 선택합니다. 이 디바이스는 이전 버전의 Unity에서 **Windows Holographic으로** 나열될 수 있습니다.
1. **가상 현실 지원 선택**

Main Camera 개체는 자동으로 카메라로 태그가 지정되므로 Unity는 모든 이동 및 변환을 수행합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함하지만 설정이 제대로 적용되지 않을 수 있는 주 카메라 GameObject가 계층 구조에 포함됩니다.