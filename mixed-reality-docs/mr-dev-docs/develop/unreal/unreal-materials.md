---
title: Unreal의 재질 권장 사항
description: Unreal engine의 재질 개요.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 개발, 자료, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609574"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="84561-104">Unreal의 재질 권장 사항</span><span class="sxs-lookup"><span data-stu-id="84561-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="84561-105">사용 하는 자료는 Unreal Engine에서 프로젝트가 얼마나 잘 실행 될 지에 직접적으로 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-105">The materials you use can directly affect how well your projects run in Unreal Engine.</span></span> <span data-ttu-id="84561-106">이 페이지는 혼합 현실 응용 프로그램에서 최상의 성능을 얻기 위해 사용 해야 하는 기본 설정에 대 한 빠른 시작 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-106">This page acts as a quick-start for the basic settings you should be using to get the best performance out of your mixed reality applications.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="84561-107">CustomizedUVs 사용</span><span class="sxs-lookup"><span data-stu-id="84561-107">Using CustomizedUVs</span></span>

<span data-ttu-id="84561-108">재질에 UV 바둑판식 배열을 제공 해야 하는 경우 텍스처 노드의 UV를 직접 수정 하는 대신 CustomizedUVs를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-108">If you need to provide UV tiling on your material, use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="84561-109">CustomizedUVs를 사용 하면 픽셀 셰이더가 아닌 꼭 짓 점 셰이더에서 UVs를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-109">CustomizedUVs let you manipulate UVs in the Vertex shaders rather than the Pixel shader.</span></span>

![진짜의 재질 설정](images/unreal-materials-img-01c.png)

