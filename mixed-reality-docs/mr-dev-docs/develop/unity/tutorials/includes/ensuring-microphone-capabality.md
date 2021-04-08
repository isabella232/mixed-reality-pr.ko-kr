---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097745"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="33064-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="33064-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="33064-102">마이크 기능 보장 및 음성 입력 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="33064-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="33064-103">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **Enable Microphone Capability**(마이크 기능 사용)가 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![마이크 기능 사용](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="33064-105">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성할 때 [MRTK Project Configurator 설정 적용](../mr-learning-base-02.md#configuring-the-unity-project) 지침을 진행하는 동안 마이크 기능을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="33064-106">하지만 사용하도록 설정되지 않으면 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="33064-107">Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 다음, Inspector(검사기) 창에서 입력 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="33064-108">**Input Data Providers(입력 데이터 공급자)** 를 확장하고 **+ Add Data Provider(데이터 공급자 추가)** 단추를 클릭하여 새 데이터 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![새 음성 명령을 추가하기 위한 데이터 공급자](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="33064-110">새 데이터 공급자의 **Type(형식)** 필드에 **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** 를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![새 음성 명령 추가 설정](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="33064-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="33064-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="33064-113">마이크 기능 보장 및 음성 입력 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="33064-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="33064-114">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **Enable Microphone Capability**(마이크 기능 사용)가 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![OpenXR의 마이크 기능 사용](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="33064-116">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성할 때 [MRTK Project Configurator 설정 적용](../mr-learning-base-02.md#configuring-the-unity-project) 지침을 진행하는 동안 마이크 기능을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="33064-117">하지만 사용하도록 설정되지 않으면 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="33064-118">Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 다음, Inspector(검사기) 창에서 입력 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="33064-119">**Input Data Providers(입력 데이터 공급자)** 를 확장하고 **+ Add Data Provider(데이터 공급자 추가)** 단추를 클릭하여 새 데이터 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![OpenXR의 새 음성 명령 추가](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="33064-121">새 데이터 공급자의 **Type(형식)** 필드에 **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** 를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![OpenXR의 새 음성 명령 추가 설정](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="33064-123">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="33064-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="33064-124">마이크 기능을 사용하도록 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="33064-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="33064-125">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **Enable Microphone Capability**(마이크 기능 사용)가 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![마이크 기능 사용](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="33064-127">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성할 때 [MRTK Project Configurator 설정 적용](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 지침을 진행하는 동안 마이크 기능을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="33064-128">하지만 사용하도록 설정되지 않으면 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33064-128">However, if it is not enabled, make sure you enable it now.</span></span>
