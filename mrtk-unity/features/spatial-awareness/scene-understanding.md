---
title: 장면 이해
description: MRTK의 Scene Understanding에 대해 설명합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143880"
---
# <a name="scene-understanding"></a><span data-ttu-id="420e5-104">장면 이해</span><span class="sxs-lookup"><span data-stu-id="420e5-104">Scene Understanding</span></span>

<span data-ttu-id="420e5-105">[Scene Understanding은](/windows/mixed-reality/scene-understanding) 장면 엔터티의 의미 체계 표현과 __HoloLens 2__ 기하학적 형식을 반환합니다(HoloLens 1세대는 지원되지 않음).</span><span class="sxs-lookup"><span data-stu-id="420e5-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="420e5-106">이 기술의 몇 가지 예상 사용 사례는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="420e5-107">특정 종류의 가장 가까운 표면(예: 벽 및 바닥)에 개체를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="420e5-108">플랫폼 스타일 게임을 위한 탐색 메시 생성</span><span class="sxs-lookup"><span data-stu-id="420e5-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="420e5-109">물리학 엔진에 친숙한 기하 도형을 쿼드로 제공</span><span class="sxs-lookup"><span data-stu-id="420e5-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="420e5-110">유사한 알고리즘을 작성할 필요가 없도록 하여 개발 가속화</span><span class="sxs-lookup"><span data-stu-id="420e5-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="420e5-111">Scene Understanding은 MRTK 2.6부터 __실험적__ 기능으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="420e5-112">MRTK는 라는 [공간 관찰자로](spatial-awareness-getting-started.md#register-observers) 통합됩니다. [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver)</span><span class="sxs-lookup"><span data-stu-id="420e5-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="420e5-113">Scene Understanding은 레거시 XR 파이프라인 및 XR SDK 파이프라인에서 모두 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="420e5-114">두 경우 모두 가 `WindowsSceneUnderstandingObserver` 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="420e5-115">관찰자 개요</span><span class="sxs-lookup"><span data-stu-id="420e5-115">Observer overview</span></span>

<span data-ttu-id="420e5-116">요청되면 는 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 애플리케이션이 주변을 이해하는 데 유용한 특성과 함께 [SpatialAwarenessSceneObject를](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="420e5-117">관찰 빈도, 반환된 개체 유형(예: 벽, 층) 및 기타 관찰자 동작은 프로필을 통한 관찰자 구성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="420e5-118">예를 들어 폐색 마스크를 원하는 경우 관찰자는 4분면을 생성하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="420e5-119">관찰된 장면을 나중에 로드하여 편집기 재생 모드에서 장면을 다시 만들 수 있는 직렬화된 파일로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="420e5-120">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="420e5-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="420e5-121">Scene Understanding은 HoloLens 2 및 Unity 2019.4 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="420e5-122">빌드 설정에서 플랫폼이 UWP로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="420e5-123">[혼합 현실 기능 도구](https://aka.ms/MRFeatureTool)를 통해 장면 이해 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="420e5-124">장면 이해 사용</span><span class="sxs-lookup"><span data-stu-id="420e5-124">Using Scene Understanding</span></span>

<span data-ttu-id="420e5-125">장면 이해를 시작 하는 가장 빠른 방법은 샘플 장면을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="420e5-126">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="420e5-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="420e5-127">Unity에서 프로젝트 탐색기를 사용 하 여에서 장면 파일을 열고 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` play를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="420e5-128">Mixed Reality 기능 도구를 사용 하거나 UPM를 통해 다른 방법으로 가져오는 경우 종속성 문제로 인해 실험적-SceneUnderstanding 샘플을 가져오기 전에 SpatialAwareness 샘플을 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="420e5-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="420e5-129">자세한 내용은 [이 GitHub 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="420e5-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="420e5-130">장면에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="420e5-131">관찰자를 구성 하기 위한 응용 프로그램 UI에서 관찰 된 장면 개체의 시각화</span><span class="sxs-lookup"><span data-stu-id="420e5-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="420e5-132">`DemoSceneUnderstandingController`관찰자 설정을 변경 하 고 관련 이벤트를 수신 하는 방법을 보여 주는 예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="420e5-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="420e5-133">오프 라인 개발을 위해 장치에 장면 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="420e5-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="420e5-134">편집기에서 개발 워크플로를 지원 하기 위해 이전에 저장 된 장면 데이터 (바이트 파일) 로드</span><span class="sxs-lookup"><span data-stu-id="420e5-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="420e5-135">샘플 장면은 레거시 XR 파이프라인을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="420e5-136">XR SDK 파이프라인을 사용 하는 경우 프로필을 적절 하 게 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="420e5-137">제공 된 장면 공간 인식 시스템 프로필 ( `DemoSceneUnderstandingSystemProfile` ) 및 장면 이해 관찰자 프로필 ( `DefaultSceneUnderstandingObserverProfile` 및)은 `DemoSceneUnderstandingObserverProfile` 두 파이프라인 모두에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="420e5-138">관찰자 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="420e5-138">Configuring the observer service</span></span>

<span data-ttu-id="420e5-139">' MixedRealityToolkit ' 게임 개체를 선택 하 고 검사기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![계층 구조에서 위치를 이해 하는 장면](../images/spatial-awareness/MRTKHierarchy.png)

![검사기의 MRTK 위치](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="420e5-142">이러한 옵션을 사용하면 를 구성할 수 `WindowsSceneUnderstandingObserver` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="420e5-143">예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="420e5-143">Example script</span></span>

<span data-ttu-id="420e5-144">_DemoSceneUnderstandingController.cs_ 예제 스크립트는 Scene Understanding 서비스 작업의 주요 개념을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="420e5-145">Scene Understanding 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="420e5-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="420e5-146">Scene Understanding 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="420e5-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="420e5-147">`WindowsSceneUnderstandingObserver`런타임에 구성</span><span class="sxs-lookup"><span data-stu-id="420e5-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="420e5-148">장면의 패널에서 토글은 이 샘플 스크립트의 공용 함수를 호출하여 장면 이해 관찰자의 동작을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="420e5-149">*Prefabs 인스턴스화* 를 설정하면 부모 개체 아래에 깔끔하게 수집된 모든 [SpatialAwarenessSceneObject에](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)맞게 크기가 인 개체를 만드는 방법을 보여 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![데모 컨트롤러 옵션](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="420e5-151">빌드된 앱 정보</span><span class="sxs-lookup"><span data-stu-id="420e5-151">Built app notes</span></span>

<span data-ttu-id="420e5-152">표준 방식으로 HoloLens를 빌드하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="420e5-153">실행되면 기능을 사용할 수 있는 단추가 여러 개 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="420e5-154">관찰자에게 쿼리를 만드는 데는 몇 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="420e5-155">페치 요청을 잘못 구성하면 이벤트 페이로드에 예상 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="420e5-156">예를 들어 쿼드를 요청하지 않으면 폐색 마스크 질감이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="420e5-157">마찬가지로 관찰자가 메시를 요청하도록 구성되지 않은 경우 세계 메시는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="420e5-158">`DemoSceneUnderstandingController`스크립트는 이러한 일부 의존성만 처리하지만 전부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="420e5-159">저장된 장면 파일은 에서 [디바이스 포털을](/windows/mixed-reality/using-the-windows-device-portal) 통해 액세스할 수 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="420e5-160">이러한 장면 파일은 검사기에서 찾은 관찰자 프로필에 지정하여 편집기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420e5-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![바이트 파일의 위치 장치 포털](../images/spatial-awareness/BytesInDevicePortal.png)

![관찰자의 직렬화된 장면 바이트](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="420e5-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="420e5-163">See Also</span></span>

* [<span data-ttu-id="420e5-164">공간 매핑 개요 WMR</span><span class="sxs-lookup"><span data-stu-id="420e5-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="420e5-165">공간 매핑 개요 WMR</span><span class="sxs-lookup"><span data-stu-id="420e5-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)