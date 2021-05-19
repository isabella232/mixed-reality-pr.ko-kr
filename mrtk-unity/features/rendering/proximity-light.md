---
title: 근접 조명
description: MRTK의 예제를 사용한 근접 조명 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145001"
---
# <a name="proximity-light"></a>근접 조명

는 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 개체의 표면 근처에서 "그라데이션 역 점 조명"을 모방 하는 [흐름 설계 시스템](https://www.microsoft.com/design/fluent/) 패러다임입니다. 거의 상호 작용에 자주 사용 되는 응용 프로그램은 구성 요소를 통해 근접 조명의 속성을 제어할 수 있습니다 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .

재질의 영향을 받는 경우 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *Mixed Reality Toolkit/Standard* 셰이더를 사용 해야 하며, *근접 라이트* 속성을 사용 하도록 설정 해야 합니다.

> [!NOTE]
> 기본적으로 최대 2 개가 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 지원 됩니다.

## <a name="examples"></a>예

MRTK 내의 대부분의 장면은를 활용 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 합니다. 가장 일반적인 사용 사례는 MRTK/SDK/Features/UX/Prefabs/Cursor/FingerCursor. prefab에서 찾을 수 있습니다.

## <a name="advanced-usage"></a>고급 사용 방법

기본적으로 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 한 번에 두 개만 [재질](https://docs.unity3d.com/ScriptReference/Material.html) 을 볼 수 있습니다. 프로젝트에서 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질](https://docs.unity3d.com/ScriptReference/Material.html) 에 영향을 주기 위해 2 개 이상이 필요한 경우 아래 샘플 코드에서는이를 수행 하는 방법을 보여 줍니다.

> [!NOTE]
> 많은 수의 수를 포함 하는 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질이](https://docs.unity3d.com/ScriptReference/Material.html) 있으면 픽셀 셰이더 명령이 증가 하 고 성능이 저하 됩니다. 이러한 변경 내용을 프로젝트 내에서 프로 파일링 하세요.

*사용 가능한 수를 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2 ~ 4 개로 늘리는 방법*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> Unity에서 아래와 비슷한 경고를 기록 하는 경우 Unity를 다시 시작 해야 변경 내용이 적용 됩니다.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>참고 항목

* [MRTK 표준 세이더](mrtk-standard-shader.md)
