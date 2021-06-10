---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748485"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK는 여러 부분으로 된 손 및 컨트롤러에서 자동으로 작동 하는 기본 [텔레포트 시스템](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) 을 제공 합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK의 teleportation 구현을 사용 하는 것이 좋습니다.
MRTK를 사용 하지 않도록 선택 하는 경우 Unity는 [XR 상호 작용 도구 키트](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)에서 teleportation 구현을 제공 합니다.
직접 구현 하도록 선택 하는 경우 카메라를 직접 이동할 수 없다는 점에 유의 해야 합니다. 헤드 추적을 위한 Unity의 카메라 제어로 인해 계층 구조에서 카메라에 부모를 지정 하 고 해당 GameObject을 대신 이동 해야 합니다. MRTK의 Playspace와 동일 합니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK의 teleportation 구현을 사용 하는 것이 좋습니다.
직접 구현 하도록 선택 하는 경우 카메라를 직접 이동할 수 없다는 점에 유의 해야 합니다. 헤드 추적을 위한 Unity의 카메라 제어로 인해 계층 구조에서 카메라에 부모를 지정 하 고 해당 GameObject을 대신 이동 해야 합니다. MRTK의 Playspace와 동일 합니다.