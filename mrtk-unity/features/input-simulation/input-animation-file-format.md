---
title: 입력 애니메이션 파일 형식
description: MRTK의 입력 애니메이션 이진 파일 형식 사양에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145123"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="e3646-104">입력 애니메이션 이진 파일 형식 사양</span><span class="sxs-lookup"><span data-stu-id="e3646-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="e3646-105">전체 구조</span><span class="sxs-lookup"><span data-stu-id="e3646-105">Overall structure</span></span>

<span data-ttu-id="e3646-106">입력 애니메이션 이진 파일은 64비트 정수 매직 넘버로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="e3646-107">16진수 표기에서 이 숫자의 값은 `0x6a8faf6e0f9e42c6` 이며 유효한 입력 애니메이션 파일을 식별하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="e3646-108">다음 8바이트는 파일의 주 버전 및 부 버전 번호를 선언하는 두 개의 Int32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="e3646-109">파일의 나머지 부분은 버전 번호 간에 변경 될 수 있는 애니메이션 데이터에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="e3646-110">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-110">Section</span></span> | <span data-ttu-id="e3646-111">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-112">매직 넘버</span><span class="sxs-lookup"><span data-stu-id="e3646-112">Magic Number</span></span> | <span data-ttu-id="e3646-113">Int64</span><span class="sxs-lookup"><span data-stu-id="e3646-113">Int64</span></span> |
| <span data-ttu-id="e3646-114">주 버전 번호</span><span class="sxs-lookup"><span data-stu-id="e3646-114">Major Version Number</span></span> | <span data-ttu-id="e3646-115">Int32</span><span class="sxs-lookup"><span data-stu-id="e3646-115">Int32</span></span> |
| <span data-ttu-id="e3646-116">부 버전 번호</span><span class="sxs-lookup"><span data-stu-id="e3646-116">Minor Version Number</span></span> | <span data-ttu-id="e3646-117">Int32</span><span class="sxs-lookup"><span data-stu-id="e3646-117">Int32</span></span> |
| <span data-ttu-id="e3646-118">애니메이션 데이터</span><span class="sxs-lookup"><span data-stu-id="e3646-118">Animation Data</span></span> | <span data-ttu-id="e3646-119">_버전 섹션 참조_</span><span class="sxs-lookup"><span data-stu-id="e3646-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="e3646-120">버전 1.1</span><span class="sxs-lookup"><span data-stu-id="e3646-120">Version 1.1</span></span>

