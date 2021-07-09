---
title: 4. 대화형 장면 만들기
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 체스 앱을 만드는 자습서 시리즈 4/6부
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 자습서, 시작, mrtk, uxt, UX Tools, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 771dd4028adfacb27544e632aa0f355d3bc91c66
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712608"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="27c7a-104">4. 대화형 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="27c7a-104">4. Making your scene interactive</span></span>

<span data-ttu-id="27c7a-105">이전 자습서에서는 ARSession, Pawn 및 게임 모드를 추가하여 체스 앱에 대한 혼합 현실 설정을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-105">In the previous tutorial, you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="27c7a-106">이 섹션에서는 조작 장면을 만들 수 있는 도구를 제공하는 오픈 소스 [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)의 사용에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-106">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="27c7a-107">이 섹션을 마치면 체스 말이 사용자 입력에 따라 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-107">By the end of this section, your chess pieces will be moving by user input.</span></span>

## <a name="objectives"></a><span data-ttu-id="27c7a-108">목표</span><span class="sxs-lookup"><span data-stu-id="27c7a-108">Objectives</span></span>

* <span data-ttu-id="27c7a-109">Mixed Reality UX Tools 플러그 인 설치</span><span class="sxs-lookup"><span data-stu-id="27c7a-109">Installing the Mixed Reality UX Tools plugin</span></span>
* <span data-ttu-id="27c7a-110">손가락 끝에 손 조작 행위자 추가</span><span class="sxs-lookup"><span data-stu-id="27c7a-110">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="27c7a-111">장면의 개체에 조작자 만들기 및 추가</span><span class="sxs-lookup"><span data-stu-id="27c7a-111">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="27c7a-112">입력 시뮬레이션을 사용하여 프로젝트의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="27c7a-112">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a><span data-ttu-id="27c7a-113">Mixed Reality UX Tools 플러그 인 다운로드</span><span class="sxs-lookup"><span data-stu-id="27c7a-113">Downloading the Mixed Reality UX Tools plugin</span></span>
<span data-ttu-id="27c7a-114">사용자 입력 작업을 시작하기 전에 Mixed Reality UX Tools 플러그 인을 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-114">Before you start working with user input, you'll need to add the Mixed Reality UX Tools plugin to the project.</span></span> <span data-ttu-id="27c7a-115">UX Tools에 대해 자세히 알아보려면 [GitHub](https://aka.ms/uxt-unreal)에서 프로젝트를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="27c7a-115">To learn more about UX Tools, you can check out the project on [GitHub](https://aka.ms/uxt-unreal).</span></span>

1. <span data-ttu-id="27c7a-116">Epic Games Launcher를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-116">Open the Epic Games Launcher.</span></span> <span data-ttu-id="27c7a-117">Unreal Engine Marketplace로 이동하여 "[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)"를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-117">Navigate to Unreal Engine Marketplace and search for "[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)".</span></span> <span data-ttu-id="27c7a-118">엔진에 플러그 인을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-118">Install the plugin to your engine.</span></span>

![Unreal Marketplace](images/unreal-uxt/2-uxt-plugin.PNG)

2. <span data-ttu-id="27c7a-120">Unreal 편집기로 돌아가 **프로젝트 설정** > **플러그 인** 으로 이동하여 "Mixed Reality UX Tools"를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-120">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Mixed Reality UX Tools".</span></span> <span data-ttu-id="27c7a-121">플러그 인이 사용하도록 설정되어 있는지 확인하고 메시지가 나타나면 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-121">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![Mixed Reality UX Tools 플러그 인 사용](images/unreal-uxt/2-enable-uxt.PNG)

3.  <span data-ttu-id="27c7a-123">UXTools 플러그 인에는 **Buttons**, **XR Simulation** 및 **Pointers** 를 포함한 구성 요소에 대한 하위 폴더가 있는 Content 폴더와 추가 코드가 있는 C++ Classes 폴더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-123">The UXTools plugin has a Content folder with subfolders for components, including **Buttons**, **XR Simulation**, and **Pointers**, and a C++ Classes folder with additional code.</span></span>  

> [!NOTE]
> <span data-ttu-id="27c7a-124">**콘텐츠 브라우저** 에 **UXTools 콘텐츠** 섹션이 표시되지 않는 경우 **보기 옵션 > 엔진 콘텐츠 표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-124">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Engine Content**.</span></span>

![엔진 콘텐츠 표시](images/unreal-uxt/4-showenginecontent.PNG)

