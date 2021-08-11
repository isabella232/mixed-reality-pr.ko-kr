---
title: 손 물리학 서비스
description: MRTK에서 직접 물리학 확장 서비스를 사용 하는 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221729"
---
# <a name="hand-physics-service"></a>손 물리학 서비스

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

### <a name="use-palm-kinematic-body"></a>팜 기구학 본문 사용

서비스에서 팜 prefab의 인스턴스화를 시도할지 여부를 제어 합니다.

### <a name="palm-kinematic-body-prefab"></a>야자수 기구학 본문 prefab

`UsePalmKinematicBody`을 사용 하도록 설정 하면이 prefab 됩니다. 마찬가지로 `FingerTipKinematicBodyPrefab` 이 prefab에는 다음이 필요 합니다.

- IsKinematic이 활성화 된 rigidbody 구성 요소
- Collider
- `JointKinematicBody` 구성 요소

## <a name="how-to-use-the-service"></a>서비스를 사용 하는 방법

사용 하도록 설정 되 면 모든 collider의 속성을 사용 `IsTrigger` 하 여 10 자리 (그리고 사용 하도록 설정 된 경우 palms)에서 충돌 이벤트를 수신 합니다.
