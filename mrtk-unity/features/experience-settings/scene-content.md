---
title: Mixed Reality 장면 콘텐츠
description: Mixed Reality 장면 콘텐츠 구성 요소에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193232"
---
# <a name="mixed-reality-scene-content"></a>Mixed Reality 장면 콘텐츠

장면에 MRTK를 추가 하면 `MixedRealitySceneContent` gameobject 생성 됩니다. 이 개체는 다양 한 환경에서 적절 하 게 확장할 수 있도록 혼합 현실 콘텐츠를 저장 하 고 인스턴스화하는 전용 장소 역할을 합니다. Gameobject에는 **맞춤 형식** 매개 변수를 통해 구성할 수 있는 동일한 **MixedRealitySceneContent** monobehavior가 있습니다. 이 매개 변수는 다음 값을 사용할 수 있습니다.

* *AlignWithExperienceScale* -구성 프로필 환경에서 설정 된 **대상 환경 규모** 및 **콘텐츠 오프셋** 을 기준으로 콘텐츠를 정렬 [설정](experience-settings.md)
* *AlignWithHeadHeight* -기본 카메라의 위치인 사용자 헤드의 y 위치에 콘텐츠를 맞춥니다.


  ![편집기에서 만든 혼합 현실 장면 콘텐츠 개체](../images/experience-settings/MixedRealitySceneContent.png)
