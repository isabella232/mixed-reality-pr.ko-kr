---
title: QR 코드 추적
description: HoloLens 2 혼합 현실 앱에서 QR 코드를 검색하고, 웹캠 기능을 추가하고, 좌표계를 관리하는 방법을 알아봅니다.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, 위치 기반 엔터테인먼트, vr 아케이드, 아케이드, 몰입형, qr, qr 코드, hololens2
ms.openlocfilehash: f6d2f224b9f477cf78ba4f0a5b6ce362f629d06988e966d71ed03bc48eda41d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193716"
---
# <a name="qr-code-tracking"></a>QR 코드 추적

HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다. 디바이스의 웹캠을 사용하도록 설정하면 Unreal 또는 Unity 프로젝트의 최신 버전에서 QR 코드를 인식할 수 있습니다. 프로덕션으로 진행하기 전에 문서의 끝에 배치한 [모범 사례를](#best-practices-for-qr-code-detection) 따르는 것이 좋습니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> QR 코드 검색</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>데스크톱 PC에서 몰입형 Windows Mixed Reality 헤드셋을 사용하여 QR 코드 추적은 Windows 10 버전 2004 이상에서 지원됩니다. Microsoft.MixedReality.QRCodeWatcher.IsSupported() API를 사용하여 현재 디바이스에서 기능이 지원되는지 여부를 확인합니다.

## <a name="getting-the-qr-package"></a>QR 패키지 받기

QR 코드 검색을 위한 NuGet 패키지는 [여기에서 다운로드할](https://nuget.org/Packages/Microsoft.MixedReality.QR)수 있습니다.

## <a name="using-openxr"></a>OpenXR 사용

OpenXR 플러그 인을 사용하는 경우 [ `SpatialGraphNodeId` QR API에서](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) 를 잡고 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API를 사용하여 QR 코드를 찾습니다.

참조를 위해 [GitHub 대한 QR 추적 샘플 프로젝트와](https://github.com/yl-msft/QRTracking) [ `SpatialGraphNode` API에](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)대한 자세한 사용 설명이 있습니다.

## <a name="detecting-qr-codes"></a>QR 코드 검색

### <a name="adding-the-webcam-capability"></a>웹캠 기능 추가

`webcam`QR 코드를 검색하려면 매니페스트에 기능을 추가해야 합니다. 사용자 환경에서 검색된 코드 내의 데이터에 중요한 정보가 포함될 수 있기 때문에 이 기능이 필요합니다.

를 호출하여 권한을 요청할 수 있습니다. `QRCodeWatcher.RequestAccessAsync()`

_C #:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C + +:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

QRCodeWatcher 개체를 생성하기 전에 권한을 요청해야 합니다.

QR 코드 검색에는 기능이 필요하지만 `webcam` 디바이스의 추적 카메라를 사용하여 검색이 수행됩니다. 이렇게 하면 디바이스의 PV(사진/비디오) 카메라를 사용하여 감지하는 데 비해 더 광범위한 감지 FOV 및 더 나은 배터리 수명을 제공합니다.

### <a name="detecting-qr-codes-in-unity"></a>Unity에서 QR 코드 검색

Unity용 NuGet 사용하여 NuGet 패키지를 설치하여 MRTK를 가져오지 않고 Unity에서 QR 코드 검색 API를 사용할 수 [있습니다.](https://github.com/GlitchEnzo/NuGetForUnity) 작동 방식을 파악하려면 [샘플 Unity 앱을](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)다운로드합니다. 샘플 앱에는 QR 코드 및 연결된 데이터(예: GUID, 물리적 크기, 타임스탬프 및 디코딩된 데이터)를 통해 홀로그램 사각형을 표시하는 예제가 있습니다.

### <a name="detecting-qr-codes-in-c"></a>C++에서 QR 코드 검색

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>QR 코드에 대한 좌표계 얻기

검색된 각 QR 코드는 왼쪽 위에 있는 빠른 검색 사각형의 왼쪽 위 모서리에 있는 QR 코드에 [맞춰진 공간 좌표계를](../../design/coordinate-systems.md) 노출합니다.  

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

QR SDK를 직접 사용하는 경우 Z축은 용지(표시되지 않음)를 가리킵니다. Unity 좌표로 변환할 때 Z축은 용지를 가리키고 왼쪽에 있습니다.

QR 코드의 SpatialCoordinateSystem은 표시된 대로 정렬됩니다. <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode를</a> 호출하고 코드의 SpatialGraphNodeId를 전달하여 플랫폼에서 좌표계를 얻을 수 있습니다.

아래 C++ 코드는 사각형을 만들고 QR 코드의 좌표계를 사용하여 배치하는 방법을 보여줍니다.

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

물리적 크기를 사용하여 QR 사각형을 만들 수 있습니다.

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

좌표계를 사용하여 QR 코드를 그리거나 홀로그램을 위치에 연결할 수 있습니다.

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

*QRCodeAddedHandler는* 다음과 같이 표시될 수 있습니다.

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>QR 코드 검색에 대한 모범 사례

### <a name="quiet-zones-around-qr-codes"></a>QR 코드 주위의 Quiet 영역

올바르게 읽으려면 QR 코드에 코드의 모든 면 주위에 여백이 필요합니다. 이 여백은 인쇄된 콘텐츠를 포함해서는 안 되며 네 개의 모듈(코드의 검은색 사각형 하나) 너비여야 합니다. 

[QR 사양에는](https://www.qrcode.com/en/howto/code.html) quiet 영역에 대한 자세한 정보가 포함되어 있습니다.

### <a name="lighting-and-backdrop"></a>조명 및 배경
QR 코드 감지 품질은 다양한 조명과 배경에 취약합니다. 

밝은 조명이 있는 장면에서 회색 배경에 검은색 코드를 인쇄합니다. 그렇지 않으면 흰색 배경에 검은색 QR 코드를 인쇄합니다.

코드 배경이 어두운 경우 검색 속도가 낮으면 회색 코드에서 검은색을 사용해 보세요. 배경이 비교적 밝은 경우 일반 코드가 제대로 작동해야 합니다.

### <a name="size-of-qr-codes"></a>QR 코드의 크기
Windows Mixed Reality 디바이스는 각각 5cm보다 작은 면이 있는 QR 코드에서 작동하지 않습니다.

5cm에서 10cm 길이의 QR 코드의 경우 코드를 검색하기 위해 상당히 가깝습니다. 또한 이 크기의 코드를 검색하는 데 더 오래 걸릴 수 있습니다. 

코드를 검색하는 정확한 시간은 QR 코드의 크기뿐만 아니라 코드에서 얼마나 멀리 떨어져 있는지에 따라 달라집니다. 코드에 더 가깝게 이동하면 크기 문제를 오프셋하는 데 도움이 됩니다.

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 코드에서의 거리 및 각도 위치
추적 카메라는 특정 수준의 세부 정보만 검색할 수 있습니다. 작은 코드(< 10cm)의 경우 상당히 가깝습니다. 10cm에서 25cm 너비까지 다양한 버전 1 QR 코드의 경우 최소 검색 거리 범위는 0.15미터에서 0.5미터입니다. 

크기에 대한 검색 거리는 선형적으로 증가하지만 QR 버전 또는 모듈 크기에 따라 달라집니다. 버전이 높을수록 더 가까운 위치에서만 검색할 수 있는 모듈이 작습니다. 감지 거리가 더 길어지도록 하려면 마이크로 QR 코드를 사용해 볼 수도 있습니다. QR 검색은 각도 범위 += 45 deg와 함께 작동하여 코드를 검색하는 데 적절한 해상도가 있는지 확인합니다.

> [!IMPORTANT]
> 항상 충분한 대비와 적절한 테두리가 있는지 확인합니다.

### <a name="qr-codes-with-logos"></a>로고가 있는 QR 코드
로고가 있는 QR 코드는 테스트되지 않았으며 현재 지원되지 않습니다.

### <a name="managing-qr-code-data"></a>QR 코드 데이터 관리
Windows Mixed Reality 디바이스는 드라이버의 시스템 수준에서 QR 코드를 검색합니다. 디바이스가 다시 부팅되면 검색된 QR 코드가 사라지고 다음에 새 개체로 다시 검색됩니다.

특정 타임스탬프보다 오래된 QR 코드를 무시하도록 앱을 구성하는 것이 좋습니다. 현재 API는 QR 코드 기록 지우기 지원을 지원하지 않습니다.

### <a name="qr-code-placement-in-a-space"></a>공간에 QR 코드 배치
QR 코드를 배치하는 위치 및 방법에 대한 권장 사항은 [HoloLens 환경 고려 사항을](/hololens/hololens-environment-considerations)참조하세요.

## <a name="qr-api-reference"></a>QR API 참조

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>추가 정보
* [좌표계](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>