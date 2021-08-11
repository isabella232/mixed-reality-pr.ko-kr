---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204269"
---
# <a name="all-platforms"></a>[모든 플랫폼](#tab/all)

게임의 입력 프로젝트 설정에서 동일한 작업 및 축 매핑을 C++에서 사용할 수 있습니다.

1. 파일/새 C++ 클래스를 사용하여 새 C++ 클래스 만들기...

![새 C++ 클래스 만들기](../images/reverb-g2-img-11.png)

2. Pawn 만들기

![Pawn 만들기](../images/reverb-g2-img-12.png)

3. 프로젝트의 Visual Studio 솔루션에서 새 Pawn 클래스를 찾아 입력을 위해 구성합니다.
* 먼저 생성자에서 AutoPossessPlayer를 첫 번째 플레이어로 설정하여 입력을 pawn으로 라우팅합니다.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* 그런 다음 SetupPlayerInputComponent에서 작업 및 축 이벤트를 프로젝트의 입력 설정에서 작업 이름에 바인딩합니다.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* 클래스에 콜백 함수를 추가합니다.

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* 콜백 함수 정의로 Pawn의 헤더를 업데이트합니다.

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Visual Studio 컴파일하여 새 pawn으로 편집기를 시작합니다. 콘텐츠 브라우저에서 게임으로 pawn을 끌어서 놓으면 이제 입력을 누를 때 pawn이 콜백을 실행합니다.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

thumbstick 축 이벤트를 사용하는 경우 축 이벤트의 이름은 사용된 키에 해당하는 "_X" 또는 "_Y"로 끝나야 합니다.

![썸틱 이벤트 사용](../images/reverb-g2-img-09.png)

마지막으로, Project 설정 > Steam VR 입력에서 **작업 매니페스트 다시 생성** 및 **컨트롤러 바인딩 다시 생성** 단추를 사용하여 Game의 작업을 SteamVR에 등록합니다.

![프로젝트 설정에 작업 등록](../images/reverb-g2-img-10.png)

