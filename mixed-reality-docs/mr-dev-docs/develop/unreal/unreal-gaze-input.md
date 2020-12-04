---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578892"
---
# <a name="gaze-input"></a>응시 입력

응시는 사용자가 보고 있는 항목을 나타내는 데 사용 됩니다.  이는 장치에서 눈 추적 카메라를 사용 하 여 사용자가 현재 보고 있는 것과 일치 하는 실제 지역에서 광선을 찾습니다.

## <a name="enabling-eye-tracking"></a>눈 추적 사용

- **프로젝트 설정 > HoloLens** 에서 **응시 입력** 기능을 사용 하도록 설정 합니다.

![응시 입력이 강조 표시 된 HoloLens 프로젝트 설정 기능의 스크린샷](images/unreal-gaze-img-01.png)

- 새 행위자를 만들어 장면에 추가 합니다.

> [!NOTE] 
> Unreal의 HoloLens 눈동자 추적에는 stereoscopic 추적에 필요한 두 광선 (지원 되지 않음)이 아닌 단일 응시 광선이 있습니다.

## <a name="using-eye-tracking"></a>시선 추적 사용

먼저 장치가 IsEyeTrackerConnected 함수를 사용 하 여 눈 추적을 지원 하는지 확인 합니다.  True가 반환 되 면 GetGazeData를 호출 하 여 현재 프레임에서 사용자의 눈이 보이는 위치를 찾습니다.

![아이 추적 연결 된 기능의 청사진](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens에서는 고정 지점과 신뢰도 값을 사용할 수 없습니다.

사용자가 보고 있는 내용을 찾으려면 선 추적에서 응시 원본 및 방향을 사용 합니다.  이 벡터의 시작은 응시 원점이 고, 끝은 원본 및 응시 방향에 원하는 거리를 곱한 값입니다.

![Get 응시 Data 함수의 청사진](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>헤드 방향 가져오기

또는 HMD 회전을 사용 하 여 사용자 헤드의 방향을 나타낼 수 있습니다.  이 경우에는 응시 입력 기능이 필요 하지 않지만 눈 추적 정보는 제공 되지 않습니다.  청사진에 대 한 참조를 올바른 출력 데이터를 얻기 위한 세계 컨텍스트로 추가 해야 합니다.

> [!NOTE]
> HMD 데이터 가져오기는 Unreal 4.26 이상 에서만 사용할 수 있습니다.

![Get HMDData 함수의 청사진](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>C++ 사용 

- 게임의 build.cs 파일에서 PublicDependencyModuleNames 목록에 "EyeTracker"를 추가 합니다.

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

- "파일/새 c + + 클래스"에서 "EyeTracker" 라는 새 c + + 행위자를 만듭니다.
    - Visual Studio 솔루션은 새 EyeTracker 클래스에 열립니다. 를 빌드하고 실행 하 여 새 EyeTracker 행위자를 사용 하 여 Unreal 게임을 엽니다.  "행위자 준비" 창에서 "EyeTracker"를 검색 합니다.  이 클래스를 게임 창으로 끌어서 놓아 프로젝트에 추가 합니다.

![행위자 창이 열려 있는 행위자의 스크린샷](images/unreal-gaze-img-06.png)

- EyeTracker에서 EyeTrackerFunctionLibrary 및 DrawDebugHelpers에 대 한 include를 추가 합니다.

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

틱에서 장치가 UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected를 사용한 아이 추적을 지원 하는지 확인 합니다.  그런 다음 UEyeTrackerFunctionLibrary:: GetGazeData에서 선 추적을 위한 광선의 시작과 끝을 찾습니다.

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

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 MRTK 핵심 구성 요소를 탐색하는 것이 좋습니다. 여기에서 다음 구성 요소로 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [손 추적](unreal-hand-tracking.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [조정](../../calibration.md)
* [편안함](../../design/comfort.md)
* [응시 및 커밋](../../design/gaze-and-commit.md)
* [음성 입력 ](../../out-of-scope/voice-design.md)
