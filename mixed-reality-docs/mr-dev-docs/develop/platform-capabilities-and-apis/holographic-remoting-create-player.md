---
title: 사용자 지정 홀로그램 원격 플레이어 작성
description: 원격 컴퓨터에서 렌더링된 콘텐츠를 HoloLens 2 표시하는 사용자 지정 Hologaphic Remoting 앱을 만듭니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, 원격, 홀로그램 원격, NuGet, 앱 매니페스트, 플레이어 컨텍스트, 원격 앱, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: b395f94f6c98b20f7c0c188f11a718e6da9394de5df3404e7c703558daf526f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190173"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>사용자 지정 홀로그램 원격 플레이어 앱 작성

>[!IMPORTANT]
>이 문서에서는 HoloLens 2 위한 사용자 지정 플레이어 애플리케이션을 만드는 작업을 설명합니다. HoloLens 2 위해 작성된 사용자 지정 플레이어는 HoloLens 1용으로 작성된 원격 애플리케이션과 호환되지 않습니다. 즉, 두 애플리케이션 모두 NuGet 패키지 버전 **2.x.x 를** 사용해야 합니다.

사용자 지정 홀로그램 원격 플레이어 앱을 만들면 HoloLens 2 원격 머신의 [에서 몰입형 보기를](../../design/app-views.md) 표시할 수 있는 사용자 지정 애플리케이션을 만들 수 있습니다. 이 페이지의 모든 코드 및 작업 프로젝트는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

홀로그램 원격 플레이어를 사용하면 앱에서 더 많은 시스템 리소스에 액세스할 수 있는 Xbox One 같은 데스크톱 PC 또는 UWP 디바이스에서 [렌더링된](rendering.md) 홀로그램 콘텐츠를 표시할 수 있습니다. 홀로그램 원격 플레이어 앱은 입력 데이터를 홀로그램 원격 원격 애플리케이션으로 스트리밍하고 몰입형 보기를 비디오 및 오디오 스트림으로 다시 받습니다. 표준 Wi-Fi를 사용하여 연결합니다. 플레이어 앱을 만들려면 NuGet 패키지를 사용하여 Holographic Remoting을 UWP 앱에 추가합니다. 그런 다음, 연결을 처리하고 몰입형 보기를 표시하는 코드를 작성합니다. 

## <a name="prerequisites"></a>필수 조건

좋은 시작점은 이미 Windows Mixed Reality API를 대상으로 하는 작동하는 DirectX 기반 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요를 참조하세요.](../native/directx-development-overview.md) 기존 앱이 없고 처음부터 시작하려는 경우 [C++ 홀로그램 프로젝트 템플릿이](../native/creating-a-holographic-directx-project.md) 좋은 시작점입니다.

>[!IMPORTANT]
>홀로그램 Remoting을 사용하는 모든 앱은 [다중 스레드 아파트](/windows/win32/com/multithreaded-apartments)를 사용하도록 작성되어야 합니다. 단일 스레드 [아파트의](/windows/win32/com/single-threaded-apartments) 사용은 지원되지만 성능이 낮아지고 재생 중에 더듬거릴 수 있습니다. C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 사용하는 경우 다중 스레드 아파트가 기본값입니다.

## <a name="get-the-holographic-remoting-nuget-package"></a>홀로그램 remoting NuGet 패키지 받기

Visual Studio 프로젝트에 NuGet 패키지를 추가하려면 다음 단계가 필요합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...를 선택합니다.**
3. 표시되는 패널에서 **찾아보기를** 선택한 다음, "홀로그램 Remoting"을 검색합니다.
4. **Microsoft.Holographic.Remoting을** 선택하고 최신 **2.x.x** 버전을 선택하고 **설치를** 선택합니다.
5. 미리 **보기** 대화 상자가 나타나면 **확인을** 선택합니다.
6. 사용권 계약 대화 상자가 나타나면 **동의를** 선택합니다.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 패키지 내의 에는 홀로그램 Remoting에서 노출하는 API에 대한 자세한 설명서가 포함되어 있습니다.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>애플리케이션의 Package.appxmanifest 수정

애플리케이션이 NuGet 패키지에서 추가한 Microsoft.Holographic.AppRemoting.dll 인식하도록 하려면 프로젝트에서 다음 단계를 수행해야 합니다.