<span data-ttu-id="27c7a-126">추가 플러그 인 설명서는 Mixed Reality UX Tools GitHub [리포지토리](https://aka.ms/uxt-unreal)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-126">Additional plugin documentation can be found on the Mixed Reality UX Tools GitHub [repository](https://aka.ms/uxt-unreal).</span></span>

<span data-ttu-id="27c7a-127">플러그 인이 설치되면 손 조작 행위자부터 제공하는 도구를 사용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-127">With the plugin installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="27c7a-128">손 조작 행위자 생성</span><span class="sxs-lookup"><span data-stu-id="27c7a-128">Spawning Hand Interaction Actors</span></span>

<span data-ttu-id="27c7a-129">UX 요소에서의 손 조작은 인접 및 원거리 조작을 위한 포인터와 시각적 개체를 만들어 구동하는 손 조작 행위자를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-129">Hand interaction with UX elements is done with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="27c7a-130">*인접 조작* - 집게와 엄지 손가락으로 요소를 집어서, 또는 손끝으로 찌릅니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-130">*Near interactions* - pinching elements between index finger and thumb or by poking them with a fingertip.</span></span>
- <span data-ttu-id="27c7a-131">*원거리 조작* - 요소에 있는 가상 손으로부터 나가는 광선을 가리키고 검지와 엄지를 한꺼번에 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-131">*Far interactions* - pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="27c7a-132">여기서는 **MRPawn** 에 손 상호 작용 행위자를 추가하면 다음 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-132">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="27c7a-133">폰의 집게 손가락 끝에 커서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-133">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="27c7a-134">폰을 통해 조작할 수 있는 관절식 손 입력 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-134">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="27c7a-135">가상 손의 손바닥에서부터 나오는 손 광선을 통해 원거리 조작 입력 이벤트를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-135">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="27c7a-136">계속하기 전에 손 조작에 대한 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)를 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-136">We recommend reading through the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) on hand interactions before continuing.</span></span>

<span data-ttu-id="27c7a-137">준비되면 **MRPawn** 청사진을 열고 **이벤트 그래프** 로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-137">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span>

1. <span data-ttu-id="27c7a-138">**Event BeginPlay** 에서 실행 핀을 끌어다 놓아 새 노드를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-138">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span>
    * <span data-ttu-id="27c7a-139">**클래스에서 행위자 생성** 을 선택하고 **클래스** 핀 옆에 있는 드롭다운을 클릭한 다음, **Uxt 손 조작 행위자** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-139">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span>  

2. <span data-ttu-id="27c7a-140">두 번째 **Uxt 손 조작 행위자** 를 생성합니다. 이번에는 **손** 을 **오른쪽** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-140">Spawn a second **Uxt Hand Interaction Actor**, this time setting the **Hand** to **Right**.</span></span> <span data-ttu-id="27c7a-141">이벤트가 시작되면 각각의 손에 Uxt 손 조작 행위자가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-141">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span>

<span data-ttu-id="27c7a-142">**이벤트 그래프** 는 다음 스크린샷과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-142">Your **Event Graph** should match the following screenshot:</span></span>

