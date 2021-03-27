---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636361"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK에는 현재 reprojection 모드에 대 한 도우미가 없습니다. 자세한 내용은 다른 탭 중 하나를 참조 하세요.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Reprojection 모드는 reprojectionMode을 적절 한 값으로 설정 하 여 구성할 수 있습니다 [.](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html)

예를 들어 엄격 본문에서 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)로 설정 하 여 reprojection 모드를 방향 으로만 명시적으로 설정할 수 있습니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Reprojection 모드는 ReprojectionMode를 적절 한 값으로 설정 하 여 구성할 수 있습니다 [.](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)

예를 들어 엄격 본문에서 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)로 설정 하 여 reprojection 모드를 방향 으로만 명시적으로 설정할 수 있습니다.