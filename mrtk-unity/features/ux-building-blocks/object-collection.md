---
title: 개체 컬렉션
description: MRTK의 개체 컬렉션 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 개체 컬렉션,
ms.openlocfilehash: 6705bd7093dbcd81912153872e4fd07c703fc5c0b9c081e0287589a7c8e959ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197558"
---
# <a name="object-collection"></a>개체 컬렉션

![개체 컬렉션](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

개체 컬렉션은 미리 정의 된 3 차원 도형에서 개체의 배열을 레이아웃 하는 데 도움이 되는 스크립트입니다. 평면, 원통, 구 및 방사형을 비롯 한 다양 한 표면 스타일을 지원 합니다. Unity에서 개체를 지원 하기 때문에 2D 및 3D 개체를 모두 레이아웃 하는 데 사용할 수 있습니다.

## <a name="object-collection-scripts"></a>개체 컬렉션 스크립트

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 원통, 평면, 구, 방사형 표면 유형 지원
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 분산 스타일 컬렉션 지원  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) GridObjectCollection에 대 한 몇 가지 추가 옵션을 제공 합니다. **참고:** TileGridObjectCollection는 확장 되지 않으며 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 여러 버그가 있습니다 ( [문제 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)참조). 따라서을 사용 하는 것이 좋습니다 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![그리드 개체 컬렉션-실린더](../images/object-collection/MRTK_ObjectCollectionCylinder.png) 그리드 개체 컬렉션-실린더 | ![그리드 개체 컬렉션-구](../images/object-collection/MRTK_ObjectCollectionSphere.png) 그리드 개체 컬렉션-구 |
|:--- | :--- |
|![그리드 개체 컬렉션-방사형](../images/object-collection/MRTK_ObjectCollectionRadial.png) 그리드 개체 컬렉션-방사형 | ![그리드 개체 컬렉션-평면](../images/object-collection/MRTK_ObjectCollectionPlane.png) 그리드 개체 컬렉션-평면 |
|![분산 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionScattered.png) 분산 개체 컬렉션 | ![바둑판식 모눈 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) 바둑판식 모눈 개체 컬렉션 |

## <a name="how-to-use-an-object-collection"></a>개체 컬렉션을 사용 하는 방법

컬렉션을 만들려면 빈 GameObject 만든 다음 개체 컬렉션 스크립트 중 하나를 할당 합니다. 모든 개체는 GameObject의 자식으로 추가할 수 있습니다. 자식 개체를 모두 추가한 후에는 검사기 패널에서 *컬렉션 업데이트* 단추를 클릭 하 여 개체 컬렉션을 생성 합니다. 개체는 컬렉션 매개 변수에 따라 장면에 배치 됩니다. 코드를 통해 업데이트 컬렉션에 액세스할 수 있습니다.

![개체 컬렉션 스크립트](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` 콘텐츠 맞춤

부모 개체가 컬렉션의 위쪽/가운데/아래쪽 및 왼쪽/가운데/오른쪽에 고정 되도록 GridObjectCollection의 콘텐츠를 정렬할 수 있습니다. **앵커** 속성을 사용 하 여 콘텐츠 맞춤을 지정 합니다.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` 레이아웃 순서

**레이아웃** 필드를 사용 하 여 자식이 배치 되는 행/열 순서를 지정 합니다.

**열이 행** -자식을 먼저 가로 (열)로 배치 된 다음 세로 (행별로)로 배치 됩니다. 숫자 **열** (또는 코드의 열 속성)을 사용 하 여 표의 열 수를 지정 합니다.

![열 다음 행 레이아웃](../images/object-collection/MRTK_ColumnThenRow.png)

**그런 다음 열** -자식은 먼저 세로 (행별로)로 배치 된 다음 가로 (열)로 배치 됩니다. 표의 행 수를 지정 하려면 **Num rows** (또는 코드에서 rows 속성)를 사용 합니다.

![행 및 열 레이아웃](../images/object-collection/MRTK_RowThenColumn.png)

**가로형** 은 열만 사용 하 여 단일 행에 배치 됩니다.

**세로** -자식 항목이 행만 사용 하 여 단일 열에 배치 됩니다.

## <a name="object-collection-examples"></a>개체 컬렉션 예제

`ObjectCollectionExamples`(Asset/MRTK/example/데모/UX/Collections/장면/ObjectCollectionExamples unity) 예제 장면에는 개체 컬렉션 형식의 다양 한 예제가 포함 되어 있습니다.

[요소의 정기 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 개체 컬렉션의 작동 방식을 보여 주는 예제 앱입니다. 개체 컬렉션을 사용 하 여 여러 도형의 3D 요소 상자를 레이아웃 합니다.

## <a name="object-collection-types"></a>개체 컬렉션 형식

**3D 개체**

개체 컬렉션을 사용 하 여 가져온 3D 개체의 레이아웃을 지정할 수 있습니다. 아래 예제에서는 컬렉션을 사용 하는 3D의 3 차원 모델 개체에 대 한 평면 및 원통형 레이아웃을 보여 줍니다.

![개체 컬렉션 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D 개체**

개체 컬렉션은 2D 이미지에서 만들 수도 있습니다. 예를 들어 여러 이미지를 그리드 스타일로 배치할 수 있습니다.

![개체 컬렉션 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
