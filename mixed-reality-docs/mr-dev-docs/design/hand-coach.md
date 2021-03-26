---
title: 핸드 코치
description: 시스템에서 사용자의 손을 검색 하 여 지원 하기 위해 직접 coach를 사용 하 여 3D 손을 트리거하는 방법에 대해 알아봅니다.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 수동 coach, 몰입 형 헤드셋, MRTK, 실습, 수동 지원, 혼합 현실 헤드셋, windows Mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 56a56893a7c5bc772268ab9980f25327eae83af5
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550073"
---
# <a name="hand-coach"></a><span data-ttu-id="64431-104">핸드 코치</span><span class="sxs-lookup"><span data-stu-id="64431-104">Hand coach</span></span>

![예: 손 coach](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="64431-106">핸드 coach는 시스템에서 사용자의 손을 감지 하지 못하는 경우 3D 모델링 된 손을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="64431-107">이 기능은 제스처를 학습 하지 않았을 때 사용자에 게 안내 하는 데 도움이 되는 "교육" 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="64431-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="64431-108">사용자가 지정 된 기간 동안 지정 된 제스처를 수행 하지 않은 경우에는 손으로 지연 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="64431-109">손 coach는 단추를 누르거나 홀로그램을 선택 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="64431-110">핸드 coach 제공 됨</span><span class="sxs-lookup"><span data-stu-id="64431-110">Hand coach provided</span></span>

<span data-ttu-id="64431-111">현재 상호 작용 모델은 스크롤, 먼 선택 및 가까운 탭과 같은 다양 한 제스처 컨트롤을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64431-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="64431-112">다음은<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> Mrtk</a>에서 제공 되는 기존 손 제스처의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="64431-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="64431-113">![Near Select의 예](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="64431-114">**거의 선택 된 사용 예 단추를 선택 하거나 interactable 개체를 닫는 방법을 보여 줍니다.**</span><span class="sxs-lookup"><span data-stu-id="64431-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-115">![대공 탭의 예](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="64431-116">**멀리 떨어져 있는 개체를 선택 하는 방법을 보여 주는 데 사용 되는 공기 탭의 예**</span><span class="sxs-lookup"><span data-stu-id="64431-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-117">![이동 예](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="64431-118">**공간에서 홀로그램을 이동 하는 방법을 보여 주는 데 사용 되는 개체를 공간으로 이동 하는 예제**</span><span class="sxs-lookup"><span data-stu-id="64431-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-119">![회전 예](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="64431-120">**Holograms 또는 개체를 회전 하는 방법을 보여 주는 Rotate-Used 예**</span><span class="sxs-lookup"><span data-stu-id="64431-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="64431-121">![크기 조정 예제](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="64431-122">**Holograms를 더 크거나 작게 조작 하는 방법을 보여 주기 위해 사용 하는 규모의 예**</span><span class="sxs-lookup"><span data-stu-id="64431-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-123">![팜 위로의 예](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="64431-124">**팜 up – 제안 된 사용의 예**</span><span class="sxs-lookup"><span data-stu-id="64431-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-125">![수동 대칭 이동의 예](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="64431-126">**직접 대칭 이동-메뉴를 표시 하는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="64431-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64431-127">![스크롤 예](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="64431-128">**스크롤 예제-목록 또는 긴 문서 스크롤에 사용**</span><span class="sxs-lookup"><span data-stu-id="64431-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="64431-129">설계 개념</span><span class="sxs-lookup"><span data-stu-id="64431-129">Design concepts</span></span>

<span data-ttu-id="64431-130">Hololens2의 경우 instinctual 및 자연 핸드 제스처를 기반으로 하는 손으로의 상호 작용을 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="64431-131">이러한 경우가 대부분의 사용자에 게 직관적 이라고 생각 하기 때문에 전용 제스처 학습 순간을 만들지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="64431-132">대신, 사용자가 이러한 제스처에 대해 학습 하는 데 도움이 되는 손 coach를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="64431-133">학습 시점이 없으면 사용자에 게 작업을 수행 하는 방법을 보여 주는 것이 가장 좋은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="64431-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="64431-134">사용자가 제스처를 파악할 수 있었지만 약간의 지침을 필요로 했습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="64431-135">사용자가 특정 기간 동안 개체와 상호 작용 하지 않는 경우 올바른 손 및 손가락 배치를 보여 주는 손 모양 coach 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="64431-136">간단</span><span class="sxs-lookup"><span data-stu-id="64431-136">Intuitive</span></span>

<span data-ttu-id="64431-137">실습에 애니메이션을 적용 하는 경우에는 명확 하 고 혼동을 일으키지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="64431-138">손 애니메이션은 사용자의 이해를 돕기 위해 시도 하는 제스처를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64431-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="64431-139">예를 들어 사용자가 단추를 누르기를 원하는 경우 단추를 누르는 손을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="64431-140">![예: 손 모양 coach 가까이 누르기](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="64431-141">*보석 가까이 누르기를 보여 주는 손 Coach*</span><span class="sxs-lookup"><span data-stu-id="64431-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="64431-142">수동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="64431-142">Hand scale</span></span>

<span data-ttu-id="64431-143">UI 메뉴를 사용 하 여 다양 한 손 크기를 테스트 하 고,이를 크기에 맞게 true로 설정 하면 menacing 느낌이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="64431-144">너무 작은 경우 제스처를 보고 이해 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="64431-145">**음성 전달 및 손**</span><span class="sxs-lookup"><span data-stu-id="64431-145">**Voice over and hands**</span></span>

<span data-ttu-id="64431-146">사용자가 음성을 통해 일련의 지침을 수신 하 고 직접 coach를 통해 다양 한 지침을 볼 수 있다고 생각 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="64431-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="64431-147">토대로 오버 로드를 줄이기 위해 사용자에 게 집중 하 고 경합에 집중 하는 데 도움이 되는 지침을 시퀀싱 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="64431-148">직접 만들 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="64431-148">Can I create my own?</span></span>

<span data-ttu-id="64431-149">예</span><span class="sxs-lookup"><span data-stu-id="64431-149">Yes!</span></span> <span data-ttu-id="64431-150">게임에 고유한 제스처를 만들어 커뮤니티에 다시 참가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="64431-151">앱에 사용할 수 있는 Rigged 손의 Maya 파일을 제공 합니다 .이 파일은 다운로드 하 여 다운로드할 수 있습니다 <a href="files/HandCoach_MRTK.zip"> HandCoach_MRTK.zip </a></span><span class="sxs-lookup"><span data-stu-id="64431-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="64431-152">![Maya의 애니메이션 실습 예](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="64431-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="64431-153">*Maya의 상자에 애니메이션을 적용 하는 Poking 예*</span><span class="sxs-lookup"><span data-stu-id="64431-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="64431-154">**권장 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="64431-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="64431-155">3D 아티스트 중에는 [Autodesk의 Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 를 사용 하도록 선택 하 고,이는 HoloLens를 사용 하 여 자산이 생성 되는 방식을 변형할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="64431-156">제공 되는 실습 파일은 Maya 이진 파일 이므로 Maya를 사용 하 여 손으로 애니메이트 하 고 내보내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="64431-157">다른 3D 프로그램을 사용 하려는 경우에는 다음을 참조 <b>하세요. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> HandCoachMRTK_FBX.zip 다운로드 </a> 하 여 사용자 고유의 컨트롤러 설치를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64431-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="64431-158">제공 된 다운로드 가능 maya 손으로 제공 된 파일을 사용 하는 경우 unity의 손을 0.6으로 축소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="64431-159">![예: Maya의 핸드 coach rig](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="64431-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="64431-160">*Rigged 손*</span><span class="sxs-lookup"><span data-stu-id="64431-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="64431-161">기술 사양</span><span class="sxs-lookup"><span data-stu-id="64431-161">Technical Specs</span></span>

*   <span data-ttu-id="64431-162">두 개의 전달 파일은 Maya Ascii 형식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="64431-163">오른쪽 및 왼쪽은 Maya 이진 형식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="64431-164">Maya 파일을 24FPS로 설정</span><span class="sxs-lookup"><span data-stu-id="64431-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="64431-165">파일 내에는 두 개의 핸드 또는 단일 면 제스처에 사용할 수 있는 왼쪽과 오른쪽이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="64431-166">오른쪽은 기본적으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="64431-167">약 10 개의 프레임에 대 한 버퍼를 시작 부분과 끝 부분에 남겨 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="64431-168">지정 된 대상을 사용 하 여 개체에 애니메이션 효과를 주려면 기본 상자 또는 Null에 애니메이션 효과를 주는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="64431-169">상자와 같은 물리적 개체에 애니메이션 효과를 적용 하는 경우에는 Maya에서 번역에 애니메이션 효과를 주지 않지만 Unity 또는 코드에서 애니메이션 효과를 주기 위해 대기 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="64431-170">표시 되는 애니메이션은 의미 있는 정보를 전달 하는 데 1.5 초 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="64431-171">애니메이션에 만족 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="64431-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="64431-172">모든 연결점 및 굽기 키 프레임 선택</span><span class="sxs-lookup"><span data-stu-id="64431-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="64431-173">컨트롤러를 삭제 하 고, 조인트 및 메시를 선택 하 고, FBX로 내보내기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="64431-174">여러 애니메이션이 있는 경우 Maya의 기본 제공 게임 내보내기를 사용할 수 있습니다. https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="64431-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="64431-175">Maya에서 내보내기</span><span class="sxs-lookup"><span data-stu-id="64431-175">Exporting from Maya</span></span>

<span data-ttu-id="64431-176">애니메이션에 만족 하는 경우</span><span class="sxs-lookup"><span data-stu-id="64431-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="64431-177">모든 조인트 선택: 계층 > 선택</span><span class="sxs-lookup"><span data-stu-id="64431-177">Select all joints: Select > Hierarchy</span></span>

     ![예: 메뉴의 계층 구조](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="64431-179">애니메이션 굽기: 애니메이션 > 키 > 굽기 애니메이션으로 전환</span><span class="sxs-lookup"><span data-stu-id="64431-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![예: 굽기 Animation Menu Location](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="64431-181">컨트롤러 Rig: Outliner > MainR_Grp 또는 MainL_Grp를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![예: 컨트롤러 Rig 메뉴 위치](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="64431-183">FBX로 내보내기: Select JNT + 메시: File > 선택 영역 내보내기 (옵션 상자) > 선택 영역 내보내기</span><span class="sxs-lookup"><span data-stu-id="64431-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![예: 선택 영역 내보내기 메뉴 위치](images/HandCoach/OptionBox.png)<br>

     ![예: 메뉴 위치](images/HandCoach/SelectionExport.png)<br>

     ![예: 내보내기 옵션 메뉴 위치](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="64431-187">FBX로 내보내고 Unity로 이동 하는 경우에는 0.6에 맞게 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="64431-188">이는 손을 표시 하는 데 완벽 한 균형을 갖고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="64431-189">![예: Unity 설정](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="64431-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="64431-190">*MRTK에서 찾은 HandCoach_R prefab에 대 한 Unity 설정*</span><span class="sxs-lookup"><span data-stu-id="64431-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="64431-191">Unity 프로젝트에 대 한 직접 구현</span><span class="sxs-lookup"><span data-stu-id="64431-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="64431-192">모범 사례</span><span class="sxs-lookup"><span data-stu-id="64431-192">Best practices</span></span>

* <span data-ttu-id="64431-193">Unity의 손을 0.6으로 축소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="64431-194">손을 두 번 재생 하 고, 완료 되지 않은 경우 제스처가 완료 될 때까지 지속적으로 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="64431-195">사용자가를 등록 하 고 제스처를 볼 수 있도록 하려면 두 번 반복 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="64431-196">바늘은 루프 간에 페이드 인 및 페이드 아웃 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="64431-197">사용자의 손을 HL2 카메라에서 볼 수 있지만 사용자가 필요한 상호 작용을 수행 하지 않는 경우 10 초 후에도 손을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="64431-198">사용자의 손을 HL2 카메라에 표시 되지 않으면 5 초 후에도 손을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="64431-199">애니메이션 중간의 HL2 카메라에서 사용자의 손을 시각적으로 추적 하는 경우 애니메이션이 완료 되 고 페이드 아웃 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64431-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="64431-200">음성을 포함 하는 경우에는 손 제스처에 해당 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="64431-201">한 번 이상 실습 한 경우 사용자가 중지 된 것을 감지 하는 경우에만 제스처를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="64431-202">특정 손가락/손 위치가 중요 한 경우 사용자가 애니메이션에서 이러한 미묘한 차이를 명확 하 게 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="64431-203">가장 중요 한 부분이 명확 하 게 표시 되도록 손을 준.</span><span class="sxs-lookup"><span data-stu-id="64431-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="64431-204">손으로 왜곡 된 경우 Unity의 품질 설정으로 이동 하 여 뼈의 수를 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="64431-205">Unity의 편집 > 프로젝트 설정 > 품질 > 기타 > 혼합 가중치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="64431-206">부드러운 조인트를 보려면 "4 뼈"가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![예: 프로젝트 설정 창](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="64431-208">피해야 할 사항</span><span class="sxs-lookup"><span data-stu-id="64431-208">What to avoid</span></span>

* <span data-ttu-id="64431-209">너무 크게 크기 조정</span><span class="sxs-lookup"><span data-stu-id="64431-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="64431-210">사용자에 게 너무 가까운 손을 두기</span><span class="sxs-lookup"><span data-stu-id="64431-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="64431-211">손을 한 번만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64431-211">Hands should only be taught once.</span></span> <span data-ttu-id="64431-212">교육을 통해 혼란을 야기 하 고 messiness 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-212">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="64431-213">Unity로 가져와서 최신 MRTK를 다운로드 합니다. https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="64431-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="64431-214">재질: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="64431-214">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="64431-215">스크립트: <a href= "/windows/mixed-reality/mrtk-docs/features/experimental/hand-coach.md">mrtk 손 coach</a> 에 대 한 mrtk 지침 참조</span><span class="sxs-lookup"><span data-stu-id="64431-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-docs/features/experimental/hand-coach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="64431-216">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="64431-216">Per- project setting</span></span>
        *   <span data-ttu-id="64431-217">UWP로 설정 된 장면: Windows Mixed Reality의 [Unity 구성 프로젝트](../develop/unity/Configure-Unity-Project.md) 에서 지침을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64431-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="64431-218">참조</span><span class="sxs-lookup"><span data-stu-id="64431-218">See also</span></span>

* [<span data-ttu-id="64431-219">상호 작용-기본 사항</span><span class="sxs-lookup"><span data-stu-id="64431-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="64431-220">자산 생성 프로세스</span><span class="sxs-lookup"><span data-stu-id="64431-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="64431-221">제스처</span><span class="sxs-lookup"><span data-stu-id="64431-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="64431-222">도구 설치</span><span class="sxs-lookup"><span data-stu-id="64431-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="64431-223">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="64431-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="64431-224">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="64431-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="64431-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="64431-225">MRTK 101</span></span>](../out-of-scope/mrtk-101.md)