---
title: 디자인 및 프로토타입 생성 시작
description: 만들 준비가 되면, 디자인 및 프로토타입 생성을 시작하는 데 필요한 기본 개념을 알아봅니다.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 검색, 배포, 인덱스, 방문 페이지, 디자인, 개발, 자습서, 샘플 앱, 기본 사항, 사례 연구, 리소스, HoloLens 방법, 오픈 소스 프로젝트, 핵심 개념, 상호 작용, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c4d9f9b4c4be1c5012ac8dc84fb55e6c5fa9eaee
ms.sourcegitcommit: 85ba3af69ec2a9056f759bab7b66f79f09a016b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2021
ms.locfileid: "111454772"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="9e57e-104">디자인 및 프로토타입 생성 시작</span><span class="sxs-lookup"><span data-stu-id="9e57e-104">Start designing and prototyping</span></span>

![혼합 현실 디자인 요약](images/design-hero-image.png)

<span data-ttu-id="9e57e-106">Mixed Reality 애플리케이션은 오늘날 전 세계의 다른 애플리케이션과 다르며 이를 설계하는 것은 어려운 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="9e57e-107">만들고 있는 현실 세계와 가상 세계의 새로운 조합뿐만 아니라 이 조합이 제공하는 새로운 사용자 환경도 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new user experiences they afford.</span></span> <span data-ttu-id="9e57e-108">Mixed Reality는 큰 장소이므로 디자인 스펙트럼에 따라 중요한 지점을 선택하여 일련의 검사점으로 아래에 배치했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="9e57e-109">이러한 검사점은 순차적이어야 하지만, 이미 참여한 경우 다음 섹션 중 하나로 자유롭게 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="9e57e-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span> 

<span data-ttu-id="9e57e-110">시작하려면 디자인 개요 비디오를 시청하세요.</span><span class="sxs-lookup"><span data-stu-id="9e57e-110">Take a look at our design overview video to get started:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a><span data-ttu-id="9e57e-111">디자인 검사점</span><span class="sxs-lookup"><span data-stu-id="9e57e-111">Design checkpoints</span></span>

<span data-ttu-id="9e57e-112">다음 검사점을 사용하여 애플리케이션 아이디어와 개념을 혼합 현실 세계로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-112">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="9e57e-113">1. 시작</span><span class="sxs-lookup"><span data-stu-id="9e57e-113">1. Getting started</span></span>

<span data-ttu-id="9e57e-114">모든 과정과 마찬가지로 Mixed Reality 애플리케이션을 설계하는 과정도 기본 사항에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-114">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="9e57e-115">[Mixed Reality란?](../discover/mixed-reality.md) 및 [홀로그램이란?](../discover/hologram.md) 문서를 숙지하여 몰입형 디자인을 준비하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-115">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="9e57e-116">자세히 살펴보았으면 Mixed Reality 디자인 과정을 시작할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-116">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![Holograms 앱 디자인에서 gif 시작하기](images/HandTracking2.gif)

