---
title: AR Foundation을 통해 Android 및 iOS 빌드 및 배포
description: Unity에서 ANDROID 및 iOS(ARFoundation)용 MRTK를 구성하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449742"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a><span data-ttu-id="5bbde-104">AR Foundation을 통해 Android 및 iOS에 빌드 및 배포 [실험적]</span><span class="sxs-lookup"><span data-stu-id="5bbde-104">Building and Deploying to Android and iOS via AR Foundation [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="5bbde-105">필요한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-105">Install required packages</span></span>

1. <span data-ttu-id="5bbde-106">[GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) 또는 Unity 패키지 관리자 **Microsoft.MixedReality.Toolkit.Unity.Foundation** 패키지를 [](../configuration/usingupm.md) 다운로드하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="5bbde-107">Unity 패키지 관리자(UPM)에서 다음 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="5bbde-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="5bbde-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="5bbde-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="5bbde-109">**Android**</span></span> | <span data-ttu-id="5bbde-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="5bbde-110">**iOS**</span></span> | <span data-ttu-id="5bbde-111">의견</span><span class="sxs-lookup"><span data-stu-id="5bbde-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="5bbde-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-112">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-113">버전: 1.5.0 - 미리 보기 6</span><span class="sxs-lookup"><span data-stu-id="5bbde-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="5bbde-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-114">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-115">버전: 1.5.0 - 미리 보기 6</span><span class="sxs-lookup"><span data-stu-id="5bbde-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="5bbde-116">Unity 2018.4의 경우 이 패키지는 미리 보기로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="5bbde-117">패키지를 보려면 다음을 수행합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="5bbde-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="5bbde-118">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-119">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="5bbde-119">Version: 2.1.2</span></span> | <span data-ttu-id="5bbde-120">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-121">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="5bbde-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="5bbde-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="5bbde-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="5bbde-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="5bbde-123">**Android**</span></span> | <span data-ttu-id="5bbde-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="5bbde-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="5bbde-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-125">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-126">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="5bbde-126">Version: 2.1.8</span></span> |  <span data-ttu-id="5bbde-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-127">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-128">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="5bbde-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="5bbde-129">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-130">버전: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="5bbde-130">Version: 2.1.11</span></span> | <span data-ttu-id="5bbde-131">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-132">버전: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="5bbde-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="5bbde-133">**Unity 2020.3.x**</span><span class="sxs-lookup"><span data-stu-id="5bbde-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="5bbde-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="5bbde-134">**Android**</span></span> | <span data-ttu-id="5bbde-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="5bbde-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="5bbde-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-136">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-137">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="5bbde-137">Version: 3.1.3</span></span> |  <span data-ttu-id="5bbde-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="5bbde-138">AR Foundation</span></span>  <br/> <span data-ttu-id="5bbde-139">버전: 4.0.12</span><span class="sxs-lookup"><span data-stu-id="5bbde-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="5bbde-140">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-141">버전: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="5bbde-141">Version: 3.1.4</span></span> | <span data-ttu-id="5bbde-142">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="5bbde-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="5bbde-143">버전: 4.1.7</span><span class="sxs-lookup"><span data-stu-id="5bbde-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="5bbde-144">메뉴 항목을 호출하여 MRTK UnityAR 스크립팅 정의 업데이트: **Mixed Reality > Toolkit > Utilities > UnityAR > 업데이트 스크립팅 정의**</span><span class="sxs-lookup"><span data-stu-id="5bbde-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![업데이트 스크립팅 정의](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="5bbde-146">Unity AR 카메라 설정 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="5bbde-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="5bbde-147">다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="5bbde-148">다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="5bbde-149">장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="5bbde-151">**복사 및 사용자 지정을** 선택하여 MRTK 프로필 복제를 선택하여 사용자 지정 구성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="5bbde-153">카메라 프로필 옆에 있는 **복제를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-153">Select **Clone** next to the Camera Profile.</span></span>

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="5bbde-155">검사기 패널을 카메라 시스템 섹션으로 이동하고 **카메라 설정 공급자 섹션을 확장합니다.**</span><span class="sxs-lookup"><span data-stu-id="5bbde-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="5bbde-157">**카메라 설정 공급자 추가를** 클릭하고 새로 추가된 새 카메라 **설정** 항목을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="5bbde-159">Unity AR 카메라 설정 공급자 선택</span><span class="sxs-lookup"><span data-stu-id="5bbde-159">Select the Unity AR Camera Settings provider</span></span>

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="5bbde-161">Unity AR 카메라 설정 공급자를 구성하는 방법에 대한 자세한 내용은 [Unity AR 카메라 설정 공급자를 참조하세요.](../features/camera-system/unity-ar-camera-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5bbde-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5bbde-162">이 설치는 AR Foundation 구성 요소가 장면에 있는지 확인합니다(애플리케이션이 시작될 때).</span><span class="sxs-lookup"><span data-stu-id="5bbde-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="5bbde-163">그렇지 않으면 ARCore 및 ARKit에서 작동하도록 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="5bbde-164">특정 동작을 설정해야 하는 경우 필요한 구성 요소를 직접 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="5bbde-165">AR Foundation 구성 요소 및 설치에 대한 자세한 내용은 이 [설명서를 참조하세요.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="5bbde-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="5bbde-166">Android 및 iOS 디바이스에 대한 장면 빌드</span><span class="sxs-lookup"><span data-stu-id="5bbde-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="5bbde-167">UnityAR 카메라 설정 공급자를 장면에 추가했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="5bbde-168">Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환</span><span class="sxs-lookup"><span data-stu-id="5bbde-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="5bbde-169">연결된 XR 플러그 인 관리 공급자가 사용하도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5bbde-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="5bbde-170">iOS XR 플러그 인 관리:  ![ XR 플러그 인 관리 iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="5bbde-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="5bbde-171">장면 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="5bbde-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="5bbde-172">참조</span><span class="sxs-lookup"><span data-stu-id="5bbde-172">See also</span></span>

- [<span data-ttu-id="5bbde-173">Unity AR 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="5bbde-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
