---
title: 손 조인트 체이서
description: MRTK의 핸드 조인트 체이서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144622"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="c8546-104">핸드 조인트 체이서 예제</span><span class="sxs-lookup"><span data-stu-id="c8546-104">Hand joint chaser example</span></span>

<span data-ttu-id="c8546-105">![](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg)이 예제 장면에서는 연결을 사용 하 여 개체를 직접 조인트에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8546-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="c8546-106">장면 예</span><span class="sxs-lookup"><span data-stu-id="c8546-106">Example scene</span></span>

<span data-ttu-id="c8546-107">아래 폴더에서 장면 **HandJointChaserExample** 장면 예제를 찾을 수 있습니다 `Assets/MRTK/Examples` `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="c8546-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="c8546-108">해 찾기 처리기</span><span class="sxs-lookup"><span data-stu-id="c8546-108">Solver handler</span></span>

<span data-ttu-id="c8546-109">**참조할 추적 된 개체를** 클릭 하 고 **직접 조인트 왼쪽** 또는 오른쪽 **조인트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8546-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="c8546-110">**추적 된 직접 공동** 삭제를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8546-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="c8546-111">드롭다운 목록에서 추적할 특정 조인트를 선택할 수 있습니다. 이 예제 장면에서는 방사형 보기 해결 기를 사용 하 여 개체를 대상 개체 다음으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8546-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="c8546-112">자세한 내용은 [ [찾기](../ux-building-blocks/solvers/solver.md) ] 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8546-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![공동 해 찾기](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
