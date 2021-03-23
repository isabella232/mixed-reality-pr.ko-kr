---
title: 일반적인 유용한 정보
description: Unreal Engine에서 혼합 현실 애플리케이션을 개발할 때 권장되는 모든 최신 모범 사례를 파악하세요.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, 편집기 확장, Unreal 편집기, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584905"
---
# <a name="general-best-practices"></a><span data-ttu-id="93a1a-104">일반적인 유용한 정보</span><span class="sxs-lookup"><span data-stu-id="93a1a-104">General best practices</span></span>

<span data-ttu-id="93a1a-105">다음은 혼합 현실용 Unreal Engine 프로젝트를 만들 때 모든 개발자에게 권장되는 몇 가지 일반적인 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-105">The following are some general best practices we recommend all developers follow when creating an Unreal Engine project for Mixed Reality.</span></span>

## <a name="constructors"></a><span data-ttu-id="93a1a-106">생성자</span><span class="sxs-lookup"><span data-stu-id="93a1a-106">Constructors</span></span>

<span data-ttu-id="93a1a-107">청사진에 "생성자"와 동일한 항목이 필요한 경우 Unreal의 [생성 스크립트](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-107">If you need the equivalent of a "constructor" in blueprints, use Unreals' [construction script](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html).</span></span> <span data-ttu-id="93a1a-108">"BeginPlay" 이벤트를 사용하는 경우와 비교할 때 주요 이점은 "편집기"에서도 생성자 스크립트가 실행된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-108">The primary advantage over using "BeginPlay" events is the constructor script runs in the "editor" as well.</span></span> <span data-ttu-id="93a1a-109">대부분의 경우에는 값을 시작 시 바로 캐시하거나 컴파일 시에도 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-109">Most of the time the values can be cached right at the start or even at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="93a1a-110">[편집기 확장 개요](unreal-editor-extensions.md#construction-scripts)에서 생성 스크립트에 대한 추가 지원 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-110">You can find more supporting information for Construction scripts in our [editor extensions overview](unreal-editor-extensions.md#construction-scripts).</span></span>

## <a name="3d-buttons-and-textures"></a><span data-ttu-id="93a1a-111">3D 단추 및 질감</span><span class="sxs-lookup"><span data-stu-id="93a1a-111">3D buttons and textures</span></span>

<span data-ttu-id="93a1a-112">혼합 현실 애플리케이션에서 3D 단추를 만드는 중이거나 사용할 계획이 있다면 성능에 대해 생각하는 것이 당연합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-112">It's natural to think about performance when creating or planning to use 3D buttons in mixed reality applications.</span></span> <span data-ttu-id="93a1a-113">그러나 모든 것이 메시에서 제작되어 3D로 인식될 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-113">However, not everything has to be made from meshes to be perceived as 3D.</span></span> <span data-ttu-id="93a1a-114">질감이 정교하게 만들어진 Paper2D를 사용하여 3D 모양을 구현하는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-114">You have the option of using Paper2D with carefully crafted textures to get that 3D look.</span></span> <span data-ttu-id="93a1a-115">이는 3D로 "보이는" 단추에 정말 잘 맞지만 쿼드의 포토샵 이미지일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-115">This works really well for buttons that "seem" 3D, but are just photoshopped images on a quad.</span></span> <span data-ttu-id="93a1a-116">이러한 이미지의 고급 버전을 [스프라이트](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-116">A fancy version of these is called a [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).</span></span>

## <a name="variants"></a><span data-ttu-id="93a1a-117">변형</span><span class="sxs-lookup"><span data-stu-id="93a1a-117">Variants</span></span>

<span data-ttu-id="93a1a-118">런타임에 여러 개체 구성이 포함된 장면을 만드는 시나리오에서는 [Unreal 변형](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-118">Use [Unreal Variants](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) in scenarios where you're creating a scene with multiple object configurations at runtime.</span></span> <span data-ttu-id="93a1a-119">변형에는 재질 또는 메시 변경이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-119">Variations can include changing materials or meshes.</span></span> 

## <a name="animation"></a><span data-ttu-id="93a1a-120">애니메이션</span><span class="sxs-lookup"><span data-stu-id="93a1a-120">Animation</span></span>

<span data-ttu-id="93a1a-121">"상호 작용 가능한 애니메이션"을 많이 만드는 경우 [스플라인 구성 요소](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html)(스플라인 "메시" 구성 요소가 아님) 및 [타임라인 노드](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)를 활용하세요.</span><span class="sxs-lookup"><span data-stu-id="93a1a-121">Take advantage of the [Spline component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (not the Spline "Mesh" Component) and [Timeline nodes](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) if you're creating lots of "interactable animations".</span></span> 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a><span data-ttu-id="93a1a-122">통신</span><span class="sxs-lookup"><span data-stu-id="93a1a-122">Communications</span></span>

<span data-ttu-id="93a1a-123">개체를 동적으로 찾는 데 문제가 있거나 여러 행위자와 청사진 간에 통신하는 데 너무 많은 대역폭을 사용 중인 경우 [수준 청사진](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-123">Use a [Level Blueprint](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) if you're having trouble dynamically finding objects or using too much bandwidth to communicate between multiple actors and blueprints.</span></span> <span data-ttu-id="93a1a-124">Unreal Engine 4는 Unity와 달리, 모든 것이 구성 요소 내부에 있을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-124">Remember, Unreal Engine 4 isn't like Unity, not everything has to be inside a component.</span></span> <span data-ttu-id="93a1a-125">수준 청사진은 여러 행위자 간의 통신을 단순화할 때 권장되는 완벽한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-125">Level Blueprints are a perfectly valid and recommended way of simplifying the communication between multiple actors.</span></span> <span data-ttu-id="93a1a-126">수준 청사진의 OnBeginPlay에서 시작 시 개체 참조를 "캐시"할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-126">Object references can even be "cached" at startup in the Level Blueprint's OnBeginPlay.</span></span>

## <a name="global-state"></a><span data-ttu-id="93a1a-127">전역 상태</span><span class="sxs-lookup"><span data-stu-id="93a1a-127">Global state</span></span>

<span data-ttu-id="93a1a-128">점수, 수준 데이터, 플레이어 관련 정보 또는 특정 개체에 속하지 않는 다른 항목 등의 수준별 상태를 저장해야 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-128">You'll often need to store level-specific state like score, level data, player-specific information, or anything else that doesn't quite belong to a particular object.</span></span> <span data-ttu-id="93a1a-129">[GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)를 간과하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="93a1a-129">Don't overlook the [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html).</span></span> <span data-ttu-id="93a1a-130">대부분의 사람들은 GameMode가 존재한다는 것을 잊고 있지만 GameMode는 수준별로 생성할 수 있으며 각 수준과 관련된 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-130">Most people forget that it exists, but the GameMode can be created per level, and contain data specific to each level.</span></span>

## <a name="optimizing-blueprints"></a><span data-ttu-id="93a1a-131">청사진 최적화</span><span class="sxs-lookup"><span data-stu-id="93a1a-131">Optimizing Blueprints</span></span>

<span data-ttu-id="93a1a-132">청사진을 찾는 데 너무 오래 걸릴 경우 Unreal에서 청사진을 "네이티브화"한 후 재정렬하여 C++로 코드를 다시 작성하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93a1a-132">If you're finding your blueprints to be too slow, let Unreal "nativize" your blueprints before resorting to rewriting the code in c++.</span></span> <span data-ttu-id="93a1a-133">사용자 지정 솔루션을 만들기 전에 자동 [네이티브화](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="93a1a-133">Try using the automatic [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) before creating your own custom solution.</span></span>

![청사진 네이티브화 방법에서 포괄이 강조 표시된 청사진 설정](images/unreal-general-practices-img-01.jpg)