![UXT 손 조작 행위자 생성](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="27c7a-144">Uxt 손 조작 행위자에는 소유자와 최초 변환 위치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-144">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="27c7a-145">이 경우 UX Tools는 가상 손이 표시되는 즉시 손 조작 행위자를 이동시키기 때문에 초기 변환은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-145">The initial transform doesn’t matter in this case because UX Tools will have the Hand Interaction Actors jump to the virtual hands as soon as they're visible.</span></span> <span data-ttu-id="27c7a-146">그러나 컴파일러 오류를 방지하려면 `SpawnActor` 함수에 변환 입력이 필요하므로 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-146">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span>

1. <span data-ttu-id="27c7a-147">**변환 생성** 핀 중 하나를 끌어다 놓아 새 노드를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-147">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span>
    * <span data-ttu-id="27c7a-148">**변환** 노드를 검색한 다음, **반환 값** 을 다른 손의 **변환 생성** 으로 끌어 **SpawnActor** 노드가 모두 연결되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-148">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span>

2.  <span data-ttu-id="27c7a-149">두 **SpawnActor** 노드의 하단에서 **아래쪽 화살표** 를 선택하여 **소유자** 핀을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-149">Select the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="27c7a-150">**소유자** 핀 중 하나를 새 노드로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-150">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span>
    * <span data-ttu-id="27c7a-151">**자체** 를 검색하고 **자체 참조 가져오기** 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-151">Search for **self** and select the **Get a reference to self** variable.</span></span>
    * <span data-ttu-id="27c7a-152">**자체** 개체 참조 노드와 다른 손 조작 행위자의 **소유자** 핀 사이에 링크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-152">Create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span>
3. <span data-ttu-id="27c7a-153">마지막으로, 손 조작 행위자 모두에 대해 **잡기 대상에 가까운 커서 표시** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-153">Lastly, check the **Show Near Cursor on Grab Targets** box for both Hand Interaction Actors.</span></span> <span data-ttu-id="27c7a-154">검지 손가락이 가까워지면 잡기 대상에 커서가 나타나야 손가락과 대상의 상대적인 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-154">A cursor should appear on the grab target as your index finger gets close, so you can see where your finger is relative to the target.</span></span>
    * <span data-ttu-id="27c7a-155">**컴파일** 하고, **저장** 하고, 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-155">**Compile**, **save**, and return to the Main window.</span></span>

<span data-ttu-id="27c7a-156">연결이 다음 스크린샷과 일치하는지 확인합니다. 그러나 노드 주변을 자유롭게 끌어 청사진의 가독성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-156">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable.</span></span>

![UXT 손 조작 행위자 설정 완료](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="27c7a-158">손 조작 행위자에 대한 자세한 내용은 [UX Tools 설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-158">You can find more information about Hand Interaction Actors in the [UX Tools documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="27c7a-159">이제 프로젝트의 가상 손이 개체를 선택할 수 있게 되었지만 아직은 조작하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-159">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="27c7a-160">앱을 테스트 하기 전의 마지막 작업은 장면의 행위자에 조작자 구성 요소를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-160">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="27c7a-161">조작자 연결</span><span class="sxs-lookup"><span data-stu-id="27c7a-161">Attaching Manipulators</span></span>

<span data-ttu-id="27c7a-162">조작자는 관절식 손 입력에 응답하고 잡기, 회전 및 전환이 가능한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-162">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="27c7a-163">조작자의 변환을 행위자의 변환에 적용하면 직접 행위자 조작이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-163">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span>

1. <span data-ttu-id="27c7a-164">**Board** 블루프린트에서 **구성 요소 추가** 를 클릭하고 **구성 요소** 패널에서 **Uxt 일반 조작자** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-164">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![일반 조작자 추가](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="27c7a-166">**세부 정보** 패널에서 **일반 조작자** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-166">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="27c7a-167">한손 또는 양손 조작, 회전 모드를 설정하고 여기서부터 다듬기를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-167">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="27c7a-168">원하는 모두를 자유롭게 선택한 다음, 보드를 **컴파일** 하고 **저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-168">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span>

![모드 설정](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="27c7a-170">**WhiteKing** 행위자에 대해 위의 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-170">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="27c7a-171">Mixed Reality UX Tools 플러그 인에서 제공하는 조작자 구성 요소에 대한 자세한 내용은 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-171">You can find more information about the Manipulator Components provided in the Mixed Reality UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="27c7a-172">장면 테스트</span><span class="sxs-lookup"><span data-stu-id="27c7a-172">Testing the scene</span></span>

<span data-ttu-id="27c7a-173">모든 것이 마무리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-173">Good news everyone!</span></span> <span data-ttu-id="27c7a-174">이제 새 가상 손과 사용자 입력으로 앱을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-174">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="27c7a-175">주 창에서 **재생** 을 누르면 두 개의 메시 손의 각 손바닥에서 광선이 나가는 모습을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-175">Press **Play** in the Main Window and you'll see two mesh hands with rays extending from each hand’s palm.</span></span> <span data-ttu-id="27c7a-176">다음과 같이 손과 조작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-176">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="27c7a-177">**왼쪽 Alt** 키를 누른 상태로 **왼손** 을, **왼쪽 Shift** 키를 누른 상태로 **오른손** 을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-177">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span>
- <span data-ttu-id="27c7a-178">마우스를 움직여 손을 움직이고 **마우스 휠** 을 스크롤하여 손을 **앞으로** 또는 **뒤로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-178">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span>
- <span data-ttu-id="27c7a-179">마우스 왼쪽 단추를 사용하면 **손가락 모으기** 동작이 수행되고, 마우스 가운데 단추를 사용하면 **찌르기** 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-179">Use the left mouse button to **pinch** and the middle mouse button to **poke**.</span></span>

> [!NOTE]
> <span data-ttu-id="27c7a-180">여러 헤드셋을 PC에 연결하는 경우 입력 시뮬레이션이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-180">Input simulation may not work if you have multiple headsets plugged into your PC.</span></span> <span data-ttu-id="27c7a-181">문제가 발생하는 경우 다른 헤드셋을 분리해 보세요.</span><span class="sxs-lookup"><span data-stu-id="27c7a-181">If you're having issues, try unplugging your other headsets.</span></span>

![뷰포트의 시뮬레이션된 손](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="27c7a-183">시뮬레이션된 손을 사용하여 백의 체스 킹을 집어서 움직여 본 후 다시 내려놓고 보드를 조작해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-183">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="27c7a-184">근거리 및 원거리 조작을 시험해 보세요. 체스 보드와 킹을 직접 잡을 수 있을 만큼 손이 가까워지면 손에서 나가는 손 광선이 검지 손가락 끝의 손가락 커서로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-184">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, a finger cursor at the tip of the index finger replaces the hand ray.</span></span>

<span data-ttu-id="27c7a-185">MRTK UX Tools 플러그 인에서 제공하는 시뮬레이션된 손 기능에 대한 자세한 내용은 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-185">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="27c7a-186">이제 가상 손이 개체와 상호 작용할 수 있으므로 다음 자습서를 진행하여 사용자 인터페이스와 이벤트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c7a-186">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="27c7a-187">다음 섹션: 5. 단추 추가 및 조각 위치 재설정</span><span class="sxs-lookup"><span data-stu-id="27c7a-187">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
