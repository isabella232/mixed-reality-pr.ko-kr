---
title: 조작 처리기
description: MRTK의 조작 처리기에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 조작,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176634"
---
# <a name="manipulation-handler"></a><span data-ttu-id="919e4-104">조작 처리기</span><span class="sxs-lookup"><span data-stu-id="919e4-104">Manipulation handler</span></span>

![조작 처리기](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="919e4-106">*ManipulationHandler* 스크립트를 사용하면 한 손 또는 두 손을 사용하여 개체를 이동 가능하고 확장 가능하며 회전 가능하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="919e4-107">조작은 특정 종류의 변환만 허용하도록 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="919e4-108">스크립트는 HoloLens 2 연결 손 입력, 손 광선, HoloLens(1세대) 제스처 입력 및 몰입형 헤드셋 모션 컨트롤러 입력을 비롯한 다양한 유형의 입력에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="919e4-109">조작 처리기를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="919e4-109">How to use the manipulation handler</span></span>

<span data-ttu-id="919e4-110">`ManipulationHandler`GameObject에 스크립트 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="919e4-111">또한 잡기 가능한 범위와 일치하는 충돌체를 개체에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="919e4-112">개체가 연결이 가까운 손 입력에 응답하도록 `NearInteractionGrabbable` 하려면 스크립트도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Unity 편집기에서 조작 처리기 사용](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="919e4-114">검사기 속성</span><span class="sxs-lookup"><span data-stu-id="919e4-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="919e4-115">**호스트 변환** 끌어 올 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="919e4-116">기본값은 구성 요소의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="919e4-117">**조작 유형** 한 손, 두 손 또는 둘 다 사용하여 개체를 조작할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="919e4-118">*한 손으로만*</span><span class="sxs-lookup"><span data-stu-id="919e4-118">*One handed only*</span></span>
* <span data-ttu-id="919e4-119">*양손만*</span><span class="sxs-lookup"><span data-stu-id="919e4-119">*Two handed only*</span></span>
* <span data-ttu-id="919e4-120">*1과 2손*</span><span class="sxs-lookup"><span data-stu-id="919e4-120">*One and Two handed*</span></span>

<span data-ttu-id="919e4-121">**양손 조작 유형**</span><span class="sxs-lookup"><span data-stu-id="919e4-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="919e4-122">*크기 조정:* 크기 조정만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="919e4-123">*회전:* 회전만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="919e4-124">*크기 조정 이동:* 이동 및 크기 조정이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="919e4-125">*Move Rotate:* 이동 및 회전이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="919e4-126">*배율 회전:* 회전 및 크기 조정이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="919e4-127">*회전 배율 이동:* 이동, 회전 및 크기 조정이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![조작 처리기](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="919e4-129">**원거리 조작 허용** 포인터와의 원거리 상호 작용을 사용하여 조작을 수행할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="919e4-130">**한 손 회전 모드 가까이** 개체가 한 손/컨트롤러 가까이에서 잡을 때 동작하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="919e4-131">**원 핸드 회전 모드 원거리** 한 손/컨트롤러를 멀리서 잡고 있을 때 개체가 동작하는 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="919e4-132">**한 손 회전 모드 옵션** 한 손으로 잡고 있을 때 개체가 회전하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="919e4-133">*원래 회전 유지 관리:* 이동 중인 개체를 회전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="919e4-134">*사용자에 대한 회전 유지 관리:* X/Y축에 대한 개체의 원래 회전을 사용자에게 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="919e4-135">*사용자에 대한 회전을 유지 관리하는 무게* 조정: 사용자에 대한 개체의 원래 회전을 유지 관리하지만 개체를 세로로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="919e4-136">경계 컨트롤이 있는 개체에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="919e4-137">*Face 사용자:* 개체가 항상 사용자를 향하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="919e4-138">슬레이트/패널에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="919e4-139">*사용자와 얼굴 분리:* 개체가 항상 사용자와 떨어져 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="919e4-140">뒤로 구성된 슬레이트/패널에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="919e4-141">*개체 중심 회전:* 굴절형 손/컨트롤러에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="919e4-142">손/컨트롤러의 회전을 사용하지만 개체 중심점을 사용하여 개체를 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="919e4-143">원거리에서 검사하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="919e4-144">*잡기 지점 회전:* 굴절형 손/컨트롤러에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="919e4-145">개체를 손/컨트롤러가 보유하고 있는 것처럼 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="919e4-146">검사에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-146">Useful for inspection.</span></span>

<span data-ttu-id="919e4-147">**릴리스 동작** 개체가 해제되면 개체의 물리적 이동 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="919e4-148">고정된 구성 요소가 해당 개체에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="919e4-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="919e4-149">*Nothing*</span></span>
* <span data-ttu-id="919e4-150">*모두*</span><span class="sxs-lookup"><span data-stu-id="919e4-150">*Everything*</span></span>
* <span data-ttu-id="919e4-151">*속도 유지*</span><span class="sxs-lookup"><span data-stu-id="919e4-151">*Keep Velocity*</span></span>
* <span data-ttu-id="919e4-152">*Angular 속도 유지*</span><span class="sxs-lookup"><span data-stu-id="919e4-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="919e4-153">**회전에 대한 제약 조건** 상호 작용할 때 개체가 회전할 축을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="919e4-154">*없음*</span><span class="sxs-lookup"><span data-stu-id="919e4-154">*None*</span></span>
* <span data-ttu-id="919e4-155">*X축만*</span><span class="sxs-lookup"><span data-stu-id="919e4-155">*X-Axis Only*</span></span>
* <span data-ttu-id="919e4-156">*Y축만*</span><span class="sxs-lookup"><span data-stu-id="919e4-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="919e4-157">*Z축만*</span><span class="sxs-lookup"><span data-stu-id="919e4-157">*Z-Axis Only*</span></span>

<span data-ttu-id="919e4-158">**제약 조건에 로컬 공간 사용** 세계 공간 축 또는 로컬 공간 축과 관련하여 제약 조건을 적용하는 사이를 전환하는 토글입니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="919e4-159">**이동에 대한 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="919e4-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="919e4-160">*없음*</span><span class="sxs-lookup"><span data-stu-id="919e4-160">*None*</span></span>
* <span data-ttu-id="919e4-161">*헤드로부터의 거리 수정*</span><span class="sxs-lookup"><span data-stu-id="919e4-161">*Fix distance from head*</span></span>

<span data-ttu-id="919e4-162">**활성 다듬기** 다듬기 가 활성 상태인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="919e4-163">**한 손 다량 다듬기** 이동, 배율, 회전에 적용할 다듬기 양입니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="919e4-164">0의 다듬기란 다듬기 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="919e4-165">최대값은 값이 변경되지 않는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="919e4-166">이벤트</span><span class="sxs-lookup"><span data-stu-id="919e4-166">Events</span></span>

<span data-ttu-id="919e4-167">조작 처리기는 다음 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="919e4-168">*OnManipulationStarted:* 조작이 시작될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="919e4-169">*OnManipulationEnded:* 조작이 종료될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="919e4-170">*OnHoverStarted:* 손/컨트롤러가 조작 가능한 마우스를 근거리 또는 멀리 가리키면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="919e4-171">*OnHoverEnded:* 손/컨트롤러가 조작 가능한 가리키기를 거의 또는 멀리 가리키면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="919e4-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
