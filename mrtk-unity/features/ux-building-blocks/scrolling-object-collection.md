---
title: 스크롤 개체 컬렉션
description: 개요 메뉴 유형 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 스크롤 개체
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300118"
---
# <a name="scrolling-object-collection"></a>스크롤 개체 컬렉션

![스크롤 개체 컬렉션](../images/scrolling-collection/ScrollingCollection_Main.jpg)

MRTK 스크롤 개체 컬렉션은 포함 된 볼 수 있는 영역을 통해 3D 콘텐츠를 스크롤할 수 있도록 하는 UX 구성 요소입니다. 스크롤 이동은 근거리 또는 원거리 입력 상호 작용과 불연속 페이지 매김에 의해 트리거될 수 있습니다. 대화형 및 비 대화형 개체를 모두 지원 합니다.

## <a name="getting-started-with-the-scrolling-object-collection"></a>스크롤 개체 컬렉션 시작

### <a name="setting-up-the-scene"></a>장면 설정

1. 새 unity 장면을 만듭니다.
1. **Mixed Reality Toolkit** 에 추가 하 여  >  **장면 및 구성** 으로 이동 하 여 mrtk를 장면에 추가 합니다.

### <a name="setting-up-the-scrolling-object"></a>스크롤 개체 설정

1. 장면에 빈 게임 개체를 만들고 해당 위치를 (0, 0, 1)로 변경 합니다.
1. Game 개체에 [스크롤 개체 컬렉션](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 구성 요소를 추가 합니다.

    스크롤 개체 컬렉션이 추가 되 면 box collider 및 [near 인터랙션 touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 구성 요소가 루트 게임 개체에 자동으로 연결 됩니다. 이러한 구성 요소를 사용 하면 scroll 개체가 포인터 터치 또는 클릭과 같은 근거리 및 원거리 상호 작용 입력 이벤트를 수신할 수 있습니다.  

    MRTK 스크롤되는 개체 컬렉션에는 루트 스크롤 개체 계층 구조 아래에 자식 게임 개체로 생성 되는 두 개의 중요 한 요소가 있습니다.
    * `Container` -모든 스크롤 콘텐츠 개체는 container game 개체의 자식 이어야 합니다.
    * `Clipping bounds` -스크롤 콘텐츠 마스킹을 사용 하도록 설정 된 경우에는 클리핑 범위 요소가 경계 내에서 스크롤 가능한 콘텐츠만 표시 되도록 합니다. 클리핑 경계 게임 개체에는 비활성화 된 상자 collider 및 [클리핑 상자](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)와 같은 두 가지 구성 요소가 있습니다.

![개체 컬렉션 요소 스크롤](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>스크롤 개체에 콘텐츠 추가

스크롤 개체 컬렉션을 [그리드 개체 컬렉션과](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 결합 하 여 크기와 간격이 균일 하 게 정렬 된 요소의 모눈에서 콘텐츠를 레이아웃 할 수 있습니다.

1. 빈 게임 개체를 스크롤 컨테이너의 자식으로 만듭니다.
1. Game 개체에 그리드 개체 컬렉션 구성 요소를 추가 합니다.
1. 세로 단일 열 스크롤의 경우 검사기 탭에서 다음과 같이 그리드 개체 컬렉션을 구성 합니다.
    * **Num columns**: 1
    * **레이아웃**: 열 다음 행
    * **앵커**: 왼쪽 위
1. 콘텐츠 개체의 크기에 따라 **셀 너비** 와 **높이** 를 변경 합니다.
1. 콘텐츠 개체를 grid 개체의 자식으로 추가 합니다.
1. **업데이트 컬렉션** 을 누릅니다.

![모눈 레이아웃](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> 표시 가능한 영역에 대 한 클리핑 효과가 제대로 작동 하려면 모든 스크롤 콘텐츠 개체 자료에서 [Mrtk 표준 셰이더](../rendering/MRTK-standard-shader.md) 를 사용 해야 합니다.

> [!NOTE]
> 스크롤 콘텐츠 마스킹을 사용 하는 경우 스크롤 개체 컬렉션은 렌더러가 첨부 된 모든 콘텐츠 개체에 [재질 인스턴스](../rendering/material-instance.md) 구성 요소를 추가 합니다. 이 구성 요소는 인스턴스 자료 수명을 관리 하 고 메모리 성능을 향상 하는 데 사용 됩니다.

### <a name="configuring-the-scrolling-viewable-area"></a>스크롤 가능 영역 구성

1. 개체의 단일 열을 통한 수직 스크롤의 경우 검사기 탭에서 다음과 같이 스크롤 개체 컬렉션을 구성 합니다.
    * **계층 당 셀** 수: 1
    * 원하는 표시 되는 행 수에 따라 **페이지 당 계층** 수를 선택 합니다.
1. 콘텐츠 개체의 크기에 따라 **페이지 셀 너비**, **높이** 및 **깊이** 를 변경 합니다.

스크롤 가능 영역 외부에 있는 콘텐츠 개체가 이제 비활성화 되는 반면, 스크롤 와이어 프레임을 교차 하는 개체는 클리핑 기본 형식에 의해 부분적으로 마스크 될 수 있습니다.

![볼 수 있는 영역](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>편집기에서 스크롤 개체 컬렉션 테스트

1. 재생을 누르고 공백 표시줄을 잡고 입력 시뮬레이션 손을 표시 합니다.
1. 스크롤 collider 또는 대화형 콘텐츠 스크롤이 포커스를 끌 때까지 손을 이동 하 고 마우스 왼쪽 단추를 클릭 하 여 위아래로 끌어서 스크롤 이동을 트리거합니다.

## <a name="controlling-the-scrolling-object-from-code"></a>코드에서 스크롤 개체 제어

MRTK 스크롤 개체 컬렉션은 속성 구성에 따라 위치를 스냅 하 여 스크롤 컨테이너를 이동할 수 있는 몇 가지 공용 메서드를 노출 합니다 `pagination` .

스크롤 개체 컬렉션 페이지 매김 인터페이스에 액세스 하는 방법에 대 한 예제는 폴더에서 사용할 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` . 스크롤할 수 있는 [페이지 매김](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 예제 스크립트는 장면의 모든 기존 스크롤 개체 컬렉션에 연결할 수 있습니다. 그런 다음 Unity 이벤트를 표시 하는 장면 구성 요소 (예: [Mrtk 단추](button.md))에서 스크립트를 참조할 수 있습니다.

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

| 일반                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 스크롤 방향             | 콘텐츠를 스크롤할 방향입니다.|

| 페이지 매김                   |               설명                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 계층 당 셀 수               | Up-down 스크롤 보기의 행에 있는 셀 수 또는 왼쪽에서 오른쪽 스크롤 뷰의 열에 있는 셀 수입니다.                                                                                                         |
| 페이지당 계층 수               | 스크롤 영역의 표시 계층 수입니다.                                                                                                                                                                         |
| 페이지 셀                    | 페이지 매김 셀의 크기입니다.                  |

| 고급 설정            |                  설명                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 마스크 편집 모드               | 클리핑 상자 마스킹 경계를 정의 하기 위한 편집 모드입니다. 자동 페이지 값을 자동으로 사용 하려면 ' 자동 '을 선택 합니다. 클리핑 상자 개체의 직접 조작을 사용 하려면 ' 수동 '을 선택 합니다.|
| Collider 편집 모드           | 스크롤 상호 작용 collider 경계를 정의 하기 위한 편집 모드입니다. 자동 페이지 값을 자동으로 사용 하려면 ' 자동 '을 선택 합니다. Collider의 직접 조작을 사용 하려면 ' 수동 '을 선택 합니다.|
| 스크롤할 수 있음                   | 거의 모든 상호 작용으로 스크롤을 사용 하거나 사용 하지 않도록 설정 합니다.                  |
| 프리 렌더링에 사용            | ScrollingObjectCollection가 카메라 OnPreRender 이벤트를 사용 하 여 콘텐츠 표시 유형을 관리 하는지 여부를 전환 합니다.                  |
| 페이지 매김 곡선             | 페이지 매김을 위한 애니메이션 곡선입니다.                  |
| 애니메이션 길이             | PaginationCurve을 평가 하는 데 걸리는 시간 (초)입니다.                  |
| 손 모양 델타 스크롤 임계값  | 스크롤 끌기를 트리거하기 전에 현재 포인터가 스크롤 방향을 따라 이동 하는 거리 (미터)입니다.                  |
| 전면 터치 거리         | 터치 조작이 스크롤 뷰의 맨 앞에서 시작 되었는지 확인 하는 데 사용 되는 로컬 xy 평면을 측정 하는 데 사용 하는 거리 (미터)입니다.                  |
| 릴리스 임계값            | 터치에서 릴리스된 것으로 전환 하는 데 필요한 스크롤 경계에서 요금을 미터 단위로 인출 합니다.                  |

| 속도 |               설명                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 개발 속도의 유형       | Scroller에 대 한 원하는 유형의 속도 감소입니다.                                                                                        |
| 속도 승수     | Scroller에 적용할 (추가) 속도의 양입니다.                                                                                                                                                        |
| 속도 dampen     | 속도에 적용 되는 밝기의 양입니다. |
| 바운스 승수     | 프레임당 밝기를 사용 하거나 항목당 밝기를 사용 하는 경우 목록의 과도 한 스크롤에 더 많은 바운스를 추가 하는 승수입니다. |

| 디버그 옵션 |            설명                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 마스크 사용       | 스크롤 콘텐츠의 표시 모드입니다. 기본값은 표시 가능한 스크롤 영역 밖의 모든 개체를 마스킹 합니다.                                                                                        |
| 임계값 평면 표시     | True 이면 편집기에서 스크롤 경계를 중심으로 터치 릴리스 임계값 비행기를 렌더링 합니다.                                                                                                                                                        |
| 디버그 페이지 매김     | 이 섹션을 사용 하 여 런타임 중 스크롤 페이지 매김을 디버깅할 수 있습니다. |

| 이벤트|    Description                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 클릭 시       | 스크롤 배경 collider 또는 해당 대화형 콘텐츠로 인해 클릭이 수신 될 때 트리거되는 이벤트입니다.                                                                                        |
| 터치 시작 시     | Scroll background collider 또는 해당 대화형 콘텐츠 중 하나에서 근접 한 상호 작용 터치를 받을 때 트리거되는 이벤트입니다.                                                                                                                                                        |
| 터치 종료 시     | 근접 한 상호 작용 포인터가 릴리스 임계값 평면 중 하나를 통과 하 여 활성 터치 조작이 종료 될 때 트리거되는 이벤트입니다. |
| 모멘텀 시작 됨     | 스크롤 컨테이너가 상호 작용을 시작 하거나, 속도를 위반 하거나, 페이지 매김을 시작할 때 트리거되는 이벤트입니다. |
| 모멘텀 종료 됨     | 스크롤 컨테이너가 상호 작용을 통해 이동을 중지할 때 트리거되는 이벤트입니다. 개발 속도가 중단 됩니다. |

## <a name="scrolling-example-scene"></a>예제 장면 스크롤

**ScrollingObjectCollection** 예제 장면은 세 개의 스크롤 가능한 예제로 구성 되며 각각은 서로 다른 속도의 밝기를 사용 합니다. 예 장면에는 계층에서 기본적으로 사용 하지 않도록 설정 된 표면 배치 동작을 보여 주는 벽이 포함 되어 있습니다. 예제 장면을 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` .

![스크롤 개체 컬렉션 예제 장면](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>스크롤 예 prefabs

편의상 두 개의 스크롤 개체 컬렉션 prefabs를 사용할 수 있습니다. 예제 prefabs는 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` .

![스크롤 개체 컬렉션 prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>참조

* [기본 클리핑](../rendering/clipping-primitive.md)
* [자재 인스턴스](../rendering/material-instance.md)
* [표준 셰이더](../rendering/MRTK-standard-shader.md)
* [개체 컬렉션](object-collection.md)
