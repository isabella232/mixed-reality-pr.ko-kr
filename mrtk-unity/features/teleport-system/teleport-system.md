---
title: 시스템로 텔레포트 개요
description: MRTK에서의 텔레포트 시스템 설정 및 해제에 대 한 개요
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 텔레포트 시스템,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144141"
---
# <a name="teleport-system"></a>시스템 텔레포트

텔레포트 시스템은 응용 프로그램에서 불투명 한 디스플레이를 사용할 때 teleporting를 처리 하는 MRTK의 하위 시스템입니다. AR 환경 (예: HoloLens)의 경우 teleportation 시스템이 활성화 되어 있지 않습니다. 모던 HMD 환경 (OpenVR, WMR)의 경우 텔레포트 시스템을 사용 하도록 설정할 수 있습니다.

## <a name="enabling-and-disabling"></a>사용 및 사용 안 함

자신의 프로필에서 확인란을 선택 취소 하 여 텔레포트 시스템을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.
이 작업을 수행 하려면 장면에서 MixedRealityToolkit 개체를 선택 하 고 "텔레포트"을 클릭 한 다음 "텔레포트 시스템 사용" 확인란을 선택 취소 합니다.

이 작업은 런타임 시에도 수행할 수 있습니다.

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a>이벤트

텔레포트 시스템은 인터페이스를 통해 이벤트 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 를 노출 하 여 텔레포트 작업이 시작, 종료 또는 취소 될 때 신호를 제공 합니다.
이벤트 및 관련 페이로드의 메커니즘에 대 한 자세한 내용은 연결 된 API 설명서를 참조 하세요.

## <a name="usage"></a>사용량

### <a name="how-to-register-for-teleportation-events"></a>Teleportation 이벤트를 등록 하는 방법

아래 코드에서는 teleportation 이벤트를 수신 하는 MonoBehaviour를 만드는 방법을 보여 줍니다. 이 코드에서는 텔레포트 시스템이 활성화 된 것으로 가정 합니다.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a>MRTK의 Teleporting

기본 구성을 사용 하 여 MR 장치의 컨트롤러를 텔레포트 하려면 엄지 스틱을 사용 합니다. 트레일러 식으로 텔레포트 하려면 인덱스 손가락을 curl 하 여 텔레포트를 완료 하 고 인덱스 및 엄지 단추를 사용 하 여 손을 향한 제스처를 만듭니다. 입력 시뮬레이션을 사용 하 여 텔레포트 하려면 업데이트 된 [입력 시뮬레이션 서비스 설명서](../input-simulation/input-simulation-service.md)를 참조 하세요.

  ![텔레포트 제스처](../images/teleport/handteleport.gif)