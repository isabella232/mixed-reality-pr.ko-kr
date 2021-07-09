---
title: HoloLens용 Unity 개발
description: 큐레이트된 검사점 경험을 통해 Unity 및 HoloLens에서 혼합 현실 앱 빌드를 시작합니다.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 가상 현실이란, 증강 현실이란, MRTK, mixed reality toolkit, 공간 매핑, 음성 입력, 위치를 찾을 수 있는 카메라, 에뮬레이터, Azure, 자습서
ms.openlocfilehash: b6d8d44851813f340997c41b2f25104b51dee2fa
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394297"
---
# <a name="unity-development-for-hololens"></a><span data-ttu-id="8f3e7-104">HoloLens용 Unity 개발</span><span class="sxs-lookup"><span data-stu-id="8f3e7-104">Unity development for HoloLens</span></span>

![Unity 배너 로고](../images/unity_logo_banner.png)

<span data-ttu-id="8f3e7-106">Unity는 시장을 선도하는 실시간 개발 플랫폼 중 하나로, C++로 작성된 기본 런타임 코드를 제공하며 모든 개발 스크립팅이 C#에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-106">Unity is one of the leading real-time development platforms on the market, with underlying runtime code written in C++ and all development scripting is done in C#.</span></span> <span data-ttu-id="8f3e7-107">Unity는 게임, 영화 및 애니메이션 영화 예술을 빌드하거나 건축 또는 엔지니어링 개념을 가상 세계에 렌더링하려는 사용자를 지원할 수 있는 인프라를 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-107">Whether you're looking to build games, movies and animation cinematics, or even render architectural or engineering concepts in a virtual world, Unity has the infrastructure to support you.</span></span> <span data-ttu-id="8f3e7-108">시작할 준비가 되면 아래 개발 검사점으로 이동하세요!</span><span class="sxs-lookup"><span data-stu-id="8f3e7-108">When you're ready to get started, head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f3e7-109">HoloLens 2로 가져오려는 기존 Unity 프로젝트가 있는 경우 **[포트 가이드](../porting-apps/porting-overview.md)** 를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-109">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="8f3e7-110">HTK, MRTK v1 또는 SteamVR을 사용하는 프로젝트에 대한 가이드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-110">We have guides for projects that are using HTK, MRTK v1, or SteamVR.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="8f3e7-111">개발 검사점</span><span class="sxs-lookup"><span data-stu-id="8f3e7-111">Development checkpoints</span></span>

<span data-ttu-id="8f3e7-112">다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="8f3e7-113">[Holograms 샘플 애플리케이션 디자인](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)을 아직 살펴보지 않았다면 이를 다운로드하여 Mixed Reality UX의 기본 사항을 숙지하는 데 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-113">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="8f3e7-114">1. 시작</span><span class="sxs-lookup"><span data-stu-id="8f3e7-114">1. Getting started</span></span>

<span data-ttu-id="8f3e7-115">Unity에서 개발하는 가장 쉬운 방법은 Mixed Reality Toolkit를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-115">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8f3e7-116">MRTK는 Mixed Reality 프로젝트를 자동으로 설정하고, 개발 프로세스를 가속화할 수 있는 기능 세트를 제공하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-116">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="8f3e7-117">이 섹션이 완료되면 Mixed Reality Toolkit, Mixed Reality 앱에 맞게 적절하게 구성된 개발 환경 및 직접 빌드한 Unity에서 작동하는 MRTK 프로젝트에 대해 기본적으로 이해할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-117">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="8f3e7-118">검사점</span><span class="sxs-lookup"><span data-stu-id="8f3e7-118">Checkpoint</span></span>  |  <span data-ttu-id="8f3e7-119">결과</span><span class="sxs-lookup"><span data-stu-id="8f3e7-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="8f3e7-120">Mixed Reality Toolkit 소개</span><span class="sxs-lookup"><span data-stu-id="8f3e7-120">Introducing the Mixed Reality Toolkit</span></span>](mrtk-getting-started.md) | <span data-ttu-id="8f3e7-121">Mixed Reality Toolkit 및 이 도구 키트에서 제공해야 하는 항목을 숙지하여 과정을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-121">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="8f3e7-122">Mixed Reality Feature Tool 다운로드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-122">Download the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md) | <span data-ttu-id="8f3e7-123">혼합 현실 기능 패키지를 검색, 업데이트하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-123">A new developer tool for discovering, updating, and adding Mixed Reality feature packages to your Unity projects</span></span> |
| [<span data-ttu-id="8f3e7-124">개발자 환경 설정</span><span class="sxs-lookup"><span data-stu-id="8f3e7-124">Setup your developer environment</span></span>](../install-the-tools.md) | <span data-ttu-id="8f3e7-125">최신 Unity 패키지를 다운로드 및 설치하고, 혼합 현실에 맞게 프로젝트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="8f3e7-126">HoloLens 2 자습서 시리즈 완료</span><span class="sxs-lookup"><span data-stu-id="8f3e7-126">Complete the HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="8f3e7-127">HoloLens 2 하드웨어에 대한 초보자 수준 MRTK 자습서를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="8f3e7-128">Mixed Reality Toolkit를 가져오지 않고 새 Unity 프로젝트를 만들려면 Windows Mixed Reality에 대해 수동으로 변경해야 하는 작은 Unity 설정 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-128">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="8f3e7-129">자세한 내용은 [구성 가이드](choosing-unity-version.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-129">Take a look at our [configuration guide](choosing-unity-version.md) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="8f3e7-130">프로젝트에서 MRTK가 설정되면 카메라와 같은 표준 Unity 게임 개체가 즉시 점등되어 좌석 크기의 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-130">Once you've setup MRTK in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="8f3e7-131">애플리케이션의 환경 크기를 조정하는 방법은 [좌표계](coordinate-systems-in-unity.md) 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-131">You can find instructions on changing the experience scale of your application on the [coordinate systems](coordinate-systems-in-unity.md) page.</span></span>

