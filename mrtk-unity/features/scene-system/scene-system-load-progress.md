---
title: 장면 시스템 로드 진행률
description: MRTK의 장면 콘텐츠 로드에 대 한 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144401"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="3782d-104">콘텐츠 로드 모니터링</span><span class="sxs-lookup"><span data-stu-id="3782d-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="3782d-105">장면 작업 진행률</span><span class="sxs-lookup"><span data-stu-id="3782d-105">Scene operation progress</span></span>

<span data-ttu-id="3782d-106">콘텐츠를 로드 하거나 언로드할 때 `SceneOperationInProgress` 속성은 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="3782d-107">속성을 통해이 작업의 진행률을 모니터링할 수 있습니다 `SceneOperationProgress` .</span><span class="sxs-lookup"><span data-stu-id="3782d-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="3782d-108">`SceneOperationProgress`값은 모든 현재 비동기 장면 작업의 평균입니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="3782d-109">콘텐츠 로드 시작 시은 0이 됩니다 `SceneOperationProgress` .</span><span class="sxs-lookup"><span data-stu-id="3782d-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="3782d-110">완전히 완료 된 후에 `SceneOperationProgress` 는 1로 설정 되 고 다음 작업이 수행 될 때까지 1로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="3782d-111">콘텐츠 장면 작업만 이러한 속성에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="3782d-112">이러한 속성은 작업에 여러 단계가 포함 된 경우에도 *전체 작업* 상태를 시작부터 끝까지 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="3782d-113">진행률 예</span><span class="sxs-lookup"><span data-stu-id="3782d-113">Progress examples</span></span>

<span data-ttu-id="3782d-114">`SceneOperationInProgress` 콘텐츠를 로드 하는 동안 작업을 일시 중단 해야 하는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="3782d-115">`SceneOperationProgress` 진행률 대화 상자를 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="3782d-116">작업으로 모니터링</span><span class="sxs-lookup"><span data-stu-id="3782d-116">Monitoring with actions</span></span>

