---
title: ExperienceSettings
description: MRTK에 대 한 다양 한 환경 설정에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647893"
---
# <a name="experience-settings"></a>환경 설정

혼합 현실에 대 한 UI를 만드는 문제 중 하나는 다양 한 환경에서 정렬 하는 것입니다. MRTK를 사용 하면 `Target Experience Scale` 장면에 대해 및를 설정할 수 있습니다 `Content Offset` . 그러면 다음을 수행 하 여 대상 배율에 맞게 적절히 동작 합니다.

- 혼합 현실 장면 콘텐츠
- 경계 시스템

  ![MRTK 구성 프로필의 경험 설정](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>대상 환경 크기 조정

**대상 환경 규모** 는 환경을 디자인 하는 환경을 지정 합니다. 다음 값을 사용할 수 있습니다.

* *OrientationOnly* -헤드셋 방향만 활용 하 고 무게를 맞춘 환경입니다. 좌표계 원점이 헤드 수준에 있습니다.
* *장착* 됨-를 사용 하도록 설계 된 환경입니다. 좌표계 원점이 바닥 수준에 있습니다.
* 고정 *-고정* 된 용도로 설계 된 환경입니다. 좌표계 원점이 바닥 수준에 있습니다.
* *대화방* -실내에서의 이동을 지원 하도록 설계 된 환경입니다. 좌표계 원점이 바닥 수준에 있습니다.
* *세계* -실제 세계를 활용 하 고 이동 하도록 설계 된 환경입니다. 좌표계 원점이 헤드 수준에 있습니다.

## <a name="content-offset"></a>콘텐츠 오프셋

이 매개 변수는 **맞춤 유형이** **환경 크기에 맞게** 설정 된 경우 혼합 된 현실을 포함 하는 [혼합 된 항목](scene-content.md) 의 높이를 지정 합니다.