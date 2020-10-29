---
title: OpenXR 성능
description: OpenXR 응용 프로그램의 GPU 성능을 디버깅 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 성능, 최적화, GPU 디버깅, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683832"
---
# <a name="openxr-performance"></a>OpenXR 성능

HoloLens 2에는 여러 가지 방법으로 컴퍼지션 데이터를 제출 하 여 `xrEndFrame` 사후 처리가 발생 하 여 성능이 저하 될 수 있습니다.
성능 penalities을 방지 하려면 다음 특성을 사용 하 여 [ `XrCompositionProjectionLayer` 단일를 제출](openxr-best-practices.md#use-a-single-projection-layer) 합니다.
* [텍스처 배열 사용이 swapchain present](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [기본 색이 swapchain present 형식 사용](openxr-best-practices.md#select-a-swapchain-format)
* [권장 되는 보기 차원 사용](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 플래그 설정 안 함 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* 를 `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0 f와 `maxDepth` 1.0 f로 설정 합니다.

추가 고려 사항으로 인해 성능이 향상 됩니다.
* [16 비트 깊이 형식 사용](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [인스턴스화된 그리기 호출 만들기](openxr-best-practices.md#render-with-texture-array-and-vprt)
