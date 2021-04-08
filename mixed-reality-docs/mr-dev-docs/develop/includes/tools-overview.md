---
ms.openlocfilehash: d7e248788d4c4976acbb9ff23177d354894f57dd
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105958191"
---
# <a name="unity"></a>[<span data-ttu-id="84986-101">Unity</span><span class="sxs-lookup"><span data-stu-id="84986-101">Unity</span></span>](#tab/unity)

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a><span data-ttu-id="84986-103">1. 권장 Unity 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="84986-103">1. Download the recommended Unity version</span></span> 

<span data-ttu-id="84986-104">Mixed Reality 개발에 권장되는 현재 버전은 **Unity 2019.4 LTS(장기 지원)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-104">The current recommended version for Mixed Reality development is **Unity 2019.4 LTS (Long Term Support)**.</span></span> <span data-ttu-id="84986-105">Unity를 설치하고 관리할 때 가장 좋은 방법은 **Unity Hub** 를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-105">The best way to install and manage Unity is through the **Unity Hub**.</span></span> 

> [!NOTE]
>  <span data-ttu-id="84986-106">Unity 2020 LTS를 사용 중인 경우 HoloLens 2 개발에 Mixed Reality 지원이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-106">If you’re using Unity 2020 LTS, Mixed Reality support is available for HoloLens 2 development.</span></span> <span data-ttu-id="84986-107">그러나 현재 몇 가지 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-107">However, there are currently some known issues.</span></span> <span data-ttu-id="84986-108">이 버전은 올해 후반에 권장 Unity 버전이 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-108">This will become the recommended Unity version later this year.</span></span> 

<span data-ttu-id="84986-109">다양한 Unity 엔진과 XR 플러그 인 버전에서 사용할 수 있는 Mixed Reality 지원을 알아보려면 [Unity 버전 및 XR 플러그 인 선택](../unity/choosing-unity-version.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-109">See [Choosing a Unity version and XR plugin](../unity/choosing-unity-version.md) to learn what Mixed Reality support is available in different Unity engine and XR plugin versions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-110">Unity Hub 다운로드</span><span class="sxs-lookup"><span data-stu-id="84986-110">Download Unity Hub</span></span>](https://unity3d.com/get-unity/download)

<span data-ttu-id="84986-111">Unity를 설치할 때는 **'Platforms'('플랫폼')** 아래에서 다음 구성 요소를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-111">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>
* <span data-ttu-id="84986-112">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="84986-112">**Universal Windows Platform Build Support**</span></span> 
* <span data-ttu-id="84986-113">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="84986-113">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../../develop/images/Unity_Install_Option_UWP.png)

<span data-ttu-id="84986-115">이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'Add Modules'('모듈 추가')** 메뉴를 통해 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-115">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

