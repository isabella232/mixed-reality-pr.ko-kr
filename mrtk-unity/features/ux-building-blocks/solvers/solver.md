---
title: 솔버 개요
description: MRTK의 솔버 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity ,HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 솔버,
ms.openlocfilehash: bf9bbfe578ace576fca8870f038f145037a6838d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176455"
---
# <a name="solver-overview"></a>솔버 개요

![솔버 기본](../../images/solver/MRTK_Solver_Main.png)

솔버는 미리 정의된 알고리즘에 따라 개체의 위치 및 방향을 계산하는 방법을 용이하게 하는 구성 요소입니다. 예를 들어 사용자의 시선 응시 광선 투사가 현재 비추는 중인 표면에 개체를 배치할 수 있습니다.

또한, 구성 요소에 대한 업데이트 순서를 Unity에 지정할 수 있는 안정적인 방법이 없으므로 솔버 시스템은 이러한 변환 계산에 대한 작업 순서를 명확하게 정의합니다.

솔버는 다른 개체나 시스템에 개체를 연결하는 다양한 동작을 제공합니다. 다른 한가지 예는 카메라에 따라 사용자의 앞에 있는 태그얼롱 개체입니다. 솔버를 컨트롤러 및 개체에 연결하여 개체가 컨트롤러를 태그얼롱하도록 할 수도 있습니다. 모든 솔버를 안전하게 누적시킬 수 있습니다(예: 태그얼롱 동작 + 표면 자성 + 탄력).

## <a name="how-to-use-a-solver"></a>솔버를 사용하는 방법

솔버 시스템은 세 가지 범주의 스크립트로 구성됩니다.

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): 모든 솔버가 파생되는 기본 추상 클래스입니다. 상태 추적, 매개 변수 및 구현 다듬기, 자동 솔버 시스템 통합 및 업데이트 순서를 제공합니다.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): 추적할 참조 개체를 설정하고(예: 기본 카메라 변환, 손 광선 등) 솔버 구성 요소 수집을 처리하고 적절한 순서로 업데이트를 실행합니다.

세 번째 범주는 솔버 자체입니다. 다음 솔버는 기본 동작에 대한 구성 요소를 제공합니다.

