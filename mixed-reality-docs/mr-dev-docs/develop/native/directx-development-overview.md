---
title: 네이티브 개발 개요
description: Windows Mixed Reality Api를 직접 사용 하 여 DirectX 기반 혼합 현실 엔진을 빌드하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱, 플랫폼 Api, 사용자 지정 엔진, 미들웨어, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: b137fad12740542deb4995485201a9bd0d1d7662
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581045"
---
# <a name="native-development-overview"></a><span data-ttu-id="e2441-104">네이티브 개발 개요</span><span class="sxs-lookup"><span data-stu-id="e2441-104">Native development overview</span></span>

![기본 배너 로고](../images/native_logo_banner.png)

<span data-ttu-id="e2441-106">[Unity](../unity/unity-development-overview.md) , [unreal](../unreal/unreal-development-overview.md) 등의 3d 엔진은 유일 하 게 혼합 된 현실 개발 경로를 사용자에 게 공개 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="e2441-107">DirectX 11 또는 DirectX 12를 사용 하 여 Windows Mixed Reality Api를 사용 하 여 혼합 현실 앱을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="e2441-108">플랫폼 소스로 이동 하 여 기본적으로 고유한 미들웨어 또는 프레임 워크를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e2441-109">유지 하려는 기존 WinRT 프로젝트가 있는 경우 주 [winrt 설명서](creating-a-holographic-directx-project.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2441-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="e2441-110">개발 검사점</span><span class="sxs-lookup"><span data-stu-id="e2441-110">Development checkpoints</span></span>

<span data-ttu-id="e2441-111">다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="e2441-112">1. 시작</span><span class="sxs-lookup"><span data-stu-id="e2441-112">1. Getting started</span></span>

<span data-ttu-id="e2441-113">Windows Mixed Reality는 다음과 같은 [두 가지 종류의 앱을](../../design/app-views.md)지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="e2441-114">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md) 또는 [OpenXR api](openxr.md) 를 사용 하는 UWP 또는 Win32 **Mixed Reality 응용 프로그램** 은 헤드셋 표시를 채우는 [몰입 형 보기](../../design/app-views.md) 를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="e2441-115">DirectX, XAML 또는 다른 프레임 워크를 사용 하 여 Windows Mixed Reality 홈의 슬레이트에서 [2d 뷰](../../design/app-views.md#2d-views) 를 렌더링 하는 **2d 앱** (UWP)</span><span class="sxs-lookup"><span data-stu-id="e2441-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="e2441-116">[2d 보기 및 몰입 형 보기](../../design/app-views.md) 에 대 한 DirectX 개발 간의 차이점은 주로 holographic 렌더링 및 공간 입력에 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="e2441-117">UWP 응용 프로그램의 [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) 또는 Win32 응용 프로그램의 HWND는 필수 이며 거의 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-117">Your UWP application's [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="e2441-118">앱에서 사용할 수 있는 WinRT Api의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="e2441-119">하지만 holographic 기능을 활용 하려면 이러한 Api의 다른 하위 집합을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="e2441-120">예를 들어 holographic 용 시스템 응용 프로그램은 포즈 예측 프레임 루프를 사용 하도록 설정 된이 swapchain present 및 프레임을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="e2441-121">2. 핵심 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e2441-121">2. Core building blocks</span></span>

<span data-ttu-id="e2441-122">Windows Mixed Reality 응용 프로그램은 다음 Api를 사용 하 여 HoloLens 및 기타 몰입 형 헤드셋에 대 한 [Mixed Reality](../../discover/mixed-reality.md) 환경을 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="e2441-123">특징</span><span class="sxs-lookup"><span data-stu-id="e2441-123">Feature</span></span>  |  <span data-ttu-id="e2441-124">기능</span><span class="sxs-lookup"><span data-stu-id="e2441-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="e2441-125">응시</span><span class="sxs-lookup"><span data-stu-id="e2441-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="e2441-126">사용자가 홀로그램을 확인하여 대상으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="e2441-127">제스처</span><span class="sxs-lookup"><span data-stu-id="e2441-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="e2441-128">앱에 공간 작업 추가</span><span class="sxs-lookup"><span data-stu-id="e2441-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="e2441-129">홀로그램 렌더링</span><span class="sxs-lookup"><span data-stu-id="e2441-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="e2441-130">사용자를 중심으로 하는 정확한 위치에서 홀로그램 그리기</span><span class="sxs-lookup"><span data-stu-id="e2441-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="e2441-131">동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="e2441-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="e2441-132">사용자가 혼합 현실 환경에서 작업을 수행 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="e2441-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="e2441-133">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="e2441-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="e2441-134">가상 메시 오버레이를 사용하여 실제 공간을 매핑하여 환경 경계 표시</span><span class="sxs-lookup"><span data-stu-id="e2441-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="e2441-135">음성</span><span class="sxs-lookup"><span data-stu-id="e2441-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="e2441-136">사용자의 음성 키워드, 구 및 받아쓰기 캡처</span><span class="sxs-lookup"><span data-stu-id="e2441-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="e2441-137">OpenXR [로드맵](openxr.md#roadmap) 설명서에서 예정 및 개발 중인 핵심 기능을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="e2441-138">3. 배포 및 테스트</span><span class="sxs-lookup"><span data-stu-id="e2441-138">3. Deploying and testing</span></span>

<span data-ttu-id="e2441-139">HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋에서 OpenXR를 사용 하 여 데스크톱에서 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="e2441-140">헤드셋에 액세스할 수 없는 경우 [HoloLens 2 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 또는 [Windows Mixed Reality 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="e2441-141">다음 작업</span><span class="sxs-lookup"><span data-stu-id="e2441-141">What's next?</span></span>

<span data-ttu-id="e2441-142">특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="e2441-143">다음 섹션에서는 이미 완료 한 초보자 수준 자료를 벗어나는 영역으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="e2441-144">이러한 항목과 리소스는 순차적으로 정렬 되지 않으므로 자유롭게 이동 하 여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2441-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e2441-145">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="e2441-145">Additional resources</span></span>

<span data-ttu-id="e2441-146">OpenXR 게임의 수준을 설정 하려면 아래 링크를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2441-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="e2441-147">OpenXR 모범 사례</span><span class="sxs-lookup"><span data-stu-id="e2441-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="e2441-148">OpenXR 성능</span><span class="sxs-lookup"><span data-stu-id="e2441-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="e2441-149">OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e2441-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="e2441-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2441-150">See also</span></span>
* [<span data-ttu-id="e2441-151">앱 모델</span><span class="sxs-lookup"><span data-stu-id="e2441-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="e2441-152">앱 보기</span><span class="sxs-lookup"><span data-stu-id="e2441-152">App views</span></span>](../../design/app-views.md)