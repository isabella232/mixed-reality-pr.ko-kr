---
title: 성능
description: MRTK의 전형을 이해하고 조정하는 설명서입니다.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6c8e060af585d7994774ea0bb575b6e5172b9558
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281763"
---
# <a name="performance"></a><span data-ttu-id="36e19-104">성능</span><span class="sxs-lookup"><span data-stu-id="36e19-104">Performance</span></span>

## <a name="getting-started"></a><span data-ttu-id="36e19-105">시작</span><span class="sxs-lookup"><span data-stu-id="36e19-105">Getting started</span></span>

<span data-ttu-id="36e19-106">성능을 합리화하는 가장 쉬운 방법은 프레임 속도 또는 애플리케이션이 초당 이미지를 렌더링할 수 있는 횟수를 통하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-106">The easiest way to rationalize performance is via framerate or how many times your application can render an image per second.</span></span> <span data-ttu-id="36e19-107">대상으로 지정되는 플랫폼에 설명된 대로 대상 프레임 전송률(즉,</span><span class="sxs-lookup"><span data-stu-id="36e19-107">It is important to meet the target framerate, as outlined by the platform being targeted (i.e</span></span> <span data-ttu-id="36e19-108">[Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)등).</span><span class="sxs-lookup"><span data-stu-id="36e19-108">[Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/), etc).</span></span> <span data-ttu-id="36e19-109">예를 들어 HoloLens 대상 프레임 속도는 60 FPS입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-109">For example, on HoloLens, the target framerate is 60 FPS.</span></span> <span data-ttu-id="36e19-110">프레임 속도 애플리케이션이 낮으면 [홀로그램 안정화,](../performance/hologram-stabilization.md)세계 추적, 손 추적 등과 같은 사용자 환경이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-110">Low framerate applications can result in deteriorated user experiences such as worsened [hologram stabilization](../performance/hologram-stabilization.md), world tracking, hand tracking, and more.</span></span> <span data-ttu-id="36e19-111">개발자가 품질 프레임 속도 추적 및 달성을 돕기 위해 Mixed Reality Toolkit 다양한 도구와 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-111">To help developers track and achieve quality framerate, the Mixed Reality Toolkit provides a variety of tools and scripts.</span></span>

### <a name="visual-profiler"></a><span data-ttu-id="36e19-112">시각적 프로파일러</span><span class="sxs-lookup"><span data-stu-id="36e19-112">Visual profiler</span></span>

<span data-ttu-id="36e19-113">개발 수명 동안 성능을 지속적으로 추적하려면 애플리케이션 디버깅을 & 실행하는 동안 항상 프레임 속도 시각적 개체를 표시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-113">To continuously track performance over the lifetime of development, it is highly recommended to always show a framerate visual while running & debugging an application.</span></span> <span data-ttu-id="36e19-114">Mixed Reality Toolkit 애플리케이션 보기에서 현재 FPS 및 메모리 사용에 대 한 실시간 정보를 제공 하는 [Visual Profiler](../features/diagnostics/using-visual-profiler.md) 진단 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-114">The Mixed Reality Toolkit provides the [Visual Profiler](../features/diagnostics/using-visual-profiler.md) diagnostic tool which gives real-time information about the current FPS and memory usage in application view.</span></span> <span data-ttu-id="36e19-115">[MRTK 프로필 검사기에서](../configuration/mixed-reality-configuration-guide.md) [진단 시스템 설정](../features/diagnostics/diagnostics-system-getting-started.md) 통해 시각적 프로파일러를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-115">The Visual Profiler can be configured via the [Diagnostics System Settings](../features/diagnostics/diagnostics-system-getting-started.md) under the [MRTK Profiles Inspector](../configuration/mixed-reality-configuration-guide.md).</span></span>

<span data-ttu-id="36e19-116">또한 Unity 편집기 또는 에뮬레이터에서 실행하는 대신 디바이스에서 실행할 때 Visual Profiler를 활용하여 프레임 전송률을 추적하는 것이 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-116">Furthermore, it is particularly important to utilize the Visual Profiler to track framerate when running on the device as opposed to running in Unity editor or an emulator.</span></span> <span data-ttu-id="36e19-117">[릴리스 구성 빌드를](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)통해 디바이스에서 실행할 때 가장 정확한 성능 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-117">The most accurate performance results will be depicted when running on the device with [Release configuration builds](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).</span></span>

> [!NOTE]
> <span data-ttu-id="36e19-118">Windows Mixed Reality 위해 빌드하는 경우 [MASTER 구성 빌드를 통해 배포합니다.](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)</span><span class="sxs-lookup"><span data-stu-id="36e19-118">If building for Windows Mixed Reality, deploy with [MASTER configuration builds](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)</span></span>

