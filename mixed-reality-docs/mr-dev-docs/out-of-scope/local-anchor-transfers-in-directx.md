---
title: DirectX의 로컬 앵커 전송
description: 공간 앵커를 전송, 내보내기 및 직렬화하여 두 HoloLens 디바이스를 동기화하는 방법을 알아봅니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 멀티 플레이, 보기, 시나리오, 연습, 샘플 코드, 전송, 로컬 앵커 전송, 앵커 내보내기, 앵커 가져오기
ms.openlocfilehash: df00e323267aa398ba45cfd7a7234c04ce8eca85f2ff3be9b6c9ddee67264085
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195670"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX의 로컬 앵커 전송

<a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>사용할 수 없는 경우 로컬 앵커 전송을 사용하면 하나의 HoloLens 디바이스에서 두 번째 HoloLens 디바이스에서 앵커를 가져올 수 있습니다.

>[!NOTE]
>로컬 앵커 전송은 <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>보다 덜 강력한 앵커 회수를 제공하며, iOS 및 Android 디바이스는 이 접근 방식에서 지원되지 않습니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 C++ 홀로그램 프로젝트 템플릿 에서 사용되는 C++17 규격 C++/WinRT 대신 [C++/CX를](../develop/native/creating-a-holographic-directx-project.md)사용하는 것을 보여줍니다.  개념은 C++/WinRT 프로젝트에 해당하지만 코드를 번역해야 합니다.

## <a name="transferring-spatial-anchors"></a>공간 앵커 전송

[SpatialAnchorTransferManager](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager)를 사용하여 Windows Mixed Reality 디바이스 간에 공간 앵커를 전송할 수 있습니다. 이 API를 사용하면 전 세계에서 정확한 위치를 찾는 데 필요한 모든 지원 센서 데이터와 앵커를 번들로 묶은 다음, 다른 디바이스에서 해당 번들을 가져올 수 있습니다. 두 번째 디바이스의 앱이 해당 앵커를 가져오면 각 앱은 해당 공유 공간 앵커의 좌표계를 사용하여 홀로그램을 렌더링할 수 있습니다. 그러면 실제 세계의 동일한 위치에 표시됩니다.

공간 앵커는 서로 다른 디바이스 유형 간에 전송할 수 없습니다. 예를 들어 몰입형 헤드셋을 사용하여 HoloLens 공간 앵커를 찾지 못할 수 있습니다.  전송된 앵커도 iOS 또는 Android 디바이스와 호환되지 않습니다.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>spatialPerception 기능을 사용하도록 앱 설정

[SpatialAnchorTransferManager](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager)을 사용하려면 먼저 SpatialPerception 기능을 사용할 수 있는 권한이 앱에 부여되어야 합니다. 공간 앵커 전송에는 시간이 지남에 따라 수집된 센서 이미지가 중요한 정보를 포함할 수 있는 해당 앵커 주변을 공유해야 하므로 이 작업이 필요합니다.

앱의 package.appxmanifest 파일에서 이 기능을 선언합니다. 예는 다음과 같습니다.

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

이 기능은 **uap2** 네임스페이스에서 제공됩니다. 매니페스트에서 이 네임스페이스에 액세스하려면 Package> 요소에 *xlmns* 특성으로 &lt; 포함합니다. 예는 다음과 같습니다.

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**참고:** 앱이 SpatialAnchor 내보내기/가져오기 API에 액세스하려면 런타임에 기능을 요청해야 합니다. 아래 예제에서는 [RequestAccessAsync를](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) 참조하세요.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager를 통해 앵커 데이터를 내보내서 직렬화합니다.

