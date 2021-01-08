---
title: MRTK 자습서 - 2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)에 대해 Unity 프로젝트를 구성하는 방법과 HoloLens 2에 배포하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859532"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="92dbd-105">2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="92dbd-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="92dbd-106">개요</span><span class="sxs-lookup"><span data-stu-id="92dbd-106">Overview</span></span>

<span data-ttu-id="92dbd-107">이 자습서에서는 새 Unity 프로젝트를 만들어서 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a> 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="92dbd-108">기본 Unity 장면을 Visual Studio에서 HoloLens 2로 구성, 빌드 및 배포하는 과정도 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="92dbd-109">HoloLens 2가 배포되면 HoloLens에서 인식한 표면을 포함하는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="92dbd-110">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="92dbd-111">목표</span><span class="sxs-lookup"><span data-stu-id="92dbd-111">Objectives</span></span>

* <span data-ttu-id="92dbd-112">HoloLens 개발을 위해 Unity를 구성하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="92dbd-113">HoloLens에 앱을 빌드하고 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="92dbd-114">HoloLens 2 디바이스에서 공간 매핑 메시, 손 메시 및 프레임 속도 카운터를 경험합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="92dbd-115">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="92dbd-115">Creating the Unity project</span></span>

1. <span data-ttu-id="92dbd-116">**Unity Hub** 를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

