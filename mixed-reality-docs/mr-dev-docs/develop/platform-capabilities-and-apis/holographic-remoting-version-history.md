---
title: Holographic 원격 버전 기록
description: HoloLens 2에 대 한 Holographic Remoting 기능의 버전 기록을 최신으로 유지 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 06/10/2021
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 버전 기록, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: dae7bc0dac792cbe1a8472415d5e9fa34532e918
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908218"
---
# <a name="holographic-remoting-version-history"></a>Holographic 원격 버전 기록

> [!IMPORTANT]
> 이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

## <a name="version-260-june-10-2021"></a>버전 2.6.0 (6 월 10 일, 2021) <a name="v2.6.0"></a>
* OpenXR API를 사용 하는 Holographic Remoting은 이제 다음을 지원 합니다.
  * 응용 프로그램이 다양 한 언어로 사용자 지정 음성 명령을 수신할 수 있게 해 주는 새로운 XR_MSFT_holographic_remoting_speech 확장입니다.
  * XR_MSFT_scene_understanding 확장은 응용 프로그램에 사용자 환경의 평면, 메시 및 개체에 대 한 구조화 된 상위 수준 표현을 제공 하 여 공간적으로 인식 되는 응용 프로그램을 개발할 수 있도록 합니다. 그러나 XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT는 xrComputeNewSceneMSFT에서 지원 되는 유일한 일관성을 유지 합니다.
  * 응용 프로그램에서 XrSpace 핸들을 만들어 다른 Windows Mixed Reality 장치 플랫폼 라이브러리 또는 Api의 공간 그래프 노드를 추적할 수 있도록 하는 XR_MSFT_spatial_graph_bridge 확장입니다. 그러나 XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT는 xrCreateSpatialGraphNodeSpaceMSFT에서 지원 되는 유일한 노드 형식입니다. 
* 혼합 현실 API를 사용 하는 Holographic Remoting은 이제 다음을 지원 합니다.
  * SpatialGraphInteropPreview CreateCoordinateSystemForNode 오버 로드를 사용 하 여 사용자가 환경에서 위치 및 사물을 알 수 있도록 응용 프로그램이 정적 공간 그래프 노드를 추적할 수 있습니다.
* OpenXR 및 Mixed Reality Api를 모두 사용 하는 Holographic Remoting은 이제 다음을 지원 합니다.
  * MixedReality SceneUnderstanding SDK를 사용 하 여 응용 프로그램이 quads, 메시 및 콘텐츠 배치 큐를 제공 하는 사용자 (예: 벽, 층 및 표면) 주위 장면에 대 한 설명을 계산할 수 있습니다.
  * 응용 프로그램에서 검색 된 QR 코드의 위치, 크기 및 콘텐츠를 추적할 수 있도록 하는 MixedReality SDK입니다.
* OpenXR 원격 샘플은 다음을 포함 하도록 업데이트 되었습니다. 
  * XR_MSFT_holographic_remoting_speech 확장을 사용 하는 예입니다.
* Mixed Reality 원격 샘플은 다음을 포함 하도록 업데이트 되었습니다.  
  * SceneUnderstanding SDK를 사용 하는 예를 MixedReality.
  * Microsoft. MixedReality SDK를 사용 하는 예 (이전 QR 코드 검색 메커니즘을 대체).
* 이제 연결이 설정 되는 동안 Holographic Remoting 플레이어에서 로드 하는 애니메이션을 표시 합니다.
* OpenXR API 런타임 및 Mixed Reality API 샘플에서 RenderDoc 호환성 문제가 해결 되었습니다.
* 다양 한 버그 수정 및 안정성 향상.

