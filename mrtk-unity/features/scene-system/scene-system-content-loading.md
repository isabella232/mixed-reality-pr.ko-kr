---
title: 장면 시스템 콘텐츠 로드
description: MRTK를 사용 하 여 장면 시스템 로드 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f310b3687a6773404c7a998a3764163daf159857
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145145"
---
# <a name="content-scene-loading"></a><span data-ttu-id="6015f-104">콘텐츠 장면 로드</span><span class="sxs-lookup"><span data-stu-id="6015f-104">Content scene loading</span></span>

<span data-ttu-id="6015f-105">모든 콘텐츠 로드 작업은 비동기적으로 수행 되며 기본적으로 모든 콘텐츠 로드는 누적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="6015f-106">관리자 및 조명 장면을 콘텐츠 로드 작업의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="6015f-107">로드 진행률 및 장면 활성화 모니터링에 대 한 자세한 내용은 [콘텐츠 로드 모니터링](scene-system-load-progress.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6015f-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="6015f-108">콘텐츠 로드 중</span><span class="sxs-lookup"><span data-stu-id="6015f-108">Loading content</span></span>

<span data-ttu-id="6015f-109">콘텐츠 장면을 로드 하려면 메서드를 사용 합니다 `LoadContent` .</span><span class="sxs-lookup"><span data-stu-id="6015f-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="6015f-110">단일 장면 로드</span><span class="sxs-lookup"><span data-stu-id="6015f-110">Single scene loading</span></span>

<span data-ttu-id="6015f-111">단일 장면 로드에 해당 하는 것은 선택적 인수를 통해 구현할 수 있습니다 `mode` .</span><span class="sxs-lookup"><span data-stu-id="6015f-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="6015f-112">`LoadSceneMode.Single` 는 로드를 계속 하기 전에 로드 된 모든 콘텐츠 장면을 먼저 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="6015f-113">다음/이전 장면 로드</span><span class="sxs-lookup"><span data-stu-id="6015f-113">Next / previous scene loading</span></span>

<span data-ttu-id="6015f-114">콘텐츠는 빌드 인덱스의 순서로 단일 로드 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="6015f-115">이는 일련의 데모 장면을 하나씩 통해 사용자를 가져오는 응용 프로그램을 소개 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![플레이어 설정에서 빌드의 현재 장면](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="6015f-117">다음/이전 콘텐츠 로드는 기본적으로 LoadSceneMode를 사용 하 여 이전 콘텐츠가 언로드되는 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="6015f-118">`PrevContentExists` 는 현재 로드 된 가장 낮은 빌드 인덱스 보다 더 낮은 빌드 인덱스를 가진 콘텐츠 장면이 하나 이상 있는 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="6015f-119">`NextContentExists` 는 현재 로드 된 가장 높은 빌드 인덱스 보다 더 높은 빌드 인덱스가 있는 콘텐츠 장면이 하나 이상 있는 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="6015f-120">`wrap`인수가 true 이면 내용이 첫 번째/마지막 빌드 인덱스로 다시 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="6015f-121">이렇게 하면 다음/이전 콘텐츠를 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="6015f-122">태그로 로드</span><span class="sxs-lookup"><span data-stu-id="6015f-122">Loading by tag</span></span>

![태그로 콘텐츠 장면 로드](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="6015f-124">콘텐츠 장면을 그룹으로 로드하는 것이 바람직한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="6015f-125">예를 들어 환경의 단계는 여러 장면으로 구성될 수 있으며, 이 모든 단계는 작동하기 위해 동시에 로드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="6015f-126">이를 용이하게 하기 위해 장면에 태그를 적용한 다음 로드하거나 해당 태그를 사용하여 언로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="6015f-127">태그로 로드하는 것은 스크립트를 수정하지 않고도 경험에서 요소를 통합/제거하려는 경우에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="6015f-128">예를 들어 다음 두 태그 집합을 사용하여 이 스크립트를 실행하면 다른 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="6015f-129">콘텐츠 테스트</span><span class="sxs-lookup"><span data-stu-id="6015f-129">Testing content</span></span>

<span data-ttu-id="6015f-130">장면 이름</span><span class="sxs-lookup"><span data-stu-id="6015f-130">Scene Name</span></span> | <span data-ttu-id="6015f-131">장면 태그</span><span class="sxs-lookup"><span data-stu-id="6015f-131">Scene Tag</span></span> | <span data-ttu-id="6015f-132">스크립트로 로드</span><span class="sxs-lookup"><span data-stu-id="6015f-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="6015f-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="6015f-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="6015f-134">지형</span><span class="sxs-lookup"><span data-stu-id="6015f-134">Terrain</span></span> | <span data-ttu-id="6015f-135">•</span><span class="sxs-lookup"><span data-stu-id="6015f-135">•</span></span>
<span data-ttu-id="6015f-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="6015f-136">StructureTesting</span></span> | <span data-ttu-id="6015f-137">구조체</span><span class="sxs-lookup"><span data-stu-id="6015f-137">Structures</span></span> | <span data-ttu-id="6015f-138">•</span><span class="sxs-lookup"><span data-stu-id="6015f-138">•</span></span>
<span data-ttu-id="6015f-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="6015f-139">VegetationTools</span></span> | <span data-ttu-id="6015f-140">식물</span><span class="sxs-lookup"><span data-stu-id="6015f-140">Vegetation</span></span> | <span data-ttu-id="6015f-141">•</span><span class="sxs-lookup"><span data-stu-id="6015f-141">•</span></span>
<span data-ttu-id="6015f-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="6015f-142">Mountain</span></span> | <span data-ttu-id="6015f-143">지형</span><span class="sxs-lookup"><span data-stu-id="6015f-143">Terrain</span></span> | <span data-ttu-id="6015f-144">•</span><span class="sxs-lookup"><span data-stu-id="6015f-144">•</span></span>
<span data-ttu-id="6015f-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="6015f-145">Cabin</span></span> | <span data-ttu-id="6015f-146">구조체</span><span class="sxs-lookup"><span data-stu-id="6015f-146">Structures</span></span> | <span data-ttu-id="6015f-147">•</span><span class="sxs-lookup"><span data-stu-id="6015f-147">•</span></span>
<span data-ttu-id="6015f-148">Trees</span><span class="sxs-lookup"><span data-stu-id="6015f-148">Trees</span></span> | <span data-ttu-id="6015f-149">식물</span><span class="sxs-lookup"><span data-stu-id="6015f-149">Vegetation</span></span> | <span data-ttu-id="6015f-150">•</span><span class="sxs-lookup"><span data-stu-id="6015f-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="6015f-151">최종 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="6015f-151">Final content</span></span>

<span data-ttu-id="6015f-152">장면 이름</span><span class="sxs-lookup"><span data-stu-id="6015f-152">Scene Name</span></span> | <span data-ttu-id="6015f-153">장면 태그</span><span class="sxs-lookup"><span data-stu-id="6015f-153">Scene Tag</span></span> | <span data-ttu-id="6015f-154">스크립트에 의해 로드 됨</span><span class="sxs-lookup"><span data-stu-id="6015f-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="6015f-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="6015f-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="6015f-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="6015f-156">DoNotInclude</span></span> |
<span data-ttu-id="6015f-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="6015f-157">StructureTesting</span></span> | <span data-ttu-id="6015f-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="6015f-158">DoNotInclude</span></span> |
<span data-ttu-id="6015f-159">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="6015f-159">VegetationTools</span></span> | <span data-ttu-id="6015f-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="6015f-160">DoNotInclude</span></span> |
<span data-ttu-id="6015f-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="6015f-161">Mountain</span></span> | <span data-ttu-id="6015f-162">지형</span><span class="sxs-lookup"><span data-stu-id="6015f-162">Terrain</span></span> | <span data-ttu-id="6015f-163">•</span><span class="sxs-lookup"><span data-stu-id="6015f-163">•</span></span>
<span data-ttu-id="6015f-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="6015f-164">Cabin</span></span> | <span data-ttu-id="6015f-165">구조체</span><span class="sxs-lookup"><span data-stu-id="6015f-165">Structures</span></span> | <span data-ttu-id="6015f-166">•</span><span class="sxs-lookup"><span data-stu-id="6015f-166">•</span></span>
<span data-ttu-id="6015f-167">Trees</span><span class="sxs-lookup"><span data-stu-id="6015f-167">Trees</span></span> | <span data-ttu-id="6015f-168">Vegetation</span><span class="sxs-lookup"><span data-stu-id="6015f-168">Vegetation</span></span> | <span data-ttu-id="6015f-169">•</span><span class="sxs-lookup"><span data-stu-id="6015f-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="6015f-170">편집기 동작</span><span class="sxs-lookup"><span data-stu-id="6015f-170">Editor behavior</span></span>

<span data-ttu-id="6015f-171">장면 시스템의 [service inspector](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 사용 하 여 편집기와 재생 모드에서 이러한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="6015f-172">편집 모드에서 장면 로드는 즉시 수행 되지만 재생 모드에서는 로드 진행 상태를 관찰 하 고 [활성화 토큰](scene-system-load-progress.md) 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6015f-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![콘텐츠 로드가 강조 표시 된 검사기의 장면 시스템](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
