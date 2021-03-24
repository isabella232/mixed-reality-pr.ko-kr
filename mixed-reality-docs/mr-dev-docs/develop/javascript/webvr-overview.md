---
title: WebVR 개요
description: Windows Mixed Reality 몰입 형 헤드셋에서 실행 되는 WebVR 응용 프로그램을 사용 하 고 개발 하는 기본 사항을 알아봅니다.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ROBOTS: NOINDEX
ms.openlocfilehash: dba3ca6b0cb9404f488db0b69a5bd89d6093a3ef
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909067"
---
# <a name="webvr-overview"></a><span data-ttu-id="02f1a-104">WebVR 개요</span><span class="sxs-lookup"><span data-stu-id="02f1a-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02f1a-105">**WebVR 1.1 api** 는 더 이상 사용 되지 않으며 **WebXR Device api** s로 대체 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-105">**WebVR 1.1 API** s are deprecated and replaced by **WebXR Device API** s.</span></span>

<span data-ttu-id="02f1a-106">WebVR 1.1 Api는 Chrome 및 새 Microsoft Edge에서 더 이상 사용 되지 않고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="02f1a-107">WebVR Api는 WebXR 장치 Api로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="02f1a-108">[Caniuse.com](https://caniuse.com/#search=webvr)에서 현재 WebVR api를 지 원하는 브라우저 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="02f1a-109">Windows Mixed Reality 모던 헤드셋에서 WebVR 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="02f1a-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="02f1a-110">**이전 버전의 Microsoft Edge (15-18)** 를 사용 하 여 몰입 형 헤드셋의 WebVR 콘텐츠에 액세스 하기 위한 지침은 [열성적인 가이드](/windows/mixed-reality/enthusiast-guide/webvr)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="02f1a-111">Edge 브라우저 검색 창에서 "edge://version/"를 입력 하 여 edge 버전을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02f1a-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="02f1a-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02f1a-112">See Also</span></span>

* [<span data-ttu-id="02f1a-113">WebXR 개요</span><span class="sxs-lookup"><span data-stu-id="02f1a-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="02f1a-114">WebXR 장치 API 사양</span><span class="sxs-lookup"><span data-stu-id="02f1a-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="02f1a-115">Windows Mixed Reality 및 새 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="02f1a-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="02f1a-116">WebVR 정보</span><span class="sxs-lookup"><span data-stu-id="02f1a-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="02f1a-117">WebVR 사양</span><span class="sxs-lookup"><span data-stu-id="02f1a-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="02f1a-118">[WebVR API](/previous-versions//mt806281(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="02f1a-118">[WebVR API](/previous-versions//mt806281(v=vs.85))</span></span>
* <span data-ttu-id="02f1a-119">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="02f1a-119">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="02f1a-120">[게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="02f1a-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="02f1a-121">WebGL에서 손실 된 컨텍스트 처리</span><span class="sxs-lookup"><span data-stu-id="02f1a-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="02f1a-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="02f1a-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="02f1a-123">글 Tf</span><span class="sxs-lookup"><span data-stu-id="02f1a-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="02f1a-124">Babylon.js를 사용 하 여 WebVR 사용</span><span class="sxs-lookup"><span data-stu-id="02f1a-124">Using Babylon.js to enable WebVR</span></span>](/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)