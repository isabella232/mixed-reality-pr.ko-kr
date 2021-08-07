---
title: 경계 상자
description: MRTK의 경계 상자에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 경계 상자
ms.openlocfilehash: fa1ace9d7aaf547ee677accfc4254ce9c64aebdfa6a01f11962812b058bc9ceb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214251"
---
# <a name="bounding-box"></a>경계 상자

![경계 상자](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> 경계 상자는 더 이상 사용 되지 않으며 후속 [범위 컨트롤로](bounds-control.md)대체 됩니다. [마이그레이션 옵션 중 하나](#migrating-to-bounds-control) 를 사용 하 여 기존 게임 개체를 업그레이드할 수 있습니다.

이 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 스크립트는 혼합 현실에서 개체를 변환 하기 위한 기본 기능을 제공 합니다. 경계 상자는가와 상호 작용할 수 있음을 나타내기 위해 홀로그램 주위에 큐브를 표시 합니다. 큐브의 모퉁이 및 가장자리에 대 한 핸들은 개체의 크기를 조정 하거나 회전할 수 있습니다. 경계 상자는 또한 사용자 입력에 반응 합니다. 예를 들어 HoloLens 2에서 경계 상자는 손가락 근접에 응답 하 고 개체에서의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 제공 합니다. 모든 상호 작용 및 시각적 개체를 쉽게 사용자 지정할 수 있습니다.

자세한 내용은 Windows 개발자 센터에서 [경계 상자 및 앱 바](/windows/mixed-reality/app-bar-and-bounding-box) 를 참조 하세요.

## <a name="example-scene"></a>장면 예

장면에서 경계 상자 구성의 예제를 찾을 수 있습니다 `BoundingBoxExamples` .

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Unity Inspector를 사용 하 여 경계 상자를 추가 및 구성 하는 방법

1. 개체에 상자 Collider 추가
2. `BoundingBox`개체에 스크립트 할당
3. ' 활성화 ' 메서드와 같은 옵션을 구성 합니다 (아래 [Inspector 속성](#inspector-properties) 섹션 참조).
4. 필드 HoloLens 2 스타일 경계 상자에 대 한 prefabs 및 재질 할당 (아래의 [핸들 스타일](#handle-styles) 섹션 참조)

> [!NOTE]
> Inspector에서 *대상 개체* 및 *범위 재정의* 필드를 사용 하 여 개체의 특정 개체 및 collider를 여러 자식 구성 요소와 함께 할당 합니다.

![경계 상자 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>코드에서 경계 상자를 추가 하 고 구성 하는 방법

1. 큐브 GameObject 인스턴스화

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundingBox`AddComponent<> ()를 사용 하 여 collider를 사용 하는 개체에 스크립트 할당

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. 옵션 구성 (아래 [검사기 속성](#inspector-properties) 섹션 참조)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. 필드 HoloLens 2 스타일 경계 상자에 대 한 prefabs 및 자료를 할당 합니다. 이 경우 자료와 prefabs를 동적으로 로드 해야 하므로 검사기를 통해 할당 해야 합니다.

> [!NOTE]
> Unity의 ' Resources ' 폴더 또는 셰이더를 사용 하 고 [있습니다.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 셰이더 순열이 런타임에 누락 될 수 있으므로 셰이더를 동적으로 로드 하는 것은 권장 되지 않습니다.

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>예: MinMaxScaleConstraint를 사용 하 여 최소, 최대 경계 상자 배율 설정

최소 및 최대 눈금을 설정 하려면를 사용 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 합니다. MinMaxScaleConstraint를 사용 하 여에 대 한 최소 및 최대 크기를 설정할 수도 있습니다 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>예: 게임 개체 주위에 경계 상자 추가

개체 주위에 경계 상자를 추가 하려면 구성 요소를 추가 하면 됩니다 `BoundingBox` .

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Inspector 속성

### <a name="target-object"></a>대상 개체

이 속성은 경계 상자 조작으로 변환할 개체를 지정 합니다. 개체를 설정 하지 않으면 경계 상자는 기본적으로 owner 개체가 됩니다.

### <a name="bounds-override"></a>경계 재정의

범위 계산을 위해 개체에서 상자 collider를 설정 합니다.

### <a name="activation-behavior"></a>활성화 동작

경계 상자 인터페이스를 활성화 하는 몇 가지 옵션이 있습니다.

* *시작 시 활성화*: 경계 상자는 장면을 시작한 후에 표시 됩니다.
* *근접 별 활성화*: 경계 상자는 개체에 근접 하는 경우 표시 됩니다.
* *포인터로 활성화*: 경계 상자는 손 모양 포인터의 대상으로 지정 될 때 표시 됩니다.
* *수동으로 활성화*: 경계 상자는 자동으로 표시 되지 않습니다. BoundingBox 속성에 액세스 하 여 스크립트를 통해 수동으로 활성화할 수 있습니다.

### <a name="scale-minimum"></a>최소 크기 조정

허용 되는 최소 소수 자릿수입니다. 이 속성은 사용 되지 않으며 스크립트를 추가 하는 것이 좋습니다 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . 이 스크립트를 추가 하면 경계 상자를 사용 하지 않고 최소 소수 자릿수가 사용 됩니다.

### <a name="scale-maximum"></a>최대 크기 조정

허용 되는 최대 크기입니다. 이 속성은 사용 되지 않으며 스크립트를 추가 하는 것이 좋습니다 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . 이 스크립트를 추가 하는 경우 경계 상자를 사용 하는 대신 최대 소수 자릿수를 가져옵니다.

### <a name="box-display"></a>상자 표시

다양 한 경계 상자 시각화 옵션입니다.

평면화 축이 *평면화 Auto* 로 설정 된 경우 스크립트는 범위가 가장 작은 축을 따라 조작이 허용 되지 않습니다. 그러면 일반적으로 씬 개체에 사용 되는 2D 경계 상자가 생성 됩니다.

### <a name="handles"></a>핸들

재질 및 prefab을 할당 하 여 핸들 스타일을 재정의할 수 있습니다. 핸들이 할당 되지 않은 경우에는 기본 스타일로 표시 됩니다.

## <a name="events"></a>이벤트

경계 상자는 다음과 같은 이벤트를 제공 합니다. 이 예제에서는 이러한 이벤트를 사용 하 여 오디오 피드백을 재생 합니다.

* **회전 시작**: 회전이 시작 될 때 발생 합니다.
* **회전 종료**: 회전이 종료 될 때 발생 합니다.
* **크기 조정 시작**: 크기 조정을 시작할 때 발생 합니다.
* **배율 종료**: 크기 조정을 끝낼 때 발생 합니다.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>핸들 스타일

기본적으로 스크립트를 할당 하면 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) HoloLens 1 세대 스타일의 핸들이 표시 됩니다. HoloLens 2 스타일 핸들을 사용 하려면 적절 한 핸들 prefabs 및 자료를 할당 해야 합니다.

![경계 상자 핸들 스타일](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

다음은 HoloLens 2 스타일 경계 상자 핸들에 대 한 prefabs, 재질 및 배율 값입니다. 이 예제는 장면에서 찾을 수 있습니다 `BoundingBoxExamples` .

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>Handles (HoloLens 2 스타일에 대 한 설정)

* **처리 자료**: BoundingBoxHandleWhite
* **핸들 Grabbed 재질**: BoundingBoxHandleBlueGrabbed
* **크기 조정 핸들 Prefab**: MRTK_BoundingBox_ScaleHandle. Prefab
* **크기 조정 핸들 슬레이트 Prefab**: MRTK_BoundingBox_ScaleHandle_Slate. Prefab
* 크기 **조정 핸들 크기**: 0.016 (1.6 cm)
* **크기 조정 핸들 Collider 패딩**: 0.016 (grabbable Collider가 시각적 개체를 처리 하는 것 보다 약간 큼)
* **회전 핸들 Prefab**: MRTK_BoundingBox_RotateHandle. Prefab
* **회전 핸들 크기**: 0.016
* **회전 핸들 Collider 패딩**: 0.016 (grabbable Collider가 시각적 개체를 처리 하는 것 보다 약간 큼)

### <a name="proximity-setup-for-hololens-2-style"></a>근접 (HoloLens 2 스타일에 대 한 설정)

손으로의 거리에 따라 애니메이션이 포함 된 핸들을 표시 하 고 숨깁니다. 2 단계 크기 조정 애니메이션을 포함 합니다.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **근접 효과 활성**: 근접 기반 핸들 활성화 활성화
* **처리 매체 근접**: 1 단계 크기 조정에 대 한 거리
* **근접 근접 처리**: 두 번째 단계 크기 조정에 대 한 거리
* **Far**: 손이 경계 상자 상호 작용의 범위를 벗어난 경우 핸들 자산의 기본 배율 값입니다 (위에서 ' 핸들 중간 근접 '으로 정의 된 거리). 0을 사용 하 여 기본적으로 핸들을 숨깁니다.)
* **중간 규모**: 핸들 자산의 크기 조정 값 (위에서 ' 핸들 닫기 '에 의해 위에서 정의 된 거리) 내에 있습니다. 1을 사용 하 여 보통 크기 표시)
* **종가**: 핸들 자산의 크기 조정 값 (위에서 ' 핸들 닫기 '에 의해 위에서 정의 된 거리) 내에 있는 경우입니다. 1. x를 사용 하 여 더 큰 크기 표시)

## <a name="making-an-object-movable-with-manipulation-handler"></a>조작 처리기를 사용 하 여 개체를 이동할 때

경계 상자를와 결합 하 여 [`ManipulationHandler.cs`](manipulation-handler.md) 개체를 멀리 떨어져 있는 상태로 만들 수 있습니다. 조작 처리기는 한 손 조작과 양손 상호 작용을 모두 지원합니다. [손 추적을](../input/hand-tracking.md) 사용하여 개체와 가까이에서 상호 작용할 수 있습니다.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

의 원거리 상호 작용을 사용하여 이동할 때 경계 상자 가장자리가 동일한 방식으로 [`ManipulationHandler`](manipulation-handler.md) 작동하려면 위의   /  스크린샷에 표시된 것처럼 *조작이 종료될* 때 조작이 시작되었을 때 에 대한 이벤트를 각각 에 연결하는 것이 `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` 좋습니다.

## <a name="migrating-to-bounds-control"></a>경계 컨트롤로 마이그레이션

[경계 상자를](bounding-box.md) 사용하는 기존 프리팹 및 인스턴스는 MRTK 도구 패키지의 일부인 [마이그레이션 창을](../tools/migration-window.md) 통해 새 경계 컨트롤로 업그레이드할 수 있습니다.

경계 상자의 개별 인스턴스를 업그레이드하기 위해 구성 요소의 속성 검사자 내에 마이그레이션 옵션도 있습니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
