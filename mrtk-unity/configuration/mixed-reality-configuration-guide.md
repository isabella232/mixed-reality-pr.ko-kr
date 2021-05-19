---
title: Mixed Reality 구성 가이드
description: MRTK를 unity로 구성하는 설명서입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143577"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="63f0b-104">Mixed Reality 도구 키트 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="63f0b-104">Mixed Reality Toolkit profile configuration guide</span></span>

![MRTK 로고](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="63f0b-106">Mixed Reality 도구 키트는 도구 키트를 관리하는 데 필요한 구성을 최대한 많이 중앙 집중화합니다(진정한 런타임 "사물"제외).</span><span class="sxs-lookup"><span data-stu-id="63f0b-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="63f0b-107">이 가이드는 현재 도구 키트에 사용할 수 있는 각 구성 프로필 화면에 대한 간단한 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="63f0b-108">기본 Mixed Reality 도구 키트 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="63f0b-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="63f0b-109">장면의 *MixedRealityToolkit* GameObject에 연결된 기본 구성 프로필은 프로젝트의 도구 키트에 대한 기본 진입점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="63f0b-110">Mixed Reality 도구 키트는 기본 구성 화면을 "잠가" 프로젝트에 대한 공통 시작점이 항상 있는지 확인하고 프로젝트가 발전함에 따라 사용자 고유의 설정을 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="63f0b-111">재생 모드 중에는 MRTK 구성을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-111">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 구성 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="63f0b-113">Mixed Reality Toolkit에 대한 모든 "기본" 프로필은 Assets/MRTK/SDK/Profiles 폴더의 SDK 프로젝트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63f0b-114">DefaultHoloLens2ConfigurationProfile은 HoloLens 2 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="63f0b-115">자세한 내용은 [프로필을](../features/profiles/profiles.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63f0b-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="63f0b-116">기본 Mixed Reality 도구 키트 구성 프로필을 열면 검사기에서 다음 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="63f0b-117">장면에서 MixedRealityToolkit 없이 MixedRealityToolkitConfigurationProfile 자산을 선택하면 MRTK가 자동으로 장면을 설정할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="63f0b-118">선택 사항이긴 하지만 모든 구성 화면에 액세스하려면 장면에 활성 MixedRealityToolkit 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="63f0b-119">여기에는 프로젝트에 대한 현재 활성 런타임 구성이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="63f0b-120">여기에서 다음을 포함하여 MRTK에 대한 모든 구성 프로필로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="63f0b-121">Mixed Reality 도구 키트 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="63f0b-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="63f0b-122">기본 Mixed Reality 도구 키트 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="63f0b-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="63f0b-123">환경 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="63f0b-124">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="63f0b-125">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="63f0b-126">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="63f0b-127">Teleportation 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="63f0b-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="63f0b-128">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="63f0b-129">진단 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="63f0b-130">시스템 설정 장면</span><span class="sxs-lookup"><span data-stu-id="63f0b-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="63f0b-131">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="63f0b-132">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="63f0b-133">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="63f0b-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="63f0b-134">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="63f0b-135">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="63f0b-136">음성 명령</span><span class="sxs-lookup"><span data-stu-id="63f0b-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="63f0b-137">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="63f0b-138">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="63f0b-139">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="63f0b-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="63f0b-140">서비스 검사기</span><span class="sxs-lookup"><span data-stu-id="63f0b-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="63f0b-141">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="63f0b-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="63f0b-142">런타임에 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="63f0b-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="63f0b-143">이전 MRTK 초기화 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="63f0b-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="63f0b-144">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="63f0b-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="63f0b-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63f0b-145">See also</span></span>](#see-also)

<span data-ttu-id="63f0b-146">이러한 구성 프로필은 아래 관련 섹션에서 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="63f0b-147">환경 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-147">Experience settings</span></span>

<span data-ttu-id="63f0b-148">기본 Mixed Reality 도구 키트 구성 페이지에 있는 이 설정은 프로젝트에 대한 [Mixed Reality 환경 확장의](/windows/mixed-reality/coordinate-systems-in-unity) 기본 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="63f0b-149">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-149">Camera settings</span></span>

<span data-ttu-id="63f0b-150">카메라 설정은 일반 클리핑, 품질 및 투명도 설정을 정의하여 Mixed Reality 프로젝트에 대한 카메라를 설정하는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="63f0b-151">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-151">Input system settings</span></span>

<span data-ttu-id="63f0b-152">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트 주변의 모든 입력 이벤트를 라우팅하기 위한 강력하고 잘 학습된 입력 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="63f0b-153">MRTK에서 제공하는 입력 시스템 뒤에는 여러 다른 시스템이 있으며, 다중 플랫폼/혼합 현실 프레임워크의 복잡성을 추상화하기 위해 필요한 복잡한 직비 간을 구동하고 관리하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="63f0b-154">각 개별 프로필은 아래에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="63f0b-155">포커스 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-155">Focus Settings</span></span>
- [<span data-ttu-id="63f0b-156">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="63f0b-157">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="63f0b-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="63f0b-158">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="63f0b-159">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="63f0b-160">음성 명령</span><span class="sxs-lookup"><span data-stu-id="63f0b-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="63f0b-161">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="63f0b-162">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="63f0b-163">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-163">Boundary visualization settings</span></span>

<span data-ttu-id="63f0b-164">경계 시스템은 기본 플랫폼 경계/보호자 시스템에서 보고하는 인식된 경계를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="63f0b-165">경계 시각화 도우미 구성을 사용하면 사용자의 위치를 기준으로 장면 내에서 기록된 경계를 자동으로 표시할 수 있습니다. 또한 경계는 사용자가 장면 내에서 원격으로 전송하는 위치에 따라 반응/업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="63f0b-166">원격 보고 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="63f0b-166">Teleportation system selection</span></span>

<span data-ttu-id="63f0b-167">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트에서 원격 보고 이벤트를 관리하기 위한 모든 기능을 갖춘 원격 보고 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="63f0b-168">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-168">Spatial awareness settings</span></span>

<span data-ttu-id="63f0b-169">Mixed Reality 프로젝트는 기본적으로 선택된 프로젝트에서 공간 검색 시스템을 사용할 수 있는 다시 빌드된 공간 인식 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="63f0b-170">Mixed Reality 도구 키트 공간 인식 구성을 사용하면 애플리케이션이 프로그래밍 방식으로 시작되거나 나중에 시작될 때 자동으로 시작되는지 여부와 관계없이 시스템이 시작되는 방식을 조정할 수 있을 뿐만 아니라 보기 필드에 대한 익스텐트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="63f0b-171">또한 메시 및 표면 설정을 구성하고 프로젝트에서 주변 환경을 이해하는 방법을 추가로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="63f0b-172">이는 검색된 환경을 제공할 수 있는 디바이스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="63f0b-173">진단 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-173">Diagnostics settings</span></span>

<span data-ttu-id="63f0b-174">MRTK의 선택적이지만 매우 유용한 기능은 플러그 인 진단 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="63f0b-175">진단 프로필은 프로젝트가 실행되는 동안 모니터링할 수 있는 몇 가지 간단한 시스템을 제공합니다. 여기에는 장면에서 디스플레이 패널을 사용하거나 사용하지 않도록 설정하는 편리한 켜기/끄기 스위치가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="63f0b-176">장면 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-176">Scene system settings</span></span>

<span data-ttu-id="63f0b-177">MRTK는 복잡한 가감 장면 로드/언로드를 관리하는 데 도움이 되는 이 선택적 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="63f0b-178">장면 시스템이 프로젝트에 적합한지 여부를 결정하려면 [장면 시스템 시작 가이드를 참조하세요.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="63f0b-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="63f0b-179">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-179">Additional services settings</span></span>

<span data-ttu-id="63f0b-180">Mixed Reality 도구 키트의 고급 영역 중 하나는 프레임워크에 "서비스"를 등록할 수 있는 [서비스 로케이터 패턴](https://en.wikipedia.org/wiki/Service_locator_pattern) 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="63f0b-181">이렇게 하면 프레임워크를 새로운 기능/시스템으로 쉽게 확장할 수 있을 뿐만 아니라 프로젝트에서 이러한 기능을 활용하여 자체 런타임 구성 요소를 등록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="63f0b-182">등록된 모든 서비스는 MonoBehaviour 또는 어설프게 싱글톤 패턴을 구현하는 오버헤드와 비용 없이 모든 Unity 이벤트를 최대한 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="63f0b-183">이를 통해 포그라운드 및 백그라운드 프로세스(예: 시스템 생성, 런타임 게임 논리 또는 거의 모든 것)를 실행하기 위한 장면 오버헤드가 없는 순수 C# 구성 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="63f0b-184">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-184">Input actions settings</span></span>

<span data-ttu-id="63f0b-185">입력 작업은 런타임 프로젝트의 모든 물리적 상호 작용 및 입력을 추상화 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="63f0b-186">모든 실제 입력 (컨트롤러/직접/마우스/등)은 런타임 프로젝트에서 사용 하기 위한 논리적 입력 동작으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="63f0b-187">이렇게 하면 입력이 제공 되는 위치와 관계 없이 프로젝트에서 이러한 작업을 내부적으로 "할 일" 또는 "상호 작용"으로 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="63f0b-188">새 입력 작업을 만들려면 "새 작업 추가" 단추를 클릭 하 고 표시 되는 내용에 대 한 텍스트 이름을 입력 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="63f0b-189">그런 다음 동작을 전달할 축 (데이터 유형)만 선택 해야 합니다. 또는 실제 컨트롤러의 경우에는 다음과 같이 연결 될 수 있는 물리적 입력 유형을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="63f0b-190">축 제약 조건</span><span class="sxs-lookup"><span data-stu-id="63f0b-190">Axis Constraint</span></span> | <span data-ttu-id="63f0b-191">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="63f0b-191">Data Type</span></span> | <span data-ttu-id="63f0b-192">설명</span><span class="sxs-lookup"><span data-stu-id="63f0b-192">Description</span></span> | <span data-ttu-id="63f0b-193">예제 사용</span><span class="sxs-lookup"><span data-stu-id="63f0b-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="63f0b-194">없음</span><span class="sxs-lookup"><span data-stu-id="63f0b-194">None</span></span> | <span data-ttu-id="63f0b-195">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="63f0b-195">No data</span></span> | <span data-ttu-id="63f0b-196">빈 동작 또는 이벤트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-196">Used for an empty action or event</span></span> | <span data-ttu-id="63f0b-197">이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="63f0b-197">Event Trigger</span></span> |
| <span data-ttu-id="63f0b-198">Raw (예약 됨)</span><span class="sxs-lookup"><span data-stu-id="63f0b-198">Raw (reserved)</span></span> | <span data-ttu-id="63f0b-199">object</span><span class="sxs-lookup"><span data-stu-id="63f0b-199">object</span></span> | <span data-ttu-id="63f0b-200">나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-200">Reserved for future use</span></span> | <span data-ttu-id="63f0b-201">해당 없음</span><span class="sxs-lookup"><span data-stu-id="63f0b-201">N/A</span></span> |
| <span data-ttu-id="63f0b-202">디지털</span><span class="sxs-lookup"><span data-stu-id="63f0b-202">Digital</span></span> | <span data-ttu-id="63f0b-203">bool</span><span class="sxs-lookup"><span data-stu-id="63f0b-203">bool</span></span> | <span data-ttu-id="63f0b-204">부울 on 또는 off 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="63f0b-204">A boolean on or off type data</span></span> | <span data-ttu-id="63f0b-205">컨트롤러 단추</span><span class="sxs-lookup"><span data-stu-id="63f0b-205">A controller button</span></span> |
| <span data-ttu-id="63f0b-206">단일 축</span><span class="sxs-lookup"><span data-stu-id="63f0b-206">Single Axis</span></span> | <span data-ttu-id="63f0b-207">float</span><span class="sxs-lookup"><span data-stu-id="63f0b-207">float</span></span> | <span data-ttu-id="63f0b-208">단일 전체 자릿수 데이터 값</span><span class="sxs-lookup"><span data-stu-id="63f0b-208">A single precision data value</span></span> | <span data-ttu-id="63f0b-209">트리거 등의 원거리 입력</span><span class="sxs-lookup"><span data-stu-id="63f0b-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="63f0b-210">이중 축</span><span class="sxs-lookup"><span data-stu-id="63f0b-210">Dual Axis</span></span> | <span data-ttu-id="63f0b-211">Vector2.x</span><span class="sxs-lookup"><span data-stu-id="63f0b-211">Vector2</span></span> | <span data-ttu-id="63f0b-212">여러 축에 대 한 이중 부동 소수점 형식 날짜</span><span class="sxs-lookup"><span data-stu-id="63f0b-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="63f0b-213">Dpad 또는 엄지 스틱</span><span class="sxs-lookup"><span data-stu-id="63f0b-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="63f0b-214">세 개의 Dof 위치</span><span class="sxs-lookup"><span data-stu-id="63f0b-214">Three Dof Position</span></span> | <span data-ttu-id="63f0b-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="63f0b-215">Vector3</span></span> | <span data-ttu-id="63f0b-216">float 축이 3개인 의 위치 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="63f0b-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="63f0b-217">3D 위치 스타일 전용 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="63f0b-217">3D position style only controller</span></span> |
| <span data-ttu-id="63f0b-218">Dof 회전 3개</span><span class="sxs-lookup"><span data-stu-id="63f0b-218">Three Dof Rotation</span></span> | <span data-ttu-id="63f0b-219">쿼터니언</span><span class="sxs-lookup"><span data-stu-id="63f0b-219">Quaternion</span></span> | <span data-ttu-id="63f0b-220">float 축이 4개인 회전 전용 입력</span><span class="sxs-lookup"><span data-stu-id="63f0b-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="63f0b-221">3도 스타일 컨트롤러(예: Oculus Go 컨트롤러)</span><span class="sxs-lookup"><span data-stu-id="63f0b-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="63f0b-222">Six Dof</span><span class="sxs-lookup"><span data-stu-id="63f0b-222">Six Dof</span></span> | <span data-ttu-id="63f0b-223">Mixed Reality 자세(Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="63f0b-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="63f0b-224">Vector3 및 Quaternion 구성 요소가 모두 있는 위치 및 회전 스타일 입력</span><span class="sxs-lookup"><span data-stu-id="63f0b-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="63f0b-225">모션 컨트롤러 또는 포인터</span><span class="sxs-lookup"><span data-stu-id="63f0b-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="63f0b-226">입력 작업을 활용하는 이벤트는 실제 컨트롤러로 제한되지 않으며, 프로젝트 내에서 계속 활용하여 런타임 효과가 새 작업을 생성하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="63f0b-227">입력 작업은 런타임에 편집할 수 없는 몇 가지 구성 요소 중 하나이며 디자인 타임 구성에만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="63f0b-228">각 작업에 대해 생성된 ID에 대한 프레임워크(및 프로젝트) 종속성으로 인해 프로젝트가 실행되는 동안에는 이 프로필을 교환해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="63f0b-229">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="63f0b-229">Input actions rules</span></span>

<span data-ttu-id="63f0b-230">입력 작업 규칙은 의 한 입력 동작에 대해 발생된 이벤트를 해당 데이터 값에 따라 다른 작업으로 자동으로 변환하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="63f0b-231">프레임워크 내에서 원활하게 관리되며 성능 비용이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="63f0b-232">예를 들어 의 DPad에서 단일 이중 축 입력 이벤트를 해당하는 4개 "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" 작업(아래 이미지에 표시)으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="63f0b-233">사용자 고유의 코드에서 이 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-233">This could also be done in your own code.</span></span> <span data-ttu-id="63f0b-234">그러나 이것이 매우 일반적인 패턴인 것을 볼 때 프레임워크는 이 작업을 "기본 제공"하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="63f0b-235">입력 작업 규칙은 사용 가능한 입력 축에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="63f0b-236">그러나 한 축 유형의 입력 작업은 동일한 축 유형의 다른 입력 동작으로 변환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="63f0b-237">이중 축 동작을 다른 이중 축 작업에 매핑할 수 있지만 디지털 또는 없음 작업에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![입력 작업 규칙 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="63f0b-239">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-239">Pointer configuration</span></span>

<span data-ttu-id="63f0b-240">포인터는 모든 입력 장치에서 장면에서 상호 작용을 구동 하는 데 사용 됩니다 .이 경우에는 (collider가 연결 되어 있거나 UI 구성 요소) 장면의 모든 개체에 방향 및 적중 테스트를 모두 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="63f0b-241">포인터는 기본적으로 컨트롤러, 헤드셋 (응시/포커스) 및 마우스/터치 입력에 대해 자동으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="63f0b-242">혼합 현실 도구 키트에서 제공 하는 다 수의 선 구성 요소 중 하나를 사용 하거나 MRTK IMixedRealityPointer 인터페이스를 구현 하는 경우 사용자 고유의 포인터를 사용 하 여 활성 장면 내에서 포인터를 시각화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="63f0b-243">가리키기 익스텐트: 응시를 포함 하 여 모든 포인터에 대 한 전역 포인팅 익스텐트를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="63f0b-244">Raycast 계층 마스크 가리키기: raycast 계층 포인터를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="63f0b-245">디버그 그리기 포인팅 광선: raycasting에 사용 되는 광선을 시각화 하는 디버그 도우미입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="63f0b-246">디버그 그리기 광선 색: 시각화에 사용할 색 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="63f0b-247">응시 cursor prefab: 장면에 대해 전역 응시 커서를 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="63f0b-248">필요한 경우에는 응시 공급자로 신속 하 게 이동 하 여 응시의 특정 값을 재정의할 수 있는 추가 도우미 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="63f0b-249">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-249">Gestures configuration</span></span>

<span data-ttu-id="63f0b-250">제스처는 다양 한 Sdk (예: HoloLens)에서 제공 하는 다양 한 "제스처" 입력 메서드에 입력 작업을 할당 하는 데 사용할 수 있는 시스템 관련 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="63f0b-251">현재 제스처 구현은 HoloLens 전용 이며 나중에 도구 키트에 추가 될 때 다른 시스템에 대해 향상 됩니다 (아직 날짜 없음).</span><span class="sxs-lookup"><span data-stu-id="63f0b-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="63f0b-252">음성 명령</span><span class="sxs-lookup"><span data-stu-id="63f0b-252">Speech commands</span></span>

<span data-ttu-id="63f0b-253">제스처와 마찬가지로 일부 런타임 플랫폼은 Unity 프로젝트에서 받을 수 있는 명령을 생성 하는 기능과 함께 지능형 "음성 텍스트" 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="63f0b-254">이 구성 프로필을 사용 하 여 다음을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="63f0b-255">일반 설정-자동 시작 또는 수동 시작으로 설정 된 "시작 동작"은 입력 시스템 시작 시 KeywordRecognizer를 초기화할 지 여부를 결정 하거나, 프로젝트에서 KeywordRecognizer를 초기화할 시기를 결정 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="63f0b-256">"인식 신뢰 수준"은 Unity의 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) 를 초기화 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="63f0b-257">음성 명령-"단어"를 등록 하 고에서 프로젝트에 수신 될 수 있는 입력 작업으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="63f0b-258">필요한 경우 키보드 작업에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63f0b-259">시스템은 현재 Windows 10 플랫폼 (예: HoloLens 및 Windows 10 desktop)에서 실행 되는 경우에만 음성을 지원 하 고 나중에 MRTK에 추가 될 때 다른 시스템에 대해 향상 됩니다 (아직 날짜 없음).</span><span class="sxs-lookup"><span data-stu-id="63f0b-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="63f0b-260">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="63f0b-260">Controller mapping configuration</span></span>

<span data-ttu-id="63f0b-261">Mixed Reality Toolkit의 핵심 구성 화면 중 하나는 프로젝트에서 사용할 수 있는 다양 한 유형의 컨트롤러를 구성 하 고 매핑할 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="63f0b-262">아래 구성 화면에서는 도구 키트에서 현재 인식 되는 컨트롤러를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="63f0b-263">MRTK는 다음 컨트롤러/시스템에 대 한 기본 구성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="63f0b-264">마우스 (3D 공간 마우스 지원 포함)</span><span class="sxs-lookup"><span data-stu-id="63f0b-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="63f0b-265">터치 스크린</span><span class="sxs-lookup"><span data-stu-id="63f0b-265">Touch Screen</span></span>
- <span data-ttu-id="63f0b-266">Xbox 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="63f0b-266">Xbox controllers</span></span>
- <span data-ttu-id="63f0b-267">Windows Mixed Reality 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="63f0b-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="63f0b-268">HoloLens 제스처</span><span class="sxs-lookup"><span data-stu-id="63f0b-268">HoloLens Gestures</span></span>
- <span data-ttu-id="63f0b-269">HTC Vive 지팡이 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="63f0b-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="63f0b-270">Octouch 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="63f0b-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="63f0b-271">원격 컨트롤러 (oculus)</span><span class="sxs-lookup"><span data-stu-id="63f0b-271">Oculus Remote controller</span></span>
- <span data-ttu-id="63f0b-272">일반 OpenVR 장치 (고급 사용자만 해당)</span><span class="sxs-lookup"><span data-stu-id="63f0b-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="63f0b-273">미리 빌드된 컨트롤러 시스템 중 하나에 대 한 이미지를 클릭 하면 해당 하는 모든 입력에 대해 단일 입력 작업을 구성할 수 있습니다. 예를 들어 아래 Oculus Touch controller 구성 화면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="63f0b-274">위에서 식별 되지 않은 다른 OpenVR 또는 Unity 입력 컨트롤러를 구성 하는 고급 화면도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="63f0b-275">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="63f0b-275">Controller visualization settings</span></span>

<span data-ttu-id="63f0b-276">컨트롤러 매핑 외에도, 컨트롤러가 장면 내에서 제공되는 방식을 사용자 지정하기 위해 별도의 구성 프로필이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="63f0b-277">"전역"(특정 손으로 컨트롤러의 모든 인스턴스) 또는 개별 컨트롤러 유형/손에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="63f0b-278">MRTK는 Windows Mixed Reality 및 OpenVR에 대한 네이티브 SDK 컨트롤러 모델도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="63f0b-279">이는 장면에 GameObjects로 로드되고 플랫폼의 컨트롤러 추적을 사용하여 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="63f0b-280">장면의 컨트롤러 표현이 실제 컨트롤러 위치에서 오프셋되어야 하는 경우 컨트롤러 모델의 프리팹에 대해 해당 오프셋을 설정하기만 하면 됩니다(예: 오프셋 위치로 컨트롤러 프리팹의 변환 위치 설정).</span><span class="sxs-lookup"><span data-stu-id="63f0b-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="63f0b-281">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="63f0b-281">Editor utilities</span></span>

<span data-ttu-id="63f0b-282">다음 유틸리티는 편집기에서만 작동하며 개발 생산성을 향상시키는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 편집기 구성 유틸리티](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="63f0b-284">서비스 검사자</span><span class="sxs-lookup"><span data-stu-id="63f0b-284">Service inspectors</span></span>

<span data-ttu-id="63f0b-285">서비스 검사기는 활성 서비스를 나타내는 장면 내 개체를 생성하는 편집기 전용 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="63f0b-286">이러한 개체를 선택하면 설명서 링크, 편집기 시각화 제어 및 서비스 상태에 대한 인사이트를 제공하는 검사기가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="63f0b-287">구성 프로필의 *편집기 설정에서* *서비스 검사기 사용을* 확인하여 서비스 검사자를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="63f0b-288">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="63f0b-288">Depth buffer renderer</span></span>

<span data-ttu-id="63f0b-289">일부 혼합 현실 플랫폼과 깊이 버퍼를 공유하면 [홀로그램 안정화가](../performance/hologram-stabilization.md)향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="63f0b-290">예를 들어 Windows Mixed Reality 플랫폼은 프레임을 렌더링하는 데 걸리는 시간 동안 미묘한 머리 이동을 고려하도록 픽셀당 렌더링된 장면을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="63f0b-291">그러나 이러한 기술을 사용하려면 정확한 데이터가 있는 깊이 버퍼가 필요하므로 기하 도형이 사용자로부터 얼마나 멀리 떨어져 있는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="63f0b-292">장면에서 필요한 모든 데이터를 깊이 버퍼에 렌더링하도록 하기 위해 개발자는 구성 프로필의 *편집기 설정에서* *렌더링 깊이 버퍼* 기능을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="63f0b-293">그러면 현재 깊이 버퍼가 사용 되 고 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , 기본 카메라에 사후 처리 효과를 적용 하 여 장면 보기에 색으로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="63f0b-294">![렌더링 깊이 버퍼 유틸리티 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>장면의 파란색 실린더에는 깊이 데이터가 기록 되지 않도록 zwrite off가 포함 된 재료가 있습니다</sup> .</span><span class="sxs-lookup"><span data-stu-id="63f0b-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="63f0b-295">런타임에 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="63f0b-295">Changing profiles at runtime</span></span>

<span data-ttu-id="63f0b-296">런타임에 프로필을 업데이트할 수 있으며, 일반적으로 다음과 같은 두 가지 시나리오와 시간이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="63f0b-297">**이전 mrtk 초기화 프로필 스위치**: 시작 시 mrtk가 초기화 되 고 프로필이 활성 상태가 되기 전에 장치 기능에 따라 다른 기능을 사용 하거나 사용 하지 않도록 설정 하는 사용 하지 않는 프로필을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="63f0b-298">예를 들어 환경이 공간 매핑 하드웨어가 없는 VR에서 실행 되는 경우 공간 매핑 구성 요소를 사용 하도록 설정 하는 것이 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="63f0b-299">**활성 프로필 스위치**: 시작 후 MRTK가 초기화 되 고 프로필이 활성 상태가 된 후 현재 사용 중인 프로필을 교환 하 여 특정 기능의 동작 방식을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="63f0b-300">예를 들어 응용 프로그램에 특정 하위 환경이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="63f0b-301">이전 MRTK 초기화 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="63f0b-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="63f0b-302">이는 MRTK 초기화 전에 실행 되는 MonoBehaviour (예:)를 연결 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="63f0b-303">스크립트 (예: 호출)는 스크립트 `SetProfileBeforeInitialization` `MixedRealityToolkit` [실행 순서 설정을](https://docs.unity3d.com/Manual/class-MonoManager.html)설정 하 여 수행할 수 있는 스크립트 보다 먼저 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="63f0b-304">"ProfileToUse" 대신 특정 플랫폼에 적용 되는 임의의 프로필 집합을 포함할 수 있습니다 (예: HoloLens 1의 경우 하나, VR의 경우 하나, HoloLens 2의 경우 하나).</span><span class="sxs-lookup"><span data-stu-id="63f0b-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="63f0b-305">로드할 프로필을 파악 하기 위해 다양 한 표시기 (예: https://docs.unity3d.com/ScriptReference/SystemInfo.html 또는 카메라가 불투명/투명 한지 여부)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="63f0b-306">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="63f0b-306">Active profile switch</span></span>

<span data-ttu-id="63f0b-307">이를 위해서는 `MixedRealityToolkit.Instance.ActiveProfile` 활성 프로필을 대체 하는 새 프로필로 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="63f0b-308">런타임 중에 를 설정하는 경우 `ActiveProfile` 현재 실행 중인 서비스의 소멸은 모든 서비스의 마지막 LateUpdate() 이후에 발생하며, 새 프로필과 연결된 서비스의 인스턴스화 및 초기화는 모든 서비스의 첫 번째 Update() 전에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="63f0b-309">이 프로세스 중에 눈에 띄는 애플리케이션 망설임이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="63f0b-310">또한 스크립트보다 우선 순위가 높은 `MixedRealityToolkit` 스크립트는 새 프로필을 제대로 설정하기 전에 업데이트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="63f0b-311">스크립트 우선 순위에 대한 자세한 내용은 [스크립트 실행 순서 설정을](https://docs.unity3d.com/Manual/class-MonoManager.html) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63f0b-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="63f0b-312">프로필 전환 프로세스에서 기존 UI 카메라는 변경되지 않은 상태로 유지되어 캔버스가 필요한 Unity UI 구성 요소가 스위치 후에도 계속 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="63f0b-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="63f0b-313">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63f0b-313">See also</span></span>

- [<span data-ttu-id="63f0b-314">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="63f0b-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)