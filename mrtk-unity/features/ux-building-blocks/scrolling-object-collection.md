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
# <a name="scrolling-object-collection"></a><span data-ttu-id="926b2-104">스크롤 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="926b2-104">Scrolling object collection</span></span>

![스크롤 개체 컬렉션](../images/scrolling-collection/ScrollingCollection_Main.jpg)

<span data-ttu-id="926b2-106">MRTK 스크롤 개체 컬렉션은 포함 된 볼 수 있는 영역을 통해 3D 콘텐츠를 스크롤할 수 있도록 하는 UX 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-106">The MRTK scrolling object collection is an UX component that enables scrolling of 3D content through a contained viewable area.</span></span> <span data-ttu-id="926b2-107">스크롤 이동은 근거리 또는 원거리 입력 상호 작용과 불연속 페이지 매김에 의해 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-107">The scrolling movement can be triggered by near or far input interaction and by discrete pagination.</span></span> <span data-ttu-id="926b2-108">대화형 및 비 대화형 개체를 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-108">It supports both interactive and non-interactive objects.</span></span>

## <a name="getting-started-with-the-scrolling-object-collection"></a><span data-ttu-id="926b2-109">스크롤 개체 컬렉션 시작</span><span class="sxs-lookup"><span data-stu-id="926b2-109">Getting started with the scrolling object collection</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="926b2-110">장면 설정</span><span class="sxs-lookup"><span data-stu-id="926b2-110">Setting up the scene</span></span>

1. <span data-ttu-id="926b2-111">새 unity 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-111">Create a new unity scene.</span></span>
1. <span data-ttu-id="926b2-112">**Mixed Reality Toolkit** 에 추가 하 여  >  **장면 및 구성** 으로 이동 하 여 mrtk를 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-112">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

### <a name="setting-up-the-scrolling-object"></a><span data-ttu-id="926b2-113">스크롤 개체 설정</span><span class="sxs-lookup"><span data-stu-id="926b2-113">Setting up the scrolling object</span></span>

