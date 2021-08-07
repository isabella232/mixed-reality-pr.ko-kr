---
title: 기본 클리핑
description: MRTK의 예제를 통해 클리핑 기본형에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 클리핑 기본형,
ms.openlocfilehash: 1feecbbd51eb80ff6113e66d053f032acb3005b9c7d1debbd5dfd46da0925798
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214418"
---
# <a name="clipping-primitive"></a>기본 클리핑

[`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive)동작을 사용하면 [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK 셰이더와 함께 사용할 때 (내부 또는 외부)에 대해 클립할 기본형의 측면을 지정하는 기능을 사용하여 , 및 도형 클리핑을 수행할 수 있습니다.

![기본 클리핑 gizmos](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 셰이더 내에서 [클립/삭제](https://developer.download.nvidia.com/cg/clip.html) 명령을 활용하고 잘린 렌더러를 일괄 처리할 수 있는 Unity 기능을 사용하지 않도록 설정합니다. 클리핑 기본형을 활용할 때는 이러한 성능 영향을 염두에 두어야 합니다.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane)[`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), 및 는 [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 클리핑 기본 속성을 쉽게 제어하는 데 사용할 수 있습니다. 다음 셰이더에서 이러한 구성 요소를 사용하여 클리핑 시나리오를 활용합니다.

- *Mixed Reality Toolkit/표준*
- *Mixed Reality Toolkit/TextMeshPro*
- *Mixed Reality Toolkit/Text3DShader*

## <a name="examples"></a>예제

**ClippingExamples** 및 **MaterialGallery** 장면에서는 동작의 사용을 보여 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 줍니다. MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>고급 사용 방법

기본적으로 한 번에 하나의 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [렌더러만 클리닝할](https://docs.unity3d.com/ScriptReference/Renderer.html) 수 있습니다. 프로젝트에 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [렌더러에](https://docs.unity3d.com/ScriptReference/Renderer.html)  영향을 주는 데 두 개 이상이 필요한 경우 아래 샘플 코드는 이를 달성하는 방법을 보여 줍니다.

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [렌더러에](https://docs.unity3d.com/ScriptReference/Renderer.html) 여러 클립이 있으면 픽셀 셰이더 명령이 증가하고 성능에 영향을 미칩니다. 프로젝트 내에서 이러한 변경 내용을 프로파일러합니다.

*두 개의 다른 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 클립을 렌더링하는 방법입니다. 예를 들어 [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 및 를 동시에 사용할 수 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 있습니다.*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> 위의 변경으로 추가 셰이더 컴파일 시간이 발생합니다.

*두 개의 동일한 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 클립을 렌더링하는 방법입니다. 예를 들어 [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 두 가지를 동시에 수행합니다.*

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

마지막으로 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 및 SecondClippingBox 구성 요소를 장면에 추가하고 두 상자에 동일한 렌더러를 지정합니다. 이제 렌더러가 두 상자에서 동시에 잘려야 합니다.

## <a name="see-also"></a>추가 정보

- [MRTK 표준 셰이더](mrtk-standard-shader.md)
