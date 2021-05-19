---
title: AR Foundation 사용
description: Unity에서 ARFoundation 사용에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 코어, AR 키트
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143945"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="7a43e-104">IOS 및 Android 용 MRTK를 구성 하는 방법 [실험적]</span><span class="sxs-lookup"><span data-stu-id="7a43e-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="7a43e-105">필요한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-105">Install required packages</span></span>

1. <span data-ttu-id="7a43e-106">[GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) 또는 [Unity 패키지 관리자](../configuration/usingupm.md) 에서 **MixedReality** 패키지를 다운로드 하 여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="7a43e-107">UPM (Unity 패키지 관리자)에서 다음 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="7a43e-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="7a43e-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="7a43e-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="7a43e-109">**Android**</span></span> | <span data-ttu-id="7a43e-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="7a43e-110">**iOS**</span></span> | <span data-ttu-id="7a43e-111">의견</span><span class="sxs-lookup"><span data-stu-id="7a43e-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="7a43e-112">AR</span><span class="sxs-lookup"><span data-stu-id="7a43e-112">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-113">버전: 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="7a43e-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="7a43e-114">AR</span><span class="sxs-lookup"><span data-stu-id="7a43e-114">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-115">버전: 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="7a43e-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="7a43e-116">Unity 2018.4의 경우이 패키지는 미리 보기로 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="7a43e-117">패키지를 보려면 다음을 수행 합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="7a43e-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="7a43e-118">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-119">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="7a43e-119">Version: 2.1.2</span></span> | <span data-ttu-id="7a43e-120">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-121">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="7a43e-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="7a43e-122">**Unity 2019.4**</span><span class="sxs-lookup"><span data-stu-id="7a43e-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="7a43e-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="7a43e-123">**Android**</span></span> | <span data-ttu-id="7a43e-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="7a43e-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="7a43e-125">AR</span><span class="sxs-lookup"><span data-stu-id="7a43e-125">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-126">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="7a43e-126">Version: 2.1.8</span></span> |  <span data-ttu-id="7a43e-127">AR</span><span class="sxs-lookup"><span data-stu-id="7a43e-127">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-128">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="7a43e-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="7a43e-129">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-130">버전: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="7a43e-130">Version: 2.1.11</span></span> | <span data-ttu-id="7a43e-131">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-132">버전: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="7a43e-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="7a43e-133">**Unity 2020.1.x(현재 공식적으로 지원되지 않음, 정보 제공 목적으로만 포함됨)**</span><span class="sxs-lookup"><span data-stu-id="7a43e-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="7a43e-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="7a43e-134">**Android**</span></span> | <span data-ttu-id="7a43e-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="7a43e-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="7a43e-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="7a43e-136">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-137">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="7a43e-137">Version: 3.1.3</span></span> |  <span data-ttu-id="7a43e-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="7a43e-138">AR Foundation</span></span>  <br/> <span data-ttu-id="7a43e-139">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="7a43e-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="7a43e-140">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-141">버전: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="7a43e-141">Version: 3.1.4</span></span> | <span data-ttu-id="7a43e-142">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="7a43e-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="7a43e-143">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="7a43e-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="7a43e-144">메뉴 항목을 호출하여 MRTK UnityAR 스크립팅 정의 업데이트: **Mixed Reality Toolkit > Utilities > UnityAR > 업데이트 스크립팅 정의**</span><span class="sxs-lookup"><span data-stu-id="7a43e-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="7a43e-145">Unity AR 카메라 설정 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="7a43e-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="7a43e-146">다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="7a43e-147">다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="7a43e-148">장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="7a43e-150">**복사 및 사용자 지정을** 선택하여 MRTK 프로필 복제를 선택하여 사용자 지정 구성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="7a43e-152">카메라 프로필 옆의 **복제** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-152">Select **Clone** next to the Camera Profile.</span></span>

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="7a43e-154">검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 설정 공급자** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="7a43e-156">**카메라 설정 공급자 추가** 를 클릭 하 고 새로 추가 된 **새 카메라 설정** 항목을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="7a43e-158">Unity AR 카메라 설정 공급자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-158">Select the Unity AR Camera Settings provider</span></span>

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="7a43e-160">Unity AR 카메라 설정 공급자를 구성 하는 방법에 대 한 자세한 내용은 [UNITY ar 카메라 설정 공급자를 제공](../features/camera-system/unity-ar-camera-settings.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7a43e-161">AR 구성 요소가 장면에 있는 경우이 설치는 응용 프로그램이 시작 될 때를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="7a43e-162">그렇지 않은 경우 ARCore 및 Arcore에서 사용할 수 있도록 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="7a43e-163">특정 동작을 설정 해야 하는 경우에는 필요한 구성 요소를 직접 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="7a43e-164">AR 기반 구성 요소 및 설치에 대 한 자세한 내용은이 [설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a43e-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="7a43e-165">Android 및 iOS 장치에 대 한 장면 빌드</span><span class="sxs-lookup"><span data-stu-id="7a43e-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="7a43e-166">장면에 UnityAR 카메라 설정 공급자를 추가 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="7a43e-167">Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="7a43e-168">플랫폼을 전환할 때 선택한 플랫폼에 대 한 설정이 포함 된 MRTK 프로젝트 구성 기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="7a43e-169">플랫폼 특정 설정을 사용 하려면 적용을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="7a43e-170">iOS 프로젝트 구성자 설정</span><span class="sxs-lookup"><span data-stu-id="7a43e-170">iOS Project Configurator Settings</span></span>

    ![iOS 프로젝트 구성기](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="7a43e-172">Android용 플랫폼을 전환한 후에는 추가 단계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="7a43e-173">플랫폼이 iOS인 경우 최적화 헤더에서 플레이어 > 기타 설정 > 프로젝트 설정 > 편집에서 엔진 코드 **제거를 선택 취소합니다.**</span><span class="sxs-lookup"><span data-stu-id="7a43e-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 설정](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="7a43e-175">줄무늬 엔진 코드의 선택을 취소하는 것은 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)오류에 대한 단기 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="7a43e-176">장기 솔루션에 대해 작업하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a43e-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="7a43e-177">장면 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="7a43e-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="7a43e-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a43e-178">See also</span></span>

- [<span data-ttu-id="7a43e-179">Unity AR 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="7a43e-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
