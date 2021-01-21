---
title: QR 코드 추적
description: HoloLens 2의 혼합 현실 앱에서 QR 코드를 검색 하 고, 웹캠 기능을 추가 하 고, 좌표계를 관리 하는 방법에 대해 알아봅니다.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, 위치 기반 엔터테인먼트, vr 아케이드, 아케이드, 모던, qr, qr 코드, hololens2
ms.openlocfilehash: 0f53b8def268b2d501c6efe3c3e40ea18f9323e0
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635435"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="657b4-104">QR 코드 추적</span><span class="sxs-lookup"><span data-stu-id="657b4-104">QR code tracking</span></span>

<span data-ttu-id="657b4-105">HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="657b4-106">장치의 웹캠을 사용 하도록 설정 하면 최신 버전의 Unreal 또는 Unity 프로젝트에서 QR 코드를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="657b4-107">프로덕션으로 전환 하기 전에 문서 끝에 있는 [모범 사례](#best-practices-for-qr-code-detection) 를 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="657b4-108">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="657b4-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="657b4-109">기능</span><span class="sxs-lookup"><span data-stu-id="657b4-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="657b4-110"><a href="/hololens/hololens1-hardware">HoloLens (첫 번째 gen)</a></span><span class="sxs-lookup"><span data-stu-id="657b4-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="657b4-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="657b4-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="657b4-112"><a href="../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="657b4-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="657b4-113">QR 코드 검색</span><span class="sxs-lookup"><span data-stu-id="657b4-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="657b4-114">️</span><span class="sxs-lookup"><span data-stu-id="657b4-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="657b4-115">✔️</span><span class="sxs-lookup"><span data-stu-id="657b4-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="657b4-116">✔️</span><span class="sxs-lookup"><span data-stu-id="657b4-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="657b4-117">데스크톱 Pc의 몰입 형 Windows Mixed Reality 헤드셋을 사용한 QR 코드 추적은 Windows 10 버전 2004 이상에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="657b4-118">MixedReality () API를 사용 하 여 기능이 현재 장치에서 지원 되는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="657b4-119">QR 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="657b4-119">Getting the QR package</span></span>

<span data-ttu-id="657b4-120">[여기](https://nuget.org/Packages/Microsoft.MixedReality.QR)에서 QR 코드 검색을 위한 NuGet 패키지를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="657b4-121">QR 코드 검색</span><span class="sxs-lookup"><span data-stu-id="657b4-121">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="657b4-122">웹캠 기능 추가</span><span class="sxs-lookup"><span data-stu-id="657b4-122">Adding the webcam capability</span></span>

<span data-ttu-id="657b4-123">`webcam`QR 코드를 검색 하려면 매니페스트에 기능을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-123">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="657b4-124">이 기능은 사용자 환경에서 검색 된 코드 내의 데이터에 중요 한 정보가 포함 될 수 있으므로 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-124">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="657b4-125">다음을 호출 하 여 사용 권한을 요청할 수 있습니다 `QRCodeWatcher.RequestAccessAsync()` .</span><span class="sxs-lookup"><span data-stu-id="657b4-125">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="657b4-126">_C #_</span><span class="sxs-lookup"><span data-stu-id="657b4-126">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="657b4-127">_C_</span><span class="sxs-lookup"><span data-stu-id="657b4-127">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="657b4-128">QRCodeWatcher 개체를 구성 하기 전에 사용 권한을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-128">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="657b4-129">QR 코드 검색 `webcam` 기능을 사용 하려면 장치의 추적 카메라를 사용 하 여 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-129">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="657b4-130">이를 통해 장치 사진/비디오 (PV) 카메라를 검색 하는 것과 비교 하 여 더 광범위 한 검색 FOV와 더 나은 배터리 수명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-130">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="657b4-131">Unity에서 QR 코드 검색</span><span class="sxs-lookup"><span data-stu-id="657b4-131">Detecting QR codes in Unity</span></span>

<span data-ttu-id="657b4-132">[Unity 용 nuget을](https://github.com/GlitchEnzo/NuGetForUnity)사용 하 여 nuget 패키지를 설치 하 여 MRTK를 가져오지 않고 UNITY에서 QR 코드 검색 API를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-132">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="657b4-133">작동 방식에 대 한 느낌을 얻으려면 [샘플 Unity 앱](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-133">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="657b4-134">샘플 앱에는 QR 코드 및 GUID, 실제 크기, 타임 스탬프 및 디코딩된 데이터와 같은 관련 데이터에 대 한 holographic 제곱을 표시 하는 예제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-134">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="657b4-135">C + +에서 QR 코드 검색</span><span class="sxs-lookup"><span data-stu-id="657b4-135">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="657b4-136">QR 코드의 좌표계 가져오기</span><span class="sxs-lookup"><span data-stu-id="657b4-136">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="657b4-137">검색 된 각 QR 코드는 왼쪽 상단에 있는 빠른 검색 사각형의 왼쪽 위 모퉁이에 있는 QR 코드와 정렬 된 [공간 좌표계](../../design/coordinate-systems.md) 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-137">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

<span data-ttu-id="657b4-139">QR SDK를 직접 사용 하는 경우 Z 축이 문서를 가리키고 (표시 되지 않음) Unity 좌표로 변환 되 면 Z 축 지점은 용지에서 제외 되며 왼쪽으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-139">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="657b4-140">QR 코드의 SpatialCoordinateSystem은 표시 된 대로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-140">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="657b4-141"><a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> 를 호출 하 고 코드의 SpatialGraphNodeId를 전달 하 여 플랫폼에서 좌표계를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-141">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="657b4-142">아래 c + + 코드는 사각형을 만들고 QR 코드의 좌표계를 사용 하 여 삽입 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-142">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="657b4-143">실제 크기를 사용 하 여 QR 사각형을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-143">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="657b4-144">좌표계를 사용 하 여 QR 코드를 그리거나 위치에 holograms을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-144">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="657b4-145">*QRCodeAddedHandler* 다음과 같이 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-145">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="657b4-146">QR 코드 검색에 대 한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="657b4-146">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="657b4-147">QR 코드 주위의 자동 영역</span><span class="sxs-lookup"><span data-stu-id="657b4-147">Quiet zones around QR Codes</span></span>

<span data-ttu-id="657b4-148">올바르게 읽도록 하려면 QR 코드에 코드의 모든 측면에 대 한 여백이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-148">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="657b4-149">이 여백은 인쇄 된 콘텐츠를 포함 하지 않아야 하 고 4 개의 모듈 (코드의 검정 사각형 하나) 너비 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-149">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="657b4-150">[QR](https://www.qrcode.com/en/howto/code.html) 사양은 자동 영역에 대 한 자세한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-150">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="657b4-151">조명 및 배경</span><span class="sxs-lookup"><span data-stu-id="657b4-151">Lighting and backdrop</span></span>
<span data-ttu-id="657b4-152">QR 코드 검색 품질은 다양 한 조명 및 배경에 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-152">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="657b4-153">밝은 조명이 있는 장면에서 회색 배경의 검정색 코드를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-153">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="657b4-154">그렇지 않으면 흰색 배경으로 검정색 QR 코드를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-154">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="657b4-155">코드에 대 한 배경이 진하게 표시 되는 경우 검색 속도가 낮은 경우 회색 코드를 검정으로 해보세요.</span><span class="sxs-lookup"><span data-stu-id="657b4-155">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="657b4-156">배경이 비교적 밝은 경우 일반 코드가 정상적으로 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-156">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="657b4-157">QR 코드 크기</span><span class="sxs-lookup"><span data-stu-id="657b4-157">Size of QR codes</span></span>
<span data-ttu-id="657b4-158">Windows Mixed Reality 장치는 각각 5cm 보다 작은 면에서 QR 코드에 대해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-158">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="657b4-159">5gb와 10gb의 QR 코드의 경우에는 코드를 검색 하는 데 매우 가까운 시간을 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-159">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="657b4-160">이 크기의 코드를 검색 하는 데 더 많은 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-160">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="657b4-161">코드를 검색 하는 정확한 시간은 QR 코드의 크기 뿐만 아니라 코드에서 떨어져 있는 정도에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-161">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="657b4-162">코드에 가까이 이동 하면 크기와 관련 된 문제를 오프셋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-162">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="657b4-163">QR 코드의 거리 및 각도 위치</span><span class="sxs-lookup"><span data-stu-id="657b4-163">Distance and angular position from the QR code</span></span>
<span data-ttu-id="657b4-164">추적 카메라는 특정 수준의 세부 정보만 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-164">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="657b4-165">작은 코드의 경우에는 옆쪽을 따라 < 10gb를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-165">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="657b4-166">10 cm에서 25cm 너비까지 다양 한 버전 1 QR 코드의 경우 최소 검색 거리가 0.15 미터에서 0.5 미터 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-166">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="657b4-167">크기에 대 한 검색 거리가 선형적으로 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-167">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="657b4-168">QR 검색은 코드를 검색 하기 위한 적절 한 해상도를 보장 하기 위해 각도 + = 45도로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-168">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="657b4-169">로고가 포함 된 QR 코드</span><span class="sxs-lookup"><span data-stu-id="657b4-169">QR codes with logos</span></span>
<span data-ttu-id="657b4-170">로고가 포함 된 QR 코드는 테스트 되지 않았으며 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-170">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="657b4-171">QR 코드 데이터 관리</span><span class="sxs-lookup"><span data-stu-id="657b4-171">Managing QR code data</span></span>
<span data-ttu-id="657b4-172">Windows Mixed Reality 장치는 드라이버의 시스템 수준에서 QR 코드를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="657b4-173">장치를 다시 부팅 하면 검색 된 QR 코드가 사라지고 다음 번에 새 개체로 다시 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-173">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="657b4-174">특정 타임 스탬프 보다 오래 된 QR 코드를 무시 하도록 앱을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-174">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="657b4-175">현재이 API는 QR 코드 기록 지우기를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="657b4-175">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="657b4-176">공간에서 QR 코드 배치</span><span class="sxs-lookup"><span data-stu-id="657b4-176">QR code placement in a space</span></span>
<span data-ttu-id="657b4-177">QR 코드를 저장 하는 위치 및 방법에 대 한 권장 사항은 [HoloLens 환경 고려 사항](/hololens/hololens-environment-considerations)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="657b4-177">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="657b4-178">QR API 참조</span><span class="sxs-lookup"><span data-stu-id="657b4-178">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="657b4-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="657b4-179">See also</span></span>
* [<span data-ttu-id="657b4-180">좌표계</span><span class="sxs-lookup"><span data-stu-id="657b4-180">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="657b4-181"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="657b4-181"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>