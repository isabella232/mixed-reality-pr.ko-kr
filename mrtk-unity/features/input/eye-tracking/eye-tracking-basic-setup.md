---
title: 시선 추적 기본 설정
description: MRTK에서 눈 추적을 설정 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 눈 추적,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144097"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="d606d-104">MRTK에서 눈 추적 시작</span><span class="sxs-lookup"><span data-stu-id="d606d-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="d606d-105">이 페이지에서는 앱에서 눈 추적을 사용 하도록 Unity MRTK 장면을 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="d606d-106">다음은 새로 새 장면으로 시작 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="d606d-107">또는 직접 빌드할 수 있는 다양 한 예제를 사용 하 여 이미 구성 된 [Mrtk 눈 추적 예제](../../example-scenes/eye-tracking-examples-overview.md) 를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="d606d-108">눈 추적 요구 사항 검사 목록</span><span class="sxs-lookup"><span data-stu-id="d606d-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="d606d-109">눈 추적이 제대로 작동 하려면 다음 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="d606d-110">HoloLens 2에 대 한 눈 추적을 처음 접하는 경우 MRTK에서 눈 추적을 설정 하는 방법은 걱정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d606d-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="d606d-111">아래에서 각 항목을 처리 하는 방법에 대해 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="d606d-112">_' 눈 응시 Data Provider '_ 을 입력 시스템에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="d606d-113">이는 플랫폼의 눈 추적 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="d606d-114">응용 프로그램 매니페스트에서 _' GazeInput '_ 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="d606d-115">**이 기능은 Unity 2019에서 설정할 수 있지만 Unity 2018 및 이전 버전에서이 기능은 Visual Studio 및 MRTK 빌드 도구를 통해서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="d606d-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="d606d-116">HoloLens는 현재 사용자에 게 눈에 맞게 **보정 되어야 합니다** .</span><span class="sxs-lookup"><span data-stu-id="d606d-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="d606d-117">[사용자가 아이 보정 인지 여부를 검색 하는 샘플](eye-tracking-is-user-calibrated.md)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="d606d-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="d606d-118">GazeInput 기능에 대 한 참고 사항</span><span class="sxs-lookup"><span data-stu-id="d606d-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="d606d-119">MRTK 제공 빌드 도구 (예: 혼합 현실 도구 키트-> 유틸리티-> 빌드 창)는 자동으로 GazeInput 기능을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="d606d-120">이렇게 하려면 ' Appx 빌드 옵션 ' 탭에서 ' 입력 기능 응시 '가 선택 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![MRTK 빌드 도구](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="d606d-122">이 도구는 Unity 빌드가 완료된 후 AppX 매니페스트를 찾고 GazeInput 기능을 수동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="d606d-123">**Unity 2019 이전에는 Unity의 기본 제공 빌드 창(즉,** 파일 -> 빌드 설정)을 사용하는 경우 이 도구가 활성화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="d606d-124">Unity 2019 이전에는 Unity의 빌드 창을 사용할 때 다음과 같이 Unity 빌드 후에 기능을 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="d606d-125">컴파일된 Visual Studio 프로젝트를 열고 솔루션에서 _'Package.appxmanifest'를_ 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="d606d-126">기능 _아래의 'GazeInput'_ 확인란을 선택해야 _합니다._</span><span class="sxs-lookup"><span data-stu-id="d606d-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="d606d-127">_'GazeInput'_ 기능이 표시되지 않으면 시스템이 MRTK(특히 Windows SDK [버전)를 사용하기 위한 필수 구성을](/windows/mixed-reality/develop/install-the-tools) 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="d606d-128">_참고:_ 새 빌드 폴더에 빌드하는 경우에만 이 작업을 수행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="d606d-129">즉, Unity 프로젝트를 이미 빌드하고 이전에 appxmanifest를 설정했고 이제 동일한 폴더를 다시 대상으로 지정한 경우 변경 내용을 다시 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="d606d-130">시선 추적 단계별 설정</span><span class="sxs-lookup"><span data-stu-id="d606d-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="d606d-131">장면 설정</span><span class="sxs-lookup"><span data-stu-id="d606d-131">Setting up the scene</span></span>

