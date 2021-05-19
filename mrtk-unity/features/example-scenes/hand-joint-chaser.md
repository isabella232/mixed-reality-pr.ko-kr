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
# <a name="hand-joint-chaser-example"></a>핸드 조인트 체이서 예제

![](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg)이 예제 장면에서는 연결을 사용 하 여 개체를 직접 조인트에 연결 하는 방법을 보여 줍니다.

## <a name="example-scene"></a>장면 예

아래 폴더에서 장면 **HandJointChaserExample** 장면 예제를 찾을 수 있습니다 `Assets/MRTK/Examples` `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>해 찾기 처리기

**참조할 추적 된 개체를** 클릭 하 고 **직접 조인트 왼쪽** 또는 오른쪽 **조인트** 를 선택 합니다. **추적 된 직접 공동** 삭제를 볼 수 있습니다. 드롭다운 목록에서 추적할 특정 조인트를 선택할 수 있습니다. 이 예제 장면에서는 방사형 보기 해결 기를 사용 하 여 개체를 대상 개체 다음으로 만듭니다. 자세한 내용은 [ [찾기](../ux-building-blocks/solvers/solver.md) ] 페이지를 참조 하세요.

![공동 해 찾기](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