1. 솔루션 탐색기 **Package.appxmanifest** 파일을 마우스 오른쪽 단추로 클릭하고 **다음으로 열기...를** 선택합니다.
2. **XML(텍스트) 편집기를** 선택하고 **확인을** 선택합니다.
3. 파일에 다음 줄을 추가하고 저장합니다.
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

첫 번째 단계로 애플리케이션은 플레이어 컨텍스트를 만들어야 합니다.

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
>홀로그램 Remoting은 Windows 일부인 Windows Mixed Reality 런타임을 remoting 특정 런타임으로 대체하여 작동합니다. 이 작업은 플레이어 컨텍스트를 만드는 동안 수행됩니다. 따라서 플레이어 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출하면 예기치 않은 동작이 발생할 수 있습니다. Mixed Reality API와 상호 작용하기 전에 최대한 빨리 플레이어 컨텍스트를 만드는 것이 좋습니다. 호출 전에 Windows Mixed Reality API를 통해 ```PlayerContext::Create``` 생성되거나 검색된 개체를 나중에 만들거나 검색된 개체와 혼합하지 마십시오.

다음으로 [HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)를 호출하여 HolographicSpace를 만들 수 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>원격 앱에 커넥트

플레이어 앱이 콘텐츠를 렌더링할 준비가 되면 원격 앱에 대한 연결을 설정할 수 있습니다.

연결은 다음 방법 중 하나로 설정할 수 있습니다.
1) HoloLens 2 실행되는 플레이어 앱이 원격 앱에 연결됩니다.
2) 원격 앱은 HoloLens 2 실행되는 플레이어 앱에 연결합니다.

플레이어 앱에서 원격 앱으로 연결하려면 ```Connect``` 호스트 이름 및 포트를 지정하는 플레이어 컨텍스트에서 메서드를 호출합니다. 기본 포트는 **8265** 입니다.

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
>C++/WinRT API와 마찬가지로 ```Connect``` 처리해야 하는 winrt::hresult_error throw할 수 있습니다.

메서드를 호출하여 플레이어 앱에서 들어오는 연결을 수신 대기할 수 ```Listen``` 있습니다. 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용됩니다. 그런 다음 전송 포트를 통해 데이터가 전송됩니다. 기본적으로 포트 번호 **8265** 및 **8266이** 사용됩니다.

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

는 ```PlayerContext``` 연결 상태를 모니터링하는 세 가지 이벤트를 노출합니다.
1) OnConnected: 원격 앱에 대한 연결이 성공적으로 설정되면 트리거됩니다.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: 설정된 연결이 종료되거나 연결을 설정할 수 없는 경우 트리거됩니다.
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
>가능한 ```ConnectionFailureReason``` 값은 파일에 설명되어 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)있습니다.

3) OnListening: 들어오는 연결을 수신 대기하는 경우 시작됩니다.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

또한 플레이어 컨텍스트에서 속성을 사용하여 연결 상태를 쿼리할 수 ```ConnectionState``` 있습니다.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>원격으로 렌더링된 프레임 표시

원격으로 렌더링된 콘텐츠를 표시하려면 ```PlayerContext::BlitRemoteFrame``` [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)을 렌더링하는 동안 를 호출합니다. 

```BlitRemoteFrame``` 에서는 현재 HolographicFrame에 대한 백 버퍼가 렌더링 대상으로 바인딩되어야 합니다. [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) 속성을 통해 [HolographicCameraRenderingParameters에서](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) 백 버퍼를 받을 수 있습니다.

