---
title: 마우스로 가리키기 조명
description: MRTK의 예제를 통해 HoverLight에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 가리키기 조명,
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176729"
---
# <a name="hover-light"></a>마우스로 가리키기 조명

[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)는 개체 표면 근처에 마우스를 가져가는 점 [광원을](https://docs.unity3d.com/Manual/Lighting.html) 모방하는 [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 패러다임입니다. 멀리 떨어진 상호 작용에 자주 사용되는 애플리케이션은 구성 요소를 통해 가리키기 조명의 속성을 제어할 수 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 있습니다.

[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *재질이 Mixed Reality Toolkit/표준* 셰이더의 영향을 받도록 하려면 을 사용하고 *Hover Light* 속성을 사용하도록 설정해야 합니다.

> [!Note]
> MRTK/표준 셰이더에서는 기본적으로 최대 2개의 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 셰이더를 지원하지만 장면에 조명이 추가되면 4개와 10개를 지원하도록 확장됩니다.

## <a name="examples"></a>예

MRTK 내의 대부분의 장면에서는 를 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 활용합니다. 가장 일반적인 사용 사례는 MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab에서 찾을 수 있습니다.

**HoverLightExamples** 장면도 동작의 사용량을 보여 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 줍니다. MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>고급 사용 방법

한 번에 10개만 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) [재질을](https://docs.unity3d.com/ScriptReference/Material.html) 비출 수 있습니다. 프로젝트에 재질에 영향을 주는 데 10개 이상이 필요한 경우 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 아래 샘플 코드는 이를 달성하는 방법을 보여 줍니다. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) [재질을](https://docs.unity3d.com/ScriptReference/Material.html) 비추면 픽셀 셰이더 명령이 늘어나고 성능에 영향을 미칩니다. **프로젝트 내에서 이러한 변경 내용을 프로파일러합니다.**

*사용 가능한 수를 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 10개에서 12개로 늘리는 방법입니다.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> Unity에서 아래와 유사한 경고를 기록하는 경우 변경 내용이 적용되기 전에 Unity를 다시 시작해야 합니다.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>참조

* [MRTK 표준 세이더](mrtk-standard-shader.md)
