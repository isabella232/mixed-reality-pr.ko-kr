---
title: 근접 광원
description: MRTK의 예제를 통해 근접 광원에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176384"
---
# <a name="proximity-light"></a><span data-ttu-id="0f92c-104">근접 광원</span><span class="sxs-lookup"><span data-stu-id="0f92c-104">Proximity light</span></span>

<span data-ttu-id="0f92c-105">는 개체 표면 근처에 마우스를 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 가져가는 "그라데이션 역점 조명"을 모방하는 [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 패러다임입니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="0f92c-106">근사 상호 작용에 자주 사용되는 애플리케이션은 구성 요소를 통해 근접 광원의 속성을 제어할 수 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="0f92c-107">[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *재질이 Mixed Reality Toolkit/표준* 셰이더의 영향을 받도록 하려면 근접 *광원* 속성을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="0f92c-108">기본적으로 최대 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2개가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="0f92c-109">예</span><span class="sxs-lookup"><span data-stu-id="0f92c-109">Examples</span></span>

<span data-ttu-id="0f92c-110">MRTK 내의 대부분의 장면에서는 를 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="0f92c-111">가장 일반적인 사용 사례는 MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="0f92c-112">고급 사용 방법</span><span class="sxs-lookup"><span data-stu-id="0f92c-112">Advanced Usage</span></span>

<span data-ttu-id="0f92c-113">기본적으로 한 번에 두 개의 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질만](https://docs.unity3d.com/ScriptReference/Material.html) 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="0f92c-114">프로젝트에 재질에 영향을 주는 데 두 개 이상이 필요한 경우 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 아래 샘플 코드는 이를 달성하는 방법을 보여 줍니다. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="0f92c-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="0f92c-115">[`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [재질을](https://docs.unity3d.com/ScriptReference/Material.html) 비추면 픽셀 셰이더 명령이 늘어나고 성능에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="0f92c-116">프로젝트 내에서 이러한 변경 내용을 프로파일러합니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="0f92c-117">*사용 가능한 수를 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2개에서 4개로 늘리는 방법입니다.*</span><span class="sxs-lookup"><span data-stu-id="0f92c-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="0f92c-118">Unity에서 아래와 유사한 경고를 기록하는 경우 변경 내용이 적용되기 전에 Unity를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f92c-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="0f92c-119">참조</span><span class="sxs-lookup"><span data-stu-id="0f92c-119">See also</span></span>

* [<span data-ttu-id="0f92c-120">MRTK 표준 세이더</span><span class="sxs-lookup"><span data-stu-id="0f92c-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
