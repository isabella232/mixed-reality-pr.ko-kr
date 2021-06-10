---
title: MRTK 구성 대화 상자
description: Unity 프로젝트에서 MRTK 구성
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345096"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="011ae-104">MRTK 프로젝트 구성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="011ae-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="011ae-105">Unity에서 프로젝트를 로드할 때 MRTK 구성 대화 상자가 표시 되 고 하나 이상의 구성 옵션에서 개발자에 게 주의가 필요한 경우를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![나중에 무시 적용](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="011ae-107">변경 내용을 적용 하려면 **적용** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="011ae-108">이후 **단추를 클릭 하면** 이후 시간에 프로젝트가 다시 로드 될 때까지 변경 내용이 지연 됩니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="011ae-109">권장 설정 중 하나 이상을 선택 하지 않은 상태로 두면 구성 대화 상자가 다시 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="011ae-110">이 문제가 발생 하지 않도록 하려면 원하는 옵션을 적용 한 다음 **혼합 현실 도구 키트**  >  **유틸리티**  >  **Unity 프로젝트 구성** 을 통해 대화 상자를 다시 시작 하 고 **무시** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="011ae-111">이렇게 하면 구성 대화 reappearing 자동으로 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="011ae-112">일반 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-112">Common settings</span></span>

<span data-ttu-id="011ae-113">모든 빌드 대상은 공용 옵션의 컬렉션을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-113">All build targets share a collection of common options.</span></span>

![일반 설정](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="011ae-115">텍스트 자산 직렬화 강제 적용 및 표시 되는 메타 파일 사용</span><span class="sxs-lookup"><span data-stu-id="011ae-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="011ae-116">이러한 설정은 Unity 프로젝트 및 소스 제어 시스템 (예: Git) 작업을 간소화 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="011ae-117">VR 지원 사용</span><span class="sxs-lookup"><span data-stu-id="011ae-117">Enable VR supported</span></span>

<span data-ttu-id="011ae-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="011ae-118">**Unity 2018**</span></span>

<span data-ttu-id="011ae-119">**플레이어 설정**  >  **XR 설정** 에서 가상 현실 지원 및 가상 현실 SDK 옵션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="011ae-120">단일 패스 인스턴스 렌더링 경로 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="011ae-121">**플레이어 설정**  >  **XR 설정**  >  **스테레오 렌더링 모드** 를 **단일 통과** 로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="011ae-122">기본 공간 인식 계층 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="011ae-123">공간 인식을 계층 31로 등록 하 여 raycast 및 물리학 옵션을 쉽고 일관 되 게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="011ae-124">오디오 spatializer</span><span class="sxs-lookup"><span data-stu-id="011ae-124">Audio spatializer</span></span>

<span data-ttu-id="011ae-125">Audio spatializers는 혼합 현실 경험을 위해 공간 사운드 및 위치 오디오의 강력한 기능을 해제 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="011ae-126">오디오 spatializer를 없음으로 설정 하면 위치 오디오 기능이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="011ae-127">일반 spatializers</span><span class="sxs-lookup"><span data-stu-id="011ae-127">Common spatializers</span></span>

- <span data-ttu-id="011ae-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="011ae-128">Microsoft Spatializer</span></span>

<span data-ttu-id="011ae-129">Microsoft에서 HoloLens 2에서 하드웨어 가속의 사용률을 지 원하는 spatializer을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="011ae-130">이 spatializer는 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 및 [GitHub](https://github.com/microsoft/spatialaudio-unity)를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="011ae-131">Microsoft Spatializer에 대 한 자세한 내용은 [공간 사운드 설명서](/windows/mixed-reality/spatial-sound-in-unity)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="011ae-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="011ae-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="011ae-133">Windows Mixed Reality 및 Windows XR 플랫폼 패키지의 일부로 Unity에서 제공 하는 Microsoft Windows spatializer입니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="011ae-134">Resonance 오디오</span><span class="sxs-lookup"><span data-stu-id="011ae-134">Resonance Audio</span></span>

<span data-ttu-id="011ae-135">Unity를 통해 제공 되는 Google의 플랫폼 간 spatializer.</span><span class="sxs-lookup"><span data-stu-id="011ae-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="011ae-136">자세한 내용은 [Resonance Audio 설명서](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 사이트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="011ae-137">유니버설 Windows 플랫폼 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-137">Universal Windows Platform settings</span></span>

![UWP 설정](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="011ae-139">UWP 기능</span><span class="sxs-lookup"><span data-stu-id="011ae-139">UWP Capabilities</span></span>

<span data-ttu-id="011ae-140">유니버설 Windows 플랫폼 응용 프로그램에 대 한 특정 응용 프로그램 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="011ae-141">이러한 기능을 통해 플랫폼은 특정 기능을 사용할 수 있는 권한을 알리고 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="011ae-142">마이크</span><span class="sxs-lookup"><span data-stu-id="011ae-142">Microphone</span></span>

  <span data-ttu-id="011ae-143">마이크를 통해 소리를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="011ae-144">인터넷 클라이언트</span><span class="sxs-lookup"><span data-stu-id="011ae-144">Internet Client</span></span>

  <span data-ttu-id="011ae-145">인터넷의 리소스에 액세스할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="011ae-146">공간 인식</span><span class="sxs-lookup"><span data-stu-id="011ae-146">Spatial Perception</span></span>

  <span data-ttu-id="011ae-147">실제 환경 사용에 대 한 지원을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="011ae-148">아이 응시</span><span class="sxs-lookup"><span data-stu-id="011ae-148">Eye Gaze</span></span>

  <span data-ttu-id="011ae-149">**Unity 2019.3 이상**</span><span class="sxs-lookup"><span data-stu-id="011ae-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="011ae-150">사용자의 눈 응시를 추적할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="011ae-151">Unity ' PlayerSettings. graphicsJob ' 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="011ae-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="011ae-152">**Unity 2019.3 이상**</span><span class="sxs-lookup"><span data-stu-id="011ae-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="011ae-153">최신 버전의 Unity 2019에서 "그래픽 작업"을 사용 하도록 설정 하면 HoloLens 2에 배포 될 때 앱이 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="011ae-154">이 설정은 Unity에서 기본적으로 사용 하도록 설정 되어 있습니다. ( [unity 버그](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)참조) 구성 기는 기본적으로 그래픽 작업을 ' f a l s e '로 설정 합니다. 따라서 HoloLens 2에 배포 된 앱이 충돌 하지 않도록 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="011ae-155">Android 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-155">Android settings</span></span>

<span data-ttu-id="011ae-156">Android 기반 장치에서 AR 응용 프로그램을 지 원하는 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Android 설정](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="011ae-158">다중 스레드 렌더링 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="011ae-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="011ae-159">**플레이어 설정**  >  **다른 설정**  >  **다중 스레드 렌더링** (Android의 AR 지원에 필요 함)을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="011ae-160">최소 API 수준 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-160">Set Minimum API Level</span></span>

<span data-ttu-id="011ae-161">  >    >  AR 응용 프로그램에 대 한 운영 체제 요구 사항을 적용 하도록 플레이어 설정 다른 설정 **최소 API 수준** 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="011ae-162">iOS 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-162">iOS settings</span></span>

<span data-ttu-id="011ae-163">IOS 기반 장치에서 AR 응용 프로그램을 지 원하는 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![iOS 설정](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="011ae-165">필요한 OS 버전 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-165">Set Required OS Version</span></span>

<span data-ttu-id="011ae-166">  >    >  AR 응용 프로그램에 대 한 운영 체제 요구 사항을 적용 하는 다른 설정 **대상 최소 iOS 버전** 의 플레이어 설정 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="011ae-167">필수 아키텍처 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-167">Set Required Architecture</span></span>

<span data-ttu-id="011ae-168">**플레이어 설정**  >  **기타 설정** 아키텍처의 값을 설정  >   하 여 AR 응용 프로그램에 대 한 플랫폼 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="011ae-169">카메라 사용 설명 설정</span><span class="sxs-lookup"><span data-stu-id="011ae-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="011ae-170">**플레이어 설정** 의 값을 설정 합니다  >  .**다른 설정**  >  **카메라 사용 설명은** 장치의 카메라 사용 권한을 요청 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="011ae-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>