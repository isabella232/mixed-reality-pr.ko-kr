---
title: Unity의 제스처 및 모션 컨트롤러
description: 핸드 제스처 및 동작 컨트롤러를 사용 하 여 Unity의 응시에서 작업을 수행 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 제스처, 동작 컨트롤러, unity, 응시, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 122642bb7fc561e505098bca00b8bf65bfd4552e
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443576"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="87450-104">Unity의 제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="87450-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="87450-105">HoloLens의 [손으로](../../design/gaze-and-commit.md#composite-gestures) 는 [Unity](gaze-in-unity.md)에서 작업을 수행 하는 두 가지 주요 방법, 그리고 HOLOLENS 및 몰입 형 HMD의 [동작 컨트롤러](../../design/motion-controllers.md) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="87450-106">Unity에서 동일한 Api를 통해 두 공간 입력 원본에 대 한 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="87450-107">Unity는 Windows Mixed Reality의 공간 입력 데이터에 액세스 하는 두 가지 기본 방법인 common *input. GetButton/input. Getbutton* api를 여러 Unity XR sdk에서 작동 하는 두 가지 기본 방법 및 사용 가능한 공간 입력 데이터의 전체 집합을 노출 하는 Windows Mixed Reality 관련 *InteractionManager/GestureRecognizer* api를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="87450-108">Unity XR 입력 Api</span><span class="sxs-lookup"><span data-stu-id="87450-108">Unity XR input APIs</span></span>

<span data-ttu-id="87450-109">새 프로젝트의 경우 처음부터 새 XR 입력 Api를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-109">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="87450-110">[XR api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-110">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="87450-111">Unity 단추/축 매핑 테이블</span><span class="sxs-lookup"><span data-stu-id="87450-111">Unity button/axis mapping table</span></span>

<span data-ttu-id="87450-112">아래 표의 단추 및 축 Id는 *입력. GetButton/Getbutton* api를 통해 Unity의 Windows Mixed Reality 동작 컨트롤러에서 지원 되지만, "Windows MR" 열은 *InteractionSourceState* 형식에서 사용할 수 있는 속성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-112">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="87450-113">이러한 각 Api에 대해서는 아래 섹션에서 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-113">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="87450-114">Windows Mixed Reality의 단추/축 ID 매핑은 일반적으로 Oculus 단추/축 Id와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-114">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="87450-115">Windows Mixed Reality의 단추/축 ID 매핑은 다음 두 가지 방법으로 OpenVR 매핑과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-115">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="87450-116">이 매핑은 thumbsticks와 터치 패드를 모두 사용 하는 컨트롤러를 지원 하기 위해 엄지 스틱과는 다른 터치 패드 Id를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-116">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="87450-117">매핑은 메뉴 단추의 A 및 X 단추 Id를 오버 로드 하지 않고 실제 ABXY 단추에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-117">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="87450-118">입력</span><span class="sxs-lookup"><span data-stu-id="87450-118">Input</span></span> </th><th colspan="2"><span data-ttu-id="87450-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="87450-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="87450-120">(입력. GetButton/Getbutton)</span><span class="sxs-lookup"><span data-stu-id="87450-120">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="87450-121"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 특정 입력 API</a></span><span class="sxs-lookup"><span data-stu-id="87450-121"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="87450-122">XR. WSA. 입력</span><span class="sxs-lookup"><span data-stu-id="87450-122">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="87450-123">왼쪽</span><span class="sxs-lookup"><span data-stu-id="87450-123">Left hand</span></span> </th><th> <span data-ttu-id="87450-124">오른쪽</span><span class="sxs-lookup"><span data-stu-id="87450-124">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="87450-125">트리거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-125">Select trigger pressed</span></span> </td><td> <span data-ttu-id="87450-126">축 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-126">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="87450-127">축 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-127">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="87450-128">selectPressed</span><span class="sxs-lookup"><span data-stu-id="87450-128">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-129">아날로그 값 트리거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-129">Select trigger analog value</span></span> </td><td> <span data-ttu-id="87450-130">축 9</span><span class="sxs-lookup"><span data-stu-id="87450-130">Axis 9</span></span> </td><td> <span data-ttu-id="87450-131">축 10</span><span class="sxs-lookup"><span data-stu-id="87450-131">Axis 10</span></span> </td><td> <span data-ttu-id="87450-132">Select보도 금액</span><span class="sxs-lookup"><span data-stu-id="87450-132">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-133">부분적으로 누른 트리거 선택</span><span class="sxs-lookup"><span data-stu-id="87450-133">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="87450-134">단추 14 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-134">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="87450-135">단추 15 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-135">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="87450-136">Select보도 Sedamount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="87450-136">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-137">메뉴 단추 누름</span><span class="sxs-lookup"><span data-stu-id="87450-137">Menu button pressed</span></span> </td><td> <span data-ttu-id="87450-138">단추 6 \*</span><span class="sxs-lookup"><span data-stu-id="87450-138">Button 6\*</span></span> </td><td> <span data-ttu-id="87450-139">단추 7 \*</span><span class="sxs-lookup"><span data-stu-id="87450-139">Button 7\*</span></span> </td><td> <span data-ttu-id="87450-140">menuPressed</span><span class="sxs-lookup"><span data-stu-id="87450-140">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-141">그립 단추 누름</span><span class="sxs-lookup"><span data-stu-id="87450-141">Grip button pressed</span></span> </td><td> <span data-ttu-id="87450-142">축 11 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="87450-142">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="87450-143">단추 4 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-143">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="87450-144">축 12 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="87450-144">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="87450-145">단추 5 <i>(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-145">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="87450-146">grasped</span><span class="sxs-lookup"><span data-stu-id="87450-146">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-147">엄지 스틱 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-147">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="87450-148">축 1</span><span class="sxs-lookup"><span data-stu-id="87450-148">Axis 1</span></span> </td><td> <span data-ttu-id="87450-149">축 4</span><span class="sxs-lookup"><span data-stu-id="87450-149">Axis 4</span></span> </td><td> <span data-ttu-id="87450-150">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="87450-150">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-151">엄지 스틱 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-151">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="87450-152">축 2</span><span class="sxs-lookup"><span data-stu-id="87450-152">Axis 2</span></span> </td><td> <span data-ttu-id="87450-153">축 5</span><span class="sxs-lookup"><span data-stu-id="87450-153">Axis 5</span></span> </td><td> <span data-ttu-id="87450-154">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="87450-154">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-155">엄지 스틱 누름</span><span class="sxs-lookup"><span data-stu-id="87450-155">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="87450-156">단추 8</span><span class="sxs-lookup"><span data-stu-id="87450-156">Button 8</span></span> </td><td> <span data-ttu-id="87450-157">단추 9</span><span class="sxs-lookup"><span data-stu-id="87450-157">Button 9</span></span> </td><td> <span data-ttu-id="87450-158">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="87450-158">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-159">터치 패드 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-159">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="87450-160">축 17 \*</span><span class="sxs-lookup"><span data-stu-id="87450-160">Axis 17\*</span></span> </td><td> <span data-ttu-id="87450-161">축 19 \*</span><span class="sxs-lookup"><span data-stu-id="87450-161">Axis 19\*</span></span> </td><td> <span data-ttu-id="87450-162">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="87450-162">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-163">터치 패드 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="87450-163">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="87450-164">축 18 \*</span><span class="sxs-lookup"><span data-stu-id="87450-164">Axis 18\*</span></span> </td><td> <span data-ttu-id="87450-165">축 20 \*</span><span class="sxs-lookup"><span data-stu-id="87450-165">Axis 20\*</span></span> </td><td> <span data-ttu-id="87450-166">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="87450-166">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-167">터치 패드 작업</span><span class="sxs-lookup"><span data-stu-id="87450-167">Touchpad touched</span></span> </td><td> <span data-ttu-id="87450-168">단추 18 \*</span><span class="sxs-lookup"><span data-stu-id="87450-168">Button 18\*</span></span> </td><td> <span data-ttu-id="87450-169">단추 19 \*</span><span class="sxs-lookup"><span data-stu-id="87450-169">Button 19\*</span></span> </td><td> <span data-ttu-id="87450-170">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="87450-170">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-171">터치 패드 누름</span><span class="sxs-lookup"><span data-stu-id="87450-171">Touchpad pressed</span></span> </td><td> <span data-ttu-id="87450-172">단추 16 \*</span><span class="sxs-lookup"><span data-stu-id="87450-172">Button 16\*</span></span> </td><td> <span data-ttu-id="87450-173">단추 17 \*</span><span class="sxs-lookup"><span data-stu-id="87450-173">Button 17\*</span></span> </td><td> <span data-ttu-id="87450-174">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="87450-174">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-175">6DoF 그립 포즈 또는 포인터 포즈</span><span class="sxs-lookup"><span data-stu-id="87450-175">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="87450-176"><i>그립</i> 포즈만: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="87450-176"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="87450-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking. GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="87450-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="87450-178">전달 <i>그립</i> 또는 <i>포인터</i> 를 인수로 전달 합니다. sourcestate TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="87450-178">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="87450-179">sourceState</span><span class="sxs-lookup"><span data-stu-id="87450-179">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="87450-180">상태 추적</span><span class="sxs-lookup"><span data-stu-id="87450-180">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="87450-181"><i>MR 특정 API를 통해서만 사용할 수 있는 위치 정확도 및 원본 손실 위험</i> </span><span class="sxs-lookup"><span data-stu-id="87450-181"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="87450-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="87450-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="87450-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="87450-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="87450-184">이러한 단추/축 Id는 gamepads, Oculus Touch 및 OpenVR에서 사용 하는 매핑의 충돌로 인해 Unity에서 OpenVR에 사용 하는 Id와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-184">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="87450-185">그립 포즈 및 포인팅 포즈</span><span class="sxs-lookup"><span data-stu-id="87450-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="87450-186">Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="87450-187">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스, **그립 포즈** 및 **포인터 포즈** 에 대해 조사할 수 있는 두 가지 종류의 포즈를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="87450-188">그립 포즈 및 포인터 포즈 좌표는 모두 전역 Unity 세계 좌표의 모든 Unity Api에 의해 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-188">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="87450-189">그립 포즈</span><span class="sxs-lookup"><span data-stu-id="87450-189">Grip pose</span></span>

<span data-ttu-id="87450-190">**그립 포즈** 는 HoloLens에서 감지한 손바닥의 위치 또는 동작 컨트롤러를 보유 하는 야자나무를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-190">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="87450-191">몰입 형 헤드셋에서 그립 포즈는 사용자 **의 손을** 만들거나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-191">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="87450-192">동작 컨트롤러에 대해 Windows에서 제공 하는 **렌더링할 모델** 은 동작 컨트롤러를 시각화할 때에도 그립 포즈를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-192">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="87450-193">그립 포즈는 구체적으로 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-193">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="87450-194">**그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="87450-194">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="87450-195">Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 보통 클릭 단추와 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="87450-195">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="87450-196">**그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87450-196">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="87450-197">**그립 방향 전방 축: 핸들** 을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-197">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="87450-198">**그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-198">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="87450-199">Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 *[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) 또는 WINDOWS MR 특정 API (*sourcestate/Rotation*, **그립** 노드에 대 한 포즈 데이터 요청)를 통해</span><span class="sxs-lookup"><span data-stu-id="87450-199">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="87450-200">포인터 포즈</span><span class="sxs-lookup"><span data-stu-id="87450-200">Pointer pose</span></span>

<span data-ttu-id="87450-201">**포인터 포즈** 는 컨트롤러의 팁을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="87450-202">시스템 제공 포인터 포즈는 **컨트롤러 모델 자체를 렌더링** 하는 경우 raycast에 가장 잘 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-202">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="87450-203">컨트롤러 대신 다른 가상 개체 (예: 가상 사용자)를 렌더링 하는 경우 앱 정의 된 포 모델의 배럴을 따라 이동 하는 광선과 같이 해당 가상 개체에 가장 자연 스러운 광선을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-203">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="87450-204">사용자는 가상 개체를 볼 수 있고 실제 컨트롤러는 볼 수 없으므로 가상 개체를 가리키면 앱을 사용 하는 것이 더 자연스럽 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="87450-205">현재 포인터 포즈는 *InteractionSourceNode* 를 인수로 전달 하는 Windows MR 특정 API 인 *TryGetPosition/Rotation* 을 통해서만 Unity에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-205">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="87450-206">컨트롤러 추적 상태</span><span class="sxs-lookup"><span data-stu-id="87450-206">Controller tracking state</span></span>

<span data-ttu-id="87450-207">헤드셋 처럼 Windows Mixed Reality 동작 컨트롤러를 사용 하려면 외부 추적 센서를 설정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-207">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="87450-208">대신, 컨트롤러는 헤드셋 자체의 센서에 의해 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-208">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="87450-209">사용자가 컨트롤러를 헤드셋의 뷰 필드에서 밖으로 이동 하는 경우 대부분의 경우 Windows는 컨트롤러 위치를 계속 유추 하 고 앱에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-209">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="87450-210">컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-210">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="87450-211">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-211">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="87450-212">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-212">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="87450-213">이를 위한 가장 좋은 방법은 직접 시도해 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-213">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="87450-214">다양 한 추적 상태에서 동작 컨트롤러와 함께 작동 하는 몰입 형 콘텐츠 예제를 통해이 비디오를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="87450-214">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="87450-215">명시적 추적 상태에 대 한 추론</span><span class="sxs-lookup"><span data-stu-id="87450-215">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="87450-216">추적 상태에 따라 위치를 다르게 처리 하려는 앱은 더 나아가 컨트롤러의 상태에 대 한 속성 (예: *SourceLossRisk* 및 *positionaccuracy*)을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-216">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="87450-217">상태 추적</span><span class="sxs-lookup"><span data-stu-id="87450-217">Tracking state</span></span> </th><th> <span data-ttu-id="87450-218">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="87450-218">SourceLossRisk</span></span> </th><th> <span data-ttu-id="87450-219">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="87450-219">PositionAccuracy</span></span> </th><th> <span data-ttu-id="87450-220">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="87450-220">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="87450-221"><b>높은 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="87450-221"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="87450-222">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-222">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="87450-223">높음</span><span class="sxs-lookup"><span data-stu-id="87450-223">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="87450-224">true</span><span class="sxs-lookup"><span data-stu-id="87450-224">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-225"><b>높은 정확도 (손실 위험)</b> </span><span class="sxs-lookup"><span data-stu-id="87450-225"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="87450-226">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-226">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="87450-227">높음</span><span class="sxs-lookup"><span data-stu-id="87450-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="87450-228">true</span><span class="sxs-lookup"><span data-stu-id="87450-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-229"><b>대략적인 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="87450-229"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="87450-230">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-230">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="87450-231">근사치</span><span class="sxs-lookup"><span data-stu-id="87450-231">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="87450-232">true</span><span class="sxs-lookup"><span data-stu-id="87450-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="87450-233"><b>위치 없음</b> </span><span class="sxs-lookup"><span data-stu-id="87450-233"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="87450-234">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="87450-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="87450-235">근사치</span><span class="sxs-lookup"><span data-stu-id="87450-235">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="87450-236">false</span><span class="sxs-lookup"><span data-stu-id="87450-236">false</span></span></td>
</tr>
</table>

<span data-ttu-id="87450-237">이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-237">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="87450-238">**높은 정확도:** 동작 컨트롤러는 헤드셋의 보기 필드 내에 있지만 일반적으로 시각적 추적에 따라 정확도가 높은 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-238">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="87450-239">일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려진 이동 컨트롤러 (예: 사용자)는 컨트롤러 자체의 관성 추적을 기반으로 짧은 시간 동안 계속 해 서 정확도가 높은 동작을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-239">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="87450-240">**높은 정확도 (손실 위험):** 사용자가 이동 컨트롤러를 헤드셋의 보기 필드 가장자리를 지나서 이동할 때 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-240">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="87450-241">앱은 **SourceLossRisk** reach 1.0을 확인 하 여 컨트롤러가이 FOV 경계에 도달한 경우를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-241">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="87450-242">이 시점에서 앱은 매우 높은 품질의 동작을 안정적으로 스트리밍하는 데 필요한 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-242">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="87450-243">**대략적인 정확도:** 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-243">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="87450-244">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="87450-245">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-245">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="87450-246">입력 요구 사항이 많은 앱은 사용자에 게이 시간 동안 오프 화면 대상에 대 한 hitbox을 제공 하는 등의 방법으로 **positionaccuracy** 속성을 검사 하 여 정확도가 **높은** **정확도부터 정확도까지** 이러한 삭제를 합리적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-246">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="87450-247">**위치 없음:** 컨트롤러는 오랜 시간 동안 정확한 정확도로 작동할 수 있지만 때때로 본문 잠금 위치가 중요 하지 않은 것을 시스템에서 인식 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-247">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="87450-248">예를 들어 방금 설정 된 컨트롤러가 시각적으로 관찰 되지 않았거나 사용자가 다른 사용자가 선택 하는 컨트롤러를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-248">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="87450-249">이러한 시간에 시스템은 앱에 어떤 위치도 제공 하지 않으며 *TryGetPosition* 는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-249">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="87450-250">Common Unity Api (입력. GetButton/Getbutton)</span><span class="sxs-lookup"><span data-stu-id="87450-250">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="87450-251">**네임 스페이스:** *unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="87450-251">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="87450-252">**형식**: *Input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="87450-252">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="87450-253">Unity는 현재 일반 입력을 사용 *합니다. GetButton/Input. Getbutton* api를 사용 하면 핸드 및 동작 컨트롤러를 포함 하 여 [oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html), [Openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality의 입력을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-253">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="87450-254">앱이 입력에 이러한 Api를 사용 하는 경우 Windows Mixed Reality를 비롯 하 여 여러 XR Sdk에서 동작 컨트롤러를 쉽게 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-254">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="87450-255">논리적 단추의 누름 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="87450-255">Getting a logical button's pressed state</span></span>

<span data-ttu-id="87450-256">일반 Unity 입력 Api를 사용 하려면 일반적으로 [Unity 입력 관리자](https://docs.unity3d.com/Manual/ConventionalGameInput.html)에서 단추와 축을 논리적 이름에 연결 하 여 단추 또는 축 id를 각 이름에 바인딩하는 것으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-256">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="87450-257">그런 다음 해당 논리적 단추/축 이름을 참조 하는 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-257">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="87450-258">예를 들어 왼쪽 동작 컨트롤러의 트리거 단추를 전송 작업에 매핑하려면 **> 프로젝트 설정 편집** 으로 이동 하 여 Unity 내에서 입력 > 하 고 축 아래에서 제출 섹션의 속성을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-258">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="87450-259">**긍정 단추** 또는 **Alt 긍정 단추** 속성을 다음과 같이 **조이스틱 단추 14** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-259">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="87450-260">![Unity의 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="87450-260">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="87450-261">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="87450-261">*Unity InputManager*</span></span>

<span data-ttu-id="87450-262">그런 다음 스크립트는 입력을 사용 하 여 전송 작업을 확인할 수 있습니다 *. GetButton*:</span><span class="sxs-lookup"><span data-stu-id="87450-262">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="87450-263">**축** 에서 **크기** 속성을 변경 하 여 논리적 단추를 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-263">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="87450-264">물리적 단추의 누름 상태를 직접 가져오기</span><span class="sxs-lookup"><span data-stu-id="87450-264">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="87450-265">*입력. GetKey* 를 사용 하 여 정규화 된 이름으로 수동으로 단추에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-265">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="87450-266">직접 또는 동작 컨트롤러의 포즈 가져오기</span><span class="sxs-lookup"><span data-stu-id="87450-266">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="87450-267">XR를 사용 하 여 컨트롤러의 위치 및 회전에 액세스할 수 있습니다 *. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="87450-267">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="87450-268">이는 컨트롤러의 그립 포즈 (사용자가 컨트롤러를 보유 하는 위치)를 나타내며 사용자의 손을 사용 하거나 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-268">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="87450-269">이 그립 포즈와 포인터 포즈 (컨트롤러의 팁) 간의 관계는 컨트롤러 마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-269">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="87450-270">이제 컨트롤러의 포인터 포즈에 액세스 하는 것은 아래 섹션에 설명 된 MR 특정 입력 API를 통해서만 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-270">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="87450-271">Windows 관련 Api (XR. WSA. 입력</span><span class="sxs-lookup"><span data-stu-id="87450-271">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="87450-272">프로젝트에서 XR를 사용 하는 경우 WSA Api는 향후 Unity 릴리스의 XR SDK에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-272">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="87450-273">새 프로젝트의 경우 처음부터 XR SDK를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-273">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="87450-274">[XR 입력 시스템 및 api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-274">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="87450-275">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="87450-275">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="87450-276">**유형**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="87450-276">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="87450-277">Windows Mixed Reality 입력 (HoloLens 용) 및 동작 컨트롤러에 대 한 자세한 정보를 보려면 *Unityengine. XR* 네임 스페이스에서 windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-277">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="87450-278">이를 통해 위치 정확도 나 소스 종류와 같은 추가 정보에 액세스할 수 있으므로 실습 및 컨트롤러를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-278">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="87450-279">직접 및 동작 컨트롤러의 상태 폴링</span><span class="sxs-lookup"><span data-stu-id="87450-279">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="87450-280">*GetCurrentReading* 메서드를 사용 하 여 각 상호 작용 소스 (직접 또는 동작 컨트롤러)에 대해이 프레임의 상태를 폴링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-280">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="87450-281">가져오는 각 *InteractionSourceState* 는 현재 시점에서 상호 작용 소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-281">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="87450-282">*InteractionSourceState* 는 다음과 같은 정보를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-282">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="87450-283">어떤 [종류의 누름](../../design/motion-controllers.md) 이 발생 합니까 (선택/메뉴/-/터치 패드/엄지 스틱)</span><span class="sxs-lookup"><span data-stu-id="87450-283">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="87450-284">터치 패드 및/또는 엄지 스틱 XY 좌표 및 작업 된 상태와 같은 동작 컨트롤러에 해당 하는 기타 데이터</span><span class="sxs-lookup"><span data-stu-id="87450-284">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="87450-285">InteractionSourceKind는 원본이 나 동작 컨트롤러 인지 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-285">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="87450-286">앞으로 예측 된 렌더링 동작에 대 한 폴링</span><span class="sxs-lookup"><span data-stu-id="87450-286">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="87450-287">손이 나 컨트롤러에서 상호 작용 원본 데이터를 폴링하는 경우이 프레임의 photons 사용자의 눈에 도달 하 게 되는 순간에 대해 앞으로 예측 하는 포즈를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-287">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="87450-288">이러한 앞으로 예측 된 포즈는 컨트롤러를 **렌더링** 하거나 각 프레임을 보유 한 개체를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-288">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="87450-289">컨트롤러를 사용 하 여 지정 된 보도 또는 릴리스를 대상으로 하는 경우 아래에 설명 된 기록 이벤트 Api를 사용 하는 경우 가장 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-289">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="87450-290">이 현재 프레임에 대해 앞으로 예측 한 헤드 포즈를 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-290">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="87450-291">원본 포즈와 마찬가지로,이 기능은 커서를 **렌더링** 하는 데 유용 합니다. 단, 아래에 설명 된 기록 이벤트 api를 사용 하는 경우에는 지정 된 누름 또는 릴리스를 대상으로 하는 것이 가장 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-291">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="87450-292">상호 작용 소스 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="87450-292">Handling interaction source events</span></span>

<span data-ttu-id="87450-293">정확한 기록 포즈 데이터에서 발생 하는 입력 이벤트를 처리 하기 위해 폴링 대신 상호 작용 소스 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-293">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="87450-294">상호 작용 소스 이벤트를 처리 하려면:</span><span class="sxs-lookup"><span data-stu-id="87450-294">To handle interaction source events:</span></span>
* <span data-ttu-id="87450-295">*InteractionManager* 입력 이벤트에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-295">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="87450-296">관심이 있는 각 상호 작용 이벤트 형식에 대해 구독 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-296">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="87450-297">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-297">Handle the event.</span></span> <span data-ttu-id="87450-298">상호 작용 이벤트를 구독 한 후에는 해당 하는 경우 콜백을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-298">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="87450-299">*Sourcepressed* 예제에서는 소스가 검색 된 후와 릴리스 또는 손실 되기 전에이 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-299">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="87450-300">이벤트 처리를 중지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="87450-300">How to stop handling an event</span></span>

<span data-ttu-id="87450-301">이벤트에 더 이상 관심이 없거나 이벤트를 구독 하는 개체를 삭제 하려는 경우에는 이벤트 처리를 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-301">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="87450-302">이벤트 처리를 중지 하려면 이벤트의 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-302">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="87450-303">상호 작용 소스 이벤트 목록</span><span class="sxs-lookup"><span data-stu-id="87450-303">List of interaction source events</span></span>

<span data-ttu-id="87450-304">사용할 수 있는 상호 작용 소스 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-304">The available interaction source events are:</span></span>
* <span data-ttu-id="87450-305">*InteractionSourceDetected* (원본이 활성화 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="87450-305">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="87450-306">*InteractionSourceLost* (비활성 상태가 됨)</span><span class="sxs-lookup"><span data-stu-id="87450-306">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="87450-307">*InteractionSourcePressed* (누르기, 단추 누르기 또는 "Select" 재생)</span><span class="sxs-lookup"><span data-stu-id="87450-307">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="87450-308">*InteractionSourceReleased* (탭의 끝, 단추 해제 또는 "Select" 재생 끝)</span><span class="sxs-lookup"><span data-stu-id="87450-308">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="87450-309">*InteractionSourceUpdated* (다른 상태를 이동 하거나 변경 하지 않음)</span><span class="sxs-lookup"><span data-stu-id="87450-309">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="87450-310">기록 대상 이벤트는 누름 또는 릴리스와 가장 정확 하 게 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-310">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="87450-311">앞에서 설명한 폴링 Api는 앱을 앞으로 예측 하는 포즈를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-311">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="87450-312">이러한 예측 된 포즈는 컨트롤러 또는 가상 핸드헬드 개체를 렌더링 하는 데 가장 적합 하지만 다음 두 가지 주요 이유로 이후 포즈는 대상 지정에 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-312">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="87450-313">사용자가 컨트롤러의 단추를 누르면 시스템이 press를 받기 전에 Bluetooth를 통해 무선 대기 시간이 20ms 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-313">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="87450-314">그런 다음 앞으로 예측 하는 포즈를 사용 하는 경우 현재 프레임의 photons가 사용자의 눈에 도달 하는 시간을 대상으로 하는 20ms 예측의 또 다른 10 개를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-314">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="87450-315">즉, 폴링을 통해 사용자의 헤드 및 손을 사용 하는 경우에는 사용자의 헤드를 30-40ms로 나타내는 소스 포즈 또는 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-315">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="87450-316">HoloLens 손으로 입력 한 경우 무선 전송 지연이 발생 하지 않지만, 누르기를 검색 하는 데 비슷한 처리 지연이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-316">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="87450-317">직접 또는 컨트롤러에 대 한 사용자의 원래 의도에 따라 정확 하 게 대상으로 지정 하려면 해당 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력 이벤트에서 기록 원본 포즈 또는 head 포즈를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-317">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="87450-318">사용자의 헤드 또는 해당 컨트롤러에서 기록 포즈 데이터를 사용 하 여 보도를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-318">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="87450-319">사용자가 [gazing](../../design/gaze-and-commit.md) 된 항목을 확인 하기 위해 **대상 지정** 에 사용할 수 있는 제스처 또는 컨트롤러를 누를 때 발생 하는 시점의 헤드입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-319">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="87450-320">이동 컨트롤러를 사용 하 여 사용자가 컨트롤러를 가리킨 **항목을 확인 하는** 데 사용 될 수 있는 시점에 발생 하는 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-320">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="87450-321">이는 누름이 발생 한 컨트롤러의 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-321">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="87450-322">컨트롤러 자체를 렌더링 하는 경우에는 핸들 포즈 대신 포인터 포즈를 요청 하 여 사용자가 렌더링 된 컨트롤러의 자연 스러운 팁을 고려 하는 대상 광선을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-322">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="87450-323">이벤트 처리기 예</span><span class="sxs-lookup"><span data-stu-id="87450-323">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="87450-324">상위 수준 복합 제스처 Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="87450-324">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="87450-325">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="87450-325">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="87450-326">**유형**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="87450-326">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="87450-327">앱은 공간 입력 원본, 탭, 유지, 조작 및 탐색 제스처에 대 한 상위 수준 복합 제스처를 인식할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-327">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="87450-328">GestureRecognizer를 사용 하 여 [직접](../../design/gaze-and-commit.md#composite-gestures) 및 [동작 컨트롤러](../../design/motion-controllers.md) 에서 이러한 복합 제스처를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-328">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="87450-329">GestureRecognizer의 각 제스처 이벤트는 입력에 대 한 SourceKind와 이벤트 시점의 대상 헤드 광선을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-329">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="87450-330">일부 이벤트는 추가 컨텍스트별 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-330">Some events provide additional context specific information.</span></span>

<span data-ttu-id="87450-331">제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-331">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="87450-332">새 제스처 인식기 만들기</span><span class="sxs-lookup"><span data-stu-id="87450-332">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="87450-333">감시할 제스처 지정</span><span class="sxs-lookup"><span data-stu-id="87450-333">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="87450-334">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="87450-334">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="87450-335">제스처 캡처 시작</span><span class="sxs-lookup"><span data-stu-id="87450-335">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="87450-336">새 제스처 인식기 만들기</span><span class="sxs-lookup"><span data-stu-id="87450-336">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="87450-337">*GestureRecognizer* 를 사용 하려면 *GestureRecognizer* 를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-337">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="87450-338">감시할 제스처 지정</span><span class="sxs-lookup"><span data-stu-id="87450-338">Specify which gestures to watch for</span></span>

<span data-ttu-id="87450-339">*SetRecognizableGestures ()* 를 통해 관심 있는 제스처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-339">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="87450-340">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="87450-340">Subscribe to events for those gestures</span></span>

<span data-ttu-id="87450-341">관심이 있는 제스처에 대 한 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-341">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="87450-342">탐색 및 조작 제스처는 *GestureRecognizer* 의 인스턴스에서 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-342">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="87450-343">제스처 캡처 시작</span><span class="sxs-lookup"><span data-stu-id="87450-343">Start capturing gestures</span></span>

<span data-ttu-id="87450-344">기본적으로 *GestureRecognizer* 는 *Startcapturinggestures ()* 를 호출할 때까지 입력을 모니터링 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-344">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="87450-345">*Stopcapturinggestures ()* 가 처리 된 프레임 보다 먼저 입력이 수행 되 면 *Stopcap의 ing제스처 ()* 가 호출 된 후에 제스처 이벤트가 생성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-345">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="87450-346">*GestureRecognizer* 는 제스처가 실제로 발생 한 이전 프레임의 설정 또는 해제 여부를 기억할 것 이므로이 프레임의 응시 대상에 따라 제스처 모니터링을 시작 및 중지 하는 것은 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-346">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="87450-347">제스처 캡처 중지</span><span class="sxs-lookup"><span data-stu-id="87450-347">Stop capturing gestures</span></span>

<span data-ttu-id="87450-348">제스처 인식을 중지 하려면:</span><span class="sxs-lookup"><span data-stu-id="87450-348">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="87450-349">제스처 인식기 제거</span><span class="sxs-lookup"><span data-stu-id="87450-349">Removing a gesture recognizer</span></span>

<span data-ttu-id="87450-350">*GestureRecognizer* 개체를 삭제 하기 전에 구독 이벤트의 구독을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-350">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="87450-351">Unity에서 동작 컨트롤러 모델 렌더링</span><span class="sxs-lookup"><span data-stu-id="87450-351">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="87450-352">![동작 컨트롤러 모델 및 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="87450-352">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="87450-353">*동작 컨트롤러 모델 및 teleportation*</span><span class="sxs-lookup"><span data-stu-id="87450-353">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="87450-354">응용 프로그램에서 사용자가 보유 하 고 있는 실제 컨트롤러와 일치 하는 동작 컨트롤러를 렌더링 하려면 [혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/)에서 **motioncontroller prefab** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-354">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="87450-355">이 prefab는 시스템의 설치 된 동작 컨트롤러 드라이버에서 런타임에 올바른 인 글 Tf 모델을 동적으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-355">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="87450-356">편집기에서 수동으로 가져오는 대신 이러한 모델을 동적으로 로드 하는 것이 중요 합니다. 따라서 앱은 사용자에 게 있을 수 있는 현재 및 미래의 모든 컨트롤러에 대해 물리적으로 정확한 3D 모델을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-356">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="87450-357">[시작](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 지침에 따라 Mixed Reality Toolkit를 다운로드 하 여 Unity 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-357">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="87450-358">시작 단계의 일부로 카메라를 *MixedRealityCameraParent* prefab로 대체 한 경우에는 계속 진행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-358">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="87450-359">이 prefab에는 동작 컨트롤러 렌더링이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-359">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="87450-360">그렇지 않으면 프로젝트 창에서 장면에 asset */HoloToolkit/Input/Prefabs/MotionControllers. prefab* 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-360">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="87450-361">사용자가 장면 내에서 teleports 때 카메라를 이동 하는 데 사용 하는 모든 부모 개체의 자식으로 해당 prefab을 추가 하 여 컨트롤러를 사용자와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-361">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="87450-362">앱에 teleporting 포함 되지 않은 경우 장면의 루트에 prefab를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-362">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="87450-363">개체 throw</span><span class="sxs-lookup"><span data-stu-id="87450-363">Throwing objects</span></span>

<span data-ttu-id="87450-364">가상 현실에서 개체를 throw 하는 것은 어려운 문제 이며, 처음에는 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-364">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="87450-365">대부분의 물리적 기반 상호 작용의 경우와 마찬가지로 게임에서 throw 되는 것이 예기치 않은 방식으로 작동 하는 경우에는 즉시 명확 하 고 집중 교육 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-365">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="87450-366">실제로 올바른 throw 동작을 나타내는 방법에 대해 자세히 살펴보고, 플랫폼 업데이트를 통해 사용할 수 있는 몇 가지 지침을 제공 하 여 사용자와 공유 하 고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-366">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="87450-367">[여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)에서 throw를 구현 하는 방법에 대 한 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-367">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="87450-368">이 샘플은 다음 네 가지 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="87450-368">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="87450-369">**위치 대신 컨트롤러의 *속도* 를 사용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-369">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="87450-370">11 월 Windows 업데이트에서는 [' ' 근사치 ' ' 위치 추적 상태](../../design/motion-controllers.md#controller-tracking-state)에 있는 경우 동작이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-370">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="87450-371">이 상태에서 컨트롤러에 대 한 속도 정보는 정확도가 높은 것으로 예상 되는 경우에도 계속 보고 됩니다 .이는 일반적으로 높은 정확도를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-371">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="87450-372">**컨트롤러의 *각도 속도* 를 통합** 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-372">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="87450-373">이 논리는 `throwing.cs` `GetThrownObjectVelAngVel` 위에 링크 된 패키지 내의 정적 메서드에 있는 파일에 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-373">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="87450-374">각도 속도가 conserved throw 된 개체는 throw 시점에 있었던 것과 동일한 각도의 속도를 유지 해야 합니다. `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="87450-374">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="87450-375">Throw 된 개체의 질량 중심은 그립 포즈의 원점에 있지 않을 수 있으므로 사용자 참조 프레임의 컨트롤러와 다른 속도를 가질 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-375">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="87450-376">이러한 방식으로 제공 되는 개체 속도의 부분은 컨트롤러 원본 주위에서 throw 된 개체의 질량 중심의 순간 탄젠트 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-376">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="87450-377">이 탄젠트 속도는 컨트롤러 원본 및 throw 된 개체의 질량 중심 사이의 거리를 나타내는 벡터와 컨트롤러의 각도 속도 간 곱입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-377">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="87450-378">따라서 throw 된 개체의 총 속도는 컨트롤러의 속도와 이러한 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="87450-378">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="87450-379">**속도를 적용 하는 *시간* 에 대 한 주의를** 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-379">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="87450-380">단추를 누르면 해당 이벤트가 Bluetooth를 통해 운영 체제에 20ms 최대의 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-380">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="87450-381">즉, 컨트롤러 상태 변경을 누른 상태에서 누르지 않음 또는 그 반대로 폴링할 때 발생 하는 컨트롤러의 정보는 실제로 이러한 변화에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="87450-381">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="87450-382">또한 폴링 API에 의해 표시 되는 컨트롤러는 프레임이 표시 될 때 발생할 수 있는 포즈를 반영 하 여 향후 20ms 될 수 있는 것으로 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-382">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="87450-383">이는 보류 중인 개체를 *렌더링* 하는 데 유용 하지만 사용자가 throw를 릴리스한 순간의 궤적을 계산할 때 개체를 *대상으로 지정* 하는 데 시간이 복합어.</span><span class="sxs-lookup"><span data-stu-id="87450-383">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="87450-384">다행히 11 월 업데이트를 사용 하는 경우 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 와 같은 Unity 이벤트가 전송 되 면이 상태에는 단추가 실제로 눌러져 있거나 해제 되었을 때의 기록 포즈 데이터가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-384">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="87450-385">을 throw 하는 동안 가장 정확한 컨트롤러 렌더링과 컨트롤러를 대상으로 하려면 적절 한 폴링 및 이벤트를 올바르게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-385">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="87450-386">각 프레임을 렌더링 하는 **컨트롤러** 의 경우 응용 프로그램은 현재 프레임의 photon 시간에 대해 앞으로 예측 되는 컨트롤러에서 컨트롤러의 *GameObject* 위치를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-386">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="87450-387">Unity 폴링 Api (예: XR)에서이 데이터를 가져옵니다 *[. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 또는 *[XR. WSA. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="87450-387">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="87450-388">Press 또는 릴리스부터 **컨트롤러를 대상** 으로 하는 경우 앱은 해당 누르기 또는 릴리스 이벤트에 대 한 기록 컨트롤러의 포즈를 기준으로 궤적을 ray로 계산 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-388">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="87450-389">*[InteractionManager InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 와 같은 Unity 이벤트 api에서이 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87450-389">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="87450-390">**그립 포즈를 사용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-390">**Use the grip pose**.</span></span> <span data-ttu-id="87450-391">각도 속도와 속도는 포인터가 아닌 그립 포즈를 기준으로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-391">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="87450-392">Throw는 향후 Windows 업데이트를 사용 하 여 계속 개선 되며 여기에서 자세한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-392">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="87450-393">MRTK v2의 제스처 및 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="87450-393">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="87450-394">입력 관리자에서 제스처 및 동작 컨트롤러에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-394">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="87450-395">MRTK v2의 제스처</span><span class="sxs-lookup"><span data-stu-id="87450-395">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="87450-396">MRTK v2의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="87450-396">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="87450-397">안내 따르기</span><span class="sxs-lookup"><span data-stu-id="87450-397">Follow along with tutorials</span></span>

<span data-ttu-id="87450-398">보다 자세한 사용자 지정 예제가 포함 된 단계별 자습서는 혼합 현실 아카데미에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87450-398">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="87450-399">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="87450-399">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="87450-400">MR 입력 213: 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="87450-400">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="87450-401">[![MR 입력 213-동작 컨트롤러](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="87450-401">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="87450-402">*MR 입력 213-동작 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="87450-402">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="87450-403">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="87450-403">Next Development Checkpoint</span></span>

<span data-ttu-id="87450-404">앞에서 설명한 Unity 개발 검사점 경험을 수행하는 경우 MRTK 핵심 구성 요소를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-404">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="87450-405">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-405">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87450-406">손 및 시선 추적</span><span class="sxs-lookup"><span data-stu-id="87450-406">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="87450-407">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="87450-407">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87450-408">공유 환경</span><span class="sxs-lookup"><span data-stu-id="87450-408">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="87450-409">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87450-409">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="87450-410">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87450-410">See also</span></span>

* [<span data-ttu-id="87450-411">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="87450-411">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="87450-412">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="87450-412">Motion controllers</span></span>](../../design/motion-controllers.md)
