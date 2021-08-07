---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212310"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK는 굴절형 손 및 컨트롤러에서 자동으로 작동하는 내부 [원격 포트 시스템을](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) 제공합니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK의 원격 보고 구현을 사용하는 것이 좋습니다.
MRTK를 사용하지 않도록 선택하는 경우 Unity는 [XR 상호 작용 Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)원격 보고 구현을 제공합니다.
사용자 고유의 구현을 선택하는 경우 카메라를 직접 이동할 수 없다는 점을 염두에 두는 것이 좋습니다. Unity의 머리 추적 카메라 제어로 인해 계층 구조에서 카메라에 부모를 부여하고 해당 GameObject를 대신 이동해야 합니다. 이는 MRTK의 플레이스페이스에 해당합니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK의 원격 보고 구현을 사용하는 것이 좋습니다.
사용자 고유의 구현을 선택하는 경우 카메라를 직접 이동할 수 없다는 점을 염두에 두는 것이 좋습니다. Unity의 머리 추적 카메라 제어로 인해 계층 구조에서 카메라에 부모를 부여하고 해당 GameObject를 대신 이동해야 합니다. 이는 MRTK의 플레이스페이스에 해당합니다.