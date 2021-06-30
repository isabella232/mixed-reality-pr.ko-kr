---
title: 컨트롤러, 포인터 및 포커스
description: 컨트롤러, 포인터 및 포커스와 상호 작용
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 포인터, 컨트롤러
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121621"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="06c4b-104">컨트롤러, 포인터 및 포커스</span><span class="sxs-lookup"><span data-stu-id="06c4b-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="06c4b-105">컨트롤러, 포인터 및 초점은 핵심 입력 시스템에 의해 설정 된 기반을 기반으로 구축 되는 상위 수준 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="06c4b-106">이와 함께 장면의 개체와 상호 작용 하는 메커니즘의 많은 부분을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="06c4b-107">Controllers</span><span class="sxs-lookup"><span data-stu-id="06c4b-107">Controllers</span></span>

<span data-ttu-id="06c4b-108">컨트롤러는 물리적 컨트롤러 (자유도, 트레일러 식 등의 6도)를 표현 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="06c4b-109">이러한 장치는 장치 관리자에 의해 생성 되며 해당 하는 기본 시스템과 통신 하 고 해당 데이터를 MRTK 모양의 데이터 및 이벤트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="06c4b-110">예를 들어 Windows Mixed Reality 플랫폼에서는 [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 기본 Windows [직접 추적 api](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 와 상호 작용 하 여 손, 포즈 및 기타 속성에 대 한 정보를 가져오기 위한 역할을 담당 하는 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="06c4b-111">RaisePoseInputChanged 또는 RaiseHandJointsUpdated를 호출 하 여이 데이터를 관련 MRTK 이벤트로 전환 하 고,에 대 한 쿼리가 올바른 데이터를 반환 하도록 자체 내부 상태를 업데이트 하는 일을 담당 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="06c4b-112">일반적으로 컨트롤러의 수명 주기에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="06c4b-113">컨트롤러는 새 원본을 검색할 때 장치 관리자에 의해 생성 됩니다. 예를 들어 장치 관리자는 직접 추적을 검색 하 고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="06c4b-114">컨트롤러의 Update () 루프에서는 기본 API 시스템을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="06c4b-115">동일한 업데이트 루프에서 핵심 입력 시스템 자체 (예: HandMeshUpdated 또는 HandJointsUpdated)를 직접 호출 하 여 입력 이벤트 변경을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="06c4b-116">포인터 및 포커스</span><span class="sxs-lookup"><span data-stu-id="06c4b-116">Pointers and focus</span></span>

<span data-ttu-id="06c4b-117">포인터는 게임 개체와 상호 작용 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="06c4b-118">이 섹션에서는 포인터를 만드는 방법, 업데이트 되는 방법 및 포커스에 있는 개체를 결정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="06c4b-119">또한 존재 하는 다양 한 유형의 포인터와 활성 상태의 시나리오를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="06c4b-120">포인터 범주</span><span class="sxs-lookup"><span data-stu-id="06c4b-120">Pointer categories</span></span>

<span data-ttu-id="06c4b-121">포인터는 일반적으로 다음 범주 중 하나에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="06c4b-122">**먼 포인터**</span><span class="sxs-lookup"><span data-stu-id="06c4b-122">**Far pointers**</span></span>

  <span data-ttu-id="06c4b-123">이러한 종류의 포인터는 사용자의 멀리 떨어져 있는 개체와 상호 작용 하는 데 사용 됩니다 (멀리 떨어져 있는 것은 단순히 "가까이 있지 않음"으로 정의 됨).</span><span class="sxs-lookup"><span data-stu-id="06c4b-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="06c4b-124">이러한 형식의 포인터는 일반적으로 전 세계에 있을 수 있는 선을 캐스트 하 고 사용자가 바로 다음에 있지 않은 개체와 상호 작용 하 고 조작할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="06c4b-125">**가까운 포인터**</span><span class="sxs-lookup"><span data-stu-id="06c4b-125">**Near pointers**</span></span>

  <span data-ttu-id="06c4b-126">이러한 형식의 포인터를 사용 하 여 사용자가 잡아 이동 하 고 조작할 수 있을 만큼 가까운 개체와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="06c4b-127">일반적으로 이러한 종류의 포인터는 가까운 주변 주변에서 개체를 검색 하 여 개체와 상호 작용 합니다. 예를 들어 작은 거리에서 raycasting를 수행 하거나 주변에서 개체를 찾는 구면 캐스트를 수행 하거나 grabbable/touchable로 간주 되는 개체 목록을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="06c4b-128">**텔레포트 포인터**</span><span class="sxs-lookup"><span data-stu-id="06c4b-128">**Teleport pointers**</span></span>

  <span data-ttu-id="06c4b-129">이러한 포인터 형식은 teleportation 시스템에 연결 하 여 포인터의 대상 위치로 사용자를 이동 하는 것을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="06c4b-130">포인터 중재</span><span class="sxs-lookup"><span data-stu-id="06c4b-130">Pointer mediation</span></span>

<span data-ttu-id="06c4b-131">단일 컨트롤러에는 여러 개의 포인터가 있을 수 있으므로 (예를 들어, 두 번째는 근접 하 고 먼 상호 작용 포인터를 사용할 수 있음) 어떤 포인터가 활성 상태 여야 mediating를 담당 하는 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="06c4b-132">예를 들어, 사용자가 pressable 단추를 사용 하는 경우가 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 표시를 중지 하 고가 사용 됩니다 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="06c4b-133">이는 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 모든 포인터의 상태에 따라 활성 상태인 포인터를 결정 하는에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="06c4b-134">이 작업을 수행 하는 주요 작업 중 하나는 가까운 포인터가 개체에 가까이 있을 때 먼 포인터를 사용 하지 않도록 설정 하는 것입니다 .를 참조 하십시오 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="06c4b-135">포인터 프로필의 속성을 변경 하 여 포인터 mediator의 대체 구현을 제공할 수 있습니다 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="06c4b-136">포인터를 사용 하지 않도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="06c4b-136">How to disable pointers</span></span>

<span data-ttu-id="06c4b-137">포인터 mediator은 모든 프레임을 실행 하므로 모든 포인터의 활성/비활성 상태를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="06c4b-138">따라서 코드에서 포인터의 IsInteractionEnabled 속성을 설정 하면 모든 프레임 mediator 포인터로 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="06c4b-139">대신, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 직접 포인터를 설정 하거나 해제할지 여부를 제어 하는를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="06c4b-140">이는 기본값 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 및 MRTK를 사용 하는 경우에만 작동 합니다 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="06c4b-141">예: MRTK에서 손 광선 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="06c4b-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="06c4b-142">다음 코드는 MRTK에서 손 광선을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="06c4b-143">다음 코드는 MRTK의 기본 동작에 손 광선을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="06c4b-144">다음 코드는 grabbable 가까이에 있든 관계 없이 핸드 광선을 강제로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="06c4b-145">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 더 많은 예제는 및를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06c4b-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="06c4b-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="06c4b-146">FocusProvider</span></span>

<span data-ttu-id="06c4b-147">는 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 모든 포인터 목록을 반복 하 고 각 포인터에 대 한 포커스가 있는 개체를 파악 하는 작업을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="06c4b-148">각 `Update()` 호출에서 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="06c4b-149">SphereOverlap raycastMode를 지정 하는 등의 방법으로 포인터 자체에서 구성 된 대로 모든 포인터를 업데이트 하 고, 포인터 자체에서 구성 된 대로 적중 검색을 수행 합니다. 예를 들어, FocusProvider는 구 기반 충돌을 발생 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="06c4b-150">포인터 단위로 포커스가 있는 개체를 업데이트 합니다. 즉, 개체가 포커스를 얻은 경우 해당 개체에 대 한 이벤트를 트리거합니다. 즉, 개체가 포커스를 잃어 잃은 경우 포커스가 손실 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="06c4b-151">포인터 구성 및 수명 주기</span><span class="sxs-lookup"><span data-stu-id="06c4b-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="06c4b-152">포인터는 입력 시스템 프로필의 *포인터* 섹션에서 [구성할 수 있습니다](../features/input/pointers.md) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="06c4b-153">포인터의 수명은 일반적으로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="06c4b-154">장치 관리자가 컨트롤러의 존재를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="06c4b-155">그런 다음이 장치 관리자는에 대 한 호출을 통해 컨트롤러와 연결 된 포인터 집합을 만듭니다 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="06c4b-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="06c4b-156">해당 Update () 루프에서 FocusProvider는 모든 유효한 포인터를 반복 하 고, 연결 된 raycast 또는 적중 검색 논리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="06c4b-157">이는 각 특정 포인터가 가리키는 개체를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="06c4b-158">한 번에 여러 개의 입력을 활성화 하는 것이 가능 하기 때문에 동시에 포커스가 있는 여러 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="06c4b-159">장치 관리자가 컨트롤러 원본이 손실 된 것을 발견 하면 손실 된 컨트롤러와 연결 된 포인터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c4b-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>