<span data-ttu-id="d606d-132">_'Mixed Reality Toolkit -> 구성...'을_ 클릭하여 _MixedRealityToolkit를_ 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="d606d-133">메뉴 모음에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-133">in the menu bar.</span></span>

![MRTK 구성](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="d606d-135">시선 추적에 필요한 MRTK 프로필 설정</span><span class="sxs-lookup"><span data-stu-id="d606d-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="d606d-136">MRTK 장면을 설정하면 MRTK에 대한 프로필을 선택하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="d606d-137">_DefaultMixedRealityToolkitConfigurationProfile을_ 선택한 _다음, '& 사용자 지정 복사'_ 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![MRTK 프로필](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="d606d-139">"시선 응시 데이터 공급자" 만들기</span><span class="sxs-lookup"><span data-stu-id="d606d-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="d606d-140">MRTK 프로필에서 _'입력'_ 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="d606d-141">_기본값('DefaultMixedRealityInputSystemProfile')을_ 편집하려면 옆에 있는 _'복제'_ 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="d606d-142">_' 프로필 복제 '_ 메뉴가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="d606d-143">해당 메뉴의 아래쪽에서 _' 복제 '_ 를 클릭 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="d606d-144">새 입력 프로필을 두 번 클릭 하 고 _' 입력 데이터 공급자 '_ 를 확장 한 다음 _' + Data Provider 추가 '_ 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="d606d-145">새 데이터 공급자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-145">Create a new data provider:</span></span>
  - <span data-ttu-id="d606d-146">**유형** 아래에서 _' MixedReality_'  ->  _' WindowsMixedRealityEyeGazeDataProvider '_ 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="d606d-147">**플랫폼** 의 경우 _' Windows 유니버설 '_ 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![MRTK 데이터 공급자](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="d606d-149">Unity 편집기에서 눈 추적 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="d606d-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="d606d-150">Unity 편집기에서 눈 추적 입력을 시뮬레이션 하 여 HoloLens 2에 앱을 배포 하기 전에 이벤트가 올바르게 트리거되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="d606d-151">눈에 지 응시 신호는 카메라의 위치를 아이 응시 원본으로 사용 하 고 카메라의 앞에 있는 벡터를 눈 응시 방향으로 사용 하 여 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="d606d-152">이 방법은 초기 테스트에 유용 하지만 신속한 시각 이동에는 좋은 모조 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="d606d-153">이 경우 HoloLens 2에서 눈에 잘 맞는 상호 작용을 자주 테스트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="d606d-154">**시뮬레이션 된 눈동자 추적 사용**:</span><span class="sxs-lookup"><span data-stu-id="d606d-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="d606d-155">MRTK 구성 프로필에서 _' 입력 '_ 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="d606d-156">여기에서 _' 입력 데이터 공급자 '_  ->  _' 입력 시뮬레이션 서비스 '_ 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="d606d-157">_' DefaultMixedRealityInputSimpulationProfile '_ 을 복제 하 여 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="d606d-158">_' 눈 위치 시뮬레이트 '_ 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK 눈동자 시뮬레이트](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="d606d-160">**기본 헤드 응시 커서 사용 안 함**: 일반적으로 눈에 _잘 드는_ 커서를 표시 하지 않거나 매우 미묘한 커서를 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="d606d-161">기본적으로 MRTK 응시 포인터 프로필에 연결 된 기본 헤드 응시 커서를 숨기는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="d606d-162">Mrtk 구성 프로필-> _' 입력 '_  ->  _' 포인터 '_ 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="d606d-163">_' DefaultMixedRealityInputPointerProfile '_ 을 복제 하 여 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="d606d-164">_' 포인터 설정 '_ 맨 위에서 _' GazeCursor '_ 에 보이지 않는 커서 prefab을 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="d606d-165">MRTK Foundation에서 _' EyeGazeCursor '_ prefab를 선택 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="d606d-166">응시 공급자에서 눈에 잘 맞는 응시 사용</span><span class="sxs-lookup"><span data-stu-id="d606d-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="d606d-167">HoloLens v1에서 헤드 응시는 기본 포인팅 기술로 사용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="d606d-168">헤드 응시는 [카메라](https://docs.unity3d.com/ScriptReference/Camera.html)에 연결 된 MRTK의 _GazeProvider_ 를 통해 계속 사용할 수 있지만, 입력 포인터 프로필의 응시 설정에서 _' IsEyeTrackingEnabled '_ 확인란을 선택 하 여 대신 눈동자 응시를 사용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="d606d-169">개발자는 _' GazeProvider '_ 의 _' IsEyeTrackingEnabled '_ 속성을 변경 하 여 코드에서 눈에 맞는 응시와 헤드 기반 응시를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="d606d-170">눈 추적 요구 사항 중 하나라도 충족 되지 않으면 응용 프로그램은 자동으로 head 기반 응시로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="d606d-171">아이 응시 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="d606d-171">Accessing eye gaze data</span></span>

<span data-ttu-id="d606d-172">이제 장면 추적을 사용 하도록 장면을 설정 했으므로 스크립트에서 액세스 하는 방법을 살펴보겠습니다. EyeGazeProvider 및 [눈에 잘 지 원하는 대상 선택을](eye-tracking-target-selection.md) [통해 아이 추적 데이터에](eye-tracking-eye-gaze-provider.md) 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="d606d-173">HoloLens 2에서 Unity 앱 테스트</span><span class="sxs-lookup"><span data-stu-id="d606d-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="d606d-174">아이 추적을 사용 하 여 앱을 빌드하는 것은 다른 HoloLens 2 MRTK 앱을 컴파일하는 방법과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="d606d-175">[*GazeInput 기능에 대 한 참고*](#a-note-on-the-gazeinput-capability)섹션에서 위에 설명 된 대로 *' 응시 입력 '* 기능을 사용 하도록 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="d606d-176">눈 보정</span><span class="sxs-lookup"><span data-stu-id="d606d-176">Eye calibration</span></span>

<span data-ttu-id="d606d-177">마지막으로, HoloLens 2에서 눈 보정을 실행 하는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d606d-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="d606d-178">사용자가 보정 되지 않은 경우에는 눈 추적 시스템에서 입력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="d606d-179">보정을 가져오는 가장 쉬운 방법은 센터를 위아래로 이동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="d606d-180">시스템 알림은 새로운 사용자에 게 환영 하 고 눈에 볼 수 있는 것으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="d606d-181">또는 시스템 설정: 설정 > 시스템 > 보정 > 눈 보정 실행에서 눈 보정을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="d606d-182">시선 추적 권한</span><span class="sxs-lookup"><span data-stu-id="d606d-182">Eye tracking permission</span></span>

<span data-ttu-id="d606d-183">HoloLens 2 앱을 처음 시작할 때 사용자에게 시선 추적을 사용할 수 있는 권한을 묻는 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="d606d-184">표시되지 않으면 일반적으로 _'GazeInput'_ 기능이 설정되지 않았다는 표시입니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="d606d-185">권한 프롬프트가 한 번 표시되면 자동으로 다시 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="d606d-186">_"시선 추적 권한을 거부"한_ 경우 설정 -> 개인 정보 -> 앱에서 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="d606d-187">이렇게 하면 MRTK Unity 앱에서 시선 추적 사용을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d606d-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="d606d-188">시선 추적 입력을 사용하는 방법을 보여 주는 [MRTK 시선 추적 자습서 및 샘플을](../../example-scenes/eye-tracking-examples-overview.md) 확인하고 프로젝트에서 재사용할 수 있는 스크립트를 편리하게 제공하는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d606d-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="d606d-189">"MixedRealityToolkit의 시선 추적"으로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="d606d-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)