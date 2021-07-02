---
title: 개체 조작자
description: MRTK에서 개체 조작자를 사용 하는 방법
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 개체 조작
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176650"
---
# <a name="object-manipulator"></a><span data-ttu-id="37ed5-104">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="37ed5-104">Object manipulator</span></span>

![개체 조작자](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="37ed5-106">*Objectmanipulator* 는 이전에 *ManipulationHandler* 에서 발견 된 조작 동작에 대 한 새 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="37ed5-107">개체 조작자를 사용 하면 다양 한 기능을 향상 시키고 단순화 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="37ed5-108">이 구성 요소는 조작 처리기의 대체 항목으로, 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="37ed5-109">*Objectmanipulator* 스크립트를 사용 하면 한 두 개의 손을 사용 하 여 개체를 이동 가능 하 고 확장 가능 하며 rotatable 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="37ed5-110">개체 조작자를 구성 하 여 개체가 다양 한 입력에 응답 하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="37ed5-111">스크립트는 HoloLens 2 부분 HoloLens HoloLens 2을 사용 하는 것과 같은 대부분의 상호 작용에서 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="37ed5-112">개체 조작자를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="37ed5-112">How to use the object manipulator</span></span>

<span data-ttu-id="37ed5-113">개체 조작자를 사용 하려면 먼저 `ObjectManipulator` GameObject에 스크립트 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="37ed5-114">Grabbable 범위와 일치 하는 개체에 collider도 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="37ed5-115">개체가 거의 유사 하 게 하는 손 모양 입력에 응답 하도록 하려면 `NearInteractionGrabbable` 스크립트도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="37ed5-116">Rigidbody 구성 요소를 개체에 추가 하 여 개체 조작자에 대해 물리학 동작을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="37ed5-117">이 구성 요소를 추가 하 여 사용 하도록 설정 된 물리학 동작은 [*물리학 및 충돌*](#physics-and-collisions)에서 더 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="37ed5-118">또한 조작 [제약 조건 구성 요소](constraint-manager.md#transform-constraints) 를 개체에 추가 하 여 조작을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="37ed5-119">이러한 구성 요소는 조작 작업을 수행 하 고 조작 동작을 변경 하는 특별 한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Unity 편집기에서 조작 처리기 사용](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="37ed5-121">Inspector 속성 및 필드</span><span class="sxs-lookup"><span data-stu-id="37ed5-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="37ed5-122">일반 속성</span><span class="sxs-lookup"><span data-stu-id="37ed5-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="37ed5-123">호스트 변환</span><span class="sxs-lookup"><span data-stu-id="37ed5-123">Host transform</span></span>

<span data-ttu-id="37ed5-124">조작할 개체 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="37ed5-125">구성 요소의 개체에 대 한 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="37ed5-126">조작 유형</span><span class="sxs-lookup"><span data-stu-id="37ed5-126">Manipulation type</span></span>

<span data-ttu-id="37ed5-127">하나 또는 두 개의 손을 사용 하 여 개체를 조작할 수 있는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="37ed5-128">이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="37ed5-129">*단방향*: 선택 하는 경우 하나의 전달 조작이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="37ed5-130">*두 번*: 선택 하는 경우 두 개의 전달 조작이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="37ed5-131">먼 조작을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-131">Allow far manipulation</span></span>

<span data-ttu-id="37ed5-132">포인터와의 먼 상호 작용을 사용 하 여 조작을 수행할 수 있는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="37ed5-133">단일 전달 조작 속성</span><span class="sxs-lookup"><span data-stu-id="37ed5-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="37ed5-134">가까운 쪽 회전 모드</span><span class="sxs-lookup"><span data-stu-id="37ed5-134">One hand rotation mode near</span></span>

<span data-ttu-id="37ed5-135">개체가 가까이 grabbed 때 동작 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="37ed5-136">이러한 옵션은 트레일러 식에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="37ed5-137">*개체 중심 회전*: 개체는 손 모양에 대 한 회전을 사용 하 여 회전 하지만 개체 중심점은 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="37ed5-138">개체는 회전할 때 보다 작게 표시 되지만 손 개체와 개체 간에 연결이 끊어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="37ed5-139">먼 상호 작용에 더 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-139">More useful for far interaction.</span></span>
- <span data-ttu-id="37ed5-140">*지점에 대 한 회전*: 엄지 단추와 인덱스 손가락 사이의 잡기 지점에 대 한 손 모양으로 개체를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="37ed5-141">개체를 직접 보유 하 고 있는 것 처럼 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="37ed5-142">한 손으로 회전 모드 멀리</span><span class="sxs-lookup"><span data-stu-id="37ed5-142">One hand rotation mode far</span></span>

<span data-ttu-id="37ed5-143">개체를 grabbed 때 개체의 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="37ed5-144">이러한 옵션은 트레일러 식에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="37ed5-145">*개체 중심 회전*: 손 모양에 대 한 회전을 사용 하 여 개체를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="37ed5-146">개체가 회전할 때 개체 센터가 이동 하지 않고 거리를 검사 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="37ed5-147">*지점* 회전: 손 모양 회전을 사용 하 여 개체를 회전 하지만 포인터 광선 적중 지점에 대해 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="37ed5-148">검사에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="37ed5-149">두 개의 전달 조작 속성</span><span class="sxs-lookup"><span data-stu-id="37ed5-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="37ed5-150">두 개의 전달 조작 형식</span><span class="sxs-lookup"><span data-stu-id="37ed5-150">Two handed manipulation type</span></span>

<span data-ttu-id="37ed5-151">두 손을 조작 하 여 개체를 변환할 수 있는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="37ed5-152">이 속성은 플래그 이기 때문에 원하는 수의 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="37ed5-153">*이동*: 선택 하면 이동이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="37ed5-154">*크기 조정*: 선택 하는 경우에는 크기 조정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="37ed5-155">*회전*: 선택한 경우 회전이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-155">*Rotate*: Rotation is allowed if selected.</span></span>

![조작 처리기](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="37ed5-157">제약 조건</span><span class="sxs-lookup"><span data-stu-id="37ed5-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="37ed5-158">제약 조건 사용</span><span class="sxs-lookup"><span data-stu-id="37ed5-158">Enable constraints</span></span>

<span data-ttu-id="37ed5-159">이 설정은 연결 된 [제약 조건 관리자](constraint-manager.md)를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="37ed5-160">변환 변경 내용은 선택한 [제약 조건 관리자](constraint-manager.md)에 등록 된 제약 조건에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="37ed5-161">제약 조건 관리자</span><span class="sxs-lookup"><span data-stu-id="37ed5-161">Constraint manager</span></span>

<span data-ttu-id="37ed5-162">드롭다운에서 연결 된 [제약 조건 관리자](constraint-manager.md)를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="37ed5-163">개체 조작자는 항상 [제약 조건 관리자](constraint-manager.md) 가 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="37ed5-164">동일한 유형의 여러 구성 요소가 unity의 동일한 이름에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="37ed5-165">동일한 개체에서 여러 제약 조건 관리자를 쉽게 구분할 수 있도록 사용 가능한 옵션은 선택한 제약 조건 관리자 (수동 또는 자동 제약 조건 선택)의 구성에 대 한 힌트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="37ed5-166">구성 요소로 이동</span><span class="sxs-lookup"><span data-stu-id="37ed5-166">Go to component</span></span>

<span data-ttu-id="37ed5-167">제약 조건 관리자 선택 항목에는 *구성 요소* 단추와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="37ed5-168">이 단추를 클릭 하면 검사기가 선택 된 구성 요소로 스크롤되며 구성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="37ed5-169">Physics</span><span class="sxs-lookup"><span data-stu-id="37ed5-169">Physics</span></span>

<span data-ttu-id="37ed5-170">이 섹션의 설정 개체에 RigidBody 구성 요소가 있는 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="37ed5-171">릴리스 동작</span><span class="sxs-lookup"><span data-stu-id="37ed5-171">Release behavior</span></span>

<span data-ttu-id="37ed5-172">조작 된 개체가 릴리스할 때 유지 해야 하는 물리적 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="37ed5-173">이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="37ed5-174">*속도 유지*: 개체가 해제 되 면이 옵션을 선택 하면 선형 속도를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="37ed5-175">*Angular 속도 유지*: 개체가 해제 되 면이 옵션을 선택 하면 각도의 속도를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="37ed5-176">거의 조작 하기 위해 강제 사용</span><span class="sxs-lookup"><span data-stu-id="37ed5-176">Use forces for near manipulation</span></span>

<span data-ttu-id="37ed5-177">거의 조작을 수행할 때 물리 힘이 개체를 이동 하는 데 사용 되는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="37ed5-178">이를 *false* 로 설정 하면 개체가 사용자에 게 직접 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="37ed5-179">이를 true로 설정 하면 개체의 질량 및 관성이 *적용* 되지만 개체가 스프링을 통해 연결 된 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="37ed5-180">기본값은 *false* 입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="37ed5-181">다듬기</span><span class="sxs-lookup"><span data-stu-id="37ed5-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="37ed5-182">지금까지 다듬기</span><span class="sxs-lookup"><span data-stu-id="37ed5-182">Smoothing far</span></span>

<span data-ttu-id="37ed5-183">먼 상호 작용에 대해 프레임 수준 독립적인 다듬기가 사용 되는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="37ed5-184">지금까지 다듬기는 기본적으로 사용 하도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="37ed5-185">가까이 다듬기</span><span class="sxs-lookup"><span data-stu-id="37ed5-185">Smoothing near</span></span>

<span data-ttu-id="37ed5-186">거의 상호 작용에 대해 프레임 수준 독립적인 다듬기가 사용 되는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="37ed5-187">가까운 다듬기는이 효과가 ' 연결 끊김 ' 상태로 인식 될 수 있으므로 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="37ed5-188">활성 다듬기</span><span class="sxs-lookup"><span data-stu-id="37ed5-188">Smoothing active</span></span>

<span data-ttu-id="37ed5-189">더 이상 사용 되지 않으며 이후 버전에서 제거 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="37ed5-190">응용 프로그램은 SmoothingFar, SmoothingNear 또는 둘의 조합을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="37ed5-191">Lerp 시간 이동</span><span class="sxs-lookup"><span data-stu-id="37ed5-191">Move lerp time</span></span>

<span data-ttu-id="37ed5-192">이동에 적용할 다듬기의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="37ed5-193">0의 다듬기는 다듬기를 의미 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="37ed5-194">최 댓 값은 값이 변경 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="37ed5-195">회전 lerp 시간</span><span class="sxs-lookup"><span data-stu-id="37ed5-195">Rotate lerp time</span></span>

<span data-ttu-id="37ed5-196">회전에 적용할 다듬기의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="37ed5-197">0의 다듬기는 다듬기를 의미 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="37ed5-198">최 댓 값은 값이 변경 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="37ed5-199">Lerp 시간 크기 조정</span><span class="sxs-lookup"><span data-stu-id="37ed5-199">Scale lerp time</span></span>

<span data-ttu-id="37ed5-200">눈금에 적용할 다듬기의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="37ed5-201">0의 다듬기란 다듬기 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="37ed5-202">최대값은 값이 변경되지 않는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="37ed5-203">조작 이벤트</span><span class="sxs-lookup"><span data-stu-id="37ed5-203">Manipulation events</span></span>

<span data-ttu-id="37ed5-204">조작 처리기는 다음 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="37ed5-205">*OnManipulationStarted:* 조작이 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="37ed5-206">*OnManipulationEnded:* 조작이 종료될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="37ed5-207">*OnHoverStarted:* 손/컨트롤러가 조작 가능한 마우스를 근거리 또는 멀리 가리키면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="37ed5-208">*OnHoverEnded:* 손/컨트롤러가 조작 가능한 가리키기를 거의 또는 멀리 가리키면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="37ed5-209">조작에 대한 이벤트 발생 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="37ed5-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="37ed5-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="37ed5-211">조작이 없으면 다음 화재 순서를 가진 가리키기 이벤트가 계속 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="37ed5-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="37ed5-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="37ed5-213">물리학 및 충돌</span><span class="sxs-lookup"><span data-stu-id="37ed5-213">Physics and collisions</span></span>

<span data-ttu-id="37ed5-214">물리학 동작은 개체 조작자로 동일한 개체에 고정된 구성 요소를 추가하여 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="37ed5-215">이렇게 하면 위의 [릴리스 동작을](#release-behavior) 구성할 수 있게 될 뿐만 아니라 충돌도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="37ed5-216">고정된 구성 요소가 없으면 조작 중에 충돌이 제대로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="37ed5-217">조작된 개체와 정적 충돌체 간의 충돌(예: 충돌체는 있지만 고정된 충돌체가 없는 개체)은 작동하지 않으며 조작된 개체는 영향을 받지 않는 정적 충돌체를 통해 직접 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="37ed5-218">조작된 개체와 고정된 개체 간의 충돌(즉,</span><span class="sxs-lookup"><span data-stu-id="37ed5-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="37ed5-219">충돌체와 고정된 표시가 둘 다 있는 개체)는 엄밀히 충돌 응답을 발생하지만 응답은 점프하고 자연스럽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="37ed5-220">조작된 개체에 대한 충돌 응답도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="37ed5-221">고정된 표시가 추가되면 충돌이 올바르게 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="37ed5-222">고정된 버디가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="37ed5-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="37ed5-223">고정된 버디를 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="37ed5-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="37ed5-224">Elastics(실험적)</span><span class="sxs-lookup"><span data-stu-id="37ed5-224">Elastics (Experimental)</span></span>

<span data-ttu-id="37ed5-225">개체 조작자를 통해 개체를 조작할 때 탄력적 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="37ed5-226">[탄력적 시스템은](../experimental/elastic-system.md) 여전히 실험적 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="37ed5-227">탄력적 기능을 사용하려면 기존 Elastics Manager 구성 요소를 연결하거나 단추를 통해 새 Elastics Manager를 만들고 `Add Elastics Manager` 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37ed5-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="37ed5-228">참조</span><span class="sxs-lookup"><span data-stu-id="37ed5-228">See also</span></span>

- [<span data-ttu-id="37ed5-229">경계 컨트롤</span><span class="sxs-lookup"><span data-stu-id="37ed5-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="37ed5-230">제약 조건 관리자</span><span class="sxs-lookup"><span data-stu-id="37ed5-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="37ed5-231">마이그레이션 기간</span><span class="sxs-lookup"><span data-stu-id="37ed5-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="37ed5-232">탄력적 시스템(실험적)</span><span class="sxs-lookup"><span data-stu-id="37ed5-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
