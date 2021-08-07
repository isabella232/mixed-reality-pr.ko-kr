---
title: 장면 전환 서비스
description: MRTK의 장면 전환에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, SceneTransition,
ms.openlocfilehash: a66922f1c9d58018ee856c3054aa71f5213ec690c5f4780b32fd735eb59f2ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189235"
---
# <a name="scene-transition-service"></a>장면 전환 서비스

이 확장은 장면을 페이드 아웃하고, 진행률 표시기를 표시하고, 장면을 로드한 다음, 다시 페이드 인하는 작업을 간소화합니다.

장면 작업은 SceneSystem 서비스에 의해 구동되지만 모든 작업 기반 작업을 사용하여 전환을 구동할 수 있습니다.

## <a name="enabling-the-extension"></a>확장 사용

확장을 사용하도록 설정하려면 RegisteredServiceProvider 프로필을 엽니다. 새 서비스 공급자 등록을 클릭하여 새 구성을 추가합니다. 구성 요소 유형 필드에서 SceneTransitionService를 선택합니다. 구성 프로필 필드에서 확장에 포함된 기본 장면 전환 프로필을 선택합니다.

## <a name="profile-options"></a>프로필 옵션

### <a name="use-default-progress-indicator"></a>기본 진행률 표시기 사용

이 옵션을 선택하면 진행률 표시기 개체가 제공되면 진행률 표시기 개체를 호출할 때 진행률 표시기 개체가 제공되지 않을 때 `DoSceneTransition.` 기본 진행률 표시기 프리팹이 사용됩니다.

### <a name="use-fade-color"></a>페이드 색 사용

이 옵션을 선택하면 전환 서비스가 전환 중에 페이드를 적용합니다. 이 설정은 서비스의 속성을 통해 런타임에 변경할 수 `UseFadeColor` 있습니다.

### <a name="fade-color"></a>페이드 색

페이드 효과의 색을 제어합니다. 알파는 무시됩니다. 이 설정은 서비스의 속성을 통해 전환하기 전에 런타임에 변경할 수 `FadeColor` 있습니다.

### <a name="fade-targets"></a>페이드 대상

어떤 카메라가 페이드 효과를 적용할지 제어합니다. 이 설정은 서비스의 속성을 통해 런타임에 변경할 수 `FadeTargets` 있습니다.

설정 | 대상 카메라
--- | --- | ---
주 | 주 카메라에 페이드 효과를 적용합니다.
UI | UI 계층의 카메라에 페이드 효과를 적용합니다. (오버레이 UI에 영향을 주지 않음)
모두 | 기본 및 UI 카메라 모두에 적용됩니다.
사용자 지정 | 을 통해 제공되는 사용자 지정 카메라 세트에 적용됩니다. `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>페이드 아웃 시간/페이드 인 시간

전환 입력/종료 시 페이드 기간의 기본 설정입니다. 이러한 설정은 서비스의 및 속성을 통해 런타임에 변경할 수 `FadeOutTime` `FadeInTime` 있습니다.

### <a name="camera-fader-type"></a>카메라 페이더 유형

`ICameraFader`카메라에 페이드 효과를 적용하는 데 사용할 클래스입니다. 기본 `CameraFaderQuad` 클래스는 클립 평면에 가까운 대상 카메라 앞에 투명한 재질이 있는 쿼드를 인스턴스화합니다. 또 다른 방법은 사후 효과 시스템을 사용하는 것입니다.

## <a name="using-the-extension"></a>확장 사용

카메라가 페이드 아웃된 동안 실행되는 작업을 전달하여 전환 서비스를 사용합니다.

### <a name="using-scene-system-tasks"></a>장면 시스템 작업 사용

대부분의 경우 SceneSystem 서비스에서 제공하는 작업을 사용하게 됩니다.

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

다른 경우에는 장면을 실제로 로드하지 않고 전환을 수행할 수 있습니다.

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

또는 SceneSystem 서비스를 사용하지 않고 장면을 로드할 수 있습니다.

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

순서대로 실행되는 여러 태스크를 제공할 수도 있습니다.

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

진행률 표시기는 인터페이스를 구현하는 모든 `IProgressIndicator` 것입니다. 이는 시작 화면, 3D tagalong 로딩 표시기 또는 전환 진행률에 대한 피드백을 제공하는 다른 모든 형식을 사용할 수 있습니다.

`UseDefaultProgressIndicator`SceneTransitionService 프로필에서 를 선택하면 전환이 시작될 때 진행률 표시기가 인스턴스화됩니다. 전환 기간 동안 이 표시기의 `Progress` 및 `Message` 속성은 해당 서비스의 및 메서드를 통해 액세스할 수 `SetProgressValue` `SetProgressMessage` 있습니다.

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

또는 를 호출할 때 `DoSceneTransition` 선택적 인수를 통해 고유한 진행률 표시기를 제공할 수 `progressIndicator` 있습니다. 그러면 기본 진행률 표시기가 재정의됩니다.
