---
title: 사용자 지정 Holographic Remoting 플레이어 작성 (c + +)
description: 원격 컴퓨터에 렌더링 된 콘텐츠를 HoloLens 2에 표시 하는 사용자 지정 Hologaphic 원격 응용 프로그램을 만듭니다.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, NuGet, 앱 매니페스트, 플레이어 컨텍스트, 원격 앱, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184734"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>사용자 지정 Holographic 원격 플레이어 앱 작성 (c + +)

>[!IMPORTANT]
>이 문서에서는 HoloLens 2에 대 한 사용자 지정 플레이어 응용 프로그램을 만드는 방법을 설명 합니다. HoloLens 2 용으로 작성 된 사용자 지정 플레이어는 HoloLens 1 용으로 작성 된 원격 응용 프로그램과 호환 되지 않습니다. 이는 두 응용 프로그램이 모두 NuGet **패키지 버전 2.x** 를 사용 해야 함을 의미 합니다.

사용자 지정 Holographic Remoting player 앱을 만들면 HoloLens 2의 원격 컴퓨터에서 [몰입 형 보기](../../design/app-views.md) 를 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다. 이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

Holographic 원격 플레이어를 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: 더 많은 시스템 리소스에 대 한 액세스 권한이 있는 Xbox One)에서 [렌더링](rendering.md) 된 Holographic 콘텐츠를 표시할 수 있습니다. Holographic Remoting player 앱은 입력 데이터를 Holographic Remoting 원격 응용 프로그램으로 스트리밍하 고 비디오 및 오디오 스트림으로 몰입 형 보기를 다시 받습니다. 연결은 표준 Wi-fi를 사용 하 여 수행 됩니다. 플레이어 앱을 만들려면 NuGet 패키지를 사용 하 여 UWP 앱에 Holographic 원격을 추가 합니다. 그런 다음 연결을 처리 하 고 몰입 형 뷰를 표시 하는 코드를 작성 합니다. 

## <a name="prerequisites"></a>필수 구성 요소

좋은 출발점은 이미 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요](../native/directx-development-overview.md)를 참조 하세요. 기존 앱이 없고 처음부터 시작 하려면 [c + + holographic 프로젝트 템플릿이](../native/creating-a-holographic-directx-project.md) 좋은 출발점입니다.

>[!IMPORTANT]
>Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다. [단일 스레드 아파트](/windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다. C + +/WinRT [winrt:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic 원격 NuGet 패키지 가져오기

Visual Studio의 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **관리 NuGet 패키지** ...를 선택 합니다.
3. 표시 되는 패널에서 **찾아보기** 를 선택한 다음 "Holographic Remoting"을 검색 합니다.
4. **Holographic** 를 선택 하 **고 최신 2.x** 버전을 선택 하 고 **설치** 를 선택 합니다.
5. **미리 보기** 대화 상자가 표시 되 면 **확인** 을 선택 합니다.
6. 사용권 계약 대화 상자가 나타나면 **동의** 함을 선택 합니다.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 패키지 내에는 Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서가 포함 되어 있습니다.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>응용 프로그램의 appxmanifest.xml을 수정 합니다.

응용 프로그램이 NuGet 패키지에 의해 추가 된 Microsoft.Holographic.AppRemoting.dll을 인식 하도록 하려면 프로젝트에서 다음 단계를 수행 해야 합니다.

1. 솔루션 탐색기에서 **appxmanifest.xml** 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램 ...을** 선택 합니다.
2. **XML (텍스트) 편집기** 를 선택 하 고 **확인** 을 선택 합니다.
3. 파일에 다음 줄을 추가 하 고 저장 합니다.
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>플레이어 컨텍스트 만들기

첫 번째 단계로 응용 프로그램은 플레이어 컨텍스트를 만들어야 합니다.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic remoting은 Windows의 일부인 Windows Mixed Reality 런타임을 원격 특정 런타임으로 바꿔 작동 합니다. 플레이어 컨텍스트를 만드는 동안이 작업을 수행 합니다. 이러한 이유로 플레이어 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다. 권장 되는 방법은 혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 플레이어 컨텍스트를 만드는 것입니다. 이후에 만들어지거나 검색 된 개체를 사용 하 여를 호출 하기 전에 Windows Mixed Reality API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요 ```PlayerContext::Create``` .

그런 다음 [HolographicSpace. CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)를 호출 하 여 HolographicSpace를 만들 수 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>원격 앱에 커넥트

플레이어 앱이 콘텐츠를 렌더링할 준비가 되 면 원격 앱에 대 한 연결을 설정할 수 있습니다.

다음 방법 중 하나로 연결을 설정할 수 있습니다.
1) HoloLens 2에서 실행 되는 플레이어 앱은 원격 앱에 연결 됩니다.
2) 원격 앱은 HoloLens 2에서 실행 되는 플레이어 앱에 연결 합니다.

