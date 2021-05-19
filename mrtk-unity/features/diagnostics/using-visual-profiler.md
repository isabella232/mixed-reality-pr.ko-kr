---
title: Profiler 사용
description: MRTK에서 Visual profiler를 사용 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143716"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="5e69a-104">시각적 프로파일러 사용</span><span class="sxs-lookup"><span data-stu-id="5e69a-104">Using the visual profiler</span></span>

<span data-ttu-id="5e69a-105">VisualProfiler는 혼합 현실 응용 프로그램의 성능에 대 한 사용 하기 쉬운 응용 프로그램 보기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="5e69a-106">프로파일러는 다음과 같은 모든 Mixed Reality 도구 키트 플랫폼에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="5e69a-107">Microsoft HoloLens (첫 번째 gen)</span><span class="sxs-lookup"><span data-stu-id="5e69a-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="5e69a-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5e69a-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="5e69a-109">Windows Mixed Reality 몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="5e69a-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="5e69a-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="5e69a-110">OpenVR</span></span>

<span data-ttu-id="5e69a-111">응용 프로그램을 개발 하는 동안 Visual Profiler가 현재 보기를 기준으로 데이터를 표시 하므로 장면의 여러 부분에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e69a-112">복합 개체, 파티클 효과 또는 활동을 사용 하 여 장면의 일부에 주목 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="5e69a-113">이러한 요소 및 기타 요소는 응용 프로그램 성능 및 이상적인 사용자 환경 감소에 영향을 주는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="5e69a-114">Visual profiler 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5e69a-114">Visual profiler interface</span></span>

![Visual Profiler 인터페이스](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="5e69a-116">Visual Profiler 인터페이스에는 다음 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="5e69a-117">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="5e69a-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="5e69a-118">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="5e69a-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="5e69a-119">프레임 그래프</span><span class="sxs-lookup"><span data-stu-id="5e69a-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="5e69a-120">메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="5e69a-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="5e69a-121">프레임 율</span><span class="sxs-lookup"><span data-stu-id="5e69a-121">Frame rate</span></span>

<span data-ttu-id="5e69a-122">인터페이스의 왼쪽 위 모퉁이에는 프레임 속도로 초당 프레임 수로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="5e69a-123">최상의 사용자 환경 및 편안 하 게이 값은 최대한 높아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="5e69a-124">특정 플랫폼 및 하드웨어 구성은 달성 가능한 최대 프레임 속도로 중요 한 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="5e69a-125">몇 가지 일반적인 대상 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-125">Some common target values include:</span></span>

- <span data-ttu-id="5e69a-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="5e69a-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="5e69a-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="5e69a-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="5e69a-128">기본 [MRC가 활성 상태일 때 HoloLens의 프레임 속도 제한으로](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)인해 비디오 및 사진이 캡처되는 동안 시각적 프로파일러가 자신을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="5e69a-129">이 설정은 진단 시스템 프로필에서 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="5e69a-130">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="5e69a-130">Frame time</span></span>

<span data-ttu-id="5e69a-131">프레임 속도의 오른쪽에는 CPU에 소요된 프레임 시간(밀리초)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="5e69a-132">앞에서 언급한 대상 프레임 속도를 달성하기 위해 애플리케이션은 프레임당 다음과 같은 시간을 소비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="5e69a-133">60fps: 16.6ms</span><span class="sxs-lookup"><span data-stu-id="5e69a-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="5e69a-134">90fps: 11.1ms</span><span class="sxs-lookup"><span data-stu-id="5e69a-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="5e69a-135">GPU 시간은 향후 릴리스에서 추가될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="5e69a-136">프레임 그래프</span><span class="sxs-lookup"><span data-stu-id="5e69a-136">Frame graph</span></span>

<span data-ttu-id="5e69a-137">프레임 그래프는 애플리케이션 프레임 속도 기록을 그래픽으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![시각적 프로파일러에서 프레임 그래프 누락](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="5e69a-139">애플리케이션을 사용하는 경우 애플리케이션이 대상 프레임 속도에 도달하지 않고 최적화 작업이 필요할 수 있음을 나타내는 누락된 프레임을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="5e69a-140">메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="5e69a-140">Memory utilization</span></span>

<span data-ttu-id="5e69a-141">메모리 사용률 표시를 사용하면 현재 보기가 애플리케이션의 메모리 소비에 미치는 영향을 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![시각적 프로파일러 메모리 그래프](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="5e69a-143">애플리케이션을 사용하는 경우 총 메모리 사용량을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="5e69a-144">핵심 지표에는 메모리 제한에 근접하고 사용량이 빠르게 변경되는 것이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="5e69a-145">시각적 프로파일러 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="5e69a-145">Customizing the visual profiler</span></span>

<span data-ttu-id="5e69a-146">Visual Profiler의 모양과 동작은 진단 시스템 프로필을 통해 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e69a-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="5e69a-147">자세한 내용은 [진단 시스템 구성을](configuring-diagnostics.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e69a-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e69a-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e69a-148">See also</span></span>

- [<span data-ttu-id="5e69a-149">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="5e69a-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="5e69a-150">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="5e69a-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)