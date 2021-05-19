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
# <a name="teleport-system"></a><span data-ttu-id="86aab-104">시스템 텔레포트</span><span class="sxs-lookup"><span data-stu-id="86aab-104">Teleport System</span></span>

<span data-ttu-id="86aab-105">텔레포트 시스템은 응용 프로그램에서 불투명 한 디스플레이를 사용할 때 teleporting를 처리 하는 MRTK의 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="86aab-106">AR 환경 (예: HoloLens)의 경우 teleportation 시스템이 활성화 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="86aab-107">모던 HMD 환경 (OpenVR, WMR)의 경우 텔레포트 시스템을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="86aab-108">사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="86aab-108">Enabling and disabling</span></span>

<span data-ttu-id="86aab-109">자신의 프로필에서 확인란을 선택 취소 하 여 텔레포트 시스템을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="86aab-110">이 작업을 수행 하려면 장면에서 MixedRealityToolkit 개체를 선택 하 고 "텔레포트"을 클릭 한 다음 "텔레포트 시스템 사용" 확인란을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="86aab-111">이 작업은 런타임 시에도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="86aab-112">이벤트</span><span class="sxs-lookup"><span data-stu-id="86aab-112">Events</span></span>

<span data-ttu-id="86aab-113">텔레포트 시스템은 인터페이스를 통해 이벤트 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 를 노출 하 여 텔레포트 작업이 시작, 종료 또는 취소 될 때 신호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="86aab-114">이벤트 및 관련 페이로드의 메커니즘에 대 한 자세한 내용은 연결 된 API 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86aab-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="86aab-115">사용량</span><span class="sxs-lookup"><span data-stu-id="86aab-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="86aab-116">Teleportation 이벤트를 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="86aab-116">How to register for teleportation events</span></span>

<span data-ttu-id="86aab-117">아래 코드에서는 teleportation 이벤트를 수신 하는 MonoBehaviour를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="86aab-118">이 코드에서는 텔레포트 시스템이 활성화 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="86aab-119">MRTK의 Teleporting</span><span class="sxs-lookup"><span data-stu-id="86aab-119">Teleporting on MRTK</span></span>

<span data-ttu-id="86aab-120">기본 구성을 사용 하 여 MR 장치의 컨트롤러를 텔레포트 하려면 엄지 스틱을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="86aab-121">트레일러 식으로 텔레포트 하려면 인덱스 손가락을 curl 하 여 텔레포트를 완료 하 고 인덱스 및 엄지 단추를 사용 하 여 손을 향한 제스처를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86aab-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="86aab-122">입력 시뮬레이션을 사용 하 여 텔레포트 하려면 업데이트 된 [입력 시뮬레이션 서비스 설명서](../input-simulation/input-simulation-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86aab-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![텔레포트 제스처](../images/teleport/handteleport.gif)