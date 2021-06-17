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
# <a name="progress-indicators"></a><span data-ttu-id="5ff90-104">진행률 표시기</span><span class="sxs-lookup"><span data-stu-id="5ff90-104">Progress Indicators</span></span>

![진행률 표시기](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="5ff90-106">예제 장면</span><span class="sxs-lookup"><span data-stu-id="5ff90-106">Example scene</span></span>

<span data-ttu-id="5ff90-107">진행률 표시기를 사용하는 방법의 예는 장면에서 찾을 수 `ProgressIndicatorExamples` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="5ff90-108">이 장면에서는 SDK에 포함된 각 진행률 표시기 프리팹을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="5ff90-109">또한 장면 로드와 같은 몇 가지 일반적인 비동기 작업과 함께 진행률 표시기를 사용하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="5ff90-110">예: 진행률 표시기 열기, 업데이트 & 닫기</span><span class="sxs-lookup"><span data-stu-id="5ff90-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="5ff90-111">진행률 표시기가 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="5ff90-112">이 인터페이스는 를 사용하여 GameObject에서 검색할 수 `GetComponent` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="5ff90-113">`IProgressIndicator.OpenAsync()`및 `IProgressIndicator.CloseAsync()` 메서드는 Tasks 를 [반환합니다.](xref:System.Threading.Tasks.Task)</span><span class="sxs-lookup"><span data-stu-id="5ff90-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="5ff90-114">비동기 메서드에서 이러한 작업을 기다리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="5ff90-115">MRTK의 기본 진행률 표시기 프리팹은 장면에 배치될 때 비활성 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="5ff90-116">해당 `IProgressIndicator.OpenAsync()` 메서드를 호출하면 진행률 표시기가 gameobject를 자동으로 활성화하고 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="5ff90-117">(이 패턴은 IProgressIndicator 인터페이스의 요구 사항이 아닙니다.)</span><span class="sxs-lookup"><span data-stu-id="5ff90-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="5ff90-118">표시기 속성을 `Progress` 0-1의 값으로 설정하여 표시된 진행 상황을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="5ff90-119">표시된 `Message` 메시지를 업데이트하려면 해당 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="5ff90-120">구현이 서로 다른 방식으로 이 콘텐츠를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="5ff90-121">표시기 상태</span><span class="sxs-lookup"><span data-stu-id="5ff90-121">Indicator states</span></span>

<span data-ttu-id="5ff90-122">표시기 `State` 속성은 유효한 작업을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="5ff90-123">잘못된 메서드를 호출하면 일반적으로 표시기가 오류를 보고하고 아무 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="5ff90-124">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="5ff90-124">State</span></span> | <span data-ttu-id="5ff90-125">유효한 작업</span><span class="sxs-lookup"><span data-stu-id="5ff90-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="5ff90-126">`AwaitTransitionAsync()` 를 사용하여 표시기를 사용하기 전에 표시기가 완전히 열리거나 닫히도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ff90-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
