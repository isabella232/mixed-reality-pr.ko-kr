---
title: 제약 조건 관리자
description: MRTK의 제약 조건 관리자 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f32f7321ec30f337e03d006f47fa92639796a74156483917331304811ea86a45
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198519"
---
# <a name="constraint-manager"></a>제약 조건 관리자

제약 조건 관리자를 사용하면 제약 조건 구성 요소 집합을 변환에 적용할 수 있습니다. 게임 개체에 연결된 형식의 구성 요소를 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 고려할 수 있습니다.
기본적으로 제약 조건 관리자는 게임 개체에 연결된 모든 [제약 조건 구성 요소를](#transform-constraints) 자동으로 수집하여 처리된 변환에 적용합니다.
그러나 사용자는 적용된 제약 조건 목록을 수동으로 구성하고 연결된 제약 조건의 하위 집합만 적용할 수 있도록 선택할 수 있습니다.

현재 다음 MRTK UX 요소는 제약 조건 관리자를 지원합니다.

- [경계 컨트롤](bounds-control.md)
- [개체 조작자](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>검사기 속성 및 필드

제약 조건 관리자는 다음 두 가지 모드로 작동할 수 있습니다.

- 자동 제약 조건 선택
- 수동 제약 조건 선택

### <a name="auto-constraint-selection"></a>자동 제약 조건 선택

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

제약 조건 관리자의 기본 모드인 자동 제약 조건 선택은 연결된 모든 제약 조건 구성 요소의 목록과 [단추로 이동](#go-to-component) 및 [제약 조건 추가 단추](#add-constraint-to-game-object)을 제공합니다.

#### <a name="add-constraint-to-game-object"></a>게임 개체에 제약 조건 추가

이 단추를 사용하면 제약 조건 관리자 검사자에서 직접 제약 조건 구성 요소를 추가할 수 있습니다. 프로젝트의 모든 제약 조건 형식은 여기에 표시되어야 합니다. 자세한 내용은 [변환 제약 조건을](#transform-constraints) 참조하세요.

#### <a name="go-to-component"></a>구성 요소로 이동

개체에 있는 모든 제약 조건은 *구성 요소로 이동* 단추와 함께 여기에 나열됩니다. 이 단추를 사용하면 검사기에서 선택한 제약 조건 구성 요소로 스크롤하여 구성할 수 있습니다.

### <a name="manual-constraint-selection"></a>수동 제약 조건 선택

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

제약 조건 관리자를 수동 모드로 설정하면 제약 조건 목록에 연결된 제약 조건만 처리되고 변환에 적용됩니다. 표시된 목록에는 사용자가 선택한 제약 조건만 표시되고 항목을 제거하거나 추가하는 단추 또는 옵션으로 [이동합니다.](#go-to-component)
수동 모드를 처음으로 사용하도록 설정하면 제약 조건 관리자가 연결된 제약 조건 구성 요소를 선택하기 위한 시작점으로 사용 가능한 모든 구성 요소가 목록을 채웁니다.

### <a name="remove-entry"></a>항목 제거

이렇게 하면 수동으로 선택한 목록에서 항목이 제거됩니다. 이 옵션은 게임 개체에서 제약 조건 구성 요소를 제거하지 않습니다. 이 구성 요소를 참조하는 다른 구성 요소를 실수로 중단하지 않도록 제약 조건 구성 요소를 항상 수동으로 제거해야 합니다.

### <a name="add-entry"></a>항목 추가

항목 추가는 아직 수동 목록에 없는 사용 가능한 모든 제약 조건 구성 요소를 보여 주는 드롭다운을 엽니다. 구성 요소가 수동 제약 조건 선택 항목에 추가되는 항목을 클릭합니다.

### <a name="add-new-constraint"></a>새 제약 조건 추가

이 옵션은 선택한 형식의 구성 요소를 게임 개체에 추가하고 새로 만든 제약 조건 구성 요소를 수동 제약 조건 목록에 추가합니다.

## <a name="transform-constraints"></a>변환 제약 조건

제약 조건은 어떤 방식으로든 조작을 제한하는 데 사용할 수 있습니다. 예를 들어 일부 애플리케이션은 회전이 필요할 수 있지만 개체를 수직으로 유지해야 할 수도 있습니다. 이 경우 개체에 를 `RotationAxisConstraint` 추가하고 회전을 y축 회전으로 제한하는 데 사용할 수 있습니다. MRTK는 다양한 제약 조건을 제공하며, 모두 아래에 설명되어 있습니다.

또한 새 제약 조건을 정의하고 이를 사용하여 일부 애플리케이션에 필요할 수 있는 고유한 조작 동작을 만들 수도 있습니다. 이렇게 하려면 에서 상속되는 스크립트를 만들고 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 추상 `ConstraintType` 속성 및 추상 `ApplyConstraint` 메서드를 구현합니다. 개체에 새 제약 조건을 추가하면 정의된 방식으로 조작을 제한해야 합니다. 이 새 제약 조건은 제약 조건 관리자 [자동 선택에도](#auto-constraint-selection) 표시되거나 수동 모드에서 항목 드롭다운을 [추가해야](#add-entry) 합니다.

MRTK에서 제공하는 모든 제약 조건은 다음 속성을 공유합니다.

#### <a name="hand-type"></a>손 유형

제약 조건이 한 손, 두 손 조작 또는 두 종류의 조작에 사용되는지 여부를 지정합니다. 이 속성은 플래그이므로 두 옵션을 모두 선택할 수 있습니다.

- *한 손:* 선택한 경우 한 손으로 조작하는 동안 제약 조건이 사용됩니다.
- *양손:* 선택한 경우 두 손으로 조작하는 동안 제약 조건이 사용됩니다.

#### <a name="proximity-type"></a>근접 유형

제약 조건이 근거리, 원거리 또는 두 종류의 조작에 사용되는지 여부를 지정합니다. 이 속성은 플래그이므로 두 옵션을 모두 선택할 수 있습니다.

- *Near:* 제약 조건은 선택된 경우 거의 조작하는 동안 사용됩니다.
- *Far*: 선택한 경우 원거리 조작 중에 제약 조건이 사용됩니다.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

이 제약 조건이 개체에 연결되면 개체가 항상 사용자를 향하도록 회전이 제한됩니다. 슬레이트 또는 패널에 유용합니다. 의 `FaceUserConstraint` 속성은 다음과 같습니다.

#### <a name="face-away"></a>Face Away

개체는 true인 경우 사용자와 얼굴을 맞대고 있습니다.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

이 제약 조건은 조작 시작 시 조작된 개체와 다른 개체 변환 사이의 거리를 수정합니다. 조작된 개체에서 헤드 변환까지의 거리를 수정하는 등의 동작에 유용합니다. 의 `FixedDistanceConstraint` 속성은 다음과 같습니다.

#### <a name="constraint-transform"></a>제약 조건 변환

조작된 개체가 고정된 거리를 가지는 다른 변환입니다. 기본값은 카메라 변환입니다.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

이 제약 조건은 조작되는 동안 사용자와 조작된 개체 간의 상대 회전을 수정합니다. 이는 조작된 개체가 조작을 시작할 때와 항상 동일한 얼굴을 사용자에게 표시하도록 하기 때문에 슬레이트 또는 패널에 유용합니다. 에는 `FixedRotationToUserConstraint` 고유한 속성이 없습니다.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

이 제약 조건은 조작된 개체가 조작되는 동안 전역 회전을 수정합니다. 이는 조작으로 회전을 하지 않아야 하는 경우에 유용할 수 있습니다. 에는 `FixedRotationToWorldConstraint` 고유한 속성이 없습니다.

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

이 제약 조건이 개체에 연결된 경우 개체가 사용자와 얼마나 떨어져 있든 관계없이 사용자에게 동일한 명백한 크기를 유지합니다(즉, 사용자 보기 필드의 동일한 비율을 차지함). 이는 슬레이트 또는 텍스트 패널을 조작하는 동안 읽을 수 있도록 하는 데 사용할 수 있습니다. 에는 `MaintainApparentSizeConstraint` 고유한 속성이 없습니다.

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

이 제약 조건을 사용하여 조작된 개체를 이동할 수 있는 축을 수정할 수 있습니다. 이는 평면 표면이나 선을 따라 개체를 조작하는 데 유용할 수 있습니다. 의 `MoveAxisConstraint` 속성은 다음과 같습니다.

#### <a name="constraint-on-movement"></a>이동에 대한 제약 조건

이동을 방지할 축을 지정합니다. 기본적으로 이러한 축은 로컬이 아닌 전역 축이지만 아래에서 변경할 수 있습니다. 이 속성은 플래그이므로 원하는 수의 옵션을 선택할 수 있습니다.

- *X축:* X축을 따라 이동하는 경우 이동이 제한됩니다.
- *Y축:* 선택한 경우 y축을 따라 이동이 제한됩니다.
- *Z축:* z축을 따라 이동하는 경우 이동이 제한됩니다.

#### <a name="use-local-space-for-constraint"></a>제약 조건에 로컬 공간 사용

true인 경우 조작된 개체의 로컬 변환 축을 기준으로 제한합니다. False(기본값).

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

이 제약 조건을 사용하여 조작된 개체를 회전할 수 있는 축을 수정할 수 있습니다. 예를 들어 조작된 개체를 수직으로 유지하지만 y축 회전을 허용하는 데 유용할 수 있습니다. 의 `RotationAxisConstraint` 속성은 다음과 같습니다.

#### <a name="constraint-on-rotation"></a>회전에 대한 제약 조건

회전을 방지할 축을 지정합니다. 기본적으로 이러한 축은 로컬이 아닌 전역 축이지만 아래에서 변경할 수 있습니다. 이 속성은 플래그이므로 원하는 수의 옵션을 선택할 수 있습니다.

- *Y축:* 선택한 경우 y축에 대한 회전이 제한됩니다.
- *Z축:* 선택한 경우 z축에 대한 회전이 제한됩니다.
- *X축:* X축에 대한 회전이 선택되어 있으면 제한됩니다.

#### <a name="use-local-space-for-constraint"></a>제약 조건에 로컬 공간 사용

true인 경우 조작된 개체의 로컬 변환 축을 기준으로 제한합니다. False(기본값).

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

이 제약 조건을 사용하면 조작된 개체의 배율에 대해 최소값과 최대값을 설정할 수 있습니다. 이 방법은 사용자가 너무 작거나 너무 큰 개체의 크기를 조정하지 못하게 하는 데 유용합니다. 의 `MinMaxScaleConstraint` 속성은 다음과 같습니다.

#### <a name="scale-minimum"></a>최소 크기 조정

조작하는 동안 최소 배율 값입니다.

#### <a name="scale-maximum"></a>최대 크기 조정

조작하는 동안의 최대 배율 값입니다.

#### <a name="relative-to-initial-state"></a>초기 상태에 대한 상대

true이면 위의 값이 개체 초기 배율에 상대적인 것으로 해석됩니다. 그렇지 않으면 절대 배율 값으로 해석됩니다.
