---
title: 카메라 시스템 개요
description: MRTK의 카메라 시스템에 대 한 방문 페이지
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 카메라,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177041"
---
# <a name="camera-system-overview"></a><span data-ttu-id="cae66-104">카메라 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="cae66-104">Camera system overview</span></span>

<span data-ttu-id="cae66-105">카메라 시스템을 사용 하면 혼합 현실 응용 프로그램에서 사용할 수 있도록 응용 프로그램의 카메라를 구성 하 고 최적화할 수 Toolkit Microsoft mixed reality를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="cae66-106">카메라 시스템을 사용 하 여 각 유형의 표시를 구분 하는 코드를 작성할 필요 없이 불투명 (예: 가상 현실) 및 투명 (예: Microsoft HoloLens) 장치를 모두 지원 하도록 응용 프로그램을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="cae66-107">카메라 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="cae66-107">Enabling the camera system</span></span>

<span data-ttu-id="cae66-108">카메라 시스템은 MixedRealityToolkit 개체 (또는 다른 서비스 등록자 구성 요소)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="cae66-109">다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="cae66-110">다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="cae66-111">장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="cae66-113">검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 시스템 사용** 이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![카메라 시스템 사용](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="cae66-115">카메라 시스템 구현을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-115">Select the camera system implementation.</span></span> <span data-ttu-id="cae66-116">MRTK에서 제공 하는 기본 클래스 구현은입니다 `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="cae66-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![카메라 시스템 구현 선택](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="cae66-118">원하는 구성 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-118">Select the desired configuration profile</span></span>

    ![카메라 시스템 프로필 선택](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="cae66-120">카메라 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="cae66-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="cae66-121">설정 공급자</span><span class="sxs-lookup"><span data-stu-id="cae66-121">Settings providers</span></span>

![카메라 설정 공급자](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="cae66-123">카메라 설정 공급자는 카메라의 플랫폼별 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="cae66-124">이러한 설정에는 사용자 지정 구성 단계 및/또는 구성 요소가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="cae66-125">공급자는 **Add Camera 설정 Provider** 단추를 클릭 하 여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="cae66-126">**-** 공급자 이름 오른쪽에 있는 단추를 클릭 하 여 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="cae66-127">일부 플랫폼에서는 카메라 설정 공급자가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="cae66-128">응용 프로그램이 실행 되는 플랫폼과 호환 되는 공급자가 없는 경우 Microsoft Mixed Reality Toolkit 기본 기본값을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="cae66-129">디스플레이 설정</span><span class="sxs-lookup"><span data-stu-id="cae66-129">Display settings</span></span>

![카메라 디스플레이 설정](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="cae66-131">표시 설정은 불투명 (예: 가상 현실)과 투명 (예: Microsoft HoloLens) 표시 모두에 대해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="cae66-132">카메라는 런타임에 이러한 설정을 사용 하 여 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="cae66-133">**가까운 클립**</span><span class="sxs-lookup"><span data-stu-id="cae66-133">**Near Clip**</span></span>

<span data-ttu-id="cae66-134">가까이 있는 클립 평면은 가상 개체가 카메라에 있을 수 있는 가장 가까운 미터 단위 이며 여전히 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="cae66-135">사용자의 편안 함을 최대한 활용 하려면이 값을 0 보다 크게 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="cae66-136">이전 이미지에는 다양 한 장치에서 편안 하 게 발견 된 값이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="cae66-137">**먼 클립**</span><span class="sxs-lookup"><span data-stu-id="cae66-137">**Far Clip**</span></span>

<span data-ttu-id="cae66-138">먼 클립 평면은 가장 quantity (미터) 이며,이는 가상 개체가 카메라에 있을 수 있으며 여전히 렌더링 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="cae66-139">투명 한 장치의 경우 실제 세계 공간을 과도 하 게 초과 하지 않고이 값을 비교적 가까이 두고 응용 프로그램의 몰입 형 품질을 해제 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="cae66-140">**플래그 지우기**</span><span class="sxs-lookup"><span data-stu-id="cae66-140">**Clear Flags**</span></span>

<span data-ttu-id="cae66-141">Clear flags 값은 그릴 때 표시 되는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="cae66-142">가상 현실 환경의 경우이 값을 Skybox로 설정 하는 것이 가장 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="cae66-143">투명 디스플레이의 경우 색으로 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="cae66-144">**배경색**</span><span class="sxs-lookup"><span data-stu-id="cae66-144">**Background Color**</span></span>

<span data-ttu-id="cae66-145">Clear 플래그를 Skybox로 설정 하지 않으면 배경색 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="cae66-146">**품질 설정**</span><span class="sxs-lookup"><span data-stu-id="cae66-146">**Quality Settings**</span></span>

<span data-ttu-id="cae66-147">품질 설정 값은 Unity가 장면을 렌더링할 때 사용 해야 하는 그래픽 품질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="cae66-148">품질 수준은 프로젝트 수준 설정이 며 한 카메라에 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cae66-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="cae66-149">자세한 내용은 Unity 설명서의 [품질](https://docs.unity3d.com/Manual/class-QualitySettings.html) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cae66-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="cae66-150">참조</span><span class="sxs-lookup"><span data-stu-id="cae66-150">See also</span></span>

- [<span data-ttu-id="cae66-151">카메라 시스템 API 설명서</span><span class="sxs-lookup"><span data-stu-id="cae66-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="cae66-152">카메라 설정 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="cae66-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
