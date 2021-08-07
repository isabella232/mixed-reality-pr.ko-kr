---
title: WebVR Faq
description: 표준 소비자 지원 설명서를 벗어나는 웹 응용 프로그램의 경우에는 혼합 현실 문제 해결을 최신 상태로 유지 하세요.
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, WebVR
ms.openlocfilehash: d0f91af9cf14d8019707e504a9f8bc076bbe39db566895f17e1e56d6b906336d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211095"
---
# <a name="webvr-faqs"></a>WebVR Faq

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Edge에서 VR 콘텐츠를 볼 때 내 컨트롤러가 표시 되지 않는 이유는 무엇 인가요?

모든 WebVR 내용이 동작 컨트롤러를 지원 하도록 작성 된 것은 아닙니다. WebVR를 사용 하면 콘텐츠 개발자가 게임 컨트롤러나 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다. 사이트에 컨트롤러가 표시 되지 않으면 동작 컨트롤러를 지원 하지 않는 것일 수 있습니다.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>몰입 형 WebVR 뷰에서 마우스를 사용할 수 없는 이유

마우스를 사용 하는 것은 WebVR 사양의 선택적 기능입니다. 모든 브라우저에서이 기능을 지원 하지는 않지만 마우스 입력을 지원 하도록 모든 WebVR 콘텐츠를 작성 하는 것은 아닙니다. WebVR를 사용 하면 콘텐츠 개발자가 마우스, 키보드, 게임 컨트롤러 또는 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다. 마우스 입력 동작은 브라우저 마다 다릅니다. Microsoft Edge 내에서 웹 사이트 작성자는 마우스 입력이 작동 하기 위해 헤드셋에 프레젠테이션할 때 ' pointerlock '를 사용 하도록 해야 합니다.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Youtube/Facebook/Vimeo/보호자 등에서 360 대의 비디오를 볼 수 없는 이유는 무엇 인가요?

웹 사이트에서 VR 환경을 브라우저에서 직접 시작할 수 있도록 하는 WebVR 사양이 있습니다. 이러한 웹 사이트의 작성자는 현재이 사양을 구현 하지 않았습니다. 이러한 공급 업체의 VR 콘텐츠를 볼 수 있는 일부 플랫폼에서 다운로드 가능한 앱이 있을 수 있습니다.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Firefox 또는 Chrome에서 VR를 입력할 수 없는 이유

WebVR는 현재 Edge의 Windows Mixed Reality 장치 에서만 지원 됩니다.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>웹 사이트에서 VR를 입력 하는 경우 헤드셋에 빈 화면이 표시 되는 이유

웹 사이트에서 다중 GPU 컴퓨터 (하이브리드 GPU 랩톱 포함)에 대 한 지원을 구현 하지 않았을 수 있습니다. 다음을 시도 합니다.

* 페이지를 다시 로드합니다.
* 데스크톱 컴퓨터에서 Microsoft Edge 표시 되는 모니터와 동일한 그래픽 어댑터에 헤드셋을 연결 합니다. 통합 그래픽 어댑터가 아닌 더 높은 전원이 켜진 그래픽 카드에 모두 연결 합니다.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Edge에서 비디오를 시청할 때 VR를 끝내 면 소리는 계속 재생 되지만 가장자리 창은 회색으로 표시 됩니다.

이 문제는 혼합 현실 절벽 집의 Edge에서 WebVR를 실행할 때 알려진 문제입니다. 이 문제를 해결 하려면 windows 단추 대신 키보드에서 esc 키를 눌러 WebVR 환경을 종료 하거나 선택 하 여 회색으로 표시 된 가장자리 창을 활성화 한 다음 비디오를 중지 합니다.

## <a name="can-i-use-webvr-on-the-hololens"></a>HoloLens에서 WebVR을 사용할 수 있습니다.

Microsoft는이 시점에서 HoloLens WebVR에 대 한 어떠한 정보도 발표 하지 않았습니다.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Edge에서 WebVR 콘텐츠를 볼 때 평면도가 바닥에 표시 되는 이유는 무엇 인가요?

웹 사이트가 Windows Mixed Reality 헤드셋을 제대로 지원 하지 않습니다. 이 문제의 해결 방법:

1. 헤드셋을 공간 바닥에 놓습니다.
2. 바탕 화면에서 Microsoft Edge를 사용 하 여 WebVR 페이지로 이동 합니다 (혼합 현실에 있지 않음).
3. "VR 입력"을 선택 합니다.
4. 환경이 전체로 전환 될 때까지 5 ~ 10 초 정도 기다립니다.
5. 헤드셋에 배치 합니다.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>일부 WebVR 환경에서는 디스플레이가 낮은 해상도입니다.

이러한 웹 사이트는 고해상도 헤드셋을 제대로 지원 하지 않습니다. 이 문제의 해결 방법:

* 혼합 현실 절벽 집이 아닌 데스크톱에서 WebVR를 시작 하는 경우 "VR 입력"을 선택 하기 전에 창이 최대화 되었는지 확인 합니다.
* VR를 입력 한 후 Microsoft Edge 창의 크기를 조정 하지 마십시오.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>브라우저 탭을 변경할 때 WebVR 몰입 보기가 종료 되는 이유

이는 예상된 동작입니다. 보안상의 이유로 활성 브라우저 탭만 연결 된 헤드셋에 액세스할 수 있습니다.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>특정 WebVR 환경에서 오디오를 듣지 못하는 이유

웹 사이트에서 Microsoft Edge 현재 지원 하지 않는 ogg 오디오 파일 형식을 사용 하 고 있을 수 있습니다.

[문제 추적기](https://developer.microsoft.com/microsoft-edge/platform/issues/)에서 또는 [#EdgeBug 해시 태그](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)를 사용 하 여 twitter를 통해 Microsoft Edge 브라우저 팀에 게 직접 끊어진 사이트를 보고할 수 있습니다.

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>햅 피드백이 동작 컨트롤러가 있는 WebVR에서 작동 하지 않는 이유는 무엇 인가요?

Microsoft Edge는 현재 WebVR 게임 프로그램 API 확장의 haptics을 지원 하지 않습니다.