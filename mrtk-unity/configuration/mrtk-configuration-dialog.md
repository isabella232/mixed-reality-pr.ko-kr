---
title: MRTK 구성 대화 상자
description: Unity 프로젝트에서 MRTK 구성
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144833"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="36ba1-104">MRTK 프로젝트 구성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="36ba1-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="36ba1-105">UNITY에서 프로젝트를 로드할 때 MRTK 구성 대화 상자가 표시되고 하나 이상의 구성 옵션에 개발자의 주의가 필요한 것으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![나중에 적용 무시](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="36ba1-107">변경 내용을 적용하려면 **적용** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="36ba1-108">**이후** 단추는 나중에 프로젝트가 다시 로드될 때까지 변경 내용을 연기합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="36ba1-109">권장 설정 중 하나 이상을 선택하지 않은 상태로 두면 구성 대화 상자가 다시 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="36ba1-110">이 문제가 발생하지 않도록 하려면 원하는 옵션을 적용한 다음 Mixed Reality **Toolkit** 유틸리티 Unity 프로젝트 구성을 통해 대화 상자를 다시 시작하고  >    >   **무시를** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="36ba1-111">이렇게 하면 구성 대화 상자가 자동으로 다시 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="36ba1-112">일반 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-112">Common settings</span></span>

<span data-ttu-id="36ba1-113">모든 빌드 대상은 공통 옵션 컬렉션을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-113">All build targets share a collection of common options.</span></span>

![일반 설정](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="36ba1-115">텍스트 자산 직렬화 강제 적용 및 표시되는 메타 파일 사용</span><span class="sxs-lookup"><span data-stu-id="36ba1-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="36ba1-116">이러한 설정은 Unity 프로젝트 및 소스 제어 시스템(예: Git) 작업을 간소화하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="36ba1-117">VR 지원 사용</span><span class="sxs-lookup"><span data-stu-id="36ba1-117">Enable VR supported</span></span>

<span data-ttu-id="36ba1-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="36ba1-118">**Unity 2018**</span></span>

<span data-ttu-id="36ba1-119">**플레이어 설정**  >  **XR 설정** 에서 Virtual Reality Supported 및 Virtual Reality SDK 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="36ba1-120">단일 패스 인스턴스 렌더링 경로 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="36ba1-121">**플레이어 설정**  >  **XR 설정**  >  **스테레오 렌더링 모드를** 단일 패스 **인스턴스화로 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="36ba1-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="36ba1-122">기본 공간 인식 계층 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="36ba1-123">공간 인식을 레이어 31로 등록하여 광선 캐스트 및 물리학 옵션을 쉽고 일관되게 구성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="36ba1-124">오디오 spatializer</span><span class="sxs-lookup"><span data-stu-id="36ba1-124">Audio spatializer</span></span>

<span data-ttu-id="36ba1-125">Audio spatializers는 혼합 현실 경험을 위해 공간 사운드 및 위치 오디오의 강력한 기능을 해제 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="36ba1-126">오디오 spatializer를 없음으로 설정 하면 위치 오디오 기능이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="36ba1-127">일반 spatializers</span><span class="sxs-lookup"><span data-stu-id="36ba1-127">Common spatializers</span></span>

- <span data-ttu-id="36ba1-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="36ba1-128">Microsoft Spatializer</span></span>

<span data-ttu-id="36ba1-129">Microsoft에서 HoloLens 2에서 하드웨어 가속의 사용률을 지 원하는 spatializer을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="36ba1-130">이 spatializer는 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 및 [GitHub](https://github.com/microsoft/spatialaudio-unity)를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="36ba1-131">Microsoft Spatializer에 대 한 자세한 내용은 [공간 사운드 설명서](/windows/mixed-reality/spatial-sound-in-unity)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="36ba1-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="36ba1-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="36ba1-133">Windows Mixed Reality 및 Windows XR 플랫폼 패키지의 일부로 Unity에서 제공 하는 Microsoft Windows spatializer입니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="36ba1-134">Resonance 오디오</span><span class="sxs-lookup"><span data-stu-id="36ba1-134">Resonance Audio</span></span>

<span data-ttu-id="36ba1-135">Unity를 통해 제공 되는 Google의 플랫폼 간 spatializer.</span><span class="sxs-lookup"><span data-stu-id="36ba1-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="36ba1-136">자세한 내용은 [Resonance Audio 설명서](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 사이트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="36ba1-137">유니버설 Windows 플랫폼 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-137">Universal Windows Platform settings</span></span>

![UWP 설정](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="36ba1-139">UWP 기능</span><span class="sxs-lookup"><span data-stu-id="36ba1-139">UWP Capabilities</span></span>

<span data-ttu-id="36ba1-140">유니버설 Windows 플랫폼 응용 프로그램에 대 한 특정 응용 프로그램 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="36ba1-141">이러한 기능을 통해 플랫폼은 특정 기능을 사용할 수 있는 권한을 알리고 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="36ba1-142">마이크</span><span class="sxs-lookup"><span data-stu-id="36ba1-142">Microphone</span></span>

  <span data-ttu-id="36ba1-143">마이크를 통해 소리를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="36ba1-144">인터넷 클라이언트</span><span class="sxs-lookup"><span data-stu-id="36ba1-144">Internet Client</span></span>

  <span data-ttu-id="36ba1-145">인터넷에서 리소스에 액세스할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="36ba1-146">공간 인식</span><span class="sxs-lookup"><span data-stu-id="36ba1-146">Spatial Perception</span></span>

  <span data-ttu-id="36ba1-147">실제 환경 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="36ba1-148">시선 응시</span><span class="sxs-lookup"><span data-stu-id="36ba1-148">Eye Gaze</span></span>

  <span data-ttu-id="36ba1-149">**Unity 2019.3 이상**</span><span class="sxs-lookup"><span data-stu-id="36ba1-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="36ba1-150">사용자의 시선 응시 추적을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="36ba1-151">Unity 'PlayerSettings.graphicsJob' 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="36ba1-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="36ba1-152">**Unity 2019.3 이상**</span><span class="sxs-lookup"><span data-stu-id="36ba1-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="36ba1-153">최신 버전의 Unity 2019에서 "그래픽 작업"을 사용하도록 설정하면 HoloLens 2 배포할 때 앱이 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="36ba1-154">이 설정은 Unity에서 기본적으로 사용하도록 설정됩니다. 이 버그가 있는 [동안(Unity 버그](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)참조) 구성기는 기본적으로 그래픽 작업을 'false'로 설정하므로 에 배포된 앱이 충돌하지 HoloLens 2 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="36ba1-155">Android 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-155">Android settings</span></span>

<span data-ttu-id="36ba1-156">Android 지원 디바이스에서 AR 애플리케이션을 지원하기 위한 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Android 설정](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="36ba1-158">다중 스레드 렌더링 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="36ba1-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="36ba1-159">Android의 AR 지원에서 요구하는 대로 **플레이어 설정**  >  **기타 설정** 다중 스레드  >  **렌더링을** 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="36ba1-160">최소 API 수준 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-160">Set Minimum API Level</span></span>

<span data-ttu-id="36ba1-161">**AR**  >  애플리케이션에 대한 운영 체제 요구 사항을 적용하도록 플레이어 설정 기타 **설정**  >  **최소 API 수준** 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="36ba1-162">iOS 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-162">iOS settings</span></span>

<span data-ttu-id="36ba1-163">iOS 지원 디바이스에서 AR 애플리케이션을 지원하기 위한 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![iOS 설정](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="36ba1-165">필수 OS 버전 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-165">Set Required OS Version</span></span>

<span data-ttu-id="36ba1-166">**AR**  >  애플리케이션에 대한 운영 체제 요구 사항을 적용하도록 플레이어 설정 기타 **설정** 대상  >  **최소 iOS 버전** 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="36ba1-167">필수 아키텍처 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-167">Set Required Architecture</span></span>

<span data-ttu-id="36ba1-168">**플레이어 설정**  >  **기타 설정** 아키텍처의 값을 설정  >   하 여 AR 응용 프로그램에 대 한 플랫폼 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="36ba1-169">카메라 사용 설명 설정</span><span class="sxs-lookup"><span data-stu-id="36ba1-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="36ba1-170">**플레이어 설정** 의 값을 설정 합니다  >  .**다른 설정**  >  **카메라 사용 설명은** 장치의 카메라 사용 권한을 요청 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36ba1-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>