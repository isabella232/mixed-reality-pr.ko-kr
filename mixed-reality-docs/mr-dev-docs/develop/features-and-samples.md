---
title: 샘플 및 기능 앱
description: 사용 가능한 모든 Microsoft 샘플 및 HoloLens용 혼합 현실 기능 앱을 최신 상태로 유지합니다.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 학습, 샘플, MRTK, 연구 모드, HoloLens 2, qr 코드, WebRTC, 혼합 현실 캡처, 홀로그램 원격 접속, UX 도구
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583194"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="85b62-104">샘플 및 기능 앱</span><span class="sxs-lookup"><span data-stu-id="85b62-104">Samples and feature apps</span></span>

![HoloLens를 착용하고 손 움직임으로 홀로그램을 조작하는 사용자의 사진](unreal/images/unreal-developer.jpg)

<span data-ttu-id="85b62-106">모든 개발 과정은 다른 개발자가 성공적으로 빌드한 것을 기반으로 하며, 혼합 현실도 다르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="85b62-107">현재 모든 자습서와 샘플 앱은 Unity 또는 Unreal에서 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="85b62-108">다른 엔진 및 플랫폼용 콘텐츠를 개발하는 경우 해당 콘텐츠는 목차의 관련 제목 아래에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="85b62-109">샘플 앱</span><span class="sxs-lookup"><span data-stu-id="85b62-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="85b62-110">기능 샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-110">Feature samples</span></span>

<span data-ttu-id="85b62-111">아래 나열된 기능 샘플은 설명서에서 다루는 특정 구현에 해당하며 다양한 개발 플랫폼 및 하드웨어 디바이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="85b62-112">연구 모드</span><span class="sxs-lookup"><span data-stu-id="85b62-112">Research Mode</span></span>

<span data-ttu-id="85b62-113">연구 모드는 1세대 HoloLens에 도입되어 특히 배포용이 아닌 연구용 디바이스의 주요 센서에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="85b62-114">아래의 샘플 애플리케이션은 연구 모드 스트림을 액세스 및 기록하고 [내재 및 외재적 기능](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)을 사용하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="85b62-115">참조 문서</span><span class="sxs-lookup"><span data-stu-id="85b62-115">Reference article</span></span> | <span data-ttu-id="85b62-116">애플리케이션 예제</span><span class="sxs-lookup"><span data-stu-id="85b62-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="85b62-117">연구 모드</span><span class="sxs-lookup"><span data-stu-id="85b62-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="85b62-118">HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="85b62-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="85b62-119">연구 모드</span><span class="sxs-lookup"><span data-stu-id="85b62-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="85b62-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="85b62-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="85b62-121">QR 코드</span><span class="sxs-lookup"><span data-stu-id="85b62-121">QR codes</span></span>

<span data-ttu-id="85b62-122">HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="85b62-123">참조 문서</span><span class="sxs-lookup"><span data-stu-id="85b62-123">Reference article</span></span> | <span data-ttu-id="85b62-124">샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="85b62-125">QR 코드</span><span class="sxs-lookup"><span data-stu-id="85b62-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="85b62-126">Unity에서 QR 코드 추적</span><span class="sxs-lookup"><span data-stu-id="85b62-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="85b62-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="85b62-127">WebRTC</span></span>

<span data-ttu-id="85b62-128">MixedReality-WebRTC 프로젝트는 혼합 현실 앱 개발자가 피어 투 피어 오디오, 비디오 및 데이터 실시간 통신을 애플리케이션에 통합할 수 있도록 지원하는 구성 요소 컬렉션입니다. WebRTC 구성 요소는 대부분의 최신 웹 브라우저에서 지원되는 RTC(Real-Time Communication)용 WebRTC 프로토콜을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="85b62-129">참조 문서</span><span class="sxs-lookup"><span data-stu-id="85b62-129">Reference article</span></span> | <span data-ttu-id="85b62-130">샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="85b62-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="85b62-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="85b62-132">WebRTC 샘플 앱</span><span class="sxs-lookup"><span data-stu-id="85b62-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="85b62-133">홀로그램 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="85b62-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="85b62-134">MRC(혼합 현실 캡처)는 실제 세계와 디지털 세계를 혼합한 1인칭 경험을 사진이나 비디오로 캡처하여 다른 사람과 실시간으로 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="85b62-135">참조 문서</span><span class="sxs-lookup"><span data-stu-id="85b62-135">Reference article</span></span> | <span data-ttu-id="85b62-136">샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="85b62-137">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="85b62-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="85b62-138">혼합 현실 캡처 샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="85b62-139">홀로그램 원격 접속</span><span class="sxs-lookup"><span data-stu-id="85b62-139">Holographic Remoting</span></span>

<span data-ttu-id="85b62-140">홀로그램 원격 플레이어는 홀로그램 원격 접속을 지원하는 PC 앱 및 게임에 연결하는 도우미 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="85b62-141">홀로그램 원격 접속은 Wi-Fi 연결을 통해 PC에서 Microsoft HoloLens로 홀로그램 콘텐츠를 실시간으로 스트리밍하며, HoloLens(1세대)와 HoloLens 2에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b62-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="85b62-142">참조 문서</span><span class="sxs-lookup"><span data-stu-id="85b62-142">Reference article</span></span> | <span data-ttu-id="85b62-143">샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="85b62-144">홀로그램 원격 접속</span><span class="sxs-lookup"><span data-stu-id="85b62-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="85b62-145">홀로그램 원격 접속 샘플</span><span class="sxs-lookup"><span data-stu-id="85b62-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |