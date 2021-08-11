---
title: 가리키기 라이트
description: MRTK의 예제와 HoverLight에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 호버 조명
ms.openlocfilehash: 948a0772cd2fad667984d8d5507664e4346a507e84b03c873eccf8d3f1e66532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198585"
---
# <a name="hover-light"></a>가리키기 라이트

는 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 개체 표면 근처의 [점 광원](https://docs.unity3d.com/Manual/Lighting.html) 가리키기를 모방 하는 [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 패러다임입니다. 자주 사용 되는 상호 작용에는 응용 프로그램에서 구성 요소를 통해 가리키기 조명의 속성을 제어할 수 있습니다 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .

혼합 현실에 영향을 주는 재질의 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 경우 *Toolkit/standard* 셰이더를 사용 해야 하 고 *가리키기 광원* 속성을 사용 하도록 설정 해야 합니다.

> [!Note]
> MRTK/Standard 셰이더는 기본적으로 최대 2 개까지 지원 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 하지만 4 개를 지원 하도록 크기를 조정 하 고 더 많은 조명을 장면에 추가 합니다.

## <a name="examples"></a>예제

MRTK 내의 대부분의 장면은를 활용 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 합니다. 가장 일반적인 사용 사례는 MRTK/SDK/Features/UX/Prefabs/Cursor/DefaultCursor에서 찾을 수 있습니다. prefab

**HoverLightExamples** 장면에서는 동작의 사용법도 보여 주며 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) , 다음에서 찾을 수 있습니다. Mrtk/예제/데모/Standardshader/장면

## <a name="advanced-usage"></a>고급 사용 방법

10 개만 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 한 번에 [재질](https://docs.unity3d.com/ScriptReference/Material.html) 을 볼 수 있습니다. 프로젝트에서 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) [재질](https://docs.unity3d.com/ScriptReference/Material.html) 에 영향을 주기 위해 10 개 이상이 필요한 경우 아래 샘플 코드에서는이를 수행 하는 방법을 보여 줍니다.

> [!Note]
> 많은 수의 수를 포함 하는 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) [재질이](https://docs.unity3d.com/ScriptReference/Material.html) 있으면 픽셀 셰이더 명령이 증가 하 고 성능이 저하 됩니다. **이러한 변경 내용을 프로젝트 내에서 프로 파일링 하세요.**

*10에서 12 사이의 사용 가능한 수를 늘리는 방법 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)*

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
> Unity에서 아래와 비슷한 경고를 기록 하는 경우 Unity를 다시 시작 해야 변경 내용이 적용 됩니다.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>추가 정보

* [MRTK 표준 셰이더](mrtk-standard-shader.md)
