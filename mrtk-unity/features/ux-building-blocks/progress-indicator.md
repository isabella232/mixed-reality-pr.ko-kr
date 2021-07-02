---
title: 진행률 표시기
description: MRTK의 진행률 표시기 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176569"
---
# <a name="progress-indicator"></a>진행률 표시기

![진행률 표시기](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>장면 예

진행률 표시기를 사용 하는 방법의 예는 장면에서 찾을 수 있습니다 `ProgressIndicatorExamples` . 이 장면에서는 SDK에 포함 된 각 진행률 표시기 prefabs를 보여 줍니다. 또한 장면 로드와 같은 몇 가지 일반적인 비동기 작업과 함께 진행률 표시기를 사용 하는 방법을 보여 줍니다.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>예: 열기, 업데이트 & 진행률 표시기 닫기

진행률 표시기는 인터페이스를 구현 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 합니다. 이 인터페이스는를 사용 하 여 GameObject에서 검색할 수 있습니다 `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

`IProgressIndicator.OpenAsync()`및 `IProgressIndicator.CloseAsync()` 메서드는 [작업](xref:System.Threading.Tasks.Task)을 반환 합니다. 비동기 메서드에서 이러한 작업을 대기 하는 것이 좋습니다.

Prefabs에 배치 된 경우 MRTK의 기본 진행률 표시기가 비활성 상태 여야 합니다. 해당 `IProgressIndicator.OpenAsync()` 메서드가 호출 되 면 진행률 표시기가 자동으로 gameobject를 활성화 하 고 비활성화 합니다. 이 패턴은 IProgressIndicator 인터페이스의 요구 사항이 아닙니다.

표시기의 속성을 `Progress` 0-1에서 값으로 설정 하 여 표시 된 진행률을 업데이트 합니다. 해당 `Message` 속성을 설정 하 여 표시 된 메시지를 업데이트 합니다. 여러 구현에서이 콘텐츠를 다양 한 방식으로 표시할 수 있습니다.

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

표시기의 `State` 속성은 유효한 작업을 결정 합니다. 잘못 된 메서드를 호출 하면 일반적으로 표시기에서 오류를 보고 하 고 아무 동작도 수행 하지 않습니다.

시스템 상태 | 유효한 작업
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` 을 사용 하 여 표시기를 사용 하기 전에 완전히 열리거나 닫 았는 지 확인할 수 있습니다.

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
