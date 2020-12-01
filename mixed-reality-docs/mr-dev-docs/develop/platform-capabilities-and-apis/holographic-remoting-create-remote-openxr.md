---
title: Holographic Remoting 원격 앱 작성 (OpenXR)
description: 원격 컴퓨터에서 렌더링 되는 원격 콘텐츠를 Holographic Remoting 원격 앱을 만들면 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469506"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>OpenXR API를 사용 하 여 Holographic Remoting 원격 앱 작성

>[!IMPORTANT]
>이 문서에서는 [OPENXR API](../native/openxr.md)를 사용 하 여 HoloLens 2 및 Windows Mixed Reality 헤드셋 용 원격 응용 프로그램을 만드는 방법을 설명 합니다. HoloLens 용 원격 응용 프로그램 **(첫 번째 gen)** 은 NuGet 패키지 **버전 1.x를 사용** 해야 합니다. 즉, HoloLens 2 용으로 작성 된 원격 응용 프로그램은 HoloLens 1과 호환 되지 않으며 그 반대의 경우도 마찬가지입니다. HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.

Holographic Remoting 원격 앱을 만들면 원격 컴퓨터에서 렌더링 되는 원격 콘텐츠를 Windows Mixed Reality 헤드셋과 같은 HoloLens 2 및 몰입 형 장치로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다. 이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

Holographic remoting을 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 렌더링 된 Holographic 콘텐츠를 사용 하 여 HoloLens 2 및 Windows Mixed Reality 헤드셋을 대상으로 할 수 있습니다 .이를 통해 더 많은 시스템 리소스에 액세스 하 고 원격 [몰입 형 보기](../../design/app-views.md) 를 기존 데스크톱 PC 소프트웨어에 통합할 수 있습니다. 원격 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다. 연결은 표준 Wi-fi를 사용 하 여 수행 됩니다. Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다. 연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.

일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다. 플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

좋은 출발점은 작업 OpenXR 기반 데스크톱 또는 UWP 앱입니다. 자세한 내용은 [OpenXR 시작](../native/openxr-getting-started.md)하기를 참조 하세요.

