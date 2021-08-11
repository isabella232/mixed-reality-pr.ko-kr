---
title: 홀로그램 Remoting 추가
description: 홀로그램 Remoting을 설치, 구성 및 사용하여 네트워크를 통해 홀로그램을 HoloLens 디바이스에 렌더링하는 방법을 알아봅니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, 홀로그램, 홀로그램 원격, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 홀로그램, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: ecfc49477e202b08303160e54ce986577a9d79eb387dc1edb1bc33c63644615f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198859"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>홀로그램 Remoting 추가(HoloLens(1세대)

>[!IMPORTANT]
> 이 문서에서는 HoloLens 1용 호스트 애플리케이션을 만드는 작업을 설명합니다. **HoloLens(1세대)용** 호스트 애플리케이션은 NuGet 패키지 버전 **1.x.x 를** 사용해야 합니다. 즉, HoloLens 1용으로 작성된 호스트 애플리케이션은 HoloLens 2 호환되지 않으며 그 반대의 경우도 마찬가지입니다.

## <a name="hololens-2"></a>HoloLens 2

holographic Remoting을 사용하는 HoloLens 개발자는 HoloLens 2 호환되도록 앱을 업데이트해야 합니다. 이렇게 하려면 Holographic Remoting NuGet 패키지의 새 버전이 필요합니다. HoloLens 2 Holographic Remoting Player에 연결할 때 Holographic Remoting NuGet 패키지 버전 2.0.0.0 이상을 사용해야 합니다. 그렇지 않을 경우 연결이 실패합니다.

>[!NOTE]
> HoloLens 2 관련 지침은 [여기에서](holographic-remoting-create-remote-wmr.md)찾을 수 있습니다.


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>데스크톱 또는 UWP 앱에 홀로그램 원격 추가

이 페이지에서는 데스크톱 또는 UWP 앱에 홀로그램 원격을 추가하는 방법을 설명합니다.

홀로그램 원격을 사용하면 앱이 데스크톱 PC 또는 UWP 디바이스(예: Xbox One)에서 호스팅되는 홀로그램 콘텐츠가 있는 HoloLens 대상으로 지정할 수 있습니다. 또한 더 많은 시스템 리소스에 액세스할 수 있어 원격 [몰입형 보기를](../../design/app-views.md) 기존 데스크톱 PC 소프트웨어에 통합할 수 있습니다. remoting 호스트 앱은 HoloLens 입력 데이터 스트림을 수신하고, 가상 몰입형 보기에서 콘텐츠를 렌더링하고, 콘텐츠 프레임을 다시 HoloLens 스트리밍합니다. 표준 Wi-Fi를 사용하여 연결합니다. 원격을 사용하려면 NuGet 패키지를 사용하여 데스크톱 또는 UWP 앱에 홀로그램 원격을 추가한 다음, 연결을 처리하고 몰입형 보기를 렌더링하는 코드를 작성합니다. 도우미 라이브러리는 디바이스 연결 처리 작업을 간소화하는 코드 샘플에 포함되어 있습니다.

일반적인 Remoting 연결의 대기 시간이 50ms입니다. 플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 C++ 홀로그램 프로젝트 템플릿 에서 사용되는 C++17 규격 C++/WinRT 대신 [C++/CX를](../native/creating-a-holographic-directx-project.md)사용하는 것을 보여줍니다.  개념은 C++/WinRT 프로젝트에 해당하지만 코드를 번역해야 합니다.

### <a name="get-the-remoting-nuget-packages"></a>remoting NuGet 패키지 받기

다음 단계에 따라 홀로그램 remoting을 위한 NuGet 패키지를 얻고 프로젝트에서 참조를 추가합니다.
1. Visual Studio 프로젝트로 이동합니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...를 선택합니다.**
3. 표시되는 패널에서 **찾아보기를** 선택하고 "홀로그램 Remoting"을 검색합니다.
4. **Microsoft.Holographic.Remoting을** 선택하고 **설치를** 선택합니다.
5. 미리 **보기** 대화 상자가 나타나면 **확인을** 선택합니다.
6. 사용권 계약 대화 상자가 나타나면 **동의를** 선택합니다.

### <a name="create-the-holographicstreamerhelpers"></a>HolographicStreamerHelpers 만들기

먼저, Remoting을 처리할 클래스에 HolographicStreamerHelpers 인스턴스를 추가해야 합니다.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

연결 상태도 추적해야 합니다. 미리 보기를 렌더링하려면 복사할 질감이 있어야 합니다. 또한 연결 상태 잠금, HoloLens IP 주소를 저장하는 방법 등과 같은 몇 가지 사항이 필요합니다.

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HolographicStreamerHelpers를 초기화하고 HoloLens

