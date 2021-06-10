---
title: 손 메뉴
description: 손 메뉴를 사용하면 자주 사용되는 함수에 대해 직접 연결된 UI를 빠르게 가져올 수 있습니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600332"
---
# <a name="hand-menu"></a><span data-ttu-id="8567e-104">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="8567e-104">Hand menu</span></span>

![Ulnar 측면 손 위치](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="8567e-106">손 메뉴는 HoloLens 2 가장 고유한 UX 패턴 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="8567e-107">이를 통해 직접 연결된 UI를 신속하게 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="8567e-108">언제든지 액세스할 수 있고 쉽게 표시하고 숨길 수 있기 때문에 빠른 작업에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="8567e-109">아래 목록에서 손 메뉴를 사용하기 위한 권장 모범 사례를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="8567e-110">[MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)에서 손 메뉴를 보여주는 예제 장면도 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-110">You can also find an example scene demonstrating the hand menu in [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="8567e-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="8567e-111">Best practices</span></span>

<span data-ttu-id="8567e-112">**단추 수를 작게 유지**</span><span class="sxs-lookup"><span data-stu-id="8567e-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="8567e-113">손으로 잠긴 메뉴와 눈 사이의 근접한 거리와 사용자가 언제든지 상대적으로 작은 시각적 영역에 집중하는 경향이 있기 때문에(시각의 주의력 원통은 약 10도임) 단추 수를 작게 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="8567e-114">탐색에 따라 세 개의 단추가 있는 하나의 열은 사용자가 FOV의 가운데로 손을 이동하는 경우에도 모든 콘텐츠를 FOV(보기 필드) 내에 유지하여 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="8567e-115">**빠른 작업에 손 메뉴 사용**</span><span class="sxs-lookup"><span data-stu-id="8567e-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="8567e-116">Arm을 발생시키고 위치를 유지 관리하면 손쉽게 암이 화를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="8567e-117">짧은 상호 작용이 필요한 메뉴에 대해 손으로 잠긴 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="8567e-118">메뉴가 복잡하고 상호 작용 시간이 길어야 하는 경우 세계 잠금 또는 본문 잠금을 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="8567e-119">**단추/패널 각도**</span><span class="sxs-lookup"><span data-stu-id="8567e-119">**Button / Panel angle**</span></span>

<span data-ttu-id="8567e-120">메뉴는 머리의 반대쪽 위를 향해야 합니다. 이렇게 하면 자연스러운 손 이동이 반대쪽 손으로 메뉴와 상호 작용할 수 있으며 단추를 터치할 때 불편하거나 머리가 눌려지는 위치를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="8567e-121">**한 손 또는 손 없는 작업을 지원하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="8567e-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="8567e-122">사용자의 손을 항상 사용할 수 있다고 가정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8567e-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="8567e-123">한 손 또는 양손을 사용할 수 없는 경우 광범위한 컨텍스트를 고려하고 이러한 상황에 맞게 디자인 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="8567e-124">한 손 메뉴를 지원하려면 손을 대칭 놓을 때 메뉴 배치를 손 잠금에서 세계 잠금으로 전환해 볼 수 있습니다(손 아래로 이동합니다).</span><span class="sxs-lookup"><span data-stu-id="8567e-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="8567e-125">핸즈프리 시나리오의 경우 음성 명령을 사용하여 손 메뉴를 호출하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="8567e-126">**집 근처에 단추를 추가하지 않습니다(시스템 홈 단추).**</span><span class="sxs-lookup"><span data-stu-id="8567e-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="8567e-127">손 메뉴 단추가 홈 단추에 너무 가까이 배치되면 손 메뉴와 상호 작용하는 동안 실수로 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="8567e-128">크고 복잡한 UI 컨트롤이 있는 손 메뉴</span><span class="sxs-lookup"><span data-stu-id="8567e-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="8567e-129">직접 연결된 메뉴에서 단추 또는 UI 컨트롤의 수를 제한하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="8567e-130">이는 많은 수의 UI 요소와 확장된 상호 작용으로 인해 암겨질 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="8567e-131">사용자 경험에 큰 메뉴가 필요한 경우 사용자가 메뉴를 쉽게 잠글 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="8567e-132">권장되는 한 가지 방법은 손을 떨어지거나 사용자와 떨어져 있을 때 메뉴를 세계 잠금으로 잠그는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="8567e-133">두 번째 방법은 사용자가 다른 손으로 메뉴를 직접 잡도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="8567e-134">사용자가 메뉴를 놓으면 메뉴가 세계 잠금으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="8567e-135">이러한 방식으로 사용자는 오랜 시간 동안 편리하고 자신 있게 다양한 UI 요소와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="8567e-136">메뉴가 세계로 잠겨 있는 경우 메뉴를 이동하는 방법을 제공하고 더 이상 필요하지 않은 경우 메뉴를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="8567e-137">메뉴의 측면 또는 위쪽에 핸들을 제공하여 메뉴를 이동 가능하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="8567e-138">메뉴를 닫을 수 있도록 닫기 단추를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="8567e-139">사용자 손을 사용할 때 메뉴가 다시 연결되도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="8567e-140">또한 잘못된 활성화를 방지하기 위해 사용자가 손을 응시하도록 요구하는 것이 좋습니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="8567e-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="8567e-141">**유용성 문제를 보여 주는 큰 메뉴**</span><span class="sxs-lookup"><span data-stu-id="8567e-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="8567e-142">**손 놓기에서 세계 잠겨 있는 메뉴**</span><span class="sxs-lookup"><span data-stu-id="8567e-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="8567e-143">**수동 잡기 & 메뉴를 세계 잠금으로 끌어오기**</span><span class="sxs-lookup"><span data-stu-id="8567e-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="8567e-144">잘못된 활성화를 방지하는 방법</span><span class="sxs-lookup"><span data-stu-id="8567e-144">How to prevent false activation</span></span>

<span data-ttu-id="8567e-145">손 메뉴를 트리거하는 이벤트로 손 업을 사용하는 경우 사용자가 의도적으로(통신 및 개체 조작을 위해) 손을 움직이기 때문에(가양성) 필요하지 않을 때 실수로 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="8567e-146">거짓 활성화를 줄이려면 손끝 이벤트 외에 손 메뉴를 호출하는 추가 단계를 추가합니다(예: 완전히 열린 손가락 또는 사용자가 의도적으로 손을 잡고 있음).</span><span class="sxs-lookup"><span data-stu-id="8567e-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="8567e-147">**플랫 팜 필요**</span><span class="sxs-lookup"><span data-stu-id="8567e-147">**Require Flat Palm**</span></span>

<span data-ttu-id="8567e-148">사용자가 환경 내에서 통신하는 동안 개체 또는 제스처를 조작할 때 발생할 수 있는 거짓 활성화를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="8567e-149">**응시 필요**</span><span class="sxs-lookup"><span data-stu-id="8567e-149">**Require Gaze**</span></span>

<span data-ttu-id="8567e-150">사용자가 시선 응시 또는 머리 응시를 사용하여 손을 응시하도록 요구하면 보조 활성화 단계(사용자의 편의를 위해 튜닝 가능한 거리 임계값 사용)로 주의를 집중해야 하기 때문에 잘못된 활성화를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="8567e-151">손 메뉴 배치 모범 사례</span><span class="sxs-lookup"><span data-stu-id="8567e-151">Hand menu placement best practices</span></span>

<span data-ttu-id="8567e-152">인체 구조에서 ulnar 게는 ulna 게 근처에서 실행되는 게아입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="8567e-153">ulna는 눈송이에서 가장 작은 손가락으로 늘이는 포아름에 있는 긴 웜입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="8567e-154">다음은 탐색을 기반으로 하는 두 가지 권장 배치입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8567e-155">![손 속의 Ulnar 측면 위치](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="8567e-156">**A. 집 안의 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="8567e-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="8567e-157">손은 서로 겹치지 않으므로 이 위치는 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="8567e-158">이는 정확한 손 감지 및 추적에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8567e-159">![Ulnar의 손 위 위치](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="8567e-160">**B. 위의 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="8567e-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="8567e-161">이 위치는 손 메뉴와 상호 작용하기 위해 손을 너무 많이 올리지 않아도 되므로 사용자에게 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="8567e-162">**13cm** 메뉴를 손만 위에 배치하고 ulnar 손무한 안에 단추를 맞추는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="8567e-163">최적의 단추 크기에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="8567e-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="8567e-164">기술적인 이유로 한 가지 필수 구현을 사용하여 이 위치를 권장합니다. 사용자의 반대쪽 손과 상호 작용에 가까워지면 개발자가 메뉴를 고정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="8567e-165">이렇게 하면 겹치는 손의 지터링을 방지하고 단추의 더 빠른 대상 지정을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="8567e-166">HoloLens 2 카메라는 서로 분리된 경우 손을 정확하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="8567e-167">손을 겹치면 손 메뉴가 앵커 위치에서 벗어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="8567e-168">권장되지 않는 메뉴 위치</span><span class="sxs-lookup"><span data-stu-id="8567e-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="8567e-169">다양한 메뉴 레이아웃 및 위치로 사용자 조사를 완료했습니다. 다음 메뉴 위치는 **권장되지 않습니다.** 아래의 각 연구 단점을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8567e-170">![위쪽 암](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="8567e-171">**암 위**</span><span class="sxs-lookup"><span data-stu-id="8567e-171">**Above the arm**</span></span><br>
        <span data-ttu-id="8567e-172">1 - 손 추적을 유지하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="8567e-173">2 - 자연스럽지 않은 위치로 인해 사용자의 불편을 유발합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8567e-174">![위 손가락](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="8567e-175">**위 손가락**</span><span class="sxs-lookup"><span data-stu-id="8567e-175">**Above fingers**</span></span><br>
        <span data-ttu-id="8567e-176">1 - 오랜 시간 동안 손을 내밀기 때문에 손의 아유</span><span class="sxs-lookup"><span data-stu-id="8567e-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="8567e-177">2 - 인덱스 및 가운데 손가락의 손 추적 문제</span><span class="sxs-lookup"><span data-stu-id="8567e-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8567e-178">![가운데 손대기 위](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="8567e-179">**가운데 위 손살마**</span><span class="sxs-lookup"><span data-stu-id="8567e-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="8567e-180">1 - 손 겹침으로 인한 손 추적 문제</span><span class="sxs-lookup"><span data-stu-id="8567e-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="8567e-181">2 - 메뉴와 상호 작용하기 위해 오랫동안 손을 붙들고 있기 때문에 손의 기운</span><span class="sxs-lookup"><span data-stu-id="8567e-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8567e-182">![위쪽 손가락 설명 ](images/TopFingerTip.gif) **위쪽 손끝**</span><span class="sxs-lookup"><span data-stu-id="8567e-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="8567e-183">1 - 손 추적 문제</span><span class="sxs-lookup"><span data-stu-id="8567e-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="8567e-184">2 - 정상 태세 위에 손을 붙들지 않도록 손의심</span><span class="sxs-lookup"><span data-stu-id="8567e-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="8567e-185">3 - 손가락 사이의 공간이 제한되어 실수로 다른 손가락으로 단추를 누르는 문제</span><span class="sxs-lookup"><span data-stu-id="8567e-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8567e-186">![Arm의 뒷면](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8567e-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="8567e-187">**암(arm) 뒷면**</span><span class="sxs-lookup"><span data-stu-id="8567e-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="8567e-188">1 - 실수로 홈 단추를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="8567e-189">2 - 자연스럽거나 편안한 위치가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8567e-190">Unity용 MRTK(Mixed Reality Toolkit)의 손 메뉴</span><span class="sxs-lookup"><span data-stu-id="8567e-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8567e-191">**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 손 메뉴에 대한 스크립트 및 예제 장면을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="8567e-192">HandConstraintPalmUp 해결기 스크립트를 사용하면 다양한 구성 가능한 옵션을 사용하여 개체를 손으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="8567e-193">MRTK의 손 메뉴 예제에는 거짓 활성화를 방지하기 위한 평면 손만 및 응시 요구 사항과 같은 유용한 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="8567e-194">손 메뉴 설명서</span><span class="sxs-lookup"><span data-stu-id="8567e-194">Hand Menu Documentations</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="8567e-195">손 메뉴 예제 장면</span><span class="sxs-lookup"><span data-stu-id="8567e-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="8567e-196">MRTK 예제 허브 앱을 HoloLens 2 손 메뉴 예제를 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8567e-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="8567e-197">MRTK 예제 허브의 손 메뉴 장면</span><span class="sxs-lookup"><span data-stu-id="8567e-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="8567e-198">참조</span><span class="sxs-lookup"><span data-stu-id="8567e-198">See also</span></span>

* [<span data-ttu-id="8567e-199">커서</span><span class="sxs-lookup"><span data-stu-id="8567e-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8567e-200">손 광선</span><span class="sxs-lookup"><span data-stu-id="8567e-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8567e-201">Button</span><span class="sxs-lookup"><span data-stu-id="8567e-201">Button</span></span>](button.md)
* [<span data-ttu-id="8567e-202">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="8567e-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8567e-203">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="8567e-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8567e-204">조작</span><span class="sxs-lookup"><span data-stu-id="8567e-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8567e-205">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="8567e-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8567e-206">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="8567e-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8567e-207">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="8567e-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8567e-208">음성 명령</span><span class="sxs-lookup"><span data-stu-id="8567e-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8567e-209">키보드</span><span class="sxs-lookup"><span data-stu-id="8567e-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8567e-210">Tooltip</span><span class="sxs-lookup"><span data-stu-id="8567e-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8567e-211">슬레이트</span><span class="sxs-lookup"><span data-stu-id="8567e-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="8567e-212">슬라이더</span><span class="sxs-lookup"><span data-stu-id="8567e-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="8567e-213">셰이더</span><span class="sxs-lookup"><span data-stu-id="8567e-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="8567e-214">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="8567e-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8567e-215">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="8567e-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8567e-216">표면 자성</span><span class="sxs-lookup"><span data-stu-id="8567e-216">Surface magnetism</span></span>](surface-magnetism.md)