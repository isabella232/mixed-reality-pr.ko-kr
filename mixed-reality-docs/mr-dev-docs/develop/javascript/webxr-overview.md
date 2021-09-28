---
title: Windows Mixed Reality WebXR 사용
description: Windows Mixed Reality 몰입형 헤드셋에서 실행되는 WebXR 애플리케이션을 사용하고 개발하는 기본 사항 알아보기
author: yonet
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 비디오, 360 비디오, 360 사진, 360 사진, 360개 콘텐츠, 몰입형 웹, 몰입형 웹, 몰입형 웹, IW
ms.openlocfilehash: b0ab1eab5f1c3e546dde367c2cdb992fba7b452d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148701"
---
# <a name="javascript-development-with-webxr"></a>WebXR을 통한 JavaScript 개발

JavaScript는 전 세계에서 가장 인기 있는 프로그래밍 언어 중 하나입니다. 간단하고 간단하며 웹에서 널리 사용됩니다. JavaScript 및 웹 기술의 능력을 활용하여 더 매력적인 Mixed Reality 환경을 만듭니다.

## <a name="mixed-reality-applications-on-the-web"></a>웹에서 애플리케이션 Mixed Reality

Mixed Reality 기능은 [WebXR을](webxr-overview.md)통해 웹에서 사용할 수 있습니다. 추가 소프트웨어 또는 플러그 인을 설치하지 않고 호환되는 WebXR 지원 브라우저에서 VR(가상 현실) 및 AR(증강 현실) 콘텐츠를 볼 수 있습니다. HoloLens 2 같은 물리적 디바이스에서 동일한 브라우저를 사용할 수 있습니다.

[**WebXR 디바이스 API는**](https://www.w3.org/TR/webxr/) 웹에서 센서 및 헤드 탑재 디스플레이를 포함하여 VR(가상 현실) 및 AR(증강 현실) 디바이스에 액세스하기 위한 것입니다. WebXR 디바이스 API는 Microsoft Edge 및 Chrome 버전 79에서 사용할 수 있으며, 이후 버전에서는 WebXR을 기본값으로 지원합니다. [caniuse.com](https://caniuse.com/#search=webxr)WebXR에 대한 최신 브라우저 지원 상태를 확인할 수 있습니다.

> [!NOTE]
> **WebVR은** 더 이상 사용되지 않으며 현재 브라우저에서 사용할 수 없으므로 새로운 개발에 사용하면 안 됩니다. 기존 **WebVR** 구현을 **WebXR** 로 마이그레이션해야 합니다.

| WebXR 기능 | 가용성 |
|---------|---------|
|[WebXR 디바이스 API(w3.org)](https://www.w3.org/TR/webxr/) | Windows Desktop의 Edge 81 <br>Hololens 2의 Edge 91|
|[WebXR 증강 현실 모듈 - 수준 1(w3.org)](https://www.w3.org/TR/webxr-ar-module-1/)|Edge 91. Hololens 2만|
|[WebXR 손 입력 모듈 - 수준 1(w3.org)](https://www.w3.org/TR/webxr-hand-input-1/)|Edge 93. Hololens 2만|
|[WebXR 앵커 모듈(immersive-web.github.io)](https://immersive-web.github.io/anchors/)|Edge 93. Hololens 2만|
|[WebXR 적중 테스트 모듈(immersive-web.github.io)](https://immersive-web.github.io/hit-test/)|Edge 93. Hololens 2만 |

### <a name="viewing-webxr"></a>WebXR 보기

[새](../../whats-new/new-microsoft-edge.md) Microsoft Edge 및 [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/) 브라우저를 Windows Mixed Reality WebXR 환경을 볼 수 있습니다.
브라우저에서 WebXR을 지원하는지 테스트하려면 브라우저에서 [WebXR 샘플로](https://immersive-web.github.io/webxr-samples/) 이동할 수 있습니다.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>몰입형 웹 환경을 개발하는 데 사용할 수 있는 것은 무엇인가요?

다음 목록에서는 현재 시장에서 우위를 점하고 혼합 현실 JavaScript 개발자가 널리 수용하고 채택하는 몰입형 환경을 구축하기 위한 JavaScript 프레임워크 및 API를 보여 제공합니다.

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon은 3D 콘텐츠 및 몰입형 애플리케이션을 쉽게 개발할 수 있게 해주는 JavaScript 3D 엔진입니다. 몰입형 애플리케이션을 시작하기 전에 Babylon.js 개발의 기본 사항 알아보는 것이 좋습니다.<br/><br/>- babylon.js 사용하여 3D 애플리케이션을 빌드하는 방법 [알아보기: 시작](https://doc.babylonjs.com/start)<br/>- babylon.js: [Playground를](https://doc.babylonjs.com/examples/) 사용하여 3D 예제 및 해당 소스 코드를 재생합니다.<br/>- [WebXR에](https://doc.babylonjs.com/divingDeeper/webXR) 대해 자세히 알아보기<br/>- 자습서를 시작하는 방법 알아보기: [첫 번째 "Hello World!" 앱 만들기](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 로고](images/babylon.js.example.png) |
|[**A 프레임**](https://aframe.io/) <br/><br/>A 프레임은 웹에서 Virtual Reality를 시작하는 데 사용할 수 있는 선언적 JavaScript 프레임워크입니다. 자세한 내용은 [A-Frame 설명서를 참조하세요.](https://aframe.io/docs/1.2.0/introduction/) |![A 프레임](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 몰입형 환경을 만들기 위한 인기 있는 3D 라이브러리입니다. [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 대해 자세히 알아보고 [예제를 살펴봅니다.](https://threejs.org/examples/#webgl_animation_cloth) |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>WebGL API를 사용하여 WebXR 디바이스 API에 직접 액세스할 수 있습니다. WebGL(웹 그래픽 라이브러리)은 플러그 인을 사용하지 않고 호환되는 웹 브라우저 내에서 고성능 대화형 3D 및 2D 그래픽을 렌더링하기 위한 JavaScript API입니다. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>참고 항목

* [WebXR 디바이스 API 사양](https://immersive-web.github.io/webxr/)
* [WebXR 디바이스 API 설명서](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR 샘플](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Babylon.js 사용하여 WebXR 환경 만들기](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality 및 새 Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [WebGL에서 손실된 컨텍스트 처리](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [몰입형 웹 커뮤니티 그룹](https://www.w3.org/community/immersive-web/)
* [몰입형 웹 W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>다음 단계--자습서

> [!div class="nextstepaction"]
> [Babylon.js사용하여 첫 번째 WebXR 애플리케이션 만들기 ](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

> [!div class="nextstepaction"]
> [Babylon.js사용하여 WebXR에서 빌드 ](tutorials/babylonjs-webxr-piano/introduction-01.md)
