---
title: GettingStartedWithMRTKAndXRSDK
description: XRSDK를 사용 하는 MRTK의 방문 페이지
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, XRSDK,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300422"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="4f8d5-104">MRTK 및 XR SDK 시작</span><span class="sxs-lookup"><span data-stu-id="4f8d5-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="4f8d5-105">XR SDK는 unity [2019.3 이상에서 unity의 새로운 XR 파이프라인](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="4f8d5-106">Unity 2019에서는 기존 XR 파이프라인에 대 한 대안을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="4f8d5-107">Unity 2020에서는 Unity의 유일한 XR 파이프라인이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f8d5-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4f8d5-108">Prerequisites</span></span>

<span data-ttu-id="4f8d5-109">Mixed Reality Toolkit를 시작 하려면 [제공 된 단계](../install-the-tools.md#importing-the-mixed-reality-toolkit) 에 따라 MRTK를 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="4f8d5-110">XR SDK 파이프라인에 대 한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="4f8d5-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="4f8d5-111">XR SDK 파이프라인은 현재 Windows Mixed Reality, Oculus 및 OpenXR의 3 개 플랫폼을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="4f8d5-112">아래 섹션에서는 각 플랫폼에 대해 XR SDK를 구성 하는 데 필요한 단계에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="4f8d5-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4f8d5-113">Windows Mixed Reality</span></span>

<span data-ttu-id="4f8d5-114">**Unity의 패키지 관리자** 로 이동 하 여 XR SDK에서 Windows Mixed Reality에 대 한 지원을 추가 하는 Windows XR 플러그 인 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="4f8d5-115">이렇게 하면 몇 가지 종속성 패키지도 풀 다운 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="4f8d5-116">다음 모두가 성공적으로 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="4f8d5-117">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="4f8d5-117">XR Plugin Management</span></span>
   * <span data-ttu-id="4f8d5-118">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="4f8d5-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="4f8d5-119">XR 레거시 입력 도우미</span><span class="sxs-lookup"><span data-stu-id="4f8d5-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="4f8d5-120">**편집 > 프로젝트 설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="4f8d5-121">프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="4f8d5-122">유니버설 Windows 플랫폼 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="4f8d5-123">시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="4f8d5-124">(**_편집기 내 HoloLens 원격 기능에 필요 하며, 그렇지 않은 경우 선택 사항_**) 독립 실행형 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="4f8d5-125">또한 시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![독립 실행형 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-02.png)

7. <span data-ttu-id="4f8d5-127">(**_선택 사항_**) XR 플러그 인 관리에서 Windows Mixed Reality 탭을 클릭 하 고 사용자 지정 설정 프로필을 만들어 기본값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="4f8d5-128">설정 목록이 이미 있는 경우 프로필을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Windows 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="4f8d5-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="4f8d5-130">Oculus</span></span>

1. <span data-ttu-id="4f8d5-131">[XR SDK 파이프라인 가이드를 사용 하 여 MRTK에서 Oculus 퀘스트를 구성 하는 방법](../features/cross-platform/oculus-quest-mrtk.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../features/cross-platform/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="4f8d5-132">이 가이드에서는 XR SDK 파이프라인을 사용 하도록 Unity와 MRTK를 모두 구성 하는 데 필요한 단계를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="4f8d5-133">OpenXR (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f8d5-134">Unity의 OpenXR는 Unity 2020.2 이상 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="4f8d5-135">현재는 x64 및 ARM64 빌드에서만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="4f8d5-136">XR 플러그 인 관리 및 최적화를 구성 하 여 프로젝트에 OpenXR 플러그 인을 설치 하는 단계를 포함 하 여 [OpenXR에 대 한 혼합 현실 플러그 인을 사용 하](/windows/mixed-reality/develop/unity/openxr-getting-started) 는 방법 가이드를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="4f8d5-137">다음이 성공적으로 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="4f8d5-138">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="4f8d5-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="4f8d5-139">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="4f8d5-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="4f8d5-140">혼합 현실 OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="4f8d5-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="4f8d5-141">편집 > 프로젝트 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="4f8d5-142">프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="4f8d5-143">시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="4f8d5-144">(**_선택 사항_**) HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 Microsoft HoloLens 기능 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![플러그 인 관리 열기 XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="4f8d5-146">UPM에서 MRTK를 사용 하는 기존 프로젝트가 있는 경우 MixedRealityToolkit 폴더에 있는 **link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="4f8d5-147">MRTK 및 OpenXR의 초기 릴리스에서는 HoloLens 2의 부분 및 Windows Mixed Reality 동작 컨트롤러만 기본적으로 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="4f8d5-148">추가 하드웨어에 대 한 지원은 향후 릴리스에 추가 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="4f8d5-149">XR SDK 파이프라인에 대 한 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="4f8d5-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="4f8d5-150">OpenXR를 사용 하는 경우 "DefaultOpenXRConfigurationProfile"을 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="4f8d5-151">Windows Mixed Reality 또는 Oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용 하는 경우 "DefaultXRSDKConfigurationProfile"를 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="4f8d5-152">이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="4f8d5-153">XR SDK를 사용한 프로필 및 샘플 지원에 대 한 자세한 내용은 [프로필 문서를](../features/profiles/profiles.md#xr-sdk) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="4f8d5-154">기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="4f8d5-155">카메라</span><span class="sxs-lookup"><span data-stu-id="4f8d5-155">Camera</span></span>

<span data-ttu-id="4f8d5-156">보낸 사람 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![레거시 카메라 설정](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="4f8d5-158">을</span><span class="sxs-lookup"><span data-stu-id="4f8d5-158">to</span></span>

| <span data-ttu-id="4f8d5-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4f8d5-159">OpenXR</span></span> | <span data-ttu-id="4f8d5-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4f8d5-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="4f8d5-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**및**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="4f8d5-163">입력</span><span class="sxs-lookup"><span data-stu-id="4f8d5-163">Input</span></span>

<span data-ttu-id="4f8d5-164">보낸 사람 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![레거시 입력 설정](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="4f8d5-166">을</span><span class="sxs-lookup"><span data-stu-id="4f8d5-166">to</span></span>

| <span data-ttu-id="4f8d5-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4f8d5-167">OpenXR</span></span> | <span data-ttu-id="4f8d5-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4f8d5-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="4f8d5-169">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="4f8d5-169">__OpenXR__:</span></span>

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="4f8d5-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="4f8d5-171">__Windows Mixed Reality__:</span></span>

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="4f8d5-173">경계</span><span class="sxs-lookup"><span data-stu-id="4f8d5-173">Boundary</span></span>

<span data-ttu-id="4f8d5-174">보낸 사람 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![레거시 경계 설정](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="4f8d5-176">을</span><span class="sxs-lookup"><span data-stu-id="4f8d5-176">to</span></span>

| <span data-ttu-id="4f8d5-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4f8d5-177">OpenXR</span></span> | <span data-ttu-id="4f8d5-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4f8d5-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="4f8d5-180">공간 인식</span><span class="sxs-lookup"><span data-stu-id="4f8d5-180">Spatial awareness</span></span>

<span data-ttu-id="4f8d5-181">보낸 사람 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="4f8d5-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![레거시 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="4f8d5-183">을</span><span class="sxs-lookup"><span data-stu-id="4f8d5-183">to</span></span>

| <span data-ttu-id="4f8d5-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4f8d5-184">OpenXR</span></span> | <span data-ttu-id="4f8d5-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4f8d5-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="4f8d5-186">진행 중</span><span class="sxs-lookup"><span data-stu-id="4f8d5-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="4f8d5-188">컨트롤러 매핑</span><span class="sxs-lookup"><span data-stu-id="4f8d5-188">Controller mappings</span></span>

<span data-ttu-id="4f8d5-189">사용자 지정 컨트롤러 매핑 프로필을 사용 하는 경우 이러한 프로필 중 하나를 열고 혼합 현실 도구 키트 > 유틸리티-> 업데이트-> 컨트롤러 매핑 프로필 메뉴 항목을 실행 하 여 새 XR SDK 컨트롤러 유형이 정의 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8d5-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f8d5-190">참조</span><span class="sxs-lookup"><span data-stu-id="4f8d5-190">See also</span></span>

* [<span data-ttu-id="4f8d5-191">Unity에서 AR 개발 시작 하기</span><span class="sxs-lookup"><span data-stu-id="4f8d5-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="4f8d5-192">Unity에서 VR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="4f8d5-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)