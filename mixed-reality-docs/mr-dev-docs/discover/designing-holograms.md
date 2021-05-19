---
title: 홀로그램 디자인
description: Microsoft의 새로운 Holograms 애플리케이션 디자인을 통해 Mixed Reality 대해 알아봅니다.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, 홀로그램, 홀로그램 디자인, 학습, 샘플 앱, 혼합 현실 헤드셋, 가상 현실 헤드셋, 가상 현실이란?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143632"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="62c8a-104">홀로그램 디자인</span><span class="sxs-lookup"><span data-stu-id="62c8a-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="62c8a-105">이 페이지의 모든 멋진 GIF 및 포함된 비디오를 설명하는 작은 로드 창을 허용하세요.</span><span class="sxs-lookup"><span data-stu-id="62c8a-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="62c8a-106">혼합 현실용으로 디자인하는 방법을 학습하는 것은 미디어가 항상 2D 디자인 프로세스로 잘 변환되지 않기 때문에 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="62c8a-107">Microsoft에서는 혼합 현실 UX 디자인의 기본 내용을 직접 학습하는 데 도움이 되는 HoloLens 2 대한 무료 앱을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="62c8a-108">Holograms 앱 디자인의 고유한 접근 방식은 혼합 현실 동작, 팁 및 권장 사항을 자세히 분석하여 사용자 고유의 흥미롭고 놀라운 HoloLens 앱을 만드는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="62c8a-109">Microsoft Store 무료로 앱을 다운로드하고 Microsoft의 Mixed Reality 디자인 팀에서 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="62c8a-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="62c8a-110">홀로그램 디자인 앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="62c8a-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![디자인 홀로그램 데모실의 머리 추적 장면에 대한 애니메이션 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="62c8a-112">*Hologram의 데모실 디자인(마스어하우스라고도 함)*</span><span class="sxs-lookup"><span data-stu-id="62c8a-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="62c8a-113">혼합 현실 디자인</span><span class="sxs-lookup"><span data-stu-id="62c8a-113">Designing for mixed reality</span></span>

<span data-ttu-id="62c8a-114">많은 사용자와 마찬가지로 모바일 앱을 디자인하는 데 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="62c8a-115">2D 디자인 세계에서 들어오는 공간 컴퓨팅은 이제 모든 것이 전 세계에 있는 전체 공간 컴퓨팅으로 전환하는 것이 상당한 변화였습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="62c8a-116">혼합 현실에서 앱은 더 이상 2D 화면으로 제한되지 않습니다. 실제로 거의 무료이며 실제 세계에 배치되고 실제 개체와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="62c8a-117">3D 환경을 기존 2D 디자인 프로세스에 연결하는 것은 혼합 현실 개발에서 가장 어려운 측면입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="62c8a-118">고객과의 대화에서 "포함할 기능과 기능을 시작하고 실행하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="62c8a-119">코드입니다. 문서와 자습서를 따를 수 있지만 사용자 환경은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="62c8a-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="62c8a-120">많은 기능, 다양한 입력 옵션, 다양한 시나리오 및 물리적 환경이 너무 많아서 너무 많습니다."</span><span class="sxs-lookup"><span data-stu-id="62c8a-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="62c8a-121">![Hololens 2의 hololens 2 디자인 워크숍의 이미지-샌프란시스코 ](images/designing-holograms/workshop.jpeg)
 *2 디자인 워크숍* 의 샌프란시스코 이미지</span><span class="sxs-lookup"><span data-stu-id="62c8a-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="62c8a-122">학습 기회</span><span class="sxs-lookup"><span data-stu-id="62c8a-122">An opportunity to teach</span></span>

<span data-ttu-id="62c8a-123">처음에는 분명히 알 수 없지만 혼합 현실를 미디어로 사용 하 여 학습 하는 것이 뛰어난 기회를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="62c8a-124">Holograms 디자인은 혼합 현실 디자인 개념 및 권장 사항을 설명 하는 시각적 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="62c8a-125">단지 사용자와 혼합 현실 설계 개념을 보여 주는 가상 교사입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="62c8a-126">모든 것은 사용자의 고유한 공간에서 환경을 확실 하 게 제공 하는 세 번째 사용자 관점에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="62c8a-127">*Holograms 트레일러 비디오 디자인*</span><span class="sxs-lookup"><span data-stu-id="62c8a-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="62c8a-128">인형 집 탐색</span><span class="sxs-lookup"><span data-stu-id="62c8a-128">Exploring the doll house</span></span>

