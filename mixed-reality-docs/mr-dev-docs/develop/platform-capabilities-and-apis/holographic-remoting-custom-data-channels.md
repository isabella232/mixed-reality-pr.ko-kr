---
title: 사용자 지정 홀로그램 원격 데이터 채널
description: 사용자 지정 데이터 채널은 이미 설정 된 Holographic 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 데이터 채널
ms.openlocfilehash: a11fe0bb023ae34692015585f6e1689db4330ac7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582614"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="cacb3-104">사용자 지정 홀로그램 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="cacb3-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="cacb3-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="cacb3-106">사용자 지정 데이터 채널을 사용 하 여 설정 된 원격 연결을 통해 사용자 지정 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="cacb3-107">사용자 지정 데이터 채널에는 두 사용자 지정 앱 간의 통신을 허용 하므로 사용자 지정 원격 앱 및 사용자 지정 플레이어 앱이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="cacb3-108">간단한 ping-ping 예제는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)내부의 원격 및 플레이어 샘플에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="cacb3-109">```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```샘플 코드를 사용 하도록 설정 하려면 SampleRemoteMain/SamplePlayerMain 파일 내에서 주석 처리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="cacb3-110">사용자 지정 데이터 채널 만들기</span><span class="sxs-lookup"><span data-stu-id="cacb3-110">Create a custom data channel</span></span>


<span data-ttu-id="cacb3-111">사용자 지정 데이터 채널을 만들려면 다음 필드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="cacb3-112">연결이 성공적으로 설정 되 면 원격 측, 플레이어 측 또는 둘 다에서 새 데이터 채널을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-112">After a connection is successfully established, you can create new data channels from either the remote side, the player side, or both.</span></span> <span data-ttu-id="cacb3-113">RemoteContext 및 PlayerContext 모두 ```CreateDataChannel()``` 데이터 채널을 만들기 위한 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method for creating data channels.</span></span> <span data-ttu-id="cacb3-114">첫 번째 매개 변수는 후속 작업에서 데이터 채널을 식별 하는 데 사용 되는 채널 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-114">The first parameter is the channel ID, which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="cacb3-115">두 번째 매개 변수는이 채널의 데이터가 다른 쪽으로 전송 되는 우선 순위를 지정 하는 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-115">The second parameter is the priority, which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="cacb3-116">원격 측의 유효한 채널 Id는 0에서 63까지, 64은 플레이어 쪽에 대 한 127을 포함 하는 0부터까지입니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-116">Valid channel IDs on the remote side are from 0 up to and including 63, and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="cacb3-117">유효한 우선 순위는 ```Low``` , ```Medium``` 또는 ```High``` (양쪽 모두)입니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-117">Valid priorities are ```Low```, ```Medium```, or ```High``` (on both sides).</span></span>

<span data-ttu-id="cacb3-118">**원격** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-118">To start the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="cacb3-119">**플레이어** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-119">To start the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="cacb3-120">새 사용자 지정 데이터 채널을 만들려면 한 쪽 (원격 또는 플레이어)만 메서드를 호출 해야 ```CreateDataChannel``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="cacb3-121">사용자 지정 데이터 채널 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="cacb3-121">Handling custom data channel events</span></span>

<span data-ttu-id="cacb3-122">사용자 지정 데이터 채널을 설정 하려면 이벤트를 처리 해야 합니다 ```OnDataChannelCreated``` (플레이어와 원격 측 모두).</span><span class="sxs-lookup"><span data-stu-id="cacb3-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="cacb3-123">한쪽에서 사용자 데이터 채널을 만들고 ```IDataChannel``` 이 채널을 통해 데이터를 보내고 받는 데 사용할 수 있는 개체를 제공 하는 경우 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="cacb3-124">이벤트에 수신기를 등록 하려면 ```OnDataChannelCreated``` :</span><span class="sxs-lookup"><span data-stu-id="cacb3-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="cacb3-125">데이터가 수신 될 때 알림 메시지를 받으려면 ```OnDataReceived``` 처리기에서 제공 하는 개체의 이벤트에 등록 합니다 ```IDataChannel``` ```OnDataChannelCreated``` .</span><span class="sxs-lookup"><span data-stu-id="cacb3-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="cacb3-126">```OnClosed```데이터 채널이 닫히면 이벤트에 등록 하 여 알림 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="cacb3-127">데이터 전송</span><span class="sxs-lookup"><span data-stu-id="cacb3-127">Sending data</span></span>

<span data-ttu-id="cacb3-128">사용자 지정 데이터 채널을 통해 데이터를 전송 하려면 메서드를 사용 ```IDataChannel::SendData()``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="cacb3-129">첫 번째 매개 변수는 ```winrt::array_view<const uint8_t>``` 보내야 하는 데이터에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="cacb3-130">두 번째 매개 변수는 다른 쪽에서 수신을 승인할 때까지 데이터를 다시 보내야 하는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="cacb3-131">네트워크 상태가 잘못 된 경우 동일한 데이터 패킷이 두 번 이상 도착할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="cacb3-132">수신 코드에서이 상황을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="cacb3-133">사용자 지정 데이터 채널 닫기</span><span class="sxs-lookup"><span data-stu-id="cacb3-133">Closing a custom data channel</span></span>

<span data-ttu-id="cacb3-134">사용자 지정 데이터 채널을 닫으려면 메서드를 사용 ```IDataChannel::Close()``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cacb3-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="cacb3-135">사용자 지정 데이터 채널이 닫히면 두 쪽 모두 이벤트에서 알림이 표시 됩니다 ```OnClosed``` .</span><span class="sxs-lookup"><span data-stu-id="cacb3-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="cacb3-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cacb3-136">See Also</span></span>
* [<span data-ttu-id="cacb3-137">Windows Mixed Reality Api를 사용 하 여 Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="cacb3-137">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="cacb3-138">OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="cacb3-138">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="cacb3-139">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="cacb3-139">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="cacb3-140">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="cacb3-140">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="cacb3-141">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="cacb3-141">Holographic Remoting software license terms</span></span>](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="cacb3-142">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="cacb3-142">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)