플레이어 앱에서 원격 앱으로 연결 하려면 ```Connect``` 호스트 이름 및 포트를 지정 하는 플레이어 컨텍스트의 메서드를 호출 합니다. 기본 포트는 **8265** 입니다.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>모든 c + +/WinRT API와 마찬가지로 처리 해야 하 ```Connect``` 는 WinRT:: hresult_error을 throw 할 수 있습니다.

플레이어 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 호출 하 여 수행할 수 있습니다 ```Listen``` . 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다. 그러면 전송 포트를 통해 데이터가 전송 됩니다. 기본적으로 포트 번호 **8265** 및 **8266** 이 사용 됩니다.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>연결 관련 이벤트 처리

는 ```PlayerContext``` 연결 상태를 모니터링 하는 세 개의 이벤트를 노출 합니다.
1) OnConnected: 원격 앱에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: 설정 된 연결이 종료 되거나 연결을 설정할 수 없는 경우 트리거됩니다.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>가능한 ```ConnectionFailureReason``` 값은 파일에 설명 되어 있습니다 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl).

3) OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

또한 플레이어 컨텍스트의 속성을 사용 하 여 연결 상태를 쿼리할 수 있습니다 ```ConnectionState``` .
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>원격으로 렌더링 된 프레임을 표시 합니다.

원격으로 렌더링 된 콘텐츠를 표시 하려면 ```PlayerContext::BlitRemoteFrame``` [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)를 렌더링 하는 동안를 호출 합니다. 

```BlitRemoteFrame``` 현재 HolographicFrame에 대 한 백 버퍼가 렌더링 대상으로 바인딩되어야 합니다. 백 버퍼는 [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) 속성을 통해 [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) 에서 받을 수 있습니다.

