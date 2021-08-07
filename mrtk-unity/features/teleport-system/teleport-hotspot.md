---
title: 핫스팟 텔레포트
description: MRTK의 Teleport 핫스팟 구성 요소에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Teleport 시스템, Teleport 핫스팟
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 755b0e8f53be2f393b52395309ed9ab0fad96cadc2e4289400cfff45a99aa6a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189466"
---
# <a name="teleport-hotspot"></a>핫스팟 텔레포트

원격 포트 핫스팟은 사용자가 해당 위치로 원격 전송할 때 특정 위치와 방향에 있는지 확인하기 위해 gameobject에 추가할 수 있는 구성 요소입니다.

## <a name="usage"></a>사용량

### <a name="how-to-create-a-teleport-hotspot"></a>원격 포트 핫스팟을 만드는 방법

원격 포트 핫스팟을 만들려면 TeleportHotspot 구성 요소를 충돌체 구성 요소가 있는 개체에 추가합니다. 

![Teleport 핫스팟 구성 요소](../images/teleport/TeleportHotspotComponent.png)

이제 Teleport 포인터의 표시기가 TeleportHotspot을 통해 전송될 때 색이 변경됩니다. 핫스팟을 통해 원격 이동 작업이 완료되면 사용자는 TeleportHotspot의 가운데로 원격 전송합니다.

재정의 방향 플래그가 선택되어 있으면 사용자의 방향이 원격 포트 핫스팟의 방향과 일치합니다.

![Teleport 핫스팟 예제](../images/teleport/TeleportHotspotExample.gif)
