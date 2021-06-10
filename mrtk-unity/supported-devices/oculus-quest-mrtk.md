---
title: Oculus Quest MRTK
description: MRTK에서 Oculus Quest를 구성하기 위한 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Oculus Quest,
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908390"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="92e4d-104">XR SDK 파이프라인을 사용하여 Oculus Quest에 MRTK 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="92e4d-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="92e4d-105">[Oculus Quest가](https://www.oculus.com/quest/) 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="92e4d-106">Oculus Quest에 대한 MRTK의 지원은 Unity의 XR SDK 파이프라인과 Oculus Integration Unity 패키지의 두 가지 소스를 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="92e4d-107">**Oculus XRSDK Data Provider** 두 소스를 모두 사용할 수 있으며 Oculus Quest에 MRTK를 배포하는 데 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="92e4d-108">[Unity XR SDK 파이프라인을](https://docs.unity3d.com/Manual/XR.html) 사용하면 Oculus Quest를 통해 Oculus Touch 컨트롤러 및 헤드 추적을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="92e4d-109">이 파이프라인은 Unity 2019.3 이상에서 XR 애플리케이션을 개발하기 위한 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="92e4d-110">이 파이프라인을 사용하려면 Unity **2019.3 이상** 을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="92e4d-111">이는 MRTK 애플리케이션을 Oculus Quest에 배포하는 **데 필요합니다.**</span><span class="sxs-lookup"><span data-stu-id="92e4d-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="92e4d-112">[Oculus Integration Unity 패키지를 사용하면 Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) Quest에서 **손 추적을** 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="92e4d-113">이 데이터 **공급자는** Unity의 **XR SDK 파이프라인** 또는 레거시 **XR 파이프라인 을** 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="92e4d-114">Oculus Quest에 대한 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="92e4d-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="92e4d-115">[다음 단계에](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 따라 프로젝트가 Oculus Quest에 배포할 준비가 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="92e4d-116">디바이스에서 [개발자 모드가](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 사용하도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="92e4d-117">Oculus ADB 드라이버를 설치하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="92e4d-118">Oculus Quest용 XR SDK 파이프라인 설정</span><span class="sxs-lookup"><span data-stu-id="92e4d-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="92e4d-119">**Oculus XR 플러그 인이** 창 **--> 패키지 관리자** 아래에 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 플러그 인 패키지](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="92e4d-121">**편집 --> 프로젝트 설정 --> XR 플러그 인 관리 --> 플러그 인 공급자로** 진행하여 Oculus 플러그 인 공급자가 프로젝트에 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 플러그 인 공급자](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="92e4d-123">수동 추적을 사용하도록 Oculus Integration Unity 패키지 설정</span><span class="sxs-lookup"><span data-stu-id="92e4d-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="92e4d-124">Unity 자산 저장소에서 [Oculus Integration을](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 다운로드하고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="92e4d-125">작동하도록 테스트된 최신 버전은 20.0.0입니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="92e4d-126">이전 버전은 이 [보관에서](https://developer.oculus.com/downloads/package/unity-integration-archive/)찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="92e4d-127">Mixed Reality Toolkit > Utilities > Oculus > Integration Unity Modules로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="92e4d-128">이렇게 하면 관련 Oculus Quest 코드가 작동하는 데 필요한 정의 및 참조를 사용하여 asmdefs가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="92e4d-129">또한 csc 파일을 업데이트하여 Oculus 통합 자산에서 생성된 사용되지 않는 경고를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="92e4d-130">MRTK 리포지션에는 경고를 오류로 변환하는 csc 파일이 포함되어 있습니다. 이 변환은 MRTK-Quest 구성 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="92e4d-132">가져온 Oculus 폴더(Assets/Oculus에서 찾을 수 있음)에는 OculusProjectConfig라는 스크립팅 가능한 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="92e4d-133">해당 구성 파일에서 HandTrackingSupport를 "컨트롤러 및 손"으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus 통합 컨트롤러 및 손](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="92e4d-135">장면 설정</span><span class="sxs-lookup"><span data-stu-id="92e4d-135">Setting up the scene</span></span>

1. <span data-ttu-id="92e4d-136">새 Unity 장면을 만들거나 HandInteractionExamples와 같은 기존 장면을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="92e4d-137">**Mixed Reality Toolkit** 장면에 추가 및 구성으로 이동하여 MRTK를  >  **장면에 추가합니다.**</span><span class="sxs-lookup"><span data-stu-id="92e4d-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="92e4d-138">Oculus XR SDK Data Provider 사용</span><span class="sxs-lookup"><span data-stu-id="92e4d-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="92e4d-139">**Oculus XR SDK Data Provider** 사용하도록 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="92e4d-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="92e4d-140">구성 프로필을 수정하지 않으려는 경우</span><span class="sxs-lookup"><span data-stu-id="92e4d-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="92e4d-141">Unity의 XR 파이프라인에서 모두 구성된 기본 MRTK 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="92e4d-142">이전 DefaultXRSDKConfigurationProfile은 이제 사용되지 않음 레이블이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="92e4d-143">프로젝트 [빌드 및 Oculus Quest 에 배포로](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="92e4d-144">그렇지 않으면 다음을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="92e4d-145">계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="92e4d-147">**입력** 구성 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-147">Select the **Input** Configuration Profile.</span></span>

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="92e4d-149">입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="92e4d-151">입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="92e4d-152">새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager 로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="92e4d-154">**Oculus XR SDK Data Provider** 사용하도록 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="92e4d-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="92e4d-155">구성 프로필을 수정하지 않으려는 경우</span><span class="sxs-lookup"><span data-stu-id="92e4d-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="92e4d-156">프로필을 DefaultXRSDKConfigurationProfile로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="92e4d-157">프로젝트 [빌드 및 Oculus Quest 에 배포로](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="92e4d-158">그렇지 않으면 다음을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="92e4d-159">계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="92e4d-161">**입력** 구성 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-161">Select the **Input** Configuration Profile.</span></span>

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="92e4d-163">입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="92e4d-165">입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="92e4d-166">새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager 로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="92e4d-168">Oculus XR SDK Data Provider 입력을 올바르게 라우팅하도록 OVR Camera Rig 및 OVR Hands를 사용하여 프로젝트를 자동으로 구성하는 OVR Camera Rig Prefab이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="92e4d-169">장면에 OVR Camera Manual을 수동으로 추가하려면 설정 및 입력을 수동으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="92e4d-170">프로젝트를 빌드하고 Oculus Quest에 배포</span><span class="sxs-lookup"><span data-stu-id="92e4d-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="92e4d-171">USB 3.0 -> USB C 케이블을 통해 Oculus Quest 플러그 인</span><span class="sxs-lookup"><span data-stu-id="92e4d-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="92e4d-172">파일 **> 빌드 설정으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="92e4d-173">**배포를 Android로** 변경</span><span class="sxs-lookup"><span data-stu-id="92e4d-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="92e4d-174">Oculus Quest가 해당 실행 디바이스로 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 디바이스 실행](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="92e4d-176">빌드 및 실행 선택</span><span class="sxs-lookup"><span data-stu-id="92e4d-176">Select Build and Run</span></span>
    - <span data-ttu-id="92e4d-177">빌드 *및 실행을* 처음 선택하면 다음과 같은 빌드 오류 집합이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="92e4d-178">*빌드 및 실행을* 다시 선택하면 성공적으로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 예상 빌드 오류](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="92e4d-180">Quest 내부에서 _USB 디버깅 허용_ 프롬프트를 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="92e4d-181">Oculus Quest 내의 장면 보기</span><span class="sxs-lookup"><span data-stu-id="92e4d-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="92e4d-182">프로젝트에서 Oculus 통합 제거</span><span class="sxs-lookup"><span data-stu-id="92e4d-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="92e4d-183">Mixed Reality Toolkit > Oculus > 별도의 Oculus Integration Unity 모듈  ![ Oculus Separation Asmdef로 이동합니다.](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="92e4d-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="92e4d-184">Unity를 Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef의 참조로 새로 고치도록 하고 다른 파일을 이 단계에서 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="92e4d-185">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="92e4d-185">Close Unity</span></span>
1. <span data-ttu-id="92e4d-186">Visual Studio 닫습니다(열려 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="92e4d-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="92e4d-187">파일 탐색기 열고 MRTK Unity 프로젝트의 루트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="92e4d-188">UnityProjectName/Library 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="92e4d-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="92e4d-189">UnityProjectName/Assets/Oculus 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="92e4d-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="92e4d-190">UnityProjectName/Assets/Oculus.meta 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="92e4d-191">Unity 다시 열기</span><span class="sxs-lookup"><span data-stu-id="92e4d-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="92e4d-192">일반 오류</span><span class="sxs-lookup"><span data-stu-id="92e4d-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="92e4d-193">Unity에서 인식할 수 없는 Quest</span><span class="sxs-lookup"><span data-stu-id="92e4d-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="92e4d-194">Android 경로가 제대로 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="92e4d-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="92e4d-195">문제가 계속 발생하면 이 [가이드를](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools) 따르세요.</span><span class="sxs-lookup"><span data-stu-id="92e4d-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="92e4d-196">**Android에서 외부 도구 > > > 기본 설정 편집**</span><span class="sxs-lookup"><span data-stu-id="92e4d-196">**Edit > Preferences > External Tools > Android**</span></span>

![Android 도구 구성](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
