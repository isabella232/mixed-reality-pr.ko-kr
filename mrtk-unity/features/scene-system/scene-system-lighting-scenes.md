---
title: 장면 시스템 조명 장면
description: 장면의 조명 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144413"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="dd60b-104">조명 장면 작업</span><span class="sxs-lookup"><span data-stu-id="dd60b-104">Lighting scene operations</span></span>

<span data-ttu-id="dd60b-105">프로필에 정의 된 기본 조명 장면을 시작할 때 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="dd60b-106">가 호출 될 때까지 조명 장면이 로드 된 상태로 유지 됩니다 `SetLightingScene` .</span><span class="sxs-lookup"><span data-stu-id="dd60b-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="dd60b-107">조명 설정 전환</span><span class="sxs-lookup"><span data-stu-id="dd60b-107">Lighting setting transitions</span></span>

<span data-ttu-id="dd60b-108">`transitionType` 새 조명 장면으로 전환 스타일을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="dd60b-109">사용 가능한 스타일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-109">The available styles are:</span></span>

<span data-ttu-id="dd60b-110">유형</span><span class="sxs-lookup"><span data-stu-id="dd60b-110">Type</span></span> | <span data-ttu-id="dd60b-111">설명</span><span class="sxs-lookup"><span data-stu-id="dd60b-111">Description</span></span> | <span data-ttu-id="dd60b-112">Duration</span><span class="sxs-lookup"><span data-stu-id="dd60b-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="dd60b-113">없음</span><span class="sxs-lookup"><span data-stu-id="dd60b-113">None</span></span> | <span data-ttu-id="dd60b-114">이전 조명 장면을 언로드하고 새 조명 장면을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="dd60b-115">전환 없음.</span><span class="sxs-lookup"><span data-stu-id="dd60b-115">No transition.</span></span> | <span data-ttu-id="dd60b-116">무시됨</span><span class="sxs-lookup"><span data-stu-id="dd60b-116">Ignored</span></span>
<span data-ttu-id="dd60b-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="dd60b-117">FadeToBlack</span></span> | <span data-ttu-id="dd60b-118">이전 조명 장면을 검정으로 페이드 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="dd60b-119">새 조명 장면이 로드 된 후 검정에서 페이드 인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="dd60b-120">위치 간의 원활한 전환을 위해 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="dd60b-121">사용됨</span><span class="sxs-lookup"><span data-stu-id="dd60b-121">Used</span></span>
<span data-ttu-id="dd60b-122">전환</span><span class="sxs-lookup"><span data-stu-id="dd60b-122">CrossFade</span></span> | <span data-ttu-id="dd60b-123">이전 조명 장면을 새 조명 장면을 페이드 아웃 하는 동안 페이드 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="dd60b-124">동일한 위치에서 조명 기능을 매끄럽게 전환 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="dd60b-125">사용됨</span><span class="sxs-lookup"><span data-stu-id="dd60b-125">Used</span></span>

<span data-ttu-id="dd60b-126">전환 중에는 일부 조명 설정을 보간 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="dd60b-127">부드러운 시각적 전환을 원할 경우 이러한 설정은 조명 장면 간에 일관 되 게 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd60b-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="dd60b-128">설정</span><span class="sxs-lookup"><span data-stu-id="dd60b-128">Setting</span></span> | <span data-ttu-id="dd60b-129">부드러운 FadeToBlack 전환</span><span class="sxs-lookup"><span data-stu-id="dd60b-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="dd60b-130">부드러운 교차 전환 전환</span><span class="sxs-lookup"><span data-stu-id="dd60b-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="dd60b-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="dd60b-131">Skybox</span></span> | <span data-ttu-id="dd60b-132">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-132">No</span></span> | <span data-ttu-id="dd60b-133">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-133">No</span></span>
<span data-ttu-id="dd60b-134">사용자 지정 리플렉션</span><span class="sxs-lookup"><span data-stu-id="dd60b-134">Custom Reflections</span></span> | <span data-ttu-id="dd60b-135">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-135">No</span></span> | <span data-ttu-id="dd60b-136">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-136">No</span></span>
<span data-ttu-id="dd60b-137">태양 광원 실시간 그림자</span><span class="sxs-lookup"><span data-stu-id="dd60b-137">Sun light realtime shadows</span></span> | <span data-ttu-id="dd60b-138">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-138">Yes</span></span> | <span data-ttu-id="dd60b-139">예</span><span class="sxs-lookup"><span data-stu-id="dd60b-139">No</span></span>
