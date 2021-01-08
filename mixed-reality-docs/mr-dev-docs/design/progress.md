---
title: 진행률 표시
description: 진행률 컨트롤이 혼합 현실 앱에서 장기 실행 작업이 진행 되 고 있음을 사용자에 게 피드백을 제공 하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, ui, ux, 진행률 표시기, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 489f4bd9fea31126f936673db7acafeab27d9cd9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009463"
---
# <a name="progress-indicator"></a><span data-ttu-id="f48c2-104">진행률 표시기</span><span class="sxs-lookup"><span data-stu-id="f48c2-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="f48c2-105">진행률 컨트롤은 장기 실행 작업이 진행 중임을 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="f48c2-106">진행률 표시기가 표시 되 면 사용자는 대기 시간을 볼 수 있으며 앱과 상호 작용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="f48c2-107">진행률 유형</span><span class="sxs-lookup"><span data-stu-id="f48c2-107">Types of progress</span></span>

<span data-ttu-id="f48c2-108">발생 한 상황에 대 한 사용자 정보를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="f48c2-109">혼합 현실에서는 앱이 좋은 시각적 피드백을가지고 있지 않은 경우 물리적 환경이 나 개체에 의해 사용자가 쉽게 무시 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="f48c2-110">데이터를 로드 하거나 장면을 업데이트 하는 경우와 같이 몇 초 정도 걸리는 경우 시각적 표시기를 표시 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="f48c2-111">작업이 진행 중인 사용자를 표시 하는 두 가지 옵션은 **진행률 표시줄이** 나 **진행 링** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="f48c2-112">진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="f48c2-112">Progress bar</span></span><br>
        <span data-ttu-id="f48c2-113">진행률 표시줄에는 태스크의 완료율이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="f48c2-114">기간이 알려진 작업 (활성화 상태의) 중에 사용 해야 하지만, 해당 진행률이 사용자의 앱 상호 작용을 차단 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="f48c2-115">*이미지: HoloLens의 진행률 표시줄 예*</span><span class="sxs-lookup"><span data-stu-id="f48c2-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f48c2-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f48c2-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f48c2-117">![HoloLens의 진행률 표시줄 예](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="f48c2-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="f48c2-118">진행률 링</span><span class="sxs-lookup"><span data-stu-id="f48c2-118">Progress ring</span></span><br>
        <span data-ttu-id="f48c2-119">진행률 링은 확정 되지 않은 상태 이며 작업이 완료 될 때까지 사용자 상호 작용이 차단 될 때 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="f48c2-120">*이미지: HoloLens의 진행 링 예*</span><span class="sxs-lookup"><span data-stu-id="f48c2-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f48c2-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f48c2-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f48c2-122">![HoloLens 장치의 진행 링 예](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="f48c2-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="f48c2-123">사용자 지정 개체의 진행률</span><span class="sxs-lookup"><span data-stu-id="f48c2-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="f48c2-124">사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성 및 브랜드 id에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="f48c2-125">*이미지: HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행*</span><span class="sxs-lookup"><span data-stu-id="f48c2-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f48c2-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f48c2-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f48c2-127">![HoloLens의 사용자 지정 메시 예제로 진행](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="f48c2-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="f48c2-128">모범 사례</span><span class="sxs-lookup"><span data-stu-id="f48c2-128">Best practices</span></span>
* <span data-ttu-id="f48c2-129">사용자가 자신의 헤드를 빈 공간으로 쉽게 이동 하 고 컨텍스트를 손실할 수 있으므로 [billboarding 또는 태그](billboarding-and-tag-along.md) 를 진행률 표시와 긴밀 하 게 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="f48c2-130">사용자가 아무것도 확인할 수 없는 경우 앱이 손상 된 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="f48c2-131">Billboarding 및 태그 동반은 Progress prefab에 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="f48c2-132">항상 사용자에 게 발생 하는 상황에 대 한 상태 정보를 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="f48c2-133">진행률 prefab 상태를 제공 하기 위한 Windows 표준 링 유형 진행률을 비롯 한 다양 한 비주얼 스타일을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="f48c2-134">응용 프로그램의 브랜드에 맞게 진행률 스타일을 조정 하려는 경우 애니메이션으로 사용자 지정 메시를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48c2-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f48c2-135">Unity 용 MRTK (Mixed Reality Toolkit)의 진행률 표시기</span><span class="sxs-lookup"><span data-stu-id="f48c2-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="f48c2-136">MRTK-진행률 표시기 prefabs</span><span class="sxs-lookup"><span data-stu-id="f48c2-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="f48c2-137">MRTK-장면 전환 서비스</span><span class="sxs-lookup"><span data-stu-id="f48c2-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="f48c2-138">참조</span><span class="sxs-lookup"><span data-stu-id="f48c2-138">See also</span></span>

* [<span data-ttu-id="f48c2-139">커서</span><span class="sxs-lookup"><span data-stu-id="f48c2-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f48c2-140">손 광선</span><span class="sxs-lookup"><span data-stu-id="f48c2-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f48c2-141">Button</span><span class="sxs-lookup"><span data-stu-id="f48c2-141">Button</span></span>](button.md)
* [<span data-ttu-id="f48c2-142">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="f48c2-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f48c2-143">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="f48c2-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f48c2-144">조작</span><span class="sxs-lookup"><span data-stu-id="f48c2-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f48c2-145">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="f48c2-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f48c2-146">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="f48c2-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f48c2-147">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="f48c2-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f48c2-148">음성 명령</span><span class="sxs-lookup"><span data-stu-id="f48c2-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f48c2-149">키보드</span><span class="sxs-lookup"><span data-stu-id="f48c2-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f48c2-150">Tooltip</span><span class="sxs-lookup"><span data-stu-id="f48c2-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f48c2-151">슬레이트</span><span class="sxs-lookup"><span data-stu-id="f48c2-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="f48c2-152">슬라이더</span><span class="sxs-lookup"><span data-stu-id="f48c2-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="f48c2-153">셰이더</span><span class="sxs-lookup"><span data-stu-id="f48c2-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="f48c2-154">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="f48c2-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f48c2-155">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="f48c2-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f48c2-156">표면 자성</span><span class="sxs-lookup"><span data-stu-id="f48c2-156">Surface magnetism</span></span>](surface-magnetism.md)