![Visual Profiler 인터페이스](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a><span data-ttu-id="36e19-120">최적화 창</span><span class="sxs-lookup"><span data-stu-id="36e19-120">Optimize window</span></span>

<span data-ttu-id="36e19-121">[MRTK 최적화 창은](../features/tools/optimize-window.md) 혼합 현실 개발자가 최상의 결과를 위해 환경을 설정하고 장면 & 자산의 잠재적 병목 현상을 식별하는 데 도움이 되는 정보 및 자동화 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-121">The [MRTK Optimize Window](../features/tools/optimize-window.md) offers information and automation tools to help mixed reality developers set up their environment for the best performing results and identify potential bottlenecks in their scene & assets.</span></span> <span data-ttu-id="36e19-122">Unity의 특정 주요 구성은 혼합 현실 프로젝트에 대해 훨씬 더 최적화된 결과를 제공하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-122">Certain key configurations in Unity can help deliver substantially more optimized results for mixed reality projects.</span></span>

<span data-ttu-id="36e19-123">일반적으로 이러한 설정에는 혼합 현실에 이상적인 렌더링 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-123">Generally, these settings involve rendering configurations that are ideal for mixed reality.</span></span> <span data-ttu-id="36e19-124">혼합 현실 애플리케이션은 두 개의 화면(즉,</span><span class="sxs-lookup"><span data-stu-id="36e19-124">Mixed reality applications are unique compared to traditional 3D graphics development in that there are two screens (i.e</span></span> <span data-ttu-id="36e19-125">두 눈)을 사용하여 전체 장면에 대해 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-125">two eyes) to render for the entire scene.</span></span>

<span data-ttu-id="36e19-126">아래에서 참조하는 권장 설정은 MRTK 최적화 창을 활용하여 Unity 프로젝트에서 자동으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-126">The recommended settings referenced below can be auto-configured in a Unity project by leveraging the MRTK Optimize Window.</span></span>

