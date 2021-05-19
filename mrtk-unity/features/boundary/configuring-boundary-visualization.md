---
title: 경계 시각화 구성
description: MRTK에서 경계 시스템을 구성하는 세부 정보
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144498"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="dbf6c-104">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="dbf6c-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="dbf6c-105">*경계 시각화 프로필은 경계* 시스템에 대한 시각적 개체 및 기타 관련 매개 변수를 구성하기 위한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="dbf6c-106">경계 시각화는 장면의 Mixed Reality Playspace 개체에 연결되고 사용자와 원격 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="dbf6c-107">일반 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-107">General settings</span></span>

![경계 시각화 일반 설정](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="dbf6c-109">경계 높이</span><span class="sxs-lookup"><span data-stu-id="dbf6c-109">Boundary height</span></span>

<span data-ttu-id="dbf6c-110">경계 높이는 경계 상한이 렌더링되어야 하는 바닥 평면 위의 거리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="dbf6c-111">기본값은 3미터입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="dbf6c-112">바닥 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-112">Floor settings</span></span>

![경계 시각화 바닥 설정](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="dbf6c-114">**표시**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-114">**Show**</span></span>

<span data-ttu-id="dbf6c-115">평면을 만들고 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="dbf6c-116">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-116">The default value is true.</span></span>

<span data-ttu-id="dbf6c-117">**재질**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-117">**Material**</span></span>

<span data-ttu-id="dbf6c-118">평면을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="dbf6c-119">**규모**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-119">**Scale**</span></span>

<span data-ttu-id="dbf6c-120">만들 평면의 크기(미터)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="dbf6c-121">기본 배율 3 미터 x 3 미터 제곱입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="dbf6c-122">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-122">**Physics Layer**</span></span>

<span data-ttu-id="dbf6c-123">평면을 설정해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="dbf6c-124">기본값은 *기본* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="dbf6c-125">재생 영역 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-125">Play area settings</span></span>

![경계 시각화 재생 영역 설정](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="dbf6c-127">**표시**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-127">**Show**</span></span>

<span data-ttu-id="dbf6c-128">재생 영역 사각형을 만들고 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="dbf6c-129">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-129">The default value is true.</span></span>

<span data-ttu-id="dbf6c-130">**재질**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-130">**Material**</span></span>

<span data-ttu-id="dbf6c-131">재생 영역 개체를 만들 때 사용 해야 하는 자료를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="dbf6c-132">**물리 계층**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-132">**Physics Layer**</span></span>

<span data-ttu-id="dbf6c-133">재생 영역을 설정 해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="dbf6c-134">기본값은 *Raycast 계층 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="dbf6c-135">추적 영역 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-135">Tracked area settings</span></span>

![경계 시각화 추적 영역 설정](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="dbf6c-137">**표시**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-137">**Show**</span></span>

<span data-ttu-id="dbf6c-138">추적 영역의 개요를 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="dbf6c-139">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-139">The default value is true.</span></span>

<span data-ttu-id="dbf6c-140">**재질**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-140">**Material**</span></span>

<span data-ttu-id="dbf6c-141">추적 된 영역 개요를 만들 때 사용 해야 하는 자료를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="dbf6c-142">**물리 계층**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-142">**Physics Layer**</span></span>

<span data-ttu-id="dbf6c-143">추적 된 영역을 설정할 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="dbf6c-144">기본값은 *Raycast 계층 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="dbf6c-145">경계 벽 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-145">Boundary wall settings</span></span>

![경계 시각화 경계 벽 설정](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="dbf6c-147">**표시**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-147">**Show**</span></span>

<span data-ttu-id="dbf6c-148">경계 벽 평면을 만들고 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="dbf6c-149">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-149">The default value is false.</span></span>

<span data-ttu-id="dbf6c-150">**재질**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-150">**Material**</span></span>

<span data-ttu-id="dbf6c-151">경계 벽 평면을 만들 때 사용 해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="dbf6c-152">**물리 계층**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-152">**Physics Layer**</span></span>

<span data-ttu-id="dbf6c-153">경계 벽을 설정 해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="dbf6c-154">기본값은 *Raycast 계층 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="dbf6c-155">경계 벽 구성 요소를 *Raycast 무시* 이외의 물리 계층으로 설정 하면 사용자가 장면 내의 개체와 상호 작용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="dbf6c-156">경계 상한 설정</span><span class="sxs-lookup"><span data-stu-id="dbf6c-156">Boundary ceiling settings</span></span>

![경계 시각화 경계 상한 설정](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="dbf6c-158">**표시**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-158">**Show**</span></span>

<span data-ttu-id="dbf6c-159">경계 최대 평면을 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="dbf6c-160">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-160">The default value is false.</span></span>

<span data-ttu-id="dbf6c-161">**재질**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-161">**Material**</span></span>

<span data-ttu-id="dbf6c-162">경계 상한 평면을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="dbf6c-163">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="dbf6c-163">**Physics Layer**</span></span>

<span data-ttu-id="dbf6c-164">경계 벽이 설정되어야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="dbf6c-165">기본값은 *Raycast 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="dbf6c-166">경계 최대값 구성 요소를 *Raycast 무시* 이외의 물리학 계층으로 설정하면 사용자가 장면 내의 개체와 상호 작용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbf6c-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbf6c-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbf6c-167">See also</span></span>

- [<span data-ttu-id="dbf6c-168">경계 API 설명서</span><span class="sxs-lookup"><span data-stu-id="dbf6c-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="dbf6c-169">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="dbf6c-169">Boundary System</span></span>](boundary-system-getting-started.md)
