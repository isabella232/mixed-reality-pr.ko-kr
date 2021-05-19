---
title: 장면 시스템 조명 장면
description: 장면의 조명 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144413"
---
# <a name="lighting-scene-operations"></a>조명 장면 작업

프로필에 정의 된 기본 조명 장면을 시작할 때 로드 됩니다. 가 호출 될 때까지 조명 장면이 로드 된 상태로 유지 됩니다 `SetLightingScene` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>조명 설정 전환

`transitionType` 새 조명 장면으로 전환 스타일을 제어 합니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

사용 가능한 스타일은 다음과 같습니다.

유형 | 설명 | Duration
--- | --- | ---
없음 | 이전 조명 장면을 언로드하고 새 조명 장면을 로드 합니다. 전환 없음. | 무시됨
FadeToBlack | 이전 조명 장면을 검정으로 페이드 아웃 합니다. 새 조명 장면이 로드 된 후 검정에서 페이드 인 됩니다. 위치 간의 원활한 전환을 위해 유용 합니다. | 사용됨
전환 | 이전 조명 장면을 새 조명 장면을 페이드 아웃 하는 동안 페이드 아웃 합니다. 동일한 위치에서 조명 기능을 매끄럽게 전환 하는 데 유용 합니다. | 사용됨

전환 중에는 일부 조명 설정을 보간 하지 못할 수 있습니다. 부드러운 시각적 전환을 원할 경우 이러한 설정은 조명 장면 간에 일관 되 게 유지 되어야 합니다.

설정 | 부드러운 FadeToBlack 전환 | 부드러운 교차 전환 전환
--- | --- | ---
Skybox | 예 | 예
사용자 지정 리플렉션 | 예 | 예
태양 광원 실시간 그림자 | 예 | 예
