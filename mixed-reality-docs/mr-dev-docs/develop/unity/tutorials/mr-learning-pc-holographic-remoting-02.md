---
title: PC 홀로그램 원격 자습서 - 2. 홀로그램 원격 PC 애플리케이션 만들기
description: 이 과정을 완료하여 혼합 현실 환경을 PC에서 HoloLens 2로 원격으로 수행하는 PC 애플리케이션을 만드는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 30ef793511285fe2fe52810912f6c5c06c8550dc
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353461"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="f4e01-105">2. 홀로그램 원격 PC 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="f4e01-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="f4e01-106">이 자습서에서는 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 제공하여 언제든지 홀로그램 원격을 위한 PC 앱을 만들고 HoloLens 2에 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4e01-107">목표</span><span class="sxs-lookup"><span data-stu-id="f4e01-107">Objectives</span></span>

* <span data-ttu-id="f4e01-108">홀로그램 원격에 대한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="f4e01-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="f4e01-109">Visual Studio를 사용하여 애플리케이션을 빌드하고 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="f4e01-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="f4e01-110">홀로그램 원격 애플리케이션 개발 및 HoloLens에 연결</span><span class="sxs-lookup"><span data-stu-id="f4e01-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="f4e01-111">홀로그램 원격에 대한 장면 구성</span><span class="sxs-lookup"><span data-stu-id="f4e01-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="f4e01-112">이 섹션에서는 Wi-Fi 연결을 통해 실시간으로 PC에서 HoloLens 2 디바이스로 혼합 현실 환경을 스트리밍하는 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="f4e01-113">Project 창에서 **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** 폴더로 이동하고, **HolographicRemoting** 프리팹을 클릭하여 장면으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![새로 추가한 HolographicRemoting 프리팹이 여전히 선택된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="f4e01-115">PC로 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="f4e01-115">Build your application to PC</span></span>

<span data-ttu-id="f4e01-116">이제 홀로그램 원격 앱을 PC에서 빌드할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="f4e01-117">아래 단계를 수행하고 이 애플리케이션을 PC에 빌드하려면 이러한 변경을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="f4e01-118">1. 플레이어 설정 지정</span><span class="sxs-lookup"><span data-stu-id="f4e01-118">1. Set the player settings</span></span>

<span data-ttu-id="f4e01-119">Unity 메뉴에서 편집 >프로젝트 설정을 차례로 선택하여 플레이어 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="f4e01-120">**XR 설정** 섹션에서 **WSA 홀로그램 원격 지원** 확인란을 선택하고 홀로그램 원격을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![WSA 홀로그램 원격 지원이 사용되도록 설정된 Unity XR 설정 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="f4e01-122">2. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="f4e01-122">2. Build the Unity Project</span></span>

<span data-ttu-id="f4e01-123">Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="f4e01-124">Build Settings(빌드 설정) 창에서 \* *_Add Open Scenes_* _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-124">In the Build Settings window, click the \* *_Add Open Scenes_* _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="f4e01-125">Build(빌드) 목록에서 _*_Build 단추_*_ 를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-125">In the Build list, then click the _*_Build button_*_ to open the Build Universal Windows Platform window:</span></span>

![장면이 추가된 Unity Build Settings 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="f4e01-127">빌드 유니버설 Windows 플랫폼 창에서 빌드를 저장할 적합한 위치(예: Documents\MixedRealityLearning)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="f4e01-128">새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="f4e01-129">그런 다음, _*_Select Folder(폴더 선택)_*_ 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-129">Then click the _*_Select Folder_*_ button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="f4e01-131">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-131">Wait for Unity to finish the build process.</span></span>

![진행 중인 Unity 빌드 프로세스](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="f4e01-133">3. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="f4e01-133">3. Build and deploy the application</span></span>

<span data-ttu-id="f4e01-134">빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="f4e01-135">폴더 내부를 탐색하고 .sln 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="f4e01-137">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 도구 설치 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="f4e01-138">릴리스 구성, x64 아키텍처 및 로컬 머신을 대상으로 선택하여 PC에 대해 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![로컬 컴퓨터에 대해 구성된 Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="f4e01-140">_\*_로컬 컴퓨터_\*_ 라고 표시된 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-140">Click the button that says _*_Local Machine_*_.</span></span> <span data-ttu-id="f4e01-141">애플리케이션을 빌드하고 PC에 배포하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="f4e01-142">애플리케이션은 기본적으로 PC에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="f4e01-143">홀로그램 원격 원격 애플리케이션 테스트</span><span class="sxs-lookup"><span data-stu-id="f4e01-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="f4e01-144">PC 애플리케이션을 HoloLens 2에 연결하려면 아래 프로세스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="f4e01-145">1. HoloLens 2 디바이스에 원격 플레이어 애플리케이션 설치</span><span class="sxs-lookup"><span data-stu-id="f4e01-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

<span data-ttu-id="f4e01-146">HoloLens 2에서 스토어 앱을 방문하여 " **원격 플레이어** "를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-146">_ On your HoloLens 2, visit the Store app and search for " **Remoting Player**."</span></span>
* <span data-ttu-id="f4e01-147">**원격 플레이어** 앱을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="f4e01-148">**설치** 를 탭하여 앱을 다운로드하고 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="f4e01-149">2. 원격 플레이어에 홀로그램 원격 PC 앱 연결</span><span class="sxs-lookup"><span data-stu-id="f4e01-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="f4e01-150">HoloLens에서 **원격 플레이어** 를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="f4e01-151">HoloLens **IP 주소** 를 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="f4e01-152">시작되는 즉시 **원격 플레이어** 에서 홀로그램으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="f4e01-153">홀로그램 원격 PC 애플리케이션을 PC에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="f4e01-154">애플리케이션이 시작되면 **IP 주소** 를 입력하고 **연결** 단추를 클릭하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f4e01-155">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-155">Congratulations</span></span>

<span data-ttu-id="f4e01-156">이 자습서에서는 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 제공하여 언제든지 홀로그램 원격 원격 앱을 만들고 HoloLens 2에 연결하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="f4e01-157">HoloLens가 홀로그램 원격 PC 애플리케이션에 연결되면 HoloLens 2 디바이스로 스트리밍되는 혼합 현실 환경이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4e01-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
