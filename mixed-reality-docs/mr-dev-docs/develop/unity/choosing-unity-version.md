---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741925"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="af6a8-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="af6a8-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="af6a8-105">현재 혼합 현실 개발용으로 **최신 Mixed Reality OpenXR 플러그 인 Unity 2020.3 LTS를 설치 하는 것이 좋습니다** . 또한 다른 Unity 구성으로 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="af6a8-106">Unity 2020.3 LTS (권장)</span><span class="sxs-lookup"><span data-stu-id="af6a8-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="af6a8-107">Microsoft의 최신 권장 Unity 구성-HoloLens 2 및 Windows Mixed Reality 개발은 **최신 Mixed Reality OpenXR 플러그 인 unity 2020.3 LTS** 입니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af6a8-108">Unity 2020은 HoloLens (첫 번째 gen)를 대상으로 지정 하는 기능을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-108">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="af6a8-109">이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하는 **[unity 2019 lts](#unity-20194-lts)** 에서 중부 2022를 통해 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-109">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="af6a8-110">Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-110">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="af6a8-111">그러면 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿 범위에 도달할 때 적중 테스트 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-111">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="af6a8-112">Unity를 설치하고 관리할 때 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-112">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="af6a8-113">설치 된 경우 Unity 허브를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-113">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="af6a8-114">**설치** 탭을 선택 하 고 **추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-114">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="af6a8-115">Unity 2020.3 LTS를 선택 하 고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-115">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity 허브 설치할 새 버전](images/unity-hub-img-01.png)

3. <span data-ttu-id="af6a8-117">**' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-117">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="af6a8-118">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="af6a8-118">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="af6a8-119">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="af6a8-119">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="af6a8-121">이러한 옵션 없이 Unity를 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 unity를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-121">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="af6a8-123">OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="af6a8-123">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="af6a8-124">모든 새 프로젝트에 OpenXR를 사용 하는 것이 좋지만 Unity 2020.3 LTS는 **[WINDOWS XR 플러그 인](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)** 도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the **[Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span></span> <span data-ttu-id="af6a8-125">홀로그램 안정성 및 HoloLens 2의 기타 기능에 영향을 주는 알려진 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-125">Known issues that affect hologram stability and other features on HoloLens 2 include:</span></span>
>
> * <span data-ttu-id="af6a8-126">유니버설 Windows 플랫폼 빌드 대상을 사용 하는 Holographic app remoting 응용 프로그램이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-126">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
> * <span data-ttu-id="af6a8-127">Unity graphics jobs 시스템은 HoloLens 프로젝트와 호환 되지 않는 경우에도 기본적으로 켜져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-127">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="af6a8-128">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="af6a8-128">Unity 2019.4 LTS</span></span>

<span data-ttu-id="af6a8-129">Unity 2019을 사용 해야 하는 경우 **unity 2019 LTS와 레거시 기본 제공 XR** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-129">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="af6a8-130">Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="af6a8-130">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af6a8-131">레거시 기본 제공 XR 설정</span><span class="sxs-lookup"><span data-stu-id="af6a8-131">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="af6a8-132">Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-132">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="af6a8-133">Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-133">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="af6a8-134">Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-134">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="af6a8-135">HoloLens 용 앱을 개발 하는 경우 (첫 번째 gen), 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 LTS를 2022 통해 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-135">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="af6a8-136">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="af6a8-136">Unity 2021.1</span></span>

<span data-ttu-id="af6a8-137">초기 **Unity 2021.1** 빌드를 시도 하는 경우 Windows XR 플러그 인이 더 이상 사용 되지 않으므로 **OpenXR 플러그 인** 으로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-137">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="af6a8-138">Unity 2021.2부터 Windows XR 플러그 인이 더 이상 지원 되지 않으므로 OpenXR 플러그 인은 혼합 현실 개발의 유일한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-138">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="af6a8-139">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="af6a8-139">Unity 2018.4 LTS</span></span>

<span data-ttu-id="af6a8-140">Unity 2018.4 LTS를 사용 하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2 년 동안 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-140">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="af6a8-141">Unity 2018 LTS는 2021의 스프링에서 서비스 종료에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="af6a8-141">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
