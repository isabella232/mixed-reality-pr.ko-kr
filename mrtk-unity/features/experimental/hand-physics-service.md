---
title: 직접 물리학 확장 서비스
description: 설명 및 물리학 확장 서비스
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143432"
---
# <a name="hand-physics-extension-services"></a>직접 물리학 확장 서비스

이에 대 한 실제 서비스를 사용 하면 엄격한 본문 충돌 이벤트와 상호 작용을 통해 상호 작용할 수 있습니다.

## <a name="getting-started-with-hand-physics-extension-service"></a>직접 물리 확장 서비스 시작

확장 서비스 목록에 직접 물리학 서비스를 추가 하 고 기본 프로필을 사용 합니다.

사용 하도록 설정 되 면 모든 collider의 IsTrigger 속성을 사용 하 여 10 자리 (및 palms) 모두에서 충돌 이벤트를 수신 합니다.

### <a name="prerequisites"></a>필수 조건

- 확장 서비스를 사용 하도록 설정
- 손가락/야자수 조인트에 적절 한 prefab을 할당 합니다.

## <a name="recommendations"></a>권장 사항

서비스는 기본적으로 "default" 계층으로 설정 되지만, 수동 물리학 개체에 대해 별도의 계층을 사용 하는 것이 좋습니다. 그렇지 않으면 원치 않는 충돌 및/또는 부정확 한 raycasts를 사용할 수 있습니다.