호출되면 ```BlitRemoteFrame``` 원격 애플리케이션에서 받은 최신 프레임을 HolographicFrame의 BackBuffer로 복사합니다. 또한 원격 애플리케이션이 원격 프레임을 렌더링하는 동안 포커스 지점을 지정한 경우 포커스 지점 집합이 설정됩니다.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 는 현재 프레임의 포커스 지점을 잠재적으로 덮어씁 수 있습니다. 
>- 대체 포커스 지점을 지정하려면 앞에 [HolographicCameraRenderingParameters::SetFocusPoint를](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 호출합니다. 
>- 원격 포커스 지점을 덮어쓰려면 후 [HolographicCameraRenderingParameters::SetFocusPoint를](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 호출합니다.

성공하면 를 ```BlitRemoteFrame``` ```BlitResult::Success_Color``` 반환합니다. 그렇지 않으면 실패 이유를 반환합니다.
- ```BlitResult::Failed_NoRemoteFrameAvailable```: 사용할 수 있는 원격 프레임이 없으므로 실패했습니다.
- ```BlitResult::Failed_NoCamera```: 카메라가 없으므로 실패했습니다.
- ```BlitResult::Failed_RemoteFrameTooOld```: 원격 프레임이 너무 오래되어 실패했습니다(PlayerContext::BlitRemoteFrameTimeout 속성 참조).

>[!IMPORTANT]
> 버전 [2.1.0부터](holographic-remoting-version-history.md#v2.1.0) 사용자 지정 플레이어에서 홀로그램 Remoting을 통해 깊이 다시 프로젝션을 사용할 수 있습니다.

```BlitResult``` 는 다음 조건에서 를 반환할 수도 ```BlitResult::Success_Color_Depth``` 있습니다.

- 원격 앱은 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋했습니다.
- 사용자 지정 플레이어 앱은 를 호출하기 전에 유효한 깊이 버퍼를 ```BlitRemoteFrame``` 바인딩했습니다.

이러한 조건이 ```BlitRemoteFrame``` 충족되면 원격 깊이를 현재 바인딩된 로컬 깊이 버퍼로 전환합니다. 그런 다음 원격 렌더링된 콘텐츠와 깊이가 교차하는 추가 로컬 콘텐츠를 렌더링할 수 있습니다. 또한 사용자 지정 플레이어에서 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer를](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 통해 로컬 깊이 버퍼를 커밋하여 원격 및 로컬 렌더링 콘텐츠에 대한 깊이 다시 프로젝션을 가질 수 있습니다. 자세한 내용은 [깊이 다시 프로젝션을](hologram-stability.md#reprojection) 참조하세요.

### <a name="projection-transform-mode"></a>프로젝션 변환 모드

홀로그램 원격을 통해 깊이 다시 프로젝션을 사용할 때 표면화되는 한 가지 문제는 원격 콘텐츠를 사용자 지정 플레이어 앱에서 직접 렌더링하는 로컬 콘텐츠와 다른 프로젝션 변환으로 렌더링할 수 있다는 것입니다. 일반적인 사용 사례는 플레이어 쪽과 원격 쪽에서 근거리 및 원거리 평면에 대해 서로 다른 값을 지정하는 [것입니다(HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 및 [HolographicCamera::SetFarPlaneDistance를](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)통해). 이 경우 플레이어 쪽의 프로젝션 변환이 원격 근거리/원거리 평면 거리 또는 로컬 거리를 반영해야 하는지 명확하지 않습니다.

버전 [2.1.0부터](holographic-remoting-version-history.md#v2.1.0) 를 통해 프로젝션 변환 모드를 제어할 수 ```PlayerContext::ProjectionTransformConfig``` 있습니다. 지원되는 값은 다음과 같습니다.

- ```Local``` - [HolographicCameraPose::P rojectionTransform은](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) HolographicCamera에서 사용자 지정 플레이어 앱이 설정한 근/원거리 평면 거리를 반영하는 프로젝션 변환을 반환합니다.
- ```Remote``` - 프로젝션 변환은 원격 앱에서 지정한 근거리/원거리 평면 거리를 반영합니다.
- ```Merged``` - 원격 앱 및 사용자 지정 플레이어 앱에서 가까운/먼 평면 거리가 병합됩니다. 기본적으로 이 작업은 가장 가까운 평면 거리와 최대 원거리 거리를 가져와서 수행합니다. 원격 또는 로컬 쪽이 반전되는 경우 멀리 < 가까운 원격/원거리 평면 거리가 대칭 이동됩니다.

## <a name="optional-set-blitremoteframetimeout"></a>선택 사항: BlitRemoteFrameTimeout 설정 <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` 는 버전 [2.0.9부터](holographic-remoting-version-history.md#v2.0.9)지원됩니다. 

```PlayerContext::BlitRemoteFrameTimeout```속성은 새 원격 프레임이 수신되지 않은 경우 원격 프레임을 다시 사용 하는 시간을 지정 합니다. 

일반적인 사용 사례는 특정 시간 동안 새 프레임이 수신되지 않는 경우 BlitRemoteFrame 시간 제한에서 빈 화면을 표시하도록 설정하는 것입니다. 사용 하도록 설정 하면 메서드의 반환 형식을 ```BlitRemoteFrame``` 사용 하 여 로컬로 렌더링 된 대체 콘텐츠로 전환할 수도 있습니다. 

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
* [Windows Mixed Reality api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [홀로그램 원격을 사용하여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)