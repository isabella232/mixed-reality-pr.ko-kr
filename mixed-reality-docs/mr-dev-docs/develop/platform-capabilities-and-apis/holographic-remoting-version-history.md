---
title: 홀로그램 Remoting 버전 기록
description: HoloLens 2 대한 홀로그램 Remoting 기능의 버전 기록을 최신 상태로 유지합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, 버전 기록, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 21ba89e477872f5dfa41468f1a7f2d7507affd681556d79843c195d7d5839e7b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223558"
---
# <a name="holographic-remoting-version-history"></a>홀로그램 Remoting 버전 기록

> [!IMPORTANT]
> 이 지침은 HoloLens 2 Holographic Remoting과 관련이 있습니다.

## <a name="version-261-july-20-2021"></a>버전 2.6.1(2021년 7월 20일) <a name="v2.6.1"></a>
* 이제 XR_MSFT_holographic_remoting_speech 확장을 사용하면 실행 중인 세션 중에 새 매개 변수를 통해 음성 인식기의 다시 초기화를 허용합니다.
* 여러 연결을 통해 음성 인식 안정성이 저하되는 문제를 해결했습니다.
* 다양한 버그 수정 및 안정성 향상.

## <a name="version-260-june-10-2021"></a>버전 2.6.0(2021년 6월 10일) <a name="v2.6.0"></a>
* OpenXR API를 사용하는 홀로그램 Remoting은 이제 다음을 지원합니다.
  * 애플리케이션이 다양한 언어로 사용자 지정 음성 명령을 수신 대기할 수 있는 새로운 XR_MSFT_holographic_remoting_speech 확장입니다.
  * XR_MSFT_scene_understanding 확장은 사용자 환경에서 평면, 메시 및 개체의 구조화되고 높은 수준의 표현을 애플리케이션에 제공하여 공간 인식 애플리케이션을 개발합니다. 그러나 xrComputeNewSceneMSFT에서 지원하는 유일한 일관성은 XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT 주의해야 합니다.
  * 애플리케이션이 XrSpace 핸들을 만들어 다른 Windows Mixed Reality 디바이스 플랫폼 라이브러리 또는 API의 공간 Graph 노드를 추적할 수 있도록 하는 XR_MSFT_spatial_graph_bridge 확장입니다. 그러나 XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT xrCreateSpatialGraphNodeSpaceMSFT에서 지원하는 유일한 노드 유형이라는 주의 사항이 있습니다. 
* 이제 Mixed Reality API를 사용하는 홀로그램 Remoting에서 다음을 지원합니다.
  * SpatialGraphInteropPreview.CreateCoordinateSystemForNode 오버로드는 애플리케이션이 정적 공간 Graph 노드를 추적하여 사용자가 환경의 장소와 사물을 추론할 수 있도록 합니다.
* OpenXR 및 Mixed Reality API를 모두 사용하는 홀로그램 Remoting은 이제 다음을 지원합니다.
  * Microsoft.MixedReality.SceneUnderstanding SDK를 사용하면 애플리케이션에서 쿼드, 메시 및 콘텐츠 배치 큐를 제공하는 사용자(예: 벽, 바닥 및 표면)를 둘러싼 장면에 대한 설명을 계산할 수 있습니다.
  * Microsoft.MixedReality.QR SDK를 사용하면 애플리케이션이 검색된 QR 코드의 위치, 크기 및 콘텐츠를 추적할 수 있습니다.
* OpenXR 원격 샘플은 다음을 포함하도록 업데이트되었습니다. 
  * XR_MSFT_holographic_remoting_speech 확장을 사용하는 예제입니다.
* Mixed Reality 원격 샘플은 다음을 포함하도록 업데이트되었습니다.  
  * Microsoft.MixedReality.SceneUnderstanding SDK를 사용하는 예제입니다.
  * 이전 QR 코드 검색 메커니즘을 대체하는 Microsoft.MixedReality.QR SDK를 사용하는 예제입니다.
* 이제 홀로그램 Remoting 플레이어에 연결이 설정되는 동안 로드 애니메이션이 표시됩니다.
* OpenXR API 런타임 및 Mixed Reality API 샘플 모두에서 RenderDoc 호환성 문제가 해결되었습니다.
* 다양한 버그 수정 및 안정성 향상.

