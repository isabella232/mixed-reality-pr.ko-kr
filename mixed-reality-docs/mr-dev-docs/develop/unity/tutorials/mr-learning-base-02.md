---
title: 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)에 대해 Unity 프로젝트를 구성하는 방법과 HoloLens 2에 배포하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176025"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="20102-104">2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="20102-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="20102-105">이 자습서에서는 새 Unity 프로젝트를 만들어서 MRTK(Mixed Reality Toolkit) 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="20102-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="20102-106">기본 Unity 장면을 Visual Studio에서 HoloLens 2로 구성, 빌드 및 배포하는 과정도 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="20102-107">HoloLens 2가 배포되면 HoloLens에서 인식한 표면을 포함하는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="20102-108">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="20102-109">목표</span><span class="sxs-lookup"><span data-stu-id="20102-109">Objectives</span></span>

* <span data-ttu-id="20102-110">HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="20102-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="20102-111">HoloLens에 앱을 빌드하고 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="20102-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="20102-112">HoloLens 2 디바이스에서 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기</span><span class="sxs-lookup"><span data-stu-id="20102-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="20102-113">단계 개요</span><span class="sxs-lookup"><span data-stu-id="20102-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="20102-114">![개요 1단계](images/mr-learning-base/base-02-overview-step1.png) **1. 새 Unity 프로젝트 만들기**</span><span class="sxs-lookup"><span data-stu-id="20102-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20102-115">![개요 2단계](images/mr-learning-base/base-02-overview-step2.png) **2. 프로젝트로 MRTK 가져오기**</span><span class="sxs-lookup"><span data-stu-id="20102-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20102-116">![개요 3단계](images/mr-learning-base/base-02-overview-step3.png) **3. MRTK로 새 장면 구성**</span><span class="sxs-lookup"><span data-stu-id="20102-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="20102-117">![개요 4단계](images/mr-learning-base/base-02-overview-step4.png) **4. Unity 프로젝트 빌드**</span><span class="sxs-lookup"><span data-stu-id="20102-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20102-118">![개요 5단계](images/mr-learning-base/base-02-overview-step5.png) **5. UWP 프로젝트 빌드**</span><span class="sxs-lookup"><span data-stu-id="20102-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="20102-119">![개요 6단계](images/mr-learning-base/base-02-overview-step6.png) **6. 디바이스에서 프로젝트 실행**</span><span class="sxs-lookup"><span data-stu-id="20102-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="20102-120">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="20102-120">Creating the Unity project</span></span>

<span data-ttu-id="20102-121">**Unity Hub** 를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="20102-122">드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="20102-123">Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="20102-124">Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-124">In the Create a new project window:</span></span>

* <span data-ttu-id="20102-125">**Templates(템플릿)** 가 **3D** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="20102-126">적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).</span><span class="sxs-lookup"><span data-stu-id="20102-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="20102-127">프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).</span><span class="sxs-lookup"><span data-stu-id="20102-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="20102-128">**Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="20102-129">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="20102-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="20102-130">따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="20102-131">Unity에서 프로젝트가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="20102-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="20102-132">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="20102-132">Switching the build platform</span></span>