## <a name="2-core-building-blocks"></a><span data-ttu-id="8f3e7-132">2. 핵심 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8f3e7-132">2. Core building blocks</span></span>

<span data-ttu-id="8f3e7-133">혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-133">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="8f3e7-134">이러한 구성 요소는 독립 실행형 기능으로 사용하거나 Mixed Reality Toolkit를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-134">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8f3e7-135">한 번에 모두 필요하지 않을 수도 있지만 일찍 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-135">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="8f3e7-136">아래에 나열된 핵심 구성 요소를 살펴보았으면 자체적으로 또는 MRTK를 통해 Mixed Reality 프로젝트에 통합할 수 있는 모든 기능을 갖춘 도구 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-136">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

|  <span data-ttu-id="8f3e7-137">기능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-137">Feature</span></span>  |  <span data-ttu-id="8f3e7-138">기능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-138">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="8f3e7-139">카메라</span><span class="sxs-lookup"><span data-stu-id="8f3e7-139">Camera</span></span>](../unity/camera-in-unity.md) | <span data-ttu-id="8f3e7-140">Mixed Reality 앱에서 시각적 품질 및 홀로그램 안정성을 완벽하게 최적화</span><span class="sxs-lookup"><span data-stu-id="8f3e7-140">Fully optimize visual quality and hologram stability in your Mixed Reality apps</span></span> |
| [<span data-ttu-id="8f3e7-141">세계 잠금 및 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="8f3e7-141">World locking and spatial anchors</span></span>](spatial-anchors-in-unity.md) | <span data-ttu-id="8f3e7-142">안정화 문제 해결, 카메라 조정 및 안정적인 좌표계 솔루션 통합</span><span class="sxs-lookup"><span data-stu-id="8f3e7-142">Solve stabilization issues, camera adjustment, and integrate a stable coordinate system solution</span></span> |
| [<span data-ttu-id="8f3e7-143">공유 환경</span><span class="sxs-lookup"><span data-stu-id="8f3e7-143">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="8f3e7-144">공간 앵커 공유를 사용하여 공간의 고정 지점에서 동일한 홀로그램을 보고 집합적으로 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-144">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="8f3e7-145">응시</span><span class="sxs-lookup"><span data-stu-id="8f3e7-145">Gaze</span></span>](../unity/gaze-in-unity.md) | <span data-ttu-id="8f3e7-146">사용자가 홀로그램을 확인하여 대상으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-146">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="8f3e7-147">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8f3e7-147">Motion controllers</span></span>](../unity/motion-controllers-in-unity.md) | <span data-ttu-id="8f3e7-148">혼합 현실 앱에 공간 작업 추가</span><span class="sxs-lookup"><span data-stu-id="8f3e7-148">Add spatial actions to your Mixed Reality apps</span></span> |
| [<span data-ttu-id="8f3e7-149">제스처</span><span class="sxs-lookup"><span data-stu-id="8f3e7-149">Gestures</span></span>](../unity/gestures-in-unity.md) | <span data-ttu-id="8f3e7-150">혼합 현실 경험에서 손 제스처를 입력으로 사용</span><span class="sxs-lookup"><span data-stu-id="8f3e7-150">Use hand gestures as input in your Mixed Reality experiences</span></span> |
| [<span data-ttu-id="8f3e7-151">손 및 시선 추적</span><span class="sxs-lookup"><span data-stu-id="8f3e7-151">Hand and eye tracking</span></span>](../unity/hand-eye-in-unity.md) | <span data-ttu-id="8f3e7-152">연결된 손 및 시선 추적 입력을 사용자 환경에 통합</span><span class="sxs-lookup"><span data-stu-id="8f3e7-152">Integrate articulated hand and eye tracking input into your user experience</span></span> |
| [<span data-ttu-id="8f3e7-153">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="8f3e7-153">Spatial mapping</span></span>](../unity/spatial-mapping-in-unity.md) | <span data-ttu-id="8f3e7-154">가상 메시 오버레이를 사용하여 실제 공간을 매핑하여 환경 경계 표시</span><span class="sxs-lookup"><span data-stu-id="8f3e7-154">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="8f3e7-155">공간 음향</span><span class="sxs-lookup"><span data-stu-id="8f3e7-155">Spatial sound</span></span>](../unity/spatial-sound-in-unity.md) | <span data-ttu-id="8f3e7-156">몰입형 3D 오디오를 사용하여 앱 향상</span><span class="sxs-lookup"><span data-stu-id="8f3e7-156">Enhance your apps with immersive 3D audio</span></span> |
| [<span data-ttu-id="8f3e7-157">Text</span><span class="sxs-lookup"><span data-stu-id="8f3e7-157">Text</span></span>](../unity/text-in-unity.md) | <span data-ttu-id="8f3e7-158">관리 가능한 크기 및 품질 렌더링을 사용하는 선명한 고품질 텍스트 가져오기</span><span class="sxs-lookup"><span data-stu-id="8f3e7-158">Get sharp, high-quality text that has a manageable size and quality rendering</span></span> |
| [<span data-ttu-id="8f3e7-159">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="8f3e7-159">Voice input</span></span>](../unity/voice-input-in-unity.md) | <span data-ttu-id="8f3e7-160">사용자의 음성 키워드, 구 및 받아쓰기 캡처</span><span class="sxs-lookup"><span data-stu-id="8f3e7-160">Capture spoken keywords, phrases, and dictation from your users</span></span>|

