---
title: 장면 시스템 조명 장면
description: 장면의 조명에 대한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202571"
---
# <a name="lighting-scene-operations"></a>조명 장면 작업

프로필에 정의된 기본 조명 장면은 시작 시 로드됩니다. 가 호출될 때까지 조명 장면 `SetLightingScene` 로드가 유지됩니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>조명 설정 전환

`transitionType` 는 새 조명 장면으로의 전환 스타일을 제어합니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

사용 가능한 스타일은 다음과 같습니다.

형식 | Description | Duration
--- | --- | ---
없음 | 이전 조명 장면을 언로드하고 새 조명 장면을 로드합니다. 전환이 없습니다. | 무시됨
FadeToBlack | 이전 조명 장면의 페이드 아웃은 검은색으로 변합니다. 새 조명 장면이 로드된 다음, 검은색에서 페이드업됩니다. 위치 간의 원활한 전환에 유용합니다. | 사용됨
크로스페이드 | 새 조명 장면 페이드 인으로 이전 조명 장면 페이드 아웃 합니다. 동일한 위치에 있는 조명 설정 간의 원활한 전환에 유용합니다. | 사용됨

일부 조명 설정은 전환 중에 보간할 수 없습니다. 원활한 시각적 전환을 원하는 경우 이러한 설정은 조명 장면 간에 일관성을 유지해야 합니다.

설정 | 부드러운 FadeToBlack 전환 | 부드러운 크로스페드 전환
--- | --- | ---
Skybox | 아니요 | 아니요
사용자 지정 리플렉션 | 아니요 | 아니요
태양 광원 실시간 그림자 | 예 | 아니요
