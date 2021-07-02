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
# <a name="progress-indicator"></a><span data-ttu-id="5639d-104">진행률 표시기</span><span class="sxs-lookup"><span data-stu-id="5639d-104">Progress indicator</span></span>

![진행률 표시기](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="5639d-106">장면 예</span><span class="sxs-lookup"><span data-stu-id="5639d-106">Example scene</span></span>

<span data-ttu-id="5639d-107">진행률 표시기를 사용 하는 방법의 예는 장면에서 찾을 수 있습니다 `ProgressIndicatorExamples` .</span><span class="sxs-lookup"><span data-stu-id="5639d-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="5639d-108">이 장면에서는 SDK에 포함 된 각 진행률 표시기 prefabs를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="5639d-109">또한 장면 로드와 같은 몇 가지 일반적인 비동기 작업과 함께 진행률 표시기를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="5639d-110">예: 열기, 업데이트 & 진행률 표시기 닫기</span><span class="sxs-lookup"><span data-stu-id="5639d-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="5639d-111">진행률 표시기는 인터페이스를 구현 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="5639d-112">이 인터페이스는를 사용 하 여 GameObject에서 검색할 수 있습니다 `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="5639d-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="5639d-113">`IProgressIndicator.OpenAsync()`및 `IProgressIndicator.CloseAsync()` 메서드는 [작업](xref:System.Threading.Tasks.Task)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="5639d-114">비동기 메서드에서 이러한 작업을 대기 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="5639d-115">Prefabs에 배치 된 경우 MRTK의 기본 진행률 표시기가 비활성 상태 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="5639d-116">해당 `IProgressIndicator.OpenAsync()` 메서드가 호출 되 면 진행률 표시기가 자동으로 gameobject를 활성화 하 고 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="5639d-117">이 패턴은 IProgressIndicator 인터페이스의 요구 사항이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="5639d-118">표시기의 속성을 `Progress` 0-1에서 값으로 설정 하 여 표시 된 진행률을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="5639d-119">해당 `Message` 속성을 설정 하 여 표시 된 메시지를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="5639d-120">여러 구현에서이 콘텐츠를 다양 한 방식으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="5639d-121">표시기 상태</span><span class="sxs-lookup"><span data-stu-id="5639d-121">Indicator states</span></span>

<span data-ttu-id="5639d-122">표시기의 `State` 속성은 유효한 작업을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="5639d-123">잘못 된 메서드를 호출 하면 일반적으로 표시기에서 오류를 보고 하 고 아무 동작도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="5639d-124">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="5639d-124">State</span></span> | <span data-ttu-id="5639d-125">유효한 작업</span><span class="sxs-lookup"><span data-stu-id="5639d-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="5639d-126">`AwaitTransitionAsync()` 을 사용 하 여 표시기를 사용 하기 전에 완전히 열리거나 닫 았는 지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5639d-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
