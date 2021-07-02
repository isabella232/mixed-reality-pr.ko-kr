---
title: 경계 상자
description: MRTK의 경계 상자 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 상자
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177541"
---
# <a name="bounding-box"></a>경계 상자

![경계 상자](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> 경계 상자는 더 이상 사용되지 않으며 후속 경계 컨트롤 로 [대체됩니다.](bounds-control.md) [마이그레이션 옵션 중 하나를](#migrating-to-bounds-control) 사용하여 기존 게임 개체를 업그레이드합니다.

[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)스크립트는 혼합 현실에서 개체를 변환하기 위한 기본 기능을 제공합니다. 경계 상자는 상호 작용할 수 있음을 나타내기 위해 홀로그램 주위에 큐브를 표시합니다. 큐브의 모퉁이와 가장자리에 있는 핸들을 사용하면 개체의 크기를 조정하거나 회전할 수 있습니다. 경계 상자는 사용자 입력에도 반응합니다. 예를 들어 HoloLens 2 경계 상자는 손가락 근접에 응답하여 개체와의 거리를 인식하는 데 도움이 되는 시각적 피드백을 제공합니다. 모든 상호 작용 및 시각적 개체를 쉽게 사용자 지정할 수 있습니다.

자세한 내용은 Windows 개발자 센터 [경계 상자 및 앱 표시줄을](/windows/mixed-reality/app-bar-and-bounding-box) 참조하세요.

## <a name="example-scene"></a>예제 장면

장면에서 경계 상자 구성의 예를 찾을 수 `BoundingBoxExamples` 있습니다.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Unity 검사기를 사용하여 경계 상자를 추가하고 구성하는 방법

1. 개체에 Box Collider 추가
2. `BoundingBox`개체에 스크립트 할당
3. 'Activation' 메서드와 같은 옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)
4. (선택 사항) HoloLens 2 스타일 경계 상자에 대한 프리팹 및 재질 할당(아래 [스타일 처리](#handle-styles) 섹션 참조)

> [!NOTE]
> 검사기에서 *대상 개체* 및 *경계 재정의* 필드를 사용하여 여러 자식 구성 요소가 있는 개체의 특정 개체 및 충돌체를 할당합니다.

![경계 상자 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>코드에서 경계 상자를 추가하고 구성하는 방법

1. GameObject 큐브 인스턴스화

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundingBox`AddComponent<>()를 사용하여 충돌체가 있는 개체에 스크립트 할당

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. 옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (선택 사항) HoloLens 2 스타일 경계 상자에 대한 프리팹 및 재질을 할당합니다. 재질과 프리팹을 동적으로 로드해야 하므로 검사자를 통해 할당해야 합니다.

> [!NOTE]
> Unity의 'Resources' 폴더 또는 [Shader.Find를]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 사용하여 셰이더를 동적으로 로드하는 것은 런타임에 셰이더 순열이 누락될 수 있기 때문에 권장되지 않습니다.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>예제: MinMaxScaleConstraint를 사용하여 최소, 최대 경계 상자 배율 설정

최소 및 최대 크기 조정을 설정하려면 를 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 사용합니다. MinMaxScaleConstraint를 사용하여 에 대한 최소 및 최대 배율도 설정할 수 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 있습니다.

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>예제: 게임 개체 주위에 경계 상자 추가

개체 주위에 경계 상자를 추가하려면 구성 `BoundingBox` 요소를 추가하기만 하면됩니다.

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>검사기 속성

### <a name="target-object"></a>대상 개체

이 속성은 경계 상자 조작에 의해 변환될 개체를 지정합니다. 개체가 설정되지 않은 경우 경계 상자는 기본적으로 소유자 개체로 설정됩니다.

### <a name="bounds-override"></a>범위 재정의

경계 계산을 위해 개체에서 상자 충돌체를 설정합니다.

### <a name="activation-behavior"></a>활성화 동작

경계 상자 인터페이스를 활성화하는 몇 가지 옵션이 있습니다.

* *시작 시 활성화:* 장면이 시작되면 경계 상자가 표시됩니다.
* *근접성으로 활성화:* 개체에 가까운 절전형 손의 경계 상자가 표시됩니다.
* *포인터로 활성화:* 손 광선 포인터의 대상이 될 때 경계 상자가 표시됩니다.
* *수동으로 활성화:* 경계 상자가 자동으로 표시되지 않습니다. boundingBox.Active 속성에 액세스하여 스크립트를 통해 수동으로 활성화할 수 있습니다.

### <a name="scale-minimum"></a>최소 크기 조정

허용되는 최소 크기입니다. 이 속성은 더 이상 사용되지 않으며 스크립트를 추가하는 것이 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 좋습니다. 이 스크립트를 추가하면 경계 상자 대신 최소 크기 조정이 제거됩니다.

### <a name="scale-maximum"></a>최대 크기 조정

허용되는 최대 크기입니다. 이 속성은 더 이상 사용되지 않으며 스크립트를 추가하는 것이 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 좋습니다. 이 스크립트를 추가하면 경계 상자 대신 최대 크기 조정이 제거됩니다.

### <a name="box-display"></a>상자 표시

다양한 경계 상자 시각화 옵션입니다.

축 평면화가 *자동 평면화로* 설정된 경우 스크립트는 가장 작은 범위로 축을 따라 조작을 허용되지 않습니다. 이로 인해 일반적으로 씬 개체에 사용되는 2D 경계 상자가 발생합니다.

### <a name="handles"></a>핸들

재질과 프리팹을 할당하여 핸들 스타일을 재정의할 수 있습니다. 할당된 핸들이 없으면 기본 스타일로 표시됩니다.

## <a name="events"></a>이벤트

경계 상자는 다음과 같은 이벤트를 제공합니다. 이 예제에서는 이러한 이벤트를 사용하여 오디오 피드백을 재생합니다.

* **회전 시작: 회전이** 시작될 때 발생합니다.
* **회전 종료:** 회전이 끝날 때 발생합니다.
* **Scale Started:** 크기 조정이 시작될 때 발생합니다.
* **확장 종료:** 크기 조정이 종료되면 발생합니다.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>스타일 처리

기본적으로 스크립트를 할당하면 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) HoloLens 1세대 스타일의 핸들이 표시됩니다. HoloLens 2 스타일 핸들을 사용하려면 적절한 핸들 프리팹 및 재질을 할당해야 합니다.

![경계 상자 핸들 스타일](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

다음은 HoloLens 2 스타일 경계 상자 핸들의 프리팹, 재질 및 크기 조정 값입니다. 장면에서 이 예제를 찾을 수 `BoundingBoxExamples` 있습니다.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>핸들(HoloLens 2 스타일에 대한 설정)

* **핸들 재질:** BoundingBoxHandleWhite.mat
* **핸들 잡기 재질:** BoundingBoxHandleBlueGrabbed.mat
* **배율 핸들 프리팹:** MRTK_BoundingBox_ScaleHandle.prefab
* **배율 핸들 슬레이트 프리팹:** MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **배율 핸들 크기:** 0.016(1.6cm)
* **배율 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)
* **회전 핸들 프리팹:** MRTK_BoundingBox_RotateHandle.prefab
* **회전 핸들 크기:** 0.016
* **회전 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)

### <a name="proximity-setup-for-hololens-2-style"></a>근접성(HoloLens 2 스타일 설정)

손까지의 거리를 기준으로 애니메이션이 있는 핸들을 표시하고 숨깁니다. 2단계 크기 조정 애니메이션이 있습니다.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **근접 효과 활성:** 근접 기반 핸들 활성화 사용
* **중간 근접 처리:** 첫 번째 단계 크기 조정을 위한 거리입니다.
* **근접 핸들:** 두 번째 단계 크기 조정을 위한 거리입니다.
* **원거리 크기** 조정: 손의 경계 상자 상호 작용 범위(위에서 '중간 근접 처리'로 정의된 거리)를 벗어나는 경우 핸들 자산의 기본 크기 조정 값입니다. 기본적으로 핸들을 숨기려면 0을 사용합니다.)
* **중간 규모:** 손의 경계 상자 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값입니다(위의 '근접 핸들'로 정의된 거리). 1을 사용하여 정상 크기 표시)
* **닫기 배율:** 손의 잡기 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값(위에서 '근접 핸들'로 정의된 거리)입니다. 1.x를 사용하여 더 큰 크기 표시)

## <a name="making-an-object-movable-with-manipulation-handler"></a>조작 처리기를 통해 개체를 이동 가능하게 만들기

경계 상자를 와 결합하여 [`ManipulationHandler.cs`](manipulation-handler.md) 원거리 상호 작용을 사용하여 개체를 이동 가능하게 만들 수 있습니다. 조작 처리기는 한 손 조작과 양손 상호 작용을 모두 지원합니다. [손 추적을](../input/hand-tracking.md) 사용하여 개체와 가까이에서 상호 작용할 수 있습니다.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

의 원거리 상호 작용을 사용하여 이동할 때 경계 상자 가장자리가 동일한 방식으로 [`ManipulationHandler`](manipulation-handler.md) 작동하려면 위의   /  스크린샷에 표시된 것처럼 *조작이 종료될* 때 조작이 시작되었을 때 에 대한 이벤트를 각각 에 연결하는 것이 `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` 좋습니다.

## <a name="migrating-to-bounds-control"></a>경계 컨트롤로 마이그레이션

[경계 상자를](bounding-box.md) 사용하는 기존 프리팹 및 인스턴스는 MRTK 도구 패키지의 일부인 [마이그레이션 창을](../tools/migration-window.md) 통해 새 경계 컨트롤로 업그레이드할 수 있습니다.

경계 상자의 개별 인스턴스를 업그레이드하기 위해 구성 요소의 속성 검사자 내에 마이그레이션 옵션도 있습니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
