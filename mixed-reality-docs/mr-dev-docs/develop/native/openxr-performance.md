---
title: OpenXR 성능
description: OpenXR mixed reality 응용 프로그램의 GPU 성능을 디버그 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 성능, 최적화, GPU 디버깅, RenderDoc, PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006763"
---
# <a name="openxr-performance"></a>OpenXR 성능

HoloLens 2에는를 통해 컴퍼지션 데이터를 제출 하는 다양 한 방법이 있으며,이로 `xrEndFrame` 인해 사후 처리 및 눈에 띄는 성능 저하가 발생할 수 있습니다.

성능 저하를 방지 하려면 다음 특징을 가진 [ `XrCompositionProjectionLayer` 단일를 제출](openxr-best-practices.md#use-a-single-projection-layer) 합니다.

* [텍스처 배열 사용이 swapchain present](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [기본 색이 swapchain present 형식 사용](openxr-best-practices.md#select-a-swapchain-format)
* [권장 되는 보기 차원 사용](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 플래그를 설정 하지 않습니다. `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* 를 `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0 f와 `maxDepth` 1.0 f로 설정 합니다.

성능을 향상 시키려면 다음을 고려 하십시오.

* [16 비트 깊이 형식 사용](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [인스턴스 그리기 호출 만들기](openxr-best-practices.md#render-with-texture-array-and-vprt)
