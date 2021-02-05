---
title: 공간 오디오 자습서-3. 비디오에서 공간화 오디오
description: 비디오 자산을 Unity 프로젝트로 가져오고 비디오에서 오디오를 spatialize.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer, 비디오 가져오기, 비디오 플레이어
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590055"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="6bb82-105">3. 비디오에서 공간화 오디오</span><span class="sxs-lookup"><span data-stu-id="6bb82-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="6bb82-106">개요</span><span class="sxs-lookup"><span data-stu-id="6bb82-106">Overview</span></span>

<span data-ttu-id="6bb82-107">이 자습서에서는 비디오 원본에서 오디오를 spatialize unity 편집기 및 HoloLens 2에서이를 테스트 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="6bb82-108">목표</span><span class="sxs-lookup"><span data-stu-id="6bb82-108">Objectives</span></span>

* <span data-ttu-id="6bb82-109">비디오 가져오기 및 비디오 플레이어 추가</span><span class="sxs-lookup"><span data-stu-id="6bb82-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="6bb82-110">Quadrangle 비디오 재생</span><span class="sxs-lookup"><span data-stu-id="6bb82-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="6bb82-111">비디오에서 quadrangle로 오디오 라우팅 및 오디오 spatialize</span><span class="sxs-lookup"><span data-stu-id="6bb82-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="6bb82-112">비디오 가져오기 및 장면에 비디오 플레이어 추가</span><span class="sxs-lookup"><span data-stu-id="6bb82-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="6bb82-113">이 자습서에서는 공간 오디오 샘플 프로젝트에서 [이 비디오](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="6bb82-114">Unity 프로젝트에 비디오를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="6bb82-114">To import Video into the unity project.</span></span> <span data-ttu-id="6bb82-115">Unity 메뉴에서 **자산**  >  **가져오기 새 자산 가져오기** 
 ![ 자산을 선택 합니다.](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="6bb82-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="6bb82-116">**새 자산 가져오기** ... 창에서 다운로드 한 **Microsoft HoloLens-공간 PTPvx7mDon4** 파일을 선택 하 고 **열기** 단추를 클릭 하 여 자산을 프로젝트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![자산 선택](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="6bb82-118">비디오 클립의 품질 설정을 조정 하면 HoloLens 2에서 부드러운 재생을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="6bb82-119">**프로젝트** 창에서 비디오 파일을 선택 하 고 비디오 파일의 검사기 창에서 **Windows 스토어 앱** 에 대 한 설정을 **재정의** 하 고 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="6bb82-120">**트랜스 코딩** 사용</span><span class="sxs-lookup"><span data-stu-id="6bb82-120">Enable **Transcode**</span></span>
* <span data-ttu-id="6bb82-121">**코덱을** H264로 설정</span><span class="sxs-lookup"><span data-stu-id="6bb82-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="6bb82-122">**비트 전송률 모드** 를 낮음으로 설정</span><span class="sxs-lookup"><span data-stu-id="6bb82-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="6bb82-123">**공간 품질** 을 보통 공간 품질로 설정</span><span class="sxs-lookup"><span data-stu-id="6bb82-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="6bb82-124">이러한 조정 후에 적용을 클릭 하 여 비디오 클립의 품질 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![비디오 속성 변경](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="6bb82-126">계층을 마우스 오른쪽 단추로 클릭 하 고 비디오  >  플레이어 구성 요소를 추가 하려면 비디오 **비디오 플레이어** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![비디오 플레이어 추가](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="6bb82-128">Quadrangle 비디오 재생</span><span class="sxs-lookup"><span data-stu-id="6bb82-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="6bb82-129">비디오 **플레이어** 개체는 비디오를 렌더링 하기 위한 질감 게임 개체가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="6bb82-130">계층을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체**  >  **쿼드** 을 선택 하 여 다음과 같이 쿼드를 만들고 해당 **변환** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="6bb82-131">**Position**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="6bb82-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="6bb82-132">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="6bb82-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="6bb82-133">**크기 조정**: X = 1.28, Y = 0.72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="6bb82-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![쿼드 추가](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="6bb82-135">이제 비디오를 사용 하 여 **쿼드** 의 질감을 선택 하 고, **프로젝트** 창에서 마우스 오른쪽 단추를 클릭 하 고, 렌더링 질감 **만들기** 를 선택 하 여 렌더링  >   텍스처 구성 요소를 만들려면, _공간 오디오 텍스처_ 와 같이 렌더링 질감에 적합 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![렌더링 질감 만들기](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="6bb82-137">**렌더링 질감** 을 선택 하 고 검사기 창에서 **Size** 속성을 비디오의 1280x720에 대 한 기본 해상도와 일치 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="6bb82-138">그러면 HoloLens 2에서 최적의 렌더링 성능을 보장 하기 위해 **깊이 버퍼** 속성을 **16 비트** 수준 이상으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![질감 속성 렌더링](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="6bb82-140">그런 다음 생성 된 렌더링 질감 **공간 오디오 텍스처** 를 **쿼드** 의 질감으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="6bb82-141">**프로젝트** 창의 **공간 오디오 텍스처** 를 계층 구조에서 **쿼드** 로 끌어 렌더링 질감을 쿼드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="6bb82-142">HoloLens 2의 성능을 보장 하려면 계층에서 쿼드를 선택 하 고 셰이더에 대 한 검사기 창에서 **Mixed Reality Toolkit**  >  **Standard** 셰이더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![쿼드 질감 속성](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="6bb82-144">비디오 **플레이어** 를 설정 하 고 **질감을 렌더링** 하 여 비디오 클립을 재생 하려면 **계층 구조** 및 **검사기** 창에서 **비디오 플레이어** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="6bb82-145">**비디오 클립** 속성을 다운로드 한 비디오 파일 ' Microsoft HoloLens-PTPvx7mDon4 '로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="6bb82-146">**루프** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="6bb82-147">**대상 질감** 을 새 렌더링 질감 **공간 오디오 질감** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![비디오 플레이어 속성](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="6bb82-149">비디오에서 오디오 Spatialize</span><span class="sxs-lookup"><span data-stu-id="6bb82-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="6bb82-150">계층 창에서 **쿼드** 개체를 선택한 다음 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 비디오에서 오디오를 라우팅할 **오디오 원본을** 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="6bb82-151">**오디오 원본** 에서:</span><span class="sxs-lookup"><span data-stu-id="6bb82-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="6bb82-152">**출력** 을 **공간 오디오 믹서** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="6bb82-153">**Spatialize** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="6bb82-154">**공간 Blend** 슬라이더를 1 (3d)로 이동</span><span class="sxs-lookup"><span data-stu-id="6bb82-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![쿼드 오디오 원본 검사기](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="6bb82-156">오디오 **원본** 으로 오디오를 라우팅하도록 비디오 플레이어를 설정 하려면 계층 창에서 **비디오 플레이어** 를 선택 하 고 검사기의 비디오 플레이어 개체에서 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="6bb82-157">오디오 **출력 모드** 를 **오디오 원본** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="6bb82-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="6bb82-158">**오디오 원본** 속성을 **쿼드** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-158">Set the **Audio Source** property to the **Quad**</span></span>

![비디오 플레이어에서 오디오 원본 설정](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="6bb82-160">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bb82-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6bb82-161">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-161">Congratulations</span></span>

<span data-ttu-id="6bb82-162">이 자습서에서는 비디오 원본에서 오디오를 spatialize 하는 방법을 알아보았습니다. HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6bb82-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="6bb82-163">비디오를 보고 듣고 비디오에서 오디오가 spatialized 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="6bb82-164">다음 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb82-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6bb82-165">다음 자습서: 4. 런타임에 spatialization 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="6bb82-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
