---
title: TeleportHotspot
description: MRTK의 텔레포트 핫스팟 구성 요소에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 텔레포트 시스템, 텔레포트 핫스팟
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582965"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="c1f8b-104">텔레포트 핫스팟 [실험적]</span><span class="sxs-lookup"><span data-stu-id="c1f8b-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="c1f8b-105">텔레포트 핫스팟은 gameobject에 추가 하 여 해당 위치로 텔레포트 할 때 사용자가 특정 위치와 방향을 갖도록 할 수 있는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c1f8b-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="c1f8b-106">사용량</span><span class="sxs-lookup"><span data-stu-id="c1f8b-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="c1f8b-107">텔레포트 핫스팟을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="c1f8b-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="c1f8b-108">텔레포트 핫스팟을 만들려면 TeleportHotspot 구성 요소를 포함 하는 개체에 collider component를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f8b-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![핫스팟 구성 요소 텔레포트](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="c1f8b-110">이제 TeleportHotspot을 통해 전달 될 때 텔레포트 포인터의 표시기가 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f8b-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="c1f8b-111">핫스팟 위에서 텔레포트 작업이 완료 되 면 사용자가 TeleportHotspot의 중심으로 텔레포트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f8b-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="c1f8b-112">재정의 방향 플래그를 선택 하면 사용자의 방향이 텔레포트 핫스폿의와 일치 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f8b-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![텔레포트 핫스팟 예](../images/teleport/TeleportHotspotExample.gif)
