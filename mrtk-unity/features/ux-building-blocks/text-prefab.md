---
title: TextPrefab
description: MRTK의 TextPrefab 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489293"
---
# <a name="text-prefab"></a><span data-ttu-id="8753f-104">텍스트 prefab</span><span class="sxs-lookup"><span data-stu-id="8753f-104">Text prefab</span></span>

<span data-ttu-id="8753f-105">이러한 prefabs은 Windows Mixed Reality의 렌더링 품질에 맞게 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="8753f-106">자세한 내용은 Microsoft Windows 개발자 센터의 [Unity에서 지침 텍스트](/windows/mixed-reality/text-in-unity) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8753f-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="8753f-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="8753f-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="8753f-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="8753f-108">3DTextPrefab</span></span>

<span data-ttu-id="8753f-109">3D 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="8753f-110">(아래 지침을 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="8753f-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="8753f-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="8753f-111">UITextPrefab</span></span>

<span data-ttu-id="8753f-112">UI 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="8753f-113">(아래 지침을 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="8753f-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="8753f-114">글꼴</span><span class="sxs-lookup"><span data-stu-id="8753f-114">Fonts</span></span>

<span data-ttu-id="8753f-115">혼합 현실 도구 키트에 포함 된 오픈 소스 글꼴 (자산/MRTK/Core/StandardAssets/Fonts).</span><span class="sxs-lookup"><span data-stu-id="8753f-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8753f-116">텍스트 Prefab는 오픈 소스 글꼴 ' Selawik '를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="8753f-117">다른 글꼴로 텍스트 Prefab을 사용 하려면 글꼴 파일을 가져오고 아래 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="8753f-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="8753f-118">아래 예제에서는 텍스트 Prefab에 ' 맑은 고딕 ' 글꼴을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![맑은 고딕 글꼴 파일 가져오기](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="8753f-120">3DTextSegoeUI 재질에 글꼴 질감을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![글꼴 질감 할당](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="8753f-122">3DTextSegoeUI.mat 재질에서 셰이더 Custom/3DTextShader.shader를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![셰이더 할당](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="8753f-124">맑은 고딕 글꼴 및 3DTextSegoeUI 재질을 프리팹의 텍스트 구성 요소에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![글꼴 파일 및 재질 할당](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="8753f-126">Unity에서 글꼴 작업</span><span class="sxs-lookup"><span data-stu-id="8753f-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="8753f-127">Unity의 장면에 새 3D TextMesh를 추가할 때 시각적으로 명백한 두 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="8753f-128">하나는 글꼴이 매우 크게 표시되고 두 글꼴은 매우 흐리게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="8753f-129">검사기에서 기본 글꼴 크기 값이 0으로 설정되어 있는지도 흥미롭습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="8753f-130">실제로 13이 기본값이므로 이 0 값을 13으로 바치면 크기가 달라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="8753f-131">Unity는 장면에 추가된 모든 새 요소의 크기가 1 Unity 단위 또는 100% 변환 배율로, HoloLens에서 약 1미터로 변환된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="8753f-132">글꼴의 경우 3D TextMesh에 대한 경계 상자가 기본적으로 약 1미터 높이로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="8753f-133">글꼴 배율 및 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="8753f-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="8753f-134">대부분의 비주얼 디자이너는 포인트 를 사용하여 실제 세계와 디자인 프로그램에서 글꼴 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="8753f-135">1미터에는 약 2835(2,834.645666399962)의 지점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="8753f-136">포인트 시스템을 1미터로 변환하고 Unity의 기본 TextMesh 글꼴 크기 13을 기준으로 13을 2835로 나눈 간단한 수학은 0.0046(정확하게 0.00458611116)과 동일하지만 일부는 0.005로 반올림하려고 할 수 있지만 시작할 수 있는 좋은 표준 배율입니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="8753f-137">어느 방법을 사용하든 Text 개체 또는 컨테이너를 이러한 값으로 확장하면 디자인 프로그램에서 글꼴 크기를 1:1로 변환할 수 있을 뿐만 아니라 애플리케이션 또는 게임 전체에서 일관성을 유지하는 표준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="8753f-138">UI 텍스트</span><span class="sxs-lookup"><span data-stu-id="8753f-138">UI Text</span></span>

<span data-ttu-id="8753f-139">장면에 UI 또는 캔버스 기반 Text 요소를 추가할 때 크기 차이는 여전히 더 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="8753f-140">두 크기의 차이는 약 1000%이며, 반올림된 값의 경우 UI 기반 Text 구성 요소의 배율 비율을 0.00046(0.0004586111116)으로 가져오거나 0.0005로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="8753f-141">**고지 사항:** 모든 글꼴의 기본값은 해당 글꼴의 질감 크기 또는 글꼴을 Unity로 가져온 방법에 의해 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="8753f-142">이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![크기 조정 요소를 사용 하는 글꼴 크기](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="8753f-144">Text3DSelawik</span><span class="sxs-lookup"><span data-stu-id="8753f-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="8753f-145">3DTextPrefab에 대 한 자료는 폐색 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8753f-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="8753f-146">3DTextShader 필요 합니다. 셰이더</span><span class="sxs-lookup"><span data-stu-id="8753f-146">Requires 3DTextShader.shader</span></span>

![기본 글꼴 재질 vs 3DTextSegoeUI 재질](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="8753f-148">Text3DShader</span><span class="sxs-lookup"><span data-stu-id="8753f-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="8753f-149">폐색를 지 원하는 3DTextPrefab 용 셰이더.</span><span class="sxs-lookup"><span data-stu-id="8753f-149">Shader for 3DTextPrefab with occlusion support.</span></span>