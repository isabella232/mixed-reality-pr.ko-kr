---
title: 혼합 현실 구성 가이드
description: Unity에 MRTK를 구성 하는 방법에 대 한 설명서입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK,
ms.openlocfilehash: b714e01a0969b88a4ca7a3a5047bc5d61516e3f3
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345146"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="c8275-104">Mixed Reality Toolkit 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="c8275-104">Mixed Reality Toolkit profile configuration guide</span></span>

![MRTK 로고](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="c8275-106">혼합 현실 도구 키트는 가능한 한 도구 키트를 관리 하는 데 필요한 많은 구성 (진정한 런타임 "사물" 제외)을 중앙 집중식으로 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="c8275-107">이 가이드는 도구 키트에 대해 현재 사용할 수 있는 각 구성 프로필 화면에 대 한 간단한 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="c8275-108">기본 Mixed Reality Toolkit 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="c8275-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="c8275-109">장면의 *MixedRealityToolkit* GameObject에 연결 된 기본 구성 프로필은 프로젝트의 도구 키트에 대 한 기본 진입점을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="c8275-110">혼합 현실 도구 키트는 기본 구성 화면을 "잠금" 하 여 프로젝트에 대 한 공통 시작 지점이 항상 있는지 확인 하 고 프로젝트가 진화 함에 따라 사용자 고유의 설정을 정의 하기 시작 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="c8275-111">MRTK 구성은 재생 모드에서 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-111">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 구성 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="c8275-113">혼합 현실 도구 키트의 모든 "기본" 프로필은 asset/MRTK/SDK/Profiles 폴더의 SDK 프로젝트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8275-114">DefaultHoloLens2ConfigurationProfile는 HoloLens 2에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="c8275-115">자세한 내용은 [프로필](../features/profiles/profiles.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8275-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="c8275-116">기본 Mixed Reality Toolkit 구성 프로필을 열면 검사기에 다음 화면이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="c8275-117">장면에서 MixedRealityToolkit 없이 MixedRealityToolkitConfigurationProfile 자산을 선택 하는 경우 MRTK에서 자동으로 장면을 설정 하도록 할 것인지 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="c8275-118">이 옵션은 선택 사항 이지만 모든 구성 화면에 액세스 하려면 장면에 활성 MixedRealityToolkit 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="c8275-119">프로젝트에 대 한 현재 활성 런타임 구성을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="c8275-120">여기에서 다음을 포함 하 여 MRTK에 대 한 모든 구성 프로필을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="c8275-121">Mixed Reality Toolkit 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="c8275-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="c8275-122">기본 Mixed Reality Toolkit 구성 프로필</span><span class="sxs-lookup"><span data-stu-id="c8275-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="c8275-123">환경 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="c8275-124">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="c8275-125">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="c8275-126">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="c8275-127">Teleportation 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="c8275-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="c8275-128">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="c8275-129">진단 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="c8275-130">시스템 설정 장면</span><span class="sxs-lookup"><span data-stu-id="c8275-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="c8275-131">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="c8275-132">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="c8275-133">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="c8275-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="c8275-134">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="c8275-135">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="c8275-136">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c8275-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="c8275-137">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="c8275-138">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="c8275-139">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="c8275-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="c8275-140">서비스 검사기</span><span class="sxs-lookup"><span data-stu-id="c8275-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="c8275-141">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="c8275-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="c8275-142">런타임에 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="c8275-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="c8275-143">이전 MRTK 초기화 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="c8275-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="c8275-144">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="c8275-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="c8275-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8275-145">See also</span></span>](#see-also)

<span data-ttu-id="c8275-146">이러한 구성 프로필은 아래 관련 섹션에서 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="c8275-147">환경 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-147">Experience settings</span></span>

<span data-ttu-id="c8275-148">기본 Mixed Reality 도구 키트 구성 페이지에 있는이 설정은 프로젝트에 대 한 [혼합 현실 환경 규모](/windows/mixed-reality/coordinate-systems-in-unity) 의 기본 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="c8275-149">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-149">Camera settings</span></span>

<span data-ttu-id="c8275-150">카메라 설정은 혼합 현실 프로젝트에 대해 카메라를 설정 하는 방법을 정의 하 여 일반 클리핑, 품질 및 투명도 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="c8275-151">입력 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-151">Input system settings</span></span>

<span data-ttu-id="c8275-152">Mixed Reality 프로젝트는 기본적으로 선택 되는 프로젝트에 대 한 모든 입력 이벤트를 라우팅하기 위한 강력 하 고 잘 학습 된 입력 시스템을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="c8275-153">MRTK에서 제공 하는 입력 시스템 뒤에는 여러 다른 시스템이 있으며,이를 통해 다중 플랫폼/혼합 현실 프레임 워크의 복잡성을 추상화 하는 데 필요한 복잡 한 비-weavings를 구동 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="c8275-154">각 개별 프로필은 아래에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="c8275-155">포커스 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-155">Focus Settings</span></span>
- [<span data-ttu-id="c8275-156">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="c8275-157">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="c8275-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="c8275-158">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="c8275-159">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="c8275-160">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c8275-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="c8275-161">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="c8275-162">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="c8275-163">경계 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-163">Boundary visualization settings</span></span>

<span data-ttu-id="c8275-164">경계 시스템은 기본 플랫폼 경계/보호자 시스템에서 보고 하는 인식 된 경계를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="c8275-165">경계 시각화 도우미 구성은 사용자의 위치를 기준으로 장면 내에 기록 된 경계를 자동으로 표시 하는 기능을 제공 합니다. 경계는 사용자의 장면 내 teleports 위치에 따라 반응 하거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="c8275-166">Teleportation 시스템 선택</span><span class="sxs-lookup"><span data-stu-id="c8275-166">Teleportation system selection</span></span>

<span data-ttu-id="c8275-167">Mixed Reality 프로젝트는 기본적으로 선택 되는 프로젝트에서 Teleportation 이벤트를 관리 하기 위한 완전 한 기능을 갖춘 Teleportation 시스템을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="c8275-168">공간 인식 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-168">Spatial awareness settings</span></span>

<span data-ttu-id="c8275-169">혼합 현실 프로젝트는 기본적으로 선택 되는 프로젝트에서 공간 검색 시스템을 사용 하기 위해 다시 작성 된 공간 인식 시스템을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="c8275-170">혼합 현실 도구 키트 공간 인식 구성을 사용 하면 응용 프로그램이 시작 될 때 자동으로 실행 되는 경우 자동으로 실행 되는 방식으로 또는 보기의 필드에 대 한 익스텐트를 설정 하는 방식으로 시스템 시작 방식을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="c8275-171">또한 메시 및 surface 설정을 구성 하 여 프로젝트에서 사용자의 환경을 이해 하는 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="c8275-172">검색 된 환경을 제공할 수 있는 장치에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="c8275-173">진단 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-173">Diagnostics settings</span></span>

<span data-ttu-id="c8275-174">MRTK의 선택적 이지만 매우 유용한 기능은 플러그 인 진단 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="c8275-175">진단 프로필은 화면에서 디스플레이 패널을 사용/사용 하지 않도록 설정 하는 편리한 켜기/끄기 스위치를 포함 하 여 프로젝트가 실행 되는 동안 모니터링 하는 몇 가지 간단한 시스템을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="c8275-176">시스템 설정 장면</span><span class="sxs-lookup"><span data-stu-id="c8275-176">Scene system settings</span></span>

<span data-ttu-id="c8275-177">MRTK는 복잡 한 추가 장면 로드/언로드를 관리 하는 데 도움이 되는 선택적 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="c8275-178">장면 시스템이 프로젝트에 적합 한지 여부를 결정 하려면 [장면 시스템 시작 가이드를 참조 하세요.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="c8275-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="c8275-179">추가 서비스 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-179">Additional services settings</span></span>

<span data-ttu-id="c8275-180">Mixed Reality Toolkit의 고급 영역 중 하나는 프레임 워크에 "서비스"를 등록 하는 데 사용할 수 있는 [서비스 로케이터 패턴](https://en.wikipedia.org/wiki/Service_locator_pattern) 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="c8275-181">이를 통해 프레임 워크를 새로운 기능/시스템으로 쉽게 확장할 수 있습니다. 또한 프로젝트에서 이러한 기능을 활용 하 여 고유한 런타임 구성 요소를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="c8275-182">등록 된 서비스에서는 MonoBehaviour 또는 clunky singleton 패턴을 구현 하는 오버 헤드와 비용 없이 모든 Unity 이벤트의 모든 이점을 누릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="c8275-183">이를 통해 포그라운드 및 백그라운드 프로세스를 실행 하는 데 필요한 장면 오버 헤드가 없는 순수 c # 구성 요소 (예: 시스템, 런타임 게임 논리 또는 거의 모든 항목)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="c8275-184">입력 작업 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-184">Input actions settings</span></span>

<span data-ttu-id="c8275-185">입력 작업은 런타임 프로젝트의 모든 물리적 상호 작용 및 입력을 추상화 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="c8275-186">모든 실제 입력 (컨트롤러/직접/마우스/등)은 런타임 프로젝트에서 사용 하기 위한 논리적 입력 동작으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="c8275-187">이렇게 하면 입력이 제공 되는 위치와 관계 없이 프로젝트에서 이러한 작업을 내부적으로 "할 일" 또는 "상호 작용"으로 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="c8275-188">새 입력 작업을 만들려면 "새 작업 추가" 단추를 클릭 하 고 표시 되는 내용에 대 한 텍스트 이름을 입력 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="c8275-189">그런 다음 동작을 전달할 축 (데이터 유형)만 선택 해야 합니다. 또는 실제 컨트롤러의 경우에는 다음과 같이 연결 될 수 있는 물리적 입력 유형을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="c8275-190">축 제약 조건</span><span class="sxs-lookup"><span data-stu-id="c8275-190">Axis Constraint</span></span> | <span data-ttu-id="c8275-191">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c8275-191">Data Type</span></span> | <span data-ttu-id="c8275-192">설명</span><span class="sxs-lookup"><span data-stu-id="c8275-192">Description</span></span> | <span data-ttu-id="c8275-193">예제 사용</span><span class="sxs-lookup"><span data-stu-id="c8275-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="c8275-194">없음</span><span class="sxs-lookup"><span data-stu-id="c8275-194">None</span></span> | <span data-ttu-id="c8275-195">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="c8275-195">No data</span></span> | <span data-ttu-id="c8275-196">빈 동작 또는 이벤트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-196">Used for an empty action or event</span></span> | <span data-ttu-id="c8275-197">이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="c8275-197">Event Trigger</span></span> |
| <span data-ttu-id="c8275-198">Raw (예약 됨)</span><span class="sxs-lookup"><span data-stu-id="c8275-198">Raw (reserved)</span></span> | <span data-ttu-id="c8275-199">object</span><span class="sxs-lookup"><span data-stu-id="c8275-199">object</span></span> | <span data-ttu-id="c8275-200">나중에 사용하도록 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-200">Reserved for future use</span></span> | <span data-ttu-id="c8275-201">N/A</span><span class="sxs-lookup"><span data-stu-id="c8275-201">N/A</span></span> |
| <span data-ttu-id="c8275-202">디지털</span><span class="sxs-lookup"><span data-stu-id="c8275-202">Digital</span></span> | <span data-ttu-id="c8275-203">bool</span><span class="sxs-lookup"><span data-stu-id="c8275-203">bool</span></span> | <span data-ttu-id="c8275-204">형식 데이터의 부울 켜기 또는 끄기</span><span class="sxs-lookup"><span data-stu-id="c8275-204">A boolean on or off type data</span></span> | <span data-ttu-id="c8275-205">컨트롤러 단추</span><span class="sxs-lookup"><span data-stu-id="c8275-205">A controller button</span></span> |
| <span data-ttu-id="c8275-206">단일 축</span><span class="sxs-lookup"><span data-stu-id="c8275-206">Single Axis</span></span> | <span data-ttu-id="c8275-207">float</span><span class="sxs-lookup"><span data-stu-id="c8275-207">float</span></span> | <span data-ttu-id="c8275-208">단정밀도 데이터 값</span><span class="sxs-lookup"><span data-stu-id="c8275-208">A single precision data value</span></span> | <span data-ttu-id="c8275-209">범위가 있는 입력(예: 트리거)</span><span class="sxs-lookup"><span data-stu-id="c8275-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="c8275-210">이중 축</span><span class="sxs-lookup"><span data-stu-id="c8275-210">Dual Axis</span></span> | <span data-ttu-id="c8275-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="c8275-211">Vector2</span></span> | <span data-ttu-id="c8275-212">여러 축에 대한 이중 float 형식 날짜</span><span class="sxs-lookup"><span data-stu-id="c8275-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="c8275-213">Dpad 또는 Thumbstick</span><span class="sxs-lookup"><span data-stu-id="c8275-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="c8275-214">Dof 위치 3개</span><span class="sxs-lookup"><span data-stu-id="c8275-214">Three Dof Position</span></span> | <span data-ttu-id="c8275-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="c8275-215">Vector3</span></span> | <span data-ttu-id="c8275-216">float 축이 3개인 의 위치 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="c8275-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="c8275-217">3D 위치 스타일만 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-217">3D position style only controller</span></span> |
| <span data-ttu-id="c8275-218">Dof 회전 3개</span><span class="sxs-lookup"><span data-stu-id="c8275-218">Three Dof Rotation</span></span> | <span data-ttu-id="c8275-219">쿼터니언</span><span class="sxs-lookup"><span data-stu-id="c8275-219">Quaternion</span></span> | <span data-ttu-id="c8275-220">float 축이 4개인 회전 전용 입력</span><span class="sxs-lookup"><span data-stu-id="c8275-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="c8275-221">3도 스타일 컨트롤러(예: Oculus Go 컨트롤러)</span><span class="sxs-lookup"><span data-stu-id="c8275-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="c8275-222">Six Dof</span><span class="sxs-lookup"><span data-stu-id="c8275-222">Six Dof</span></span> | <span data-ttu-id="c8275-223">Mixed Reality 자세(Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="c8275-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="c8275-224">Vector3 및 Quaternion 구성 요소가 모두 있는 위치 및 회전 스타일 입력</span><span class="sxs-lookup"><span data-stu-id="c8275-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="c8275-225">모션 컨트롤러 또는 포인터</span><span class="sxs-lookup"><span data-stu-id="c8275-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="c8275-226">입력 작업을 활용하는 이벤트는 실제 컨트롤러로 제한되지 않으며, 프로젝트 내에서 계속 활용하여 런타임 효과가 새 작업을 생성하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="c8275-227">입력 작업은 런타임에 편집할 수 없는 몇 가지 구성 요소 중 하나이며 디자인 타임 구성에만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="c8275-228">각 작업에 대해 생성된 ID에 대한 프레임워크(및 프로젝트) 종속성으로 인해 프로젝트가 실행되는 동안에는 이 프로필을 교환해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="c8275-229">입력 작업 규칙</span><span class="sxs-lookup"><span data-stu-id="c8275-229">Input actions rules</span></span>

<span data-ttu-id="c8275-230">입력 작업 규칙은 의 한 입력 동작에 대해 발생된 이벤트를 해당 데이터 값에 따라 다른 작업으로 자동으로 변환하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="c8275-231">프레임워크 내에서 원활하게 관리되며 성능 비용이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="c8275-232">예를 들어 의 DPad에서 단일 이중 축 입력 이벤트를 해당하는 4개 "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" 작업(아래 이미지에 표시)으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="c8275-233">사용자 고유의 코드에서 이 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-233">This could also be done in your own code.</span></span> <span data-ttu-id="c8275-234">그러나 이것이 매우 일반적인 패턴인 것을 볼 때 프레임워크는 이 작업을 "기본 제공"하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="c8275-235">입력 작업 사용 가능한 입력 축에 대해 규칙을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="c8275-236">그러나 한 축 형식의 입력 동작을 동일한 축 형식의 다른 입력 동작으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="c8275-237">이중 축 동작을 다른 이중 축 작업에 매핑할 수 있지만 디지털 또는 없음 작업에는 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![입력 작업 규칙 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="c8275-239">포인터 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-239">Pointer configuration</span></span>

<span data-ttu-id="c8275-240">포인터는 입력 디바이스에서 장면의 대화형 활동을 구동하는 데 사용되며, 장면의 모든 개체(충돌체가 연결되어 있거나 UI 구성 요소)를 사용하여 방향과 적중 테스트를 모두 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="c8275-241">포인터는 기본적으로 컨트롤러, 헤드셋(응시/포커스) 및 마우스/터치 입력에 대해 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="c8275-242">Mixed Reality Toolkit에서 제공하는 여러 줄 구성 요소 중 하나를 사용하거나 MRTK IMixedRealityPointer 인터페이스를 구현하는 경우 직접 포인터를 사용하여 활성 장면 내에서 포인터를 시각화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="c8275-243">포인팅 익스텐트: 응시를 비롯한 모든 포인터에 대한 전역 포인팅 익스텐트 결정</span><span class="sxs-lookup"><span data-stu-id="c8275-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="c8275-244">포인팅 광선 캐스트 계층 마스크: 광선 캐스팅할 레이어 포인터를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="c8275-245">디버그 그리기 포인팅 광선: 광선 캐스팅에 사용되는 광선을 시각화하기 위한 디버그 도우미입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="c8275-246">그리기 포인팅 광선 색 디버그: 시각화에 사용할 색 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="c8275-247">응시 커서 프리팹: 모든 장면에 대한 전역 응시 커서를 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="c8275-248">필요한 경우 응시에 대한 특정 값을 재정의하기 위해 응시 공급자로 빠르게 이동할 수 있는 추가 도우미 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="c8275-249">제스처 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-249">Gestures configuration</span></span>

<span data-ttu-id="c8275-250">제스처는 다양한 SDK(예: HoloLens)에서 제공하는 다양한 "제스처" 입력 메서드에 입력 작업을 할당할 수 있도록 하는 시스템별 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="c8275-251">현재 제스처 구현은 HoloLens 전용이며 나중에 도구 키트에 추가될 때(아직 날짜 없음) 다른 시스템에 대해 향상될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="c8275-252">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c8275-252">Speech commands</span></span>

<span data-ttu-id="c8275-253">제스처와 마찬가지로 일부 런타임 플랫폼은 Unity 프로젝트에서 수신할 수 있는 명령을 생성하는 기능과 함께 지능형 "Speech to Text" 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="c8275-254">이 구성 프로필을 사용하면 다음을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="c8275-255">일반 설정 - 자동 시작 또는 수동 시작으로 설정된 "시작 동작"은 입력 시스템 시작 시 KeywordRecognizer를 초기화할지 또는 프로젝트에서 KeywordRecognizer를 초기화할 시기를 결정하도록 할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="c8275-256">"인식 신뢰도 수준"은 Unity의 [KeywordRecognizer API를](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) 초기화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="c8275-257">음성 명령 - "단어"를 등록하고 프로젝트에서 받을 수 있는 입력 작업으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="c8275-258">필요한 경우 키보드 작업에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8275-259">시스템은 현재 Windows 10 플랫폼에서 실행하는 경우에만 음성을 지원합니다(예: HoloLens 및 Windows 10 Desktop). 향후 MRTK에 추가될 때(아직 날짜 없음) 다른 시스템에 대해 향상될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="c8275-260">컨트롤러 매핑 구성</span><span class="sxs-lookup"><span data-stu-id="c8275-260">Controller mapping configuration</span></span>

<span data-ttu-id="c8275-261">Mixed Reality 도구 키트의 핵심 구성 화면 중 하나는 프로젝트에서 활용할 수 있는 다양한 유형의 컨트롤러를 구성하고 매핑하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="c8275-262">아래 구성 화면에서는 도구 키트에서 현재 인식되는 컨트롤러를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="c8275-263">MRTK는 다음 컨트롤러/시스템에 대한 기본 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="c8275-264">마우스(3D 공간 마우스 지원 포함)</span><span class="sxs-lookup"><span data-stu-id="c8275-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="c8275-265">터치 스크린</span><span class="sxs-lookup"><span data-stu-id="c8275-265">Touch Screen</span></span>
- <span data-ttu-id="c8275-266">Xbox 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-266">Xbox controllers</span></span>
- <span data-ttu-id="c8275-267">Windows Mixed Reality 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="c8275-268">HoloLens 제스처</span><span class="sxs-lookup"><span data-stu-id="c8275-268">HoloLens Gestures</span></span>
- <span data-ttu-id="c8275-269">HTC Vive wand 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="c8275-270">Oculus Touch 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="c8275-271">Oculus 원격 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c8275-271">Oculus Remote controller</span></span>
- <span data-ttu-id="c8275-272">일반 OpenVR 디바이스(고급 사용자만 해당)</span><span class="sxs-lookup"><span data-stu-id="c8275-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="c8275-273">미리 빌드된 컨트롤러 시스템의 이미지를 클릭하면 모든 해당 입력에 대해 단일 입력 작업을 구성할 수 있습니다. 예를 들어 아래의 Oculus Touch 컨트롤러 구성 화면을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8275-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="c8275-274">위에서 식별되지 않은 다른 OpenVR 또는 Unity 입력 컨트롤러를 구성하기 위한 고급 화면도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="c8275-275">컨트롤러 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="c8275-275">Controller visualization settings</span></span>

<span data-ttu-id="c8275-276">컨트롤러 매핑 외에도, 컨트롤러가 장면 내에서 제공되는 방식을 사용자 지정하기 위해 별도의 구성 프로필이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="c8275-277">"전역"(특정 손으로 컨트롤러의 모든 인스턴스) 또는 개별 컨트롤러 유형/손에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="c8275-278">MRTK는 Windows Mixed Reality 및 OpenVR에 대한 네이티브 SDK 컨트롤러 모델도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="c8275-279">이러한 구성은 장면에 GameObjects로 로드되고 플랫폼의 컨트롤러 추적을 사용하여 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="c8275-280">장면의 컨트롤러 표현이 실제 컨트롤러 위치에서 오프셋되어야 하는 경우 컨트롤러 모델의 프리팹에 대해 해당 오프셋을 설정하기만 하면 됩니다(예: 오프셋 위치로 컨트롤러 프리팹의 변환 위치 설정).</span><span class="sxs-lookup"><span data-stu-id="c8275-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="c8275-281">편집기 유틸리티</span><span class="sxs-lookup"><span data-stu-id="c8275-281">Editor utilities</span></span>

<span data-ttu-id="c8275-282">다음 유틸리티는 편집기에서만 작동하며 개발 생산성을 향상시키는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 편집기 구성 유틸리티](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="c8275-284">서비스 검사기</span><span class="sxs-lookup"><span data-stu-id="c8275-284">Service inspectors</span></span>

<span data-ttu-id="c8275-285">서비스 검사기는 활성 서비스를 나타내는 장면 내 개체를 생성하는 편집기 전용 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="c8275-286">이러한 개체를 선택하면 설명서 링크, 편집기 시각화 제어 및 서비스 상태에 대한 인사이트를 제공하는 검사기가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="c8275-287">구성 프로필의 *편집기 설정에서* *서비스 검사기 사용을* 확인하여 서비스 검사자를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="c8275-288">깊이 버퍼 렌더러</span><span class="sxs-lookup"><span data-stu-id="c8275-288">Depth buffer renderer</span></span>

<span data-ttu-id="c8275-289">일부 혼합 현실 플랫폼과 깊이 버퍼를 공유하면 [홀로그램 안정화가](../performance/hologram-stabilization.md)향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="c8275-290">예를 들어 Windows Mixed Reality 플랫폼은 프레임을 렌더링하는 데 걸리는 시간 동안 미묘한 머리 이동을 고려하도록 픽셀당 렌더링된 장면을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="c8275-291">그러나 이러한 기술을 사용하려면 정확한 데이터가 있는 깊이 버퍼가 필요하므로 기하 도형이 사용자로부터 얼마나 멀리 떨어져 있는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="c8275-292">장면에서 필요한 모든 데이터를 깊이 버퍼에 렌더링하도록 하기 위해 개발자는 구성 프로필의 *편집기 설정에서* *렌더링 깊이 버퍼* 기능을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="c8275-293">그러면 현재 깊이 버퍼가 적용되고 후처리 효과인 를 주 카메라에 적용하여 장면 보기에 색으로 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="c8275-294">![렌더링 깊이 버퍼 유틸리티 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>장면의 파란색 실린더에는 ZWrite가 꺼진 재질이 있으므로 깊이 데이터가 기록되지 않습니다.</sup></span><span class="sxs-lookup"><span data-stu-id="c8275-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="c8275-295">런타임 시 프로필 변경</span><span class="sxs-lookup"><span data-stu-id="c8275-295">Changing profiles at runtime</span></span>

<span data-ttu-id="c8275-296">런타임에 프로필을 업데이트할 수 있으며 일반적으로 다음과 같은 두 가지 시나리오와 시간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="c8275-297">**MRTK 초기화 프로필 전환 전:** 시작 시 MRTK가 초기화되고 프로필이 활성화되기 전에 아직 사용되지 않는 프로필을 대체하여 디바이스 기능에 따라 다른 기능을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="c8275-298">예를 들어 환경이 공간 매핑 하드웨어가 없는 VR에서 실행되는 경우 공간 매핑 구성 요소를 사용하도록 설정하는 것이 타의가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="c8275-299">**활성 프로필 전환:** 시작 후 MRTK가 초기화되고 프로필이 활성화된 후 현재 사용 중인 프로필을 교환하여 특정 기능의 동작 방식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="c8275-300">예를 들어 원거리 포인터를 완전히 제거하려는 애플리케이션의 특정 하위 환경이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="c8275-301">이전 MRTK 초기화 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="c8275-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="c8275-302">이는 MRTK 초기화 전에 실행 되는 MonoBehaviour (예:)를 연결 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="c8275-303">스크립트 (예: 호출)는 스크립트 `SetProfileBeforeInitialization` `MixedRealityToolkit` [실행 순서 설정을](https://docs.unity3d.com/Manual/class-MonoManager.html)설정 하 여 수행할 수 있는 스크립트 보다 먼저 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="c8275-304">"ProfileToUse" 대신 특정 플랫폼에 적용 되는 임의의 프로필 집합을 포함할 수 있습니다 (예: HoloLens 1의 경우 하나, VR의 경우 하나, HoloLens 2의 경우 하나).</span><span class="sxs-lookup"><span data-stu-id="c8275-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="c8275-305">로드할 프로필을 파악 하기 위해 다양 한 표시기 (예: https://docs.unity3d.com/ScriptReference/SystemInfo.html 또는 카메라가 불투명/투명 한지 여부)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="c8275-306">활성 프로필 스위치</span><span class="sxs-lookup"><span data-stu-id="c8275-306">Active profile switch</span></span>

<span data-ttu-id="c8275-307">이를 위해서는 `MixedRealityToolkit.Instance.ActiveProfile` 활성 프로필을 대체 하는 새 프로필로 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="c8275-308">참고 런타임 중에 설정 하는 경우 `ActiveProfile` 현재 실행 중인 서비스의 삭제는 모든 서비스의 마지막 behaviour () 이후에 발생 하며, 새 프로필과 연결 된 서비스의 인스턴스화 및 초기화는 모든 서비스의 첫 번째 업데이트 () 이전에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="c8275-309">이 프로세스 중에는 눈에 띄는 응용 프로그램 hesitation 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="c8275-310">또한 스크립트 보다 우선 순위가 높은 모든 스크립트는 `MixedRealityToolkit` 새 프로필이 제대로 설정 되기 전에 해당 업데이트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="c8275-311">스크립트 우선 순위에 대 한 자세한 내용은 [스크립트 실행 순서 설정](https://docs.unity3d.com/Manual/class-MonoManager.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8275-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="c8275-312">프로필 전환 프로세스에서 기존 UI 카메라는 변경 되지 않은 상태로 유지 되 고, canvas를 필요로 하는 Unity UI 구성 요소가 스위치 후에도 계속 작동 하도록 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8275-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8275-313">참조</span><span class="sxs-lookup"><span data-stu-id="c8275-313">See also</span></span>

- [<span data-ttu-id="c8275-314">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="c8275-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)