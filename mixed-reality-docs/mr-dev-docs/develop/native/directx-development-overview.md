---
title: 네이티브 개발 개요
description: Windows Mixed Reality Api를 직접 사용 하 여 DirectX 기반 혼합 현실 엔진을 빌드합니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱, 플랫폼 Api, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903128"
---
# <a name="native-development-overview"></a><span data-ttu-id="57c04-104">네이티브 개발 개요</span><span class="sxs-lookup"><span data-stu-id="57c04-104">Native development overview</span></span>

![기본 배너 로고](../images/native_logo_banner.png)

<span data-ttu-id="57c04-106">[Unity](../unity/unity-development-overview.md) , [unreal](../unreal/unreal-development-overview.md) 등의 3d 엔진은 유일 하 게 혼합 된 현실 개발 경로를 사용자에 게 공개 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="57c04-107">DirectX 11 또는 DirectX 12를 사용 하 여 Windows Mixed Reality Api로 직접 코딩 하 여 혼합 현실 앱을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="57c04-108">플랫폼을 직접 활용 하 여 기본적으로 고유한 미들웨어 또는 프레임 워크를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="57c04-109">유지 하려는 기존 WinRT 프로젝트가 있는 경우 주 [winrt 설명서](creating-a-holographic-directx-project.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57c04-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="57c04-110">개발 검사점</span><span class="sxs-lookup"><span data-stu-id="57c04-110">Development checkpoints</span></span>

<span data-ttu-id="57c04-111">다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="57c04-112">1. 시작</span><span class="sxs-lookup"><span data-stu-id="57c04-112">1. Getting started</span></span>

<span data-ttu-id="57c04-113">Windows Mixed Reality는 다음과 같은 [두 가지 종류의 앱을](../../design/app-views.md)지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="57c04-114">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md) 또는 [OpenXR api](openxr.md) 를 사용 하 여 헤드셋 표시를 채우는 사용자에 게 [몰입 형 보기](../../design/app-views.md) 를 렌더링 하는 **혼합 현실 응용 프로그램** (UWP 또는 Win32)</span><span class="sxs-lookup"><span data-stu-id="57c04-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="57c04-115">DirectX, XAML 또는 다른 프레임 워크를 사용 하 여 Windows Mixed Reality 홈의 슬레이트에서 [2d 뷰](../../design/app-views.md#2d-views) 를 렌더링 하는 **2d 앱** (UWP)</span><span class="sxs-lookup"><span data-stu-id="57c04-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="57c04-116">[2d 보기 및 몰입 형 보기](../../design/app-views.md) 에 대 한 DirectX 개발 간의 차이점은 주로 holographic 렌더링 및 공간 입력에 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="57c04-117">UWP 응용 프로그램의 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 또는 Win32 응용 프로그램의 HWND는 필수 이며 거의 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="57c04-118">앱에서 사용할 수 있는 WinRT Api의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="57c04-119">하지만 holographic 기능을 활용 하려면 이러한 Api의 다른 하위 집합을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="57c04-120">예를 들어이 swapchain present 및 프레임은 holographic 응용 프로그램에 대해 시스템에서 관리 되므로 포즈 예측 프레임 루프를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="57c04-121">2. 핵심 구성 요소</span><span class="sxs-lookup"><span data-stu-id="57c04-121">2. Core building blocks</span></span>

<span data-ttu-id="57c04-122">Windows Mixed Reality 응용 프로그램은 다음 Api를 사용 하 여 HoloLens 및 기타 몰입 형 헤드셋에 대 한 [Mixed Reality](../../discover/mixed-reality.md) 환경을 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="57c04-123">특징</span><span class="sxs-lookup"><span data-stu-id="57c04-123">Feature</span></span>  |  <span data-ttu-id="57c04-124">기능</span><span class="sxs-lookup"><span data-stu-id="57c04-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="57c04-125">응시</span><span class="sxs-lookup"><span data-stu-id="57c04-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="57c04-126">사용자가 홀로그램을 확인하여 대상으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="57c04-127">제스처</span><span class="sxs-lookup"><span data-stu-id="57c04-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="57c04-128">앱에 공간 작업 추가</span><span class="sxs-lookup"><span data-stu-id="57c04-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="57c04-129">홀로그램 렌더링</span><span class="sxs-lookup"><span data-stu-id="57c04-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="57c04-130">사용자를 중심으로 하는 정확한 위치에서 홀로그램 그리기</span><span class="sxs-lookup"><span data-stu-id="57c04-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="57c04-131">동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="57c04-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="57c04-132">사용자가 혼합 현실 환경에서 작업을 수행 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="57c04-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="57c04-133">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="57c04-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="57c04-134">가상 메시 오버레이를 사용하여 실제 공간을 매핑하여 환경 경계 표시</span><span class="sxs-lookup"><span data-stu-id="57c04-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="57c04-135">음성</span><span class="sxs-lookup"><span data-stu-id="57c04-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="57c04-136">사용자의 음성 키워드, 구 및 받아쓰기 캡처</span><span class="sxs-lookup"><span data-stu-id="57c04-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="57c04-137">OpenXR [로드맵](openxr.md#roadmap) 설명서에서 예정 및 개발 중인 핵심 기능을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="57c04-138">3. 배포 및 테스트</span><span class="sxs-lookup"><span data-stu-id="57c04-138">3. Deploying and testing</span></span>

<span data-ttu-id="57c04-139">데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="57c04-140">헤드셋에 액세스할 수 없는 경우 [HoloLens 2 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 또는 [Windows Mixed Reality 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="57c04-141">다음 작업</span><span class="sxs-lookup"><span data-stu-id="57c04-141">What's next?</span></span>

<span data-ttu-id="57c04-142">특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="57c04-143">다음 섹션에서는 이미 완료한 초보자 수준 자료를 벗어난 영역으로 안내할 수 있으며, 어려움이 있을 때 유용한 리소스로 안내할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c04-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="57c04-144">이러한 항목과 리소스는 순차적으로 정렬되지 않으므로 자유롭게 이동하여 탐색하세요.</span><span class="sxs-lookup"><span data-stu-id="57c04-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="57c04-145">추가 자료</span><span class="sxs-lookup"><span data-stu-id="57c04-145">Additional resources</span></span>

<span data-ttu-id="57c04-146">OpenXR 게임의 수준을 설정 하려면 아래 링크를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="57c04-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="57c04-147">OpenXR 모범 사례</span><span class="sxs-lookup"><span data-stu-id="57c04-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="57c04-148">OpenXR 성능</span><span class="sxs-lookup"><span data-stu-id="57c04-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="57c04-149">OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="57c04-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="57c04-150">추가 정보</span><span class="sxs-lookup"><span data-stu-id="57c04-150">See also</span></span>
* [<span data-ttu-id="57c04-151">앱 모델</span><span class="sxs-lookup"><span data-stu-id="57c04-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="57c04-152">앱 보기</span><span class="sxs-lookup"><span data-stu-id="57c04-152">App views</span></span>](../../design/app-views.md)
