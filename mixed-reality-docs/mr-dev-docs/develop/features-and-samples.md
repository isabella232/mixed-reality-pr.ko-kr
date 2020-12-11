---
title: 샘플 및 기능 앱
description: HoloLens에 사용할 수 있는 기능 샘플을 살펴보세요.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 학습, 샘플, MRTK, 연구 모드, HoloLens 2, qr 코드, WebRTC, 혼합 현실 캡처, 홀로그램 원격 접속, UX 도구
ms.localizationpriority: high
ms.openlocfilehash: 2624949dd21b4c8e14ed45f152d41900b5f91faf
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615552"
---
# <a name="samples-and-feature-apps"></a>샘플 및 기능 앱

![HoloLens를 착용하고 손 움직임으로 홀로그램을 조작하는 사용자의 사진](unreal/images/unreal-developer.jpg)

모든 개발 과정은 다른 개발자가 성공적으로 빌드한 것을 기반으로 하며, 혼합 현실도 다르지 않습니다. 현재 모든 자습서와 샘플 앱은 Unity 또는 Unreal에서 빌드되었습니다. 다른 엔진 및 플랫폼용 콘텐츠를 개발하는 경우 해당 콘텐츠는 목차의 관련 제목 아래에서 찾을 수 있습니다.

## <a name="sample-apps"></a>샘플 앱

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>기능 샘플

아래 나열된 기능 샘플은 설명서에서 다루는 특정 구현에 해당하며 다양한 개발 플랫폼 및 하드웨어 디바이스를 포함합니다.

### <a name="research-mode"></a>연구 모드

연구 모드는 1세대 HoloLens에 도입되어 특히 배포용이 아닌 연구용 디바이스의 주요 센서에 대한 액세스 권한을 부여합니다. 아래의 샘플 애플리케이션은 연구 모드 스트림을 액세스 및 기록하고 [내재 및 외재적 기능](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)을 사용하는 예입니다.

<br>

| 참조 문서 | 애플리케이션 예제 |
| --- | --- |
| [연구 모드](platform-capabilities-and-apis/research-mode.md) | [HoloLens(1세대)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [연구 모드](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR 코드

HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다.

<br>

| 참조 문서 | 샘플 |
| --- | --- |
| [QR 코드](platform-capabilities-and-apis/qr-code-tracking.md) | [Unity에서 QR 코드 추적](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a>WebRTC

MixedReality-WebRTC 프로젝트는 혼합 현실 앱 개발자가 피어 투 피어 오디오, 비디오 및 데이터 실시간 통신을 애플리케이션에 통합할 수 있도록 지원하는 구성 요소 컬렉션입니다. WebRTC 구성 요소는 대부분의 최신 웹 브라우저에서 지원되는 RTC(Real-Time Communication)용 WebRTC 프로토콜을 기반으로 합니다.

<br>

| 참조 문서 | 샘플 |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [WebRTC 샘플 앱](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>홀로그램 혼합 현실 캡처

MRC(혼합 현실 캡처)는 실제 세계와 디지털 세계를 혼합한 1인칭 경험을 사진이나 비디오로 캡처하여 다른 사람과 실시간으로 공유합니다.

<br>

| 참조 문서 | 샘플 |
| --- | --- |
| [혼합 현실 캡처](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [혼합 현실 캡처 샘플](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>홀로그램 원격 접속

홀로그램 원격 플레이어는 홀로그램 원격 접속을 지원하는 PC 앱 및 게임에 연결하는 도우미 앱입니다. 홀로그램 원격 접속은 Wi-Fi 연결을 통해 PC에서 Microsoft HoloLens로 홀로그램 콘텐츠를 실시간으로 스트리밍하며, HoloLens(1세대)와 HoloLens 2에서 지원됩니다.

<br>

| 참조 문서 | 샘플 |
| --- | --- |
| [홀로그램 원격 접속](platform-capabilities-and-apis/holographic-remoting-player.md) | [홀로그램 원격 접속 샘플](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |