---
title: OpenXR 성능
description: OpenXR 응용 프로그램의 GPU 성능을 디버깅 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 성능, 최적화, GPU 디버깅, RenderDoc, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613177"
---
# <a name="openxr-performance"></a><span data-ttu-id="f83ce-104">OpenXR 성능</span><span class="sxs-lookup"><span data-stu-id="f83ce-104">OpenXR performance</span></span>

<span data-ttu-id="f83ce-105">HoloLens 2에는를 통해 컴퍼지션 데이터를 제출 하는 다양 한 방법이 있으며,이로 `xrEndFrame` 인해 사후 처리 및 눈에 띄는 성능 저하가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83ce-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="f83ce-106">성능 저하를 방지 하려면 다음 특징을 가진 [ `XrCompositionProjectionLayer` 단일를 제출](openxr-best-practices.md#use-a-single-projection-layer) 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83ce-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="f83ce-107">텍스처 배열 사용이 swapchain present</span><span class="sxs-lookup"><span data-stu-id="f83ce-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="f83ce-108">기본 색이 swapchain present 형식 사용</span><span class="sxs-lookup"><span data-stu-id="f83ce-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="f83ce-109">권장 되는 보기 차원 사용</span><span class="sxs-lookup"><span data-stu-id="f83ce-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="f83ce-110">플래그를 설정 하지 않습니다. `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="f83ce-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="f83ce-111">를 `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0 f와 `maxDepth` 1.0 f로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83ce-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="f83ce-112">성능을 향상 시키려면 다음을 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f83ce-112">For better performance, consider:</span></span>
* [<span data-ttu-id="f83ce-113">16 비트 깊이 형식 사용</span><span class="sxs-lookup"><span data-stu-id="f83ce-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="f83ce-114">인스턴스 그리기 호출 만들기</span><span class="sxs-lookup"><span data-stu-id="f83ce-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
