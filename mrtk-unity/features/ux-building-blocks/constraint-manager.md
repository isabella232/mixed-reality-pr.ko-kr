---
title: 제약 조건 관리자
description: MRTK의 제약 조건 관리자 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177551"
---
# <a name="constraint-manager"></a>제약 조건 관리자

제약 조건 관리자를 사용 하면 제약 조건 구성 요소 집합을 변환에 적용할 수 있습니다. 게임 개체에 연결 된 형식의 구성 요소를 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 고려할 수 있습니다.
기본적으로 제약 조건 관리자는 게임 개체에 연결 된 모든 [제약 조건 구성 요소](#transform-constraints) 를 자동으로 수집 하 여 처리 된 변환에 적용 합니다.
그러나 사용자는 적용 된 제약 조건 목록을 수동으로 구성 하 고 연결 된 제약 조건의 하위 집합만 적용 하도록 선택할 수 있습니다.

현재 다음 MRTK UX 요소는 제약 조건 관리자를 지원 합니다.

- [범위 제어](bounds-control.md)
- [개체 조작자](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Inspector 속성 및 필드

제약 조건 관리자는 다음과 같은 두 가지 모드로 작동할 수 있습니다.

- 자동 제약 조건 선택
- 수동 제약 조건 선택

### <a name="auto-constraint-selection"></a>자동 제약 조건 선택

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

제약 조건 관리자의 기본 모드, 자동 제약 조건 선택은 연결 된 모든 제약 조건 구성 요소와 [단추 이동](#go-to-component) 및 [제약 조건 추가 단추](#add-constraint-to-game-object)를 제공 합니다.

#### <a name="add-constraint-to-game-object"></a>게임 개체에 제약 조건 추가

이 단추를 사용 하면 제약 조건 관리자 검사기에서 직접 제약 조건 구성 요소를 추가할 수 있습니다. 프로젝트의 모든 제약 조건 형식은 여기에 표시 되어야 합니다. 자세한 정보는 [transform 제약 조건](#transform-constraints) 을 참조 하세요.

#### <a name="go-to-component"></a>구성 요소로 이동

개체에 있는 모든 제약 조건은 여기에 나열 커밋되지 *구성 요소 단추로 이동* 합니다. 이 단추를 클릭 하면 검사기가 선택 된 제약 조건 구성 요소로 스크롤되며 구성 될 수 있습니다.

### <a name="manual-constraint-selection"></a>수동 제약 조건 선택

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

제약 조건 관리자가 수동 모드로 설정 된 경우 제약 조건 목록에 연결 된 제약 조건만 처리 되어 변환에 적용 됩니다. 표시 된 목록에는 사용자가 선택한 제약 조건 뿐만 아니라 항목 [을](#go-to-component) 제거 하거나 추가 하는 단추 또는 옵션으로 이동 하는 것만 표시 됩니다.
수동 모드를 처음 사용 하는 경우 제약 조건 관리자는 사용 가능한 모든 구성 요소를 연결 된 제약 조건 구성 요소를 선택 하기 위한 시작 점으로 채웁니다.

### <a name="remove-entry"></a>항목 제거

이렇게 하면 수동으로 선택한 목록에서 항목이 제거 됩니다. 이 옵션은 game 개체에서 제약 조건 구성 요소를 제거 하지 않습니다. 제약 조건 구성 요소는이 구성 요소를 참조 하는 다른 구성 요소를 실수로 손상 시 키 지 않도록 항상 수동으로 제거 해야 합니다.

### <a name="add-entry"></a>항목 추가

항목 추가를 사용 하면 아직 수동 목록에 없는 사용 가능한 모든 제약 조건 구성 요소가 표시 되는 드롭다운이 열립니다. 항목을 클릭 하면 해당 구성 요소가 수동 제약 조건 선택 항목에 추가 됩니다.

### <a name="add-new-constraint"></a>새 제약 조건 추가

이 옵션을 선택 하면 선택한 형식의 구성 요소가 game 개체에 추가 되 고 새로 만든 제약 조건 구성 요소가 수동 제약 조건 목록에 추가 됩니다.

## <a name="transform-constraints"></a>변환 제약 조건

제약 조건을 사용 하 여 특정 방식으로 조작을 제한할 수 있습니다. 예를 들어 일부 응용 프로그램에는 회전이 필요할 수 있지만 개체는 수직으로도 유지 되어야 합니다. 이 경우를 `RotationAxisConstraint` 개체에 추가 하 고 y 축 회전으로 회전을 제한 하는 데 사용할 수 있습니다. MRTK는 아래에 설명 된 다양 한 제약 조건을 제공 합니다.

또한 새 제약 조건을 정의 하 고이를 사용 하 여 일부 응용 프로그램에 필요할 수 있는 고유한 조작 동작을 만들 수 있습니다. 이렇게 하려면에서 상속 하는 스크립트를 만들고 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) abstract `ConstraintType` 속성과 추상 메서드를 구현 `ApplyConstraint` 합니다. 개체에 새 제약 조건을 추가할 때 정의 된 방식으로 조작을 제한 해야 합니다. 또한이 새 제약 조건은 수동 모드의 제약 조건 관리자 [자동 선택](#auto-constraint-selection) 또는 [항목 추가](#add-entry) 드롭다운에서 표시 되어야 합니다.

MRTK에서 제공 하는 모든 제약 조건은 다음 속성을 공유 합니다.

#### <a name="hand-type"></a>손으로 형식

단방향, 두 가지 또는 두 종류의 조작에 제약 조건이 사용 되는지 여부를 지정 합니다. 이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.

- *단방향*: 제약 조건은 하나의 전달 조작 중에 사용 됩니다 (선택 하는 경우).
- 두 *개의 왼손*: 제약 조건이 선택 되어 있는 경우 두 개의 전달 조작이 사용 됩니다.

#### <a name="proximity-type"></a>근접 유형

제약 조건이 거의 모든 종류의 조작에 사용 되는지 여부를 지정 합니다. 이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.

- *Near*: 선택 하는 경우 거의 조작 하는 동안 제약 조건이 사용 됩니다.
- *Far*: 선택한 경우 제약 조건이 사용 됩니다.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

이 제약 조건이 개체에 연결 되 면 개체가 항상 사용자를 대상으로 하는 회전이 제한 됩니다. 이는 슬레이트 또는 패널에 유용 합니다. 의 속성은 다음과 같습니다 `FaceUserConstraint` .

#### <a name="face-away"></a>얼굴 떨어져

True 이면 개체가 사용자의 얼굴을 벗어납니다.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

이 제약 조건은 조작 된 개체와 조작 시작 시 다른 개체 변환 간의 거리를 수정 합니다. 이는 조작 된 개체에서 head 변환 까지의 거리를 수정 하는 것과 같은 동작에 유용 합니다. 의 속성은 다음과 같습니다 `FixedDistanceConstraint` .

#### <a name="constraint-transform"></a>제약 조건 변환

조작 된 개체의 거리가 고정 되는 다른 변환입니다. 카메라 변환이 기본값으로 설정 됩니다.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

이 제약 조건은 조작 중인 사용자와 조작 된 개체 간의 상대적 회전을 수정 합니다. 이 기능은 조작 된 개체가 조작을 시작할 때와 동일한 얼굴을 항상 사용자에 게 표시 하는 것을 슬레이트 하거나 패널에 유용 합니다. 에는 `FixedRotationToUserConstraint` 고유한 속성이 없습니다.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

이 제약 조건은 조작 되는 개체의 전역 회전을 수정 합니다. 이는 조작을 통해 회전을 필요한 하지 않아야 하는 경우에 유용할 수 있습니다. 에는 `FixedRotationToWorldConstraint` 고유한 속성이 없습니다.

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

이 제약 조건이 개체에 연결 된 경우 사용자의 개체 수에 관계 없이 사용자에 게 동일한 명백한 크기가 유지 됩니다 (즉, 사용자의 보기 필드와 동일한 비율을 차지 함). 이를 사용 하면 조작 하는 동안 슬레이트 또는 텍스트 패널을 읽을 수 있는 상태로 유지할 수 있습니다. 에는 `MaintainApparentSizeConstraint` 고유한 속성이 없습니다.

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

이 제약 조건을 사용 하 여 조작 된 개체를 이동할 수 있는 축을 따라 수정할 수 있습니다. 이는 평면의 표면 또는 선을 따라 개체를 조작 하는 데 유용할 수 있습니다. 의 속성은 다음과 같습니다 `MoveAxisConstraint` .

#### <a name="constraint-on-movement"></a>이동 시 제약 조건

이동을 방지 하는 축을 지정 합니다. 기본적으로 이러한 축은 로컬이 아닌 전역 이지만 아래에서 변경할 수 있습니다. 이 속성은 플래그 이기 때문에 원하는 수의 옵션을 선택할 수 있습니다.

- *X 축*: x 축 방향의 이동은 선택 된 경우 제약을 받습니다.
- *Y 축*: 선택 하면 y 축을 따라 이동 하는 것이 제한 됩니다.
- *Z 축*: 선택 하면 z 축 방향의 이동이 제한 됩니다.

#### <a name="use-local-space-for-constraint"></a>제약 조건에 로컬 공간 사용

True 인 경우 조작 된 개체의 로컬 변환 축에 대 한 상대를 제한 합니다. False(기본값).

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

이 제약 조건을 사용 하 여 조작 된 개체가 회전할 수 있는 축을 수정할 수 있습니다. 이는 조작 된 개체를 수직으로 유지 하지만 y 축 회전을 계속 허용 하는 데 유용할 수 있습니다 (예:). 의 속성은 다음과 같습니다 `RotationAxisConstraint` .

#### <a name="constraint-on-rotation"></a>회전에 대한 제약 조건

회전을 방지할 축을 지정합니다. 기본적으로 이러한 축은 로컬이 아닌 전역 축이지만 아래에서 변경할 수 있습니다. 이 속성은 플래그이므로 원하는 수의 옵션을 선택할 수 있습니다.

- *Y축:* 선택한 경우 y축에 대한 회전이 제한됩니다.
- *Z축:* 선택한 경우 z축에 대한 회전이 제한됩니다.
- *X축:* X축에 대한 회전이 선택되면 제한됩니다.

#### <a name="use-local-space-for-constraint"></a>제약 조건에 로컬 공간 사용

true인 경우 조작된 개체의 로컬 변환 축을 상대적으로 제한합니다. False(기본값).

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

이 제약 조건을 사용하면 조작된 개체의 배율에 대해 최소값과 최대값을 설정할 수 있습니다. 이 방법은 사용자가 너무 작거나 너무 큰 개체의 크기를 조정하지 못하게 하는 데 유용합니다. 의 `MinMaxScaleConstraint` 속성은 다음과 같습니다.

#### <a name="scale-minimum"></a>최소 크기 조정

조작하는 동안 최소 배율 값입니다.

#### <a name="scale-maximum"></a>최대 크기 조정

조작하는 동안 최대 배율 값입니다.

#### <a name="relative-to-initial-state"></a>초기 상태에 대한 상대

true이면 위의 값이 개체 초기 배율에 상대적인 것으로 해석됩니다. 그렇지 않으면 절대 배율 값으로 해석됩니다.
