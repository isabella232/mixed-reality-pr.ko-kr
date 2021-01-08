---
title: Unreal에서 입력 응시
description: Unreal에서 HoloLens 앱에 대 한 눈 추적 및 헤드 방향으로 응시 입력을 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010143"
---
# <a name="gaze-input"></a><span data-ttu-id="1c16e-104">응시 입력</span><span class="sxs-lookup"><span data-stu-id="1c16e-104">Gaze Input</span></span>

<span data-ttu-id="1c16e-105">혼합 현실 앱에 입력을 입력 하는 것은 사용자가 원하는 항목을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="1c16e-106">장치에서 눈 추적 카메라를 실제 세계 공간의 광선과 일치 시키는 경우 사용자의 시야 데이터를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="1c16e-107">응시는 청사진과 c + +에서 모두 사용할 수 있으며 개체 상호 작용, 방법 찾기 및 카메라 컨트롤과 같은 메커니즘의 핵심 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="1c16e-108">눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="1c16e-108">Enabling eye tracking</span></span>

- <span data-ttu-id="1c16e-109">**프로젝트 설정 > HoloLens** 에서 **응시 입력** 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![응시 입력이 강조 표시 된 HoloLens 프로젝트 설정 기능의 스크린샷](images/unreal-gaze-img-01.png)

- <span data-ttu-id="1c16e-111">새 행위자를 만들어 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="1c16e-112">Unreal의 HoloLens 눈 추적에는 두 눈에 모두 단일 응시 레이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="1c16e-113">Stereoscopic 추적 (두 개의 광선 필요)은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="1c16e-114">시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="1c16e-114">Using eye tracking</span></span>

<span data-ttu-id="1c16e-115">먼저 장치가 **IsEyeTrackerConnected** 함수를 사용 하 여 눈 추적을 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="1c16e-116">함수에서 true를 반환 하는 경우 **GetGazeData** 를 호출 하 여 현재 프레임에서 사용자의 눈이 보이는 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![아이 추적 연결 된 기능의 청사진](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="1c16e-118">HoloLens에서는 고정 지점과 신뢰도 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="1c16e-119">줄 추적에서 응시 원본 및 방향을 사용 하 여 사용자가 원하는 위치를 정확 하 게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="1c16e-120">응시 값은 응시 원점에서 시작 하 여 원본에서 시작 하 여 응시 방향에 선 추적 거리를 곱하여 하는 벡터입니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Get 응시 Data 함수의 청사진](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="1c16e-122">헤드 방향 가져오기</span><span class="sxs-lookup"><span data-stu-id="1c16e-122">Getting head orientation</span></span>

<span data-ttu-id="1c16e-123">HMD (헤드 탑재 디스플레이)의 회전을 사용 하 여 사용자 헤드의 방향을 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="1c16e-124">사용자가 입력 기능을 사용 하지 않고 사용자 헤드 방향을 가져올 수 있지만 눈 추적 정보를 얻을 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="1c16e-125">올바른 출력 데이터를 얻기 위해 청사진에 대 한 참조를 세계 컨텍스트로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="1c16e-126">HMD 데이터 가져오기는 Unreal 4.26 이상 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 함수의 청사진](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="1c16e-128">C++ 사용</span><span class="sxs-lookup"><span data-stu-id="1c16e-128">Using C++</span></span>

- <span data-ttu-id="1c16e-129">게임의 **build.cs** 파일에서 **PublicDependencyModuleNames** 목록에 **EyeTracker** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="1c16e-130">**파일/새 c + + 클래스** 에서 **EyeTracker** 라는 새 c + + 행위자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="1c16e-131">Visual Studio 솔루션은 새 EyeTracker 클래스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="1c16e-132">를 빌드하고 실행 하 여 새 EyeTracker 행위자를 사용 하 여 Unreal 게임을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="1c16e-133">**행위자** 창에서 "EyeTracker"를 검색 하 고 클래스를 게임 창으로 끌어서 놓아 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![행위자 창이 열려 있는 행위자의 스크린샷](images/unreal-gaze-img-06.png)

- <span data-ttu-id="1c16e-135">EyeTracker에서 **EyeTrackerFunctionLibrary** 및 **DrawDebugHelpers** 에 대 한 include를 추가 **합니다**.</span><span class="sxs-lookup"><span data-stu-id="1c16e-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="1c16e-136">모든 응시 데이터를 가져오기 전에 장치에서 **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** 를 사용 하 여 눈동자 추적을 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="1c16e-137">눈 추적이 지원 되는 경우 **UEyeTrackerFunctionLibrary:: GetGazeData** 에서 선 추적을 위한 광선의 시작과 끝을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="1c16e-138">여기서는 응시 벡터를 생성 하 고 해당 콘텐츠를 **LineTraceSingleByChannel** 에 전달 하 여 빛 적중 결과를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="1c16e-139">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="1c16e-139">Next Development Checkpoint</span></span>

<span data-ttu-id="1c16e-140">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1c16e-141">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c16e-142">손 추적</span><span class="sxs-lookup"><span data-stu-id="1c16e-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="1c16e-143">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c16e-144">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="1c16e-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1c16e-145">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c16e-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c16e-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c16e-146">See also</span></span>
* [<span data-ttu-id="1c16e-147">조정</span><span class="sxs-lookup"><span data-stu-id="1c16e-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="1c16e-148">편안함</span><span class="sxs-lookup"><span data-stu-id="1c16e-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="1c16e-149">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="1c16e-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="1c16e-150">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="1c16e-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
