---
title: 개체 조작자
description: MRTK에서 개체 조작자를 사용 하는 방법
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 개체 조작
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176650"
---
# <a name="object-manipulator"></a>개체 조작자

![개체 조작자](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*Objectmanipulator* 는 이전에 *ManipulationHandler* 에서 발견 된 조작 동작에 대 한 새 구성 요소입니다. 개체 조작자를 사용 하면 다양 한 기능을 향상 시키고 단순화 수 있습니다. 이 구성 요소는 조작 처리기의 대체 항목으로, 사용 되지 않습니다.

*Objectmanipulator* 스크립트를 사용 하면 한 두 개의 손을 사용 하 여 개체를 이동 가능 하 고 확장 가능 하며 rotatable 수 있습니다. 개체 조작자를 구성 하 여 개체가 다양 한 입력에 응답 하는 방식을 제어할 수 있습니다. 스크립트는 HoloLens 2 부분 HoloLens HoloLens 2을 사용 하는 것과 같은 대부분의 상호 작용에서 작동 해야 합니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>개체 조작자를 사용 하는 방법

개체 조작자를 사용 하려면 먼저 `ObjectManipulator` GameObject에 스크립트 구성 요소를 추가 합니다. Grabbable 범위와 일치 하는 개체에 collider도 추가 해야 합니다.

개체가 거의 유사 하 게 하는 손 모양 입력에 응답 하도록 하려면 `NearInteractionGrabbable` 스크립트도 추가 합니다.

Rigidbody 구성 요소를 개체에 추가 하 여 개체 조작자에 대해 물리학 동작을 사용 하도록 설정할 수 있습니다. 이 구성 요소를 추가 하 여 사용 하도록 설정 된 물리학 동작은 [*물리학 및 충돌*](#physics-and-collisions)에서 더 자세히 설명 합니다.

또한 조작 [제약 조건 구성 요소](constraint-manager.md#transform-constraints) 를 개체에 추가 하 여 조작을 제한할 수 있습니다. 이러한 구성 요소는 조작 작업을 수행 하 고 조작 동작을 변경 하는 특별 한 구성 요소입니다.

![Unity 편집기에서 조작 처리기 사용](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Inspector 속성 및 필드

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>일반 속성

#### <a name="host-transform"></a>호스트 변환

조작할 개체 변환입니다. 구성 요소의 개체에 대 한 기본값입니다.

#### <a name="manipulation-type"></a>조작 유형

하나 또는 두 개의 손을 사용 하 여 개체를 조작할 수 있는지 여부를 지정 합니다. 이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.

- *단방향*: 선택 하는 경우 하나의 전달 조작이 가능 합니다.
- *두 번*: 선택 하는 경우 두 개의 전달 조작이 가능 합니다.

#### <a name="allow-far-manipulation"></a>먼 조작을 허용 합니다.

포인터와의 먼 상호 작용을 사용 하 여 조작을 수행할 수 있는지 여부를 지정 합니다.

### <a name="one-handed-manipulation-properties"></a>단일 전달 조작 속성

#### <a name="one-hand-rotation-mode-near"></a>가까운 쪽 회전 모드

개체가 가까이 grabbed 때 동작 하는 방법을 지정 합니다. 이러한 옵션은 트레일러 식에만 적용 됩니다.

- *개체 중심 회전*: 개체는 손 모양에 대 한 회전을 사용 하 여 회전 하지만 개체 중심점은 회전 합니다. 개체는 회전할 때 보다 작게 표시 되지만 손 개체와 개체 간에 연결이 끊어질 수 있습니다. 먼 상호 작용에 더 유용 합니다.
- *지점에 대 한 회전*: 엄지 단추와 인덱스 손가락 사이의 잡기 지점에 대 한 손 모양으로 개체를 회전 합니다. 개체를 직접 보유 하 고 있는 것 처럼 느껴질 수 있습니다.

#### <a name="one-hand-rotation-mode-far"></a>한 손으로 회전 모드 멀리

개체를 grabbed 때 개체의 동작을 지정 합니다. 이러한 옵션은 트레일러 식에만 적용 됩니다.

- *개체 중심 회전*: 손 모양에 대 한 회전을 사용 하 여 개체를 회전 합니다. 개체가 회전할 때 개체 센터가 이동 하지 않고 거리를 검사 하는 데 유용 합니다.
- *지점* 회전: 손 모양 회전을 사용 하 여 개체를 회전 하지만 포인터 광선 적중 지점에 대해 회전 합니다. 검사에 유용 합니다.

### <a name="two-handed-manipulation-properties"></a>두 개의 전달 조작 속성

#### <a name="two-handed-manipulation-type"></a>두 개의 전달 조작 형식

두 손을 조작 하 여 개체를 변환할 수 있는 방법을 지정 합니다. 이 속성은 플래그 이기 때문에 원하는 수의 옵션을 선택할 수 있습니다.

- *이동*: 선택 하면 이동이 허용 됩니다.
- *크기 조정*: 선택 하는 경우에는 크기 조정을 사용할 수 있습니다.
- *회전*: 선택한 경우 회전이 허용 됩니다.

![조작 처리기](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>제약 조건

#### <a name="enable-constraints"></a>제약 조건 사용

이 설정은 연결 된 [제약 조건 관리자](constraint-manager.md)를 사용 하도록 설정 합니다. 변환 변경 내용은 선택한 [제약 조건 관리자](constraint-manager.md)에 등록 된 제약 조건에 의해 처리 됩니다.

#### <a name="constraint-manager"></a>제약 조건 관리자

드롭다운에서 연결 된 [제약 조건 관리자](constraint-manager.md)를 선택할 수 있습니다. 개체 조작자는 항상 [제약 조건 관리자](constraint-manager.md) 가 연결 되어 있는지 확인 합니다.
동일한 유형의 여러 구성 요소가 unity의 동일한 이름에 표시 됩니다. 동일한 개체에서 여러 제약 조건 관리자를 쉽게 구분할 수 있도록 사용 가능한 옵션은 선택한 제약 조건 관리자 (수동 또는 자동 제약 조건 선택)의 구성에 대 한 힌트를 표시 합니다.

#### <a name="go-to-component"></a>구성 요소로 이동

제약 조건 관리자 선택 항목에는 *구성 요소* 단추와 함께 제공 됩니다. 이 단추를 클릭 하면 검사기가 선택 된 구성 요소로 스크롤되며 구성 될 수 있습니다.

### <a name="physics"></a>Physics

이 섹션의 설정 개체에 RigidBody 구성 요소가 있는 경우에만 표시 됩니다.

#### <a name="release-behavior"></a>릴리스 동작

조작 된 개체가 릴리스할 때 유지 해야 하는 물리적 속성을 지정 합니다. 이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.

- *속도 유지*: 개체가 해제 되 면이 옵션을 선택 하면 선형 속도를 유지 합니다.
- *Angular 속도 유지*: 개체가 해제 되 면이 옵션을 선택 하면 각도의 속도를 유지 합니다.

#### <a name="use-forces-for-near-manipulation"></a>거의 조작 하기 위해 강제 사용

거의 조작을 수행할 때 물리 힘이 개체를 이동 하는 데 사용 되는지 여부입니다. 이를 *false* 로 설정 하면 개체가 사용자에 게 직접 연결 됩니다. 이를 true로 설정 하면 개체의 질량 및 관성이 *적용* 되지만 개체가 스프링을 통해 연결 된 것 처럼 보일 수 있습니다. 기본값은 *false* 입니다.

### <a name="smoothing"></a>다듬기

#### <a name="smoothing-far"></a>지금까지 다듬기

먼 상호 작용에 대해 프레임 수준 독립적인 다듬기가 사용 되는지 여부입니다. 지금까지 다듬기는 기본적으로 사용 하도록 설정 되어 있습니다.

#### <a name="smoothing-near"></a>가까이 다듬기

거의 상호 작용에 대해 프레임 수준 독립적인 다듬기가 사용 되는지 여부입니다. 가까운 다듬기는이 효과가 ' 연결 끊김 ' 상태로 인식 될 수 있으므로 기본적으로 사용 하지 않도록 설정 되어 있습니다.

#### <a name="smoothing-active"></a>활성 다듬기

더 이상 사용 되지 않으며 이후 버전에서 제거 될 예정입니다. 응용 프로그램은 SmoothingFar, SmoothingNear 또는 둘의 조합을 사용 해야 합니다.

#### <a name="move-lerp-time"></a>Lerp 시간 이동

이동에 적용할 다듬기의 양입니다. 0의 다듬기는 다듬기를 의미 하지 않습니다. 최 댓 값은 값이 변경 되지 않음을 의미 합니다.

#### <a name="rotate-lerp-time"></a>회전 lerp 시간

회전에 적용할 다듬기의 양입니다. 0의 다듬기는 다듬기를 의미 하지 않습니다. 최 댓 값은 값이 변경 되지 않음을 의미 합니다.

#### <a name="scale-lerp-time"></a>Lerp 시간 크기 조정

눈금에 적용할 다듬기의 양입니다. 0의 다듬기란 다듬기 없음을 의미합니다. 최대값은 값이 변경되지 않는 것을 의미합니다.

### <a name="manipulation-events"></a>조작 이벤트

조작 처리기는 다음 이벤트를 제공합니다.

- *OnManipulationStarted:* 조작이 시작될 때 발생합니다.
- *OnManipulationEnded:* 조작이 종료될 때 발생합니다.
- *OnHoverStarted:* 손/컨트롤러가 조작 가능한 마우스를 근거리 또는 멀리 가리키면 발생합니다.
- *OnHoverEnded:* 손/컨트롤러가 조작 가능한 가리키기를 거의 또는 멀리 가리키면 발생합니다.

조작에 대한 이벤트 발생 순서는 다음과 같습니다.

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

조작이 없으면 다음 화재 순서를 가진 가리키기 이벤트가 계속 발생합니다.

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>물리학 및 충돌

물리학 동작은 개체 조작자로 동일한 개체에 고정된 구성 요소를 추가하여 활성화할 수 있습니다. 이렇게 하면 위의 [릴리스 동작을](#release-behavior) 구성할 수 있게 될 뿐만 아니라 충돌도 가능합니다. 고정된 구성 요소가 없으면 조작 중에 충돌이 제대로 작동하지 않습니다.

- 조작된 개체와 정적 충돌체 간의 충돌(예: 충돌체는 있지만 고정된 충돌체가 없는 개체)은 작동하지 않으며 조작된 개체는 영향을 받지 않는 정적 충돌체를 통해 직접 전달됩니다.
- 조작된 개체와 고정된 개체 간의 충돌(즉, 충돌체와 고정된 표시가 둘 다 있는 개체)는 엄밀히 충돌 응답을 발생하지만 응답은 점프하고 자연스럽지 않습니다. 조작된 개체에 대한 충돌 응답도 없습니다.

고정된 표시가 추가되면 충돌이 올바르게 작동해야 합니다.

### <a name="without-rigidbody"></a>고정된 버디가 없는 경우

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>고정된 버디를 사용하는 경우

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastics(실험적)

개체 조작자를 통해 개체를 조작할 때 탄력적 을 사용할 수 있습니다. [탄력적 시스템은](../experimental/elastic-system.md) 여전히 실험적 상태입니다. 탄력적 기능을 사용하려면 기존 Elastics Manager 구성 요소를 연결하거나 단추를 통해 새 Elastics Manager를 만들고 `Add Elastics Manager` 연결합니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>참조

- [경계 컨트롤](bounds-control.md)
- [제약 조건 관리자](constraint-manager.md)
- [마이그레이션 기간](../tools/migration-window.md)
- [탄력적 시스템(실험적)](../experimental/elastic-system.md)
