---
title: UsingARFoundation
description: Unity에서 ARFoundation을 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR Core, AR Kit
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852431"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="8b279-104">iOS 및 Android용 MRTK를 구성하는 방법 [실험적]</span><span class="sxs-lookup"><span data-stu-id="8b279-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="8b279-105">필요한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-105">Install required packages</span></span>

1. <span data-ttu-id="8b279-106">[GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) 또는 Unity 패키지 관리자 **Microsoft.MixedReality.Toolkit.Unity.Foundation** 패키지를 [](../configuration/usingupm.md) 다운로드하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="8b279-107">Unity 패키지 관리자(UPM)에서 다음 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="8b279-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="8b279-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="8b279-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="8b279-109">**Android**</span></span> | <span data-ttu-id="8b279-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8b279-110">**iOS**</span></span> | <span data-ttu-id="8b279-111">의견</span><span class="sxs-lookup"><span data-stu-id="8b279-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="8b279-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8b279-112">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-113">버전: 1.5.0 - 미리 보기 6</span><span class="sxs-lookup"><span data-stu-id="8b279-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8b279-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8b279-114">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-115">버전: 1.5.0 - 미리 보기 6</span><span class="sxs-lookup"><span data-stu-id="8b279-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8b279-116">Unity 2018.4의 경우 이 패키지는 미리 보기로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="8b279-117">패키지를 보려면 다음을 수행합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="8b279-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="8b279-118">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8b279-119">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="8b279-119">Version: 2.1.2</span></span> | <span data-ttu-id="8b279-120">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8b279-121">버전: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="8b279-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="8b279-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="8b279-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="8b279-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="8b279-123">**Android**</span></span> | <span data-ttu-id="8b279-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8b279-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8b279-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8b279-125">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-126">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="8b279-126">Version: 2.1.8</span></span> |  <span data-ttu-id="8b279-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8b279-127">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-128">버전: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="8b279-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="8b279-129">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8b279-130">버전: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="8b279-130">Version: 2.1.11</span></span> | <span data-ttu-id="8b279-131">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8b279-132">버전: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="8b279-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="8b279-133">**Unity 2020.1 (현재 공식적으로 지원 되지 않음, 정보 제공 목적 으로만 포함)**</span><span class="sxs-lookup"><span data-stu-id="8b279-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="8b279-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="8b279-134">**Android**</span></span> | <span data-ttu-id="8b279-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8b279-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8b279-136">AR</span><span class="sxs-lookup"><span data-stu-id="8b279-136">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-137">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="8b279-137">Version: 3.1.3</span></span> |  <span data-ttu-id="8b279-138">AR</span><span class="sxs-lookup"><span data-stu-id="8b279-138">AR Foundation</span></span>  <br/> <span data-ttu-id="8b279-139">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="8b279-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="8b279-140">ARCore XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8b279-141">버전: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="8b279-141">Version: 3.1.4</span></span> | <span data-ttu-id="8b279-142">ARKit XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="8b279-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8b279-143">버전: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="8b279-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="8b279-144">MRTK UnityAR 스크립팅 업데이트는 메뉴 항목을 호출 하 여 정의 합니다. **혼합 현실 도구 키트 > 유틸리티 > UnityAR > Update 스크립팅 정의**</span><span class="sxs-lookup"><span data-stu-id="8b279-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="8b279-145">Unity AR 카메라 설정 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="8b279-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="8b279-146">다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="8b279-147">다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="8b279-148">장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="8b279-150">**복사 및 사용자 지정을** 선택하여 MRTK 프로필 복제를 선택하여 사용자 지정 구성을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="8b279-152">카메라 프로필 옆에 있는 **복제를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-152">Select **Clone** next to the Camera Profile.</span></span>

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="8b279-154">검사기 패널을 카메라 시스템 섹션으로 이동하고 **카메라 설정 공급자 섹션을 확장합니다.**</span><span class="sxs-lookup"><span data-stu-id="8b279-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="8b279-156">**카메라 설정 공급자 추가를** 클릭하고 새로 추가된 새 카메라 **설정** 항목을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="8b279-158">Unity AR 카메라 설정 공급자 선택</span><span class="sxs-lookup"><span data-stu-id="8b279-158">Select the Unity AR Camera Settings provider</span></span>

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="8b279-160">Unity AR 카메라 설정 공급자를 구성하는 방법에 대한 자세한 내용은 [Unity AR 카메라 설정 공급자를 참조하세요.](../features/camera-system/unity-ar-camera-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8b279-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b279-161">이 설치는 AR Foundation 구성 요소가 장면에 있는지 확인합니다(애플리케이션이 시작될 때).</span><span class="sxs-lookup"><span data-stu-id="8b279-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="8b279-162">그렇지 않으면 ARCore 및 ARKit에서 작동하도록 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="8b279-163">특정 동작을 설정해야 하는 경우 필요한 구성 요소를 직접 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="8b279-164">AR Foundation 구성 요소 및 설치에 대한 자세한 내용은 이 [설명서를 참조하세요.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="8b279-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="8b279-165">Android 및 iOS 디바이스에 대한 장면 빌드</span><span class="sxs-lookup"><span data-stu-id="8b279-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="8b279-166">UnityAR 카메라 설정 공급자를 장면에 추가했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="8b279-167">Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환</span><span class="sxs-lookup"><span data-stu-id="8b279-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="8b279-168">플랫폼을 전환하면 선택한 플랫폼에 대한 설정이 있는 MRTK 프로젝트 구성기 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="8b279-169">적용을 클릭하여 플랫폼별 설정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="8b279-170">iOS 프로젝트 구성자 설정</span><span class="sxs-lookup"><span data-stu-id="8b279-170">iOS Project Configurator Settings</span></span>

    ![iOS 프로젝트 구성 기](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="8b279-172">Android 용 플랫폼을 전환한 후에는 추가 단계가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="8b279-173">플랫폼이 iOS 인 경우 > 프로젝트 설정 > 플레이어 > 기타 설정을 최적화 헤더 아래에서 편집 합니다. **코드 스트립 엔진** 코드</span><span class="sxs-lookup"><span data-stu-id="8b279-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 설정](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="8b279-175">Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)의 오류에 대 한 단기 해결책은 스트립 엔진 코드를 해제 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="8b279-176">장기적으로 해결 하기 위해 노력 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="8b279-177">장면을 빌드하고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b279-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="8b279-178">추가 정보</span><span class="sxs-lookup"><span data-stu-id="8b279-178">See also</span></span>

- [<span data-ttu-id="8b279-179">Unity AR 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="8b279-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
