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
# <a name="object-collection"></a><span data-ttu-id="c7b9e-104">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="c7b9e-104">Object collection</span></span>

![개체 컬렉션](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="c7b9e-106">개체 컬렉션은 미리 정의된 3차원 도형으로 개체 배열의 레이아웃을 지정하는 데 도움이 되는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="c7b9e-107">평면, 실린더, 구 및 방사형을 비롯한 다양한 표면 스타일을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="c7b9e-108">Unity에서 모든 개체를 지원하기 때문에 2D 및 3D 개체를 모두 레이아웃하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="c7b9e-109">개체 컬렉션 스크립트</span><span class="sxs-lookup"><span data-stu-id="c7b9e-109">Object collection scripts</span></span>

- <span data-ttu-id="c7b9e-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 는 원통, 평면, 구, 방사형 표면 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="c7b9e-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 은 분산형 스타일 컬렉션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="c7b9e-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 에서는 GridObjectCollection에 대한 몇 가지 추가 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="c7b9e-113">**참고:** TileGridObjectCollection은 를 확장하지 않으며 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 여러 버그가 있습니다(문제 [6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)참조).</span><span class="sxs-lookup"><span data-stu-id="c7b9e-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="c7b9e-114">따라서 를 사용하는 것이 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Grid 개체 컬렉션 - 원통](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="c7b9e-116">Grid 개체 컬렉션 - 원통</span><span class="sxs-lookup"><span data-stu-id="c7b9e-116">Grid Object Collection - Cylinder</span></span> | ![Grid 개체 컬렉션 - Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="c7b9e-118">Grid 개체 컬렉션 - Sphere</span><span class="sxs-lookup"><span data-stu-id="c7b9e-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Grid 개체 컬렉션 - 방사형](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="c7b9e-120">Grid 개체 컬렉션 - 방사형</span><span class="sxs-lookup"><span data-stu-id="c7b9e-120">Grid Object Collection - Radial</span></span> | ![Grid 개체 컬렉션 - 평면](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="c7b9e-122">Grid 개체 컬렉션 - 평면</span><span class="sxs-lookup"><span data-stu-id="c7b9e-122">Grid Object Collection - Plane</span></span> |
|![분산된 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="c7b9e-124">분산된 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="c7b9e-124">Scattered Object Collection</span></span> | ![타일 그리드 개체 컬렉션](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="c7b9e-126">타일 그리드 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="c7b9e-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="c7b9e-127">개체 컬렉션을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="c7b9e-127">How to use an object collection</span></span>

<span data-ttu-id="c7b9e-128">컬렉션을 만들려면 빈 GameObject를 만들고 개체 컬렉션 스크립트 중 하나를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="c7b9e-129">모든 개체를 GameObject의 자식으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="c7b9e-130">자식 개체 추가가 완료되면 검사기 패널에서 *컬렉션 업데이트* 단추를 클릭하여 개체 컬렉션을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="c7b9e-131">개체는 컬렉션 매개 변수에 따라 장면에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="c7b9e-132">업데이트 컬렉션도 코드를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-132">Update Collection can be accessed through the code too.</span></span>

![개체 컬렉션 스크립트](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="c7b9e-134">`GridObjectCollection` 콘텐츠 맞춤</span><span class="sxs-lookup"><span data-stu-id="c7b9e-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="c7b9e-135">GridObjectCollection의 콘텐츠를 정렬하여 부모 개체가 컬렉션의 위쪽/가운데/아래쪽 및 왼쪽/가운데/오른쪽에 고정되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="c7b9e-136">**앵커** 속성을 사용하여 콘텐츠 맞춤을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="c7b9e-137">`GridObjectCollection` 레이아웃 순서</span><span class="sxs-lookup"><span data-stu-id="c7b9e-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="c7b9e-138">**레이아웃** 필드를 사용하여 자식이 배치되는 행/열 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="c7b9e-139">**Column Then Row** - 자식은 먼저 가로(열)로 배치된 다음 세로(행)로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="c7b9e-140">**Num 열(또는** 코드의 열 속성)을 사용하여 표의 열 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![열 및 행 레이아웃](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="c7b9e-142">**Row Then Column** - 자식은 먼저 세로(행)로 배치된 다음 가로(열별)로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="c7b9e-143">**Num 행(또는** 코드의 Rows 속성)을 사용하여 표의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![행 및 열 레이아웃](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="c7b9e-145">**가로** - 자식은 열만 사용하여 단일 행에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="c7b9e-146">**세로** - 자식은 행만 사용하여 단일 열에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="c7b9e-147">개체 컬렉션 예제</span><span class="sxs-lookup"><span data-stu-id="c7b9e-147">Object collection examples</span></span>

<span data-ttu-id="c7b9e-148">`ObjectCollectionExamples`(Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) 예제 장면에는 개체 컬렉션 형식의 다양한 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="c7b9e-149">[요소의 주기적 테이블은](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 개체 컬렉션의 작동 방식을 보여 주는 예제 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="c7b9e-150">개체 컬렉션을 사용하여 3D 요소 상자를 다양한 모양으로 레이아웃합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="c7b9e-151">개체 컬렉션 형식</span><span class="sxs-lookup"><span data-stu-id="c7b9e-151">Object collection types</span></span>

<span data-ttu-id="c7b9e-152">**3D 개체**</span><span class="sxs-lookup"><span data-stu-id="c7b9e-152">**3D objects**</span></span>

<span data-ttu-id="c7b9e-153">개체 컬렉션을 사용하여 가져온 3D 개체의 레이아웃을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="c7b9e-154">아래 예제에서는 컬렉션을 사용하는 3D 자식 모델 개체의 평면 및 원통형 레이아웃을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![개체 컬렉션 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="c7b9e-156">**2D 개체**</span><span class="sxs-lookup"><span data-stu-id="c7b9e-156">**2D Objects**</span></span>

<span data-ttu-id="c7b9e-157">개체 컬렉션은 2D 이미지에서 crated할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="c7b9e-158">예를 들어 여러 이미지를 그리드 스타일로 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-158">For example, multiple images can be placed in a grid style.</span></span>

![개체 컬렉션 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
