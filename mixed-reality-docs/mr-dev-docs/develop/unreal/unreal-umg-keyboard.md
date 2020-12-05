---
title: Unreal의 UMG 및 키보드
description: 영역 없는 동작 그래픽을 사용 하 여 widget에서 UI 시스템을 만드는 방법에 대해 알아봅니다.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed reality 헤드셋, 가상 현실 헤드셋, 위젯, UI, UMG, Unreal 움직임 그래픽, Unreal Engine, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609764"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="be963-104">Unreal의 UMG 및 키보드</span><span class="sxs-lookup"><span data-stu-id="be963-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="be963-105">UNSUMG (실제 동작 그래픽)는 메뉴 및 텍스트 상자와 같은 인터페이스를 만드는 데 사용 되는 실제 엔진의 기본 제공 UI 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="be963-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="be963-106">UMG로 빌드된 사용자 인터페이스는 위젯을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="be963-107">새 위젯을 만들고, 전 세계 공간에 추가 하 고, 시스템 키보드를 사용 하 여 상호 작용을 사용 하도록 설정 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="be963-108">공식 Unreal Engine [설명서](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)에서 umg에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="be963-109">새 위젯 만들기</span><span class="sxs-lookup"><span data-stu-id="be963-109">Create a new widget</span></span>

- <span data-ttu-id="be963-110">위젯 청사진을 만들어 게임 UI를 레이아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Unreal 메뉴에서 위젯 청사진을 추가 하는 스크린샷](images/unreal-umg-img-01.png)

- <span data-ttu-id="be963-112">새 청사진을 열고 색상표의 구성 요소를 캔버스에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="be963-113">이 경우 "Input" 섹션에서 두 개의 텍스트 상자 구성 요소를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![텍스트 위젯 구성 요소가 강조 표시 되 고 확장 된 계층 창의 스크린샷](images/unreal-umg-img-02.png)

- <span data-ttu-id="be963-115">계층 구조 또는 디자이너 창에서 위젯을 선택 하 고 세부 정보 패널에서 매개 변수를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="be963-116">이 경우 기본 "힌트 텍스트"와 텍스트 상자를 마우스로 가리킬 때 표시 되는 색조 색을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="be963-117">텍스트 상자는와 상호 작용할 때 HoloLens의 가상 키보드를 팝업 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![계층 구조 창에서 수정 된 매개 변수의 스크린샷](images/unreal-umg-img-03.png)

- <span data-ttu-id="be963-119">세부 정보 패널에서 이벤트를 구독할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-119">Events can also be subscribed to in the details panel:</span></span>

![세부 정보 패널 이벤트의 스크린샷](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="be963-121">세계 공간에 위젯 추가</span><span class="sxs-lookup"><span data-stu-id="be963-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="be963-122">새 행위자를 만들고, 위젯 구성 요소를 추가 하 고, 장면에 행위자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![위젯이 첨부 된 행위자의 스크린샷](images/unreal-umg-img-05.png)

- <span data-ttu-id="be963-124">위젯의 세부 정보 패널에서 **위젯 클래스** 를 앞에서 만든 위젯 청사진으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![위젯 클래스 집합을 사용 하는 청사진 정보 패널의 스크린샷](images/unreal-umg-img-06.png)

- <span data-ttu-id="be963-126">텍스트 위젯에 대해 **하드웨어 입력 수신** 이 선택 취소 되어 있는지 확인 하 여 가상 키보드의 텍스트만 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![하드웨어 입력 수신이 있는 상호 작용 섹션의 스크린샷 선택 취소 됨](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="be963-128">위젯 상호 작용</span><span class="sxs-lookup"><span data-stu-id="be963-128">Widget Interaction</span></span>

<span data-ttu-id="be963-129">UMG 위젯은 일반적으로 마우스에서 입력을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="be963-130">HoloLens 또는 VR에서는 동일한 이벤트를 가져오기 위해 위젯 상호 작용 구성 요소를 사용 하 여 마우스를 시뮬레이션 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="be963-131">새 행위자를 만들고, **위젯 상호 작용** 구성 요소를 추가 하 고, 장면에 행위자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![위젯 상호 작용 구성 요소가 강조 표시 된 새 행위자의 스크린샷](images/unreal-umg-img-08.png)

- <span data-ttu-id="be963-133">위젯 상호 작용 구성 요소에 대 한 세부 정보 패널에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="be963-134">상호 작용 거리를 원하는 거리 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="be963-135">**상호 작용 소스** 를 **사용자 지정** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="be963-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="be963-136">개발의 경우 **디버그 표시** 를 **true** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-136">For development, set **Show Debug** to **true**:</span></span>

![위젯 상호 작용 및 디버깅 구성 요소 속성의 스크린샷](images/unreal-umg-img-09.png)

<span data-ttu-id="be963-138">상호 작용 원본의 기본값은 "세계" 이며,이는 위젯 상호 작용 구성 요소의 세계 위치를 기준으로 raycasts를 전송 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="be963-139">AR 및 VR에서이는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="be963-140">"디버그 표시"를 사용 하도록 설정 하 고 위젯에 항목을 위젯에 추가 하는 것은 위젯 상호 작용 구성 요소가 원하는 대로 작동 하는지 확인 하는 데 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="be963-141">해결 방법은 사용자 지정 원본을 사용 하 고 핸드 레이에서 이벤트 그래프에 raycast를 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="be963-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="be963-142">여기서는 Event Tick에서이를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-142">Here we're calling this from Event Tick:</span></span>

![Event tick의 청사진](images/unreal-umg-img-10.png)

<span data-ttu-id="be963-144">그런 다음, HoloLens 입력에 반응 하는 위젯 상호 작용 구성 요소에 가상 마우스 포인터 이벤트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="be963-145">이 경우 손을 grasped 때 왼쪽 마우스 누르기 이벤트를 보내고 grasped 하지 않을 경우 왼쪽 마우스 릴리스 이벤트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="be963-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![가상 마우스 포인터 이벤트가 추가 된 청사진](images/unreal-umg-img-13.png)

<span data-ttu-id="be963-147">이제 HoloLens 2에 앱을 배포 하는 경우 오른쪽에서 연장 된 손 모양으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be963-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="be963-148">편집 가능한 텍스트 상자와 공중 탭 중 하나를 사용 하는 경우 시스템 키보드는 앞에 표시 되며 텍스트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="be963-149">HoloLens 시스템 키보드에는 Unreal Engine 4.26 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="be963-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="be963-150">또한 앱이 장치에서 실행 되는 경우에만 Unreal 편집기에서 헤드셋으로 스트리밍되는 경우 키보드가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be963-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="be963-151">참고 항목:</span><span class="sxs-lookup"><span data-stu-id="be963-151">See Also:</span></span>
* [<span data-ttu-id="be963-152">Unreal의 UMG 설명서</span><span class="sxs-lookup"><span data-stu-id="be963-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="be963-153">Unreal의 UMG 자습서</span><span class="sxs-lookup"><span data-stu-id="be963-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
