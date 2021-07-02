---
title: Oculus Quest에 배포
description: MRTK의 Oculus 퀘스트를 구성 하는 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, oculus 퀘스트
ms.openlocfilehash: d910f26374b21be26377bd40b9be0d45872e007a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177454"
---
# <a name="deploying-to-oculus-quest"></a><span data-ttu-id="b1282-104">Oculus Quest에 배포</span><span class="sxs-lookup"><span data-stu-id="b1282-104">Deploying to Oculus Quest</span></span>

<span data-ttu-id="b1282-105">[Oculus 퀘스트](https://www.oculus.com/quest/) 를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="b1282-106">Oculus 퀘스트에 대 한 MRTK의 지원은 두 개의 다른 원본, 즉 Unity의 XR SDK 파이프라인 및 Oculus Integration Unity 패키지를 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="b1282-107">**oculus xrsdk Data Provider** 는 두 소스를 사용 하도록 설정 하 고, oculus 퀘스트에서 mrtk를 배포 하는 데 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="b1282-108">[UNITY XR SDK 파이프라인](https://docs.unity3d.com/Manual/XR.html) 을 사용 하면 Oculus Quest로 헤드 추적 및 헤드 추적을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="b1282-109">이 파이프라인은 Unity 2019.3 이상에서 XR 응용 프로그램을 개발 하는 데 사용할 수 있는 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="b1282-110">이 파이프라인을 사용 하려면 **Unity 2019.3 이상 버전** 을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="b1282-111">이는 MRTK 응용 프로그램을 Oculus 퀘스트에 배포 하는 **데 필요** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="b1282-112">[Oculus 통합 Unity 패키지](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 를 사용 하면 Oculus 퀘스트를 통해 **손으로 추적할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="b1282-113">이 데이터 공급자는 Unity의 **XR SDK 파이프라인** 또는 **레거시 XR 파이프라인** 을 사용 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="b1282-114">Oculus 퀘스트에 대 한 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b1282-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="b1282-115">[다음 단계](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 를 수행 하 여 프로젝트를 Oculus 퀘스트에 배포할 준비가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="b1282-116">장치에서 [개발자 모드](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 를 사용 하도록 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="b1282-117">Oculus ADB 드라이버를 설치 하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="b1282-118">Oculus 퀘스트에 대 한 XR SDK 파이프라인 설정</span><span class="sxs-lookup"><span data-stu-id="b1282-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="b1282-119">**oculus XR 플러그 인** 이 창에 설치 되어 있는지 확인 합니다 **(> 패키지 관리자**</span><span class="sxs-lookup"><span data-stu-id="b1282-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 플러그 인 패키지](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="b1282-121">**편집-> Project 설정 > XR 플러그 인 관리--> 플러그** 인 공급자를 사용 하 여 oculus 플러그 인 공급자가 프로젝트에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 플러그 인 공급자](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="b1282-123">수동 추적을 사용 하도록 Oculus 통합 Unity 패키지 설정</span><span class="sxs-lookup"><span data-stu-id="b1282-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="b1282-124">Unity Asset Store에서 [Oculus 통합](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 을 다운로드 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="b1282-125">작동 하도록 테스트 된 최신 버전은 20.0.0입니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="b1282-126">이 [보관 파일](https://developer.oculus.com/downloads/package/unity-integration-archive/)에서 이전 버전을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="b1282-127">> 유틸리티를 Toolkit 혼합 현실로 이동 하 여 oculus Integration Unity 모듈을 통합 > > 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="b1282-128">이렇게 하면 해당 asmdefs가 작동 하는 데 필요한 정의 및 참조를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="b1282-129">또한 csc 파일을 업데이트 하 여 Oculus 통합 자산에 의해 생성 된 사용 되지 않는 경고를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="b1282-130">MRTK 리포지토리에는 경고를 오류로 변환 하는 csc 파일이 포함 되어 있습니다 .이 변환은 MRTK-Quest 구성 프로세스를 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus 통합 Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="b1282-132">가져온 Oculus 폴더 (자산/Oculus에서 찾을 수 있어야 함)에서 OculusProjectConfig 라는 스크립트 가능한 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="b1282-133">해당 구성 파일에서 수동 Trackingsupport를 "컨트롤러 및 손을"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus 통합 컨트롤러 및 손](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="b1282-135">장면 설정</span><span class="sxs-lookup"><span data-stu-id="b1282-135">Setting up the scene</span></span>

1. <span data-ttu-id="b1282-136">새 Unity 장면을 만들거나 HandInteractionExamples와 같은 기존 장면을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="b1282-137">**Mixed Reality** 로 이동 하 여 장면에 mrtk를 추가 Toolkit  >  **장면에 추가 하 고 구성** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="b1282-138">Oculus XR SDK 사용 Data Provider</span><span class="sxs-lookup"><span data-stu-id="b1282-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="b1282-139">**Oculus XR SDK** 를 사용 하도록 프로필을 구성 Data Provider</span><span class="sxs-lookup"><span data-stu-id="b1282-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="b1282-140">구성 프로필을 수정할 예정인 경우</span><span class="sxs-lookup"><span data-stu-id="b1282-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="b1282-141">모든 Unity의 XR 파이프라인에서 구성 된 기본 MRTK 프로필을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="b1282-142">이전 DefaultXRSDKConfigurationProfile은 이제 사용 되지 않는 것으로 레이블이 지정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="b1282-143">빌드로 이동 하 여 [프로젝트를 배포 해 보세요](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="b1282-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="b1282-144">그렇지 않으면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="b1282-145">계층에서 MixedRealityToolkit game 개체를 선택 하 고 **복사 및 사용자 지정** 을 선택 하 여 기본 혼합 현실 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="b1282-147">**입력** 구성 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-147">Select the **Input** Configuration Profile.</span></span>

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="b1282-149">입력 시스템 프로필에서 **복제** 를 선택 하 여 수정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="b1282-151">**입력 데이터 공급자** 섹션을 열고 맨 위에 있는 **Data Provider 추가** 를 선택 하면 새 데이터 공급자가 목록의 끝에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b1282-152">새 데이터 공급자를 열고 **형식을** Toolkit MixedReality로 설정 합니다. **XRSDK. OculusXRSDKDeviceManager >** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="b1282-154">**Oculus XR SDK** 를 사용 하도록 프로필을 구성 Data Provider</span><span class="sxs-lookup"><span data-stu-id="b1282-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="b1282-155">구성 프로필을 수정할 예정인 경우</span><span class="sxs-lookup"><span data-stu-id="b1282-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="b1282-156">프로필을 DefaultXRSDKConfigurationProfile로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="b1282-157">빌드로 이동 하 여 [프로젝트를 배포 해 보세요](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="b1282-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="b1282-158">그렇지 않으면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="b1282-159">계층에서 MixedRealityToolkit game 개체를 선택 하 고 **복사 및 사용자 지정** 을 선택 하 여 기본 혼합 현실 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="b1282-161">**입력** 구성 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-161">Select the **Input** Configuration Profile.</span></span>

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="b1282-163">입력 시스템 프로필에서 **복제** 를 선택 하 여 수정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="b1282-165">**입력 데이터 공급자** 섹션을 열고 맨 위에 있는 **Data Provider 추가** 를 선택 하면 새 데이터 공급자가 목록의 끝에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b1282-166">새 데이터 공급자를 열고 **형식을** Toolkit MixedReality로 설정 합니다. **XRSDK. OculusXRSDKDeviceManager >** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="b1282-168">oculus XR SDK Data Provider에는 OVR camera rig와 OVR 손을 사용 하 여 프로젝트를 자동으로 구성 하는 OVR 카메라 rig Prefab 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="b1282-169">장면에 OVR 카메라 Rig를 수동으로 추가 하려면 설정 및 입력을 수동으로 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="b1282-170">프로젝트를 빌드하고 배포 하 여 Oculus 퀘스트</span><span class="sxs-lookup"><span data-stu-id="b1282-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="b1282-171">USB 3.0-> USB C 케이블을 통해 Oculus 퀘스트를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="b1282-172">**파일 > 빌드** 로 이동 설정</span><span class="sxs-lookup"><span data-stu-id="b1282-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="b1282-173">**Android** 로 배포 변경</span><span class="sxs-lookup"><span data-stu-id="b1282-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="b1282-174">Oculus 퀘스트를 해당 실행 장치로 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![장치 실행 장치](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="b1282-176">빌드 및 실행을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-176">Select Build and Run</span></span>
    - <span data-ttu-id="b1282-177">*빌드를* 선택 하 고 처음 실행 하는 경우 다음과 같은 빌드 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="b1282-178">빌드를 선택 하 *고 다시 실행할* 때 성공적으로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![예상 빌드 오류가 발생 했습니다.](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="b1282-180">퀘스트 내에서 _USB 디버깅 프롬프트 허용_ 을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="b1282-181">Oculus 퀘스트 내에서 장면 보기</span><span class="sxs-lookup"><span data-stu-id="b1282-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="b1282-182">Project에서 Oculus 통합 제거</span><span class="sxs-lookup"><span data-stu-id="b1282-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="b1282-183">혼합 된 현실로 이동 하 여 Toolkit > > oculus Integration Unity 모듈을 분리 합니다. ![ asmdef를 분리 합니다.](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="b1282-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="b1282-184">Unity를 MixedReality에서 참조로 새로 고칠 수 있습니다. Toolkit. 공급자. asmdef 및 기타 파일은이 단계에서 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="b1282-185">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="b1282-185">Close Unity</span></span>
1. <span data-ttu-id="b1282-186">열려 있는 경우 Visual Studio를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="b1282-187">파일 탐색기를 열고 MRTK Unity 프로젝트의 루트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="b1282-188">UnityProjectName/Library 디렉터리를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="b1282-189">UnityProjectName/자산/Oculus 디렉터리를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="b1282-190">UnityProjectName/asset/Oculus. 메타 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="b1282-191">Unity 다시 열기</span><span class="sxs-lookup"><span data-stu-id="b1282-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="b1282-192">일반 오류</span><span class="sxs-lookup"><span data-stu-id="b1282-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="b1282-193">Unity에서 Quest를 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="b1282-194">Android 경로가 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1282-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="b1282-195">문제가 계속 발생 하면이 [가이드](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools) 를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b1282-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="b1282-196">**Android > 외부 도구 > > 기본 설정 편집**</span><span class="sxs-lookup"><span data-stu-id="b1282-196">**Edit > Preferences > External Tools > Android**</span></span>

![Android 도구 구성](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
