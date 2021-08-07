---
title: 자재 인스턴스
description: Material Instance 및 MRTK의 용도에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, MaterialInstance,
ms.openlocfilehash: 6d9a2a35a009bfce1fcfae15000ea02c47be637a8c5a483254ea30d9948922e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210053"
---
# <a name="material-instance"></a>자재 인스턴스

[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)이 동작은 인스턴스 재질 수명을 추적하며 사용자에 대한 인스턴스 재질을 자동으로 삭제합니다. 이 유틸리티 구성 요소는 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 또는 [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)를 대체하는 용도로 사용할 수 있습니다.

> [!NOTE]
> [MaterialPropertyBlock은](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 재질 인탄싱보다 선호되지만 모든 시나리오에서 항상 사용할 수 있는 것은 아닙니다.

[Renderer.material을](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 사용하는 것이 문제가 될 수 있는 이유는 무엇인가요? 아래 코드를 Unity 장면에 추가하고 적중 재생 메모리 사용량이 계속 늘어나고 늘어나는 경우:

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> 위의 누수 동작은 너무 오래 실행된 경우 **Unity를 충돌합니다.**

대신 동작을 사용해 보세요. [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a>사용량

Unity의 [Renderer.material(s)을](https://docs.unity3d.com/ScriptReference/Renderer-material.html)호출할 때 Unity는 자동으로 새 재질을 인스턴스화합니다. 재질이 더 이상 필요하지 않거나 게임 개체가 제거될 때 재질을 삭제하는 것은 호출자의 책임입니다. [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)이 동작은 재질 누출을 방지하고 편집 및 런타임 동안 재질 할당 경로를 일관되게 유지하는 데 도움이 됩니다.

[MaterialPropertyBlock을](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 사용할 수 없으며 재질을 인스턴스화해야 하는 경우 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 다음과 같이 를 사용할 수 있습니다.

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

여러 개체에 재질 인스턴스의 소유권이 필요한 경우 참조 추적을 위해 명시적 소유권을 취하는 것이 가장 좋습니다. (라는 선택적 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 인터페이스는 소유권을 가진 를 소유하기 위해 존재합니다.) 다음은 사용 예입니다.

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

자세한 내용은 동작 내에 설명된 사용 예제를 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 참조하세요.

## <a name="see-also"></a>추가 정보

* [MRTK 표준 셰이더](mrtk-standard-shader.md)
