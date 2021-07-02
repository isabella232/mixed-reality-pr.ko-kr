---
title: 입력 애니메이션 파일 형식
description: MRTK의 입력 애니메이션 이진 파일 형식 사양에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 400212d80833f5d8dfbb3c5265c755ed2e127131
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177005"
---
# <a name="input-animation-file-format"></a><span data-ttu-id="9e022-104">입력 애니메이션 파일 형식</span><span class="sxs-lookup"><span data-stu-id="9e022-104">Input animation file format</span></span>

## <a name="overall-structure"></a><span data-ttu-id="9e022-105">전체 구조</span><span class="sxs-lookup"><span data-stu-id="9e022-105">Overall structure</span></span>

<span data-ttu-id="9e022-106">입력 애니메이션 이진 파일은 64비트 정수 매직 넘버로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="9e022-107">16진수 표기에서 이 숫자의 값은 `0x6a8faf6e0f9e42c6` 이며 유효한 입력 애니메이션 파일을 식별하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="9e022-108">다음 8바이트는 파일의 주 버전 및 부 버전 번호를 선언하는 두 개의 Int32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="9e022-109">파일의 나머지 부분은 버전 번호 간에 변경 될 수 있는 애니메이션 데이터에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="9e022-110">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-110">Section</span></span> | <span data-ttu-id="9e022-111">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-112">매직 넘버</span><span class="sxs-lookup"><span data-stu-id="9e022-112">Magic Number</span></span> | <span data-ttu-id="9e022-113">Int64</span><span class="sxs-lookup"><span data-stu-id="9e022-113">Int64</span></span> |
| <span data-ttu-id="9e022-114">주 버전 번호</span><span class="sxs-lookup"><span data-stu-id="9e022-114">Major Version Number</span></span> | <span data-ttu-id="9e022-115">Int32</span><span class="sxs-lookup"><span data-stu-id="9e022-115">Int32</span></span> |
| <span data-ttu-id="9e022-116">부 버전 번호</span><span class="sxs-lookup"><span data-stu-id="9e022-116">Minor Version Number</span></span> | <span data-ttu-id="9e022-117">Int32</span><span class="sxs-lookup"><span data-stu-id="9e022-117">Int32</span></span> |
| <span data-ttu-id="9e022-118">애니메이션 데이터</span><span class="sxs-lookup"><span data-stu-id="9e022-118">Animation Data</span></span> | <span data-ttu-id="9e022-119">_버전 섹션 참조_</span><span class="sxs-lookup"><span data-stu-id="9e022-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="9e022-120">버전 1.1</span><span class="sxs-lookup"><span data-stu-id="9e022-120">Version 1.1</span></span>

