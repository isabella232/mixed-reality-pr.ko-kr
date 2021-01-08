---
title: 혼합 현실 성능 이해
description: Windows Mixed Reality 앱 성능을 분석 하 고 최적화 하기 위한 고급 정보 및 세부 정보를 알아보세요.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 성능, 최적화, CPU, GPU
ms.openlocfilehash: ff3db5d49ddab13a20c4c32de8e5640fff4f0d81
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008473"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="92783-104">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="92783-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="92783-105">이 문서에서는 혼합 현실 앱의 성능에 대 한 중요 한 개념을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="92783-106">최적의 프레임 속도에서 응용 프로그램이 실행 되지 않으면 사용자 환경이 크게 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-106">User experience can be greatly degraded if your application doesn't run at optimal frame rate.</span></span> <span data-ttu-id="92783-107">Holograms가 불안정 하 게 표시 되 고 환경에 대 한 헤드 추적이 부정확 하 게 표시 되어 사용자에 게 잘못 된 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="92783-108">성능은 혼합 현실 개발의 경우 첫 번째 클래스 기능으로 간주 되어야 하며,이는 폴란드어 작업이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="92783-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="92783-109">각 대상 플랫폼에 대 한 성능의 프레임 속도 값은 아래에 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="92783-110">플랫폼</span><span class="sxs-lookup"><span data-stu-id="92783-110">Platform</span></span> | <span data-ttu-id="92783-111">대상 프레임 율</span><span class="sxs-lookup"><span data-stu-id="92783-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="92783-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="92783-112">HoloLens</span></span>](../../hololens-hardware-details.md) | <span data-ttu-id="92783-113">60FPS</span><span class="sxs-lookup"><span data-stu-id="92783-113">60 FPS</span></span> |
| [<span data-ttu-id="92783-114">Windows Mixed Reality 울트라 Pc</span><span class="sxs-lookup"><span data-stu-id="92783-114">Windows Mixed Reality Ultra PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="92783-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="92783-115">90 FPS</span></span> |
| [<span data-ttu-id="92783-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="92783-116">Windows Mixed Reality PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="92783-117">60FPS</span><span class="sxs-lookup"><span data-stu-id="92783-117">60 FPS</span></span> |

<span data-ttu-id="92783-118">아래 프레임 워크는 대상 프레임 속도 적중에 대 한 모범 사례를 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="92783-119">Unity 환경에서 프레임 속도를 측정 하 고 개선 하는 방법에 대 한 팁은 [unity의 성능 권장 사항 문서를 참조](../unity/performance-recommendations-for-unity.md) 하세요.</span><span class="sxs-lookup"><span data-stu-id="92783-119">We recommend reading the [performance recommendations for Unity article](../unity/performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="92783-120">성능 병목 상태 이해</span><span class="sxs-lookup"><span data-stu-id="92783-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="92783-121">앱에 실적이 떨어지는 프레임 속도가 있는 경우 첫 번째 단계는 응용 프로그램의 계산 집약적 위치를 분석 하 고 이해 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="92783-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="92783-122">장면을 렌더링 하는 작업을 담당 하는 두 가지 기본 프로세서가 있습니다. CPU와 GPU는 혼합 현실 앱의 다양 한 측면을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU, each handling different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="92783-123">병목 현상이 발생할 수 있는 세 가지 주요 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-123">The three key places where bottlenecks may occur are:</span></span> 

1. <span data-ttu-id="92783-124">**앱 스레드-CPU** -
    입력, 애니메이션, 물리 및 기타 응용 프로그램 논리를 비롯 한 응용 프로그램 논리를 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-124">**App Thread - CPU** -
 Responsible for your app logic, including processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="92783-125">Gpu에 대 한 그리기 호출을 전송 하는 gpu에 **스레드 CPU를 렌더링** 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-125">**Render Thread - CPU to GPU** - Responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="92783-126">응용 프로그램에서 큐브나 모델 등의 개체를 렌더링 하려는 경우이 스레드는 작업을 수행 하기 위해 GPU에 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="92783-126">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to do the operations.</span></span>
3. <span data-ttu-id="92783-127">**GPU** -가장 일반적으로 응용 프로그램의 그래픽 파이프라인을 처리 하 여 3d 데이터 (모델, 질감 등)를 픽셀로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-127">**GPU** - Most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, and so on) into pixels.</span></span> <span data-ttu-id="92783-128">궁극적으로 장치 화면에 제출할 2D 이미지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-128">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![프레임 수명](images/lifetime-of-a-frame.png)

<span data-ttu-id="92783-130">일반적으로 HoloLens 응용 프로그램은 GPU에 바인딩되므로 항상 그렇지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-130">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="92783-131">아래 도구와 기술을 사용 하 여 특정 앱의 병목 현상이 발생 하는 위치를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-131">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="92783-132">응용 프로그램을 분석 하는 방법</span><span class="sxs-lookup"><span data-stu-id="92783-132">How to analyze your application</span></span>

<span data-ttu-id="92783-133">혼합 현실 응용 프로그램의 성능 프로필 및 잠재적 병목 상태를 이해할 수 있는 많은 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-133">There are many tools that allow you to understand the performance profile and potential bottlenecks in your mixed reality application.</span></span> 

<span data-ttu-id="92783-134">응용 프로그램에 대 한 심층 프로 파일링 정보를 수집 하는 데 도움이 되는 몇 가지 일반적인 도구는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-134">Below are some common tools to help you gather deep profiling information for your application:</span></span>
- [<span data-ttu-id="92783-135">Intel 그래픽 성능 분석기</span><span class="sxs-lookup"><span data-stu-id="92783-135">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="92783-136">Visual Studio 그래픽 디버거</span><span class="sxs-lookup"><span data-stu-id="92783-136">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [<span data-ttu-id="92783-137">Unity 프로파일러</span><span class="sxs-lookup"><span data-stu-id="92783-137">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="92783-138">Unity 프레임 디버거</span><span class="sxs-lookup"><span data-stu-id="92783-138">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="92783-139">모든 환경에서 프로 파일링 하는 방법</span><span class="sxs-lookup"><span data-stu-id="92783-139">How to profile in any environment</span></span>

<span data-ttu-id="92783-140">앱이 GPU 인지 아니면 CPU에 바인딩되어 있는지를 확인 하는 한 가지 방법은 렌더링 대상 출력의 해상도를 낮추는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="92783-140">One way to determine if your app is GPU or CPU bound is to lower the resolution of the render target output.</span></span> <span data-ttu-id="92783-141">계산할 픽셀 수를 줄이면 GPU 부하가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="92783-141">By reducing the number of pixels to calculate, you'll reduce your GPU load.</span></span> <span data-ttu-id="92783-142">장치는 작은 질감으로 렌더링 된 다음 위쪽의 샘플을 통해 최종 이미지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-142">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="92783-143">렌더링 해상도를 낮춘 후 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-143">After lowering rendering resolution, if:</span></span>
1) <span data-ttu-id="92783-144">응용 프로그램 프레임 속도가 **늘어나면** **GPU가 바인딩될** 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-144">Application framerate **increases**, then you're likely **GPU Bound**</span></span>
1) <span data-ttu-id="92783-145">응용 프로그램 프레임 속도가 **변경 되지 않은** 경우 **CPU 바인딩될** 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-145">Application framerate **unchanged**, then you're likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="92783-146">Unity는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해 런타임에 응용 프로그램의 렌더링 대상 해상도를 쉽게 수정할 수 있는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-146">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="92783-147">장치에 표시 되는 최종 이미지의 해상도는 고정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-147">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="92783-148">플랫폼은 디스플레이에서 렌더링 하기 위한 더 높은 해상도 이미지를 빌드하기 위해 낮은 해상도 출력을 샘플링 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-148">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="92783-149">응용 프로그램을 개선 하는 방법</span><span class="sxs-lookup"><span data-stu-id="92783-149">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="92783-150">CPU 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="92783-150">CPU performance recommendations</span></span>

<span data-ttu-id="92783-151">일반적으로 CPU의 혼합 현실 응용 프로그램에서 대부분의 작업은 장면의 "시뮬레이션"을 수행 하 고 응용 프로그램 논리를 처리 하는 작업을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-151">Generally, most work in a mixed reality application on the CPU involves doing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="92783-152">다음 영역은 최적화를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-152">The following areas are targeted for optimization:</span></span>

- <span data-ttu-id="92783-153">애니메이션</span><span class="sxs-lookup"><span data-stu-id="92783-153">Animations</span></span>
- <span data-ttu-id="92783-154">Physics</span><span class="sxs-lookup"><span data-stu-id="92783-154">Physics</span></span>
- <span data-ttu-id="92783-155">메모리 할당</span><span class="sxs-lookup"><span data-stu-id="92783-155">Memory allocations</span></span>
- <span data-ttu-id="92783-156">복합 알고리즘 (예:</span><span class="sxs-lookup"><span data-stu-id="92783-156">Complex algorithms (i.e</span></span> <span data-ttu-id="92783-157">역 기구학, 경로 찾기)</span><span class="sxs-lookup"><span data-stu-id="92783-157">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="92783-158">GPU 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="92783-158">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="92783-159">대역폭 및 채우기 빈도 이해</span><span class="sxs-lookup"><span data-stu-id="92783-159">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="92783-160">GPU에서 프레임을 렌더링할 때 응용 프로그램은 메모리 대역폭이 나 채우기 속도로 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="92783-160">When rendering a frame on the GPU, an application is either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="92783-161">**메모리 대역폭** 은 GPU에서 메모리를 통해 수행할 수 있는 읽기 및 쓰기의 률입니다.</span><span class="sxs-lookup"><span data-stu-id="92783-161">**Memory bandwidth** is the rate of reads and writes the GPU can do from memory</span></span>
    - <span data-ttu-id="92783-162">대역폭 제한을 확인 하려면 질감 품질을 줄이고 프레임 속도가 개선 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-162">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="92783-163">Unity에서    >  **프로젝트 설정**  >  **[품질 설정](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 편집에서 질감 품질을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-163">In Unity, change **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="92783-164">**채우기 비율은** GPU에서 초당 그릴 수 있는 픽셀을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92783-164">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="92783-165">채우기 속도 제한을 파악 하려면 디스플레이 해상도를 낮추고 프레임 속도가 개선 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-165">To identify fill rate limitations, lower the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="92783-166">Unity에서  *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-166">In Unity, use the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="92783-167">메모리 대역폭은 일반적으로 다음 중 하나에 대 한 최적화를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-167">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="92783-168">낮은 텍스처 해상도</span><span class="sxs-lookup"><span data-stu-id="92783-168">Lower texture resolutions</span></span>
2) <span data-ttu-id="92783-169">질감 (법선, 반사 등)을 덜 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-169">Use fewer textures (normals, specular, and so on)</span></span>

<span data-ttu-id="92783-170">채우기 비율은 다음과 같이 렌더링 된 최종 픽셀에 대해 계산 되어야 하는 작업의 수를 줄이는 데 중점을 두었습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-170">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel, including:</span></span>
1) <span data-ttu-id="92783-171">렌더링/처리할 개체 수</span><span class="sxs-lookup"><span data-stu-id="92783-171">Number of objects to render/process</span></span>
2) <span data-ttu-id="92783-172">셰이더 당 작업 수</span><span class="sxs-lookup"><span data-stu-id="92783-172">Number of operations per shader</span></span>
3) <span data-ttu-id="92783-173">최종 결과에 대 한 GPU 단계 수 (기 하 도형 셰이더, 처리 후 효과 등)</span><span class="sxs-lookup"><span data-stu-id="92783-173">Number of GPU stages to final result (geometry shaders, post-processing effects, and so on)</span></span>
4) <span data-ttu-id="92783-174">렌더링할 픽셀 수 (해상도 표시)</span><span class="sxs-lookup"><span data-stu-id="92783-174">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="92783-175">다각형 수 줄이기</span><span class="sxs-lookup"><span data-stu-id="92783-175">Reduce polygon count</span></span>

