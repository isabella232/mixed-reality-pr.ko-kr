---
title: 첫 번째 HoloLens Unreal 애플리케이션 만들기
description: HoloLens 혼합 현실 개발을 위해 장면 개체 및 입력 상호 작용을 사용하여 Unreal 프로젝트를 올바르게 구성하는 방법을 알아봅니다.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal 편집기, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421432"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="44aba-104">첫 번째 HoloLens Unreal 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="44aba-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="44aba-105">이 가이드는 Unreal Engine의 HoloLens에서 첫 번째 혼합 현실 앱을 실행하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="44aba-106">화면에 큐브를 표시하는 간단한 앱을 만듭니다("Hello World"와 유사함).</span><span class="sxs-lookup"><span data-stu-id="44aba-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="44aba-107">유용성을 높이기 위해 큐브를 돌리고 애플리케이션을 종료하는 첫 번째 제스처도 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="44aba-108">목표</span><span class="sxs-lookup"><span data-stu-id="44aba-108">Objectives</span></span>

* <span data-ttu-id="44aba-109">HoloLens 프로젝트 시작</span><span class="sxs-lookup"><span data-stu-id="44aba-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="44aba-110">올바른 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="44aba-110">Enable the correct plugins</span></span>
* <span data-ttu-id="44aba-111">ARSessionConfig 데이터 자산 만들기</span><span class="sxs-lookup"><span data-stu-id="44aba-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="44aba-112">제스처 입력 설정</span><span class="sxs-lookup"><span data-stu-id="44aba-112">Set up gesture inputs</span></span>
* <span data-ttu-id="44aba-113">기본 수준 빌드</span><span class="sxs-lookup"><span data-stu-id="44aba-113">Build a basic level</span></span>
* <span data-ttu-id="44aba-114">손가락 모으기 제스처 구현</span><span class="sxs-lookup"><span data-stu-id="44aba-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="44aba-115">새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="44aba-115">Creating a new project</span></span>

