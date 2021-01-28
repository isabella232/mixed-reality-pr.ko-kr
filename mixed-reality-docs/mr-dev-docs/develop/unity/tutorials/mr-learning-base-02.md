---
title: 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)에 대해 Unity 프로젝트를 구성하는 방법과 HoloLens 2에 배포하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4d82d0974a0a797e7f8d2de2d4943666f7d32a4f
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635518"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="fb974-104">2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="fb974-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="fb974-105">이 자습서에서는 새 Unity 프로젝트를 만들어서 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a> 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="fb974-106">기본 Unity 장면을 Visual Studio에서 HoloLens 2로 구성, 빌드 및 배포하는 과정도 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="fb974-107">HoloLens 2가 배포되면 HoloLens에서 인식한 표면을 포함하는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="fb974-108">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="fb974-109">목표</span><span class="sxs-lookup"><span data-stu-id="fb974-109">Objectives</span></span>

* <span data-ttu-id="fb974-110">HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="fb974-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="fb974-111">HoloLens에 앱을 빌드하고 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="fb974-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="fb974-112">HoloLens 2 디바이스에서 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기</span><span class="sxs-lookup"><span data-stu-id="fb974-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="fb974-113">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="fb974-113">Creating the Unity project</span></span>

<span data-ttu-id="fb974-114">**Unity Hub** 를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![New 단추가 강조 표시된 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="fb974-116">드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![새 버전 선택기 드롭다운이 있는 Unity Hub](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="fb974-118">Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="fb974-119">Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-119">In the Create a new project window:</span></span>

* <span data-ttu-id="fb974-120">**Templates(템플릿)** 가 **3D** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="fb974-121">적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).</span><span class="sxs-lookup"><span data-stu-id="fb974-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="fb974-122">프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).</span><span class="sxs-lookup"><span data-stu-id="fb974-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="fb974-123">**Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-123">Click the **Create** button to create and launch your new Unity project</span></span>

![새 프로젝트 만들기 창이 채워진 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="fb974-125">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="fb974-126">따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="fb974-127">Unity에서 프로젝트가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-127">Wait for Unity to create the project:</span></span>

![진행 중인 Unity 새 프로젝트 만들기](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="fb974-129">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="fb974-129">Switching the build platform</span></span>

<span data-ttu-id="fb974-130">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="fb974-132">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="fb974-134">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-134">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="fb974-136">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![닫기 아이콘이 강조 표시된 Unity 빌드 창](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="fb974-138">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="fb974-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="fb974-139">Unity 메뉴에서 **Window**(창) > **TextMeshPro** > **Import TMP Essential Resources**(TMP 필수 리소스 가져오기)를 선택하여 Import Unity Package(Unity 패키지 가져오기) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity Import TMP Essential Resources 메뉴 경로](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="fb974-141">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity TMP 필수 리소스 가져오기 창](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="fb974-143">TextMeshPro 필수 리소스는 MRTK의 UI 요소에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="fb974-144">프로젝트에서 MRTK의 UI 요소를 사용할 계획이 없으면 이 단계를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="fb974-145">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="fb974-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="fb974-146">다음 Unity 사용자 지정 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="fb974-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fb974-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="fb974-148">Unity 메뉴에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 차례로 선택하여 Import package(패키지 가져오기)... 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Unity 사용자 지정 패키지 가져오기... 메뉴 경로](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="fb974-150">Import package(패키지 가져오기)... 창에서 다운로드한 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** 를 선택하고 **Open(열기)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![Unity 열기 프롬프트 창을 사용하여 사용자 지정 패키지 가져오기](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="fb974-152">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity MRTK Foundation 가져오기 창](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="fb974-154">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="fb974-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="fb974-155">1. MRTK Project Configurator 설정 적용</span><span class="sxs-lookup"><span data-stu-id="fb974-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="fb974-156">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="fb974-157">그렇지 않으면 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-157">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity 프로젝트 구성 메뉴 경로](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="fb974-159">MRTK Project Configurator 창에서 **Modify Configurations**(구성 수정) 섹션을 펼치고, 모든 옵션이 선택되어 있는지 확인한 후 **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity MRTK Project Configurator 창](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="fb974-161">MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="fb974-162">단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-162">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="fb974-163">이 항목에 대한 자세한 내용은 MRTK의 [성능](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) 설명서의 [단일 패스 인스턴스 렌더링](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb974-163">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="fb974-164">기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-164">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="fb974-165">Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb974-165">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="fb974-166">2. 추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="fb974-166">2. Configure additional project settings</span></span>

<span data-ttu-id="fb974-167">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity Project Settings... 메뉴 경로](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="fb974-169">프로젝트 설정 창에서 **XR Plug-in Management** > **Install XR Plug-in Management(XR Plug-in Management 설치)** 를 선택하여 XR Plug-in Management를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-169">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![패키지 이름이 구성된 Unity 게시 설정](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="fb974-171">Unity에서 XR Plug-in Management 설치를 완료한 후</span><span class="sxs-lookup"><span data-stu-id="fb974-171">after Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="fb974-172">유니버설 Windows 플랫폼 설정에 있는지 확인하고 시작 시 XR 초기화를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-172">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Unity XR 플러그 인 관리 구성](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="fb974-174">프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택하고 **+** 아이콘을 클릭한 후 Windows Mixed Reality를 선택하여 Windows Mixed Reality SDK를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-174">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Windows Mixed Reality SDK 추가가 선택된 Unity XR 설정](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="fb974-176">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-176">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="fb974-177">그렇지 않으면 Unity 메뉴를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-177">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="fb974-178">MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-178">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Windows Mixed Reality SDK 추가가 선택된 Unity XR 설정](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="fb974-180">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-180">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="fb974-181">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-181">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="fb974-182">이 항목에 대한 자세한 정보는 <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb974-182">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="fb974-183">프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-183">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 16 깊이 사용](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="fb974-185">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-185">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="fb974-186">이 항목에 대한 자세한 정보는 MRTK의 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">성능</a> 설명서의 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb974-186">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="fb974-187">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-187">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![패키지 이름이 구성된 Unity 게시 설정](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="fb974-189">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-189">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="fb974-190">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-190">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="fb974-191">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-191">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="fb974-192">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-192">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="fb974-193">장면 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="fb974-193">Creating and configuring the scene</span></span>

<span data-ttu-id="fb974-194">Unity 메뉴에서 **파일** > **New Scene**(새 장면)을 선택하여 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-194">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity New Scene 메뉴 경로](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="fb974-196">Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure...** (장면에 추가 및 구성)를 차례로 선택하여 MRTK를 현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-196">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity Add to Scene and Configure... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="fb974-198">계층 구조 창에 **MixedRealityToolkit** 개체가 아직 선택된 상태로 검사기 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-198">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![DefaultMixedRealityTookitConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="fb974-200">Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity Save As... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="fb974-202">Save Scene 창에서 프로젝트의 **Scenes(장면)** 폴더로 이동하여 장면에 적합한 이름(예: _시작_)을 지정하고, **Save(저장)** 단추를 클릭하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Unity Save Scene Save 프롬프트 창](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="fb974-204">HoloLens 2에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="fb974-204">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="fb974-205">1. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="fb974-205">1. Build the Unity project</span></span>

<span data-ttu-id="fb974-206">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="fb974-207">Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="fb974-209">Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="fb974-211">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-211">Wait for Unity to finish the build process:</span></span>

![진행 중인 Unity 빌드 프로세스](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="fb974-213">2. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="fb974-213">2. Build and deploy the application</span></span>

<span data-ttu-id="fb974-214">빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-214">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="fb974-215">폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fb974-217">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](../../install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-217">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="fb974-218">**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스** 를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-218">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![HoloLens 2에 배포하도록 구성된 Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="fb974-220">HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-220">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="fb974-221">HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-221">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="fb974-222">하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-222">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="fb974-223">권장 해결 방법은 ARM64용으로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-223">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="fb974-224">그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정** 으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-224">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="fb974-225">디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-225">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="fb974-226">이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-226">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="fb974-227">HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작** 을 선택하여 빌드하고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-227">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio Start Without Debugging 메뉴 경로](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="fb974-229">디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-229">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="fb974-230">이 두 단계는 모두 [이러한 지침](../../platform-capabilities-and-apis/using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-230">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="fb974-231">[HoloLens 에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-231">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="fb974-232">디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-232">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="fb974-233">**빌드 > 솔루션 배포** 를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-233">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="fb974-234">앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **Toggle Diagnostics** 를 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-234">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="fb974-235">앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-235">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="fb974-236">예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-236">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="fb974-237">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-237">Congratulations</span></span>

<span data-ttu-id="fb974-238">이제 첫 번째 HoloLens 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-238">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="fb974-239">연습을 진행하는 동안 HoloLens가 인식한 표면을 덮는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-239">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="fb974-240">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-240">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="fb974-241">이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-241">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="fb974-242">다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="fb974-242">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb974-243">다음 자습서: 3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="fb974-243">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)