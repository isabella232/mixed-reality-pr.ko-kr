---
title: Mixed Reality 구성 가이드
description: UNITY로 MRTK를 구성하는 설명서입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK,
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588864"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="136c7-104">Mixed Reality 도구 키트 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="136c7-104">Mixed Reality Toolkit profile configuration guide</span></span>

<span data-ttu-id="136c7-105">Mixed Reality 도구 키트는 도구 키트를 관리하는 데 필요한 구성을 최대한 많이 중앙 집중화합니다(진정한 런타임 "사물"제외).</span><span class="sxs-lookup"><span data-stu-id="136c7-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="136c7-106">이 가이드는 현재 도구 키트에 사용할 수 있는 각 구성 프로필 화면에 대한 간단한 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="136c7-107">기본 Mixed Reality 도구 키트 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="136c7-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="136c7-108">장면의 *MixedRealityToolkit* GameObject에 연결된 기본 구성 프로필은 프로젝트의 도구 키트에 대한 기본 진입점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="136c7-109">Mixed Reality 도구 키트는 기본 구성 화면을 "잠가" 프로젝트에 대한 공통 시작점이 항상 있는지 확인하고 프로젝트가 발전함에 따라 사용자 고유의 설정을 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="136c7-110">재생 모드 중에는 MRTK 구성을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-110">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 구성 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="136c7-112">Mixed Reality Toolkit에 대한 모든 "기본" 프로필은 Assets/MRTK/SDK/Profiles 폴더의 SDK 프로젝트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="136c7-113">DefaultHoloLens2ConfigurationProfile은 HoloLens 2 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="136c7-114">자세한 내용은 [프로필을](../features/profiles/profiles.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="136c7-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="136c7-115">기본 Mixed Reality 도구 키트 구성 프로필을 열면 검사기에서 다음 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="136c7-116">장면에서 MixedRealityToolkit 없이 MixedRealityToolkitConfigurationProfile 자산을 선택하면 MRTK가 자동으로 장면을 설정할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="136c7-117">선택 사항이긴 하지만 모든 구성 화면에 액세스하려면 장면에 활성 MixedRealityToolkit 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="136c7-118">여기에는 프로젝트에 대한 현재 활성 런타임 구성이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="136c7-119">여기에서 다음을 포함하여 MRTK에 대한 모든 구성 프로필로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="136c7-120">Mixed Reality 도구 키트 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="136c7-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="136c7-121">기본 Mixed Reality 도구 키트 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="136c7-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="136c7-122">환경 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="136c7-123">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="136c7-124">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="136c7-125">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="136c7-126">원격 보고 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="136c7-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="136c7-127">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="136c7-128">진단 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="136c7-129">장면 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="136c7-130">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="136c7-131">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="136c7-132">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="136c7-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="136c7-133">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="136c7-134">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="136c7-135">음성 명령</span><span class="sxs-lookup"><span data-stu-id="136c7-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="136c7-136">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="136c7-137">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="136c7-138">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="136c7-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="136c7-139">서비스 검사기</span><span class="sxs-lookup"><span data-stu-id="136c7-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="136c7-140">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="136c7-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="136c7-141">런타임 시 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="136c7-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="136c7-142">MRTK 초기화 프로필 전환 전</span><span class="sxs-lookup"><span data-stu-id="136c7-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="136c7-143">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="136c7-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="136c7-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="136c7-144">See also</span></span>](#see-also)

<span data-ttu-id="136c7-145">이러한 구성 프로필은 관련 섹션에서 아래에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="136c7-146">환경 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-146">Experience settings</span></span>

<span data-ttu-id="136c7-147">기본 Mixed Reality 도구 키트 구성 페이지에 있는 이 설정은 프로젝트에 대한 [Mixed Reality 환경 확장의](/windows/mixed-reality/coordinate-systems-in-unity) 기본 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="136c7-148">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-148">Camera settings</span></span>

<span data-ttu-id="136c7-149">카메라 설정은 일반 클리핑, 품질 및 투명도 설정을 정의하여 Mixed Reality 프로젝트에 대한 카메라를 설정하는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="136c7-150">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-150">Input system settings</span></span>

<span data-ttu-id="136c7-151">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트 주변의 모든 입력 이벤트를 라우팅하기 위한 강력하고 잘 학습된 입력 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="136c7-152">MRTK에서 제공하는 입력 시스템 뒤에는 여러 다른 시스템이 있으며, 다중 플랫폼/혼합 현실 프레임워크의 복잡성을 추상화하기 위해 필요한 복잡한 인터위브를 구동하고 관리하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="136c7-153">각 개별 프로필은 아래에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="136c7-154">포커스 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-154">Focus Settings</span></span>
- [<span data-ttu-id="136c7-155">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="136c7-156">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="136c7-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="136c7-157">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="136c7-158">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="136c7-159">음성 명령</span><span class="sxs-lookup"><span data-stu-id="136c7-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="136c7-160">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="136c7-161">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="136c7-162">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-162">Boundary visualization settings</span></span>

<span data-ttu-id="136c7-163">경계 시스템은 기본 플랫폼 경계/보호자 시스템에서 보고한 인식된 경계를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="136c7-164">경계 시각화 도우미 구성을 사용하면 사용자의 위치를 기준으로 장면 내에서 기록된 경계를 자동으로 표시할 수 있습니다. 또한 경계는 사용자가 장면 내에서 원격으로 전송하는 위치에 따라 반응/업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="136c7-165">원격 보고 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="136c7-165">Teleportation system selection</span></span>

<span data-ttu-id="136c7-166">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트에서 원격 보고 이벤트를 관리하기 위한 모든 기능을 갖춘 원격 보고 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="136c7-167">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-167">Spatial awareness settings</span></span>

<span data-ttu-id="136c7-168">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트에서 공간 검색 시스템을 사용할 수 있는 다시 빌드된 공간 인식 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="136c7-169">Mixed Reality 도구 키트 공간 인식 구성을 사용하면 애플리케이션이 프로그래밍 방식으로 시작되거나 나중에 시작될 때 자동으로 시작되는지 여부와 관계없이 시스템이 시작되는 방식을 조정할 수 있을 뿐만 아니라 보기 필드에 대한 익스텐트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="136c7-170">또한 메시 및 표면 설정을 구성하고 프로젝트에서 주변 환경을 이해하는 방법을 추가로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="136c7-171">이는 검색된 환경을 제공할 수 있는 디바이스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="136c7-172">진단 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-172">Diagnostics settings</span></span>

<span data-ttu-id="136c7-173">MRTK의 선택적이지만 매우 유용한 기능은 플러그 인 진단 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="136c7-174">진단 프로필은 프로젝트가 실행되는 동안 모니터링할 수 있는 몇 가지 간단한 시스템을 제공합니다. 여기에는 장면에서 디스플레이 패널을 사용하거나 사용하지 않도록 설정하는 편리한 켜기/끄기 스위치가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="136c7-175">장면 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-175">Scene system settings</span></span>

<span data-ttu-id="136c7-176">MRTK는 복잡한 가감 장면 로드/언로드를 관리하는 데 도움이 되는 이 선택적 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="136c7-177">장면 시스템이 프로젝트에 적합한지 여부를 결정하려면 [장면 시스템 시작 가이드를 참조하세요.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="136c7-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="136c7-178">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-178">Additional services settings</span></span>

<span data-ttu-id="136c7-179">Mixed Reality 도구 키트의 고급 영역 중 하나는 프레임워크에 "서비스"를 등록할 수 있는 [서비스 로케이터 패턴](https://en.wikipedia.org/wiki/Service_locator_pattern) 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="136c7-180">이렇게 하면 프레임워크를 새로운 기능/시스템으로 쉽게 확장할 수 있을 뿐만 아니라 프로젝트에서 이러한 기능을 활용하여 자체 런타임 구성 요소를 등록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="136c7-181">등록된 모든 서비스는 MonoBehaviour 또는 어설프게 싱글톤 패턴을 구현하는 오버헤드와 비용 없이 모든 Unity 이벤트를 최대한 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="136c7-182">이를 통해 시스템 생성, 런타임 게임 논리 또는 실제로 다른 모든 것과 같은 포그라운드 및 백그라운드 프로세스를 실행하기 위한 장면 오버헤드가 없는 순수 C# 구성 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="136c7-183">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-183">Input actions settings</span></span>

<span data-ttu-id="136c7-184">입력 작업은 런타임 프로젝트의 물리적 상호 작용 및 입력을 추상화할 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="136c7-185">모든 실제 입력(컨트롤러/손/마우스/등)은 런타임 프로젝트에서 사용할 논리적 입력 작업으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="136c7-186">이렇게 하면 입력이 어디에서 오는지와 관계없이 프로젝트에서 이러한 작업을 장면에서 "수행할 작업" 또는 "상호 작용"으로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="136c7-187">새 입력 작업을 만들려면 "새 작업 추가" 단추를 클릭하고 표시되는 내용에 대한 친숙한 텍스트 이름을 입력하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="136c7-188">그런 다음 작업이 전달하려는 축(데이터 형식)만 선택하거나 물리적 컨트롤러의 경우 연결할 수 있는 물리적 입력 형식만 있으면 됩니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="136c7-189">축 제약 조건</span><span class="sxs-lookup"><span data-stu-id="136c7-189">Axis Constraint</span></span> | <span data-ttu-id="136c7-190">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="136c7-190">Data Type</span></span> | <span data-ttu-id="136c7-191">설명</span><span class="sxs-lookup"><span data-stu-id="136c7-191">Description</span></span> | <span data-ttu-id="136c7-192">예제 사용</span><span class="sxs-lookup"><span data-stu-id="136c7-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="136c7-193">없음</span><span class="sxs-lookup"><span data-stu-id="136c7-193">None</span></span> | <span data-ttu-id="136c7-194">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="136c7-194">No data</span></span> | <span data-ttu-id="136c7-195">빈 작업 또는 이벤트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-195">Used for an empty action or event</span></span> | <span data-ttu-id="136c7-196">이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="136c7-196">Event Trigger</span></span> |
| <span data-ttu-id="136c7-197">원시(예약됨)</span><span class="sxs-lookup"><span data-stu-id="136c7-197">Raw (reserved)</span></span> | <span data-ttu-id="136c7-198">object</span><span class="sxs-lookup"><span data-stu-id="136c7-198">object</span></span> | <span data-ttu-id="136c7-199">나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-199">Reserved for future use</span></span> | <span data-ttu-id="136c7-200">해당 없음</span><span class="sxs-lookup"><span data-stu-id="136c7-200">N/A</span></span> |
| <span data-ttu-id="136c7-201">디지털</span><span class="sxs-lookup"><span data-stu-id="136c7-201">Digital</span></span> | <span data-ttu-id="136c7-202">bool</span><span class="sxs-lookup"><span data-stu-id="136c7-202">bool</span></span> | <span data-ttu-id="136c7-203">부울 on 또는 off 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="136c7-203">A boolean on or off type data</span></span> | <span data-ttu-id="136c7-204">컨트롤러 단추</span><span class="sxs-lookup"><span data-stu-id="136c7-204">A controller button</span></span> |
| <span data-ttu-id="136c7-205">단일 축</span><span class="sxs-lookup"><span data-stu-id="136c7-205">Single Axis</span></span> | <span data-ttu-id="136c7-206">float</span><span class="sxs-lookup"><span data-stu-id="136c7-206">float</span></span> | <span data-ttu-id="136c7-207">단일 전체 자릿수 데이터 값</span><span class="sxs-lookup"><span data-stu-id="136c7-207">A single precision data value</span></span> | <span data-ttu-id="136c7-208">트리거 등의 원거리 입력</span><span class="sxs-lookup"><span data-stu-id="136c7-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="136c7-209">이중 축</span><span class="sxs-lookup"><span data-stu-id="136c7-209">Dual Axis</span></span> | <span data-ttu-id="136c7-210">Vector2.x</span><span class="sxs-lookup"><span data-stu-id="136c7-210">Vector2</span></span> | <span data-ttu-id="136c7-211">여러 축에 대 한 이중 부동 소수점 형식 날짜</span><span class="sxs-lookup"><span data-stu-id="136c7-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="136c7-212">Dpad 또는 엄지 스틱</span><span class="sxs-lookup"><span data-stu-id="136c7-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="136c7-213">세 개의 Dof 위치</span><span class="sxs-lookup"><span data-stu-id="136c7-213">Three Dof Position</span></span> | <span data-ttu-id="136c7-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="136c7-214">Vector3</span></span> | <span data-ttu-id="136c7-215">3 개의 float 축에서의 위치 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="136c7-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="136c7-216">3D 위치 스타일 전용 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="136c7-216">3D position style only controller</span></span> |
| <span data-ttu-id="136c7-217">3 Dof 회전</span><span class="sxs-lookup"><span data-stu-id="136c7-217">Three Dof Rotation</span></span> | <span data-ttu-id="136c7-218">시작할</span><span class="sxs-lookup"><span data-stu-id="136c7-218">Quaternion</span></span> | <span data-ttu-id="136c7-219">4 개의 float 축이 있는 회전 전용 입력</span><span class="sxs-lookup"><span data-stu-id="136c7-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="136c7-220">3도 스타일 컨트롤러 (예: Oculus Go 컨트롤러)</span><span class="sxs-lookup"><span data-stu-id="136c7-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="136c7-221">6 Dof</span><span class="sxs-lookup"><span data-stu-id="136c7-221">Six Dof</span></span> | <span data-ttu-id="136c7-222">혼합 현실 포즈 (Vector3, 4 원수)</span><span class="sxs-lookup"><span data-stu-id="136c7-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="136c7-223">Vector3 및 4 원수 구성 요소를 모두 사용 하는 위치 및 회전 스타일 입력</span><span class="sxs-lookup"><span data-stu-id="136c7-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="136c7-224">동작 컨트롤러 또는 포인터</span><span class="sxs-lookup"><span data-stu-id="136c7-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="136c7-225">입력 작업을 활용 하는 이벤트는 실제 컨트롤러로 제한 되지 않으며 런타임 효과를 사용 하 여 새 작업을 생성 하는 프로젝트 내에서 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="136c7-226">입력 작업은 런타임에 편집할 수 없는 몇 가지 구성 요소 중 하나 이며 디자인 타임 구성 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="136c7-227">이 프로필은 각 작업에 대해 생성 된 ID의 프레임 워크 (및 프로젝트) 종속성으로 인해 프로젝트가 실행 되는 동안에는 교환 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="136c7-228">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="136c7-228">Input actions rules</span></span>

<span data-ttu-id="136c7-229">입력 동작 규칙은의 한 입력 작업에 대해 발생 한 이벤트를 해당 데이터 값을 기반으로 하는 다른 작업으로 자동으로 변환 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="136c7-230">이러한 작업은 프레임 워크 내에서 원활 하 게 관리 되며 성능 비용은 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="136c7-231">예를 들어 아래 이미지에 나와 있는 것 처럼 DPad의 단일 이중 축 입력 이벤트를에서 4 개의 해당 "Dpad Up"/"DPad Down"/"Dpad Left"/"Dpad Right" 동작으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="136c7-232">사용자의 코드에서이 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-232">This could also be done in your own code.</span></span> <span data-ttu-id="136c7-233">그러나 이것이 매우 일반적인 패턴 이라고 표시 되는 것 처럼 프레임 워크는이를 "바로" 제공 하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="136c7-234">입력 작업 규칙은 사용 가능한 입력 축에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="136c7-235">그러나 한 축 유형의 입력 작업은 동일한 축 유형의 다른 입력 동작으로 변환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="136c7-236">이중 축 동작을 다른 이중 축 작업에 매핑할 수 있지만 디지털 또는 없음 작업에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![입력 작업 규칙 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="136c7-238">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-238">Pointer configuration</span></span>

<span data-ttu-id="136c7-239">포인터는 모든 입력 장치에서 장면에서 상호 작용을 구동 하는 데 사용 됩니다 .이 경우에는 (collider가 연결 되어 있거나 UI 구성 요소) 장면의 모든 개체에 방향 및 적중 테스트를 모두 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="136c7-240">포인터는 기본적으로 컨트롤러, 헤드셋 (응시/포커스) 및 마우스/터치 입력에 대해 자동으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="136c7-241">혼합 현실 도구 키트에서 제공 하는 다 수의 선 구성 요소 중 하나를 사용 하거나 MRTK IMixedRealityPointer 인터페이스를 구현 하는 경우 사용자 고유의 포인터를 사용 하 여 활성 장면 내에서 포인터를 시각화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="136c7-242">가리키기 익스텐트: 응시를 포함 하 여 모든 포인터에 대 한 전역 포인팅 익스텐트를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="136c7-243">Raycast 계층 마스크 가리키기: raycast 계층 포인터를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="136c7-244">디버그 그리기 포인팅 광선: raycasting에 사용 되는 광선을 시각화 하는 디버그 도우미입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="136c7-245">디버그 그리기 광선 색: 시각화에 사용할 색 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="136c7-246">응시 cursor prefab: 장면에 대해 전역 응시 커서를 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="136c7-247">필요한 경우에는 응시 공급자로 신속 하 게 이동 하 여 응시의 특정 값을 재정의할 수 있는 추가 도우미 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="136c7-248">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-248">Gestures configuration</span></span>

<span data-ttu-id="136c7-249">제스처는 다양 한 Sdk (예: HoloLens)에서 제공 하는 다양 한 "제스처" 입력 메서드에 입력 작업을 할당 하는 데 사용할 수 있는 시스템 관련 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="136c7-250">현재 제스처 구현은 HoloLens 전용 이며 나중에 도구 키트에 추가 될 때 다른 시스템에 대해 향상 됩니다 (아직 날짜 없음).</span><span class="sxs-lookup"><span data-stu-id="136c7-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="136c7-251">음성 명령</span><span class="sxs-lookup"><span data-stu-id="136c7-251">Speech commands</span></span>

<span data-ttu-id="136c7-252">제스처와 마찬가지로 일부 런타임 플랫폼은 Unity 프로젝트에서 받을 수 있는 명령을 생성 하는 기능과 함께 지능형 "음성 텍스트" 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="136c7-253">이 구성 프로필을 사용 하 여 다음을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="136c7-254">일반 설정-자동 시작 또는 수동 시작으로 설정 된 "시작 동작"은 입력 시스템 시작 시 KeywordRecognizer를 초기화할 지 여부를 결정 하거나, 프로젝트에서 KeywordRecognizer를 초기화할 시기를 결정 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="136c7-255">"인식 신뢰 수준"은 Unity의 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) 를 초기화 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="136c7-256">음성 명령-"단어"를 등록 하 고에서 프로젝트에 수신 될 수 있는 입력 작업으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="136c7-257">필요한 경우 키보드 작업에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="136c7-258">시스템은 현재 Windows 10 플랫폼 (예: HoloLens 및 Windows 10 desktop)에서 실행 되는 경우에만 음성을 지원 하 고 나중에 MRTK에 추가 될 때 다른 시스템에 대해 향상 됩니다 (아직 날짜 없음).</span><span class="sxs-lookup"><span data-stu-id="136c7-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="136c7-259">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="136c7-259">Controller mapping configuration</span></span>

<span data-ttu-id="136c7-260">Mixed Reality Toolkit의 핵심 구성 화면 중 하나는 프로젝트에서 사용할 수 있는 다양 한 유형의 컨트롤러를 구성 하 고 매핑할 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="136c7-261">아래 구성 화면에서는 도구 키트에서 현재 인식 되는 컨트롤러를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="136c7-262">MRTK는 다음 컨트롤러/시스템에 대 한 기본 구성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="136c7-263">마우스 (3D 공간 마우스 지원 포함)</span><span class="sxs-lookup"><span data-stu-id="136c7-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="136c7-264">터치 스크린</span><span class="sxs-lookup"><span data-stu-id="136c7-264">Touch Screen</span></span>
- <span data-ttu-id="136c7-265">Xbox 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="136c7-265">Xbox controllers</span></span>
- <span data-ttu-id="136c7-266">Windows Mixed Reality 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="136c7-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="136c7-267">HoloLens 제스처</span><span class="sxs-lookup"><span data-stu-id="136c7-267">HoloLens Gestures</span></span>
- <span data-ttu-id="136c7-268">HTC Vive 지팡이 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="136c7-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="136c7-269">Octouch 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="136c7-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="136c7-270">원격 컨트롤러 (oculus)</span><span class="sxs-lookup"><span data-stu-id="136c7-270">Oculus Remote controller</span></span>
- <span data-ttu-id="136c7-271">일반 OpenVR 장치 (고급 사용자만 해당)</span><span class="sxs-lookup"><span data-stu-id="136c7-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="136c7-272">미리 빌드된 컨트롤러 시스템 중 하나에 대 한 이미지를 클릭 하면 해당 하는 모든 입력에 대해 단일 입력 작업을 구성할 수 있습니다. 예를 들어 아래 Oculus Touch controller 구성 화면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="136c7-273">위에서 식별 되지 않은 다른 OpenVR 또는 Unity 입력 컨트롤러를 구성 하는 고급 화면도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="136c7-274">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="136c7-274">Controller visualization settings</span></span>

<span data-ttu-id="136c7-275">컨트롤러 매핑 외에도 별도의 구성 프로필을 제공 하 여 사용자가 배후에 컨트롤러를 표시 하는 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="136c7-276">이는 "전역" (특정 손으로 컨트롤러의 모든 인스턴스)에서 구성 하거나 개별 컨트롤러 유형/손으로 특정 하 게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="136c7-277">MRTK는 Windows Mixed Reality 및 OpenVR에 대해 네이티브 SDK 컨트롤러 모델도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="136c7-278">이러한는 장면에서 Gameobject로 로드 되 고 플랫폼의 컨트롤러 추적을 사용 하 여 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="136c7-279">장면의 컨트롤러 표현이 실제 컨트롤러 위치에서 오프셋 되어야 하는 경우에는 컨트롤러 모델의 prefab (예: 오프셋 위치를 사용 하 여 컨트롤러 prefab의 변환 위치 설정)에 대해 해당 오프셋을 설정 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="136c7-280">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="136c7-280">Editor utilities</span></span>

<span data-ttu-id="136c7-281">다음 유틸리티는 편집기 에서만 작동 하며 개발 생산성을 높이는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 편집기 구성 유틸리티](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="136c7-283">서비스 검사기</span><span class="sxs-lookup"><span data-stu-id="136c7-283">Service inspectors</span></span>

<span data-ttu-id="136c7-284">서비스 검사기는 활성 서비스를 나타내는 장면 내 개체를 생성 하는 편집기 전용 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="136c7-285">이러한 개체를 선택 하면 설명서 링크를 제공 하 고, 편집기 시각화를 제어 하 고, 서비스 상태를 파악 하는 검사가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="136c7-286">구성 프로필의 *편집기 설정* 에서 *서비스 검사기 사용* 을 선택 하 여 서비스 검사기를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="136c7-287">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="136c7-287">Depth buffer renderer</span></span>

<span data-ttu-id="136c7-288">일부 혼합 현실 플랫폼과 깊이 버퍼를 공유 하면 [홀로그램 안정화](../performance/hologram-stabilization.md)를 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="136c7-289">예를 들어 Windows Mixed Reality 플랫폼은 프레임을 렌더링 하는 데 걸린 시간 동안 미세한 헤드 이동을 고려 하 여 픽셀 당 렌더링 된 장면을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="136c7-290">그러나 이러한 기술에는 사용자 로부터 기 하 도형 어디에 있는지 파악 하기 위해 정확한 데이터가 포함 된 깊이 버퍼가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="136c7-291">장면에서 필요한 모든 데이터를 깊이 버퍼로 렌더링 하도록 하기 위해 개발자는 구성 프로필의 *편집기 설정* 에서 *렌더링 수준 버퍼* 기능을 설정/해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="136c7-292">그러면 현재 깊이 버퍼가 사용 되 고 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , 기본 카메라에 사후 처리 효과를 적용 하 여 장면 보기에 색으로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="136c7-293">![렌더링 깊이 버퍼 유틸리티 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>장면의 파란색 실린더에는 깊이 데이터가 기록 되지 않도록 zwrite off가 포함 된 재료가 있습니다</sup> .</span><span class="sxs-lookup"><span data-stu-id="136c7-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="136c7-294">런타임에 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="136c7-294">Changing profiles at runtime</span></span>

<span data-ttu-id="136c7-295">런타임에 프로필을 업데이트할 수 있으며, 일반적으로 다음과 같은 두 가지 시나리오와 시간이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="136c7-296">**이전 mrtk 초기화 프로필 스위치**: 시작 시 mrtk가 초기화 되 고 프로필이 활성 상태가 되기 전에 장치 기능에 따라 다른 기능을 사용 하거나 사용 하지 않도록 설정 하는 사용 하지 않는 프로필을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="136c7-297">예를 들어 환경이 공간 매핑 하드웨어가 없는 VR에서 실행 되는 경우 공간 매핑 구성 요소를 사용 하도록 설정 하는 것이 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="136c7-298">**활성 프로필 스위치**: 시작 후 MRTK가 초기화 되 고 프로필이 활성 상태가 된 후 현재 사용 중인 프로필을 교환 하 여 특정 기능의 동작 방식을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="136c7-299">예를 들어 응용 프로그램에 특정 하위 환경이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="136c7-300">이전 MRTK 초기화 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="136c7-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="136c7-301">이는 MRTK 초기화 전에 실행 되는 MonoBehaviour (예:)를 연결 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="136c7-302">스크립트 (예: 호출)는 스크립트 `SetProfileBeforeInitialization` `MixedRealityToolkit` [실행 순서 설정을](https://docs.unity3d.com/Manual/class-MonoManager.html)설정 하 여 수행할 수 있는 스크립트 보다 먼저 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="136c7-303">"ProfileToUse" 대신 특정 플랫폼에 적용 되는 임의의 프로필 집합을 포함할 수 있습니다 (예: HoloLens 1의 경우 하나, VR의 경우 하나, HoloLens 2의 경우 하나).</span><span class="sxs-lookup"><span data-stu-id="136c7-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="136c7-304">로드할 프로필을 파악 하기 위해 다양 한 표시기 (예: https://docs.unity3d.com/ScriptReference/SystemInfo.html 또는 카메라가 불투명/투명 한지 여부)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="136c7-305">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="136c7-305">Active profile switch</span></span>

<span data-ttu-id="136c7-306">이를 위해서는 `MixedRealityToolkit.Instance.ActiveProfile` 활성 프로필을 대체 하는 새 프로필로 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="136c7-307">참고 런타임 중에 설정 하는 경우 `ActiveProfile` 현재 실행 중인 서비스의 삭제는 모든 서비스의 마지막 behaviour () 이후에 발생 하며, 새 프로필과 연결 된 서비스의 인스턴스화 및 초기화는 모든 서비스의 첫 번째 업데이트 () 이전에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="136c7-308">이 프로세스 중에는 눈에 띄는 응용 프로그램 hesitation 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="136c7-309">또한 스크립트 보다 우선 순위가 높은 모든 스크립트는 `MixedRealityToolkit` 새 프로필이 제대로 설정 되기 전에 해당 업데이트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="136c7-310">스크립트 우선 순위에 대 한 자세한 내용은 [스크립트 실행 순서 설정](https://docs.unity3d.com/Manual/class-MonoManager.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="136c7-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="136c7-311">프로필 전환 프로세스에서 기존 UI 카메라는 변경 되지 않은 상태로 유지 되 고, canvas를 필요로 하는 Unity UI 구성 요소가 스위치 후에도 계속 작동 하도록 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="136c7-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="136c7-312">참조</span><span class="sxs-lookup"><span data-stu-id="136c7-312">See also</span></span>

- [<span data-ttu-id="136c7-313">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="136c7-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)