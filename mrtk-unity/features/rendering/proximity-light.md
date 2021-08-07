---
title: 근접 조명
description: MRTK의 예제를 통해 근접 광원에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 1be58cd22228258d51f63b2a4db0294bceaec1320640ecbbfa2795edde5e39bd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208323"
---
# <a name="proximity-light"></a>근접 조명

는 개체 표면 근처에 마우스를 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 가져가는 "그라데이션 역점 조명"을 모방하는 [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 패러다임입니다. 근사 상호 작용에 자주 사용되는 애플리케이션은 구성 요소를 통해 근접 광원의 속성을 제어할 수 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 있습니다.

[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *재질이 Mixed Reality Toolkit/표준* 셰이더의 영향을 받도록 하려면 근접 *광원* 속성을 사용해야 합니다.

> [!NOTE]
> 기본적으로 최대 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2개가 지원됩니다.

## <a name="examples"></a>예제

MRTK 내의 대부분의 장면에서는 를 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 활용합니다. 가장 일반적인 사용 사례는 MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab에서 찾을 수 있습니다.

## <a name="advanced-usage"></a>고급 사용 방법

기본적으로 한 번에 두 개의 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질만](https://docs.unity3d.com/ScriptReference/Material.html) 표시할 수 있습니다. 프로젝트에 재질에 영향을 주는 데 두 개 이상이 필요한 경우 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 아래 샘플 코드는 이를 달성하는 방법을 보여 줍니다. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!NOTE]
> [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질을](https://docs.unity3d.com/ScriptReference/Material.html) 비추면 픽셀 셰이더 명령이 늘어나고 성능에 영향을 미칩니다. 프로젝트 내에서 이러한 변경 내용을 프로파일러합니다.

*사용 가능한 수를 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2개에서 4개로 늘리는 방법입니다.*

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
> Unity에서 아래와 유사한 경고를 기록하는 경우 변경 내용이 적용되기 전에 Unity를 다시 시작해야 합니다.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>추가 정보

* [MRTK 표준 셰이더](mrtk-standard-shader.md)
