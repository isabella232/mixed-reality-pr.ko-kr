---
title: Windows Mixed Reality에서 WebXR 사용
description: Windows Mixed Reality 몰입 형 헤드셋에서 실행 되는 WebXR 응용 프로그램을 사용 하 고 개발 하는 기본 사항을 알아봅니다.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, 웹 vr, 웹 xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: e49f5f2422c9802f94b63943f8a38949a2969f83
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006943"
---
# <a name="webxr-overview"></a><span data-ttu-id="1db12-104">WebXR 개요</span><span class="sxs-lookup"><span data-stu-id="1db12-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="1db12-105">WebXR 정의</span><span class="sxs-lookup"><span data-stu-id="1db12-105">What is WebXR</span></span>

<span data-ttu-id="1db12-106">**WebXR DEVICE API** 는 **웹** 의 **센서** 및 **헤드 탑재 된 디스플레이** 를 비롯 하 여 **VR (가상 현실)** 및 **AR (보강 된 현실)** 장치에 액세스 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="1db12-107">WebXR device API는 현재 Microsoft Edge에서 사용할 수 있으며 Chrome 버전 79 이상 버전에서는 WebXR을 기본값으로 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="1db12-108">WebXR에서 [caniuse.com](https://caniuse.com/#search=webxr)에 대 한 최신 브라우저 지원 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="1db12-109">[Windows Mixed Reality 및](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)새로운 [기능](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) 섹션에서 새로운 Microsoft Edge에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="1db12-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="1db12-110">WebXR 보기</span><span class="sxs-lookup"><span data-stu-id="1db12-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1db12-111">Microsoft Edge (레거시)는 현재 브라우저에서 사용할 수 없는 사용 되지 않는 API 인 WebVR 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="1db12-112">그러나 새로운 **[Chromium 기반 Edge 브라우저](../../whats-new/new-microsoft-edge.md)** 는 WebXR를 지원 하며 Windows Mixed REALITY의 VR 프로토타입화에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="1db12-113">WebVR는 새 Chromium 기반 Edge 브라우저에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="1db12-114">현재 HoloLens 2에서 WebXR를 프로토타입 하는 방법을 찾고 있는 경우 [Firefox 현실](https://mixedreality.mozilla.org/firefox-reality/)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="1db12-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="1db12-115">브라우저에서 WebXR을 지원 하는지 테스트 하려면 브라우저에서 [WebXR Samples](https://immersive-web.github.io/webxr-samples/) 로 이동 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db12-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="1db12-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1db12-116">See Also</span></span>

* [<span data-ttu-id="1db12-117">WebXR 장치 API 사양</span><span class="sxs-lookup"><span data-stu-id="1db12-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="1db12-118">WebXR 장치 API 설명서</span><span class="sxs-lookup"><span data-stu-id="1db12-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="1db12-119">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="1db12-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="1db12-120">WebXR 샘플</span><span class="sxs-lookup"><span data-stu-id="1db12-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="1db12-121">Windows Mixed Reality 및 새 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1db12-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="1db12-122">몰입 형 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="1db12-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="1db12-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1db12-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="1db12-124">[게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="1db12-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="1db12-125">WebGL에서 손실 된 컨텍스트 처리</span><span class="sxs-lookup"><span data-stu-id="1db12-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="1db12-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="1db12-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="1db12-127">글 Tf</span><span class="sxs-lookup"><span data-stu-id="1db12-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="1db12-128">Babylon.js를 사용 하 여 WebXR 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="1db12-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="1db12-129">몰입 형 웹 커뮤니티 그룹</span><span class="sxs-lookup"><span data-stu-id="1db12-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
