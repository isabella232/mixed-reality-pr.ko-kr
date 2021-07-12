---
title: MRTK 및 XR SDK 시작
description: XR SDK를 사용 하는 MRTK의 방문 페이지
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, xrsdk, XR SDK
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603694"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="fdbe3-104">MRTK 및 XR SDK 시작</span><span class="sxs-lookup"><span data-stu-id="fdbe3-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="fdbe3-105">XR SDK는 unity [2019.3 이상에서 unity의 새로운 XR 파이프라인](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)입니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="fdbe3-106">Unity 2019에서는 기존 XR 파이프라인에 대 한 대안을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="fdbe3-107">Unity 2020에서는 Unity의 유일한 XR 파이프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdbe3-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="fdbe3-108">Prerequisites</span></span>

<span data-ttu-id="fdbe3-109">혼합 현실 Toolkit를 시작 하려면 [제공 된 단계](../install-the-tools.md#importing-the-mixed-reality-toolkit) 에 따라 mrtk를 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="fdbe3-110">XR SDK 파이프라인에 대 한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="fdbe3-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="fdbe3-111">XR SDK 파이프라인은 현재 Windows Mixed Reality, oculus 및 OpenXR의 3 개 플랫폼을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="fdbe3-112">아래 섹션에서는 각 플랫폼에 대해 XR SDK를 구성 하는 데 필요한 단계에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="fdbe3-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="fdbe3-113">Windows Mixed Reality</span></span>

<span data-ttu-id="fdbe3-114">**Unity의 패키지 관리자** 로 이동 하 여 XR SDK에서 Windows Mixed Reality에 대 한 지원을 추가 하는 Windows XR 플러그 인 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="fdbe3-115">이렇게 하면 몇 가지 종속성 패키지도 풀 다운 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="fdbe3-116">다음 모두가 성공적으로 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="fdbe3-117">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="fdbe3-117">XR Plugin Management</span></span>
   * <span data-ttu-id="fdbe3-118">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="fdbe3-119">XR 레거시 입력 도우미</span><span class="sxs-lookup"><span data-stu-id="fdbe3-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="fdbe3-120">**편집 > 프로젝트 설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="fdbe3-121">Project 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="fdbe3-122">유니버설 Windows 플랫폼 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="fdbe3-123">시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="fdbe3-124">(**_편집기 내 HoloLens 원격 기능에 필요 하며, 그렇지 않은 경우 선택 사항_**) 독립 실행형 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="fdbe3-125">또한 시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![독립 실행형 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-02.png)

7. <span data-ttu-id="fdbe3-127">(**_선택 사항_**) XR 플러그 인 관리 아래에서 Windows Mixed Reality 탭을 클릭 하 고 사용자 지정 설정 프로필을 만들어 기본값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="fdbe3-128">설정 목록이 이미 있는 경우 프로필을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![Windows 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="fdbe3-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="fdbe3-130">Oculus</span></span>

1. <span data-ttu-id="fdbe3-131">[XR SDK 파이프라인 가이드를 사용 하 여 MRTK에서 Oculus 퀘스트를 구성 하는 방법](../supported-devices/oculus-quest-mrtk.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="fdbe3-132">이 가이드에서는 XR SDK 파이프라인을 사용 하도록 Unity와 MRTK를 모두 구성 하는 데 필요한 단계를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr"></a><span data-ttu-id="fdbe3-133">OpenXR</span><span class="sxs-lookup"><span data-stu-id="fdbe3-133">OpenXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdbe3-134">Unity의 OpenXR는 Unity 2020.2 이상 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="fdbe3-135">또한 x64, ARM 및 ARM64 빌드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="fdbe3-136">XR 플러그 인 관리 및 최적화를 구성 하 여 프로젝트에 OpenXR 플러그 인을 설치 하는 단계를 포함 하 여 [OpenXR에 대 한 혼합 현실 플러그 인을 사용 하](/windows/mixed-reality/develop/unity/openxr-getting-started) 는 방법 가이드를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="fdbe3-137">다음이 성공적으로 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="fdbe3-138">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="fdbe3-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="fdbe3-139">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="fdbe3-140">혼합 현실 OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="fdbe3-141">편집 > Project 설정로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="fdbe3-142">Project 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="fdbe3-143">시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="fdbe3-144">(**_선택 사항_**) HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 Microsoft HoloLens 기능 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![플러그 인 관리 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="fdbe3-146">UPM에서 MRTK를 사용 하는 기존 프로젝트가 있는 경우 MixedRealityToolkit 폴더에 있는 **link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="fdbe3-147">mrtk 및 OpenXR의 초기 릴리스에서는 HoloLens 2로 된 Windows Mixed Reality 동작 컨트롤러만 기본적으로 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="fdbe3-148">추가 하드웨어에 대 한 지원은 향후 릴리스에 추가 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="fdbe3-149">XR SDK 파이프라인에 대 한 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="fdbe3-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-150">모든 Unity의 XR 파이프라인에서 구성 된 기본 MRTK 프로필을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="fdbe3-151">이전 "DefaultOpenXRConfigurationProfile" 및 "DefaultXRSDKConfigurationProfile"은 이제 사용 되지 않는 것으로 레이블이 지정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="fdbe3-152">OpenXR를 사용 하는 경우 "DefaultOpenXRConfigurationProfile"을 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="fdbe3-153">Windows Mixed Reality 또는 oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용 하는 경우 "DefaultXRSDKConfigurationProfile"를 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="fdbe3-154">이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="fdbe3-155">XR SDK를 사용한 프로필 및 샘플 지원에 대 한 자세한 내용은 [프로필 문서를](../features/profiles/profiles.md#xr-sdk) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="fdbe3-156">기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-157">Unity 2019의 XR SDK 탭에서 또는 레거시 XR이 없는 Unity 2020 +의 주/전용 보기에서 새 데이터 공급자를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![XR SDK 탭](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="fdbe3-159">카메라</span><span class="sxs-lookup"><span data-stu-id="fdbe3-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-160">다음 데이터 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="fdbe3-161">보낸 사람 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![레거시 카메라 설정](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="fdbe3-163">을</span><span class="sxs-lookup"><span data-stu-id="fdbe3-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="fdbe3-164">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-164">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-165">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="fdbe3-166">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-166">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-167">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="fdbe3-169">입력</span><span class="sxs-lookup"><span data-stu-id="fdbe3-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-170">다음 데이터 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="fdbe3-171">보낸 사람 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![레거시 입력 설정](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="fdbe3-173">을</span><span class="sxs-lookup"><span data-stu-id="fdbe3-173">to</span></span>
::: moniker-end

| <span data-ttu-id="fdbe3-174">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-174">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-175">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="fdbe3-176">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="fdbe3-176">__OpenXR__:</span></span>

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="fdbe3-178">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="fdbe3-178">__Windows Mixed Reality__:</span></span>

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="fdbe3-180">경계</span><span class="sxs-lookup"><span data-stu-id="fdbe3-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-181">다음 데이터 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="fdbe3-182">보낸 사람 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![레거시 경계 설정](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="fdbe3-184">을</span><span class="sxs-lookup"><span data-stu-id="fdbe3-184">to</span></span>
::: moniker-end

| <span data-ttu-id="fdbe3-185">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-185">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-186">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="fdbe3-188">공간 인식</span><span class="sxs-lookup"><span data-stu-id="fdbe3-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="fdbe3-189">다음 데이터 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="fdbe3-190">보낸 사람 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![레거시 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="fdbe3-192">을</span><span class="sxs-lookup"><span data-stu-id="fdbe3-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="fdbe3-193">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-193">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-194">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="fdbe3-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (UWP의 경우)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="fdbe3-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (UWP의 경우)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="fdbe3-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (비 UWP)</span><span class="sxs-lookup"><span data-stu-id="fdbe3-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="fdbe3-198">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-198">OpenXR Plugin</span></span> | <span data-ttu-id="fdbe3-199">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="fdbe3-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="fdbe3-201">컨트롤러 매핑</span><span class="sxs-lookup"><span data-stu-id="fdbe3-201">Controller mappings</span></span>

<span data-ttu-id="fdbe3-202">사용자 지정 컨트롤러 매핑 프로필을 사용하는 경우 해당 프로필 중 하나를 열고 Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles 메뉴 항목을 실행하여 새 XR SDK 컨트롤러 유형이 정의되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fdbe3-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdbe3-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fdbe3-203">See also</span></span>

* [<span data-ttu-id="fdbe3-204">Unity에서 AR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="fdbe3-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="fdbe3-205">Unity에서 VR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="fdbe3-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
