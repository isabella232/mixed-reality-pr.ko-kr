---
title: 공간 오디오 자습서-1. 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가 하 여 HoloLens 2 HRTF 하드웨어 오프 로드에 액세스 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590045"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="98af9-105">1. Unity 프로젝트에 공간 오디오 추가</span><span class="sxs-lookup"><span data-stu-id="98af9-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="98af9-106">개요</span><span class="sxs-lookup"><span data-stu-id="98af9-106">Overview</span></span>

<span data-ttu-id="98af9-107">HoloLens2의 Unity 용 공간 오디오 자습서를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="98af9-108">이 자습서 시리즈를 통해 HoloLens 2에서 HRTF (head 관련 전송 함수) 오프 로드를 사용 하는 방법과 HRTF 오프 로드를 사용할 때 반향를 사용 하도록 설정 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="98af9-109">[Microsoft Spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity) 는이 자습서 시퀀스의 완료 된 Unity 프로젝트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="98af9-110">유용 하 게 사용할 수 있는 경우 HRTF 기반 spatialization 기술과 권장 사항을 사용 하 여 소리를 spatialize 소리를 이해 하려면 [공간 음향 디자인](/windows/mixed-reality/spatial-sound-design)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98af9-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="98af9-111">HRTF 오프 로드 란?</span><span class="sxs-lookup"><span data-stu-id="98af9-111">What is HRTF offload?</span></span>

<span data-ttu-id="98af9-112">HRTF 기반 알고리즘을 사용 하 여 오디오를 처리 하려면 많은 양의 특수 한 계산을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="98af9-113">HoloLens 2에는 응용 프로그램 프로세서의 부담을 방지 하기 위해 활용할 수 있는 전용 하드웨어가 포함 되어 있습니다. 따라서 HRTF 기반 알고리즘의 처리를 "오프 로딩" 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="98af9-114">Microsoft spatializer 플러그 인을 사용 하면 응용 프로그램이 공간 오디오 이외의 작업에 더 많은 응용 프로그램 프로세서를 사용할 수 있도록 응용 프로그램에서 전용 HRTF 하드웨어를 활용할 수 있는 쉬운 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="98af9-115">목표</span><span class="sxs-lookup"><span data-stu-id="98af9-115">Objectives</span></span>

* <span data-ttu-id="98af9-116">Microsoft spatializer 플러그 인 가져오기 및 사용</span><span class="sxs-lookup"><span data-stu-id="98af9-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="98af9-117">개발자 워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="98af9-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98af9-118">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="98af9-118">Prerequisites</span></span>

* <span data-ttu-id="98af9-119">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="98af9-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="98af9-120">기본적인 C# 프로그래밍 지식</span><span class="sxs-lookup"><span data-stu-id="98af9-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="98af9-121">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="98af9-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="98af9-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2019 LTS가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가되어 있음)</span><span class="sxs-lookup"><span data-stu-id="98af9-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="98af9-123">계속 하기 전에 [초보자](mr-learning-base-01.md) 를 위한 자습서 시리즈를 완료 하거나 Unity 및 MRTK를 사용 하 여 몇 가지 기본 사전 경험을 사용 하는 **것이 좋습니다** .</span><span class="sxs-lookup"><span data-stu-id="98af9-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="98af9-124">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019 LTS입니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="98af9-125">이는 위에서 연결된 필수 구성 요소에서 설명하는 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="98af9-126">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="98af9-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="98af9-127">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="98af9-128">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="98af9-129">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="98af9-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="98af9-130">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="98af9-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="98af9-131">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="98af9-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="98af9-132">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="98af9-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="98af9-133">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="98af9-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="98af9-134">[장면을 만들고 설정](mr-learning-base-02.md#creating-and-configuring-the-scene) 하 고 장면에 적절 한 이름 (예: *SpatialAudio* )을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="98af9-135">그런 다음 [공간 인식 디스플레이 변경 옵션](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필이 **DefaultHoloLens2ConfigurationProfile** 고 공간 인식 메시의 표시 옵션을 **폐색** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="98af9-136">프로젝트에 Microsoft Spatializer 추가</span><span class="sxs-lookup"><span data-stu-id="98af9-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="98af9-137">Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio Spatializer</a> 를 다운로드 하 여 가져옵니다. 1.0.18. unitypackage</span><span class="sxs-lookup"><span data-stu-id="98af9-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="98af9-138">Unity 사용자 지정 패키지를 가져오는 방법에 대 한 미리 알림은 [자습서 자산 가져오기](mr-learning-base-04.md#importing-the-tutorial-assets) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-138">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="98af9-139">Microsoft Spatializer 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="98af9-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="98af9-140">**Microsoft Spatializer** 를 가져온 후에는 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="98af9-141">**편집 > 프로젝트 설정-오디오 >** 열고 **Spatializer 플러그 인** 을 "Microsoft Spatializer"로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Spatializer 플러그 인을 보여 주는 프로젝트 설정](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="98af9-143">워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="98af9-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="98af9-144">데스크톱 버전의 Windows에서는 공간 오디오가 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="98af9-145">작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="98af9-146">HoloLens 2에서 제공 하는 내용을 가장 잘 표시 하려면 **공간 사운드-헤드폰 용 Windows Sonic >** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![데스크톱 공간 오디오 설정](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="98af9-148">이 설정은 Unity 편집기에서 프로젝트를 테스트 하려는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="98af9-149">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-149">Congratulations</span></span>

<span data-ttu-id="98af9-150">이 자습서에서는 Microsoft Spatializer 플러그 인을 가져오고 사용 하도록 설정 하는 방법 및 워크스테이션에서 공간 오디오를 사용 하도록 설정 하는 방법을 학습.</span><span class="sxs-lookup"><span data-stu-id="98af9-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="98af9-151">다음 자습서에서는 unity 프로젝트에서 공간 오디오를 추가 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="98af9-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="98af9-152">다음 자습서: 2. Spatializing button 상호 작용 소리</span><span class="sxs-lookup"><span data-stu-id="98af9-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
