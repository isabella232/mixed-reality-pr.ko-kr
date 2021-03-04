---
title: Unity의 동작 컨트롤러
description: XR 및 일반 단추 및 축 Api를 사용 하 여 동작 컨트롤러 입력을 통해 Unity에서 작업을 수행 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 동작 컨트롤러, unity, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 6dee5f03ab5fe84ac11a4eb10ef0483fea6e0083
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759064"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="dc7b7-104">Unity의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="dc7b7-104">Motion controllers in Unity</span></span>

<span data-ttu-id="dc7b7-105">HoloLens의 [손으로](../../design/gaze-and-commit.md#composite-gestures) 는 [Unity](gaze-in-unity.md)에서 작업을 수행 하는 두 가지 주요 방법, 그리고 HOLOLENS 및 몰입 형 HMD의 [동작 컨트롤러](../../design/motion-controllers.md) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="dc7b7-106">Unity에서 동일한 Api를 통해 두 공간 입력 원본에 대 한 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="dc7b7-107">Unity는 Windows Mixed Reality의 공간 입력 데이터에 액세스 하는 두 가지 기본 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="dc7b7-108">일반적인 *입력. GetButton/Input. Getbutton* api는 여러 Unity XR sdk에서 작동 하는 반면, Windows Mixed Reality와 관련 된 *InteractionManager/GestureRecognizer* api는 전체 공간 입력 데이터 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="dc7b7-109">Unity XR 입력 Api</span><span class="sxs-lookup"><span data-stu-id="dc7b7-109">Unity XR input APIs</span></span>

<span data-ttu-id="dc7b7-110">새 프로젝트의 경우 처음부터 새 XR 입력 Api를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="dc7b7-111">[XR api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="dc7b7-112">Unity 단추/축 매핑 테이블</span><span class="sxs-lookup"><span data-stu-id="dc7b7-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="dc7b7-113">Unity의 Windows Mixed Reality의 입력 관리자 동작 컨트롤러는 *입력. getbutton/Getbutton* api를 통해 아래에 나열 된 단추 및 축 id를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="dc7b7-114">"Windows MR" 열은 *InteractionSourceState* 유형에 서 사용할 수 있는 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="dc7b7-115">이러한 각 Api에 대해서는 아래 섹션에서 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="dc7b7-116">Windows Mixed Reality의 단추/축 ID 매핑은 일반적으로 Oculus 단추/축 Id와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="dc7b7-117">Windows Mixed Reality의 단추/축 ID 매핑은 다음 두 가지 방법으로 OpenVR 매핑과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="dc7b7-118">이 매핑은 thumbsticks와 터치 패드를 모두 사용 하는 컨트롤러를 지원 하기 위해 엄지 스틱과는 다른 터치 패드 Id를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="dc7b7-119">매핑은 메뉴 단추의 A 및 X 단추 Id를 오버 로드 하지 않고 실제 ABXY 단추에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="dc7b7-120">입력</span><span class="sxs-lookup"><span data-stu-id="dc7b7-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="dc7b7-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="dc7b7-122">(입력. GetButton/Getbutton)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="dc7b7-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 특정 입력 API</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="dc7b7-124">XR. WSA. 입력</span><span class="sxs-lookup"><span data-stu-id="dc7b7-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="dc7b7-125">왼쪽</span><span class="sxs-lookup"><span data-stu-id="dc7b7-125">Left hand</span></span> </th><th> <span data-ttu-id="dc7b7-126">오른쪽</span><span class="sxs-lookup"><span data-stu-id="dc7b7-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="dc7b7-127">트리거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="dc7b7-128">축 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="dc7b7-129">축 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="dc7b7-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="dc7b7-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-131">아날로그 값 트리거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="dc7b7-132">축 9</span><span class="sxs-lookup"><span data-stu-id="dc7b7-132">Axis 9</span></span> </td><td> <span data-ttu-id="dc7b7-133">축 10</span><span class="sxs-lookup"><span data-stu-id="dc7b7-133">Axis 10</span></span> </td><td> <span data-ttu-id="dc7b7-134">Select보도 금액</span><span class="sxs-lookup"><span data-stu-id="dc7b7-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-135">부분적으로 누른 트리거 선택</span><span class="sxs-lookup"><span data-stu-id="dc7b7-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="dc7b7-136">단추 14 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="dc7b7-137">단추 15 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="dc7b7-138">Select보도 Sedamount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-139">메뉴 단추 누름</span><span class="sxs-lookup"><span data-stu-id="dc7b7-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="dc7b7-140">단추 6 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-140">Button 6\*</span></span> </td><td> <span data-ttu-id="dc7b7-141">단추 7 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-141">Button 7\*</span></span> </td><td> <span data-ttu-id="dc7b7-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="dc7b7-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-143">그립 단추 누름</span><span class="sxs-lookup"><span data-stu-id="dc7b7-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="dc7b7-144">축 11 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="dc7b7-145">단추 4 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="dc7b7-146">축 12 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="dc7b7-147">단추 5 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="dc7b7-148">grasped</span><span class="sxs-lookup"><span data-stu-id="dc7b7-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-149">엄지 스틱 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="dc7b7-150">축 1</span><span class="sxs-lookup"><span data-stu-id="dc7b7-150">Axis 1</span></span> </td><td> <span data-ttu-id="dc7b7-151">축 4</span><span class="sxs-lookup"><span data-stu-id="dc7b7-151">Axis 4</span></span> </td><td> <span data-ttu-id="dc7b7-152">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-153">엄지 스틱 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="dc7b7-154">축 2</span><span class="sxs-lookup"><span data-stu-id="dc7b7-154">Axis 2</span></span> </td><td> <span data-ttu-id="dc7b7-155">축 5</span><span class="sxs-lookup"><span data-stu-id="dc7b7-155">Axis 5</span></span> </td><td> <span data-ttu-id="dc7b7-156">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-157">엄지 스틱 누름</span><span class="sxs-lookup"><span data-stu-id="dc7b7-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="dc7b7-158">단추 8</span><span class="sxs-lookup"><span data-stu-id="dc7b7-158">Button 8</span></span> </td><td> <span data-ttu-id="dc7b7-159">단추 9</span><span class="sxs-lookup"><span data-stu-id="dc7b7-159">Button 9</span></span> </td><td> <span data-ttu-id="dc7b7-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="dc7b7-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-161">터치 패드 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="dc7b7-162">축 17 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="dc7b7-163">축 19 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="dc7b7-164">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-165">터치 패드 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="dc7b7-166">축 18 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="dc7b7-167">축 20 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="dc7b7-168">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-169">터치 패드 작업</span><span class="sxs-lookup"><span data-stu-id="dc7b7-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="dc7b7-170">단추 18 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-170">Button 18\*</span></span> </td><td> <span data-ttu-id="dc7b7-171">단추 19 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-171">Button 19\*</span></span> </td><td> <span data-ttu-id="dc7b7-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="dc7b7-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-173">터치 패드 누름</span><span class="sxs-lookup"><span data-stu-id="dc7b7-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="dc7b7-174">단추 16 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-174">Button 16\*</span></span> </td><td> <span data-ttu-id="dc7b7-175">단추 17 \*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-175">Button 17\*</span></span> </td><td> <span data-ttu-id="dc7b7-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="dc7b7-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-177">6DoF 그립 포즈 또는 포인터 포즈</span><span class="sxs-lookup"><span data-stu-id="dc7b7-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="dc7b7-178"><i>그립</i> 포즈만: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="dc7b7-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking. GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="dc7b7-180">전달 <i>그립</i> 또는 <i>포인터</i> 를 인수로 전달 합니다. sourcestate TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="dc7b7-181">sourceState</span><span class="sxs-lookup"><span data-stu-id="dc7b7-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-182">상태 추적</span><span class="sxs-lookup"><span data-stu-id="dc7b7-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="dc7b7-183"><i>MR 특정 API를 통해서만 사용할 수 있는 위치 정확도 및 원본 손실 위험</i> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="dc7b7-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="dc7b7-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="dc7b7-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="dc7b7-186">이러한 단추/축 Id는 gamepads, Oculus Touch 및 OpenVR에서 사용 하는 매핑의 충돌로 인해 Unity에서 OpenVR에 사용 하는 Id와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="dc7b7-187">그립 포즈 및 포인팅 포즈</span><span class="sxs-lookup"><span data-stu-id="dc7b7-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="dc7b7-188">Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="dc7b7-189">각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때를 가리키는 데 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="dc7b7-190">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스, **그립 포즈** 및 **포인터 포즈** 에 대해 조사할 수 있는 두 가지 종류의 포즈를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="dc7b7-191">그립 포즈 및 포인터 포즈 좌표는 모두 전역 Unity 세계 좌표의 모든 Unity Api에 의해 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="dc7b7-192">그립 포즈</span><span class="sxs-lookup"><span data-stu-id="dc7b7-192">Grip pose</span></span>

<span data-ttu-id="dc7b7-193">**그립 포즈** 는 HoloLens에서 검색 되거나 동작 컨트롤러를 보유 하는 사용자 palm의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="dc7b7-194">몰입 형 헤드셋에서 그립 포즈는 사용자의 **손을** 만들거나 **사용자의 손을 보유 한 개체** 를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="dc7b7-195">그립 포즈는 동작 컨트롤러를 시각화할 때에도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="dc7b7-196">동작 컨트롤러에 대해 Windows에서 제공 하는 **렌더링할 모델** 은 그립 포즈를 원본 및 회전 중심으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="dc7b7-197">그립 포즈는 구체적으로 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="dc7b7-198">**그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="dc7b7-199">Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 보통 클릭 단추와 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="dc7b7-200">**그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="dc7b7-201">**그립 방향 전방 축: 핸들** 을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="dc7b7-202">**그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="dc7b7-203">Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 *[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) 또는 WINDOWS MR 특정 API (*sourcestate/Rotation*, **그립** 노드에 대 한 포즈 데이터 요청)를 통해</span><span class="sxs-lookup"><span data-stu-id="dc7b7-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="dc7b7-204">포인터 포즈</span><span class="sxs-lookup"><span data-stu-id="dc7b7-204">Pointer pose</span></span>

<span data-ttu-id="dc7b7-205">**포인터 포즈** 는 컨트롤러의 팁을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="dc7b7-206">시스템에서 제공 하는 포인터 포즈는 **컨트롤러 모델 자체를 렌더링** 하는 경우 raycast를 사용 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="dc7b7-207">컨트롤러 대신 다른 가상 개체 (예: 가상 사용자)를 렌더링 하는 경우 앱 정의 된 포 모델의 배럴을 따라 이동 하는 광선과 같이 해당 가상 개체에 가장 자연 스러운 광선을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="dc7b7-208">사용자는 가상 개체를 볼 수 있고 실제 컨트롤러는 볼 수 없으므로 가상 개체를 가리키면 앱을 사용 하는 것이 더 자연스럽 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="dc7b7-209">현재 포인터 포즈는 *InteractionSourceNode* 를 인수로 전달 하는 Windows MR 특정 API 인 *TryGetPosition/Rotation* 을 통해서만 Unity에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="dc7b7-210">컨트롤러 추적 상태</span><span class="sxs-lookup"><span data-stu-id="dc7b7-210">Controller tracking state</span></span>

<span data-ttu-id="dc7b7-211">헤드셋 처럼 Windows Mixed Reality 동작 컨트롤러를 사용 하려면 외부 추적 센서를 설정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="dc7b7-212">대신, 컨트롤러는 헤드셋 자체의 센서에 의해 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="dc7b7-213">사용자가 헤드셋의 보기 필드에서 컨트롤러를 이동 하면 대부분의 경우 Windows에서는 계속 해 서 컨트롤러 위치를 유추 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="dc7b7-214">컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="dc7b7-215">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="dc7b7-216">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="dc7b7-217">이를 위한 가장 좋은 방법은 직접 시도해 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="dc7b7-218">다양 한 추적 상태에서 동작 컨트롤러와 함께 작동 하는 몰입 형 콘텐츠 예제를 통해이 비디오를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="dc7b7-219">명시적 추적 상태에 대 한 추론</span><span class="sxs-lookup"><span data-stu-id="dc7b7-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="dc7b7-220">추적 상태에 따라 위치를 다르게 처리 하려는 앱은 더 나아가 컨트롤러의 상태에 대 한 속성 (예: *SourceLossRisk* 및 *positionaccuracy*)을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="dc7b7-221">상태 추적</span><span class="sxs-lookup"><span data-stu-id="dc7b7-221">Tracking state</span></span> </th><th> <span data-ttu-id="dc7b7-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="dc7b7-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="dc7b7-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="dc7b7-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="dc7b7-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="dc7b7-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="dc7b7-225"><b>높은 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-226">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-227">높음</span><span class="sxs-lookup"><span data-stu-id="dc7b7-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-228">true</span><span class="sxs-lookup"><span data-stu-id="dc7b7-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-229"><b>높은 정확도 (손실 위험)</b> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="dc7b7-230">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-231">높음</span><span class="sxs-lookup"><span data-stu-id="dc7b7-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-232">true</span><span class="sxs-lookup"><span data-stu-id="dc7b7-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-233"><b>대략적인 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="dc7b7-234">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="dc7b7-235">근사치</span><span class="sxs-lookup"><span data-stu-id="dc7b7-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="dc7b7-236">true</span><span class="sxs-lookup"><span data-stu-id="dc7b7-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dc7b7-237"><b>위치 없음</b> </span><span class="sxs-lookup"><span data-stu-id="dc7b7-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="dc7b7-238">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="dc7b7-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="dc7b7-239">근사치</span><span class="sxs-lookup"><span data-stu-id="dc7b7-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="dc7b7-240">false</span><span class="sxs-lookup"><span data-stu-id="dc7b7-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="dc7b7-241">이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="dc7b7-242">**높은 정확도:** 동작 컨트롤러는 헤드셋의 보기 필드 내에 있지만 일반적으로 시각적 추적에 따라 정확도가 높은 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="dc7b7-243">일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려진 이동 컨트롤러 (예: 사용자)는 컨트롤러 자체의 관성 추적을 기반으로 짧은 시간 동안 계속 해 서 정확도가 높은 포즈를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="dc7b7-244">**높은 정확도 (손실 위험):** 사용자가 이동 컨트롤러를 헤드셋의 보기 필드 가장자리를 지나서 이동할 때 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="dc7b7-245">앱은 **SourceLossRisk** reach 1.0을 확인 하 여 컨트롤러가이 FOV 경계에 도달한 경우를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="dc7b7-246">이 시점에서 앱은 고품질 포즈의 안정적인 스트림을 필요로 하는 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="dc7b7-247">**대략적인 정확도:** 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="dc7b7-248">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="dc7b7-249">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="dc7b7-250">입력 요구 사항이 많은 앱은 사용자에 게이 시간 동안 오프 화면 대상에 대 한 hitbox을 제공 하는 등의 방법으로 **positionaccuracy** 속성을 검사 하 여 정확도가 **높은** **정확도부터 정확도까지** 이러한 삭제를 합리적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="dc7b7-251">**위치 없음:** 컨트롤러는 오랜 시간 동안 정확한 정확도로 작동할 수 있지만, 경우에 따라 본문 잠금 위치가 중요 하지 않은 경우에도 시스템에서 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="dc7b7-252">예를 들어 설정 된 컨트롤러가 시각적으로 관찰 되지 않았거나 사용자가 다른 사용자가 선택 하는 컨트롤러를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="dc7b7-253">이러한 시간에 시스템은 앱에 어떤 위치도 제공 하지 않으며 *TryGetPosition* 는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="dc7b7-254">Common Unity Api (입력. GetButton/Getbutton)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="dc7b7-255">**네임 스페이스:** *unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="dc7b7-256">**형식**: *Input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="dc7b7-257">Unity는 현재 일반 입력을 사용 *합니다. GetButton/Input. Getbutton* api를 사용 하면 핸드 및 동작 컨트롤러를 포함 하 여 [oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html), [Openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality의 입력을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="dc7b7-258">앱이 입력에 이러한 Api를 사용 하는 경우 Windows Mixed Reality를 비롯 하 여 여러 XR Sdk에서 동작 컨트롤러를 쉽게 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="dc7b7-259">논리적 단추의 누름 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc7b7-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="dc7b7-260">일반 Unity 입력 Api를 사용 하려면 일반적으로 [Unity 입력 관리자](https://docs.unity3d.com/Manual/ConventionalGameInput.html)에서 단추와 축을 논리적 이름에 연결 하 여 단추 또는 축 id를 각 이름에 바인딩하는 것으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="dc7b7-261">그런 다음 해당 논리적 단추/축 이름을 참조 하는 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="dc7b7-262">예를 들어 왼쪽 동작 컨트롤러의 트리거 단추를 전송 작업에 매핑하려면 **> 프로젝트 설정 편집** 으로 이동 하 여 Unity 내에서 입력 > 하 고 축 아래에서 제출 섹션의 속성을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="dc7b7-263">**긍정 단추** 또는 **Alt 긍정 단추** 속성을 다음과 같이 **조이스틱 단추 14** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="dc7b7-264">![Unity의 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="dc7b7-265">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-265">*Unity InputManager*</span></span>

<span data-ttu-id="dc7b7-266">그런 다음 스크립트는 입력을 사용 하 여 전송 작업을 확인할 수 있습니다 *. GetButton*:</span><span class="sxs-lookup"><span data-stu-id="dc7b7-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="dc7b7-267">**축** 에서 **크기** 속성을 변경 하 여 논리적 단추를 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="dc7b7-268">물리적 단추의 누름 상태를 직접 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc7b7-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="dc7b7-269">*입력. GetKey* 를 사용 하 여 정규화 된 이름으로 수동으로 단추에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="dc7b7-270">직접 또는 동작 컨트롤러의 포즈 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc7b7-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="dc7b7-271">XR를 사용 하 여 컨트롤러의 위치 및 회전에 액세스할 수 있습니다 *. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="dc7b7-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="dc7b7-272">위의 코드는 컨트롤러의 그립 포즈 (사용자가 컨트롤러를 보유 하는 위치)를 나타내며,이는 사용자 쪽에서 소드를 렌더링 하거나 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="dc7b7-273">이 그립 포즈와 포인터 포즈 (컨트롤러의 팁) 간의 관계는 컨트롤러 마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="dc7b7-274">이제 컨트롤러의 포인터 포즈에 액세스 하는 것은 아래 섹션에 설명 된 MR 특정 입력 API를 통해서만 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="dc7b7-275">Windows 관련 Api (XR. WSA. 입력</span><span class="sxs-lookup"><span data-stu-id="dc7b7-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="dc7b7-276">프로젝트에서 XR를 사용 하는 경우 WSA Api는 향후 Unity 릴리스의 XR SDK에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="dc7b7-277">새 프로젝트의 경우 처음부터 XR SDK를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="dc7b7-278">[XR 입력 시스템 및 api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="dc7b7-279">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="dc7b7-280">**유형**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="dc7b7-281">Windows Mixed Reality 입력 (HoloLens 용) 및 동작 컨트롤러에 대 한 자세한 정보를 보려면 *Unityengine. XR* 네임 스페이스에서 windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="dc7b7-282">이를 통해 위치 정확도 나 소스 종류와 같은 추가 정보에 액세스할 수 있으므로 실습 및 컨트롤러를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="dc7b7-283">직접 및 동작 컨트롤러의 상태 폴링</span><span class="sxs-lookup"><span data-stu-id="dc7b7-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="dc7b7-284">*GetCurrentReading* 메서드를 사용 하 여 각 상호 작용 소스 (직접 또는 동작 컨트롤러)에 대해이 프레임의 상태를 폴링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="dc7b7-285">가져오는 각 *InteractionSourceState* 는 현재 시점에서 상호 작용 소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="dc7b7-286">*InteractionSourceState* 는 다음과 같은 정보를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="dc7b7-287">어떤 [종류의 누름](../../design/motion-controllers.md) 이 발생 합니까 (선택/메뉴/-/터치 패드/엄지 스틱)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="dc7b7-288">터치 패드 및/또는 엄지 스틱 XY 좌표 및 작업 된 상태와 같은 동작 컨트롤러에 해당 하는 기타 데이터</span><span class="sxs-lookup"><span data-stu-id="dc7b7-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="dc7b7-289">InteractionSourceKind는 원본이 나 동작 컨트롤러 인지 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="dc7b7-290">앞으로 예측 된 렌더링 동작에 대 한 폴링</span><span class="sxs-lookup"><span data-stu-id="dc7b7-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="dc7b7-291">손이 나 컨트롤러에서 상호 작용 원본 데이터를 폴링하는 경우이 프레임의 photons 사용자의 눈에 도달 하 게 되는 순간에 대해 앞으로 예측 하는 포즈를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="dc7b7-292">앞으로 예측 되는 포즈는 컨트롤러를 렌더링 하거나 각 프레임에서 보유 한 개체를 **렌더링** 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="dc7b7-293">Controller를 사용 하 여 지정 된 보도 또는 릴리스를 대상으로 하는 경우 아래에 설명 된 기록 이벤트 Api를 사용 하는 경우 가장 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="dc7b7-294">이 현재 프레임에 대해 앞으로 예측 한 헤드 포즈를 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="dc7b7-295">원본 포즈와 마찬가지로,이 기능은 커서를 **렌더링** 하는 데 유용 합니다. 단, 아래에 설명 된 기록 이벤트 api를 사용 하는 경우에는 지정 된 누름 또는 릴리스를 대상으로 하는 것이 가장 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="dc7b7-296">상호 작용 소스 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="dc7b7-296">Handling interaction source events</span></span>

<span data-ttu-id="dc7b7-297">정확한 기록 포즈 데이터에서 발생 하는 입력 이벤트를 처리 하기 위해 폴링 대신 상호 작용 소스 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="dc7b7-298">상호 작용 소스 이벤트를 처리 하려면:</span><span class="sxs-lookup"><span data-stu-id="dc7b7-298">To handle interaction source events:</span></span>
* <span data-ttu-id="dc7b7-299">*InteractionManager* 입력 이벤트에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="dc7b7-300">관심이 있는 각 상호 작용 이벤트 형식에 대해 구독 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="dc7b7-301">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-301">Handle the event.</span></span> <span data-ttu-id="dc7b7-302">상호 작용 이벤트를 구독 한 후에는 해당 하는 경우 콜백을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="dc7b7-303">*Sourcepressed* 예제에서는 소스가 검색 된 후와 릴리스 또는 손실 되기 전에이 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="dc7b7-304">이벤트 처리를 중지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="dc7b7-304">How to stop handling an event</span></span>

<span data-ttu-id="dc7b7-305">이벤트에 더 이상 관심이 없거나 이벤트를 구독 하는 개체를 삭제 하려는 경우에는 이벤트 처리를 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="dc7b7-306">이벤트 처리를 중지 하려면 이벤트의 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="dc7b7-307">상호 작용 소스 이벤트 목록</span><span class="sxs-lookup"><span data-stu-id="dc7b7-307">List of interaction source events</span></span>

<span data-ttu-id="dc7b7-308">사용할 수 있는 상호 작용 소스 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-308">The available interaction source events are:</span></span>
* <span data-ttu-id="dc7b7-309">*InteractionSourceDetected* (원본이 활성화 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="dc7b7-310">*InteractionSourceLost* (비활성 상태가 됨)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="dc7b7-311">*InteractionSourcePressed* (누르기, 단추 누르기 또는 "Select" 재생)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="dc7b7-312">*InteractionSourceReleased* (탭의 끝, 단추 해제 또는 "Select" 재생 끝)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="dc7b7-313">*InteractionSourceUpdated* (다른 상태를 이동 하거나 변경 하지 않음)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="dc7b7-314">기록 대상 이벤트는 누름 또는 릴리스와 가장 정확 하 게 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="dc7b7-315">앞에서 설명한 폴링 Api는 앱을 앞으로 예측 하는 포즈를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="dc7b7-316">이러한 예측 된 포즈는 컨트롤러 또는 가상 핸드헬드 개체를 렌더링 하는 데 가장 적합 하지만 다음 두 가지 주요 이유로 이후 포즈는 대상 지정에 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="dc7b7-317">사용자가 컨트롤러의 단추를 누를 때 시스템에서 누르기를 수신 하기 전에 Bluetooth를 통해 무선 대기 시간이 20 밀리초 정도 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="dc7b7-318">그런 다음 앞으로 예측 하는 포즈를 사용 하는 경우 현재 프레임의 photons 사용자의 눈에 도달 하는 시간을 대상으로 적용 하는 다른 10-20 ms의 전달 예측이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="dc7b7-319">즉, 폴링을 통해 사용자의 헤드와 손을 모두 사용 하는 경우에는 사용자의 헤드와 30-40를 전달 하는 소스 포즈 또는 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="dc7b7-320">HoloLens 손으로 입력 한 경우 무선 전송 지연이 발생 하지 않지만, 누르기를 검색 하는 데 비슷한 처리 지연이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="dc7b7-321">직접 또는 컨트롤러에 대 한 사용자의 원래 의도에 따라 정확 하 게 대상으로 지정 하려면 해당 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력 이벤트에서 기록 원본 포즈 또는 head 포즈를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="dc7b7-322">사용자의 헤드 또는 해당 컨트롤러에서 기록 포즈 데이터를 사용 하 여 보도를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="dc7b7-323">사용자가 [gazing](../../design/gaze-and-commit.md) 된 항목을 확인 하기 위해 **대상 지정** 에 사용할 수 있는 제스처 또는 컨트롤러를 누를 때 발생 하는 시점의 헤드입니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="dc7b7-324">이동 컨트롤러를 사용 하 여 사용자가 컨트롤러를 가리킨 **항목을 확인 하는** 데 사용 될 수 있는 시점에 발생 하는 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="dc7b7-325">이는 누름이 발생 한 컨트롤러의 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="dc7b7-326">컨트롤러 자체를 렌더링 하는 경우에는 핸들 포즈 대신 포인터 포즈를 요청 하 여 사용자가 렌더링 된 컨트롤러의 자연 스러운 팁을 고려 하는 대상 광선을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="dc7b7-327">이벤트 처리기 예</span><span class="sxs-lookup"><span data-stu-id="dc7b7-327">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="dc7b7-328">MRTK의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="dc7b7-328">Motion Controllers in MRTK</span></span>

<span data-ttu-id="dc7b7-329">입력 관리자에서 [제스처 및 동작 컨트롤러](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md) 에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-329">You can access [gesture and motion controller](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="dc7b7-330">안내 따르기</span><span class="sxs-lookup"><span data-stu-id="dc7b7-330">Follow along with tutorials</span></span>

<span data-ttu-id="dc7b7-331">보다 자세한 사용자 지정 예제가 포함 된 단계별 자습서는 혼합 현실 아카데미에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="dc7b7-332">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="dc7b7-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="dc7b7-333">MR 입력 213: 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="dc7b7-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="dc7b7-334">[![MR 입력 213-동작 컨트롤러](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="dc7b7-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="dc7b7-335">*MR 입력 213-동작 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="dc7b7-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="dc7b7-336">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="dc7b7-336">Next Development Checkpoint</span></span>

<span data-ttu-id="dc7b7-337">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="dc7b7-338">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc7b7-339">손 및 시선 추적</span><span class="sxs-lookup"><span data-stu-id="dc7b7-339">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="dc7b7-340">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc7b7-341">공유 환경</span><span class="sxs-lookup"><span data-stu-id="dc7b7-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="dc7b7-342">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc7b7-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc7b7-343">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc7b7-343">See also</span></span>

* [<span data-ttu-id="dc7b7-344">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="dc7b7-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="dc7b7-345">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="dc7b7-345">Motion controllers</span></span>](../../design/motion-controllers.md)