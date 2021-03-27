---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636373"
---
# <a name="mrtk"></a>[<span data-ttu-id="ef863-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="ef863-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ef863-102">MRTK는 여러 부분으로 된 손 및 컨트롤러에서 자동으로 작동 하는 기본 [텔레포트 시스템](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) 을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="ef863-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="ef863-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ef863-104">MRTK의 teleportation 구현을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="ef863-105">MRTK를 사용 하지 않도록 선택 하는 경우 Unity는 [XR 상호 작용 도구 키트](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)에서 teleportation 구현을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="ef863-106">직접 구현 하도록 선택 하는 경우 카메라를 직접 이동할 수 없다는 점에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="ef863-107">헤드 추적을 위한 Unity의 카메라 제어로 인해 계층 구조에서 카메라에 부모를 지정 하 고 해당 GameObject을 대신 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="ef863-108">MRTK의 Playspace와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ef863-109">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="ef863-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ef863-110">MRTK의 teleportation 구현을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="ef863-111">직접 구현 하도록 선택 하는 경우 카메라를 직접 이동할 수 없다는 점에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="ef863-112">헤드 추적을 위한 Unity의 카메라 제어로 인해 계층 구조에서 카메라에 부모를 지정 하 고 해당 GameObject을 대신 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="ef863-113">MRTK의 Playspace와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef863-113">This is the equivalent of MRTK's Playspace.</span></span>