---
title: 개체 컬렉션 스크롤
description: 개요 메뉴 유형 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 스크롤 개체
ms.openlocfilehash: a97ea9919cf484cf5240dde027f38baca37ba9570588bca032bee9c116aed873
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221755"
---
# <a name="scrolling-object-collection"></a>개체 컬렉션 스크롤

![개체 컬렉션 스크롤](../images/scrolling-collection/ScrollingCollection_Main.jpg)

MRTK 스크롤 개체 컬렉션은 포함된 보기 가능한 영역을 통해 3D 콘텐츠를 스크롤할 수 있는 UX 구성 요소입니다. 스크롤 이동은 근사 또는 원거리 입력 상호 작용 및 개별 페이지 지정을 통해 트리거할 수 있습니다. 대화형 개체와 비대화형 개체를 모두 지원합니다.

## <a name="getting-started-with-the-scrolling-object-collection"></a>스크롤 개체 컬렉션 시작

### <a name="setting-up-the-scene"></a>장면 설정

1. 새 Unity 장면을 만듭니다.
1. **장면에** 추가 및 구성 Mixed Reality Toolkit 이동하여 MRTK를  >  **장면에 추가합니다.**

### <a name="setting-up-the-scrolling-object"></a>스크롤 개체 설정

1. 장면에서 빈 게임 개체를 만들고 위치를 (0, 0, 1)로 변경합니다.
1. 게임 [개체에 스크롤 개체 컬렉션](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 구성 요소를 추가합니다.

    스크롤 개체 컬렉션이 추가되면 상자 충돌체와 [거의 상호 작용이 가능한](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 구성 요소가 루트 게임 개체에 자동으로 연결됩니다. 이러한 구성 요소를 사용하면 스크롤 개체가 포인터 터치 또는 클릭과 같은 근사 및 원거리 상호 작용 입력 이벤트를 수신 대기할 수 있습니다.  

    MRTK 스크롤 개체 컬렉션에는 루트 스크롤 개체 계층 구조 아래에 자식 게임 개체로 생성되는 두 가지 중요한 요소가 있습니다.
    * `Container` - 모든 스크롤 콘텐츠 개체는 컨테이너 게임 개체의 자식이어야 합니다.
    * `Clipping bounds` - 스크롤 콘텐츠 마스킹을 사용하는 경우 클리핑 범위 요소는 경계 내의 스크롤 가능한 콘텐츠만 표시되도록 합니다. 클리핑 경계 게임 개체에는 비활성화된 상자 충돌체와 [클리핑 상자](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)의 두 가지 구성 요소가 있습니다.

![개체 컬렉션 요소 스크롤](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>스크롤 개체에 콘텐츠 추가

스크롤 개체 컬렉션을 그리드 개체 [컬렉션과](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 결합하여 크기 및 간격이 균일한 정렬된 요소의 그리드에서 콘텐츠를 레이아웃할 수 있습니다.

1. 스크롤 컨테이너의 자식으로 빈 게임 개체를 만듭니다.
1. 게임 개체에 그리드 개체 컬렉션 구성 요소를 추가합니다.
1. 세로 단일 열 스크롤의 경우 검사기 탭에서 그리드 개체 컬렉션을 다음과 같이 구성합니다.
    * **Num 열:** 1
    * **레이아웃:** column then row
    * **앵커:** 왼쪽 위
1. 내용 개체의 크기에 따라 **셀 너비와** **높이를** 변경합니다.
1. 콘텐츠 개체를 그리드 개체의 자식으로 추가합니다.
1. **업데이트 컬렉션** 를 누릅니다.

![모눈 레이아웃](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> 스크롤 콘텐츠 개체 재질은 보기 가능한 영역에 대한 클리핑 효과가 제대로 작동하려면 [MRTK 표준 셰이더를](../rendering/MRTK-standard-shader.md) 사용해야 합니다.

> [!NOTE]
> 스크롤 콘텐츠 마스킹을 사용하는 경우 스크롤 개체 컬렉션은 렌더러가 연결된 모든 콘텐츠 개체에 [재질 인스턴스](../rendering/material-instance.md) 구성 요소를 추가합니다. 이 구성 요소는 인스턴스화 재질 수명을 관리하고 메모리 성능을 향상시키는 데 사용됩니다.

### <a name="configuring-the-scrolling-viewable-area"></a>스크롤할 수 있는 영역 구성

1. 개체의 단일 열을 세로로 스크롤하려면 검사기 탭에서 다음과 같이 스크롤 개체 컬렉션을 구성합니다.
    * **계층당 셀** 수: 1
    * 원하는 표시 행 수에 따라 **페이지당 계층** 수를 선택합니다.
1. 콘텐츠 개체의 크기에 따라 **페이지 셀 너비**, **높이** 및 **깊이를** 변경합니다.

스크롤할 수 있는 영역 외부에 있는 콘텐츠 개체가 비활성화된 반면 스크롤 와이어프레임과 교차하는 개체는 클리핑 기본 형식에 의해 부분적으로 마스킹될 수 있습니다.

![볼 수 있는 영역](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>편집기에서 스크롤 개체 컬렉션 테스트

1. 재생을 누르고 스페이스바를 길게 눌러 입력 시뮬레이션 손을 표시합니다.
1. 스크롤 충돌체 또는 스크롤 대화형 콘텐츠에 포커스가 올 때까지 손을 이동하고 마우스 왼쪽에서 위아래로 클릭하고 끌어 스크롤 이동을 트리거합니다.

## <a name="controlling-the-scrolling-object-from-code"></a>코드에서 스크롤 개체 제어

MRTK 스크롤 개체 컬렉션은 속성 구성에 따라 해당 위치를 맞춰 스크롤 컨테이너를 이동할 수 있는 몇 가지 공용 메서드를 `pagination` 노출합니다.

스크롤 개체 컬렉션 페이지 지정 인터페이스에 액세스하는 방법의 예는 폴더 아래에서 사용할 수 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 있습니다. [스크롤 가능한 페이지 지정](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 예제 스크립트는 장면의 모든 기존 스크롤 개체 컬렉션에 연결할 수 있습니다. 그런 다음 Unity 이벤트를 노출하는 장면 구성 요소(예: [MRTK 단추)에서](button.md)스크립트를 참조할 수 있습니다.

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a>개체 컬렉션 속성 스크롤

| 일반          | Description                                   |
| :--------------- | :-------------------------------------------- |
| 스크롤 방향 | 콘텐츠를 스크롤해야 하는 방향입니다. |

| 페이지 매김     | Description                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| 계층당 셀 수 | 위로 스크롤 뷰에 있는 행의 셀 수 또는 왼쪽 오른쪽 스크롤 뷰의 열에 있는 셀 수입니다. |
| 페이지당 계층 | 스크롤 영역에 표시되는 계층의 수입니다.                                                            |
| 페이지 셀      | 페이지가 지정 셀의 차원입니다.                                                                        |

| 고급 설정           | Description                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 마스크 편집 모드              | 클리핑 상자 마스킹 경계를 정의하기 위한 편집 모드입니다. 'Auto'는 자동으로 페이지 지정 값을 사용합니다. 'Manual'을 사용하면 클리핑 상자 개체를 직접 조작할 수 있습니다. |
| 충돌자 편집 모드          | 스크롤 상호 작용 충돌 경계를 정의하기 위한 모드를 편집합니다. 'Auto'는 자동으로 페이지 지정 값을 사용합니다. 'Manual'을 사용하면 충돌체를 직접 조작할 수 있습니다.     |
| 스크롤 가능                  | 근접/원거리 상호 작용을 사용하여 스크롤을 사용하거나 사용하지 않도록 설정합니다.                                                                                                                      |
| 미리 렌더링할 때 사용           | scrollingObjectCollection이 Camera OnPreRender 이벤트를 사용하여 콘텐츠 표시 여부를 관리할지 여부를 전환합니다.                                                          |
| 페이지가 지정 곡선            | 페이지가 지정하는 애니메이션 곡선입니다.                                                                                                                                            |
| 애니메이션 길이            | PaginationCurve가 평가하는 데 걸리는 시간(초)입니다.                                                                                                 |
| 손 델타 스크롤 임계값 | 거리(미터)는 스크롤 끌기를 트리거하기 전에 현재 포인터가 스크롤 방향을 따라 이동될 수 있습니다.                                                        |
| 전면 터치 거리        | 거리(미터)는 터치 상호 작용이 스크롤 보기의 앞에서 시작되었는지 확인하는 데 사용되는 로컬 xy 평면을 배치합니다.                                           |
| 릴리스 임계값           | 터치 개입에서 해제로 전환하는 데 필요한 스크롤 경계에서 인출된 양(미터)입니다.                                                                |

| 속도            | Description                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| 속도 유형    | 스크롤러에 대해 원하는 속도 대체 형식입니다.                                                      |
| 속도 승수 | 스크롤에 적용할 (추가) 속도입니다.                                                       |
| Velocity 지체     | 속도에 적용되는 falloff의 양입니다.                                                                  |
| 반송 승수   | 프레임당 폴오프 또는 항목당 폴오프를 사용할 때 목록의 오버스크롤에 더 많은 반송을 추가하는 승수입니다. |

| 디버그 옵션         | Description                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| 마스크 사용          | 스크롤 콘텐츠의 표시 모드입니다. 기본값은 스크롤 표시 가능 영역 외부의 모든 개체를 마스킹합니다. |
| 임계값 평면 표시 | true이면 편집기는 스크롤 경계를 중심으로 터치 릴리스 임계값 평면을 렌더링합니다.            |
| 디버그 페이지 지정      | 이 섹션을 사용하여 런타임 중에 스크롤 페이지 지정을 디버그할 수 있습니다.                                             |

| 이벤트              | Description                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 클릭            | 스크롤 배경 충돌체 또는 대화형 콘텐츠 중에서 클릭을 받을 때 트리거됩니다.                             |
| 터치 시작 시    | 스크롤 배경 충돌체 또는 대화형 콘텐츠가 거의 상호 작용 터치를 받을 때 트리거됩니다.            |
| 터치 종료 시      | 가까운 상호 작용 포인터가 릴리스 임계값 평면을 초과할 때 활성 터치 상호 작용이 종료될 때 트리거됩니다. |
| 시작 시 | 스크롤 컨테이너가 상호 작용, 속도 폴오프 또는 페이지 매김에 의해 이동하기 시작할 때 트리거됩니다.                            |
| 2018년 3월 종료   | 스크롤 컨테이너가 상호 작용, 속도 폴오프 또는 페이지 매김에 의해 이동을 중지할 때 트리거됩니다.                             |

## <a name="scrolling-example-scene"></a>스크롤 예제 장면

**ScrollingObjectCollection.unity** 예제 장면에는 각각 다른 속도의 falloff 구성이 있는 3개의 스크롤 가능한 예제가 있습니다. 장면 예에는 계층 구조에서 기본적으로 사용하지 않도록 설정된 표면 배치 동작을 보여 주는 벽이 포함되어 있습니다. 예제 장면은 폴더 아래에서 찾을 수 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 있습니다.

![스크롤 개체 컬렉션 예제 장면](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>스크롤 예제 프리팹

편의상 두 개의 스크롤 개체 컬렉션 프리팹을 사용할 수 있습니다. 예제 프리팹은 폴더 아래에서 찾을 수 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 있습니다.

![개체 컬렉션 프리팹 스크롤](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>추가 정보

* [클리핑 기본형](../rendering/clipping-primitive.md)
* [재질 인스턴스](../rendering/material-instance.md)
* [표준 셰이더](../rendering/MRTK-standard-shader.md)
* [개체 컬렉션](object-collection.md)
