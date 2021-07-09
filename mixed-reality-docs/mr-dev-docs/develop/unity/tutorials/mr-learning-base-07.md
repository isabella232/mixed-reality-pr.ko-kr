---
title: 3D 개체와 상호 작용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 앱에서 3D 개체와 상호 작용하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 개체 상호 작용, 경계 컨트롤
ms.localizationpriority: high
ms.openlocfilehash: cbf2bbf78a34cfdd4856b7b8d192e4ac7c2f0154
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110265"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="921ea-104">7. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="921ea-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="921ea-105">이 자습서에서는 3D 개체의 근거리 및 원거리 조작을 사용하도록 설정하고 허용되는 조작 유형을 제한하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="921ea-106">개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 컨트롤을 추가하는 방법도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="921ea-107">목표</span><span class="sxs-lookup"><span data-stu-id="921ea-107">Objectives</span></span>

* <span data-ttu-id="921ea-108">3D 개체가 상호 작용할 수 있도록 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="921ea-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="921ea-109">3D 개체에 경계 컨트롤을 추가하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="921ea-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="921ea-110">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="921ea-110">Manipulating 3D objects</span></span>

<span data-ttu-id="921ea-111">이 섹션에서는 [장면에서 개체 위치 지정](mr-learning-base-04.md) 자습서를 진행하는 동안 테이블에서 구성한 모든 Rover 파트를 조작하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="921ea-112">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="921ea-113">모든 파트 개체에 Object Manipulator(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="921ea-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="921ea-114">모든 파트 개체에 NearInteractionGrabbable 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="921ea-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="921ea-115">Object Manipulator(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="921ea-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="921ea-116">**개체를 조작** 하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="921ea-117">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="921ea-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="921ea-118">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="921ea-119">추적 손으로 개체에 대한 **조작** 및 **잡기** 를 수행하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="921ea-120">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="921ea-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="921ea-121">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="921ea-122">**NearInteractionGrabbable** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="921ea-123">또한 Rover 파트를 Rover에 배치하여 완전한 Rover 어셈블리로 만들 수 있도록 Rover Explorer를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="921ea-124">Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverParts** 개체를 펼치고, 자식 Rover 파트 개체와 **RoverAssembly** 개체를 모두 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 선택한 모든 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="921ea-125">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="921ea-126">**NearInteractionGrabbable** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="921ea-127">**Part Assembly Controller(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-127">**Part Assembly Controller (Script)** component</span></span>

![RoverAssembly 및 모든 로버 부품 개체가 선택되고 구성 요소가 추가된 Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="921ea-129">서로 인접하지 않은 여러 개체를 선택하려면 Ctrl 키를 누른 채 마우스를 사용하여 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="921ea-130">이 경우 개체 조작자(스크립트)를 추가하면 개체 조작자(스크립트)가 종속되어 있으므로 제약 조건 관리자(스크립트)가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="921ea-131">이 자습서의 학습 목표를 달성하기 위해 Rover 파트에 충돌체가 이미 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="921ea-132">충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="921ea-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="921ea-133">Part Assembly Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="921ea-134">Rover 파트 개체와 RoverAssembly 개체를 선택한 상태로, Inspector(인스펙터) 창에서 **Object Manipulator(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="921ea-135">**Two Handed Manipulation Type**(양손 조작 유형) 드롭다운에서 Scale(크기 조정) 선택을 취소하고 **Move**(이동) 및 **Rotate**(회전)만 가능하도록 설정</span><span class="sxs-lookup"><span data-stu-id="921ea-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Two Handed Manipulation Type(양손 조작 유형)이 구성된 Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="921ea-137">이제 모든 Rover 파트 개체와 RoverAssembly 개체에 대해 개체 조작이 가능하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="921ea-138">Project 창에서 **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** 폴더로 이동하여 오디오 클립을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![Audio 폴더가 선택된 Unity 프로젝트 창](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="921ea-140">Hierarchy(계층 구조) 창에서 **Rover 파트 개체** 를 다시 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **Audio Sources**(오디오 소스) 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="921ea-141">**MRTK_Scale_Start** 오디오 클립을 **AudioClip** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="921ea-142">**Play On Awake**(활성 상태일 때 재생) 확인란의 선택을 취소</span><span class="sxs-lookup"><span data-stu-id="921ea-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="921ea-143">**Spatial Blend**(공간 블렌드)를 1로 변경</span><span class="sxs-lookup"><span data-stu-id="921ea-143">Change **Spatial Blend** to 1</span></span>

![모든 로버 부품이 선택되고 Audio Source 구성 요소가 추가되고 구성된 Unity](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="921ea-145">계층 구조 창에서 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 개체를 펼쳐서 모든 배치 힌트 개체를 표시한 다음, Camera_part Rover 파트 RoverParts > **Camera_Part** 를 선택하고 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the Camera_part rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="921ea-146">**Camera_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Camera_Part PartAssemblyController 구성 요소가 구성된 Unity](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="921ea-148">나머지 Rover 파트 개체와 RoverAssembly 개체 각각에 대해 이 단계를 **반복** 하여 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="921ea-149">**Generator_Part** 의 경우 **Generator_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="921ea-150">**Lights_Part** 의 경우 **Lights_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="921ea-151">**UHFAntenna_Part** 의 경우 **UHFAntenna_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="921ea-152">**Spectrometer_Part** 의 경우 **Spectrometer_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="921ea-153">**RoverAssembly** 의 경우 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="921ea-154">Hierarchy(계층 구조) 창에서 RoverExplorer > Buttons > **Reset**(초기화) 단추 개체를 선택한 다음, Inspector(인스펙터) 창에서 상호작용 가능 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="921ea-155">**RoverAssembly** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="921ea-156">**No Function**(함수 없음) 드롭다운에서 **PartAssemblyController** > **ResetPlacement ()** 를 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정</span><span class="sxs-lookup"><span data-stu-id="921ea-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Reset 단추 개체 OnClick 이벤트가 구성된 Unity](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="921ea-158">이제 게임 모드로 전환하면 근거리 또는 원거리 상호 작용을 사용하여 Rover 파트를 Rover에 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="921ea-159">파트가 해당하는 배치 힌트에 가까워지면 위치로 맞춰져서 Rover의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="921ea-160">배치를 다시 설정하려면 Reset(초기화) 단추를 누르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-160">To reset the placements, you can press the Reset button:</span></span>

![Reset 단추가 눌러져 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="921ea-162">Object Manipulator 구성 요소 및 관련 속성에 대해 자세히 알아보려면 [MRTK 설명서 포털](/windows/mixed-reality/mrtk-unity/)에서 [Object Manipulator](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="921ea-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) guide in the [MRTK Documentation Portal](/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="921ea-163">경계 컨트롤 추가</span><span class="sxs-lookup"><span data-stu-id="921ea-163">Adding Bounds Control</span></span>

<span data-ttu-id="921ea-164">경계 컨트롤을 사용하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공하여 근거리 및 원거리 상호 작용 모두에서 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="921ea-165">이 예제에서는 전체 환경을 쉽게 이동, 회전, 확장할 수 있도록 RoverExplorer 개체에 BoundsControl을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="921ea-166">또한 경계 컨트롤을 켜고 끌 수 있도록 메뉴를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="921ea-167">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="921ea-168">**BoundsControl** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-168">**BoundsControl** component</span></span>
* <span data-ttu-id="921ea-169">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="921ea-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="921ea-170">그런 다음, 모든 구성 요소 옆에 있는 확인란을 **선택 취소** 하여 기본적으로 **사용하지 않도록 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![RoverExplorer 개체가 선택되고 구성 요소가 추가되고 사용하지 않도록 설정된 Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="921ea-172">경계 컨트롤 시각화는 런타임에 생성되므로 게임 모드로 전환하기 전에는 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="921ea-173">개체 조작자(스크립트)는 제약 조건 관리자(스크립트)를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="921ea-174">Hierarchy 창에서 Menu > **ButtonCollection** 개체를 펼쳐서 단추 4개를 표시하고 3번째 단추의 이름을 **BoundsControl_Enable** 로 변경한 다음, 인스펙터 창에서 **Button Config Helper (Script)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="921ea-175">**Main Label Text**(기본 레이블 텍스트)를 **Enable**(사용)로 변경</span><span class="sxs-lookup"><span data-stu-id="921ea-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="921ea-176">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="921ea-177">**No Function** 드롭다운에서 **BoundsControl** > **bool Enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="921ea-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="921ea-178">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="921ea-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="921ea-179">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="921ea-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="921ea-180">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="921ea-181">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="921ea-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="921ea-182">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="921ea-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="921ea-183">**아이콘** 을 'cube with bounds control'(경계 컨트롤과 큐브) 아이콘으로 유지</span><span class="sxs-lookup"><span data-stu-id="921ea-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![BoundsControl_Enable 단추 개체가 선택되고 Button Config Helper 구성 요소가 구성된 Unity](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="921ea-185">네 번째와 마지막 단추의 이름을 **BoundsControl_Disable** 로 바꾼 다음, 인스펙터 창에서 **Button Config Helper (Script)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="921ea-186">**Main Label Text**(기본 레이블 텍스트)를 **Disable**(사용 안 함)로 변경</span><span class="sxs-lookup"><span data-stu-id="921ea-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="921ea-187">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="921ea-188">**No Function** 드롭다운에서 **BoundsControl** > **bool Enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="921ea-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="921ea-189">인수 확인란이 **선택 취소** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="921ea-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="921ea-190">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="921ea-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="921ea-191">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="921ea-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="921ea-192">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="921ea-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="921ea-193">인수 확인란이 **선택 취소** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="921ea-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="921ea-194">**아이콘** 을 'cube with bounds control'(경계 컨트롤과 큐브) 아이콘으로 변경</span><span class="sxs-lookup"><span data-stu-id="921ea-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![BoundsControl_Disable 단추 개체가 선택되고 Button Config Helper 구성 요소가 구성된 Unity](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="921ea-196">이제 게임 모드로 전환하여 Enable 단추를 클릭하여 경계 컨트롤을 사용하도록 설정하면, 근거리나 원거리 상호 작용을 사용하여 경계 컨트롤을 이동 및 회전하고 크기를 조정할 수 있으며 Disable 단추를 사용하여 경계 컨트롤을 다시 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![경계 컨트롤이 조작되고 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="921ea-198">경계 컨트롤 구성 요소 및 관련 속성에 대한 자세한 정보를 보려면 [MRTK 설명서 포털](/windows/mixed-reality/mrtk-unity/)에서 [경계 컨트롤](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="921ea-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) guide in the [MRTK Documentation Portal](/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="921ea-199">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-199">Congratulations</span></span>

<span data-ttu-id="921ea-200">이 자습서에서는 3D 개체에 대한 근거리 및 원거리 조작을 사용하도록 설정하는 방법과 허용되는 조작 유형을 제한하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="921ea-201">개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 컨트롤을 추가하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="921ea-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="921ea-202">다음 자습서: 8. 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="921ea-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)