---
title: JavaScript 개발 개요
description: 웹, 모바일 및 Windows 몰입형 헤드셋용 JavaScript를 사용한 Mixed Reality 개발 개요입니다.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 비디오, 360 비디오, 360 사진, 360 사진, 360 콘텐츠, 몰입형 웹, 몰입형 웹, IW, 몰입형 웹
ms.openlocfilehash: 311241d9dec6f5d086a45766c040b1b2b9eb4128
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394347"
---
# <a name="javascript-development-overview"></a>JavaScript 개발 개요

JavaScript는 전 세계에서 가장 인기 있는 프로그래밍 언어 중 하나입니다. 간단하고 간단하며 웹에서 널리 사용됩니다. JavaScript 및 웹 기술의 능력을 활용하여 더 매력적인 Mixed Reality 환경을 만듭니다.

## <a name="mixed-reality-applications-on-the-web"></a>웹에서 애플리케이션 Mixed Reality

Mixed Reality 기능은 [WebXR](webxr-overview.md)를 사용하여 웹에서 사용할 수 있습니다. 추가 소프트웨어 또는 플러그 인을 설치하지 않고 호환되는 WebXR 지원 브라우저에서 VR(가상 현실) 및 AR(증강 현실) 콘텐츠를 볼 수 있습니다. HoloLens 2 같은 물리적 디바이스에서 동일한 브라우저를 사용할 수 있습니다. 자세한 내용은 [WebXR](webxr-overview.md) 설명서를 확인하세요.

> [!NOTE]
> **WebVR은** 더 이상 사용되지 않으며 현재 브라우저에서 사용할 수 없으므로 새로운 개발에 사용하면 안 됩니다. 기존 **WebVR** 구현을 **WebXR** 로 마이그레이션해야 합니다.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>몰입형 웹 환경을 개발하는 데 무엇을 사용할 수 있나요?

다음 목록에서는 현재 시장에서 우위를 점하고 Mixed Reality JavaScript 개발자가 널리 수용하고 채택하는 몰입형 환경을 구축하기 위한 JavaScript 프레임워크 및 API를 보여줍니다.

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon은 3D 콘텐츠 및 몰입형 애플리케이션을 쉽게 개발할 수 있게 해주는 JavaScript 3D 엔진입니다. 몰입형 애플리케이션을 시작하기 전에 Babylon.js 개발의 기본 사항 알아보는 것이 좋습니다.<br/><br/>- babylon.js 시작을 사용하여 3D 애플리케이션을 [빌드하는](https://doc.babylonjs.com/start)방법을 알아봅니다.<br/>- babylon.js [Playground를](https://doc.babylonjs.com/examples/) 사용하여 3D 예제 및 소스 코드를 재생합니다.<br/>- [WebXR에](https://doc.babylonjs.com/divingDeeper/webXR) 대해 자세히 알아보기<br/>- [첫 번째 "Hello World!" 앱 만들기](tutorials/babylonjs-webxr-helloworld/introduction-01.md) 자습서를 시작하는 방법을 알아봅니다.|![BabylonJS 로고](images/babylon.js.example.png) |
|[**A 프레임**](https://aframe.io/) <br/><br/>A 프레임은 웹에서 Virtual Reality를 시작하기 위한 선언적 JavaScript 프레임워크입니다. 자세한 내용은 [A-Frame 설명서를 참조하세요.](https://aframe.io/docs/1.2.0/introduction/) |![A 프레임](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 몰입형 환경을 만들기 위한 인기 있는 3D 라이브러리입니다. 설명서 페이지에서 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 대해 자세히 알아보고 [예제를 살펴보세요.](https://threejs.org/examples/#webgl_animation_cloth) |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>WebGL API를 사용하여 WebXR 디바이스 API에 직접 액세스할 수 있습니다. WebGL(웹 그래픽 라이브러리)은 플러그 인을 사용하지 않고 호환되는 웹 브라우저 내에서 고성능 대화형 3D 및 2D 그래픽을 렌더링하기 위한 JavaScript API입니다. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>다음 단계

자습서를 시작하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [첫 번째 "Hello World!" 앱 만들기](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>참고 항목

* [WebXR 개요](webxr-overview.md)
* [WebXR 디바이스 API 사양](https://immersive-web.github.io/webxr/)
* [WebXR 디바이스 API 설명서](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [WebXR 샘플](https://immersive-web.github.io/webxr-samples/)
* [Babylon.js 사용하여 WebXR 환경 만들기](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 및 새 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [몰입형 웹 W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)