## <a name="version-250-february-12-2021"></a>버전 2.5.0(2021년 2월 12일) <a name="v2.5.0"></a>
* [OpenXR API를](../native/openxr.md) 사용하는 홀로그램 Remoting은 이제 다음을 지원합니다.
  * 확장 XR_MSFT_spatial_anchor. 이 확장을 사용하면 애플리케이션에서 공간 앵커를 만들 수 있습니다. 이 공간 앵커는 런타임에서 추적할 사용자의 물리적 환경에서 임의의 프리스페이스 지점입니다.
  * XR_MSFT_controller_model 확장. 이 확장은 컨트롤러에 대한 GLTF 모델을 로드하는 메커니즘을 제공합니다.
  * XR_MSFT_holographic_remoting 확장의 일부로 사용자 지정 데이터 채널. 에 대한 예제는 [OpenXR 원격 샘플](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에 표시됩니다.
* 플레이어와 원격 쪽 간의 동기화가 향상되었습니다. 이렇게 하면 원격 렌더링된 콘텐츠가 예상 대상 프레임 속도로 디스플레이에 원활하게 도달할 수 있도록 하는 자세 및 프레임 버퍼링을 동적으로 변경할 수 있습니다.
* Microsoft Store 통해 사용할 수 있는 홀로그램 Remoting 플레이어의 성능이 향상되었습니다. HoloLens 2 플레이어는 이제 초당 60프레임에서 단색으로 실행됩니다.
* 원격 앱에서 [SpatialSurfaceObserver를](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) 통해 쿼리할 수 있는 공간 표면 메시의 최적화된 전송입니다.
* SpatialAnchorManager 메서드를 호출하거나 앵커를 해제하면 연결이 끊어질 때 예외가 발생하는 문제가 해결되었습니다.
* PlayerContext 또는 RemoteContext 인스턴스를 닫을 때 크래시로 이어지는 스레딩 문제가 해결되었습니다.
* 데스크톱의 홀로그램 원격 플레이어: 자동으로 닫는 대신 Windows Mixed Reality 설치되지 않은 경우 오류 메시지를 표시합니다.
* 기타 많은 버그 수정 및 안정성 향상.

## <a name="version-241-january-22-2021"></a>버전 2.4.1(2021년 1월 22일) <a name="v2.4.1"></a>

* 연결하는 동안 호출할 때 SpatialAnchorManager::RequestStoreAsync가 안정적으로 작동하지 않는 문제가 해결되었습니다.
* 해당 앵커를 찾아올 수 없는 경우 SpatialAnchorManager::TrySave가 앵커를 올바르게 저장하지 않는 문제가 해결되었습니다.

## <a name="version-240-december-1-2020"></a>버전 2.4.0(2020년 12월 1일) <a name="v2.4.0"></a>

* 홀로그램 원격은 이제 [OpenXR API를](../native/openxr.md)사용하여 원격 앱 작성을 지원합니다. [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성을](holographic-remoting-create-remote-openxr.md) 확인하여 시작하세요.
* 버그 수정 및 안정성 향상.

## <a name="version-231-october-10-2020"></a>버전 2.3.1(2020년 10월 10일) <a name="v2.3.1"></a>

* 시각적 지터를 발생시킨 원격 자세 예측을 사용하여 회귀를 수정했습니다.
* Holographic Remoting과 함께 제공되는 PerceptionDevice.dll Windows 10 함께 제공되는 버전을 방해하지 않도록 하는 PerceptionDeviceSetCreateFactoryOverride가 구현되었습니다.

## <a name="version-230-october-2-2020"></a>버전 2.3.0(2020년 10월 2일) <a name="v2.3.0"></a>

* 홀로그램 Remoting Player가 일시 중단될 때 발생할 수 있는 크래시 수정
* 안정성 향상

## <a name="version-223-august-28-2020"></a>버전 2.2.3(2020년 8월 28일) <a name="v2.2.3"></a>

* 버그 수정 및 안정성 향상.

## <a name="version-222-july-10-2020"></a>버전 2.2.2(2020년 7월 10일) <a name="v2.2.2"></a>

* Windows Mixed Reality 헤드셋에서 스트리밍할 때 [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 및 [HolographicCamera.RightViewportParameters가](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 숨겨진 영역 메시 꼭짓점을 반환하지 않는 문제가 해결되었습니다.
* 네트워크 연결이 끊어질 때 발생할 수 있는 크래시 문제가 해결되었습니다.

## <a name="version-221-july-6-2020"></a>버전 2.2.1(2020년 7월 6일) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [버전](https://developer.microsoft.com/windows/downloads/app-certification-kit/) [2.2.0을](holographic-remoting-version-history.md#v2.2.0) Windows 앱 인증 키트 유효성 검사가 실패합니다. 버전 [2.2.0을](holographic-remoting-version-history.md#v2.2.0) 사용 중이고 적어도 버전 2.2.1로 업데이트된 Microsoft Store p 임대에 애플리케이션을 제출하려는 경우
* [Windows 앱 인증 키트](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 준수 문제가 해결되었습니다.

## <a name="version-220-july-1-2020"></a>버전 2.2.0(2020년 7월 1일) <a name="v2.2.0"></a>

* 이제 홀로그램 Remoting 플레이어를 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)실행 중인 PC에 설치하여 몰입형 헤드셋으로 스트리밍할 수 있습니다.
* [이제 홀로그램](../../design/motion-controllers.md) Remoting에서 모션 컨트롤러를 지원하며, [SpatialInteractionSource.Controller를](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)통해 컨트롤러 관련 데이터를 검색할 수 있습니다.
* [이제 SpatialStageFrameOfReference가](/uwp/api/windows.perception.spatial.spatialstageframeofreference) 지원되며 현재 스테이지는 [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)를 통해 검색할 수 있습니다. 또한 [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)를 통해 새 스테이지를 요청할 수 있습니다.
* 이전 버전에서는 홀로그램 Remoting 플레이어가 플레이어 쪽에서 자세 예측을 처리했습니다. 버전 2.2.0부터 홀로그램 원격에 시간 동기화가 있으며 원격 애플리케이션에서 예측이 완전히 수행됩니다. 또한 사용자는 어려운 네트워크 상황에서 향상된 홀로그램 안정성을 기대해야 합니다.

## <a name="version-213-may-25-2020"></a>버전 2.1.3(2020년 5월 25일) <a name="v2.1.3"></a>

* [HolographicSpace.CameraAdded 이벤트의 동작이 변경되었습니다.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 이전 버전에서는 [HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)을 통해 다음 프레임을 만들 때 추가된 [HolographicCamera에도](/uwp/api/windows.graphics.holographic.holographiccamera) 유효한 [HolographicCameraPose가](/uwp/api/windows.graphics.holographic.holographiccamerapose) 있다고 **보장되지 않았습니다.** 버전 2.1.3부터 [HolographicSpace.CameraAdded는 홀로그램](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) Remoting Player에서 오는 자세 데이터와 동기화됩니다. 사용자는 카메라가 추가되면 다음 프레임에서 해당 카메라에 사용할 수 있는 유효한 [HolographicCameraPose도](/uwp/api/windows.graphics.holographic.holographiccamerapose) 있다고 예상할 수 있습니다.
* RemoteContext.Config ureDepthVideoStream을 통해 깊이 버퍼 스트리밍을 사용하지 않도록 설정하는 데 사용할 수 있는 DepthBufferStreamResolution에 사용 안 함이 추가되었습니다. 사용된 경우 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer는](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) *E_ILLEGAL_METHOD_CALL* 실패합니다.
* 홀로그램 Remoting Player의 시작 화면이 다시 디자인되었으며 이제 사용자 보기를 차단하지 않습니다.
* 안정성 향상 및 버그 수정.

## <a name="version-212-april-5-2020"></a>버전 2.1.2(2020년 4월 5일) <a name="v2.1.2"></a>

* 2.1.0보다 작은 버전을 사용하는 최신 홀로그램 원격 플레이어와 원격 앱 간의 오디오 이전 버전과의 호환성 문제가 해결되었습니다.
* 홀로그램 Remoting 플레이어를 예기치 않게 닫은 공간 앵커 문제가 해결되었습니다. 이 문제는 사용자 지정 플레이어에도 영향을 미칩니다.

## <a name="version-211-march-20-2020"></a>버전 2.1.1(2020년 3월 20일) <a name="v2.1.1"></a>

* AMD GPU를 사용할 때 원격 앱의 비디오 인코딩 문제가 해결되었습니다.
* 홀로그램 Remoting Player 성능이 향상되었습니다.

## <a name="version-210-march-11-2020"></a>버전 2.1.0(2020년 3월 11일) <a name="v2.1.0"></a>

* UDP를 통해 [RTP를](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) 사용하도록 네트워크 전송을 전환했습니다. 이제 보안 연결에서 [SRTP를](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 사용합니다. [홀로그램 Remoting Player는](holographic-remoting-player.md) 이전 릴리스의 모든 Holographic Remoting 버전과 여전히 호환됩니다. 새 네트워크 전송을 활용하려면 Holographic Remoting Player와 해당 원격 앱 모두 버전 2.1.0을 사용해야 합니다.
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer에](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)대한 지원이 추가되었습니다. 

## <a name="version-2020-february-2-2020"></a>버전 2.0.20(2020년 2월 2일) <a name="v2.0.20"></a>

* 크래시로 이어지는 다양한 버그를 수정했습니다.

## <a name="version-2018-december-17-2019"></a>버전 2.0.18(2019년 12월 17일) <a name="v2.0.18"></a>

* [HolographicViewConfiguration에](/uwp/api/windows.graphics.holographic.holographicviewconfiguration) 대한 지원이 추가되었습니다.
* 크래시로 이어지는 다양한 버그를 수정했습니다.
* HolographicCamera가 허용되고 HolographicFrame에 추가된 카메라로 표시되려면 HolographicSpace.CameraAdded 콜백이 필요한 버그가 수정되었습니다.

## <a name="version-2016-november-11-2019"></a>버전 2.0.16(2019년 11월 11일) <a name="2.0.16"></a>

* QR 코드 추적에서 교착 상태가 수정되었습니다.
* 주 스레드에서 차단 대기로 인해 처리되지 않은 예외가 수정되었습니다.

## <a name="version-2014-october-26-2019"></a>버전 2.0.14(2019년 10월 26일) <a name="v2.0.14"></a>

* 새 PerceptionDevice API 지원(Windows 10 2019년 11월 업데이트)
* SpatialGestureRecognizer에 의해 트리거되는 보류 제스처 이벤트를 방지하는 문제가 해결되었습니다.
* SpatialSurfaceObserver.SetBoundingVolume을 사용할 때의 스레딩 문제가 해결되었습니다.

## <a name="version-2012-october-18-2019"></a>버전 2.0.12(2019년 10월 18일) <a name="v2.0.12"></a>

* NavigationRail(X/Y/Z)을 사용할 때 SpatialGestureRecognizer의 크래시 수정

## <a name="version-2010-october-10-2019"></a>버전 2.0.10(2019년 10월 10일) <a name="v2.0.10"></a>

* VR 컨트롤러의 트리거 단추를 사용할 때의 충돌을 수정했습니다. 홀로그램 Remoting은 컨트롤러를 완벽하게 지원하지 않으며, 트리거 단추와 Windows 단추만 HoloLens 2 쌍을 이루는 경우 작동합니다.

## <a name="version-209-september-19-2019"></a>버전 2.0.9(2019년 9월 19일) <a name="v2.0.9"></a>

* [SpatialAnchorExporter에](/uwp/api/windows.perception.spatial.spatialanchorexporter) 대한 지원이 추가되었습니다.
* 다음 멤버를 제공하는 새 ```IPlayerContext2``` 인터페이스(에 의해 구현)가 추가되었습니다. ```PlayerContext```
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  속성입니다.
* ```Failed_RemoteFrameTooOld```??에 값 추가```BlitResult```
* 안정성 및 안정성 향상

## <a name="version-208-august-20-2019"></a>버전 2.0.8(2019년 8월 20일) <a name="v2.0.8"></a>

* [IDXGISurface2를](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) 매개 변수로 통해 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer를](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 호출할 때의 크래시 문제가 해결되었습니다.
* 안정성 및 안정성 향상

## <a name="version-207-july-26-2019"></a>버전 2.0.7(2019년 7월 26일) <a name="v2.0.7"></a>

* HoloLens 2 Holographic Remoting의 첫 번째 공개 릴리스입니다.

## <a name="see-also"></a>참고 항목

* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 Remoting 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)