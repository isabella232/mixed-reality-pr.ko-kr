---
title: 공간 오디오 자습서 - 2. 공간화 단추 상호 작용 소리
description: 프로젝트에 단추를 추가하고 단추 상호 작용 소리를 공간화합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer, 프리팹, 볼륨 곡선
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712810"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="f3f66-105">2. 공간화 단추 상호 작용 소리</span><span class="sxs-lookup"><span data-stu-id="f3f66-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="f3f66-106">개요</span><span class="sxs-lookup"><span data-stu-id="f3f66-106">Overview</span></span>

<span data-ttu-id="f3f66-107">이 자습서에서는 단추 상호 작용 소리를 공간화하는 방법과 오디오 클립을 사용하여 공간화된 단추 상호 작용을 테스트하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="f3f66-108">목표</span><span class="sxs-lookup"><span data-stu-id="f3f66-108">Objectives</span></span>

* <span data-ttu-id="f3f66-109">단추 클릭 소리 추가 및 공간화</span><span class="sxs-lookup"><span data-stu-id="f3f66-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="f3f66-110">단추 추가</span><span class="sxs-lookup"><span data-stu-id="f3f66-110">Add a button</span></span>

<span data-ttu-id="f3f66-111">단추 프리팹을 추가하려면 **프로젝트** 창에서 **패키지를** 선택하고 검색 창에 "PressableButtonHoloLens2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![자산의 단추 프리팹](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="f3f66-113">단추 프리팹은 파란색 아이콘으로 표시되는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="f3f66-114">**PressableButtonHoloLens2 프리팹을** 클릭하고 계층 구조로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="f3f66-115">**PressableButtonHoloLens2** 개체를 선택한 상태에서 검사기 창에서 **다음과** 같이 변환 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f3f66-116">**위치**: X = 0, Y = -0.4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="f3f66-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="f3f66-117">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f3f66-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3f66-118">**크기 조정**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="f3f66-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![단추 변환](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="f3f66-120">장면의 개체에 초점을 맞추려면 **PressableButtonHoloLens2** 개체를 두 번 클릭한 다음, 약간 다시 확대하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="f3f66-121">공간화 단추 피드백</span><span class="sxs-lookup"><span data-stu-id="f3f66-121">Spatialize button feedback</span></span>

<span data-ttu-id="f3f66-122">이 단계에서는 단추에 대한 오디오 피드백을 공간화합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="f3f66-123">관련 디자인 제안은 [공간 음향 디자인](../../../design/spatial-sound-design.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3f66-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="f3f66-124">오디오 **혼합기** 창에서 오디오 **원본** 구성 요소에서 오디오 재생을 위해 **Mixer Groups라는** 대상을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="f3f66-125">**오디오 혼합기** 창을 열려면 Unity 메뉴에서 **창**  >  **오디오**  >  **오디오 혼합기:** ![ 오디오 혼합기 창 열기를 선택합니다.](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="f3f66-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="f3f66-126">**Mixers** 옆에 있는 '+'를 클릭하여 **Mixer를** 만들고 Mixer에 적절한 이름(예: _Spatial Audio Mixer)을_ 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="f3f66-127">새 mixer에는 **Master라는** 기본 **그룹이** 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-127">The new mixer will include a default **Group** called **Master**.</span></span>

![첫 번째 mixer가 있는 Mixer 패널](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="f3f66-129">5장에서 반향을 사용하도록 설정할 [때까지: reverb를 사용하여 공간 오디오에 거리를 추가하면,](unity-spatial-audio-ch5.md)혼합기 볼륨 미터는 Microsoft Spatializer를 통해 재생되는 소리에 대한 활동을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="f3f66-130">계층 구조 창에서 **PressableButtonHoloLens2를** 선택한 다음, 검사기 창에서 **오디오 원본** 구성 요소를 찾고 다음과 같이 오디오 원본 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="f3f66-131">**Output** 속성에 대해 선택기를 클릭하고 만든 **Mixer를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="f3f66-132">**공간화** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="f3f66-133">**Spatial Blend** 슬라이더를 3D(1)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![단추 오디오 원본](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="f3f66-135">공간화 확인란을 선택하지 않고 **Spatial Blend를**  1(3D)로 이동하는 경우 Unity는 HRTF가 있는 **Microsoft Spatializer** 대신 해당 이동 공간화기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="f3f66-136">볼륨 곡선 조정</span><span class="sxs-lookup"><span data-stu-id="f3f66-136">Adjust the Volume curve</span></span>

<span data-ttu-id="f3f66-137">기본적으로 Unity는 수신기에서 더 멀리 떨어져 있을 때 공간화된 소리를 감쇠합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="f3f66-138">이 감쇠가 상호 작용 피드백 소리에 적용되면 인터페이스를 사용하기가 더 어려워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="f3f66-139">이 감쇠를 사용하지 않도록 설정하려면 **오디오 원본** 구성 요소에서 **볼륨** 곡선을 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="f3f66-140">계층 구조 창에서 **PressableButtonHoloLens2를** 선택한 다음, 검사기 창에서 **오디오 원본**  >  **3D 소리 설정으로** 이동하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="f3f66-141">볼륨 **롤오프** 속성을 선형 롤오프로 설정</span><span class="sxs-lookup"><span data-stu-id="f3f66-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="f3f66-142">**볼륨** 곡선(빨간색 곡선)의 엔드포인트를 y축의 '0'에서 '1'까지 끕</span><span class="sxs-lookup"><span data-stu-id="f3f66-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="f3f66-143">**볼륨** 곡선의 모양을 평면으로 조정하려면 흰색 곡선 모양 컨트롤을 X축과 병렬로 끌어서</span><span class="sxs-lookup"><span data-stu-id="f3f66-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![단추 3D 소리 설정](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="f3f66-145">공간화 오디오 테스트</span><span class="sxs-lookup"><span data-stu-id="f3f66-145">Testing the spatialize audio</span></span>

<span data-ttu-id="f3f66-146">Unity 편집기에서 공간화 오디오를 테스트하려면 **PressableButtonHoloLens2** 개체에서 루프 **옵션을** 선택한 **오디오 원본** 구성 요소에 오디오 클립을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="f3f66-147">재생 모드에서 **PressableButtonHoloLens2** 개체를 왼쪽에서 오른쪽으로 이동하고 워크스테이션에서 공간 오디오를 사용하는 경우와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="f3f66-148">다음을 수행하여 테스트할 오디오 원본 설정을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="f3f66-149">**Spatial Blend** 속성을 0에서 1 사이로 이동(2D 공간화가 아닌 소리와 3D 공간화된 소리)</span><span class="sxs-lookup"><span data-stu-id="f3f66-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="f3f66-150">**Spatialize** 속성 확인 및 선택 취소</span><span class="sxs-lookup"><span data-stu-id="f3f66-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="f3f66-151">HoloLens 2 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f3f66-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="f3f66-152">앱에서 단추를 클릭하고 공간화된 단추 상호 작용 소리를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="f3f66-153">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3f66-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f3f66-154">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-154">Congratulations</span></span>

<span data-ttu-id="f3f66-155">이 자습서에서는 단추 상호 작용 소리를 공간화하고 오디오 클립을 사용하여 공간화된 단추 상호 작용을 테스트하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="f3f66-156">다음 자습서에서는 비디오 원본에서 오디오를 공간화하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f3f66-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3f66-157">다음 자습서: 3. 비디오에서 오디오 공간화</span><span class="sxs-lookup"><span data-stu-id="f3f66-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
