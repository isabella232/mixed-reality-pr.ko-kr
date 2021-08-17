---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2 장치에서 Holographic 원격 기능에 대 한 문제 해결 리소스 및 지침을 찾습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic 원격, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말, 혼합 현실 헤드셋, Windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: d49f73f4cbe205e71cb2f76ab02769ddad5f3ed2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184614"
---
# <a name="holographic-remoting-troubleshooting"></a>Holographic 원격 문제 해결

> [!IMPORTANT]
> 이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

## <a name="spectre-mitigated-libraries-not-found"></a>스펙터 완화 라이브러리를 찾을 수 없습니다.

Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.

*vccorlib를 가져올 수 없는* 경우 오류가 발생할 수 있습니다. Visual Studio 작업에 [스펙터 완화 된 라이브러리가](/cpp/build/reference/qspectre) 포함 되어 있는지 확인 하세요.

## <a name="speech"></a>음성

Holographic Remoting Player는 진단 오버레이를 지원 합니다 .이 오버레이는에 대해 말하고 사용 하지 않도록 설정할 수 있습니다 ```Enable Diagnostics``` ```Disable Diagnostics``` . 이러한 음성 명령에 문제가 있는 경우를 URL로 사용 하 여 웹 브라우저를 통해 Holographic 원격 플레이어를 시작할 수도 있습니다 ```ms-holographic-remoting:?stats``` .

## <a name="h265-video-codec-not-available"></a>H265 비디오 코덱을 사용할 수 없음

원격 앱에서 H265 비디오 코덱을 사용 하는 경우 [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 를 설치 합니다. 코덱이 설치 되어 있지만 사용할 수 없는 문제가 발생 하는 경우 [문제 해결](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 가이드를 확인 하세요.

## <a name="limitations"></a>제한 사항

다음 api는 HoloLens 2에 대해 Holographic 원격을 사용 하는 경우 현재 지원 **되지** 않으며 ```ERROR_NOT_SUPPORTED``` 달리 지정 되지 않은 경우 오류를 발생 시킵니다.

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - [2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨
  - 이전 버전에서는 항상 오류가 발생 합니다.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - [2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨
  - 이전 버전에서는 실패 하지만 렌더링 대상 크기는 변경 되지 않습니다.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose. OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - [2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Doe.
  - [2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 지원 됨
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - HolographicViewConfigurationKind. PhotoVideoCamera를 쿼리하면 항상이 반환 됩니다 ```nullptr``` .
  - [2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨
  - 이전 버전에서는 항상 오류가 발생 합니다.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay. GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 는 연결을 설정 하기 전에 호출 되는 경우 오류를 보고 합니다.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [Spatiallocation이. AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [Spatiallocation이. AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [Spatiallocation이. AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [Spatiallocation이. AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - [2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨
  - 이전 버전에서는 항상을 반환 ```nullptr``` 합니다.
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - [2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - [2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다. 
  - 이전 버전에서는 항상을 반환 ```nullptr``` 합니다. 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - [2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다. 
  - 이전 버전에서 비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.
* [SpatialAnchorTransferManager](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 비동기 작업은 항상를 사용 하 여 완료 ```false``` 됩니다.
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 비동기 작업은 항상를 사용 하 여 완료 ```nullptr``` 됩니다.

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - [2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>참고 항목
* [Holographic 원격 기능 개요](holographic-remoting-overview.md)
* [Holographic 원격 버전 기록](holographic-remoting-version-history.md)
* [Windows Mixed Reality api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)