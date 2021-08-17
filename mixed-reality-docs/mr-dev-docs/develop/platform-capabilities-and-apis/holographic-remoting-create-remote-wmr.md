---
title: WMR(홀로그램 원격 원격 앱) 작성
description: 원격 컴퓨터에서 렌더링된 원격 콘텐츠를 스트리밍하여 HolographicSpace를 사용하여 홀로그램 원격 앱을 HoloLens 2 방법을 알아봅니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184724"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>HolographicSpace API를 사용하여 홀로그램 원격 원격 앱 작성

>[!IMPORTANT]
>이 문서에서는 [HolographicSpace API를](../native/getting-a-holographicspace.md)사용하여 HoloLens 2 위한 원격 애플리케이션을 만드는 작업을 설명합니다. **HoloLens(1세대)용** 원격 애플리케이션은 NuGet 패키지 버전 **1.x.x 를** 사용해야 합니다. 즉, HoloLens 2 위해 작성된 원격 애플리케이션은 HoloLens 1과 호환되지 않으며 그 반대의 경우도 마찬가지입니다. HoloLens 1에 대한 설명서는 [여기에서](add-holographic-remoting.md)찾을 수 있습니다.

홀로그램 원격 앱은 원격으로 렌더링된 콘텐츠를 스트리밍하여 HoloLens 2 몰입형 헤드셋을 Windows Mixed Reality 수 있습니다. 또한 더 많은 시스템 리소스에 액세스하고 원격 [몰입형 보기를](../../design/app-views.md) 기존 데스크톱 PC 소프트웨어에 통합할 수 있습니다. 원격 앱은 HoloLens 2 입력 데이터 스트림을 수신하고, 가상 몰입형 보기에서 콘텐츠를 렌더링하고, 콘텐츠 프레임을 다시 HoloLens 2 스트리밍합니다. 표준 Wi-Fi를 사용하여 연결합니다. 홀로그램 원격은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가됩니다. 연결을 처리하고 몰입형 보기에서 렌더링하는 추가 코드가 필요합니다. 일반적인 Remoting 연결의 대기 시간이 50ms입니다. 플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.

이 페이지의 모든 코드 및 작업 프로젝트는 [홀로그램 Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

좋은 시작점은 [HolographicSpace API](../native/getting-a-holographicspace.md)를 대상으로 하는 작동하는 DirectX 기반 데스크톱 또는 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요를 참조하세요.](../native/directx-development-overview.md) [C++ 홀로그램 프로젝트 템플릿은](../native/creating-a-holographic-directx-project.md) 좋은 시작점입니다.

>[!IMPORTANT]
>홀로그램 Remoting을 사용하는 모든 앱은 [다중 스레드 아파트](/windows/win32/com/multithreaded-apartments)를 사용하도록 작성되어야 합니다. 단일 스레드 [아파트의](/windows/win32/com/single-threaded-apartments) 사용은 지원되지만 최적이 아닌 성능으로 이어지고 재생 중에 더듬거릴 수 있습니다. C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 사용하는 경우 다중 스레드 아파트가 기본값입니다.



## <a name="get-the-holographic-remoting-nuget-package"></a>홀로그램 remoting NuGet 패키지 받기

Visual Studio 프로젝트에 NuGet 패키지를 추가하려면 다음 단계가 필요합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...를 선택합니다.**
3. 표시되는 패널에서 **찾아보기를** 선택한 다음, "홀로그램 Remoting"을 검색합니다.
4. **Microsoft.Holographic.Remoting을** 선택하고, 최신 **2.x.x** 버전을 **선택하고, 설치를** 선택합니다.
5. 미리 **보기** 대화 상자가 나타나면 **확인을** 선택합니다.
6. 사용권 계약 대화 상자가 나타나면 **동의를** 선택합니다.

>[!NOTE]
>NuGet 패키지의 버전 **1.x.x는** HoloLens 1을 대상으로 하려는 개발자가 계속 사용할 수 있습니다. 자세한 내용은 [홀로그램 Remoting 추가(HoloLens(1세대))를 참조하세요.](add-holographic-remoting.md)

## <a name="create-the-remote-context"></a>원격 컨텍스트 만들기

첫 번째 단계로 애플리케이션은 원격 컨텍스트를 만들어야 합니다.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>홀로그램 Remoting은 Windows 일부인 Windows Mixed Reality 런타임을 remoting 특정 런타임으로 대체하여 작동합니다. 이 작업은 원격 컨텍스트를 만드는 동안 수행됩니다. 따라서 원격 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출하면 예기치 않은 동작이 발생할 수 있습니다. 권장되는 방법은 Mixed Reality API와 상호 작용하기 전에 가능한 한 빨리 원격 컨텍스트를 만드는 것입니다. CreateRemoteContext를 호출하기 전에 Windows Mixed Reality API를 통해 생성되거나 검색된 개체를 나중에 만들거나 검색한 개체와 혼합하지 마십시오.

다음으로 홀로그램 공간을 만들어야 합니다. CoreWindow를 지정할 필요는 없습니다. CoreWindow가 없는 데스크톱 앱은 를 전달할 수 ```nullptr``` 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>디바이스에 커넥트

원격 앱이 콘텐츠를 렌더링할 준비가 되면 플레이어 디바이스에 대한 연결을 설정할 수 있습니다.

연결은 두 가지 방법 중 하나로 수행할 수 있습니다.
1) 원격 앱은 디바이스에서 실행 중인 플레이어에 연결합니다.
2) 디바이스에서 실행 중인 플레이어가 원격 앱에 연결됩니다.

