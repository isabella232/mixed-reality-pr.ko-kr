---
title: 포팅 가이드
description: 기존 몰입 형 응용 프로그램을 Windows Mixed Reality로 이식 하는 방법을 설명 하는 단계별 연습입니다.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 포트, 포팅, unity, 미들웨어, 엔진, UWP, Win32
ms.openlocfilehash: 9822976ab7dac9ae7567e5f38ca44ceee646d098
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638548"
---
# <a name="porting-guides"></a><span data-ttu-id="59ecb-104">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="59ecb-104">Porting guides</span></span>

<span data-ttu-id="59ecb-105">Windows 10에는 몰입 형 및 holographic 헤드셋을 직접 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-105">Windows 10 includes direct support for immersive and holographic headsets.</span></span> <span data-ttu-id="59ecb-106">Rift 또는 HTC Vive와 같은 다른 장치에 대 한 콘텐츠를 빌드한 경우 운영 체제의 플랫폼 API 위에 있는 라이브러리에 대 한 종속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-106">If you've built content for other devices, such as the Oculus Rift or HTC Vive, these have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="59ecb-107">기존 Win32 Unity VR 앱을 Windows Mixed Reality로 가져오면 공급 업체의 특정 VR Sdk 사용이 Unity의 공급 업체의 VR Api로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-overview"></a><span data-ttu-id="59ecb-108">포팅 개요</span><span class="sxs-lookup"><span data-stu-id="59ecb-108">Porting overview</span></span>

<span data-ttu-id="59ecb-109">개략적인 수준에서 다음과 같은 단계를 수행 하 여 기존 콘텐츠를 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="59ecb-110">**PC에서 Windows 10의 작성자 업데이트 (16299)를 실행 하 고 있는지 확인 합니다.**</span><span class="sxs-lookup"><span data-stu-id="59ecb-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="59ecb-111">이러한 빌드는 혼합 현실 개발에 가장 안정적이 아니므로 Insider Skip에서 preview 빌드를 수신 하는 것이 더 이상 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="59ecb-112">**최신 버전의 그래픽 또는 게임 엔진으로 업그레이드 합니다.**</span><span class="sxs-lookup"><span data-stu-id="59ecb-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="59ecb-113">게임 엔진은 Windows 10 SDK 버전 10.0.15063.0 (4 월 2017에 릴리스된) 이상을 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="59ecb-114">**미들웨어, 플러그 인 또는 구성 요소를 업그레이드 합니다.**</span><span class="sxs-lookup"><span data-stu-id="59ecb-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="59ecb-115">앱에 구성 요소가 있는 경우 최신 버전으로 업그레이드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="59ecb-116">**중복 된 sdk에 대 한 종속성을 제거** 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-116">**Remove dependencies on duplicate SDKs** .</span></span> <span data-ttu-id="59ecb-117">콘텐츠를 대상으로 하는 장치에 따라 Windows Api를 대상으로 지정할 수 있도록 해당 SDK (예: SteamVR)를 제거 하거나 조건부로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK (for example, SteamVR) so you can target the Windows APIs instead.</span></span>
5. <span data-ttu-id="59ecb-118">**빌드 문제를 해결 합니다.**</span><span class="sxs-lookup"><span data-stu-id="59ecb-118">**Work through build issues.**</span></span> <span data-ttu-id="59ecb-119">이때 포팅 연습은 앱, 엔진 및 구성 요소 종속성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-119">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="59ecb-120">일반적인 포팅 단계</span><span class="sxs-lookup"><span data-stu-id="59ecb-120">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="59ecb-121">1. 올바른 개발 하드웨어가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-121">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="59ecb-122">[도구 설치](../install-the-tools.md#immersive-vr-headset-requirements) 페이지에 권장 되는 개발 하드웨어가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-122">The [install the tools](../install-the-tools.md#immersive-vr-headset-requirements) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="59ecb-123">2. Windows 10의 최신 비행로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="59ecb-123">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="59ecb-124">Windows Mixed Reality 플랫폼은 아직 개발 중입니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-124">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="59ecb-125">Windows 참가자 [프로그램에 가입](https://insider.windows.com/) 하 여 "windows 참가자가 빠르게" 비행에 액세스 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-125">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="59ecb-126">[Windows 10 크리에이터 스 업데이트](https://www.microsoft.com/software-download/windows10) 설치</span><span class="sxs-lookup"><span data-stu-id="59ecb-126">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="59ecb-127">Windows 참가자 프로그램에 [참여](https://insider.windows.com/) 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-127">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="59ecb-128">[개발자 모드](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) 사용</span><span class="sxs-lookup"><span data-stu-id="59ecb-128">Enable [Developer Mode](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="59ecb-129">**설정 > 업데이트 & 보안 섹션** 을 통해 [Windows Insider Fast flight](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) 로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-129">Switch to the [Windows Insider Fast flights](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="59ecb-130">3. Visual Studio의 최신 빌드로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="59ecb-130">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="59ecb-131">Visual Studio를 사용 하는 경우 가장 최근 빌드로 업그레이드 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-131">If you're using Visual Studio then upgrade to the most recent build</span></span>
* <span data-ttu-id="59ecb-132">Visual Studio 2019 [의 도구 설치 페이지를](../install-the-tools.md#installation-checklist) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59ecb-132">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="59ecb-133">4. 올바른 어댑터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-133">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="59ecb-134">두 개의 Gpu가 있는 노트북 같은 시스템에서 [올바른 어댑터를 대상](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-134">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="59ecb-135">이는 ID3D11Device가 명시적 또는 암시적으로 (미디어 파운데이션) 해당 기능에 대해 생성 되는 Unity 및 네이티브 DirectX 앱에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59ecb-135">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="59ecb-136">Unity 포팅 지침</span><span class="sxs-lookup"><span data-stu-id="59ecb-136">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="59ecb-137">Unreal 포팅 지침</span><span class="sxs-lookup"><span data-stu-id="59ecb-137">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59ecb-138">HP 반향 G2 컨트롤러를 사용 하는 경우 추가 입력 매핑 지침은 [이 문서](../unreal/unreal-reverb-g2-controllers.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59ecb-138">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="59ecb-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59ecb-139">See also</span></span>
* [<span data-ttu-id="59ecb-140">Windows Mixed Reality 최소 PC 하드웨어 호환성 지침</span><span class="sxs-lookup"><span data-stu-id="59ecb-140">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="59ecb-141">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="59ecb-141">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="59ecb-142">Unity에 대 한 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="59ecb-142">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="59ecb-143">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="59ecb-143">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="59ecb-144">Unity의 제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="59ecb-144">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="59ecb-145">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="59ecb-145">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="59ecb-146">UnityEngine. XR 추적</span><span class="sxs-lookup"><span data-stu-id="59ecb-146">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="59ecb-147">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="59ecb-147">Porting guides</span></span>](porting-guides.md)