---
title: Windows Mixed Reality에서 WebVR 사용
description: WebVR 및 Windows Mixed Reality 헤드셋에서 Microsoft Edge와 함께 사용 하는 방법을 설명 합니다.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, WebVR, Edge, Microsoft Edge, 웹 검색
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131857"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="baddc-104">Windows Mixed Reality에서 WebVR 사용</span><span class="sxs-lookup"><span data-stu-id="baddc-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="baddc-105">대부분의 최신 웹 브라우저에서는 WebVR를 사용 하는 것이 더 이상 지원 되지 않으며,이는 VR 헤드셋을 위한 몰입 형 웹 환경을 만들기 위한 새로운 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="baddc-106">[새 Microsoft Edge](using-microsoft-edge.md) for WebXR 지원을 설치 하세요.</span><span class="sxs-lookup"><span data-stu-id="baddc-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="baddc-107">WebVR이란?</span><span class="sxs-lookup"><span data-stu-id="baddc-107">What is WebVR</span></span>

<span data-ttu-id="baddc-108">[WebVR](https://webvr.info) 는 브라우저에서 VR 경험을 가능 하 게 하는 공개 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="baddc-109">웹 사이트에서 WebVR 지원을 구현 하 고 3D 콘텐츠를 제공 하는 경우 사용자 동의를 사용 하 여 헤드셋에 몰입 형 콘텐츠를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="baddc-110">WebVR와 VR의 웹 검색 간의 차이점은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="baddc-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="baddc-111">WebVR는 웹 사이트 작성자가 페이지에 VR 기능을 추가할 수 있는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="baddc-112">WebVR API는 페이지에서 3D 콘텐츠 (예: 360 학위 video, 3D 모델 또는 3D 게임)를 전체 헤드셋에 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="baddc-113">**예:** [Cnn.com/vr](http://cnn.com/vr)에서 360 비디오 보기</span><span class="sxs-lookup"><span data-stu-id="baddc-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="baddc-114">페이지에서 WebVR를 지 원하는 경우 단추 또는 다른 UI 요소를 추가 하 여 클릭 하 여 VR를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="baddc-115">VR에서 웹을 검색 하는 것은 Cliffhouse 내에서 2D 앱 슬레이트로 헤드셋을 입고 있는 동안 Edge 브라우저를 사용 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="baddc-116">모든 websites 지원 WebVR</span><span class="sxs-lookup"><span data-stu-id="baddc-116">Do all websites support WebVR</span></span>

<span data-ttu-id="baddc-117">아니요.</span><span class="sxs-lookup"><span data-stu-id="baddc-117">No.</span></span> <span data-ttu-id="baddc-118">웹 사이트 작성자는 WebVR을 사용 하도록 옵트인 (opt in) 해야 하며, 특정 브라우저, 헤드셋 및 컨트롤러에 대해 최적화 된 사이트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="baddc-119">예를 들어 일부 WebVR 콘텐츠는 모바일 VR 장치에 대해서만 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="baddc-120">또한 웹 사이트는 WebVR 콘텐츠를 명시적으로 만들고 제공 해야 한다는 점에 유의 하세요.</span><span class="sxs-lookup"><span data-stu-id="baddc-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="baddc-121">WebVR 호환 콘텐츠가 있는 사이트의 수는 매일 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="baddc-122">WebVR를 사용 하 여 Microsoft Edge에서 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="baddc-123">아니요.</span><span class="sxs-lookup"><span data-stu-id="baddc-123">No.</span></span> <span data-ttu-id="baddc-124">Edge에서 WebVR를 사용 하려면 Windows Mixed Reality 헤드셋을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="baddc-125">그러나 다른 브라우저에서 WebVR 콘텐츠에 액세스할 수 있습니다. 에서 호환 되는 장치 및 브라우저의 전체 목록을 참조 하세요. [WebVR](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="baddc-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="baddc-126">WebVR 개발자 설명서는 어디서 찾을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="baddc-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="baddc-127">개발자 설명서는 여기에 있습니다. [WebVR Developer 설명서](https://docs.microsoft.com/microsoft-edge/webvr/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="baddc-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="baddc-128">Windows Mixed Reality에서 작동 하지 않는 WebVR가 있는 웹 사이트를 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="baddc-129">뭐 할까요</span><span class="sxs-lookup"><span data-stu-id="baddc-129">What do I do</span></span>

<span data-ttu-id="baddc-130">[문제 추적기](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)에서 또는 [#EdgeBug 해시 태그](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)를 사용 하 여 Twitter를 통해 Microsoft Edge 브라우저 팀에 직접 끊어진 사이트를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="baddc-131">범주 아래에서 Windows 피드백 허브 앱을 사용 하 여 버그를 기록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="baddc-132">Microsoft Edge > 웹 사이트 문제</span><span class="sxs-lookup"><span data-stu-id="baddc-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="baddc-133">WebVR가 작동 하는지 테스트 하는 데 유용한 페이지는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="baddc-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="baddc-134">[Webvr.info 샘플](http://webvr.info/samples/XX-vr-controllers.html)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="baddc-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="baddc-135">WebVR 설정 어떻게 할까요?</span><span class="sxs-lookup"><span data-stu-id="baddc-135">How do I set up WebVR</span></span>

<span data-ttu-id="baddc-136">Windows Mixed Reality 헤드셋 (하드웨어 또는 시뮬레이션 사용)에서 WebVR 콘텐츠를 경험 하려면 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>

1. <span data-ttu-id="baddc-137">헤드셋이 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="baddc-138">바탕 화면에서 또는 혼합 현실에서 Microsoft Edge를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="baddc-139">WebVR 사용 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="baddc-140">페이지 내에서 VR 입력 단추를 클릭 합니다 .이 단추의 위치 및 시각적 표현은 웹 사이트 마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="baddc-141">다음과 유사 하 게 표시 될 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="baddc-141">It may look similar to:</span></span>\
   ![VR Goggles 이미지](images/75px-enter-vr.png)
5. <span data-ttu-id="baddc-143">처음에 특정 도메인에서 VR를 입력 하려고 하면 브라우저는 몰입 형 보기 사용에 대 한 동의를 요청 하 고 예를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![특정 도메인에 대 한 첫 번째 시도를 시작 하는 데 표시 되는 동의 UI](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="baddc-145">헤드셋은 WebVR 콘텐츠를 표시 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="baddc-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="baddc-146">추가 정보</span><span class="sxs-lookup"><span data-stu-id="baddc-146">See also</span></span>

* [<span data-ttu-id="baddc-147">> WebVR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="baddc-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="baddc-148">첫 번째 WebVR 환경을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="baddc-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="baddc-149">Windows Mixed Reality에서 게임과 앱 사용</span><span class="sxs-lookup"><span data-stu-id="baddc-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="baddc-150">혼합 현실 집</span><span class="sxs-lookup"><span data-stu-id="baddc-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="baddc-151">추적 시스템</span><span class="sxs-lookup"><span data-stu-id="baddc-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="baddc-152">동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="baddc-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="baddc-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="baddc-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="baddc-154">사용자 의견 보내기</span><span class="sxs-lookup"><span data-stu-id="baddc-154">Filing feedback</span></span>](filing-feedback.md)