## <a name="3-advanced-features"></a><span data-ttu-id="8f3e7-161">3. 고급 기능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-161">3. Advanced features</span></span>

<span data-ttu-id="8f3e7-162">혼합 현실 애플리케이션에서 역할을 수행하는 다른 주요 기능은 추가 패키지 또는 설정 없이 Unity API를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-162">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="8f3e7-163">이러한 기능은 MRTK의 설치 여부에 관계없이 Unity 프로젝트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-163">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="8f3e7-164">Unity에서 제공하는 고급 기능을 자세히 살펴보았으면 더 깊고 복잡한 Mixed Reality 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-164">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="8f3e7-165">기능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-165">Feature</span></span>  |  <span data-ttu-id="8f3e7-166">기능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-166">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="8f3e7-167">사진 비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="8f3e7-167">Photo video camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="8f3e7-168">Mixed Reality 애플리케이션에서 사진 및 비디오 콘텐츠를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-168">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="8f3e7-169">포커스 지점</span><span class="sxs-lookup"><span data-stu-id="8f3e7-169">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="8f3e7-170">현재 표시 중인 홀로그램에서 안정화를 가장 효율적으로 수행하는 방법에 대한 힌트를 HoloLens에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-170">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="8f3e7-171">추적 손실</span><span class="sxs-lookup"><span data-stu-id="8f3e7-171">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="8f3e7-172">디바이스가 애플리케이션 세계 공간에서 자체를 찾을 수 없는 시나리오를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-172">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="8f3e7-173">키보드 입력</span><span class="sxs-lookup"><span data-stu-id="8f3e7-173">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="8f3e7-174">현실 세계 및 Mixed Reality 키보드의 입력을 앱에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-174">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