<span data-ttu-id="62c8a-129">인형 회사는 앱 전체에서 사용 하는 가상 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="62c8a-130">환경은 벽, 전구, 가구, 테이블, TV 등 대부분의 방에 공통적으로 포함 하는 기본 요소를 포함 하는 80 x 60 x 40-cm 소형 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="62c8a-131">인형 회사는 앱 환경의 주요 protagonist 모든 환경에서 잘 작동 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="62c8a-132">모든 종류의 혼합 현실 개념을 시각화할 수 있는 작은 데모 공간 이라고 생각 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="62c8a-133">*Dollhouse 조정 동작 비디오*</span><span class="sxs-lookup"><span data-stu-id="62c8a-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="62c8a-134">1:1 vs 1:10 프로토타입</span><span class="sxs-lookup"><span data-stu-id="62c8a-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="62c8a-135">처음에는 실제 교사와 거의 유사 하 게 1:1 데모를 사용할 수 있다고 가정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="62c8a-136">사용자는 선생님이 실제 규모에서 볼 수 있는 모든 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="62c8a-137">그러나 다음과 같은 몇 가지 문제가 있다는 것을 즉시 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="62c8a-138">대부분의 개발자는 사무실에서 앱을 실행 하거나, 데모 공간 보다 작은 방에서 앱을 실행 하므로 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="62c8a-139">표시는 추가 가능 합니다. 즉, 전체 가상 환경이 사용자의 방에 걸쳐 중첩 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="62c8a-140">두 테이블, 즉 두 개의 테이블을 사용 하면 혼동을 couches 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="62c8a-141">그리고 모든 가상 환경이 보기 필드로 크게 제한되는 최악의 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="62c8a-142">미니 1:10 배율로 시도한 결과는 사실적인 방의 멋진 조감도였습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="62c8a-143">모든 각도에서 동시에 진행되는 모든 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="62c8a-144">가장 놀라운 점은 대부분의 테스터가 작은 버전을 보기 위해 훨씬 더 몰입형을 찾은 다음, 1:1 규모로 다시 전환하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="62c8a-145">따라서 실제로 1:1 버전을 폐기하고 UI 및 앱의 다른 측면을 조정하는 데 필요한 추가 작업을 방지하기로 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="62c8a-146">![1:1 배율의 ](images/designing-holograms/1-1-scale.png)
 *필드1:1 배율의 보기 필드*</span><span class="sxs-lookup"><span data-stu-id="62c8a-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="62c8a-147">![1:10 배율의 ](images/designing-holograms/1-10-scale.png)
 *필드1:10 배율의 보기 필드*</span><span class="sxs-lookup"><span data-stu-id="62c8a-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="62c8a-148">혼합 현실 캡처 사용</span><span class="sxs-lookup"><span data-stu-id="62c8a-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="62c8a-149">이 앱의 가장 특징적인 기능 중 하나는 혼합 현실 캡처 사용하여 혼합 현실 디자인 개념을 교육하고 시연하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="62c8a-150">Microsoft는 샌프란시스코에 혼합 현실 캡처 Studio를 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="62c8a-151">또한 Microsoft는 이 기술을 워싱턴 D.C.의 아바타 차원, 로스앤젤레스의 메타 스테이지, 런던 차원 스튜디오, Sk Telecom inAngeles 및필로의 Volucap을 비롯한 다른 스튜디오에 라이선스를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="62c8a-152">[혼합 현실 캡처 Studio에](https://www.microsoft.com/mixed-reality/capture-studios)대한 자세한 내용은 여기에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="62c8a-153">*샌프란시스코의 혼합 현실 캡처 Studio에 있는 106대의 카메라 중 하나에서 나온 Daniel Escudero의 원시 장면입니다.*</span><span class="sxs-lookup"><span data-stu-id="62c8a-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="62c8a-154">캡처 프로세스는 추가 프로덕션 후를 위해 OBJ/PNG 파일로 배달되거나 H.264 압축 MP4 파일로 재생할 준비가 될 수 있는 키 프레임 메시, 기본 및 질감을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="62c8a-155">이러한 파일을 Unity, Unreal, Native 및 WebXR 프로젝트로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="62c8a-156">파일은 Windows, iOS, Mac, Android, Magic Leap 및 Playstation VR에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="62c8a-157">*오디오 및 포함된 메시가 있는 비디오가 포함된 mp4를 분석하기 위해 제공된 캡처 플레이어입니다.*</span><span class="sxs-lookup"><span data-stu-id="62c8a-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="62c8a-158">캡처 및 가상 개체 조작</span><span class="sxs-lookup"><span data-stu-id="62c8a-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="62c8a-159">Mixed Reality 캡처는 사람 또는 동물에 대한 가상 표현을 생성하지만, 때로는 다른 가상 개체와 상호 작용하기 위해 해당 문자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="62c8a-160">다음 두 예제에서는 이러한 효과를 얻기 위해 장면을 조작 하는 다양 한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="62c8a-161">헤드 응시 조정</span><span class="sxs-lookup"><span data-stu-id="62c8a-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="62c8a-162">헤드 응시 조정을 사용 하면 캡처된 사람의 헤드를 런타임에 이동할 수 있습니다. 즉, 사용자에 대 한 캡처 얼굴을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="62c8a-163">여기서는이를 사용 하 여 보기 필드와 관심 있는 필드를 표시 했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="62c8a-164">아래에서 볼 수 있는 것은 헤드 응시에서 볼 수 있는 대상의 역할을 하는 이동 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="62c8a-165">대상을 측에서 쪽으로 이동 하는 경우 캡처의 헤드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="62c8a-166">이 트릭을 사용 하 여 유휴 캡처가 항상 인형의 서로 다른 부분에 배치 된 holograms에 직면 하 고 있는지 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처 헤드입니다.](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="62c8a-168">*Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처의 헤드입니다.*</span><span class="sxs-lookup"><span data-stu-id="62c8a-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="62c8a-169">애니메이션 개체 동기화</span><span class="sxs-lookup"><span data-stu-id="62c8a-169">Syncing Animated Objects</span></span>

<span data-ttu-id="62c8a-170">두 번째는 개체에서 캡처 이동과의 동기화에 애니메이션을 적용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="62c8a-171">앱의 여러 부분에서 5 개 프레임 마다 특정 캡처의 순차적 Obj을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="62c8a-172">그런 다음 Obj는이 캡처의 해당 프레임과 일치 하는지 확인 하기 위해 장면에 애니메이션을 적용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="62c8a-173">애니메이션 및 프레임을 적용 하는 지루한 작업 이지만 결과는 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="62c8a-174">이제 캡처되지 않은 개체와 상호 작용 하는 혼합 현실 캡처가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="62c8a-176">*혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션*</span><span class="sxs-lookup"><span data-stu-id="62c8a-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="62c8a-177">UI 창작 프로세스</span><span class="sxs-lookup"><span data-stu-id="62c8a-177">UI creative process</span></span>

<span data-ttu-id="62c8a-178">UI 디자인을 시작할 때 holograms에서 제공 해야 하는 몇 가지 매직 및 가능성을 보여 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="62c8a-179">단순히 정적 2D 창과 텍스트 상자를 표시 하는 것은 3D 세계에서 적절 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="62c8a-180">많은 가능성이 표시되지 않으므로 처음부터 바로 이를 벗어나 홀로그램 3D 공간을 최대한 활용하기로 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="62c8a-181">처음에는 패널, 아이콘 및 텍스트 정보에 일부 두께를 추가하는 것으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="62c8a-182">그래도 사용자가 볼 수 있는 것은 텍스트 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="62c8a-183">이미지가 있는 입력란이지만, 아직 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="62c8a-184">MRTK(Mixed Reality Toolkit) 셰이더를 사용하여 더 발전했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="62c8a-185">MRTK 셰이더가 강력한 도구가 되었으며, 스텐실 기능을 사용하여 패널에 음의 깊이를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="62c8a-186">즉, 텍스트 상자 앞에 요소를 추가하는 대신 이제 아이콘이 투명 패널 뒤에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="62c8a-187">이제 사용자로 볼 수 있는 것은 실제 세계에서 더 이상 복제할 수 없는 것이며, 홀로그램 매직이 발생하기 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="62c8a-188">또한 실제로 읽고 싶지 않은 사용자로서 실제 세계에서 이미 많은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="62c8a-189">물론 아이콘은 간단한 텍스트보다 훨씬 더 잘 작동합니다. 훨씬 더 강력한 지침을 제공하기 위해 애니메이션 개체 및 아바타 집합을 만들기 시작했습니다. 각 아이콘은 각 시나리오에서 수행되는 작업과 사용 방법에 대한 작은 스토리를 제공하기 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![대화형 홀로그램 메뉴 시스템의 애니메이션 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="62c8a-191">핵심 개념</span><span class="sxs-lookup"><span data-stu-id="62c8a-191">Core concepts</span></span>

<span data-ttu-id="62c8a-192">**헤드 추적 및 시선 추적**</span><span class="sxs-lookup"><span data-stu-id="62c8a-192">**Head Tracking and Eye Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="62c8a-193">**손 추적**</span><span class="sxs-lookup"><span data-stu-id="62c8a-193">**Hand Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="62c8a-194">**공간 인식**</span><span class="sxs-lookup"><span data-stu-id="62c8a-194">**Spatial Awareness**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="62c8a-195">**홀로그램 프레임**</span><span class="sxs-lookup"><span data-stu-id="62c8a-195">**Holographic frame**</span></span>

![홀로그램 프레임이 강조 표시된 톨로지 주변을 둘러보는 사용자의 애니메이션 GIF](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="62c8a-197">**좌표계**</span><span class="sxs-lookup"><span data-stu-id="62c8a-197">**Coordinate systems**</span></span>

![좌표계가 강조 표시된 좌표집을 둘러보는 사용자의 애니메이션 GIF](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="62c8a-199">**시선 추적**</span><span class="sxs-lookup"><span data-stu-id="62c8a-199">**Eye tracking**</span></span>

![시선 응시 광선이 강조 표시된 고정 홀로그램을 보는 사용자의 애니메이션 GIF](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="62c8a-201">**공간 검색 시각화 및 공간 매핑**</span><span class="sxs-lookup"><span data-stu-id="62c8a-201">**Room scan visualization and spatial mapping**</span></span>

![매핑되는 히어하우스 내의 모든 표면의 애니메이션 GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="62c8a-203">**장면 이해**</span><span class="sxs-lookup"><span data-stu-id="62c8a-203">**Scene understanding**</span></span>

![인식되는 달하우스의 개체에 대한 애니메이션 GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="62c8a-205">**직접 광선을 사용 하 여 점 및 커밋**</span><span class="sxs-lookup"><span data-stu-id="62c8a-205">**Point and commit with hand rays**</span></span>

![손으로 강조 표시 된 손으로 그린 사용자의 애니메이션 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="62c8a-207">"시험 사용해 보기" 분</span><span class="sxs-lookup"><span data-stu-id="62c8a-207">"Try it out" moments</span></span>

<span data-ttu-id="62c8a-208">Holograms을 디자인 하는 것은 혼합 현실 개념 이지만 방에서 사용해 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-208">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="62c8a-209">이러한 설명 중 일부를 일시 중지 하 고 대화형으로 이동 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-209">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="62c8a-210">이러한 대화형 순간의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-210">Here are some examples of those interactive moments:</span></span>

![손이 검색 된 시간과 보기 필드를 입력 하는 시점을 보여 주는 손 추적 프레임의 애니메이션 GIF](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="62c8a-212">*손 모양 추적 프레임은 손을 검색 하는 시기와 보기 필드를 입력 하는 시간을 보여 줍니다.*</span><span class="sxs-lookup"><span data-stu-id="62c8a-212">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![먼 상호 작용을 통해 충돌 하는 crystals와 상호 작용 하는 애니메이션 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="62c8a-214">*먼 상호 작용을 통해 충돌 하는 crystals 상호 작용*</span><span class="sxs-lookup"><span data-stu-id="62c8a-214">*Interacting with colliding crystals through far interaction*</span></span>

![거의 상호 작용 affordances를 탐색 하는 애니메이션 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="62c8a-216">*거의 상호 작용 affordances 탐색*</span><span class="sxs-lookup"><span data-stu-id="62c8a-216">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="62c8a-217">팀 정보</span><span class="sxs-lookup"><span data-stu-id="62c8a-217">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="62c8a-218"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="62c8a-218"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="62c8a-219"><i>선임 기술 디자이너</i></span><span class="sxs-lookup"><span data-stu-id="62c8a-219"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="62c8a-220">Dan은 Holograms 디자인에 대 한 독창적인 담당 이사 이며 현재는 샌프란시스코의 Microsoft Mixed Reality 아카데미를 위한 디자인 리드로 작동 하며, 이전에는 런던의 Microsoft Mixed Reality 스튜디오 중 하나인 디자이너 였습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-220">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="62c8a-221"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="62c8a-221"><b>Martin Wettig</b></span></span><br><span data-ttu-id="62c8a-222"><i>선임 3D 음악가</i></span><span class="sxs-lookup"><span data-stu-id="62c8a-222"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="62c8a-223">Martin는 Holograms 디자인에 3D 아트 및 UI 디자인을 선도 하며, 이전에는 베를린의 Microsoft Mixed Reality 스튜디오 중 하나에서 선임 3D 음악가 였습니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-223">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="62c8a-224">매우 많은 정보를 공유 하 고, [개체 이론](https://objecttheory.com/) 에서 프로젝트의 모든 단계를 통해 필수적인 팀으로 서 많은 정보를 공유 하기 위해 혼합 현실 설계 팀에 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-224">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="62c8a-225">디자인에 대한 열정을 가지고 뛰어난 시각을 발휘해 주셔서 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="62c8a-225">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="62c8a-226">홀로그램 디자인 앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="62c8a-226">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)