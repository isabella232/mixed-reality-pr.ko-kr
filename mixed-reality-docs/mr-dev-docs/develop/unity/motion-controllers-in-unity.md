---
title: Unity의 모션 컨트롤러
description: XR 및 공통 단추 및 축 API를 사용하여 모션 컨트롤러 입력을 사용하여 Unity에서 응시에 대한 조치를 취하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 모션 컨트롤러, unity, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394517"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="0a69f-104">Unity의 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="0a69f-104">Motion controllers in Unity</span></span>

<span data-ttu-id="0a69f-105">HoloLens 및 몰입형 HMD에서 Unity , [손 제스처](../../design/gaze-and-commit.md#composite-gestures) 및 [모션 컨트롤러의](../../design/motion-controllers.md) [응시에](gaze-in-unity.md)대한 작업을 수행하려면 두 가지 주요 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="0a69f-106">Unity에서 동일한 API를 통해 공간 입력의 두 원본에 대한 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="0a69f-107">Unity는 Windows Mixed Reality 공간 입력 데이터에 액세스하는 두 가지 기본 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="0a69f-108">일반적인 *Input.GetButton/Input.GetAxis* API는 여러 Unity XR SDK에서 작동하지만, Windows Mixed Reality 특정 *InteractionManager/GestureRecognizer* API는 공간 입력 데이터의 전체 집합을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="0a69f-109">Unity XR 입력 API</span><span class="sxs-lookup"><span data-stu-id="0a69f-109">Unity XR input APIs</span></span>

<span data-ttu-id="0a69f-110">새 프로젝트의 경우 처음부터 새 XR 입력 API를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="0a69f-111">[XR API에](https://docs.unity3d.com/Manual/xr_input.html)대한 자세한 내용은 에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="0a69f-112">Unity 단추/축 매핑 테이블</span><span class="sxs-lookup"><span data-stu-id="0a69f-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="0a69f-113">Unity의 Windows Mixed Reality 동작 컨트롤러용 Input Manager는 *Input.GetButton/GetAxis* API를 통해 아래에 나열된 단추 및 축 ID를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="0a69f-114">"Windows MR 관련" 열은 *InteractionSourceState* 형식에서 사용할 수 있는 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="0a69f-115">이러한 각 API는 아래 섹션에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="0a69f-116">Windows Mixed Reality 대한 단추/축 ID 매핑은 일반적으로 Oculus 단추/축 ID와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="0a69f-117">Windows Mixed Reality 대한 단추/축 ID 매핑은 다음 두 가지 방법으로 OpenVR의 매핑과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="0a69f-118">매핑은 엄지스틱과 구별되는 터치 패드 ID를 사용하여 엄지스틱과 터치패드를 모두 사용하는 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="0a69f-119">매핑은 메뉴 단추에 대한 A 및 X 단추의 ID를 오버로드하여 실제 ABXY 단추에 사용할 수 있도록 하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="0a69f-120">입력</span><span class="sxs-lookup"><span data-stu-id="0a69f-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="0a69f-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="0a69f-122">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="0a69f-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="0a69f-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 관련 입력 API</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="0a69f-124">(XR. Wsa. 입력)</span><span class="sxs-lookup"><span data-stu-id="0a69f-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="0a69f-125">왼손</span><span class="sxs-lookup"><span data-stu-id="0a69f-125">Left hand</span></span> </th><th> <span data-ttu-id="0a69f-126">오른쪽</span><span class="sxs-lookup"><span data-stu-id="0a69f-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0a69f-127">트리거 누른 선택</span><span class="sxs-lookup"><span data-stu-id="0a69f-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="0a69f-128">축 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="0a69f-129">축 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="0a69f-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="0a69f-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-131">트리거 아날로그 값 선택</span><span class="sxs-lookup"><span data-stu-id="0a69f-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="0a69f-132">축 9</span><span class="sxs-lookup"><span data-stu-id="0a69f-132">Axis 9</span></span> </td><td> <span data-ttu-id="0a69f-133">축 10</span><span class="sxs-lookup"><span data-stu-id="0a69f-133">Axis 10</span></span> </td><td> <span data-ttu-id="0a69f-134">SelectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="0a69f-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-135">트리거를 부분적으로 누른 경우 선택</span><span class="sxs-lookup"><span data-stu-id="0a69f-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="0a69f-136">단추 <i>14(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0a69f-137">단추 <i>15(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0a69f-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-139">메뉴 단추를 눌렀습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="0a69f-140">단추 6\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-140">Button 6\*</span></span> </td><td> <span data-ttu-id="0a69f-141">단추 7\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-141">Button 7\*</span></span> </td><td> <span data-ttu-id="0a69f-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="0a69f-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-143">그립 단추를 눌렀습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="0a69f-144">축 11 = 1.0(아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="0a69f-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0a69f-145">단추 <i>4(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0a69f-146">축 12 = 1.0(아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="0a69f-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0a69f-147">단추 <i>5(게임 패드 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0a69f-148">파악</span><span class="sxs-lookup"><span data-stu-id="0a69f-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-149">Thumbstick <i>X(왼쪽: -1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0a69f-150">축 1</span><span class="sxs-lookup"><span data-stu-id="0a69f-150">Axis 1</span></span> </td><td> <span data-ttu-id="0a69f-151">축 4</span><span class="sxs-lookup"><span data-stu-id="0a69f-151">Axis 4</span></span> </td><td> <span data-ttu-id="0a69f-152">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="0a69f-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-153">Thumbstick <i>Y(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0a69f-154">축 2</span><span class="sxs-lookup"><span data-stu-id="0a69f-154">Axis 2</span></span> </td><td> <span data-ttu-id="0a69f-155">축 5</span><span class="sxs-lookup"><span data-stu-id="0a69f-155">Axis 5</span></span> </td><td> <span data-ttu-id="0a69f-156">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="0a69f-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-157">Thumbstick 누른 경우</span><span class="sxs-lookup"><span data-stu-id="0a69f-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="0a69f-158">단추 8</span><span class="sxs-lookup"><span data-stu-id="0a69f-158">Button 8</span></span> </td><td> <span data-ttu-id="0a69f-159">단추 9</span><span class="sxs-lookup"><span data-stu-id="0a69f-159">Button 9</span></span> </td><td> <span data-ttu-id="0a69f-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="0a69f-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-161">터치 패드 <i>X(왼쪽: -1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0a69f-162">축 17\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="0a69f-163">축 19\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="0a69f-164">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="0a69f-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-165">터치 패드 <i>Y(위쪽: -1.0, 아래쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0a69f-166">축 18\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="0a69f-167">축 20\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="0a69f-168">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="0a69f-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-169">터치 패드 터치</span><span class="sxs-lookup"><span data-stu-id="0a69f-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="0a69f-170">단추 18\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-170">Button 18\*</span></span> </td><td> <span data-ttu-id="0a69f-171">단추 19\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-171">Button 19\*</span></span> </td><td> <span data-ttu-id="0a69f-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="0a69f-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-173">터치 패드 누른</span><span class="sxs-lookup"><span data-stu-id="0a69f-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="0a69f-174">단추 16\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-174">Button 16\*</span></span> </td><td> <span data-ttu-id="0a69f-175">단추 17\*</span><span class="sxs-lookup"><span data-stu-id="0a69f-175">Button 17\*</span></span> </td><td> <span data-ttu-id="0a69f-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="0a69f-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-177">6DoF 그립 자세 또는 포인터 자세</span><span class="sxs-lookup"><span data-stu-id="0a69f-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="0a69f-178"><i>그립</i> 자세만: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="0a69f-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="0a69f-180"><i>그립</i> 또는 <i>포인터를</i> 인수로 전달: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0a69f-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="0a69f-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="0a69f-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-182">추적 상태</span><span class="sxs-lookup"><span data-stu-id="0a69f-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="0a69f-183"><i>MR별 API를 통해서만 사용할 수 있는 위치 정확도 및 원본 손실 위험</i> </span><span class="sxs-lookup"><span data-stu-id="0a69f-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="0a69f-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="0a69f-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="0a69f-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="0a69f-186">이러한 단추/축 ID는 게임 패드, Oculus Touch 및 OpenVR에서 사용하는 매핑의 충돌로 인해 Unity에서 OpenVR에 사용하는 ID와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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

### <a name="openxr"></a><span data-ttu-id="0a69f-187">OpenXR</span><span class="sxs-lookup"><span data-stu-id="0a69f-187">OpenXR</span></span>

<span data-ttu-id="0a69f-188">Unity의 혼합 현실 상호 작용에 대한 기본 사항 알아보려면 Unity [XR 입력에 대한 Unity 설명서를 참조하세요.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="0a69f-188">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="0a69f-189">이 Unity 설명서에서는 컨트롤러별 입력에서 보다 일반적인 **InputFeatureUsage로의** 매핑, 사용 가능한 XR 입력을 식별하고 분류하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-189">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="0a69f-190">Mixed Reality OpenXR 플러그 인은 아래에 설명된 대로 표준 **InputFeatureUsage에** 매핑된 추가 입력 상호 작용 프로필을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-190">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="0a69f-191">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="0a69f-191">InputFeatureUsage</span></span> | <span data-ttu-id="0a69f-192">HP Reverb G2 컨트롤러(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="0a69f-192">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="0a69f-193">HoloLens Hand(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="0a69f-193">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="0a69f-194">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="0a69f-194">primary2DAxis</span></span> | <span data-ttu-id="0a69f-195">조이스틱</span><span class="sxs-lookup"><span data-stu-id="0a69f-195">Joystick</span></span> | |
| <span data-ttu-id="0a69f-196">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="0a69f-196">primary2DAxisClick</span></span> | <span data-ttu-id="0a69f-197">운정 - 클릭</span><span class="sxs-lookup"><span data-stu-id="0a69f-197">Joystick - Click</span></span> | |
| <span data-ttu-id="0a69f-198">트리거</span><span class="sxs-lookup"><span data-stu-id="0a69f-198">trigger</span></span> | <span data-ttu-id="0a69f-199">트리거</span><span class="sxs-lookup"><span data-stu-id="0a69f-199">Trigger</span></span>  | |
| <span data-ttu-id="0a69f-200">그립</span><span class="sxs-lookup"><span data-stu-id="0a69f-200">grip</span></span> | <span data-ttu-id="0a69f-201">그립</span><span class="sxs-lookup"><span data-stu-id="0a69f-201">Grip</span></span> | <span data-ttu-id="0a69f-202">에어 탭 또는 에어 탭</span><span class="sxs-lookup"><span data-stu-id="0a69f-202">Air tap or squeeze</span></span> |
| <span data-ttu-id="0a69f-203">primaryButton</span><span class="sxs-lookup"><span data-stu-id="0a69f-203">primaryButton</span></span> | <span data-ttu-id="0a69f-204">[X/A] - 누르기</span><span class="sxs-lookup"><span data-stu-id="0a69f-204">[X/A] - Press</span></span> | <span data-ttu-id="0a69f-205">에어 탭</span><span class="sxs-lookup"><span data-stu-id="0a69f-205">Air tap</span></span> |
| <span data-ttu-id="0a69f-206">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="0a69f-206">secondaryButton</span></span> | <span data-ttu-id="0a69f-207">[Y/B] - 누르기</span><span class="sxs-lookup"><span data-stu-id="0a69f-207">[Y/B] - Press</span></span> | |
| <span data-ttu-id="0a69f-208">gripButton</span><span class="sxs-lookup"><span data-stu-id="0a69f-208">gripButton</span></span> | <span data-ttu-id="0a69f-209">그립 - 누르기</span><span class="sxs-lookup"><span data-stu-id="0a69f-209">Grip - Press</span></span> | |
| <span data-ttu-id="0a69f-210">triggerButton</span><span class="sxs-lookup"><span data-stu-id="0a69f-210">triggerButton</span></span> | <span data-ttu-id="0a69f-211">트리거 - 누르기</span><span class="sxs-lookup"><span data-stu-id="0a69f-211">Trigger - Press</span></span> | |
| <span data-ttu-id="0a69f-212">menuButton</span><span class="sxs-lookup"><span data-stu-id="0a69f-212">menuButton</span></span> | <span data-ttu-id="0a69f-213">메뉴</span><span class="sxs-lookup"><span data-stu-id="0a69f-213">Menu</span></span> | |

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="0a69f-214">그립 자세와 포인팅 자세</span><span class="sxs-lookup"><span data-stu-id="0a69f-214">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="0a69f-215">Windows Mixed Reality 다양한 폼 팩터에서 모션 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-215">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="0a69f-216">각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 가리키는 데 사용해야 하는 자연스러운 "앞으로" 방향 간의 관계가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-216">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="0a69f-217">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 자세인 **그립 자세와** **포인터 자세가** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-217">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="0a69f-218">그립 자세와 포인터 자세 좌표는 모두 전역 Unity 세계 좌표의 모든 Unity API로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-218">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="0a69f-219">그립 자세</span><span class="sxs-lookup"><span data-stu-id="0a69f-219">Grip pose</span></span>

<span data-ttu-id="0a69f-220">**그립 자세는** HoloLens에서 감지하거나 모션 컨트롤러를 보유하는 사용자의 손무한 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-220">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="0a69f-221">몰입형 헤드셋에서 그립 자세는 **사용자의 손** 또는 사용자의 **손 에 보관된 개체를 렌더링하는** 데 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-221">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="0a69f-222">그립 자세는 모션 컨트롤러를 시각화할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-222">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="0a69f-223">동작 컨트롤러에 대해 Windows에서 제공하는 **렌더링 가능한 모델은** 그립 자세를 회전의 원점과 중심으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-223">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="0a69f-224">그립 자세는 다음과 같이 구체적으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-224">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="0a69f-225">**그립 위치:** 컨트롤러를 자연스럽게 보유할 때의 손만 중심으로, 그립 내의 위치를 가운데에 맞도록 왼쪽 또는 오른쪽으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-225">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="0a69f-226">Windows Mixed Reality 모션 컨트롤러에서 이 위치는 일반적으로 이해 단추에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-226">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="0a69f-227">**그립 방향의 오른쪽 축:** 손을 완전히 열어 플랫 5 손가락 자세를 형성하면 손끝에 정상인 광선(왼쪽 손끝에서 앞으로, 오른쪽 손끝에서 뒤로)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-227">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="0a69f-228">**그립 방향의 앞으로 축:** 손을 부분적으로 닫을 때(컨트롤러를 보유하는 것처럼) 엄지 손가락이 아닌 손가락으로 형성된 선을 통해 "앞으로" 가리키는 광선입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-228">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="0a69f-229">**그립 방향의 Up 축:** 오른쪽 및 앞으로 정의에 암시된 Up 축입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-229">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="0a69f-230">Unity의 공급업체 간 입력 API(XR)를 통해 그립 자세에 액세스할 수 *[있습니다. InputTracking .](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html) GetLocalPosition/Rotation*) 또는 Windows MR 관련 API를 *통해(sourceState.sourcePose.TryGetPosition/Rotation*, **그립** 노드에 대한 자세 데이터 요청)</span><span class="sxs-lookup"><span data-stu-id="0a69f-230">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="0a69f-231">포인터 자세</span><span class="sxs-lookup"><span data-stu-id="0a69f-231">Pointer pose</span></span>

<span data-ttu-id="0a69f-232">**포인터 자세는** 앞으로 가리키는 컨트롤러의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-232">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="0a69f-233">시스템 제공 포인터 자세는 **컨트롤러 모델 자체를 렌더링할** 때 raycast에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-233">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="0a69f-234">가상 총과 같은 컨트롤러 대신 다른 가상 개체를 렌더링하는 경우 앱에서 정의한 총 모델을 따라 이동하는 광선과 같이 해당 가상 개체에 가장 자연스러운 광선을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-234">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="0a69f-235">사용자는 실제 컨트롤러가 아닌 가상 개체를 볼 수 있으므로 가상 개체를 가리키는 것이 앱을 사용하는 사용자에게 더 자연스럽습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-235">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="0a69f-236">현재 포인터 자세는 Windows MR별 *API인 sourceState.sourcePose.TryGetPosition/Rotation을* 통해서만 Unity에서 사용할 수 있으며 *InteractionSourceNode.Pointer를* 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-236">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

### <a name="openxr"></a><span data-ttu-id="0a69f-237">OpenXR</span><span class="sxs-lookup"><span data-stu-id="0a69f-237">OpenXR</span></span> 

<span data-ttu-id="0a69f-238">OpenXR 입력 상호 작용을 통해 두 가지 자세 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-238">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="0a69f-239">손에서 개체를 렌더링하기 위한 그립 자세</span><span class="sxs-lookup"><span data-stu-id="0a69f-239">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="0a69f-240">목표는 세계를 가리키는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-240">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="0a69f-241">이 디자인과 두 가지 자세 간의 차이점에 대한 자세한 내용은 [OpenXR 사양 - 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-241">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="0a69f-242">InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** 및 **DeviceAngularVelocity에서** 제공하는 자세는 모두 OpenXR **그립** 자세를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-242">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="0a69f-243">그립 자세와 관련된 InputFeatureUsages는 Unity의 [CommonUsages 에 정의되어 있습니다.](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)</span><span class="sxs-lookup"><span data-stu-id="0a69f-243">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="0a69f-244">InputFeatureUsages **PointerPosition,** **PointerRotation,** PointerVelocity 및 **PointerAngularVelocity에서** 제공하는 자세는 모두 OpenXR **목표** 자세를 나타냅니다. </span><span class="sxs-lookup"><span data-stu-id="0a69f-244">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="0a69f-245">이러한 InputFeatureUsages는 포함된 C# 파일에 정의되지 않으므로 다음과 같이 고유한 InputFeatureUsages를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-245">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a><span data-ttu-id="0a69f-246">햅 틱</span><span class="sxs-lookup"><span data-stu-id="0a69f-246">Haptics</span></span>

<span data-ttu-id="0a69f-247">Unity의 XR 입력 시스템에서 haptics 사용에 대한 자세한 내용은 Unity [XR 입력을 위한 Unity 설명서 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-247">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="0a69f-248">컨트롤러 추적 상태</span><span class="sxs-lookup"><span data-stu-id="0a69f-248">Controller tracking state</span></span>

<span data-ttu-id="0a69f-249">헤드셋과 마찬가지로 Windows Mixed Reality 모션 컨트롤러에는 외부 추적 센서를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-249">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="0a69f-250">대신 컨트롤러는 헤드셋 자체의 센서에 의해 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-250">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="0a69f-251">사용자가 헤드셋의 보기 필드에서 컨트롤러를 이동하는 경우 Windows는 대부분의 경우 컨트롤러 위치를 계속 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-251">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="0a69f-252">컨트롤러가 오랫동안 시각적 추적을 손실한 경우 컨트롤러의 위치는 근사 정확도 위치로 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-252">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="0a69f-253">이 시점에서 시스템은 내부 방향 센서를 사용하여 컨트롤러의 진정한 방향을 계속 노출하면서 사용자가 이동할 때 사용자의 위치를 추적하여 컨트롤러를 사용자에게 본문 잠금합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-253">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0a69f-254">컨트롤러를 사용하여 UI 요소를 가리키고 활성화하는 많은 앱은 사용자가 모르게 대략적인 정확도로 정상적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-254">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="0a69f-255">명시적으로 상태를 추적하는 이유</span><span class="sxs-lookup"><span data-stu-id="0a69f-255">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="0a69f-256">추적 상태에 따라 위치를 다르게 처리하려는 앱은 더 나아가서 컨트롤러의 상태(예: *SourceLossRisk* 및 *PositionAccuracy)에서* 속성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-256">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="0a69f-257">추적 상태</span><span class="sxs-lookup"><span data-stu-id="0a69f-257">Tracking state</span></span> </th><th> <span data-ttu-id="0a69f-258">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="0a69f-258">SourceLossRisk</span></span> </th><th> <span data-ttu-id="0a69f-259">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="0a69f-259">PositionAccuracy</span></span> </th><th> <span data-ttu-id="0a69f-260">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0a69f-260">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0a69f-261"><b>높은 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="0a69f-261"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-262">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-262">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-263">높은</span><span class="sxs-lookup"><span data-stu-id="0a69f-263">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-264">true</span><span class="sxs-lookup"><span data-stu-id="0a69f-264">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-265"><b>높은 정확도(손실 위험)</b> </span><span class="sxs-lookup"><span data-stu-id="0a69f-265"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0a69f-266">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-266">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-267">높은</span><span class="sxs-lookup"><span data-stu-id="0a69f-267">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-268">true</span><span class="sxs-lookup"><span data-stu-id="0a69f-268">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-269"><b>대략적 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="0a69f-269"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0a69f-270">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-270">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0a69f-271">근사치</span><span class="sxs-lookup"><span data-stu-id="0a69f-271">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0a69f-272">true</span><span class="sxs-lookup"><span data-stu-id="0a69f-272">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0a69f-273"><b>위치 없음</b> </span><span class="sxs-lookup"><span data-stu-id="0a69f-273"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0a69f-274">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0a69f-274">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0a69f-275">근사치</span><span class="sxs-lookup"><span data-stu-id="0a69f-275">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0a69f-276">false</span><span class="sxs-lookup"><span data-stu-id="0a69f-276">false</span></span></td>
</tr>
</table>

<span data-ttu-id="0a69f-277">이러한 모션 컨트롤러 추적 상태는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-277">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="0a69f-278">**높은 정확도:** 모션 컨트롤러는 헤드셋의 보기 필드 내에 있는 동안 일반적으로 시각적 추적을 기반으로 높은 정확도 위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-278">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="0a69f-279">일시적으로 보기 필드를 벗어나거나 헤드셋 센서(예: 사용자의 다른 손으로)에서 일시적으로 가려지는 이동 컨트롤러는 컨트롤러 자체의 관성 추적에 따라 짧은 시간 동안 높은 정확도의 자세를 계속 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-279">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="0a69f-280">**높은 정확도(손실 위험):** 사용자가 헤드셋의 보기 필드 가장자리를 지나 모션 컨트롤러를 이동하면 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-280">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="0a69f-281">앱은 **SourceLossRisk가** 1.0에 도달하는 것을 확인하여 컨트롤러가 이 FOV 경계에 도달한 시기를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-281">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="0a69f-282">이 시점에서 앱은 안정적인 고품질 자세 스트림이 필요한 컨트롤러 제스처를 일시 중지하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-282">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="0a69f-283">**대략적 정확도:** 컨트롤러가 오랫동안 시각적 추적을 손실한 경우 컨트롤러의 위치는 근사 정확도 위치로 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-283">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="0a69f-284">이 시점에서 시스템은 내부 방향 센서를 사용하여 컨트롤러의 진정한 방향을 계속 노출하면서 사용자가 이동할 때 사용자의 위치를 추적하여 컨트롤러를 사용자에게 본문 잠금합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-284">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0a69f-285">컨트롤러를 사용하여 UI 요소를 가리키고 활성화하는 많은 앱은 사용자가 모르게 대략적인 정확도로 정상적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-285">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="0a69f-286">입력 요구 사항이 더 많은 앱은 **PositionAccuracy** 속성을 검사하여 높은 **정확도에서** **근사** 정확도로 이 저하를 감지하도록 선택할 수 있습니다. 예를 들어 이 시간 동안 사용자에게 화면 끄기 대상에서 더 큰 적중 상자를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-286">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="0a69f-287">**위치 없음:** 컨트롤러가 오랜 시간 동안 대략적인 정확도로 작동할 수 있지만, 시스템에서는 현재 본문이 잠긴 위치도 의미가 없다는 것을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-287">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="0a69f-288">예를 들어 켜진 컨트롤러가 시각적으로 관찰되지 않았거나 사용자가 컨트롤러를 내려 놓은 다음 다른 사용자가 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-288">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="0a69f-289">이 경우 시스템은 앱에 위치를 제공하지 않으며 *TryGetPosition은* false를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-289">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="0a69f-290">일반적인 Unity API(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="0a69f-290">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="0a69f-291">**네임스페이스:** *UnityEngine,* *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="0a69f-291">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="0a69f-292">**형식:** *입력*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="0a69f-292">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="0a69f-293">Unity는 현재 일반 *Input.GetButton/Input.GetAxis API를* 사용하여 손과 모션 컨트롤러를 [포함하여 Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality 대한 입력을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-293">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="0a69f-294">앱에서 이러한 API를 입력에 사용하는 경우 Windows Mixed Reality 포함하여 여러 XR SDK에서 모션 컨트롤러를 쉽게 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-294">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="0a69f-295">논리 단추의 누른 상태 얻기</span><span class="sxs-lookup"><span data-stu-id="0a69f-295">Getting a logical button's pressed state</span></span>

<span data-ttu-id="0a69f-296">일반 Unity 입력 API를 사용하려면 일반적으로 단추와 축을 [Unity 입력 관리자의](https://docs.unity3d.com/Manual/ConventionalGameInput.html)논리적 이름에 연결하고 단추 또는 축 ID를 각 이름에 바인딩하는 것으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-296">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="0a69f-297">그런 다음 해당 논리 단추/축 이름을 참조하는 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-297">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="0a69f-298">예를 들어 왼쪽 모션 컨트롤러의 트리거 단추를 제출 작업에 매핑하려면 Unity 내에서 **프로젝트 설정 > 입력 > 편집으로** 이동하고 축 아래의 제출 섹션의 속성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-298">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="0a69f-299">다음과 같이 **양의 단추** 또는 Alt **긍정 단추** 속성을 변경하여 **14 단추를** 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-299">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="0a69f-300">![Unity의 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="0a69f-300">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="0a69f-301&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0a69f-301&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;0a69f-302&quot;>그러면 스크립트에서 *Input.GetButton* 을 사용하여 제출 작업을 확인할 수 있습니다.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0a69f-302&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="0a69f-303">축 아래에서 **Size** 속성을 변경하여 논리 단추를 더 추가할 수 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="0a69f-303">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="0a69f-304">실제 단추의 누른 상태 직접 받기</span><span class="sxs-lookup"><span data-stu-id="0a69f-304">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="0a69f-305">*Input.GetKey* 를 사용하여 정규화된 이름으로 단추에 수동으로 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-305">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="0a69f-306">손 또는 모션 컨트롤러의 자세 얻기</span><span class="sxs-lookup"><span data-stu-id="0a69f-306">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="0a69f-307">XR을 사용하여 컨트롤러의 위치 및 회전에 액세스할 수 *있습니다. InputTracking:*</span><span class="sxs-lookup"><span data-stu-id="0a69f-307">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="0a69f-308">위의 코드는 컨트롤러의 그립 자세(사용자가 컨트롤러를 보유하는 위치)를 나타내며, 사용자의 손이나 컨트롤러 자체의 모델을 렌더링하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-308">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="0a69f-309">이 그립 자세와 포인터 자세(컨트롤러의 팁이 가리키는 위치) 간의 관계는 컨트롤러 간에 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-309">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="0a69f-310">현재 컨트롤러의 포인터 자세에 액세스하는 것은 아래 섹션에 설명된 MR 관련 입력 API를 통해서만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-310">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="0a69f-311">Windows 관련 API(XR. Wsa. 입력)</span><span class="sxs-lookup"><span data-stu-id="0a69f-311">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="0a69f-312">프로젝트에서 XR을 사용하는 경우 WSA API는 향후 Unity 릴리스에서 XR SDK를 위해 단계적으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-312">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="0a69f-313">새 프로젝트의 경우 XR SDK를 처음부터 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-313">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="0a69f-314">[XR 입력 시스템 및 API에](https://docs.unity3d.com/Manual/xr_input.html)대한 자세한 내용은 에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-314">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="0a69f-315">**네임스페이스:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="0a69f-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="0a69f-316">**형식:** *InteractionManager,* *InteractionSourceState,* *InteractionSource*, *InteractionSourceProperties,* *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="0a69f-316">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="0a69f-317">Windows Mixed Reality 손 입력(HoloLens용) 및 모션 컨트롤러에 대한 자세한 정보를 얻으려면 *UnityEngine.XR.WSA.Input* 네임스페이스에서 Windows 관련 공간 입력 API를 사용하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-317">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="0a69f-318">이렇게 하면 위치 정확도 또는 원본 종류와 같은 추가 정보에 액세스하여 손과 컨트롤러를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-318">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="0a69f-319">손 및 모션 컨트롤러의 상태에 대한 폴링</span><span class="sxs-lookup"><span data-stu-id="0a69f-319">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="0a69f-320">*GetCurrentReading* 메서드를 사용하여 각 상호 작용 원본(손 또는 모션 컨트롤러)에 대해 이 프레임의 상태를 폴링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-320">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="0a69f-321">다시 얻는 각 *InteractionSourceState는* 현재 시점의 상호 작용 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-321">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="0a69f-322">*InteractionSourceState는* 다음과 같은 정보를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-322">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="0a69f-323">어떤 [종류의 누를](../../design/motion-controllers.md) 발생시키는지(선택/메뉴/이해/터치패드/엄지스틱)</span><span class="sxs-lookup"><span data-stu-id="0a69f-323">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="0a69f-324">터치 패드 및/또는 썸틱의 XY 좌표 및 터치된 상태와 같은 동작 컨트롤러 관련 기타 데이터</span><span class="sxs-lookup"><span data-stu-id="0a69f-324">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="0a69f-325">소스가 손 또는 모션 컨트롤러인지 알 수 있는 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="0a69f-325">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="0a69f-326">앞으로 예측된 렌더링에 대한 폴링포지</span><span class="sxs-lookup"><span data-stu-id="0a69f-326">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="0a69f-327">손과 컨트롤러에서 상호 작용 원본 데이터를 폴링할 때 얻을 수 있는 자세는 이 프레임의 광자가 사용자의 눈에 도달하는 순간의 정방향 예측 자세입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-327">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="0a69f-328">정방향 예측 자세는 각 프레임에서 컨트롤러 또는 보유된 **개체를 렌더링하는** 데 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-328">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="0a69f-329">컨트롤러를 사용하여 지정된 누르기 또는 릴리스를 대상으로 하는 경우 아래에 설명된 기록 이벤트 API를 사용하는 경우 가장 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-329">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="0a69f-330">이 현재 프레임에 대해 정방향 예측 머리 자세를 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-330">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="0a69f-331">소스 자세와 마찬가지로 이는 **커서를 렌더링하는** 데 유용하지만, 아래에 설명된 기록 이벤트 API를 사용하는 경우 지정된 누르기 또는 릴리스를 대상으로 지정하는 것이 가장 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-331">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="0a69f-332">상호 작용 원본 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="0a69f-332">Handling interaction source events</span></span>

<span data-ttu-id="0a69f-333">정확한 기록 자세 데이터에서 발생하는 입력 이벤트를 처리하려면 폴링 대신 상호 작용 원본 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-333">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="0a69f-334">상호 작용 원본 이벤트를 처리하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-334">To handle interaction source events:</span></span>
* <span data-ttu-id="0a69f-335">*InteractionManager* 입력 이벤트에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-335">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="0a69f-336">관심 있는 상호 작용 이벤트의 각 유형에 대해 구독해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-336">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="0a69f-337">이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-337">Handle the event.</span></span> <span data-ttu-id="0a69f-338">상호 작용 이벤트를 구독하면 해당하는 경우 콜백이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-338">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="0a69f-339">*SourcePressed* 예제에서는 소스가 검색된 후와 소스가 해제되거나 손실되기 전이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-339">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="0a69f-340">이벤트 처리를 중지하는 방법</span><span class="sxs-lookup"><span data-stu-id="0a69f-340">How to stop handling an event</span></span>

<span data-ttu-id="0a69f-341">이벤트에 더 이상 관심이 없거나 이벤트를 구독한 개체를 삭제하는 경우 이벤트 처리를 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-341">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="0a69f-342">이벤트 처리를 중지하려면 이벤트에서 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-342">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="0a69f-343">상호 작용 원본 이벤트 목록</span><span class="sxs-lookup"><span data-stu-id="0a69f-343">List of interaction source events</span></span>

<span data-ttu-id="0a69f-344">사용 가능한 상호 작용 원본 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-344">The available interaction source events are:</span></span>
* <span data-ttu-id="0a69f-345">*InteractionSourceDetected(원본이* 활성화됩니다.)</span><span class="sxs-lookup"><span data-stu-id="0a69f-345">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="0a69f-346">*InteractionSourceLost(비활성* 상태가 되도록)</span><span class="sxs-lookup"><span data-stu-id="0a69f-346">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="0a69f-347">*InteractionSourcePressed(탭,* 단추 누르기 또는 "선택" 발화)</span><span class="sxs-lookup"><span data-stu-id="0a69f-347">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="0a69f-348">*InteractionSourceReleased(탭의* 끝, 해제된 단추 또는 발화된 "선택"의 끝)</span><span class="sxs-lookup"><span data-stu-id="0a69f-348">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="0a69f-349">*InteractionSourceUpdated(일부* 상태를 이동하거나 변경)</span><span class="sxs-lookup"><span data-stu-id="0a69f-349">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="0a69f-350">기록 대상 지정에 대한 이벤트는 누르기 또는 릴리스와 가장 정확하게 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-350">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="0a69f-351">앞서 설명한 폴링 API는 앱에 앞으로 예측된 자세를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-351">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="0a69f-352">이러한 예측된 자세는 컨트롤러 또는 가상 핸드 실드 개체를 렌더링하는 데 가장 적합하지만, 다음 두 가지 주요 이유로 향후의 자세는 대상 지정에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-352">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="0a69f-353">사용자가 컨트롤러에서 단추를 누르면 시스템에서 누를 때 Bluetooth를 통해 약 20ms의 무선 대기 시간이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-353">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="0a69f-354">그런 다음, 정방향 예측 자세를 사용하는 경우 현재 프레임의 광자가 사용자의 눈에 도달하는 시간을 대상으로 하는 또 다른 10-20ms의 정방향 예측이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-354">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="0a69f-355">즉, 폴링은 누를 때 사용자의 머리 및 손을 실제로 돌아간 위치에서 앞으로 30-40ms 정도의 소스 자세 또는 머리 자세를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-355">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="0a69f-356">HoloLens 손 입력의 경우 무선 전송 지연은 없지만 누르기를 감지하는 데 비슷한 처리 지연이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-356">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="0a69f-357">손 또는 컨트롤러 누르기에 대한 사용자의 원래 의도를 정확하게 대상으로 지정하려면 해당 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력 이벤트에서 기록 소스 자세 또는 머리 자세를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-357">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="0a69f-358">사용자의 머리 또는 컨트롤러에서 기록적인 자세 데이터를 통해 누르기 또는 릴리스를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-358">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="0a69f-359">제스처 또는 컨트롤러 누르기가 발생한 시점의 머리 자세로, **대상을 지정하여** 사용자가 무엇을 하고 [있는지](../../design/gaze-and-commit.md) 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-359">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="0a69f-360">모션 컨트롤러 누르기가 발생한 시점의 소스 자세로, **대상 지정에** 사용하여 사용자가 컨트롤러를 가리키고 있는 대상을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-360">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="0a69f-361">이 상태는 누를 때 발생한 컨트롤러의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-361">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="0a69f-362">컨트롤러 자체를 렌더링하는 경우 그립 자세가 아닌 포인터 자세를 요청하여 사용자가 렌더링된 컨트롤러의 자연스러운 팁을 고려하는 대상 광선을 찍을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-362">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="0a69f-363">이벤트 처리기 예제</span><span class="sxs-lookup"><span data-stu-id="0a69f-363">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="0a69f-364">MRTK의 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="0a69f-364">Motion Controllers in MRTK</span></span>

<span data-ttu-id="0a69f-365">입력 관리자에서 [제스처 및 모션 컨트롤러에](/windows/mixed-reality/mrtk-unity/features/input/controllers) 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-365">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="0a69f-366">안내 따르기</span><span class="sxs-lookup"><span data-stu-id="0a69f-366">Follow along with tutorials</span></span>

<span data-ttu-id="0a69f-367">자세한 사용자 지정 예제가 있는 단계별 자습서는 Mixed Reality Academy에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-367">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="0a69f-368">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="0a69f-368">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="0a69f-369">MR 입력 213: 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="0a69f-369">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="0a69f-370">[![MR 입력 213 - 모션 컨트롤러](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="0a69f-370">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="0a69f-371">*MR 입력 213 - 모션 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="0a69f-371">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0a69f-372">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="0a69f-372">Next Development Checkpoint</span></span>

<span data-ttu-id="0a69f-373">앞에서 설명한 Unity 개발 여정을 수행하는 경우 MRTK 핵심 구성 요소 탐색을 진행하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-373">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0a69f-374">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-374">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a69f-375">손 및 시선 추적</span><span class="sxs-lookup"><span data-stu-id="0a69f-375">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="0a69f-376">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-376">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a69f-377">공유 환경</span><span class="sxs-lookup"><span data-stu-id="0a69f-377">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="0a69f-378">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a69f-378">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a69f-379">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a69f-379">See also</span></span>

* [<span data-ttu-id="0a69f-380">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="0a69f-380">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="0a69f-381">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="0a69f-381">Motion controllers</span></span>](../../design/motion-controllers.md)