---
title: 손 메뉴
description: MRTK의 손 메뉴 예제 장면
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, HandMenu,
ms.openlocfilehash: ecf05b687c52dab68302b9b66b3890aca31b5635b803084abd6845f31de974e0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226508"
---
# <a name="hand-menu"></a>손 메뉴

![손 메뉴 UX 예](../images/solver/MRTK_UX_HandMenu.png)

손 메뉴를 사용하면 자주 사용되는 함수에 대해 직접 연결된 UI를 빠르게 가져올 수 있습니다. 다른 개체와 상호 작용하는 동안 잘못된 활성화를 방지하기 위해 손 메뉴에는 '플랫 핸드 필요' 및 '응시 활성화 사용'과 같은 옵션이 제공됩니다. 원치 않는 활성화를 방지하려면 이러한 옵션을 사용하는 것이 좋습니다.

## <a name="hand-menu-examples"></a>손 메뉴 예제

**HandMenuExamples.unity** 장면의 폴더 아래에 ``MRTK/Examples/Demos/HandTracking/Scenes`` 있습니다. 실행 중이면 장면에 현재 선택한 메뉴 유형만 활성화됩니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

폴더 아래에서 이러한 손 메뉴 프리팹을 찾을 수 ``MRTK/Examples/Demos/HandTracking/Prefabs`` 있습니다.

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop 및 HandMenu_Medium_HideOnHandDrop

이 두 예제는 단순히 MenuContent 개체를 활성화하고 비활성화하여 **OnFirstHandDetected()** 및 **OnLastHandLost()** 이벤트에 메뉴를 표시하고 숨깁니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

더 긴 상호 작용 시간이 필요한 더 복잡한 메뉴의 경우 메뉴를 세계 잠금으로 잠그는 것이 좋습니다. 이 예제에서 사용자는 **OnFirstHandDetected()** 및 **OnLastHandLost()** 이벤트에서 MenuContent를 활성화하고 비활성화하는 것 외에도 메뉴를 잡고 끌어와서 메뉴를 세계 잠금으로 만들 수 있습니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

백플레이트의 `ManipulationHandler` 는 잡기 가능하고 이동 가능하게 만듭니다. **Manipulation Started** 이벤트에서 **SolverHandler.UpdateSolvers가** 비활성화되어 메뉴를 세계 잠금으로 잠급니다. 또한 작업이 완료되면 사용자가 메뉴를 닫을 수 있도록 **닫기** 단추가 표시됩니다. **Manipulation Ended** 이벤트에서 **HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine을** 호출하여 사용자가 손 등을 들어와서 메뉴를 다시 가져올 수 있도록 합니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

**닫기** 단추는 **SolverHandler.UpdateSolvers를** 다시 활성화하고 **MenuContent** 를 숨깁니다.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

이 예제는 HandMenu_Large_WorldLock_On_GrabAndPull 비슷합니다. 유일한 차이점은 메뉴가 손 놓기 시 자동으로 세계로 잠겨 있다는 것입니다. 이 작업은 **단순히 OnLastHandLost()** 이벤트에서 MenuContent를 숨기지 않고 수행합니다. 잡기 & 끌어오기 동작은 HandMenu_Large_WorldLock_On_GrabAndPull 예제와 동일합니다.

## <a name="scripts"></a>스크립트

