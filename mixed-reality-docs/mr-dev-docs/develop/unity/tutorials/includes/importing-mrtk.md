---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176114"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="2305d-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="2305d-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="2305d-102">**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="2305d-103">첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).</span><span class="sxs-lookup"><span data-stu-id="2305d-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="2305d-104">프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="2305d-105">그런 다음 **기능 검색** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="2305d-106">Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="2305d-107">파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="2305d-108">Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="2305d-109">폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="2305d-110">기능은 카테고리별로 그룹화되어 있어 쉽게 찾을 수 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하여 Mixed Reality Toolkit과 관련된 패키지를 찾고 **플랫폼 지원** 드롭다운을 클릭하여 다양한 지원 플랫폼 관련 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="2305d-111">**Mixed Reality Toolkit Foundation** 을 선택하고 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.2** 를 선택하고 **Mixed Reality OpenXR Plugin 1.0.0** 도 선택하고 옆에 있는 드롭다운을 클릭하여 사용 가능한 최신 버전을 선택한 다음 **기능 가져오기** 단추를 클릭하여 선택한 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="2305d-112">다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="2305d-113">**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="2305d-114">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-114">Configuring the Unity project</span></span>

<span data-ttu-id="2305d-115">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 새 플러그 인 시스템의 백 엔드를 사용하도록 설정하기 위해 Unity 편집기를 다시 시작하라는 경고 메시지가 표시됩니다. **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="2305d-116">Unity가 다시 시작되면 MRTK Project Configurator 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="2305d-117">그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![MRTK Project Configurator 창을 엽니다.](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="2305d-119">**Unity OpenXR 플러그 인** 을 클릭하여 XR 플러그 인 관리를 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="2305d-120">Unity OpenXR 플러그 인 추가</span><span class="sxs-lookup"><span data-stu-id="2305d-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="2305d-121">그러면 XR 플러그 인 관리에 필요한 Unity 패키지를 가져옵니다. 완료되면 MRTK Project Configurator에서 **XR 플러그 인 관리 설정 표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="2305d-122">XR 플러그 인 관리 설정 표시</span><span class="sxs-lookup"><span data-stu-id="2305d-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="2305d-123">그러면 **프로젝트 설정 창** 이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="2305d-124">**XR 플러그 인 관리** 아래의 프로젝트 설정 창에서 유니버설 Windows 플랫폼 설정(Windows 로고 탭)에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="2305d-125">또한 **시작 시 XR 초기화** 가 선택되어 있는지 확인한 다음 **OpenXR** 확인란과 **Microsoft HoloLens 기능 세트** 확인란을 클릭하여 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Open XR 사용 설정](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="2305d-127">OpenXR 확인란을 선택하면 MRTK Project Configurator 창에 **설정 적용** 단추와 함께 업데이트된 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="2305d-128">**설정 적용** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-128">Click **Apply Settings** button.</span></span> 

![프로젝트 설정 창 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="2305d-130">설정 적용을 클릭하면 콘솔에 이 오류 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="2305d-131">이것이 유일한 오류이거나 오류가 없는 경우 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-131">You can proceed if this is the only error or there is no error.</span></span>

![OpenXR 원격 오류 메시지](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="2305d-133">OpenXR 구성을 확인하려면 **XR 플러그 인 관리** 에서 **OpenXR** 을 클릭하고 다음 항목을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="2305d-134">깊이 제출 모드: **깊이 16비트**</span><span class="sxs-lookup"><span data-stu-id="2305d-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="2305d-135">상호 작용 프로필: **Microsoft 손 상호 작용 프로필**</span><span class="sxs-lookup"><span data-stu-id="2305d-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![프로젝트 설정 창 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="2305d-137">Depth Format(심도 형식)을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="2305d-138">이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="2305d-139">**MRTK Project Configurator** 창에서 **다음** 을 클릭한 후 **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="2305d-140">(닫은 경우 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 구성 프로젝트** 로 이동하여 수동으로 열 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="2305d-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![프로젝트 설정 창 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![프로젝트 설정 창 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="2305d-143">적용을 클릭하면 Unity가 입력 시스템을 적용하기 위해 다시 시작을 시도하고 **적용** 을 클릭하여 Unity 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="2305d-144">추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-144">Configure additional project settings</span></span>

<span data-ttu-id="2305d-145">Unity 메뉴에서 **Edit(편집)** > **Project Settings(프로젝트 설정)** 를 선택하여 Project Settngs(프로젝트 설정) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="2305d-146">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 게시 설정.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="2305d-149">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2305d-150">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="2305d-151">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2305d-152">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="2305d-153">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="2305d-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="2305d-154">**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="2305d-155">첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).</span><span class="sxs-lookup"><span data-stu-id="2305d-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="2305d-156">프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="2305d-157">그런 다음 **기능 검색** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="2305d-158">Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="2305d-159">파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="2305d-160">Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="2305d-161">폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="2305d-162">기능은 쉽게 찾을 수 있도록 카테고리별로 그룹화되어 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하면 Mixed Reality Toolkit과 관련된 패키지를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="2305d-163">**Mixed Reality Toolkit Foundation** 에 대한 확인란을 선택하고 그 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.0** 을 선택한 후 **기능 다운로드** 단추를 클릭하여 선택한 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="2305d-164">다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="2305d-165">**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="2305d-166">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-166">Configuring the Unity project</span></span>

<span data-ttu-id="2305d-167">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="2305d-168">그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![MRTK 구성 도구 열기](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="2305d-170">**Unity 플러그 인(비OpenXR) 기본 제공** 을 클릭하여 XR 플러그 인 관리를 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="2305d-171">MRTK 구성 도구</span><span class="sxs-lookup"><span data-stu-id="2305d-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="2305d-172">위 스크린샷은 Unity 2020에서 가져온 것입니다. Unity 2019를 사용하는 경우 **XR SDK/XR 관리** 를 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="2305d-173">이렇게 하면 XR 플러그 인 관리에 필요한 Unity 패키지를 가져옵니다. 완료되면 MRTK Project Configurator에서 **설정 표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![플레이어 설정 창](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="2305d-175">그러면 **프로젝트 설정 창** 이 열립니다. 프로젝트 설정 창의 **XR 플러그 인 관리** 아래에서 유니버설 Windows 플랫폼 설정에 있는지 확인하고 **시작 시 XR 초기화** 를 선택하고 **Windows Mixed Reality** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![플레이어 설정 창 Mixed Reality 사용-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="2305d-177">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="2305d-178">그렇지 않으면 Unity 메뉴를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="2305d-179">MRTK Project Configurator 창에서 **다음** 을 클릭한 후 Audio spatializer 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK Project Configurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="2305d-181">MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="2305d-182">단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="2305d-183">이 항목에 대한 자세한 내용은 MRTK의 [성능](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 설명서의 [단일 패스 인스턴스 렌더링](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="2305d-184">기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="2305d-185">Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="2305d-186">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="2305d-187">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="2305d-188">이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="2305d-189">**다음** 을 클릭한 다음 MRTK Project Configurator 창에서 **완료** 를 클릭하여 XRSDK에 대한 Unity 프로젝트 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="2305d-190">추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-190">Configure additional project settings</span></span>

<span data-ttu-id="2305d-191">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="2305d-192">프로젝트 설정 창에서 **XR 플러그 인 관리** > **Windows Mixed Reality** > **런타임 설정** 을 선택한 후 **깊이 버퍼 형식** 드롭다운을 사용하여 **16비트 깊이** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="2305d-194">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="2305d-195">이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="2305d-196">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 게시 설정.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="2305d-199">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2305d-200">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="2305d-201">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2305d-202">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="2305d-203">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="2305d-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="2305d-204">**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="2305d-205">첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).</span><span class="sxs-lookup"><span data-stu-id="2305d-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="2305d-206">프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="2305d-207">그런 다음 **기능 검색** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="2305d-208">Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="2305d-209">파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="2305d-210">Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="2305d-211">폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="2305d-212">기능은 쉽게 찾을 수 있도록 카테고리별로 그룹화되어 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하면 Mixed Reality Toolkit과 관련된 패키지를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="2305d-213">**Mixed Reality Toolkit Foundation** 에 대한 확인란을 선택하고 그 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.0** 을 선택한 후 **기능 다운로드** 단추를 클릭하여 선택한 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="2305d-214">다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="2305d-215">**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="2305d-216">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-216">Configuring the Unity project</span></span>

<span data-ttu-id="2305d-217">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="2305d-218">그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Unity 프로젝트 구성 메뉴 경로](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="2305d-220">**레거시 XR** 을 클릭하여 레거시 XR을 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![초](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="2305d-222">다음 단추를 클릭하여 레거시 XR에 대한 XR 파이프라인 설정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Unity MRTK 구성 창](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="2305d-224">MRTK Project Configurator 창에서 모든 옵션이 선택되었는지 확인하고 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 구성 창](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="2305d-226">MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="2305d-227">단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="2305d-228">이 항목에 대한 자세한 내용은 MRTK의 [성능](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 설명서의 [단일 패스 인스턴스 렌더링](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="2305d-229">기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="2305d-230">Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="2305d-231">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="2305d-232">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="2305d-233">이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="2305d-234">**다음** 을 클릭한 다음 MRTK Project Configurator 창에서 **완료** 단추를 클릭하여 레거시 XR에 대한 Unity 프로젝트 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="2305d-235">추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="2305d-235">Configure additional project settings</span></span>

<span data-ttu-id="2305d-236">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="2305d-237">프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="2305d-239">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="2305d-240">이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2305d-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="2305d-241">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 게시 설정.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="2305d-244">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2305d-245">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="2305d-246">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2305d-247">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="2305d-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
