---
title: Windows Mixed Reality에서 WebXR 사용
description: Windows Mixed Reality 모던 헤드셋에서 실행 되는 WebXR 응용 프로그램을 사용 하 고 개발 하는 방법에 대 한 기본 사항을 알아봅니다.
author: yonet
ms.author: v-vtieto
ms.date: 09/16/2021
ms.topic: article
keywords: WebXR, winmr, webar, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, 웹 vr, 웹 xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: f99637c79d1147d940bb6a72d68969c99a2482ec
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932529"
---
# <a name="javascript-development-with-webxr"></a>WebXR를 사용 하 여 JavaScript 개발

JavaScript는 전 세계에서 가장 많이 사용 되는 프로그래밍 언어 중 하나입니다. 웹에서 간단 하 고 간단 하며 널리 사용 됩니다. JavaScript 및 웹 기술의 강력한 기능을 활용 하 여 보다 매력적인 혼합 현실 환경을 만들 수 있습니다.

## <a name="mixed-reality-applications-on-the-web"></a>웹의 혼합 현실 응용 프로그램

혼합 현실 기능은 [WebXR](webxr-overview.md)를 사용 하 여 웹에서 사용할 수 있습니다. 추가 소프트웨어 또는 플러그 인을 설치 하지 않고도 호환 되는 WebXR 사용 브라우저에서 VR (가상 현실) 및 AR (보강 된 현실) 콘텐츠를 볼 수 있습니다. HoloLens 2 같은 물리적 장치와 동일한 브라우저를 사용할 수 있습니다.

[**WebXR DEVICE API**](https://www.w3.org/TR/webxr/) 는 **웹** 의 **센서** 및 **헤드 탑재 된 디스플레이** 를 비롯 하 여 **VR (가상 현실)** 및 **AR (보강 된 현실)** 장치에 액세스 하기 위한 것입니다. WebXR device API는 현재 Microsoft Edge에서 사용할 수 있으며 Chrome 버전 79 이상 버전에서는 WebXR을 기본값으로 지원 합니다. WebXR에서 [caniuse.com](https://caniuse.com/#search=webxr)에 대 한 최신 브라우저 지원 상태를 확인할 수 있습니다.

> [!NOTE]
> **WebVR** 는 더 이상 사용 되지 않으며 현재 브라우저에서 사용할 수 없으므로 새로운 개발에 사용 하면 안 됩니다. 모든 기존 **WebVR** 구현을 **WebXR** 로 마이그레이션해야 합니다.

### <a name="viewing-webxr"></a>WebXR 보기

[Windows Mixed Reality 및 새 Microsoft Edge](../../whats-new/new-microsoft-edge.md) 와 [Firefox 현실](https://mixedreality.mozilla.org/firefox-reality/)에서 WebXR experinces를 볼 수 있습니다.
브라우저에서 WebXR을 지원 하는지 테스트 하려면 브라우저에서 [WebXR Samples](https://immersive-web.github.io/webxr-samples/) 로 이동할 수 있습니다.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>몰입 형 웹 환경을 개발 하는 데 사용할 수 있는 작업은 무엇 인가요?

다음 목록에는 현재 시장을 대상으로 하는 몰입 형 환경을 빌드하기 위한 JavaScript 프레임 워크 및 Api와 혼합 현실 JavaScript 개발자가 널리 승인 하 고 채택 하는 기능이 나와 있습니다.

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon는 3D 콘텐츠 및 몰입 형 응용 프로그램을 쉽게 개발할 수 있도록 하는 JavaScript 3D 엔진입니다. 몰입 형 응용 프로그램을 시작 하기 전에 Babylon.js 개발의 기본 사항에 대해 알아보는 것이 좋습니다.<br/><br/>- [시작](https://doc.babylonjs.com/start)babylon.js를 사용 하 여 3d 응용 프로그램을 빌드하는 방법을 알아봅니다.<br/>-babylon.js [필드](https://doc.babylonjs.com/examples/) 를 사용 하 여 3d 예제와 해당 소스 코드를 사용 하 여 재생<br/>- [WebXR](https://doc.babylonjs.com/divingDeeper/webXR) 에 대 한 심층 분석<br/>-자습서를 시작 하 여 [첫 번째 "헬로 월드!" 앱 만들기](tutorials/babylonjs-webxr-helloworld/introduction-01.md) 를 시작 하는 방법을 알아봅니다.|![BabylonJS 로고](images/babylon.js.example.png) |
|[**A-프레임**](https://aframe.io/) <br/><br/>A-프레임은 웹에서 가상 현실를 시작 하기 위한 선언적 JavaScript 프레임 워크입니다. 자세한 내용은 [프레임 설명서](https://aframe.io/docs/1.2.0/introduction/) 를 확인 하세요. |![A-프레임](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js는 몰입 형 환경을 만들기 위한 인기 있는 3D 라이브러리입니다. 설명서 페이지에서 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 하 고 [예제](https://threejs.org/examples/#webgl_animation_cloth)를 탐색 하는 방법에 대해 자세히 알아보세요. |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>WebGL Api를 사용 하 여 WebXR 장치 Api에 직접 액세스할 수 있습니다. WebGL (웹 그래픽 라이브러리)는 플러그 인을 사용 하지 않고 호환 되는 웹 브라우저 내에서 고성능 대화형 3D 및 2D 그래픽을 렌더링 하기 위한 JavaScript API입니다. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>참고 항목

* [WebXR 개요](webxr-overview.md)
* [WebXR 장치 API 사양](https://immersive-web.github.io/webxr/)
* [WebXR 장치 API 설명서](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR 샘플](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Babylon.js를 사용 하 여 WebXR 환경 만들기](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality 및 새 Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [WebGL에서 손실 된 컨텍스트 처리](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [몰입 형 웹 커뮤니티 그룹](https://www.w3.org/community/immersive-web/)
* [몰입 형 Web W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>다음 단계--자습서

> [!div class="nextstepaction"]
> [Babylon.js를 사용 하 여 첫 번째 WebXR 응용 프로그램 만들기 ](tutorials/babylonjs-webxr-helloworld/introduction-01.md)
> [!div class="nextstepaction"]

> [Babylon.js를 사용 하 여 WebXR에서 피아노 빌드 ](tutorials/babylonjs-webxr-piano/introduction-01.md)
