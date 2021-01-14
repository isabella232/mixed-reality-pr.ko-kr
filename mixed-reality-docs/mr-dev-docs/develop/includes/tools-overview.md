---
ms.openlocfilehash: 4b9a1c20a8d885ea796c296f6a542d41e3ab58ef
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98052944"
---
# <a name="unity"></a>[<span data-ttu-id="c1840-101">Unity</span><span class="sxs-lookup"><span data-stu-id="c1840-101">Unity</span></span>](#tab/unity)

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="c1840-103">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="c1840-103">1. Download the latest version</span></span>

<span data-ttu-id="c1840-104">새 프로젝트를 시작할 때 사용하기 가장 좋은 버전은 [Unity LTS(장기 지원)](https://unity3d.com/unity/qa/lts-releases) 스트림이며, 이것을 최신 개정판으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="c1840-105">현재 추천 사항은 아래의 MRTK v2에 필요한 LTS 빌드인 **Unity 2019** 를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="c1840-106">특정 이유로 인해 다른 Unity 버전을 사용해야 하는 경우 Unity는 서로 다른 버전을 함께 설치하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="c1840-107">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1840-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="c1840-109">MRTK([Mixed Reality Toolkit](../unity/mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="c1840-110">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="c1840-111">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="c1840-112">설치의 경우 큐레이션된 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 또는 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 개발 경험의 시작 섹션을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-112">For installation, we recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="c1840-113">HoloLens용 Unity 개발 경험을 이미 따르고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unity/tutorials/mr-learning-base-01.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-113">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1840-114">설치 지침은 **MRTK 2.4.0** 및 **Unity 2019.3.15** 인 MRTK 및 Unity 릴리스의 안정적인 최신 조합을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-115">Unity에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c1840-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="c1840-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="c1840-117">**Mixed Reality Toolkit-Unity(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="c1840-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="c1840-118">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="c1840-118">Other tools [optional]</span></span>
* <span data-ttu-id="c1840-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="c1840-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="c1840-121">3. Mixed Reality 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="c1840-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="c1840-122">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="c1840-123">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="c1840-124">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-125">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="c1840-126">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="c1840-127">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="c1840-127">For HoloLens development</span></span>

<span data-ttu-id="c1840-128">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="c1840-129">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="c1840-130">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="c1840-131">HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="c1840-132">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="c1840-133">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c1840-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="c1840-134">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="c1840-135">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](https://docs.microsoft.com/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="c1840-136">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="c1840-137">하지만 [HoloLens 보안 설명서](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="c1840-138">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-138">Possible solutions include:</span></span>

* <span data-ttu-id="c1840-139">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="c1840-140">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="c1840-141">이 정책은 [프로비전 패키지](https://docs.microsoft.com/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="c1840-142">[ARC(Advanced Recovery Companion)](https://docs.microsoft.com/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="c1840-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-143">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="c1840-144">USB를 통해 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-144">I can't deploy over USB</span></span>

<span data-ttu-id="c1840-145">USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unity/tutorials/mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="c1840-146">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1840-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="c1840-147">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="c1840-148">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="c1840-149">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="c1840-150">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-150">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="c1840-151">최소값</span><span class="sxs-lookup"><span data-stu-id="c1840-151">Minimum</span></span></th><th> <span data-ttu-id="c1840-152">권장</span><span class="sxs-lookup"><span data-stu-id="c1840-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="c1840-153">프로세서</span><span class="sxs-lookup"><span data-stu-id="c1840-153">Processor</span></span></td><td> <span data-ttu-id="c1840-154"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="c1840-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="c1840-155"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="c1840-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-156">GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-156">GPU</span></span></td><td> <span data-ttu-id="c1840-157"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="c1840-158"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-159">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="c1840-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="c1840-160">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="c1840-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-161">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="c1840-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="c1840-162">15W 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-163">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-164">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="c1840-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-165">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="c1840-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="c1840-166">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="c1840-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-167">메모리</span><span class="sxs-lookup"><span data-stu-id="c1840-167">Memory</span></span></td><td> <span data-ttu-id="c1840-168">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="c1840-169">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-170">스토리지</span><span class="sxs-lookup"><span data-stu-id="c1840-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="c1840-171">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="c1840-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-172">USB 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-173">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="c1840-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c1840-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="c1840-175">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="c1840-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="c1840-176">Unity를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unity 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-177">HoloLens용 Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="c1840-177">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-178">VR용 Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="c1840-178">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="c1840-179">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="c1840-179">Next Development Checkpoint</span></span>

<span data-ttu-id="c1840-180">앞에서 설명한 HoloLens용 Unity 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-180">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-181">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="c1840-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="c1840-182">VR용 Unity 경험을 따르고 있는 경우, 다음 작업은 프로젝트를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-182">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-183">WMR용 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="c1840-183">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="c1840-184">언제든지 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 및 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)용 Unity 개발 검사점으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-184">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="c1840-185">Unreal</span><span class="sxs-lookup"><span data-stu-id="c1840-185">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="c1840-187">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="c1840-187">1. Download the latest version</span></span>

<span data-ttu-id="c1840-188">HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-188">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="c1840-189">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="c1840-189">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="c1840-191">MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-191">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="c1840-192">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-192">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="c1840-193">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-193">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="c1840-194">설치의 경우 큐레이션된 [Unreal 개발 경험](../unreal/unreal-development-overview.md)의 [시작 섹션](../unreal/unreal-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-194">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="c1840-195">Unreal 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unreal/tutorials/unreal-uxt-ch1.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-195">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c1840-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 로고 이미지](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="c1840-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="c1840-197">**Mixed Reality Toolkit-Unreal(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="c1840-197">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="c1840-198">Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-198">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="c1840-199">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="c1840-199">Other tools [optional]</span></span>
* <span data-ttu-id="c1840-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="c1840-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="c1840-202">3. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="c1840-202">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="c1840-203">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-203">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="c1840-204">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-204">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="c1840-205">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-205">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-206">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-206">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="c1840-207">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-207">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="c1840-208">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="c1840-208">For HoloLens development</span></span>

<span data-ttu-id="c1840-209">HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-209">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="c1840-210">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-210">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="c1840-211">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-211">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="c1840-212">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-212">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="c1840-213">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c1840-213">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="c1840-214">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-214">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="c1840-215">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](https://docs.microsoft.com/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-215">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="c1840-216">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-216">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="c1840-217">하지만 [HoloLens 보안 설명서](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-217">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="c1840-218">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-218">Possible solutions include:</span></span>

* <span data-ttu-id="c1840-219">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-219">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="c1840-220">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-220">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="c1840-221">이 정책은 [프로비전 패키지](https://docs.microsoft.com/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-221">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="c1840-222">[ARC(Advanced Recovery Companion)](https://docs.microsoft.com/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="c1840-222">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-223">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-223">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="c1840-224">USB를 통해 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-224">I can't deploy over USB</span></span>

<span data-ttu-id="c1840-225">USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unreal/tutorials/unreal-uxt-ch6.md)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-225">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="c1840-226">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1840-226">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="c1840-227">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-227">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="c1840-228">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-228">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="c1840-229">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-229">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="c1840-230">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-230">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="c1840-231">최소값</span><span class="sxs-lookup"><span data-stu-id="c1840-231">Minimum</span></span></th><th> <span data-ttu-id="c1840-232">권장</span><span class="sxs-lookup"><span data-stu-id="c1840-232">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="c1840-233">프로세서</span><span class="sxs-lookup"><span data-stu-id="c1840-233">Processor</span></span></td><td> <span data-ttu-id="c1840-234"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="c1840-234"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="c1840-235"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="c1840-235"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-236">GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-236">GPU</span></span></td><td> <span data-ttu-id="c1840-237"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-237"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="c1840-238"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-238"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-239">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="c1840-239">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="c1840-240">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="c1840-240">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-241">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="c1840-241">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="c1840-242">15W 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-242">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-243">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-243">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-244">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="c1840-244">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-245">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="c1840-245">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="c1840-246">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="c1840-246">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-247">메모리</span><span class="sxs-lookup"><span data-stu-id="c1840-247">Memory</span></span></td><td> <span data-ttu-id="c1840-248">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-248">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="c1840-249">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-249">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-250">스토리지</span><span class="sxs-lookup"><span data-stu-id="c1840-250">Storage</span></span></td><td colspan="2"> <span data-ttu-id="c1840-251">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="c1840-251">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-252">USB 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-252">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-253">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="c1840-253">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-254">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c1840-254">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="c1840-255">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="c1840-255">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="c1840-256">Unreal를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unreal 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-256">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-257">Unreal 경험 시작</span><span class="sxs-lookup"><span data-stu-id="c1840-257">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="c1840-258">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="c1840-258">Next Development Checkpoint</span></span>

<span data-ttu-id="c1840-259">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-259">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-260">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="c1840-260">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="c1840-261">언제든지 [Unreal 개발 검사점](../unreal/unreal-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-261">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="c1840-262">네이티브(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="c1840-262">Native (OpenXR)</span></span>](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

<span data-ttu-id="c1840-264">네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-264">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="c1840-265">개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../native/openxr-getting-started.md) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-265">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="c1840-266">1. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="c1840-266">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="c1840-267">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-267">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="c1840-268">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-268">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="c1840-269">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-269">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="c1840-270">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="c1840-270">For HoloLens development</span></span>

<span data-ttu-id="c1840-271">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-271">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="c1840-272">HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-272">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="c1840-273">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-273">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="c1840-274">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-274">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-275">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-275">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="c1840-276">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-276">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="c1840-277">HoloLens 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c1840-277">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="c1840-278">개발자 모드 설정은 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-278">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="c1840-279">디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](https://docs.microsoft.com/hololens/security-adminless-os)가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-279">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="c1840-280">다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-280">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="c1840-281">하지만 [HoloLens 보안 설명서](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-281">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="c1840-282">가능한 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-282">Possible solutions include:</span></span>

* <span data-ttu-id="c1840-283">디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-283">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="c1840-284">IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-284">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="c1840-285">이 정책은 [프로비전 패키지](https://docs.microsoft.com/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-285">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="c1840-286">[ARC(Advanced Recovery Companion)](https://docs.microsoft.com/hololens/hololens-recovery) 사용</span><span class="sxs-lookup"><span data-stu-id="c1840-286">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="c1840-287">디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-287">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="c1840-288">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1840-288">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="c1840-289">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-289">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="c1840-290">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c1840-290">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="c1840-291">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-291">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="c1840-292">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-292">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="c1840-293">최소값</span><span class="sxs-lookup"><span data-stu-id="c1840-293">Minimum</span></span></th><th> <span data-ttu-id="c1840-294">권장</span><span class="sxs-lookup"><span data-stu-id="c1840-294">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="c1840-295">프로세서</span><span class="sxs-lookup"><span data-stu-id="c1840-295">Processor</span></span></td><td> <span data-ttu-id="c1840-296"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="c1840-296"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="c1840-297"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="c1840-297"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-298">GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-298">GPU</span></span></td><td> <span data-ttu-id="c1840-299"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-299"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="c1840-300"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="c1840-300"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-301">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="c1840-301">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="c1840-302">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="c1840-302">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-303">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="c1840-303">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="c1840-304">15W 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-304">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-305">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-305">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-306">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="c1840-306">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-307">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="c1840-307">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="c1840-308">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="c1840-308">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-309">메모리</span><span class="sxs-lookup"><span data-stu-id="c1840-309">Memory</span></span></td><td> <span data-ttu-id="c1840-310">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-310">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="c1840-311">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="c1840-311">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-312">스토리지</span><span class="sxs-lookup"><span data-stu-id="c1840-312">Storage</span></span></td><td colspan="2"> <span data-ttu-id="c1840-313">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="c1840-313">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-314">USB 포트</span><span class="sxs-lookup"><span data-stu-id="c1840-314">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="c1840-315">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="c1840-315">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="c1840-316">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c1840-316">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="c1840-317">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="c1840-317">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="c1840-318">MRTK를 사용하는 네이티브 개발을 처음 접하는 경우 큐레이션된 네이티브 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-318">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-319">기본 경험 시작</span><span class="sxs-lookup"><span data-stu-id="c1840-319">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="c1840-320">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="c1840-320">Next Development Checkpoint</span></span>

<span data-ttu-id="c1840-321">앞에서 설명한 네이티브 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2에 대한 개발 환경을 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-321">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1840-322">HoloLens 2 설정</span><span class="sxs-lookup"><span data-stu-id="c1840-322">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="c1840-323">언제든지 [네이티브 개발 검사점](../native/directx-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1840-323">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
