---
title: Unity 용 Mixed Reality OpenXR 플러그 인 사용
description: Unity 프로젝트용 Mixed Reality OpenXR 플러그 인을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 61474ecf749b16c8c78352d9f28a6482bfa3334c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105549923"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="54627-104">Unity 용 Mixed Reality OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="54627-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="54627-105">Unity 버전 2020.2부터 Microsoft의 Mixed Reality OpenXR 플러그 인 패키지는 UPM (Unity 패키지 관리자)를 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54627-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="54627-106">Prerequisites</span></span>

* <span data-ttu-id="54627-107">Unity 2020.2 이상</span><span class="sxs-lookup"><span data-stu-id="54627-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="54627-108">Unity OpenXR plugin 0.1.4 이상</span><span class="sxs-lookup"><span data-stu-id="54627-108">Unity OpenXR plugin 0.1.4 or later</span></span>
* <span data-ttu-id="54627-109">Visual Studio 2019 이상</span><span class="sxs-lookup"><span data-stu-id="54627-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="54627-110">HoloLens 2 앱 용 Unity에서 **UWP** 플랫폼 지원 설치</span><span class="sxs-lookup"><span data-stu-id="54627-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="54627-111">Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="54627-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="54627-112">그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="54627-113">혼합 현실 기능 도구를 사용 하 여 OpenXR 설치</span><span class="sxs-lookup"><span data-stu-id="54627-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="54627-114">새 Mixed Reality 기능 도구 응용 프로그램을 사용 하 여 OpenXR 플러그 인을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="54627-115">[설치 및 사용 지침](welcome-to-mr-feature-tool.md) 을 따르고 Mixed reality Toolkit 범주의 **Mixed Reality OpenXR 플러그 인** 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Open xr 플러그 인이 강조 표시 된 혼합 현실 기능 도구 패키지 창](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="54627-117">OpenXR에 대 한 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="54627-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="54627-118">OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="54627-119">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="54627-120">설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="54627-121">**INITIALIZE XR On Startup** and **OpenXR (미리 보기)** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="54627-122">HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="54627-124">**OpenXR 플러그 인 (미리 보기)** 옆에 빨간색 경고 아이콘이 표시 되는 경우 계속 하기 전에 아이콘을 클릭 하 고 **모두 수정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="54627-125">Unity 편집기를 다시 시작 해야 변경 내용이 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

<span data-ttu-id="54627-127">이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="54627-128">OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="54627-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="54627-129">Optimization</span></span>

<span data-ttu-id="54627-130">HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="54627-132">Unity 샘플 장면을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="54627-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="54627-133">하나 이상의 예제를 활용 하려면 **패키지 관리자** 에서 [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) 를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![AR가 강조 표시 된 unity 편집기에서 open Unity 패키지 관리자의 스크린샷](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="54627-135">HoloLens 2 샘플</span><span class="sxs-lookup"><span data-stu-id="54627-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="54627-136">Unity 편집기에서 **창 > 패키지 관리자** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="54627-137">패키지 목록에서 **Mixed Reality OpenXR 플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="54627-138">**샘플 목록에서** 샘플을 찾고 **가져오기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity 편집기에서 open Reality OpenXR 플러그 인을 선택 하 고 샘플 가져오기 단추가 강조 표시 된 Unity 패키지 관리자의 스크린샷](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="54627-140">패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="54627-141">가져온 샘플을 업데이트 하면 샘플 및 연결 된 자산에 대 한 모든 변경 내용이 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="54627-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="54627-142">OpenXR 지원과 함께 MRTK 사용</span><span class="sxs-lookup"><span data-stu-id="54627-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="54627-143">MRTK-Unity 2.5.3 릴리스부터 혼합 현실 OpenXR 플러그 인을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-143">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="54627-144">혼합 현실 [기능 도구](welcome-to-mr-feature-tool.md) 를 다시 열어 혼합 현실 도구 키트 (아직 없는 경우)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="54627-145">OpenXR 지원은 **Foundation** 패키지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-145">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="54627-146">검사기에서 MixedReality Toolkit 구성 요소 스크립트로 이동 하 고 **Defaultopenxrconfigurationprofile** 프로필로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-146">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![검사기의 Mixed Reality Toolkit 구성 요소에서 MRTK 구성 전환 스크린샷](images/openxr-img-11.png)

    1. <span data-ttu-id="54627-148">[OpenXR로 마이그레이션하](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)는 방법에 대 한 자세한 내용은 MRTK 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54627-148">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="54627-149">이전 버전의 MRTK에서 업그레이드 하는 경우 asset **/MixedRealityToolkit/link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-149">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="54627-150">이 줄은 MRTK 2.5.4 이상으로 시작한 경우 기본적으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54627-150">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="54627-151">다음 단계</span><span class="sxs-lookup"><span data-stu-id="54627-151">Next steps</span></span>

<span data-ttu-id="54627-152">이제 OpenXR에 대해 프로젝트를 구성 하 고 샘플에 액세스할 수 있으므로, OpenXR 플러그 인에서 현재 지원 되는 [기능](openxr-supported-features.md) 을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="54627-152">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="54627-153">피드백이 있나요?</span><span class="sxs-lookup"><span data-stu-id="54627-153">Have Feedback?</span></span>

<span data-ttu-id="54627-154">OpenXR는 여전히 실험적 이므로 피드백을 제공 하는 데 도움이 되도록 피드백을 보내 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="54627-154">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="54627-155">[](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** 및 **HoloLens 2** 또는 **Windows Mixed Reality** 를 사용 하 여 포럼 게시물에 태그를 지정 하 여 Unity 포럼에서이를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54627-155">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="54627-156">참조</span><span class="sxs-lookup"><span data-stu-id="54627-156">See also</span></span>

* [<span data-ttu-id="54627-157">MRTK를 사용하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="54627-157">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="54627-158">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="54627-158">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="54627-159">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="54627-159">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)