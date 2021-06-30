---
title: 용어
description: MRTK의 다른 입력 시스템 용어
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 입력,
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121461"
---
# <a name="input-system"></a><span data-ttu-id="74404-104">입력 시스템</span><span class="sxs-lookup"><span data-stu-id="74404-104">Input system</span></span>

<span data-ttu-id="74404-105">입력 시스템은 MRTK에서 제공 하는 모든 기능 중에서 가장 큰 시스템 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-105">The input system is one of the largest systems out of all features offered by the MRTK.</span></span>
<span data-ttu-id="74404-106">따라서 도구 키트 내의 많은 항목이이를 기반으로 작성 됩니다 (포인터, 포커스, prefabs).</span><span class="sxs-lookup"><span data-stu-id="74404-106">So many things within the toolkit build on top of it (pointers, focus, prefabs).</span></span> <span data-ttu-id="74404-107">입력 시스템 내의 코드는 플랫폼 간 잡기 및 회전과 같은 자연 스러운 상호 작용을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-107">The code within the input system is what allows for natural interactions like grab and rotate across platforms.</span></span>

<span data-ttu-id="74404-108">입력 시스템에는 다음과 같은 고유한 용어를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-108">The input system has some of its own terminology that are worth defining:</span></span>

- <span data-ttu-id="74404-109">**데이터 공급자**</span><span class="sxs-lookup"><span data-stu-id="74404-109">**Data providers**</span></span>

    <span data-ttu-id="74404-110">입력 프로필의 입력 설정에는 데이터 공급자 라고 하는 엔터티에 대 한 참조가 있습니다. 이러한 항목을 설명 하는 다른 단어는 장치 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-110">The input settings in the input profile have references to entities known as data providers - another word that describes these are device managers.</span></span> <span data-ttu-id="74404-111">이는 특정 기본 시스템과 상호 작용 하 여 MRTK 입력 시스템을 확장 하는 작업을 포함 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-111">These are components whose job is to extend the MRTK input system by interfacing with a specific underlying system.</span></span> <span data-ttu-id="74404-112">공급자의 예로는 Windows Mixed Reality 공급자가 있습니다 .이 공급자는 기본 Windows Mixed Reality Api와 통신 하 고 해당 Api의 데이터를 아래의 MRTK 관련 입력 개념으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-112">An example of a provider is the Windows Mixed Reality provider, whose job it is to talk with the underlying Windows Mixed Reality APIs and then translate the data from those APIs into MRTK-specific input concepts below.</span></span> <span data-ttu-id="74404-113">또 다른 예는 OpenVR 공급자 (해당 작업은 Unity로 추상화 된 OpenVR 버전의 OpenVR와 통신 하 고 해당 데이터를 MRTK 입력 개념으로 변환)입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-113">Another example would be the OpenVR provider (whose job it is to talk to Unity-abstracted version of OpenVR APIs and then translate that data into MRTK input concepts).</span></span>

