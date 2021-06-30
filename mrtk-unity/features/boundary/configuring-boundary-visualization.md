---
title: 경계 시각화 구성
description: MRTK에서 경계 시스템을 구성하는 세부 정보
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121251"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="3fee7-104">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="3fee7-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="3fee7-105">*경계 시각화 프로필은 경계* 시스템에 대한 시각적 개체 및 기타 관련 매개 변수를 구성하기 위한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="3fee7-106">경계 시각화는 장면의 Mixed Reality Playspace 개체에 연결되고 사용자와 원격 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="3fee7-107">일반 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-107">General settings</span></span>

![경계 시각화 일반 설정](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="3fee7-109">경계 높이</span><span class="sxs-lookup"><span data-stu-id="3fee7-109">Boundary height</span></span>

<span data-ttu-id="3fee7-110">경계 높이는 경계 상한이 렌더링되어야 하는 바닥 평면 위의 거리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="3fee7-111">기본값은 3미터입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="3fee7-112">바닥 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-112">Floor settings</span></span>

![경계 시각화 바닥 설정](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="3fee7-114">**표시**</span><span class="sxs-lookup"><span data-stu-id="3fee7-114">**Show**</span></span>

<span data-ttu-id="3fee7-115">평면을 만들고 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="3fee7-116">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-116">The default value is true.</span></span>

<span data-ttu-id="3fee7-117">**재질**</span><span class="sxs-lookup"><span data-stu-id="3fee7-117">**Material**</span></span>

<span data-ttu-id="3fee7-118">평면을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="3fee7-119">**규모**</span><span class="sxs-lookup"><span data-stu-id="3fee7-119">**Scale**</span></span>

<span data-ttu-id="3fee7-120">만들 평면의 크기(미터)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="3fee7-121">기본 배율 3 미터 x 3 미터 제곱입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="3fee7-122">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="3fee7-122">**Physics Layer**</span></span>

<span data-ttu-id="3fee7-123">평면을 설정해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="3fee7-124">기본값은 *기본* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="3fee7-125">재생 영역 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-125">Play area settings</span></span>

![경계 시각화 재생 영역 설정](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="3fee7-127">**표시**</span><span class="sxs-lookup"><span data-stu-id="3fee7-127">**Show**</span></span>

<span data-ttu-id="3fee7-128">재생 영역 사각형을 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="3fee7-129">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-129">The default value is true.</span></span>

<span data-ttu-id="3fee7-130">**재질**</span><span class="sxs-lookup"><span data-stu-id="3fee7-130">**Material**</span></span>

<span data-ttu-id="3fee7-131">재생 영역 개체를 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="3fee7-132">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="3fee7-132">**Physics Layer**</span></span>

<span data-ttu-id="3fee7-133">재생 영역을 설정해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="3fee7-134">기본값은 *Raycast 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="3fee7-135">추적된 영역 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-135">Tracked area settings</span></span>

![경계 시각화 추적 영역 설정](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="3fee7-137">**표시**</span><span class="sxs-lookup"><span data-stu-id="3fee7-137">**Show**</span></span>

<span data-ttu-id="3fee7-138">추적된 영역의 윤곽선을 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="3fee7-139">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-139">The default value is true.</span></span>

<span data-ttu-id="3fee7-140">**재질**</span><span class="sxs-lookup"><span data-stu-id="3fee7-140">**Material**</span></span>

<span data-ttu-id="3fee7-141">추적된 영역 윤곽선을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="3fee7-142">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="3fee7-142">**Physics Layer**</span></span>

<span data-ttu-id="3fee7-143">추적된 영역을 설정해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="3fee7-144">기본값은 *Raycast 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="3fee7-145">경계 벽 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-145">Boundary wall settings</span></span>

![경계 시각화 경계 벽 설정](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="3fee7-147">**표시**</span><span class="sxs-lookup"><span data-stu-id="3fee7-147">**Show**</span></span>

<span data-ttu-id="3fee7-148">경계 벽면을 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="3fee7-149">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-149">The default value is false.</span></span>

<span data-ttu-id="3fee7-150">**재질**</span><span class="sxs-lookup"><span data-stu-id="3fee7-150">**Material**</span></span>

<span data-ttu-id="3fee7-151">경계 벽면을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="3fee7-152">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="3fee7-152">**Physics Layer**</span></span>

<span data-ttu-id="3fee7-153">경계 벽이 설정되어야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="3fee7-154">기본값은 *Raycast 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="3fee7-155">경계 벽 구성 요소를 *Raycast 무시* 이외의 물리학 계층으로 설정하면 사용자가 장면 내의 개체와 상호 작용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="3fee7-156">경계 상한 설정</span><span class="sxs-lookup"><span data-stu-id="3fee7-156">Boundary ceiling settings</span></span>

![경계 시각화 경계 상한 설정](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="3fee7-158">**표시**</span><span class="sxs-lookup"><span data-stu-id="3fee7-158">**Show**</span></span>

<span data-ttu-id="3fee7-159">경계 최대 평면을 만들어 장면에 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="3fee7-160">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-160">The default value is false.</span></span>

<span data-ttu-id="3fee7-161">**재질**</span><span class="sxs-lookup"><span data-stu-id="3fee7-161">**Material**</span></span>

<span data-ttu-id="3fee7-162">경계 상한 평면을 만들 때 사용해야 하는 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="3fee7-163">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="3fee7-163">**Physics Layer**</span></span>

<span data-ttu-id="3fee7-164">경계 벽이 설정되어야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="3fee7-165">기본값은 *Raycast 무시* 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="3fee7-166">경계 최대값 구성 요소를 *Raycast 무시* 이외의 물리학 계층으로 설정하면 사용자가 장면 내의 개체와 상호 작용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fee7-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fee7-167">참조</span><span class="sxs-lookup"><span data-stu-id="3fee7-167">See also</span></span>

- [<span data-ttu-id="3fee7-168">경계 API 설명서</span><span class="sxs-lookup"><span data-stu-id="3fee7-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="3fee7-169">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="3fee7-169">Boundary System</span></span>](boundary-system-getting-started.md)
