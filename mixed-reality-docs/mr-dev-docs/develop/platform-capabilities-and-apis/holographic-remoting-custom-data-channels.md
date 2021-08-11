---
title: 사용자 지정 홀로그램 원격 데이터 채널
description: 사용자 지정 데이터 채널을 사용하여 이미 설정된 홀로그램 Remoting 연결을 통해 사용자 데이터를 보낼 수 있습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, 홀로그램 Remoting, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 데이터 채널
ms.openlocfilehash: 09fea161f9042d7afc59c16d3b5e8a6c69892e84b1de5e9ab4a4808733b4f171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217089"
---
# <a name="custom-holographic-remoting-data-channels"></a>사용자 지정 홀로그램 원격 데이터 채널

>[!NOTE]
>이 지침은 HoloLens 2 Holographic Remoting과 관련이 있습니다.

사용자 지정 데이터 채널을 사용하여 설정된 Remoting 연결을 통해 사용자 지정 데이터를 보냅니다.

>[!IMPORTANT]
>사용자 지정 데이터 채널은 두 사용자 지정 앱 간의 통신을 허용하므로 사용자 지정 원격 앱과 사용자 지정 플레이어 앱이 필요합니다.

>[!TIP]
>간단한 ping-pong 예제는 홀로그램 원격 샘플 [github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)내의 원격 및 플레이어 샘플에서 찾을 수 있습니다. ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```샘플 코드를 사용하도록 설정하려면 SampleRemoteMain.h/ SamplePlayerMain.h 파일 내에서 압축을 풀 수 있습니다.


## <a name="create-a-custom-data-channel"></a>사용자 지정 데이터 채널 만들기


사용자 지정 데이터 채널을 만들려면 다음 필드가 필요합니다.
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

연결이 성공적으로 설정되면 원격 쪽, 플레이어 쪽 또는 둘 다에서 새 데이터 채널을 만들 수 있습니다. RemoteContext와 PlayerContext는 모두 ```CreateDataChannel()``` 데이터 채널을 만들기 위한 메서드를 제공합니다. 첫 번째 매개 변수는 후속 작업에서 데이터 채널을 식별하는 데 사용되는 채널 ID입니다. 두 번째 매개 변수는 우선 순위이며, 이 채널의 데이터가 다른 쪽으로 전송되는 우선 순위를 지정합니다. 원격 쪽의 유효한 채널 ID는 0부터 63까지, 플레이어 쪽의 경우 127개까지 64개까지 포함됩니다. 유효한 우선 순위는 ```Low``` ```Medium``` , 또는 ```High``` (양쪽 모두)입니다.

**원격** 쪽에서 데이터 채널 만들기를 시작하려면 다음을 수행합니다.
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

**플레이어** 쪽에서 데이터 채널 만들기를 시작하려면 다음을 수행합니다.
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>새 사용자 지정 데이터 채널을 만들려면 한 쪽(원격 또는 플레이어)만 메서드를 호출해야 ```CreateDataChannel``` 합니다.

## <a name="handling-custom-data-channel-events"></a>사용자 지정 데이터 채널 이벤트 처리

사용자 지정 데이터 채널을 설정하려면 ```OnDataChannelCreated``` 플레이어와 원격 쪽 모두에서 이벤트를 처리해야 합니다. 두 쪽에서 사용자 데이터 채널을 만들 때 트리거되고 ```IDataChannel``` 이 채널을 통해 데이터를 보내고 받는 데 사용할 수 있는 개체를 제공합니다.

이벤트에 수신기를 등록하려면 ```OnDataChannelCreated``` 다음을 수행합니다.
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

데이터를 받을 때 알림을 받으려면 ```OnDataReceived``` ```IDataChannel``` 처리기에서 제공하는 개체의 이벤트에 ```OnDataChannelCreated``` 등록합니다. ```OnClosed```이벤트에 등록하여 데이터 채널이 닫혔을 때 알림을 받습니다.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>데이터 전송

사용자 지정 데이터 채널을 통해 데이터를 보내려면 ```IDataChannel::SendData()``` 메서드를 사용합니다. 첫 번째 매개 변수는 ```winrt::array_view<const uint8_t>``` 전송해야 하는 데이터에 대한 입니다. 두 번째 매개 변수는 다른 쪽에서 수신을 승인할 때까지 데이터를 다시 전송할 위치를 지정합니다. 

>[!IMPORTANT]
>네트워크 상태가 잘못된 경우 동일한 데이터 패킷이 두 번 이상 도착할 수 있습니다. 수신 코드는 이 상황을 처리할 수 있어야 합니다.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>사용자 지정 데이터 채널 닫기

사용자 지정 데이터 채널을 닫려면 ```IDataChannel::Close()``` 메서드를 사용합니다. ```OnClosed```사용자 지정 데이터 채널이 닫히면 양쪽 모두 이벤트에 의해 알림이 전송됩니다.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>참고 항목
* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 Remoting 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)