- <span data-ttu-id="74404-114">**컨트롤러**</span><span class="sxs-lookup"><span data-stu-id="74404-114">**Controller**</span></span>

    <span data-ttu-id="74404-115">실제 컨트롤러에 대 한 표현으로,이 컨트롤러는 사용 하는 것이 좋습니다. 즉, 사용 되는 경우에는 6 자유도이 고, 제스처를 지 원하는 경우에는 HoloLens 1 스타일 손을 사용 하 고, 완전히 구분 되는 손 모양, 도약 동작 컨트롤러 등</span><span class="sxs-lookup"><span data-stu-id="74404-115">A representation of a physical controller (whether it's a 6-degree-of-freedom controller, a HoloLens 1-style hand with gesture support, a fully articulated hand, a leap motion controller, etc.).</span></span> <span data-ttu-id="74404-116">컨트롤러는 장치 관리자에 의해 생성 됩니다. 즉, WMR 장치 관리자는 컨트롤러를 생성 하 고 해당 되는 것으로 간주 되는 경우에는 해당 수명 주기를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-116">Controllers are spawned by device managers (i.e. the WMR device manager will spawn a controller and manage its lifetime when it sees an articulated hand coming into existence).</span></span>

- <span data-ttu-id="74404-117">**포인터**</span><span class="sxs-lookup"><span data-stu-id="74404-117">**Pointer**</span></span>

    <span data-ttu-id="74404-118">컨트롤러는 포인터를 사용 하 여 게임 개체와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-118">Controllers use pointers to interact with game objects.</span></span> <span data-ttu-id="74404-119">예를 들어 근거리 상호 작용 포인터는 손 (컨트롤러)이 ' 근접 한 상호 작용 '을 지 원하는 것으로 광고 하는 개체와 가까운 경우를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-119">For example, the near interaction pointer is responsible for detecting when the hand (which is a controller) is close to objects that advertise themselves as supporting 'near interaction'.</span></span> <span data-ttu-id="74404-120">포인터에 대 한 다른 예는 먼 raycasts를 사용 하는 teleportation 또는 far 포인터 (즉, 셸 손 광선 포인터)입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-120">Other examples for pointers are teleportation or far pointers (i.e. the shell hand ray pointer) that use far raycasts to engage with content that is longer than arms-length from the user.</span></span>

    <span data-ttu-id="74404-121">포인터는 장치 관리자에 의해 생성 된 다음 입력 소스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74404-121">Pointers are created by the device manager and then attached to an input source.</span></span> <span data-ttu-id="74404-122">컨트롤러에 대 한 모든 포인터를 가져오려면 다음을 수행 합니다. `controller.InputSource.Pointers`</span><span class="sxs-lookup"><span data-stu-id="74404-122">To get all of the pointers for a controller, do: `controller.InputSource.Pointers`</span></span>

    <span data-ttu-id="74404-123">컨트롤러는 여러 포인터와 동시에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-123">Note that a controller can be associated with many different pointers at the same time.</span></span> <span data-ttu-id="74404-124">이 작업이 비정상 상태로 미치는지를 않도록 하기 위해 활성화 될 수 있는 포인터를 제어 하는 포인터 mediator 있습니다. 예를 들어 근처의 상호 작용이 감지 되 면 mediator는 먼 상호 작용 포인터를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-124">In order to ensure that this doesn't devolve into chaos, there is a pointer mediator which controls which pointers are allowed to be active (for example, the mediator will disable far interaction pointers when near interaction is detected).</span></span>

- <span data-ttu-id="74404-125">**주의**</span><span class="sxs-lookup"><span data-stu-id="74404-125">**Focus**</span></span>

    <span data-ttu-id="74404-126">포인터 이벤트는 **포커스** 로 개체에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74404-126">Pointer events are sent to objects in **focus**.</span></span> <span data-ttu-id="74404-127">포커스 선택은 포인터 유형에 따라 달라 집니다. 손 모양 포인터는 raycasts를 사용 하는 반면, poke 포인터는 spherecasts를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-127">Focus selection will vary by pointer type; a hand ray pointer will use raycasts, while a poke pointer will use spherecasts.</span></span> <span data-ttu-id="74404-128">개체는 포커스를 받을 IMixedRealityFocusHandler을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-128">An object must implement IMixedRealityFocusHandler to receive focus.</span></span> <span data-ttu-id="74404-129">개체를 전역적으로 등록 하 여 필터링 되지 않은 포인터 이벤트를 받을 수 있지만이 방법은 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-129">It's possible to globally register an object to receive unfiltered pointer events, but this approach is not recommended.</span></span>

    <span data-ttu-id="74404-130">포커스가 있는 개체를 업데이트 하는 구성 요소는 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span><span class="sxs-lookup"><span data-stu-id="74404-130">The component that updates which objects are in focus is the [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span></span>

- <span data-ttu-id="74404-131">**커서**</span><span class="sxs-lookup"><span data-stu-id="74404-131">**Cursor**</span></span>

    <span data-ttu-id="74404-132">포인터 상호 작용에 대 한 추가 시각적 신호를 제공 하는 포인터와 연결 된 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-132">An entity associated with a pointer that gives additional visual cues around pointer interaction.</span></span> <span data-ttu-id="74404-133">예를 들어 FingerCursor는 손가락 주위에 고리를 렌더링 하 고 손가락이 ' near interactable ' 개체에 근접 한 경우 해당 링을 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-133">For example, the FingerCursor will render a ring around your finger and may rotate that ring when your finger is close to 'near interactable' objects.</span></span> <span data-ttu-id="74404-134">포인터는 한 번에 하나의 커서와 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-134">A pointer can be associated with a single cursor at time.</span></span>

- <span data-ttu-id="74404-135">**상호 작용 및 조작**</span><span class="sxs-lookup"><span data-stu-id="74404-135">**Interaction and Manipulation**</span></span>

    <span data-ttu-id="74404-136">개체에는 상호 작용 또는 조작 스크립트를 사용 하 여 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74404-136">Objects can be tagged with an interaction or manipulation script.</span></span> <span data-ttu-id="74404-137">또는와 같은을 통해이 작업을 수행할 수 있습니다 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="74404-137">This may be via a [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable), or something like [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)/[`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

    <span data-ttu-id="74404-138">예를 들어, NearInteractionGrabbable 및 NearInteractionTouchable는 특정 포인터 (특히 상호 작용 포인터 근처)에서 포커스를 받을 수 있는 개체를 알 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-138">For example, NearInteractionGrabbable and NearInteractionTouchable allow for certain pointers (especially   near interaction pointers) to know which objects can be focused on.</span></span>

    <span data-ttu-id="74404-139">Interactable 및 ManipulationHandler는 포인터 이벤트를 수신 하 여 UI 시각적 개체를 수정 하거나 게임 개체를 이동/배율 조정/회전 하는 구성 요소의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="74404-139">Interactable and ManipulationHandler are examples of components that listen to pointer events to modify   UI visuals or move/scale/rotate game objects.</span></span>

<span data-ttu-id="74404-140">아래 이미지는 MRTK 입력 스택의 상위 수준 빌드 (상향식)를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="74404-140">The image below captures the high level build up (from bottom up) of the MRTK input stack:</span></span>

![입력 시스템 다이어그램](../features/images/input/MRTK_InputSystem.png)
