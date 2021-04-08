---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098003"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="ab453-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="ab453-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="ab453-102">1. 기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="ab453-103">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="ab453-104">따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="ab453-105">Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(검사기) 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultXRSDKConfigurationProfile** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![DefaultHoloLens2ConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="ab453-107">다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 구성 요소 Copy & Customize 단추](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="ab453-109">Clone Profile(프로필 복제) 창에서 적절한 **Profile Name(프로필 이름)** (예: _GettingStarted_XRSDKConfigurationProfile_)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultXRSDKConfigurationProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 복제 Configuration Profile 팝업 창](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="ab453-111">이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![새로 만든 사용자 지정 HoloLens2ConfigurationProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="ab453-113">Unity 메뉴에서 **파일** > **저장** 을 선택하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="ab453-114">자습서를 진행하는 동안 항상 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="ab453-115">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="ab453-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="ab453-116">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![공간 인식 시스템이 사용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="ab453-118">향후 프로젝트에서 앱이 환경에 응답하거나 상호 작용할 필요가 없는 경우, 성능 비용을 줄이기 위해 공간 인식을 계속 해제해 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="ab453-119">3. 기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="ab453-120">다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![공간 인식 탭이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="ab453-122">Clone Profile(프로필 복제) 창에서 적절한 **프로필 이름**(예: _GettingStarted_XRSDKSpatialAwarenessSystemProfile_)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultXRSDKSpatialAwarenessSystemProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 인식 시스템 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="ab453-124">이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessSystemProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="ab453-126">4. 기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="ab453-127">다음과 같이 **Spatial Awareness(공간 인식)** 탭을 선택한 상태로 **XR SDK Windows Mixed Reality Spatial Mesh Observer(XR SDK Windows Mixed Reality 공간 메시 관찰자)** 섹션을 확장한 다음, **Clone(복제)** 단추를 클릭하여 Clone Profile(프로필 복제) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Windows Mixed Reality 공간 메시 관찰자 섹션이 확장된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="ab453-129">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 메시 관찰자 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="ab453-131">이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessMeshObserverProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="ab453-133">5. 공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="ab453-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="ab453-134">다음과 같이 **공간 메시 관찰자 설정** 에서 **표시 옵션** 을 **폐색** 으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![공간 메시 관찰자 표시 옵션이 폐색으로 설정된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="ab453-136">공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="ab453-137">예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="ab453-138">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="ab453-139">보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="ab453-140">기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="ab453-141">MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)의 [MRTK 프로필 구성 가이드](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab453-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ab453-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="ab453-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="ab453-143">1. 기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="ab453-144">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="ab453-145">따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="ab453-146">Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(검사기) 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultOpenXRConfigurationProfile** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![기본 openXR 프로필이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="ab453-148">다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![openxr 프로필의 Unity MixedRealityToolkit 구성 요소 Copy & Customize(복사 및 사용자 지정) 단추](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="ab453-150">Clone Profile(프로필 복제) 창에서 적절한 **Profile Name(프로필 이름)** (예: _GettingStarted_OpenXRConfigurationProfile_)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultOpenXRConfigurationProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![openxr 프로필의 Unity MixedRealityToolkit 복제 Configuration Profile 팝업 창](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="ab453-152">이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![새로 만든 사용자 지정 OpenXR이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="ab453-154">Unity 메뉴에서 **파일** > **저장** 을 선택하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="ab453-155">자습서를 진행하는 동안 항상 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="ab453-156">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="ab453-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="ab453-157">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![공간 인식 시스템이 사용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="ab453-159">향후 프로젝트에서 앱이 환경에 응답하거나 상호 작용할 필요가 없는 경우, 성능 비용을 줄이기 위해 공간 인식을 계속 해제해 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="ab453-160">3. 기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="ab453-161">다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![공간 인식 탭이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="ab453-163">Clone Profile(프로필 복제) 창에서 적절한 **프로필 이름**(예: GettingStarted_OpenXRSpatialAwarenessSystemProfile)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultXRSDKSpatialAwarenessSystemProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 인식 시스템 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="ab453-165">이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessSystemProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="ab453-167">4. 기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="ab453-168">다음과 같이 **Spatial Awareness(공간 인식)** 탭을 선택한 상태로 **XR SDK Windows Mixed Reality Spatial Mesh Observer(XR SDK Windows Mixed Reality 공간 메시 관찰자)** 섹션을 확장한 다음, **Clone(복제)** 단추를 클릭하여 Clone Profile(프로필 복제) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Windows Mixed Reality 공간 메시 관찰자 섹션이 확장된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="ab453-170">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 메시 관찰자 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="ab453-172">이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessMeshObserverProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="ab453-174">5. 공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="ab453-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="ab453-175">다음과 같이 **공간 메시 관찰자 설정** 에서 **표시 옵션** 을 **폐색** 으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![공간 메시 관찰자 표시 옵션이 폐색으로 설정된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="ab453-177">공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="ab453-178">예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="ab453-179">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="ab453-180">보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="ab453-181">기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="ab453-182">MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)의 [MRTK 프로필 구성 가이드](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab453-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="ab453-183">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="ab453-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="ab453-184">1. 기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="ab453-185">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="ab453-186">따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="ab453-187">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **MixedRealityToolkit** 구성 프로필을 **DefaultHoloLens2ConfigurationProfile** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![DefaultHoloLens2ConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="ab453-189">다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 구성 요소 Copy & Customize 단추](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="ab453-191">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_HoloLens2ConfigurationProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultHololens2ConfigurationProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 복제 Configuration Profile 팝업 창](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="ab453-193">이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![새로 만든 사용자 지정 HoloLens2ConfigurationProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="ab453-195">Unity 메뉴에서 **파일** > **저장** 을 선택하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="ab453-196">자습서를 진행하는 동안 항상 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="ab453-197">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="ab453-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="ab453-198">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![공간 인식 시스템이 사용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="ab453-200">향후 프로젝트에서 앱이 환경에 응답하거나 상호 작용할 필요가 없는 경우, 성능 비용을 줄이기 위해 공간 인식을 계속 해제해 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="ab453-201">3. 기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="ab453-202">다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![공간 인식 탭이 선택된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="ab453-204">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessSystemProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 인식 시스템 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="ab453-206">이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessSystemProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="ab453-208">4. 기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="ab453-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="ab453-209">다음과 같이 **공간 인식** 탭을 선택한 상태로 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장한 다음, **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Windows Mixed Reality 공간 메시 관찰자 섹션이 확장된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="ab453-211">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 복제 공간 메시 관찰자 프로필 팝업 창](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="ab453-213">이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessMeshObserverProfile이 적용된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="ab453-215">5. 공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="ab453-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="ab453-216">다음과 같이 **공간 메시 관찰자 설정** 에서 **표시 옵션** 을 **폐색** 으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![공간 메시 관찰자 표시 옵션이 폐색으로 설정된 Unity MixedRealityToolkit 구성 요소](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="ab453-218">공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="ab453-219">예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="ab453-220">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="ab453-221">보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="ab453-222">기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab453-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="ab453-223">MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)의 [MRTK 프로필 구성 가이드](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab453-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
