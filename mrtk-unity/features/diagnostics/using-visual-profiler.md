---
title: 시각적 프로파일러 사용
description: MRTK에서 시각적 프로파일러를 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177226"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="74744-104">시각적 프로파일러 사용</span><span class="sxs-lookup"><span data-stu-id="74744-104">Using the visual profiler</span></span>

<span data-ttu-id="74744-105">VisualProfiler는 혼합 현실 애플리케이션의 성능에 대한 사용하기 쉬운 애플리케이션 내 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="74744-106">프로파일러가 다음을 비롯한 모든 Mixed Reality Toolkit 플랫폼에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="74744-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="74744-107">Microsoft HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="74744-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="74744-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="74744-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="74744-109">Windows Mixed Reality 몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="74744-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="74744-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="74744-110">OpenVR</span></span>

<span data-ttu-id="74744-111">애플리케이션을 개발하는 동안 시각적 프로파일러가 현재 뷰에 상대적인 데이터를 표시하기 때문에 장면의 여러 부분에 집중합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74744-112">복잡한 개체, 파티클 효과 또는 활동을 통해 장면의 일부에 집중합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="74744-113">이러한 요소와 기타 요인은 종종 애플리케이션 성능의 감소와 이상적인 사용자 환경보다 작은 영향을 요합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="74744-114">시각적 프로파일러 인터페이스</span><span class="sxs-lookup"><span data-stu-id="74744-114">Visual profiler interface</span></span>

![Visual Profiler 인터페이스](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="74744-116">Visual Profiler 인터페이스에는 다음 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74744-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="74744-117">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="74744-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="74744-118">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="74744-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="74744-119">프레임 Graph</span><span class="sxs-lookup"><span data-stu-id="74744-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="74744-120">메모리 사용량</span><span class="sxs-lookup"><span data-stu-id="74744-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="74744-121">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="74744-121">Frame rate</span></span>

<span data-ttu-id="74744-122">인터페이스의 왼쪽 위 모서리에는 초당 프레임 단위로 측정된 프레임 속도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="74744-123">최상의 사용자 환경과 편의를 위해 이 값은 최대한 높아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="74744-124">특정 플랫폼 및 하드웨어 구성은 달성 가능한 최대 프레임 속도에서 중요한 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="74744-125">몇 가지 일반적인 대상 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-125">Some common target values include:</span></span>

- <span data-ttu-id="74744-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="74744-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="74744-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="74744-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="74744-128">기본 [MRC가 활성 상태일 때 HoloLens 프레임 속도 제한으로](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)인해 비디오 및 사진을 캡처하는 동안 시각적 프로파일러가 자신을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="74744-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="74744-129">이 설정은 진단 시스템 프로필에서 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="74744-130">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="74744-130">Frame time</span></span>

<span data-ttu-id="74744-131">프레임 속도의 오른쪽에는 CPU에 소요된 프레임 시간(밀리초)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="74744-132">앞에서 언급한 대상 프레임 속도를 달성하기 위해 애플리케이션은 프레임당 다음과 같은 시간을 소비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="74744-133">60fps: 16.6ms</span><span class="sxs-lookup"><span data-stu-id="74744-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="74744-134">90fps: 11.1ms</span><span class="sxs-lookup"><span data-stu-id="74744-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="74744-135">GPU 시간은 향후 릴리스에서 추가될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="74744-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="74744-136">프레임 그래프</span><span class="sxs-lookup"><span data-stu-id="74744-136">Frame graph</span></span>

<span data-ttu-id="74744-137">프레임 그래프는 애플리케이션 프레임 속도 기록을 그래픽으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="74744-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Visual Profiler 누락된 프레임 Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="74744-139">애플리케이션을 사용하는 경우 애플리케이션이 대상 프레임 속도에 도달하지 않고 최적화 작업이 필요할 수 있음을 나타내는 누락된 프레임을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="74744-140">메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="74744-140">Memory utilization</span></span>

<span data-ttu-id="74744-141">메모리 사용률 표시를 사용하면 현재 보기가 애플리케이션의 메모리 소비에 미치는 영향을 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler 메모리 Graph](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="74744-143">애플리케이션을 사용하는 경우 총 메모리 사용량을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="74744-144">핵심 지표에는 메모리 제한에 근접하고 사용량이 빠르게 변경되는 것이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74744-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="74744-145">시각적 프로파일러 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="74744-145">Customizing the visual profiler</span></span>

<span data-ttu-id="74744-146">Visual Profiler의 모양과 동작은 진단 시스템 프로필을 통해 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74744-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="74744-147">자세한 내용은 [진단 시스템 구성을](configuring-diagnostics.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74744-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="74744-148">참조</span><span class="sxs-lookup"><span data-stu-id="74744-148">See also</span></span>

- [<span data-ttu-id="74744-149">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="74744-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="74744-150">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="74744-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