## <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="8f3e7-175">4. 디바이스 또는 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="8f3e7-175">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="8f3e7-176">홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 Unity Visual Studio 솔루션을 내보내고 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-176">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="8f3e7-177">해당 VS 솔루션을 직접 사용하는 경우 실제 디바이스 또는 시뮬레이션된 디바이스에서 다음 세 가지 방법 중 하나로 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-177">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="8f3e7-178">이 섹션이 완료되면 개발 요구 사항에 맞는 디바이스 또는 에뮬레이터에 애플리케이션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-178">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="8f3e7-179">HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="8f3e7-179">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="8f3e7-180">HoloLens 에뮬레이터</span><span class="sxs-lookup"><span data-stu-id="8f3e7-180">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="8f3e7-181">Windows Mixed Reality 몰입형 헤드셋 시뮬레이터</span><span class="sxs-lookup"><span data-stu-id="8f3e7-181">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a><span data-ttu-id="8f3e7-182">5. 서비스 추가</span><span class="sxs-lookup"><span data-stu-id="8f3e7-182">5. Adding services</span></span>

<span data-ttu-id="8f3e7-183">개발 과정의 이 시점에서 서비스를 추가하거나 상업적 배포에 도움을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-183">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="8f3e7-184">[Azure Cloud Services](../mixed-reality-cloud-services.md)를 통합하면 주요 방식으로 프로젝트 수준을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-184">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) can level up your projects in a major way.</span></span> <span data-ttu-id="8f3e7-185">Mixed Reality 지식을 검색하고 확장할 수 있는 몇 가지 시작 지점을 컴파일했습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-185">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="8f3e7-186">또한 자체 서비스를 기반으로 하여 Unity 프로젝트에 추가할 수 있는 [추가 Azure 서비스에 대한 포괄적인 지원 설명서 목록](../mixed-reality-cloud-services.md#standalone-unity-services)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-186">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="6-low-code-alternatives"></a><span data-ttu-id="8f3e7-187">6. 로우 코드 대안</span><span class="sxs-lookup"><span data-stu-id="8f3e7-187">6. Low-code alternatives</span></span>

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a><span data-ttu-id="8f3e7-188">다음 작업</span><span class="sxs-lookup"><span data-stu-id="8f3e7-188">What's next?</span></span>

<span data-ttu-id="8f3e7-189">특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-189">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="8f3e7-190">다음 섹션에서는 이미 완료한 초보자 수준 자료와 중단되는 경우 유용한 리소스 영역으로 모두 안내할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-190">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="8f3e7-191">이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 이동하여 살펴보세요!</span><span class="sxs-lookup"><span data-stu-id="8f3e7-191">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="8f3e7-192">포팅</span><span class="sxs-lookup"><span data-stu-id="8f3e7-192">Porting</span></span>