<span data-ttu-id="84561-111">다음 스크린샷에서 [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 및 모범 사례 예제에서 자료 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-111">You can find material details in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="84561-112">[ ![ 실제 ](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox) 
 *권장 자료* 설정의 권장 자료 설정</span><span class="sxs-lookup"><span data-stu-id="84561-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="84561-113">실제 권장 되지 않는 재질 설정 [ ![ 의 권장 되지 않는 재질 설정 ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *Non-recommended material setup*</span><span class="sxs-lookup"><span data-stu-id="84561-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="84561-114">Blend 모드 변경</span><span class="sxs-lookup"><span data-stu-id="84561-114">Changing Blend Mode</span></span>

<span data-ttu-id="84561-115">그렇지 않은 경우에는 강한 이유가 없으면 blend 모드를 불투명 모드로 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-115">We recommend setting the blend mode to opaque unless there's a strong reason to do otherwise.</span></span> <span data-ttu-id="84561-116">마스킹된 및 반투명 자료는 느립니다.</span><span class="sxs-lookup"><span data-stu-id="84561-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="84561-117">자료에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Blend 모드 변경](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="84561-119">모바일에 대 한 조명 업데이트</span><span class="sxs-lookup"><span data-stu-id="84561-119">Updating lighting for mobile</span></span>

<span data-ttu-id="84561-120">전체 전체 자릿수가 꺼져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-120">Full precision should be turned off.</span></span> <span data-ttu-id="84561-121">방향 정보를 켜서 Lightmap 조명을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="84561-122">이 기능을 사용 하지 않도록 설정 하면 lightmaps의 조명이 평면 이지만 비용이 저렴 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Unreal의 모바일 재질 설정](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="84561-124">전방 음영 조정</span><span class="sxs-lookup"><span data-stu-id="84561-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="84561-125">이러한 옵션은 성능 비용으로 시각적 충실도를 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="84561-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="84561-126">최대 성능을 위해 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-126">They should be turned off for maximum performance.</span></span>

![Unreal의 전방 음영 재질 설정](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="84561-128">재질 반투명도 설정</span><span class="sxs-lookup"><span data-stu-id="84561-128">Setting material translucency</span></span>

<span data-ttu-id="84561-129">블 룸 또는 DOF의 반투명 재질에 영향을 주지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84561-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="84561-130">MR에서는 이러한 효과가 거의 없기 때문에이 설정은 기본적으로 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Unreal의 모바일 개별 반투명도 설정](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="84561-132">선택적 설정</span><span class="sxs-lookup"><span data-stu-id="84561-132">Optional settings</span></span>

<span data-ttu-id="84561-133">다음 설정을 사용 하면 성능이 향상 될 수 있지만 특정 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="84561-134">해당 기능이 필요하지 않는 경우에만 이 설정을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="84561-134">Only use these settings if you're sure you don't need the features in question.</span></span>

![Unreal의 선택적 재질 설정](images/unreal-materials-img-06.jpg)

<span data-ttu-id="84561-136">재질에 반사 또는 빛이 필요 하지 않은 경우이 옵션을 설정 하면 성능이 크게 향상 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="84561-137">내부 테스트에서 조명 정보를 제공 하는 동안 "unlit" 만큼 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="84561-137">In internal testing, it's as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="84561-138">모범 사례</span><span class="sxs-lookup"><span data-stu-id="84561-138">Best practices</span></span>

<span data-ttu-id="84561-139">다음은 자료와 관련 된 모범 사례 만큼 "설정" 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-139">The following aren't "settings" as much as they're best practices related to Materials.</span></span>

<span data-ttu-id="84561-140">매개 변수를 만들 때 가능 하면 "정적 매개 변수"를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="84561-141">정적 스위치를 사용 하 여 런타임 비용 없이 재질의 전체 분기를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="84561-142">인스턴스는 서로 다른 값을 가질 수 있으므로 템플릿 셰이더를 설정 하 여 성능 손실을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-142">Instances can have different values, making it possible to have a templated shader set up with no performance loss.</span></span> <span data-ttu-id="84561-143">단점은 셰이더 재컴파일을 발생 시키는 여러 순열이 생성 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84561-143">The downside, is that several permutations are created that will cause shader recompilation.</span></span> <span data-ttu-id="84561-144">재질의 정적 매개 변수 수와 사용 되는 정적 매개 변수의 순열의 수를 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are used.</span></span> <span data-ttu-id="84561-145">문서를 렌더링 하는 방법에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![재질 설정에 대 한 모범 사례](images/unreal-materials-img-07.jpg)

<span data-ttu-id="84561-147">재질 인스턴스를 만들 때 재질에 대해 재료 인스턴스 **상수** 에 대 한 기본 설정을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84561-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="84561-148">**재질 인스턴스 상수** 는 런타임 전 한 번만 계산 하는 인스턴스화된 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="84561-148">**Material Instance Constant** is an instanced Material that calculates only once before runtime.</span></span>

<span data-ttu-id="84561-149">콘텐츠 브라우저를 통해 만든 재질 인스턴스 (**재질 인스턴스 > 만들기를 마우스 오른쪽 단추로 클릭**)는 재질 인스턴스 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="84561-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="84561-150">자재 인스턴스 동적은 코드를 통해 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84561-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="84561-151">자료 인스턴스에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Unreal에서 재질 인스턴스 만들기](images/unreal-materials-img-08.png)

<span data-ttu-id="84561-153">재질/셰이더의 복잡성에 주목 하세요.</span><span class="sxs-lookup"><span data-stu-id="84561-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="84561-154">플랫폼 통계 아이콘을 클릭 하 여 다양 한 플랫폼에서 자료의 비용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="84561-155">또한, [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)에서 자료에 대 한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Unreal에서 재질 인스턴스 동적 설정 만들기](images/unreal-materials-img-09.png)

<span data-ttu-id="84561-157">셰이더 복잡성 [보기 모드](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)를 통해 셰이더의 상대적 복잡도를 빠르게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84561-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="84561-158">보기 모드 바로 가기 키: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="84561-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="84561-159">콘솔 명령: viewmode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="84561-159">Console command: viewmode shadercomplexity</span></span>

![실수부의 자재 복잡성](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="84561-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84561-161">See also</span></span>
* [<span data-ttu-id="84561-162">모바일 자료</span><span class="sxs-lookup"><span data-stu-id="84561-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="84561-163">보기 모드</span><span class="sxs-lookup"><span data-stu-id="84561-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="84561-164">재질 인스턴스</span><span class="sxs-lookup"><span data-stu-id="84561-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
