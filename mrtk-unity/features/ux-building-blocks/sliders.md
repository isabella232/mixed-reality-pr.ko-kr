---
title: 슬라이더
description: 슬라이더의 개요 MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 슬라이더,
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177506"
---
# <a name="sliders"></a><span data-ttu-id="cd986-104">슬라이더</span><span class="sxs-lookup"><span data-stu-id="cd986-104">Sliders</span></span>

![슬라이더 예제](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="cd986-106">슬라이더는 트랙의 슬라이더를 이동 하 여 값을 지속적으로 변경할 수 있도록 하는 UI 구성 요소입니다. 현재 손가락을 직접 또는 거리에 직접 이동 하 여 손가락을 끄는 슬라이더를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="cd986-107">슬라이더는 모션 컨트롤러, 손 또는 제스처 + 음성을 사용 하 여 AR 및 VR에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="cd986-108">장면 예</span><span class="sxs-lookup"><span data-stu-id="cd986-108">Example scene</span></span>

<span data-ttu-id="cd986-109">의 **SliderExample** 장면에서 예제를 찾을 수 있습니다 `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="cd986-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="cd986-110">슬라이더를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="cd986-110">How to use sliders</span></span>

<span data-ttu-id="cd986-111">**Pinchslider** prefab를 장면 계층 구조에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="cd986-112">사용자 고유의 슬라이더를 수정 하거나 만들려면 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="cd986-113">Thumb 개체에 collider가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="cd986-114">PinchSlider prefab에서 collider가 on입니다. `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="cd986-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="cd986-115">근처의 슬라이더를 사용할 수 있도록 하려면 collider를 포함 하는 개체에 근접 한 상호 작용 Grabbable 구성 요소가 있는지도 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="cd986-116">또한 다음 계층 구조를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="cd986-117">PinchSlider-sliderComponent을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="cd986-118">슬라이더의 선택 가능한 전체 영역을 포함 하는 TouchCollider입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="cd986-119">위치에 맞추기 동작을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="cd986-120">SliderThumb-이동 가능한 엄지 단추를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="cd986-121">트랙 및 다른 시각적 개체를 포함 하는 트랙볼 시각적 개체</span><span class="sxs-lookup"><span data-stu-id="cd986-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="cd986-122">OtherVisuals 개체-다른 시각적 개체 포함</span><span class="sxs-lookup"><span data-stu-id="cd986-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="cd986-123">슬라이더 이벤트</span><span class="sxs-lookup"><span data-stu-id="cd986-123">Slider events</span></span>

<span data-ttu-id="cd986-124">슬라이더는 다음과 같은 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="cd986-125">OnValueUpdated-슬라이더 값이 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="cd986-126">OnInteractionStarted-사용자가 슬라이더를 가져와 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="cd986-127">OnInteractionEnded-사용자가 슬라이더를 놓을 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="cd986-128">OnHoverEntered-사용자의 손을/controller가 near 또는 far 상호 작용을 사용 하 여 슬라이더를 가리킬 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="cd986-129">OnHoverExited-사용자의 손/컨트롤러가 더 이상 슬라이더 근처에 있지 않을 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="cd986-130">슬라이더 바인딩 및 축 구성</span><span class="sxs-lookup"><span data-stu-id="cd986-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="cd986-131">장면에서 핸들을 이동 하 여 슬라이더의 시작점과 끝점을 직접 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![슬라이더 구성](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="cd986-133">슬라이더 _축_ 필드를 통해 슬라이더의 축 (로컬 공간)을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="cd986-134">핸들을 사용할 수 없는 경우에는 슬라이더 _시작 거리_ 및 _슬라이더 끝 거리_ 필드를 통해 슬라이더의 시작점과 끝점을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="cd986-135">슬라이더의 시작/끝 위치를 슬라이더의 중심에서 로컬 좌표로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="cd986-136">즉, 슬라이더 시작과 끝 거리를 원하는 대로 설정한 후에는 시작 및 끝 거리를 업데이트할 필요 없이 슬라이더를 더 작거나 더 크게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="cd986-137">Inspector 속성</span><span class="sxs-lookup"><span data-stu-id="cd986-137">Inspector properties</span></span>

<span data-ttu-id="cd986-138">**Thumb Root** 슬라이더 엄지 단추를 포함 하는 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="cd986-139">**위치에 맞추기** 슬라이더의 지정 된 위치에이 슬라이더를 맞출지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="cd986-140">**Touchable** 터치 이벤트를 통해이 슬라이더를 제어할 수 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="cd986-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="cd986-141">**Thumb Collider** 슬라이더 엄지 단추를 제어 하는 collider입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="cd986-142">**Touchable Collider** 위치에 맞추기가 true 일 때 작업 하거나 선택할 수 있는 슬라이더 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="cd986-143">**슬라이더 값** 슬라이더의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="cd986-144">**슬라이더 단계 분할선 사용** 이 슬라이더가 단계 또는 연속으로 증가 하는지 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="cd986-145">**슬라이더 단계 분할선** 사용 슬라이더 단계 나누기를 사용 하는 경우 슬라이더가 분할 되는 하위 구분선의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="cd986-146">**시각적 개체 추적** 슬라이더를 따라 이동 하는 원하는 트랙 시각적 개체를 포함 하는 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="cd986-147">**눈금 표시** 슬라이더를 따라 이동 하는 원하는 눈금 표시를 포함 하는 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="cd986-148">**Thumb 시각적 개체** 슬라이더를 따라 이동 하는 원하는 thumb 시각적 개체를 포함 하는 gameobject입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="cd986-149">**슬라이더 축** 슬라이더가 이동 하는 축입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="cd986-150">**슬라이더 시작 거리** 슬라이더 트랙이 시작 되는 위치는 슬라이더 축의 가운데에서 로컬 공간 단위로 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="cd986-151">**슬라이더 끝 거리** 슬라이더 트랙이 끝나는 위치는 슬라이더 축의 가운데에서 로컬 공간 단위로 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="cd986-152">사용자가 편집기에서 슬라이더 축 값을 업데이트 하면 시각적 개체 또는 시각적 개체 추적이 지정 된 경우 해당 변환이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="cd986-153">특히 로컬 위치가 다시 설정 되 고 해당 로컬 회전이 슬라이더 축 방향에 맞게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="cd986-154">크기는 수정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-154">Their scale isn't modified.</span></span>
<span data-ttu-id="cd986-155">눈금 표시에 그리드 개체 컬렉션 구성 요소가 있는 경우 레이아웃 및 셀 너비 또는 셀 높이가 슬라이더 축과 일치 하도록 적절 하 게 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd986-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="cd986-156">예 슬라이더 구성</span><span class="sxs-lookup"><span data-stu-id="cd986-156">Example Slider Configurations</span></span>

<span data-ttu-id="cd986-157">위치 연속 슬라이더에 맞추기의 연속 슬라이더 ![](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="cd986-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="cd986-158">위치에 맞추기의 단계 슬라이더</span><span class="sxs-lookup"><span data-stu-id="cd986-158">Step Sliders with Snap To Position</span></span>

![단계 슬라이더](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="cd986-160">터치 슬라이더</span><span class="sxs-lookup"><span data-stu-id="cd986-160">Touch Sliders</span></span>

![터치 슬라이더](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
