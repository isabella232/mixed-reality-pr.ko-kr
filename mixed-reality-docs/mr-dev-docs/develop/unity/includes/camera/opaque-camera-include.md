---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748488"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK는 카메라 시스템 프로필 의 [구성에](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)따라 특정 카메라 설정을 자동으로 처리합니다.

**네임스페이스:** *Microsoft.MixedReality.Toolkit.CameraSystem*<br>
**형식:** *MixedRealityCameraSystem*

카메라의 불투명도를 확인하기 위해 MixedRealityCamera 시스템에는 [ `IsOpaque` 속성이](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)있습니다.

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDisplaySubsystem*

스크립트 코드를 사용하여 현재 실행 중인 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)에서 [displayOpaque를](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 확인하여 헤드셋이 몰입형인지 또는 홀로그램인지 런타임에 확인할 수 있습니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**네임스페이스:** *UnityEngine.XR.WSA*<br>
**유형:** *HolographicSettings*

[HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인하여 런타임에 스크립트 코드를 사용하여 헤드셋이 몰입형인지 또는 홀로그램인지 확인할 수 있습니다.