---
title: 제약 조건 관리자
description: MRTK의 제약 조건 관리자 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177551"
---
# <a name="constraint-manager"></a><span data-ttu-id="9af00-104">제약 조건 관리자</span><span class="sxs-lookup"><span data-stu-id="9af00-104">Constraint manager</span></span>

<span data-ttu-id="9af00-105">제약 조건 관리자를 사용 하면 제약 조건 구성 요소 집합을 변환에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="9af00-106">게임 개체에 연결 된 형식의 구성 요소를 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="9af00-107">기본적으로 제약 조건 관리자는 게임 개체에 연결 된 모든 [제약 조건 구성 요소](#transform-constraints) 를 자동으로 수집 하 여 처리 된 변환에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="9af00-108">그러나 사용자는 적용 된 제약 조건 목록을 수동으로 구성 하 고 연결 된 제약 조건의 하위 집합만 적용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="9af00-109">현재 다음 MRTK UX 요소는 제약 조건 관리자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="9af00-110">범위 제어</span><span class="sxs-lookup"><span data-stu-id="9af00-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="9af00-111">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="9af00-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="9af00-112">Inspector 속성 및 필드</span><span class="sxs-lookup"><span data-stu-id="9af00-112">Inspector properties and fields</span></span>

<span data-ttu-id="9af00-113">제약 조건 관리자는 다음과 같은 두 가지 모드로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="9af00-114">자동 제약 조건 선택</span><span class="sxs-lookup"><span data-stu-id="9af00-114">Auto constraint selection</span></span>
- <span data-ttu-id="9af00-115">수동 제약 조건 선택</span><span class="sxs-lookup"><span data-stu-id="9af00-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="9af00-116">자동 제약 조건 선택</span><span class="sxs-lookup"><span data-stu-id="9af00-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="9af00-117">제약 조건 관리자의 기본 모드, 자동 제약 조건 선택은 연결 된 모든 제약 조건 구성 요소와 [단추 이동](#go-to-component) 및 [제약 조건 추가 단추](#add-constraint-to-game-object)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="9af00-118">게임 개체에 제약 조건 추가</span><span class="sxs-lookup"><span data-stu-id="9af00-118">Add constraint to game object</span></span>

<span data-ttu-id="9af00-119">이 단추를 사용 하면 제약 조건 관리자 검사기에서 직접 제약 조건 구성 요소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="9af00-120">프로젝트의 모든 제약 조건 형식은 여기에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="9af00-121">자세한 정보는 [transform 제약 조건](#transform-constraints) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9af00-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="9af00-122">구성 요소로 이동</span><span class="sxs-lookup"><span data-stu-id="9af00-122">Go to component</span></span>

<span data-ttu-id="9af00-123">개체에 있는 모든 제약 조건은 여기에 나열 커밋되지 *구성 요소 단추로 이동* 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="9af00-124">이 단추를 클릭 하면 검사기가 선택 된 제약 조건 구성 요소로 스크롤되며 구성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="9af00-125">수동 제약 조건 선택</span><span class="sxs-lookup"><span data-stu-id="9af00-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="9af00-126">제약 조건 관리자가 수동 모드로 설정 된 경우 제약 조건 목록에 연결 된 제약 조건만 처리 되어 변환에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="9af00-127">표시 된 목록에는 사용자가 선택한 제약 조건 뿐만 아니라 항목 [을](#go-to-component) 제거 하거나 추가 하는 단추 또는 옵션으로 이동 하는 것만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="9af00-128">수동 모드를 처음 사용 하는 경우 제약 조건 관리자는 사용 가능한 모든 구성 요소를 연결 된 제약 조건 구성 요소를 선택 하기 위한 시작 점으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="9af00-129">항목 제거</span><span class="sxs-lookup"><span data-stu-id="9af00-129">Remove entry</span></span>

<span data-ttu-id="9af00-130">이렇게 하면 수동으로 선택한 목록에서 항목이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="9af00-131">이 옵션은 game 개체에서 제약 조건 구성 요소를 제거 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="9af00-132">제약 조건 구성 요소는이 구성 요소를 참조 하는 다른 구성 요소를 실수로 손상 시 키 지 않도록 항상 수동으로 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="9af00-133">항목 추가</span><span class="sxs-lookup"><span data-stu-id="9af00-133">Add entry</span></span>

<span data-ttu-id="9af00-134">항목 추가를 사용 하면 아직 수동 목록에 없는 사용 가능한 모든 제약 조건 구성 요소가 표시 되는 드롭다운이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="9af00-135">항목을 클릭 하면 해당 구성 요소가 수동 제약 조건 선택 항목에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="9af00-136">새 제약 조건 추가</span><span class="sxs-lookup"><span data-stu-id="9af00-136">Add new constraint</span></span>

<span data-ttu-id="9af00-137">이 옵션을 선택 하면 선택한 형식의 구성 요소가 game 개체에 추가 되 고 새로 만든 제약 조건 구성 요소가 수동 제약 조건 목록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="9af00-138">변환 제약 조건</span><span class="sxs-lookup"><span data-stu-id="9af00-138">Transform constraints</span></span>

<span data-ttu-id="9af00-139">제약 조건을 사용 하 여 특정 방식으로 조작을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="9af00-140">예를 들어 일부 응용 프로그램에는 회전이 필요할 수 있지만 개체는 수직으로도 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="9af00-141">이 경우를 `RotationAxisConstraint` 개체에 추가 하 고 y 축 회전으로 회전을 제한 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="9af00-142">MRTK는 아래에 설명 된 다양 한 제약 조건을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="9af00-143">또한 새 제약 조건을 정의 하 고이를 사용 하 여 일부 응용 프로그램에 필요할 수 있는 고유한 조작 동작을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="9af00-144">이렇게 하려면에서 상속 하는 스크립트를 만들고 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) abstract `ConstraintType` 속성과 추상 메서드를 구현 `ApplyConstraint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="9af00-145">개체에 새 제약 조건을 추가할 때 정의 된 방식으로 조작을 제한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="9af00-146">또한이 새 제약 조건은 수동 모드의 제약 조건 관리자 [자동 선택](#auto-constraint-selection) 또는 [항목 추가](#add-entry) 드롭다운에서 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="9af00-147">MRTK에서 제공 하는 모든 제약 조건은 다음 속성을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="9af00-148">손으로 형식</span><span class="sxs-lookup"><span data-stu-id="9af00-148">Hand Type</span></span>

<span data-ttu-id="9af00-149">단방향, 두 가지 또는 두 종류의 조작에 제약 조건이 사용 되는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="9af00-150">이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="9af00-151">*단방향*: 제약 조건은 하나의 전달 조작 중에 사용 됩니다 (선택 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="9af00-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="9af00-152">두 *개의 왼손*: 제약 조건이 선택 되어 있는 경우 두 개의 전달 조작이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="9af00-153">근접 유형</span><span class="sxs-lookup"><span data-stu-id="9af00-153">Proximity Type</span></span>

<span data-ttu-id="9af00-154">제약 조건이 거의 모든 종류의 조작에 사용 되는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="9af00-155">이 속성은 플래그 이므로 두 옵션을 모두 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="9af00-156">*Near*: 선택 하는 경우 거의 조작 하는 동안 제약 조건이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="9af00-157">*Far*: 선택한 경우 제약 조건이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="9af00-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="9af00-159">이 제약 조건이 개체에 연결 되 면 개체가 항상 사용자를 대상으로 하는 회전이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="9af00-160">이는 슬레이트 또는 패널에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-160">This is useful for slates or panels.</span></span> <span data-ttu-id="9af00-161">의 속성은 다음과 같습니다 `FaceUserConstraint` .</span><span class="sxs-lookup"><span data-stu-id="9af00-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="9af00-162">얼굴 떨어져</span><span class="sxs-lookup"><span data-stu-id="9af00-162">Face away</span></span>

<span data-ttu-id="9af00-163">True 이면 개체가 사용자의 얼굴을 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="9af00-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="9af00-165">이 제약 조건은 조작 된 개체와 조작 시작 시 다른 개체 변환 간의 거리를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="9af00-166">이는 조작 된 개체에서 head 변환 까지의 거리를 수정 하는 것과 같은 동작에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="9af00-167">의 속성은 다음과 같습니다 `FixedDistanceConstraint` .</span><span class="sxs-lookup"><span data-stu-id="9af00-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="9af00-168">제약 조건 변환</span><span class="sxs-lookup"><span data-stu-id="9af00-168">Constraint transform</span></span>

<span data-ttu-id="9af00-169">조작 된 개체의 거리가 고정 되는 다른 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="9af00-170">카메라 변환이 기본값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="9af00-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="9af00-172">이 제약 조건은 조작 중인 사용자와 조작 된 개체 간의 상대적 회전을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="9af00-173">이 기능은 조작 된 개체가 조작을 시작할 때와 동일한 얼굴을 항상 사용자에 게 표시 하는 것을 슬레이트 하거나 패널에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="9af00-174">에는 `FixedRotationToUserConstraint` 고유한 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="9af00-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="9af00-176">이 제약 조건은 조작 되는 개체의 전역 회전을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="9af00-177">이는 조작을 통해 회전을 필요한 하지 않아야 하는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="9af00-178">에는 `FixedRotationToWorldConstraint` 고유한 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="9af00-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="9af00-180">이 제약 조건이 개체에 연결 된 경우 사용자의 개체 수에 관계 없이 사용자에 게 동일한 명백한 크기가 유지 됩니다 (즉, 사용자의 보기 필드와 동일한 비율을 차지 함).</span><span class="sxs-lookup"><span data-stu-id="9af00-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="9af00-181">이를 사용 하면 조작 하는 동안 슬레이트 또는 텍스트 패널을 읽을 수 있는 상태로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="9af00-182">에는 `MaintainApparentSizeConstraint` 고유한 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="9af00-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="9af00-184">이 제약 조건을 사용 하 여 조작 된 개체를 이동할 수 있는 축을 따라 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="9af00-185">이는 평면의 표면 또는 선을 따라 개체를 조작 하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="9af00-186">의 속성은 다음과 같습니다 `MoveAxisConstraint` .</span><span class="sxs-lookup"><span data-stu-id="9af00-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="9af00-187">이동 시 제약 조건</span><span class="sxs-lookup"><span data-stu-id="9af00-187">Constraint on movement</span></span>

<span data-ttu-id="9af00-188">이동을 방지 하는 축을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="9af00-189">기본적으로 이러한 축은 로컬이 아닌 전역 이지만 아래에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="9af00-190">이 속성은 플래그 이기 때문에 원하는 수의 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="9af00-191">*X 축*: x 축 방향의 이동은 선택 된 경우 제약을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="9af00-192">*Y 축*: 선택 하면 y 축을 따라 이동 하는 것이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="9af00-193">*Z 축*: 선택 하면 z 축 방향의 이동이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="9af00-194">제약 조건에 로컬 공간 사용</span><span class="sxs-lookup"><span data-stu-id="9af00-194">Use local space for constraint</span></span>

<span data-ttu-id="9af00-195">True 인 경우 조작 된 개체의 로컬 변환 축에 대 한 상대를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="9af00-196">False(기본값).</span><span class="sxs-lookup"><span data-stu-id="9af00-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="9af00-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="9af00-198">이 제약 조건을 사용 하 여 조작 된 개체가 회전할 수 있는 축을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="9af00-199">이는 조작 된 개체를 수직으로 유지 하지만 y 축 회전을 계속 허용 하는 데 유용할 수 있습니다 (예:).</span><span class="sxs-lookup"><span data-stu-id="9af00-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="9af00-200">의 속성은 다음과 같습니다 `RotationAxisConstraint` .</span><span class="sxs-lookup"><span data-stu-id="9af00-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="9af00-201">회전에 대한 제약 조건</span><span class="sxs-lookup"><span data-stu-id="9af00-201">Constraint on rotation</span></span>

<span data-ttu-id="9af00-202">회전을 방지할 축을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="9af00-203">기본적으로 이러한 축은 로컬이 아닌 전역 축이지만 아래에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="9af00-204">이 속성은 플래그이므로 원하는 수의 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="9af00-205">*Y축:* 선택한 경우 y축에 대한 회전이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="9af00-206">*Z축:* 선택한 경우 z축에 대한 회전이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="9af00-207">*X축:* X축에 대한 회전이 선택되면 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="9af00-208">제약 조건에 로컬 공간 사용</span><span class="sxs-lookup"><span data-stu-id="9af00-208">Use local space for constraint</span></span>

<span data-ttu-id="9af00-209">true인 경우 조작된 개체의 로컬 변환 축을 상대적으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="9af00-210">False(기본값).</span><span class="sxs-lookup"><span data-stu-id="9af00-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="9af00-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="9af00-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="9af00-212">이 제약 조건을 사용하면 조작된 개체의 배율에 대해 최소값과 최대값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="9af00-213">이 방법은 사용자가 너무 작거나 너무 큰 개체의 크기를 조정하지 못하게 하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="9af00-214">의 `MinMaxScaleConstraint` 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="9af00-215">최소 크기 조정</span><span class="sxs-lookup"><span data-stu-id="9af00-215">Scale minimum</span></span>

<span data-ttu-id="9af00-216">조작하는 동안 최소 배율 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="9af00-217">최대 크기 조정</span><span class="sxs-lookup"><span data-stu-id="9af00-217">Scale maximum</span></span>

<span data-ttu-id="9af00-218">조작하는 동안 최대 배율 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="9af00-219">초기 상태에 대한 상대</span><span class="sxs-lookup"><span data-stu-id="9af00-219">Relative to initial state</span></span>

<span data-ttu-id="9af00-220">true이면 위의 값이 개체 초기 배율에 상대적인 것으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="9af00-221">그렇지 않으면 절대 배율 값으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="9af00-221">Otherwise they will be interpreted as absolute scale values.</span></span>
