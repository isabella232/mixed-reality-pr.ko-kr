---
title: Azure Speech Services 자습서 - 1. 음성 인식 및 전사 통합 및 사용
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, 음성 인식, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656634"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="dfb2e-105">1. 음성 인식 및 전사 통합 및 사용</span><span class="sxs-lookup"><span data-stu-id="dfb2e-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="dfb2e-106">개요</span><span class="sxs-lookup"><span data-stu-id="dfb2e-106">Overview</span></span>

<span data-ttu-id="dfb2e-107">이 자습서 시리즈에서는 HoloLens 2에서 Azure Speech Services의 사용을 검색하는 Mixed Reality 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="dfb2e-108">이 자습서 시리즈를 완료하면 디바이스의 마이크를 사용하여 음성을 텍스트로 실시간으로 전사하고, 음성을 다른 언어로 번역하고, 의도 인식 기능을 활용하여 AI를 통해 음성 명령을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="dfb2e-109">목표</span><span class="sxs-lookup"><span data-stu-id="dfb2e-109">Objectives</span></span>

* <span data-ttu-id="dfb2e-110">Azure Speech Services를 HoloLens 2 애플리케이션과 통합하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="dfb2e-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="dfb2e-111">음성 인식을 사용하여 텍스트를 전사하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="dfb2e-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dfb2e-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="dfb2e-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="dfb2e-113">[시작 자습서](mr-learning-base-01.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="dfb2e-114">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="dfb2e-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="dfb2e-115">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="dfb2e-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="dfb2e-116">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="dfb2e-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="dfb2e-117">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="dfb2e-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="dfb2e-118">Unity 2020/2019 LTS가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="dfb2e-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="dfb2e-119">이 자습서 시리즈는 Open XR 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)와 레거시 WSA 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="dfb2e-120">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="dfb2e-121">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="dfb2e-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="dfb2e-122">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="dfb2e-123">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="dfb2e-124">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="dfb2e-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="dfb2e-125">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="dfb2e-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="dfb2e-126">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="dfb2e-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="dfb2e-127">Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="dfb2e-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="dfb2e-128">[장면 만들기 및 구성](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름(예: *AzureSpeechServices*) 지정</span><span class="sxs-lookup"><span data-stu-id="dfb2e-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="dfb2e-129">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필이 **DefaultHoloLens2ConfigurationProfile** 인지 확인하고, 공간 인식 메시의 표시 옵션을 **Occlusion(폐색)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="dfb2e-130">음성 명령 시작 동작 구성</span><span class="sxs-lookup"><span data-stu-id="dfb2e-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="dfb2e-131">음성 인식 및 전사에 음성 SDK를 사용하므로 음성 SDK 기능을 방해하지 않도록 MRTK 음성 명령을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="dfb2e-132">이를 위해 음성 명령 시작 동작을 [자동 시작]에서 [수동 시작]으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="dfb2e-133">[계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 채 [검사기] 창에서 **입력** 탭을 선택하고, **DefaultHoloLens2InputSystemProfile** 및 **DefaultMixedRealitySpeechCommandsProfile** 을 복제한 다음, 음성 명령 **시작 동작** 을 **수동 시작** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="dfb2e-135">기능 구성</span><span class="sxs-lookup"><span data-stu-id="dfb2e-135">Configuring the capabilities</span></span>

<span data-ttu-id="dfb2e-136">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="dfb2e-138">**게시 설정** 에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="dfb2e-139">그런 다음, **InternetClientServer** 및 **PrivateNetworkClientServer** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="dfb2e-141">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="dfb2e-141">Importing the tutorial assets</span></span>