[`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 동작은 추적된 개체를 손으로 제한된 콘텐츠(예: 손 UI, 메뉴 등)에 안전한 지역으로 제한하는 솔버를 제공합니다. 안전 지역은 손으로 교차하지 않는 영역으로 간주됩니다. 손바닥이 사용자를 향하고 있을 때 솔버 추적 개체를 활성화하는 일반적인 동작을 보여 주기 위해 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp)이라는 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint)의 파생 클래스도 포함됩니다.

추가 설명서는 각 속성에 사용할 수 있는 도구 팁을 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 참조하세요. 아래에는 몇 가지 속성이 더 자세히 정의되어 있습니다.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **금고 영역:** 안전 영역은 콘텐츠를 제한할 위치를 지정합니다. 손과 겹치지 않도록 콘텐츠를 Ulnar 쪽에 배치하고 상호 작용 품질을 개선하는 것이 좋습니다. 금고 영역은 평면 또는 직각으로 프로젝션된 손 방향을 카메라 보기로 가져와서 손 주위의 경계 상자에 대해 광선 캐스팅하여 계산됩니다. 금고 영역은 에서 작동하도록 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 정의되지만 다른 컨트롤러 유형에서도 작동합니다. 각 안전 영역이 서로 다른 컨트롤러 유형에서 무엇을 나타내는지 살펴보는 것이 좋습니다.

* **카메라를 향할 때까지 손 따르기** 이 활성 상태에서 해결기는 메뉴가 응시에 충분히 맞춰질 때까지 손 회전을 따르며, 이때 카메라를 향합니다. 이는 Solver의 GazeAlignment 각도가 변경됨에 따라 HandConstraintSolver의 SolverRotationBehavior를 LookAtTrackedObject에서 LookAtMainCamera로 변경하여 작동합니다.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **활성화 이벤트:** 현재 는 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 4개의 활성화 이벤트를 트리거합니다. 이러한 이벤트는 다양한 조합으로 사용하여 고유한 동작을 만들 수 있습니다. [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 이러한 동작의 예는 아래의 HandBasedMenuExample 장면을 `MRTK/Examples/Demos/HandTracking/Scenes/` 참조하세요.

  * *OnHandActivate*: 손에서 IsHandActive 메서드를 충족할 때 트리거됩니다.
  * *OnHandDeactivate*: IsHandActive 메서드가 더 이상 충족되지 않을 때 트리거됩니다.
  * *OnFirstHandDetected*: 손 추적 상태가 보기에 없는 손에서 보기의 첫 번째 손으로 변경될 때 발생합니다.
  * *OnLastHandLost*: 손 추적 상태가 보기의 한 손에서 보기에 있는 손 없음으로 변경되면 발생합니다.

* **Solver 활성화/비활성화 논리:** 현재 논리 활성화 및 비활성화에 대한 권장 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 사항은 개체를 사용하지 않도록 설정/활성화하는 대신 SolverHandler의 UpdateSolver 값을 사용하여 활성화하는 것입니다. 연결된 메뉴의 ManipulationHandler "OnManipulationStarted/Ended" 이벤트 후에 트리거되는 편집기 기반 후크를 통해 예제 장면에서 볼 수 있습니다.

  * *손 제약 조건 논리 중지:* 손 제약된 개체를 중지하도록 설정하려고 할 때(활성화/비활성화 논리를 실행하지 않을 뿐만 아니라) HandConstraintPalmUp을 사용하지 않도록 설정하는 대신 UpdateSolver를 False로 설정합니다.
    * 응시 기반(또는 응시 기반이 아닌) 다시 연결 논리를 사용하도록 설정하려면 다음으로 HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine() 함수를 호출합니다. 그러면 코루틴이 트리거되고 "IsValidController" 조건이 충족되는지 계속 확인하고 UpdateSolver가 True이면(또는 개체가 비활성화됨)
  * *손 제약 조건 논리 시작:* 손 제약된 개체가 활성화 조건을 충족하는지 여부에 따라 다시 손을 따라 시작하도록 설정하려고 할 때 SolverHandler의 UpdateSolver를 true로 설정합니다.

* **논리 다시 연결:** 현재 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 는 SolverHandler의 UpdateSolver가 True인지 여부에 관계없이 대상 개체를 추적된 지점에 자동으로 다시 연결할 수 있습니다. 이 작업은 World-Locked가 적용된 후 HandConstraintPalmUp의 StartWorldLockReattachCheckCoroutine() 함수를 호출하여 수행됩니다(이 경우 SolverHandler의 UpdateSolver를 False로 효과적으로 설정).

## <a name="see-also"></a>추가 정보

* [Button](button.md)
* [Near 메뉴](near-menu.md)
