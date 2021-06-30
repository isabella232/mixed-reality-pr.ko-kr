---
title: 진단 구성
description: MRTK에서 진단을 구성하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121801"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="f36e2-104">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="f36e2-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="f36e2-105">일반 설정</span><span class="sxs-lookup"><span data-stu-id="f36e2-105">General settings</span></span>

![진단 일반 설정](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="f36e2-107">자세한 정보 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="f36e2-107">Enable verbose logging</span></span>

<span data-ttu-id="f36e2-108">자세한 MRTK 로깅을 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="f36e2-109">이 기본값은 false이지만 MRTK 팀이 문제를 디버그/분석할 수 있도록 자세한 추적을 설정하도록 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="f36e2-110">예를 들어 문제를 제출할 때 Unity 플레이어 로그(편집기 또는 플레이어에서)를 연결하면 버그 및 문제의 원인을 좁히는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="f36e2-111">이 옵션은 진단 시스템을 사용하는지 여부와는 독립적입니다. 이는 로깅 옵션이기 때문에 진단 시스템에 표시되지만 전체 MRTK 코드베이스의 로깅에 영향을 주므로 궁극적으로 더 높은 수준에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="f36e2-112">진단 표시</span><span class="sxs-lookup"><span data-stu-id="f36e2-112">Show diagnostics</span></span>

<span data-ttu-id="f36e2-113">진단 시스템이 구성된 진단 옵션을 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="f36e2-114">사용하지 않도록 설정하면 구성된 모든 진단 옵션이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="f36e2-115">프로파일러 설정</span><span class="sxs-lookup"><span data-stu-id="f36e2-115">Profiler settings</span></span>

![진단 프로파일러 설정](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="f36e2-117">프로파일러 표시</span><span class="sxs-lookup"><span data-stu-id="f36e2-117">Show profiler</span></span>

<span data-ttu-id="f36e2-118">시각적 프로파일러를 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="f36e2-119">프레임 샘플 속도</span><span class="sxs-lookup"><span data-stu-id="f36e2-119">Frame sample rate</span></span>

<span data-ttu-id="f36e2-120">프레임 속도 계산을 위해 프레임을 수집하는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="f36e2-121">범위는 0~5초입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="f36e2-122">창 앵커</span><span class="sxs-lookup"><span data-stu-id="f36e2-122">Window anchor</span></span>

<span data-ttu-id="f36e2-123">프로파일러 창이 고정되어야 하는 뷰 포트의 어떤 부분으로.</span><span class="sxs-lookup"><span data-stu-id="f36e2-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="f36e2-124">기본값은 Lower Center입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="f36e2-125">창 오프셋</span><span class="sxs-lookup"><span data-stu-id="f36e2-125">Window offset</span></span>

<span data-ttu-id="f36e2-126">보기 포트의 가운데에서 시각적 프로파일러를 배치할 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="f36e2-127">오프셋은 *Window Anchor* 속성의 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="f36e2-128">창 크기 조정</span><span class="sxs-lookup"><span data-stu-id="f36e2-128">Window scale</span></span>

<span data-ttu-id="f36e2-129">프로파일러 창에 적용된 크기 승수입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="f36e2-130">예를 들어 값을 2로 설정하면 창 크기가 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="f36e2-131">창 팔로우 속도</span><span class="sxs-lookup"><span data-stu-id="f36e2-131">Window follow speed</span></span>

<span data-ttu-id="f36e2-132">보기 포트 내에서 표시 여부를 유지하기 위해 프로파일러 창을 이동할 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="f36e2-133">프로그래밍 방식으로 진단 시스템 제어</span><span class="sxs-lookup"><span data-stu-id="f36e2-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="f36e2-134">또한 런타임에 진단 시스템 및 프로파일러의 표시 여부를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="f36e2-135">예를 들어 아래 코드는 진단 시스템 및 프로파일러를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="f36e2-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="f36e2-136">참조</span><span class="sxs-lookup"><span data-stu-id="f36e2-136">See also</span></span>

- [<span data-ttu-id="f36e2-137">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="f36e2-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="f36e2-138">Visual Profiler 사용</span><span class="sxs-lookup"><span data-stu-id="f36e2-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
