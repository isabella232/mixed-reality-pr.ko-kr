---
title: Windows Mixed Reality에서 WebXR 사용
description: Windows Mixed Reality 몰입 형 헤드셋에서 실행 되는 WebXR 응용 프로그램을 사용 하 고 개발 하는 기본 사항을 알아봅니다.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, 웹 vr, 웹 xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600112"
---
# <a name="webxr-overview"></a><span data-ttu-id="09e42-104">WebXR 개요</span><span class="sxs-lookup"><span data-stu-id="09e42-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="09e42-105">WebXR 정의</span><span class="sxs-lookup"><span data-stu-id="09e42-105">What is WebXR</span></span>

<span data-ttu-id="09e42-106">[**WebXR DEVICE API**](https://www.w3.org/TR/webxr/) 는 **웹** 의 **센서** 및 **헤드 탑재 된 디스플레이** 를 비롯 하 여 **VR (가상 현실)** 및 **AR (보강 된 현실)** 장치에 액세스 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="09e42-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="09e42-107">WebXR device API는 현재 Microsoft Edge에서 사용할 수 있으며 Chrome 버전 79 이상 버전에서는 WebXR을 기본값으로 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e42-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="09e42-108">WebXR에서 [caniuse.com](https://caniuse.com/#search=webxr)에 대 한 최신 브라우저 지원 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e42-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="09e42-109">WebXR 보기</span><span class="sxs-lookup"><span data-stu-id="09e42-109">Viewing WebXR</span></span>

<span data-ttu-id="09e42-110">[Windows Mixed reality와 새로운 Microsoft Edge](../../whats-new/new-microsoft-edge.md) 및 [Firefox 현실](https://mixedreality.mozilla.org/firefox-reality/)에서 WebXR experinces를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e42-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="09e42-111">브라우저에서 WebXR을 지원 하는지 테스트 하려면 브라우저에서 [WebXR Samples](https://immersive-web.github.io/webxr-samples/) 로 이동 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e42-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="09e42-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09e42-112">See Also</span></span>

* [<span data-ttu-id="09e42-113">Babylon.js를 사용 하 여 WebXR 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="09e42-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="09e42-114">WebXR 장치 API 사양</span><span class="sxs-lookup"><span data-stu-id="09e42-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="09e42-115">WebXR 장치 API 설명서</span><span class="sxs-lookup"><span data-stu-id="09e42-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="09e42-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="09e42-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="09e42-117">WebXR 샘플</span><span class="sxs-lookup"><span data-stu-id="09e42-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="09e42-118">Windows Mixed Reality 및 새 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="09e42-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="09e42-119">몰입 형 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="09e42-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="09e42-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="09e42-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="09e42-121">[게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="09e42-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="09e42-122">WebGL에서 손실 된 컨텍스트 처리</span><span class="sxs-lookup"><span data-stu-id="09e42-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="09e42-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="09e42-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="09e42-124">glTF</span><span class="sxs-lookup"><span data-stu-id="09e42-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="09e42-125">몰입 형 웹 커뮤니티 그룹</span><span class="sxs-lookup"><span data-stu-id="09e42-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)