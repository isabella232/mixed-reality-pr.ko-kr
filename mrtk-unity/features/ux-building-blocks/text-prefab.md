---
title: 텍스트 prefab
description: MRTK의 TextPrefab 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, TMP,
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175641"
---
# <a name="text-prefab"></a><span data-ttu-id="7b257-104">텍스트 prefab</span><span class="sxs-lookup"><span data-stu-id="7b257-104">Text prefab</span></span>

<span data-ttu-id="7b257-105">이러한 prefabs는 Windows Mixed Reality의 렌더링 품질에 맞게 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="7b257-106">자세한 내용은 Microsoft Windows 개발자 센터에서 [Unity의 지침 텍스트](/windows/mixed-reality/text-in-unity) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b257-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="7b257-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="7b257-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="7b257-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="7b257-108">3DTextPrefab</span></span>

<span data-ttu-id="7b257-109">3D 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="7b257-110">(아래 지침을 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="7b257-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="7b257-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="7b257-111">UITextPrefab</span></span>

<span data-ttu-id="7b257-112">UI 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="7b257-113">(아래 지침을 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="7b257-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="7b257-114">글꼴</span><span class="sxs-lookup"><span data-stu-id="7b257-114">Fonts</span></span>

<span data-ttu-id="7b257-115">혼합 현실 Toolkit에 포함 된 오픈 소스 글꼴 (자산/MRTK/Core/StandardAssets/Fonts)입니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b257-116">텍스트 Prefab는 오픈 소스 글꼴 ' Selawik '를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="7b257-117">다른 글꼴로 텍스트 Prefab을 사용 하려면 글꼴 파일을 가져오고 아래 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="7b257-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="7b257-118">아래 예제에서는 텍스트 Prefab에 ' 맑은 고딕 ' 글꼴을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![맑은 고딕 글꼴 파일 가져오기](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="7b257-120">3DTextSegoeUI 재질에 글꼴 질감을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![글꼴 질감 할당](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="7b257-122">3DTextSegoeUI 재질에서 셰이더 Custom/3DTextShader를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![셰이더 할당](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="7b257-124">Prefabs의 텍스트 구성 요소에 맑은 고딕 font 및 3DTextSegoeUI 재질을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![글꼴 파일 및 재질 할당](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="7b257-126">Unity에서 글꼴 작업</span><span class="sxs-lookup"><span data-stu-id="7b257-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="7b257-127">Unity에서 장면에 새 3D TextMesh를 추가 하는 경우 시각적으로 눈에 띄는 두 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="7b257-128">하나는 글꼴이 매우 크고 두 번 표시 되 면 글꼴이 매우 흐리게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="7b257-129">또한 검사기에서 기본 글꼴 크기 값이 0으로 설정 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="7b257-130">이 값이 0 인 값을 13으로 바꾸면 13이 실제로 기본값 이기 때문에 크기 차이는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="7b257-131">Unity는 장면에 추가 된 모든 새 요소가 1 개의 Unity 단위 또는 100% Transform 배율 (HoloLens에서 약 1 미터로 변환 됨) 이라고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="7b257-132">글꼴의 경우 3D TextMesh의 경계 상자는 기본적으로 높이의 약 1 미터에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="7b257-133">글꼴 배율 및 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="7b257-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="7b257-134">대부분의 비주얼 디자이너에서는 요소를 사용 하 여 실제 세계의 글꼴 크기와 디자인 프로그램을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="7b257-135">1 미터에 약 2835 (2, 834.645666399962) 점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="7b257-136">1 미터에 대 한 시점 시스템 변환과 Unity의 기본 TextMesh 글꼴 크기인 13을 기반으로 하 여 2835 13의 단순 수학 13은 0.0046 (정확 하 게 0.004586111116)로 시작 하는 데 적합 한 표준 크기를 제공 합니다. 단, 일부는 0.005로 반올림 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="7b257-137">어느 방법을 사용 하 든 텍스트 개체 또는 컨테이너를 이러한 값으로 크기를 조정 하면 디자인 프로그램에서의 글꼴 크기를 1:1으로 변환할 수 있을 뿐만 아니라 응용 프로그램 또는 게임 전체에서 일관성을 유지 하는 표준도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="7b257-138">UI 텍스트</span><span class="sxs-lookup"><span data-stu-id="7b257-138">UI Text</span></span>

<span data-ttu-id="7b257-139">장면에 UI 또는 canvas 기반 텍스트 요소를 추가 하는 경우 차이가 크기는 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="7b257-140">두 크기의 차이점은 약 1000% 이며,이는 UI 기반 텍스트 구성 요소에 대 한 배율 인수를 0.00046 (정확 하 게 0.0004586111116) 또는 0.0005 (반올림 된 값)로 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="7b257-141">고 **지** 사항: 글꼴의 기본값은 해당 글꼴의 질감 크기 또는 해당 글꼴을 Unity로 가져온 방법에 의해 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="7b257-142">이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![크기 조정 요소를 사용 하는 글꼴 크기](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="7b257-144">Text3DSelawik</span><span class="sxs-lookup"><span data-stu-id="7b257-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="7b257-145">3DTextPrefab에 대 한 자료는 폐색 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b257-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="7b257-146">3DTextShader 필요 합니다. 셰이더</span><span class="sxs-lookup"><span data-stu-id="7b257-146">Requires 3DTextShader.shader</span></span>

![기본 글꼴 재질 vs 3DTextSegoeUI 재질](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="7b257-148">Text3DShader</span><span class="sxs-lookup"><span data-stu-id="7b257-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="7b257-149">폐색를 지 원하는 3DTextPrefab 용 셰이더.</span><span class="sxs-lookup"><span data-stu-id="7b257-149">Shader for 3DTextPrefab with occlusion support.</span></span>
