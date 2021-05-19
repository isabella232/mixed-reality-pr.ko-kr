---
title: 최적화 창
description: MRTK의 설명서 최적화 창
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 7ffc2173cc55c83f126f66002d9240cb349d7f59
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144316"
---
# <a name="optimize-window"></a><span data-ttu-id="8a261-104">창 최적화</span><span class="sxs-lookup"><span data-stu-id="8a261-104">Optimize window</span></span>

<span data-ttu-id="8a261-105">MRTK 최적화 창은 Unity에서 최상의 [성능을](../../performance/perf-getting-started.md) 위해 혼합 현실 프로젝트를 구성하는 프로세스를 자동화하고 알리는 데 도움이 되는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-105">The MRTK Optimize Window is a utility to help automate and inform in the process of configuring a mixed reality project for best [performance](../../performance/perf-getting-started.md) in Unity.</span></span> <span data-ttu-id="8a261-106">이 도구는 일반적으로 올바른 사전 설정으로 설정하면 처리 시간을 밀리초 절약할 수 있는 렌더링 구성에 중점을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-106">This tool generally focuses on rendering configurations that when set to the correct preset can save milliseconds of processing.</span></span>

<span data-ttu-id="8a261-107">*활성 빌드 대상은* 현재 컴파일을 위해 프로젝트의 [대상이 되는 빌드 플랫폼입니다.](https://docs.unity3d.com/Manual/BuildSettings.html)</span><span class="sxs-lookup"><span data-stu-id="8a261-107">The *Active Build Target* is the [build platform currently targeted](https://docs.unity3d.com/Manual/BuildSettings.html) by the project for compiling.</span></span>

<span data-ttu-id="8a261-108">*성능 대상은* 대상 디바이스 엔드포인트의 종류에 대해 최적화 도구에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-108">The *Performance Target* instructs the optimize tool on what kind of device endpoints to target.</span></span>

- <span data-ttu-id="8a261-109">*AR 헤드셋은* HoloLens와 같은 모바일 클래스 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-109">*AR Headsets* are mobile-class devices, such as HoloLens</span></span>
- <span data-ttu-id="8a261-110">*VR 독립 실행형은* Oculus Go 또는 Quest와 같은 모바일 클래스 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-110">*VR Standalone* are mobile-class devices, such as the Oculus Go or Quest</span></span>
- <span data-ttu-id="8a261-111">*VR Tethered는* Samsung Odyssey, Oculus Room 또는 HTC Vive 등 PC 기반 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-111">*VR Tethered* are PC-powered devices, such as the Samsung Odyssey, Oculus Rift or HTC Vive etc.</span></span>

![MRTK 창 성능 목표 최적화](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a><span data-ttu-id="8a261-113">최적화 설정</span><span class="sxs-lookup"><span data-stu-id="8a261-113">Setting optimizations</span></span>

<span data-ttu-id="8a261-114">설정 최적화 탭에는 Unity 프로젝트에 대한 몇 가지 중요한 렌더링 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-114">The settings optimization tab covers some of the important rendering configurations for a Unity project.</span></span> <span data-ttu-id="8a261-115">이 섹션은 최상의 결과를 위해 변경해야 하는 설정을 자동화하고 알리는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-115">This section can help automate and inform you of which settings should be changed for the best performing results.</span></span>

<span data-ttu-id="8a261-116">녹색 확인 아이콘은 이 특정 설정에 대한 프로젝트/장면에서 최적 값이 구성되었다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-116">A green check icon means that an optimal value has been configured in the project/scene for this particular setting.</span></span> <span data-ttu-id="8a261-117">노란색 경고 아이콘은 현재 구성을 개선할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-117">A yellow warning icon indicates the current configuration can be improved.</span></span> <span data-ttu-id="8a261-118">지정된 섹션에서 연결된 단추를 클릭하면 Unity 프로젝트/장면에서 해당 설정을 더 최적의 값으로 자동 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-118">Clicking the associated button in a given section will auto-configure that setting in the Unity project/scene to a more optimal value.</span></span>

![MRTK 창 설정 최적화](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="8a261-120">단일 패스 인스턴스 렌더링</span><span class="sxs-lookup"><span data-stu-id="8a261-120">Single Pass Instanced rendering</span></span>

<span data-ttu-id="8a261-121">[단일 패스 인스턴스 렌더링은](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 혼합 현실 애플리케이션에 대한 가장 효율적인 렌더링 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-121">[Single Pass instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) is the most efficient rendering path for mixed reality applications.</span></span> <span data-ttu-id="8a261-122">이 구성을 통해 렌더링 파이프라인이 두 눈 모두에 대해 한 번만 실행되고 그리기 호출이 양쪽 눈에서 인스턴스화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-122">This configuration ensures the render pipeline is executed only once for both eyes and that draw calls are instanced across both eyes.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="8a261-123">깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="8a261-123">Depth buffer sharing</span></span>

<span data-ttu-id="8a261-124">[홀로그램 안정화](../../performance/hologram-Stabilization.md)를 개선 하기 위해 개발자는 렌더링 된 장면에서 안정화 되는 위치 및 holograms에 대 한 플랫폼 정보를 제공 하는 응용 프로그램의 깊이 버퍼를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-124">To improve [hologram stabilization](../../performance/hologram-Stabilization.md), developers can share the application's depth buffer which gives the platform information on where and what holograms to stabilize in the rendered scene.</span></span>

### <a name="depth-buffer-format"></a><span data-ttu-id="8a261-125">깊이 버퍼 형식</span><span class="sxs-lookup"><span data-stu-id="8a261-125">Depth buffer format</span></span>

<span data-ttu-id="8a261-126">또한 *AR 헤드셋* 의 경우 24 비트와 비교 하 여 깊이 버퍼를 공유할 수 있도록 설정 하는 경우 16 비트 깊이 형식을 활용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-126">Furthermore, for *AR Headsets*, it is recommended to utilize a 16-bit depth format when enabling depth buffer sharing compared to 24-bit.</span></span> <span data-ttu-id="8a261-127">이는 더 낮은 정밀도를 의미 하지만 성능에는 절약 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-127">This means lower precision but saves on performance.</span></span> <span data-ttu-id="8a261-128">픽셀에 대 한 깊이를 계산 하는 데 더 낮은 정밀도가 있기 때문에 [z](https://en.wikipedia.org/wiki/Z-fighting) 이동이 발생 하는 경우에는 [먼 클립 평면](https://docs.unity3d.com/Manual/class-Camera.html) 을 카메라에 가깝게 이동 하는 것이 좋습니다 (예: 1000m 대신 5천만 개).</span><span class="sxs-lookup"><span data-stu-id="8a261-128">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs because there is less precision in calculating depth for pixels, then it is recommended to move the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) closer to the camera (ex: 50m instead of 1000m).</span></span>

> [!NOTE]
> <span data-ttu-id="8a261-129">*16 비트 깊이 형식을* 사용 하는 경우 Unity에서이 설정에 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 스텐실 버퍼 필요 효과가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-129">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="8a261-130">이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 해당 하는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html)생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-130">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="8a261-131">스텐실 버퍼가 필요한 [마스크 구성 요소](https://docs.unity3d.com/Manual/script-Mask.html) 를 사용 하는 경우 스텐실 버퍼를 요구 하지 않으므로 *16 비트 깊이 형식과* 함께 사용할 수 있는 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) 를 대신 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-131">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

### <a name="real-time-global-illumination"></a><span data-ttu-id="8a261-132">실시간 글로벌 조명</span><span class="sxs-lookup"><span data-stu-id="8a261-132">Real-time Global Illumination</span></span>

<span data-ttu-id="8a261-133">Unity의 [실시간 글로벌 조명이](https://docs.unity3d.com/Manual/GIIntro.html) 뛰어난 미적 결과를 제공할 수 있지만 매우 많은 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-133">[Real-time Global illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide fantastic aesthetic results but at a very high cost.</span></span> <span data-ttu-id="8a261-134">글로벌 조명 조명은 혼합 현실에서 매우 많은 비용이 들기 때문에 개발에서이 기능을 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-134">Global illumination lighting is very expensive in mixed reality and thus it is recommended to disable this feature in development.</span></span>

> [!NOTE]
> <span data-ttu-id="8a261-135">Unity의 전역 조명 설정은 전체 프로젝트에서 한 번도 설정 되지 않고 장면 별로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-135">Global illumination settings in Unity are set per-scene and not once across the entire project.</span></span>

## <a name="scene-analysis"></a><span data-ttu-id="8a261-136">장면 분석</span><span class="sxs-lookup"><span data-stu-id="8a261-136">Scene analysis</span></span>

<span data-ttu-id="8a261-137">*장면 분석* 탭은 현재 장면에 있는 어떤 요소가 성능에 가장 많은 영향을 줄 가능성이 있음을 개발자에 게 알리기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-137">The *Scene Analysis* tab is designed to inform developers on which elements currently in the scene will likely have the most impact on performance.</span></span>

![MRTK 최적화 창 설정 장면 분석](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a><span data-ttu-id="8a261-139">조명 분석</span><span class="sxs-lookup"><span data-stu-id="8a261-139">Lighting analysis</span></span>

<span data-ttu-id="8a261-140">이 섹션에서는 그림자를 사용 하지 않도록 설정 해야 하는 조명 뿐만 아니라 장면의 현재 조명 수를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-140">This section will examine the number of lights currently in the scene, as well as any lights that should disable shadows.</span></span> <span data-ttu-id="8a261-141">섀도 캐스팅은 비용이 많이 드는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-141">Shadow casting is a very expensive operation.</span></span>

### <a name="polygon-count-analysis"></a><span data-ttu-id="8a261-142">다각형 개수 분석</span><span class="sxs-lookup"><span data-stu-id="8a261-142">Polygon count analysis</span></span>

<span data-ttu-id="8a261-143">이 도구는 다각형 개수 통계도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-143">The tool also provides polygon count statistics.</span></span> <span data-ttu-id="8a261-144">최적화를 대상으로 하는 지정된 장면에서 다각형 복잡성이 가장 높은 GameObject를 빠르게 식별하는 것이 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-144">It can be very helpful to quickly identify which GameObjects have the highest polygon complexity in a given scene to target for optimizations.</span></span>

### <a name="unity-ui-raycast-analysis"></a><span data-ttu-id="8a261-145">Unity UI 광선 캐스트 분석</span><span class="sxs-lookup"><span data-stu-id="8a261-145">Unity UI raycast analysis</span></span>

<span data-ttu-id="8a261-146">그래픽 광선 캐스트 작업은 MRTK의 포인터별로 수행되어 Unity UI 요소가 포커스에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-146">Graphics raycast operations are performed per pointer in MRTK to determine if any Unity UI elements are in focus.</span></span> <span data-ttu-id="8a261-147">이러한 광선 캐스트는 비용이 많이 들 수 있으며 성능 향상을 위해 결과에 반환할 필요가 없는 UI 요소를 raycast 대상으로 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-147">These raycasts can be quite expensive and to help improve performance, UI elements that do not need to be returned in the results should be disabled as raycast targets.</span></span> <span data-ttu-id="8a261-148">모든 [Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 요소에는 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-148">Every [Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) element has a [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) property.</span></span> <span data-ttu-id="8a261-149">이 도구는 이 속성을 사용하도록 설정하여 사용하지 않도록 설정할 가능성이 높은 텍스트 UI 요소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-149">This tool will search for text UI elements that have this property enabled and thus are likely candidates to be disabled.</span></span>

## <a name="shader-analysis"></a><span data-ttu-id="8a261-150">셰이더 분석</span><span class="sxs-lookup"><span data-stu-id="8a261-150">Shader analysis</span></span>

<span data-ttu-id="8a261-151">[Unity 표준 셰이더에서는](https://docs.unity3d.com/Manual/shader-StandardShader.html) 게임에 대해 매우 높은 품질의 시각적 결과를 생성할 수 있지만, 일반적으로 혼합 현실 애플리케이션의 성능 요구 사항에 가장 적합하지는 않습니다. 특히 이러한 애플리케이션은 일반적으로 GPU에 제한되기 때문에 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-151">The [Unity Standard shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) can produce very high quality visual results for games but is not generally best suited for the performance needs of mixed reality applications, especially since such applications are generally GPU bounded.</span></span> <span data-ttu-id="8a261-152">따라서 개발자는 [MRTK 표준 셰이더를](../rendering/mrtk-standard-shader.md) 활용하여 미적 & 그래픽 기능과 성능의 균형을 맞추는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-152">Thus, it is recommended to developers to utilize the [MRTK Standard shader](../rendering/mrtk-standard-shader.md) to balance aesthetics & graphical features with performance.</span></span>

<span data-ttu-id="8a261-153">*셰이더 분석* 탭은 Unity 표준 셰이더를 사용하여 현재 프로젝트의 자산 폴더에서 재질을 검색하거나, 원하는 경우 Mixed Reality Toolkit 제공 셰이더를 사용하지 않는 모든 재질을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-153">The *Shader Analysis* tab scans the current project's Asset folder for materials using the Unity Standard shader or if desired, all materials not using Mixed Reality Toolkit provided shaders.</span></span> <span data-ttu-id="8a261-154">검색되면 개발자는 적절한 단추를 사용하여 모든 재질을 변환하거나 개별적으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a261-154">Once discovered, developers can convert all materials or convert individually using the appropriate buttons.</span></span>

![MRTK 창 설정 셰이더 분석 최적화](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a><span data-ttu-id="8a261-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a261-156">See also</span></span>

- [<span data-ttu-id="8a261-157">성능</span><span class="sxs-lookup"><span data-stu-id="8a261-157">Performance</span></span>](../../performance/perf-getting-started.md)
- [<span data-ttu-id="8a261-158">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="8a261-158">Hologram Stabilization</span></span>](../../performance/hologram-stabilization.md)
