---
title: 자재 인스턴스
description: MRTK의 자재 인스턴스 및 사용에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, MaterialInstance,
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176725"
---
# <a name="material-instance"></a>자재 인스턴스

[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)인스턴스 자료 추적의 동작으로, 사용자에 대 한 인스턴스 자료를 자동으로 삭제 합니다. 이 유틸리티 구성 요소는 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 자료 또는 [렌더러 자료](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)로 대체 하는 데 사용할 수 있습니다.

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 은 자료 인스턴스 보다 선호 되지만 모든 시나리오에서 항상 사용할 수 있는 것은 아닙니다.

[렌더러](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 를 사용 하 여 문제가 발생 하는 이유는 무엇 인가요? Unity 장면에 아래 코드를 추가 하 고 재생 메모리 사용은 계속 증가 하 고 증가 합니다.

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
> 위의 누수 동작은 너무 오랫동안 실행 되는 경우 **Unity에서 충돌** 합니다.

대신, 동작을 사용 하 여 시도 합니다 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) .

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

## <a name="usage"></a>사용

Unity의 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer-material.html)를 호출할 때 unity는 새 자료를 자동으로 인스턴스화합니다. 자료가 더 이상 필요 하지 않거나 게임 개체가 제거 될 때 자료를 제거 하는 것은 호출자의 책임입니다. [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)동작을 사용 하면 편집 및 실행 중에 자재 누수를 방지 하 고 재질 할당 경로를 일관 되 게 유지할 수 있습니다.

[MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 를 사용할 수 없고 재료가 인스턴스 되어야 하는 경우 다음과 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 같이 사용할 수 있습니다.

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

여러 개체가 재료 인스턴스의 소유권을 요구 하는 경우 참조 추적에 대해 명시적 소유권을 사용 하는 것이 가장 좋습니다. (라는 선택적 인터페이스는 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 소유권이 있는 도움이 될에 존재 합니다.) 사용 예는 다음과 같습니다.

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

자세한 내용은 동작 내에서 보여 주는 예제 사용법을 참조 하세요 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) .

## <a name="see-also"></a>참조

* [MRTK 표준 세이더](mrtk-standard-shader.md)
