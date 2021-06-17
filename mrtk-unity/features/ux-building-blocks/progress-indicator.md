---
title: ProgressIndicator
description: MRTK의 진행률 표시기 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110130"
---
# <a name="progress-indicators"></a>진행률 표시기

![진행률 표시기](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>예제 장면

진행률 표시기를 사용하는 방법의 예는 장면에서 찾을 수 `ProgressIndicatorExamples` 있습니다. 이 장면에서는 SDK에 포함된 각 진행률 표시기 프리팹을 보여줍니다. 또한 장면 로드와 같은 몇 가지 일반적인 비동기 작업과 함께 진행률 표시기를 사용하는 방법을 보여줍니다.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>예: 진행률 표시기 열기, 업데이트 & 닫기

진행률 표시기가 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 인터페이스를 구현합니다. 이 인터페이스는 를 사용하여 GameObject에서 검색할 수 `GetComponent` 있습니다.

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

`IProgressIndicator.OpenAsync()`및 `IProgressIndicator.CloseAsync()` 메서드는 Tasks 를 [반환합니다.](xref:System.Threading.Tasks.Task) 비동기 메서드에서 이러한 작업을 기다리는 것이 좋습니다.

MRTK의 기본 진행률 표시기 프리팹은 장면에 배치될 때 비활성 상태여야 합니다. 해당 `IProgressIndicator.OpenAsync()` 메서드를 호출하면 진행률 표시기가 gameobject를 자동으로 활성화하고 비활성화합니다. (이 패턴은 IProgressIndicator 인터페이스의 요구 사항이 아닙니다.)

표시기 속성을 `Progress` 0-1의 값으로 설정하여 표시된 진행 상황을 업데이트합니다. 표시된 `Message` 메시지를 업데이트하려면 해당 속성을 설정합니다. 구현이 서로 다른 방식으로 이 콘텐츠를 표시할 수 있습니다.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>표시기 상태

표시기 `State` 속성은 유효한 작업을 결정합니다. 잘못된 메서드를 호출하면 일반적으로 표시기가 오류를 보고하고 아무 작업도 수행하지 않습니다.

시스템 상태 | 유효한 작업
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` 를 사용하여 표시기를 사용하기 전에 표시기가 완전히 열리거나 닫히도록 할 수 있습니다.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
