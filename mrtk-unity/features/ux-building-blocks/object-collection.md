---
title: 개체 컬렉션
description: MRTK의 개체 컬렉션 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 개체 컬렉션,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177050"
---
# <a name="object-collection"></a>개체 컬렉션

![개체 컬렉션](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

개체 컬렉션은 미리 정의된 3차원 도형으로 개체 배열의 레이아웃을 지정하는 데 도움이 되는 스크립트입니다. 평면, 실린더, 구 및 방사형을 비롯한 다양한 표면 스타일을 지원합니다. Unity에서 모든 개체를 지원하기 때문에 2D 및 3D 개체를 모두 레이아웃하는 데 사용할 수 있습니다.

## <a name="object-collection-scripts"></a>개체 컬렉션 스크립트

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 는 원통, 평면, 구, 방사형 표면 형식을 지원합니다.
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 은 분산형 스타일 컬렉션을 지원합니다.  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 에서는 GridObjectCollection에 대한 몇 가지 추가 옵션을 제공합니다. **참고:** TileGridObjectCollection은 를 확장하지 않으며 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 여러 버그가 있습니다(문제 [6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)참조). 따라서 를 사용하는 것이 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 좋습니다.

|![Grid 개체 컬렉션 - 원통](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Grid 개체 컬렉션 - 원통 | ![Grid 개체 컬렉션 - Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Grid 개체 컬렉션 - Sphere |
|:--- | :--- |
|![Grid 개체 컬렉션 - 방사형](../images/object-collection/MRTK_ObjectCollectionRadial.png) Grid 개체 컬렉션 - 방사형 | ![Grid 개체 컬렉션 - 평면](../images/object-collection/MRTK_ObjectCollectionPlane.png) Grid 개체 컬렉션 - 평면 |
|![분산된 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionScattered.png) 분산된 개체 컬렉션 | ![타일 그리드 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) 타일 그리드 개체 컬렉션 |

## <a name="how-to-use-an-object-collection"></a>개체 컬렉션을 사용하는 방법

컬렉션을 만들려면 빈 GameObject를 만들고 개체 컬렉션 스크립트 중 하나를 할당합니다. 모든 개체를 GameObject의 자식으로 추가할 수 있습니다. 자식 개체 추가가 완료되면 검사기 패널에서 *컬렉션 업데이트* 단추를 클릭하여 개체 컬렉션을 생성합니다. 개체는 컬렉션 매개 변수에 따라 장면에 배치됩니다. 업데이트 컬렉션도 코드를 통해 액세스할 수 있습니다.

![개체 컬렉션 스크립트](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` 콘텐츠 맞춤

GridObjectCollection의 콘텐츠를 정렬하여 부모 개체가 컬렉션의 위쪽/가운데/아래쪽 및 왼쪽/가운데/오른쪽에 고정되도록 할 수 있습니다. **앵커** 속성을 사용하여 콘텐츠 맞춤을 지정합니다.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` 레이아웃 순서

**레이아웃** 필드를 사용하여 자식이 배치되는 행/열 순서를 지정합니다.

**Column Then Row** - 자식은 먼저 가로(열)로 배치된 다음 세로(행)로 배치됩니다. **Num 열(또는** 코드의 열 속성)을 사용하여 표의 열 수를 지정합니다.

![열 및 행 레이아웃](../images/object-collection/MRTK_ColumnThenRow.png)

**Row Then Column** - 자식은 먼저 세로(행)로 배치된 다음 가로(열별)로 배치됩니다. **Num 행(또는** 코드의 Rows 속성)을 사용하여 표의 행 수를 지정합니다.

![행 및 열 레이아웃](../images/object-collection/MRTK_RowThenColumn.png)

**가로** - 자식은 열만 사용하여 단일 행에 배치됩니다.

**세로** - 자식은 행만 사용하여 단일 열에 배치됩니다.

## <a name="object-collection-examples"></a>개체 컬렉션 예제

`ObjectCollectionExamples`(Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) 예제 장면에는 개체 컬렉션 형식의 다양한 예제가 포함되어 있습니다.

[요소의 주기적 테이블은](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 개체 컬렉션의 작동 방식을 보여 주는 예제 앱입니다. 개체 컬렉션을 사용하여 3D 요소 상자를 다양한 모양으로 레이아웃합니다.

## <a name="object-collection-types"></a>개체 컬렉션 형식

**3D 개체**

개체 컬렉션을 사용하여 가져온 3D 개체의 레이아웃을 지정할 수 있습니다. 아래 예제에서는 컬렉션을 사용하는 3D 자식 모델 개체의 평면 및 원통형 레이아웃을 보여줍니다.

![개체 컬렉션 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D 개체**

개체 컬렉션은 2D 이미지에서 crated할 수도 있습니다. 예를 들어 여러 이미지를 그리드 스타일로 배치할 수 있습니다.

![개체 컬렉션 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
