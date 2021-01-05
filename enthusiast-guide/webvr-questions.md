---
title: WebVR Faq
description: 표준 소비자 지원 설명서를 벗어나는 웹 혼합 현실 문제 해결.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, WebVR
ms.openlocfilehash: fd9906ca36c71b1bf959466d90c57e07be0eca5e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725634"
---
# <a name="webvr-faqs"></a><span data-ttu-id="407e0-104">WebVR Faq</span><span class="sxs-lookup"><span data-stu-id="407e0-104">WebVR FAQs</span></span>

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a><span data-ttu-id="407e0-105">Edge에서 VR 콘텐츠를 볼 때 내 컨트롤러가 표시 되지 않는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="407e0-105">Why can’t I see my controllers when viewing VR content from Edge</span></span>

<span data-ttu-id="407e0-106">모든 WebVR 내용이 동작 컨트롤러를 지원 하도록 작성 된 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-106">Not all WebVR content is authored to support motion controllers.</span></span> <span data-ttu-id="407e0-107">WebVR를 사용 하면 콘텐츠 개발자가 게임 컨트롤러나 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-107">WebVR allows content developers to support different types of input, such as game controllers or motion controllers.</span></span> <span data-ttu-id="407e0-108">사이트에 컨트롤러가 표시 되지 않으면 동작 컨트롤러를 지원 하지 않는 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-108">If you don't see your controllers on a site, it probably doesn’t have motion controller support.</span></span>

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a><span data-ttu-id="407e0-109">몰입 형 WebVR 뷰에서 마우스를 사용할 수 없는 이유</span><span class="sxs-lookup"><span data-stu-id="407e0-109">Why can't I use the mouse in an immersive WebVR view</span></span>

<span data-ttu-id="407e0-110">마우스를 사용 하는 것은 WebVR 사양의 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-110">Using a mouse is an optional feature of the WebVR specification.</span></span> <span data-ttu-id="407e0-111">모든 브라우저에서이 기능을 지원 하지는 않지만 마우스 입력을 지원 하도록 모든 WebVR 콘텐츠를 작성 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-111">Not all browsers support this feature, and not all WebVR content is authored to support mouse input.</span></span> <span data-ttu-id="407e0-112">WebVR를 사용 하면 콘텐츠 개발자가 마우스, 키보드, 게임 컨트롤러 또는 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-112">WebVR allows content developers to support different types of input, such as mouse, keyboard, game controllers, or motion controllers.</span></span> <span data-ttu-id="407e0-113">마우스 입력 동작은 브라우저 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-113">Mouse input behavior varies per browser.</span></span> <span data-ttu-id="407e0-114">Microsoft Edge 내에서 웹 사이트 작성자는 마우스 입력이 작동 하기 위해 헤드셋에 프레젠테이션할 때 ' pointerlock '를 사용 하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-114">Within Microsoft Edge, website authors must ensure they take 'pointerlock' when presenting to the headset for mouse input to work.</span></span>

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a><span data-ttu-id="407e0-115">Youtube/Facebook/Vimeo/보호자 등에서 360 대의 비디오를 볼 수 없는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="407e0-115">Why can’t I view 360-degree videos from Youtube/Facebook/Vimeo/The Guardian, etc. from Edge in VR</span></span>

<span data-ttu-id="407e0-116">웹 사이트에서 VR 환경을 브라우저에서 직접 시작할 수 있도록 하는 WebVR 사양이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-116">There's a WebVR specification that lets websites launch VR experiences directly from the browser.</span></span> <span data-ttu-id="407e0-117">이러한 웹 사이트의 작성자는 현재이 사양을 구현 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-117">The authors of these websites haven't implemented this specification at this time.</span></span> <span data-ttu-id="407e0-118">이러한 공급 업체의 VR 콘텐츠를 볼 수 있는 일부 플랫폼에서 다운로드 가능한 앱이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-118">There may be downloadable apps on some platforms that enable viewing of VR content from these vendors.</span></span>

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a><span data-ttu-id="407e0-119">Firefox 또는 Chrome에서 VR를 입력할 수 없는 이유</span><span class="sxs-lookup"><span data-stu-id="407e0-119">Why can’t I enter VR from Firefox or Chrome</span></span>

