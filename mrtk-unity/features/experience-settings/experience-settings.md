---
title: 환경 설정
description: MRTK에 대한 다양한 환경 설정에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203252"
---
# <a name="experience-settings"></a>환경 설정

Mixed Reality UI를 만들 때의 과제 중 하나는 다양한 환경 간에 조정하는 것입니다. MRTK를 사용하면 장면에 대한 및 를 설정할 수 `Target Experience Scale` `Content Offset` 있으며, 대상 배율에 맞게 적절하게 동작하도록 다음을 구성합니다.

- 장면 콘텐츠 Mixed Reality
- 경계 시스템

  ![MRTK 구성 프로필의 환경 설정](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>대상 환경 크기 조정

**대상 환경 크기 조정은** 환경이 디자인된 환경을 지정합니다. 다음 값을 사용할 수 있습니다.

* *OrientationOnly* - 헤드셋 방향만 활용하고 무게가 정렬된 환경입니다. 좌표계 원점이 헤드 수준에 있습니다.
* *Seated - 착석* 용도로 설계된 환경입니다. 좌표계 원점은 바닥 수준입니다.
* *고정* - 고정 고정 사용을 위해 설계된 환경입니다. 좌표계 원점은 바닥 수준입니다.
* *Room* - 실내 전체의 이동을 지원하도록 설계된 환경입니다. 좌표계 원점은 바닥 수준입니다.
* *세계* - 실제 세계를 활용하고 이동하도록 설계된 환경입니다. 좌표계 원점이 헤드 수준에 있습니다.

## <a name="content-offset"></a>콘텐츠 오프셋

이 매개 변수는 **맞춤 유형이** **환경 배율에 맞추기로** 설정된 [경우 장면 콘텐츠에 Mixed Reality](scene-content.md) 오프셋할 바닥 위의 높이를 지정합니다.
