---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097495"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="e150e-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="e150e-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="e150e-102">시선 응시 입력 기능 보장 및 시선 응시 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="e150e-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="e150e-103">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **시선 응시 입력 기능 사용** 이 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity MRTK Project Configurator 창](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e150e-105">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성한 경우 [MRTK Project Configurator 설정 적용](../mr-learning-base-02.md#configuring-the-unity-project) 동안에는 응시 입력 기능이 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="e150e-106">그러나 사용하도록 설정되지 않은 경우 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="e150e-107">Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 다음, Inspector(검사기) 창에서 입력 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="e150e-108">**Input Data Providers(입력 데이터 공급자)** 를 확장하고 **+ Add Data Provider(데이터 공급자 추가)** 단추를 클릭하여 새 데이터 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![시선 데이터 공급자 1 추가](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="e150e-110">새 데이터 공급자의 **형식** 필드에 **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** 를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![시선 데이터 공급자 2 추가](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="e150e-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="e150e-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="e150e-113">시선 응시 입력 기능 보장 및 시선 응시 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="e150e-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="e150e-114">Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 다음, Inspector(검사기) 창에서 입력 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="e150e-115">**Input Data Providers(입력 데이터 공급자)** 를 확장하고 **+ Add Data Provider(데이터 공급자 추가)** 단추를 클릭하여 새 데이터 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![시선 데이터 공급자 1 추가](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="e150e-117">새 데이터 공급자의 **형식** 필드에 **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** 를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![시선 데이터 공급자 2 추가](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="e150e-119">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="e150e-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="e150e-120">시선 응시 입력 기능이 활성화되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="e150e-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="e150e-121">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **시선 응시 입력 기능 사용** 이 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity MRTK Project Configurator 창](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e150e-123">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성한 경우 [MRTK Project Configurator 설정 적용](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 동안에는 응시 입력 기능이 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="e150e-124">그러나 사용하도록 설정되지 않은 경우 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e150e-124">However, if it is not enabled, make sure you enable it now.</span></span>
