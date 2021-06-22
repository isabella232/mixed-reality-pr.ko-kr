---
title: 장면 이해
description: MRTK의 장면 이해에 대해 설명 합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 장면 이해
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449752"
---
# <a name="scene-understanding"></a><span data-ttu-id="246a0-104">장면 이해</span><span class="sxs-lookup"><span data-stu-id="246a0-104">Scene Understanding</span></span>

<span data-ttu-id="246a0-105">[장면 이해](/windows/mixed-reality/scene-understanding) 는 장면 엔터티에 대 한 의미 체계 및 __hololens 2__ 의 기하학적 형태 (hololens 1 Gen은 지원 되지 않음)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="246a0-106">이 기술의 몇 가지 예상 사용 사례는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="246a0-107">특정 종류의 가장 가까운 표면 (예: 벽 및 층)에 개체를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="246a0-108">구성 탐색-플랫폼 스타일 게임의 메시</span><span class="sxs-lookup"><span data-stu-id="246a0-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="246a0-109">Quads로 물리학 엔진 친화적인 기 하 도형을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="246a0-110">비슷한 알고리즘을 작성할 필요가 없도록 하 여 개발 가속화</span><span class="sxs-lookup"><span data-stu-id="246a0-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="246a0-111">장면 이해는 MRTK 2.6에서 __실험적__ 기능으로 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="246a0-112">이라는 [공간 관찰자](spatial-awareness-getting-started.md#register-observers) 로 MRTK에 통합 됩니다 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="246a0-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="246a0-113">장면 이해는 레거시 XR 파이프라인과 XR SDK 파이프라인 (OpenXR (MRTK 2.7에서 시작) 및 Windows XR Plugin) 모두에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="246a0-114">두 경우 모두 `WindowsSceneUnderstandingObserver` 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="246a0-115">원격에서 장면 이해를 사용 하는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="246a0-116">관찰자 개요</span><span class="sxs-lookup"><span data-stu-id="246a0-116">Observer overview</span></span>

<span data-ttu-id="246a0-117">메시지가 표시 되 면는 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 응용 프로그램에서 주변을 이해 하는 데 유용한 특성과 함께 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="246a0-118">관찰 빈도, 반환 된 개체 형식 (예: 벽, 층) 및 기타 관찰자 동작은 프로필을 통한 관찰자의 구성에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="246a0-119">예를 들어 폐색 mask가 필요한 경우 관찰자는 quads를 생성 하도록 구성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="246a0-120">관찰 된 장면을 나중에 로드 하 여 편집기 재생 모드에서 장면을 다시 만들 수 있도록 serialize 된 파일로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="246a0-121">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="246a0-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="246a0-122">장면 이해는 HoloLens 2 및 Unity 2019.4 이상 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="246a0-123">빌드 설정에서 플랫폼이 UWP로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="246a0-124">[혼합 현실 기능 도구](https://aka.ms/MRFeatureTool)를 통해 장면 이해 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="246a0-125">장면 이해 사용</span><span class="sxs-lookup"><span data-stu-id="246a0-125">Using Scene Understanding</span></span>

<span data-ttu-id="246a0-126">장면 이해를 시작 하는 가장 빠른 방법은 샘플 장면을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="246a0-127">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="246a0-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="246a0-128">Unity에서 프로젝트 탐색기를 사용 하 여에서 장면 파일을 열고 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` play를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="246a0-129">MRTK 2.6.0에만 적용 됩니다. 혼합 현실 기능 도구를 사용 하거나, 다른 방법으로는 UPM를 통해 가져오는 경우 종속성 문제로 인해 실험적-SceneUnderstanding 샘플을 가져오기 전에 SpatialAwareness 샘플을 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="246a0-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="246a0-130">자세한 내용은 [이 GitHub 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="246a0-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="246a0-131">장면에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="246a0-132">관찰자를 구성 하기 위한 응용 프로그램 UI에서 관찰 된 장면 개체의 시각화</span><span class="sxs-lookup"><span data-stu-id="246a0-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="246a0-133">`DemoSceneUnderstandingController`관찰자 설정을 변경 하 고 관련 이벤트를 수신 하는 방법을 보여 주는 예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="246a0-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="246a0-134">오프 라인 개발을 위해 장치에 장면 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="246a0-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="246a0-135">편집기에서 개발 워크플로를 지원 하기 위해 이전에 저장 된 장면 데이터 (바이트 파일) 로드</span><span class="sxs-lookup"><span data-stu-id="246a0-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="246a0-136">기본적으로 `ShouldLoadFromFile` 관찰자의 속성은 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="246a0-137">직렬화 된 샘플 대화방의 시각화를 보려면 아래의 [관찰자 서비스 구성](#configuring-the-observer-service) 섹션을 참조 하 고 편집기에서 속성을 true로 설정 하세요.</span><span class="sxs-lookup"><span data-stu-id="246a0-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="246a0-138">샘플 장면은 레거시 XR 파이프라인을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="246a0-139">XR SDK 파이프라인을 사용 하는 경우 프로필을 적절 하 게 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="246a0-140">제공 된 장면 공간 인식 시스템 프로필 ( `DemoSceneUnderstandingSystemProfile` ) 및 장면 이해 관찰자 프로필 ( `DefaultSceneUnderstandingObserverProfile` 및)은 `DemoSceneUnderstandingObserverProfile` 두 파이프라인 모두에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="246a0-141">샘플 장면에서는 `There is no active AsyncCoroutineRunner when an action is posted.` 초기화/스레드 실행 순서로 인해 특정 상황에서 경고를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="246a0-142">`AsyncCoroutineRunner`구성 요소가 "Demo Controller" GameObject에 연결 되어 있는지 확인 하 고 구성 요소/GameObject가 장면 (기본 경우)에서 사용 하도록 설정 된 상태를 유지 하도록 할 수 있는 경우 경고를 안전 하 게 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="246a0-143">**그러나 장면 이해를 사용 하 여 새 장면을 만들 때 루트에 빈 GameObject를 만들어 `AsyncCoroutineRunner` 스크립트를 연결 해야 합니다. 그렇지 않으면 장면 이해가 제대로 작동 하지 않을 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="246a0-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="246a0-144">관찰자 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="246a0-144">Configuring the observer service</span></span>

<span data-ttu-id="246a0-145">' MixedRealityToolkit ' 게임 개체를 선택 하 고 검사기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![계층 구조에서 위치를 이해 하는 장면](../images/spatial-awareness/MRTKHierarchy.png)

![검사기의 MRTK 위치](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="246a0-148">이러한 옵션은를 구성 하는 데 사용할 수 `WindowsSceneUnderstandingObserver` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="246a0-149">예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="246a0-149">Example script</span></span>

<span data-ttu-id="246a0-150">예제 스크립트 _DemoSceneUnderstandingController_ 는 장면 이해 서비스를 사용 하는 주요 개념을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="246a0-151">장면 이해 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="246a0-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="246a0-152">장면 이해 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="246a0-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="246a0-153">`WindowsSceneUnderstandingObserver`런타임에 구성</span><span class="sxs-lookup"><span data-stu-id="246a0-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="246a0-154">장면의 패널에 대 한 토글은이 샘플 스크립트의 public 함수를 호출 하 여 관찰자를 이해 하는 장면의 동작을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="246a0-155">*인스턴스화 Prefabs* 을 켜면 부모 개체 아래에서 깔끔하게 수집 된 모든 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)에 맞게 크기를 조정 하는 개체를 만드는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![데모 컨트롤러 옵션](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="246a0-157">빌드된 앱 메모</span><span class="sxs-lookup"><span data-stu-id="246a0-157">Built app notes</span></span>

<span data-ttu-id="246a0-158">표준 방식으로 HoloLens에 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="246a0-159">실행 한 후에는 기능을 사용 하 여 많은 단추가 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="246a0-160">관찰자에 게 쿼리를 만드는 일부 pit가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="246a0-161">인출 요청이 잘못 구성 되 면 이벤트 페이로드가 필요한 데이터를 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="246a0-162">예를 들어 quads를 요청 하지 않는 경우 폐색 mask 질감이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="246a0-163">예를 들어 관찰자가 메시를 요청 하도록 구성 되지 않은 경우에는 세계 메쉬가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="246a0-164">`DemoSceneUnderstandingController`스크립트는 이러한 종속성 중 일부를 처리 하지만 모두는 처리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="246a0-165">저장 된 장면 파일은에서 [장치 포털](/windows/mixed-reality/using-the-windows-device-portal) 을 통해 액세스할 수 있습니다 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="246a0-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="246a0-166">이러한 장면 파일은 검사기에서 찾은 관찰자 프로필에 지정 하 여 편집기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="246a0-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![바이트 파일의 장치 포털 위치](../images/spatial-awareness/BytesInDevicePortal.png)

![관찰자의 serialize 된 장면 바이트](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="246a0-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="246a0-169">See Also</span></span>

* [<span data-ttu-id="246a0-170">장면 이해 개요</span><span class="sxs-lookup"><span data-stu-id="246a0-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="246a0-171">장면 이해 SDK 개요</span><span class="sxs-lookup"><span data-stu-id="246a0-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)