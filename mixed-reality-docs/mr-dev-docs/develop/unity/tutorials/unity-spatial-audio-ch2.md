---
title: 공간화 단추 상호 작용 소리
description: 혼합 현실 응용 프로그램에서 단추를 추가 하 고 단추 상호 작용 소리를 spatialize는 방법에 대해 알아봅니다.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer, prefabs, volume curve
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007363"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="4757a-104">공간화 단추 상호 작용 소리</span><span class="sxs-lookup"><span data-stu-id="4757a-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="4757a-105">목표</span><span class="sxs-lookup"><span data-stu-id="4757a-105">Objectives</span></span>

<span data-ttu-id="4757a-106">HoloLens 2 자습서의 공간 오디오 모듈의이 두 번째 장에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="4757a-107">단추 추가</span><span class="sxs-lookup"><span data-stu-id="4757a-107">Add a button</span></span>
* <span data-ttu-id="4757a-108">단추 클릭 소리 Spatialize</span><span class="sxs-lookup"><span data-stu-id="4757a-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="4757a-109">단추 추가</span><span class="sxs-lookup"><span data-stu-id="4757a-109">Add a button</span></span>

<span data-ttu-id="4757a-110">**프로젝트** 창에서 **자산** 을 선택 하 고 검색 표시줄에 "PressableButtonHoloLens2"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![자산에서 prefab 단추](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="4757a-112">Prefab 단추는 흰색 아이콘이 아니라 파란색 아이콘으로 표시 되는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="4757a-113">**PressableButtonHoloLens2** 라는 Prefab을 **계층** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="4757a-114">새 단추의 **검사기** 창에서 **위치** 속성을 (0,-0.4, 2)로 설정 하 여 응용 프로그램이 시작 될 때 사용자 앞에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="4757a-115">단추의 **변환** 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-115">The **Transform** component of the button will look like this:</span></span>

![단추 변형](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="4757a-117">Spatialize 단추 피드백</span><span class="sxs-lookup"><span data-stu-id="4757a-117">Spatialize button feedback</span></span>

<span data-ttu-id="4757a-118">이 단계에서는 단추에 대 한 오디오 피드백을 spatialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="4757a-119">관련 디자인 제안 사항은 [공간 음향 디자인](../../../design/spatial-sound-design.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4757a-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="4757a-120">오디오 **믹서** 창에서는 오디오 **원본** 구성 요소에서 오디오 재생을 위해 **믹서 그룹** 이라는 대상을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="4757a-121">**창 > 오디오-> 오디오 믹서** 를 사용 하 여 메뉴 모음에서 **오디오 믹서** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="4757a-122">**Mixers** 옆의 ' + '를 클릭 하 여 **믹서** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="4757a-123">새 믹서에는 **Master** 라는 기본 **그룹이** 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="4757a-124">이제 **믹서** 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-124">Your **Mixer** pane will now look like this:</span></span>

![첫 번째 믹서가 있는 믹서 패널](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="4757a-126">[5 장](unity-spatial-audio-ch5.md)에서 반향를 사용 하도록 설정할 때까지 믹서의 볼륨 미터는 Microsoft Spatializer을 통해 재생 된 소리에 대 한 활동을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="4757a-127">**계층** 창에서 **PressableButtonHoloLens2** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="4757a-128">**검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="4757a-129">**오디오 원본** 구성 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="4757a-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="4757a-130">**출력** 속성의 경우 선택기를 클릭 하 고 믹서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="4757a-131">**Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="4757a-132">**공간 Blend** 슬라이더를 3d (1)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="4757a-133">2019 이전의 Unity 버전에서 ' Spatialize ' 확인란은 **오디오 소스** 에 대 한 **검사기** 창의 아래쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="4757a-134">이러한 변경 후 **PressableButtonHoloLens2** 의 **오디오 원본** 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![오디오 원본 단추](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="4757a-136">**Spatialize** 확인란을 선택 하지 않고 **공간 Blend** 를 1 (3d)로 이동 하는 경우 Unity는 **Microsoft spatializer** with hrtfs 대신 패닝 spatializer를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="4757a-137">볼륨 곡선 조정</span><span class="sxs-lookup"><span data-stu-id="4757a-137">Adjust the Volume curve</span></span>

<span data-ttu-id="4757a-138">기본적으로 Unity는 수신기에서 더 멀리 경우 spatialized 소리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="4757a-139">이 감쇠가 상호 작용 피드백 소리에 적용 되 면 인터페이스를 사용 하기가 더 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="4757a-140">이 감쇠를 사용 하지 않도록 설정 하려면 **볼륨** 곡선을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="4757a-141">**PressableButtonHoloLens2** 에 대 한 **검사기** 창의 **오디오 원본** 구성 요소에는 **3d 소리 설정** 이라는 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="4757a-142">해당 섹션에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-142">In that section:</span></span>
1. <span data-ttu-id="4757a-143">**Volume Rolloff** 속성을 Linear로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="4757a-144">Y 축의 ' 0 '에서 ' 1 '까지 **볼륨** 곡선 (빨간색 곡선)의 끝점을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="4757a-145">**볼륨** 곡선의 모양을 평면으로 조정 하려면 흰색 곡선 셰이프 컨트롤을 X 축에 평행으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="4757a-146">이러한 변경 후에는 **PressableButtonHoloLens2** **오디오 원본** 속성의 **3d 사운드 설정** 섹션이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![3D 소리 설정 단추](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="4757a-148">Spatialize 오디오 테스트</span><span class="sxs-lookup"><span data-stu-id="4757a-148">Testing the spatialize audio</span></span>

<span data-ttu-id="4757a-149">새 spatialized button 상호 작용 소리를 자유롭게 테스트 하세요.</span><span class="sxs-lookup"><span data-stu-id="4757a-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="4757a-150">Unity 편집기에서 게임 모드를 입력 하 고, 장면의 루프 오디오 샘플을 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="4757a-151">오디오 소스가 있는 개체를 왼쪽에서 오른쪽으로 이동 하 고 공간 오디오를 사용 하도록 설정 하거나 제외 하 고 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="4757a-152">다음을 기준으로 테스트를 위해 오디오 원본 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="4757a-153">0-1 (2D 비 spatialized 및 3D spatialized 소리) 간에 공간 Blend 속성 이동</span><span class="sxs-lookup"><span data-stu-id="4757a-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="4757a-154">Spatialize 속성 확인 및 선택 취소</span><span class="sxs-lookup"><span data-stu-id="4757a-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="4757a-155">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4757a-155">Next steps</span></span>

<span data-ttu-id="4757a-156">HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="4757a-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="4757a-157">앱에서 단추를 터치 하 고 spatialized 단추 상호 작용 소리를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="4757a-158">Unity 편집기에서 테스트 하는 경우 스페이스바를 눌러 스크롤 휠을 눌러 직접 시뮬레이션을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4757a-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="4757a-159">자세한 내용은 [Mrtk 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4757a-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4757a-160">3 장</span><span class="sxs-lookup"><span data-stu-id="4757a-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

