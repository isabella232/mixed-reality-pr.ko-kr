---
title: 공간 오디오 자습서 - 1. 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가하여 HoloLens 2 HRTF 하드웨어 오프로드에 액세스합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175368"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="edf7d-105">1. Unity 프로젝트에 공간 오디오 추가</span><span class="sxs-lookup"><span data-stu-id="edf7d-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="edf7d-106">개요</span><span class="sxs-lookup"><span data-stu-id="edf7d-106">Overview</span></span>

<span data-ttu-id="edf7d-107">HoloLens2의 Unity에 대한 공간 오디오 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="edf7d-108">이 자습서 시리즈를 통해 HoloLens 2 HRTF(헤드 관련 전송 함수) 오프로드를 사용하는 방법과 HRTF 오프로드를 사용할 때 반향을 사용하도록 설정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="edf7d-109">[Microsoft Spatializer GitHub 리포지토리에는](https://github.com/microsoft/spatialaudio-unity) 이 자습서 시퀀스의 완료된 Unity 프로젝트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="edf7d-110">HRTF 기반 공간화 기술을 사용하여 소리를 공간화하는 것의 의미와 도움이 될 수 있는 경우에 대한 권장 사항을 이해하려면 [공간 음향 디자인을](/windows/mixed-reality/spatial-sound-design)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="edf7d-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="edf7d-111">HRTF 오프로드란?</span><span class="sxs-lookup"><span data-stu-id="edf7d-111">What is HRTF offload?</span></span>

<span data-ttu-id="edf7d-112">HRTF 기반 알고리즘을 사용하여 오디오를 처리하려면 많은 양의 특수 계산이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="edf7d-113">HoloLens 2 애플리케이션 프로세서의 부담을 피하기 위해 활용할 수 있는 전용 하드웨어를 포함하므로 HRTF 기반 알고리즘의 처리를 "오프로드"합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="edf7d-114">Microsoft spatializer 플러그 인은 애플리케이션이 전용 HRTF 하드웨어를 활용할 수 있는 쉬운 방법을 제공하므로 애플리케이션이 공간 오디오 이외의 작업에 더 많은 애플리케이션 프로세서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="edf7d-115">목표</span><span class="sxs-lookup"><span data-stu-id="edf7d-115">Objectives</span></span>

* <span data-ttu-id="edf7d-116">Microsoft spatializer 플러그 인 가져오기 및 사용</span><span class="sxs-lookup"><span data-stu-id="edf7d-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="edf7d-117">개발자 워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="edf7d-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edf7d-118">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="edf7d-118">Prerequisites</span></span>

* <span data-ttu-id="edf7d-119">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="edf7d-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="edf7d-120">기본적인 C# 프로그래밍 지식</span><span class="sxs-lookup"><span data-stu-id="edf7d-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="edf7d-121">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="edf7d-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="edf7d-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity</a> 2020/2019 LTS가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 Unity Hub</span><span class="sxs-lookup"><span data-stu-id="edf7d-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="edf7d-123">계속하기 전에 [시작](mr-learning-base-01.md) 자습서 시리즈를 완료하거나 Unity 및 MRTK에 대한 기본적인 사전 경험을 갖추는 **것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="edf7d-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="edf7d-124">이 자습서 시리즈는 Open XR 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)를 지원하고 레거시 WSA 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="edf7d-125">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="edf7d-126">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="edf7d-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="edf7d-127">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="edf7d-128">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="edf7d-129">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="edf7d-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="edf7d-130">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="edf7d-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="edf7d-131">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="edf7d-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="edf7d-132">Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="edf7d-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="edf7d-133">[장면 만들기 및 구성](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름(예: *SpatialAudio)을* 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="edf7d-134">그런 다음 [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면에 대한 MRTK 구성 프로필이 **DefaultHoloLens2ConfigurationProfile인지** 확인하고 공간 인식 메시의 표시 옵션을 **폐색으로 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="edf7d-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="edf7d-135">Project Microsoft Spatializer 추가</span><span class="sxs-lookup"><span data-stu-id="edf7d-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="edf7d-136">Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage</a> 다운로드 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="edf7d-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="edf7d-137">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [자습서 자산 가져오기](mr-learning-base-04.md#importing-the-tutorial-assets) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="edf7d-138">Microsoft Spatializer 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="edf7d-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="edf7d-139">Microsoft Spatializer를 Unity 프로젝트로 가져오면 **MRTK Project Configurator** 창이 **나타나고, Audio spatializer** 드롭다운을 사용하여 Microsoft **Spatializer** 를 선택한 다음, 적용 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![MRTK Project 구성기](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="edf7d-141">Microsoft Spatializer: **Edit -> Project 설정 -> Audio를** 수동으로 사용하도록 설정하고 **Spatializer 플러그 인을** "Microsoft Spatializer"로 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![spatializer 플러그 인을 보여 Project 설정](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="edf7d-143">워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="edf7d-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="edf7d-144">데스크톱 버전의 Windows 공간 오디오는 기본적으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="edf7d-145">작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭하여 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="edf7d-146">HoloLens 2 가장 잘 표현하려면 **공간 소리 -> 헤드폰용 Windows Sonic** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![데스크톱 공간 오디오 설정](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="edf7d-148">이 설정은 Unity 편집기에서 프로젝트를 테스트하려는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="edf7d-149">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-149">Congratulations</span></span>

<span data-ttu-id="edf7d-150">이 자습서에서는 Microsoft Spatializer 플러그 인을 가져오고 사용하도록 설정하고 워크스테이션에서 공간 오디오를 사용하도록 설정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="edf7d-151">다음 자습서에서는 Unity 프로젝트에서 공간 오디오를 추가하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="edf7d-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="edf7d-152">다음 자습서: 2. 단추 상호 작용 소리 공간화</span><span class="sxs-lookup"><span data-stu-id="edf7d-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
