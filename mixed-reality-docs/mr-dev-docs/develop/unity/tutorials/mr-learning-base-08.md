---
title: 시선 추적 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 앱에서 시선 추적을 사용하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 시선 추적
ms.localizationpriority: high
ms.openlocfilehash: a5b93b9e66ffb1e4e9f60251cdc146f48005ae8b
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110713761"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="0385b-104">8. 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="0385b-104">8. Using eye-tracking</span></span>

<span data-ttu-id="0385b-105">이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0385b-106">이 프로젝트를 HoloLens(첫 번째 세대)에 배포하는 경우에는 HoloLens 2에서만 시선 추적이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="0385b-107">목표</span><span class="sxs-lookup"><span data-stu-id="0385b-107">Objectives</span></span>

* <span data-ttu-id="0385b-108">HoleLens 2에 대한 시선 추적을 사용하도록 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="0385b-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="0385b-109">시선 추적을 사용하여 작업을 트리거하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="0385b-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="0385b-110">시선 응시 입력 기능이 활성화되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="0385b-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="0385b-111">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **MRTK용 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **시선 응시 입력 기능 사용** 이 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-111">In the Unity menu, select Mixed Reality > Toolkit > Utilities > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity MRTK Project Configurator 창](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0385b-113">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성한 경우 [MRTK Project Configurator 설정 적용](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 동안에는 응시 입력 기능이 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="0385b-114">그러나 사용하도록 설정되지 않은 경우 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="0385b-115">응시 공급자에서 시선 기반 응시 사용</span><span class="sxs-lookup"><span data-stu-id="0385b-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="0385b-116">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="0385b-117">**DefaultHoloLens2InputSystemProfile** 을 복제하고 적절한 이름(예: _GettingStarted_HoloLens2InputSystemProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="0385b-118">**포인터** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="0385b-119">**DefaultMixedRealityPointerProfile** 을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityPointerProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="0385b-120">**응시 설정** 섹션을 찾고 **시선 추적 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![새로 만든 프로필이 적용되고 시선 추적을 사용하도록 설정된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="0385b-122">MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0385b-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="0385b-123">Unity 편집기에 대해 시뮬레이션된 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="0385b-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="0385b-124">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **입력** 탭으로 이동한 다음, 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="0385b-125">**입력 데이터 공급자** > **입력 시뮬레이션 서비스** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="0385b-126">**DefaultMixedRealityInputSimulationProfile** 을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityInputSimulationProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="0385b-127">**Eye Gaze Simulation(눈 응시 시뮬레이션)** 를 찾고 **Default Eye Gaze Simulation Mode(기본 눈 응시 시뮬레이션 모드)** 를 **Camera Forward Axis(카메라 전방 축)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![TextMeshPro 개체가 선택된 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="0385b-129">개체에 시선 추적 추가</span><span class="sxs-lookup"><span data-stu-id="0385b-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="0385b-130">Hierarchy(계층 구조) 창에서 **RoverExplorer** > **Buttons** 를 확장한 다음, 세 개의 자식 단추 개체를 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-130">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Button 개체가 선택된 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="0385b-132">세 개의 Button 개체를 모두 선택한 상태로 Inspector 창에서 **구성 요소 추가** 단추를 사용하여 **EyeTrackingTarget** 구성 요소를 선택한 모든 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-132">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![TextMeshPro 개체가 선택되고 구성 요소가 추가된 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="0385b-134">Hierarchy(계층 구조) 창에서 **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro** 를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-134">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="0385b-135">그런 다음, Hierarchy(계층 구조) 창에서 **Hints** 단추 개체를 선택하고, 다음과 같이 **EyeTrackingTarget** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-135">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="0385b-136">**On Look At Start ()** 이벤트 섹션에서</span><span class="sxs-lookup"><span data-stu-id="0385b-136">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="0385b-137">작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="0385b-138">**Hints** 단추의 **TextMeshPro** 개체를 **None (Object)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="0385b-139">**No Function**(함수 없음) 드롭다운에서 **TextMeshPro** > **float fontSize** 를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="0385b-140">인수를 **0.06** 으로 설정하여 현재 글꼴 크기인 0.04 x 50%를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-140">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="0385b-141">**On Look Away ()** 이벤트 섹션에서</span><span class="sxs-lookup"><span data-stu-id="0385b-141">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="0385b-142">작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-142">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="0385b-143">**Hints** 단추의 **TextMeshPro** 개체를 **None (Object)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-143">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="0385b-144">**No Function**(함수 없음) 드롭다운에서 **TextMeshPro** > **float fontSize** 를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-144">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="0385b-145">인수를 **0.04** 로 설정하여 글꼴 크기를 0.04로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-145">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Hints TextMeshPro 개체가 선택되고 EyeTrackingTarget 구성 요소가 구성된 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="0385b-147">**Explode** 및 **Reset** 단추 개체에 대해 이 단계를 **반복** 하여 나머지 단추에 대해 시선 추적을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-147">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="0385b-148">이제 게임 모드로 들어간 다음, 마우스 오른쪽 버튼을 누른 상태에서 시선이 버튼 중 하나에 닿을 때까지 마우스를 움직이면 텍스트 글꼴 크기가 50%씩 증가하고 시선을 돌렸을 때 원래 크기로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-148">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![시선 추적 대상 Explode 단추 레이블을 응시하고 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="0385b-150">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-150">Congratulations</span></span>

<span data-ttu-id="0385b-151">이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="0385b-151">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0385b-152">다음 자습서: 9. 음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="0385b-152">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