1. <span data-ttu-id="926b2-114">장면에 빈 게임 개체를 만들고 해당 위치를 (0, 0, 1)로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-114">Create an empty game object in the scene and change its position to (0, 0, 1).</span></span>
1. <span data-ttu-id="926b2-115">Game 개체에 [스크롤 개체 컬렉션](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-115">Add a [scrolling object collection](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) component to the game object.</span></span>

    <span data-ttu-id="926b2-116">스크롤 개체 컬렉션이 추가 되 면 box collider 및 [near 인터랙션 touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 구성 요소가 루트 게임 개체에 자동으로 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-116">When the scrolling object collection is added, a box collider and a [near interaction touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component will be automatically attached to the root game object.</span></span> <span data-ttu-id="926b2-117">이러한 구성 요소를 사용 하면 scroll 개체가 포인터 터치 또는 클릭과 같은 근거리 및 원거리 상호 작용 입력 이벤트를 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-117">These components allow the scroll object to listen to near and far interaction input events, like a pointer touch or click.</span></span>  

    <span data-ttu-id="926b2-118">MRTK 스크롤되는 개체 컬렉션에는 루트 스크롤 개체 계층 구조 아래에 자식 게임 개체로 생성 되는 두 개의 중요 한 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-118">The MRTK scrolling object collection has two important elements that are created as child game objects under the root scrolling object hierarchy:</span></span>
    * <span data-ttu-id="926b2-119">`Container` -모든 스크롤 콘텐츠 개체는 container game 개체의 자식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-119">`Container` - All scrolling content objects must be children of the container game object.</span></span>
    * <span data-ttu-id="926b2-120">`Clipping bounds` -스크롤 콘텐츠 마스킹을 사용 하도록 설정 된 경우에는 클리핑 범위 요소가 경계 내에서 스크롤 가능한 콘텐츠만 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-120">`Clipping bounds` - If scrolling content masking is enabled, the clipping bounds element ensures that only the scrollable content inside its boundaries is visible.</span></span> <span data-ttu-id="926b2-121">클리핑 경계 게임 개체에는 비활성화 된 상자 collider 및 [클리핑 상자](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)와 같은 두 가지 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-121">The clipping bounds game object has two components: a disabled box collider and a [clipping box](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).</span></span>

![개체 컬렉션 요소 스크롤](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a><span data-ttu-id="926b2-123">스크롤 개체에 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="926b2-123">Adding content to the scrolling object</span></span>

<span data-ttu-id="926b2-124">스크롤 개체 컬렉션을 [그리드 개체 컬렉션과](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 결합 하 여 크기와 간격이 균일 하 게 정렬 된 요소의 모눈에서 콘텐츠를 레이아웃 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-124">The scrolling object collection can be combined with a [grid object collection](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to layout content in a grid of aligned elements that have uniform size and spacing.</span></span>

1. <span data-ttu-id="926b2-125">빈 게임 개체를 스크롤 컨테이너의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-125">Create an empty game object as a child of the scroll container.</span></span>
1. <span data-ttu-id="926b2-126">Game 개체에 그리드 개체 컬렉션 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-126">Add a grid object collection component to the game object.</span></span>
1. <span data-ttu-id="926b2-127">세로 단일 열 스크롤의 경우 검사기 탭에서 다음과 같이 그리드 개체 컬렉션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-127">For a vertical single column scroll, in the inspector tab, configure the grid object collection as follow:</span></span>
    * <span data-ttu-id="926b2-128">**Num columns**: 1</span><span class="sxs-lookup"><span data-stu-id="926b2-128">**Num columns**: 1</span></span>
    * <span data-ttu-id="926b2-129">**레이아웃**: 열 다음 행</span><span class="sxs-lookup"><span data-stu-id="926b2-129">**Layout**: column then row</span></span>
    * <span data-ttu-id="926b2-130">**앵커**: 왼쪽 위</span><span class="sxs-lookup"><span data-stu-id="926b2-130">**Anchor**: upper left</span></span>
1. <span data-ttu-id="926b2-131">콘텐츠 개체의 크기에 따라 **셀 너비** 와 **높이** 를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-131">Change the **cell width** and **height** according to the dimensions of the content objects.</span></span>
1. <span data-ttu-id="926b2-132">콘텐츠 개체를 grid 개체의 자식으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-132">Add the content objects as children of the grid object.</span></span>
1. <span data-ttu-id="926b2-133">**업데이트 컬렉션** 을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-133">Press **update collection**.</span></span>

![모눈 레이아웃](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> <span data-ttu-id="926b2-135">표시 가능한 영역에 대 한 클리핑 효과가 제대로 작동 하려면 모든 스크롤 콘텐츠 개체 자료에서 [Mrtk 표준 셰이더](../rendering/MRTK-standard-shader.md) 를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-135">Any scrolling content object material must use the [MRTK standard shader](../rendering/MRTK-standard-shader.md) in order for the clipping effect on the viewable area to work properly.</span></span>

> [!NOTE]
> <span data-ttu-id="926b2-136">스크롤 콘텐츠 마스킹을 사용 하는 경우 스크롤 개체 컬렉션은 렌더러가 첨부 된 모든 콘텐츠 개체에 [재질 인스턴스](../rendering/material-instance.md) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-136">If scrolling content masking is enabled, the scrolling object collection will add a [material instance](../rendering/material-instance.md) component to any content objects that have a renderer attached.</span></span> <span data-ttu-id="926b2-137">이 구성 요소는 인스턴스 자료 수명을 관리 하 고 메모리 성능을 향상 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-137">This component is used to manage instanced materials lifetime and improve memory performance.</span></span>

### <a name="configuring-the-scrolling-viewable-area"></a><span data-ttu-id="926b2-138">스크롤 가능 영역 구성</span><span class="sxs-lookup"><span data-stu-id="926b2-138">Configuring the scrolling viewable area</span></span>

1. <span data-ttu-id="926b2-139">개체의 단일 열을 통한 수직 스크롤의 경우 검사기 탭에서 다음과 같이 스크롤 개체 컬렉션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-139">For vertical scrolling through a single column of objects, in the inspector tab, configure the scrolling object collection as follow:</span></span>
    * <span data-ttu-id="926b2-140">**계층 당 셀** 수: 1</span><span class="sxs-lookup"><span data-stu-id="926b2-140">**Cells per tier**: 1</span></span>
    * <span data-ttu-id="926b2-141">원하는 표시 되는 행 수에 따라 **페이지 당 계층** 수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-141">Choose the number of **tiers per page** according to the desired number of visible rows</span></span>
1. <span data-ttu-id="926b2-142">콘텐츠 개체의 크기에 따라 **페이지 셀 너비**, **높이** 및 **깊이** 를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-142">Change the **page cell width**, **height** and **depth** according to the dimensions of the content objects.</span></span>

<span data-ttu-id="926b2-143">스크롤 가능 영역 외부에 있는 콘텐츠 개체가 이제 비활성화 되는 반면, 스크롤 와이어 프레임을 교차 하는 개체는 클리핑 기본 형식에 의해 부분적으로 마스크 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-143">Notice how the content objects lying outside the scrolling viewable area are now disabled, while objects intersecting the scroll wireframe might be partially masked by the clipping primitive.</span></span>

![볼 수 있는 영역](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a><span data-ttu-id="926b2-145">편집기에서 스크롤 개체 컬렉션 테스트</span><span class="sxs-lookup"><span data-stu-id="926b2-145">Testing the scrolling object collection in the editor</span></span>

1. <span data-ttu-id="926b2-146">재생을 누르고 공백 표시줄을 잡고 입력 시뮬레이션 손을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-146">Press play and hold the space bar to show an input simulation hand.</span></span>
1. <span data-ttu-id="926b2-147">스크롤 collider 또는 대화형 콘텐츠 스크롤이 포커스를 끌 때까지 손을 이동 하 고 마우스 왼쪽 단추를 클릭 하 여 위아래로 끌어서 스크롤 이동을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-147">Move the hand until the scrolling collider or any scrolling interactive content is in focus and trigger the scrolling movement by clicking and dragging up and down with the left mouse.</span></span>

## <a name="controlling-the-scrolling-object-from-code"></a><span data-ttu-id="926b2-148">코드에서 스크롤 개체 제어</span><span class="sxs-lookup"><span data-stu-id="926b2-148">Controlling the scrolling object from code</span></span>

<span data-ttu-id="926b2-149">MRTK 스크롤 개체 컬렉션은 속성 구성에 따라 위치를 스냅 하 여 스크롤 컨테이너를 이동할 수 있는 몇 가지 공용 메서드를 노출 합니다 `pagination` .</span><span class="sxs-lookup"><span data-stu-id="926b2-149">The MRTK scrolling object collection exposes a few public methods that allow moving the scrolling container by snapping its position according to the `pagination` properties configuration.</span></span>

<span data-ttu-id="926b2-150">스크롤 개체 컬렉션 페이지 매김 인터페이스에 액세스 하는 방법에 대 한 예제는 폴더에서 사용할 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` .</span><span class="sxs-lookup"><span data-stu-id="926b2-150">An example of how to access the scrolling object collection pagination interface is available to use under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` folder.</span></span> <span data-ttu-id="926b2-151">스크롤할 수 있는 [페이지 매김](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 예제 스크립트는 장면의 모든 기존 스크롤 개체 컬렉션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-151">The [scrollable pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) example script can be linked to any existing scrolling object collection in the scene.</span></span> <span data-ttu-id="926b2-152">그런 다음 Unity 이벤트를 표시 하는 장면 구성 요소 (예: [Mrtk 단추](button.md))에서 스크립트를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-152">The script can then be referenced by scene components exposing Unity events (e.g, [MRTK button](button.md)).</span></span>

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

## <a name="scrolling-object-collection-properties"></a><span data-ttu-id="926b2-153">개체 컬렉션 속성 스크롤</span><span class="sxs-lookup"><span data-stu-id="926b2-153">Scrolling object collection properties</span></span>

| <span data-ttu-id="926b2-154">일반</span><span class="sxs-lookup"><span data-stu-id="926b2-154">General</span></span>                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-155">스크롤 방향</span><span class="sxs-lookup"><span data-stu-id="926b2-155">Scroll direction</span></span>             | <span data-ttu-id="926b2-156">콘텐츠를 스크롤할 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-156">The direction in which content should scroll.</span></span>|

| <span data-ttu-id="926b2-157">페이지 매김</span><span class="sxs-lookup"><span data-stu-id="926b2-157">Pagination</span></span>                   |               <span data-ttu-id="926b2-158">설명</span><span class="sxs-lookup"><span data-stu-id="926b2-158">Description</span></span>                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-159">계층 당 셀 수</span><span class="sxs-lookup"><span data-stu-id="926b2-159">Cells per tier</span></span>               | <span data-ttu-id="926b2-160">Up-down 스크롤 보기의 행에 있는 셀 수 또는 왼쪽에서 오른쪽 스크롤 뷰의 열에 있는 셀 수입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-160">Number of cells in a row on up-down scroll view or number of cells in a column on left-right scroll view.</span></span>                                                                                                         |
| <span data-ttu-id="926b2-161">페이지당 계층 수</span><span class="sxs-lookup"><span data-stu-id="926b2-161">Tiers per page</span></span>               | <span data-ttu-id="926b2-162">스크롤 영역의 표시 계층 수입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-162">Number of visible tiers in the scrolling area.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="926b2-163">페이지 셀</span><span class="sxs-lookup"><span data-stu-id="926b2-163">Page cell</span></span>                    | <span data-ttu-id="926b2-164">페이지 매김 셀의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-164">Dimensions of the pagination cell.</span></span>                  |

| <span data-ttu-id="926b2-165">고급 설정</span><span class="sxs-lookup"><span data-stu-id="926b2-165">Advanced settings</span></span>            |                  <span data-ttu-id="926b2-166">설명</span><span class="sxs-lookup"><span data-stu-id="926b2-166">Description</span></span>                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-167">마스크 편집 모드</span><span class="sxs-lookup"><span data-stu-id="926b2-167">Mask edit mode</span></span>               | <span data-ttu-id="926b2-168">클리핑 상자 마스킹 경계를 정의 하기 위한 편집 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-168">Edit modes for defining the clipping box masking boundaries.</span></span> <span data-ttu-id="926b2-169">자동 페이지 값을 자동으로 사용 하려면 ' 자동 '을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-169">Choose 'Auto' to automatically use pagination values.</span></span> <span data-ttu-id="926b2-170">클리핑 상자 개체의 직접 조작을 사용 하려면 ' 수동 '을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-170">Choose 'Manual' for enabling direct manipulation of the clipping box object.</span></span>|
| <span data-ttu-id="926b2-171">Collider 편집 모드</span><span class="sxs-lookup"><span data-stu-id="926b2-171">Collider edit mode</span></span>           | <span data-ttu-id="926b2-172">스크롤 상호 작용 collider 경계를 정의 하기 위한 편집 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-172">Edit modes for defining the scroll interaction collider boundaries.</span></span> <span data-ttu-id="926b2-173">자동 페이지 값을 자동으로 사용 하려면 ' 자동 '을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-173">Choose 'Auto' to automatically use pagination values.</span></span> <span data-ttu-id="926b2-174">Collider의 직접 조작을 사용 하려면 ' 수동 '을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-174">Choose 'Manual' for enabling direct manipulation of the collider.</span></span>|
| <span data-ttu-id="926b2-175">스크롤할 수 있음</span><span class="sxs-lookup"><span data-stu-id="926b2-175">Can scroll</span></span>                   | <span data-ttu-id="926b2-176">거의 모든 상호 작용으로 스크롤을 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-176">Enables/disables scrolling with near/far interaction.</span></span>                  |
| <span data-ttu-id="926b2-177">프리 렌더링에 사용</span><span class="sxs-lookup"><span data-stu-id="926b2-177">Use on pre render</span></span>            | <span data-ttu-id="926b2-178">ScrollingObjectCollection가 카메라 OnPreRender 이벤트를 사용 하 여 콘텐츠 표시 유형을 관리 하는지 여부를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-178">Toggles whether the scrollingObjectCollection will use the Camera OnPreRender event to manage content visibility.</span></span>                  |
| <span data-ttu-id="926b2-179">페이지 매김 곡선</span><span class="sxs-lookup"><span data-stu-id="926b2-179">Pagination curve</span></span>             | <span data-ttu-id="926b2-180">페이지 매김을 위한 애니메이션 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-180">Animation curve for pagination.</span></span>                  |
| <span data-ttu-id="926b2-181">애니메이션 길이</span><span class="sxs-lookup"><span data-stu-id="926b2-181">Animation length</span></span>             | <span data-ttu-id="926b2-182">PaginationCurve을 평가 하는 데 걸리는 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-182">The amount of time (in seconds) the PaginationCurve will take to evaluate.</span></span>                  |
| <span data-ttu-id="926b2-183">손 모양 델타 스크롤 임계값</span><span class="sxs-lookup"><span data-stu-id="926b2-183">Hand delta scroll threshold</span></span>  | <span data-ttu-id="926b2-184">스크롤 끌기를 트리거하기 전에 현재 포인터가 스크롤 방향을 따라 이동 하는 거리 (미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-184">The distance, in meters, the current pointer can travel along the scroll direction before triggering a scroll drag.</span></span>                  |
| <span data-ttu-id="926b2-185">전면 터치 거리</span><span class="sxs-lookup"><span data-stu-id="926b2-185">Front touch distance</span></span>         | <span data-ttu-id="926b2-186">터치 조작이 스크롤 뷰의 맨 앞에서 시작 되었는지 확인 하는 데 사용 되는 로컬 xy 평면을 측정 하는 데 사용 하는 거리 (미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-186">Distance, in meters, to position a local xy plane used to verify if a touch interaction started in the front of the scroll view.</span></span>                  |
| <span data-ttu-id="926b2-187">릴리스 임계값</span><span class="sxs-lookup"><span data-stu-id="926b2-187">Release threshold</span></span>            | <span data-ttu-id="926b2-188">터치에서 릴리스된 것으로 전환 하는 데 필요한 스크롤 경계에서 요금을 미터 단위로 인출 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-188">Withdraw amount, in meters, from the scroll boundaries needed to transition from touch engaged to released.</span></span>                  |

| <span data-ttu-id="926b2-189">속도</span><span class="sxs-lookup"><span data-stu-id="926b2-189">Velocity</span></span> |               <span data-ttu-id="926b2-190">설명</span><span class="sxs-lookup"><span data-stu-id="926b2-190">Description</span></span>                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-191">개발 속도의 유형</span><span class="sxs-lookup"><span data-stu-id="926b2-191">Type of velocity</span></span>       | <span data-ttu-id="926b2-192">Scroller에 대 한 원하는 유형의 속도 감소입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-192">The desired type of velocity falloff for the scroller.</span></span>                                                                                        |
| <span data-ttu-id="926b2-193">속도 승수</span><span class="sxs-lookup"><span data-stu-id="926b2-193">Velocity multiplier</span></span>     | <span data-ttu-id="926b2-194">Scroller에 적용할 (추가) 속도의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-194">Amount of (extra) velocity to be applied to scroller.</span></span>                                                                                                                                                        |
| <span data-ttu-id="926b2-195">속도 dampen</span><span class="sxs-lookup"><span data-stu-id="926b2-195">Velocity dampen</span></span>     | <span data-ttu-id="926b2-196">속도에 적용 되는 밝기의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-196">Amount of falloff applied to the velocity.</span></span> |
| <span data-ttu-id="926b2-197">바운스 승수</span><span class="sxs-lookup"><span data-stu-id="926b2-197">Bounce multiplier</span></span>     | <span data-ttu-id="926b2-198">프레임당 밝기를 사용 하거나 항목당 밝기를 사용 하는 경우 목록의 과도 한 스크롤에 더 많은 바운스를 추가 하는 승수입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-198">Multiplier to add more bounce to the overscroll of a list when using falloff per frame or falloff per item.</span></span> |

| <span data-ttu-id="926b2-199">디버그 옵션</span><span class="sxs-lookup"><span data-stu-id="926b2-199">Debug options</span></span> |            <span data-ttu-id="926b2-200">설명</span><span class="sxs-lookup"><span data-stu-id="926b2-200">Description</span></span>                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-201">마스크 사용</span><span class="sxs-lookup"><span data-stu-id="926b2-201">Mask enabled</span></span>       | <span data-ttu-id="926b2-202">스크롤 콘텐츠의 표시 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-202">Visibility mode of scroll content.</span></span> <span data-ttu-id="926b2-203">기본값은 표시 가능한 스크롤 영역 밖의 모든 개체를 마스킹 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-203">Default value will mask all objects outside of the scroll viewable area.</span></span>                                                                                        |
| <span data-ttu-id="926b2-204">임계값 평면 표시</span><span class="sxs-lookup"><span data-stu-id="926b2-204">Show threshold planes</span></span>     | <span data-ttu-id="926b2-205">True 이면 편집기에서 스크롤 경계를 중심으로 터치 릴리스 임계값 비행기를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-205">If true, the editor will render the touch release threshold planes around the scroll boundaries.</span></span>                                                                                                                                                        |
| <span data-ttu-id="926b2-206">디버그 페이지 매김</span><span class="sxs-lookup"><span data-stu-id="926b2-206">Debug pagination</span></span>     | <span data-ttu-id="926b2-207">이 섹션을 사용 하 여 런타임 중 스크롤 페이지 매김을 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-207">Use this section to debug the scroll pagination during runtime.</span></span> |

| <span data-ttu-id="926b2-208">이벤트</span><span class="sxs-lookup"><span data-stu-id="926b2-208">Events</span></span>|    <span data-ttu-id="926b2-209">Description</span><span class="sxs-lookup"><span data-stu-id="926b2-209">Description</span></span>                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="926b2-210">클릭 시</span><span class="sxs-lookup"><span data-stu-id="926b2-210">On click</span></span>       | <span data-ttu-id="926b2-211">스크롤 배경 collider 또는 해당 대화형 콘텐츠로 인해 클릭이 수신 될 때 트리거되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-211">Event triggered when the scroll background collider or any of its interactive content receives a click.</span></span>                                                                                        |
| <span data-ttu-id="926b2-212">터치 시작 시</span><span class="sxs-lookup"><span data-stu-id="926b2-212">On touch started</span></span>     | <span data-ttu-id="926b2-213">Scroll background collider 또는 해당 대화형 콘텐츠 중 하나에서 근접 한 상호 작용 터치를 받을 때 트리거되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-213">Event triggered when the scroll background collider or any of its interactive content receives a near interaction touch.</span></span>                                                                                                                                                        |
| <span data-ttu-id="926b2-214">터치 종료 시</span><span class="sxs-lookup"><span data-stu-id="926b2-214">On touch ended</span></span>     | <span data-ttu-id="926b2-215">근접 한 상호 작용 포인터가 릴리스 임계값 평면 중 하나를 통과 하 여 활성 터치 조작이 종료 될 때 트리거되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-215">Event triggered when an active touch interaction is terminated by having the near interaction pointer crossing one of the release threshold planes.</span></span> |
| <span data-ttu-id="926b2-216">모멘텀 시작 됨</span><span class="sxs-lookup"><span data-stu-id="926b2-216">On momentum started</span></span>     | <span data-ttu-id="926b2-217">스크롤 컨테이너가 상호 작용을 시작 하거나, 속도를 위반 하거나, 페이지 매김을 시작할 때 트리거되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-217">Event triggered when the scroll container starts moving by interaction, velocity fallofff or pagination.</span></span> |
| <span data-ttu-id="926b2-218">모멘텀 종료 됨</span><span class="sxs-lookup"><span data-stu-id="926b2-218">On momentum ended</span></span>     | <span data-ttu-id="926b2-219">스크롤 컨테이너가 상호 작용을 통해 이동을 중지할 때 트리거되는 이벤트입니다. 개발 속도가 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-219">Event triggered when the scroll container stops moving by interaction, velocity fallofff or pagination.</span></span> |

## <a name="scrolling-example-scene"></a><span data-ttu-id="926b2-220">예제 장면 스크롤</span><span class="sxs-lookup"><span data-stu-id="926b2-220">Scrolling example scene</span></span>

<span data-ttu-id="926b2-221">**ScrollingObjectCollection** 예제 장면은 세 개의 스크롤 가능한 예제로 구성 되며 각각은 서로 다른 속도의 밝기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-221">**ScrollingObjectCollection.unity** example scene consists of 3 scrollable examples, each one with a different velocity falloff configuration.</span></span> <span data-ttu-id="926b2-222">예 장면에는 계층에서 기본적으로 사용 하지 않도록 설정 된 표면 배치 동작을 보여 주는 벽이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-222">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="926b2-223">예제 장면을 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` .</span><span class="sxs-lookup"><span data-stu-id="926b2-223">The example scene can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` folder.</span></span>

![스크롤 개체 컬렉션 예제 장면](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a><span data-ttu-id="926b2-225">스크롤 예 prefabs</span><span class="sxs-lookup"><span data-stu-id="926b2-225">Scrolling example prefabs</span></span>

<span data-ttu-id="926b2-226">편의상 두 개의 스크롤 개체 컬렉션 prefabs를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="926b2-226">For convenience, two scrolling object collection prefabs are available to use.</span></span> <span data-ttu-id="926b2-227">예제 prefabs는 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` .</span><span class="sxs-lookup"><span data-stu-id="926b2-227">The example prefabs can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` folder.</span></span>

![스크롤 개체 컬렉션 prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a><span data-ttu-id="926b2-229">참조</span><span class="sxs-lookup"><span data-stu-id="926b2-229">See also</span></span>

* [<span data-ttu-id="926b2-230">기본 클리핑</span><span class="sxs-lookup"><span data-stu-id="926b2-230">Clipping Primitive</span></span>](../rendering/clipping-primitive.md)
* [<span data-ttu-id="926b2-231">자재 인스턴스</span><span class="sxs-lookup"><span data-stu-id="926b2-231">Material Instance</span></span>](../rendering/material-instance.md)
* [<span data-ttu-id="926b2-232">표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="926b2-232">Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
* [<span data-ttu-id="926b2-233">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="926b2-233">Object collection</span></span>](object-collection.md)