<span data-ttu-id="407e0-120">WebVR는 현재 Edge의 Windows Mixed Reality 장치 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-120">WebVR is only supported by Windows Mixed Reality devices in Edge at this time.</span></span>

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a><span data-ttu-id="407e0-121">웹 사이트에서 VR를 입력 하는 경우 헤드셋에 빈 화면이 표시 되는 이유</span><span class="sxs-lookup"><span data-stu-id="407e0-121">When I enter VR from a website, why do I see a blank screen in my headset</span></span>

<span data-ttu-id="407e0-122">웹 사이트에서 다중 GPU 컴퓨터 (하이브리드 GPU 랩톱 포함)에 대 한 지원을 구현 하지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-122">The website may not have implemented support for multi GPU machines (including hybrid GPU laptops).</span></span> <span data-ttu-id="407e0-123">다음을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-123">Try to:</span></span>

* <span data-ttu-id="407e0-124">페이지를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-124">Reload the page.</span></span>
* <span data-ttu-id="407e0-125">데스크톱 컴퓨터에서 Microsoft Edge를 표시 하는 모니터와 동일한 그래픽 어댑터에 헤드셋을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-125">On desktop machines, plug the headset into the same graphics adapter as the monitor that is displaying Microsoft Edge.</span></span> <span data-ttu-id="407e0-126">통합 그래픽 어댑터가 아닌 더 높은 전원이 켜진 그래픽 카드에 모두 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-126">Plug both into the higher powered graphics card, not into the integrated graphics adapter.</span></span>

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a><span data-ttu-id="407e0-127">Edge에서 비디오를 시청할 때 VR를 끝내 면 소리는 계속 재생 되지만 가장자리 창은 회색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-127">When I exit VR when watching a video from Edge, the sound continues playing but the Edge window is grayed out</span></span>

<span data-ttu-id="407e0-128">이 문제는 혼합 현실 절벽 집의 Edge에서 WebVR를 실행할 때 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-128">This is a known issue when running WebVR from Edge in the Mixed Reality Cliff House.</span></span> <span data-ttu-id="407e0-129">이 문제를 해결 하려면 windows 단추 대신 키보드에서 esc 키를 눌러 WebVR 환경을 종료 하거나 선택 하 여 회색으로 표시 된 가장자리 창을 활성화 한 다음 비디오를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-129">To resolve it, press escape on the keyboard instead of the windows button to exit the WebVR experience, or activate the greyed out Edge window by selecting it and then stop the video.</span></span>

## <a name="can-i-use-webvr-on-the-hololens"></a><span data-ttu-id="407e0-130">HoloLens에서 WebVR을 사용할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="407e0-130">Can I use WebVR on the HoloLens</span></span>

<span data-ttu-id="407e0-131">Microsoft는이 시점에서 HoloLens WebVR에 대 한 어떠한 정보도 발표 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-131">Microsoft hasn't announced anything about WebVR on the HoloLens at this point.</span></span>

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a><span data-ttu-id="407e0-132">Edge에서 WebVR 콘텐츠를 볼 때 평면도가 바닥에 표시 되는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="407e0-132">Why is my view at floor level when viewing WebVR content from Edge</span></span>

<span data-ttu-id="407e0-133">웹 사이트가 Windows Mixed Reality 헤드셋을 제대로 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-133">The website doesn't properly support Windows Mixed Reality headsets.</span></span> <span data-ttu-id="407e0-134">이 문제의 해결 방법:</span><span class="sxs-lookup"><span data-stu-id="407e0-134">To work around this:</span></span>

