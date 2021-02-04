---
title: Unity용 MRTK 소개
description: 플랫폼 간 Mixed Reality Toolkit이 새로운 혼합 현실 개발자에게 제공하는 모든 기능을 시작합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 플랫폼 간
ms.openlocfilehash: 54ad49bbf4da577a398a0bfb12fbdc84cdff34d9
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238121"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="35dec-104">Unity용 MRTK 소개</span><span class="sxs-lookup"><span data-stu-id="35dec-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="35dec-106">MRTK(Mixed Reality Toolkit)란?</span><span class="sxs-lookup"><span data-stu-id="35dec-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="35dec-107">MRTK는 HoloLens가 처음 릴리스된 이후부터 사용되어 온 놀라운 오픈 소스 도구 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="35dec-108">기여 개발자 커뮤니티의 노력이 없었다면 오늘날의 도구 키트가 될 수 없었을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="35dec-109">가장 중요한 문제를 고려하기 위해 지난 3년간 개발자 커뮤니티의 피드백을 주의 깊게 살피면서 MRTK v2를 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="35dec-110">Unity용 MRTK는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="35dec-111">도구 키트를 설치하는 가장 쉬운 방법은 새로운 Mixed Reality Feature Tool 애플리케이션을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="35dec-112">[설치 및 사용 지침](welcome-to-mr-feature-tool.md)을 따르고 Mixed Reality Toolkit 범주에서 **Mixed Reality Toolkit Foundation** 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span> 

<span data-ttu-id="35dec-113">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="35dec-114">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="35dec-115">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="35dec-116">자세한 기능 정보는 [GitHub의 MRTK 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="35dec-116">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="35dec-117">MRTK v2의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="35dec-117">New with MRTK v2</span></span>

<span data-ttu-id="35dec-118">여기서는 이러한 플랫폼 도구에 대한 약속을 강조하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-118">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="35dec-119">실제로 MRTK 버전 2를 사용하여 OOBE(Out-of-Box Setup Experience) 및 Mixed Reality 팁 애플리케이션과 같은 받은 편지함 환경을 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-119">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="35dec-120">또한 플랫폼에서 개발하는 것이 가장 좋은 방법이라고 생각하므로 새로운 HoloLens 2 기능이 MRTK를 통해 처음 공개될 것으로 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-120">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="35dec-121">모듈식</span><span class="sxs-lookup"><span data-stu-id="35dec-121">Modular</span></span>

<span data-ttu-id="35dec-122">모듈식으로 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-122">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="35dec-123">실제로 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-123">There are actually a few benefits to this.</span></span>  <span data-ttu-id="35dec-124">이를 통해 프로젝트 크기를 더 작게 유지하고 관리하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-124">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="35dec-125">또한 스크립트 가능한 개체를 사용하여 빌드되고 인터페이스를 기반으로 하므로 포함된 구성 요소를 사용자 고유의 구성 요소로 바꿔 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-125">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="35dec-126">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="35dec-126">Cross-platform</span></span>

<span data-ttu-id="35dec-127">다른 플랫폼과 관련하여 플랫폼 간 지원이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-127">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="35dec-128">이는 모든 단일 플랫폼이 지원된다는 것을 의미하지는 않지만, 빌드 대상을 다른 플랫폼으로 전환할 때 도구 키트 코드가 중단되지 않도록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-128">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="35dec-129">모듈식 설계를 통한 견고성과 확장성은 ARCore, ARKit 및 OpenVR과 같은 여러 플랫폼을 지원하도록 앱을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-129">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="35dec-130">성능 기준에 적합</span><span class="sxs-lookup"><span data-stu-id="35dec-130">Performant</span></span>

<span data-ttu-id="35dec-131">모바일 플랫폼을 사용하는 경우 성능을 고려하여 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-131">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="35dec-132">이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 하려 했습니다.</span><span class="sxs-lookup"><span data-stu-id="35dec-132">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="35dec-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35dec-133">See also</span></span>

* [<span data-ttu-id="35dec-134">도구 설치</span><span class="sxs-lookup"><span data-stu-id="35dec-134">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="35dec-135">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="35dec-135">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="35dec-136">Unity용 MRTK를 사용한 개발</span><span class="sxs-lookup"><span data-stu-id="35dec-136">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="35dec-137">MRTK - 설명서 홈(GitHub)</span><span class="sxs-lookup"><span data-stu-id="35dec-137">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="35dec-138">HoloToolkit/MRTK에서 MRTK 버전 2로 포팅(GitHub)</span><span class="sxs-lookup"><span data-stu-id="35dec-138">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
