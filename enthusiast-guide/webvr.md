---
title: Windows Mixed Reality에서 WebVR 사용
description: WebVR의 기본 사항, Windows Mixed Reality에서 Microsoft Edge를 사용 하는 방법 헤드셋 및 일반적인 문제 해결 문제에 대해 알아봅니다.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, WebVR, Edge, Microsoft Edge, 웹 검색
ms.openlocfilehash: 0b0d07383b43feaa11fb9bfac2b071d8d4d80b19
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009443"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Windows Mixed Reality에서 WebVR 사용

>[!IMPORTANT]
>대부분의 최신 웹 브라우저에서는 WebVR를 사용 하는 것이 더 이상 지원 되지 않으며,이는 VR 헤드셋을 위한 몰입 형 웹 환경을 만들기 위한 새로운 표준입니다. [새 Microsoft Edge](using-microsoft-edge.md) for WebXR 지원을 설치 하세요.

## <a name="what-is-webvr"></a>WebVR이란?

[WebVR](https://webvr.info) 는 브라우저에서 VR를 바로 사용할 수 있게 해 주는 오픈 사양입니다. 웹 사이트에서 WebVR 지원을 구현 하 고 3D 콘텐츠를 제공 하는 경우 사용자 동의를 사용 하 여 헤드셋에 몰입 형 콘텐츠를 표시할 수 있습니다.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>WebVR와 VR의 웹 검색 간의 차이점은 무엇 인가요?

WebVR는 웹 사이트 작성자가 페이지에 VR 기능을 추가할 수 있는 기술입니다. WebVR API는 페이지에서 3D 콘텐츠 (예: 360도 비디오, 3D 모델 또는 3D 게임)를 전체 헤드셋에 표시 하는 데 사용 됩니다. **예:** [Cnn.com/vr](http://cnn.com/vr)에서 360 비디오 보기 페이지에서 WebVR를 지 원하는 경우 단추 또는 다른 UI 요소를 추가 합니다 .이 요소는 VR를 입력 하도록 선택할 수 있습니다.

VR에서 웹을 검색 하는 것은 Cliffhouse 내에서 2D 앱 슬레이트로 헤드셋을 입고 있는 동안 Edge 브라우저를 사용 하는 것을 의미 합니다.

## <a name="do-all-websites-support-webvr"></a>모든 websites 지원 WebVR

아니요. 웹 사이트 작성자는 WebVR을 사용 하도록 옵트인 (opt in) 해야 하며 특정 브라우저, 헤드셋 및 컨트롤러에 대해 최적화 된 사이트를 만들 수 있습니다. 일부 WebVR 콘텐츠는 모바일 VR 장치에 대해서만 최적화 됩니다. 또한 웹 사이트는 WebVR 콘텐츠를 명시적으로 만들고 제공 해야 한다는 점에 유의 하세요. WebVR 호환 콘텐츠가 있는 사이트의 수는 매일 증가 합니다.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>WebVR를 사용 하 여 Microsoft Edge에서 콘텐츠를 볼 수 있습니다.

아니요. Edge에서 WebVR를 사용 하려면 Windows Mixed Reality 헤드셋이 필요 합니다. 그러나 다른 브라우저에서 WebVR 콘텐츠에 액세스할 수 있습니다. 에서 호환 되는 장치 및 브라우저의 전체 목록을 참조 하세요. [WebVR](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>WebVR 개발자 설명서는 어디서 찾을 수 있나요?

개발자 설명서는 여기에 있습니다. [WebVR Developer 설명서](https://docs.microsoft.com/microsoft-edge/webvr/)를 참조 하세요.

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Windows Mixed Reality에서 작동 하지 않는 WebVR가 있는 웹 사이트를 찾았습니다. 뭐 할까요

[문제 추적기](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)에서 또는 [#EdgeBug 해시 태그](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)를 사용 하 여 Twitter를 통해 Microsoft Edge 브라우저 팀에 직접 끊어진 사이트를 보고할 수 있습니다.

범주 아래에서 Windows 피드백 허브 앱을 사용 하 여 버그를 기록할 수도 있습니다.

Microsoft Edge > 웹 사이트 문제

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>WebVR가 작동 하는지 테스트 하는 데 유용한 페이지는 무엇 인가요?

[Webvr.info 샘플](http://webvr.info/samples/XX-vr-controllers.html)을 참조 하세요.

## <a name="how-do-i-set-up-webvr"></a>WebVR 설정 어떻게 할까요?

Windows Mixed Reality 헤드셋 (하드웨어 또는 시뮬레이션 사용)에서 WebVR 콘텐츠를 경험 하려면 다음을 수행 해야 합니다.

1. 헤드셋이 연결 되어 있는지 확인 합니다.
2. 바탕 화면에서 또는 혼합 현실에서 Microsoft Edge를 시작 합니다.
3. WebVR 사용 페이지로 이동 합니다.
4. 페이지 내에서 VR 입력 단추를 선택 합니다 .이 단추의 위치 및 시각적 표현은 웹 사이트 마다 다를 수 있습니다. 다음과 유사 하 게 표시 될 수 있습니다. \
   ![VR Goggles 이미지](images/75px-enter-vr.png)
5. 처음에 특정 도메인에서 VR를 입력 하려고 하면 브라우저는 몰입 형 보기 사용에 대 한 동의를 요청 하 고 예를 선택 합니다. ![특정 도메인에 대 한 첫 번째 시도를 시작 하는 데 표시 되는 동의 UI](images/1053px-Webvr-consent-ui.png)
6. 헤드셋은 WebVR 콘텐츠를 표시 하기 시작 합니다.

## <a name="see-also"></a>참조

* [> WebVR 문제 해결](webvr-questions.md)
* [첫 번째 WebVR 환경을 시작 하는 방법](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Windows Mixed Reality에서 게임과 앱 사용](using-games-and-apps-in-windows-mixed-reality.md)
* [혼합 현실 집](your-mixed-reality-home.md)
* [추적 시스템](tracking-system.md)
* [동작 컨트롤러](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [사용자 의견 보내기](filing-feedback.md)
