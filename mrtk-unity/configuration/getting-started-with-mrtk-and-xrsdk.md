---
title: MRTK 및 XR SDK 시작
description: XR SDK를 통해 MRTK에 대한 방문 페이지
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, XRSDK, XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647209"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="ac5e8-104">MRTK 및 XR SDK 시작</span><span class="sxs-lookup"><span data-stu-id="ac5e8-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="ac5e8-105">XR SDK는 Unity [2019.3 이상에서 Unity의 새로운 XR 파이프라인입니다.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="ac5e8-106">Unity 2019에서는 기존 XR 파이프라인에 대한 대안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="ac5e8-107">Unity 2020에서는 Unity에서 유일한 XR 파이프라인이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac5e8-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ac5e8-108">Prerequisites</span></span>

<span data-ttu-id="ac5e8-109">Mixed Reality 도구 키트를 시작하려면 [제공된 단계에](../install-the-tools.md#importing-the-mixed-reality-toolkit) 따라 MRTK를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ac5e8-110">XR SDK 파이프라인에 대한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="ac5e8-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="ac5e8-111">XR SDK 파이프라인은 현재 3개의 플랫폼인 Windows Mixed Reality, Oculus 및 OpenXR을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="ac5e8-112">아래 섹션에서는 각 플랫폼에 대해 XR SDK를 구성하는 데 필요한 단계를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="ac5e8-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-113">Windows Mixed Reality</span></span>

<span data-ttu-id="ac5e8-114">**Unity의 패키지 관리자** 이동하여 Windows XR 플러그 인 패키지를 설치합니다. 이 패키지는 XR SDK에서 Windows Mixed Reality 대한 지원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="ac5e8-115">그러면 몇 가지 종속성 패키지도 풀다운됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="ac5e8-116">다음이 모두 성공적으로 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="ac5e8-117">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="ac5e8-117">XR Plugin Management</span></span>
   * <span data-ttu-id="ac5e8-118">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="ac5e8-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="ac5e8-119">XR 레거시 입력 도우미</span><span class="sxs-lookup"><span data-stu-id="ac5e8-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="ac5e8-120">**편집 > 프로젝트 설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="ac5e8-121">프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="ac5e8-122">유니버설 Windows 플랫폼 설정으로 이동하여 플러그 인 공급자에서 Windows Mixed Reality 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="ac5e8-123">시작 시 XR 초기화가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="ac5e8-124">**_(편집기 내 HoloLens Remoting에 필요하고, 그렇지 않으면 선택 사항)_** 독립 실행형 설정으로 이동하여 플러그 인 공급자에서 Windows Mixed Reality 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="ac5e8-125">또한 시작 시 XR 초기화가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![독립 실행형 탭이 선택된 XR 플러그 인 관리](images/xr-management-img-02.png)

7. <span data-ttu-id="ac5e8-127">(**_선택 사항)_** XR 플러그 인 관리 아래의 Windows Mixed Reality 탭을 클릭하고 사용자 지정 설정 프로필을 만들어 기본값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="ac5e8-128">설정 목록이 이미 있는 경우 프로필을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Windows 탭이 선택된 XR 플러그 인 관리](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="ac5e8-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="ac5e8-130">Oculus</span></span>

1. <span data-ttu-id="ac5e8-131">[끝으로 XR SDK 파이프라인을 사용하여 MRTK에서 Oculus Quest를 구성하는 방법](../supported-devices/oculus-quest-mrtk.md) 가이드를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="ac5e8-132">이 가이드에서는 Oculus Quest에 XR SDK 파이프라인을 사용하도록 Unity 및 MRTK를 구성하는 데 필요한 단계를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="ac5e8-133">OpenXR(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac5e8-134">Unity의 OpenXR은 Unity 2020.2 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="ac5e8-135">현재 x64 및 ARM64 빌드만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="ac5e8-136">프로젝트에 [OpenXR 플러그 인을](/windows/mixed-reality/develop/unity/openxr-getting-started) 설치하도록 XR 플러그 인 관리 및 최적화를 구성하는 단계를 포함하여 Unity용 Mixed Reality OpenXR 플러그 인 사용 가이드를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="ac5e8-137">다음이 성공적으로 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="ac5e8-138">XR 플러그 인 관리</span><span class="sxs-lookup"><span data-stu-id="ac5e8-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="ac5e8-139">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="ac5e8-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="ac5e8-140">OpenXR 플러그 인 Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="ac5e8-141">프로젝트 설정 > 편집으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="ac5e8-142">프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="ac5e8-143">시작 시 XR 초기화가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="ac5e8-144">(**_선택 사항)_** HoloLens 2 대상으로 하는 경우 UWP 플랫폼에 있는지 확인하고 Microsoft HoloLens 기능 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![플러그 인 관리 Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="ac5e8-146">UPM의 MRTK를 사용하는 기존 프로젝트가 있는 경우 다음 줄이 MixedRealityToolkit.Generated 폴더에 있는 **link.xml** 파일에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="ac5e8-147">MRTK 및 OpenXR의 초기 릴리스에서는 HoloLens 2 개의 굴절된 손과 Windows Mixed Reality 모션 컨트롤러만 기본적으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="ac5e8-148">추가 하드웨어에 대한 지원은 향후 릴리스에서 추가될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ac5e8-149">XR SDK 파이프라인에 대한 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="ac5e8-149">Configuring MRTK for the XR SDK pipeline</span></span>
::: moniker range=">= mrtkunity-2021-05" 
<span data-ttu-id="ac5e8-150">OpenXR을 사용하는 경우 활성 프로필로 "DefaultOpenXRConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ac5e8-151">Windows Mixed Reality 또는 Oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용하는 경우 활성 프로필로 "DefaultXRSDKConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ac5e8-152">이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 통해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="ac5e8-153">XR SDK의 프로필 및 샘플 지원에 대한 자세한 내용은 프로필 [문서를](../features/profiles/profiles.md#xr-sdk) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="ac5e8-154">기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-154">To migrate an existing profile to XR SDK, the following services and data providers should be added.</span></span> <span data-ttu-id="ac5e8-155">XR SDK 탭에서 새 데이터 공급자를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-155">You will be able to see the new data providers under the XR SDK tab</span></span>

![XR SDK 탭](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a><span data-ttu-id="ac5e8-157">카메라</span><span class="sxs-lookup"><span data-stu-id="ac5e8-157">Camera</span></span>

<span data-ttu-id="ac5e8-158">다음 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="ac5e8-158">Add the following data providers</span></span> 

| <span data-ttu-id="ac5e8-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-159">OpenXR</span></span> | <span data-ttu-id="ac5e8-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="ac5e8-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**및**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="ac5e8-163">입력</span><span class="sxs-lookup"><span data-stu-id="ac5e8-163">Input</span></span>

<span data-ttu-id="ac5e8-164">다음 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="ac5e8-164">Add the following data providers</span></span> 

| <span data-ttu-id="ac5e8-165">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-165">OpenXR</span></span> | <span data-ttu-id="ac5e8-166">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-166">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="ac5e8-167">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="ac5e8-167">__OpenXR__:</span></span>

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="ac5e8-169">__Windows Mixed Reality:__</span><span class="sxs-lookup"><span data-stu-id="ac5e8-169">__Windows Mixed Reality__:</span></span>

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="ac5e8-171">경계</span><span class="sxs-lookup"><span data-stu-id="ac5e8-171">Boundary</span></span>

<span data-ttu-id="ac5e8-172">다음 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="ac5e8-172">Add the following data providers</span></span> 

| <span data-ttu-id="ac5e8-173">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-173">OpenXR</span></span> | <span data-ttu-id="ac5e8-174">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-174">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="ac5e8-176">공간 인식</span><span class="sxs-lookup"><span data-stu-id="ac5e8-176">Spatial awareness</span></span>

<span data-ttu-id="ac5e8-177">다음 데이터 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="ac5e8-177">Add the following data providers</span></span> 

| <span data-ttu-id="ac5e8-178">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-178">OpenXR</span></span> | <span data-ttu-id="ac5e8-179">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-179">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="ac5e8-180">진행 중</span><span class="sxs-lookup"><span data-stu-id="ac5e8-180">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="ac5e8-182">컨트롤러 매핑</span><span class="sxs-lookup"><span data-stu-id="ac5e8-182">Controller mappings</span></span>

<span data-ttu-id="ac5e8-183">사용자 지정 컨트롤러 매핑 프로필을 사용하는 경우 해당 프로필 중 하나를 열고 Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles 메뉴 항목을 실행하여 새 XR SDK 컨트롤러 유형이 정의되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-183">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac5e8-184">참조</span><span class="sxs-lookup"><span data-stu-id="ac5e8-184">See also</span></span>

* [<span data-ttu-id="ac5e8-185">Unity에서 AR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="ac5e8-185">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="ac5e8-186">Unity에서 VR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="ac5e8-186">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="ac5e8-187">OpenXR을 사용하는 경우 활성 프로필로 "DefaultOpenXRConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-187">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ac5e8-188">Windows Mixed Reality 또는 Oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용하는 경우 활성 프로필로 "DefaultXRSDKConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-188">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ac5e8-189">이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 통해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-189">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="ac5e8-190">XR SDK의 프로필 및 샘플 지원에 대한 자세한 내용은 프로필 [문서를](../features/profiles/profiles.md#xr-sdk) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-190">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="ac5e8-191">기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-191">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="ac5e8-192">카메라</span><span class="sxs-lookup"><span data-stu-id="ac5e8-192">Camera</span></span>

<span data-ttu-id="ac5e8-193">보낸 사람 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-193">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![레거시 카메라 설정](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="ac5e8-195">을</span><span class="sxs-lookup"><span data-stu-id="ac5e8-195">to</span></span>

| <span data-ttu-id="ac5e8-196">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-196">OpenXR</span></span> | <span data-ttu-id="ac5e8-197">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-197">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="ac5e8-198">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**및**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-198">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="ac5e8-200">입력</span><span class="sxs-lookup"><span data-stu-id="ac5e8-200">Input</span></span>

<span data-ttu-id="ac5e8-201">보낸 사람 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-201">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![레거시 입력 설정](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="ac5e8-203">을</span><span class="sxs-lookup"><span data-stu-id="ac5e8-203">to</span></span>

| <span data-ttu-id="ac5e8-204">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-204">OpenXR</span></span> | <span data-ttu-id="ac5e8-205">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-205">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="ac5e8-206">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="ac5e8-206">__OpenXR__:</span></span>

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="ac5e8-208">__Windows Mixed Reality:__</span><span class="sxs-lookup"><span data-stu-id="ac5e8-208">__Windows Mixed Reality__:</span></span>

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="ac5e8-210">경계</span><span class="sxs-lookup"><span data-stu-id="ac5e8-210">Boundary</span></span>

<span data-ttu-id="ac5e8-211">보낸 사람 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-211">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![레거시 경계 설정](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="ac5e8-213">을</span><span class="sxs-lookup"><span data-stu-id="ac5e8-213">to</span></span>

| <span data-ttu-id="ac5e8-214">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-214">OpenXR</span></span> | <span data-ttu-id="ac5e8-215">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-215">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="ac5e8-217">공간 인식</span><span class="sxs-lookup"><span data-stu-id="ac5e8-217">Spatial awareness</span></span>

<span data-ttu-id="ac5e8-218">보낸 사람 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="ac5e8-218">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![레거시 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="ac5e8-220">을</span><span class="sxs-lookup"><span data-stu-id="ac5e8-220">to</span></span>

| <span data-ttu-id="ac5e8-221">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5e8-221">OpenXR</span></span> | <span data-ttu-id="ac5e8-222">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ac5e8-222">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="ac5e8-223">진행 중</span><span class="sxs-lookup"><span data-stu-id="ac5e8-223">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="ac5e8-225">컨트롤러 매핑</span><span class="sxs-lookup"><span data-stu-id="ac5e8-225">Controller mappings</span></span>

<span data-ttu-id="ac5e8-226">사용자 지정 컨트롤러 매핑 프로필을 사용하는 경우 해당 프로필 중 하나를 열고 Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles 메뉴 항목을 실행하여 새 XR SDK 컨트롤러 유형이 정의되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e8-226">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac5e8-227">참조</span><span class="sxs-lookup"><span data-stu-id="ac5e8-227">See also</span></span>

* [<span data-ttu-id="ac5e8-228">Unity에서 AR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="ac5e8-228">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="ac5e8-229">Unity에서 VR 개발 시작</span><span class="sxs-lookup"><span data-stu-id="ac5e8-229">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end