|  <span data-ttu-id="9e57e-118">검사점</span><span class="sxs-lookup"><span data-stu-id="9e57e-118">Checkpoint</span></span>  |  <span data-ttu-id="9e57e-119">결과</span><span class="sxs-lookup"><span data-stu-id="9e57e-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="9e57e-120">디자인 프로세스 확장</span><span class="sxs-lookup"><span data-stu-id="9e57e-120">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="9e57e-121">Microsoft 내부 및 외부의 디자이너로부터 수집한 Mixed Reality의 디자인 프로세스를 직접 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="9e57e-121">Get a first-hand look at design process for Mixed Reality, gathered from designers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="9e57e-122">Mixed Reality 앱 유형</span><span class="sxs-lookup"><span data-stu-id="9e57e-122">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="9e57e-123">앱 환경이 Mixed Reality 스펙트럼에서 라이브 상태가 되는 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-123">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="9e57e-124">Holograms 앱 디자인</span><span class="sxs-lookup"><span data-stu-id="9e57e-124">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="9e57e-125">놀라운 HoloLens 앱을 만들기 위한 동작, 팁 및 권장 사항을 경험하면서 혼합 현실 UX 디자인의 기본 사항에 대해 알아봅니다(HoloLens 2의 Microsoft Store에서 다운로드 가능).</span><span class="sxs-lookup"><span data-stu-id="9e57e-125">Learn the fundamentals of Mixed Reality UX Design by experiencing with behaviors, tips, and recommendations for creating amazing HoloLens apps (available for download from Microsoft Store in HoloLens 2)</span></span> |
| [<span data-ttu-id="9e57e-126">MRTK 예제 허브</span><span class="sxs-lookup"><span data-stu-id="9e57e-126">MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | <span data-ttu-id="9e57e-127">혼합 현실을 위한 공통 공간 상호 작용 및 UX 구성 요소를 경험할 수 있습니다(HoloLens 2의 Microsoft Store에서 다운로드할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9e57e-127">Experience common spatial interactions and UX building blocks for Mixed Reality (available for download from Microsoft Store in HoloLens 2)</span></span> |
| <span data-ttu-id="9e57e-128">**선택 사항** [Figma 도구 키트 다운로드](figma-toolkit.md)</span><span class="sxs-lookup"><span data-stu-id="9e57e-128">**Optional** [Download the Figma Toolkit](figma-toolkit.md)</span></span> | <span data-ttu-id="9e57e-129">Figma 도구 키트는 MRTK에서 사용할 수 있는 구성 요소를 기반으로 UI를 스케치하고 레이아웃하는 데 사용할 자산을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-129">The Figma Toolkit provides assets for you to use for sketching and laying out UI based on the components available in MRTK</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="9e57e-130">2. 핵심 개념</span><span class="sxs-lookup"><span data-stu-id="9e57e-130">2. Core concepts</span></span>

<span data-ttu-id="9e57e-131">VR 또는 AR용으로 개발하는지에 관계없이 유동적인 몰입형 환경을 설계하는 데 적용되는 몇 가지 핵심 개념이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-131">Whether you're developing for VR or AR, there are several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="9e57e-132">사용자의 관점을 이해하고, 개체를 배치하며, 모든 사람이 편안하고 안전한지 확인하는 것이 이 과정의 가장 중요한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-132">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="9e57e-133">이 섹션이 완료되면 상호 작용 디자인을 통해 수행할 수 있는 견고한 토대가 갖추어집니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-133">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![핵심 개념 예제 이미지](images/fragments-750px.jpg)

|  <span data-ttu-id="9e57e-135">개념</span><span class="sxs-lookup"><span data-stu-id="9e57e-135">Concept</span></span>  |  <span data-ttu-id="9e57e-136">결과</span><span class="sxs-lookup"><span data-stu-id="9e57e-136">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="9e57e-137">홀로그램 프레임</span><span class="sxs-lookup"><span data-stu-id="9e57e-137">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="9e57e-138">헤드셋을 착용하면 현실 세계에 겹쳐진 콘텐츠가 사용자에게 표시되는 방법을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-138">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="9e57e-139">좌표계</span><span class="sxs-lookup"><span data-stu-id="9e57e-139">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="9e57e-140">물리적 공간인지, 아니면 직접 만든 가상 영역인지에 관계없이 의미 있는 위치에 홀로그램을 정확하게 배치하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-140">Learn how to position holograms in meaningful places in the world, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="9e57e-141">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="9e57e-141">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="9e57e-142">개체를 사용자의 세계에 고정하고, 현실 세계의 물리적 표면을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-142">Anchor objects in the user's world and take advantage of real world's physical surfaces</span></span> |
| [<span data-ttu-id="9e57e-143">편안함 고려사항</span><span class="sxs-lookup"><span data-stu-id="9e57e-143">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="9e57e-144">자연 세계를 모방하는 방식으로 몰입형 콘텐츠를 만들고 제공하여 사용자의 편의와 안전을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-144">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="9e57e-145">3. 상호 작용 디자인</span><span class="sxs-lookup"><span data-stu-id="9e57e-145">3. Interaction design</span></span>

<span data-ttu-id="9e57e-146">가상 환경의 아름다움과 몰입감에 관계없이 상호 작용이 없으면 쓸모가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-146">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="9e57e-147">이 섹션에서는 기본적인 상호 작용 모델, 손 및 모션 컨트롤러, 음성 입력 및 사용자로부터 시선 추적 데이터를 수집하는 방법을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-147">This section will walk you through basic interaction models, hand and motion controllers, voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="9e57e-148">이 섹션이 완료되면 디자인 과정의 마지막 주요 항목인 사용자 환경을 다룰 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-148">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![상호 작용 디자인 요소](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="9e57e-150">개념</span><span class="sxs-lookup"><span data-stu-id="9e57e-150">Concept</span></span>  |  <span data-ttu-id="9e57e-151">결과</span><span class="sxs-lookup"><span data-stu-id="9e57e-151">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="9e57e-152">상호 작용 모델</span><span class="sxs-lookup"><span data-stu-id="9e57e-152">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="9e57e-153">손, 눈, 음성 입력을 통해 사용자에게 직관적인 상호 작용을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-153">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="9e57e-154">실습 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="9e57e-154">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="9e57e-155">사용자의 손으로 가까운 거리에서 또는 정확한 상호 작용으로 먼 거리에서 홀로그램과 상호 작용하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-155">Learn how to interact with holograms at close range with a user' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="9e57e-156">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="9e57e-156">Voice input</span></span>](voice-input.md) | <span data-ttu-id="9e57e-157">몰입형 앱에서 음성 명령을 입력으로 사용하여 주변의 홀로그램과 환경을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-157">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="9e57e-158">시선 추적</span><span class="sxs-lookup"><span data-stu-id="9e57e-158">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="9e57e-159">사용자가 보고 있는 항목에 대한 정보를 사용하여 홀로그램 환경에서 새로운 수준의 컨텍스트 및 인간 이해를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-159">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="9e57e-160">4. 사용자 환경 요소</span><span class="sxs-lookup"><span data-stu-id="9e57e-160">4. User experience elements</span></span>

<span data-ttu-id="9e57e-161">이제 기본 상호 작용을 숙지했으므로 사용자 환경 요소의 세부 요소와 고유한 Mixed Reality 환경에 맞게 이를 조정하는 방법을 중점적으로 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-161">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="9e57e-162">사용자에게 직관적인 환경을 만들면서 일반적인 동작, 자산 디자인, 개체 크기 조정 및 입력 체계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-162">You'll cover common behaviors, asset design, object scaling, and typography, while making the experience intuitive for your users.</span></span> <span data-ttu-id="9e57e-163">이 섹션은 공식적인 Mixed Reality 디자인 과정의 끝을 나타내지만, [다음 작업](#whats-next) 섹션에는 계속 진행할 수 있는 더 많은 리소스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-163">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![UX 요소](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="9e57e-165">개념</span><span class="sxs-lookup"><span data-stu-id="9e57e-165">Concept</span></span>  |  <span data-ttu-id="9e57e-166">결과</span><span class="sxs-lookup"><span data-stu-id="9e57e-166">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="9e57e-167">공용 컨트롤 및 동작</span><span class="sxs-lookup"><span data-stu-id="9e57e-167">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="9e57e-168">자주 사용되는 공간 상호 작용 및 UI 구성 요소에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-168">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="9e57e-169">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="9e57e-169">Color, light, and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="9e57e-170">색, 조명 및 재질을 고려한 Mixed Reality에 대한 품질 자산을 설계합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-170">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="9e57e-171">개체 크기 조정</span><span class="sxs-lookup"><span data-stu-id="9e57e-171">Object scale</span></span>](scale.md) | <span data-ttu-id="9e57e-172">최대한 많은 현실 세계 시각적 신호를 통합하여 사용자가 개체의 위치, 크기 및 구성 요소를 이해하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-172">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="9e57e-173">입력 체계</span><span class="sxs-lookup"><span data-stu-id="9e57e-173">Typography</span></span>](typography.md) | <span data-ttu-id="9e57e-174">3차원 공간에서 명확하고 읽기 쉬운 텍스트를 사용하여 사용자에게 필요한 중요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-174">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="9e57e-175">다음 작업</span><span class="sxs-lookup"><span data-stu-id="9e57e-175">What's next?</span></span>

<span data-ttu-id="9e57e-176">디자이너 작업은 수행되지 않습니다(특히 새 패러다임에서 몰입형 환경을 만드는 법을 학습하는 경우).</span><span class="sxs-lookup"><span data-stu-id="9e57e-176">A designer's job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="9e57e-177">다음 섹션에서는 이미 완료한 초보자 수준 디자인 자료와 Mixed Reality 개발 분야로 모두 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-177">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="9e57e-178">이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="9e57e-178">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="9e57e-179">프로토타입 생성 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="9e57e-179">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
        <span data-ttu-id="9e57e-180">[![MRTK Figma Toolkit](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="9e57e-180">[![MRTK Figma Toolkit](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="9e57e-181">**[Figma 도구 키트](figma-toolkit.md)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-181">**[Figma Toolkit](figma-toolkit.md)**</span></span><br>   
        <span data-ttu-id="9e57e-182">Figma Toolkit은 UI 스케치 및 배치에 사용할 수 있는 자산을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-182">Figma Toolkit provides the assets that can be used for sketching and laying out UI.</span></span> <span data-ttu-id="9e57e-183">모든 UI 컨트롤은 MRTK에서 사용할 수 있는 구성 요소를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-183">All UI controls are based on the components available in MRTK.</span></span>
    :::column-end:::        
    :::column:::    
       <span data-ttu-id="9e57e-184">[![Unity 배우기](../images/Final_unity_logo.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="9e57e-184">[![Learn Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="9e57e-185">**[Unity 배우기](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-185">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="9e57e-186">Unity를 사용하여 대화형 환경을 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-186">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="9e57e-187">처음부터 끝까지 수행하여 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-187">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="9e57e-188">[![Mixed Reality Toolkit(MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="9e57e-188">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="9e57e-189">**[Mixed Reality Toolkit(MRTK)](/windows/mixed-reality/mrtk-unity/)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-189">**[Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/)**</span></span><br>  
        <span data-ttu-id="9e57e-190">공간 상호 작용 및 UI의 기본 구성 요소와 함께 Unity를 사용하여 혼합 현실 디자인 및 개발을 바로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-190">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="9e57e-191">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="9e57e-191">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="9e57e-192">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-192">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="9e57e-193">VR을 위한 디자인.</span><span class="sxs-lookup"><span data-stu-id="9e57e-193">Design for VR.</span></span> <span data-ttu-id="9e57e-194">Microsoft Maquette를 사용하면 공간 프로토타입을 쉽고 빠르며 몰입감 있게 제작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-194">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a><span data-ttu-id="9e57e-195">다른 리소스</span><span class="sxs-lookup"><span data-stu-id="9e57e-195">Other resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="9e57e-196">[![기본 사항 이해](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="9e57e-196">[![Understand the basics](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="9e57e-197">**[기본 사항 이해](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-197">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="9e57e-198">혼합 현실을 정의하는 것이 무엇이며, 혼합 현실이 어떻게 사용되는지에 대해 더 잘 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-198">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9e57e-199">[![이벤트 참가](images/74-16.png)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="9e57e-199">[![Come to an event](images/74-16.png)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="9e57e-200">**[이벤트 참가](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-200">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="9e57e-201">하드웨어를 살펴보고 첫 번째 HoloLens 2 애플리케이션을 만들기 위한 실습 자습서를 받으세요.</span><span class="sxs-lookup"><span data-stu-id="9e57e-201">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9e57e-202">[![도구 설치](images/74-17.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="9e57e-202">[![Install the tools](images/74-17.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="9e57e-203">**[도구 설치](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-203">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="9e57e-204">설치 체크리스트를 사용하여 HoloLens와 혼합 현실용 앱을 빌드하는 데 필요한 도구를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-204">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9e57e-205">[![개발 시작](images/74-18.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="9e57e-205">[![Start developing](images/74-18.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="9e57e-206">**[개발 시작](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="9e57e-206">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="9e57e-207">자신의 기술 수준, 작업 스타일 또는 플랫폼 관심 분야에 따라 개발 경로를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e57e-207">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>
