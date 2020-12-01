---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354346"
---
# <a name="gaze-input"></a><span data-ttu-id="e75d5-104">응시 입력</span><span class="sxs-lookup"><span data-stu-id="e75d5-104">Gaze Input</span></span>

<span data-ttu-id="e75d5-105">응시는 사용자가 보고 있는 항목을 나타내는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="e75d5-106">이는 장치에서 눈 추적 카메라를 사용 하 여 사용자가 현재 보고 있는 것과 일치 하는 실제 지역에서 광선을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="e75d5-107">눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="e75d5-107">Enabling eye tracking</span></span>

- <span data-ttu-id="e75d5-108">**프로젝트 설정 > HoloLens** 에서 **응시 입력** 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![응시 입력이 강조 표시 된 HoloLens 프로젝트 설정 기능의 스크린샷](images/unreal-gaze-img-01.png)

- <span data-ttu-id="e75d5-110">새 행위자를 만들어 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="e75d5-111">Unreal의 HoloLens 눈동자 추적에는 stereoscopic 추적에 필요한 두 광선 (지원 되지 않음)이 아닌 단일 응시 광선이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="e75d5-112">시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="e75d5-112">Using eye tracking</span></span>

<span data-ttu-id="e75d5-113">먼저 장치가 IsEyeTrackerConnected 함수를 사용 하 여 눈 추적을 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="e75d5-114">True가 반환 되 면 GetGazeData를 호출 하 여 현재 프레임에서 사용자의 눈이 보이는 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![아이 추적 연결 된 기능의 청사진](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="e75d5-116">HoloLens에서는 고정 지점과 신뢰도 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="e75d5-117">사용자가 보고 있는 내용을 찾으려면 선 추적에서 응시 원본 및 방향을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="e75d5-118">이 벡터의 시작은 응시 원점이 고, 끝은 원본 및 응시 방향에 원하는 거리를 곱한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Get 응시 Data 함수의 청사진](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="e75d5-120">헤드 방향 가져오기</span><span class="sxs-lookup"><span data-stu-id="e75d5-120">Getting head orientation</span></span>

<span data-ttu-id="e75d5-121">또는 HMD 회전을 사용 하 여 사용자 헤드의 방향을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="e75d5-122">이 경우에는 응시 입력 기능이 필요 하지 않지만 눈 추적 정보는 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="e75d5-123">청사진에 대 한 참조를 올바른 출력 데이터를 얻기 위한 세계 컨텍스트로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="e75d5-124">HMD 데이터 가져오기는 Unreal 4.26 이상 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 함수의 청사진](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="e75d5-126">C++ 사용</span><span class="sxs-lookup"><span data-stu-id="e75d5-126">Using C++</span></span> 

- <span data-ttu-id="e75d5-127">게임의 build.cs 파일에서 PublicDependencyModuleNames 목록에 "EyeTracker"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="e75d5-128">"파일/새 c + + 클래스"에서 "EyeTracker" 라는 새 c + + 행위자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="e75d5-129">Visual Studio 솔루션은 새 EyeTracker 클래스에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="e75d5-130">를 빌드하고 실행 하 여 새 EyeTracker 행위자를 사용 하 여 Unreal 게임을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="e75d5-131">"행위자 준비" 창에서 "EyeTracker"를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="e75d5-132">이 클래스를 게임 창으로 끌어서 놓아 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-132">Drag and drop this class into the game window to add it to the project:</span></span>

![행위자 창이 열려 있는 행위자의 스크린샷](images/unreal-gaze-img-06.png)

- <span data-ttu-id="e75d5-134">EyeTracker에서 EyeTrackerFunctionLibrary 및 DrawDebugHelpers에 대 한 include를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="e75d5-135">틱에서 장치가 UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected를 사용한 아이 추적을 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="e75d5-136">그런 다음 UEyeTrackerFunctionLibrary:: GetGazeData에서 선 추적을 위한 광선의 시작과 끝을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="e75d5-137">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="e75d5-137">Next Development Checkpoint</span></span>

<span data-ttu-id="e75d5-138">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 MRTK 핵심 구성 요소를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="e75d5-139">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="e75d5-140">손 추적</span><span class="sxs-lookup"><span data-stu-id="e75d5-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="e75d5-141">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e75d5-142">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="e75d5-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="e75d5-143">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e75d5-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e75d5-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e75d5-144">See also</span></span>
* [<span data-ttu-id="e75d5-145">조정</span><span class="sxs-lookup"><span data-stu-id="e75d5-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="e75d5-146">편안함</span><span class="sxs-lookup"><span data-stu-id="e75d5-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="e75d5-147">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="e75d5-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="e75d5-148">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="e75d5-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
