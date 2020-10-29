---
title: OpenXR 모범 사례
description: OpenXR 응용 프로그램의 시각적 품질, 안정성 및 성능에 대 한 모범 사례를 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 모범 사례, 성능, 품질, 안정성
ms.openlocfilehash: dad4622e4186ecc8b090e2abe2e33d3d39ac7525
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683881"
---
# <a name="openxr-app-best-practices"></a><span data-ttu-id="6477f-104">OpenXR 앱 모범 사례</span><span class="sxs-lookup"><span data-stu-id="6477f-104">OpenXR app best practices</span></span>

<span data-ttu-id="6477f-105">아래 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>의 OpenXRProgram .cpp 파일에서 모범 사례에 대 한 예제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-105">You can see an example of the best practices below in <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>'s OpenXRProgram.cpp file.</span></span> <span data-ttu-id="6477f-106">시작 부분에 있는 Run () 함수는 일반적인 OpenXR 앱 코드 흐름을 초기화에서 이벤트 및 렌더링 루프로 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-106">The Run() function at the beginning captures a typical OpenXR app code flow from initialization to the event and rendering loop.</span></span>

## <a name="best-practices-for-visual-quality-and-stability"></a><span data-ttu-id="6477f-107">시각적 품질 및 안정성에 대 한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="6477f-107">Best practices for visual quality and stability</span></span>

<span data-ttu-id="6477f-108">이 섹션의 모범 사례에서는 모든 OpenXR 응용 프로그램에서 최상의 시각적 품질 및 안정성을 얻는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-108">The best practices in this section describe how to get the best visual quality and stability in any OpenXR application.</span></span>

