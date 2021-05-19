---
title: 진단 구성
description: MRTK에서 진단 구성 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 2ff761baa728017eb011cb9105cf203e6e3a72e4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144170"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="50f08-104">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="50f08-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="50f08-105">일반 설정</span><span class="sxs-lookup"><span data-stu-id="50f08-105">General settings</span></span>

![진단 일반 설정](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="50f08-107">자세한 정보 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="50f08-107">Enable verbose logging</span></span>

<span data-ttu-id="50f08-108">Verbose MRTK 로깅을 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="50f08-109">이 기본값은 false 이지만 MRTK 팀에서 디버그/문제를 해결 하는 데 사용할 수 있는 자세한 추적을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="50f08-110">예를 들어 문제를 해결할 때 Unity 플레이어 로그 (편집기나 플레이어)를 연결 하면 버그와 문제의 원인을 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="50f08-111">이 옵션은 진단 시스템이 사용 하도록 설정 되었는지 여부와는 독립적입니다 .이 옵션은 로깅 옵션 이지만 궁극적으로는 전체 MRTK 코드 베이스의 로깅에 영향을 주므로 더 높은 수준에서 작동 하므로 진단 시스템에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="50f08-112">진단 표시</span><span class="sxs-lookup"><span data-stu-id="50f08-112">Show diagnostics</span></span>

<span data-ttu-id="50f08-113">진단 시스템이 구성 된 진단 옵션을 표시 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="50f08-114">사용 하지 않도록 설정 하면 구성 된 모든 진단 옵션이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="50f08-115">프로파일러 설정</span><span class="sxs-lookup"><span data-stu-id="50f08-115">Profiler settings</span></span>

![진단 프로파일러 설정](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="50f08-117">프로파일러 표시</span><span class="sxs-lookup"><span data-stu-id="50f08-117">Show profiler</span></span>

<span data-ttu-id="50f08-118">시각적 프로파일러를 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="50f08-119">프레임 샘플링 주기</span><span class="sxs-lookup"><span data-stu-id="50f08-119">Frame sample rate</span></span>

<span data-ttu-id="50f08-120">프레임 주기 계산에 대 한 프레임을 수집 하는 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="50f08-121">범위는 0 초에서 5 초입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="50f08-122">창 앵커</span><span class="sxs-lookup"><span data-stu-id="50f08-122">Window anchor</span></span>

<span data-ttu-id="50f08-123">프로파일러 창이 고정 되는 뷰 포트의 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="50f08-124">기본값은 아래쪽 가운데입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="50f08-125">창 오프셋</span><span class="sxs-lookup"><span data-stu-id="50f08-125">Window offset</span></span>

<span data-ttu-id="50f08-126">보기 포트의 가운데에서 시각적 프로파일러를 배치할 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="50f08-127">오프셋은 *Window Anchor* 속성의 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="50f08-128">창 크기 조정</span><span class="sxs-lookup"><span data-stu-id="50f08-128">Window scale</span></span>

<span data-ttu-id="50f08-129">프로파일러 창에 적용된 크기 승수입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="50f08-130">예를 들어 값을 2로 설정하면 창 크기가 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="50f08-131">창 팔로우 속도</span><span class="sxs-lookup"><span data-stu-id="50f08-131">Window follow speed</span></span>

<span data-ttu-id="50f08-132">보기 포트 내에서 표시 여부를 유지하기 위해 프로파일러 창을 이동할 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="50f08-133">프로그래밍 방식으로 진단 시스템 제어</span><span class="sxs-lookup"><span data-stu-id="50f08-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="50f08-134">또한 런타임에 진단 시스템 및 프로파일러의 표시 여부를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="50f08-135">예를 들어 아래 코드는 진단 시스템 및 프로파일러를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="50f08-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="50f08-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50f08-136">See also</span></span>

- [<span data-ttu-id="50f08-137">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="50f08-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="50f08-138">Visual Profiler 사용</span><span class="sxs-lookup"><span data-stu-id="50f08-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