* [`Orbital`](#orbital): 참조된 개체에서 지정된 위치 및 오프셋으로 잠급니다.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): 참조된 개체의 보기와 관련된 일정한 크기를 유지하도록 크기를 조정합니다.
* [`RadialView`](#radialview): 참조된 개체가 캐스팅하는 보기 콘 내에 개체를 유지합니다.
* [`Follow`](#follow): 참조된 개체의 사용자 정의 경계 집합 내에 개체를 유지합니다.
* [`InBetween`](#inbetween): 추적된 두 개체 사이에 개체를 유지합니다.
* [`SurfaceMagnetism`](#surfacemagnetism): 세계의 표면에 광선을 투사하고 개체를 해당 표면에 정렬합니다.
* [`DirectionalIndicator`](#directionalindicator): 방향 표시기로 개체의 위치와 방향을 결정합니다. SolverHandler 추적 대상의 참조 지점에서 이 표시기는 제공된 DirectionalTarget 방향으로 표시됩니다.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): 가속/속도/마찰을 적용하여 다른 솔버/구성 요소에 의해 이동되는 개체의 탄력과 탄성을 시뮬레이션합니다.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): GameObject와 손이 교차하지 않는 영역에서 손을 따르도록 개체를 제한합니다. 메뉴 등과 같이 손이 제한된 대화형 콘텐츠에 유용합니다. 이 솔버는 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand)와 함께 작동하지만 [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController)에서도 작동합니다.
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): HandConstraint에서 파생되지만 활성화 전에 손바닥이 사용자를 향하고 있는지 테스트하는 로직이 포함되어 있습니다. 이 솔버는 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 컨트롤러에서만 작동하며 다른 컨트롤러 유형에서는 이 솔버가 기본 클래스처럼 작동합니다.

솔버 시스템을 사용하기 위해 위에 나열된 구성 요소 중 하나를 GameObject에 추가하기만 하면 됩니다. 모든 솔버에는 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)가 필요하므로 Unity에서 자동으로 생성됩니다.

> [!NOTE]
> 솔버 시스템 사용 방법의 예는 **SolverExamples.scene** 파일에서 찾을 수 있습니다.

## <a name="how-to-change-tracking-reference"></a>추적 참조를 변경하는 방법

[`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 구성 요소의 *Tracked Target Type*(추적 대상 유형) 속성은 모든 솔버가 알고리즘을 계산하는 데 사용할 참조 지점을 정의합니다. 예를 들어 단순한 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 구성 요소가 있는 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)의 값 유형은 어떤 표면에 비추는지를 해결하기 위해 사용자의 시선 응시 방향으로 헤드에서 광선 투사를 발생시킵니다. `TrackedTargetType` 속성의 잠재적 값은 다음과 같습니다.

* *Head*: 참조 지점이 기본 카메라의 변환입니다.
* *ControllerRay*: 참조 지점이 선 광선의 방향을 가리키는 컨트롤러의 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) 변환입니다(예: 모션 컨트롤러 또는 핸드 컨트롤러의 포인터 원점).
  * `TrackedHandedness` 속성을 사용하여 사용하는 손 기본 설정을 선택합니다(예: 왼쪽, 오른쪽, 둘 다).
* *HandJoint*: 참조 지점이 특정 손 관절의 변환입니다.
  * `TrackedHandedness` 속성을 사용하여 사용하는 손 기본 설정을 선택합니다(예: 왼쪽, 오른쪽, 둘 다).
  * `TrackedHandJoint` 속성을 사용하여 활용할 관절 변환을 결정합니다.
* *CustomOverride*: 지정된 `TransformOverride`의 참조 지점입니다.

> [!NOTE]
> *ControllerRay* 및 *HandJoint* 유형 모두에 대해 솔버 처리기는 먼저 왼쪽 컨트롤러/손 변환을 제공한 다음 전자를 사용할 수 없거나 `TrackedHandedness` 속성이 달리 지정하지 않은 경우 오른쪽을 제공합니다.

![솔버가 추적한 개체](../../images/solver/TrackedObjectType-Example.gif) 
*각 TrackedTargetType과 관련된 다양한 속성의 예*

> [!IMPORTANT]
> 대부분의 솔버는 `SolverHandler`에서 제공하는 추적된 변환 대상의 앞으로 벡터를 사용합니다. *손 관절* 추적 대상 유형을 사용하는 경우 손바닥 관절의 전방 벡터가 손바닥이 아닌 손가락을 가리킬 수 있습니다. 이는 손 관절 데이터를 제공하는 플랫폼에 따라 달라집니다. 입력 시뮬레이션 및 Windows Mixed Reality의 경우 손바닥을 통해 위로 향하는 *위 벡터* 입니다(예: 녹색 벡터는 위로, 파란색 벡터는 앞으로).
>
> ![앞으로 위로 벡터](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> 이를 극복하려면 `SolverHandler`의 *추가 회전* 속성을 **<90, 0, 0>** 으로 업데이트합니다. 이렇게 하면 솔버에 제공된 앞으로 벡터가 손바닥을 통해 손에서 바깥쪽으로 향하게 됩니다.
>
> ![추가 회전](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> 또는 *컨트롤러 광선* 추적 대상 유형을 사용하여 손으로 가리키는 유사한 동작을 얻습니다.

## <a name="how-to-chain-solvers"></a>솔버를 연결하는 방법

동일한 GameObject에 여러 `Solver` 구성 요소를 추가하여 알고리즘을 연결할 수 있습니다. `SolverHandler` 구성 요소는 동일한 GameObject의 모든 솔버 업데이트를 처리합니다. 기본적으로 `SolverHandler`는 시작 시 `GetComponents<Solver>()`를 호출하여 검사기에 나타나는 순서대로 솔버를 반환합니다.

또한 *업데이트된 연결 변환* 속성을 true로 설정하면 해당 `Solver`에게 계산된 위치, 방향 및 배율을 모든 솔버가 액세스할 수 있는 중간 변수에 저장하라고 지시합니다(예: `GoalPosition`). false인 경우 `Solver`는 GameObject의 변환을 직접 업데이트합니다. 다른 솔버는 중간 위치에 변환 속성을 저장하여 중간 변수부터 계산을 수행할 수 있습니다. Unity가 gameObject.transform에 대한 업데이트가 동일한 프레임 내에서 누적되도록 허용하지 않기 때문입니다.

> [!NOTE]
> 개발자는 `SolverHandler.Solvers` 속성을 직접 설정하여 솔버의 실행 순서를 수정할 수 있습니다.

## <a name="how-to-create-a-new-solver"></a>새 솔버를 만드는 방법

모든 솔버는 추상 기본 클래스 [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver)에서 상속해야 합니다. 솔버 확장의 기본 요구 사항에는 `SolverUpdate` 메서드 재정의가 포함됩니다. 이 메서드에서 개발자는 상속된 `GoalPosition`, `GoalRotation` 및 `GoalScale` 속성을 원하는 값으로 업데이트해야 합니다. 또한 일반적으로 소비자가 원하는 참조 프레임으로 `SolverHandler.TransformTarget`을 활용하는 것이 중요합니다.

아래에 제공된 코드는 첨부된 개체를 `SolverHandler.TransformTarget`의 2m 앞에 배치하는 `InFront`라는 새 솔버 구성 요소의 예를 제공합니다. 소비자가 `SolverHandler.TrackedTargetType`을 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)로 설정하면 `SolverHandler.TransformTarget`이 카메라 변환이 되므로 이 솔버는 프레임마다 사용자의 시선 응시의 2m 앞에 연결된 GameObject를 배치합니다.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>솔버 구현 가이드

### <a name="common-solver-properties"></a>일반적인 솔버 속성

모든 솔버 구성 요소에는 코어 솔버 동작을 제어하는 동일한 속성의 코어 집합이 있습니다.

*다듬기* 가 사용하도록 설정된 경우 솔버는 시간이 지남에 따라 GameObject의 변환을 계산된 값으로 점진적으로 업데이트합니다. 이 변경의 속도는 모든 변환 구성 요소의 *LerpTime* 속성에 의해 결정됩니다. 예를 들어 *MoveLerpTime* 값이 높을수록 프레임 간의 이동 증가가 느려집니다.

*MaintainScale* 이 사용하도록 설정된 경우 솔버는 GameObject의 기본 로컬 배율을 사용합니다.

![코어 솔버 속성](../../images/solver/GeneralSolverProperties.png)  
*모든 솔버 구성 요소에서 상속되는 공통 속성*

### <a name="orbital"></a>궤도

[`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) 클래스는 태양계의 행성처럼 작동하는 태그얼롱 구성 요소입니다. 이 솔버는 연결된 GameObject가 추적된 변환 주위를 공전하게 합니다. 따라서 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)의 *추적 대상 유형* 이 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)로 설정되면 GameObject가 고정 오프셋이 적용되어 사용자의 헤드 주위를 공전합니다.

개발자는 이 고정 오프셋을 수정하여 메뉴 또는 기타 장면 구성 요소를 사용자 주변의 눈 높이나 허리 높이 등으로 유지할 수 있습니다. 이는 *로컬 오프셋* 및 *월드 오프셋* 속성을 수정하여 수행됩니다. *방향 유형* 속성은 개체가 원래 회전을 유지해야 하거나 항상 카메라를 향해야 하거나 위치를 제어하는 변환이 무엇이든 직면해야 하는 경우 개체에 적용되는 회전을 결정합니다.

![궤도 예](../../images/solver/OrbitalExample.png)  
*궤도 예*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView)는 사용자 보기의 절두체 내에 GameObject의 특정 부분을 유지하는 또 다른 태그얼롱 구성 요소입니다.

*최소 및 최대 보기 정도* 속성은 GameObject의 일부가 항상 보기에 있어야 하는 크기를 결정합니다.

*최소 및 최대 거리* 속성은 GameObject가 사용자로부터 얼마나 멀리 떨어져 있어야 하는지를 결정합니다. 예를 들어 *최소 거리* 가 1m인 GameObject를 향해 걸어 가면 GameObject가 사용자에게 1m 이상 가까워지지 않도록 멀리 밀려납니다.

일반적으로 [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView)는 구성 요소가 사용자의 시선을 따르도록 *추적된 대상 유형* 이 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)로 설정된 것과 함께 사용됩니다. 그러나 이 구성 요소는 *추적된 대상 유형* 의 *"보기"* 에서 유지되도록 작동할 수 있습니다.