<span data-ttu-id="92783-176">다각형 수가 높을수록 GPU에 대 한 추가 작업이 발생 하므로 장면의 [다각형 수를 줄이면](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 렌더링 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="92783-176">Higher polygon counts result in more operations for the GPU, so [reducing the number of polygons](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene reduces the render time.</span></span> <span data-ttu-id="92783-177">기 하 도형에 비용이 많이 들 수 있는 다른 요인이 있지만 다각형 수는 장면을 렌더링 하는 데 걸리는 작업의 양을 결정 하는 가장 간단한 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="92783-177">There are other factors that make shading the geometry expensive, but polygon count is the simplest metric to determine how much work it will take to render a scene.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="92783-178">과도한 그리기 제한</span><span class="sxs-lookup"><span data-stu-id="92783-178">Limit overdraw</span></span>

<span data-ttu-id="92783-179">Occluding 개체에 의해 숨겨질 때 여러 개체가 렌더링 되지만 화면에 표시 되지 않는 경우에는 높은 오버 그리기가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-179">High overdraw occurs when multiple objects are rendered but not shown on screen as they're hidden by an occluding object.</span></span> <span data-ttu-id="92783-180">개체 뒤에 개체를 포함 하는 벽을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-180">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="92783-181">모든 기 하 도형은 렌더링을 위해 처리 되지만 불투명 벽만 렌더링 해야 하므로 불필요 한 작업이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-181">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered, which results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="92783-182">셰이더</span><span class="sxs-lookup"><span data-stu-id="92783-182">Shaders</span></span>

<span data-ttu-id="92783-183">셰이더는 GPU에서 실행 되는 작은 프로그램으로, 렌더링 시 다음 두 가지 중요 한 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-183">Shaders are small programs that run on the GPU and do two important steps in rendering:</span></span>
1) <span data-ttu-id="92783-184">그려야 하는 꼭 짓 점 및 화면 공간에 있는 위치 결정 (꼭 짓 점 셰이더)</span><span class="sxs-lookup"><span data-stu-id="92783-184">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="92783-185">꼭 짓 점 셰이더는 모든 메시에 대해 꼭 짓 점 마다 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92783-185">The Vertex shader is executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="92783-186">각 픽셀의 색 확인 (픽셀 셰이더)</span><span class="sxs-lookup"><span data-stu-id="92783-186">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="92783-187">픽셀 셰이더는 픽셀 단위로 실행 되 고 기 하 도형에 의해 대상 렌더링 질감으로 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92783-187">The Pixel shader is executed per pixel and rendered by the geometry to the target render texture.</span></span>

<span data-ttu-id="92783-188">일반적으로 셰이더는 많은 변환 및 조명 계산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-188">Typically, shaders do many transformations and lighting calculations.</span></span> <span data-ttu-id="92783-189">복합 조명 모델, 그림자 및 기타 작업은 환상적인 결과를 생성할 수 있지만 가격과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92783-189">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="92783-190">셰이더에서 계산 된 작업의 수를 줄이면 프레임 당 GPU에 필요한 작업을 크게 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-190">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="92783-191">셰이더 코딩 권장 사항</span><span class="sxs-lookup"><span data-stu-id="92783-191">Shader coding recommendations</span></span>

- <span data-ttu-id="92783-192">가능 하면 이중 선형 필터링 사용</span><span class="sxs-lookup"><span data-stu-id="92783-192">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="92783-193">식의 순서를 다시 정렬 하 여 여러 곱하기를 수행 하 고 동시에 추가</span><span class="sxs-lookup"><span data-stu-id="92783-193">Rearrange expressions to use MAD intrinsics to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="92783-194">CPU에서 최대한 Precalculate 하 고 재질에 상수로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-194">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="92783-195">**픽셀 셰이더의 작업을 꼭 짓 점 셰이더로 이동 합니다.**</span><span class="sxs-lookup"><span data-stu-id="92783-195">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="92783-196">일반적으로 꼭 짓 점 수는 픽셀 수 (720p는 921600 픽셀, 1080p는 2073600 픽셀 등) 보다 훨씬 작습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-196">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, and so on)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="92783-197">GPU 단계 제거</span><span class="sxs-lookup"><span data-stu-id="92783-197">Remove GPU stages</span></span>

