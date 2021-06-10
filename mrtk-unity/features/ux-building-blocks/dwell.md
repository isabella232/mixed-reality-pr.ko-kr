---
title: 연연
description: Dwell 상호 작용
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647863"
---
# <a name="dwell"></a><span data-ttu-id="c6a12-104">연연</span><span class="sxs-lookup"><span data-stu-id="c6a12-104">Dwell</span></span>

![Dwell Hero](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="c6a12-106">헤드 응시 및 번지는 사람의 손을 다른 작업으로 사용 중인 시나리오에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="c6a12-107">이 기능은 음성이 100% 안정적이지 않거나 환경 또는 소셜 제약으로 인해 사용할 수 없는 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="c6a12-108">MRTK의 dwell 예제는 구성 가능한 응답 시간 및 시각적 피드백을 통해 다양한 유형의 UI 구성 요소를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="c6a12-109">디자인 권장 사항은 [헤드 응시 및 상주 지침](/windows/mixed-reality/design/gaze-and-dwell-head) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6a12-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="c6a12-110">Dwell 스크립트</span><span class="sxs-lookup"><span data-stu-id="c6a12-110">Dwell scripts</span></span>

- <span data-ttu-id="c6a12-111">**DwellHandler:** UI 대상에 유지 형식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="c6a12-112">**DwellStateType: dwell** 처리기의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="c6a12-113">**DwellUnityEvent:** 유지 이벤트에 대한 Unity 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="c6a12-114">포인터 참조를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="c6a12-115">**BaseDwellPressableButton.cs:** PressableButtonHoloLens2 프리팹의 에서 OnClick() 이벤트를 트리거하는 `Interactable` 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="c6a12-116">**ToggleDwellPressableButton.cs:** 이 `_BorderWidth` `dwellVisualImage` 스크립트는 MRTK 표준 셰이더를 사용하는 의 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="c6a12-117">Dwell 프로필</span><span class="sxs-lookup"><span data-stu-id="c6a12-117">Dwell profiles</span></span>
<span data-ttu-id="c6a12-118">Dwell 프로필은 **Dwell 처리기에서** 다양한 임계값을 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="c6a12-119">**ButtonDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="c6a12-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="c6a12-120">**InstandDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="c6a12-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="c6a12-121">**DwellProfileWithDecay.asset**</span><span class="sxs-lookup"><span data-stu-id="c6a12-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="c6a12-122">프리 팹</span><span class="sxs-lookup"><span data-stu-id="c6a12-122">Prefabs</span></span>

<span data-ttu-id="c6a12-123">이러한 프리팹은 유지 상호 작용을 지원하는 추가 구성 요소가 있는 HoloLens 2 스타일 누를 수 있는 단추 프리팹의 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="c6a12-124">**PressableButtonHoloLens2_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="c6a12-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="c6a12-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="c6a12-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="c6a12-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="c6a12-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="c6a12-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="c6a12-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="c6a12-128">이러한 프리팹에는 더 많은 백플레이트 구성 요소 **QuadDwellVisual이** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="c6a12-129">**HolographicBackPlateDwellVisual.mat** 재질이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="c6a12-130">**ToggleDwellPressableButton.cs는** MRTK 표준 셰이더의 **_BorderWidth** 속성을 업데이트하여 dwell 입력을 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="c6a12-131">예제 장면</span><span class="sxs-lookup"><span data-stu-id="c6a12-131">Example scene</span></span>

<span data-ttu-id="c6a12-132">장면에서 예제를 찾을 수 `DwellExample` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="c6a12-133">예제 장면에는 볼륨이 많은 UI 예제와 Unity UI 예제가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6a12-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="c6a12-134">참조</span><span class="sxs-lookup"><span data-stu-id="c6a12-134">See also</span></span>

- [<span data-ttu-id="c6a12-135">**단추**</span><span class="sxs-lookup"><span data-stu-id="c6a12-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="c6a12-136">**상호 작용 가능**</span><span class="sxs-lookup"><span data-stu-id="c6a12-136">**Interactable**</span></span>](interactable.md)
