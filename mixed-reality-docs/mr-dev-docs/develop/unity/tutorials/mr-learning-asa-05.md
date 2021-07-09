---
title: Android 및 iOS용 Azure Spatial Anchors
description: 이 과정을 완료하면 MRTK(Mixed Reality Toolkit) 및 Azure Spatial Anchors가 포함된 Unity 프로젝트를 Android 및 iOS에 배포하는 방법을 알아볼 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, android, ios, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403436"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="efe21-104">5. Android 및 iOS용 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="efe21-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="efe21-105">이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="efe21-106">목표</span><span class="sxs-lookup"><span data-stu-id="efe21-106">Objectives</span></span>

* <span data-ttu-id="efe21-107">Unity AR Foundation 및 ARCore XR 플러그 인을 사용하여 Android 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="efe21-108">Unity AR Foundation 및 ARKit XR 플러그 인을 사용하여 iOS 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="efe21-109">기본 제공 Unity 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="efe21-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="efe21-110">AR Foundation Camera에 대한 MRTK 구성</span><span class="sxs-lookup"><span data-stu-id="efe21-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="efe21-111">이 섹션에서는 모바일 디바이스에 배포하기 위해 MRTK를 구성하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="efe21-112">Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="efe21-113">그런 다음, Inspector(인스펙터) 창에서 **Camera** 탭을 선택하고 카메라 프로필을 복제한 다음, 적절한 이름(예: **AzureSpatialAnchors_ARCameraProfile**)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![새로 만든 ARCameraProfile이 선택된 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="efe21-115">MRTK 프로필을 복제하는 방법은 [Mixed Reality Toolkit 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efe21-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="efe21-116">검사기 창에서 **카메라** 탭을 선택한 상태에서 **카메라 설정 공급자** 를 확장하고 "-"를 클릭하여 **Windows Mixed Reality 카메라 설정** 또는 **XR SDK Windows Mixed Reality 카메라 설정** 을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="efe21-117">새 데이터 공급자가 추가된 Unity ARCameraProfile</span><span class="sxs-lookup"><span data-stu-id="efe21-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="efe21-118">**+ 카메라 설정 공급자 추가** 단추를 클릭한 다음 새로 추가된 **새 데이터 공급자** 를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Android에 대해 추가된 AR 카메라](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="efe21-120">**유형** 드롭다운을 사용하여 유형을 **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![데이터 공급자 유형 선택 경로가 있는 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="efe21-122">메뉴 항목을 호출하여 MRTK UnityAR 스크립팅 정의를 업데이트합니다. **Mixed Reality** > **Toolkit** > **유틸리티** > **UnityAR** > 스크립팅 정의 업데이트</span><span class="sxs-lookup"><span data-stu-id="efe21-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="efe21-123">Android 디바이스에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="efe21-123">Building your application to your Android device</span></span>

<span data-ttu-id="efe21-124">이 섹션에서는 프로젝트를 구성하고 빌드하여 Android 디바이스에 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="efe21-125">Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 연 다음, 플랫폼을 Android로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Android 플랫폼이 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="efe21-127">빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efe21-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="efe21-128">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-128">Close the Build Settings window.</span></span>

<span data-ttu-id="efe21-129">Unity 메뉴에서 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity MRTK Project Configurator 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="efe21-131">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Vulkan** 을 선택하고 **"-"** 기호를 클릭하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Vulcan이 선택된 Unity Other Settings](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="efe21-133">빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="efe21-134">그런 다음, USB 케이블을 사용하여 Android 디바이스를 컴퓨터에 연결하고 **Run Device**(디바이스 실행) 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![장면이 추가되고 Run Device가 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="efe21-136">Run Device(디바이스 실행) 드롭다운 목록에 디바이스가 보이지 않으면 드롭다운 목록 옆에 있는 새로 고침 단추를 눌러야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="efe21-137">빌드 설정 창에서 **빌드 및 실행** 단추를 클릭하여 Build Android(Android 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="efe21-138">빌드를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택한 다음, apk에 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정하고 **저장** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Save 프롬프트 창이 있는 Unity Build Settings 창 Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="efe21-140">Android SDK, NDK 및 JDK 모듈과 관련된 Unity 콘솔 창에 오류가 발생하면 Unity Hub를 열고 Android 빌드 지원 모듈과 관련된 Android 빌드 지원 모듈을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="efe21-141">빌드 프로세스가 완료되면 앱이 Android 디바이스에 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="efe21-142">iOS 디바이스에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="efe21-142">Building your application to your iOS device</span></span>

<span data-ttu-id="efe21-143">이 섹션에서는 프로젝트를 구성하고 빌드하여 iOS 디바이스에 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="efe21-144">Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 열고 플랫폼을 iOS로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![iOS가 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="efe21-146">빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efe21-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="efe21-147">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-147">Close the Build Settings window.</span></span>

<span data-ttu-id="efe21-148">Unity 메뉴에서 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity MRTK Project Configurator 창 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="efe21-150">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Strip Engine Code**(엔진 코드 스트립) 확인란 선택을 취소하여 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![스트립 엔진 코드가 비활성화된 Unity Other Settings](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="efe21-152">플레이어 설정 창을 닫고 **빌드** 설정 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="efe21-153">빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![장면이 추가된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="efe21-155">빌드 설정 창에서 **빌드** 단추를 클릭하여 Build iOS(iOS 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="efe21-156">Xcode 프로젝트를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어서 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정한 다음, **폴더 선택** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![저장 프롬프트 창이 있는 Unity Build Settings 창 iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="efe21-158">빌드 프로세스가 완료되면 [Xcode 프로젝트 내보내기](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) 지침에 따라 Xcode 프로젝트를 iOS 디바이스에 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="efe21-159">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-159">Congratulations</span></span>

<span data-ttu-id="efe21-160">이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="efe21-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