<span data-ttu-id="92783-198">사후 처리 효과는 부담이 될 수 있으며 MSAA와 같은 앤티앨리어스 기법을 포함 하 여 응용 프로그램의 채우기 율을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-198">Post-processing effects can be expensive and increase the fill rate of your application, including anti-aliasing techniques like MSAA.</span></span> <span data-ttu-id="92783-199">HoloLens에서는 이러한 기술과 기 하 도형, 선체 및 계산 셰이더와 같은 추가 셰이더 단계를 방지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-199">On HoloLens, we recommended avoiding these techniques and additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="92783-200">메모리 추천 사항</span><span class="sxs-lookup"><span data-stu-id="92783-200">Memory recommendations</span></span>

<span data-ttu-id="92783-201">과도 한 메모리 할당 및 할당 취소 작업을 수행 하면 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92783-201">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="92783-202">메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-202">It's especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="92783-203">개체 풀링</span><span class="sxs-lookup"><span data-stu-id="92783-203">Object pooling</span></span>

<span data-ttu-id="92783-204">개체 풀링은 연속 할당 및 개체 할당 해제 비용을 줄이는 인기 있는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="92783-204">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="92783-205">이 작업을 수행하려면 시간이 지남에 따라 개체를 지속적으로 만들고 삭제하는 대신, 동일한 개체의 대량 풀을 할당하고 이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-205">This is done by allocating a large pool of identical objects and reusing inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="92783-206">개체 풀은 앱 중에 수명이 가변적인 다시 사용할 수 있는 구성 요소에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="92783-206">Object pools are great for reuseable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="92783-207">참조</span><span class="sxs-lookup"><span data-stu-id="92783-207">See also</span></span>
- [<span data-ttu-id="92783-208">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="92783-208">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
- [<span data-ttu-id="92783-209">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="92783-209">Recommended settings for Unity</span></span>](../unity/recommended-settings-for-unity.md)
- [<span data-ttu-id="92783-210">3D 모델 최적화</span><span class="sxs-lookup"><span data-stu-id="92783-210">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="92783-211">실시간 3D 모델 변환 및 최적화를 위한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="92783-211">Best practices for converting and optimizing real-time 3D Models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