<span data-ttu-id="6477f-109">HoloLens 2와 관련 된 추가 성능 권장 사항은 아래의 [hololens의 성능에 대 한 모범 사례 2](#best-practices-for-performance-on-hololens-2) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6477f-109">For further performance recommendations specific to HoloLens 2, see the [Best practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) section below.</span></span>

### <a name="gamma-correct-rendering"></a><span data-ttu-id="6477f-110">감마-올바른 렌더링</span><span class="sxs-lookup"><span data-stu-id="6477f-110">Gamma-correct rendering</span></span>

<span data-ttu-id="6477f-111">렌더링 파이프라인이 감마를 정확 하 게 유지 하도록 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-111">Care must be taken to ensure that your rendering pipeline is gamma-correct.</span></span> <span data-ttu-id="6477f-112">이 swapchain present 렌더링할 때 렌더링 대상 뷰 형식은이 swapchain present 형식과 일치 해야 합니다 (예: `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 이 swapchain present 형식 및 렌더링 대상 뷰의 경우).</span><span class="sxs-lookup"><span data-stu-id="6477f-112">When rendering to a swapchain, the render-target view format should match the swapchain format (e.g. `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` for both the swapchain format and the render-target view).</span></span>
<span data-ttu-id="6477f-113">응용 프로그램의 렌더링 파이프라인이 셰이더 코드에서 수동 sRGB 변환을 수행 하는 경우는 예외입니다 .이 경우 응용 프로그램은 sRGB이 swapchain present 형식을 요청 하지만 렌더링 대상 보기의 선형 형식 (예: `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 이 swapchain present 형식으로 사용 하지만 `DXGI_FORMAT_B8G8R8A8_UNORM` 렌더링 대상 뷰로 사용)을 사용 하 여 콘텐츠를 이중 감마로 수정 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-113">The exception is if the app's rendering pipeline does a manual sRGB conversion in shader code, in which case the app should request an sRGB swapchain format but use the linear format for the render-target view (e.g. request `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` as the swapchain format but use `DXGI_FORMAT_B8G8R8A8_UNORM` as the render-target view) to prevent content from being double-gamma corrected.</span></span>

### <a name="submit-depth-buffer-for-projection-layers"></a><span data-ttu-id="6477f-114">프로젝션 계층에 대 한 깊이 버퍼를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-114">Submit depth buffer for projection layers</span></span>

<span data-ttu-id="6477f-115">항상 확장을 사용 하 `XR_KHR_composition_layer_depth` 고에 프레임을 제출할 때 프로젝션 계층과 함께 깊이 버퍼를 제출 `xrEndFrame` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-115">Always use `XR_KHR_composition_layer_depth` extension and submit the depth buffer together with the projection layer when submitting a frame to `xrEndFrame`.</span></span>
<span data-ttu-id="6477f-116">이렇게 하면 HoloLens 2에서 하드웨어 깊이 다시 프로젝션을 사용 하 여 홀로그램의 안정성을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-116">This improves hologram stability by enabling hardware depth reprojection on HoloLens 2.</span></span>

### <a name="choose-a-reasonable-depth-range"></a><span data-ttu-id="6477f-117">적절 한 깊이 범위 선택</span><span class="sxs-lookup"><span data-stu-id="6477f-117">Choose a reasonable depth range</span></span>

<span data-ttu-id="6477f-118">더 좁은 깊이 범위를 사용 하 여 HoloLens의 홀로그램 안정성을 위해 가상 콘텐츠의 범위를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-118">Prefer a narrower depth range to scope the virtual content to help hologram stability on HoloLens.</span></span>
<span data-ttu-id="6477f-119">예를 들어 OpenXrProgram .cpp 샘플은 0.1 ~ 20 미터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-119">For example, the OpenXrProgram.cpp sample is using 0.1 to 20 meters.</span></span>
<span data-ttu-id="6477f-120">보다 균일 한 깊이 해상도를 위해 [역방향-Z](https://developer.nvidia.com/content/depth-precision-visualized) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-120">Use [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) for a more uniform depth resolution.</span></span>
<span data-ttu-id="6477f-121">HoloLens 2에서 기본 깊이 형식을 사용 하면 향상 된 `DXGI_FORMAT_D16_UNORM` 프레임 속도와 성능을 얻을 수 있습니다. 하지만 16 비트 깊이 버퍼는 24 비트 깊이 버퍼 보다 깊이 있는 해상도를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-121">Note that, on HoloLens 2, using the preferred `DXGI_FORMAT_D16_UNORM` depth format will help achieve better frame rate and performance, although 16-bit depth buffers provide less depth resolution than 24-bit depth buffers.</span></span>
<span data-ttu-id="6477f-122">따라서 깊이 해상도를 가장 잘 활용 하기 위해 이러한 모범 사례를 따르는 것이 더 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-122">Therefore, following these best practices to make best use of the depth resolution becomes more important.</span></span>

### <a name="prepare-for-different-environment-blend-modes"></a><span data-ttu-id="6477f-123">다른 환경 blend 모드 준비</span><span class="sxs-lookup"><span data-stu-id="6477f-123">Prepare for different environment blend modes</span></span>

<span data-ttu-id="6477f-124">응용 프로그램이 전 세계에 완전히 차단 되는 몰입 형 헤드셋에서 실행 되는 경우에는 API를 사용 하 여 지원 되는 환경 blend 모드를 열거 하 `xrEnumerateEnvironmentBlendModes` 고 렌더링 콘텐츠를 적절 하 게 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-124">If your application will also run on immersive headsets that completely block out the world, be sure to enumerate supported environment blend modes using `xrEnumerateEnvironmentBlendModes` API, and prepare your rendering content accordingly.</span></span>
<span data-ttu-id="6477f-125">예를 들어 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` HoloLens와 같은 시스템의 경우 앱은 투명 한 색으로 투명 한 색으로 사용 해야 하지만, 시스템의 경우 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` 앱은 일부 불투명 색 또는 일부 가상 공간을 백그라운드에서 렌더링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-125">For example, for a system with `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` such as the HoloLens, the app should use transparent as the clear color, while for a system with `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, the app should render some opaque color or some virtual room in the background.</span></span>

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a><span data-ttu-id="6477f-126">응용 프로그램의 루트 공간으로 바인딩되지 않은 참조 공간을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-126">Choose unbounded reference space as application's root space</span></span>

<span data-ttu-id="6477f-127">응용 프로그램은 일반적으로 뷰, 작업 및 holograms를 연결 하는 데 루트 세계 좌표 공간을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-127">Applications typically establish some root world coordinate space to connect views, actions and holograms together.</span></span>
<span data-ttu-id="6477f-128">`XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`확장이 지원 되는 경우를 사용 하 여 [전 세계 규모의 좌표계](../../design/coordinate-systems.md#building-a-world-scale-experience)를 설정 하면 사용자가 앱이 시작 되는 위치에서 멀리 (예: 5 미터) 이동할 때 앱에서 원치 않는 홀로그램 드리프트를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-128">Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` when the extension is supported to establish a [world-scale coordinate system](../../design/coordinate-systems.md#building-a-world-scale-experience), enabling your app to avoid undesired hologram drift when the user moves far (e.g. 5 meters away) from where the app starts.</span></span>
<span data-ttu-id="6477f-129">`XR_REFERENCE_SPACE_TYPE_LOCAL`제한 없는 공간 확장을 사용 하지 않는 경우 대체 (fallback)로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-129">Use `XR_REFERENCE_SPACE_TYPE_LOCAL` as a fallback if the unbounded space extension doesn't exist.</span></span>

### <a name="associate-hologram-with-spatial-anchor"></a><span data-ttu-id="6477f-130">홀로그램을 공간 앵커와 연결</span><span class="sxs-lookup"><span data-stu-id="6477f-130">Associate hologram with spatial anchor</span></span>

<span data-ttu-id="6477f-131">바인딩되지 않은 참조 공간을 사용 하는 경우 사용자가 holograms 하 게 되 면 해당 참조 공간이 [달라질 수](../../design/coordinate-systems.md#building-a-world-scale-experience)있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-131">When using an unbounded reference space, holograms you place directly in that reference space [may drift as the user walks to distant rooms and then comes back](../../design/coordinate-systems.md#building-a-world-scale-experience).</span></span>
<span data-ttu-id="6477f-132">홀로그램 사용자가 전 세계의 불연속 위치에 배치 하는 경우 확장 함수를 사용 하 여 [공간 앵커를 만들고](../../design/spatial-anchors.md#best-practices) `xrCreateSpatialAnchorSpaceMSFT` 홀로그램을 원점에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-132">For hologram users place at a discrete location in the world, [create a spatial anchor](../../design/spatial-anchors.md#best-practices) using the `xrCreateSpatialAnchorSpaceMSFT` extension function and position the hologram at its origin.</span></span>
<span data-ttu-id="6477f-133">그러면 홀로그램은 시간이 지남에 따라 독립적으로 안정적으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-133">That will keep that hologram independently stable over time.</span></span>

### <a name="support-mixed-reality-capture"></a><span data-ttu-id="6477f-134">혼합 현실 캡처 지원</span><span class="sxs-lookup"><span data-stu-id="6477f-134">Support mixed reality capture</span></span>

<span data-ttu-id="6477f-135">HoloLens 2의 기본 디스플레이는 추가 환경 혼합을 사용 하지만, 사용자가 [혼합 된 현실 캡처](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)를 시작 하면 앱의 렌더링 콘텐츠가 환경 비디오 스트림과 알파 혼합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-135">Although HoloLens 2's primary display uses additive environment blending, when the user initiates [mixed reality capture](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md), the app's rendering content will be alpha-blended with the environment video stream.</span></span>
<span data-ttu-id="6477f-136">혼합 현실에서 최상의 시각적 품질을 얻으려면 비디오를 캡처하는 것이 좋습니다 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` `layerFlags` .</span><span class="sxs-lookup"><span data-stu-id="6477f-136">To achieve the best visual quality in mixed reality capture videos, it's best to set the `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` in your projection layer's `layerFlags`.</span></span>

## <a name="best-practices-for-performance-on-hololens-2"></a><span data-ttu-id="6477f-137">HoloLens의 성능에 대 한 모범 사례 2</span><span class="sxs-lookup"><span data-stu-id="6477f-137">Best practices for performance on HoloLens 2</span></span>

<span data-ttu-id="6477f-138">하드웨어 재 프로젝션 지원을 포함 하는 모바일 장치인 HoloLens 2에는 최적의 성능을 얻기 위한 보다 엄격한 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-138">As a mobile device with hardware reprojection support, HoloLens 2 has stricter requirements to obtain optimal performance.</span></span>  <span data-ttu-id="6477f-139">이를 통해 컴퍼지션 데이터를 제출 하면 `xrEndFrame` 사후 처리가 발생 하 여 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-139">There are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>

### <a name="select-a-swapchain-format"></a><span data-ttu-id="6477f-140">이 swapchain present 형식 선택</span><span class="sxs-lookup"><span data-stu-id="6477f-140">Select a swapchain format</span></span>

<span data-ttu-id="6477f-141">는 항상를 사용 하 여 지원 되는 픽셀 형식을 열거 하 `xrEnumerateSwapchainFormats` 고 앱이 지 원하는 런타임의 첫 번째 색 및 깊이 픽셀 형식을 선택 합니다 .이는 런타임이 최적의 성능을 위해 선호 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-141">Always enumerate supported pixel formats using `xrEnumerateSwapchainFormats`, and choose the first color and depth pixel format from the runtime that the app supports, because that's what the runtime prefers for optimal performance.</span></span> <span data-ttu-id="6477f-142">HoloLens 2에서 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 및 `DXGI_FORMAT_D16_UNORM` 는 일반적으로 렌더링 성능을 향상 시키기 위한 첫 번째 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-142">Note, on HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` and `DXGI_FORMAT_D16_UNORM` is typically the first choice to achieve better rendering performance.</span></span> <span data-ttu-id="6477f-143">이 기본 설정은 데스크톱 PC에서 실행 되는 VR 헤드셋에서 다를 수 있습니다. 여기서 24 비트 깊이 버퍼는 성능에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-143">This preference can be different on VR headsets running on a Desktop PC, where 24-bit depth buffers have less of a performance impact.</span></span>
  
<span data-ttu-id="6477f-144">**성능 경고:** 기본이 swapchain present 색 형식이 아닌 형식을 사용 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-144">**Performance Warning:** Using a format other than the primary swapchain color format will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a><span data-ttu-id="6477f-145">권장 되는 렌더링 매개 변수 및 프레임 타이밍으로 렌더링</span><span class="sxs-lookup"><span data-stu-id="6477f-145">Render with recommended rendering parameters and frame timing</span></span>

<span data-ttu-id="6477f-146">항상 권장 된 보기 구성 너비/높이를 사용 하 여 렌더링 하 `recommendedImageRectWidth` `recommendedImageRectHeight` `XrViewConfigurationView` 고, 항상 `xrLocateViews` API를 사용 하 여 권장 되는 보기 포즈, fov 및 렌더링 전에 다른 렌더링 매개 변수를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-146">Always render with the recommended view configuration width/height (`recommendedImageRectWidth` and `recommendedImageRectHeight` from `XrViewConfigurationView`), and always use `xrLocateViews` API to query for the recommended view pose, fov, and other rendering parameters before rendering.</span></span>
<span data-ttu-id="6477f-147">항상 `XrFrameEndInfo.predictedDisplayTime` `xrWaitFrame` 포즈 및 뷰를 쿼리할 때 최신 호출에서를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-147">Always use the `XrFrameEndInfo.predictedDisplayTime` from the latest `xrWaitFrame` call when querying for poses and views.</span></span>
<span data-ttu-id="6477f-148">이를 통해 HoloLens는 HoloLens를 입고 있는 사용자의 렌더링을 조정 하 고 시각적 품질을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-148">This allows HoloLens to adjust rendering and optimize visual quality for the person who is wearing the HoloLens.</span></span>

### <a name="use-a-single-projection-layer"></a><span data-ttu-id="6477f-149">단일 프로젝션 계층 사용</span><span class="sxs-lookup"><span data-stu-id="6477f-149">Use a single projection layer</span></span>

<span data-ttu-id="6477f-150">HoloLens 2는 응용 프로그램에서 콘텐츠를 렌더링할 수 있는 GPU 능력과 단일 프로젝션 계층에 최적화 된 하드웨어 compositor 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-150">HoloLens 2 has limited GPU power for applications to render content and a hardware compositor optimized for a single projection layer.</span></span>
<span data-ttu-id="6477f-151">항상 단일 프로젝션 계층을 사용 하면 응용 프로그램의 프레임 속도, 홀로그램 안정성 및 시각적 품질에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-151">Always using a single projection layer can help the application's framerate, hologram stability and visual quality.</span></span>  
  
<span data-ttu-id="6477f-152">**성능 경고:** 단일 보호 계층을 제외한 모든 항목을 제출 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-152">**Performance Warning:** Submitting anything but a single protection layer will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-texture-array-and-vprt"></a><span data-ttu-id="6477f-153">질감 배열 및 VPRT를 사용 하 여 렌더링</span><span class="sxs-lookup"><span data-stu-id="6477f-153">Render with texture array and VPRT</span></span>

<span data-ttu-id="6477f-154">`xrSwapchain`Color이 swapchain present를 사용 하 여 왼쪽 및 오른쪽 눈에 하나씩 `arraySize=2` , 깊이를 위한 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-154">Create one `xrSwapchain` for both left and right eye using `arraySize=2` for color swapchain, and one for depth.</span></span>
<span data-ttu-id="6477f-155">왼쪽 눈동자를 조각 0에 그리고 올바른 눈을 조각 1로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-155">Render the left eye into slice 0 and the right eye into slice 1.</span></span>
<span data-ttu-id="6477f-156">Stereoscopic 렌더링에 대해 VPRT 및 인스턴스화된 그리기 호출에 셰이더를 사용 하 여 GPU 로드를 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-156">Use a shader with VPRT and instanced draw calls for stereoscopic rendering to minimize GPU load.</span></span>
<span data-ttu-id="6477f-157">이를 통해 런타임의 최적화를 사용 하 여 HoloLens 2에서 최상의 성능을 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-157">This also enables the runtime's optimization to achieve the best performance on HoloLens 2.</span></span>
<span data-ttu-id="6477f-158">이중 전체 렌더링 또는 눈에이 swapchain present 별도의 개별 같이 질감 배열을 사용 하는 대신, 런타임 사후 처리가 발생 하 여 상당한 성능 저하가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-158">Alternatives to using a texture array, such as double-wide rendering or a separate swapchain per eye, will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="avoid-quad-layers"></a><span data-ttu-id="6477f-159">쿼드 계층 방지</span><span class="sxs-lookup"><span data-stu-id="6477f-159">Avoid quad layers</span></span>

<span data-ttu-id="6477f-160">4 개의 계층을의 컴포지션 계층으로 제출 하는 대신 `XrCompositionLayerQuad` 쿼드 콘텐츠를 프로젝션이 swapchain present 직접 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-160">Rather than submitting quad layers as composition layers with `XrCompositionLayerQuad`, render the quad content directly into the projection swapchain.</span></span>

<span data-ttu-id="6477f-161">**성능 경고:** 쿼드 계층과 같이 단일 프로젝션 계층 밖의 추가 계층을 제공 하면 런타임 사후 처리가 발생 하 여 상당한 성능 저하가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="6477f-161">**Performance Warning:** Providing additional layers beyond a single projection layer, such as quad layers, will result in runtime post-processing which comes at a significant performance penalty.</span></span>