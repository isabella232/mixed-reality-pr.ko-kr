---
title: 손 메뉴
description: MRTK의 손 모양 메뉴 예제 장면
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 수동 메뉴,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177524"
---
# <a name="hand-menu"></a>손 메뉴

![손 메뉴 UX 예제](../images/solver/MRTK_UX_HandMenu.png)

사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다. 다른 개체와 상호 작용 하는 동안 거짓 활성화를 방지 하기 위해 손 모양 메뉴에는 ' 평면 필요 ' 및 ' 응시 활성화 사용 '과 같은 옵션이 제공 됩니다. 이러한 옵션을 사용 하 여 원치 않는 활성화를 방지 하는 것이 좋습니다.

## <a name="hand-menu-examples"></a>손 모양 메뉴 예제

**수동 Menu예제. unity** 장면이 폴더 아래에 있습니다. ``MRTK/Examples/Demos/HandTracking/Scenes`` 실행 되는 동안에는 현재 선택한 메뉴 유형만 활성화 됩니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

폴더 아래에서 prefabs 메뉴를 찾을 수 있습니다 ``MRTK/Examples/Demos/HandTracking/Prefabs`` .

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop 및 HandMenu_Medium_HideOnHandDrop

이러한 두 예제에서는 **OnFirstHandDetected ()** 및 **OnLastHandLost ()** 이벤트에서 메뉴를 표시 하 고 숨기는 메뉴를 활성화 하 고 비활성화 합니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

더 긴 상호 작용 시간이 필요한 복잡 한 메뉴의 경우 메뉴를 세계에서 잠그는 것이 좋습니다. 이 예제에서 사용자는 **OnFirstHandDetected ()** 및 **OnLastHandLost ()** 이벤트에서 menucontent를 활성화 및 비활성화 하는 것 외에도 메뉴를 잡아 잠글 수 있습니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

배경 판을 `ManipulationHandler` 사용 하면 grabbable 이동할 수 있습니다. **조작 시작 이벤트에서** **SolverHandler. UpdateSolvers** 는 메뉴를 세계에서 잠그기 위해 비활성화 됩니다. 또한 사용자가 작업이 완료 되 면 메뉴를 닫을 수 있는 **닫기 단추** 를 표시 합니다. **조작 종료 시** 이벤트는 HandConstraintPalmUp를 호출 하 여 사용자가 야자나무를 올리고 확인 하 여 메뉴를 다시 사용할 수 있도록 합니다 **.**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

**닫기** 단추가 **SolverHandler. UpdateSolvers** 를 다시 활성화 하 고 **menucontent** 를 숨깁니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

이 예는 HandMenu_Large_WorldLock_On_GrabAndPull와 비슷합니다. 유일한 차이점은 메뉴가 자동으로 삭제 될 때 자동으로 잠겨 있기 때문입니다. 이 작업은 **OnLastHandLost ()** 이벤트에서 menucontent를 숨기지 않는 방법으로 수행 됩니다. & 가져오기 동작은 HandMenu_Large_WorldLock_On_GrabAndPull 예제와 동일 합니다.

## <a name="scripts"></a>스크립트

이 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 동작은 직접 UI, 메뉴 등의 직접 제한 된 콘텐츠에 대해 추적 된 개체를 안전한 지역으로 제한 하는 해를 제공 합니다. 금고 지역은 손으로 교차 하지 않는 영역으로 간주 됩니다. 또한 호출 된의 파생 클래스는 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) palm이 사용자를 향한 경우에는 해 찾기 추적 된 개체를 활성화 하는 일반적인 동작을 보여 주기 위해 포함 되었습니다.