>[!IMPORTANT]
>Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다. [단일 스레드 아파트](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다. C + +/WinRT [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic 원격 NuGet 패키지 가져오기

Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
3. 표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.
4. **Holographic** 를 선택 하 **고 최신 2.x** 버전을 선택 하 고 **설치** 를 클릭 합니다.
5. **미리 보기** 대화 상자가 표시 되 면 **확인** 을 클릭 합니다.
6. 표시 되는 다음 대화 상자는 사용권 계약입니다. **동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.
7. 다음 NuGet 패키지에 대해 3 ~ 6 단계를 반복 합니다. OpenXR, OpenXR

>[!NOTE]
>HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다. 자세한 내용은 [Holographic 원격 추가 (HoloLens (첫 번째 gen))](add-holographic-remoting.md)를 참조 하세요.

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Holographic Remoting OpenXR runtime을 선택 합니다.

원격 앱에서 수행 해야 하는 첫 번째 단계는 OpenXr NuGet 패키지의 일부인 Holographic Remoting OpenXR runtime을 선택 하는 것입니다. 이렇게 하려면 ```XR_RUNTIME_JSON``` 환경 변수를 앱 내 파일의 RemotingXR.js경로에 설정 합니다. 이 환경 변수는 OpenXR 로더가 시스템 기본 OpenXR 런타임을 사용 하지 않고 대신 Holographic Remoting OpenXR 런타임으로 리디렉션하는 데 사용 됩니다. Holographic OpenXr NuGet 패키지를 사용 하는 경우 파일에 대 한 RemotingXR.js는 출력 폴더로 컴파일하는 동안 자동으로 복사 되므로 일반적으로 OpenXR 런타임 선택은 다음과 같이 표시 됩니다.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Holographic Remoting 확장을 사용 하 여 XrInstance 만들기

일반적인 OpenXR 앱이 수행 해야 하는 첫 번째 단계는 OpenXR extensions를 선택 하 고 XrInstance를 만드는 것입니다. OpenXR core 사양은 remoting 특정 API를 제공 하지 않습니다. 이러한 이유로 Holographic Remoting은 이라는 고유한 OpenXR 확장을 도입 ```XR_MSFT_holographic_remoting``` 합니다. XrCreateInstance를 호출할 때 ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` XrInstanceCreateInfo에 포함 되어 있는지 확인 합니다.

>[!TIP]
>기본적으로 앱의 렌더링 된 콘텐츠는 HoloLens 2 또는 Windows Mixed Reality 헤드셋에서 실행 되는 Holographic Remoting 플레이어로만 스트리밍됩니다. 또한 원격 PC에서 렌더링 된 콘텐츠를 표시 하기 위해 예를 들어 창의 스왑 체인을 통해 Holographic Remoting은 이라는 두 번째 OpenXR 확장을 제공 ```XR_MSFT_holographic_remoting_frame_mirroring``` 합니다. 해당 기능을 사용 하려는 경우에도를 사용 하 여이 확장을 사용 하도록 설정 해야 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` 합니다.

>[!IMPORTANT]
>Holographic Remoting OpenXR extension API에 대 한 자세한 내용은 [Holographic remoting 샘플 github 리포지토리에서](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)찾을 수 있는 [사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) 확인 하세요.

## <a name="connect-to-the-device"></a>장치에 연결

원격 앱이 XrInstance를 만들고 xrGetSystem을 통해 XrSystemId를 쿼리하면 플레이어 장치에 대 한 연결을 설정할 수 있습니다.

>[!WARNING]
> Holographic Remoting OpenXR 런타임은 연결이 설정 된 후에 보기 구성 또는 환경 blend 모드와 같은 장치별 데이터를 제공할 수 있습니다. ```xrEnumerateViewConfigurations```,,, ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` 및 ```xrGetSystemProperties``` 는 모두 연결 되기 전에 HoloLens 2에서 실행 되는 플레이어에 연결 하는 경우 일반적으로 얻을 수 있는 값과 일치 하는 기본값을 제공 합니다.
연결이 설정 되기 전에는 이러한 메서드를 호출 하지 않는 것이 좋습니다. 이 방법은 XrSession을 성공적으로 만들고 세션 상태가 XR_SESSION_STATE_READY 이상인 경우에 사용 됩니다.

다음을 통해 최대 비트 전송률, 오디오 사용, 비디오 코덱 또는 깊이 버퍼 스트림 확인과 같은 일반 속성을 구성할 수 있습니다 ```xrRemotingSetContextPropertiesMSFT``` .

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

연결은 두 가지 방법 중 하나로 수행할 수 있습니다.
1) 원격 앱은 장치에서 실행 중인 플레이어에 연결 합니다.
2) 장치에서 실행 되는 플레이어가 원격 앱에 연결 합니다.

원격 앱에서 플레이어 장치로의 연결을 설정 하려면 ```xrRemotingConnectMSFT``` 구조를 통해 호스트 이름 및 포트를 지정 하는 메서드를 호출 합니다  ```XrRemotingConnectInfoMSFT``` . Holographic Remoting 플레이어에서 사용 하는 포트는 **8265** 입니다.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

원격 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 호출 하 여 수행할 수 있습니다 ```xrRemotingListenMSFT``` . 핸드셰이크 포트와 전송 포트는 모두 구조를 통해 지정할 수 있습니다 ```XrRemotingListenInfoMSFT``` . 핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다. 그런 다음 데이터는 전송 포트를 통해 전송 됩니다. 기본적으로 **8265** 및 **8266** 이 사용 됩니다.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

또는를 호출할 때 연결 상태를 해제 해야 ```xrRemotingConnectMSFT``` 합니다 ```xrRemotingListenMSFT``` . XrInstance를 만들고를 통해 XrSystemId에 대해 쿼리 한 후 언제 든 지 연결 상태를 가져올 수 있습니다 ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

사용 가능한 연결 상태는 다음과 같습니다.
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```xrCreateSession를 통해 XrSession을 만들기 전에 또는를 호출 해야 합니다. 연결 상태가 인 동안 XrSession을 만들려고 하면 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 세션 생성은 성공 하지만 세션 상태는 즉시 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.

Holographic Remoting의 구현은 ```xrCreateSession``` 연결 설정 대기를 지원 합니다. ```xrRemotingConnectMSFT```를 호출 하거나 ```xrRemotingListenMSFT``` 바로 다음에 호출 하 여 ```xrCreateSession``` 연결이 설정 될 때까지 대기 하는 호출을 수행할 수 있습니다. 제한 시간은 10 초로 고정 됩니다. 이 시간 내에 연결을 설정할 수 있는 경우 XrSession 만들기가 성공 하 고 세션 상태가 XR_SESSION_STATE_READY로 전환 됩니다. 연결을 설정할 수 없는 경우에도 세션 만들기는 성공 하지만 즉시 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.

일반적으로 연결 상태는 XrSession 상태와 두 가지입니다. 연결 상태에 대 한 변경 내용은 세션 상태에도 영향을 줍니다. 예를 들어 연결 상태가에서 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` 로 전환 되 면 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 세션 상태가 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.

## <a name="handling-remoting-specific-events"></a>원격 특정 이벤트 처리

Holographic Remoting OpenXR runtime은 연결 상태를 모니터링 하는 데 중요 한 세 개의 이벤트를 노출 합니다.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: 장치에 대 한 연결이 성공적으로 설정 된 경우에 트리거됩니다.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우에 트리거됩니다.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: 들어오는 연결을 수신 하는 작업이 시작 됩니다.

이러한 이벤트는 큐에 배치 되며 원격 앱은 질서 via를 사용 하 여 큐에서 읽어야 합니다 ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>스트리밍 콘텐츠를 로컬로 미리 봅니다.

장치에 전송 되는 원격 앱에 동일한 콘텐츠를 표시 하려면 ```XR_MSFT_holographic_remoting_frame_mirroring``` 확장을 사용할 수 있습니다. 이 확장을 사용 하면 xrEndFrame에 질감을 제출할 수 있습니다. ```XrRemotingFrameMirrorImageInfoMSFT```다음과 같이 Xr프레임 끝 정보에 연결 되는 구조를 사용 하 여이 작업을 수행 합니다.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

위의 예제에서는 DX11를 사용 하 여 xrEndFrame에 대 한 호출 바로 뒤에 창을 표시 합니다. 사용량은 스왑 체인 질감으로 제한 되지 않으며 추가 GPU 동기화가 필요 하지 않습니다. 사용 및 제약 조건에 대 한 자세한 내용은 [확장 사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)확인 하세요.
원격 앱에서 DX12를 사용 하는 경우 XrRemotingFrameMirrorImageD3D11MSFT 대신 XrRemotingFrameMirrorImageD3D12MSFT를 사용 합니다.

## <a name="see-also"></a>참고 항목
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 원격을 사용하여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)
