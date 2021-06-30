---
title: 시각적 프로파일러 사용
description: MRTK에서 Visual profiler를 사용 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121651"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="af3fb-104">시각적 프로파일러 사용</span><span class="sxs-lookup"><span data-stu-id="af3fb-104">Using the visual profiler</span></span>

<span data-ttu-id="af3fb-105">VisualProfiler는 혼합 현실 응용 프로그램의 성능에 대 한 사용 하기 쉬운 응용 프로그램 보기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="af3fb-106">프로파일러는 다음과 같은 모든 Mixed Reality 도구 키트 플랫폼에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="af3fb-107">Microsoft HoloLens (첫 번째 gen)</span><span class="sxs-lookup"><span data-stu-id="af3fb-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="af3fb-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="af3fb-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="af3fb-109">Windows Mixed Reality 몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="af3fb-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="af3fb-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="af3fb-110">OpenVR</span></span>

<span data-ttu-id="af3fb-111">응용 프로그램을 개발 하는 동안 Visual Profiler가 현재 보기를 기준으로 데이터를 표시 하므로 장면의 여러 부분에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af3fb-112">복합 개체, 파티클 효과 또는 활동을 사용 하 여 장면의 일부에 주목 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="af3fb-113">이러한 요소 및 기타 요소는 응용 프로그램 성능 및 이상적인 사용자 환경 감소에 영향을 주는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="af3fb-114">Visual profiler 인터페이스</span><span class="sxs-lookup"><span data-stu-id="af3fb-114">Visual profiler interface</span></span>

![Visual Profiler 인터페이스](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="af3fb-116">Visual Profiler 인터페이스에는 다음 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="af3fb-117">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="af3fb-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="af3fb-118">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="af3fb-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="af3fb-119">프레임 그래프</span><span class="sxs-lookup"><span data-stu-id="af3fb-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="af3fb-120">메모리 사용량</span><span class="sxs-lookup"><span data-stu-id="af3fb-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="af3fb-121">프레임 율</span><span class="sxs-lookup"><span data-stu-id="af3fb-121">Frame rate</span></span>

<span data-ttu-id="af3fb-122">인터페이스의 왼쪽 위 모퉁이에는 프레임 속도로 초당 프레임 수로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="af3fb-123">최상의 사용자 환경 및 편안 하 게이 값은 최대한 높아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="af3fb-124">특정 플랫폼 및 하드웨어 구성은 달성 가능한 최대 프레임 속도로 중요 한 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="af3fb-125">몇 가지 일반적인 대상 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-125">Some common target values include:</span></span>

- <span data-ttu-id="af3fb-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="af3fb-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="af3fb-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="af3fb-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="af3fb-128">[기본 MRC가 활성 상태인 경우 HoloLens에서 프레임 속도로 제한](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)되기 때문에, 비디오와 사진을 캡처하는 동안에는 시각적 프로파일러가 자신을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="af3fb-129">이 설정은 진단 시스템 프로필에서 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="af3fb-130">프레임 시간</span><span class="sxs-lookup"><span data-stu-id="af3fb-130">Frame time</span></span>

<span data-ttu-id="af3fb-131">프레임 주기 오른쪽은 CPU에 소요 된 프레임 시간 (밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="af3fb-132">이전에 언급 한 대상 프레임 속도를 얻기 위해 응용 프로그램은 프레임당 다음과 같은 시간을 소비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="af3fb-133">60 fps: 16.6 밀리초</span><span class="sxs-lookup"><span data-stu-id="af3fb-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="af3fb-134">90 fps: 11.1 밀리초</span><span class="sxs-lookup"><span data-stu-id="af3fb-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="af3fb-135">GPU 시간은 이후 릴리스에 추가 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="af3fb-136">프레임 그래프</span><span class="sxs-lookup"><span data-stu-id="af3fb-136">Frame graph</span></span>

<span data-ttu-id="af3fb-137">프레임 그래프는 응용 프로그램 프레임 요금 기록의 그래픽 표시를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![시각적 프로파일러 누락 프레임 그래프](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="af3fb-139">응용 프로그램을 사용 하는 경우 응용 프로그램이 대상 프레임 속도로 적중 하지 않으며 최적화 작업이 필요할 수 있음을 나타내는 누락 된 프레임을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="af3fb-140">메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="af3fb-140">Memory utilization</span></span>

<span data-ttu-id="af3fb-141">메모리 사용률 표시를 사용 하면 현재 뷰가 응용 프로그램의 메모리 사용에 영향을 주는 방법을 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler 메모리 그래프](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="af3fb-143">응용 프로그램을 사용 하는 경우 총 메모리 사용량을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="af3fb-144">키 표시기에는 메모리 제한과 사용량에 대 한 빠른 변경 내용이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="af3fb-145">시각적 프로파일러 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="af3fb-145">Customizing the visual profiler</span></span>

<span data-ttu-id="af3fb-146">진단 시스템 프로필을 통해 Visual Profiler의 모양과 동작을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3fb-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="af3fb-147">자세한 내용은 [진단 시스템 구성](configuring-diagnostics.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3fb-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="af3fb-148">참조</span><span class="sxs-lookup"><span data-stu-id="af3fb-148">See also</span></span>

- [<span data-ttu-id="af3fb-149">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="af3fb-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="af3fb-150">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="af3fb-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)