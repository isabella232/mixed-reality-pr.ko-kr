---
title: Unity 용 Mixed Reality OpenXR 플러그 인 사용
description: Unity 프로젝트용 Mixed Reality OpenXR 플러그 인을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 05adee2d88bc90dcfb5cf8b780212c7622aff786
ms.sourcegitcommit: ce4975f584bb62075bcb66349237b77081fb982b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644920"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="e6a92-104">Unity 용 Mixed Reality OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="e6a92-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="e6a92-105">Unity 버전 2020.2부터 Microsoft의 Mixed Reality OpenXR 플러그 인 패키지는 UPM (Unity 패키지 관리자)를 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6a92-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e6a92-106">Prerequisites</span></span>

*   <span data-ttu-id="e6a92-107">Unity 2020.2 이상</span><span class="sxs-lookup"><span data-stu-id="e6a92-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="e6a92-108">Unity OpenXR plugin 0.1.1 이상</span><span class="sxs-lookup"><span data-stu-id="e6a92-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="e6a92-109">Visual Studio 2019 이상</span><span class="sxs-lookup"><span data-stu-id="e6a92-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="e6a92-110">HoloLens 2 앱 용 Unity에서 **UWP** 플랫폼 지원 설치</span><span class="sxs-lookup"><span data-stu-id="e6a92-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="e6a92-111">Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="e6a92-112">그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="e6a92-113">Mixed Reality OpenXR 플러그 인 설치</span><span class="sxs-lookup"><span data-stu-id="e6a92-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="e6a92-114">혼합 현실 OpenXR 플러그 인을 사용 하기 전에 프로젝트에서 **OpenXR 플러그** 인 및 **XR 플러그 인 관리** 패키지를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="e6a92-115">이미 설치한 경우 좋은 방법입니다!</span><span class="sxs-lookup"><span data-stu-id="e6a92-115">If you've already installed them, great!</span></span> <span data-ttu-id="e6a92-116">그렇지 않으면 Mixed Reality OpenXR 플러그 인을 설치 하면 자동으로 종속성으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="e6a92-117">Unity 편집기에서 **편집 > 프로젝트 설정 > 패키지 관리자** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="e6a92-118">범위가 지정 된 **레지스트리** 섹션을 확장 하 고, 다음 정보를 입력 하 고, **저장** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="e6a92-119">**이름을** **Microsoft Mixed Reality** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="e6a92-120">**URL** 설정 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="e6a92-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="e6a92-121">**범위** 를 mixedreality로 설정 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="e6a92-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="e6a92-122">**고급 설정** 아래에서 **미리 보기 패키지 사용** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![프로젝트 설정에서 열려 있는 Unity 패키지 관리자 창의 스크린샷](images/openxr-img-01.png)

<span data-ttu-id="e6a92-124">Unity 패키지 관리자는 *manifest.js* 이라는 매니페스트 파일을 사용 하 여 설치할 패키지와 설치할 수 있는 패키지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6a92-125">OpenXR는 Unity에서 여전히 실험적 이며 개발자 환경을 최적화 하기 위해이 프로세스는 시간이 지남에 따라 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="e6a92-126">Mixed Reality 종속성 등록</span><span class="sxs-lookup"><span data-stu-id="e6a92-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="e6a92-127">Microsoft Mixed Reality 범위 레지스트리가 매니페스트에 추가 된 후에는 OpenXR 패키지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="e6a92-128">OpenXR 패키지를 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="e6a92-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="e6a92-129">Visual Studio Code와 같은 텍스트 편집기에서 **<projectRoot> /Packages/manifest.js을** 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-129">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="e6a92-130">다음과 같이 파일 *에서 패키지/manifest.js* 의 종속성 섹션을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-130">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6a92-131">매니페스트 파일에는 여기에 표시 된 것 보다 더 많은 종속성이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-131">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="e6a92-132">이러한 항목을 삭제 하지 않고 OpenXR 종속성을 목록에 추가 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-132">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="e6a92-133">파일을 저장 하 고 Unity 편집기로 다시 전환한 후 **패키지 관리자** 를 열어 플러그 인이 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-133">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![혼합 현실 OpenXR 플러그 인이 강조 표시 된 unity 편집기에서 열리는 Unity 패키지 관리자의 스크린샷](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="e6a92-135">Unity 패키지 관리자를 사용 하 여 OpenXR 패키지를 제거 하는 경우 앞에서 설명한 단계를 사용 하 여 패키지를 다시 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-135">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="e6a92-136">OpenXR에 대 한 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="e6a92-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="e6a92-137">OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-137">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="e6a92-138">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="e6a92-139">설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="e6a92-140">**INITIALIZE XR On Startup** and **OpenXR (미리 보기)** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-140">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="e6a92-141">HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="e6a92-143">**OpenXR 플러그 인 (미리 보기)** 옆에 빨간색 경고 아이콘이 표시 되는 경우 계속 하기 전에 아이콘을 클릭 하 고 **모두 수정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-143">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="e6a92-144">Unity 편집기를 다시 시작 해야 변경 내용이 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-144">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

<span data-ttu-id="e6a92-146">이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-146">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="e6a92-147">OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-147">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="e6a92-148">Optimization</span><span class="sxs-lookup"><span data-stu-id="e6a92-148">Optimization</span></span>

<span data-ttu-id="e6a92-149">HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-149">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="e6a92-151">Unity 샘플 장면을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="e6a92-151">Try out the Unity sample scenes</span></span>

<span data-ttu-id="e6a92-152">하나 이상의 예제를 활용 하려면 **패키지 Manager** 에서 [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) 를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-152">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![AR가 강조 표시 된 unity 편집기에서 open Unity 패키지 관리자의 스크린샷](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="e6a92-154">HoloLens 2 샘플</span><span class="sxs-lookup"><span data-stu-id="e6a92-154">HoloLens 2 samples</span></span>

1. <span data-ttu-id="e6a92-155">Unity 편집기에서 **창 > 패키지 관리자** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-155">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="e6a92-156">패키지 목록에서 **Mixed Reality OpenXR 플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-156">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="e6a92-157">**샘플 목록에서** 샘플을 찾고 **가져오기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-157">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity 편집기에서 open Reality OpenXR 플러그 인을 선택 하 고 샘플 가져오기 단추가 강조 표시 된 Unity 패키지 관리자의 스크린샷](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="e6a92-159">패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-159">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="e6a92-160">가져온 샘플을 업데이트 하면 샘플 및 연결 된 자산에 대 한 모든 변경 내용이 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="e6a92-160">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e6a92-161">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e6a92-161">Next steps</span></span> 

<span data-ttu-id="e6a92-162">이제 OpenXR에 대해 프로젝트를 구성 하 고 샘플에 액세스할 수 있으므로, OpenXR 플러그 인에서 현재 지원 되는 [기능](openxr-supported-features.md) 을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6a92-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a92-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6a92-163">See also</span></span>
* [<span data-ttu-id="e6a92-164">MRTK를 사용 하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="e6a92-164">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="e6a92-165">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="e6a92-165">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="e6a92-166">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="e6a92-166">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)