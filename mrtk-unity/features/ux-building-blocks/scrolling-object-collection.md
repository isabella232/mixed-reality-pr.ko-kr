---
title: 스크롤 개체 컬렉션
description: 개요 메뉴 유형 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 스크롤 개체
ms.openlocfilehash: a724b9fb4a0f72910e16353a6c76b9e31005a76e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176607"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="e3076-104">스크롤 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="e3076-104">Scrolling object collection</span></span>

![스크롤 개체 컬렉션](../images/scrolling-collection/ScrollingCollection_Main.jpg)

<span data-ttu-id="e3076-106">MRTK 스크롤 개체 컬렉션은 포함된 보기 가능한 영역을 통해 3D 콘텐츠를 스크롤할 수 있는 UX 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-106">The MRTK scrolling object collection is an UX component that enables scrolling of 3D content through a contained viewable area.</span></span> <span data-ttu-id="e3076-107">스크롤 이동은 근사 또는 원거리 입력 상호 작용 및 개별 페이지 지정을 통해 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-107">The scrolling movement can be triggered by near or far input interaction and by discrete pagination.</span></span> <span data-ttu-id="e3076-108">대화형 개체와 비대화형 개체를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-108">It supports both interactive and non-interactive objects.</span></span>

## <a name="getting-started-with-the-scrolling-object-collection"></a><span data-ttu-id="e3076-109">스크롤 개체 컬렉션 시작</span><span class="sxs-lookup"><span data-stu-id="e3076-109">Getting started with the scrolling object collection</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="e3076-110">장면 설정</span><span class="sxs-lookup"><span data-stu-id="e3076-110">Setting up the scene</span></span>

1. <span data-ttu-id="e3076-111">새 Unity 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-111">Create a new unity scene.</span></span>
1. <span data-ttu-id="e3076-112">**장면에** 추가 및 구성 Mixed Reality Toolkit 이동하여 MRTK를  >  **장면에 추가합니다.**</span><span class="sxs-lookup"><span data-stu-id="e3076-112">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

### <a name="setting-up-the-scrolling-object"></a><span data-ttu-id="e3076-113">스크롤 개체 설정</span><span class="sxs-lookup"><span data-stu-id="e3076-113">Setting up the scrolling object</span></span>