<span data-ttu-id="e3646-121">입력 애니메이션 데이터는 애니메이션에 카메라, 손 및 시선 응시 데이터와 애니메이션 곡선 시퀀스가 포함되는지 여부를 나타내는 세 개의 부울 값으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="e3646-122">존재하는 곡선은 이러한 부울의 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="e3646-123">각 곡선에는 서로 다른 수의 키 프레임이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="e3646-124">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-124">Section</span></span> | <span data-ttu-id="e3646-125">Type</span><span class="sxs-lookup"><span data-stu-id="e3646-125">Type</span></span> | <span data-ttu-id="e3646-126">참고</span><span class="sxs-lookup"><span data-stu-id="e3646-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="e3646-127">카메라 자세가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-127">Has Camera Pose</span></span> | <span data-ttu-id="e3646-128">부울</span><span class="sxs-lookup"><span data-stu-id="e3646-128">Boolean</span></span> | |
| <span data-ttu-id="e3646-129">손 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="e3646-129">Has Hand Data</span></span> | <span data-ttu-id="e3646-130">부울</span><span class="sxs-lookup"><span data-stu-id="e3646-130">Boolean</span></span> | |
| <span data-ttu-id="e3646-131">시선 응시</span><span class="sxs-lookup"><span data-stu-id="e3646-131">Has Eye Gaze</span></span>| <span data-ttu-id="e3646-132">부울</span><span class="sxs-lookup"><span data-stu-id="e3646-132">Boolean</span></span> | |
| <span data-ttu-id="e3646-133">카메라</span><span class="sxs-lookup"><span data-stu-id="e3646-133">Camera</span></span> | [<span data-ttu-id="e3646-134">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="e3646-135">카메라 자세가 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="e3646-136">왼쪽 추적</span><span class="sxs-lookup"><span data-stu-id="e3646-136">Hand Tracked Left</span></span> | [<span data-ttu-id="e3646-137">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="e3646-138">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-139">직접 추적 권한</span><span class="sxs-lookup"><span data-stu-id="e3646-139">Hand Tracked Right</span></span> | [<span data-ttu-id="e3646-140">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="e3646-141">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-142">손 집기 Left</span><span class="sxs-lookup"><span data-stu-id="e3646-142">Hand Pinching Left</span></span> | [<span data-ttu-id="e3646-143">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="e3646-144">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-145">손 집기 Right</span><span class="sxs-lookup"><span data-stu-id="e3646-145">Hand Pinching Right</span></span> | [<span data-ttu-id="e3646-146">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="e3646-147">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-148">왼쪽 조인트</span><span class="sxs-lookup"><span data-stu-id="e3646-148">Hand Joints Left</span></span> | [<span data-ttu-id="e3646-149">조인트 포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="e3646-150">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-151">직접 조인트</span><span class="sxs-lookup"><span data-stu-id="e3646-151">Hand Joints Right</span></span> | [<span data-ttu-id="e3646-152">조인트 포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="e3646-153">가 손 데이터를 만족 하는 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="e3646-154">아이 응시</span><span class="sxs-lookup"><span data-stu-id="e3646-154">Eye Gaze</span></span> | <span data-ttu-id="e3646-155">[광선 곡선](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="e3646-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="e3646-156">시선 응시가 true인 경우에만</span><span class="sxs-lookup"><span data-stu-id="e3646-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="e3646-157">버전 1.0</span><span class="sxs-lookup"><span data-stu-id="e3646-157">Version 1.0</span></span>

<span data-ttu-id="e3646-158">입력 애니메이션 데이터는 애니메이션 곡선 시퀀스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="e3646-159">애니메이션 곡선의 수와 의미는 고정되어 있지만 각 곡선에는 서로 다른 수의 키 프레임이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="e3646-160">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-160">Section</span></span> | <span data-ttu-id="e3646-161">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-162">카메라</span><span class="sxs-lookup"><span data-stu-id="e3646-162">Camera</span></span> | [<span data-ttu-id="e3646-163">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-164">왼쪽에서 손 추적</span><span class="sxs-lookup"><span data-stu-id="e3646-164">Hand Tracked Left</span></span> | [<span data-ttu-id="e3646-165">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="e3646-166">직접 추적 오른쪽</span><span class="sxs-lookup"><span data-stu-id="e3646-166">Hand Tracked Right</span></span> | [<span data-ttu-id="e3646-167">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="e3646-168">왼쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="e3646-168">Hand Pinching Left</span></span> | [<span data-ttu-id="e3646-169">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="e3646-170">오른쪽 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="e3646-170">Hand Pinching Right</span></span> | [<span data-ttu-id="e3646-171">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="e3646-172">왼쪽 손 조인트</span><span class="sxs-lookup"><span data-stu-id="e3646-172">Hand Joints Left</span></span> | [<span data-ttu-id="e3646-173">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="e3646-174">손 조인트 오른쪽</span><span class="sxs-lookup"><span data-stu-id="e3646-174">Hand Joints Right</span></span> | [<span data-ttu-id="e3646-175">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="e3646-176">공동 자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-176">Joint pose curves</span></span>

<span data-ttu-id="e3646-177">각 손의 경우 일련의 조인 애니메이션 곡선이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="e3646-178">조인 수가 고정되고 각 조인에 대해 자세 곡선 집합이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="e3646-179">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-179">Section</span></span> | <span data-ttu-id="e3646-180">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-181">없음</span><span class="sxs-lookup"><span data-stu-id="e3646-181">None</span></span> | [<span data-ttu-id="e3646-182">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-183">손목</span><span class="sxs-lookup"><span data-stu-id="e3646-183">Wrist</span></span> | [<span data-ttu-id="e3646-184">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-185">Palm</span><span class="sxs-lookup"><span data-stu-id="e3646-185">Palm</span></span> | [<span data-ttu-id="e3646-186">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="e3646-188">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="e3646-190">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="e3646-192">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="e3646-193">ThumbTip</span></span> | [<span data-ttu-id="e3646-194">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="e3646-195">IndexMetacarpal</span></span> | [<span data-ttu-id="e3646-196">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="e3646-197">IndexKnuckle</span></span> | [<span data-ttu-id="e3646-198">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="e3646-200">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-201">IndexDistalJoint</span></span> | [<span data-ttu-id="e3646-202">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-203">IndexTip</span><span class="sxs-lookup"><span data-stu-id="e3646-203">IndexTip</span></span> | [<span data-ttu-id="e3646-204">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="e3646-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="e3646-206">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="e3646-207">MiddleKnuckle</span></span> | [<span data-ttu-id="e3646-208">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="e3646-210">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="e3646-212">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="e3646-213">MiddleTip</span></span> | [<span data-ttu-id="e3646-214">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="e3646-215">RingMetacarpal</span></span> | [<span data-ttu-id="e3646-216">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="e3646-217">RingKnuckle</span></span> | [<span data-ttu-id="e3646-218">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-219">RingMiddleJoint</span></span> | [<span data-ttu-id="e3646-220">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-221">RingDistalJoint</span></span> | [<span data-ttu-id="e3646-222">자세 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="e3646-223">RingTip</span></span> | [<span data-ttu-id="e3646-224">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="e3646-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="e3646-226">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-227">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="e3646-227">PinkyKnuckle</span></span> | [<span data-ttu-id="e3646-228">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="e3646-230">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="e3646-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="e3646-232">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="e3646-233">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="e3646-233">PinkyTip</span></span> | [<span data-ttu-id="e3646-234">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="e3646-235">포즈 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-235">Pose curves</span></span>

<span data-ttu-id="e3646-236">포즈 곡선은 회전 4 원수에 대 한 4 개의 애니메이션 곡선 뒤에 위치 벡터에 대 한 3 개의 애니메이션 곡선의 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="e3646-237">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-237">Section</span></span> | <span data-ttu-id="e3646-238">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-239">X 위치</span><span class="sxs-lookup"><span data-stu-id="e3646-239">Position X</span></span> | [<span data-ttu-id="e3646-240">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-241">Y 위치</span><span class="sxs-lookup"><span data-stu-id="e3646-241">Position Y</span></span> | [<span data-ttu-id="e3646-242">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-243">Z 위치</span><span class="sxs-lookup"><span data-stu-id="e3646-243">Position Z</span></span> | [<span data-ttu-id="e3646-244">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-245">회전 X</span><span class="sxs-lookup"><span data-stu-id="e3646-245">Rotation X</span></span> | [<span data-ttu-id="e3646-246">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-247">회전 Y</span><span class="sxs-lookup"><span data-stu-id="e3646-247">Rotation Y</span></span> | [<span data-ttu-id="e3646-248">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-249">회전 Z</span><span class="sxs-lookup"><span data-stu-id="e3646-249">Rotation Z</span></span> | [<span data-ttu-id="e3646-250">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-251">회전 W</span><span class="sxs-lookup"><span data-stu-id="e3646-251">Rotation W</span></span> | [<span data-ttu-id="e3646-252">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="e3646-253">광선 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-253">Ray curves</span></span>

<span data-ttu-id="e3646-254">광선 곡선은 원점 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 방향 벡터에 대해 3개의 애니메이션 곡선이 잇는 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="e3646-255">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-255">Section</span></span> | <span data-ttu-id="e3646-256">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-257">원본 X</span><span class="sxs-lookup"><span data-stu-id="e3646-257">Origin X</span></span> | [<span data-ttu-id="e3646-258">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-259">원본 Y</span><span class="sxs-lookup"><span data-stu-id="e3646-259">Origin Y</span></span> | [<span data-ttu-id="e3646-260">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-261">원본 Z</span><span class="sxs-lookup"><span data-stu-id="e3646-261">Origin Z</span></span> | [<span data-ttu-id="e3646-262">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-263">Direction X</span><span class="sxs-lookup"><span data-stu-id="e3646-263">Direction X</span></span> | [<span data-ttu-id="e3646-264">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-265">Direction Y</span><span class="sxs-lookup"><span data-stu-id="e3646-265">Direction Y</span></span> | [<span data-ttu-id="e3646-266">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="e3646-267">방향 Z</span><span class="sxs-lookup"><span data-stu-id="e3646-267">Direction Z</span></span> | [<span data-ttu-id="e3646-268">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="e3646-269">Float 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-269">Float curve</span></span>

<span data-ttu-id="e3646-270">부동 소수점 곡선은 여러 개의 키 프레임을 사용 하는 완벽 한 베 지 어 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="e3646-271">각 키프레임에는 시간과 곡선 값 뿐만 아니라 각 키 프레임의 왼쪽과 오른쪽에 접선 및 가중치가 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="e3646-272">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-272">Section</span></span> | <span data-ttu-id="e3646-273">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-274">래핑 전 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="e3646-275">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="e3646-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="e3646-276">줄 바꿈 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-276">Post-Wrap Mode</span></span> | <span data-ttu-id="e3646-277">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="e3646-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="e3646-278">키 프레임 수</span><span class="sxs-lookup"><span data-stu-id="e3646-278">Number of keyframes</span></span> | <span data-ttu-id="e3646-279">Int32</span><span class="sxs-lookup"><span data-stu-id="e3646-279">Int32</span></span> |
| <span data-ttu-id="e3646-280">키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-280">Keyframes</span></span> | [<span data-ttu-id="e3646-281">Float 키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="e3646-282">Float 키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-282">Float keyframe</span></span>

<span data-ttu-id="e3646-283">Float 키프레임은 기본 시간 및 값과 함께 탄젠트 및 가중치 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="e3646-284">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-284">Section</span></span> | <span data-ttu-id="e3646-285">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-286">Time</span><span class="sxs-lookup"><span data-stu-id="e3646-286">Time</span></span> | <span data-ttu-id="e3646-287">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-287">Float32</span></span> |
| <span data-ttu-id="e3646-288">값</span><span class="sxs-lookup"><span data-stu-id="e3646-288">Value</span></span> | <span data-ttu-id="e3646-289">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-289">Float32</span></span> |
| <span data-ttu-id="e3646-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="e3646-290">InTangent</span></span> | <span data-ttu-id="e3646-291">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-291">Float32</span></span> |
| <span data-ttu-id="e3646-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="e3646-292">OutTangent</span></span> | <span data-ttu-id="e3646-293">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-293">Float32</span></span> |
| <span data-ttu-id="e3646-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="e3646-294">InWeight</span></span> | <span data-ttu-id="e3646-295">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-295">Float32</span></span> |
| <span data-ttu-id="e3646-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="e3646-296">OutWeight</span></span> | <span data-ttu-id="e3646-297">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-297">Float32</span></span> |
| <span data-ttu-id="e3646-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="e3646-298">WeightedMode</span></span> | <span data-ttu-id="e3646-299">Int32, [가중치가 적용 모드](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="e3646-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="e3646-300">부울 곡선</span><span class="sxs-lookup"><span data-stu-id="e3646-300">Boolean curve</span></span>

<span data-ttu-id="e3646-301">부울 곡선은 설정/해제 값의 단순 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="e3646-302">모든 키 프레임에서 곡선의 값이 즉시 대칭 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="e3646-303">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-303">Section</span></span> | <span data-ttu-id="e3646-304">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-305">래핑 전 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="e3646-306">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="e3646-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="e3646-307">줄 바꿈 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-307">Post-Wrap Mode</span></span> | <span data-ttu-id="e3646-308">Int32, [Wrap 모드](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="e3646-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="e3646-309">키 프레임 수</span><span class="sxs-lookup"><span data-stu-id="e3646-309">Number of keyframes</span></span> | <span data-ttu-id="e3646-310">Int32</span><span class="sxs-lookup"><span data-stu-id="e3646-310">Int32</span></span> |
| <span data-ttu-id="e3646-311">키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-311">Keyframes</span></span> | [<span data-ttu-id="e3646-312">부울 키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="e3646-313">부울 키 프레임</span><span class="sxs-lookup"><span data-stu-id="e3646-313">Boolean keyframe</span></span>

<span data-ttu-id="e3646-314">부울 키프레임은 시간 및 값만 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="e3646-315">섹션</span><span class="sxs-lookup"><span data-stu-id="e3646-315">Section</span></span> | <span data-ttu-id="e3646-316">유형</span><span class="sxs-lookup"><span data-stu-id="e3646-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="e3646-317">Time</span><span class="sxs-lookup"><span data-stu-id="e3646-317">Time</span></span> | <span data-ttu-id="e3646-318">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-318">Float32</span></span> |
| <span data-ttu-id="e3646-319">값</span><span class="sxs-lookup"><span data-stu-id="e3646-319">Value</span></span> | <span data-ttu-id="e3646-320">Float32</span><span class="sxs-lookup"><span data-stu-id="e3646-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="e3646-321">줄 바꿈 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-321">Wrap mode</span></span>

<span data-ttu-id="e3646-322">사전 및 사후 줄 바꿈 모드의 의미 체계는 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 정의를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="e3646-323">다음 비트의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="e3646-324">값</span><span class="sxs-lookup"><span data-stu-id="e3646-324">Value</span></span> | <span data-ttu-id="e3646-325">의미</span><span class="sxs-lookup"><span data-stu-id="e3646-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="e3646-326">0</span><span class="sxs-lookup"><span data-stu-id="e3646-326">0</span></span> | <span data-ttu-id="e3646-327">기본값: 높게 설정 된 기본 반복 모드를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="e3646-328">1</span><span class="sxs-lookup"><span data-stu-id="e3646-328">1</span></span> | <span data-ttu-id="e3646-329">한 번: 시간이 애니메이션 클립의 끝에 도달 하면 클립이 자동으로 재생을 중지 하 고 시간이 클립의 시작 부분으로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="e3646-330">2</span><span class="sxs-lookup"><span data-stu-id="e3646-330">2</span></span> | <span data-ttu-id="e3646-331">Loop: 시간이 애니메이션 클립의 끝에 도달 하면 시작 시 시간이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="e3646-332">4</span><span class="sxs-lookup"><span data-stu-id="e3646-332">4</span></span> | <span data-ttu-id="e3646-333">PingPong: 시간이 애니메이션 클립의 끝에 도달 하면 time은 시작과 끝 사이에 ping를 다시 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="e3646-334">8</span><span class="sxs-lookup"><span data-stu-id="e3646-334">8</span></span> | <span data-ttu-id="e3646-335">ClampForever: 애니메이션을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="e3646-336">끝에 도달 하면 마지막 프레임을 계속 재생 하 고 재생을 중지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="e3646-337">가 중 모드</span><span class="sxs-lookup"><span data-stu-id="e3646-337">Weighted mode</span></span>

<span data-ttu-id="e3646-338">가중치가 적용 되는 모드의 의미 체계는 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 정의를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="e3646-339">값</span><span class="sxs-lookup"><span data-stu-id="e3646-339">Value</span></span> | <span data-ttu-id="e3646-340">의미</span><span class="sxs-lookup"><span data-stu-id="e3646-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="e3646-341">0</span><span class="sxs-lookup"><span data-stu-id="e3646-341">0</span></span> | <span data-ttu-id="e3646-342">없음: 곡선 세그먼트를 계산할 때 inWeight 또는 outWeight를 모두 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="e3646-343">1</span><span class="sxs-lookup"><span data-stu-id="e3646-343">1</span></span> | <span data-ttu-id="e3646-344">In: 이전 곡선 세그먼트를 계산할 때 inWeight를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="e3646-345">2</span><span class="sxs-lookup"><span data-stu-id="e3646-345">2</span></span> | <span data-ttu-id="e3646-346">Out: 다음 곡선 세그먼트를 계산할 때 outWeight를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="e3646-347">3</span><span class="sxs-lookup"><span data-stu-id="e3646-347">3</span></span> | <span data-ttu-id="e3646-348">둘 다: 곡선 세그먼트를 계산할 때 inWeight 및 outWeight를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e3646-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
