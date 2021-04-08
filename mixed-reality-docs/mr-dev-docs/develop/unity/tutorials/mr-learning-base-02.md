---
title: 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)에 대해 Unity 프로젝트를 구성하는 방법과 HoloLens 2에 배포하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088666"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="83878-104">2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="83878-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="83878-105">이 자습서에서는 새 Unity 프로젝트를 만들어서 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">MRTK(Mixed Reality Toolkit)</a> 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="83878-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="83878-106">기본 Unity 장면을 Visual Studio에서 HoloLens 2로 구성, 빌드 및 배포하는 과정도 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="83878-107">HoloLens 2가 배포되면 HoloLens에서 인식한 표면을 포함하는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="83878-108">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="83878-110">목표</span><span class="sxs-lookup"><span data-stu-id="83878-110">Objectives</span></span>

* <span data-ttu-id="83878-111">HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="83878-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="83878-112">HoloLens에 앱을 빌드하고 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="83878-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="83878-113">HoloLens 2 디바이스에서 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기</span><span class="sxs-lookup"><span data-stu-id="83878-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="83878-114">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="83878-114">Creating the Unity project</span></span>

<span data-ttu-id="83878-115">**Unity Hub** 를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![New 단추가 강조 표시된 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="83878-117">드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![새 버전 선택기 드롭다운이 있는 Unity Hub](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="83878-119">Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="83878-120">Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-120">In the Create a new project window:</span></span>

* <span data-ttu-id="83878-121">**Templates(템플릿)** 가 **3D** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="83878-122">적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).</span><span class="sxs-lookup"><span data-stu-id="83878-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="83878-123">프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).</span><span class="sxs-lookup"><span data-stu-id="83878-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="83878-124">**Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-124">Click the **Create** button to create and launch your new Unity project</span></span>

![새 프로젝트 만들기 창이 채워진 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="83878-126">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="83878-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="83878-127">따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="83878-128">Unity에서 프로젝트가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="83878-128">Wait for Unity to create the project:</span></span>

![진행 중인 Unity 새 프로젝트 만들기](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="83878-130">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="83878-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="83878-131">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="83878-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="83878-132">Unity 메뉴에서 **Window**(창) > **TextMeshPro** > **Import TMP Essential Resources**(TMP 필수 리소스 가져오기)를 선택하여 Import Unity Package(Unity 패키지 가져오기) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity Import TMP Essential Resources 메뉴 경로](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="83878-134">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83878-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity TMP 필수 리소스 가져오기 창](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="83878-136">TextMeshPro 필수 리소스는 MRTK의 UI 요소에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="83878-137">프로젝트에서 MRTK의 UI 요소를 사용할 계획이 없으면 이 단계를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="83878-138">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="83878-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="83878-139">Mixed Reality Toolkit을 Unity 프로젝트로 가져오려면 개발자가 Unity 프로젝트에 Mixed Reality 기능 패키지를 검색, 업데이트 및 추가할 수 있는 [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="83878-140">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="83878-141">[Microsoft 다운로드 센터](https://aka.ms/MRFeatureTool)에서 최신 버전의 Mixed Reality Feature Tool을 다운로드합니다. 다운로드가 완료되면 파일의 압축을 풀고 데스크톱에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="83878-142">Mixed Reality Feature Tool을 실행하기 전에 [.NET 5.0 런타임](https://dotnet.microsoft.com/download/dotnet/5.0)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="83878-143">Mixed Reality Feature Tool은 현재 Windows에서만 실행됩니다. MacOS의 경우 이 [절차](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages)에 따라 Mixed Reality Toolkit을 다운로드하여 Unity 프로젝트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83878-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="83878-144">다운로드한 폴더에서 실행 파일 **MixedRealityFeatureTool** 을 열어 Mixed Reality Feature Tool을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![MixedRealityFeatureTool 열기](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="83878-146">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="83878-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="83878-147">1. MRTK Project Configurator 설정 적용</span><span class="sxs-lookup"><span data-stu-id="83878-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="83878-148">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="83878-149">그렇지 않으면 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity 프로젝트 구성 메뉴 경로](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="83878-151">MRTK Project Configurator 창에서 **Modify Configurations**(구성 수정) 섹션을 펼치고, 모든 옵션이 선택되어 있는지 확인한 후 **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity MRTK Project Configurator 창](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="83878-153">MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="83878-154">단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="83878-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="83878-155">이 항목에 대한 자세한 내용은 MRTK의 [성능](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 설명서의 [단일 패스 인스턴스 렌더링](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83878-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="83878-156">기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="83878-157">Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83878-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="83878-158">2. 추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="83878-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="83878-159">장면 만들기 및 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="83878-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="83878-160">Unity 메뉴에서 **파일** > **New Scene**(새 장면)을 선택하여 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83878-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity New Scene 메뉴 경로](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="83878-162">Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure...** (장면에 추가 및 구성)를 차례로 선택하여 MRTK를 현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity Add to Scene and Configure... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="83878-164">Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity Save As... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="83878-166">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-166">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="83878-167">이 항목에 대한 자세한 정보는 MRTK의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">성능</a> 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83878-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Unity Save Scene Save 프롬프트 창](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="83878-169">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="83878-169">Importing the tutorial assets</span></span>

<span data-ttu-id="83878-170">다음 Unity 사용자 지정 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="83878-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="83878-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="83878-172">Unity 사용자 지정 패키지를 가져오려면 Unity 메뉴에서 **Assets** > **Import Package** > **Custom Package...** 를 차례로 선택하여 Import package... 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![사용자 지정 패키지 가져오기](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="83878-174">Import package... 창에서 다운로드한 **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** 를 선택하고 [열기] 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![자산 패키지 선택](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="83878-176">Import Unity Package(Unity 패키지 가져오기) 창에서 All(모두) 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, Import(가져오기) 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83878-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![가져올 모든 자산 선택](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="83878-178">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![자산을 가져온 이후의 Unity 프로젝트 창](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="83878-180">장면 구성</span><span class="sxs-lookup"><span data-stu-id="83878-180">Configuring the Scene</span></span>

<span data-ttu-id="83878-181">Project 창에서 Assets > MRTK.Tutorials.GettingStarted > Prefabs 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="83878-182">Project 창에서 **Cube** 프리팹을 클릭하고 Hierarchy 창으로 끌어다 놓은 다음, Inspector 창에서 해당 **Transform** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="83878-183">**위치**: X = 0, Y = 0, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="83878-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="83878-184">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="83878-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="83878-185">**크기 조정**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="83878-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![장면에 큐브 추가](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="83878-187">장면의 개체에 초점을 맞추기 위해 **Cube** 개체를 두 번 클릭한 다음, 약간씩 다시 확대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="83878-188">추적된 손으로 개체를 상호 작용하고 잡으려면 개체에 **Box Collider**, **Object Manipulator(Script)** 구성 요소 및 **NearInteractionGrabbable(Script)** 구성 요소와 같은 Collider 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="83878-189">Hierarchy 창에서 **Cube** 를 선택한 상태로 Inspector 창에서 **Add Component** 단추를 클릭한 다음, **Object Manipulator** 스크립트를 검색하고 선택하여 Object Manipulator 스크립트를 큐브 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![큐브에 Object Manipulator 추가](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="83878-191">동일한 작업을 반복하여 **Near Interaction Grabbable 스크립트** 를 큐브에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![큐브에 Near Interaction Grabable 추가](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="83878-193">이 경우 Object Manipulator(Script)를 추가하면 Object Manipulator(Script)가 종속되어 있으므로 Constraint Manager(Script)가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="83878-194">이 자습서의 학습 목표를 달성하기 위해 이미 Cube Object에 충돌체가 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="83878-195">충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83878-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="83878-196">Unity 편집기에서 이 테스트를 수행하려면 재생 모드로 들어가서 **LeftShift** 또는 **Space** 키를 누르고 있으면 컨트롤러를 마우스로 이동시킬 수 있으며 마우스 휠로 컨트롤러를 더 멀리 또는 더 가까이 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="83878-197">포인터가 Cube에 있으면 **마우스 오른쪽 단추** 를 누른 상태로 Cube 개체를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![게임 모드](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="83878-199">HoloLens 2에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="83878-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="83878-200">1. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="83878-200">1. Build the Unity project</span></span>

<span data-ttu-id="83878-201">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="83878-202">Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="83878-204">Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="83878-206">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="83878-206">Wait for Unity to finish the build process:</span></span>

![진행 중인 Unity 빌드 프로세스](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="83878-208">2. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="83878-208">2. Build and deploy the application</span></span>

<span data-ttu-id="83878-209">빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="83878-210">폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83878-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="83878-212">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](../../install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="83878-213">**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스** 를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![HoloLens 2에 배포하도록 구성된 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="83878-215">HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="83878-216">HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="83878-217">하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="83878-218">권장 해결 방법은 ARM64용으로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83878-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="83878-219">그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정** 으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="83878-220">디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="83878-221">이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="83878-222">HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작** 을 선택하여 빌드하고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio Start Without Debugging 메뉴 경로](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="83878-224">디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="83878-225">이 두 단계는 모두 [이러한 지침](../../platform-capabilities-and-apis/using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="83878-226">[HoloLens 에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="83878-227">디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="83878-228">**빌드 > 솔루션 배포** 를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="83878-229">앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **Toggle Diagnostics** 를 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="83878-230">앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="83878-231">예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="83878-232">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-232">Congratulations</span></span>

<span data-ttu-id="83878-233">이제 첫 번째 HoloLens 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="83878-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="83878-234">앱이 열리면 Cube 개체가 앞에 표시되어야 하며 큐브를 이동함으로써 상호 작용할 수 있어야 하며, 연습을 진행할 때 HoloLens가 인식하는 표면을 덮는 공간 매핑 메시가 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83878-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="83878-235">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83878-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="83878-236">이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="83878-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="83878-237">다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="83878-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83878-238">다음 자습서: 3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="83878-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)