<span data-ttu-id="3782d-117">장면 시스템은 장면이 로드 되거나 언로드될 때를 알려 주는 여러 가지 작업을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="3782d-118">각 작업은 영향을 받는 장면의 이름을 릴레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="3782d-119">로드 또는 언로드 작업이 여러 장면을 포함 하는 경우 관련 작업은 영향을 받는 장면 마다 한 번씩 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="3782d-120">또한 로드 또는 언로드 작업이 *완전히 완료* 될 때 한 번에 모두 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="3782d-121">이러한 이유로, *OnWillUnload* 작업을 사용 하 여 삭제 되는 콘텐츠를 검색 하는 것이 좋습니다 .이는 *onunloaded* 작업을 사용 하 여 팩트 이후에 *소멸 된 콘텐츠* 를 검색 하는 것과는 반대입니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="3782d-122">*OnLoaded* 작업은 모든 장면이 활성화 되 고 완전히 로드 될 때만 호출 되기 때문에 *OnLoaded* 작업을 사용 하 여 새 콘텐츠를 검색 하 고 사용 하는 것은 안전 하다 고 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="3782d-123">작업</span><span class="sxs-lookup"><span data-stu-id="3782d-123">Action</span></span> | <span data-ttu-id="3782d-124">호출되는 경우</span><span class="sxs-lookup"><span data-stu-id="3782d-124">When it's invoked</span></span> | <span data-ttu-id="3782d-125">콘텐츠 장면</span><span class="sxs-lookup"><span data-stu-id="3782d-125">Content Scenes</span></span> | <span data-ttu-id="3782d-126">조명 장면</span><span class="sxs-lookup"><span data-stu-id="3782d-126">Lighting Scenes</span></span> | <span data-ttu-id="3782d-127">관리자 장면</span><span class="sxs-lookup"><span data-stu-id="3782d-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="3782d-128">콘텐츠 장면 로드 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-128">Just prior to a content scene load</span></span> | <span data-ttu-id="3782d-129">•</span><span class="sxs-lookup"><span data-stu-id="3782d-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="3782d-130">로드 작업의 모든 콘텐츠 장면을 완전히 로드하고 활성화한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="3782d-131">•</span><span class="sxs-lookup"><span data-stu-id="3782d-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="3782d-132">콘텐츠 장면 언로드 작업 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="3782d-133">•</span><span class="sxs-lookup"><span data-stu-id="3782d-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="3782d-134">언로드 작업의 모든 콘텐츠 장면을 완전히 언로드한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="3782d-135">•</span><span class="sxs-lookup"><span data-stu-id="3782d-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="3782d-136">조명 장면 로드 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="3782d-137">•</span><span class="sxs-lookup"><span data-stu-id="3782d-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="3782d-138">조명 장면을 완전히 로드하고 활성화한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="3782d-139">•</span><span class="sxs-lookup"><span data-stu-id="3782d-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="3782d-140">조명 장면 언로드 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="3782d-141">•</span><span class="sxs-lookup"><span data-stu-id="3782d-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="3782d-142">조명 장면을 완전히 언로드한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="3782d-143">•</span><span class="sxs-lookup"><span data-stu-id="3782d-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="3782d-144">장면 로드 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-144">Just prior to a scene load</span></span> | <span data-ttu-id="3782d-145">•</span><span class="sxs-lookup"><span data-stu-id="3782d-145">•</span></span> | <span data-ttu-id="3782d-146">•</span><span class="sxs-lookup"><span data-stu-id="3782d-146">•</span></span> | <span data-ttu-id="3782d-147">•</span><span class="sxs-lookup"><span data-stu-id="3782d-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="3782d-148">작업의 모든 장면을 완전히 로드하고 활성화한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="3782d-149">•</span><span class="sxs-lookup"><span data-stu-id="3782d-149">•</span></span> | <span data-ttu-id="3782d-150">•</span><span class="sxs-lookup"><span data-stu-id="3782d-150">•</span></span> | <span data-ttu-id="3782d-151">•</span><span class="sxs-lookup"><span data-stu-id="3782d-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="3782d-152">장면 언로드 직전에</span><span class="sxs-lookup"><span data-stu-id="3782d-152">Just prior to a scene unload</span></span> | <span data-ttu-id="3782d-153">•</span><span class="sxs-lookup"><span data-stu-id="3782d-153">•</span></span> | <span data-ttu-id="3782d-154">•</span><span class="sxs-lookup"><span data-stu-id="3782d-154">•</span></span> | <span data-ttu-id="3782d-155">•</span><span class="sxs-lookup"><span data-stu-id="3782d-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="3782d-156">장면을 완전히 언로드한 후</span><span class="sxs-lookup"><span data-stu-id="3782d-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="3782d-157">•</span><span class="sxs-lookup"><span data-stu-id="3782d-157">•</span></span> | <span data-ttu-id="3782d-158">•</span><span class="sxs-lookup"><span data-stu-id="3782d-158">•</span></span> | <span data-ttu-id="3782d-159">•</span><span class="sxs-lookup"><span data-stu-id="3782d-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="3782d-160">작업 예제</span><span class="sxs-lookup"><span data-stu-id="3782d-160">Action examples</span></span>

<span data-ttu-id="3782d-161">업데이트 대신 작업 및 코루틴을 사용하는 또 다른 진행률 대화 상자 예제:</span><span class="sxs-lookup"><span data-stu-id="3782d-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="3782d-162">장면 활성화 제어</span><span class="sxs-lookup"><span data-stu-id="3782d-162">Controlling scene activation</span></span>

<span data-ttu-id="3782d-163">기본적으로 콘텐츠 장면을 로드할 때 활성화하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="3782d-164">장면 활성화를 수동으로 제어 하려면 `SceneActivationToken` 모든 콘텐츠 로드 메서드에를 전달 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="3782d-165">단일 작업으로 여러 콘텐츠 장면을 로드 하는 경우이 활성화 토큰은 모든 장면에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="3782d-166">로드 된 콘텐츠 확인</span><span class="sxs-lookup"><span data-stu-id="3782d-166">Checking which content is loaded</span></span>

<span data-ttu-id="3782d-167">`ContentSceneNames`속성은 빌드 인덱스 순서 대로 사용 가능한 콘텐츠 장면 배열을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3782d-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="3782d-168">이러한 장면이를 통해 로드 되는지 여부를 확인할 수 있습니다 `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="3782d-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
