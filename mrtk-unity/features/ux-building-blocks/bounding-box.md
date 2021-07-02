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
# <a name="bounding-box"></a><span data-ttu-id="6951f-104">경계 상자</span><span class="sxs-lookup"><span data-stu-id="6951f-104">Bounding box</span></span>

![경계 상자](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="6951f-106">경계 상자는 더 이상 사용되지 않으며 후속 경계 컨트롤 로 [대체됩니다.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="6951f-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="6951f-107">[마이그레이션 옵션 중 하나를](#migrating-to-bounds-control) 사용하여 기존 게임 개체를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="6951f-108">[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)스크립트는 혼합 현실에서 개체를 변환하기 위한 기본 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="6951f-109">경계 상자는 상호 작용할 수 있음을 나타내기 위해 홀로그램 주위에 큐브를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="6951f-110">큐브의 모퉁이와 가장자리에 있는 핸들을 사용하면 개체의 크기를 조정하거나 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="6951f-111">경계 상자는 사용자 입력에도 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="6951f-112">예를 들어 HoloLens 2 경계 상자는 손가락 근접에 응답하여 개체와의 거리를 인식하는 데 도움이 되는 시각적 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="6951f-113">모든 상호 작용 및 시각적 개체를 쉽게 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="6951f-114">자세한 내용은 Windows 개발자 센터 [경계 상자 및 앱 표시줄을](/windows/mixed-reality/app-bar-and-bounding-box) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6951f-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="6951f-115">예제 장면</span><span class="sxs-lookup"><span data-stu-id="6951f-115">Example scene</span></span>

<span data-ttu-id="6951f-116">장면에서 경계 상자 구성의 예를 찾을 수 `BoundingBoxExamples` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="6951f-117">Unity 검사기를 사용하여 경계 상자를 추가하고 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="6951f-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="6951f-118">개체에 Box Collider 추가</span><span class="sxs-lookup"><span data-stu-id="6951f-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="6951f-119">`BoundingBox`개체에 스크립트 할당</span><span class="sxs-lookup"><span data-stu-id="6951f-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="6951f-120">'Activation' 메서드와 같은 옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="6951f-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="6951f-121">(선택 사항) HoloLens 2 스타일 경계 상자에 대한 프리팹 및 재질 할당(아래 [스타일 처리](#handle-styles) 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="6951f-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="6951f-122">검사기에서 *대상 개체* 및 *경계 재정의* 필드를 사용하여 여러 자식 구성 요소가 있는 개체의 특정 개체 및 충돌체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![경계 상자 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="6951f-124">코드에서 경계 상자를 추가하고 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="6951f-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="6951f-125">GameObject 큐브 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="6951f-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="6951f-126">`BoundingBox`AddComponent<>()를 사용하여 충돌체가 있는 개체에 스크립트 할당</span><span class="sxs-lookup"><span data-stu-id="6951f-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="6951f-127">옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="6951f-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="6951f-128">(선택 사항) HoloLens 2 스타일 경계 상자에 대한 프리팹 및 재질을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="6951f-129">재질과 프리팹을 동적으로 로드해야 하므로 검사자를 통해 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="6951f-130">Unity의 'Resources' 폴더 또는 [Shader.Find를]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 사용하여 셰이더를 동적으로 로드하는 것은 런타임에 셰이더 순열이 누락될 수 있기 때문에 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="6951f-131">예제: MinMaxScaleConstraint를 사용하여 최소, 최대 경계 상자 배율 설정</span><span class="sxs-lookup"><span data-stu-id="6951f-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="6951f-132">최소 및 최대 크기 조정을 설정하려면 를 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="6951f-133">MinMaxScaleConstraint를 사용하여 에 대한 최소 및 최대 배율도 설정할 수 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="6951f-134">예제: 게임 개체 주위에 경계 상자 추가</span><span class="sxs-lookup"><span data-stu-id="6951f-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="6951f-135">개체 주위에 경계 상자를 추가하려면 구성 `BoundingBox` 요소를 추가하기만 하면됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="6951f-136">검사기 속성</span><span class="sxs-lookup"><span data-stu-id="6951f-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="6951f-137">대상 개체</span><span class="sxs-lookup"><span data-stu-id="6951f-137">Target object</span></span>

<span data-ttu-id="6951f-138">이 속성은 경계 상자 조작에 의해 변환될 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="6951f-139">개체가 설정되지 않은 경우 경계 상자는 기본적으로 소유자 개체로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="6951f-140">범위 재정의</span><span class="sxs-lookup"><span data-stu-id="6951f-140">Bounds override</span></span>

<span data-ttu-id="6951f-141">경계 계산을 위해 개체에서 상자 충돌체를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="6951f-142">활성화 동작</span><span class="sxs-lookup"><span data-stu-id="6951f-142">Activation behavior</span></span>

<span data-ttu-id="6951f-143">경계 상자 인터페이스를 활성화하는 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="6951f-144">*시작 시 활성화:* 장면이 시작되면 경계 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="6951f-145">*근접성으로 활성화:* 개체에 가까운 절전형 손의 경계 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="6951f-146">*포인터로 활성화:* 손 광선 포인터의 대상이 될 때 경계 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="6951f-147">*수동으로 활성화:* 경계 상자가 자동으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="6951f-148">boundingBox.Active 속성에 액세스하여 스크립트를 통해 수동으로 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="6951f-149">최소 크기 조정</span><span class="sxs-lookup"><span data-stu-id="6951f-149">Scale minimum</span></span>

<span data-ttu-id="6951f-150">허용되는 최소 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-150">The minimum allowed scale.</span></span> <span data-ttu-id="6951f-151">이 속성은 더 이상 사용되지 않으며 스크립트를 추가하는 것이 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="6951f-152">이 스크립트를 추가하면 경계 상자 대신 최소 크기 조정이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="6951f-153">최대 크기 조정</span><span class="sxs-lookup"><span data-stu-id="6951f-153">Scale maximum</span></span>

<span data-ttu-id="6951f-154">허용되는 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-154">The maximum allowed scale.</span></span> <span data-ttu-id="6951f-155">이 속성은 더 이상 사용되지 않으며 스크립트를 추가하는 것이 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="6951f-156">이 스크립트를 추가하면 경계 상자 대신 최대 크기 조정이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="6951f-157">상자 표시</span><span class="sxs-lookup"><span data-stu-id="6951f-157">Box display</span></span>

<span data-ttu-id="6951f-158">다양한 경계 상자 시각화 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="6951f-159">축 평면화가 *자동 평면화로* 설정된 경우 스크립트는 가장 작은 범위로 축을 따라 조작을 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="6951f-160">이로 인해 일반적으로 씬 개체에 사용되는 2D 경계 상자가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="6951f-161">핸들</span><span class="sxs-lookup"><span data-stu-id="6951f-161">Handles</span></span>

<span data-ttu-id="6951f-162">재질과 프리팹을 할당하여 핸들 스타일을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="6951f-163">할당된 핸들이 없으면 기본 스타일로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="6951f-164">이벤트</span><span class="sxs-lookup"><span data-stu-id="6951f-164">Events</span></span>

<span data-ttu-id="6951f-165">경계 상자는 다음과 같은 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-165">Bounding box provides the following events.</span></span> <span data-ttu-id="6951f-166">이 예제에서는 이러한 이벤트를 사용하여 오디오 피드백을 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="6951f-167">**회전 시작: 회전이** 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="6951f-168">**회전 종료:** 회전이 끝날 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="6951f-169">**Scale Started:** 크기 조정이 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="6951f-170">**확장 종료:** 크기 조정이 종료되면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="6951f-171">스타일 처리</span><span class="sxs-lookup"><span data-stu-id="6951f-171">Handle styles</span></span>

<span data-ttu-id="6951f-172">기본적으로 스크립트를 할당하면 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) HoloLens 1세대 스타일의 핸들이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="6951f-173">HoloLens 2 스타일 핸들을 사용하려면 적절한 핸들 프리팹 및 재질을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![경계 상자 핸들 스타일](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="6951f-175">다음은 HoloLens 2 스타일 경계 상자 핸들의 프리팹, 재질 및 크기 조정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="6951f-176">장면에서 이 예제를 찾을 수 `BoundingBoxExamples` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="6951f-177">핸들(HoloLens 2 스타일에 대한 설정)</span><span class="sxs-lookup"><span data-stu-id="6951f-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="6951f-178">**핸들 재질:** BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="6951f-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="6951f-179">**핸들 잡기 재질:** BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="6951f-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="6951f-180">**배율 핸들 프리팹:** MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="6951f-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="6951f-181">**배율 핸들 슬레이트 프리팹:** MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="6951f-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="6951f-182">**배율 핸들 크기:** 0.016(1.6cm)</span><span class="sxs-lookup"><span data-stu-id="6951f-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="6951f-183">**배율 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)</span><span class="sxs-lookup"><span data-stu-id="6951f-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="6951f-184">**회전 핸들 프리팹:** MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="6951f-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="6951f-185">**회전 핸들 크기:** 0.016</span><span class="sxs-lookup"><span data-stu-id="6951f-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="6951f-186">**회전 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)</span><span class="sxs-lookup"><span data-stu-id="6951f-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="6951f-187">근접성(HoloLens 2 스타일 설정)</span><span class="sxs-lookup"><span data-stu-id="6951f-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="6951f-188">손까지의 거리를 기준으로 애니메이션이 있는 핸들을 표시하고 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="6951f-189">2단계 크기 조정 애니메이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="6951f-190">**근접 효과 활성:** 근접 기반 핸들 활성화 사용</span><span class="sxs-lookup"><span data-stu-id="6951f-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="6951f-191">**중간 근접 처리:** 첫 번째 단계 크기 조정을 위한 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="6951f-192">**근접 핸들:** 두 번째 단계 크기 조정을 위한 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="6951f-193">**원거리 크기** 조정: 손의 경계 상자 상호 작용 범위(위에서 '중간 근접 처리'로 정의된 거리)를 벗어나는 경우 핸들 자산의 기본 크기 조정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="6951f-194">기본적으로 핸들을 숨기려면 0을 사용합니다.)</span><span class="sxs-lookup"><span data-stu-id="6951f-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="6951f-195">**중간 규모:** 손의 경계 상자 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값입니다(위의 '근접 핸들'로 정의된 거리).</span><span class="sxs-lookup"><span data-stu-id="6951f-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="6951f-196">1을 사용하여 정상 크기 표시)</span><span class="sxs-lookup"><span data-stu-id="6951f-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="6951f-197">**닫기 배율:** 손의 잡기 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값(위에서 '근접 핸들'로 정의된 거리)입니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="6951f-198">1.x를 사용하여 더 큰 크기 표시)</span><span class="sxs-lookup"><span data-stu-id="6951f-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="6951f-199">조작 처리기를 통해 개체를 이동 가능하게 만들기</span><span class="sxs-lookup"><span data-stu-id="6951f-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="6951f-200">경계 상자를 와 결합하여 [`ManipulationHandler.cs`](manipulation-handler.md) 원거리 상호 작용을 사용하여 개체를 이동 가능하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="6951f-201">조작 처리기는 한 손 조작과 양손 상호 작용을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="6951f-202">[손 추적을](../input/hand-tracking.md) 사용하여 개체와 가까이에서 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="6951f-203">의 원거리 상호 작용을 사용하여 이동할 때 경계 상자 가장자리가 동일한 방식으로 [`ManipulationHandler`](manipulation-handler.md) 작동하려면 위의   /  스크린샷에 표시된 것처럼 *조작이 종료될* 때 조작이 시작되었을 때 에 대한 이벤트를 각각 에 연결하는 것이 `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="6951f-204">경계 컨트롤로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="6951f-204">Migrating to bounds control</span></span>

<span data-ttu-id="6951f-205">[경계 상자를](bounding-box.md) 사용하는 기존 프리팹 및 인스턴스는 MRTK 도구 패키지의 일부인 [마이그레이션 창을](../tools/migration-window.md) 통해 새 경계 컨트롤로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="6951f-206">경계 상자의 개별 인스턴스를 업그레이드하기 위해 구성 요소의 속성 검사자 내에 마이그레이션 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6951f-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
