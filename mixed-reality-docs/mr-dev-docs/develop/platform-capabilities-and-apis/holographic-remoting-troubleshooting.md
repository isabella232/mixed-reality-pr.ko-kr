---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2 장치에서 Holographic 원격 기능에 대 한 문제 해결 리소스 및 지침을 찾습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말, 혼합 현실 헤드셋, windows Mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 429ca7364d82e1713af059aa3c6da01852283120
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583838"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="73a99-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="73a99-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73a99-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="73a99-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="73a99-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="73a99-108">*Vccorlib를 가져올 수 없는* 경우 오류가 발생할 수 있습니다. Visual Studio 워크 로드에 [스펙터 완화 된 라이브러리가](/cpp/build/reference/qspectre) 포함 되어 있는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="73a99-108">If you get the *vccorlib.lib cannot be opened* fatal error, make sure that your Visual Studio Workload includes the [Spectre mitigated libraries](/cpp/build/reference/qspectre)</span></span>

## <a name="speech"></a><span data-ttu-id="73a99-109">음성</span><span class="sxs-lookup"><span data-stu-id="73a99-109">Speech</span></span>

<span data-ttu-id="73a99-110">Holographic Remoting Player는 진단 오버레이를 지원 합니다 .이 오버레이는에 대해 말하고 사용 하지 않도록 설정할 수 있습니다 ```Enable Diagnostics``` ```Disable Diagnostics``` .</span><span class="sxs-lookup"><span data-stu-id="73a99-110">The Holographic Remoting Player supports a diagnostics overlay, which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="73a99-111">이러한 음성 명령에 문제가 있는 경우를 URL로 사용 하 여 웹 브라우저를 통해 Holographic 원격 플레이어를 시작할 수도 있습니다 ```ms-holographic-remoting:?stats``` .</span><span class="sxs-lookup"><span data-stu-id="73a99-111">If you have trouble with these voice commands, you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as a URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="73a99-112">H265 비디오 코덱을 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="73a99-112">H265 video codec not available</span></span>

<span data-ttu-id="73a99-113">원격 앱에서 H265 video 코덱을 사용할 때 [HEVC 비디오 확장](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-113">Install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="73a99-114">코덱이 설치 되어 있지만 사용할 수 없는 문제가 발생 하는 경우 [문제 해결](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 가이드를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="73a99-114">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="73a99-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="73a99-115">Limitations</span></span>

<span data-ttu-id="73a99-116">다음 Api는 현재 HoloLens 2에 대 한 Holographic 원격을 사용 하는 경우 지원 **되지** 않으며 별도로 ```ERROR_NOT_SUPPORTED``` 명시 하지 않는 한 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-116">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raise an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="73a99-117">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="73a99-117">Windows.Graphics.Holographic</span></span>](/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="73a99-118">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="73a99-118">HolographicCamera.ViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="73a99-119">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-119">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="73a99-120">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-120">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="73a99-121">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="73a99-121">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="73a99-122">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="73a99-122">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="73a99-123">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-123">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="73a99-124">이전 버전에서는 실패 하지만 렌더링 대상 크기는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-124">On previous versions don't fail, but the render target size won't be changed.</span></span>
* [<span data-ttu-id="73a99-125">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="73a99-125">HolographicCameraPose.OverrideProjectionTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="73a99-126">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="73a99-126">HolographicCameraPose.OverrideViewport</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="73a99-127">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="73a99-127">HolographicCameraPose.OverrideViewTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="73a99-128">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-128">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="73a99-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="73a99-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="73a99-130">Doe.</span><span class="sxs-lookup"><span data-stu-id="73a99-130">Doe.</span></span>
  - <span data-ttu-id="73a99-131">[2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-131">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="73a99-132">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="73a99-132">HolographicDisplay.TryGetViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="73a99-133">HolographicViewConfigurationKind. PhotoVideoCamera를 쿼리하면 항상이 반환 됩니다 ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="73a99-133">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="73a99-134">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-134">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="73a99-135">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-135">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="73a99-136">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="73a99-136">HolographicSpace.CreateFramePresentationMonitor</span></span>](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="73a99-137">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="73a99-137">HolographicDisplay.GetDefault</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="73a99-138">는 연결을 설정 하기 전에 호출 되는 경우 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-138">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="73a99-139">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="73a99-139">Windows.Perception.Spatial</span></span>](/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="73a99-140">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="73a99-140">SpatialLocation.AbsoluteAngularAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="73a99-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="73a99-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="73a99-142">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="73a99-142">SpatialLocation.AbsoluteAngularVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="73a99-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="73a99-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="73a99-144">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="73a99-144">SpatialLocation.AbsoluteLinearAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="73a99-145">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="73a99-145">SpatialLocation.AbsoluteLinearVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="73a99-146">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="73a99-146">SpatialStageFrameOfReference.Current</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="73a99-147">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-147">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="73a99-148">이전 버전에서는 항상을 반환 ```nullptr``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-148">On previous versions always return ```nullptr```.</span></span>
* [<span data-ttu-id="73a99-149">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="73a99-149">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="73a99-150">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-150">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="73a99-151">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="73a99-151">SpatialAnchor.RemovedByUser</span></span>](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="73a99-152">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="73a99-152">SpatialAnchorExporter.GetDefault</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="73a99-153">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-153">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="73a99-154">이전 버전에서는 항상을 반환 ```nullptr``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-154">On previous versions always return ```nullptr```.</span></span> 
* [<span data-ttu-id="73a99-155">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="73a99-155">SpatialAnchorExporter.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="73a99-156">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-156">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="73a99-157">이전 버전에서 비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-157">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="73a99-158">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="73a99-158">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="73a99-159">비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-159">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="73a99-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="73a99-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="73a99-161">비동기 작업은 항상를 사용 하 여 완료 ```false``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-161">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="73a99-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="73a99-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="73a99-163">비동기 작업은 항상를 사용 하 여 완료 ```nullptr``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a99-163">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="73a99-164">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="73a99-164">Windows.UI.Input.Spatial</span></span>](/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="73a99-165">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="73a99-165">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="73a99-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="73a99-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="73a99-167">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="73a99-167">SpatialInteractionSource.Controller</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="73a99-168">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="73a99-168">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="73a99-169">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="73a99-169">Windows.Perception.Spatial.Preview</span></span>](/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="73a99-170">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="73a99-170">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="73a99-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="73a99-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="73a99-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73a99-172">See Also</span></span>
* [<span data-ttu-id="73a99-173">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="73a99-173">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="73a99-174">Windows Mixed Reality Api를 사용 하 여 Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="73a99-174">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="73a99-175">OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="73a99-175">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="73a99-176">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="73a99-176">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="73a99-177">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="73a99-177">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="73a99-178">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="73a99-178">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)