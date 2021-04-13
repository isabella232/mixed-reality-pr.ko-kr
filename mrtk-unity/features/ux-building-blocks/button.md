---
title: 단추
description: MRTK의 단추에 대 한 개요
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, MRTK 단추
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003118"
---
# <a name="button"></a><span data-ttu-id="75dfb-104">단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-104">Button</span></span>

![주 단추](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="75dfb-106">단추를 사용하면 즉각적인 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="75dfb-107">혼합 현실에서 가장 기본적인 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="75dfb-108">MRTK는 다양 한 형식의 단추 prefabs 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="75dfb-109">MRTK의 단추 prefabs</span><span class="sxs-lookup"><span data-stu-id="75dfb-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="75dfb-110">폴더 아래에 있는 단추 prefabs의 예 ``MRTK/SDK/Features/UX/Interactable/Prefabs``</span><span class="sxs-lookup"><span data-stu-id="75dfb-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="75dfb-111">Unity UI 이미지/그래픽 기반 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="75dfb-112">Collider 기반 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="75dfb-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="75dfb-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="75dfb-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="75dfb-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="75dfb-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="75dfb-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="75dfb-119">테두리 밝은, 근접 조명 및 압축 된 front와 같은 다양 한 시각적 피드백을 지 원하는 백 판이 있는 HoloLens 2의 셸 스타일 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-120">HoloLens 2의 셸 스타일 단추 (backplate 불포함)</span><span class="sxs-lookup"><span data-stu-id="75dfb-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-121">원형 셰이프를 사용 하는 HoloLens 2의 셸 스타일 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="75dfb-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="75dfb-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="75dfb-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="75dfb-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="75dfb-125">광역 HoloLens 2의 셸 스타일 단추 32x96mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-126">공유 백 판의 가로 HoloLens 2 단추 모음</span><span class="sxs-lookup"><span data-stu-id="75dfb-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-127">공유 백 판의 세로 HoloLens 2 단추 모음</span><span class="sxs-lookup"><span data-stu-id="75dfb-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="75dfb-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="75dfb-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="75dfb-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="75dfb-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="75dfb-131">HoloLens 2의 셸 스타일 확인란 32x32mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-132">HoloLens 2의 셸 스타일 스위치 32x32mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-133">HoloLens 2의 셸 스타일 라디오 32x32mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="75dfb-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="75dfb-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="75dfb-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="75dfb-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="75dfb-137">HoloLens 2의 셸 스타일 확인란 32x96mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-138">HoloLens 2의 셸 스타일 스위치 32x96mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-139">HoloLens 2의 셸 스타일 라디오 32x96mm</span><span class="sxs-lookup"><span data-stu-id="75dfb-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="75dfb-140">![방사형 ](../images/button/MRTK_Button_Radial.png) **방사형**</span><span class="sxs-lookup"><span data-stu-id="75dfb-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-141">![확인란](../images/button/MRTK_Button_Checkbox.png) **확인란**</span><span class="sxs-lookup"><span data-stu-id="75dfb-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="75dfb-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="75dfb-143">방사형 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-144">확인란</span><span class="sxs-lookup"><span data-stu-id="75dfb-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-145">토글 스위치</span><span class="sxs-lookup"><span data-stu-id="75dfb-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="75dfb-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="75dfb-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="75dfb-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-148">![단추 기준 ](../images/button/MRTK_Button_Base.png) **단추**</span><span class="sxs-lookup"><span data-stu-id="75dfb-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="75dfb-149">HoloLens 1 세대 셸 스타일 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-150">둥근 모양 푸시 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="75dfb-151">기본 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="75dfb-152">`Button`(자산/m a RTK/SDK/Features/UX/Interactable/Prefabs/prefab)는 [Interactable](interactable.md) 개념을 기반으로 하 여 단추 또는 다른 유형의 대화형 화면에 대 한 간편한 UI 컨트롤을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="75dfb-153">기준선 단추는 근접 한 상호 작용에 대 한 트레일러 입력을 포함 하는 모든 사용 가능한 입력 메서드를 지원 하며, 먼 상호 작용을 위해 응시 + 공기 탭도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="75dfb-154">음성 명령을 사용 하 여 단추를 트리거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="75dfb-155">`PressableButtonHoloLens2` (Asset/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2)는 직접 추적 입력 단추를 정확 하 게 이동할 수 있도록 하는 HoloLens 2의 셸 스타일 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="75dfb-156">스크립트 `Interactable` 와 스크립트를 결합 `PressableButton` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="75dfb-157">HoloLens 2의 경우 불투명 backplate 사용 하는 단추를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="75dfb-158">투명 단추는 다음과 같은 유용성 및 안정성 문제로 인해 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="75dfb-159">물리적 환경에서 아이콘 및 텍스트를 읽기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="75dfb-160">이벤트가 트리거되는 시기를 이해 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="75dfb-161">투명 평면을 통해 표시 되는 Holograms는 HoloLens 2의 깊이 LSR 안정화를 사용 하 여 불안정 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Plated 단추](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="75dfb-163">Pressable 단추를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="75dfb-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="75dfb-164">Unity UI 기반 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-164">Unity UI based buttons</span></span>

<span data-ttu-id="75dfb-165">장면 (GameObject >-> Canvas)에서 캔버스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="75dfb-166">캔버스의 검사기 패널에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="75dfb-167">"MRTK 캔버스로 변환"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="75dfb-168">"NearInteractionTouchableUnityUI 추가"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="75dfb-169">Rect Transform 구성 요소의 X, Y 및 Z 소수 자릿수를 0.001으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="75dfb-170">그런 다음 (asset/ `PressableButtonUnityUI` mrtk/sdk/features/ux/Interactable/Prefabs/prefab), `PressableButtonUnityUICircular` (asset/MRTK/Sdk/FEATURES/Ux/Interactable/Prefabs/PressableButtonUnityUICircular) 또는 `PressableButtonHoloLens2UnityUI` (ASSET/mrtk/sdk/features/ux/prefab/Interactable/Prefabs)를 캔버스에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="75dfb-171">Collider 기반 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-171">Collider based buttons</span></span>

<span data-ttu-id="75dfb-172">(Asset `PressableButtonHoloLens2` /mrtk/sdk/features/ux/Interactable/Prefabs/PressableButtonHoloLens2) 또는 `PressableButtonHoloLens2Unplated` (자산/m RTK/Sdk/FEATURES/Ux/Interactable/Prefabs/PressableButtonHoloLens2Unplated)를 장면으로 끌어 놓기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="75dfb-173">이러한 단추 prefabs는 여러 개의 입력 형식에 대 한 오디오 시각적 피드백을 포함 하도록 이미 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="75dfb-174">Prefab 자체와 [Interactable](interactable.md) 구성 요소에 노출 되는 이벤트를 사용 하 여 추가 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="75dfb-175">[HandInteractionExample 장면의](../example-scenes/hand-interaction-examples.md) pressable 단추는 Interactable의 *OnClick* 이벤트를 사용 하 여 큐브의 색 변경을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="75dfb-176">이 이벤트는 pressable button 스크립트를 통해 실제 단추를 누르는 것 뿐만 아니라 응시, 공중 탭, 손으로 그린 등의 여러 입력 방법에 대해 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="75dfb-177">단추를 통해 pressable 단추가 *OnClick* 이벤트를 발생 시키는 시점을 구성할 수 있습니다 `PhysicalPressEventRouter` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="75dfb-178">예를 들어 누름 시 이벤트를 *클릭* 하 여 *누르기* 를 설정 하는 대신 단추를 처음 누를 때 Interactable *를 실행 하도록 설정할 수* 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="75dfb-179">특정 트레일러 식 입력 상태 정보를 활용 하려면 pressable buttons 이벤트- *터치 시작*, *터치 종료*, *단추 누름*, *단추* 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="75dfb-180">그러나 이러한 이벤트는 공중 탭, 손 광선 또는 눈 입력에 대 한 응답으로 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="75dfb-181">**Near 및 far 상호 작용을 모두 지원 하려면 Interactable의 *OnClick* 이벤트를 사용 하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="75dfb-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="75dfb-182">상호 작용 상태</span><span class="sxs-lookup"><span data-stu-id="75dfb-182">Interaction states</span></span>

<span data-ttu-id="75dfb-183">유휴 상태에서는 단추의 front 판이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="75dfb-184">손가락으로 나 응시 입력의 커서가 표면을 대상으로 하는 경우 front 판의 광선 테두리가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="75dfb-185">Front 판금 표면의 fingertip 위치를 추가로 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="75dfb-186">손가락이 푸시되 면 front 판금이 fingertip으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="75dfb-187">Fingertip는 프런트 판의 표면에 닿을 때 터치 점에 대 한 시각적 피드백을 제공 하기 위한 미묘한 펄스 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="75dfb-188">HoloLens 2 shell 스타일 단추에는 많은 시각적 신호 및 affordances 있어 사용자의 상호 작용에 대 한 신뢰도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![근접 조명](../images/button/ux_button_affordance_proximitylight.jpg) | ![포커스 강조 표시](../images/button/ux_button_affordance_focushighlight.jpg)  | ![케이지 압축](../images/button/ux_button_affordance_compression.jpg) | ![펄스 on 트리거](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="75dfb-193">근접 조명</span><span class="sxs-lookup"><span data-stu-id="75dfb-193">Proximity light</span></span> | <span data-ttu-id="75dfb-194">포커스 강조 표시</span><span class="sxs-lookup"><span data-stu-id="75dfb-194">Focus highlight</span></span> | <span data-ttu-id="75dfb-195">케이지 압축</span><span class="sxs-lookup"><span data-stu-id="75dfb-195">Compressing cage</span></span> | <span data-ttu-id="75dfb-196">펄스 on 트리거</span><span class="sxs-lookup"><span data-stu-id="75dfb-196">Pulse on trigger</span></span> |

<span data-ttu-id="75dfb-197">미묘한 펄스 효과는 현재 상호 작용 하는 포인터에 살고 있는 *ProximityLight* 를 검색 하는 pressable 단추에 의해 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="75dfb-198">근접 조명이 발견 되 면 `ProximityLight.Pulse` 이 메서드를 호출 하 여 펄스를 표시 하는 셰이더 매개 변수에 자동으로 애니메이션 효과를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="75dfb-199">Inspector 속성</span><span class="sxs-lookup"><span data-stu-id="75dfb-199">Inspector properties</span></span>

![단추 구조](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="75dfb-201">**상자 Collider** 
 `Box Collider` 단추의 front 플레이트입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="75dfb-202">**Pressable 단추** 직접 누르기 상호 작용을 사용 하 여 단추 이동에 대 한 논리입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="75dfb-203">**실제 누르기 이벤트 라우터** 이 스크립트는 [Interactable](interactable.md)에 대 한 직접 누르기 상호 작용에서 이벤트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="75dfb-204">**Interactable** 
 [Interactable](interactable.md) 는 다양 한 유형의 상호 작용 상태와 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="75dfb-205">HoloLens 응시, 제스처 및 음성 입력 및 몰입 형 헤드셋 동작 컨트롤러 입력은이 스크립트에 의해 직접 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="75dfb-206">**오디오 원본** 오디오 피드백 클립에 대 한 Unity 오디오 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="75dfb-207">*NearInteractionTouchable* 은 모든 개체를 touchable로 설정 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="75dfb-208">Prefab 레이아웃</span><span class="sxs-lookup"><span data-stu-id="75dfb-208">Prefab layout</span></span>

<span data-ttu-id="75dfb-209">*Buttoncontent* 개체에는 front 판금, 텍스트 레이블 및 아이콘이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="75dfb-210">*FrontPlate* 는 *Button_Box* 셰이더를 사용 하 여 인덱스 fingertip 근접에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="75dfb-211">빛나는 테두리, 근접 조명 및 터치에 대 한 펄스 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="75dfb-212">텍스트 레이블은 TextMesh Pro를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="75dfb-213">*SeeItSayItLabel* 의 표시 유형은 [Interactable](interactable.md)의 테마에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![단추 레이아웃](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="75dfb-215">아이콘 및 텍스트를 변경 하는 방법</span><span class="sxs-lookup"><span data-stu-id="75dfb-215">How to change the icon and text</span></span>

<span data-ttu-id="75dfb-216">MRTK 단추는 `ButtonConfigHelper` 구성 요소를 사용 하 여 단추의 아이콘, 텍스트 및 레이블을 변경 하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="75dfb-217">선택 된 단추에 요소가 없는 경우 일부 필드는 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![단추 구성 도우미](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="75dfb-219">아이콘 집합 만들기 및 수정</span><span class="sxs-lookup"><span data-stu-id="75dfb-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="75dfb-220">**아이콘 집합** 은 구성 요소에서 사용 하는 아이콘 자산의 공유 집합입니다 `ButtonConfigHelper` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="75dfb-221">세 가지 아이콘 *스타일이* 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="75dfb-222">**쿼드** 아이콘은를 사용 하 여 쿼드로 렌더링 됩니다 `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="75dfb-223">기본 아이콘 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-223">This is the default icon style.</span></span>
* <span data-ttu-id="75dfb-224">**스프라이트** 아이콘은를 사용 하 여 렌더링 됩니다 `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="75dfb-225">이 기능은 스프라이트 시트로 아이콘을 가져오거나 Unity UI 구성 요소와 아이콘 자산을 공유 하려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="75dfb-226">이 스타일을 사용 하려면 스프라이트 편집기 패키지 **(Windows-> 패키지 관리자-> 2D 스프라이트)** 를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="75dfb-227">**문자** 아이콘은 구성 요소를 사용 하 여 렌더링 됩니다 `TextMeshPro` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="75dfb-228">이는 아이콘 글꼴을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="75dfb-229">HoloLens 아이콘 글꼴을 사용 하려면 `TextMeshPro` 글꼴 자산을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="75dfb-230">단추에 사용 되는 스타일을 변경 하려면 ButtonConfigHelper의 *아이콘* 드롭다운을 확장 하 고 *아이콘 스타일* 드롭다운에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="75dfb-231">자산 메뉴를 사용 하 여 새 단추 아이콘 집합을 만들 수 있습니다. **> Mixed Reality Toolkit > 아이콘 집합을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="75dfb-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="75dfb-232">쿼드 및 스프라이트 아이콘을 추가 하려면 해당 하는 배열로 끌어 놓기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="75dfb-233">문자 아이콘을 추가 하려면 먼저 글꼴 자산을 만들고 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="75dfb-234">MRTK 2.4 이상에서는 사용자 지정 아이콘 질감이 IconSet로 이동 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="75dfb-235">프로젝트의 모든 단추에 대 한 자산을 새 권장 형식으로 업그레이드 하려면 ButtonConfigHelperMigrationHandler를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="75dfb-236">(혼합 현실 도구 키트-> 유틸리티-> 마이그레이션 창-> 마이그레이션 처리기 선택-> MixedReality)</span><span class="sxs-lookup"><span data-stu-id="75dfb-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="75dfb-237">단추를 업그레이드 하는 데 필요한 MixedRealityToolkit 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![업그레이드 창 대화 상자](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="75dfb-239">마이그레이션 중에 기본 아이콘 집합에 아이콘이 없으면 사용자 지정 아이콘 집합이 MixedRealityToolkit/CustomIconSets에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="75dfb-240">이 작업이 수행 되었음을 나타내는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-240">A dialog will indicate that this has taken place.</span></span>

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="75dfb-242">HoloLens 아이콘 글꼴 자산 만들기</span><span class="sxs-lookup"><span data-stu-id="75dfb-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="75dfb-243">먼저 아이콘 글꼴을 Unity로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="75dfb-244">Windows 컴퓨터에서는 *windows/Fonts/holomdl2* 에서 기본 HoloLens 글꼴을 찾을 수 있습니다. .ttf.</span><span class="sxs-lookup"><span data-stu-id="75dfb-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="75dfb-245">이 파일을 복사 하 여 자산 폴더에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="75dfb-246">다음으로, **Window > TextMeshPro > Font Asset creator** 를 통해 TextMeshPro Font 자산 작성자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="75dfb-247">HoloLens 글꼴 아틀라스를 생성 하기 위한 권장 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="75dfb-248">모든 아이콘을 포함 하려면 다음 유니코드 범위를 *문자 시퀀스* 필드에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![단추 만들기 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="75dfb-250">글꼴 자산이 생성 되 면 프로젝트에 저장 하 고 아이콘 집합의 *Char 아이콘 글꼴* 필드에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="75dfb-251">이제 *사용 가능한 아이콘* 드롭다운이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="75dfb-252">단추에서 아이콘을 사용할 수 있도록 하려면 해당 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="75dfb-253">*선택한 아이콘* 드롭다운에 추가 되며, 필요에 따라 `ButtonConfigHelper.` 아이콘에 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="75dfb-254">이렇게 하면 런타임에 아이콘을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-254">This enables setting the icon at runtime.</span></span>

![단추 생성 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![단추 생성 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="75dfb-257">아이콘 집합을 사용 하려면 단추를 선택 하 고에서 아이콘 드롭다운을 확장 `ButtonConfigHelper` 한 다음 *아이콘 집합* 필드에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![단추 아이콘 집합](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="75dfb-259">단추 크기를 변경 하는 방법</span><span class="sxs-lookup"><span data-stu-id="75dfb-259">How to change the size of a button</span></span>

<span data-ttu-id="75dfb-260">HoloLens 2의 셸 스타일 단추 크기는 32x32mm입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="75dfb-261">차원을 사용자 지정 하려면 prefab 단추에서 이러한 개체의 크기를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="75dfb-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="75dfb-262">**FrontPlate**</span></span>
2. <span data-ttu-id="75dfb-263">백 판금에서 **쿼드**</span><span class="sxs-lookup"><span data-stu-id="75dfb-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="75dfb-264">루트의 **Box Collider**</span><span class="sxs-lookup"><span data-stu-id="75dfb-264">**Box Collider** on the root</span></span>

<span data-ttu-id="75dfb-265">그런 다음 단추의 루트에 있는 NearInteractionTouchable 스크립트에서 **범위 고정** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="75dfb-266">FrontPlate ![ 단추 크기 사용자 지정 1의 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="75dfb-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="75dfb-267">4 ![ 단추 크기 사용자 지정 2의 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="75dfb-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="75dfb-268">상자 Collider ![ Button 크기 사용자 지정 3 상자 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="75dfb-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="75dfb-269">' 범위 수정 ' ![ 단추 크기 사용자 지정 4를 클릭 합니다.](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="75dfb-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="75dfb-270">음성 명령 (' 참조-it ')</span><span class="sxs-lookup"><span data-stu-id="75dfb-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="75dfb-271">**음성 입력 처리기** Pressable의 [Interactable](interactable.md) 스크립트는 이미을 구현 `IMixedRealitySpeechHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="75dfb-272">음성 명령 키워드는 여기에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="75dfb-273">**음성 입력 프로필** 또한 전역 *음성 명령 프로필* 에 음성 명령 키워드를 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="75dfb-274">**참조-it 레이블** Pressable button prefab에는 *SeeItSayItLabel* 개체 아래에 자리 표시자 Textmesh Pro 레이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="75dfb-275">이 레이블을 사용 하 여 단추에 대 한 음성 명령 키워드를 사용자에 게 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="75dfb-276">단추를 처음부터 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="75dfb-276">How to make a button from scratch</span></span>

<span data-ttu-id="75dfb-277">이러한 단추의 예는 **보도 Sablebuttonexample** 장면에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="75dfb-278">1. cube를 사용 하 여 pressable 단추 만들기 (근거리 상호 작용에만 해당)</span><span class="sxs-lookup"><span data-stu-id="75dfb-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="75dfb-279">Unity 큐브 만들기 (GameObject > 3D 개체 > 큐브)</span><span class="sxs-lookup"><span data-stu-id="75dfb-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="75dfb-280">`PressableButton.cs`스크립트 추가</span><span class="sxs-lookup"><span data-stu-id="75dfb-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="75dfb-281">`NearInteractionTouchable.cs`스크립트 추가</span><span class="sxs-lookup"><span data-stu-id="75dfb-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="75dfb-282">`PressableButton`의 검사기 패널에서 큐브 개체를 **이동 단추 시각적** 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="75dfb-283">큐브를 선택 하면 개체에 색이 지정 된 여러 계층이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="75dfb-284">그러면 **누름 설정** 에서 거리 값이 시각화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="75dfb-285">핸들을 사용 하 여 누르기를 시작할 시기 (개체 이동)와 이벤트를 트리거할 시기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="75dfb-286">단추를 누르면 `PressableButton.cs` TouchBegin (), TouchEnd (), ButtonPressed (), Buttonpressed ()와 같은 스크립트에 노출 된 적절 한 이벤트가 이동 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="75dfb-287">문제 해결</span><span class="sxs-lookup"><span data-stu-id="75dfb-287">Troubleshooting</span></span>

<span data-ttu-id="75dfb-288">단추에서 두 번 누르기를 실행 하는 경우에는 **Front Push 적용** 속성이 활성 상태이 고 **푸시 거리** 평면이 **근접 한 상호 작용 Touchable** 평면 앞에 배치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="75dfb-289">**근접 한 상호 작용 Touchable** 평면은 아래 gif에서 흰색 화살표의 원점 앞에 놓인 파란색 평면으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Front Push 속성이 강조 표시 된 Pressable button 스크립트 구성 요소](../images/button/MRTK_Button_Enforce_Push.png)

![근접 한 상호 작용 touchable 평면 앞에서 시작 푸시 거리를 이동 하는 애니메이션 예제](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="75dfb-292">2. 기본 큐브에 시각적 피드백 추가 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="75dfb-293">MRTK 표준 셰이더는 시각적 피드백을 쉽게 추가할 수 있게 해 주는 다양 한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="75dfb-294">재질을 만들고 셰이더를 선택 `Mixed Reality Toolkit/Standard` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="75dfb-295">또는에서 MRTK 표준 셰이더를 사용 하는 기존 자료 중 하나를 사용 하거나 복제할 수 있습니다 `/SDK/StandardAssets/Materials/` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="75dfb-296">`Hover Light` `Proximity Light` **흐름 옵션** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="75dfb-297">이를 통해 근거리 (근접 조명)와 원거리 포인터 (가리키기 광원) 상호 작용에 대 한 시각적 피드백을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="75dfb-298">3. 기본 큐브에 오디오 피드백 추가 단추</span><span class="sxs-lookup"><span data-stu-id="75dfb-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="75dfb-299">`PressableButton.cs`스크립트는 TouchBegin (), TouchEnd (), ButtonPressed (), Buttonpressed ()와 같은 이벤트를 노출 하므로 오디오 피드백을 쉽게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="75dfb-300">`Audio Source`큐브 개체에 Unity를 추가 하 고 PlayOneShot ()를 선택 하 여 오디오 클립을 할당 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="75dfb-301">폴더에서 MRTK_Select_Main 및 MRTK_Select_Secondary 오디오 클립을 사용할 수 있습니다 `/SDK/StandardAssets/Audio/` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="75dfb-302">4. 시각적 상태 추가 및 far 상호 작용 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="75dfb-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="75dfb-303">[Interactable](interactable.md) 는 다양 한 유형의 입력 상호 작용에 대 한 시각적 상태를 쉽게 만들 수 있도록 해 주는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="75dfb-304">또한 먼 상호 작용 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-304">It also handles far interaction events.</span></span> <span data-ttu-id="75dfb-305">`Interactable.cs`큐브 개체를 추가 하 여 **프로필** 의 **대상** 필드에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="75dfb-306">그런 다음 **ScaleOffsetColorTheme** 형식으로 새 테마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="75dfb-307">이 테마에서 **포커스** 및 **눌린** 특정 상호 작용 상태에 대 한 개체의 색을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="75dfb-308">크기 조정 및 오프셋도 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="75dfb-309">**감속/가속** 을 선택 하 고 시각적 전환을 매끄럽게 하기 위해 기간을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![프로필 테마 선택](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="75dfb-311">개체가 far (손 모양 또는 응시 커서)와 근거리 (손) 상호 작용에 응답 하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="75dfb-312">사용자 지정 단추 예제</span><span class="sxs-lookup"><span data-stu-id="75dfb-312">Custom button examples</span></span>

<span data-ttu-id="75dfb-313">[HandInteractionExample 장면](../example-scenes/hand-interaction-examples.md)에서를 사용 하는 피아노 및 round 단추 예를 참조 하세요 `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="75dfb-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="75dfb-314">각 피아노 키에는 `PressableButton` 및 `NearInteractionTouchable` 스크립트가 할당 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="75dfb-315">의 *로컬 정방향* 방향이 올바른지 확인 하는 것이 중요 `NearInteractionTouchable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="75dfb-316">편집기에서 흰색 화살표로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="75dfb-317">화살표가 단추의 정면 면을 가리키는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="75dfb-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="75dfb-318">참조</span><span class="sxs-lookup"><span data-stu-id="75dfb-318">See also</span></span>

* [<span data-ttu-id="75dfb-319">상호 작용 가능</span><span class="sxs-lookup"><span data-stu-id="75dfb-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="75dfb-320">시각적 개체 테마</span><span class="sxs-lookup"><span data-stu-id="75dfb-320">Visual Themes</span></span>](visual-themes.md)