호출 되 면 ```BlitRemoteFrame``` 원격 응용 프로그램에서 수신 된 최신 프레임을 HolographicFrame의 백 버퍼에 복사 합니다. 원격 응용 프로그램에서 원격 프레임을 렌더링 하는 동안 포커스 지점을 지정 하는 경우에도 포커스 지점 집합이 설정 됩니다.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 현재 프레임의 포커스 지점을 덮어쓸 수 있습니다. 
>- 대체 (fallback) 포커스 지점을 지정 하려면 이전에 [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 를 호출 ```PlayerContext::BlitRemoteFrame``` 합니다. 
>- 원격 포커스 지점을 덮어쓰려면 [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  를 호출 ```PlayerContext::BlitRemoteFrame``` 합니다.

성공 하면를 ```BlitRemoteFrame``` 반환 ```BlitResult::Success_Color``` 합니다. 그렇지 않으면 실패 원인을 반환 합니다.
- ```BlitResult::Failed_NoRemoteFrameAvailable```: 사용할 수 있는 원격 프레임이 없기 때문에 실패 했습니다.
- ```BlitResult::Failed_NoCamera```: 카메라가 없어 실패 했습니다.
- ```BlitResult::Failed_RemoteFrameTooOld```: 원격 프레임이 너무 오래 되어 실패 했습니다 (PlayerContext:: BlitRemoteFrameTimeout 속성 참조).

>[!IMPORTANT]
> [2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 사용자 지정 플레이어를 사용 하 여 Holographic 원격을 통해 깊이 재 프로젝션을 사용할 수 있습니다.

```BlitResult``````BlitResult::Success_Color_Depth```는 다음과 같은 경우에도 반환할 수 있습니다.

- 원격 앱이 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋 했습니다.
- 사용자 지정 플레이어 앱은를 호출 하기 전에 유효한 깊이 버퍼를 바인딩 했습니다 ```BlitRemoteFrame``` .

이러한 조건이 충족 되 면 ```BlitRemoteFrame``` 원격 깊이가 현재 바인딩된 로컬 깊이 버퍼로 array.blit 됩니다. 그러면 원격 렌더링 된 콘텐츠와 깊이 교차 하는 추가 로컬 콘텐츠를 렌더링할 수 있습니다. 또한 사용자 지정 플레이어에서 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 를 통해 로컬 수준 버퍼를 커밋하여 원격 및 로컬 렌더링 된 콘텐츠에 대해 깊이 있게 프로젝션 할 수 있습니다. 자세한 내용은 [깊이 Reprojection](hologram-stability.md#reprojection) 을 참조 하세요.

### <a name="projection-transform-mode"></a>프로젝션 변환 모드

한 가지 문제는 Holographic Remoting을 통해 깊이 다시 프로젝션을 사용 하는 경우 사용자 지정 플레이어 앱에서 직접 렌더링 하는 로컬 콘텐츠와 다른 프로젝션 변환을 사용 하 여 원격 콘텐츠를 렌더링할 수 있는 것입니다. 일반적인 사용 사례는 선수 및 원격 측면에서 근거리 및 far 평면 ( [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 및 [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)를 통해)에 대해 서로 다른 값을 지정 하는 것입니다. 이 경우 플레이어 쪽의 프로젝션 변환에 멀리 떨어져 있는 원격 평면 거리 또는 로컬 항목이 반영 되어야 하는지는 명확 하지 않습니다.

버전 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 부터를 통해 프로젝션 변환 모드를 제어할 수 있습니다 ```PlayerContext::ProjectionTransformConfig``` . 지원되는 값은 다음과 같습니다.

- ```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 는 HolographicCamera에서 사용자 지정 플레이어 앱에 의해 설정 된 근거리/원거리 평면 거리를 반영 하는 프로젝션 변환을 반환 합니다.
- ```Remote``` -프로젝션 변환은 원격 앱에서 지정 된 근거리/원거리 평면 거리를 반영 합니다.
- ```Merged``` -원격 앱 및 사용자 지정 플레이어 앱의 근거리/Far 비행기 거리가 병합 됩니다. 기본적으로이 작업은 근거리 평면 거리의 최소 및 최대 평면 거리의 최대값을 차지 하 여 수행 됩니다. 원격 또는 로컬 쪽이 반전 된 경우 (근처 < 멀리 떨어져 있는 경우 멀리 떨어져 있는 근거리/원거리 비행기 거리가 대칭 이동 합니다.

## <a name="optional-set-blitremoteframetimeout"></a>선택 사항: BlitRemoteFrameTimeout 설정 <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` 는 버전 [2.0.9](holographic-remoting-version-history.md#v2.0.9)부터 지원 됩니다. 

```PlayerContext::BlitRemoteFrameTimeout```속성은 새 원격 프레임을 받지 못한 경우 원격 프레임을 다시 사용 하는 시간을 지정 합니다. 

일반적인 사용 사례는 특정 시간 동안 새 프레임을 받지 못한 경우 BlitRemoteFrame 시간 제한을 사용 하 여 빈 화면을 표시 하는 것입니다. 사용 하도록 설정 하면 메서드의 반환 형식을 ```BlitRemoteFrame``` 사용 하 여 로컬로 렌더링 된 대체 콘텐츠로 전환할 수도 있습니다. 

시간 제한을 사용 하도록 설정 하려면 속성 값을 100 밀리초 보다 크거나 같은 기간으로 설정 합니다. 시간 제한을 사용 하지 않도록 설정 하려면 속성을 0 duration으로 설정 합니다. 제한 시간을 설정 하 고 설정 된 기간 동안 원격 프레임을 받지 못한 경우에는 BlitRemoteFrame이 실패 하 고 ```Failed_RemoteFrameTooOld``` 새 원격 프레임을 받을 때까지 반환 됩니다.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>선택 사항: 마지막 원격 프레임에 대 한 통계 가져오기

성능 또는 네트워크 문제를 진단 하려면 속성을 통해 마지막 원격 프레임에 대 한 통계를 검색할 수 있습니다 ```PlayerContext::LastFrameStatistics``` . [HolographicFrame::P resentusingcurrentprediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)를 호출 하는 동안 통계가 업데이트 됩니다.

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

자세한 내용은 ```PlayerFrameStatistics``` 파일의 설명서를 참조 하십시오 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl).

## <a name="optional-custom-data-channels"></a>선택 사항: 사용자 지정 데이터 채널

사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다. 자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목
* [Holographic 원격 기능 개요](holographic-remoting-overview.md)
* [Windows Mixed Reality api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [홀로그램 원격을 사용하여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)