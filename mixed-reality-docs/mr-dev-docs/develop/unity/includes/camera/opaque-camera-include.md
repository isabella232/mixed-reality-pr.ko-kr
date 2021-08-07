---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212300"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK는 [카메라 시스템 프로필의 구성](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)에 따라 특정 카메라 설정을 자동으로 처리 합니다.

**네임 스페이스:** *MixedReality. Toolkit. CameraSystem*<br>
**유형:** *MixedRealityCameraSystem*

카메라의 opaqueness를 확인 하기 위해 MixedRealityCamera 시스템에는 [ `IsOpaque` 속성이](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)있습니다.

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdisplaysubsystem*

스크립트 코드를 사용 하 여 적극적으로 실행 중인 [Xrdisplaysubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)에서 [displayopaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 을 확인 하 여 헤드셋이 몰입 형 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형:** *HolographicSettings*

스크립트 코드를 사용 하 여 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인 하 여 헤드셋이 몰입 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.