---
title: 예제 Hub
description: '예: MRTK의 장면 개요'
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 212fc6e1489a22995241368a9bf4db96d206c44a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144755"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="e150a-104">MRTK 예제 허브</span><span class="sxs-lookup"><span data-stu-id="e150a-104">MRTK Examples Hub</span></span>

![MRTK 예제 허브](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="e150a-106">MRTK 예제 허브는 여러 장면을 쉽게 경험할 수 있도록 하는 Unity 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="e150a-107">MRTK의 장면 시스템을 사용 하 여 장면을 로드 & 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="e150a-108">**MRTKExamplesHub** 는 및를 비롯 한 공유 구성 요소가 있는 컨테이너 장면입니다. ``MixedRealityToolkit`` ``MixedRealityPlayspace``</span><span class="sxs-lookup"><span data-stu-id="e150a-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="e150a-109">**MRTKExamplesHubMainMenu** 장면에는 큐브 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="e150a-110">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e150a-110">Prerequisite</span></span>

<span data-ttu-id="e150a-111">MRTK 예제 허브는 [장면 전환 서비스](../extensions/scene-transition-service.md) 와 관련 스크립트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="e150a-112">Unity 패키지를 통해 MRTK를 사용 하는 경우 [릴리스 패키지](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)의 일부인 **MixedReality** . x. x. x. x. x. x. x. x. x. x. x. x. x. x. x. x. x.</span><span class="sxs-lookup"><span data-stu-id="e150a-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="e150a-113">리포지토리 클론을 통해 MRTK를 사용 하는 경우 프로젝트에 **mrtk/Extensions** 폴더가 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="e150a-114">MRTKExamplesHub 장면 및 장면 시스템</span><span class="sxs-lookup"><span data-stu-id="e150a-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="e150a-115"> `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace 및 LoadHubOnStartup를 사용 하 여 빈 장면에 있는 MRTKExamplesHub을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="e150a-116">이 장면은 MRTK의 장면 시스템을 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="e150a-117">`MixedRealitySceneSystem`MixedRealityToolkit 아래를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="e150a-118">그러면 검사기 패널에 장면 시스템 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="e150a-119">검사기 아래쪽에는 장면 시스템 프로필에 정의 된 장면의 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="e150a-120">장면 이름을 클릭 하 여 로드/언로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="e150a-121">목록에서 장면 이름을 클릭 하 여 _MRTKExamplesHub_ 장면을 로드 하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="e150a-122">_HandInteractionExamples_ 장면을 로드 하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="e150a-123">여러 장면을 로드 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="e150a-124">장면 실행</span><span class="sxs-lookup"><span data-stu-id="e150a-124">Running the scene</span></span>

<span data-ttu-id="e150a-125">장면은 Unity의 게임 모드와 장치에서 모두 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="e150a-126">Unity 편집기에서 **MRTKExamplesHub** 장면을 실행 하 고 MRTK의 입력 시뮬레이션을 사용 하 여 장면 콘텐츠와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="e150a-127">빌드 및 배포를 수행 하려면 장면 시스템의 목록에 포함 된 다른 장면으로 **MRTKExamplesHub** 장면을 빌드 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="e150a-128">또한 검사기를 사용 하 여 빌드 설정에 장면을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="e150a-129">빌딩 설정에서 **MRTKExamplesHub** 장면이 인덱스 0의 목록 맨 위에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="e150a-130">MRTKExamplesHub가 장면을 로드 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e150a-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="e150a-131">**MRTKExamplesHub** 장면에서 prefab를 찾을 수 있습니다 ``ExamplesHubButton`` .</span><span class="sxs-lookup"><span data-stu-id="e150a-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="e150a-132">을 포함 하는 prefab에는 **FrontPlate** 개체가 있습니다 ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="e150a-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="e150a-133">Interactable의 ``OnClick()`` 및 이벤트를 사용 하 여 ``OnTouch()`` **loadcontentscene** 스크립트의 **loadcontent ()** 함수를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="e150a-134">**Loadcontentscene** 스크립트의 검사기에서 로드할 장면 이름을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="e150a-135">이 스크립트는 장면 시스템의 LoadContent () 함수를 사용 하 여 장면을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="e150a-136">자세한 내용은 [시스템 장면](../scene-system/scene-system-getting-started.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e150a-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="e150a-137">주 메뉴 장면으로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="e150a-137">Returning to the main menu scene</span></span>

<span data-ttu-id="e150a-138">주 메뉴 장면 (MRTKExamplesHubMainMenu 장면)으로 돌아가려면 동일한 장면 시스템 메서드를 사용할 수 있습니다 `LoadContent()` .</span><span class="sxs-lookup"><span data-stu-id="e150a-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="e150a-139">**ToggleFeaturesPanelExamplesHub prefab** 는 **loadcontentscene** 스크립트를 포함 하는 ' 홈 ' 단추를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="e150a-140">이 prefab를 사용 하거나 각 장면에서 사용자 지정 홈 단추를 제공 하 여 사용자가 주 장면으로 돌아올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="e150a-141">**MRTKExamplesHub** 는 공유 컨테이너 장면 이므로 항상 표시 되도록 **ToggleFeaturesPanelExamplesHub prefab** 을 **MRTKExamplesHub** 장면에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="e150a-142">각 예제 장면에서 **Prefab ToggleFeaturesPanel** 을 숨기 거 나 비활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="e150a-143">추가 단추 추가</span><span class="sxs-lookup"><span data-stu-id="e150a-143">Adding additional buttons</span></span>

<span data-ttu-id="e150a-144">**CubeCollection** 개체에서 _ExampleHubButton_ 프리팹을 복제(또는 추가)하고 에서 **컬렉션 업데이트를** `GridObjectCollection` 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="e150a-145">그러면 새 총 단추 수에 따라 실린더 레이아웃이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="e150a-146">자세한 내용은 [개체 컬렉션](../ux-building-blocks/object-collection.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e150a-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="e150a-147">단추를 추가한 후 **LoadContentScene** 스크립트(위에서 설명)에서 장면 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="e150a-148">장면 시스템의 프로필에 장면을 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e150a-148">Add additional scenes to the Scene System's profile.</span></span>
