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
# <a name="monitoring-content-loading"></a>콘텐츠 로드 모니터링

## <a name="scene-operation-progress"></a>장면 작업 진행률

콘텐츠를 로드 하거나 언로드할 때 `SceneOperationInProgress` 속성은 true를 반환 합니다. 속성을 통해이 작업의 진행률을 모니터링할 수 있습니다 `SceneOperationProgress` .

`SceneOperationProgress`값은 모든 현재 비동기 장면 작업의 평균입니다. 콘텐츠 로드 시작 시은 0이 됩니다 `SceneOperationProgress` . 완전히 완료 된 후에 `SceneOperationProgress` 는 1로 설정 되 고 다음 작업이 수행 될 때까지 1로 유지 됩니다. 콘텐츠 장면 작업만 이러한 속성에 영향을 줍니다.

이러한 속성은 작업에 여러 단계가 포함 된 경우에도 *전체 작업* 상태를 시작부터 끝까지 반영 합니다.

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

### <a name="progress-examples"></a>진행률 예

`SceneOperationInProgress` 콘텐츠를 로드 하는 동안 작업을 일시 중단 해야 하는 경우에 유용할 수 있습니다.

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

`SceneOperationProgress` 진행률 대화 상자를 표시 하는 데 사용할 수 있습니다.

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

## <a name="monitoring-with-actions"></a>작업으로 모니터링

장면 시스템은 장면이 로드 되거나 언로드될 때를 알려 주는 여러 가지 작업을 제공 합니다. 각 작업은 영향을 받는 장면의 이름을 릴레이 합니다.

로드 또는 언로드 작업이 여러 장면을 포함 하는 경우 관련 작업은 영향을 받는 장면 마다 한 번씩 호출 됩니다. 또한 로드 또는 언로드 작업이 *완전히 완료* 될 때 한 번에 모두 호출 됩니다. 이러한 이유로, *OnWillUnload* 작업을 사용 하 여 삭제 되는 콘텐츠를 검색 하는 것이 좋습니다 .이는 *onunloaded* 작업을 사용 하 여 팩트 이후에 *소멸 된 콘텐츠* 를 검색 하는 것과는 반대입니다.

*OnLoaded* 작업은 모든 장면이 활성화 되 고 완전히 로드 될 때만 호출 되기 때문에 *OnLoaded* 작업을 사용 하 여 새 콘텐츠를 검색 하 고 사용 하는 것은 안전 하다 고 보장할 수 있습니다.

작업 | 호출되는 경우 | 콘텐츠 장면 | 조명 장면 | 관리자 장면
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | 콘텐츠 장면 로드 직전에 | • | |  
`OnContentLoaded` | 로드 작업의 모든 콘텐츠 장면을 완전히 로드하고 활성화한 후 | • | |
`OnWillUnloadContent` | 콘텐츠 장면 언로드 작업 직전에 | • | |
`OnContentUnloaded` | 언로드 작업의 모든 콘텐츠 장면을 완전히 언로드한 후 | • | |
`OnWillLoadLighting` | 조명 장면 로드 직전에 | | • |
`OnLightingLoaded` | 조명 장면을 완전히 로드하고 활성화한 후| | • |
`OnWillUnloadLighting` | 조명 장면 언로드 직전에 | | • |
`OnLightingUnloaded` | 조명 장면을 완전히 언로드한 후 | | • |
`OnWillLoadScene` | 장면 로드 직전에 | • | • | •
`OnSceneLoaded` | 작업의 모든 장면을 완전히 로드하고 활성화한 후 | • | • | •
`OnWillUnloadScene` | 장면 언로드 직전에 | • | • | •
`OnSceneUnloaded` | 장면을 완전히 언로드한 후 |  • | • | •

### <a name="action-examples"></a>작업 예제

업데이트 대신 작업 및 코루틴을 사용하는 또 다른 진행률 대화 상자 예제:

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

## <a name="controlling-scene-activation"></a>장면 활성화 제어

기본적으로 콘텐츠 장면을 로드할 때 활성화하도록 설정됩니다. 장면 활성화를 수동으로 제어 하려면 `SceneActivationToken` 모든 콘텐츠 로드 메서드에를 전달 하면 됩니다. 단일 작업으로 여러 콘텐츠 장면을 로드 하는 경우이 활성화 토큰은 모든 장면에 적용 됩니다.

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

## <a name="checking-which-content-is-loaded"></a>로드 된 콘텐츠 확인

`ContentSceneNames`속성은 빌드 인덱스 순서 대로 사용 가능한 콘텐츠 장면 배열을 제공 합니다. 이러한 장면이를 통해 로드 되는지 여부를 확인할 수 있습니다 `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
