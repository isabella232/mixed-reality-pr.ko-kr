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
# <a name="bounds-control"></a><span data-ttu-id="9303b-104">범위 제어</span><span class="sxs-lookup"><span data-stu-id="9303b-104">Bounds control</span></span>

![범위 제어](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="9303b-106">*BoundsControl* 는 이전에 *BoundingBox* 에서 발견 된 조작 동작에 대 한 새 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="9303b-107">경계 제어를 사용 하면 여러 가지 기능을 향상 시키고 설치를 단순화 새 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="9303b-108">이 구성 요소는 더 이상 사용 되지 않는 경계 상자를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="9303b-109">이 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 스크립트는 혼합 현실에서 개체를 변환 하기 위한 기본 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="9303b-110">경계 컨트롤은 홀로그램 주위에 상자를 표시 하 여 상호 작용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="9303b-111">상자의 모퉁이 및 가장자리에 대 한 핸들은 개체의 크기 조정, 회전 또는 변환을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="9303b-112">또한 경계 컨트롤은 사용자 입력에 반응 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="9303b-113">예를 들어 HoloLens 2에서 경계 컨트롤은 손가락 근접에 응답 하 고 개체에서의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="9303b-114">모든 상호 작용 및 시각적 개체를 쉽게 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="9303b-115">장면 예</span><span class="sxs-lookup"><span data-stu-id="9303b-115">Example scene</span></span>

<span data-ttu-id="9303b-116">장면에서 범위 제어 구성의 예제를 찾을 수 있습니다 `BoundsControlExamples` .</span><span class="sxs-lookup"><span data-stu-id="9303b-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="9303b-117">Inspector 속성</span><span class="sxs-lookup"><span data-stu-id="9303b-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="9303b-118">대상 개체</span><span class="sxs-lookup"><span data-stu-id="9303b-118">Target object</span></span>

<span data-ttu-id="9303b-119">이 속성은 경계 컨트롤 조작을 통해 변환할 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="9303b-120">개체를 설정 하지 않으면 기본적으로 owner 개체가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="9303b-121">활성화 동작</span><span class="sxs-lookup"><span data-stu-id="9303b-121">Activation behavior</span></span>

<span data-ttu-id="9303b-122">범위 제어 인터페이스를 활성화 하는 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="9303b-123">*시작 시 활성화*: 장면을 시작한 후에 범위 컨트롤이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="9303b-124">*근접 별 활성화*: 트레일러 식이 개체에 가까이 있는 경우 경계 컨트롤이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="9303b-125">*포인터로 활성화*: 경계 컨트롤은 손 모양 포인터의 대상으로 지정 될 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="9303b-126">*근접 및 포인터를 기준으로 활성화*: 경계 컨트롤은 손 모양 포인터의 대상 이거나 개체에 근접 하는 경우 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="9303b-127">*수동으로 활성화*: 범위 컨트롤이 자동으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="9303b-128">BoundsControl 속성에 액세스 하 여 스크립트를 통해 수동으로 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="9303b-129">경계 재정의</span><span class="sxs-lookup"><span data-stu-id="9303b-129">Bounds override</span></span>

<span data-ttu-id="9303b-130">범위 계산을 위해 개체에서 상자 collider를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="9303b-131">상자 안쪽 여백</span><span class="sxs-lookup"><span data-stu-id="9303b-131">Box padding</span></span>

<span data-ttu-id="9303b-132">컨트롤의 범위를 계산 하는 데 사용 되는 collider 경계에 안쪽 여백을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="9303b-133">이렇게 하면 상호 작용 뿐만 아니라 시각적 개체에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="9303b-134">축 결합</span><span class="sxs-lookup"><span data-stu-id="9303b-134">Flatten axis</span></span>

<span data-ttu-id="9303b-135">컨트롤이 축 중 하나에서 평면화 되는지 여부를 나타내며 2 차원으로 만들고 해당 축을 따라 조작이 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="9303b-136">이 기능은 슬레이트와 같은 씬 개체에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="9303b-137">평면화 축이 *자동 평면화* 로 설정 된 경우 스크립트는 크기가 가장 작은 축을 평면화 축으로 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="9303b-138">다듬기</span><span class="sxs-lookup"><span data-stu-id="9303b-138">Smoothing</span></span>

<span data-ttu-id="9303b-139">다듬기 섹션에서는 컨트롤의 크기 조정 및 회전에 대 한 다듬기 동작을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="9303b-140">시각적 개체</span><span class="sxs-lookup"><span data-stu-id="9303b-140">Visuals</span></span>

<span data-ttu-id="9303b-141">해당 하는 시각적 개체 구성 중 하나를 수정 하 여 범위 컨트롤의 모양을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="9303b-142">시각적 구성은 연결 되거나 인라인 스크립트 가능한 개체 이며 [구성 개체 섹션](#configuration-objects)에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="9303b-143">구성 개체</span><span class="sxs-lookup"><span data-stu-id="9303b-143">Configuration Objects</span></span>

<span data-ttu-id="9303b-144">컨트롤은 스크립트 가능한 개체로 저장 되 고 다른 인스턴스 또는 prefabs 간에 공유 될 수 있는 구성 개체 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="9303b-145">구성은 개별 스크립트 가능한 자산 파일 또는 prefabs 내에서 스크립트 가능한 중첩 자산으로 공유 하 고 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="9303b-146">외부 또는 중첩 된 스크립트 가능한 자산에 연결 하지 않고도 인스턴스에서 직접 구성을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="9303b-147">범위 컨트롤 검사기는 속성 검사자에 메시지를 표시 하 여 구성이 현재 인스턴스의 일부로 공유 되는지 또는 인라인 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="9303b-148">또한 공유 인스턴스는 범위 컨트롤 속성 창 자체에서 직접 편집할 수 없지만, 연결 되는 자산은 공유 구성에 대 한 실수로 인 한 변경 사항을 방지 하기 위해 직접 수정한 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="9303b-149">현재 범위 제어는 다음 기능에 대 한 구성 개체 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="9303b-150">핸들</span><span class="sxs-lookup"><span data-stu-id="9303b-150">Handles</span></span>
  * [<span data-ttu-id="9303b-151">크기 조정 핸들</span><span class="sxs-lookup"><span data-stu-id="9303b-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="9303b-152">회전 핸들</span><span class="sxs-lookup"><span data-stu-id="9303b-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="9303b-153">변환 핸들</span><span class="sxs-lookup"><span data-stu-id="9303b-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="9303b-154">링크/와이어 프레임</span><span class="sxs-lookup"><span data-stu-id="9303b-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="9303b-155">상자 표시</span><span class="sxs-lookup"><span data-stu-id="9303b-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="9303b-156">근접 효과</span><span class="sxs-lookup"><span data-stu-id="9303b-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="9303b-157">Box 구성</span><span class="sxs-lookup"><span data-stu-id="9303b-157">Box configuration</span></span>

<span data-ttu-id="9303b-158">Box 구성은 collider size 및 box 안쪽 여백을 통해 정의 된 범위를 사용 하 여 실선 상자를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="9303b-159">다음 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-159">The following properties can be set up:</span></span>

* <span data-ttu-id="9303b-160">**Box 재질**: 상호 작용이 발생 하지 않을 때 렌더링 된 상자에 적용 되는 재질을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="9303b-161">이 자료가 설정 된 경우에만 상자가 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="9303b-162">**Box grabbed material**: near 또는 far 상호 작용을 통해 사용자가 컨트롤과 상호 작용 하는 경우의 상자 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="9303b-163">**축 표시 비율 평면화**: 축 중 하나가 [평면화](#flatten-axis)되 면 상자에 적용 되는 눈금이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="9303b-164">크기 조정 핸들 구성</span><span class="sxs-lookup"><span data-stu-id="9303b-164">Scale handles configuration</span></span>

<span data-ttu-id="9303b-165">이 속성 서랍을 사용 하면 범위 컨트롤의 크기 조정 핸들 동작 및 시각화를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="9303b-166">**핸들 재질**: 핸들에 적용 되는 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="9303b-167">Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="9303b-168">**핸들 prefab**: 크기 조정 핸들의 선택적 prefab입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="9303b-169">설정 되지 않은 경우 MRTK는 큐브를 기본값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="9303b-170">**핸들 크기**: 크기 조정 핸들의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="9303b-171">**Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="9303b-172">**조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="9303b-173">**핸들 무시 collider**: collider가 여기에 연결 된 경우 핸들은이 collider와 충돌을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="9303b-174">컨트롤이 평면화 될 때 핸들에 사용할 **슬레이트 prefab**: Prefab를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="9303b-175">**배율 핸들 표시**: 핸들의 표시 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="9303b-176">**크기 조정 동작**: 균일 또는 균일 하지 않은 배율로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="9303b-177">회전 핸들 구성</span><span class="sxs-lookup"><span data-stu-id="9303b-177">Rotation handles configuration</span></span>

<span data-ttu-id="9303b-178">이 구성은 회전 핸들 동작을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="9303b-179">**핸들 재질**: 핸들에 적용 되는 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="9303b-180">Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="9303b-181">**핸들 prefab**: 핸들의 선택적 prefab입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="9303b-182">설정 되지 않은 경우 MRTK에서 구를 기본값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="9303b-183">**핸들 크기**: 핸들의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="9303b-184">**Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="9303b-185">**조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="9303b-186">**핸들 무시 collider**: collider가 여기에 연결 된 경우 핸들은이 collider와 충돌을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="9303b-187">**Prefab collider type**: 만든 핸들과 함께 사용할 collider Type을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="9303b-188">**X에 대 한 핸들 표시**: x 축의 핸들 표시 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="9303b-189">**Y에 대 한 핸들 표시**: y 축에 대 한 핸들의 표시 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="9303b-190">**Z에 대 한 핸들 표시**: z 축의 핸들 표시 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="9303b-191">변환 핸들 구성</span><span class="sxs-lookup"><span data-stu-id="9303b-191">Translation handles configuration</span></span>

<span data-ttu-id="9303b-192">범위 제어에 대해 변환 핸들을 설정 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="9303b-193">변환 핸들은 기본적으로 비활성화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="9303b-194">**핸들 재질**: 핸들에 적용 되는 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="9303b-195">Grabbed 핸들에 적용 되는 **grabbed 재질**: 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="9303b-196">**핸들 prefab**: 핸들의 선택적 prefab입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="9303b-197">설정 되지 않은 경우 MRTK에서 구를 기본값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="9303b-198">**핸들 크기**: 핸들의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="9303b-199">**Collider 패딩**: 핸들 Collider에 추가할 패딩입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="9303b-200">**조작할 때 그리기**: 활성화 되 면 상호 작용 시작 지점에서 현재 손 모양 또는 포인터 위치로의 tether 그리기를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="9303b-201">**핸들은 충돌체 무시:** 충돌체가 여기에 연결되면 핸들은 이 충돌체와의 충돌을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="9303b-202">**프리팹 충돌체 형식 처리:** 생성된 핸들과 함께 사용할 충돌체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="9303b-203">**X에 대한 핸들 표시**: X축에 대한 핸들의 표시를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="9303b-204">**Y에 대한 핸들 표시: Y축** 핸들의 표시를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="9303b-205">**Z에 대한 핸들 표시: Z축에** 대한 핸들의 표시를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="9303b-206">링크 구성(와이어프레임)</span><span class="sxs-lookup"><span data-stu-id="9303b-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="9303b-207">링크 구성을 사용하면 경계 컨트롤의 와이어프레임 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="9303b-208">다음 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-208">The following properties can be configured:</span></span>

* <span data-ttu-id="9303b-209">**와이어프레임 재질:** 와이어프레임 메시에 적용되는 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="9303b-210">**와이어프레임 가장자리 반지름:** 와이어프레임의 두께입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="9303b-211">**Wireframe 셰이프:** 와이어프레임의 모양은 입방형 또는 원통형일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="9303b-212">**와이어프레임 표시: 와이어프레임의** 표시를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="9303b-213">근접 효과 구성</span><span class="sxs-lookup"><span data-stu-id="9303b-213">Proximity effect configuration</span></span>

<span data-ttu-id="9303b-214">손까지의 거리를 기준으로 애니메이션이 있는 핸들을 표시하고 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="9303b-215">2단계 크기 조정 애니메이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-215">It has two-step scaling animation.</span></span> <span data-ttu-id="9303b-216">기본값은 HoloLens 2 스타일 동작으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="9303b-217">**근접 효과 활성:** 근접 기반 핸들 활성화 사용</span><span class="sxs-lookup"><span data-stu-id="9303b-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="9303b-218">**개체 중간 근접:** 첫 번째 단계 크기 조정을 위한 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="9303b-219">**개체 근접:** 두 번째 단계 크기 조정을 위한 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="9303b-220">**원거리 크기 조정:** 손의 범위가 범위 컨트롤 상호 작용('중간 근접 처리'로 정의된 거리)을 벗어나는 경우 핸들 자산의 기본 소수점 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="9303b-221">기본적으로 핸들을 숨기려면 0을 사용합니다.)</span><span class="sxs-lookup"><span data-stu-id="9303b-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="9303b-222">**중간 규모:** 손을 경계 컨트롤 상호 작용 범위 내에 있는 경우 핸들 자산의 배율 값입니다(위의 '근접 핸들'에 의해 정의된 거리).</span><span class="sxs-lookup"><span data-stu-id="9303b-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="9303b-223">1을 사용하여 정상 크기 표시)</span><span class="sxs-lookup"><span data-stu-id="9303b-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="9303b-224">**닫기 배율:** 손의 잡기 상호 작용 범위 내에 있을 때 핸들 자산의 배율 값(위에서 '근접 핸들'로 정의된 거리)입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="9303b-225">1.x를 사용하여 더 큰 크기 표시)</span><span class="sxs-lookup"><span data-stu-id="9303b-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="9303b-226">**원거리 증가율:** 손의 크기가 중간에서 원거리로 이동하면 근접 크기 조정된 개체의 배율을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="9303b-227">**중간 증가율:** 손을 중간에서 가까운 근접으로 이동할 때 근접 크기 조정된 개체 배율을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="9303b-228">**증가율 닫기:** 손의 근접한 위치에서 개체 중심까지 이동할 때 근접 크기 조정된 개체 배율을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="9303b-229">제약 조건 시스템</span><span class="sxs-lookup"><span data-stu-id="9303b-229">Constraint System</span></span>

<span data-ttu-id="9303b-230">경계 컨트롤은 제약 [조건 관리자를](constraint-manager.md) 사용하여 경계 컨트롤 핸들을 사용하는 동안 변환, 회전 또는 크기 조정 동작을 제한하거나 수정할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="9303b-231">속성 검사자는 선택한 제약 조건 관리자를 스크롤하고 강조 표시하는 옵션을 사용하여 동일한 게임 개체에 연결된 사용 가능한 모든 제약 조건 관리자를 드롭다운에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="9303b-232">이벤트</span><span class="sxs-lookup"><span data-stu-id="9303b-232">Events</span></span>

<span data-ttu-id="9303b-233">범위 컨트롤은 다음 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-233">Bounds control provides the following events.</span></span> <span data-ttu-id="9303b-234">이 예제에서는 이러한 이벤트를 사용하여 오디오 피드백을 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="9303b-235">**회전 시작: 회전이** 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="9303b-236">**회전 중지: 회전이 중지될** 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="9303b-237">**Scale Started:** 크기 조정이 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="9303b-238">**크기 조정 중지:** 크기 조정이 중지되면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="9303b-239">**번역 시작됨:** 번역이 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="9303b-240">**중지된 번역: 번역이** 중지되면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="9303b-241">Elastics(실험적)</span><span class="sxs-lookup"><span data-stu-id="9303b-241">Elastics (Experimental)</span></span>

<span data-ttu-id="9303b-242">범위 컨트롤을 통해 개체를 조작할 때 탄력적 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="9303b-243">[탄력적 시스템은](../elastics/elastic-system.md) 여전히 실험적 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-243">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="9303b-244">탄력적 기능을 사용하려면 기존 Elastics Manager 구성 요소를 연결하거나 단추를 통해 새 Elastics Manager를 만들고 `Add Elastics Manager` 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="9303b-245">스타일 처리</span><span class="sxs-lookup"><span data-stu-id="9303b-245">Handle styles</span></span>

<span data-ttu-id="9303b-246">기본적으로 스크립트를 할당하면 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) HoloLens 1세대 스타일의 핸들이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="9303b-247">HoloLens 2 스타일 핸들을 사용하려면 적절한 핸들 프리팹 및 재질을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![경계 컨트롤 핸들 스타일 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="9303b-249">다음은 HoloLens 2 스타일 범위 컨트롤 핸들의 프리팹, 재질 및 크기 조정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="9303b-250">장면에서 이 예제를 찾을 수 `BoundsControlExamples` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="9303b-251">핸들(HoloLens 2 스타일에 대한 설정)</span><span class="sxs-lookup"><span data-stu-id="9303b-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="9303b-252">**핸들 재질:** BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="9303b-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="9303b-253">**핸들 잡기 재질:** BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="9303b-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="9303b-254">**배율 핸들 프리팹:** MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="9303b-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="9303b-255">**배율 핸들 슬레이트 프리팹:** MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="9303b-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="9303b-256">**배율 핸들 크기:** 0.016(1.6cm)</span><span class="sxs-lookup"><span data-stu-id="9303b-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="9303b-257">**배율 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)</span><span class="sxs-lookup"><span data-stu-id="9303b-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="9303b-258">**회전 핸들 프리팹:** MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="9303b-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="9303b-259">**회전 핸들 크기:** 0.016</span><span class="sxs-lookup"><span data-stu-id="9303b-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="9303b-260">**회전 핸들 Collider Padding:** 0.016(잡기 가능한 충돌체를 핸들 시각적 개체보다 약간 더 크게 만듭니다.)</span><span class="sxs-lookup"><span data-stu-id="9303b-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="9303b-261">개체 조작자를 통해 변환 변경</span><span class="sxs-lookup"><span data-stu-id="9303b-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="9303b-262">범위 컨트롤을 와 함께 사용하여 특정 유형의 조작을 허용할 수 [`ObjectManipulator.cs`](object-manipulator.md) 있습니다(예:</span><span class="sxs-lookup"><span data-stu-id="9303b-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="9303b-263">개체 이동) 핸들을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-263">moving the object) without using handles.</span></span> <span data-ttu-id="9303b-264">조작 처리기는 한 손 조작과 양손 상호 작용을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="9303b-265">[손 추적을](../input/hand-tracking.md) 사용하여 개체와 가까이에서 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="9303b-266">의 원거리 상호 작용을 사용하여 이동할 때 경계 컨트롤 가장자리가 동일한 방식으로 동작하도록 하려면 [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` 위의 스크린샷에 표시된 것처럼 조작 종료 시 조작 시작 시 에 대한 이벤트를 각각 에 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="9303b-267">Unity 검사기를 사용하여 경계 컨트롤을 추가하고 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="9303b-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="9303b-268">개체에 Box Collider 추가</span><span class="sxs-lookup"><span data-stu-id="9303b-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="9303b-269">`BoundsControl`개체에 스크립트 할당</span><span class="sxs-lookup"><span data-stu-id="9303b-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="9303b-270">'Activation' 메서드와 같은 옵션 구성(아래 [검사기 속성](#inspector-properties) 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="9303b-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="9303b-271">(선택 사항) HoloLens 2 스타일 경계 컨트롤에 대한 프리팹 및 재질 할당(아래 [스타일 처리](#handle-styles) 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="9303b-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="9303b-272">검사기에서 *대상 개체* 및 *경계 재정의* 필드를 사용하여 여러 자식 구성 요소가 있는 개체의 특정 개체 및 충돌체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![범위 제어](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="9303b-274">코드에서 경계 컨트롤을 추가하고 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="9303b-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="9303b-275">GameObject 큐브 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="9303b-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="9303b-276">`BoundsControl`AddComponent<>()를 사용하여 충돌체가 있는 개체에 스크립트 할당</span><span class="sxs-lookup"><span data-stu-id="9303b-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="9303b-277">컨트롤에서 직접 또는 스크립트 가능한 구성 중 하나를 통해 옵션을 구성합니다(아래 [검사기 속성](#inspector-properties) 및 [구성](#configuration-objects) 섹션 참조).</span><span class="sxs-lookup"><span data-stu-id="9303b-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="9303b-278">(선택 사항) HoloLens 2 스타일 경계 컨트롤에 대한 프리팹 및 재질을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="9303b-279">재질과 프리팹을 동적으로 로드해야 하므로 검사자를 통해 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="9303b-280">Unity의 'Resources' 폴더 또는 [Shader.Find를]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 사용하여 셰이더를 동적으로 로드하는 것은 런타임에 셰이더 순열이 누락될 수 있기 때문에 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="9303b-281">예제: MinMaxScaleConstraint를 사용하여 최소, 최대 범위 컨트롤 배율 설정</span><span class="sxs-lookup"><span data-stu-id="9303b-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="9303b-282">최소 및 최대 크기 조정을 설정하려면 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 컨트롤에 를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="9303b-283">경계 컨트롤이 제약 조건 관리자를 자동으로 연결하고 활성화하면 MinMaxScaleConstraint가 연결 및 구성되면 변환 변경 내용에 자동으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="9303b-284">MinMaxScaleConstraint를 사용하여 에 대한 최소 및 최대 배율도 설정할 수 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="9303b-285">예제: 게임 개체 주위에 경계 컨트롤 추가</span><span class="sxs-lookup"><span data-stu-id="9303b-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="9303b-286">개체 주위에 경계 컨트롤을 추가하려면 `BoundsControl` 구성 요소를 추가하기만 하면됩니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="9303b-287">경계 상자에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="9303b-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="9303b-288">[경계 상자를](bounding-box.md) 사용하는 기존 프리팹 및 인스턴스는 MRTK 도구 패키지의 일부인 [마이그레이션 창을](../tools/migration-window.md) 통해 새 경계 컨트롤로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="9303b-289">경계 상자의 개별 인스턴스를 업그레이드하기 위해 구성 요소의 속성 검사자 내에 마이그레이션 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9303b-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="9303b-290">참조</span><span class="sxs-lookup"><span data-stu-id="9303b-290">See also</span></span>

* [<span data-ttu-id="9303b-291">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="9303b-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="9303b-292">제약 조건 관리자</span><span class="sxs-lookup"><span data-stu-id="9303b-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="9303b-293">마이그레이션 기간</span><span class="sxs-lookup"><span data-stu-id="9303b-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="9303b-294">탄력적 시스템(실험적)</span><span class="sxs-lookup"><span data-stu-id="9303b-294">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
