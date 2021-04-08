---
ms.openlocfilehash: 20cfe36028c6fe95cbdc79a1ea8884ed9c3cd5bd
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088714"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="42bd1-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="42bd1-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="42bd1-102">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-102">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity Project Settings... 메뉴 경로](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="42bd1-104">프로젝트 설정 창에서 **XR Plug-in Management** > **Install XR Plug-in Management(XR Plug-in Management 설치)** 를 선택하여 XR Plug-in Management를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-104">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="42bd1-106">Unity에서 XR Plug-in Management 설치를 완료한 후</span><span class="sxs-lookup"><span data-stu-id="42bd1-106">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="42bd1-107">유니버설 Windows 플랫폼 설정에 있는지 확인하고 **Initialize XR on Startup(시작 시 XR 초기화)** 및 **Windows Mixed Reality** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-107">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup** and **Windows Mixed Reality** checkbox.</span></span>

![Windows Mixed Reality SDK 추가가 표시된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-1.png)

<span data-ttu-id="42bd1-109">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-109">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="42bd1-110">그렇지 않으면 Unity 메뉴를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-110">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="42bd1-111">MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-111">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Windows Mixed Reality SDK가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="42bd1-113">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-113">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="42bd1-114">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-114">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="42bd1-115">이 항목에 대한 자세한 정보는 <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42bd1-115">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="42bd1-116">Project Settings(프로젝트 설정) 창에서 **XR Plug-in Management(XR 플러그 인 관리)**  > **Windows Mixed Reality** > **Runtime Settings(런타임 설정)** 를 선택한 후 **Depth Buffer Format(깊이 버퍼 형식)** 드롭다운을 사용하여 **16-bit depth(16비트 깊이)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-116">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth:**</span></span>

![패키지 이름이 강조 표시된 Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> <span data-ttu-id="42bd1-118">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-118">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="42bd1-119">이 항목에 대한 자세한 정보는 MRTK의 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">성능</a> 설명서의 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42bd1-119">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="42bd1-120">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-120">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![패키지 이름이 표시된 Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="42bd1-122">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-122">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="42bd1-123">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-123">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="42bd1-124">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-124">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="42bd1-125">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-125">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="42bd1-126">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="42bd1-126">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="42bd1-127">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-127">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity Project Settings... 메뉴 경로](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="42bd1-129">프로젝트 설정 창에서 **XR Plug-in Management** > **Install XR Plug-in Management(XR Plug-in Management 설치)** 를 선택하여 XR Plug-in Management를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-129">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Install XR plug-in management(XR 플러그 인 설치 관리)가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="42bd1-131">Unity에서 XR Plug-in Management 설치를 완료한 후</span><span class="sxs-lookup"><span data-stu-id="42bd1-131">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="42bd1-132">유니버설 Windows 플랫폼 설정에 있는지 확인하고 **Initialize XR on Startup(시작 시 XR 초기화)** , **OpenXR** 및 **Microsoft HoloLens feature set(Microsoft HoloLens 기능 세트)** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-132">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup**, **OpenXR** and **Microsoft HoloLens feature set** checkboxes.</span></span>

![OpenXR 및 Microsoft HoloLens 기능 추가가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

<span data-ttu-id="42bd1-134">화면 상단의 메뉴 모음에서 **Mixed Reality > OpenXR > Apply recommended project settings for HoloLens 2(HoloLens 2에 권장되는 프로젝트 설정 적용)** 로 이동하여 앱 성능을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-134">In the menu bar at the top of the screen, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR 및 HoloLens 2에 권장되는 프로젝트 설정 적용이 선택된 Mixed Reality 메뉴](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
><span data-ttu-id="42bd1-136">OpenXR 플러그 인(미리 보기) 옆에 빨간색 경고 아이콘이 표시되는 경우 계속하기 전에 아이콘을 클릭하고 Fix all(모두 해결)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-136">If you see a red warning icon next to OpenXR Plugin (Preview), click the icon and select Fix all before continuing.</span></span> <span data-ttu-id="42bd1-137">Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>
><span data-ttu-id="42bd1-138">![모든 문제가 해결 대상으로 선택된 OpenXR 프로젝트 유효성 검사 메뉴](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span><span class="sxs-lookup"><span data-stu-id="42bd1-138">![OpenXR project validation menu with all issues selected to be fixed.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span></span>

<span data-ttu-id="42bd1-139">Unity가 필요한 파일 가져오기를 마치면 MRTK Project Configurator(MRTK 프로젝트 구성기) 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-139">After Unity has finished importing necessary files, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="42bd1-140">그렇지 않으면 Unity 메뉴를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-140">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="42bd1-141">MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-141">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![기본 옵션이 선택된 MRTK 구성 창](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="42bd1-143">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-143">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="42bd1-144">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-144">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="42bd1-145">이 항목에 대한 자세한 정보는 <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42bd1-145">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>


<span data-ttu-id="42bd1-146">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="42bd1-148">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-148">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="42bd1-149">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-149">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="42bd1-150">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-150">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="42bd1-151">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-151">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="42bd1-152">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="42bd1-152">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="42bd1-153">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-153">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="42bd1-154">프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택하고 **Virual Reality Supported** 확인란을 선택한 다음, **+** 아이콘을 클릭하고 Windows Mixed Reality를 선택하여 Windows Mixed Reality SDK를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-154">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Windows Mixed Reality SDK 추가가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="42bd1-156">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-156">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="42bd1-157">그렇지 않으면 Unity 메뉴에서 **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** 로 이동하여 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-157">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="42bd1-158">MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-158">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 구성 창](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="42bd1-160">Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-160">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="42bd1-161">MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-161">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="42bd1-162">이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42bd1-162">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="42bd1-163">프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-163">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="42bd1-165">Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-165">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="42bd1-166">이 항목에 대한 자세한 정보는 MRTK의 <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">성능</a> 설명서의 <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42bd1-166">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="42bd1-167">프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-167">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 게시 설정.](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="42bd1-170">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-170">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="42bd1-171">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-171">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="42bd1-172">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-172">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="42bd1-173">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bd1-173">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>