<span data-ttu-id="20102-133">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="20102-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="20102-135">Build Settings(빌드 설정) 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고</span><span class="sxs-lookup"><span data-stu-id="20102-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="20102-136">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="20102-137">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="20102-138">**Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="20102-139">**Target SDK Version(대상 SDK 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="20102-140">**최소 플랫폼 버전** 을 **10.0.1024.0** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="20102-141">**Target Studio Version(대상 Studio 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="20102-142">**Build and Run on(빌드 및 실행)** 을 **USB Device(USB 디바이스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="20102-143">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="20102-144">Switch Platform(플랫폼 전환) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-144">Click the Switch Platform button</span></span>

![유니버설 Windows 플랫폼 설정이 지정된 Unity 빌드 설정](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="20102-146">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="20102-146">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="20102-148">Unity에서 플랫폼 전환을 완료하면 **x** 아이콘을 클릭하여 빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="20102-149">Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="20102-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="20102-150">Mixed Reality Toolkit을 Unity 프로젝트로 가져오려면 개발자가 Unity 프로젝트에 Mixed Reality 기능 패키지를 검색, 업데이트 및 추가할 수 있는 [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="20102-151">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="20102-152">[Microsoft 다운로드 센터](https://aka.ms/MRFeatureTool)에서 최신 버전의 Mixed Reality Feature Tool을 다운로드합니다. 다운로드가 완료되면 파일의 압축을 풀고 데스크톱에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="20102-153">Mixed Reality Feature Tool을 실행하기 전에 [.NET 5.0 런타임](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="20102-154">다운로드한 폴더에서 실행 파일 **MixedRealityFeatureTool** 을 열어 Mixed Reality Feature Tool을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="20102-155">장면 만들기 및 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="20102-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="20102-156">Unity 메뉴에서 **파일** > **새 장면** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity New Scene 메뉴 경로](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="20102-158">**새 장면** 창에서 **기본(기본 제공)** 을 선택하고 **만들기** 를 클릭하여 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20102-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Unity 새 장면 창](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="20102-160">위 스크린샷은 Unity 버전 2020에서 가져온 것입니다. Unity 2019를 사용하는 경우 **만들기** 를 클릭하면 새로운 빈 장면이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="20102-161">Unity 메뉴에서 **Mixed Reality** > **Toolkit** >  **장면에 추가 및 구성...** 을 차례로 선택하여 MRTK를 현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity Add to Scene and Configure... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="20102-163">계층 구조 창에 **MixedRealityToolkit** 개체가 아직 선택된 상태로 검사기 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![DefaultMixedRealityTookitConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="20102-165">Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="20102-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity Save As... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="20102-167">**자산** > **장면** 에서 프로젝트의 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Unity Save Scene Save 프롬프트 창](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="20102-169">개체에 손 상호 작용 추가</span><span class="sxs-lookup"><span data-stu-id="20102-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="20102-170">Unity 메뉴에서 **GameObject** > **3D 개체** > **큐브** 를 선택하여 장면에 큐브 개체를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![장면에 큐브 추가](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="20102-172">계층 구조 창에서 **큐브** 개체를 클릭한 다음 검사기 창에서 다음과 같이 **변환** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="20102-173">**위치**: X = 0, Y = 0.1, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="20102-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="20102-174">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="20102-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="20102-175">**배율**: X = 0.1, Y = 0.1, Z = 0.1</span><span class="sxs-lookup"><span data-stu-id="20102-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="20102-176">1 Unity 단위는 1미터입니다.</span><span class="sxs-lookup"><span data-stu-id="20102-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="20102-177">큐브의 크기를 헤드셋 위치(0,0,0)에서 50cm에,</span><span class="sxs-lookup"><span data-stu-id="20102-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="20102-178">편안한 상호 작용을 위해 눈높이 10cm 아래에 배치하여 10x10x10cm로 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="20102-179">기본 배율(1,1,1)을 사용하면 큐브가 너무 커집니다.</span><span class="sxs-lookup"><span data-stu-id="20102-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="20102-180">기본 위치(0,0,0)를 사용하면 큐브가 헤드셋과 같은 위치에 배치되고 뒤로 이동할 때까지 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![변환 정보 조정](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="20102-182">장면의 개체에 초점을 맞추기 위해 **Cube** 개체를 두 번 클릭한 다음, 약간씩 다시 확대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="20102-183">또는 F 키를 사용하여 개체를 확대/축소하고 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="20102-184">추적된 손으로 개체를 상호 작용하고 잡으려면 개체에 다음이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="20102-185">**상자 충돌체** 와 같은 충돌체 구성 요소(Unity의 큐브에는 기본적으로 상자 충돌체가 이미 있음)</span><span class="sxs-lookup"><span data-stu-id="20102-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="20102-186">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="20102-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="20102-187">**NearInteractionGrabbable(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="20102-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="20102-188">MRTK의 **ObjectManipulator** 스크립트를 사용하면 한 손 또는 양손을 사용하여 개체를 이동, 크기 조정, 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="20102-189">사용자가 손으로 홀로그램을 직접 터치할 수 있으므로 이 스크립트는 직접 조작 입력 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="20102-190">Hierarchy 창에서 **Cube** 를 선택한 상태로 Inspector 창에서 **Add Component** 단추를 클릭한 다음, **Object Manipulator** 스크립트를 검색하고 선택하여 Object Manipulator 스크립트를 큐브 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![큐브에 Object Manipulator 추가](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="20102-192">동일한 작업을 반복하여 **Near Interaction Grabbable 스크립트** 를 큐브에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![큐브에 Near Interaction Grabable 추가](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="20102-194">이 경우 Object Manipulator(Script)를 추가하면 Object Manipulator(Script)가 종속되어 있으므로 Constraint Manager(Script)가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="20102-195">MRTK 입력 시뮬레이션을 사용하여 Unity 편집기에서 애플리케이션 테스트</span><span class="sxs-lookup"><span data-stu-id="20102-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="20102-196">MRTK의 입력 시뮬레이션을 사용하면 디바이스를 빌드하고 배포하지 않고도 Unity 편집기에서 다양한 유형의 상호 작용을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="20102-197">이를 통해 설계 및 개발 프로세스에서 아이디어를 빠르게 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="20102-198">키보드와 마우스 조합을 사용하여 시뮬레이션된 입력을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="20102-199">재생 단추를 클릭하여 재생 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="20102-200">**왼쪽 Shift** 또는 **스페이스바** 키를 눌러 컨트롤러(시뮬레이션된 손)를 불러 오면 마우스 움직임으로 컨트롤러가 이동하고 마우스 휠을 사용하여 카메라에 더 가깝게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="20102-201">포인터가 Cube에 있으면 **마우스 왼쪽 단추** 를 누른 상태로 Cube 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20102-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="20102-202">**W, A, S, D, Q, E** 키를 눌러 카메라를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="20102-203">**마우스 오른쪽 단추** 를 누른 채 마우스를 움직여 주위를 둘러봅니다.</span><span class="sxs-lookup"><span data-stu-id="20102-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="20102-204">시뮬레이션된 손을 들어 가져오려면 **스페이스 바(오른손)** 또는 **왼쪽 Shift 키(왼손)** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="20102-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="20102-205">시뮬레이션된 손을 뷰에 유지하려면 **T** 또는 **Y** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="20102-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="20102-206">시뮬레이션된 손을 회전하려면 **Ctrl** 키를 누른 상태에서 마우스를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![게임 모드](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="20102-208">HoloLens 2에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="20102-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="20102-209">1. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="20102-209">1. Build the Unity project</span></span>

<span data-ttu-id="20102-210">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="20102-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="20102-211">Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="20102-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="20102-213">Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="20102-215">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="20102-215">Wait for Unity to finish the build process:</span></span>

![진행 중인 Unity 빌드 프로세스](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="20102-217">2. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="20102-217">2. Build and deploy the application</span></span>

<span data-ttu-id="20102-218">빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="20102-219">폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="20102-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="20102-221">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](../../install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="20102-222">**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스** 를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![HoloLens 2에 배포하도록 구성된 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="20102-224">HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="20102-225">HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="20102-226">하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="20102-227">권장 해결 방법은 ARM64용으로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="20102-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="20102-228">그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정** 으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="20102-229">디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="20102-230">이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="20102-231">HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작** 을 선택하여 빌드하고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio Start Without Debugging 메뉴 경로](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="20102-233">디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="20102-234">이 두 단계는 모두 [이러한 지침](../../platform-capabilities-and-apis/using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="20102-235">[HoloLens 에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="20102-236">디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="20102-237">**빌드 > 솔루션 배포** 를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="20102-238">앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **"Toggle Diagnostics"** 를 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="20102-239">앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="20102-240">예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="20102-241">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-241">Congratulations</span></span>

<span data-ttu-id="20102-242">이제 첫 번째 HoloLens 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="20102-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="20102-243">앱이 열리면 Cube 개체가 앞에 표시되어야 하며 큐브를 이동함으로써 상호 작용할 수 있어야 하며, 연습을 진행할 때 HoloLens가 인식하는 표면을 덮는 공간 매핑 메시가 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20102-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="20102-244">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20102-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="20102-245">이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="20102-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="20102-246">다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="20102-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20102-247">다음 자습서: 3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="20102-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
