---
title: 원격 포트 핫스폿
description: MRTK의 Teleport 핫스팟 구성 요소에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Teleport 시스템, Teleport 핫스팟
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 01ae900800c4a13ca7bafc3391ff51b752a95ae0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176199"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="55e03-104">원격 포트 핫스폿</span><span class="sxs-lookup"><span data-stu-id="55e03-104">Teleport hotspot</span></span>

<span data-ttu-id="55e03-105">원격 포트 핫스팟은 사용자가 해당 위치로 원격 전송할 때 특정 위치와 방향에 있는지 확인하기 위해 gameobject에 추가할 수 있는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55e03-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="55e03-106">사용</span><span class="sxs-lookup"><span data-stu-id="55e03-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="55e03-107">원격 포트 핫스팟을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="55e03-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="55e03-108">원격 포트 핫스팟을 만들려면 TeleportHotspot 구성 요소를 충돌체 구성 요소가 있는 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="55e03-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Teleport 핫스팟 구성 요소](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="55e03-110">이제 Teleport 포인터의 표시기가 TeleportHotspot을 통해 전송될 때 색이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="55e03-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="55e03-111">핫스팟을 통해 원격 이동 작업이 완료되면 사용자는 TeleportHotspot의 가운데로 원격 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="55e03-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="55e03-112">재정의 방향 플래그가 선택되어 있으면 사용자의 방향이 원격 포트 핫스팟의 방향과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="55e03-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Teleport 핫스팟 예제](../images/teleport/TeleportHotspotExample.gif)
