---
title: 장면 시스템 콘텐츠 로드
description: MRTK를 통해 장면 시스템을 로드하는 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177579"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="bdf30-104">장면 시스템 콘텐츠 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-104">Scene system content loading</span></span>

<span data-ttu-id="bdf30-105">모든 콘텐츠 로드 작업은 비동기적이며 기본적으로 모든 콘텐츠 로드는 가산적입니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="bdf30-106">관리자 및 조명 장면에는 콘텐츠 로드 작업의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="bdf30-107">부하 진행률 및 장면 활성화 모니터링에 대한 자세한 내용은 [콘텐츠 로드 모니터링을 참조하세요.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="bdf30-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="bdf30-108">콘텐츠 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-108">Loading content</span></span>

<span data-ttu-id="bdf30-109">콘텐츠 장면을 로드하려면 메서드를 사용합니다. `LoadContent`</span><span class="sxs-lookup"><span data-stu-id="bdf30-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="bdf30-110">단일 장면 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-110">Single scene loading</span></span>

<span data-ttu-id="bdf30-111">단일 장면 로드에 해당하는 는 선택적 인수를 통해 달성할 수 `mode` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="bdf30-112">`LoadSceneMode.Single` 는 로드를 계속하기 전에 먼저 로드된 모든 콘텐츠 장면을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="bdf30-113">다음/이전 장면 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-113">Next / previous scene loading</span></span>

<span data-ttu-id="bdf30-114">콘텐츠는 빌드 인덱스 순으로 로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="bdf30-115">이는 사용자가 일련의 데모 장면을 하나씩 안내하는 애플리케이션을 소개하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![플레이어 설정에서 빌드의 현재 장면](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="bdf30-117">다음/prev 콘텐츠 로드는 기본적으로 LoadSceneMode.Single을 사용하여 이전 콘텐츠가 언로드되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="bdf30-118">`PrevContentExists` 는 현재 로드된 가장 낮은 빌드 인덱스보다 낮은 빌드 인덱스 가 있는 콘텐츠 장면이 하나 이상 있는 경우 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="bdf30-119">`NextContentExists` 는 현재 로드된 가장 높은 빌드 인덱스보다 높은 빌드 인덱스 가 있는 콘텐츠 장면이 하나 이상 있는 경우 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="bdf30-120">`wrap`인수가 true이면 콘텐츠가 첫 번째/마지막 빌드 인덱스로 다시 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="bdf30-121">이렇게 하면 다음/이전 콘텐츠를 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="bdf30-122">태그로 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-122">Loading by tag</span></span>

![태그로 콘텐츠 장면 로드](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="bdf30-124">콘텐츠 장면을 그룹으로 로드하는 것이 바람직한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="bdf30-125">예를 들어 환경의 단계는 여러 장면으로 구성될 수 있으며, 이 모든 단계는 작동하기 위해 동시에 로드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="bdf30-126">이를 용이하게 하기 위해 장면에 태그를 적용한 다음 로드하거나 해당 태그를 사용하여 언로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="bdf30-127">태그로 로드하는 것은 스크립트를 수정하지 않고도 경험에서 요소를 통합/제거하려는 경우에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="bdf30-128">예를 들어 다음 두 태그 집합을 사용하여 이 스크립트를 실행하면 다른 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="bdf30-129">콘텐츠 테스트</span><span class="sxs-lookup"><span data-stu-id="bdf30-129">Testing content</span></span>

<span data-ttu-id="bdf30-130">장면 이름</span><span class="sxs-lookup"><span data-stu-id="bdf30-130">Scene Name</span></span> | <span data-ttu-id="bdf30-131">장면 태그</span><span class="sxs-lookup"><span data-stu-id="bdf30-131">Scene Tag</span></span> | <span data-ttu-id="bdf30-132">스크립트로 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="bdf30-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="bdf30-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="bdf30-134">지형</span><span class="sxs-lookup"><span data-stu-id="bdf30-134">Terrain</span></span> | <span data-ttu-id="bdf30-135">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-135">•</span></span>
<span data-ttu-id="bdf30-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="bdf30-136">StructureTesting</span></span> | <span data-ttu-id="bdf30-137">구조체</span><span class="sxs-lookup"><span data-stu-id="bdf30-137">Structures</span></span> | <span data-ttu-id="bdf30-138">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-138">•</span></span>
<span data-ttu-id="bdf30-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="bdf30-139">VegetationTools</span></span> | <span data-ttu-id="bdf30-140">식물</span><span class="sxs-lookup"><span data-stu-id="bdf30-140">Vegetation</span></span> | <span data-ttu-id="bdf30-141">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-141">•</span></span>
<span data-ttu-id="bdf30-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="bdf30-142">Mountain</span></span> | <span data-ttu-id="bdf30-143">지형</span><span class="sxs-lookup"><span data-stu-id="bdf30-143">Terrain</span></span> | <span data-ttu-id="bdf30-144">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-144">•</span></span>
<span data-ttu-id="bdf30-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="bdf30-145">Cabin</span></span> | <span data-ttu-id="bdf30-146">구조체</span><span class="sxs-lookup"><span data-stu-id="bdf30-146">Structures</span></span> | <span data-ttu-id="bdf30-147">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-147">•</span></span>
<span data-ttu-id="bdf30-148">Trees</span><span class="sxs-lookup"><span data-stu-id="bdf30-148">Trees</span></span> | <span data-ttu-id="bdf30-149">식물</span><span class="sxs-lookup"><span data-stu-id="bdf30-149">Vegetation</span></span> | <span data-ttu-id="bdf30-150">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="bdf30-151">최종 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="bdf30-151">Final content</span></span>

<span data-ttu-id="bdf30-152">장면 이름</span><span class="sxs-lookup"><span data-stu-id="bdf30-152">Scene Name</span></span> | <span data-ttu-id="bdf30-153">장면 태그</span><span class="sxs-lookup"><span data-stu-id="bdf30-153">Scene Tag</span></span> | <span data-ttu-id="bdf30-154">스크립트로 로드</span><span class="sxs-lookup"><span data-stu-id="bdf30-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="bdf30-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="bdf30-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="bdf30-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="bdf30-156">DoNotInclude</span></span> |
<span data-ttu-id="bdf30-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="bdf30-157">StructureTesting</span></span> | <span data-ttu-id="bdf30-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="bdf30-158">DoNotInclude</span></span> |
<span data-ttu-id="bdf30-159">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="bdf30-159">VegetationTools</span></span> | <span data-ttu-id="bdf30-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="bdf30-160">DoNotInclude</span></span> |
<span data-ttu-id="bdf30-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="bdf30-161">Mountain</span></span> | <span data-ttu-id="bdf30-162">지형</span><span class="sxs-lookup"><span data-stu-id="bdf30-162">Terrain</span></span> | <span data-ttu-id="bdf30-163">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-163">•</span></span>
<span data-ttu-id="bdf30-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="bdf30-164">Cabin</span></span> | <span data-ttu-id="bdf30-165">구조체</span><span class="sxs-lookup"><span data-stu-id="bdf30-165">Structures</span></span> | <span data-ttu-id="bdf30-166">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-166">•</span></span>
<span data-ttu-id="bdf30-167">Trees</span><span class="sxs-lookup"><span data-stu-id="bdf30-167">Trees</span></span> | <span data-ttu-id="bdf30-168">식물</span><span class="sxs-lookup"><span data-stu-id="bdf30-168">Vegetation</span></span> | <span data-ttu-id="bdf30-169">•</span><span class="sxs-lookup"><span data-stu-id="bdf30-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="bdf30-170">편집기 동작</span><span class="sxs-lookup"><span data-stu-id="bdf30-170">Editor behavior</span></span>

<span data-ttu-id="bdf30-171">장면 시스템의 [서비스 검사기를](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용하여 편집기 및 재생 모드에서 이러한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="bdf30-172">편집 모드에서는 장면 로드가 즉시 진행되지만 재생 모드에서는 로드 진행 상황을 관찰하고 [활성화 토큰을](scene-system-load-progress.md) 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdf30-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![콘텐츠 로드가 강조 표시된 검사자의 장면 시스템](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
