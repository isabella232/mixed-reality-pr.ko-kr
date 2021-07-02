---
title: Near 메뉴
description: MRTK의 메뉴 형식 근처에서 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 주변 메뉴,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175654"
---
# <a name="near-menu"></a><span data-ttu-id="0d4d5-104">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="0d4d5-104">Near menu</span></span>

![Near 메뉴](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="0d4d5-106">Near Menu는 단추나 다른 UI 구성 요소의 컬렉션을 제공 하는 UX 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="0d4d5-107">사용자의 본문 주위에 떠 있고 언제 든 지 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="0d4d5-108">사용자와 느슨하게 연결 되어 있으므로 대상 콘텐츠와의 상호 작용을 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="0d4d5-109">사용자는 ' 고정 ' 단추를 사용 하 여 전 세계의 메뉴 잠금/잠금 해제를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="0d4d5-110">메뉴를 grabbed 하 고 특정 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="0d4d5-111">상호 작용 동작</span><span class="sxs-lookup"><span data-stu-id="0d4d5-111">Interaction behavior</span></span>

- <span data-ttu-id="0d4d5-112">**태그** 표시:이 메뉴는 사용자를 따르며 가까운 상호 작용을 위해 사용자의 30-60cm 범위 내에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="0d4d5-113">**고정**: ' 핀 ' 단추를 사용 하 여 메뉴를 전 세계에서 잠그고 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="0d4d5-114">**잡기 및 이동**: 메뉴는 항상 grabbable 및 이동 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="0d4d5-115">이전 상태와 관계 없이 grabbed 및 해제 된 경우 메뉴가 고정 (세계 잠금) 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="0d4d5-116">Grabbable 영역에 대 한 시각적 단서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="0d4d5-117">이는 가까이에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="0d4d5-118">Prefabs</span><span class="sxs-lookup"><span data-stu-id="0d4d5-118">Prefabs</span></span>

<span data-ttu-id="0d4d5-119">Near 메뉴 prefabs는 MRTK의 다양 한 구성 요소를 사용 하 여 거의 상호 작용 하는 메뉴를 만드는 방법을 보여 주기 위해 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="0d4d5-120">**NearMenu2x4. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="0d4d5-121">**NearMenu3x1. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="0d4d5-122">**NearMenu3x2. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="0d4d5-123">**NearMenu3x3. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="0d4d5-124">**NearMenu4x1. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="0d4d5-125">**NearMenu4x2. prefab**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="0d4d5-126">장면 예</span><span class="sxs-lookup"><span data-stu-id="0d4d5-126">Example scene</span></span>

<span data-ttu-id="0d4d5-127">장면에서 메뉴 prefabs 근처의 예제를 찾을 수 있습니다 `NearMenuExamples` .</span><span class="sxs-lookup"><span data-stu-id="0d4d5-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="0d4d5-128">구조체</span><span class="sxs-lookup"><span data-stu-id="0d4d5-128">Structure</span></span>

<span data-ttu-id="0d4d5-129">Near 메뉴 prefabs 다음 MRTK 구성 요소를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="0d4d5-130">[**PressableButtonHoloLens2**](button.md) prefab</span><span class="sxs-lookup"><span data-stu-id="0d4d5-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="0d4d5-131">[**Grid 개체 컬렉션**](object-collection.md): 모눈의 여러 단추 레이아웃</span><span class="sxs-lookup"><span data-stu-id="0d4d5-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="0d4d5-132">[**조작 처리기**](manipulation-handler.md): 메뉴를 잡고 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="0d4d5-133">[**RadialView 해 찾기**](solvers/solver.md): 팔 로우 하기 (태그 동반) 동작</span><span class="sxs-lookup"><span data-stu-id="0d4d5-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![메뉴 Prefab 가까이](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="0d4d5-135">사용자 지정 방법</span><span class="sxs-lookup"><span data-stu-id="0d4d5-135">How to customize</span></span>

<span data-ttu-id="0d4d5-136">**1. 단추 추가/제거**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="0d4d5-137">개체 아래에서 `ButtonCollection` 단추를 추가 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="0d4d5-138">**2. 그리드 개체 컬렉션 업데이트**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="0d4d5-139">`Update Collection`개체의 검사기에서 단추를 클릭 `ButtonCollection` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="0d4d5-140">그리드 레이아웃이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="0d4d5-141">Grid 개체 컬렉션의 속성을 사용 하 여 행 수를 구성할 수 있습니다 `Rows` .</span><span class="sxs-lookup"><span data-stu-id="0d4d5-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="0d4d5-142">**3. backplate 크기 조정**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="0d4d5-143">개체의 크기를 조정 `Quad` 합니다 `Backplate` .</span><span class="sxs-lookup"><span data-stu-id="0d4d5-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="0d4d5-144">Backplate의 너비와 높이는 이어야 합니다 `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="0d4d5-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="0d4d5-145">예를 들어 3 개의 x 단추가 있는 경우 backplate의 너비는이 `0.032 * 4` 고 높이는 `0.032 * 3` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="0d4d5-146">Unity의 필드에이 식을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="0d4d5-147">HoloLens 2 단추의 기본 크기는 3.2 x 3.2 cm (0.032 m)입니다.</span><span class="sxs-lookup"><span data-stu-id="0d4d5-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="0d4d5-148">참조</span><span class="sxs-lookup"><span data-stu-id="0d4d5-148">See also</span></span>

- [<span data-ttu-id="0d4d5-149">**단추**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="0d4d5-150">**범위 제어**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="0d4d5-151">**슬라이더**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="0d4d5-152">**Grid 개체 컬렉션**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="0d4d5-153">**조작 처리기**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="0d4d5-154">**RadialView 해 찾기**</span><span class="sxs-lookup"><span data-stu-id="0d4d5-154">**RadialView Solver**</span></span>](solvers/solver.md)