![Unity Windows 빌드 지원 옵션](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="84986-117">2. Mixed Reality Feature Tool 설치</span><span class="sxs-lookup"><span data-stu-id="84986-117">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="84986-118">[Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)은 개발자가 혼합형 현실 기능 패키지를 검색하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-118">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="84986-119">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-119">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="84986-120">원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-120">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="84986-121">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="84986-121">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="84986-123">MRTK([Mixed Reality Toolkit](../unity/mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-123">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="84986-124">[설치 및 사용 지침](../unity/welcome-to-mr-feature-tool.md#system-requirements)을 따르고 **Mixed Reality Toolkit Foundation** 패키지를 선택하여 Mixed Reality Toolkit 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-124">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="84986-125">큐레이트된 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 또는 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 개발 경험의 시작 섹션을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-125">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="84986-126">HoloLens용 Unity 개발 경험을 이미 따르고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unity/tutorials/mr-learning-base-01.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-126">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84986-127">설치 지침은 MRTK 및 Unity 릴리스의 안정적인 최신 조합인 **MRTK 2.6.1** 및 **Unity 2019.4 LTS** 를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-127">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="84986-128">Unity에 MRTK를 사용하지 않으려면 [모든 상호 작용과 동작을 직접 스크립팅](../unity/configure-unity-project.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-128">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="84986-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="84986-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="84986-130">**Mixed Reality Toolkit-Unity(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="84986-130">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="84986-131">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="84986-131">Other tools [optional]</span></span>
* <span data-ttu-id="84986-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="84986-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="84986-134">3. Mixed Reality 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="84986-134">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="84986-135">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-135">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="84986-136">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-136">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="84986-137">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-137">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="84986-138">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-138">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="84986-139">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-139">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="84986-140">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="84986-140">For HoloLens development</span></span>

<span data-ttu-id="84986-141">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-141">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="84986-142">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-142">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="84986-143">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-143">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="84986-144">HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-144">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="84986-145">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-145">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="84986-146">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="84986-146">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="84986-147">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-147">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="84986-148">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-148">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="84986-149">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-149">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="84986-150">하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-150">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="84986-151">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-151">Possible solutions include:</span></span>

* <span data-ttu-id="84986-152">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-152">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="84986-153">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-153">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="84986-154">이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-154">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="84986-155">[ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="84986-155">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="84986-156">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-156">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="84986-157">USB를 통해 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-157">I can't deploy over USB</span></span>

<span data-ttu-id="84986-158">USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="84986-158">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="84986-159">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="84986-159">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="84986-160">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-160">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="84986-161">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="84986-161">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="84986-162">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-162">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="84986-163">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-163">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="84986-164">최소값</span><span class="sxs-lookup"><span data-stu-id="84986-164">Minimum</span></span></th><th> <span data-ttu-id="84986-165">권장</span><span class="sxs-lookup"><span data-stu-id="84986-165">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="84986-166">프로세서</span><span class="sxs-lookup"><span data-stu-id="84986-166">Processor</span></span></td><td> <span data-ttu-id="84986-167"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="84986-167"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="84986-168"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="84986-168"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-169">GPU</span><span class="sxs-lookup"><span data-stu-id="84986-169">GPU</span></span></td><td> <span data-ttu-id="84986-170"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-170"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="84986-171"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-171"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-172">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="84986-172">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="84986-173">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="84986-173">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-174">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="84986-174">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="84986-175">15W 이상</span><span class="sxs-lookup"><span data-stu-id="84986-175">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-176">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="84986-176">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-177">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="84986-177">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-178">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="84986-178">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="84986-179">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="84986-179">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-180">메모리</span><span class="sxs-lookup"><span data-stu-id="84986-180">Memory</span></span></td><td> <span data-ttu-id="84986-181">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-181">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="84986-182">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-182">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-183">스토리지</span><span class="sxs-lookup"><span data-stu-id="84986-183">Storage</span></span></td><td colspan="2"> <span data-ttu-id="84986-184">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="84986-184">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-185">USB 포트</span><span class="sxs-lookup"><span data-stu-id="84986-185">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-186">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="84986-186">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-187">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="84986-187">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="84986-188">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="84986-188">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="84986-189">Unity를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unity 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-189">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-190">HoloLens용 Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="84986-190">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-191">VR용 Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="84986-191">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="84986-192">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="84986-192">Next Development Checkpoint</span></span>

<span data-ttu-id="84986-193">앞에서 설명한 HoloLens용 Unity 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-193">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-194">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="84986-194">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="84986-195">VR용 Unity 경험을 따르고 있는 경우, 다음 작업은 프로젝트를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-195">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-196">WMR용 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="84986-196">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="84986-197">언제든지 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 및 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)용 Unity 개발 검사점으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-197">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="84986-198">Unreal</span><span class="sxs-lookup"><span data-stu-id="84986-198">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="84986-200">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="84986-200">1. Download the latest version</span></span>

<span data-ttu-id="84986-201">HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-201">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="84986-202">Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-202">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="84986-203">**대상 플랫폼** 에서 **HoloLens 2** 를 선택하고 **적용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-203">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="84986-204">![Unreal 설치 옵션 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="84986-204">![Unreal Install Option HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="84986-205">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="84986-205">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="84986-207">MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-207">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="84986-208">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-208">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="84986-209">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-209">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="84986-210">설치의 경우 큐레이션된 [Unreal 개발 경험](../unreal/unreal-development-overview.md)의 [시작 섹션](../unreal/unreal-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-210">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="84986-211">Unreal 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unreal/tutorials/unreal-uxt-ch1.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-211">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="84986-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 로고 이미지](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="84986-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="84986-213">**Mixed Reality Toolkit-Unreal(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="84986-213">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="84986-214">Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-214">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="84986-215">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="84986-215">Other tools [optional]</span></span>
* <span data-ttu-id="84986-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="84986-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="84986-218">3. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="84986-218">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="84986-219">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-219">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="84986-220">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-220">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="84986-221">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-221">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="84986-222">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-222">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="84986-223">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-223">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="84986-224">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="84986-224">For HoloLens development</span></span>

<span data-ttu-id="84986-225">HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-225">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="84986-226">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-226">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="84986-227">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-227">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="84986-228">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-228">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="84986-229">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="84986-229">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="84986-230">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-230">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="84986-231">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-231">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="84986-232">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-232">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="84986-233">하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-233">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="84986-234">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-234">Possible solutions include:</span></span>

* <span data-ttu-id="84986-235">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-235">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="84986-236">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-236">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="84986-237">이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-237">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="84986-238">[ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="84986-238">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="84986-239">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-239">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="84986-240">USB를 통해 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-240">I can't deploy over USB</span></span>

<span data-ttu-id="84986-241">USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unreal/tutorials/unreal-uxt-ch6.md)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="84986-241">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="84986-242">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="84986-242">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="84986-243">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-243">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="84986-244">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="84986-244">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="84986-245">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-245">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="84986-246">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-246">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="84986-247">최소값</span><span class="sxs-lookup"><span data-stu-id="84986-247">Minimum</span></span></th><th> <span data-ttu-id="84986-248">권장</span><span class="sxs-lookup"><span data-stu-id="84986-248">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="84986-249">프로세서</span><span class="sxs-lookup"><span data-stu-id="84986-249">Processor</span></span></td><td> <span data-ttu-id="84986-250"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="84986-250"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="84986-251"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="84986-251"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-252">GPU</span><span class="sxs-lookup"><span data-stu-id="84986-252">GPU</span></span></td><td> <span data-ttu-id="84986-253"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-253"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="84986-254"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-254"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-255">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="84986-255">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="84986-256">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="84986-256">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-257">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="84986-257">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="84986-258">15W 이상</span><span class="sxs-lookup"><span data-stu-id="84986-258">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-259">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="84986-259">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-260">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="84986-260">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-261">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="84986-261">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="84986-262">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="84986-262">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-263">메모리</span><span class="sxs-lookup"><span data-stu-id="84986-263">Memory</span></span></td><td> <span data-ttu-id="84986-264">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-264">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="84986-265">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-265">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-266">스토리지</span><span class="sxs-lookup"><span data-stu-id="84986-266">Storage</span></span></td><td colspan="2"> <span data-ttu-id="84986-267">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="84986-267">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-268">USB 포트</span><span class="sxs-lookup"><span data-stu-id="84986-268">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-269">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="84986-269">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-270">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="84986-270">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="84986-271">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="84986-271">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="84986-272">Unreal를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unreal 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-272">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-273">Unreal 경험 시작</span><span class="sxs-lookup"><span data-stu-id="84986-273">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="84986-274">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="84986-274">Next Development Checkpoint</span></span>

<span data-ttu-id="84986-275">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-275">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-276">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="84986-276">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="84986-277">언제든지 [Unreal 개발 검사점](../unreal/unreal-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-277">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="84986-278">네이티브(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="84986-278">Native (OpenXR)</span></span>](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

<span data-ttu-id="84986-280">네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-280">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="84986-281">개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../native/openxr-getting-started.md) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-281">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="84986-282">1. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="84986-282">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="84986-283">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-283">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="84986-284">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-284">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="84986-285">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-285">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="84986-286">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="84986-286">For HoloLens development</span></span>

<span data-ttu-id="84986-287">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-287">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="84986-288">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-288">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="84986-289">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-289">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="84986-290">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84986-290">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="84986-291">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-291">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="84986-292">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-292">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="84986-293">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="84986-293">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="84986-294">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-294">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="84986-295">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-295">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="84986-296">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-296">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="84986-297">하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-297">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="84986-298">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-298">Possible solutions include:</span></span>

* <span data-ttu-id="84986-299">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-299">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="84986-300">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-300">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="84986-301">이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-301">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="84986-302">[ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="84986-302">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="84986-303">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-303">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="84986-304">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="84986-304">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="84986-305">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="84986-305">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="84986-306">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="84986-306">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="84986-307">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="84986-307">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="84986-308">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-308">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="84986-309">최소값</span><span class="sxs-lookup"><span data-stu-id="84986-309">Minimum</span></span></th><th> <span data-ttu-id="84986-310">권장</span><span class="sxs-lookup"><span data-stu-id="84986-310">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="84986-311">프로세서</span><span class="sxs-lookup"><span data-stu-id="84986-311">Processor</span></span></td><td> <span data-ttu-id="84986-312"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="84986-312"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="84986-313"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="84986-313"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-314">GPU</span><span class="sxs-lookup"><span data-stu-id="84986-314">GPU</span></span></td><td> <span data-ttu-id="84986-315"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-315"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="84986-316"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="84986-316"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-317">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="84986-317">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="84986-318">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="84986-318">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-319">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="84986-319">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="84986-320">15W 이상</span><span class="sxs-lookup"><span data-stu-id="84986-320">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-321">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="84986-321">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-322">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="84986-322">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-323">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="84986-323">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="84986-324">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="84986-324">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-325">메모리</span><span class="sxs-lookup"><span data-stu-id="84986-325">Memory</span></span></td><td> <span data-ttu-id="84986-326">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-326">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="84986-327">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="84986-327">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-328">스토리지</span><span class="sxs-lookup"><span data-stu-id="84986-328">Storage</span></span></td><td colspan="2"> <span data-ttu-id="84986-329">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="84986-329">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-330">USB 포트</span><span class="sxs-lookup"><span data-stu-id="84986-330">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="84986-331">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="84986-331">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="84986-332">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="84986-332">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="84986-333">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="84986-333">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="84986-334">MRTK를 사용하는 네이티브 개발을 처음 접하는 경우 큐레이션된 네이티브 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-334">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-335">기본 경험 시작</span><span class="sxs-lookup"><span data-stu-id="84986-335">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="84986-336">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="84986-336">Next Development Checkpoint</span></span>

<span data-ttu-id="84986-337">앞에서 설명한 네이티브 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2에 대한 개발 환경을 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84986-337">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84986-338">HoloLens 2 설정</span><span class="sxs-lookup"><span data-stu-id="84986-338">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="84986-339">언제든지 [네이티브 개발 검사점](../native/directx-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84986-339">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>