<span data-ttu-id="8f3e7-193">포팅하려는 기존 앱이 있는 경우 아래 나열된 문서가 다음 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-193">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="8f3e7-194">HoloToolkit/MRTK에서 MRTK v2로</span><span class="sxs-lookup"><span data-stu-id="8f3e7-194">HoloToolkit/MRTK to MRTK v2</span></span>](../porting-apps/porting-hl1-hl2.md)
* [<span data-ttu-id="8f3e7-195">몰입형 앱 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-195">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="8f3e7-196">입력 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-196">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="8f3e7-197">자습서</span><span class="sxs-lookup"><span data-stu-id="8f3e7-197">Tutorials</span></span>

<span data-ttu-id="8f3e7-198">특정 Mixed Reality 기능을 애플리케이션에 추가하려는 경우 엔드투엔드 프로세스를 실행할 수 있는 몇 가지 큐레이팅된 자습서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-198">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="8f3e7-199">가장 인기 있는 HoloLens 2 및 HoloLens(1세대) 콘텐츠가 아래에 나열되어 있지만, 자습서 개요를 방문하면 전체 컬렉션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-199">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="8f3e7-200">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="8f3e7-200">Additional resources</span></span>

<span data-ttu-id="8f3e7-201">혼합 현실 세계로 직접 들어가기 전에 아래에 나열된 MRTK 관련 설명서를 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-201">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="8f3e7-202">이러한 문서는 MRTK가 작동하는 방법을 더 자세히 이해하기 위한 훌륭한 출발 지점이며, 앱을 성능 기준에 맞게 만드는 데 적합한 인사이트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-202">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="8f3e7-203">항목</span><span class="sxs-lookup"><span data-stu-id="8f3e7-203">Topic</span></span>  |  <span data-ttu-id="8f3e7-204">Description</span><span class="sxs-lookup"><span data-stu-id="8f3e7-204">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="8f3e7-205">MRTK 아키텍처 개요</span><span class="sxs-lookup"><span data-stu-id="8f3e7-205">MRTK Architecture overview</span></span>](/windows/mixed-reality/mrtk-unity/architecture/overview) | <span data-ttu-id="8f3e7-206">MRTK SDK가 프로젝트에서 작동하는 방법을 더 자세히 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-206">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="8f3e7-207">설정 및 성능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-207">Settings and performance</span></span>](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | <span data-ttu-id="8f3e7-208">앱을 프로파일링하고, Unity 설정을 업데이트하고, 최상의 홀로그램 안정화 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-208">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="8f3e7-209">MRTK + XR 시작</span><span class="sxs-lookup"><span data-stu-id="8f3e7-209">Getting started with MRTK + XR</span></span>](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | <span data-ttu-id="8f3e7-210">Unity에서 제공하는 대체 XR 파이프라인으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-210">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="8f3e7-211">Unity 리소스</span><span class="sxs-lookup"><span data-stu-id="8f3e7-211">Unity resources</span></span>

<span data-ttu-id="8f3e7-212">Unity는 docs.microsoft.com에서 사용할 수 있는 이 설명서 외에도 Windows Mixed Reality 기능에 대한 설명서를 Unity 편집기와 함께 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-212">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="8f3e7-213">Unity에서 제공하는 설명서에는 별도의 다음 두 가지 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-213">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="8f3e7-214">리소스</span><span class="sxs-lookup"><span data-stu-id="8f3e7-214">Resource</span></span>  |  <span data-ttu-id="8f3e7-215">Description</span><span class="sxs-lookup"><span data-stu-id="8f3e7-215">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="8f3e7-216">스크립팅 참조</span><span class="sxs-lookup"><span data-stu-id="8f3e7-216">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="8f3e7-217">설명서의 이 섹션에는 Unity에서 제공하는 스크립팅 API에 대한 세부 정보가 포함되어 있으며, **도움말 > 스크립팅 참조** 를 차례로 클릭하여 Unity 편집기에서 온라인으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-217">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="8f3e7-218">수동</span><span class="sxs-lookup"><span data-stu-id="8f3e7-218">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="8f3e7-219">이 설명서는 기본 기술에서 고급 기술까지 Unity를 사용하는 방법을 학습하는 데 도움이 되도록 설계되었으며, 온라인 또는 Unity 편집기에서 **도움말 > 수동** 을 차례로 클릭하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-219">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f3e7-220">MRTK 살펴보기</span><span class="sxs-lookup"><span data-stu-id="8f3e7-220">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="have-feedback"></a><span data-ttu-id="8f3e7-221">의견이 있으신가요?</span><span class="sxs-lookup"><span data-stu-id="8f3e7-221">Have feedback?</span></span>

<span data-ttu-id="8f3e7-222">[Unity 포럼](https://aka.ms/unityforums)에서 **Microsoft** 를 태그로 지정하면 당사를 찾을 수 있으며 다음 태그를 조합하면 귀하가 피드백을 제공하는 플러그 인이 무엇인지 당사가 파악하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f3e7-222">You can find us on the [Unity Forums](https://aka.ms/unityforums) by tagging **Microsoft** and a combination of the following tags to help us understand what plugin you're providing feedback for:</span></span>

* <span data-ttu-id="8f3e7-223">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8f3e7-223">HoloLens 2</span></span> 
* <span data-ttu-id="8f3e7-224">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f3e7-224">Windows Mixed Reality</span></span>
* <span data-ttu-id="8f3e7-225">OpenXR</span><span class="sxs-lookup"><span data-stu-id="8f3e7-225">OpenXR</span></span>
* <span data-ttu-id="8f3e7-226">XRSDK</span><span class="sxs-lookup"><span data-stu-id="8f3e7-226">XRSDK</span></span>
* <span data-ttu-id="8f3e7-227">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="8f3e7-227">Legacy XR</span></span>

## <a name="see-also"></a><span data-ttu-id="8f3e7-228">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f3e7-228">See also</span></span>

* [<span data-ttu-id="8f3e7-229">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="8f3e7-229">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="8f3e7-230">MR 기본 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="8f3e7-230">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="8f3e7-231">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="8f3e7-231">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="8f3e7-232">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="8f3e7-232">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="8f3e7-233">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-233">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8f3e7-234">HoloLens용 Unity 앱에서 Windows 네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="8f3e7-234">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="8f3e7-235">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="8f3e7-235">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="8f3e7-236">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-236">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="8f3e7-237">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="8f3e7-237">Porting guides</span></span>](../porting-apps/porting-guides.md)