<span data-ttu-id="44aba-116">가장 먼저 필요한 것은 작업할 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="44aba-117">초보 Unreal 개발자라면 Epic Launcher에서 [지원 파일을 다운로드](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="44aba-118">Unreal Engine 실행</span><span class="sxs-lookup"><span data-stu-id="44aba-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="44aba-119">**New Project Categories(새 프로젝트 범주)** 에서 **Games(게임)** 를 선택하고 **Next(다음)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Games(게임)가 강조 표시된 상태로 열려 있는 최근 프로젝트 창](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="44aba-121">**Blank(빈)** 템플릿을 선택하고 **Next(다음)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-121">Select the **Blank** template and click **Next**:</span></span>

![Blank(빈) 템플릿이 강조 표시된 Unreal 프로젝트 브라우저 창](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="44aba-123">**Project Settings(프로젝트 설정)** 에서 **C++, Scalable 3D or 2D(확장 가능한 3D 또는 2D), Mobile/Tablet(모바일/태블릿)** , **No Starter Content(시작 콘텐츠 없음)** 를 설정한 후 **Create Project(프로젝트 만들기)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="44aba-124">나중에 OpenXR 플러그 인을 사용할 수 있도록 청사진 프로젝트가 아닌 C++를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="44aba-125">이 빠른 시작에서는 Unreal Engine과 함께 제공되는 기본 OpenXR 플러그 인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="44aba-126">하지만 공식 Microsoft OpenXR 플러그 인을 다운로드하여 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="44aba-127">이렇게 하려면 프로젝트가 C++ 프로젝트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-127">That requires the project to be a C++ project.</span></span>

![프로젝트, 성능, 대상 플랫폼 및 시작 콘텐츠 선택 항목이 강조 표시된 프로젝트 설정 창](images/unreal-quickstart-img-03.png)

<span data-ttu-id="44aba-129">Unreal 편집기에서 새 프로젝트가 자동으로 열리므로, 다음 섹션에 대한 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="44aba-130">필수 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="44aba-130">Enabling required plugins</span></span>

<span data-ttu-id="44aba-131">장면에 개체를 추가하기 전에 두 플러그 인을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="44aba-132">**편집 > 플러그 인** 을 열고 기본 제공 옵션 목록에서 **증강 현실** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="44aba-133">**HoloLens** 까지 아래로 스크롤하고 **Enabled(사용)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![증강 현실 섹션이 열려 있고 HoloLens가 강조 표시된 플러그 인 창](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="44aba-135">오른쪽 상단의 검색창에 **OpenXR** 을 입력하고 **OpenXR** 및 **OpenXRMsftHandInteraction** 플러그 인을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![OpenXR이 사용하도록 설정된 플러그 인 창](images/unreal-quickstart-img-05.jpg)

![Open XR Msft Hand Interaction이 사용하도록 설정된 플러그 인 창](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="44aba-138">편집기 다시 시작</span><span class="sxs-lookup"><span data-stu-id="44aba-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="44aba-139">이 자습서에서는 OpenXR을 사용하지만 위에서 설치한 두 플러그 인은 현재 HoloLens 개발을 위한 전체 기능 집합을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="44aba-140">HandInteraction 플러그 인은 나중에 사용할 "손가락 모으기" 제스처에 충분하지만 기본 이상을 원한다면 [OpenXR 플러그 인을 다운로드](https://github.com/microsoft/Microsoft-OpenXR-Unreal)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="44aba-141">이러한 플러그 인을 사용하도록 설정하면 콘텐츠로 채우는 데 집중할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="44aba-142">수준 만들기</span><span class="sxs-lookup"><span data-stu-id="44aba-142">Creating a level</span></span>

<span data-ttu-id="44aba-143">다음 작업은 참조 및 규모에 대한 시작 지점과 큐브를 사용하여 플레이어 설정을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="44aba-144">**파일 > 새 수준** 을 선택하고 **빈 수준** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="44aba-145">이제 뷰포트의 기본 장면이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="44aba-146">**Modes(모드)** 탭에서 **Basic(기본)** 을 선택하고 장면으로 **PlayerStart** 를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="44aba-147">**Details(세부 정보)** 탭에서 **Location(위치)** 을 **X = 0, Y = 0** 및 **Z = 0** 으로 설정하고 앱이 시작될 때 사용자를 장면의 중앙에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![위치 및 플레이어 시작이 추가된 Unreal 편집기 장면](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="44aba-149">**Basic(기본)** 탭에서 **Cube(큐브)** 를 장면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="44aba-150">큐브의 **Location(위치)** 을 **X = 50, Y = 0** 및 **Z = 0** 으로 설정하여 시작 시 플레이어에서 50cm 거리에 큐브를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="44aba-151">큐브의 **Scale(눈금)** 을 **X = 0.2, Y = 0.2** 및 **Z = 0.2** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="44aba-152">장면을 테스트하기 전에 마지막으로 장면에 조명을 추가하지 않으면 큐브를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="44aba-153">**Modes(모드)** 패널에서 **Lights(조명)** 탭으로 전환하고 **Directional Light(방향성 광원)** 을 장면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="44aba-154">**PlayerStart** 위에 조명을 배치하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-154">Position the light above **PlayerStart** so you can see it</span></span>

![큐브 및 방향성 광원이 추가된 Unreal 편집기 장면](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="44aba-156">**File(파일) > Save Current(현재 저장)** 로 이동하고, 수준 이름을 **Main(기본)** 으로 지정한 후 **Save(저장)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="44aba-157">장면 집합에서 도구 모음의 **재생** 을 눌러 큐브의 작동을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="44aba-158">작업을 감상한 후 Esc를 눌러 애플리케이션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![큐브가 화면 중앙에 위치한 재생 모드의 장면](images/unreal-quickstart-img-09.png)

<span data-ttu-id="44aba-160">장면이 설정되었으므로 이제 AR에서 몇 가지 기본적인 상호 작용을 준비하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="44aba-161">먼저 AR 세션을 만들고 청사진을 추가하여 손 조작을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="44aba-162">세션 자산 추가</span><span class="sxs-lookup"><span data-stu-id="44aba-162">Adding a session asset</span></span>

<span data-ttu-id="44aba-163">Unreal의 AR 세션은 스스로 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="44aba-164">세션을 사용하려면 다음 작업을 위한 ARSessionConfig 데이터 자산이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="44aba-165">**Content Browser(콘텐츠 브라우저)** 에서 **새로 추가(Add New) > Miscellaneous(기타) > Data Asset(데이터 자산)** 을 선택하고 루트 콘텐츠 폴더 수준에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="44aba-166">**ARSessionConfig** 를 선택하고 **Select(선택)** 를 클릭한 다음, 자산의 이름을 **ARSessionConfig** 로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![AR 세션 구성 자산이 강조 표시된 상태로 열려 있는 데이터 자산 클래스 선택 창](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="44aba-168">**ARSessionConfig** 를 두 번 클릭하여 열고 모든 기본 설정을 그대로 둔 다음, **Save(저장)** 를 눌러 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![AR 세션 구성 자산 세부 정보 창](images/unreal-quickstart-img-11.png)

<span data-ttu-id="44aba-170">작업이 완료되면 다음 단계는 수준이 로드되고 종료될 때 AR 세션이 시작되고 중지되도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="44aba-171">다행히 Unreal에는 수준 전체 글로벌 이벤트 그래프 역할을 하는 **수준 청사진** 이라는 특수 청사진이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="44aba-172">수준 청사진에서 ARSessionConfig 자산을 연결하면 게임 재생이 시작될 때 AR 세션이 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="44aba-173">편집기 도구 모음에서 **Blueprints(청사진) > Open Level Blueprint(수준 청사진 열기)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![수준 청사진 옵션이 강조 표시된 상태로 열려 있는 청사진 메뉴](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="44aba-175">실행 노드(왼쪽 화살표 아이콘)를 **Event BeginPlay(이벤트 BeginPlay)** 에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="44aba-176">**Start AR Session node(AR 세션 시작 노드)** 를 검색하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="44aba-177">**Session Config(세션 구성)** 에서 **Select Asset(자산 선택)** 드롭다운을 클릭하고 **ARSessionConfig** 자산을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![이벤트 시작 재생이 AR 세션 시작 기능에 연결된 청사진 그래프](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="44aba-179">마우스 오른쪽 단추로 EventGraph의 아무 곳을 클릭하고, 새 **Event EndPlay** 노드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="44aba-180">실행 핀을 끌어 놓은 다음, **Stop AR Session(AR 세션 중지)** 노드를 검색하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="44aba-181">**Compile(컴파일)** 을 누른 다음, **Save(저장)** 하고 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44aba-182">수준이 종료될 때 AR 세션이 계속 실행 중이면 헤드셋으로 스트리밍하는 동안 앱을 다시 시작할 때 특정 기능이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![AR 세션 중지 기능에 연결된 이벤트 종료 재생 노드](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="44aba-184">입력 설정</span><span class="sxs-lookup"><span data-stu-id="44aba-184">Setting up inputs</span></span>

1. <span data-ttu-id="44aba-185">**Edit(편집) > Project Settings(프로젝트 설정)** 를 선택하고 **Engine(엔진) > Input(입력)** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="44aba-186">**Action Mappings(작업 매핑)** 옆에 있는 **+** 아이콘을 선택하고 **RightPinch** 및 **LeftPinch** 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![오른쪽 손가락 모으기 및 왼쪽 손가락 모으기 작업 매핑이 강조 표시된 바인딩 입력 설정](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="44aba-188">**RightPinch** 및 **LeftPinch** 작업을 각 **OpenXR Msft Hand Interaction** 작업에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![OpenXR Msft Hand Interaction 옵션이 강조 표시된 작업 매핑](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="44aba-190">제스처 설정</span><span class="sxs-lookup"><span data-stu-id="44aba-190">Setting up gestures</span></span>

<span data-ttu-id="44aba-191">이제 입력을 설정했으므로 흥미로운 부분으로 넘어가 보겠습니다. 바로 제스처를 추가하는 겁니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="44aba-192">오른쪽 손가락을 모아서 큐브를 돌리고 왼쪽 손가락을 모아서 애플리케이션을 종료해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="44aba-193">**Level Blueprint(수준 청사진)** 를 열고 **InputAction RightPinch** 및 **InputAction LeftPinch** 를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="44aba-194">**Cube(큐브)** 를 대상으로 사용하고 **Delta Rotation(델타 회전)** 을 **X = 0, Y = 0** 및 **Z = 20** 으로 설정하여 오른쪽 손가락 모으기 이벤트를 **AddActorLocalRotation** 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="44aba-195">이제 손가락을 모을 때마다 큐브가 20도 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="44aba-196">왼쪽 손가락 모으기 이벤트를 **Quit Game(게임 종료)** 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-196">Connect the left pinch event to **Quit Game**</span></span>

![오른쪽 및 왼쪽 손가락 모으기 이벤트에 대한 입력 작업을 사용하여 열린 수준 청사진](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="44aba-198">큐브의 **Transform(변환)** 설정에서 **Mobility(이동성)** 를 **Movable(이동 가능)** 로 설정하여 동적으로 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![이동성 속성이 강조 표시된 변환 설정](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="44aba-200">이제 애플리케이션을 배포하고 테스트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44aba-200">At this point, you're ready to deploy and test the application!</span></span>