![RadialView 예](../../images/solver/RadialViewExample.png)  
*RadialView 예*

### <a name="follow"></a>팔로우

[`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) 클래스는 로컬 전방 축을 기준으로 추적된 대상 앞에 요소를 배치합니다. 요소는 느슨하게 제한(즉, 태그얼롱)될 수 있습니다. 따라서 추적 대상이 사용자 정의된 범위를 벗어나 이동할 때까지 따르지 않습니다.

RadialView 솔버와 유사하게 작동하며 *최대 수평 및 수직 뷰 각도* 를 관리하기 위한 추가 컨트롤과 개체의 *방향* 을 변경하는 메커니즘이 있습니다.

![팔로우 속성](../../images/solver/FollowExample.png)  
*팔로우 속성*

![팔로우 장면 예](../../images/solver/FollowExampleScene.gif)  
*팔로우 장면 예(Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

[`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 클래스는 두 변환 사이에 연결된 GameObject를 유지합니다. 이 두 변환 엔드포인트는 GameObject의 자체 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) *추적 대상 유형* 및 [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 구성 요소의 *두 번째 추적 대상 유형* 속성에 의해 정의됩니다. 일반적으로 두 유형 모두 [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride)로 설정되고 결과 `SolverHandler.TransformOverride` 및 `InBetween.SecondTransformOverride` 값은 두 개의 추적된 엔드포인트로 설정됩니다.

런타임 시 [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 구성 요소는 *두 번째 추적 대상 유형* 및 *두 번째 변환 재정의* 속성을 기반으로 또 다른 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 구성 요소를 만듭니다.

`PartwayOffset`은 두 변환 사이의 선을 따라 개체가 중간에 0.5, 첫 번째 변환에 1.0, 두 번째 변환에 0.0으로 배치될 위치를 정의합니다.

![InBetween 예](../../images/solver/InBetweenExample.png)  
*InBetween 솔버를 사용하여 두 변환 사이에 개체를 유지하는 예*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism)은 표면의 설정된 LayerMask에 대해 광선 투사를 수행하고 해당 접촉 지점에 GameObject를 배치하는 방식으로 작동합니다.

*표면 법선 오프셋* 은 GameObject를 표면에 비추는 지점에서 표면으로부터 법선 방향으로 설정된 거리(미터 단위)에 배치합니다.

반대로 *표면 광선 오프셋* 은 GameObject를 표면에서 미터 단위로 설정된 거리에 배치하지만 수행된 광선 투사의 반대 방향에 배치합니다. 따라서 광선 투사가 사용자의 시선인 경우 GameObject는 표면에 비추는 지점에서 카메라까지 선을 따라 더 가깝게 이동됩니다.

*방향 모드* 는 표면의 법선과 관련하여 적용할 회전 유형을 결정합니다.

* *없음* - 회전이 적용되지 않습니다.
* *TrackedTarget* - 개체가 광선 투사를 구동하는 추적된 변환을 향합니다.
* *SurfaceNormal* - 개체가 표면에 비추는 지점에서 법선을 기준으로 정렬됩니다.
* *Blended* - 개체가 표면에 비추는 지점에서 법선을 기준으로 정렬되고 추적된 변환을 향하는 것을 기준으로 정렬됩니다.

연결된 GameObject가 *없음* 이외의 모드에서 수직으로 유지되도록 하려면 *방향을 세로로 유지* 를 사용하도록 설정합니다.

> [!NOTE]
> *방향 모드* 가 *혼합* 으로 설정된 경우 *방향 혼합* 속성을 사용하여 회전 계수 간의 균형을 제어합니다. 0\.0 값은 *TrackedTarget* 모드에 의해 완전히 구동되는 방향을 가지며 1.0 값은 *SurfaceNormal* 에 의해 완전히 구동되는 방향을 갖습니다.

![SurfaceMagnetism 예](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>비출 수 있는 표면 결정

GameObject에 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 구성 요소를 추가할 때 충돌체가 있는 경우 GameObject와 그 하위 계층을 고려하는 것이 중요합니다. 구성 요소는 다양한 형식의 광선 투사를 수행하여 어떤 표면이 자체적으로 "자성"의 성질을 가지는지 결정하는 방식으로 작동합니다. 솔버 GameObject가 `SurfaceMagnetism`의 `MagneticSurfaces` 속성에 나열된 계층 중 하나에 충돌체를 가지고 있는 경우, 광선 투사가 스스로 비춰 GameObject가 자체 충돌체 지점에 연결될 수 있습니다. 이 이상한 동작은 기본 GameObject와 모든 하위 항목을 *광선 투사 무시* 계층으로 설정하거나 `MagneticSurfaces` LayerMask 배열을 적절하게 수정하여 피할 수 있습니다.

반대로 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject는 `MagneticSurfaces` 속성에 나열되지 않은 계층의 표면과 충돌하지 않습니다. 일반적으로 모든 원하는 표면을 전용 계층(즉, *표면*)에 배치하고 `MagneticSurfaces` 속성을 이 계층로만 설정하는 것이 좋습니다.  *기본값* 또는 *모두* 를 사용하면 UI 구성 요소 또는 커서가 솔버에 기여할 수 있습니다.

마지막으로 `MaxRaycastDistance` 속성 설정보다 더 멀리 있는 표면은 `SurfaceMagnetism` 광선 투사에서 무시됩니다.

### <a name="directionalindicator"></a>DirectionalIndicator

[`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) 클래스는 공간에서 원하는 지점의 방향으로 자체적으로 향하는 태그얼롱 구성 요소입니다.

[`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)의 *추적된 대상 유형* 이 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)로 설정된 경우 가장 일반적으로 사용됩니다. 이러한 방식으로 [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) 솔버가 있는 UX 구성 요소는 사용자가 공간에서 원하는 지점을 보도록 안내합니다.

공간에서 원하는 지점은 *방향 대상* 속성을 통해 결정됩니다.

사용자가 방향 대상을 볼 수 있거나 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)에 설정된 참조 프레임이 무엇이든 이 솔버는 그 아래에 있는 모든 [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) 구성 요소를 사용하지 않도록 설정합니다. 표시되지 않는 경우 모든 항목이 표시기에 대해 사용하도록 설정됩니다.

