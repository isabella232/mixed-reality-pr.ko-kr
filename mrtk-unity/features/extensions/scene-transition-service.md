---
title: 장면 전환 서비스
description: MRTK의 장면 전환에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, SceneTransition,
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176216"
---
# <a name="scene-transition-service"></a>장면 전환 서비스

이 확장은 장면을 페이드 아웃 하 고 진행률 표시기를 표시 하 고 장면을 로드 한 다음 페이드 인 하는 업무를 간소화 합니다.

장면 작업은 SceneSystem 서비스에서 구동 하지만 모든 작업 기반 작업을 사용 하 여 전환을 수행할 수 있습니다.

## <a name="enabling-the-extension"></a>확장 사용

확장을 사용 하도록 설정 하려면 RegisteredServiceProvider 프로필을 엽니다. 새 서비스 공급자 등록을 클릭 하 여 새 구성을 추가 합니다. 구성 요소 유형 필드에서 SceneTransitionService를 선택 합니다. 구성 프로필 필드에서 확장에 포함 된 기본 장면 전환 프로필을 선택 합니다.

## <a name="profile-options"></a>프로필 옵션

### <a name="use-default-progress-indicator"></a>기본 진행률 표시기 사용

이 확인란을 선택 하면 진행률 표시기 개체가 제공 되는 경우를 호출할 때 진행률 표시기 개체가 제공 되지 않을 때 기본 진행률 표시기 prefab가 사용 됩니다 `DoSceneTransition.` . 기본값은 무시 됩니다.

### <a name="use-fade-color"></a>페이드 색 사용

이 확인란을 선택 하는 경우 전환 서비스는 전환 하는 동안 페이드를 적용 합니다. 이 설정은 서비스의 속성을 통해 런타임에 변경할 수 있습니다 `UseFadeColor` .

### <a name="fade-color"></a>페이드 색

페이드 효과의 색을 제어 합니다. 알파는 무시됩니다. 이 설정은 서비스의 속성을 통해 전환 하기 전에 런타임에 변경할 수 있습니다 `FadeColor` .

### <a name="fade-targets"></a>대상 페이드

페이드 효과를 적용 하는 카메라를 제어 합니다. 이 설정은 서비스의 속성을 통해 런타임에 변경할 수 있습니다 `FadeTargets` .

설정 | 대상 카메라
--- | --- | ---
주 | 기본 카메라에 페이드 효과를 적용 합니다.
UI | UI 계층에서 카메라에 페이드 효과를 적용 합니다. (오버레이 UI에 영향을 주지 않음)
모두 | 주 및 UI 카메라 모두에 적용 됩니다.
사용자 지정 | 를 통해 제공 되는 카메라의 사용자 지정 집합에 적용 됩니다. `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>페이드 아웃 시간/페이드 시간

전환을 시작 하거나 종료 하는 동안 페이드 인 기간에 대 한 기본 설정입니다. 이러한 설정은 서비스의 및 속성을 통해 런타임에 변경할 수 `FadeOutTime` 있습니다 `FadeInTime` .

### <a name="camera-fader-type"></a>카메라 페이더 유형

`ICameraFader`카메라에 페이드 효과를 적용 하는 데 사용할 클래스입니다. 기본 `CameraFaderQuad` 클래스는 클립 평면 가까이에 있는 대상 카메라 앞에 투명 한 재질을 사용 하 여 쿼드를 인스턴스화합니다. 또 다른 방법은 post 영향 시스템을 사용 하는 것입니다.

## <a name="using-the-extension"></a>확장 사용

카메라를 페이드 아웃 하는 동안 실행 되는 작업을 전달 하 여 전환 서비스를 사용 합니다.

### <a name="using-scene-system-tasks"></a>시스템 장면 작업 사용

대부분의 경우 SceneSystem 서비스에서 제공 하는 작업을 사용 합니다.

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a>사용자 지정 작업 사용

경우에 따라 장면을 실제로 로드 하지 않고도 전환을 수행할 수 있습니다.

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

또는 SceneSystem 서비스를 사용 하지 않고 장면을 로드 하는 것이 좋습니다.

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a>여러 작업 사용

다음 순서 대로 실행 되는 여러 작업을 제공할 수도 있습니다.

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a>진행률 표시기 사용

진행률 표시기는 인터페이스를 구현 하는 모든 항목입니다 `IProgressIndicator` . 이는 시작 화면의 형태, 3D tagalong 로드 표시기 또는 전환 진행에 대 한 피드백을 제공 하는 다른 모든 항목을 사용할 수 있습니다.

`UseDefaultProgressIndicator`가 SceneTransitionService profile에서 확인 되 면 전환이 시작 될 때 진행률 표시기가 인스턴스화됩니다. 전환 기간 동안이 표시기의 `Progress` 및 `Message` 속성은 해당 서비스의 및 메서드를 통해 액세스할 수 `SetProgressValue` 있습니다 `SetProgressMessage` .

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

또는를 호출할 때 `DoSceneTransition` 선택적 인수를 통해 고유한 진행률 표시기를 제공할 수 있습니다 `progressIndicator` . 이렇게 하면 기본 진행률 표시기가 재정의 됩니다.