도우미 함수는 [SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 데이터를 내보내기(직렬화)하는 코드 샘플에 포함되어 있습니다. 이 내보내기 API는 문자열을 앵커와 연결한 키-값 쌍 컬렉션의 모든 앵커를 직렬화합니다.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

먼저 데이터 스트림을 설정해야 합니다. 이렇게 하면 1이 허용됩니다.) TryExportAnchorsAsync를 사용하여 앱이 소유한 버퍼에 데이터를 배치하고 2를 사용합니다. 내보낸 바이트 버퍼 스트림(WinRT 데이터 스트림)에서 std::vector 바이트> 고유한 메모리 버퍼로 데이터를 &lt; 읽습니다.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

시스템에서 내보낸 앵커를 포함하여 공간 데이터에 액세스할 수 있는 권한을 요청해야 합니다.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

권한을 얻고 앵커를 내보내면 데이터 스트림을 읽을 수 있습니다. 여기서는 데이터를 읽는 데 사용할 DataReader 및 InputStream을 만드는 방법도 보여줍니다.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

스트림에서 바이트를 읽은 후에는 마찬가지로 자체 데이터 버퍼에 저장할 수 있습니다.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager를 사용하여 시스템에 앵커 데이터를 가져와서 앵커 데이터를 deserialize합니다.

도우미 함수는 코드 샘플에 포함되어 이전에 내보낸 데이터를 로드합니다. 이 deserialization 함수는 SpatialAnchorStore가 제공하는 것과 유사한 키-값 쌍의 컬렉션을 제공합니다. 단, 네트워크 소켓과 같은 다른 원본에서 이 데이터를 얻은 것입니다. 오프라인으로 저장하거나, 앱 내 메모리를 사용하거나(해당하는 경우) 앱의 SpatialAnchorStore를 사용하여 데이터를 저장하기 전에 이 데이터를 처리하고 추론할 수 있습니다.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

먼저 앵커 데이터에 액세스하기 위해 스트림 개체를 만들어야 합니다. 버퍼의 데이터를 시스템 버퍼에 쓰므로 바이트 버퍼에서 SpatialAnchors로 시스템으로 앵커를 얻는 목표를 달성하기 위해 메모리 내 데이터 스트림에 쓰는 DataWriter를 만듭니다.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

다시 한 번, 사용자 환경에 대한 개인 정보를 포함할 수 있는 공간 앵커 데이터를 내보낼 수 있는 권한이 앱에 있는지 확인해야 합니다.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

액세스가 허용되면 버퍼에서 시스템 데이터 스트림으로 바이트를 쓸 수 있습니다.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

데이터 스트림에 바이트를 성공적으로 저장한 경우 SpatialAnchorTransferManager를 사용하여 해당 데이터를 가져올 수 있습니다.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

데이터를 가져올 수 있는 경우 문자열을 앵커와 연결한 키-값 쌍의 맵 보기를 가져옵니다. 이를 메모리 내 데이터 컬렉션에 로드하고 해당 컬렉션을 사용하여 사용하려는 앵커를 찾을 수 있습니다.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**참고:** 앵커를 가져올 수 있다고 해서 반드시 즉시 사용할 수 있는 것은 아닙니다. 앵커는 다른 방이나 다른 물리적 위치에 있을 수 있습니다. 앵커를 받은 디바이스에 앵커가 만들어진 환경에 대한 시각적 정보가 충분하여 알려진 현재 환경에 상대적으로 앵커의 위치를 복원할 때까지 앵커를 배치할 수 없습니다. 클라이언트 구현은 라이브 콘텐츠에 계속 사용하기 전에 로컬 좌표계 또는 참조 프레임을 기준으로 앵커를 찾아야 합니다. 예를 들어 앵커를 찾기 시작할 때까지 현재 좌표계를 기준으로 앵커를 주기적으로 찾습니다.

## <a name="special-considerations"></a>특별 고려 사항

