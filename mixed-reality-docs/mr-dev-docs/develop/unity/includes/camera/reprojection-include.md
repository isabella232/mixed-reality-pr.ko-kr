---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212307"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK에는 현재 다시 프로젝션 모드에 대한 도우미가 없습니다. 자세한 내용은 다른 탭 중 하나를 참조하세요.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

다시 프로젝션 모드는 [XRDisplaySubsystem.reprojectionMode를](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) 적절한 값으로 설정하여 구성할 수 있습니다.

예를 들어 본문이 엄격하게 잠긴 콘텐츠(예: 360도 비디오 콘텐츠)를 사용하여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 다시 프로젝션 모드를 [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)로 설정해야만 방향으로 명시적으로 설정할 수 있습니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[HolographicSettings.ReprojectionMode를](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 적절한 값으로 설정하여 다시 프로젝션 모드를 구성할 수 있습니다.

예를 들어 본문이 엄격하게 잠긴 콘텐츠(예: 360도 비디오 콘텐츠)를 사용하여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)로 설정해야만 다시 프로젝션 모드를 방향으로 명시적으로 설정할 수 있습니다.