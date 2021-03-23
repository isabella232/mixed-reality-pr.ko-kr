---
title: Unreal의 편집기 확장
description: 사용자 지정 스크립트, 스크립팅된 작업 및 유틸리티 위젯을 사용하여 Unreal Engine 편집기를 확장하는 방법을 알아보세요.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, 편집기 확장, Unreal 편집기, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584920"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="2596b-104">Unreal의 편집기 확장</span><span class="sxs-lookup"><span data-stu-id="2596b-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="2596b-105">Unreal은 요구 사항에 맞게 엔진을 사용자 지정할 수 있는 광범위한 기능 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="2596b-106">단순하지만 제한적인 것부터 매우 강력하지만 복잡한 것까지 다양한 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="2596b-107">다음 단계는 복잡성 증가순으로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="2596b-108">일반적으로 더 간단한 문제 해결 방법부터 접근하고 해당 옵션을 샅샅이 살펴본 뒤에 좀 더 복잡한 옵션으로 넘어가야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="2596b-109">예를 들어 대부분의 시간 동안 플러그 인 대신 기본 생성 스크립트를 사용할 수 있다는 사실이 확인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="2596b-110">생성 스크립트</span><span class="sxs-lookup"><span data-stu-id="2596b-110">Construction scripts</span></span>

<span data-ttu-id="2596b-111">생성 스크립트를 사용하여 청사진 인스턴스가 생성될 때 실행되는 초기화 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="2596b-112">사용자 생성 스크립트</span><span class="sxs-lookup"><span data-stu-id="2596b-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="2596b-113">청사진 예제</span><span class="sxs-lookup"><span data-stu-id="2596b-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="2596b-114">비디오 자습서</span><span class="sxs-lookup"><span data-stu-id="2596b-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="2596b-115">스크립팅된 작업</span><span class="sxs-lookup"><span data-stu-id="2596b-115">Scripted actions</span></span>

<span data-ttu-id="2596b-116">스크립팅된 작업은 편집기 유틸리티 청사진입니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="2596b-117">다음을 수행하여 Unreal 편집기에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="2596b-118">콘텐츠 브라우저에서 **Assets(자산)** 를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="2596b-119">또는 수준 뷰포트 또는 월드 아웃라이너에서 **Actors(행위자)** 를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="2596b-120">스크립팅된 동작은 자산 또는 행위자 집합에 대한 상황별 인식을 포함하는 청사진 논리가 필요한 경우에 특히 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="2596b-121">일반적으로 스크립팅된 작업은 작업이 실행될 때 선택한 자산 또는 행위자의 목록을 가져온 다음, 해당 개체를 수정하거나 그래프에 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="2596b-122">스크립팅된 작업</span><span class="sxs-lookup"><span data-stu-id="2596b-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="2596b-123">프로젝트를 시작할 때 스크립팅된 작업 실행</span><span class="sxs-lookup"><span data-stu-id="2596b-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="2596b-124">편집기 유틸리티 위젯</span><span class="sxs-lookup"><span data-stu-id="2596b-124">Editor utility widgets</span></span>

<span data-ttu-id="2596b-125">새 UI 요소를 추가하고 싶을 때마다 [편집기 유틸리티](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) 위젯을 사용하여 Unreal 편집기의 UI(사용자 인터페이스)를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="2596b-126">편집기 유틸리티 위젯은 UMG(Unreal Motion Graphics)를 기반으로 하기 때문에 다른 UMG 위젯 청사진과 마찬가지로 청사진에 위젯을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="2596b-127">이러한 위젯은 편집기 UI 전용이며 사용자 지정 편집기 탭을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="2596b-128">그런 다음, 기존 편집기 탭을 선택할 때처럼 Windows 메뉴에서 이러한 사용자 지정 탭을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="2596b-129">플러그 인</span><span class="sxs-lookup"><span data-stu-id="2596b-129">Plugins</span></span>

<span data-ttu-id="2596b-130">Unreal을 사용하면 UE4 도구 및 런타임과 함께 사용할 사용자 지정 [플러그 인](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html)을 개발하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="2596b-131">Unreal 편집기에서 언제든지 플러그 인을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="2596b-132">플러그 인은 런타임 게임 플레이 기능을 추가하고, 기본 제공 엔진 기능을 수정하고, 새 파일 형식을 만들고, 편집기의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

