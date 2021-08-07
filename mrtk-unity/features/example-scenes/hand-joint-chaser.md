---
title: 손 관절 체이서
description: MRTK의 손 공동 추적기
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189570"
---
# <a name="hand-joint-chaser"></a>손 관절 체이서

![손 조인트 체이서 ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 이 예제 장면에서는 Solver를 사용하여 손 연결에 개체를 연결하는 방법을 보여줍니다.

## <a name="example-scene"></a>예제 장면

아래 폴더에서 **HandJointChaserExample** 장면 예제 장면을 찾을 수 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 있습니다.

## <a name="solver-handler"></a>해결기 처리기

**참조할 추적된 개체를** 클릭하고 **손 공동 왼쪽** 또는 손 **공동 오른쪽 을** 선택합니다. **추적된 손 공동 드롭다운을** 볼 수 있습니다. 드롭다운 목록에서 추적할 특정 조인을 선택할 수 있습니다. 이 예제 장면에서는 방사형 뷰 해결기를 사용하여 개체가 대상 개체를 따르도록 합니다. 자세한 내용은 [Solver](../ux-building-blocks/solvers/solver.md) 페이지를 참조하세요.

![손 공동 해결기](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
