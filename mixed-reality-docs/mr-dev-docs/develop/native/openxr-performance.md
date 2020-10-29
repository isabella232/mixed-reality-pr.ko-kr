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
# <a name="openxr-performance"></a><span data-ttu-id="c46a8-104">OpenXR 성능</span><span class="sxs-lookup"><span data-stu-id="c46a8-104">OpenXR performance</span></span>

<span data-ttu-id="c46a8-105">HoloLens 2에는 여러 가지 방법으로 컴퍼지션 데이터를 제출 하 여 `xrEndFrame` 사후 처리가 발생 하 여 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c46a8-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="c46a8-106">성능 penalities을 방지 하려면 다음 특성을 사용 하 여 [ `XrCompositionProjectionLayer` 단일를 제출](openxr-best-practices.md#use-a-single-projection-layer) 합니다.</span><span class="sxs-lookup"><span data-stu-id="c46a8-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="c46a8-107">텍스처 배열 사용이 swapchain present</span><span class="sxs-lookup"><span data-stu-id="c46a8-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="c46a8-108">기본 색이 swapchain present 형식 사용</span><span class="sxs-lookup"><span data-stu-id="c46a8-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="c46a8-109">권장 되는 보기 차원 사용</span><span class="sxs-lookup"><span data-stu-id="c46a8-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="c46a8-110">플래그 설정 안 함 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="c46a8-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="c46a8-111">를 `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0 f와 `maxDepth` 1.0 f로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c46a8-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="c46a8-112">추가 고려 사항으로 인해 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c46a8-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="c46a8-113">16 비트 깊이 형식 사용</span><span class="sxs-lookup"><span data-stu-id="c46a8-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="c46a8-114">인스턴스화된 그리기 호출 만들기</span><span class="sxs-lookup"><span data-stu-id="c46a8-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
