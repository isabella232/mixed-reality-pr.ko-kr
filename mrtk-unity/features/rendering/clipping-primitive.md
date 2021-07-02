---
title: 기본 클리핑
description: MRTK의 예제를 사용한 클리핑 기본 형식에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 클리핑 기본 형식,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176743"
---
# <a name="clipping-primitive"></a>기본 클리핑

[`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) 이 동작은 [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) mrtk 셰이더에 사용할 때 클리핑할 기본 형식 (내부 또는 외부)을 지정할 수 있는 기능을 사용 하 여 성능, 및 셰이프 클리핑을 가능 하 게 합니다.

![기본 클리핑 gizmo 그리려면](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 셰이더 내에서 [clip/버리도록](https://developer.download.nvidia.com/cg/clip.html) 명령을 활용 하 고 Unity에서 잘린 렌더러를 일괄 처리 하는 기능을 사용 하지 않도록 설정 합니다. 클리핑 기본 형식을 사용할 때 이러한 성능 문제를 염두에 두어야 합니다.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 및를 [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 사용 하 여 기본 속성 클리핑을 쉽게 제어할 수 있습니다. 다음 셰이더를 사용 하 여 이러한 구성 요소를 사용 하 여 클리핑 시나리오를 활용 합니다.

- *혼합 현실 Toolkit/standard*
- *혼합 현실 Toolkit/TextMeshPro*
- *혼합 현실 Toolkit/text이상 셰이더*

## <a name="examples"></a>예

**ClippingExamples** 및 **MaterialGallery** 장면에서는 동작의 사용법 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 을 보여 주고, Mrtk/예제/데모/standardshader/장면에서 찾을 수 있습니다.

## <a name="advanced-usage"></a>고급 사용 방법

기본적으로 한 번 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 에 하나씩 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer.html) 를 클리핑할 수 있습니다. 프로젝트에서 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [렌더러에](https://docs.unity3d.com/ScriptReference/Renderer.html)  영향을 주기 위해 두 개 이상 필요한 경우 아래 샘플 코드에서는이를 수행 하는 방법을 보여 줍니다.

> [!NOTE]
> 클립을 여러 개 포함 하는 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 경우에는 픽셀 셰이더 명령이 증가 하 고 성능에 영향을 줍니다. [](https://docs.unity3d.com/ScriptReference/Renderer.html) 이러한 변경 내용을 프로젝트 내에서 프로 파일링 하세요.

*두 개의 다른 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 클립을 렌더링 하는 방법입니다. 예를 들어 [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 및는 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 다음과 같습니다.*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> 위의 변경 내용으로 인해 추가 셰이더 컴파일 시간이 발생 합니다.

*동일한 클립 두 개를 렌더링 하는 방법입니다 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) . 예를 들어 [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) , 다음과 같은 두 가지 경우입니다.*

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

마지막으로, [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 장면에 및 SecondClippingBox 구성 요소를 추가 하 고 두 상자에 동일한 렌더러를 지정 합니다. 이제 렌더러를 두 상자 모두 동시에 잘라내야 합니다.

## <a name="see-also"></a>참조

- [MRTK 표준 세이더](mrtk-standard-shader.md)