!["New(새로 만들기)" 단추의 아래쪽 화살표가 강조 표시된 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="92dbd-118">드롭다운 메뉴에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity 버전 선택](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="92dbd-120">Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="92dbd-121">**Create a new project(새 프로젝트 만들기)** 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="92dbd-122">**Templates(템플릿)** 가 **3D** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="92dbd-123">**Project Name(프로젝트 이름)** 상자에 프로젝트에 적합한 이름(예: "MRTK 자습서")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="92dbd-124">**Location(위치)** 옆에 3개의 점으로 된 단추를 클릭한 다음, 프로젝트를 저장할 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="92dbd-125">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="92dbd-126">따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="92dbd-127">**만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-127">Click the **Create** button.</span></span> <span data-ttu-id="92dbd-128">그러면 새 Unity 프로젝트가 만들어지고 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-128">This creates and launches your new Unity project.</span></span>

!["Create a new project(새 프로젝트 만들기)" 창이 채워진 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="92dbd-130">상태 표시줄은 진행 상황에 대한 최신 정보를 계속 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-130">The status bar keeps you updated on your progress.</span></span>

![Unity 진행률 표시줄이 "프로젝트 만들기" 상태에 대한 최신 정보를 계속 알려줍니다.](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="92dbd-132">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="92dbd-132">Switching the build platform</span></span>

1. <span data-ttu-id="92dbd-133">메뉴 모음에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity Build Settings... 메뉴 경로](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="92dbd-135">**Build Settings(빌드 설정)** 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택한 다음, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="92dbd-137">Unity가 플랫폼 전환을 완료할 때까지 기다린 다음, **Build Settings(빌드 설정)** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="92dbd-138">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="92dbd-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="92dbd-139">TextMeshPro 필수 리소스는 MRTK의 UI 요소에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="92dbd-140">프로젝트에서 MRTK의 UI 요소를 사용할 계획이 없으면 이 단계를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="92dbd-141">메뉴 모음에서 **Window(창)**  > **TextMeshPro** > **Import TMP Essential Resources(TMP 필수 리소스 가져오기)** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Unity Import TMP Essential Resources 메뉴 경로](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="92dbd-143">**Import Unity Package(Unity 패키지 가져오기)** 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Unity TMP 필수 리소스 가져오기 창](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="92dbd-145">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="92dbd-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="92dbd-146">다음 Unity 사용자 지정 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="92dbd-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="92dbd-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="92dbd-148">메뉴 모음에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="92dbd-149">**Import package(패키지 가져오기)...** 대화 상자에서 방금 다운로드한 패키지의 위치로 이동한 후 해당 패키지를 선택한 다음, **Open(열기)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="92dbd-150">**Import Unity Package(Unity 패키지 가져오기)** 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="92dbd-151">MRTK 및 프로젝트 설정 선택</span><span class="sxs-lookup"><span data-stu-id="92dbd-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="92dbd-152">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 **MRTK Project Configurator** 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="92dbd-153">그렇지 않으면 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity 프로젝트 구성 메뉴 경로](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="92dbd-155">**MRTK Project Configurator** 창에서 **Modify Configurations(구성 수정)** 섹션을 펼치고(필요한 경우), 모든 옵션이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Modify Configurations(구성 수정)이 표시된 Unity MRTK Project Configurator 창](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="92dbd-157">설정을 적용하려면 **적용** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-157">To apply the settings, click the **Apply** button.</span></span>

![MRTK의 적용 단추](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="92dbd-159">새 시스템이 이 자습서 시리즈에 [추천되는 Unity 및 MRTK 버전](mr-learning-base-01.md#prerequisites)과 완전히 호환되지 않으므로 새 XR 플러그 인 시스템 대신 Unity의 기본 제공 레거시 XR을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="92dbd-160">사용이 중단된 기본 제공 XR에 대한 경고가 표시될 경우 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="92dbd-161">MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="92dbd-162">레거시 XR 사용: VR을 프로젝트에 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="92dbd-163">단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="92dbd-164">이 항목에 대한 자세한 내용은 MRTK의 [성능](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) 설명서의 [단일 패스 인스턴스 렌더링](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92dbd-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="92dbd-165">기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="92dbd-166">Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92dbd-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="92dbd-167">메뉴 모음에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="92dbd-168">**Project Settings(프로젝트 설정)** 창에서 **Player(플레이어)** 를 선택하고 **XR Settings(XR 설정)** 드롭다운을 클릭한 다음, **Virtual Reality Supported(가상 현실 지원)** 옆에 있는 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Virtual Reality Supported(가상 현실 지원)가 표시된 Unity XR Settings(XR 설정)](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="92dbd-170">그러면 Unity가 Windows Mixed Reality SDK를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-170">This imports the Windows Mixed Reality SDK:</span></span>

![Virtual Reality SDKs(Virtual Reality SDK)가 표시된 Unity XR Settings(XR 설정)](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="92dbd-172">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 **MRTK Project Configurator** 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="92dbd-173">그렇지 않으면 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 를 선택하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="92dbd-174">**MRTK Project Configurator** 창에서 **Audio spatializer(오디오 스페이셜라이저)** 드롭다운을 클릭한 다음, **MS HRTF Spatializer** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Audio spatializer(오디오 스페이셜라이저) 옵션이 표시된 Project Settings(프로젝트 설정)](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="92dbd-176">**적용** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-176">Click the **Apply** button.</span></span> <span data-ttu-id="92dbd-177">그러면 **MRTK Project Configurator** 창이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="92dbd-178">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="92dbd-179">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="92dbd-180">이 항목에 대한 자세한 내용은 공간 오디오 자습서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92dbd-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="92dbd-181">**Project Settings(프로젝트 설정)** 창에서 **Depth Format(심도 형식)** 드롭다운을 클릭한 다음, **16-bit depth(16비트 심도)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="16-bit depth(16비트 심도)가 선택된 Unity XR Settings(Unity XR 설정)":::

    > [!TIP]
    > <span data-ttu-id="92dbd-183">Depth Format(심도 형식)을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="92dbd-184">이 항목에 대한 자세한 내용은 MRTK의 [성능](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) 설명서의 [깊이 버퍼 공유(HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92dbd-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="92dbd-185">**Publishing Settings(게시 설정)** 드롭다운을 클릭한 다음, **Package name(패키지 이름)** 상자에 적절한 이름을 입력합니다(예: "MRTK-Tutorials-Getting-Started").</span><span class="sxs-lookup"><span data-stu-id="92dbd-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Package Name(패키지 이름)이 구성된 Unity Publishing Settings(Unity 게시 설정)":::

    <span data-ttu-id="92dbd-187">**Package Name(패키지 이름) 및 Product Name(제품 이름)**</span><span class="sxs-lookup"><span data-stu-id="92dbd-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="92dbd-188">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="92dbd-189">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="92dbd-190">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="92dbd-191">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하여 맨 위에 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Product name(제품 이름)이 구성된 Unity Project Settings(Unity 프로젝트 설정)":::

9. <span data-ttu-id="92dbd-193">**Project Settings(프로젝트 설정)** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="92dbd-194">장면 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="92dbd-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="92dbd-195">메뉴 모음에서 **File(파일)**  > **New Scene(새 장면)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="92dbd-196">장면에 MRTK를 추가하려면 메뉴 모음에서 **Mixed Reality Toolkit** > **Add to Scene and Configure(장면에 추가 및 구성)...** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity Add to Scene and Configure(장면에 추가 및 구성)... 메뉴 경로":::

3. <span data-ttu-id="92dbd-198">**Hierarchy(계층 구조)** 창에서 **MixedRealityToolkit** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="MixedRealityTookit이 선택되어 있는지 확인합니다.":::

4. <span data-ttu-id="92dbd-200">**Inspector(검사기)** 창의 **MixedRealityToolkit** 섹션에서 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="DefaultMixedRealityTookitConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소":::

    > [!IMPORTANT]
    > <span data-ttu-id="92dbd-202">일반적으로는 HoloLens용으로 개발할 때 DefaultHoloLens2ConfigurationProfile을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="92dbd-203">그러나 이 자습서에서는 DefaultMixedRealityToolkitConfigurationProfile을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="92dbd-204">다음 자습서 [MRTK 프로필 구성](mr-learning-base-03.md)에서는 DefaultHoloLens2ConfigurationProfile로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="92dbd-205">메뉴 모음에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="92dbd-206">**Save Scene(장면 저장)** 대화 상자에서 프로젝트의 **Scenes(장면)** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="92dbd-207">**File name(파일 이름)** 상자에서 장면에 적절한 이름(예: "\_GettingStarted\_")을 지정한 다음, **Save(저장)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity Save Scene(장면 저장) - Save(저장) 프롬프트 창":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="92dbd-209">HoloLens 2에 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="92dbd-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="92dbd-210">디바이스에 빌드하기 전에 다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="92dbd-211">디바이스가 개발자 모드인지 여부</span><span class="sxs-lookup"><span data-stu-id="92dbd-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="92dbd-212">디바이스가 개발 컴퓨터와 페어링되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="92dbd-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="92dbd-213">그렇지 않은 경우 빌드 프로세스 중에 Visual Studio에 다음과 같은 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![디바이스 페어링을 위한 PIN 입력](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="92dbd-215">이러한 두 단계에 대해 자세히 알아보려면 [Visual Studio를 사용하여 배포 및 디버그](../../platform-capabilities-and-apis/using-visual-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92dbd-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="92dbd-216">메뉴 모음에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="92dbd-217">**Build Settings(빌드 설정)** 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

!["Scenes In Build(빌드 중인 장면)" 목록에 현재 장면 추가](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="92dbd-219">**빌드** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="빌드 단추를 클릭합니다.":::

4. <span data-ttu-id="92dbd-221">**Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드)** 대화 상자에서 빌드를 저장할 적합한 위치를 선택합니다. 예를 들어 "MRTK 자습서" 폴더에 "빌드" 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="92dbd-222">새 폴더를 만들고 적절한 이름(예: "GettingStarted")을 지정한 다음, 폴더를 선택하고 **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="빌드 폴더가 표시된 Unity Build(빌드) 창":::

    <span data-ttu-id="92dbd-224">상태 표시줄이 나타나고 빌드 진행 상황에 대한 최신 정보를 계속 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="진행 중인 Unity 빌드 프로세스":::

    > [!TIP]
    > <span data-ttu-id="92dbd-226">[HoloLens 에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="92dbd-227">빌드 프로세스가 완료되면 파일 탐색기에서 빌드를 저장한 위치로 이동한 후 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="새로 만든 Visual Studio 솔루션 파일이 선택된 Windows 탐색기":::

    > [!NOTE]
    > <span data-ttu-id="92dbd-229">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](../../install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="92dbd-230">**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스** 를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="92dbd-231">HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="HoloLens 2에 배포하도록 구성된 Visual Studio":::

    > [!NOTE]
    > <span data-ttu-id="92dbd-233">HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="92dbd-234">하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="92dbd-235">권장 해결 방법은 ARM64용으로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="92dbd-236">그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정** 으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="92dbd-237">디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="92dbd-238">이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭한 다음, **시작 프로젝트로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="92dbd-239">컴퓨터에 HoloLens를 연결하고 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="92dbd-240">Visual Studio 디버거를 연결하지 않고 앱을 빌드하고 HoloLens에 배포한 후 자동으로 시작하려면 메뉴 모음에서 **Debug(디버그)**  > **Start Without Debugging(디버깅하지 않고 시작)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio 디버깅하지 않고 시작 메뉴 경로":::

- <span data-ttu-id="92dbd-242">앱을 빌드하고 HoloLens에 배포하되, 자동으로 시작되지 않게 하려면 메뉴 모음에서 **Build(빌드) > Deploy Solution(솔루션 배포)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="92dbd-243">앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **Toggle Diagnostics** 를 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="92dbd-244">앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="92dbd-245">예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="92dbd-246">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-246">Congratulations</span></span>

<span data-ttu-id="92dbd-247">이제 첫 번째 HoloLens 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="92dbd-248">연습을 진행하는 동안 HoloLens가 인식한 표면을 덮는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="92dbd-249">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="92dbd-250">이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="92dbd-251">다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="92dbd-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92dbd-252">다음 자습서: 3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="92dbd-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
