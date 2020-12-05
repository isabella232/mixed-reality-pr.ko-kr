---
title: 진짜의 HP 반향 G2 컨트롤러
description: OpenXR 및 SteamVR에서 HP 반향 G2 컨트롤러를 사용 하는 방법에 대 한 지침
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 419f5b803a6abb2b19080807ef9f403b96758683
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609594"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="aa01f-104">진짜의 HP 반향 G2 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="aa01f-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="aa01f-105">시작</span><span class="sxs-lookup"><span data-stu-id="aa01f-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa01f-106">Hp 동작 컨트롤러 플러그 인에 액세스 하려면 unreal Engine 4.26 및 OpenXR 또는 SteamVR가 필요 합니다. HP 반향 G2 컨트롤러를 사용 하 여 작업 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="aa01f-107">기존 OpenXR 앱 포팅</span><span class="sxs-lookup"><span data-stu-id="aa01f-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="aa01f-108">HP Mixed Reality 컨트롤러의 게임에 컨트롤러 바인딩이 없으면 OpenXR 런타임은 기존 바인딩을 활성 컨트롤러로 다시 매핑하려는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will try to remap existing bindings to the active controller.</span></span>  <span data-ttu-id="aa01f-109">이 경우 게임에는 Microsoft의 터치 바인딩과 HP 혼합 현실 컨트롤러 바인딩이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![컨트롤러 바인딩이 없을 때 기존 바인딩 다시 매핑](images/reverb-g2-img-04.png)

<span data-ttu-id="aa01f-111">이벤트는 계속 발생 하지만, 게임에서 오른쪽 메뉴 단추와 같은 컨트롤러 특정 바인딩을 사용 해야 하는 경우 HP 혼합 현실 상호 작용 프로필을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-111">The events will still fire, but if the game needs to make use of controller-specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="aa01f-112">여러 장치를 보다 효율적으로 지원 하기 위해 작업 마다 여러 컨트롤러 바인딩을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![여러 컨트롤러 바인딩 사용](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="aa01f-114">입력 작업 매핑 추가</span><span class="sxs-lookup"><span data-stu-id="aa01f-114">Adding input action mappings</span></span> 

<span data-ttu-id="aa01f-115">새 작업을 정의 하 고 HP Mixed Reality 컨트롤러 섹션의 키 누름 중 하나에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![새 작업 및 매핑 정의](images/reverb-g2-img-02.png)

<span data-ttu-id="aa01f-117">HP 반향 G2 컨트롤러에는 "아웃 축" 바인딩을 사용 하는 축 매핑에서 사용할 수 있는 아날로그 그립도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="aa01f-118">그립 단추가 완전히 눌린 상태에서 작업 매핑에 사용 해야 하는 별도의 꽉 binding이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-118">There's a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![아웃 축 바인딩 사용](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="aa01f-120">입력 이벤트 추가</span><span class="sxs-lookup"><span data-stu-id="aa01f-120">Adding input events</span></span>

<span data-ttu-id="aa01f-121">청사진을 마우스 오른쪽 단추로 클릭 하 고 입력 시스템에서 새 작업 이름을 검색 하 여 이러한 동작에 대 한 이벤트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-121">Right-click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="aa01f-122">여기서 청사진은 현재 단추 및 축 상태를 출력 하는 인쇄 문자열이 있는 이벤트에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa01f-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![청사진 이벤트에 응답 하 고 현재 단추 및 축 상태를 출력 합니다.](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="aa01f-124">입력 사용</span><span class="sxs-lookup"><span data-stu-id="aa01f-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="aa01f-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa01f-125">See also</span></span>
* [<span data-ttu-id="aa01f-126">SteamVR 입력</span><span class="sxs-lookup"><span data-stu-id="aa01f-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="aa01f-127">Windows Mixed Reality에서 SteamVR 사용</span><span class="sxs-lookup"><span data-stu-id="aa01f-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="aa01f-128">Unreal Player 카메라</span><span class="sxs-lookup"><span data-stu-id="aa01f-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)