<span data-ttu-id="dfb2e-142">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="dfb2e-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)(최신 버전)</span><span class="sxs-lookup"><span data-stu-id="dfb2e-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="dfb2e-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="dfb2e-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="dfb2e-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="dfb2e-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="dfb2e-146">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mr-learning-base-04.md#importing-the-tutorial-assets) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="dfb2e-147">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="dfb2e-149">ARM64용 Azure Speech 플러그 인을 게시하도록 Unity 프로젝트를 설정해야 합니다. 프로젝트 창에서 이 작업을 수행하려면 **자산** > **SpeechSDK** > **플러그 인** > **WSA** > **ARM64** 로 이동하고 **Microsoft.CognitiveServices.Speech.core** 플러그 인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="dfb2e-151">**Microsoft.CognitiveServices.Speech.core** 플러그 인이 선택된 상태에서 검사기 창에서 **WSA Player** 를 사용하도록 설정한 다음 **플랫폼 설정** 에서 SDK에 대해 **UWP** 를, CPU에 대해 **ARM64** 를 선택하고 적용을 클릭하여 이 설정을 플러그 인에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="dfb2e-153">나머지 각 플러그 인에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="dfb2e-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="dfb2e-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="dfb2e-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="dfb2e-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="dfb2e-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="dfb2e-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="dfb2e-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="dfb2e-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="dfb2e-158">장면 준비</span><span class="sxs-lookup"><span data-stu-id="dfb2e-158">Preparing the scene</span></span>

<span data-ttu-id="dfb2e-159">이 섹션에서는 자습서 프리팹을 추가하여 장면을 준비하고, 장면을 제어하는 Lunarcom 컨트롤러(스크립트) 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="dfb2e-160">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** 폴더로 차례로 이동하고, **Lunarcom** 프리팹을 [계층 구조] 창으로 끌어 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="dfb2e-162">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 채로 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 컨트롤러(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="dfb2e-164">Lunarcom 컨트롤러(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="dfb2e-165">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="dfb2e-166">**Lunarcom** 개체를 선택한 상태에서 이 개체를 펼쳐 자식 개체를 표시한 다음, **Terminal** 개체를 Lunarcom 컨트롤러(스크립트) 구성 요소의 **터미널** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="dfb2e-168">**Lunarcom** 개체를 선택한 상태에서 Terminal 개체를 펼쳐 자식 개체를 표시한 다음, **ConnectionLight** 개체 및 **OutputText** 개체를 각각 Lunarcom 컨트롤러(스크립트) 구성 요소의 **연결 조명** 필드 및 **출력 텍스트** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="dfb2e-170">**Lunarcom** 개체를 선택한 상태에서 Buttons 개체를 펼쳐 자식 개체를 표시한 다음, [검사기] 창에서 **단추** 목록을 펼치고, **크기** 를 3으로 설정하고, **MicButton**, **SatelliteButton** 및 **RocketButton** 필드를 각각 **요소** 0, 1 및 2 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="dfb2e-172">Unity 프로젝트를 Azure 리소스에 연결</span><span class="sxs-lookup"><span data-stu-id="dfb2e-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="dfb2e-173">Azure Speech Services를 사용하려면 Azure 리소스를 만들고, Speech Service에 대한 API 키를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="dfb2e-174">[Speech Service 체험해 보기](/azure/cognitive-services/speech-service/get-started) 지침을 수행하고, 서비스 지역(위치라고도 함) 및 API 키(Key1 또는 Key2라고도 함)를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="dfb2e-175">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **Lunarcom 컨트롤러(스크립트)** 구성 요소의 **Speech SDK 자격 증명** 섹션을 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="dfb2e-176">**Speech Service API 키** 필드에서 API 키(Key1 또는 Key2)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="dfb2e-177">**Speech Service 지역** 필드에서 공백 없이 소문자를 사용하여 서비스 지역(위치)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="dfb2e-179">음성 인식을 사용하여 음성 전사</span><span class="sxs-lookup"><span data-stu-id="dfb2e-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="dfb2e-180">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 음성 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="dfb2e-182">Lunarcom 음성 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="dfb2e-183">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="dfb2e-184">이제 게임 모드로 들어가면 먼저 마이크 단추를 눌러 음성 인식을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="dfb2e-186">그런 다음, 마이크가 컴퓨터에 있다고 가정하여 사용자가 무언가를 말하면 음성이 터미널 패널에 전사됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="dfb2e-188">애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="dfb2e-189">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-189">Congratulations</span></span>

<span data-ttu-id="dfb2e-190">Azure에서 구동하는 음성 인식을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="dfb2e-191">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="dfb2e-192">다음 자습서에서는 Azure 음성 인식을 사용하여 명령을 실행하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2e-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dfb2e-193">다음 자습서: 2. Azure 음성 인식을 사용하여 명령 실행</span><span class="sxs-lookup"><span data-stu-id="dfb2e-193">Next tutorial: 2. Execute commands using Azure speech recognition</span></span>](mrlearning-speechSDK-ch2.md)