추가 설명서는 각 속성에 사용할 수 있는 도구 설명을 참조 하십시오 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) . 몇 가지 속성은 아래에 자세히 설명 되어 있습니다.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **금고 영역**: 안전한 영역에서 콘텐츠를 제한할 위치를 지정 합니다. 손으로와 개선 된 상호 작용 품질과 겹치지 않도록 콘텐츠를 Ulnar 측면에 배치 하는 것이 좋습니다. 금고 영역은 카메라 보기와 직교 하 고 바늘의 경계 상자에 대 한 raycasting의 평면으로 투영 된 중심을 계산 하 여 계산 됩니다. 금고 영역은에서 사용 하도록 정의 되어 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 있지만 다른 컨트롤러 형식 에서도 작동 합니다. 각 안전 영역이 여러 컨트롤러 유형에 서 무엇을 나타내는지 살펴보는 것이 좋습니다.

* **카메라를 연결 하기 전까지 팔 로우** 이 활성 상태에서 [찾기]는 메뉴가 카메라를 향하도록 하는 응시와 충분히 나란히 정렬 될 때까지 회전을 따릅니다. 이는 SolverRotationBehavior에서 HandConstraintSolver의 LookAtTrackedObject를 LookAtMainCamera으로 변경 하는 방식으로 작동 합니다.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **활성화 이벤트**: 현재는 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 4 개의 활성화 이벤트를 트리거합니다. 이러한 이벤트는 다양 한 조합으로 사용 하 여 고유한 동작을 만들 수 있습니다 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) `MRTK/Examples/Demos/HandTracking/Scenes/` . 이러한 동작에 대 한 예제는의 HandBasedMenuExample 장면을 참조 하세요.

  * *On핸드 활성화*:가 IsHandActive 메서드를 만족 하는 경우 트리거합니다.
  * *On핸드 비활성화*: IsHandActive 메서드가 더 이상 충족 되지 않을 때 트리거됩니다.
  * *OnFirstHandDetected*: 손 모양 추적 상태가 뷰에서 손을 볼 때 뷰에서 첫 번째 손 모양으로 변경 되 면 발생 합니다.
  * *OnLastHandLost*: 직접 추적 상태가 뷰에서 손을 볼 수 없도록 변경 될 때 발생 합니다.

* **해 찾기 활성화/비활성화 논리**: 현재 논리 활성화 및 비활성화에 대 한 권장 사항은 개체를 사용 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 하지 않도록 설정 하거나 사용 하지 않고 SolverHandler의 UpdateSolver 값을 사용 하 여 수행 하는 것입니다. 이는 연결 된 메뉴의 ManipulationHandler "OnManipulationStarted/종료" 이벤트 후에 트리거되는 편집기 기반 후크를 통해 예제 장면에서 볼 수 있습니다.

  * *직접 제약 조건 논리 중지: 수동 제약 조건* 개체를 중지 (활성화/비활성화 논리를 실행 하지 않음) 하도록 설정 하는 경우 HandConstraintPalmUp을 비활성화 하는 대신 UpdateSolver를 False로 설정 합니다.
    * 응시 기반 (또는 비-응시 기반)을 다시 연결 하는 논리를 사용 하도록 설정 하려면이 다음에 HandConstraintPalmUp () 함수를 호출 합니다. 그러면 계속 해 서 "Is코 루틴 Controller" 조건이 충족 되는지 확인 하 고 UpdateSolver를 True로 설정 (또는 개체가 비활성화 된 경우) 하는 것을 확인 합니다.
  * *직접 제약 조건 논리 시작*: 활성화 조건을 충족 하는지 여부에 따라 직접 제약 조건 개체를 다시 시작 하도록 설정 하려는 경우 SolverHandler의 UpdateSolver을 true로 설정 합니다.

* **논리** 다시 연결: 현재 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) SolverHandler의 UpdateSolver이 True 인지 여부에 관계 없이에서 대상 개체를 추적 된 지점에 자동으로 다시 연결할 수 있습니다. 이는 HandConstraintPalmUp의 StartWorldLockReattachCheckCoroutine () 함수를 호출 하 여 수행 됩니다 .이 함수는 세계에서 잠긴 후 (이 경우 실제로 SolverHandler의 UpdateSolver을 False로 설정 합니다.)

## <a name="see-also"></a>참조

* [Button](button.md)
* [메뉴 근처](near-menu.md)
