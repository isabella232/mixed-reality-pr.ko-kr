---
title: 장면 콘텐츠 Mixed Reality
description: Mixed Reality 장면 콘텐츠 구성 요소에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177342"
---
# <a name="mixed-reality-scene-content"></a>장면 콘텐츠 Mixed Reality

장면에 MRTK를 추가하면 `MixedRealitySceneContent` gameobject가 만들어집니다. 이 개체는 다양한 환경 간에 적절하게 크기가 조정되도록 Mixed Reality 콘텐츠를 배치하고 인스턴스화하기 위한 전용 위치 역할을 합니다. gameobject에는 **맞춤 형식** 매개 변수를 통해 구성할 수 있는 동일한 **MixedRealitySceneContent** monobehavior가 있습니다. 이 매개 변수는 다음 값을 사용할 수 있습니다.

* *AlignWithExperienceScale* - 구성 프로필의 **Experience** [설정](experience-settings.md) 설정된 대상 환경 크기 조정 및 **콘텐츠 오프셋에** 따라 콘텐츠를 정렬합니다.
* *AlignWithHeadHeight* - 콘텐츠를 주 카메라의 위치인 사용자 머리의 y 위치에 맞춥니다.


  ![편집기에서 만든 장면 콘텐츠 개체 Mixed Reality](../images/experience-settings/MixedRealitySceneContent.png)
