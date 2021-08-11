---
title: 홀로그램 Remoting 문제 해결 및 제한 사항
description: HoloLens 2 디바이스에서 홀로그램 Remoting 기능에 대한 문제 해결 리소스 및 지침을 찾습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, 홀로그램, 홀로그램 원격, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 홀로그램, 문제 해결, 도움말, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: fa984e89fb6eb770917d9a1d62ce7c1007d45fab7fbcb2723f9642ac81814054
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223573"
---
# <a name="holographic-remoting-troubleshooting"></a>홀로그램 Remoting 문제 해결

> [!IMPORTANT]
> 이 지침은 HoloLens 2 Holographic Remoting과 관련이 있습니다.

## <a name="spectre-mitigated-libraries-not-found"></a>스펙터 완화 라이브러리를 찾을 수 없습니다.

홀로그램 Remoting 샘플 앱은 릴리스 구성에서 스펙터 완화(/Qspectre)를 사용하도록 설정했습니다.

*vccorlib.lib를 심각한 오류로 열 수 없는* 경우 Visual Studio 워크로드에 Spectre 완화 라이브러리가 포함되어 있는지 [확인합니다.](/cpp/build/reference/qspectre)

## <a name="speech"></a>음성

Holographic Remoting Player는 진단 오버레이를 지원합니다. 이 오버레이는 를 말하여 활성화하고 을 사용하여 사용하지 않도록 설정할 수 ```Enable Diagnostics``` ```Disable Diagnostics``` 있습니다. 이러한 음성 명령에 문제가 있는 경우 URL로 를 사용하여 웹 브라우저를 통해 홀로그램 Remoting 플레이어를 시작할 수도 ```ms-holographic-remoting:?stats``` 있습니다.

## <a name="h265-video-codec-not-available"></a>H265 비디오 코덱을 사용할 수 없습니다.

원격 앱에서 H265 비디오 코덱을 사용하는 경우 [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 설치합니다. 코덱이 설치되어 있지만 사용할 수 없는 문제가 발생하면 문제 [해결 가이드를](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 확인하세요.

## <a name="limitations"></a>제한 사항

다음 API는 현재 HoloLens 2 Holographic Remoting을 사용할 때 **지원되지 않으며** 달리 명시되지 않는 한 오류가 발생합니다. ```ERROR_NOT_SUPPORTED```

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 버전 [2.0.18부터](holographic-remoting-version-history.md#v2.0.18) 지원됨
  - 이전 버전에서 항상 오류가 발생합니다.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 지원됨
  - 이전 버전에서는 실패하지 않지만 렌더링 대상 크기는 변경되지 않습니다.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - 버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 지원됨
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Doe.
  - 버전 [2.1.0부터](holographic-remoting-version-history.md#v2.1.0) 지원됨
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - HolographicViewConfigurationKind.PhotoVideoCamera를 쿼리하면 항상 가 ```nullptr``` 반환됩니다.
  - 버전 [2.0.18부터](holographic-remoting-version-history.md#v2.0.18) 지원됨
  - 이전 버전에서 항상 오류가 발생합니다.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 연결이 설정되기 전에 호출된 경우 오류를 보고합니다.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation.AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation.AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation.AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation.AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 지원됨
  - 이전 버전에서 는 항상 ```nullptr``` 를 반환합니다.
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - 버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 지원됨
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 버전 [2.0.9부터](holographic-remoting-version-history.md#v2.0.9)지원합니다. 
  - 이전 버전에서 는 항상 ```nullptr``` 를 반환합니다. 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 버전 [2.0.9부터](holographic-remoting-version-history.md#v2.0.9)지원합니다. 
  - 이전 버전에서 비동기 작업은 항상 로 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 완료되었습니다.
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 비동기 작업은 항상 로 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 완료됩니다.
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 비동기 작업은 항상 로 ```false``` 완료됩니다.
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 비동기 작업은 항상 로 ```nullptr``` 완료됩니다.

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - 버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 지원됨

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>참고 항목
* [홀로그램 Remoting 버전 기록](holographic-remoting-version-history.md)
* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)