![MRTK 최적화 창 설정](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a><span data-ttu-id="36e19-128">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="36e19-128">Unity Profiler</span></span>

<span data-ttu-id="36e19-129">[Unity Profiler는](https://docs.unity3d.com/Manual/ProfilerWindow.html) 프레임 단위 수준에서 애플리케이션 성능의 세부 정보를 조사하는 데 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-129">The [Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) is a useful tool to investigate details of application performance at a frame-by-frame level.</span></span>

#### <a name="time-spent-on-the-cpu"></a><span data-ttu-id="36e19-130">CPU에 소요된 시간</span><span class="sxs-lookup"><span data-stu-id="36e19-130">Time spent on the CPU</span></span>

![Unity Profiler Graph 예제](../features/images/performance/UnityProfilerGraph.png)

<span data-ttu-id="36e19-132">편한 프레임 속도(일반적으로 초당 60프레임)를 유지하려면 애플리케이션에서 최대 16.6밀리초의 CPU 시간을 달성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-132">To maintain comfortable frame rates (typically 60 frames per second), applications need to achieve a maximum frame time of 16.6 milliseconds of CPU time.</span></span> <span data-ttu-id="36e19-133">MRTK 기능의 비용을 식별하기 위해 Microsoft Mixed Reality Toolkit 내부 루프(프레임당) 코드 경로에 대한 표식이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-133">To help identify the cost of MRTK functionality, the Microsoft Mixed Reality Toolkit contains a markers for inner loop (per frame) code paths.</span></span> <span data-ttu-id="36e19-134">이러한 표식은 사용 중인 특정 기능을 이해하는 데 도움이 하려면 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-134">These markers use the following format, to assist in understanding the specific functionality being utilized:</span></span>

```
[MRTK] className.methodName
```

> [!Note]
> <span data-ttu-id="36e19-135">메서드 이름 다음에 추가 데이터가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-135">There may be additional data following the method name.</span></span> <span data-ttu-id="36e19-136">이 기능은 애플리케이션 코드를 작게 변경하여 방지할 수 있는 조건부로 실행되고 비용이 많이 들 수 있는 기능을 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-136">This is used to identify conditionally executed, potentially expensive functionality that may be avoided by small changes to application code.</span></span>

![Unity Profiler 계층 구조 예제](../features/images/performance/UnityProfilerHierarchy.png)

<span data-ttu-id="36e19-138">이 예제에서는 계층 구조가 확장되어 WindowsMixedRealityArticulatedHand 클래스의 UpdateHandData 메서드가 분석되는 프레임 동안 0.44ms의 CPU 시간을 사용함을 보여 했습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-138">In this example, the hierarchy has been expanded to show that the UpdateHandData method of WindowsMixedRealityArticulatedHand class is consuming 0.44 ms of CPU time during the frame being analyzed.</span></span> <span data-ttu-id="36e19-139">이 데이터는 성능 문제가 애플리케이션 코드 또는 시스템의 다른 위치에서 관련되어 있는지 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-139">This data can be used to help determine if a performance issue is related to application code or from elsewhere in the system.</span></span>

<span data-ttu-id="36e19-140">개발자는 비슷한 방식으로 애플리케이션 코드를 계측하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-140">It is highly recommended that developers instrument application code in a similar fashion.</span></span> <span data-ttu-id="36e19-141">애플리케이션 코드 계측에 대한 주요 영역은 이벤트가 발생할 때 이러한 메서드가 MRTK 업데이트 루프에 청구되기 때문에 이벤트 처리기 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-141">Primary areas of focus for application code instrumentation is within event handlers as these methods are charged to the MRTK update loop as events are raised.</span></span> <span data-ttu-id="36e19-142">MRTK 업데이트 루프 내에서 프레임 시간이 높으면 이벤트 처리기 메서드에서 비용이 많이 드는 코드를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-142">High frame times within the MRTK update loop can be indicative of expensive code in event handler methods.</span></span>

## <a name="recommended-settings-for-unity"></a><span data-ttu-id="36e19-143">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="36e19-143">Recommended settings for Unity</span></span>

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="36e19-144">인스턴스 렌더링 Single-Pass</span><span class="sxs-lookup"><span data-stu-id="36e19-144">Single-Pass Instanced rendering</span></span>

<span data-ttu-id="36e19-145">Unity의 XR에 대한 기본 렌더링 구성은 [다중 패스](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-145">The default rendering configuration for XR in Unity is [Multi-pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html).</span></span> <span data-ttu-id="36e19-146">이 설정은 전체 렌더링 파이프라인을 각 시선에 대해 한 번씩 두 번 실행하도록 Unity에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-146">This setting instructs Unity to execute the entire render pipeline twice, once for each eye.</span></span> <span data-ttu-id="36e19-147">대신 단일 패스 인스턴스 [렌더링을](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 선택하여 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-147">This can be optimized by selecting [Single Pass Instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) instead.</span></span> <span data-ttu-id="36e19-148">이 구성은 [렌더링 대상 배열을](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 활용하여 각 눈의 적절한 렌더링 [대상에](https://en.wikipedia.org/wiki/Render_Target) 인스턴스가 있는 단일 그리기 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-148">This configuration leverages [render target arrays](https://en.wikipedia.org/wiki/Multiple_Render_Targets) to be able to perform a single draw call that instances into the appropriate [render target](https://en.wikipedia.org/wiki/Render_Target) for each eye.</span></span> <span data-ttu-id="36e19-149">또한 이 모드를 사용하면 렌더링 파이프라인의 단일 실행에서 모든 렌더링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-149">Furthermore, this mode allows all rendering to be done in a single execution of the rendering pipeline.</span></span> <span data-ttu-id="36e19-150">따라서 단일 패스 인스턴스 렌더링을 혼합 현실 애플리케이션의 렌더링 경로로 선택하면 [CPU & GPU에서 상당한 시간을 절약할](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) 수 있으며 권장되는 렌더링 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-150">Thus, selecting Single Pass Instanced rendering as the rendering path for a mixed reality application can [save substantial time on both the CPU & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) and is the recommended rendering configuration.</span></span>

<span data-ttu-id="36e19-151">그러나 각 눈에 대한 각 메시에 대해 단일 그리기 호출을 발급하려면 모든 [셰이더에서 GPU 인탄싱을](https://docs.unity3d.com/Manual/GPUInstancing.html) 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-151">However, in order to issue a single draw call for each mesh to each eye, [GPU instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) must be supported by all shaders.</span></span> <span data-ttu-id="36e19-152">인스턴싱을 사용하면 GPU가 양쪽 눈에서 호출을 멀티플렉싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-152">Instancing allows the GPU to multiplex draw calls across both eyes.</span></span> <span data-ttu-id="36e19-153">기본적으로 Unity 기본 제공 셰이더와 [MRTK 표준 셰이더에는](../features/rendering/mrtk-standard-shader.md) 셰이더 코드에 필요한 인탄싱 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-153">Unity built-in shaders as well as the [MRTK Standard shader](../features/rendering/mrtk-standard-shader.md) by default contain the necessary instancing instructions in shader code.</span></span> <span data-ttu-id="36e19-154">Unity에 대해 사용자 지정 셰이더를 작성하는 경우 Single Pass Instanced 렌더링을 지원하도록 이러한 셰이더를 업데이트해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-154">If writing custom shaders though for Unity, these shaders may need to be updated to support Single Pass Instanced rendering.</span></span>

#### <a name="example-code-for-custom-shader"></a>[<span data-ttu-id="36e19-155">사용자 지정 셰이더에 대한 예제 코드</span><span class="sxs-lookup"><span data-stu-id="36e19-155">Example Code for Custom Shader</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a><span data-ttu-id="36e19-156">품질 설정</span><span class="sxs-lookup"><span data-stu-id="36e19-156">Quality settings</span></span>

<span data-ttu-id="36e19-157">Unity는 각 플랫폼 엔드포인트에 대한 렌더링 [품질을 제어하기](https://docs.unity3d.com/Manual/class-QualitySettings.html) 위한 사전 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-157">Unity provides [presets to control quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) of rendering for each platform endpoint.</span></span> <span data-ttu-id="36e19-158">이러한 사전 설정은 그림자, 앤티 앨리어싱, 전역 조명 등과 같이 사용할 수 있는 그래픽 기능을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-158">These presets control what graphical features can be enabled such as shadows, anti-aliasing, global illumination, and more.</span></span> <span data-ttu-id="36e19-159">이러한 설정을 낮추고 렌더링하는 동안 수행되는 계산 수를 최적화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-159">It is recommended to lower these settings and optimize the number of calculations performed during rendering.</span></span>

<span data-ttu-id="36e19-160">*1단계:* *낮은 품질* 수준 설정을 사용하도록 혼합 현실 Unity 프로젝트 업데이트</span><span class="sxs-lookup"><span data-stu-id="36e19-160">*Step 1:* Update mixed reality Unity projects to use the *Low Quality* level setting</span></span>  
<span data-ttu-id="36e19-161">**편집**  >  **Project 설정** 품질 **범주** > UWP 플랫폼에 낮은 *품질* 선택</span><span class="sxs-lookup"><span data-stu-id="36e19-161">**Edit** > **Project Settings**, then select the **Quality** category >  Select *Low Quality* for the UWP Platform</span></span>

<span data-ttu-id="36e19-162">*2단계:* 모든 Unity 장면 파일에 대해 [실시간 글로벌 조명을](https://docs.unity3d.com/Manual/LightMode-Realtime.html) 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-162">*Step 2:* For every Unity scene file, disable [real-time Global Illumination](https://docs.unity3d.com/Manual/LightMode-Realtime.html)</span></span>  
<span data-ttu-id="36e19-163">**창**  >  **렌더링**  >  **조명 설정**  >  [ *실시간 전역 조명* 선택 취소](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span><span class="sxs-lookup"><span data-stu-id="36e19-163">**Window** > **Rendering** > **Lighting Settings** > [Uncheck *Real-time Global Illumination*](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span></span>

### <a name="depth-buffer-sharing-hololens"></a><span data-ttu-id="36e19-164">깊이 버퍼 공유(HoloLens)</span><span class="sxs-lookup"><span data-stu-id="36e19-164">Depth buffer sharing (HoloLens)</span></span>

<span data-ttu-id="36e19-165">Windows Mixed Reality 플랫폼 및 특히 HoloLens 대해 개발하는 경우 *XR 설정* 따라 *깊이 버퍼 공유를* 사용하도록 설정하면 [홀로그램 안정화에](../performance/hologram-stabilization.md)도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-165">If developing for the Windows Mixed Reality platform and in particular HoloLens, enabling *Depth Buffer Sharing* under *XR Settings* can help with [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="36e19-166">그러나 깊이 버퍼를 처리하면 특히 [24비트 깊이 형식 을](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)사용하는 경우 성능 비용이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-166">However, processing of the depth buffer can incur a performance cost, particularly if using [24-bit depth format](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html).</span></span> <span data-ttu-id="36e19-167">따라서 깊이 버퍼를 16비트 전체 자릿수로 구성하는 *것이 좋습니다.*</span><span class="sxs-lookup"><span data-stu-id="36e19-167">Thus, it is *highly recommended* to configure the depth buffer to 16-bit precision.</span></span>

<span data-ttu-id="36e19-168">낮은 비트 형식으로 인해 [z-fighting이](https://en.wikipedia.org/wiki/Z-fighting) 발생하는 경우 모든 카메라의 [원거리 클립 평면이](https://docs.unity3d.com/Manual/class-Camera.html) 애플리케이션에 대해 가능한 가장 낮은 값으로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-168">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs due to the lower bit format, confirm the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) of all cameras is set to the lowest possible value for the application.</span></span> <span data-ttu-id="36e19-169">Unity는 기본적으로 1000m의 원거리 클립 평면을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-169">Unity by default sets a far clip plane of 1000m.</span></span> <span data-ttu-id="36e19-170">HoloLens 50m의 원거리 클립 평면은 일반적으로 대부분의 애플리케이션 시나리오에서 충분한 것보다 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-170">On HoloLens, a far clip plane of 50m is generally more than enough for most application scenarios.</span></span>

> [!NOTE]
> <span data-ttu-id="36e19-171">*16비트 깊이 형식을* 사용하는 경우 Unity가 이 설정에서 [스텐실 버퍼를 만들지 않으므로 스텐실 버퍼에](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 필요한 효과가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-171">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="36e19-172">*24비트 깊이 형식을* 선택하면 일반적으로 엔드포인트 그래픽 플랫폼에 해당하는 경우 8비트 스텐실 버퍼가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-172">Selecting *24-bit depth format* conversely will generally create an 8-bit stencil buffer, if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="36e19-173">스텐실 버퍼가 필요한 [마스크 구성 요소를](https://docs.unity3d.com/Manual/script-Mask.html) 사용하는 경우 스텐실 버퍼가 필요하지 않으므로 *16비트 깊이 형식* 과 함께 사용할 수 있는 [RectMask2D를](https://docs.unity3d.com/Manual/script-RectMask2D.html) 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-173">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

> [!NOTE]
> <span data-ttu-id="36e19-174">장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 빠르게 확인하려면 MRTK 구성 프로필의 *편집기 설정* 아래에 [ *있는 렌더링 깊이 버퍼* 유틸리티를](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-174">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

### <a name="optimize-mesh-data"></a><span data-ttu-id="36e19-175">Mesh 데이터 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-175">Optimize Mesh Data</span></span>

<span data-ttu-id="36e19-176">[Mesh 데이터 최적화](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) 설정은 애플리케이션 내에서 사용되지 않는 꼭짓점 특성을 제거하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-176">The [Optimize Mesh Data](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) settings tries to remove unused vertex attributes within your application.</span></span> <span data-ttu-id="36e19-177">설정은 빌드의 모든 메시에 있는 모든 재질의 모든 셰이더 패스에 대해 를 실행하여 이를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-177">The setting performs this by running over every shader pass in every material that is on every mesh in the build.</span></span> <span data-ttu-id="36e19-178">이는 게임 데이터 크기 및 런타임 성능에 적합하지만 빌드 시간을 크게 저하할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-178">This is good for game data size and runtime performance but can drastically hinder build times.</span></span>

<span data-ttu-id="36e19-179">개발 중에 이 설정을 사용하지 않도록 설정하고 "마스터" 빌드를 만드는 동안 다시 사용하도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-179">It is recommended to disable this setting during development and re-enable during "Master" build creation.</span></span> <span data-ttu-id="36e19-180">설정은 Project 설정 플레이어 **편집**  >    >    >  **기타 설정** 메시 데이터 최적화에서 찾을 수  >  **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="36e19-180">The setting can be found under **Edit** > **Project Settings** > **Player** > **Other Settings** > **Optimize Mesh Data**.</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="36e19-181">일반 권장 사항</span><span class="sxs-lookup"><span data-stu-id="36e19-181">General recommendations</span></span>

<span data-ttu-id="36e19-182">성능은 혼합 현실 개발자에게 모호하고 지속적으로 변화하는 과제일 수 있으며 성능을 합리화하기 위한 지식 스펙트럼은 방대합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-182">Performance can be an ambiguous and constantly changing challenge for mixed reality developers and the spectrum of knowledge to rationalize performance is vast.</span></span> <span data-ttu-id="36e19-183">그러나 애플리케이션의 성능에 접근하는 방법을 이해하기 위한 몇 가지 일반적인 권장 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-183">There are some general recommendations for understanding how to approach performance for an application though.</span></span>

<span data-ttu-id="36e19-184">*CPU* 또는 *GPU에서* 실행되는 구성 요소로 애플리케이션 실행을 간소화하여 앱이 어느 구성 요소에 의해 제한되는지 여부를 식별하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-184">It is useful to simplify the execution of an application into the pieces that run on the *CPU* or the *GPU* and thus identify whether an app is bounded by either component.</span></span>  <span data-ttu-id="36e19-185">처리 단위와 신중하게 조사해야 하는 몇 가지 고유한 시나리오에 걸쳐 있는 병목 현상이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-185">There can be bottlenecks that span both processing units and some unique scenarios that have to be carefully investigated.</span></span> <span data-ttu-id="36e19-186">그러나 시작하기 위해 애플리케이션이 가장 많은 시간 동안 실행되는 위치를 파악하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-186">However, for getting started, it is good to grasp where an application is executing for the most amount of time.</span></span>

### <a name="gpu-bounded"></a><span data-ttu-id="36e19-187">GPU 경계</span><span class="sxs-lookup"><span data-stu-id="36e19-187">GPU bounded</span></span>

<span data-ttu-id="36e19-188">혼합 현실 애플리케이션에 대한 대부분의 플랫폼은 [스테레오 범위 렌더링을](https://en.wikipedia.org/wiki/Stereoscopy)활용하기 때문에 "이중 너비" 화면을 렌더링하는 특성으로 인해 GPU에 바인딩되는 것이 매우 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-188">Since most platforms for mixed reality applications are utilizing [stereoscopic rendering](https://en.wikipedia.org/wiki/Stereoscopy), it is very common to be GPU-bounded due to the nature of rendering a "double-wide" screen.</span></span> <span data-ttu-id="36e19-189">또한 HoloLens 또는 Oculus Quest와 같은 모바일 혼합 현실 플랫폼은 모바일 클래스 CPU & GPU 처리 능력으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-189">Futhermore, mobile mixed reality platforms such as HoloLens or Oculus Quest will be limited by mobile-class CPU & GPU processing power.</span></span>

<span data-ttu-id="36e19-190">GPU에 집중할 때 일반적으로 애플리케이션이 모든 프레임을 완료해야 하는 두 가지 중요한 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-190">When focusing on the GPU, there are generally two important stages that an application must complete every frame.</span></span>

1. <span data-ttu-id="36e19-191">[꼭짓점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) 실행</span><span class="sxs-lookup"><span data-stu-id="36e19-191">Execute the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)</span></span>
2. <span data-ttu-id="36e19-192">픽셀 [셰이더(조각 셰이더라고도](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 함)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-192">Execute the [pixel shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (also known as the fragment shader)</span></span>

<span data-ttu-id="36e19-193">렌더링 [파이프라인을](https://en.wikipedia.org/wiki/Graphics_pipeline)& 컴퓨터 그래픽의 복잡한 필드를 심도 있게 분석하지 않으면 각 셰이더 단계는 GPU에서 실행되어 다음을 생성하는 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-193">Without deep diving into the complex field of computer graphics & [rendering pipelines](https://en.wikipedia.org/wiki/Graphics_pipeline), each shader stage is a program that runs on the GPU to produce the following.</span></span>

1. <span data-ttu-id="36e19-194">꼭짓점 셰이더가 메시 꼭짓점을 화면 공간의 좌표로 변환(즉,</span><span class="sxs-lookup"><span data-stu-id="36e19-194">Vertex shaders transform mesh vertices to coordinates in screen-space (i.e</span></span> <span data-ttu-id="36e19-195">꼭짓점당 실행된 코드)</span><span class="sxs-lookup"><span data-stu-id="36e19-195">code executed per vertex)</span></span>
2. <span data-ttu-id="36e19-196">픽셀 셰이더가 지정된 픽셀 및 메시 조각(즉,</span><span class="sxs-lookup"><span data-stu-id="36e19-196">Pixel shaders calculate the color to draw for a given pixel and mesh fragment (i.e</span></span> <span data-ttu-id="36e19-197">픽셀당 코드 실행)</span><span class="sxs-lookup"><span data-stu-id="36e19-197">code execute per pixel)</span></span>

<span data-ttu-id="36e19-198">성능 튜닝과 관련하여 일반적으로 픽셀 셰이더에서 작업을 최적화하는 데 집중하는 것이 더 좋은 일입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-198">In regards to performance tuning, it is usually more fruitful to focus on optimizing the operations in the pixel shader.</span></span> <span data-ttu-id="36e19-199">애플리케이션은 꼭짓점이 8개인 큐브를 그리기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-199">An application may only need to draw a cube which will just be 8 vertices.</span></span> <span data-ttu-id="36e19-200">그러나 큐브가 차지하는 화면 공간은 수백만 픽셀 순서로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-200">However, the screen space that cube occupies is likely on the order of millions of pixels.</span></span> <span data-ttu-id="36e19-201">따라서 10 개의 작업을 통해 셰이더 코드를 줄이면 꼭 짓 점 셰이더 보다 픽셀 셰이더에 감소할 경우 훨씬 더 많은 작업을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-201">Thus, reducing shader code by say 10 operations can save significantly more work if reduced on the pixel shader than the vertex shader.</span></span>

<span data-ttu-id="36e19-202">이 셰이더가 일반적으로 [Mrtk 표준 셰이더](../features/rendering/mrtk-standard-shader.md) 를 활용 하는 주된 이유 중 하나는 미적 결과를 달성 하는 동안 Unity 표준 셰이더에 비해 픽셀 & 꼭 짓 점 마다 더 많은 명령을 실행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-202">This is one of the primary reasons for leveraging the [MRTK Standard shader](../features/rendering/mrtk-standard-shader.md) as this shader generally executes many less instructions per pixel & vertex than the Unity Standard shader while achieving comparable aesthetic results.</span></span>

|    <span data-ttu-id="36e19-203">CPU 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-203">CPU Optimizations</span></span>      |             <span data-ttu-id="36e19-204">GPU 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-204">GPU Optimizations</span></span>              |
|---------------------------|--------------------------------------------|
| <span data-ttu-id="36e19-205">앱 시뮬레이션 논리</span><span class="sxs-lookup"><span data-stu-id="36e19-205">App simulation logic</span></span>      | <span data-ttu-id="36e19-206">렌더링 작업</span><span class="sxs-lookup"><span data-stu-id="36e19-206">Rendering operations</span></span> |
| <span data-ttu-id="36e19-207">물리학 단순화</span><span class="sxs-lookup"><span data-stu-id="36e19-207">Simplify Physics</span></span>          | <span data-ttu-id="36e19-208">조명 계산 줄이기</span><span class="sxs-lookup"><span data-stu-id="36e19-208">Reduce lighting calculations</span></span> |
| <span data-ttu-id="36e19-209">애니메이션 간소화</span><span class="sxs-lookup"><span data-stu-id="36e19-209">Simplify Animations</span></span>       | <span data-ttu-id="36e19-210">그릴 수 있는 개체 수 & polygon 수 줄이기</span><span class="sxs-lookup"><span data-stu-id="36e19-210">Reduce polygon count & # of drawable objects</span></span> |
| <span data-ttu-id="36e19-211">가비지 수집 관리</span><span class="sxs-lookup"><span data-stu-id="36e19-211">Manage Garbage Collection</span></span> | <span data-ttu-id="36e19-212">투명 개체의 개수 줄이기</span><span class="sxs-lookup"><span data-stu-id="36e19-212">Reduce # of transparent objects</span></span> |
| <span data-ttu-id="36e19-213">캐시 참조</span><span class="sxs-lookup"><span data-stu-id="36e19-213">Cache References</span></span>          | <span data-ttu-id="36e19-214">사후 처리/전체 화면 효과 방지</span><span class="sxs-lookup"><span data-stu-id="36e19-214">Avoid post-processing/full-screen effects</span></span>  |

### <a name="draw-call-instancing"></a><span data-ttu-id="36e19-215">호출 인스턴스 그리기</span><span class="sxs-lookup"><span data-stu-id="36e19-215">Draw call instancing</span></span>

<span data-ttu-id="36e19-216">Unity에서 성능을 줄이는 가장 일반적인 실수 중 하나는 런타임에 대 한 복제 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-216">One of the most common mistakes in Unity that reduces performance is cloning materials at runtime.</span></span> <span data-ttu-id="36e19-217">Gameobject가 동일한 재질 및/또는 동일한 메시를 공유 하는 경우 *[정적 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[동적 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[GPU 인스턴스](https://docs.unity3d.com/Manual/GPUInstancing.html)* 등의 기술을 통해 단일 그리기 호출로 최적화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-217">If GameObjects share the same material and/or are the same mesh, they can be optimized into single draw calls via techniques such as *[static batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[dynamic batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, and *[GPU Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html)*.</span></span> <span data-ttu-id="36e19-218">그러나 개발자가 런타임에 [렌더러 재질](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 의 속성을 수정 하는 경우 Unity는 할당 된 자료의 클론 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-218">However, if developer's modify properties of a [Renderer's material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) at runtime, Unity will create a clone copy of the assigned material.</span></span>

<span data-ttu-id="36e19-219">예를 들어 장면에 100 큐브가 있는 경우 개발자는 런타임에 각각에 고유한 색을 할당 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-219">For example, if there are a 100 cubes in a scene, a developer may want to assign a unique color to each at runtime.</span></span> <span data-ttu-id="36e19-220">C #에서 [*렌더러에*](https://docs.unity3d.com/ScriptReference/Material-color.html) 대 한 액세스를 통해 Unity는이 특정 렌더러/GameObject에 대해 메모리에 새 자료를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-220">The access of [*renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# will make Unity create a new material in memory for this particular renderer/GameObject.</span></span> <span data-ttu-id="36e19-221">각 100 큐브는 고유한 자료를 포함 하므로 하나의 그리기 호출로 결합 될 수는 없으며, 대신 CPU에서 GPU로의 100 그리기 호출 요청이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-221">Each of the 100 cubes will have its own material and thus they cannot be merged together into one draw call, but instead will become 100 draw call requests from the CPU to the GPU.</span></span>

<span data-ttu-id="36e19-222">이러한 장애물을 극복 하 고 큐브 별로 고유한 색을 할당 하려면 개발자가 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)를 활용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-222">To overcome this obstacle and still assign a unique color per cube, developers should leverage [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span>

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a><span data-ttu-id="36e19-223">Unity 성능 도구</span><span class="sxs-lookup"><span data-stu-id="36e19-223">Unity performance tools</span></span>

<span data-ttu-id="36e19-224">Unity는 편집기에 기본 제공 되는 뛰어난 성능 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-224">Unity provides great performance tools that are built into the editor.</span></span>

- [<span data-ttu-id="36e19-225">Unity 프로파일러</span><span class="sxs-lookup"><span data-stu-id="36e19-225">Unity Profiler</span></span>](https://docs.unity3d.com/Manual//Profiler.html)
- [<span data-ttu-id="36e19-226">Unity 프레임 디버거</span><span class="sxs-lookup"><span data-stu-id="36e19-226">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

<span data-ttu-id="36e19-227">하나의 셰이더와 다른 셰이더 간의 대략적인 성능 균형을 예측 하는 경우 각 셰이더를 컴파일하고 셰이더 단계 당 작업 수를 확인 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-227">If estimating the rough performance tradeoff between one shader and another, it is useful to compile each shader and view the number of operations per shader stage.</span></span> <span data-ttu-id="36e19-228">[셰이더 자산](https://docs.unity3d.com/Manual/class-Shader.html) 을 선택 하 고 *컴파일 및 코드 표시* 단추를 클릭 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-228">This can be done by selecting a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) and clicking the *Compile and show code* button.</span></span> <span data-ttu-id="36e19-229">그러면 모든 셰이더 변형이 컴파일되고 결과가 포함 된 visual studio가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-229">This will compile all the shader variants and open visual studio with the results.</span></span> <span data-ttu-id="36e19-230">참고: 생성 된 통계 결과는 지정 된 셰이더를 활용 하는 자료에서 사용 하도록 설정 된 기능에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-230">Note: The statistic results produced may vary depending on what features have been enabled on materials utilizing the given shader.</span></span> <span data-ttu-id="36e19-231">Unity는 현재 프로젝트에서 직접 사용 되는 셰이더 변형만 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="36e19-231">Unity will only compile the shader variants being directly used in the current project.</span></span>

<span data-ttu-id="36e19-232">Unity 표준 셰이더 통계 예제</span><span class="sxs-lookup"><span data-stu-id="36e19-232">Unity Standard shader statistics example</span></span>

![Unity 표준 셰이더 통계 1](../features/images/performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="36e19-234">MRTK 표준 셰이더 통계 예제</span><span class="sxs-lookup"><span data-stu-id="36e19-234">MRTK Standard shader statistics example</span></span>

![MRTK 표준 셰이더 통계 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a><span data-ttu-id="36e19-236">참조</span><span class="sxs-lookup"><span data-stu-id="36e19-236">See also</span></span>

### <a name="unity"></a><span data-ttu-id="36e19-237">Unity</span><span class="sxs-lookup"><span data-stu-id="36e19-237">Unity</span></span>

- [<span data-ttu-id="36e19-238">초보자를 위한 Unity 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-238">Unity Performance Optimization for Beginners</span></span>](https://www.youtube.com/watch?v=1e5WY2qf600)
- [<span data-ttu-id="36e19-239">Unity 성능 최적화 자습서</span><span class="sxs-lookup"><span data-stu-id="36e19-239">Unity Performance Optimization Tutorials</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [<span data-ttu-id="36e19-240">Unity 최적화 모범 사례</span><span class="sxs-lookup"><span data-stu-id="36e19-240">Unity Optimization Best Practices</span></span>](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [<span data-ttu-id="36e19-241">그래픽 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-241">Optimizing graphics performance</span></span>](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [<span data-ttu-id="36e19-242">모바일 최적화 실용적인 가이드</span><span class="sxs-lookup"><span data-stu-id="36e19-242">Mobile Optimization Practical Guide</span></span>](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a><span data-ttu-id="36e19-243">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="36e19-243">Windows Mixed Reality</span></span>

- [<span data-ttu-id="36e19-244">Unity에 권장 되는 설정</span><span class="sxs-lookup"><span data-stu-id="36e19-244">Recommended Settings for Unity</span></span>](/windows/mixed-reality/recommended-settings-for-unity)
- [<span data-ttu-id="36e19-245">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="36e19-245">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="36e19-246">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="36e19-246">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)
- [<span data-ttu-id="36e19-247">ETW(Windows용 이벤트 추적) Unity 가이드</span><span class="sxs-lookup"><span data-stu-id="36e19-247">Event Tracing for Windows Unity Guide</span></span>](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a><span data-ttu-id="36e19-248">Oculus</span><span class="sxs-lookup"><span data-stu-id="36e19-248">Oculus</span></span>

- [<span data-ttu-id="36e19-249">성능 지침</span><span class="sxs-lookup"><span data-stu-id="36e19-249">Performance Guidelines</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [<span data-ttu-id="36e19-250">성능 도구</span><span class="sxs-lookup"><span data-stu-id="36e19-250">Performance Tools</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a><span data-ttu-id="36e19-251">메시 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-251">Mesh optimization</span></span>

- [<span data-ttu-id="36e19-252">3D 모델 최적화</span><span class="sxs-lookup"><span data-stu-id="36e19-252">Optimize 3D models</span></span>](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="36e19-253">실시간 3D 모델 변환 및 최적화를 위한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="36e19-253">Best practices for converting and optimizing real-time 3D models</span></span>](/dynamics365/mixed-reality/import-tool/best-practices)
