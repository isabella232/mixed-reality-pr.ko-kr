---
title: 개체 조작자
description: MRTK에서 개체 조작자를 사용하는 방법
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 개체 조작,
ms.openlocfilehash: 4c43a35e164d3e66e662afc927d28f84463e1586250e9847a2d88c219ba27f23
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191615"
---
# <a name="object-manipulator"></a>개체 조작자

![개체 조작자](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator는* 조작 동작에 대한 새로운 구성 요소이며, 이전에는 *ManipulationHandler* 에 있습니다. 개체 조작자는 다양한 개선 및 간소화를 제공합니다. 이 구성 요소는 더 이상 사용되지 않는 조작 처리기를 대체합니다.

*ObjectManipulator* 스크립트는 한 손 또는 두 손을 사용하여 개체를 이동 가능하고 확장 가능하며 회전 가능하게 만듭니다. 개체 조작자는 개체가 다양한 입력에 응답하는 방법을 제어하도록 구성할 수 있습니다. 스크립트는 HoloLens 2 연결 손, HoloLens 2 손 광선, HoloLens 1개의 응시 및 제스처, 몰입형 헤드셋 모션 컨트롤러 입력과 같은 대부분의 형태의 상호 작용에서 작동해야 합니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>개체 조작자를 사용하는 방법

개체 조작자를 사용하려면 먼저 `ObjectManipulator` 스크립트 구성 요소를 GameObject에 추가합니다. 또한 잡기 가능한 범위와 일치하는 충돌체를 개체에 추가해야 합니다.

개체가 연결이 가까운 손 입력에 응답하도록 `NearInteractionGrabbable` 하려면 스크립트도 추가합니다.

개체 조작자는 개체에 고정된 구성 요소를 추가하여 물리학 동작을 사용하도록 설정할 수 있습니다. 이 구성 요소를 추가하여 활성화된 물리학 동작은 물리학 및 충돌 에서 자세히 [*설명합니다.*](#physics-and-collisions)

또한 조작 제약 조건 구성 요소를 개체에 추가하여 조작을 제한할 수 [있습니다.](constraint-manager.md#transform-constraints) 이러한 구성 요소는 조작과 함께 작동하며 어떤 방식으로든 조작 동작을 변경하는 특수 구성 요소입니다.

![Unity 편집기에서 조작 처리기 사용](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>검사기 속성 및 필드

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>일반 속성

#### <a name="host-transform"></a>호스트 변환

조작할 개체 변환입니다. 기본값은 구성 요소의 개체입니다.

#### <a name="manipulation-type"></a>조작 유형

한 손 또는 두 손을 사용하여 개체를 조작할 수 있는지 여부를 지정합니다. 이 속성은 플래그이므로 두 옵션을 모두 선택할 수 있습니다.

- *한 손:* 선택한 경우 한 손 조작을 사용하도록 설정합니다.
- *양손:* 선택된 경우 두 손으로 조작할 수 있습니다.

#### <a name="allow-far-manipulation"></a>원거리 조작 허용

포인터와의 원거리 상호 작용을 사용하여 조작을 수행할 수 있는지 여부를 지정합니다.

### <a name="one-handed-manipulation-properties"></a>한 손 조작 속성

#### <a name="one-hand-rotation-mode-near"></a>한 손 회전 모드 근처

한 손으로 가까이 있을 때 개체가 동작하는 방식을 지정합니다. 이러한 옵션은 굴절된 손에서만 작동합니다.

- *개체 중심 회전: 개체는* 손의 회전을 사용하지만 개체 중심점을 중심으로 회전합니다. 개체는 회전할 때 덜 이동하는 것처럼 보이지만 손과 개체 간의 연결이 끊어질 수 있습니다. 원거리 상호 작용에 더 유용합니다.
- *잡기 지점 회전:* 엄지 손가락과 인덱스 손가락 사이의 잡기 지점에 대한 손으로 개체를 회전합니다. 개체가 손을 잡고 있는 것처럼 느낄 수 있습니다.

#### <a name="one-hand-rotation-mode-far"></a>한 손 회전 모드 멀리

한 손으로 멀리 떨어져 있을 때 개체가 동작하는 방식을 지정합니다. 이러한 옵션은 굴절된 손에서만 작동합니다.

- *개체 중심* 회전: 손의 회전을 사용하지만 개체 중심점을 사용하여 개체를 회전합니다. 개체가 회전할 때 개체 중심이 이동하지 않고 멀리 있는 상태에서 검사하는 데 유용합니다.
- *잡기 지점 회전:* 손의 회전을 사용하지만 포인터 광선 적중 지점을 사용하여 개체를 회전합니다. 검사에 유용합니다.

### <a name="two-handed-manipulation-properties"></a>양손 조작 속성

#### <a name="two-handed-manipulation-type"></a>양손 조작 유형

두 손 조작이 개체를 변환하는 방법을 지정합니다. 이 속성은 플래그이므로 원하는 수의 옵션을 선택할 수 있습니다.

- *이동:* 선택한 경우 이동이 허용됩니다.
- *크기 조정:* 선택한 경우 크기 조정이 허용됩니다.
- *회전:* 선택하면 회전이 허용됩니다.

![조작 처리기](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>제약 조건

#### <a name="enable-constraints"></a>제약 조건 사용

이 설정은 연결된 [제약 조건 관리자](constraint-manager.md)를 사용하도록 설정합니다. 변환 변경 내용은 선택한 제약 조건 관리자 에 등록된 [제약](constraint-manager.md)조건에 의해 처리됩니다.

#### <a name="constraint-manager"></a>제약 조건 관리자

드롭다운을 사용하면 연결된 제약 조건 관리자 를 선택할 수 [있습니다.](constraint-manager.md) 개체 조작자는 제약 조건 [관리자가](constraint-manager.md) 항상 연결되어 있는지 확인합니다.
동일한 형식의 여러 구성 요소가 unity에서 동일한 이름 아래에 표시됩니다. 동일한 개체에서 여러 제약 조건 관리자를 보다 쉽게 구분할 수 있도록 사용 가능한 옵션은 선택한 제약 조건 관리자(수동 또는 자동 제약 조건 선택)의 구성에 대한 힌트를 표시합니다.

#### <a name="go-to-component"></a>구성 요소로 이동

제약 조건 관리자 선택 항목에는 *구성 요소로 이동* 단추가 함께 제공됩니다. 이 단추를 사용하면 검사기에서 구성될 수 있도록 선택한 구성 요소로 스크롤합니다.

### <a name="physics"></a>Physics

이 섹션의 설정 개체에 RigidBody 구성 요소가 있는 경우에만 나타납니다.

#### <a name="release-behavior"></a>릴리스 동작

조작된 개체가 해제될 때 유지해야 하는 물리적 속성을 지정합니다. 이 속성은 플래그이므로 두 옵션을 모두 선택할 수 있습니다.

- *속도 유지:* 개체가 해제될 때 이 옵션을 선택하면 선형 속도를 유지합니다.
- *Velocity Angular 유지:* 개체가 해제될 때 이 옵션을 선택하면 각 속도를 유지합니다.

#### <a name="use-forces-for-near-manipulation"></a>근 조작에 강제로 사용

거의 조작을 수행할 때 물리학력을 사용하여 개체를 이동할지 여부입니다. 이 개체를 *false로* 설정하면 개체가 사용자 손과 직접 연결되어 있다고 느낄 수 있습니다. 이 개체를 *true로* 설정하면 개체의 대용량 및 관성은 그대로 있지만 개체가 Spring을 통해 연결된 것처럼 보일 수 있습니다. 기본값은 *false* 입니다.

### <a name="smoothing"></a>다듬기

#### <a name="smoothing-far"></a>원거리 다듬기

원거리 상호 작용에 프레임 속도 독립적 다듬기 사용 여부. 원거리 다듬기는 기본적으로 사용하도록 설정됩니다.

#### <a name="smoothing-near"></a>가까이 다듬기

가까운 상호 작용에 프레임 속도 독립적 다듬기 사용 여부. 효과가 손에서 '연결 끊김'으로 인식될 수 있으므로 거의 다듬기는 기본적으로 사용하지 않도록 설정됩니다.

#### <a name="smoothing-active"></a>활성 다듬기

사용되지 않으며 향후 버전에서 제거될 예정입니다. 애플리케이션은 SmoothingFar, SmoothingNear 또는 둘의 조합을 사용해야 합니다.

#### <a name="move-lerp-time"></a>이동 lerp 시간

이동에 적용할 다듬기 양입니다. 0을 다듬는 것은 다듬기 없음을 의미합니다. 최대값은 값이 변경되지 않는 것을 의미합니다.

#### <a name="rotate-lerp-time"></a>회전 lerp 시간

회전에 적용할 다듬기 양입니다. 0을 다듬는 것은 다듬기 없음을 의미합니다. 최대값은 값이 변경되지 않는 것을 의미합니다.

#### <a name="scale-lerp-time"></a>크기 조정 lerp 시간

배율에 적용할 다듬기 양입니다. 0을 다듬는 것은 다듬기 없음을 의미합니다. 최대값은 값이 변경되지 않는 것을 의미합니다.

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

개체 조작자로 동일한 개체에 고정된 구성 요소를 추가하여 물리학 동작을 사용하도록 설정할 수 있습니다. 이렇게 하면 위의 [릴리스 동작을](#release-behavior) 구성할 수 있게 될 뿐만 아니라 충돌도 가능합니다. 고정된 구성 요소가 없으면 조작 중에 충돌이 제대로 작동하지 않습니다.

- 조작된 개체와 정적 충돌체 간의 충돌(예: 충돌체는 있지만 고정된 충돌체가 없는 개체)은 작동하지 않으며 조작된 개체는 영향을 받지 않는 정적 충돌체를 통해 직접 전달됩니다.
- 조작된 개체와 고정된 개체 간의 충돌(즉, 충돌체와 강체가 둘 다 있는 개체)를 지정하면 고정된 표시에 충돌 응답이 발생하지만 응답은 점프하고 자연스럽지 않습니다. 조작된 개체에 대한 충돌 응답도 없습니다.

고정된 표시가 추가되면 충돌이 올바르게 작동해야 합니다.

### <a name="without-rigidbody"></a>고정된 버디가 없는 경우

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>고정된 버디를 사용하는 경우

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastics(실험적)

개체 조작자를 통해 개체를 조작할 때 탄력적 을 사용할 수 있습니다. [탄력적 시스템은](../experimental/elastic-system.md) 여전히 실험적 상태입니다. 탄력적 기능을 사용하려면 기존 Elastics Manager 구성 요소를 연결하거나 단추를 통해 새 Elastics Manager를 만들고 `Add Elastics Manager` 연결합니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>추가 정보

- [경계 컨트롤](bounds-control.md)
- [제약 조건 관리자](constraint-manager.md)
- [마이그레이션 기간](../tools/migration-window.md)
- [탄력적 시스템(실험적)](../experimental/elastic-system.md)
