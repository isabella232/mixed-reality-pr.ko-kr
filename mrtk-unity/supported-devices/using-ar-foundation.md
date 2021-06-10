---
title: Android 및 iOS MRTK 구성 (ARFoundation)
description: Unity에서 MRTK for Android 및 iOS (ARFoundation)를 구성 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 코어, AR 키트, iOS, IOS, Android, AR
ms.openlocfilehash: 9f621008db76e3f8e443545b795db442d7c17dda
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345136"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="028e7-104">IOS 및 Android 용 MRTK를 구성 하는 방법 [실험적]</span><span class="sxs-lookup"><span data-stu-id="028e7-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="028e7-105">필요한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-105">Install required packages</span></span>

1. <span data-ttu-id="028e7-106">[GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) 또는 [Unity 패키지 관리자](../configuration/usingupm.md) 에서 **MixedReality** 패키지를 다운로드 하 여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="028e7-107">UPM (Unity 패키지 관리자)에서 다음 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="028e7-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="028e7-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="028e7-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="028e7-109">**Android**</span></span> | <span data-ttu-id="028e7-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="028e7-110">**iOS**</span></span> | <span data-ttu-id="028e7-111">의견</span><span class="sxs-lookup"><span data-stu-id="028e7-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="028e7-112">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-112">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-113">버전: 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="028e7-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="028e7-114">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-114">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-115">버전: 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="028e7-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="028e7-116">Unity 2018.4의 경우이 패키지는 미리 보기로 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="028e7-117">패키지를 보려면 다음을 수행 합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="028e7-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="028e7-118">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="028e7-119">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="028e7-119">Version: 2.1.2</span></span> | <span data-ttu-id="028e7-120">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="028e7-121">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="028e7-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="028e7-122">**Unity 2019.4**</span><span class="sxs-lookup"><span data-stu-id="028e7-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="028e7-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="028e7-123">**Android**</span></span> | <span data-ttu-id="028e7-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="028e7-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="028e7-125">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-125">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-126">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="028e7-126">Version: 2.1.8</span></span> |  <span data-ttu-id="028e7-127">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-127">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-128">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="028e7-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="028e7-129">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="028e7-130">버전: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="028e7-130">Version: 2.1.11</span></span> | <span data-ttu-id="028e7-131">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="028e7-132">버전: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="028e7-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="028e7-133">**Unity 2020.1 (현재 공식적으로 지원 되지 않음, 정보 제공 목적 으로만 포함)**</span><span class="sxs-lookup"><span data-stu-id="028e7-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="028e7-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="028e7-134">**Android**</span></span> | <span data-ttu-id="028e7-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="028e7-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="028e7-136">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-136">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-137">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="028e7-137">Version: 3.1.3</span></span> |  <span data-ttu-id="028e7-138">AR</span><span class="sxs-lookup"><span data-stu-id="028e7-138">AR Foundation</span></span>  <br/> <span data-ttu-id="028e7-139">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="028e7-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="028e7-140">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="028e7-141">버전: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="028e7-141">Version: 3.1.4</span></span> | <span data-ttu-id="028e7-142">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="028e7-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="028e7-143">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="028e7-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="028e7-144">메뉴 항목을 호출 하 여 MRTK UnityAR scripting를 업데이트 합니다. **혼합 현실 > Toolkit > 유틸리티 > UnityAR > 업데이트 스크립팅 정의**</span><span class="sxs-lookup"><span data-stu-id="028e7-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![업데이트 스크립팅 정의](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="028e7-146">Unity AR 카메라 설정 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="028e7-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="028e7-147">다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="028e7-148">다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="028e7-149">장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="028e7-151">**복사 및 사용자** 지정을 선택 하 여 MRTK 프로필을 복제 하 고 사용자 지정 구성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="028e7-153">카메라 프로필 옆의 **복제** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-153">Select **Clone** next to the Camera Profile.</span></span>

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="028e7-155">검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 설정 공급자** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="028e7-157">**카메라 설정 공급자 추가** 를 클릭 하 고 새로 추가 된 **새 카메라 설정** 항목을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="028e7-159">Unity AR 카메라 설정 공급자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-159">Select the Unity AR Camera Settings provider</span></span>

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="028e7-161">Unity AR 카메라 설정 공급자를 구성 하는 방법에 대 한 자세한 내용은 [UNITY ar 카메라 설정 공급자를 제공](../features/camera-system/unity-ar-camera-settings.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="028e7-162">AR 구성 요소가 장면에 있는 경우이 설치는 응용 프로그램이 시작 될 때를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="028e7-163">그렇지 않은 경우 ARCore 및 Arcore에서 사용할 수 있도록 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="028e7-164">특정 동작을 설정 해야 하는 경우에는 필요한 구성 요소를 직접 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="028e7-165">AR 기반 구성 요소 및 설치에 대 한 자세한 내용은이 [설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="028e7-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="028e7-166">Android 및 iOS 장치에 대 한 장면 빌드</span><span class="sxs-lookup"><span data-stu-id="028e7-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="028e7-167">장면에 UnityAR 카메라 설정 공급자를 추가 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="028e7-168">Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="028e7-169">연결 된 XR 플러그 인 관리 공급자가 사용 하도록 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="028e7-170">iOS XR 플러그 인 관리:  ![ XR 플러그 인 관리 iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="028e7-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="028e7-171">장면을 빌드하고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="028e7-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="028e7-172">참조</span><span class="sxs-lookup"><span data-stu-id="028e7-172">See also</span></span>

- [<span data-ttu-id="028e7-173">Unity AR 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="028e7-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