표시기의 크기는 사용자가 FOV에서 *방향 대상* 을 가깝게 캡처할수록 줄어듭니다.

* *최소 표시기 배율* - 표시기 개체의 최소 배율
* *최대 표시기 배율* - 표시기 개체의 최대 배율

* *표시 배율* - *방향 대상* 지점을 볼 수 있는지 여부를 결정하는 FOV를 늘리거나 줄이는 승수
* *보기 오프셋* - 참조 프레임의 관점(예: 카메라 가능)에서 이 속성은 표시기 방향에서 개체가 뷰포트의 중심에서 떨어져 있는 정도를 정의합니다.

![방향 표시기 속성](../../images/solver/DirectionalIndicatorExample.png)  
*방향 표시기 속성*

![방향 표시기 장면 예](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*방향 표시기 장면 예(Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>HandConstraint 및 HandConstraintPalmUp이 있는 손 메뉴

![손 메뉴 UX 예](../../images/solver/MRTK_UX_HandMenu.png)

[`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 동작은 추적된 개체를 손으로 제한된 콘텐츠(예: 손 UI, 메뉴 등)에 안전한 지역으로 제한하는 솔버를 제공합니다. 안전 지역은 손으로 교차하지 않는 영역으로 간주됩니다. 손바닥이 사용자를 향하고 있을 때 솔버 추적 개체를 활성화하는 일반적인 동작을 보여 주기 위해 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp)이라는 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint)의 파생 클래스도 포함됩니다.

손 제한 솔버를 사용하여 손 메뉴를 만드는 예는 [손 메뉴 페이지를 참조하세요](../hand-menu.md).

## <a name="see-also"></a>참조

* [손 추적](../../input/hand-tracking.md)
* [응시](../../input/gaze.md)