1. <span data-ttu-id="e3076-114">장면에서 빈 게임 개체를 만들고 위치를 (0, 0, 1)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-114">Create an empty game object in the scene and change its position to (0, 0, 1).</span></span>
1. <span data-ttu-id="e3076-115">게임 [개체에 스크롤 개체 컬렉션](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-115">Add a [scrolling object collection](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) component to the game object.</span></span>

    <span data-ttu-id="e3076-116">스크롤 개체 컬렉션이 추가되면 상자 충돌체와 [거의 상호 작용이 가능한](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 구성 요소가 루트 게임 개체에 자동으로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-116">When the scrolling object collection is added, a box collider and a [near interaction touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component will be automatically attached to the root game object.</span></span> <span data-ttu-id="e3076-117">이러한 구성 요소를 사용하면 스크롤 개체가 포인터 터치 또는 클릭과 같은 근사 및 원거리 상호 작용 입력 이벤트를 수신 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-117">These components allow the scroll object to listen to near and far interaction input events, like a pointer touch or click.</span></span>  

    <span data-ttu-id="e3076-118">MRTK 스크롤 개체 컬렉션에는 루트 스크롤 개체 계층 구조 아래에 자식 게임 개체로 생성되는 두 가지 중요한 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-118">The MRTK scrolling object collection has two important elements that are created as child game objects under the root scrolling object hierarchy:</span></span>
    * <span data-ttu-id="e3076-119">`Container` - 모든 스크롤 콘텐츠 개체는 컨테이너 게임 개체의 자식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-119">`Container` - All scrolling content objects must be children of the container game object.</span></span>
    * <span data-ttu-id="e3076-120">`Clipping bounds` - 스크롤 콘텐츠 마스킹을 사용하는 경우 클리핑 범위 요소는 경계 내의 스크롤 가능한 콘텐츠만 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-120">`Clipping bounds` - If scrolling content masking is enabled, the clipping bounds element ensures that only the scrollable content inside its boundaries is visible.</span></span> <span data-ttu-id="e3076-121">클리핑 경계 게임 개체에는 비활성화된 상자 충돌체와 [클리핑 상자](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)의 두 가지 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-121">The clipping bounds game object has two components: a disabled box collider and a [clipping box](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).</span></span>

![개체 컬렉션 요소 스크롤](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a><span data-ttu-id="e3076-123">스크롤 개체에 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="e3076-123">Adding content to the scrolling object</span></span>

<span data-ttu-id="e3076-124">스크롤 개체 컬렉션을 그리드 개체 [컬렉션과](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 결합하여 균일한 크기와 간격을 갖는 정렬된 요소의 그리드에서 콘텐츠를 레이아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-124">The scrolling object collection can be combined with a [grid object collection](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to layout content in a grid of aligned elements that have uniform size and spacing.</span></span>

1. <span data-ttu-id="e3076-125">스크롤 컨테이너의 자식으로 빈 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-125">Create an empty game object as a child of the scroll container.</span></span>
1. <span data-ttu-id="e3076-126">게임 개체에 그리드 개체 컬렉션 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-126">Add a grid object collection component to the game object.</span></span>
1. <span data-ttu-id="e3076-127">세로 단일 열 스크롤의 경우 검사기 탭에서 그리드 개체 컬렉션을 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-127">For a vertical single column scroll, in the inspector tab, configure the grid object collection as follow:</span></span>
    * <span data-ttu-id="e3076-128">**Num 열:** 1</span><span class="sxs-lookup"><span data-stu-id="e3076-128">**Num columns**: 1</span></span>
    * <span data-ttu-id="e3076-129">**레이아웃:** column then row</span><span class="sxs-lookup"><span data-stu-id="e3076-129">**Layout**: column then row</span></span>
    * <span data-ttu-id="e3076-130">**앵커:** 왼쪽 위</span><span class="sxs-lookup"><span data-stu-id="e3076-130">**Anchor**: upper left</span></span>
1. <span data-ttu-id="e3076-131">내용 개체의 크기에 따라 **셀 너비와** **높이를** 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-131">Change the **cell width** and **height** according to the dimensions of the content objects.</span></span>
1. <span data-ttu-id="e3076-132">콘텐츠 개체를 그리드 개체의 자식으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-132">Add the content objects as children of the grid object.</span></span>
1. <span data-ttu-id="e3076-133">**업데이트 컬렉션** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-133">Press **update collection**.</span></span>

![모눈 레이아웃](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> <span data-ttu-id="e3076-135">스크롤 콘텐츠 개체 재질은 보기 가능한 영역에 대한 클리핑 효과가 제대로 작동하려면 [MRTK 표준 셰이더를](../rendering/MRTK-standard-shader.md) 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-135">Any scrolling content object material must use the [MRTK standard shader](../rendering/MRTK-standard-shader.md) in order for the clipping effect on the viewable area to work properly.</span></span>

> [!NOTE]
> <span data-ttu-id="e3076-136">스크롤 콘텐츠 마스킹을 사용하는 경우 스크롤 개체 컬렉션은 렌더러가 연결된 모든 콘텐츠 개체에 [재질 인스턴스](../rendering/material-instance.md) 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-136">If scrolling content masking is enabled, the scrolling object collection will add a [material instance](../rendering/material-instance.md) component to any content objects that have a renderer attached.</span></span> <span data-ttu-id="e3076-137">이 구성 요소는 인스턴스화 재질 수명을 관리하고 메모리 성능을 향상시키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-137">This component is used to manage instanced materials lifetime and improve memory performance.</span></span>

### <a name="configuring-the-scrolling-viewable-area"></a><span data-ttu-id="e3076-138">스크롤할 수 있는 영역 구성</span><span class="sxs-lookup"><span data-stu-id="e3076-138">Configuring the scrolling viewable area</span></span>

1. <span data-ttu-id="e3076-139">개체의 단일 열을 세로로 스크롤하려면 검사기 탭에서 스크롤 개체 컬렉션을 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-139">For vertical scrolling through a single column of objects, in the inspector tab, configure the scrolling object collection as follow:</span></span>
    * <span data-ttu-id="e3076-140">**계층당 셀** 수: 1</span><span class="sxs-lookup"><span data-stu-id="e3076-140">**Cells per tier**: 1</span></span>
    * <span data-ttu-id="e3076-141">원하는 표시 행 수에 따라 **페이지당 계층** 수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-141">Choose the number of **tiers per page** according to the desired number of visible rows</span></span>
1. <span data-ttu-id="e3076-142">콘텐츠 개체의 크기에 따라 **페이지 셀 너비**, **높이** 및 **깊이를** 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-142">Change the **page cell width**, **height** and **depth** according to the dimensions of the content objects.</span></span>

<span data-ttu-id="e3076-143">스크롤할 수 있는 영역 외부에 있는 콘텐츠 개체가 비활성화된 반면 스크롤 와이어프레임과 교차하는 개체는 클리핑 기본 형식에 의해 부분적으로 마스킹될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-143">Notice how the content objects lying outside the scrolling viewable area are now disabled, while objects intersecting the scroll wireframe might be partially masked by the clipping primitive.</span></span>

![볼 수 있는 영역](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a><span data-ttu-id="e3076-145">편집기에서 스크롤 개체 컬렉션 테스트</span><span class="sxs-lookup"><span data-stu-id="e3076-145">Testing the scrolling object collection in the editor</span></span>

1. <span data-ttu-id="e3076-146">재생을 누르고 스페이스바를 길게 눌러 입력 시뮬레이션 손을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-146">Press play and hold the space bar to show an input simulation hand.</span></span>
1. <span data-ttu-id="e3076-147">스크롤 충돌체 또는 스크롤 대화형 콘텐츠에 포커스가 올 때까지 손을 이동하고 마우스 왼쪽에서 위아래로 클릭하고 끌어 스크롤 이동을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-147">Move the hand until the scrolling collider or any scrolling interactive content is in focus and trigger the scrolling movement by clicking and dragging up and down with the left mouse.</span></span>

## <a name="controlling-the-scrolling-object-from-code"></a><span data-ttu-id="e3076-148">코드에서 스크롤 개체 제어</span><span class="sxs-lookup"><span data-stu-id="e3076-148">Controlling the scrolling object from code</span></span>

<span data-ttu-id="e3076-149">MRTK 스크롤 개체 컬렉션은 속성 구성에 따라 해당 위치를 맞춰 스크롤 컨테이너를 이동할 수 있는 몇 가지 공용 메서드를 `pagination` 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-149">The MRTK scrolling object collection exposes a few public methods that allow moving the scrolling container by snapping its position according to the `pagination` properties configuration.</span></span>

<span data-ttu-id="e3076-150">스크롤 개체 컬렉션 페이지 지정 인터페이스에 액세스하는 방법의 예는 폴더 아래에서 사용할 수 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-150">An example of how to access the scrolling object collection pagination interface is available to use under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` folder.</span></span> <span data-ttu-id="e3076-151">[스크롤 가능한 페이지 지정](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 예제 스크립트는 장면의 모든 기존 스크롤 개체 컬렉션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-151">The [scrollable pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) example script can be linked to any existing scrolling object collection in the scene.</span></span> <span data-ttu-id="e3076-152">그런 다음 Unity 이벤트를 노출하는 장면 구성 요소(예: [MRTK 단추)에서](button.md)스크립트를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-152">The script can then be referenced by scene components exposing Unity events (e.g, [MRTK button](button.md)).</span></span>

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

## <a name="scrolling-object-collection-properties"></a><span data-ttu-id="e3076-153">개체 컬렉션 속성 스크롤</span><span class="sxs-lookup"><span data-stu-id="e3076-153">Scrolling object collection properties</span></span>

| <span data-ttu-id="e3076-154">일반</span><span class="sxs-lookup"><span data-stu-id="e3076-154">General</span></span>          | <span data-ttu-id="e3076-155">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-155">Description</span></span>                                   |
| :--------------- | :-------------------------------------------- |
| <span data-ttu-id="e3076-156">스크롤 방향</span><span class="sxs-lookup"><span data-stu-id="e3076-156">Scroll direction</span></span> | <span data-ttu-id="e3076-157">콘텐츠를 스크롤해야 하는 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-157">The direction in which content should scroll.</span></span> |

| <span data-ttu-id="e3076-158">페이지 매김</span><span class="sxs-lookup"><span data-stu-id="e3076-158">Pagination</span></span>     | <span data-ttu-id="e3076-159">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-159">Description</span></span>                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3076-160">계층당 셀 수</span><span class="sxs-lookup"><span data-stu-id="e3076-160">Cells per tier</span></span> | <span data-ttu-id="e3076-161">위로 스크롤 뷰에 있는 행의 셀 수 또는 왼쪽 오른쪽 스크롤 뷰의 열에 있는 셀 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-161">Number of cells in a row on up-down scroll view or number of cells in a column on left-right scroll view.</span></span> |
| <span data-ttu-id="e3076-162">페이지당 계층</span><span class="sxs-lookup"><span data-stu-id="e3076-162">Tiers per page</span></span> | <span data-ttu-id="e3076-163">스크롤 영역에 표시되는 계층의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-163">Number of visible tiers in the scrolling area.</span></span>                                                            |
| <span data-ttu-id="e3076-164">페이지 셀</span><span class="sxs-lookup"><span data-stu-id="e3076-164">Page cell</span></span>      | <span data-ttu-id="e3076-165">페이지가 지정 셀의 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-165">Dimensions of the pagination cell.</span></span>                                                                        |

| <span data-ttu-id="e3076-166">고급 설정</span><span class="sxs-lookup"><span data-stu-id="e3076-166">Advanced settings</span></span>           | <span data-ttu-id="e3076-167">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-167">Description</span></span>                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3076-168">마스크 편집 모드</span><span class="sxs-lookup"><span data-stu-id="e3076-168">Mask edit mode</span></span>              | <span data-ttu-id="e3076-169">클리핑 상자 마스킹 경계를 정의하기 위한 편집 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-169">Edit modes for defining the clipping box masking boundaries.</span></span> <span data-ttu-id="e3076-170">'Auto'는 자동으로 페이지 지정 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-170">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="e3076-171">'Manual'을 사용하면 클리핑 상자 개체를 직접 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-171">'Manual' enables direct manipulation of the clipping box object.</span></span> |
| <span data-ttu-id="e3076-172">충돌자 편집 모드</span><span class="sxs-lookup"><span data-stu-id="e3076-172">Collider edit mode</span></span>          | <span data-ttu-id="e3076-173">스크롤 상호 작용 충돌 경계를 정의하기 위한 모드를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-173">Edit modes for defining the scroll interaction collider boundaries.</span></span> <span data-ttu-id="e3076-174">'Auto'는 자동으로 페이지 지정 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-174">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="e3076-175">'수동'을 사용하면 충돌체를 직접 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-175">'Manual' enables direct manipulation of the collider.</span></span>     |
| <span data-ttu-id="e3076-176">스크롤 가능</span><span class="sxs-lookup"><span data-stu-id="e3076-176">Can scroll</span></span>                  | <span data-ttu-id="e3076-177">근접/원거리 상호 작용을 사용하여 스크롤을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-177">Enables/disables scrolling with near/far interaction.</span></span>                                                                                                                      |
| <span data-ttu-id="e3076-178">미리 렌더링할 때 사용</span><span class="sxs-lookup"><span data-stu-id="e3076-178">Use on pre render</span></span>           | <span data-ttu-id="e3076-179">scrollingObjectCollection이 Camera OnPreRender 이벤트를 사용하여 콘텐츠 표시 여부를 관리할지 여부를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-179">Toggles whether the scrollingObjectCollection will use the Camera OnPreRender event to manage content visibility.</span></span>                                                          |
| <span data-ttu-id="e3076-180">페이지가 지정 곡선</span><span class="sxs-lookup"><span data-stu-id="e3076-180">Pagination curve</span></span>            | <span data-ttu-id="e3076-181">페이지가 지정하는 애니메이션 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-181">Animation curve for pagination.</span></span>                                                                                                                                            |
| <span data-ttu-id="e3076-182">애니메이션 길이</span><span class="sxs-lookup"><span data-stu-id="e3076-182">Animation length</span></span>            | <span data-ttu-id="e3076-183">PaginationCurve가 평가하는 데 걸리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-183">The amount of time (in seconds) the PaginationCurve will take to evaluate.</span></span>                                                                                                 |
| <span data-ttu-id="e3076-184">손 델타 스크롤 임계값</span><span class="sxs-lookup"><span data-stu-id="e3076-184">Hand delta scroll threshold</span></span> | <span data-ttu-id="e3076-185">거리(미터)는 스크롤 끌기를 트리거하기 전에 현재 포인터가 스크롤 방향을 따라 이동될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-185">The distance, in meters, the current pointer can travel along the scroll direction before triggering a scroll drag.</span></span>                                                        |
| <span data-ttu-id="e3076-186">전면 터치 거리</span><span class="sxs-lookup"><span data-stu-id="e3076-186">Front touch distance</span></span>        | <span data-ttu-id="e3076-187">거리(미터)는 터치 조작이 스크롤 보기의 앞에서 시작되었는지 확인하는 데 사용되는 로컬 xy 평면을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-187">Distance, in meters, to position a local xy plane used to verify if a touch interaction started in the front of the scroll view.</span></span>                                           |
| <span data-ttu-id="e3076-188">릴리스 임계값</span><span class="sxs-lookup"><span data-stu-id="e3076-188">Release threshold</span></span>           | <span data-ttu-id="e3076-189">터치 개입에서 해제로 전환하는 데 필요한 스크롤 경계에서 인출된 양(미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-189">Withdraw amount, in meters, from the scroll boundaries needed to transition from touch engaged to released.</span></span>                                                                |

| <span data-ttu-id="e3076-190">속도</span><span class="sxs-lookup"><span data-stu-id="e3076-190">Velocity</span></span>            | <span data-ttu-id="e3076-191">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-191">Description</span></span>                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3076-192">속도 유형</span><span class="sxs-lookup"><span data-stu-id="e3076-192">Type of velocity</span></span>    | <span data-ttu-id="e3076-193">스크롤러에 대해 원하는 속도 대체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-193">The desired type of velocity falloff for the scroller.</span></span>                                                      |
| <span data-ttu-id="e3076-194">Velocity 승수</span><span class="sxs-lookup"><span data-stu-id="e3076-194">Velocity multiplier</span></span> | <span data-ttu-id="e3076-195">스크롤에 적용할 (추가) 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-195">Amount of (extra) velocity to be applied to scroller.</span></span>                                                       |
| <span data-ttu-id="e3076-196">Velocity 지체</span><span class="sxs-lookup"><span data-stu-id="e3076-196">Velocity dampen</span></span>     | <span data-ttu-id="e3076-197">속도에 적용되는 falloff의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-197">Amount of falloff applied to the velocity.</span></span>                                                                  |
| <span data-ttu-id="e3076-198">반송 승수</span><span class="sxs-lookup"><span data-stu-id="e3076-198">Bounce multiplier</span></span>   | <span data-ttu-id="e3076-199">프레임당 폴오프 또는 항목당 폴오프를 사용할 때 목록의 오버스크롤에 더 많은 반송을 추가하는 승수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-199">Multiplier to add more bounce to the overscroll of a list when using falloff per frame or falloff per item.</span></span> |

| <span data-ttu-id="e3076-200">디버그 옵션</span><span class="sxs-lookup"><span data-stu-id="e3076-200">Debug options</span></span>         | <span data-ttu-id="e3076-201">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-201">Description</span></span>                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3076-202">마스크 사용</span><span class="sxs-lookup"><span data-stu-id="e3076-202">Mask enabled</span></span>          | <span data-ttu-id="e3076-203">스크롤 콘텐츠의 표시 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-203">Visibility mode of scroll content.</span></span> <span data-ttu-id="e3076-204">기본값은 표시 가능한 스크롤 영역 밖의 모든 개체를 마스킹 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-204">Default value will mask all objects outside of the scroll viewable area.</span></span> |
| <span data-ttu-id="e3076-205">임계값 평면 표시</span><span class="sxs-lookup"><span data-stu-id="e3076-205">Show threshold planes</span></span> | <span data-ttu-id="e3076-206">True 이면 편집기에서 스크롤 경계를 중심으로 터치 릴리스 임계값 비행기를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-206">If true, the editor will render the touch release threshold planes around the scroll boundaries.</span></span>            |
| <span data-ttu-id="e3076-207">디버그 페이지 매김</span><span class="sxs-lookup"><span data-stu-id="e3076-207">Debug pagination</span></span>      | <span data-ttu-id="e3076-208">이 섹션을 사용 하 여 런타임 중 스크롤 페이지 매김을 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-208">Use this section to debug the scroll pagination during runtime.</span></span>                                             |

| <span data-ttu-id="e3076-209">이벤트</span><span class="sxs-lookup"><span data-stu-id="e3076-209">Events</span></span>              | <span data-ttu-id="e3076-210">Description</span><span class="sxs-lookup"><span data-stu-id="e3076-210">Description</span></span>                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3076-211">클릭 시</span><span class="sxs-lookup"><span data-stu-id="e3076-211">On click</span></span>            | <span data-ttu-id="e3076-212">스크롤 배경 collider 또는 해당 대화형 콘텐츠로 인해 클릭이 수신 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-212">Triggered when the scroll background collider or any of its interactive content receives a click.</span></span>                             |
| <span data-ttu-id="e3076-213">터치 시작 시</span><span class="sxs-lookup"><span data-stu-id="e3076-213">On touch started</span></span>    | <span data-ttu-id="e3076-214">Scroll background collider 또는 해당 대화형 콘텐츠 중 하나라도 가까운 상호 작용 터치를 수신 하면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-214">Triggered when the scroll background collider or any of its interactive content receives a near interaction touch.</span></span>            |
| <span data-ttu-id="e3076-215">터치 종료 시</span><span class="sxs-lookup"><span data-stu-id="e3076-215">On touch ended</span></span>      | <span data-ttu-id="e3076-216">근접 한 상호 작용 포인터가 릴리스 임계값 평면과 교차할 때 활성 터치 조작이 종료 될 때 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-216">Triggered when an active touch interaction is terminated when the near interaction pointer crosses a release threshold plane.</span></span> |
| <span data-ttu-id="e3076-217">모멘텀 시작 됨</span><span class="sxs-lookup"><span data-stu-id="e3076-217">On momentum started</span></span> | <span data-ttu-id="e3076-218">스크롤 컨테이너가 상호 작용, 속도 감소 또는 페이지 매김을 통해 이동 하기 시작 하면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-218">Triggered when the scroll container starts moving by interaction, velocity falloff, or pagination.</span></span>                            |
| <span data-ttu-id="e3076-219">모멘텀 종료 됨</span><span class="sxs-lookup"><span data-stu-id="e3076-219">On momentum ended</span></span>   | <span data-ttu-id="e3076-220">스크롤 컨테이너에서 상호 작용, 속도 감소 또는 페이지 매김을 통해 이동을 중지할 때 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-220">Triggered when the scroll container stops moving by interaction, velocity falloff, or pagination.</span></span>                             |

## <a name="scrolling-example-scene"></a><span data-ttu-id="e3076-221">예제 장면 스크롤</span><span class="sxs-lookup"><span data-stu-id="e3076-221">Scrolling example scene</span></span>

<span data-ttu-id="e3076-222">**ScrollingObjectCollection** 예제 장면은 세 개의 스크롤 가능한 예제로 구성 되며 각각은 서로 다른 속도의 밝기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-222">**ScrollingObjectCollection.unity** example scene consists of 3 scrollable examples, each one with a different velocity falloff configuration.</span></span> <span data-ttu-id="e3076-223">예 장면에는 계층에서 기본적으로 사용 하지 않도록 설정 된 표면 배치 동작을 보여 주는 벽이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-223">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="e3076-224">예제 장면을 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` .</span><span class="sxs-lookup"><span data-stu-id="e3076-224">The example scene can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` folder.</span></span>

![스크롤 개체 컬렉션 예제 장면](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a><span data-ttu-id="e3076-226">스크롤 예 prefabs</span><span class="sxs-lookup"><span data-stu-id="e3076-226">Scrolling example prefabs</span></span>

<span data-ttu-id="e3076-227">편의상 두 개의 스크롤 개체 컬렉션 prefabs를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3076-227">For convenience, two scrolling object collection prefabs are available to use.</span></span> <span data-ttu-id="e3076-228">예제 prefabs는 폴더 아래에서 찾을 수 있습니다 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` .</span><span class="sxs-lookup"><span data-stu-id="e3076-228">The example prefabs can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` folder.</span></span>

![스크롤 개체 컬렉션 prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a><span data-ttu-id="e3076-230">참조</span><span class="sxs-lookup"><span data-stu-id="e3076-230">See also</span></span>

* [<span data-ttu-id="e3076-231">기본 클리핑</span><span class="sxs-lookup"><span data-stu-id="e3076-231">Clipping Primitive</span></span>](../rendering/clipping-primitive.md)
* [<span data-ttu-id="e3076-232">자재 인스턴스</span><span class="sxs-lookup"><span data-stu-id="e3076-232">Material Instance</span></span>](../rendering/material-instance.md)
* [<span data-ttu-id="e3076-233">표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="e3076-233">Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
* [<span data-ttu-id="e3076-234">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="e3076-234">Object collection</span></span>](object-collection.md)