## <a name="version-250-february-12-2021"></a>버전 2.5.0 (2 월 12 일, 2021) <a name="v2.5.0"></a>
* [OPENXR API](../native/openxr.md) 를 사용 하는 Holographic Remoting은 이제 다음을 지원 합니다.
  * XR_MSFT_spatial_anchor 확장입니다. 이 확장을 통해 응용 프로그램은 사용자의 실제 환경에서 런타임에 의해 추적 되는 임의의 freespace 지점만 공간 앵커를 만들 수 있습니다.
  * XR_MSFT_controller_model 확장입니다. 이 확장은 컨트롤러에 대 한 지 수 TF 모델을 로드 하는 메커니즘을 제공 합니다.
  * XR_MSFT_holographic_remoting 확장의 일부로 사용자 지정 데이터 채널 이에 대 한 예제는 [OpenXR 원격 샘플](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에 나와 있습니다.
* 플레이어와 원격 측 간의 동기화가 향상 되었습니다. 이를 통해 동적으로 변경 되는 포즈 및 프레임 버퍼링을 사용할 수 있습니다 .이를 통해 원격 렌더링 된 콘텐츠가 필요한 대상 프레임 속도의 디스플레이에 매끄럽게 전달 됩니다.
* Microsoft Store를 통해 사용할 수 있는 Holographic 원격 플레이어의 성능이 개선 되었습니다. HoloLens 2에서 플레이어는 이제 초당 60 프레임에서 solid를 실행 합니다.
* 원격 앱에서 [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) 를 통해 쿼리할 수 있는 공간 노출 영역 메시의 전송 최적화.
* SpatialAnchorManager 메서드를 호출 하거나 앵커 해제 시 예외가 발생 하는 문제를 해결 했습니다.
* PlayerContext 또는 RemoteContext 인스턴스를 닫을 때 충돌 하는 스레딩 문제가 발생 합니다.
* 데스크톱의 Holographic 원격 플레이어: 자동으로 닫지 않고 Windows Mixed Reality가 설치 되지 않은 경우 오류 메시지를 표시 합니다.
* 다른 많은 버그 수정 및 안정성 향상.

## <a name="version-241-january-22-2021"></a>버전 2.4.1 (2021 년 1 월 22 일) <a name="v2.4.1"></a>

* 연결 하는 동안 호출 되는 경우 SpatialAnchorManager:: RequestStoreAsync가 안정적으로 작동 하지 않는 문제가 해결 되었습니다.
* 문제의 앵커가 과정이 되지 않는 경우 SpatialAnchorManager:: Trsave가 앵커를 올바르게 저장 하지 않는 문제를 해결 했습니다.

## <a name="version-240-december-1-2020"></a>버전 2.4.0 (2020 년 12 월 1 일) <a name="v2.4.0"></a>

* Holographic Remoting은 이제 [OPENXR API](../native/openxr.md)를 사용 하 여 원격 앱 작성을 지원 합니다. [OpenXR api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-openxr.md) 을 확인 하 여 시작 하세요.
* 버그 수정 및 안정성 향상.

## <a name="version-231-october-10-2020"></a>버전 2.3.1 (2020 년 10 월 10 일) <a name="v2.3.1"></a>

* 시각적 지터를 일으킨 원격 포즈 예측을 사용 하 여 회귀를 수정 했습니다.
* PerceptionDeviceSetCreateFactoryOverride을 구현 하 여 Holographic Remoting과 함께 제공 되는 PerceptionDevice.dll Windows 10과 함께 제공 되는 버전과 충돌 하지 않도록 합니다.

## <a name="version-230-october-2-2020"></a>버전 2.3.0 (2020 년 10 월 2 일) <a name="v2.3.0"></a>

* Holographic Remoting Player가 일시 중단 된 경우 발생할 수 있는 충돌 문제를 수정 했습니다.
* 안정성 향상

## <a name="version-223-august-28-2020"></a>버전 2.2.3 (2020 년 8 월 28 일) <a name="v2.2.3"></a>

* 버그 수정 및 안정성 향상.

## <a name="version-222-july-10-2020"></a>버전 2.2.2 (2020 년 7 월 10 일) <a name="v2.2.2"></a>

* Windows Mixed Reality 헤드셋에서 스트리밍할 때 숨겨진 영역 메시 꼭지점이 반환 되지 않는 [HolographicCamera viewportparameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 및 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 문제를 해결 했습니다.
* 네트워크 연결 불량으로 인해 발생할 수 있는 충돌 문제를 해결 했습니다.

## <a name="version-221-july-6-2020"></a>버전 2.2.1 (2020 년 7 월 6 일) <a name="v2.2.1"></a>

> [!IMPORTANT]
> 버전 [2.2.0](holographic-remoting-version-history.md#v2.2.0) 를 사용 하는 [Windows 앱 인증 키트](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 유효성 검사가 실패 합니다. 버전 [2.2.0](holographic-remoting-version-history.md#v2.2.0) 를 사용할 때 응용 프로그램을 Microsoft store p 임대가 최소 버전 2.2.1로 업데이트 하려면이를 선택 합니다.
* [Windows 앱 인증 키트](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 준수 문제를 수정 했습니다.

## <a name="version-220-july-1-2020"></a>버전 2.2.0 (2020 년 7 월 1 일) <a name="v2.2.0"></a>

* 이제 Holographic 원격 플레이어를 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)를 실행 하는 pc에 설치 하 여 몰입 형 헤드셋으로 스트리밍할 수 있습니다.
* 이제 Holographic 원격에서 [동작 컨트롤러](../../design/motion-controllers.md) 를 지원 하며 [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)를 통해 컨트롤러 관련 데이터를 검색할 수 있습니다.
* 이제 [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) 가 지원 되며 현재 단계는 [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)를 통해 검색할 수 있습니다. 또한 [SpatialStageFrameOfReference. RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)를 통해 새 단계를 요청할 수 있습니다.
* 이전 버전에서는 Holographic Remoting 플레이어에 의해 플레이어 쪽에서 포즈 예측이 처리 되었습니다. 2.2.0 버전부터 Holographic Remoting은 시간 동기화를 수행 하 고 예측은 원격 응용 프로그램에 의해 완전히 수행 됩니다. 또한 사용자는 까다로운 네트워크 상황에서 홀로그램 안정성이 향상 되어야 합니다.

## <a name="version-213-may-25-2020"></a>버전 2.1.3 (5 월 25 일, 2020) <a name="v2.1.3"></a>

* [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 이벤트의 동작이 변경 되었습니다. 이전 버전에서는 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)를 통해 다음 프레임을 만들 때 추가 된 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) 도 유효한 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 를 보장 **하지** 않았습니다. 2.1.3 버전부터 [HolographicSpace CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 는 Holographic 원격 플레이어에서 제공 되는 포즈 데이터와 동기화 됩니다. 사용자는 카메라가 추가 될 때 다음 프레임에서 해당 카메라에 사용할 수 있는 유효한 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 을 예측할 수 있습니다.
* RemoteContext.ConfigureDepthVideoStream를 통해 깊이 버퍼 스트리밍을 사용 하지 않도록 설정 하는 데 사용할 수 있는 DepthBufferStreamResolution에 사용 **안 함** 이 추가 되었습니다. HolographicCameraRenderingParameters를 사용 하는 경우 CommitDirect3D11DepthBuffer는 *E_ILLEGAL_METHOD_CALL* 와 함께 실패 합니다 [.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)
* Holographic Remoting 플레이어의 시작 화면이 다시 디자인 되었으며 이제 사용자 보기를 차단 하지 않습니다.
* 안정성 향상 및 버그 수정.

## <a name="version-212-april-5-2020"></a>버전 2.1.2 (2020 4 월 5 일) <a name="v2.1.2"></a>

* 2.1.0 보다 작은 버전을 사용 하 여 최신 Holographic 원격 플레이어와 원격 앱 간에 오디오의 이전 버전과의 호환성 문제가 해결 되었습니다.
* Holographic 원격 플레이어를 예기치 않게 닫은 공간 고정 문제를 수정 했습니다. 이 문제는 사용자 지정 플레이어에도 영향을 줍니다.

## <a name="version-211-march-20-2020"></a>버전 2.1.1 (3 월 20 일, 2020) <a name="v2.1.1"></a>

* AMD Gpu를 사용 하는 경우 원격 앱에 대 한 비디오 인코딩 문제를 수정 했습니다.
* Holographic 원격 플레이어의 성능 향상.

## <a name="version-210-march-11-2020"></a>버전 2.1.0 (2020 년 3 월 11 일) <a name="v2.1.0"></a>

* UDP를 통해 [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) 를 사용 하도록 네트워크 전송을 전환 했습니다. 보안 연결에는 [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 가 사용 됩니다. [Holographic Remoting Player](holographic-remoting-player.md) 는 이전의 모든 Release Holographic 원격 버전과 여전히 호환 됩니다. 새 네트워크 전송을 활용 하려면 Holographic Remoting 플레이어와 해당 원격 앱이 버전 2.1.0을 사용 해야 합니다.
* CommitDirect3D11DepthBuffer에 대 한 지원이 추가 되었습니다. [HolographicCameraRenderingParameters.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 

## <a name="version-2020-february-2-2020"></a>버전 2.0.20 이상을 (2 월 2 일, 2020) <a name="v2.0.20"></a>

* 충돌이 발생할 수 있는 다양 한 버그를 수정 했습니다.

## <a name="version-2018-december-17-2019"></a>버전 2.0.18 이상을 (2019 년 12 월 17 일) <a name="v2.0.18"></a>

* [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration) 에 대 한 지원이 추가 됨
* 충돌이 발생할 수 있는 다양 한 버그를 수정 했습니다.
* HolographicCamera를 수락 하 고 HolographicFrame에 추가 된 카메라로 표시 하는 데 HolographicSpace. CameraAdded 콜백이 필요한 버그를 수정 했습니다.

## <a name="version-2016-november-11-2019"></a>버전 2.0.16(2019년 11월 11일) <a name="2.0.16"></a>

* QR 코드 추적에서 교착 상태가 수정되었습니다.
* 주 스레드에서 차단 대기로 인해 처리되지 않은 예외가 수정되었습니다.

## <a name="version-2014-october-26-2019"></a>버전 2.0.14(2019년 10월 26일) <a name="v2.0.14"></a>

* 새 PerceptionDevice API 지원(Windows 10 2019년 11월 업데이트)
* SpatialGestureRecognizer에 의해 트리거되는 보류 제스처 이벤트를 방지하는 문제가 해결되었습니다.
* SpatialSurfaceObserver.SetBoundingVolume을 사용할 때의 스레딩 문제가 해결되었습니다.

## <a name="version-2012-october-18-2019"></a>버전 2.0.12(2019년 10월 18일) <a name="v2.0.12"></a>

* NavigationRail(X/Y/Z)을 사용할 때 SpatialGestureRecognizer의 충돌을 수정했습니다.

## <a name="version-2010-october-10-2019"></a>버전 2.0.10(2019년 10월 10일) <a name="v2.0.10"></a>

* VR 컨트롤러의 트리거 단추를 사용할 때의 충돌을 수정했습니다. 홀로그램 Remoting은 컨트롤러를 완전히 지원하지 않으며, HoloLens 2 쌍을 이루는 경우 트리거 단추와 Windows 단추만 작동합니다.

## <a name="version-209-september-19-2019"></a>버전 2.0.9(2019년 9월 19일) <a name="v2.0.9"></a>

* [SpatialAnchorExporter에](/uwp/api/windows.perception.spatial.spatialanchorexporter) 대한 지원이 추가되었습니다.
* 다음 멤버를 제공하는 새 ```IPlayerContext2``` 인터페이스(에 의해 구현)가 추가되었습니다. ```PlayerContext```
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  속성입니다.
* ```Failed_RemoteFrameTooOld```에 값이 추가되었습니다.```BlitResult```
* 안정성 및 안정성 향상

## <a name="version-208-august-20-2019"></a>버전 2.0.8(2019년 8월 20일) <a name="v2.0.8"></a>

* [IDXGISurface2를](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) 매개 변수로 통해 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer를](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 호출할 때의 크래시 문제가 해결되었습니다.
* 안정성 및 안정성 향상

## <a name="version-207-july-26-2019"></a>버전 2.0.7(2019년 7월 26일) <a name="v2.0.7"></a>

* HoloLens 2 대한 홀로그램 Remoting의 첫 번째 공개 릴리스입니다.

## <a name="see-also"></a>참고 항목

* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 Remoting 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)