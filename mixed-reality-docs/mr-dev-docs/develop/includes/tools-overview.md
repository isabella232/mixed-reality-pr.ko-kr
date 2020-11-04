---
ms.openlocfilehash: ad8f4a5ea9bda7915731f879da96cf7e007c58fb
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755385"
---
# <a name="unity"></a>[<span data-ttu-id="7ddb8-101">Unity</span><span class="sxs-lookup"><span data-stu-id="7ddb8-101">Unity</span></span>](#tab/unity)

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="7ddb8-103">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="7ddb8-103">1. Download the latest version</span></span>

<span data-ttu-id="7ddb8-104">새 프로젝트를 시작할 때 사용하기 가장 좋은 버전은 [Unity LTS(장기 지원)](https://unity3d.com/unity/qa/lts-releases) 스트림이며, 이것을 최신 개정판으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="7ddb8-105">현재 추천 사항은 아래의 MRTK v2에 필요한 LTS 빌드인 **Unity 2019** 를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-105">The current recommendation is to use **Unity 2019** , which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="7ddb8-106">특정 이유로 인해 다른 Unity 버전을 사용해야 하는 경우 Unity는 서로 다른 버전을 함께 설치하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="7ddb8-107">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="7ddb8-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="7ddb8-109">MRTK([Mixed Reality Toolkit](../unity/mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="7ddb8-110">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="7ddb8-111">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="7ddb8-112">설치의 경우 큐레이션된 [Unity 개발 경험](../unity/unity-development-overview.md)의 [시작 섹션](../unity/unity-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="7ddb8-113">Unity 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unity/tutorials/mr-learning-base-01.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddb8-114">설치 지침은 **MRTK 2.4.0** 및 **Unity 2019.3.15** 인 MRTK 및 Unity 릴리스의 안정적인 최신 조합을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddb8-115">Unity에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7ddb8-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="7ddb8-117">**Mixed Reality Toolkit-Unity(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="7ddb8-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="7ddb8-118">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="7ddb8-118">Other tools [optional]</span></span>
* <span data-ttu-id="7ddb8-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="7ddb8-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7ddb8-121">3. Mixed Reality 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="7ddb8-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="7ddb8-122">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7ddb8-123">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7ddb8-124">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddb8-125">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7ddb8-126">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7ddb8-127">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="7ddb8-127">For HoloLens development</span></span>

<span data-ttu-id="7ddb8-128">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7ddb8-129">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-129">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7ddb8-130">HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-130">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="7ddb8-131">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-131">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7ddb8-132">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7ddb8-132">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7ddb8-133">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-133">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7ddb8-134">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-134">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7ddb8-135">**Reverb G2** 헤드셋을 사용하는 경우 **Microsoft-Valve OpenXR** 플러그 인(TODO: // 링크 필요)을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-135">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="7ddb8-136">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-136">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7ddb8-137">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-137">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7ddb8-138">최소값</span><span class="sxs-lookup"><span data-stu-id="7ddb8-138">Minimum</span></span></th><th> <span data-ttu-id="7ddb8-139">권장</span><span class="sxs-lookup"><span data-stu-id="7ddb8-139">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ddb8-140">프로세서</span><span class="sxs-lookup"><span data-stu-id="7ddb8-140">Processor</span></span></td><td> <span data-ttu-id="7ddb8-141"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="7ddb8-141"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7ddb8-142"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-142"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-143">GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-143">GPU</span></span></td><td> <span data-ttu-id="7ddb8-144"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-144"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7ddb8-145"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-145"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-146">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="7ddb8-146">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-147">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="7ddb8-147">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-148">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="7ddb8-148">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-149">15W 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-149">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-150">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-150">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-151">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-151">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-152">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="7ddb8-152">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-153">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-153">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-154">메모리</span><span class="sxs-lookup"><span data-stu-id="7ddb8-154">Memory</span></span></td><td> <span data-ttu-id="7ddb8-155">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-155">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7ddb8-156">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-156">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-157">스토리지</span><span class="sxs-lookup"><span data-stu-id="7ddb8-157">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-158">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="7ddb8-158">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-159">USB 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-159">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-160">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="7ddb8-160">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-161">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7ddb8-161">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-162">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-162">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7ddb8-163">Unity를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unity 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-163">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-164">Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="7ddb8-164">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7ddb8-165">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="7ddb8-165">Next Development Checkpoint</span></span>

<span data-ttu-id="7ddb8-166">앞에서 설명한 Unity 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-166">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-167">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="7ddb8-167">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="7ddb8-168">언제든지 [Unity 개발 검사점](../unity/unity-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-168">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="7ddb8-169">Unreal</span><span class="sxs-lookup"><span data-stu-id="7ddb8-169">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="7ddb8-171">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="7ddb8-171">1. Download the latest version</span></span>

<span data-ttu-id="7ddb8-172">HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-172">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="7ddb8-173">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="7ddb8-173">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="7ddb8-175">MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-175">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="7ddb8-176">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-176">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="7ddb8-177">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-177">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="7ddb8-178">설치의 경우 큐레이션된 [Unreal 개발 경험](../unreal/unreal-development-overview.md)의 [시작 섹션](../unreal/unreal-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-178">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="7ddb8-179">Unreal 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unreal/tutorials/unreal-uxt-ch1.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-179">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7ddb8-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 로고 이미지](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="7ddb8-181">**Mixed Reality Toolkit-Unreal(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="7ddb8-181">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="7ddb8-182">Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-182">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="7ddb8-183">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="7ddb8-183">Other tools [optional]</span></span>
* <span data-ttu-id="7ddb8-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="7ddb8-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7ddb8-186">3. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="7ddb8-186">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="7ddb8-187">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-187">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7ddb8-188">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-188">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7ddb8-189">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-189">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddb8-190">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-190">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7ddb8-191">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-191">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7ddb8-192">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="7ddb8-192">For HoloLens development</span></span>

<span data-ttu-id="7ddb8-193">HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-193">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7ddb8-194">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-194">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7ddb8-195">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-195">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7ddb8-196">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7ddb8-196">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7ddb8-197">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-197">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7ddb8-198">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-198">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7ddb8-199">**Reverb G2** 헤드셋을 사용하는 경우 **Microsoft-Valve OpenXR** 플러그 인(TODO: // 링크 필요)을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-199">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="7ddb8-200">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-200">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7ddb8-201">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-201">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7ddb8-202">최소값</span><span class="sxs-lookup"><span data-stu-id="7ddb8-202">Minimum</span></span></th><th> <span data-ttu-id="7ddb8-203">권장</span><span class="sxs-lookup"><span data-stu-id="7ddb8-203">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ddb8-204">프로세서</span><span class="sxs-lookup"><span data-stu-id="7ddb8-204">Processor</span></span></td><td> <span data-ttu-id="7ddb8-205"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="7ddb8-205"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7ddb8-206"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-206"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-207">GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-207">GPU</span></span></td><td> <span data-ttu-id="7ddb8-208"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-208"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7ddb8-209"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-209"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-210">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="7ddb8-210">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-211">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="7ddb8-211">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-212">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="7ddb8-212">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-213">15W 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-213">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-214">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-214">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-215">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-215">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-216">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="7ddb8-216">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-217">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-217">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-218">메모리</span><span class="sxs-lookup"><span data-stu-id="7ddb8-218">Memory</span></span></td><td> <span data-ttu-id="7ddb8-219">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-219">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7ddb8-220">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-220">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-221">스토리지</span><span class="sxs-lookup"><span data-stu-id="7ddb8-221">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-222">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="7ddb8-222">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-223">USB 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-223">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-224">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="7ddb8-224">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-225">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7ddb8-225">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-226">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-226">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7ddb8-227">Unreal를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unreal 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-227">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-228">Unreal 경험 시작</span><span class="sxs-lookup"><span data-stu-id="7ddb8-228">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7ddb8-229">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="7ddb8-229">Next Development Checkpoint</span></span>

<span data-ttu-id="7ddb8-230">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-230">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-231">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="7ddb8-231">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="7ddb8-232">언제든지 [Unreal 개발 검사점](../unreal/unreal-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-232">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="7ddb8-233">네이티브(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-233">Native (OpenXR)</span></span>](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

<span data-ttu-id="7ddb8-235">네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-235">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="7ddb8-236">개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../native/openxr-getting-started.md) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-236">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7ddb8-237">1. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="7ddb8-237">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="7ddb8-238">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-238">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7ddb8-239">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-239">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7ddb8-240">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-240">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7ddb8-241">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="7ddb8-241">For HoloLens development</span></span>

<span data-ttu-id="7ddb8-242">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-242">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7ddb8-243">[HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-243">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7ddb8-244">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-244">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddb8-245">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-245">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7ddb8-246">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-246">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7ddb8-247">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7ddb8-247">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7ddb8-248">다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-248">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7ddb8-249">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-249">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7ddb8-250">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-250">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7ddb8-251">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-251">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7ddb8-252">최소값</span><span class="sxs-lookup"><span data-stu-id="7ddb8-252">Minimum</span></span></th><th> <span data-ttu-id="7ddb8-253">권장</span><span class="sxs-lookup"><span data-stu-id="7ddb8-253">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ddb8-254">프로세서</span><span class="sxs-lookup"><span data-stu-id="7ddb8-254">Processor</span></span></td><td> <span data-ttu-id="7ddb8-255"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="7ddb8-255"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7ddb8-256"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-256"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-257">GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-257">GPU</span></span></td><td> <span data-ttu-id="7ddb8-258"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-258"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7ddb8-259"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="7ddb8-259"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-260">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="7ddb8-260">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-261">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="7ddb8-261">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-262">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="7ddb8-262">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-263">15W 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-263">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-264">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-264">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-265">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-265">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-266">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="7ddb8-266">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-267">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-267">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-268">메모리</span><span class="sxs-lookup"><span data-stu-id="7ddb8-268">Memory</span></span></td><td> <span data-ttu-id="7ddb8-269">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-269">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7ddb8-270">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="7ddb8-270">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-271">스토리지</span><span class="sxs-lookup"><span data-stu-id="7ddb8-271">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-272">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="7ddb8-272">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-273">USB 포트</span><span class="sxs-lookup"><span data-stu-id="7ddb8-273">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-274">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="7ddb8-274">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ddb8-275">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7ddb8-275">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7ddb8-276">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="7ddb8-276">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7ddb8-277">MRTK를 사용하는 네이티브 개발을 처음 접하는 경우 큐레이션된 네이티브 개발 경험을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-277">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-278">기본 경험 시작</span><span class="sxs-lookup"><span data-stu-id="7ddb8-278">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7ddb8-279">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="7ddb8-279">Next Development Checkpoint</span></span>

<span data-ttu-id="7ddb8-280">앞에서 설명한 네이티브 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2에 대한 개발 환경을 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-280">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ddb8-281">HoloLens 2 설정</span><span class="sxs-lookup"><span data-stu-id="7ddb8-281">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="7ddb8-282">언제든지 [네이티브 개발 검사점](../native/directx-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-282">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
