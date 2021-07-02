---
title: Teleport 시스템
description: MRTK에서 Teleport 시스템 사용 및 사용 안 됨 개요
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Teleport 시스템,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176185"
---
# <a name="teleport-system"></a><span data-ttu-id="6e588-104">시스템 텔레포트</span><span class="sxs-lookup"><span data-stu-id="6e588-104">Teleport system</span></span>

<span data-ttu-id="6e588-105">원격 통신 시스템은 애플리케이션이 불투명 표시를 사용할 때 사용자에게 원격 전송을 처리하는 MRTK의 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="6e588-106">AR 환경(예: HoloLens)의 경우 원격 보고 시스템이 활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="6e588-107">몰입형 HMD 환경(OpenVR, WMR)의 경우 원격 포트 시스템을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="6e588-108">사용 및 사용 안 됨</span><span class="sxs-lookup"><span data-stu-id="6e588-108">Enabling and disabling</span></span>

<span data-ttu-id="6e588-109">프로필에서 확인란을 설정/해제하여 원격 포트 시스템을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="6e588-110">이 작업은 장면에서 MixedRealityToolkit 개체를 선택하고 "Teleport"를 클릭한 다음 "Teleport 시스템 사용" 확인란을 토글하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="6e588-111">이 작업은 런타임에 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="6e588-112">이벤트</span><span class="sxs-lookup"><span data-stu-id="6e588-112">Events</span></span>

<span data-ttu-id="6e588-113">teleport 시스템은 인터페이스를 통해 이벤트를 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 노출하여 원격 전송 작업이 시작, 종료 또는 취소될 때 신호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="6e588-114">이벤트 메커니즘 및 관련 페이로드에 대한 자세한 내용은 연결된 API 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e588-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="6e588-115">사용</span><span class="sxs-lookup"><span data-stu-id="6e588-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="6e588-116">원격 보고 이벤트에 등록하는 방법</span><span class="sxs-lookup"><span data-stu-id="6e588-116">How to register for teleportation events</span></span>

<span data-ttu-id="6e588-117">아래 코드는 원격 보고 이벤트를 수신 대기하는 MonoBehaviour를 만드는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="6e588-118">이 코드는 원격 포트 시스템을 사용하도록 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="6e588-119">MRTK에서 원격 보고</span><span class="sxs-lookup"><span data-stu-id="6e588-119">Teleporting on MRTK</span></span>

<span data-ttu-id="6e588-120">기본 구성을 사용하여 MR 디바이스에서 컨트롤러와 원격 통신하려면 엄지스틱을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="6e588-121">굴절된 손으로 원격 이동하려면 손끝이 인덱스 및 엄지 손가락으로 바깥쪽을 향하도록 제스처를 만들고, 인덱스 손가락으로 말려서 원격 통신을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="6e588-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="6e588-122">입력 시뮬레이션을 사용하여 원격 전송하려면 업데이트된 [입력 시뮬레이션 서비스 설명서를](../input-simulation/input-simulation-service.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e588-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![원격 이동 제스처](../images/teleport/handteleport.gif)