원격 앱에서 플레이어 디바이스로 연결을 설정하려면 ```Connect``` 호스트 이름 및 포트를 지정하는 원격 컨텍스트에서 메서드를 호출합니다. 홀로그램 Remoting Player에서 사용하는 포트는 **8265입니다.**

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>C++/WinRT API와 마찬가지로 ```Connect``` 처리해야 하는 winrt::hresult_error throw할 수 있습니다.

>[!TIP]
>[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) 언어 프로젝션을 사용하지 않으려면 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` Holographic Remoting NuGet 패키지 내에 있는 파일을 포함할 수 있습니다. 기본 COM 인터페이스의 선언을 포함합니다. 그러나 C++/WinRT를 사용하는 것이 좋습니다.

메서드를 호출하여 원격 앱에서 들어오는 연결을 수신 대기할 수 ```Listen``` 있습니다. 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용됩니다. 그런 다음 전송 포트를 통해 데이터가 전송됩니다. 기본적으로 **8265** 및 **8266이** 사용됩니다.

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 패키지 내의 에는 홀로그램 Remoting에서 노출하는 API에 대한 자세한 설명서가 포함되어 있습니다.

## <a name="handling-remoting-specific-events"></a>Remoting 특정 이벤트 처리

원격 컨텍스트는 연결 상태를 모니터링하는 데 중요한 세 가지 이벤트를 노출합니다.
1) OnConnected: 디바이스에 대한 연결이 성공적으로 설정되면 트리거됩니다.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: 설정된 연결이 닫히거나 연결을 설정할 수 없는 경우 트리거됩니다.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening: 들어오는 연결을 수신 대기하는 경우 시작됩니다.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

또한 원격 컨텍스트에서 속성을 사용하여 연결 상태를 쿼리할 수 ```ConnectionState``` 있습니다.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>음성 이벤트 처리

원격 음성 인터페이스를 사용하면 HoloLens 2 음성 트리거를 등록하고 원격 애플리케이션에 원격으로 사용할 수 있습니다.

이 추가 멤버는 원격 음성의 상태를 추적하는 데 필요합니다.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

먼저 원격 음성 인터페이스를 검색해야 합니다.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

비동기 도우미 메서드를 사용하여 원격 음성을 초기화할 수 있습니다. 초기화하는 데 상당한 시간이 걸릴 수 있기 때문에 비동기적으로 이 작업을 수행해야 합니다. [C++/WinRT를 이용한 동시성 및 비동기 작업은 C++/WinRT를](/windows/uwp/cpp-and-winrt-apis/concurrency) 사용하여 비동기 함수를 제작하는 방법을 설명합니다.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

인식할 구를 지정하는 방법에는 두 가지가 있습니다.
1) 음성 문법 xml 파일 내의 사양입니다. 자세한 내용은 [기본 XML 문법을 만드는 방법을](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 참조하세요.
2) 사전 벡터 내에 를 전달하여 를 ```ApplyParameters``` 지정합니다.

OnRecognizedSpeech 콜백 내에서 음성 이벤트를 처리할 수 있습니다.

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>로컬로 스트리밍된 콘텐츠 미리 보기

디바이스로 전송되는 원격 앱에서 동일한 콘텐츠를 표시하려면 ```OnSendFrame``` 원격 컨텍스트의 이벤트를 사용할 수 있습니다. 이 ```OnSendFrame``` 이벤트는 홀로그램 원격 라이브러리가 현재 프레임을 원격 디바이스로 보낼 때마다 트리거됩니다. 콘텐츠를 데스크톱 또는 UWP 창으로 전환할 수 있는 이상적인 시간입니다.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>깊이 다시 프로젝션

버전 [2.1.0부터](holographic-remoting-version-history.md#v2.1.0)홀로그램 Remoting은 [깊이 다시 프로젝션](hologram-stability.md#reprojection)을 지원합니다. 이렇게 하려면 원격 애플리케이션에서 HoloLens 2 색 버퍼와 깊이 버퍼를 모두 스트리밍해야 합니다. 기본적으로 깊이 버퍼 스트리밍은 색 버퍼 해상도의 절반을 사용하도록 설정되고 구성됩니다. 이 변경은 다음과 같이 변경할 수 있습니다.

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

HoloLens 2 연결을 설정하기 전에 기본값을 사용하지 않아야 하는 경우 를 ```ConfigureDepthVideoStream``` 호출해야 합니다. 가장 좋은 위치는 원격 컨텍스트를 만든 직후입니다. DepthBufferStreamResolution에 사용할 수 있는 값은 다음과 같습니다.

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* 사용 안 함(버전 [2.1.3으로](holographic-remoting-version-history.md#v2.1.3) 추가되고, 사용되는 경우 추가 깊이 비디오 스트림이 생성되지 않습니다.)

전체 해상도 깊이 버퍼를 사용하면 대역폭 요구 사항에도 영향을 미치며 에 제공하는 최대 대역폭 값에서 를 고려해야 ```CreateRemoteContext``` 합니다.

해상도를 구성하는 것 외에도 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋해야 합니다.

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

깊이 다시 프로젝션이 HoloLens 2 올바르게 작동하는지 확인하려면 장치 포털 통해 깊이 시각화 도우미를 사용하도록 설정할 수 있습니다. 자세한 내용은 [깊이 확인이 올바르게 설정되었는지](hologram-stability.md#verifying-depth-is-set-correctly) 확인 을 참조하세요.

## <a name="optional-custom-data-channels"></a>선택 사항: 사용자 지정 데이터 채널

사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다. 자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목
* [Holographic 원격 기능 개요](holographic-remoting-overview.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [사용자 지정 홀로그램 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [홀로그램 원격을 사용하여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)