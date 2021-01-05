---
title: 홀로그램 디자인
description: Microsoft의 새로운 디자인 Holograms 응용 프로그램을 통해 혼합 현실에 대해 알아보세요.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, holograms, 디자인 Holograms, 학습, 샘플 앱, 혼합 현실 헤드셋, 가상 현실 헤드셋, 가상 현실 이란?
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757761"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="4c15d-104">Holograms 디자인</span><span class="sxs-lookup"><span data-stu-id="4c15d-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="4c15d-105">이 페이지의 모든 쿨 Gif 및 포함 된 비디오를 고려 하는 작은 로드 창에 대해 허용 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c15d-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="4c15d-106">약간의 혼합 현실 디자인 방법은 항상 2D 디자인 프로세스에 잘 변환 되지 않기 때문에 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="4c15d-107">Microsoft의 Microsoft는이 문서에 나와 있는 Microsoft의 Microsoft에서는 혼합 현실 UX Design 어떠한 체험의 기본 사항을 배우는 데 도움이 되는 HoloLens 2 용 무료 앱을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="4c15d-108">Holograms 앱 디자인의 고유한 접근 방식은 혼합 현실 동작, 팁 및 권장 사항을 제공 하 여 사용자가 직접 매력적인 HoloLens 앱을 만드는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="4c15d-109">Microsoft Store에서 무료로 무료로 앱을 다운로드 하 고 Microsoft의 혼합 현실 디자인 팀에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="4c15d-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4c15d-110">Holograms 앱 디자인 다운로드</span><span class="sxs-lookup"><span data-stu-id="4c15d-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![홀로그램의 데모 객실 디자인에서 헤드 추적 장면의 애니메이션 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="4c15d-112">*홀로그램의 데모 실 디자인 (인형 집이 라고도 함)*</span><span class="sxs-lookup"><span data-stu-id="4c15d-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="4c15d-113">혼합 현실 디자인</span><span class="sxs-lookup"><span data-stu-id="4c15d-113">Designing for mixed reality</span></span>

<span data-ttu-id="4c15d-114">많은 사용자와 마찬가지로 모바일 앱을 설계 하는 데 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="4c15d-115">2D 디자인 환경에서 제공 되는 모든 것이 세계에 있는 공간 컴퓨팅에서 전체로 이동 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="4c15d-116">혼합 현실에서 앱은 더 이상 2D 화면으로 제한 되지 않습니다. 실제로는 거의 무료 이며 실제 개체와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="4c15d-117">기존 2D 디자인 프로세스에 3D 환경을 연결 하는 것은 혼합 현실 개발의 가장 어려운 측면입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="4c15d-118">고객과 대화 하는 경우 "포함할 기능 및 다운로드 및 실행 방법에 대해 알고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="4c15d-119">코드입니다. 문서와 자습서를 따를 수 있지만 사용자 경험을 따를 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="4c15d-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="4c15d-120">따라서 다양 한 기능, 다양 한 입력 옵션, 다양 한 시나리오 및 물리적 환경을 제공 합니다. "</span><span class="sxs-lookup"><span data-stu-id="4c15d-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="4c15d-121">![Hololens 2의 hololens 2 디자인 워크숍의 이미지-샌프란시스코 ](images/designing-holograms/workshop.jpeg)
 *2 디자인 워크숍* 의 샌프란시스코 이미지</span><span class="sxs-lookup"><span data-stu-id="4c15d-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="4c15d-122">학습 기회</span><span class="sxs-lookup"><span data-stu-id="4c15d-122">An opportunity to teach</span></span>

<span data-ttu-id="4c15d-123">처음에는 분명히 알 수 없지만 혼합 현실를 미디어로 사용 하 여 학습 하는 것이 뛰어난 기회를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="4c15d-124">Holograms 디자인은 혼합 현실 디자인 개념 및 권장 사항을 설명 하는 시각적 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="4c15d-125">단지 사용자와 혼합 현실 설계 개념을 보여 주는 가상 교사입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="4c15d-126">모든 것은 사용자의 고유한 공간에서 환경을 확실 하 게 제공 하는 세 번째 사용자 관점에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="4c15d-127">*Holograms 트레일러 비디오 디자인*</span><span class="sxs-lookup"><span data-stu-id="4c15d-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="4c15d-128">인형 집 탐색</span><span class="sxs-lookup"><span data-stu-id="4c15d-128">Exploring the doll house</span></span>