1. <span data-ttu-id="407e0-135">헤드셋을 공간 바닥에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-135">Place the headset on the floor of your space.</span></span>
2. <span data-ttu-id="407e0-136">바탕 화면에서 Microsoft Edge를 사용 하 여 WebVR 페이지로 이동 합니다 (혼합 현실에 있지 않음).</span><span class="sxs-lookup"><span data-stu-id="407e0-136">Navigate to the WebVR page using Microsoft Edge on your desktop (not within mixed reality).</span></span>
3. <span data-ttu-id="407e0-137">"VR 입력"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-137">Select "Enter VR".</span></span>
4. <span data-ttu-id="407e0-138">환경이 전체로 전환 될 때까지 5 ~ 10 초 정도 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-138">Wait five to 10 seconds for the experience to fully enter immersive mode.</span></span>
5. <span data-ttu-id="407e0-139">헤드셋에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-139">Put on the headset.</span></span>

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a><span data-ttu-id="407e0-140">일부 WebVR 환경에서는 디스플레이가 낮은 해상도입니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-140">The display is low resolution in some WebVR experiences</span></span>

<span data-ttu-id="407e0-141">이러한 웹 사이트는 고해상도 헤드셋을 제대로 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-141">Those websites don't properly support high-resolution headsets.</span></span> <span data-ttu-id="407e0-142">이 문제의 해결 방법:</span><span class="sxs-lookup"><span data-stu-id="407e0-142">To work around this:</span></span>

* <span data-ttu-id="407e0-143">혼합 현실 절벽 집이 아닌 데스크톱에서 WebVR를 시작 하는 경우 "VR 입력"을 선택 하기 전에 창이 최대화 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-143">If launching WebVR from the desktop (rather than the mixed reality Cliff House), ensure the window is maximized before selecting "Enter VR".</span></span>
* <span data-ttu-id="407e0-144">VR를 입력 한 후에 Microsoft Edge 창의 크기를 조정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="407e0-144">Avoid resizing the Microsoft Edge window after you have entered VR.</span></span>

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a><span data-ttu-id="407e0-145">브라우저 탭을 변경할 때 WebVR 몰입 보기가 종료 되는 이유</span><span class="sxs-lookup"><span data-stu-id="407e0-145">Why does the WebVR immersive view exit when I change browser tabs</span></span>

<span data-ttu-id="407e0-146">이는 예상된 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-146">This is expected behavior.</span></span> <span data-ttu-id="407e0-147">보안상의 이유로 활성 브라우저 탭만 연결 된 헤드셋에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-147">For security reasons, only the active browser tab can access connected headsets.</span></span>

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a><span data-ttu-id="407e0-148">특정 WebVR 환경에서 오디오를 듣지 못하는 이유</span><span class="sxs-lookup"><span data-stu-id="407e0-148">Why can't I hear audio on a particular WebVR experience</span></span>

<span data-ttu-id="407e0-149">이 웹 사이트는 Microsoft Edge에서 현재 지원 하지 않는 OGG 오디오 파일 형식을 사용 하 고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-149">The website may be using the OGG audio file format, which Microsoft Edge doesn't currently support.</span></span>

<span data-ttu-id="407e0-150">[문제 추적기](https://developer.microsoft.com/microsoft-edge/platform/issues/)에서 또는 [#EdgeBug 해시 태그](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)를 사용 하 여 Twitter를 통해 Microsoft Edge 브라우저 팀에 직접 끊어진 사이트를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-150">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a><span data-ttu-id="407e0-151">햅 피드백이 동작 컨트롤러가 있는 WebVR에서 작동 하지 않는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="407e0-151">Why does haptic feedback not work in WebVR with motion controllers</span></span>

<span data-ttu-id="407e0-152">Microsoft Edge는 현재 WebVR 게임 프로그램 API 확장에서 haptics을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="407e0-152">Microsoft Edge doesn't currently support haptics on the WebVR gamepad API extensions.</span></span>