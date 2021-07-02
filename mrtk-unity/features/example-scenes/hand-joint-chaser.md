---
title: 손 공동 추적기
description: MRTK의 손 공동 추적기
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175364"
---
# <a name="hand-joint-chaser"></a><span data-ttu-id="3d9d8-104">손 공동 추적기</span><span class="sxs-lookup"><span data-stu-id="3d9d8-104">Hand joint chaser</span></span>

<span data-ttu-id="3d9d8-105">![손 조인트 체이서 ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 이 예제 장면에서는 Solver를 사용하여 손 연결에 개체를 연결하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="3d9d8-106">예제 장면</span><span class="sxs-lookup"><span data-stu-id="3d9d8-106">Example scene</span></span>

<span data-ttu-id="3d9d8-107">아래 폴더에서 **HandJointChaserExample** 장면 예제 장면을 찾을 수 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="3d9d8-108">해결기 처리기</span><span class="sxs-lookup"><span data-stu-id="3d9d8-108">Solver handler</span></span>

<span data-ttu-id="3d9d8-109">**참조할 추적된 개체를** 클릭하고 **손 공동 왼쪽** 또는 손 **공동 오른쪽 을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="3d9d8-110">**추적된 손 공동 드롭다운을** 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="3d9d8-111">드롭다운 목록에서 추적할 특정 조인을 선택할 수 있습니다. 이 예제 장면에서는 방사형 뷰 해결기를 사용하여 개체가 대상 개체를 따르도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="3d9d8-112">자세한 내용은 [Solver](../ux-building-blocks/solvers/solver.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d9d8-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![손 공동 해결기](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
