---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938142"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="8ff24-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="8ff24-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="8ff24-105">현재 **Unity 2019.4 LTS를 설치 하 고 혼합 현실 개발용으로 레거시 기본 제공 XR를 사용 하는 것이 좋습니다** . 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="8ff24-106">Unity 2019.4 LTS (권장)</span><span class="sxs-lookup"><span data-stu-id="8ff24-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="8ff24-107">Microsoft의 최신 권장 Unity 구성-HoloLens 2 및 Windows Mixed Reality 개발은 **레거시 기본 제공 XR 지원을 사용 하는 Unity 2019.4 LTS** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="8ff24-108">Unity를 설치 하 고 관리 하는 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 허브]</a>를 통하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="8ff24-109">설치 된 경우 Unity 허브를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="8ff24-110">**설치** 탭을 선택 하 고 **추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="8ff24-111">Unity 2019.4 LTS를 선택 하 고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 허브 설치할 새 버전](images/unity-hub-img-01.png)

3. <span data-ttu-id="8ff24-113">**' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="8ff24-114">**빌드 지원 유니버설 Windows 플랫폼**</span><span class="sxs-lookup"><span data-stu-id="8ff24-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="8ff24-115">**Windows 빌드 지원 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="8ff24-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="8ff24-117">이러한 옵션 없이 Unity를 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 unity를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="8ff24-119">Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ff24-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ff24-120">레거시 기본 제공 XR 설정</span><span class="sxs-lookup"><span data-stu-id="8ff24-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="8ff24-121">Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="8ff24-122">Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="8ff24-123">Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="8ff24-124">HoloLens 용 앱을 개발 하는 경우 (첫 번째 gen), 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 LTS를 2022 통해 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="8ff24-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="8ff24-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="8ff24-126">**Unity 2020.3 LTS** 를 사용 하는 경우 **windows XR 플러그 인** 을 사용 하 여 HoloLens 2 및 Windows Mixed Reality 응용 프로그램을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="8ff24-127">그러나 HoloLens 안정성 및 HoloLens 2의 기타 기능에 영향을 주는 알려진 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="8ff24-128">깊이 버퍼 전송이 최근 Unity 2020 빌드에서 재발 되어 심각한 홀로그램 불안정성이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="8ff24-129">유니버설 Windows 플랫폼 빌드 대상을 사용 하는 Holographic app remoting 응용 프로그램이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="8ff24-130">Unity graphics jobs 시스템은 HoloLens 프로젝트와 호환 되지 않는 경우에도 기본적으로 켜져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="8ff24-131">지금 Unity 2020에서 새 프로젝트를 시작 하도록 선택 하는 경우 앱을 출시 하기 전에 업데이트 된 Unity 빌드 및 Windows XR 플러그 인 빌드에 대 한 향후 몇 개월을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="8ff24-132">이렇게 하면 사용자가 홀로그램의 적절 한 안정성을 경험 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ff24-133">Windows XR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="8ff24-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="8ff24-134">OpenXR 사용</span><span class="sxs-lookup"><span data-stu-id="8ff24-134">Using OpenXR</span></span>

<span data-ttu-id="8ff24-135">Unity 2020.3 LTS는 **혼합 현실 OpenXR** 플러그 인에 대 한 공개 미리 보기도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="8ff24-136">Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="8ff24-137">그러면 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿 범위에 도달할 때 적중 테스트 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="8ff24-138">올해 후반에 OpenXR 플러그 인을 사용 하는 **unity 2020.3 LTS** 는 권장 unity 구성이 되며 unity의 이후 HoloLens 2 기능은이 플러그 인을 통해서만 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="8ff24-139">지금은 여기에서 프로젝트를 시작할 수 있습니다. 그러나 프로젝트가 HoloLens 2를 대상으로 하는 경우 현재 Unity 2020 홀로그램 안정성 및 위에 나열 된 기타 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="8ff24-140">앱을 출시 하기 전에 업데이트 된 Unity 빌드 및 OpenXR plugin 빌드에 대 한 향후 몇 개월 후에 다시 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ff24-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="8ff24-141">이렇게 하면 사용자가 홀로그램의 적절 한 안정성을 경험 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ff24-142">OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="8ff24-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="8ff24-143">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="8ff24-143">Unity 2021.1</span></span>

<span data-ttu-id="8ff24-144">초기 **Unity 2021.1** 빌드를 시도 하는 경우 Windows XR 플러그 인이 더 이상 사용 되지 않으므로 **OpenXR 플러그 인** 으로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="8ff24-145">Unity 2021.2부터 Windows XR 플러그 인이 더 이상 지원 되지 않으므로 OpenXR 플러그 인은 혼합 현실 개발의 유일한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="8ff24-146">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="8ff24-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="8ff24-147">Unity 2018.4 LTS를 사용 하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2 년 동안 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="8ff24-148">Unity 2018 LTS는 2021의 스프링에서 서비스 종료에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff24-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
