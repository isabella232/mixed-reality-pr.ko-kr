---
title: 손 메뉴
description: 사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 8a8b80843b7a107255a45b11868b0bd29a4e3108
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759459"
---
# <a name="hand-menu"></a><span data-ttu-id="74b3e-104">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="74b3e-104">Hand menu</span></span>

![Ulnar 사이드 위치](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="74b3e-106">손 메뉴는 HoloLens 2에서 가장 고유한 UX 패턴 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="74b3e-107">이를 통해 직접 연결 된 UI를 신속 하 게 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="74b3e-108">언제 든 지 액세스할 수 있으며 쉽게 표시 하 고 숨길 수 있으므로 빠른 작업에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="74b3e-109">아래 목록에서 직접 메뉴를 사용 하는 방법에 대 한 권장 모범 사례를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="74b3e-110">[Mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)의 손 메뉴를 보여 주는 예제 장면을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="74b3e-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="74b3e-111">Best practices</span></span>

<span data-ttu-id="74b3e-112">**단추 수를 작게 유지 합니다.**</span><span class="sxs-lookup"><span data-stu-id="74b3e-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="74b3e-113">직접 잠긴 메뉴와 눈동자 간의 거리가 거의 없고 사용자가 언제 든 지 상대적으로 작은 시각적 영역에 초점을 맞출 수 있는 경향이 있으므로 (시각의 attentional 원뿔 약 10도), 단추 수를 작게 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="74b3e-114">탐색을 기반으로 세 개의 단추가 있는 한 열은 사용자가 시계를 FOV의 중심으로 이동 하는 경우에도 뷰 (FOV)의 모든 콘텐츠를 유지 하 여 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="74b3e-115">**빠른 작업에 손 메뉴 사용**</span><span class="sxs-lookup"><span data-stu-id="74b3e-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="74b3e-116">Arm을 발생 시키고 위치를 유지 하면 arm 피로이 쉽게 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="74b3e-117">짧은 상호 작용을 필요로 하는 메뉴에 대해 직접 잠긴 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="74b3e-118">메뉴가 복잡 하 고 확장 된 상호 작용 시간이 필요한 경우에는 대신 세계 잠금 또는 본문 잠금을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="74b3e-119">**단추/패널 각도**</span><span class="sxs-lookup"><span data-stu-id="74b3e-119">**Button / Panel angle**</span></span>

<span data-ttu-id="74b3e-120">메뉴는 head의 반대 어깨와 중간 방향으로 빌보드를 수행 해야 합니다. 이렇게 하면 자연스럽 게 왼쪽 이동이 반대 방향으로 메뉴와 상호 작용 하 고 단추를 터치 하는 경우에는 불쾌 하거나 불편 한 위치를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="74b3e-121">**단일 전달 또는 실습 작업 지원 고려**</span><span class="sxs-lookup"><span data-stu-id="74b3e-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="74b3e-122">사용자의 손을 항상 사용할 수 있다고 가정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="74b3e-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="74b3e-123">하나 또는 둘 다를 사용할 수 없는 경우 광범위 한 컨텍스트를 고려 하 고 이러한 상황에 대 한 설계 계정이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="74b3e-124">단방향 메뉴를 지원 하기 위해 손을 대칭 이동 하면 (팜 아래로 이동) 메뉴 배치를 왼쪽에서 잠김으로 전환 해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="74b3e-125">직접 사용 하지 않는 시나리오의 경우 음성 명령을 사용 하 여 손 메뉴를 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="74b3e-126">**손목 (시스템 홈 단추) 근처에 단추를 추가 하지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="74b3e-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="74b3e-127">손 메뉴 단추가 홈 단추 가까이에 배치 되 면 손 메뉴와 상호 작용 하는 동안 실수로 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="74b3e-128">크고 복잡 한 UI 컨트롤이 포함 된 손 모양 메뉴</span><span class="sxs-lookup"><span data-stu-id="74b3e-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="74b3e-129">직접 연결 된 메뉴에서 단추나 UI 컨트롤의 수를 제한 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="74b3e-130">이는 많은 수의 UI 요소와의 확장 된 상호 작용이 arm 피로을 일으킬 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="74b3e-131">환경에 많은 메뉴가 필요한 경우 사용자가 메뉴를 쉽게 잠글 수 있는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="74b3e-132">사용자가 손을 벗어나거나 대칭 이동 하는 경우에는 세계 잠금을 해제 한 다음 메뉴를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="74b3e-133">두 번째 방법은 사용자가 메뉴를 직접 가져올 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="74b3e-134">사용자가 메뉴를 놓으면 메뉴는 전 세계 잠금을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="74b3e-135">이러한 방식으로 사용자는 오랜 시간 동안 편안 하 고 안전 하 게 다양 한 UI 요소를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="74b3e-136">메뉴가 세계에서 잠긴 경우 메뉴를 이동 하는 방법을 제공 하 고 더 이상 필요 하지 않은 경우 메뉴를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="74b3e-137">메뉴의 측면 또는 위쪽에 핸들을 제공 하 여 메뉴를 이동 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="74b3e-138">닫기 단추를 추가 하 여 메뉴를 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="74b3e-139">사용자가 사용자에 게 손을 면 메뉴를 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="74b3e-140">또한 거짓 활성화를 방지 하기 위해 사용자가 손을 응시 하도록 요구 하는 것이 좋습니다 (아래 참조).</span><span class="sxs-lookup"><span data-stu-id="74b3e-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="74b3e-141">**유용성 문제를 보여 주는 커다란 메뉴**</span><span class="sxs-lookup"><span data-stu-id="74b3e-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="74b3e-142">**직접 삭제 시 전 세계 잠긴 메뉴**</span><span class="sxs-lookup"><span data-stu-id="74b3e-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="74b3e-143">**수동으로 가져오기 & 전 세계로 가져오기-메뉴 잠금**</span><span class="sxs-lookup"><span data-stu-id="74b3e-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="74b3e-144">False 활성화를 방지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="74b3e-144">How to prevent false activation</span></span>

<span data-ttu-id="74b3e-145">손 메뉴를 트리거하는 이벤트로 palm을 사용 하는 경우 사용자가 의도적으로 (통신 및 개체 조작을 위해) 손을 이동 하 고 실수로 해당 손을 이동 하기 때문에 필요 하지 않은 경우 실수로 나타날 수 있습니다 (가양성).</span><span class="sxs-lookup"><span data-stu-id="74b3e-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="74b3e-146">False 활성화를 줄이려면 손 모양 메뉴를 호출 하는 추가 단계를 추가 합니다 (예: 완전히 열린 손가락 또는 사용자가 의도적으로 의도적으로 gazing).</span><span class="sxs-lookup"><span data-stu-id="74b3e-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="74b3e-147">**평면 팜 필요**</span><span class="sxs-lookup"><span data-stu-id="74b3e-147">**Require Flat Palm**</span></span>

<span data-ttu-id="74b3e-148">평면을 사용 하면 사용자가 환경 내에서 통신 하는 동안 개체 또는 제스처를 조작 하는 경우에 발생할 수 있는 거짓 활성화를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="74b3e-149">**응시 필요**</span><span class="sxs-lookup"><span data-stu-id="74b3e-149">**Require Gaze**</span></span>

<span data-ttu-id="74b3e-150">사용자가 손 모양 (눈에 띄게 또는 헤드 응시)을 사용 하도록 요구 하면 사용자가 손을 사용 하도록 허용 하는 데 조정 가능한 거리 임계값을 사용 하 여 보조 활성화 단계로 직접 주의가 필요 하므로 거짓 활성화를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="74b3e-151">손 메뉴 배치 모범 사례</span><span class="sxs-lookup"><span data-stu-id="74b3e-151">Hand menu placement best practices</span></span>

<span data-ttu-id="74b3e-152">인간 분석에서 ulnar nerve은 ulna 뼈 근처에서 실행 되는 nerve입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="74b3e-153">Ulna는 엘보우에서 가장 작은 손가락으로 확장 되는 긴 뼈가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="74b3e-154">다음은 탐색를 기반으로 하는 두 가지 권장 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="74b3e-155">![팜 내부의 ulnar 측면 위치](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="74b3e-156">**야자수 내부에 있는 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="74b3e-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="74b3e-157">이 위치는 서로 겹치지 않으므로 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="74b3e-158">정확한 직접 검색 및 추적에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="74b3e-159">![위쪽의 ulnar 측면 위치](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="74b3e-160">**2. 전 사랑 Nar**</span><span class="sxs-lookup"><span data-stu-id="74b3e-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="74b3e-161">이 위치는 손 메뉴와 상호 작용 하는 데 너무 많은 arm을 발생 시킬 필요가 없기 때문에 사용자에 게 친숙 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="74b3e-162">**메뉴를** palm 위에 배치 하 고 ulnar 팜 내에서 단추를 정렬 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="74b3e-163">최적의 단추 크기에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="74b3e-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="74b3e-164">기술적인 이유로이 위치에는 하나의 필수 구현이 권장 됩니다. 개발자는 사용자의 반대 바늘이 가까이와 상호 작용할 때 메뉴를 고정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="74b3e-165">이렇게 하면 겹치는 jitteriness 방지 하 고 더 빠르게 단추를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="74b3e-166">HoloLens 2 카메라는 서로 분리 된 경우를 정확 하 게 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="74b3e-167">모든 겹치는 손을 통해 고정 위치에서 바로 메뉴가 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="74b3e-168">권장 되지 않는 메뉴 위치</span><span class="sxs-lookup"><span data-stu-id="74b3e-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="74b3e-169">다른 메뉴 레이아웃 및 위치를 사용 하 여 사용자 연구를 완료 했습니다. 다음 메뉴 위치를 사용 **하지 않는 것이 좋습니다**. 아래 각 연구의 단점을 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="74b3e-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="74b3e-170">![Arm 위](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="74b3e-171">**Arm 위**</span><span class="sxs-lookup"><span data-stu-id="74b3e-171">**Above the arm**</span></span><br>
        <span data-ttu-id="74b3e-172">1-좋은 수동 추적을 유지 하기 어렵게 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="74b3e-173">2-비 자연으로 인해 사용자 피로 발생</span><span class="sxs-lookup"><span data-stu-id="74b3e-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="74b3e-174">![손가락 위](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="74b3e-175">**손가락 위**</span><span class="sxs-lookup"><span data-stu-id="74b3e-175">**Above fingers**</span></span><br>
        <span data-ttu-id="74b3e-176">피로 오랫동안 보유 하 고 있기 때문에 1 손을.</span><span class="sxs-lookup"><span data-stu-id="74b3e-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="74b3e-177">2-인덱스 및 가운데 손가락에 대 한 추적 문제</span><span class="sxs-lookup"><span data-stu-id="74b3e-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="74b3e-178">![센터 팜 위](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="74b3e-179">**위쪽-가운데 palm**</span><span class="sxs-lookup"><span data-stu-id="74b3e-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="74b3e-180">겹친 실습으로 인해 1 손으로 추적 하는 문제</span><span class="sxs-lookup"><span data-stu-id="74b3e-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="74b3e-181">2 손 피로 메뉴와 상호 작용 하는 데 오랜 시간이 걸림</span><span class="sxs-lookup"><span data-stu-id="74b3e-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="74b3e-182">![Top Fingertip ](images/TopFingerTip.gif) **top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="74b3e-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="74b3e-183">1 손을 추적 하는 문제</span><span class="sxs-lookup"><span data-stu-id="74b3e-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="74b3e-184">2 손을 피로 정상 상태를 유지 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="74b3e-185">3-손가락 사이의 제한 된 공간으로 인해 실수로 다른 손가락으로 단추를 누르는 문제</span><span class="sxs-lookup"><span data-stu-id="74b3e-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="74b3e-186">![Arm의 후면](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="74b3e-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="74b3e-187">**Arm의 후면**</span><span class="sxs-lookup"><span data-stu-id="74b3e-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="74b3e-188">1-실수로 홈 단추를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="74b3e-189">2-자연 또는 편안한 위치가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="74b3e-190">Unity 용 MRTK (Mixed Reality Toolkit)의 손 모양 메뉴</span><span class="sxs-lookup"><span data-stu-id="74b3e-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="74b3e-191">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 손 메뉴에 대 한 스크립트와 예제 장면을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="74b3e-192">HandConstraintPalmUp 해결 프로그램 스크립트를 사용 하면 다양 한 구성 가능한 옵션을 통해 개체를 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="74b3e-193">MRTK의 손 메뉴 예제에는 거짓 활성화를 방지 하기 위한 flat palm 및 응시 요구 사항과 같은 유용한 옵션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="74b3e-194">손 메뉴 설명서</span><span class="sxs-lookup"><span data-stu-id="74b3e-194">Hand Menu Documentations</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)
* [<span data-ttu-id="74b3e-195">손 모양 메뉴 예제 장면</span><span class="sxs-lookup"><span data-stu-id="74b3e-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="74b3e-196">MRTK 예제 허브 앱을 사용 하 여 HoloLens 2에서 직접 메뉴 예제를 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74b3e-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="74b3e-197">MRTK 예제 허브의 손 메뉴 장면</span><span class="sxs-lookup"><span data-stu-id="74b3e-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="74b3e-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74b3e-198">See also</span></span>

* [<span data-ttu-id="74b3e-199">커서</span><span class="sxs-lookup"><span data-stu-id="74b3e-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="74b3e-200">손 광선</span><span class="sxs-lookup"><span data-stu-id="74b3e-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="74b3e-201">Button</span><span class="sxs-lookup"><span data-stu-id="74b3e-201">Button</span></span>](button.md)
* [<span data-ttu-id="74b3e-202">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="74b3e-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="74b3e-203">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="74b3e-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="74b3e-204">조작</span><span class="sxs-lookup"><span data-stu-id="74b3e-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="74b3e-205">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="74b3e-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="74b3e-206">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="74b3e-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="74b3e-207">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="74b3e-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="74b3e-208">음성 명령</span><span class="sxs-lookup"><span data-stu-id="74b3e-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="74b3e-209">키보드</span><span class="sxs-lookup"><span data-stu-id="74b3e-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="74b3e-210">Tooltip</span><span class="sxs-lookup"><span data-stu-id="74b3e-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="74b3e-211">슬레이트</span><span class="sxs-lookup"><span data-stu-id="74b3e-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="74b3e-212">슬라이더</span><span class="sxs-lookup"><span data-stu-id="74b3e-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="74b3e-213">셰이더</span><span class="sxs-lookup"><span data-stu-id="74b3e-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="74b3e-214">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="74b3e-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="74b3e-215">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="74b3e-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="74b3e-216">표면 자성</span><span class="sxs-lookup"><span data-stu-id="74b3e-216">Surface magnetism</span></span>](surface-magnetism.md)
