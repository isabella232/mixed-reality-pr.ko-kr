---
title: Fingertip 시각화
description: MRTK의 FingerTip 시각화 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, Fingertip
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177533"
---
# <a name="fingertip-visualization"></a><span data-ttu-id="a382b-104">Fingertip 시각화</span><span class="sxs-lookup"><span data-stu-id="a382b-104">Fingertip visualization</span></span>

![Fingertip 시각화 기본](../images/fingertip/MRTK_FingertipVisualization_Main.png)

<span data-ttu-id="a382b-106">Fingertip affordance를 사용 하면 사용자가 대상 개체 로부터의 거리를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-106">The fingertip affordance helps the user recognize the distance from the target object.</span></span> <span data-ttu-id="a382b-107">링 모양 시각적 개체는 fingertip에서 개체로의 거리를 기준으로 크기를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-107">The ring shape visual adjusts its size based on the distance from the fingertip to the object.</span></span> <span data-ttu-id="a382b-108">Fingertip 시각화는 기본적으로 `FingerCursor` *Pokepointer* 의 커서 prefab로 생성 되는 (ASSET/MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor) (및 스크립트)에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-108">The fingertip visualization is primarily controlled by the `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (and script) which is spawned as the cursor prefab of the *PokePointer*.</span></span> <span data-ttu-id="a382b-109">시각화의 다른 구성 요소에는 *ProximityLight* 스크립트와 *MixedRealityStandard* 셰이더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-109">Other components of the visualization include the *ProximityLight* script, and *MixedRealityStandard* shader.</span></span>

## <a name="how-to-use-the-fingertip-visualization"></a><span data-ttu-id="a382b-110">Fingertip 시각화를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="a382b-110">How to use the fingertip visualization</span></span>

<span data-ttu-id="a382b-111">기본적으로 fingertip 시각화는 FingerCursor를 생성 하도록 구성 된 모든 Unity 장면에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-111">By default the fingertip visualization will work in any Unity scene that is configured to spawn a FingerCursor.</span></span> <span data-ttu-id="a382b-112">FingerCursor의 생성은 다음 *DefaultMixedRealityToolkitConfigurationProfile* 에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-112">Spawning of the FingerCursor occurs in the *DefaultMixedRealityToolkitConfigurationProfile* under:</span></span>

<span data-ttu-id="a382b-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span><span class="sxs-lookup"><span data-stu-id="a382b-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span></span>

<span data-ttu-id="a382b-114">높은 수준에서 fingertip 시각화는 근접 조명을 사용 하 여 근접 조명을 허용 하는 주변 표면에서 색이 지정 된 그라데이션을 프로젝션 하는 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-114">At a high level the fingertip visualization works by using a proximity light to project a colored gradient on any nearby surfaces that accept proximity lights.</span></span> <span data-ttu-id="a382b-115">그러면 손가락 커서는 부모에 의해 결정 되는 주변의 interactable 표면을 검색 하 여 `IMixedRealityNearPointer(s)` 손가락이 화면으로 이동 하는 것 처럼 손가락 링을 표면과 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-115">The finger cursor then looks for any nearby interactable surfaces, which are determined by parent `IMixedRealityNearPointer(s)`, to align the finger ring with a surface as the finger moves towards a surface.</span></span> <span data-ttu-id="a382b-116">손가락이 표면에 가까워지면 손가락 링은 MixedRealityStandard 셰이더의 둥근 모퉁이 속성을 사용 하 여 동적으로 애니메이션을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-116">As a finger approaches a surface the finger ring is also dynamically animated using the round corner properties of the MixedRealityStandard shader.</span></span>

## <a name="example-scene"></a><span data-ttu-id="a382b-117">장면 예</span><span class="sxs-lookup"><span data-stu-id="a382b-117">Example scene</span></span>

<span data-ttu-id="a382b-118">Fingertip 시각화 예제는 트레일러 식에서 작동 하는 거의 모든 장면에서 볼 수 있지만 [HandInteractionExample 장면](../example-scenes/hand-interaction-examples.md)에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-118">You can find fingertip visualization examples in almost any scene that works with articulated hands, but is prominent in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md).</span></span>

![Fingertip 시각화 상태](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a><span data-ttu-id="a382b-120">Inspector 속성</span><span class="sxs-lookup"><span data-stu-id="a382b-120">Inspector properties</span></span>

<span data-ttu-id="a382b-121">**FingerCursor** 대부분의 손가락 커서 속성은 기본 커서 클래스에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-121">**FingerCursor** Many of the finger cursor properties are inherited from the base cursor class.</span></span> <span data-ttu-id="a382b-122">중요 한 속성에는 MixedRealityStandard 셰이더에 손가락 링 애니메이션을 구동 하는 멀리 떨어져 있는 표면 여백 및 너비가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-122">Important properties include the far / near surface margins and widths which drive the finger ring animation in the MixedRealityStandard shader.</span></span> <span data-ttu-id="a382b-123">다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-123">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

<span data-ttu-id="a382b-124">**ProximityLight** 근접 조명 설정은 화면 가까이와 멀리 떨어져 있는 경우 조명이 표시 되는 방식을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-124">**ProximityLight** The proximity light settings control how the light looks when near and far from a surface.</span></span> <span data-ttu-id="a382b-125">가운데, 가운데 및 외부 색은 조명의 그라데이션 모양을 제어 하며 응용 프로그램의 색상표에 맞게 사용자 지정이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-125">The center, middle, and outer colors control the gradient look of the light and can be custom tailored for the color palette of your application.</span></span> <span data-ttu-id="a382b-126">색은 사용자가 근접 한 조명을 위의 값으로 밝게 할 수 있도록 하는 HDR (높은 동적 범위)입니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-126">Note, the colors are HDR (High Dynamic Range) to allow users to brighten the proximity light to values above one.</span></span> <span data-ttu-id="a382b-127">다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-127">For other properties please hover over the inspector tool tips.</span></span>

<span data-ttu-id="a382b-128">**MixedRealityStandard 셰이더** MixedRealityStandard 셰이더는 MRTK의 많은 효과에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-128">**MixedRealityStandard Shader** The MixedRealityStandard shader is used for many effects in the MRTK.</span></span> <span data-ttu-id="a382b-129">Fingertip 시각화에 중요 한 두 가지 설정은 "근거리 페이드" 및 "근접 조명"입니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-129">The two settings important for fingertip visualization are "Near Fade" and "Proximity Light."</span></span> <span data-ttu-id="a382b-130">가까이 페이드를 사용 하면 개체를 카메라 또는 빛으로 페이드 인 하거나 빛을 희미하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-130">Near Fade allows objects to fade in / out as a camera or light nears them.</span></span> <span data-ttu-id="a382b-131">근접 조명이 카메라 대신 페이드를 구동 하도록 하려면 "Light"를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-131">Make sure to check "Light" to allow proximity lights to drive the fade (rather than the camera).</span></span> <span data-ttu-id="a382b-132">"페이드 Begin" 및 "페이드 완료" 값을 반대로 바꿔 페이드를 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-132">You can reverse the values of "Fade Begin" and "Fade Complete" to reverse a fade.</span></span> <span data-ttu-id="a382b-133">근접 조명을 밝게 하려는 모든 표면에 대해 "근접 조명"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-133">Check "Proximity Light" for any surface you would like the proximity light to brighten.</span></span> <span data-ttu-id="a382b-134">다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a382b-134">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
