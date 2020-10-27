---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638726"
---
# <a name="all-platforms"></a>[<span data-ttu-id="7ce09-101">모든 플랫폼</span><span class="sxs-lookup"><span data-stu-id="7ce09-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="7ce09-102">게임의 입력 프로젝트 설정에서 동일한 작업 및 축 매핑을 c + +에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="7ce09-103">파일/새 c + + 클래스를 사용 하 여 새 c + + 클래스 만들기 ...</span><span class="sxs-lookup"><span data-stu-id="7ce09-103">Create a new C++ Class with File/New C++ Class...</span></span>

![새 c + + 클래스 만들기](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="7ce09-105">폰을 만들기</span><span class="sxs-lookup"><span data-stu-id="7ce09-105">Create a pawn</span></span>

![폰을 만들기](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="7ce09-107">프로젝트의 Visual Studio 솔루션에서 새 폰을 클래스를 찾고 입력을 위해 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="7ce09-108">먼저 생성자에서 AutoPossessPlayer를 첫 번째 플레이어로 설정 하 여 입력을 폰을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="7ce09-109">그런 다음 SetupPlayerInputComponent에서 작업 및 축 이벤트를 프로젝트의 입력 설정에서 작업 이름에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="7ce09-110">클래스에 콜백 함수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="7ce09-111">콜백 함수 정의를 사용 하 여 폰을 헤더를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="7ce09-112">새 폰을 편집기를 시작 하려면 Visual Studio에서 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="7ce09-113">콘텐츠 브라우저에서 게임으로 폰을 끌어서 놓고 이제 입력을 누를 때 폰을 콜백을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="7ce09-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="7ce09-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="7ce09-115">엄지 스틱 축 이벤트를 사용 하는 경우 축 이벤트의 이름은 사용 된 키에 해당 하는 "_X" 또는 "_Y"로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![엄지 스틱 이벤트 사용](../images/reverb-g2-img-09.png)

<span data-ttu-id="7ce09-117">마지막으로 프로젝트 설정 > 스트림 VR 입력에서 **작업 매니페스트 다시 생성** 및 **컨트롤러 바인딩 다시** 생성 단추를 사용 하 여 게임의 작업을 SteamVR로 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce09-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![프로젝트 설정에 동작 등록](../images/reverb-g2-img-10.png)

