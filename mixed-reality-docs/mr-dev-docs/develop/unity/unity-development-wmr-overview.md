---
title: VR용 Unity 개발
description: VR 및 Windows Mixed Reality 몰입형 헤드셋에 대해 Unity에서 혼합 현실 앱 빌드를 시작합니다.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 가상 현실이란, 증강 현실이란, MRTK, mixed reality toolkit, 음성 입력, 위치를 찾을 수 있는 카메라, 에뮬레이터, Azure, 자습서
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528715"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="ea33d-104">VR 및 Windows Mixed Reality용 Unity 개발</span><span class="sxs-lookup"><span data-stu-id="ea33d-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity 배너 로고](../images/unity_logo_banner.png)

<span data-ttu-id="ea33d-106">Unity를 처음 접하는 경우 계속하기 전에 Unity 학습 플랫폼에서 초보자 수준 [자습서](https://unity3d.com/learn/tutorials)를 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="ea33d-107">또한 [Unity Mixed Reality 포럼](https://forum.unity3d.com/forums/hololens.102/)을 방문하여 혼합 현실 앱을 빌드하는 온라인 커뮤니티에 참여하는 것도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="ea33d-108">거친 세계에서는 어떤 멋진 자산 또는 솔루션을 찾을 수 있는지 전혀 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="ea33d-109">MRTK를 시작할 준비가 되면 아래 개발 검사점으로 이동하세요!</span><span class="sxs-lookup"><span data-stu-id="ea33d-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea33d-110">Windows Mixed Reality 몰입형 헤드셋으로 가져오려는 기존 Unity 프로젝트가 있는 경우 **[포트 가이드](../porting-apps/porting-overview.md)** 를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="ea33d-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="ea33d-111">개발 검사점</span><span class="sxs-lookup"><span data-stu-id="ea33d-111">Development checkpoints</span></span>

<span data-ttu-id="ea33d-112">다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="ea33d-113">1. 시작</span><span class="sxs-lookup"><span data-stu-id="ea33d-113">1. Getting started</span></span>

<span data-ttu-id="ea33d-114">Windows Mixed Reality 및 VR 개발을 위해 수동으로 변경해야 하는 몇 가지 Unity 설정 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="ea33d-115">이러한 설정은 두 가지 범주, 즉 프로젝트별 및 장면별 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="ea33d-116">이 섹션을 마치면 도구와 프로젝트 설정을 통해 자신만의 앱을 만들 수 있습니다!</span><span class="sxs-lookup"><span data-stu-id="ea33d-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="ea33d-117">검사점</span><span class="sxs-lookup"><span data-stu-id="ea33d-117">Checkpoint</span></span>  |  <span data-ttu-id="ea33d-118">결과</span><span class="sxs-lookup"><span data-stu-id="ea33d-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ea33d-119">최신 도구 설치</span><span class="sxs-lookup"><span data-stu-id="ea33d-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="ea33d-120">최신 Unity 패키지를 다운로드 및 설치하고, 혼합 현실에 맞게 프로젝트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="ea33d-121">WMR용 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="ea33d-121">Configuring your project for WMR</span></span>](windows-xr-plugin.md) | <span data-ttu-id="ea33d-122">홀로그램 및 VR 디스플레이 디바이스에서 디지털 콘텐츠를 렌더링하는 애플리케이션을 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="ea33d-123">프로젝트 설정에 대한 자세한 내용은 Unity 프로젝트 [구성 가이드](choosing-unity-version.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea33d-123">Check out our Unity project [configuration guide](choosing-unity-version.md) for more information on setting up your projects.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="ea33d-124">2. 핵심 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ea33d-124">2. Core building blocks</span></span>

<span data-ttu-id="ea33d-125">새로운 몰입형 프로젝트를 시작한 후에는 몰입형 앱을 개발하기 위해 몇 가지 기본 구성 요소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-125">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="ea33d-126">혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-126">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="ea33d-127">한 번에 모두 필요하지 않을 수도 있지만 일찍 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-127">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="ea33d-128">아래에 나열된 핵심 구성 요소를 살펴본 후 VR 프로젝트에 통합할 수 있는 모든 기능을 갖춘 도구 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-128">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

|  <span data-ttu-id="ea33d-129">기능</span><span class="sxs-lookup"><span data-stu-id="ea33d-129">Feature</span></span>  |  <span data-ttu-id="ea33d-130">기능</span><span class="sxs-lookup"><span data-stu-id="ea33d-130">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="ea33d-131">카메라</span><span class="sxs-lookup"><span data-stu-id="ea33d-131">Camera</span></span>](../unity/camera-in-unity.md) | <span data-ttu-id="ea33d-132">Mixed Reality 앱에서 시각적 품질 및 홀로그램 안정성을 완벽하게 최적화</span><span class="sxs-lookup"><span data-stu-id="ea33d-132">Fully optimize visual quality and hologram stability in your Mixed Reality apps</span></span> |
| [<span data-ttu-id="ea33d-133">세계 잠금 및 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="ea33d-133">World locking and spatial anchors</span></span>](spatial-anchors-in-unity.md) | <span data-ttu-id="ea33d-134">안정화 문제 해결, 카메라 조정 및 안정적인 좌표계 솔루션 통합</span><span class="sxs-lookup"><span data-stu-id="ea33d-134">Solve stabilization issues, camera adjustment, and integrate a stable coordinate system solution</span></span> || [<span data-ttu-id="ea33d-135">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ea33d-135">Motion controllers</span></span>](../unity/motion-controllers-in-unity.md) | <span data-ttu-id="ea33d-136">혼합 현실 앱에 공간 작업 추가</span><span class="sxs-lookup"><span data-stu-id="ea33d-136">Add spatial actions to your Mixed Reality apps</span></span> |
| [<span data-ttu-id="ea33d-137">제스처</span><span class="sxs-lookup"><span data-stu-id="ea33d-137">Gestures</span></span>](../unity/gestures-in-unity.md) | <span data-ttu-id="ea33d-138">혼합 현실 경험에서 손 제스처를 입력으로 사용</span><span class="sxs-lookup"><span data-stu-id="ea33d-138">Use hand gestures as input in your Mixed Reality experiences</span></span> |
| [<span data-ttu-id="ea33d-139">공간 음향</span><span class="sxs-lookup"><span data-stu-id="ea33d-139">Spatial sound</span></span>](../unity/spatial-sound-in-unity.md) | <span data-ttu-id="ea33d-140">몰입형 3D 오디오를 사용하여 앱 향상</span><span class="sxs-lookup"><span data-stu-id="ea33d-140">Enhance your apps with immersive 3D audio</span></span> |
| [<span data-ttu-id="ea33d-141">Text</span><span class="sxs-lookup"><span data-stu-id="ea33d-141">Text</span></span>](../unity/text-in-unity.md) | <span data-ttu-id="ea33d-142">관리 가능한 크기 및 품질 렌더링을 사용하는 선명한 고품질 텍스트 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea33d-142">Get sharp, high-quality text that has a manageable size and quality rendering</span></span> |
| [<span data-ttu-id="ea33d-143">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="ea33d-143">Voice input</span></span>](../unity/voice-input-in-unity.md) | <span data-ttu-id="ea33d-144">사용자의 음성 키워드, 구 및 받아쓰기 캡처</span><span class="sxs-lookup"><span data-stu-id="ea33d-144">Capture spoken keywords, phrases, and dictation from your users</span></span>|

### <a name="3-advanced-features"></a><span data-ttu-id="ea33d-145">3. 고급 기능</span><span class="sxs-lookup"><span data-stu-id="ea33d-145">3. Advanced features</span></span>

<span data-ttu-id="ea33d-146">몰입형 애플리케이션에서 역할을 수행하는 다른 주요 기능은 추가 패키지 또는 설정 없이 Unity API를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-146">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="ea33d-147">Unity에서 제공하는 고급 기능을 자세히 살펴본 후에는 더 깊고 복잡한 VR 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-147">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="ea33d-148">기능</span><span class="sxs-lookup"><span data-stu-id="ea33d-148">Feature</span></span>  |  <span data-ttu-id="ea33d-149">기능</span><span class="sxs-lookup"><span data-stu-id="ea33d-149">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="ea33d-150">추적 손실</span><span class="sxs-lookup"><span data-stu-id="ea33d-150">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="ea33d-151">디바이스가 애플리케이션 세계 공간에서 자체를 찾을 수 없는 시나리오를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-151">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="ea33d-152">키보드 입력</span><span class="sxs-lookup"><span data-stu-id="ea33d-152">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="ea33d-153">현실 세계 및 Mixed Reality 키보드의 입력을 앱에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-153">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="ea33d-154">4. 디바이스 또는 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="ea33d-154">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="ea33d-155">홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 Unity Visual Studio 솔루션을 내보내고 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-155">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="ea33d-156">해당 VS 솔루션을 직접 사용하는 경우 실제 또는 시뮬레이션된 디바이스에서 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-156">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="ea33d-157">이 섹션이 완료되면 개발 요구 사항에 맞는 디바이스 또는 에뮬레이터에 애플리케이션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-157">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="ea33d-158">Windows Mixed Reality 몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="ea33d-158">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="ea33d-159">Windows Mixed Reality 몰입형 헤드셋 시뮬레이터</span><span class="sxs-lookup"><span data-stu-id="ea33d-159">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="ea33d-160">다음 작업</span><span class="sxs-lookup"><span data-stu-id="ea33d-160">What's next?</span></span>

<span data-ttu-id="ea33d-161">특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-161">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="ea33d-162">다음 섹션에서는 이미 완료한 초보자 수준 자료와 중단되는 경우 유용한 리소스 영역으로 모두 안내할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-162">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="ea33d-163">이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 이동하여 살펴보세요!</span><span class="sxs-lookup"><span data-stu-id="ea33d-163">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="ea33d-164">포팅</span><span class="sxs-lookup"><span data-stu-id="ea33d-164">Porting</span></span>

<span data-ttu-id="ea33d-165">포팅하려는 기존 앱이 있는 경우 아래 나열된 문서가 다음 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-165">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="ea33d-166">VR 앱을 Windows Mixed Reality로 포팅</span><span class="sxs-lookup"><span data-stu-id="ea33d-166">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="ea33d-167">Windows Mixed Reality용 SteamVR 앱 업데이트</span><span class="sxs-lookup"><span data-stu-id="ea33d-167">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="ea33d-168">추가 자료</span><span class="sxs-lookup"><span data-stu-id="ea33d-168">Additional resources</span></span>

<span data-ttu-id="ea33d-169">혼합 현실 세계로 직접 들어가기 전에 아래에 나열된 추가 설명서를 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea33d-169">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="ea33d-170">VR 마니아 가이드</span><span class="sxs-lookup"><span data-stu-id="ea33d-170">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="ea33d-171">Unity 자산 스토어</span><span class="sxs-lookup"><span data-stu-id="ea33d-171">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="ea33d-172">참조</span><span class="sxs-lookup"><span data-stu-id="ea33d-172">See also</span></span> 

* [<span data-ttu-id="ea33d-173">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="ea33d-173">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ea33d-174">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="ea33d-174">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ea33d-175">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="ea33d-175">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="ea33d-176">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="ea33d-176">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)