---
title: 최적화 창
description: MRTK의 문서 최적화 창
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f9f8ad638b8f7cb1007c923f6b568dffc4340360
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177563"
---
# <a name="optimize-window"></a><span data-ttu-id="4570d-104">최적화 창</span><span class="sxs-lookup"><span data-stu-id="4570d-104">Optimize window</span></span>

<span data-ttu-id="4570d-105">MRTK Optimize 창은 Unity에서 최상의 [성능을](../../performance/perf-getting-started.md) 위해 혼합 현실 프로젝트를 구성 하는 프로세스를 자동화 하 고 알리는 데 도움이 되는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-105">The MRTK Optimize Window is a utility to help automate and inform in the process of configuring a mixed reality project for best [performance](../../performance/perf-getting-started.md) in Unity.</span></span> <span data-ttu-id="4570d-106">이 도구는 일반적으로 올바른 사전 설정으로 설정 하면 처리 시간 (밀리초)을 줄일 수 있는 렌더링 구성에 중점을 둔 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-106">This tool generally focuses on rendering configurations that when set to the correct preset can save milliseconds of processing.</span></span>

<span data-ttu-id="4570d-107">*활성 빌드 대상은* 현재 프로젝트에서 컴파일을 위해 대상으로 하는 [빌드 플랫폼](https://docs.unity3d.com/Manual/BuildSettings.html) 입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-107">The *Active Build Target* is the [build platform currently targeted](https://docs.unity3d.com/Manual/BuildSettings.html) by the project for compiling.</span></span>

<span data-ttu-id="4570d-108">*성능 목표* 는 대상으로 할 장치 끝점의 종류에 맞게 최적화 도구에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-108">The *Performance Target* instructs the optimize tool on what kind of device endpoints to target.</span></span>

- <span data-ttu-id="4570d-109">*AR 헤드셋* 은 HoloLens와 같은 모바일 클래스 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-109">*AR Headsets* are mobile-class devices, such as HoloLens</span></span>
- <span data-ttu-id="4570d-110">*VR 독립 실행형* 은 Oculus Go 또는 Quest와 같은 모바일 클래스 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-110">*VR Standalone* are mobile-class devices, such as the Oculus Go or Quest</span></span>
- <span data-ttu-id="4570d-111">*VR 테더 링 된* 는 Samsung Odyssey, Oculus RIFT 또는 HTC vive 등의 PC 구동 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-111">*VR Tethered* are PC-powered devices, such as the Samsung Odyssey, Oculus Rift or HTC Vive etc.</span></span>

![MRTK 창 성능 목표를 최적화 합니다.](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a><span data-ttu-id="4570d-113">최적화 설정</span><span class="sxs-lookup"><span data-stu-id="4570d-113">Setting optimizations</span></span>

<span data-ttu-id="4570d-114">설정 최적화 탭에는 Unity 프로젝트에 대 한 몇 가지 중요 한 렌더링 구성 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-114">The settings optimization tab covers some of the important rendering configurations for a Unity project.</span></span> <span data-ttu-id="4570d-115">이 섹션은 가장 적합 한 결과를 위해 변경 해야 하는 설정을 자동화 하 고 알리는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-115">This section can help automate and inform you of which settings should be changed for the best performing results.</span></span>

<span data-ttu-id="4570d-116">녹색 확인 아이콘은이 특정 설정에 대 한 프로젝트/장면에서 최적의 값이 구성 되었음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-116">A green check icon means that an optimal value has been configured in the project/scene for this particular setting.</span></span> <span data-ttu-id="4570d-117">노란색 경고 아이콘은 현재 구성이 향상 될 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-117">A yellow warning icon indicates the current configuration can be improved.</span></span> <span data-ttu-id="4570d-118">지정 된 섹션에서 연결 된 단추를 클릭 하면 Unity 프로젝트/장면의 해당 설정이 보다 최적 값으로 자동 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-118">Clicking the associated button in a given section will auto-configure that setting in the Unity project/scene to a more optimal value.</span></span>

![MRTK 창 설정 최적화](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="4570d-120">단일 패스 인스턴스화된 렌더링</span><span class="sxs-lookup"><span data-stu-id="4570d-120">Single Pass Instanced rendering</span></span>

<span data-ttu-id="4570d-121">[단일 패스 인스턴스화된 렌더링](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 은 혼합 현실 응용 프로그램의 가장 효율적인 렌더링 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-121">[Single Pass instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) is the most efficient rendering path for mixed reality applications.</span></span> <span data-ttu-id="4570d-122">이 구성을 사용 하면 렌더링 파이프라인이 눈에 한 번만 실행 되 고 그리기 호출이 두 눈 모두에 걸쳐 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-122">This configuration ensures the render pipeline is executed only once for both eyes and that draw calls are instanced across both eyes.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="4570d-123">깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="4570d-123">Depth buffer sharing</span></span>

<span data-ttu-id="4570d-124">[홀로그램 안정화](../../performance/hologram-Stabilization.md)를 개선 하기 위해 개발자는 렌더링 된 장면에서 안정화 되는 위치 및 holograms에 대 한 플랫폼 정보를 제공 하는 응용 프로그램의 깊이 버퍼를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-124">To improve [hologram stabilization](../../performance/hologram-Stabilization.md), developers can share the application's depth buffer which gives the platform information on where and what holograms to stabilize in the rendered scene.</span></span>

### <a name="depth-buffer-format"></a><span data-ttu-id="4570d-125">깊이 버퍼 형식</span><span class="sxs-lookup"><span data-stu-id="4570d-125">Depth buffer format</span></span>

<span data-ttu-id="4570d-126">또한 *AR 헤드셋* 의 경우 24 비트와 비교 하 여 깊이 버퍼를 공유할 수 있도록 설정 하는 경우 16 비트 깊이 형식을 활용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-126">Furthermore, for *AR Headsets*, it is recommended to utilize a 16-bit depth format when enabling depth buffer sharing compared to 24-bit.</span></span> <span data-ttu-id="4570d-127">이는 더 낮은 정밀도를 의미 하지만 성능에는 절약 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-127">This means lower precision but saves on performance.</span></span> <span data-ttu-id="4570d-128">픽셀에 대 한 깊이를 계산 하는 데 더 낮은 정밀도가 있기 때문에 [z](https://en.wikipedia.org/wiki/Z-fighting) 이동이 발생 하는 경우에는 [먼 클립 평면](https://docs.unity3d.com/Manual/class-Camera.html) 을 카메라에 가깝게 이동 하는 것이 좋습니다 (예: 1000m 대신 5천만 개).</span><span class="sxs-lookup"><span data-stu-id="4570d-128">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs because there is less precision in calculating depth for pixels, then it is recommended to move the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) closer to the camera (ex: 50m instead of 1000m).</span></span>

> [!NOTE]
> <span data-ttu-id="4570d-129">*16 비트 깊이 형식을* 사용 하는 경우 Unity에서이 설정에 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 스텐실 버퍼 필요 효과가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-129">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="4570d-130">이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 해당 하는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html)생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-130">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="4570d-131">스텐실 버퍼가 필요한 [마스크 구성 요소](https://docs.unity3d.com/Manual/script-Mask.html) 를 사용 하는 경우 스텐실 버퍼를 요구 하지 않으므로 *16 비트 깊이 형식과* 함께 사용할 수 있는 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) 를 대신 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-131">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

### <a name="real-time-global-illumination"></a><span data-ttu-id="4570d-132">실시간 글로벌 조명</span><span class="sxs-lookup"><span data-stu-id="4570d-132">Real-time Global Illumination</span></span>

<span data-ttu-id="4570d-133">Unity의 [실시간 글로벌 조명이](https://docs.unity3d.com/Manual/GIIntro.html) 뛰어난 미적 결과를 제공할 수 있지만 매우 많은 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-133">[Real-time Global illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide fantastic aesthetic results but at a very high cost.</span></span> <span data-ttu-id="4570d-134">글로벌 조명 조명은 혼합 현실에서 매우 많은 비용이 들기 때문에 개발에서이 기능을 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-134">Global illumination lighting is very expensive in mixed reality and thus it is recommended to disable this feature in development.</span></span>

> [!NOTE]
> <span data-ttu-id="4570d-135">Unity의 전역 조명 설정은 전체 프로젝트에서 한 번도 설정 되지 않고 장면 별로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-135">Global illumination settings in Unity are set per-scene and not once across the entire project.</span></span>

## <a name="scene-analysis"></a><span data-ttu-id="4570d-136">장면 분석</span><span class="sxs-lookup"><span data-stu-id="4570d-136">Scene analysis</span></span>

<span data-ttu-id="4570d-137">*장면 분석* 탭은 현재 장면에 있는 어떤 요소가 성능에 가장 많은 영향을 줄 가능성이 있음을 개발자에 게 알리기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-137">The *Scene Analysis* tab is designed to inform developers on which elements currently in the scene will likely have the most impact on performance.</span></span>

![MRTK 창 설정 장면 분석 최적화](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a><span data-ttu-id="4570d-139">조명 분석</span><span class="sxs-lookup"><span data-stu-id="4570d-139">Lighting analysis</span></span>

<span data-ttu-id="4570d-140">이 섹션에서는 그림자를 사용 하지 않도록 설정 해야 하는 조명 뿐만 아니라 장면의 현재 조명 수를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-140">This section will examine the number of lights currently in the scene, as well as any lights that should disable shadows.</span></span> <span data-ttu-id="4570d-141">섀도 캐스팅은 비용이 많이 드는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-141">Shadow casting is a very expensive operation.</span></span>

### <a name="polygon-count-analysis"></a><span data-ttu-id="4570d-142">다각형 개수 분석</span><span class="sxs-lookup"><span data-stu-id="4570d-142">Polygon count analysis</span></span>

<span data-ttu-id="4570d-143">이 도구는 다각형 개수 통계도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-143">The tool also provides polygon count statistics.</span></span> <span data-ttu-id="4570d-144">지정 된 장면에서 가장 높은 polygon 복잡성이 최적화를 대상으로 지정할 Gameobject을 신속 하 게 식별 하는 데 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-144">It can be very helpful to quickly identify which GameObjects have the highest polygon complexity in a given scene to target for optimizations.</span></span>

### <a name="unity-ui-raycast-analysis"></a><span data-ttu-id="4570d-145">Unity UI raycast 분석</span><span class="sxs-lookup"><span data-stu-id="4570d-145">Unity UI raycast analysis</span></span>

<span data-ttu-id="4570d-146">그래픽 raycast 연산은 MRTK의 포인터 당 수행 되어 Unity UI 요소가 포커스에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-146">Graphics raycast operations are performed per pointer in MRTK to determine if any Unity UI elements are in focus.</span></span> <span data-ttu-id="4570d-147">이러한 raycasts는 상당한 비용이 소요 될 수 있으며 성능을 향상 하는 데 도움이 될 수 있습니다. 결과에서 반환 하지 않아도 되는 UI 요소는 raycasts 대상으로 사용 하지 않도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-147">These raycasts can be quite expensive and to help improve performance, UI elements that do not need to be returned in the results should be disabled as raycast targets.</span></span> <span data-ttu-id="4570d-148">모든 [그래픽](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 요소에는 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-148">Every [Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) element has a [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) property.</span></span> <span data-ttu-id="4570d-149">이 도구는이 속성이 설정 된 텍스트 UI 요소를 검색 하므로 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-149">This tool will search for text UI elements that have this property enabled and thus are likely candidates to be disabled.</span></span>

## <a name="shader-analysis"></a><span data-ttu-id="4570d-150">셰이더 분석</span><span class="sxs-lookup"><span data-stu-id="4570d-150">Shader analysis</span></span>

<span data-ttu-id="4570d-151">[Unity 표준 셰이더](https://docs.unity3d.com/Manual/shader-StandardShader.html) 는 게임에 대해 매우 높은 품질의 시각적 결과를 생성할 수 있지만 일반적으로 혼합 현실 응용 프로그램의 성능 요구 사항에 가장 적합 한 것은 아닙니다. 이러한 응용 프로그램은 일반적으로 GPU 경계에 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-151">The [Unity Standard shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) can produce very high quality visual results for games but is not generally best suited for the performance needs of mixed reality applications, especially since such applications are generally GPU bounded.</span></span> <span data-ttu-id="4570d-152">따라서 개발자는 [Mrtk 표준 셰이더](../rendering/mrtk-standard-shader.md) 를 활용 하 여 미관 & 그래픽 기능과 성능의 균형을 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-152">Thus, it is recommended to developers to utilize the [MRTK Standard shader](../rendering/mrtk-standard-shader.md) to balance aesthetics & graphical features with performance.</span></span>

<span data-ttu-id="4570d-153">*셰이더 분석* 탭은 Unity 표준 셰이더를 사용 하는 자료에 대 한 현재 프로젝트의 자산 폴더를 검색 하거나, 원하는 경우 혼합 된 현실을 사용 하지 않는 모든 자료에서 셰이더를 제공 Toolkit 합니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-153">The *Shader Analysis* tab scans the current project's Asset folder for materials using the Unity Standard shader or if desired, all materials not using Mixed Reality Toolkit provided shaders.</span></span> <span data-ttu-id="4570d-154">개발자는 검색 되 면 모든 자료를 변환 하거나 적절 한 단추를 사용 하 여 개별적으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4570d-154">Once discovered, developers can convert all materials or convert individually using the appropriate buttons.</span></span>

![MRTK 창 설정 셰이더 분석 최적화](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a><span data-ttu-id="4570d-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4570d-156">See also</span></span>

- [<span data-ttu-id="4570d-157">성능</span><span class="sxs-lookup"><span data-stu-id="4570d-157">Performance</span></span>](../../performance/perf-getting-started.md)
- [<span data-ttu-id="4570d-158">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="4570d-158">Hologram Stabilization</span></span>](../../performance/hologram-stabilization.md)