[TryExportAnchorsAsync](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) API를 사용하면 여러 [SpatialAnchors를](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 동일한 불투명 이진 Blob으로 내보낼 수 있습니다. 그러나 단일 SpatialAnchor 또는 여러 SpatialAnchor를 단일 호출로 내보낼지 여부에 따라 Blob에 포함될 데이터에는 미묘한 차이가 있습니다.

### <a name="export-of-a-single-spatialanchor"></a>단일 SpatialAnchor 내보내기

Blob에는 SpatialAnchor를 가져오는 디바이스에서 환경을 인식할 수 있도록 SpatialAnchor 주변 환경의 표현이 포함됩니다. 가져오기가 완료되면 디바이스에서 새 SpatialAnchor를 사용할 수 있습니다. 사용자가 최근에 앵커 근처에 있다고 가정하면 해당 앵커를 찾아서 SpatialAnchor에 연결된 홀로그램을 렌더링할 수 있습니다. 이러한 홀로그램은 SpatialAnchor를 내보낸 원래 디바이스에서와 동일한 물리적 위치에 표시됩니다.

![단일 SpatialAnchor 내보내기](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>여러 SpatialAnchors 내보내기

단일 SpatialAnchor 내보내기와 마찬가지로 Blob에는 지정된 모든 SpatialAnchors 주변에 환경의 표현이 포함됩니다. 또한 Blob은 동일한 물리적 공간에 있는 경우 포함된 SpatialAnchors 간의 연결에 대한 정보를 포함합니다. 즉, 두 개의 주변 SpatialAnchors를 가져오면 *두* SpatialAnchor 간에 변환을 컴퓨팅하기에 충분한 데이터가 Blob에 포함되기 때문에 디바이스가 *첫 번째* SpatialAnchor 주위의 환경만 인식하더라도 두 번째 SpatialAnchor에 연결된 홀로그램을 배치할 수 있습니다. 두 SpatialAnchors를 개별적으로 내보낸 경우(TryExportSpatialAnchors에 대한 두 개의 별도 호출) 두 번째 SpatialAnchor에 연결된 홀로그램을 첫 번째 SpatialAnchor에 배치할 수 있도록 Blob에 데이터가 충분히 포함되지 않을 수 있습니다.

![단일 TryExportAnchorsAsync 호출을 사용하여 내보낸 여러 앵커](images/multipleanchors.png) ![각 앵커에 대해 별도의 TryExportAnchorsAsync 호출을 사용하여 내보낸 여러 앵커](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>예제: Windows::Networking::StreamSocket을 사용하여 앵커 데이터 보내기

여기서는 내보낸 앵커 데이터를 TCP 네트워크를 통해 전송하여 사용하는 방법의 예제를 제공합니다. HolographicSpatialAnchorTransferSample에서 나온 것입니다.

WinRT StreamSocket 클래스는 PPL 작업 라이브러리를 사용합니다. 네트워크 오류의 경우 다시 throw되는 예외를 사용하여 체인의 다음 작업으로 오류가 반환됩니다. 예외에는 오류 상태를 나타내는 HRESULT가 포함되어 있습니다.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>TCP와 함께 Windows::Networking::StreamSocketListener를 사용하여 내보낸 앵커 데이터를 보냅니다.

연결을 수신 대기하는 서버 인스턴스를 만듭니다.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

연결이 수신되면 클라이언트 소켓 연결을 사용하여 앵커 데이터를 보냅니다.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

이제 내보낸 앵커 데이터가 포함된 데이터 스트림을 보낼 수 있습니다.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

스트림 자체를 보내기 전에 먼저 헤더 패킷을 보내야 합니다. 이 헤더 패킷은 고정 길이여야 하며 앵커 데이터 스트림인 바이트의 변수 배열 길이도 나타내야 합니다. 이 예제에서는 보낼 다른 헤더 데이터가 없으므로 헤더 길이는 4바이트이고 부호 없는 32비트 정수를 포함합니다.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

스트림 길이(바이트)가 클라이언트로 전송되면 데이터 스트림 자체를 소켓 스트림에 계속 쓸 수 있습니다. 이렇게 하면 앵커 저장소 바이트가 클라이언트로 전송됩니다.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

이 항목의 앞에서 언급했듯이 네트워크 오류 상태 메시지가 포함된 예외를 처리할 준비가 되어 있어야 합니다. 예상할 수 없는 오류의 경우 다음과 같이 예외 정보를 디버그 콘솔에 쓸 수 있습니다. 이렇게 하면 코드 샘플이 연결을 완료할 수 없거나 앵커 데이터 전송을 완료할 수 없는 경우 어떤 일이 발생했는지에 대한 단서를 얻을 수 있습니다.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>TCP와 함께 Windows::Networking::StreamSocket을 사용하여 내보낸 앵커 데이터를 받습니다.

먼저 서버에 연결해야 합니다. 이 코드 샘플에서는 StreamSocket을 만들고 구성하는 방법을 보여 하며, 소켓 연결을 사용하여 네트워크 데이터를 얻는 데 사용할 수 있는 DataReader를 만듭니다.

**참고:** 이 샘플 코드를 실행하는 경우 클라이언트를 시작하기 전에 서버를 구성하고 시작해야 합니다.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

연결되면 서버가 데이터를 보낼 때까지 기다릴 수 있습니다. 스트림 데이터 판독기에서 LoadAsync를 호출하여 이 작업을 수행합니다.

받는 첫 번째 바이트 집합은 항상 이전 섹션에서 설명한 대로 앵커 데이터 스트림 바이트 길이를 나타내는 헤더 패킷이어야 합니다.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

헤더 패킷을 받은 후에는 예상해야 하는 앵커 데이터의 바이트 수를 알 수 있습니다. 스트림에서 해당 바이트를 계속 읽을 수 있습니다.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

앵커 데이터 스트림을 수신하기 위한 코드는 다음과 같습니다. 다시 말하지만, 먼저 스트림에서 바이트를 로드합니다. StreamSocket이 네트워크에서 해당 바이트 양을 받기 위해 대기하는 동안 이 작업을 완료하는 데 다소 시간이 걸릴 수 있습니다.

로드 작업이 완료되면 해당 바이트 수를 읽을 수 있습니다. 앵커 데이터 스트림에 대해 예상되는 바이트 수를 받은 경우 계속 진행하여 앵커 데이터를 가져올 수 있습니다. 그렇지 않은 경우 일종의 오류가 있어야 합니다. 예를 들어 이 문제는 서버 인스턴스가 종료된 후 데이터 스트림 보내기를 완료하거나 클라이언트가 전체 데이터 스트림을 수신하기 전에 네트워크가 다운될 때 발생할 수 있습니다.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

다시 알 수 없는 네트워크 오류를 처리할 준비가 되어 있어야 합니다.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

이것으로 끝입니다. 이제 네트워크를 통해 받은 앵커를 찾기 위한 충분한 정보가 있어야 합니다. 다시 말하지만 클라이언트는 앵커를 찾을 수 있는 충분한 시각적 추적 데이터가 있어야 합니다. 지금 바로 작동하지 않으면 잠시 시도해 보세요. 그래도 작동하지 않으면 서버에서 더 많은 앵커를 보내고 네트워크 통신을 사용하여 클라이언트에 대해 작동하는 앵커에 동의하도록 합니다. HolographicSpatialAnchorTransferSample을 다운로드하고, 클라이언트 및 서버 IP를 구성하고, 클라이언트 및 서버 HoloLens 디바이스에 배포하여 이 작업을 시도할 수 있습니다.

## <a name="see-also"></a>추가 정보
* [PPL(병렬 패턴 라이브러리)](/cpp/parallel/concrt/parallel-patterns-library-ppl)
* [Windows. Networking.StreamSocket](/uwp/api/Windows.Networking.Sockets.StreamSocket)
* [Windows. Networking.StreamSocketListener](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)