HoloLens 디바이스에 연결하려면 HolographicStreamerHelpers의 인스턴스를 만들고 대상 IP 주소에 연결합니다. Holographic Remoting 라이브러리에는 인코더 및 디코더 해상도가 정확하게 일치해야 하므로 비디오 프레임 크기를 HoloLens 표시 너비 및 높이와 일치하도록 설정해야 합니다.

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

디바이스 연결은 비동기입니다. 앱은 연결, 연결 끊기 및 프레임 전송 이벤트에 대한 이벤트 처리기를 제공해야 합니다.

OnConnected 이벤트는 UI를 업데이트하고 렌더링을 시작할 수 있습니다. 데스크톱 코드 샘플에서는 창 제목을 "연결된" 메시지로 업데이트합니다.

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 이벤트는 다시 연결, UI 업데이트 등을 처리할 수 있습니다. 이 예제에서는 일시적인 오류가 있는 경우 다시 연결합니다.

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Remoting 구성 요소가 프레임을 보낼 준비가 되면 SendFrameEvent에서 복사본을 만들 수 있는 기회가 앱에 제공됩니다. 여기서는 미리 보기 창에 표시할 수 있도록 프레임을 스왑 체인에 복사합니다.

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>홀로그램 콘텐츠 렌더링

원격을 사용하여 콘텐츠를 렌더링하려면 데스크톱 또는 UWP 앱 내에서 가상 IFrameworkView를 설정하고 원격에서 홀로그램 프레임을 처리합니다. 모든 Windows Holographic API는 이 보기에서 동일한 방식으로 사용되지만 약간 다르게 설정됩니다.

홀로그램 공간 및 음성 구성 요소는 직접 만드는 대신 HolographicRemotingHelpers 클래스에서 제공됩니다.

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Run 메서드에서 업데이트 루프를 사용하는 대신 데스크톱 또는 UWP 앱의 주 루프에서 틱 업데이트를 제공합니다. 이렇게 하면 데스크톱 또는 UWP 앱이 메시지 처리를 제어할 수 있습니다.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

홀로그램 앱 보기의 Tick() 메서드는 업데이트, 그리기, 현재 루프의 반복 하나를 완료합니다.

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

홀로그램 앱 보기 업데이트, 렌더링 및 현재 루프는 데스크톱 PC에서 훨씬 더 많은 양의 시스템 리소스에 액세스할 수 있다는 점을 제외하고 HoloLens 실행할 때와 정확히 동일합니다. 더 많은 삼각형을 렌더링하고, 더 많은 그리기 패스가 있고, 더 많은 물리학을 수행하며, x64 프로세스를 사용하여 2GB 이상의 RAM이 필요한 콘텐츠를 로드할 수 있습니다.

### <a name="disconnect-and-end-the-remote-session"></a>원격 세션 연결 끊기 및 종료

연결을 끊려면(예: 사용자가 UI 단추를 클릭하여 연결을 끊을 때) HolographicStreamerHelpers에서 Disconnect()를 호출한 다음 개체를 해제합니다.

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Remoting 플레이어 얻기

Windows Holographic remoting player는 Windows 앱 스토어에서 연결할 호스트 앱을 위한 엔드포인트로 제공됩니다. Windows 홀로그램 Remoting 플레이어를 얻으려면 HoloLens Windows 앱 스토어를 방문하여 Remoting을 검색하고 앱을 다운로드합니다. Remoting 플레이어에는 화면에 통계를 표시하는 기능이 포함되어 있으며, 이 기능은 Remoting 호스트 앱을 디버그할 때 유용할 수 있습니다.

## <a name="notes-and-resources"></a>참고 및 리소스

홀로그램 앱 보기에는 홀로그램 공간을 초기화하는 데 사용해야 하는 Direct3D 디바이스를 앱에 제공하는 방법이 필요합니다. 앱은 이 Direct3D 디바이스를 사용하여 미리 보기 프레임을 복사하고 표시해야 합니다.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**코드 샘플:** 데스크톱 Win32, UWP DirectX 및 XAML을 사용하여 UWP에 대한 원격 및 원격 호스트 프로젝트와 호환되는 홀로그램 애플리케이션 보기를 포함하는 전체 [홀로그램](https://github.com/Microsoft/HoloLensCompanionKit) 원격 코드 샘플을 사용할 수 있습니다. 

**디버깅 참고 사항:** 홀로그램 Remoting 라이브러리는 첫째 예외를 throw할 수 있습니다. 이러한 예외는 당시 활성 상태인 Visual Studio 예외 설정에 따라 디버깅 세션에서 표시될 수 있습니다. 이러한 예외는 홀로그램 Remoting 라이브러리에 의해 내부적으로 포착되며 무시될 수 있습니다.
