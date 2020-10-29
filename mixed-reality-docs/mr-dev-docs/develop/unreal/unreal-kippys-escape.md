---
title: Kippy의 이스케이프 만들기
description: Unreal Engine에서 HoloLens 2에 대 한 Kippy의 이스케이프를 만드는 과정을 살펴볼 때에도 문의 하십시오.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 장치에 배포, PC, 설명서
appliesto:
- HoloLens 2
ms.openlocfilehash: 5c029e91bb33192b02dd32aca224a23fc4b5289d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684529"
---
# <a name="the-making-of-kippys-escape"></a><span data-ttu-id="6b707-104">Kippy의 이스케이프 만들기</span><span class="sxs-lookup"><span data-stu-id="6b707-104">The Making of Kippy's Escape</span></span>

<span data-ttu-id="6b707-105">Kippy가 아일랜드에서 남겨진 상태를 찾도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-105">Kippy the robot wakes up to find itself stranded on an island.</span></span> <span data-ttu-id="6b707-106">문제를 해결 하는 데 도움이 되는 문제를 해결 하는 데 도움이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-106">It’s up to you to put on your problem-solving hat to help it find a path back to its rocket ship!</span></span> <span data-ttu-id="6b707-107">스트랩을에서 앱을 다운로드 하 고 Microsoft Store에서 [앱을 다운로드](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 하거나 GitHub에서 [리포지토리](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 를 복제 하 고 Kippy home safe를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-107">Strap on your HoloLens 2 and [download the app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) from the Microsoft Store or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and get Kippy home safe!</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="6b707-108">GitHub 리포지토리에서 Kippy의 이스케이프를 빌드하는 경우 **Unreal Engine 4.25** 이상을 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-108">Make sure you're using **Unreal Engine 4.25 or later** if you're building Kippy's Escape from the GitHub repository.</span></span>

## <a name="overview"></a><span data-ttu-id="6b707-109">개요</span><span class="sxs-lookup"><span data-stu-id="6b707-109">Overview</span></span>

<span data-ttu-id="6b707-110">Kippy의 이스케이프는 Unreal Engine 4로 빌드된 오픈 소스 [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) 샘플 앱 이며, [Unreal 용 혼합 현실 UX 도구](https://github.com/microsoft/MixedReality-UXTools-Unreal)입니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-110">Kippy’s Escape is an open-source [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) sample app built with Unreal Engine 4 and [Mixed Reality UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal).</span></span> <span data-ttu-id="6b707-111">이 게시물에서는 첫 번째 원칙 및 시각적 디자인에서 환경을 구현 하 고 최적화 하는 데 Kippy의 이스케이프를 가져오는 프로세스를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-111">In this post, we’ll walk you through our process for bringing Kippy’s Escape to life, from first principles and visual design to implementing and optimizing the experience.</span></span> <span data-ttu-id="6b707-112">MRTK UX 도구를 사용 하 여 혼합 현실 응용 프로그램을 개발 하는 방법에 대 한 자세한 내용은 [Unreal development 개요](unreal-development-overview.md)를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-112">You can find more information on developing Mixed Reality applications with MRTK UX Tools in the [Unreal development overview](unreal-development-overview.md).</span></span>

## <a name="first-principles"></a><span data-ttu-id="6b707-113">첫 번째 원칙</span><span class="sxs-lookup"><span data-stu-id="6b707-113">First principles</span></span> 

<span data-ttu-id="6b707-114">Kippy의 이스케이프 만들기에서 목표는 [Unreal Engine의 HoloLens 2 지원](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), hololens 2의 기능 및 혼합 현실 도구 키트를 강조 하는 환경을 만드는 것 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-114">In setting out to create Kippy’s Escape, our goal was to create an experience that would highlight [Unreal Engine’s HoloLens 2 support](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), the HoloLens 2’s capabilities, and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6b707-115">개발자가 Unreal 및 HoloLens 2를 사용 하 여 만들 수 있는 기능을 영감 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-115">We wanted to inspire developers to imagine what they could create with Unreal and HoloLens 2.</span></span>  

<span data-ttu-id="6b707-116">환경에 대 한 세 가지 안내 원칙 (재미 있고 대화형이 필요 하 고 진입에 대 한 장벽을 낮음)을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-116">We came up with three guiding principles for the experience: that it needed to be fun, interactive, and have a low barrier to entry.</span></span> <span data-ttu-id="6b707-117">처음에는 혼합 된 현실 사용자에 게는 자습서를 사용 하지 않아도 되도록 충분히 직관적으로 경험을 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-117">We wanted the experience to be intuitive enough that even a first-time mixed reality user won’t need a tutorial to go through it.</span></span>  

## <a name="designing-the-game"></a><span data-ttu-id="6b707-118">게임 디자인</span><span class="sxs-lookup"><span data-stu-id="6b707-118">Designing the game</span></span> 

<span data-ttu-id="6b707-119">HoloLens 2는 현재 게임에서 다른 곳에서 찾을 수 없는 디자인 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-119">The HoloLens 2 has access to design features found nowhere else in gaming today.</span></span> <span data-ttu-id="6b707-120">사용자를 사용 하 여 개체를 직접 푸시되 나 조작 하거나 시각 추적을 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-120">Objects can be directly pushed or manipulated using your hands or targeted with eye tracking.</span></span> <span data-ttu-id="6b707-121">이러한 주요 기능은 Kippy의 이스케이프에서 작성 한 흥미로운 몇 분 뒤에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-121">These key features are behind some of the fun moments we built out in Kippy’s Escape.</span></span>  

<span data-ttu-id="6b707-122">고유한 HoloLens 2 기능을 게임 디자인에 대 한 지침으로 사용 하 여 몇 가지 작은 환경 시나리오의 범위를 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-122">Using the unique HoloLens 2 features as guidance for our game design, we scoped out a few small environment scenarios.</span></span> <span data-ttu-id="6b707-123">다른 플레이어 높이에 맞게 조정 될 수 있고 몇 가지 오락 아이디어 아이디어를 제공 하기 때문에 제도는 매우 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-123">Islands made a lot of sense because they can be adjusted for different player heights, and provided some entertaining bridge ideas.</span></span> <span data-ttu-id="6b707-124">여기서는 좋아하는에 대 한 배치의 테마에 따라 각 아일랜드에서 제공 하는 이상한 에너지를 방해 하는 활용에 대 한 기계를 구축 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-124">From there, we landed on the theme of ancient civilization meets sci-fi tech, with the idea that someone had built machinery over ruins harnessing a strange energy provided by each island.</span></span> <span data-ttu-id="6b707-125">각각은 시각적 효과를 만드는 데 도움이 되는 고유한 모양과 느낌을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-125">The islands were each given their own look and feel, a detail that helped create visual interest.</span></span> <span data-ttu-id="6b707-126">모델링 및 질감의 균형을 유지 하는 것은 렌더링 성능에 대 한 그리기 호출을 낮게 유지 하는 것이 중요 하기 때문에 스타일을 염두에 두고 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-126">A good balance between modeling and texturing was top of mind to keep draw calls low for rendering performance, so a stylized look was designed with that in mind.</span></span> 

<span data-ttu-id="6b707-127">![초기 게임 디자인 ](images/kippys-escape/kippys-escape-img-01.png)
 *은 환경에 대 한 초기 스케치를 스케치 합니다* .</span><span class="sxs-lookup"><span data-stu-id="6b707-127">![Early game design sketches](images/kippys-escape/kippys-escape-img-01.png)
*Some early sketches for what the experience might look like*</span></span>

<span data-ttu-id="6b707-128">![두 번째 섬에 ](images/kippys-escape/kippys-escape-img-02.png)
 *대 한* 두 번째 섬 렌더링 렌더링</span><span class="sxs-lookup"><span data-stu-id="6b707-128">![Renderings of the second island](images/kippys-escape/kippys-escape-img-02.png)
*Renderings of the second island*</span></span>

<span data-ttu-id="6b707-129">짧은 프로덕션 일정 내에서 유지 하기 위해 부동 문자가 엄격한 애니메이션 주기 없이 의도 및 emotion를 캡처할 수 있도록 합의 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-129">To keep within our short production schedule, we agreed that a floating character could capture intent and emotion without rigorous animation cycles.</span></span> <span data-ttu-id="6b707-130">Kippy.</span><span class="sxs-lookup"><span data-stu-id="6b707-130">And so Kippy was born!</span></span> <span data-ttu-id="6b707-131">눈에 최소형 vocal 음향 효과를 통해 몇 가지 다른 식을 표현 하 고 플레이어를 통해 플레이어를 안내할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-131">It emotes a few different expressions through its eyes and through minimalistic vocal sound effects to help guide the player throughout the experience.</span></span> 

![눈동자를 통해 다양 한 식을 보여 주는 Kippy](images/kippys-escape/kippys-escape-img-03.gif)

<span data-ttu-id="6b707-133">*눈동자를 통해 다양 한 식을 보여 주는 Kippy*</span><span class="sxs-lookup"><span data-stu-id="6b707-133">*Kippy showing different expressions via its eyes*</span></span>

![사용자가 퍼즐을 해결 하는 데 너무 오래 걸리는 경우 Kippy는 사용자에 게 힌트를 제공 합니다.](images/kippys-escape/kippys-escape-img-04.gif)

<span data-ttu-id="6b707-135">*사용자가 퍼즐을 해결 하는 데 너무 오래 걸리는 경우 Kippy는 사용자에 게 힌트를 제공 합니다.*</span><span class="sxs-lookup"><span data-stu-id="6b707-135">*If the user takes too long to solve a puzzle, Kippy will give the user a hint*</span></span>

<span data-ttu-id="6b707-136">문자 및 환경 설계 외에도 게임을 재미 있게 하기 위한 노력을 율 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-136">Beyond the character and environment design, we made a concerted effort to make the game feel fun.</span></span> <span data-ttu-id="6b707-137">아이 추적을 통해 게임의 주요 부분을 강조 표시 하는 재질 및 음향 특성을 실행할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-137">Eye tracking allowed us to fire off material and sound attributes, which highlighted key pieces of the game.</span></span> <span data-ttu-id="6b707-138">공간 오디오는 플레이어 환경의 집에서 수준을 느낌을 주는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-138">Spatial audio helped make the levels feel at home in the player’s surroundings.</span></span> <span data-ttu-id="6b707-139">개체를 잡고, 단추를 조작 하 고, 슬라이더를 조작 하는 것은 혁신적인 플레이어 계약을 확인할 수 있으므로 이러한 연결 지점이 자연스럽 게 보이도록 하는 것이 중요 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-139">Being able to grab objects, push buttons and manipulate sliders drives innovative player engagements, so it was important to make sure these connection points felt natural.</span></span> 

![사용자가 손 모양에 도달할 때 연결 케이블의 끝입니다.](images/kippys-escape/kippys-escape-img-05.gif)

<span data-ttu-id="6b707-141">*사용자가 손 모양에 도달할 때 연결 케이블의 끝입니다.*</span><span class="sxs-lookup"><span data-stu-id="6b707-141">*The end of the bridge cable glows when the user’s hand approaches it*</span></span>

## <a name="building-the-game-mechanics"></a><span data-ttu-id="6b707-142">게임 메커니즘 구축</span><span class="sxs-lookup"><span data-stu-id="6b707-142">Building the game mechanics</span></span> 

<span data-ttu-id="6b707-143">Kippy의 이스케이프는 혼합 현실 UX 도구 구성 요소에 크게 의존 하 여 게임을 대화형으로 진행 하 고, 범위 컨트롤, 조작자, 슬라이더 및 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-143">Kippy’s Escape relies heavily on Mixed Reality UX Tools components to make the game interactive - namely hand interaction actors, bounds controls, manipulators, sliders, and buttons.</span></span>   

<span data-ttu-id="6b707-144">[손 상호 작용 행위자](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) 는 holograms의 직접 조작과 직접 조작을 모두 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-144">The [hand interaction actor](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) enables both direct and far manipulation of holograms.</span></span> <span data-ttu-id="6b707-145">Kippy의 이스케이프 시작 부분에서 사용자에 게 게임의 위치를 설정할 수 있는 기회가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-145">At the start of Kippy’s Escape, the user is given the opportunity to set the location of the game.</span></span> <span data-ttu-id="6b707-146">빔 사용자의 palm에서 확장 하면 아래에 나와 있는 것 처럼 훨씬 멀리 떨어져 있는 holograms를 쉽게 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-146">Hand beams extending from the user’s palm make it easy to manipulate large holograms that are far away, as seen in the gif below.</span></span>  

![직접 상호 작용 행위자 gif](images/kippys-escape/kippys-escape-img-06.gif)

<span data-ttu-id="6b707-148">UX 도구의 [범위 컨트롤](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) 구성 요소를 사용 하 여 자리 표시자 장면 자체를 끌어서 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-148">The placeholder scene itself can be dragged and rotated using UX Tools’ [bounds control](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) component.</span></span>  

<span data-ttu-id="6b707-149">두 번째 아일랜드에서 사용자는 보석을 선택 하 여 일치 하는 슬롯에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-149">On the second island, the user must pick up gems and place them in their matching slots.</span></span> <span data-ttu-id="6b707-150">보석에는 사용자가 선택 하 여 배치할 수 있도록 하는 [조작자](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) 가 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-150">The gems have [manipulators](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) attached to them that allow the user to pick them up and place them down.</span></span> 

![조작자 예제 gif](images/kippys-escape/kippys-escape-img-07.gif)

<span data-ttu-id="6b707-152">[Pressable 단추](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) 는 세 번째 섬에서 사용할 폭탄를 가져오는 키입니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-152">A [pressable button](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) is the key to bringing up bombs for use on the third island.</span></span>  

![Pressable button 예제 gif](images/kippys-escape/kippys-escape-img-08.gif)

<span data-ttu-id="6b707-154">네 번째 섬에 [슬라이더](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) 구성 요소가 표시 되 고 발생 시킬 최종 브리지가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-154">A [slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) component appears on the fourth island, triggering the final bridge to be raised.</span></span>  

![Slider 구성 요소 예제 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a><span data-ttu-id="6b707-156">HoloLens 2 용 최적화</span><span class="sxs-lookup"><span data-stu-id="6b707-156">Optimizing for HoloLens 2</span></span> 

<span data-ttu-id="6b707-157">모바일 장치에서 실행 되도록 제작 된 환경을 사용 하 여 성능에 대 한 눈을 유지 하는 것은 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-157">With any experience built to run on a mobile device, keeping an eye on performance is critical.</span></span> <span data-ttu-id="6b707-158">Unreal 4.25에는 모바일 다중 뷰 지원에 대 한 주요 업데이트가 포함 되어 있습니다 .이로 인해 렌더링 오버 헤드가 크게 줄어들고 프레임 비율이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-158">Unreal 4.25 includes a major update to support for mobile multi-view, which significantly reduces rendering overhead and boosts frame-rate.</span></span> <span data-ttu-id="6b707-159">최적화 하는 경우에는 사용 하지 않는 HoloLens 2 개발에 대 한 다른 [권장 성능 설정을](performance-recommendations-for-unreal.md) 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-159">We recommend checking out our other [recommended performance settings](performance-recommendations-for-unreal.md) for HoloLens 2 development with Unreal when you're optimizing.</span></span>  

<span data-ttu-id="6b707-160">물리 개체는 여전히 성능에 대해 비용이 많이 들기 때문에 몇 가지 해결 방법을 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-160">Physics objects still remain costly for performance, so a couple clever workarounds were used.</span></span> <span data-ttu-id="6b707-161">예를 들어 세 번째 "브리지"를 사용 하려면 stairway를 차단 하는 일부 이물질을 죠 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-161">For instance, the third “bridge” requires blowing up some debris blocking the stairway.</span></span> <span data-ttu-id="6b707-162">충격을 힘 개체로 강제 적용 하는 대신, 폭탄 detonation는 폭발을 트리거하고 폭발 파티클 효과에 대 한 정적 스톤을 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-162">Instead of having a force impact the stones as physics objects, the bomb detonation triggers a swap, switching the static stones for an exploding particle effect.</span></span> 

![HoloLens 2 gif에 대해 최적화 된 예제](images/kippys-escape/kippys-escape-img-10.gif) 

<span data-ttu-id="6b707-164">또한 다음을 수행 하 여 400 ~ 260의 그리기 호출을 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-164">We also cut down our draw calls from over 400 to  ~260 by:</span></span> 
* <span data-ttu-id="6b707-165">메시 복잡성 감소</span><span class="sxs-lookup"><span data-stu-id="6b707-165">Reducing mesh complexity</span></span>
* <span data-ttu-id="6b707-166">메시 조합</span><span class="sxs-lookup"><span data-stu-id="6b707-166">Combining meshes</span></span>
* <span data-ttu-id="6b707-167">초기 동적 조명 요소 중 일부를 제거 하는 중</span><span class="sxs-lookup"><span data-stu-id="6b707-167">Removing some of our initial dynamic lighting elements</span></span>

<span data-ttu-id="6b707-168">더 많은 작업을 수행할 수 있지만 성능 및 시각적 품질 간에는 잘 조화를 느낄 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-168">While there’s likely more we could have done, we felt that was a good balance between performance and visual quality.</span></span>  

## <a name="try-it-out"></a><span data-ttu-id="6b707-169">기능 직접 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="6b707-169">Try it out!</span></span> 

<span data-ttu-id="6b707-170">HoloLens 2를 부팅 하 고 Microsoft Store에서 앱을 [다운로드](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 하거나 GitHub에서 [리포지토리](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 를 복제 하 고 앱을 직접 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-170">Boot up your HoloLens 2 and [download](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) the app from the Microsoft Store, or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and build the app yourself!</span></span>  

## <a name="about-the-team"></a><span data-ttu-id="6b707-171">팀 정보</span><span class="sxs-lookup"><span data-stu-id="6b707-171">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6b707-172"><b>잭 Caron</b></span><span class="sxs-lookup"><span data-stu-id="6b707-172"><b>Jack Caron</b></span></span><br><span data-ttu-id="6b707-173"><i>리드 게임 디자이너</i></span><span class="sxs-lookup"><span data-stu-id="6b707-173"><i>Lead Game Designer</i></span></span><br><span data-ttu-id="6b707-174">현재는 HoloLens 2 프로젝트 및 AltspaceVR를 비롯 하 여 Microsoft의 혼합 현실 환경에서 작동 하며 이전에 HoloLens 플랫폼 팀의 디자이너 였습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-174">Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6b707-175"><b>여름 Wu</b></span><span class="sxs-lookup"><span data-stu-id="6b707-175"><b>Summer Wu</b></span></span><br><span data-ttu-id="6b707-176"><i>Producer</i></span><span class="sxs-lookup"><span data-stu-id="6b707-176"><i>Producer</i></span></span><br><span data-ttu-id="6b707-177">여름은 혼합 현실 개발자 플랫폼에서 작동 하 고 팀의 실제 엔진 관련 활동을 수용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-177">Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</span></span></td>
</tr>
</table>

<span data-ttu-id="6b707-178">Kippy의 이스케이프를 다음 수준으로 [Framestore](https://www.framestore.com/) 하는 데 도움이 되는 친구에 게 특별 해 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-178">Special thanks to our friends at [Framestore](https://www.framestore.com/) for helping us take Kippy’s Escape to the next level.</span></span> <span data-ttu-id="6b707-179">문자 개발, 자산 디자인, 게임 프로그래밍에 이르기까지,이 프로젝트에 대 한 공동 작업은 pivotal 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b707-179">From character development, to asset design, to game programming, their collaboration on this project was pivotal.</span></span>  