---
title: BoundsControl
description: MRTK의 범위 컨트롤에 대 한 개요
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 제어,
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487730"
---
# <a name="bounds-control"></a>범위 제어

![범위 제어](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* 는 이전에 *BoundingBox* 에서 발견 된 조작 동작에 대 한 새 구성 요소입니다. 경계 제어를 사용 하면 여러 가지 기능을 향상 시키고 설치를 단순화 새 기능을 추가할 수 있습니다. 이 구성 요소는 더 이상 사용 되지 않는 경계 상자를 대체 합니다.

이 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 스크립트는 혼합 현실에서 개체를 변환 하기 위한 기본 기능을 제공 합니다. 경계 컨트롤은 홀로그램 주위에 상자를 표시 하 여 상호 작용할 수 있음을 나타냅니다. 상자의 모퉁이 및 가장자리에 대 한 핸들은 개체의 크기 조정, 회전 또는 변환을 허용 합니다. 또한 경계 컨트롤은 사용자 입력에 반응 합니다. 예를 들어 HoloLens 2에서 경계 컨트롤은 손가락 근접에 응답 하 고 개체에서의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 제공 합니다. 모든 상호 작용 및 시각적 개체를 쉽게 사용자 지정할 수 있습니다.

## <a name="example-scene"></a>장면 예

장면에서 범위 제어 구성의 예제를 찾을 수 있습니다 `BoundsControlExamples` .

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Inspector 속성

### <a name="target-object"></a>대상 개체

이 속성은 경계 컨트롤 조작을 통해 변환할 개체를 지정 합니다. 개체를 설정 하지 않으면 기본적으로 owner 개체가 됩니다.

### <a name="activation-behavior"></a>활성화 동작

범위 제어 인터페이스를 활성화 하는 몇 가지 옵션이 있습니다.

* *시작 시 활성화*: 장면을 시작한 후에 범위 컨트롤이 표시 됩니다.
* *근접 별 활성화*: 트레일러 식이 개체에 가까이 있는 경우 경계 컨트롤이 표시 됩니다.
* *포인터로 활성화*: 경계 컨트롤은 손 모양 포인터의 대상으로 지정 될 때 표시 됩니다.
* *근접 및 포인터를 기준으로 활성화*: 경계 컨트롤은 손 모양 포인터의 대상 이거나 개체에 근접 하는 경우 표시 됩니다.
* *수동으로 활성화*: 범위 컨트롤이 자동으로 표시 되지 않습니다. BoundsControl 속성에 액세스 하 여 스크립트를 통해 수동으로 활성화할 수 있습니다.

### <a name="bounds-override"></a>경계 재정의

범위 계산을 위해 개체에서 상자 collider를 설정 합니다.

### <a name="box-padding"></a>상자 안쪽 여백

컨트롤의 범위를 계산 하는 데 사용 되는 collider 경계에 안쪽 여백을 추가 합니다. 이렇게 하면 상호 작용 뿐만 아니라 시각적 개체에도 영향을 줍니다.

### <a name="flatten-axis"></a>축 결합

컨트롤이 축 중 하나에서 평면화 되는지 여부를 나타내며 2 차원으로 만들고 해당 축을 따라 조작이 허용 되지 않습니다. 이 기능은 슬레이트와 같은 씬 개체에 사용할 수 있습니다.
평면화 축이 *자동 평면화* 로 설정 된 경우 스크립트는 크기가 가장 작은 축을 평면화 축으로 자동으로 선택 합니다.

### <a name="smoothing"></a>다듬기

다듬기 섹션에서는 컨트롤의 크기 조정 및 회전에 대 한 다듬기 동작을 구성할 수 있습니다.

### <a name="visuals"></a>시각적 개체

해당 하는 시각적 개체 구성 중 하나를 수정 하 여 범위 컨트롤의 모양을 구성할 수 있습니다.
시각적 구성은 연결 되거나 인라인 스크립트 가능한 개체 이며 [구성 개체 섹션](#configuration-objects)에 자세히 설명 되어 있습니다.

## <a name="configuration-objects"></a>구성 개체

컨트롤은 스크립트 가능한 개체로 저장 되 고 다른 인스턴스 또는 prefabs 간에 공유 될 수 있는 구성 개체 집합과 함께 제공 됩니다. 구성은 개별 스크립트 가능한 자산 파일 또는 prefabs 내에서 스크립트 가능한 중첩 자산으로 공유 하 고 연결할 수 있습니다. 외부 또는 중첩 된 스크립트 가능한 자산에 연결 하지 않고도 인스턴스에서 직접 구성을 정의할 수도 있습니다.

범위 컨트롤 검사기는 속성 검사자에 메시지를 표시 하 여 구성이 현재 인스턴스의 일부로 공유 되는지 또는 인라인 되는지 여부를 나타냅니다. 또한 공유 인스턴스는 범위 컨트롤 속성 창 자체에서 직접 편집할 수 없지만, 연결 되는 자산은 공유 구성에 대 한 실수로 인 한 변경 사항을 방지 하기 위해 직접 수정한 사용 해야 합니다.

현재 범위 제어는 다음 기능에 대 한 구성 개체 옵션을 제공 합니다.

* 핸들
  * [크기 조정 핸들](#scale-handles-configuration)
  * [회전 핸들](#rotation-handles-configuration)
  * [변환 핸들](#translation-handles-configuration)
* [링크/와이어 프레임](#links-configuration-wireframe)
* [상자 표시](#box-configuration)
* [근접 효과](#proximity-effect-configuration)

### <a name="box-configuration"></a>Box 구성

Box 구성은 collider size 및 box 안쪽 여백을 통해 정의 된 범위를 사용 하 여 실선 상자를 렌더링 합니다. 다음 속성을 설정할 수 있습니다.

* **Box 재질**: 상호 작용이 발생 하지 않을 때 렌더링 된 상자에 적용 되는 재질을 정의 합니다. 이 자료가 설정 된 경우에만 상자가 렌더링 됩니다.
* **Box grabbed material**: near 또는 far 상호 작용을 통해 사용자가 컨트롤과 상호 작용 하는 경우의 상자 재질입니다.
* **축 표시 비율 평면화**: 축 중 하나가 [평면화](#flatten-axis)되 면 상자에 적용 되는 눈금이 표시 됩니다.

### <a name="scale-handles-configuration"></a>크기 조정 핸들 구성

이 속성 서랍을 사용 하면 범위 컨트롤의 크기 조정 핸들 동작 및 시각화를 수정할 수 있습니다.

* **핸들 재질**: 핸들에 적용 되는 재질입니다.
* Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.
* **핸들 prefab**: 크기 조정 핸들의 선택적 prefab입니다. 설정 되지 않은 경우 MRTK는 큐브를 기본값으로 사용 합니다.
* **핸들 크기**: 크기 조정 핸들의 크기입니다.
* **Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.
* **조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.
* **핸들 무시 collider**: collider가 여기에 연결 된 경우 핸들은이 collider와 충돌을 무시 합니다.
* 컨트롤이 평면화 될 때 핸들에 사용할 **슬레이트 prefab**: Prefab를 처리 합니다.
* **배율 핸들 표시**: 핸들의 표시 여부를 제어 합니다.
* **크기 조정 동작**: 균일 또는 균일 하지 않은 배율로 설정할 수 있습니다.

### <a name="rotation-handles-configuration"></a>회전 핸들 구성

이 구성은 회전 핸들 동작을 정의 합니다.

* **핸들 재질**: 핸들에 적용 되는 재질입니다.
* Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.
* **핸들 prefab**: 핸들의 선택적 prefab입니다. 설정 되지 않은 경우 MRTK에서 구를 기본값으로 사용 합니다.
* **핸들 크기**: 핸들의 크기입니다.
* **Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.
* **조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.
* **핸들 무시 collider**: collider가 여기에 연결 된 경우 핸들은이 collider와 충돌을 무시 합니다.
* **Prefab collider type**: 만든 핸들과 함께 사용할 collider Type을 처리 합니다.
* **X에 대 한 핸들 표시**: x 축의 핸들 표시 여부를 제어 합니다.
* **Y에 대 한 핸들 표시**: y 축에 대 한 핸들의 표시 여부를 제어 합니다.
* **Z에 대 한 핸들 표시**: z 축의 핸들 표시 여부를 제어 합니다.

### <a name="translation-handles-configuration"></a>변환 핸들 구성

범위 제어에 대해 변환 핸들을 설정 및 구성할 수 있습니다. 변환 핸들은 기본적으로 비활성화 되어 있습니다.

* **핸들 재질**: 핸들에 적용 되는 재질입니다.
* Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.
* **핸들 prefab**: 핸들의 선택적 prefab입니다. 설정 되지 않은 경우 MRTK에서 구를 기본값으로 사용 합니다.
* **핸들 크기**: 핸들의 크기입니다.
* **Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.
* **조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.
* **핸들은 충돌체 무시:** 충돌체가 여기에 연결되면 핸들은 이 충돌체와의 충돌을 무시합니다.
* **프리팹 충돌체 형식 처리:** 생성된 핸들과 함께 사용할 충돌체 형식입니다.
* **X에 대한 핸들 표시**: X축에 대한 핸들의 표시를 제어합니다.
* **Y에 대한 핸들 표시: Y축** 핸들의 표시를 제어합니다.
* **Z에 대한 핸들 표시: Z축에** 대한 핸들의 표시를 제어합니다.

### <a name="links-configuration-wireframe"></a>링크 구성(와이어프레임)

링크 구성을 사용하면 경계 컨트롤의 와이어프레임 기능을 사용할 수 있습니다. 다음 속성을 구성할 수 있습니다.

* **와이어프레임 재질:** 와이어프레임 메시에 적용되는 재질입니다.
* **와이어프레임 가장자리 반지름:** 와이어프레임의 두께입니다.
* **Wireframe 셰이프:** 와이어프레임의 모양은 입방형 또는 원통형일 수 있습니다.
* **와이어프레임 표시: 와이어프레임의** 표시를 제어합니다.

### <a name="proximity-effect-configuration"></a>근접 효과 구성

손까지의 거리를 기준으로 애니메이션이 있는 핸들을 표시하고 숨깁니다. 2단계 크기 조정 애니메이션이 있습니다. 기본값은 HoloLens 2 스타일 동작으로 설정됩니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **근접 효과 활성:** 근접 기반 핸들 활성화 사용
* **개체 중간 근접:** 첫 번째 단계 크기 조정을 위한 거리입니다.
* **개체 근접:** 두 번째 단계 크기 조정을 위한 거리입니다.
* **원거리 크기 조정:** 손의 범위가 범위 컨트롤 상호 작용('중간 근접 처리'로 정의된 거리)을 벗어나는 경우 핸들 자산의 기본 소수점 값입니다. 기본적으로 핸들을 숨기려면 0을 사용합니다.)
* **중간 규모:** 손을 경계 컨트롤 상호 작용 범위 내에 있는 경우 핸들 자산의 배율 값입니다(위의 '근접 핸들'에 의해 정의된 거리). 1을 사용하여 정상 크기 표시)
* **닫기 배율:** 손의 잡기 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값(위에서 '근접 핸들'로 정의된 거리)입니다. 1.x를 사용하여 더 큰 크기 표시)
* **원거리 증가율:** 손의 크기가 중간에서 원거리로 이동하면 근접 크기 조정된 개체의 배율을 조정합니다.
* **중간 증가율:** 손을 중간에서 가까운 근접으로 이동할 때 근접 크기 조정된 개체 배율을 평가합니다.
* **증가율 닫기:** 손의 근접한 위치에서 개체 중심까지 이동할 때 근접 크기 조정된 개체 배율을 평가합니다.

## <a name="constraint-system"></a>제약 조건 시스템

경계 컨트롤은 제약 [조건 관리자를](constraint-manager.md) 사용하여 경계 컨트롤 핸들을 사용하는 동안 변환, 회전 또는 크기 조정 동작을 제한하거나 수정할 수 있도록 지원합니다.

속성 검사자는 선택한 제약 조건 관리자를 스크롤하고 강조 표시하는 옵션을 사용하여 동일한 게임 개체에 연결된 사용 가능한 모든 제약 조건 관리자를 드롭다운에 표시합니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>이벤트

범위 컨트롤은 다음 이벤트를 제공합니다. 이 예제에서는 이러한 이벤트를 사용하여 오디오 피드백을 재생합니다.

* **회전 시작: 회전이** 시작될 때 발생합니다.
* **회전 중지: 회전이 중지될** 때 발생합니다.
* **Scale Started:** 크기 조정이 시작될 때 발생합니다.
* **크기 조정 중지:** 크기 조정이 중지되면 발생합니다.
* **번역 시작됨:** 번역이 시작될 때 발생합니다.
* **중지된 번역: 번역이** 중지되면 발생합니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elastics(실험적)

범위 컨트롤을 통해 개체를 조작할 때 탄력적 을 사용할 수 있습니다. [탄력적 시스템은](../elastics/elastic-system.md) 여전히 실험적 상태입니다. 탄력적 기능을 사용하려면 기존 Elastics Manager 구성 요소를 연결하거나 단추를 통해 새 Elastics Manager를 만들고 `Add Elastics Manager` 연결합니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>스타일 처리

기본적으로 스크립트를 할당하면 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) HoloLens 1세대 스타일의 핸들이 표시됩니다. HoloLens 2 스타일 핸들을 사용하려면 적절한 핸들 프리팹 및 재질을 할당해야 합니다.

![경계 컨트롤 핸들 스타일 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

다음은 HoloLens 2 스타일 범위 컨트롤 핸들의 프리팹, 재질 및 크기 조정 값입니다. 장면에서 이 예제를 찾을 수 `BoundsControlExamples` 있습니다.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>개체 조작자를 통해 변환 변경

범위 컨트롤을 와 함께 사용하여 특정 유형의 조작을 허용할 수 [`ObjectManipulator.cs`](object-manipulator.md) 있습니다(예: 개체 이동) 핸들을 사용하지 않습니다. 조작 처리기는 한 손 조작과 양손 상호 작용을 모두 지원합니다. [손 추적을](../input/hand-tracking.md) 사용하여 개체와 가까이에서 상호 작용할 수 있습니다.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

의 원거리 상호 작용을 사용하여 이동할 때 경계 컨트롤 가장자리가 동일한 방식으로 동작하도록 하려면 [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` 위의 스크린샷에 표시된 것처럼 조작 종료 시 조작 시작 시 에 대한 이벤트를 각각 에 연결하는 것이 좋습니다.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Unity 검사기를 사용하여 경계 컨트롤을 추가하고 구성하는 방법

1. 개체에 Box Collider 추가
2. `BoundsControl`개체에 스크립트 할당
3. 'Activation' 메서드와 같은 옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)
4. (선택 사항) HoloLens 2 스타일 경계 컨트롤에 대한 프리팹 및 재질 할당(아래 [스타일 처리](#handle-styles) 섹션 참조)

> [!NOTE]
> 검사기에서 *대상 개체* 및 *경계 재정의* 필드를 사용하여 여러 자식 구성 요소가 있는 개체의 특정 개체 및 충돌체를 할당합니다.

![범위 제어](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>코드에서 경계 컨트롤을 추가하고 구성하는 방법

1. GameObject 큐브 인스턴스화

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundsControl`AddComponent<>()를 사용하여 충돌체가 있는 개체에 스크립트 할당

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. 컨트롤에서 직접 또는 스크립트 가능한 구성 중 하나를 통해 옵션을 구성합니다(아래 [검사기 속성](#inspector-properties) 및 [구성](#configuration-objects) 섹션 참조).

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (선택 사항) HoloLens 2 스타일 경계 컨트롤에 대한 프리팹 및 재질을 할당합니다. 재질과 프리팹을 동적으로 로드해야 하므로 검사자를 통해 할당해야 합니다.

> [!NOTE]
> Unity의 'Resources' 폴더 또는 [Shader.Find를]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 사용하여 셰이더를 동적으로 로드하는 것은 런타임에 셰이더 순열이 누락될 수 있기 때문에 권장되지 않습니다.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>예제: MinMaxScaleConstraint를 사용하여 최소, 최대 범위 컨트롤 배율 설정

최소 및 최대 크기 조정을 설정하려면 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 컨트롤에 를 연결합니다. 경계 컨트롤이 제약 조건 관리자를 자동으로 연결하고 활성화하면 MinMaxScaleConstraint가 연결 및 구성되면 변환 변경 내용에 자동으로 적용됩니다.

MinMaxScaleConstraint를 사용하여 에 대한 최소 및 최대 배율도 설정할 수 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 있습니다.

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>예제: 게임 개체 주위에 경계 컨트롤 추가

개체 주위에 경계 컨트롤을 추가하려면 `BoundsControl` 구성 요소를 추가하기만 하면됩니다.

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>경계 상자에서 마이그레이션

[경계 상자를](bounding-box.md) 사용하는 기존 프리팹 및 인스턴스는 MRTK 도구 패키지의 일부인 [마이그레이션 창을](../tools/migration-window.md) 통해 새 경계 컨트롤로 업그레이드할 수 있습니다.

경계 상자의 개별 인스턴스를 업그레이드하기 위해 구성 요소의 속성 검사자 내에 마이그레이션 옵션도 있습니다.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>참조

* [개체 조작자](object-manipulator.md)
* [제약 조건 관리자](constraint-manager.md)
* [마이그레이션 기간](../tools/migration-window.md)
* [탄력적 시스템(실험적)](../elastics/elastic-system.md)
