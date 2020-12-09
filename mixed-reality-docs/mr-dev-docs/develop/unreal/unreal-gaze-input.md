---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925989"
---
# <a name="gaze-input"></a>응시 입력

혼합 현실 앱에 입력을 입력 하는 것은 사용자가 원하는 항목을 확인 하는 것입니다. 장치에서 눈 추적 카메라를 실제 세계 공간의 광선과 일치 시키는 경우 사용자의 시야 데이터를 사용할 수 있게 됩니다. 응시는 청사진과 c + +에서 모두 사용할 수 있으며 개체 상호 작용, 방법 찾기 및 카메라 컨트롤과 같은 메커니즘의 핵심 기능입니다.

## <a name="enabling-eye-tracking"></a>눈 추적 사용

- **프로젝트 설정 > HoloLens** 에서 **응시 입력** 기능을 사용 하도록 설정 합니다.

![응시 입력이 강조 표시 된 HoloLens 프로젝트 설정 기능의 스크린샷](images/unreal-gaze-img-01.png)

- 새 행위자를 만들어 장면에 추가 합니다.

> [!NOTE]
> Unreal의 HoloLens 눈 추적에는 두 눈에 모두 단일 응시 레이가 있습니다. Stereoscopic 추적 (두 개의 광선 필요)은 지원 되지 않습니다.

## <a name="using-eye-tracking"></a>시선 추적 사용

먼저 장치가 **IsEyeTrackerConnected** 함수를 사용 하 여 눈 추적을 지원 하는지 확인 합니다.  함수에서 true를 반환 하는 경우 **GetGazeData** 를 호출 하 여 현재 프레임에서 사용자의 눈이 보이는 위치를 찾습니다.

![아이 추적 연결 된 기능의 청사진](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens에서는 고정 지점과 신뢰도 값을 사용할 수 없습니다.

줄 추적에서 응시 원본 및 방향을 사용 하 여 사용자가 원하는 위치를 정확 하 게 찾을 수 있습니다.  응시 값은 응시 원점에서 시작 하 여 원본에서 시작 하 여 응시 방향에 선 추적 거리를 곱하여 하는 벡터입니다.

![Get 응시 Data 함수의 청사진](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>헤드 방향 가져오기

HMD (헤드 탑재 디스플레이)의 회전을 사용 하 여 사용자 헤드의 방향을 나타낼 수도 있습니다. 사용자가 입력 기능을 사용 하지 않고 사용자 헤드 방향을 가져올 수 있지만 눈 추적 정보를 얻을 수는 없습니다.  올바른 출력 데이터를 얻기 위해 청사진에 대 한 참조를 세계 컨텍스트로 추가 합니다.

> [!NOTE]
> HMD 데이터 가져오기는 Unreal 4.26 이상 에서만 사용할 수 있습니다.

![Get HMDData 함수의 청사진](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>C++ 사용

- 게임의 **build.cs** 파일에서 **PublicDependencyModuleNames** 목록에 **EyeTracker** 를 추가 합니다.

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

- **파일/새 c + + 클래스** 에서 **EyeTracker** 라는 새 c + + 행위자를 만듭니다.
    - Visual Studio 솔루션은 새 EyeTracker 클래스를 엽니다. 를 빌드하고 실행 하 여 새 EyeTracker 행위자를 사용 하 여 Unreal 게임을 엽니다.  **행위자** 창에서 "EyeTracker"를 검색 하 고 클래스를 게임 창으로 끌어서 놓아 프로젝트에 추가 합니다.

![행위자 창이 열려 있는 행위자의 스크린샷](images/unreal-gaze-img-06.png)

- EyeTracker에서 **EyeTrackerFunctionLibrary** 및 **DrawDebugHelpers** 에 대 한 include를 추가 **합니다**.

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

모든 응시 데이터를 가져오기 전에 장치에서 **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** 를 사용 하 여 눈동자 추적을 지원 하는지 확인 합니다.  눈 추적이 지원 되는 경우 **UEyeTrackerFunctionLibrary:: GetGazeData** 에서 선 추적을 위한 광선의 시작과 끝을 찾습니다. 여기서는 응시 벡터를 생성 하 고 해당 콘텐츠를 **LineTraceSingleByChannel** 에 전달 하 여 빛 적중 결과를 디버그할 수 있습니다.

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

앞에서 설명한 실제 개발 경험을 수행 하는 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소를 계속 진행할 수 있습니다.

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
