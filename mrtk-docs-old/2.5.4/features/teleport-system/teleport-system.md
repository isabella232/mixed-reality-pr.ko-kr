---
title: TeleportSystemOverview
description: MRTK에서 텔레포트 시스템 사용 및 사용 안 함 개요
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 텔레포트 시스템,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197643"
---
# <a name="teleport-system"></a>시스템 텔레포트

텔레포트 시스템은 애플리케이션이 불투명 디스플레이를 사용할 때 사용자 텔레포트를 처리하는 MRTK의 하위 시스템입니다. AR 환경(예: HoloLens)의 경우 텔레포테이션 시스템이 활성화되지 않습니다. 몰입형 HMD 환경(OpenVR, WMR)의 경우 텔레포트 시스템을 사용할 수 있습니다.

## <a name="enabling-and-disabling"></a>사용 및 사용 안 함

프로필에서 확인란을 토글하여 텔레포트 시스템을 사용하거나 사용하지 않도록 설정할 수 있습니다.
이 작업은 장면에서 MixedRealityToolkit 개체를 선택하고 "텔레포트"를 클릭한 다음, "텔레포트 시스템 사용" 확인란을 토글하여 수행할 수 있습니다.

이 작업은 런타임 시에도 가능합니다.

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

텔레포트 시스템은 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 인터페이스를 통해 이벤트를 노출하여 텔레포트 작업이 시작, 종료 또는 취소될 때 신호를 제공합니다.
이벤트 메커니즘 및 관련 페이로드에 대한 자세한 내용은 연결된 API 설명서를 참조하세요.

## <a name="usage"></a>사용량

### <a name="how-to-register-for-teleportation-events"></a>텔레포트 이벤트 등록 방법

아래 코드는 텔레포테이션 이벤트를 수신할 MonoBehaviour를 만드는 방법을 보여줍니다. 이 코드는 텔레포트 시스템을 사용한다고 가정합니다.

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