<span data-ttu-id="4c15d-129">인형 회사는 앱 전체에서 사용 하는 가상 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="4c15d-130">환경은 벽, 전구, 가구, 테이블, TV 등 대부분의 방에 공통적으로 포함 하는 기본 요소를 포함 하는 80 x 60 x 40-cm 소형 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="4c15d-131">인형 회사는 앱 환경의 주요 protagonist 모든 환경에서 잘 작동 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="4c15d-132">모든 종류의 혼합 현실 개념을 시각화할 수 있는 작은 데모 공간 이라고 생각 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="4c15d-133">*Dollhouse 조정 동작 비디오*</span><span class="sxs-lookup"><span data-stu-id="4c15d-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="4c15d-134">1:1 vs 1:10 프로토타입</span><span class="sxs-lookup"><span data-stu-id="4c15d-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="4c15d-135">처음에는 실제 교사와 거의 유사 하 게 1:1 데모를 사용할 수 있다고 가정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="4c15d-136">사용자는 선생님이 실제 규모에서 볼 수 있는 모든 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="4c15d-137">그러나 다음과 같은 몇 가지 문제가 있다는 것을 즉시 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="4c15d-138">대부분의 개발자는 사무실에서 앱을 실행 하거나, 데모 공간 보다 작은 방에서 앱을 실행 하므로 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="4c15d-139">표시는 추가 가능 합니다. 즉, 전체 가상 환경이 사용자의 방에 걸쳐 중첩 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="4c15d-140">두 테이블, 즉 두 개의 테이블을 사용 하면 혼동을 couches 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="4c15d-141">그리고 모든 가상 환경의 최악의 경우 보기의 필드에 의해 과도 하 게 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="4c15d-142">미니 1:10 규모를 사용해 볼 때 그 결과는 현실적인 공간에 대 한 훌륭한 상의 눈에 보기 였습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="4c15d-143">모든 각도에서 동시에 진행 된 모든 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="4c15d-144">가장 놀라운 일은 대부분의 테스터가 작은 버전을 보기 위해 훨씬 더 몰입 형을 발견 하는 것입니다. 즉, 1:1 배율로 다시 전환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="4c15d-145">따라서 실제로 1:1 버전을 스크랩 하 고 UI 및 앱의 다른 측면을 조정 하는 데 필요한 추가 작업을 방지 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="4c15d-146">![](images/designing-holograms/1-1-scale.png)
*1:1 소수 자릿수가 있는* 보기의 1:1 눈금 필드가 있는 보기 필드</span><span class="sxs-lookup"><span data-stu-id="4c15d-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="4c15d-147">![](images/designing-holograms/1-10-scale.png)
*1:10 소수 자릿수가 있는* 보기의 1:10 눈금 필드가 있는 보기 필드</span><span class="sxs-lookup"><span data-stu-id="4c15d-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="4c15d-148">혼합 현실 캡처 사용</span><span class="sxs-lookup"><span data-stu-id="4c15d-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="4c15d-149">이 앱의 특징 중 하나는 혼합 현실 캡처를 사용 하 여 혼합 현실 디자인 개념을 학습 하 고 시연 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="4c15d-150">Microsoft에는 샌프란시스코의 혼합 현실 캡처 스튜디오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="4c15d-151">Microsoft는 워싱턴 D.C, Metastage의 스튜디오, 런던의 Dimension 스튜디오, 서울의, 서울의, 서울의 Vol텔레콤 및 베를린의 Volap와 같은 다른에이 기술을 라이선스 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="4c15d-152">[여기에서 혼합 현실 캡처 스튜디오](https://www.microsoft.com/mixed-reality/capture-studios)에 대 한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="4c15d-153">*Daniel Escudero의 원시 푸티지는 샌프란시스코의 혼합 현실 캡처 스튜디오에서 106 카메라 중 하나에서 시작 합니다.*</span><span class="sxs-lookup"><span data-stu-id="4c15d-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="4c15d-154">캡처 프로세스는 keyframed 메시, 법선 및 질감을 생성 합니다 .이는 추가 사후 프로덕션을 위해 OBJ/PNG 파일로 전달 하거나, h.264 압축 MP4 파일로 재생할 준비를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="4c15d-155">이러한 파일은 Unity, Unreal, Native 및 WebXR 프로젝트로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="4c15d-156">파일은 Windows, iOS, Mac, Android, 매직 Leap 및 Playstation VR에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="4c15d-157">*오디오 및 포함 된 메시를 사용 하 여 비디오를 포함 하는 mp4를 분석 하기 위해 제공 된 캡처 플레이어입니다.*</span><span class="sxs-lookup"><span data-stu-id="4c15d-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="4c15d-158">캡처 및 가상 개체 조작</span><span class="sxs-lookup"><span data-stu-id="4c15d-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="4c15d-159">혼합 현실 캡처는 사람이 나 동물의 가상 표현을 생성 하지만, 때때로 다른 가상 개체와 상호 작용 하는 문자를 필요로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="4c15d-160">다음 두 예제에서는 이러한 효과를 얻기 위해 장면을 조작 하는 다양 한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="4c15d-161">헤드 응시 조정</span><span class="sxs-lookup"><span data-stu-id="4c15d-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="4c15d-162">헤드 응시 조정을 사용 하면 캡처된 사람의 헤드를 런타임에 이동할 수 있습니다. 즉, 사용자에 대 한 캡처 얼굴을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="4c15d-163">여기서는이를 사용 하 여 보기 필드와 관심 있는 필드를 표시 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="4c15d-164">아래에서 볼 수 있는 것은 헤드 응시에서 볼 수 있는 대상의 역할을 하는 이동 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="4c15d-165">대상을 측에서 쪽으로 이동 하는 경우 캡처의 헤드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="4c15d-166">이 트릭을 사용 하 여 유휴 캡처가 항상 인형의 서로 다른 부분에 배치 된 holograms에 직면 하 고 있는지 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처 헤드입니다.](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="4c15d-168">*Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처의 헤드입니다.*</span><span class="sxs-lookup"><span data-stu-id="4c15d-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="4c15d-169">애니메이션 개체 동기화</span><span class="sxs-lookup"><span data-stu-id="4c15d-169">Syncing Animated Objects</span></span>

<span data-ttu-id="4c15d-170">두 번째는 개체에서 캡처 이동과의 동기화에 애니메이션을 적용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="4c15d-171">앱의 여러 부분에서 5 개 프레임 마다 특정 캡처의 순차적 Obj을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="4c15d-172">그런 다음 Obj는이 캡처의 해당 프레임과 일치 하는지 확인 하기 위해 장면에 애니메이션을 적용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="4c15d-173">애니메이션 및 프레임을 적용 하는 지루한 작업 이지만 결과는 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="4c15d-174">이제 캡처되지 않은 개체와 상호 작용 하는 혼합 현실 캡처가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="4c15d-176">*혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션*</span><span class="sxs-lookup"><span data-stu-id="4c15d-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="4c15d-177">UI 창작 프로세스</span><span class="sxs-lookup"><span data-stu-id="4c15d-177">UI creative process</span></span>

<span data-ttu-id="4c15d-178">UI 디자인을 시작할 때 holograms에서 제공 해야 하는 몇 가지 매직 및 가능성을 보여 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="4c15d-179">단순히 정적 2D 창과 텍스트 상자를 표시 하는 것은 3D 세계에서 적절 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="4c15d-180">그 외에도 대부분의 가능성은 표시 되지 않으므로 처음부터 그 밖으로 이동 하 여 holographic 3D 공간을 모두 사용 하도록 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="4c15d-181">처음에는 패널, 아이콘 및 텍스트 정보에 일부 두께를 추가 하는 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="4c15d-182">사용자로 서는 텍스트 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="4c15d-183">이미지가 있는 텍스트 상자에는 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="4c15d-184">이제 MRTK (Mixed Reality Toolkit) 셰이더를 사용 하 여 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="4c15d-185">MRTK 셰이더는 강력한 도구가 되었으며 스텐실 기능을 사용 하 여 패널에 음수 깊이를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="4c15d-186">즉, 입력란 앞에 요소를 추가 하는 대신 아이콘이 투명 패널 뒤에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="4c15d-187">사용자로 서 이제는 더 이상 실제 지역에서 복제할 수 없는 것으로 표시 되며,이는 holographic magic이 시작 되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="4c15d-188">또한 실제로 읽을 필요가 없는 사용자는 이미 실제 세계에 있는 많은 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="4c15d-189">분명히 아이콘은 간단한 텍스트 보다 훨씬 더 효율적으로 작동 하므로 훨씬 더 강력한 지침을 제공 하 고, 애니메이션 개체 및 아바타 집합을 만들기 시작 하 고 각각의 시나리오에서 수행 되는 작업 및 사용 방법에 대 한 간단한 스토리를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![대화형 holographic 메뉴 시스템의 애니메이션 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="4c15d-191">핵심 개념</span><span class="sxs-lookup"><span data-stu-id="4c15d-191">Core concepts</span></span>

<span data-ttu-id="4c15d-192">**홀로그램 프레임**</span><span class="sxs-lookup"><span data-stu-id="4c15d-192">**Holographic frame**</span></span>

![Holographic 프레임이 강조 표시 된 상태에서 dollhouse를 찾는 사용자의 애니메이션 GIF](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="4c15d-194">**좌표계**</span><span class="sxs-lookup"><span data-stu-id="4c15d-194">**Coordinate systems**</span></span>

![좌표계가 강조 표시 된 상태로 dollhouse를 찾는 사용자의 애니메이션 GIF](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="4c15d-196">**시선 추적**</span><span class="sxs-lookup"><span data-stu-id="4c15d-196">**Eye tracking**</span></span>

![눈에 보이는 응시 빛이 강조 표시 된 고정 된 holograms를 확인 하는 사용자의 애니메이션 GIF](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="4c15d-198">**대화방 스캔 시각화 및 공간 매핑**</span><span class="sxs-lookup"><span data-stu-id="4c15d-198">**Room scan visualization and spatial mapping**</span></span>

![매핑되는 dollhouse 내 모든 표면의 애니메이션 GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="4c15d-200">**장면 이해**</span><span class="sxs-lookup"><span data-stu-id="4c15d-200">**Scene understanding**</span></span>

![인식 되는 dollhouse의 개체에 대 한 애니메이션 GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="4c15d-202">**직접 광선을 사용 하 여 점 및 커밋**</span><span class="sxs-lookup"><span data-stu-id="4c15d-202">**Point and commit with hand rays**</span></span>

![손으로 강조 표시 된 손으로 그린 사용자의 애니메이션 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="4c15d-204">"시험 사용해 보기" 분</span><span class="sxs-lookup"><span data-stu-id="4c15d-204">"Try it out" moments</span></span>

<span data-ttu-id="4c15d-205">Holograms을 디자인 하는 것은 혼합 현실 개념 이지만 방에서 사용해 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="4c15d-206">이러한 설명 중 일부를 일시 중지 하 고 대화형으로 이동 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="4c15d-207">이러한 대화형 순간의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-207">Here are some examples of those interactive moments:</span></span>

![손이 검색 된 시간과 보기 필드를 입력 하는 시점을 보여 주는 손 추적 프레임의 애니메이션 GIF](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="4c15d-209">*손 모양 추적 프레임은 손을 검색 하는 시기와 보기 필드를 입력 하는 시간을 보여 줍니다.*</span><span class="sxs-lookup"><span data-stu-id="4c15d-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![먼 상호 작용을 통해 충돌 하는 crystals와 상호 작용 하는 애니메이션 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="4c15d-211">*먼 상호 작용을 통해 충돌 하는 crystals 상호 작용*</span><span class="sxs-lookup"><span data-stu-id="4c15d-211">*Interacting with colliding crystals through far interaction*</span></span>

![거의 상호 작용 affordances를 탐색 하는 애니메이션 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="4c15d-213">*거의 상호 작용 affordances 탐색*</span><span class="sxs-lookup"><span data-stu-id="4c15d-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="4c15d-214">팀 정보</span><span class="sxs-lookup"><span data-stu-id="4c15d-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="4c15d-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="4c15d-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="4c15d-216"><i>선임 기술 디자이너</i></span><span class="sxs-lookup"><span data-stu-id="4c15d-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="4c15d-217">Dan은 Holograms 디자인에 대 한 독창적인 담당 이사 이며 현재는 샌프란시스코의 Microsoft Mixed Reality 아카데미를 위한 디자인 리드로 작동 하며, 이전에는 런던의 Microsoft Mixed Reality 스튜디오 중 하나인 디자이너 였습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="4c15d-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="4c15d-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="4c15d-219"><i>선임 3D 음악가</i></span><span class="sxs-lookup"><span data-stu-id="4c15d-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="4c15d-220">Martin는 Holograms 디자인에 3D 아트 및 UI 디자인을 선도 하며, 이전에는 베를린의 Microsoft Mixed Reality 스튜디오 중 하나에서 선임 3D 음악가 였습니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="4c15d-221">매우 많은 정보를 공유 하 고, [개체 이론](https://objecttheory.com/) 에서 프로젝트의 모든 단계를 통해 필수적인 팀으로 서 많은 정보를 공유 하기 위해 혼합 현실 설계 팀에 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="4c15d-222">열정과 디자인의 뛰어난 눈에 대해 놀라운 인재을 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c15d-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4c15d-223">Holograms 앱 디자인 다운로드</span><span class="sxs-lookup"><span data-stu-id="4c15d-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)