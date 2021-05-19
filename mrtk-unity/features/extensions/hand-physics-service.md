---
title: 직접 물리학 서비스 개요
description: MRTK에서 직접 물리학 확장 서비스를 사용 하는 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145086"
---
# <a name="hand-physics-extension-service"></a>직접 물리학 확장 서비스

![직접 물리학 확장 서비스](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

이에 대 한 실제 서비스를 사용 하면 엄격한 본문 충돌 이벤트와 상호 작용을 통해 상호 작용할 수 있습니다.

## <a name="enabling-the-extension"></a>확장 사용

확장을 사용 하도록 설정 하려면 RegisteredServiceProvider 프로필을 엽니다. `Register a new Service Provider`새 구성을 추가 하려면 클릭 합니다. 구성 요소 유형 필드에서 HandPhysicsService를 선택 합니다. 구성 프로필 필드에서 확장에 포함 된 기본 직접 물리학 프로필을 선택 합니다.

## <a name="profile-options"></a>프로필 옵션

### <a name="hand-physics-layer"></a>직접 물리학 계층

인스턴스화된 손을 조인트가 이동할 계층을 제어 합니다.

서비스는 기본적으로 "default" 계층 (0)으로 설정 되지만, 직접 물리 개체에 대해 별도의 계층을 사용 하는 것이 좋습니다. 그렇지 않으면 원치 않는 충돌 및/또는 부정확 한 raycasts를 사용할 수 있습니다.

### <a name="finger-tip-kinematic-body-prefab"></a>핑거 팁 기구학 본문 prefab

어떤 prefab를 손쉽게 인스턴스화할 수 있습니다. 서비스가 예상 대로 작동 하려면 prefab에 다음이 필요 합니다.

- IsKinematic이 활성화 된 rigidbody 구성 요소
- Collider
- `JointKinematicBody` 구성 요소

### <a name="use-palm-kinematic-body"></a>손무한 키니틱 본문 사용

서비스가 손만 조인트에서 프리팹을 인스턴스화하려고 하는지 여부를 제어합니다.

### <a name="palm-kinematic-body-prefab"></a>손무한 키네틱 본문 프리팹

`UsePalmKinematicBody`를 사용하도록 설정하면 인스턴스화할 프리팹입니다. 와 마찬가지로 `FingerTipKinematicBodyPrefab` 이 프리팹에는 다음이 필요합니다.

- isKinematic을 사용하도록 설정된 고정된 구성 요소
- 충돌(collider)
- `JointKinematicBody` 구성 요소

## <a name="how-to-use-the-service"></a>서비스를 사용하는 방법

사용하도록 설정되면 모든 충돌자의 속성을 사용하여 `IsTrigger` 10자리 전체에서 충돌 이벤트를 수신합니다(활성화된 경우 손아귀).