<span data-ttu-id="9e022-121">입력 애니메이션 데이터는 애니메이션에 카메라, 손 및 시선 응시 데이터와 애니메이션 곡선 시퀀스가 포함되는지 여부를 나타내는 세 개의 부울 값으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="9e022-122">존재하는 곡선은 이러한 부울의 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="9e022-123">각 곡선에는 서로 다른 수의 키 프레임이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="9e022-124">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-124">Section</span></span> | <span data-ttu-id="9e022-125">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-125">Type</span></span> | <span data-ttu-id="9e022-126">참고</span><span class="sxs-lookup"><span data-stu-id="9e022-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="9e022-127">카메라 자세가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-127">Has Camera Pose</span></span> | <span data-ttu-id="9e022-128">부울</span><span class="sxs-lookup"><span data-stu-id="9e022-128">Boolean</span></span> | |
| <span data-ttu-id="9e022-129">손 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="9e022-129">Has Hand Data</span></span> | <span data-ttu-id="9e022-130">부울</span><span class="sxs-lookup"><span data-stu-id="9e022-130">Boolean</span></span> | |
| <span data-ttu-id="9e022-131">시선 응시</span><span class="sxs-lookup"><span data-stu-id="9e022-131">Has Eye Gaze</span></span>| <span data-ttu-id="9e022-132">부울</span><span class="sxs-lookup"><span data-stu-id="9e022-132">Boolean</span></span> | |
| <span data-ttu-id="9e022-133">카메라</span><span class="sxs-lookup"><span data-stu-id="9e022-133">Camera</span></span> | [<span data-ttu-id="9e022-134">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="9e022-135">카메라 자세가 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="9e022-136">왼쪽에서 손 추적</span><span class="sxs-lookup"><span data-stu-id="9e022-136">Hand Tracked Left</span></span> | [<span data-ttu-id="9e022-137">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9e022-138">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-139">직접 추적 오른쪽</span><span class="sxs-lookup"><span data-stu-id="9e022-139">Hand Tracked Right</span></span> | [<span data-ttu-id="9e022-140">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9e022-141">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-142">왼쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="9e022-142">Hand Pinching Left</span></span> | [<span data-ttu-id="9e022-143">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9e022-144">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-145">오른쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="9e022-145">Hand Pinching Right</span></span> | [<span data-ttu-id="9e022-146">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9e022-147">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-148">왼쪽 손 조인트</span><span class="sxs-lookup"><span data-stu-id="9e022-148">Hand Joints Left</span></span> | [<span data-ttu-id="9e022-149">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="9e022-150">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-151">손 조인트 오른쪽</span><span class="sxs-lookup"><span data-stu-id="9e022-151">Hand Joints Right</span></span> | [<span data-ttu-id="9e022-152">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="9e022-153">손 데이터 사용이 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9e022-154">시선 응시</span><span class="sxs-lookup"><span data-stu-id="9e022-154">Eye Gaze</span></span> | <span data-ttu-id="9e022-155">[Ray Curves](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="9e022-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="9e022-156">시선 응시가 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="9e022-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="9e022-157">버전 1.0</span><span class="sxs-lookup"><span data-stu-id="9e022-157">Version 1.0</span></span>

<span data-ttu-id="9e022-158">입력 애니메이션 데이터는 애니메이션 곡선 시퀀스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="9e022-159">애니메이션 곡선의 수와 의미는 고정되어 있지만 각 곡선의 키 프레임 수는 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="9e022-160">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-160">Section</span></span> | <span data-ttu-id="9e022-161">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-162">카메라</span><span class="sxs-lookup"><span data-stu-id="9e022-162">Camera</span></span> | [<span data-ttu-id="9e022-163">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-164">왼쪽에서 손 추적</span><span class="sxs-lookup"><span data-stu-id="9e022-164">Hand Tracked Left</span></span> | [<span data-ttu-id="9e022-165">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9e022-166">직접 추적 오른쪽</span><span class="sxs-lookup"><span data-stu-id="9e022-166">Hand Tracked Right</span></span> | [<span data-ttu-id="9e022-167">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9e022-168">왼쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="9e022-168">Hand Pinching Left</span></span> | [<span data-ttu-id="9e022-169">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9e022-170">오른쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="9e022-170">Hand Pinching Right</span></span> | [<span data-ttu-id="9e022-171">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9e022-172">왼쪽 손 조인트</span><span class="sxs-lookup"><span data-stu-id="9e022-172">Hand Joints Left</span></span> | [<span data-ttu-id="9e022-173">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="9e022-174">손 조인트 오른쪽</span><span class="sxs-lookup"><span data-stu-id="9e022-174">Hand Joints Right</span></span> | [<span data-ttu-id="9e022-175">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="9e022-176">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-176">Joint pose curves</span></span>

<span data-ttu-id="9e022-177">각 손의 경우 일련의 조인 애니메이션 곡선이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="9e022-178">조인 수가 고정되고 각 조인에 대해 자세 곡선 집합이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="9e022-179">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-179">Section</span></span> | <span data-ttu-id="9e022-180">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-181">없음</span><span class="sxs-lookup"><span data-stu-id="9e022-181">None</span></span> | [<span data-ttu-id="9e022-182">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-183">손목</span><span class="sxs-lookup"><span data-stu-id="9e022-183">Wrist</span></span> | [<span data-ttu-id="9e022-184">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-185">Palm</span><span class="sxs-lookup"><span data-stu-id="9e022-185">Palm</span></span> | [<span data-ttu-id="9e022-186">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="9e022-188">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="9e022-190">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="9e022-192">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="9e022-193">ThumbTip</span></span> | [<span data-ttu-id="9e022-194">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9e022-195">IndexMetacarpal</span></span> | [<span data-ttu-id="9e022-196">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="9e022-197">IndexKnuckle</span></span> | [<span data-ttu-id="9e022-198">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="9e022-200">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-201">IndexDistalJoint</span></span> | [<span data-ttu-id="9e022-202">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-203">IndexTip</span><span class="sxs-lookup"><span data-stu-id="9e022-203">IndexTip</span></span> | [<span data-ttu-id="9e022-204">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9e022-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="9e022-206">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="9e022-207">MiddleKnuckle</span></span> | [<span data-ttu-id="9e022-208">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="9e022-210">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="9e022-212">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="9e022-213">MiddleTip</span></span> | [<span data-ttu-id="9e022-214">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9e022-215">RingMetacarpal</span></span> | [<span data-ttu-id="9e022-216">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="9e022-217">RingKnuckle</span></span> | [<span data-ttu-id="9e022-218">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-219">RingMiddleJoint</span></span> | [<span data-ttu-id="9e022-220">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-221">RingDistalJoint</span></span> | [<span data-ttu-id="9e022-222">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="9e022-223">RingTip</span></span> | [<span data-ttu-id="9e022-224">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9e022-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="9e022-226">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-227">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="9e022-227">PinkyKnuckle</span></span> | [<span data-ttu-id="9e022-228">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="9e022-230">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9e022-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="9e022-232">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9e022-233">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="9e022-233">PinkyTip</span></span> | [<span data-ttu-id="9e022-234">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="9e022-235">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-235">Pose curves</span></span>

<span data-ttu-id="9e022-236">자세 곡선은 위치 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 회전 쿼터니언에 4개의 애니메이션 곡선이 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="9e022-237">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-237">Section</span></span> | <span data-ttu-id="9e022-238">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-239">위치 X</span><span class="sxs-lookup"><span data-stu-id="9e022-239">Position X</span></span> | [<span data-ttu-id="9e022-240">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-241">위치 Y</span><span class="sxs-lookup"><span data-stu-id="9e022-241">Position Y</span></span> | [<span data-ttu-id="9e022-242">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-243">위치 Z</span><span class="sxs-lookup"><span data-stu-id="9e022-243">Position Z</span></span> | [<span data-ttu-id="9e022-244">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-245">회전 X</span><span class="sxs-lookup"><span data-stu-id="9e022-245">Rotation X</span></span> | [<span data-ttu-id="9e022-246">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-247">회전 Y</span><span class="sxs-lookup"><span data-stu-id="9e022-247">Rotation Y</span></span> | [<span data-ttu-id="9e022-248">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-249">회전 Z</span><span class="sxs-lookup"><span data-stu-id="9e022-249">Rotation Z</span></span> | [<span data-ttu-id="9e022-250">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-251">회전 W</span><span class="sxs-lookup"><span data-stu-id="9e022-251">Rotation W</span></span> | [<span data-ttu-id="9e022-252">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="9e022-253">광선 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-253">Ray curves</span></span>

<span data-ttu-id="9e022-254">광선 곡선은 원점 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 방향 벡터에 대해 3개의 애니메이션 곡선이 잇는 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="9e022-255">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-255">Section</span></span> | <span data-ttu-id="9e022-256">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-257">원본 X</span><span class="sxs-lookup"><span data-stu-id="9e022-257">Origin X</span></span> | [<span data-ttu-id="9e022-258">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-259">원본 Y</span><span class="sxs-lookup"><span data-stu-id="9e022-259">Origin Y</span></span> | [<span data-ttu-id="9e022-260">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-261">원본 Z</span><span class="sxs-lookup"><span data-stu-id="9e022-261">Origin Z</span></span> | [<span data-ttu-id="9e022-262">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-263">Direction X</span><span class="sxs-lookup"><span data-stu-id="9e022-263">Direction X</span></span> | [<span data-ttu-id="9e022-264">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-265">Direction Y</span><span class="sxs-lookup"><span data-stu-id="9e022-265">Direction Y</span></span> | [<span data-ttu-id="9e022-266">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9e022-267">방향 Z</span><span class="sxs-lookup"><span data-stu-id="9e022-267">Direction Z</span></span> | [<span data-ttu-id="9e022-268">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="9e022-269">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-269">Float curve</span></span>

<span data-ttu-id="9e022-270">부동 소수점 곡선은 가변 개수의 키 프레임이 있는 완전히 얽힌 3차원 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="9e022-271">각 키 프레임은 시간 및 곡선 값뿐만 아니라 각 키 프레임의 왼쪽과 오른쪽에 탄젠트 및 가중치를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="9e022-272">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-272">Section</span></span> | <span data-ttu-id="9e022-273">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-274">사전 래핑 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="9e022-275">Int32, [래핑 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9e022-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9e022-276">사후 래핑 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-276">Post-Wrap Mode</span></span> | <span data-ttu-id="9e022-277">Int32, [래핑 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9e022-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9e022-278">키 프레임 수</span><span class="sxs-lookup"><span data-stu-id="9e022-278">Number of keyframes</span></span> | <span data-ttu-id="9e022-279">Int32</span><span class="sxs-lookup"><span data-stu-id="9e022-279">Int32</span></span> |
| <span data-ttu-id="9e022-280">키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-280">Keyframes</span></span> | [<span data-ttu-id="9e022-281">Float 키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="9e022-282">Float 키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-282">Float keyframe</span></span>

<span data-ttu-id="9e022-283">float 키 프레임은 탄젠트 및 가중치 값을 기본 시간 및 값과 함께 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="9e022-284">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-284">Section</span></span> | <span data-ttu-id="9e022-285">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-286">시간</span><span class="sxs-lookup"><span data-stu-id="9e022-286">Time</span></span> | <span data-ttu-id="9e022-287">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-287">Float32</span></span> |
| <span data-ttu-id="9e022-288">값</span><span class="sxs-lookup"><span data-stu-id="9e022-288">Value</span></span> | <span data-ttu-id="9e022-289">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-289">Float32</span></span> |
| <span data-ttu-id="9e022-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="9e022-290">InTangent</span></span> | <span data-ttu-id="9e022-291">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-291">Float32</span></span> |
| <span data-ttu-id="9e022-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="9e022-292">OutTangent</span></span> | <span data-ttu-id="9e022-293">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-293">Float32</span></span> |
| <span data-ttu-id="9e022-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="9e022-294">InWeight</span></span> | <span data-ttu-id="9e022-295">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-295">Float32</span></span> |
| <span data-ttu-id="9e022-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="9e022-296">OutWeight</span></span> | <span data-ttu-id="9e022-297">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-297">Float32</span></span> |
| <span data-ttu-id="9e022-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="9e022-298">WeightedMode</span></span> | <span data-ttu-id="9e022-299">Int32, [가중 모드](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="9e022-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="9e022-300">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="9e022-300">Boolean curve</span></span>

<span data-ttu-id="9e022-301">부울 곡선은 설정/해제 값의 단순 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="9e022-302">모든 키 프레임에서 곡선의 값이 즉시 대칭 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="9e022-303">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-303">Section</span></span> | <span data-ttu-id="9e022-304">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-305">래핑 전 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="9e022-306">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9e022-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9e022-307">줄 바꿈 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-307">Post-Wrap Mode</span></span> | <span data-ttu-id="9e022-308">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9e022-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9e022-309">키 프레임 수</span><span class="sxs-lookup"><span data-stu-id="9e022-309">Number of keyframes</span></span> | <span data-ttu-id="9e022-310">Int32</span><span class="sxs-lookup"><span data-stu-id="9e022-310">Int32</span></span> |
| <span data-ttu-id="9e022-311">키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-311">Keyframes</span></span> | [<span data-ttu-id="9e022-312">부울 키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="9e022-313">부울 키 프레임</span><span class="sxs-lookup"><span data-stu-id="9e022-313">Boolean keyframe</span></span>

<span data-ttu-id="9e022-314">부울 키프레임은 시간 및 값만 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="9e022-315">섹션</span><span class="sxs-lookup"><span data-stu-id="9e022-315">Section</span></span> | <span data-ttu-id="9e022-316">형식</span><span class="sxs-lookup"><span data-stu-id="9e022-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="9e022-317">시간</span><span class="sxs-lookup"><span data-stu-id="9e022-317">Time</span></span> | <span data-ttu-id="9e022-318">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-318">Float32</span></span> |
| <span data-ttu-id="9e022-319">값</span><span class="sxs-lookup"><span data-stu-id="9e022-319">Value</span></span> | <span data-ttu-id="9e022-320">Float32</span><span class="sxs-lookup"><span data-stu-id="9e022-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="9e022-321">줄 바꿈 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-321">Wrap mode</span></span>

<span data-ttu-id="9e022-322">사전 및 사후 줄 바꿈 모드의 의미 체계는 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 정의를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="9e022-323">다음 비트의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="9e022-324">값</span><span class="sxs-lookup"><span data-stu-id="9e022-324">Value</span></span> | <span data-ttu-id="9e022-325">의미</span><span class="sxs-lookup"><span data-stu-id="9e022-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="9e022-326">0</span><span class="sxs-lookup"><span data-stu-id="9e022-326">0</span></span> | <span data-ttu-id="9e022-327">기본값: 높게 설정 된 기본 반복 모드를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="9e022-328">1</span><span class="sxs-lookup"><span data-stu-id="9e022-328">1</span></span> | <span data-ttu-id="9e022-329">한 번: 시간이 애니메이션 클립의 끝에 도달 하면 클립이 자동으로 재생을 중지 하 고 시간이 클립의 시작 부분으로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="9e022-330">2</span><span class="sxs-lookup"><span data-stu-id="9e022-330">2</span></span> | <span data-ttu-id="9e022-331">Loop: 시간이 애니메이션 클립의 끝에 도달 하면 시작 시 시간이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="9e022-332">4</span><span class="sxs-lookup"><span data-stu-id="9e022-332">4</span></span> | <span data-ttu-id="9e022-333">PingPong: 시간이 애니메이션 클립의 끝에 도달 하면 time은 시작과 끝 사이에 ping를 다시 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="9e022-334">8</span><span class="sxs-lookup"><span data-stu-id="9e022-334">8</span></span> | <span data-ttu-id="9e022-335">ClampForever: 애니메이션을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="9e022-336">끝에 도달 하면 마지막 프레임을 계속 재생 하 고 재생을 중지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="9e022-337">가 중 모드</span><span class="sxs-lookup"><span data-stu-id="9e022-337">Weighted mode</span></span>

<span data-ttu-id="9e022-338">가중치가 적용 되는 모드의 의미 체계는 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 정의를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="9e022-339">값</span><span class="sxs-lookup"><span data-stu-id="9e022-339">Value</span></span> | <span data-ttu-id="9e022-340">의미</span><span class="sxs-lookup"><span data-stu-id="9e022-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="9e022-341">0</span><span class="sxs-lookup"><span data-stu-id="9e022-341">0</span></span> | <span data-ttu-id="9e022-342">None: 곡선 세그먼트를 계산할 때 inWeight 또는 outWeight를 모두 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="9e022-343">1</span><span class="sxs-lookup"><span data-stu-id="9e022-343">1</span></span> | <span data-ttu-id="9e022-344">In: 이전 곡선 세그먼트를 계산할 때 inWeight를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="9e022-345">2</span><span class="sxs-lookup"><span data-stu-id="9e022-345">2</span></span> | <span data-ttu-id="9e022-346">Out: 다음 곡선 세그먼트를 계산할 때 outWeight를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="9e022-347">3</span><span class="sxs-lookup"><span data-stu-id="9e022-347">3</span></span> | <span data-ttu-id="9e022-348">Both: 곡선 세그먼트를 계산할 때 inWeight와 outWeight를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e022-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
