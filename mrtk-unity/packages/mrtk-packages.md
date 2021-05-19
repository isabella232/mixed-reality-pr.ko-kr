---
title: MRTK 패키지
description: 혼합 현실 하드웨어 및 플랫폼을 지 원하는 MRTK의 패키지입니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Unity 패키지 관리자
ms.openlocfilehash: 3c92448d99cd67efa0a06feff9b0c7561a6aea79
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143801"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="caf3c-104">혼합 현실 도구 키트 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="caf3c-105">Mixed Reality Toolkit (MRTK)은 혼합 현실 하드웨어 및 플랫폼에 대 한 지원을 제공 하 여 플랫폼 간 혼합 현실 응용 프로그램 개발을 가능 하 게 하는 패키지 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="caf3c-106">MRTK는 [asset](#asset-packages) (. unitypackage) 패키지와 [Unity 패키지 관리자](#unity-package-manager)를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-106">MRTK is available as [asset](#asset-packages) (.unitypackage) packages and via the [Unity Package Manager](#unity-package-manager).</span></span>

## <a name="asset-packages"></a><span data-ttu-id="caf3c-107">자산 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-107">Asset packages</span></span>

<span data-ttu-id="caf3c-108">MRTK 자산 (. unitypackage)은 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-108">The MRTK asset (.unitypackage) can be downloaded from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span>

<span data-ttu-id="caf3c-109">자산 패키지를 사용 하는 몇 가지 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-109">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="caf3c-110">Unity 2018.4 이상에서 사용 가능</span><span class="sxs-lookup"><span data-stu-id="caf3c-110">Available for Unity 2018.4 and newer</span></span>
- <span data-ttu-id="caf3c-111">MRTK를 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-111">Easy to make changes to MRTK</span></span>
  - <span data-ttu-id="caf3c-112">MRTK가 자산 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-112">MRTK is in the Assets folder</span></span>

<span data-ttu-id="caf3c-113">다음은 몇 가지 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-113">Some of the challenges are:</span></span>

- <span data-ttu-id="caf3c-114">MRTK는 프로젝트의 자산 폴더의 일부 이며,</span><span class="sxs-lookup"><span data-stu-id="caf3c-114">MRTK is part of the project's Assets folder, leading to</span></span>
  - <span data-ttu-id="caf3c-115">대규모 프로젝트</span><span class="sxs-lookup"><span data-stu-id="caf3c-115">Larger projects</span></span>
  - <span data-ttu-id="caf3c-116">컴파일 시간 느림</span><span class="sxs-lookup"><span data-stu-id="caf3c-116">Slower compilation times</span></span>
- <span data-ttu-id="caf3c-117">종속성 관리 안 함</span><span class="sxs-lookup"><span data-stu-id="caf3c-117">No dependency management</span></span>
  - <span data-ttu-id="caf3c-118">고객은 패키지 종속성을 수동으로 해결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-118">Customers are required to resolve package dependencies manually</span></span>
- <span data-ttu-id="caf3c-119">수동 업데이트 프로세스</span><span class="sxs-lookup"><span data-stu-id="caf3c-119">Manual update process</span></span>
  - <span data-ttu-id="caf3c-120">여러 단계</span><span class="sxs-lookup"><span data-stu-id="caf3c-120">Multiple steps</span></span>
  - <span data-ttu-id="caf3c-121">대량 (3000 개 이상 파일) 소스 제어 업데이트</span><span class="sxs-lookup"><span data-stu-id="caf3c-121">Large (3000+ file) source control updates</span></span>
  - <span data-ttu-id="caf3c-122">MRTK에 대 한 변경 내용이 손실 될 위험</span><span class="sxs-lookup"><span data-stu-id="caf3c-122">Risk of losing changes made to MRTK</span></span>
- <span data-ttu-id="caf3c-123">예제 패키지를 가져오는 것은 일반적으로 모든 예제를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-123">Importing the examples package typically means including all examples</span></span>

<span data-ttu-id="caf3c-124">사용 가능한 패키지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-124">The available packages are:</span></span>

- [<span data-ttu-id="caf3c-125">재단</span><span class="sxs-lookup"><span data-stu-id="caf3c-125">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="caf3c-126">확장</span><span class="sxs-lookup"><span data-stu-id="caf3c-126">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="caf3c-127">도구</span><span class="sxs-lookup"><span data-stu-id="caf3c-127">Tools</span></span>](#tools-package)
- [<span data-ttu-id="caf3c-128">테스트 유틸리티</span><span class="sxs-lookup"><span data-stu-id="caf3c-128">Test utilities</span></span>](#test-utilities-package)
- [<span data-ttu-id="caf3c-129">예제</span><span class="sxs-lookup"><span data-stu-id="caf3c-129">Examples</span></span>](#examples-package)

<span data-ttu-id="caf3c-130">이러한 패키지는 GitHub의 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 분기에 있는 소스 코드에서 Microsoft에서 릴리스 및 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-130">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

### <a name="foundation-package"></a><span data-ttu-id="caf3c-131">Foundation 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-131">Foundation package</span></span>

<span data-ttu-id="caf3c-132">Mixed Reality Toolkit Foundation은 애플리케이션이 Mixed Reality 플랫폼에서 공통 기능을 활용할 수 있도록 하는 코드 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-132">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<span data-ttu-id="caf3c-133"><sup>MRTK Foundation 패키지</sup></span><span class="sxs-lookup"><span data-stu-id="caf3c-133"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="caf3c-134">MRTK Foundation 패키지에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-134">The MRTK Foundation package contains the following.</span></span>

| <span data-ttu-id="caf3c-135">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-135">Folder</span></span> | <span data-ttu-id="caf3c-136">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-136">Component</span></span> | <span data-ttu-id="caf3c-137">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-137">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-138">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="caf3c-138">MRTK/Core</span></span> | | <span data-ttu-id="caf3c-139">인터페이스 및 형식 정의, 기본 클래스, 표준 셰이더.</span><span class="sxs-lookup"><span data-stu-id="caf3c-139">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="caf3c-140">MRTK/Core/Providers</span><span class="sxs-lookup"><span data-stu-id="caf3c-140">MRTK/Core/Providers</span></span> | | <span data-ttu-id="caf3c-141">플랫폼에 구애받지 않은 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-141">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="caf3c-142">손을</span><span class="sxs-lookup"><span data-stu-id="caf3c-142">Hands</span></span> | <span data-ttu-id="caf3c-143">손 추적을 위한 기본 클래스 지원 및 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-143">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="caf3c-144">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="caf3c-144">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="caf3c-145">머리 이동 및 손 추적 데이터 기록을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-145">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="caf3c-146">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="caf3c-146">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="caf3c-147">손 및 눈 입력의 편집기 내 시뮬레이션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-147">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="caf3c-148">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="caf3c-148">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="caf3c-149">3D 모델을 데이터로 사용하는 공간 인식 관찰자입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-149">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="caf3c-150">UnityInput</span><span class="sxs-lookup"><span data-stu-id="caf3c-150">UnityInput</span></span> | <span data-ttu-id="caf3c-151">Unity의 입력 API를 통해 구현 되는 일반적인 입력 장치 (조이스틱, 마우스 등).</span><span class="sxs-lookup"><span data-stu-id="caf3c-151">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="caf3c-152">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-152">MRTK/Providers</span></span> | | <span data-ttu-id="caf3c-153">플랫폼별 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-153">Platform specific data providers</span></span> |
| | <span data-ttu-id="caf3c-154">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="caf3c-154">LeapMotion</span></span> | <span data-ttu-id="caf3c-155">UltraLeap Leap 동작 컨트롤러에 대 한 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-155">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="caf3c-156">OpenVR</span><span class="sxs-lookup"><span data-stu-id="caf3c-156">OpenVR</span></span> | <span data-ttu-id="caf3c-157">OpenVR 장치 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-157">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="caf3c-158">Oculus</span><span class="sxs-lookup"><span data-stu-id="caf3c-158">Oculus</span></span> | <span data-ttu-id="caf3c-159">Quest와 같은 Oculus 장치 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-159">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="caf3c-160">UnityAR</span><span class="sxs-lookup"><span data-stu-id="caf3c-160">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="caf3c-161">시험용 모바일 AR 장치에서 MRTK를 사용 하도록 설정 하는 카메라 설정 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-161">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="caf3c-162">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="caf3c-162">WindowsMixedReality</span></span> | <span data-ttu-id="caf3c-163">Microsoft HoloLens 및 몰입 형 헤드셋을 비롯 한 Windows Mixed Reality 장치 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-163">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="caf3c-164">Windows</span><span class="sxs-lookup"><span data-stu-id="caf3c-164">Windows</span></span> | <span data-ttu-id="caf3c-165">Microsoft Windows 특정 Api에 대 한 지원 (예: 음성 및 받아쓰기).</span><span class="sxs-lookup"><span data-stu-id="caf3c-165">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="caf3c-166">XR SDK</span><span class="sxs-lookup"><span data-stu-id="caf3c-166">XR SDK</span></span> | <span data-ttu-id="caf3c-167">시험용 Unity 2019.3 이상에서 [unity의 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-167">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="caf3c-168">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="caf3c-168">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="caf3c-169">실험적</span><span class="sxs-lookup"><span data-stu-id="caf3c-169">Experimental</span></span> | <span data-ttu-id="caf3c-170">셰이더, 사용자 인터페이스 컨트롤 및 개별 시스템 관리자를 비롯 한 실험적 기능</span><span class="sxs-lookup"><span data-stu-id="caf3c-170">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="caf3c-171">기능</span><span class="sxs-lookup"><span data-stu-id="caf3c-171">Features</span></span> | <span data-ttu-id="caf3c-172">기본 패키지를 기반으로 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-172">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="caf3c-173">프로필</span><span class="sxs-lookup"><span data-stu-id="caf3c-173">Profiles</span></span> | <span data-ttu-id="caf3c-174">Microsoft Mixed Reality Toolkit 시스템 및 서비스에 대 한 기본 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-174">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="caf3c-175">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="caf3c-175">StandardAssets</span></span> | <span data-ttu-id="caf3c-176">일반 자산; 모델, 질감, 재질 등</span><span class="sxs-lookup"><span data-stu-id="caf3c-176">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="caf3c-177">MRTK/SceneSystemResources</span><span class="sxs-lookup"><span data-stu-id="caf3c-177">MRTK/SceneSystemResources</span></span> | | <span data-ttu-id="caf3c-178">장면 시스템에서 사용하는 자산 및 리소스</span><span class="sxs-lookup"><span data-stu-id="caf3c-178">Assets and resources used by the Scene System</span></span> |
| <span data-ttu-id="caf3c-179">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="caf3c-179">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="caf3c-180">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-180">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="caf3c-181">VR 경계 지원을 구현하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-181">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="caf3c-182">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-182">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="caf3c-183">카메라 구성 및 관리를 구현하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-183">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="caf3c-184">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-184">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="caf3c-185">애플리케이션 진단에서 구현하는 시스템(예: 시각적 프로파일러)</span><span class="sxs-lookup"><span data-stu-id="caf3c-185">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="caf3c-186">InputSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-186">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="caf3c-187">사용자 입력 액세스 및 처리에 대한 지원을 제공하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-187">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="caf3c-188">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-188">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="caf3c-189">다중 장면 애플리케이션 지원을 제공하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-189">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="caf3c-190">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-190">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="caf3c-191">사용자 환경을 인식하기 위한 지원을 제공하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-191">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="caf3c-192">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-192">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="caf3c-193">원격 보고(점프 환경 이동)에 대한 지원을 제공하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-193">System providing support for teleporting (moving about the experience in jumps).</span></span> |
| <span data-ttu-id="caf3c-194">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="caf3c-194">MRTK/StandardAssets</span></span> | | <span data-ttu-id="caf3c-195">혼합 현실 환경을 위한 MRTK 표준 셰이더, 기본 재질 및 기타 표준 자산</span><span class="sxs-lookup"><span data-stu-id="caf3c-195">MRTK Standard shader, basic materials and other standard assets for mixed reality experiences</span></span> |

### <a name="extensions-package"></a><span data-ttu-id="caf3c-196">확장 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-196">Extensions package</span></span>

<span data-ttu-id="caf3c-197">선택적 MixedRealityToolkit 패키지에는 Microsoft Mixed Reality Toolkit의 기능을 확장 하는 추가 서비스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-197">The optional Microsoft.MixedRealityToolkit.Unity.Extensions package includes additional services that extend the functionality of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="caf3c-198">확장 패키지에는 MixedRealityToolkit가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-198">The extensions package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="caf3c-199">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-199">Folder</span></span> | <span data-ttu-id="caf3c-200">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-200">Component</span></span> | <span data-ttu-id="caf3c-201">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-201">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-202">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="caf3c-202">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="caf3c-203">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="caf3c-203">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="caf3c-204">트레일러 지원을 추가 하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-204">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="caf3c-205">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="caf3c-205">LostTrackingService</span></span> | <span data-ttu-id="caf3c-206">Microsoft HoloLens 장치에서 추적 손실의 처리를 간소화 하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-206">Service that simplifies handling of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="caf3c-207">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="caf3c-207">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="caf3c-208">부드러운 장면 전환 추가를 간소화 하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-208">Service that simplifies adding smooth scene transitions.</span></span> |

### <a name="tools-package"></a><span data-ttu-id="caf3c-209">도구 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-209">Tools package</span></span>

<span data-ttu-id="caf3c-210">선택적 MixedRealityToolkit 패키지에는 Microsoft Mixed Reality 도구 키트를 사용 하 여 혼합 현실 개발 환경을 개선 하는 유용한 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-210">The optional Microsoft.MixedRealityToolkit.Unity.Tools package includes helpful tools that enhance the mixed reality development experience using the Microsoft Mixed Reality Toolkit.</span></span>
<span data-ttu-id="caf3c-211">이러한 도구는 Unity 편집기의 **Mixed Reality Toolkit > 유틸리티** 메뉴에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-211">These tools are located in the **Mixed Reality Toolkit > Utilities** menu in the Unity Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="caf3c-212">도구 패키지에는 MixedRealityToolkit가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-212">The tools package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="caf3c-213">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-213">Folder</span></span> | <span data-ttu-id="caf3c-214">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-214">Component</span></span> | <span data-ttu-id="caf3c-215">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-215">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-216">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="caf3c-216">MRTK/Tools</span></span> | |
| | <span data-ttu-id="caf3c-217">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-217">BuildWindow</span></span> | <span data-ttu-id="caf3c-218">UWP 응용 프로그램 빌드 및 배포 프로세스를 간소화 하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-218">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="caf3c-219">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-219">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="caf3c-220">프로젝트의 자산에 대 한 종속성 그래프를 만드는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-220">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="caf3c-221">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="caf3c-221">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="caf3c-222">확장 서비스 만들기를 지원하는 마법사입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-222">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="caf3c-223">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-223">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="caf3c-224">사용되지 않는 MRTK 구성 요소를 사용하는 코드를 업데이트하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-224">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="caf3c-225">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-225">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="caf3c-226">Unity에서 최상의 성능을 위해 혼합 현실 프로젝트 구성을 자동화하는 데 도움이 되는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-226">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="caf3c-227">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="caf3c-227">ReserializeAssetsUtility</span></span> | <span data-ttu-id="caf3c-228">특정 Unity 파일의 재시작을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-228">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="caf3c-229">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="caf3c-229">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="caf3c-230">유틸리티를 사용하면 개발자가 하드웨어 컨트롤러에 대한 Unity 매핑을 신속하게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-230">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="caf3c-231">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="caf3c-231">ScreenshotUtility</span></span> | <span data-ttu-id="caf3c-232">Unity 편집기에서 애플리케이션 이미지를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-232">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="caf3c-233">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-233">TextureCombinerWindow</span></span> | <span data-ttu-id="caf3c-234">그래픽 질감을 결합하는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-234">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="caf3c-235">도구 상자</span><span class="sxs-lookup"><span data-stu-id="caf3c-235">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="caf3c-236">MRTK UX 구성 요소를 쉽게 검색하고 사용할 수 있는 UI입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-236">UI that makes it easy to discover and use MRTK UX components.</span></span> |

### <a name="test-utilities-package"></a><span data-ttu-id="caf3c-237">유틸리티 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="caf3c-237">Test utilities package</span></span>

<span data-ttu-id="caf3c-238">선택적 Microsoft.MixedRealityToolkit.TestUtilities 패키지는 개발자가 재생 모드 테스트를 쉽게 [만들](../contributing/unit-tests.md#play-mode-tests)수 있도록 하는 도우미 스크립트의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-238">The optional Microsoft.MixedRealityToolkit.TestUtilities package is a collection of helper scripts that enable developers to easily [create play mode tests](../contributing/unit-tests.md#play-mode-tests).</span></span> <span data-ttu-id="caf3c-239">이러한 유틸리티는 MRTK 구성 요소를 만드는 개발자에게 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-239">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="caf3c-240">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-240">Folder</span></span> | <span data-ttu-id="caf3c-241">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-241">Component</span></span> | <span data-ttu-id="caf3c-242">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-242">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-243">MRTK/테스트</span><span class="sxs-lookup"><span data-stu-id="caf3c-243">MRTK/Tests</span></span> | |
| | <span data-ttu-id="caf3c-244">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="caf3c-244">TestUtilities</span></span> | <span data-ttu-id="caf3c-245">손 시뮬레이션 유틸리티를 포함하여 재생 모드 테스트 만들기를 간소화하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-245">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

### <a name="examples-package"></a><span data-ttu-id="caf3c-246">예제 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-246">Examples package</span></span>

<span data-ttu-id="caf3c-247">예제 패키지에는 기본 패키지에서 기능을 연습하는 데모, 샘플 스크립트 및 샘플 장면이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-247">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="caf3c-248">이 패키지에는 다양한 유형의 손 입력에 응답하는 샘플 개체(굴절형 및 비음열)가 포함된 [HandInteractionExample 장면(아래](../features/example-scenes/hand-interaction-examples.md) 그림 참조)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-248">This package contains the [HandInteractionExample scene](../features/example-scenes/hand-interaction-examples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![HandInteractionExample 장면](../features/images/MRTK_Examples.png)

<span data-ttu-id="caf3c-250">이 패키지에는 [여기에 문서화된](../features/example-scenes/eye-tracking-examples-overview.md) 시선 추적 데모도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-250">This package also contains eye tracking demos, which are [documented here](../features/example-scenes/eye-tracking-examples-overview.md)</span></span>

<span data-ttu-id="caf3c-251">일반적으로 MRTK의 모든 새 기능에는 예제 패키지에 해당하는 예제가 포함되어야 하며 대략 동일한 폴더 구조와 위치를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-251">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

> [!NOTE]
> <span data-ttu-id="caf3c-252">예제 패키지에는 Microsoft.MixedRealityToolkit.Unity.Foundation이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-252">The examples package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="caf3c-253">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-253">Folder</span></span> | <span data-ttu-id="caf3c-254">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-254">Component</span></span> | <span data-ttu-id="caf3c-255">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-255">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-256">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="caf3c-256">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="caf3c-257">데모</span><span class="sxs-lookup"><span data-stu-id="caf3c-257">Demos</span></span> | <span data-ttu-id="caf3c-258">하나 또는 두 개의 관련 기능을 보여주는 간단한 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-258">Simple scenes illustrating one or two related features.</span></span> |
| | <span data-ttu-id="caf3c-259">실험적</span><span class="sxs-lookup"><span data-stu-id="caf3c-259">Experimental</span></span> | <span data-ttu-id="caf3c-260">실험적 기능을 보여주는 데모 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-260">Demo scenes illustrating experimental features.</span></span> |
| | <span data-ttu-id="caf3c-261">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="caf3c-261">StandardAssets</span></span> | <span data-ttu-id="caf3c-262">여러 데모 장면에서 공유하는 공통 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-262">Common assets shared by multiple demo scenes.</span></span> |

## <a name="unity-package-manager"></a><span data-ttu-id="caf3c-263">Unity 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="caf3c-263">Unity Package Manager</span></span>

<span data-ttu-id="caf3c-264">Unity 2019.4 이상에서 만드는 환경의 경우 [Unity 패키지 관리자](https://docs.unity3d.com/Manual/Packages.html)통해 MRTK를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-264">For experiences being created using Unity 2019.4 and newer, the MRTK is available via the [Unity Package Manager](https://docs.unity3d.com/Manual/Packages.html).</span></span>

<span data-ttu-id="caf3c-265">자산 패키지 사용의 이점 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-265">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="caf3c-266">더 작은 프로젝트</span><span class="sxs-lookup"><span data-stu-id="caf3c-266">Smaller projects</span></span>
  - <span data-ttu-id="caf3c-267">더 클리너 Visual Studio 솔루션</span><span class="sxs-lookup"><span data-stu-id="caf3c-267">Cleaner Visual Studio solutions</span></span>
  - <span data-ttu-id="caf3c-268">체크 인할 파일 수가 더 적습니다(MRTK는 파일의 간단한 참조). `Packages/manifest.json`</span><span class="sxs-lookup"><span data-stu-id="caf3c-268">Fewer files to check in (MRTK is a simple reference in the `Packages/manifest.json` file)</span></span>
- <span data-ttu-id="caf3c-269">더 빠른 컴파일</span><span class="sxs-lookup"><span data-stu-id="caf3c-269">Faster compilation</span></span>
  - <span data-ttu-id="caf3c-270">Unity는 빌드하는 동안 MRTK를 다시 컴파일할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-270">Unity does not need to recompile MRTK during building</span></span>
- <span data-ttu-id="caf3c-271">종속성 확인</span><span class="sxs-lookup"><span data-stu-id="caf3c-271">Dependency resolution</span></span>
  - <span data-ttu-id="caf3c-272">필수 MRTK 패키지는 필수 항목이 있는 패키지를 지정할 때 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-272">Required MRTK packages are automatically installed when specifying packages with dependencies</span></span>
- <span data-ttu-id="caf3c-273">새 MRTK 버전으로 쉽게 업데이트</span><span class="sxs-lookup"><span data-stu-id="caf3c-273">Easy update to new MRTK versions</span></span>
  - <span data-ttu-id="caf3c-274">파일의 버전을 변경 합니다. `Packages/manifest.json`</span><span class="sxs-lookup"><span data-stu-id="caf3c-274">Change the version in the `Packages/manifest.json` file</span></span>

<span data-ttu-id="caf3c-275">다음은 몇 가지 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-275">Some of the challenges are:</span></span>

- <span data-ttu-id="caf3c-276">MRTK는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-276">MRTK is immutable</span></span>
  - <span data-ttu-id="caf3c-277">패키지 확인 중 제거 되지 않으면 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-277">Cannot make changes without them being removed during package resolution</span></span>
- <span data-ttu-id="caf3c-278">MRTK는 Unity 2018.4를 사용 하는 UPM 패키지를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-278">MRTK does not support UPM packages with Unity 2018.4</span></span>

### <a name="foundation-package"></a><span data-ttu-id="caf3c-279">Foundation 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-279">Foundation package</span></span>

<span data-ttu-id="caf3c-280">Foundation 패키지 ( `com.microsoft.mixedreality.toolkit.foundation` )는 혼합 현실 도구 키트의 기본을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-280">The foundation package (`com.microsoft.mixedreality.toolkit.foundation`) forms the basis of the Mixed Reality Toolkit.</span></span>

| <span data-ttu-id="caf3c-281">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-281">Folder</span></span> | <span data-ttu-id="caf3c-282">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-282">Component</span></span> | <span data-ttu-id="caf3c-283">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-283">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-284">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="caf3c-284">MRTK/Core</span></span> | | <span data-ttu-id="caf3c-285">인터페이스 및 형식 정의, 기본 클래스, 표준 셰이더.</span><span class="sxs-lookup"><span data-stu-id="caf3c-285">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="caf3c-286">MRTK/코어/공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-286">MRTK/Core/Providers</span></span> | | <span data-ttu-id="caf3c-287">플랫폼 독립적 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-287">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="caf3c-288">훈련</span><span class="sxs-lookup"><span data-stu-id="caf3c-288">Hands</span></span> | <span data-ttu-id="caf3c-289">직접 추적을 위한 기본 클래스 지원 및 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-289">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="caf3c-290">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="caf3c-290">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="caf3c-291">헤드 이동 및 핸드 추적 데이터 기록을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-291">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="caf3c-292">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="caf3c-292">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="caf3c-293">수동 및 눈 입력의 편집기 내 시뮬레이션 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-293">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="caf3c-294">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="caf3c-294">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="caf3c-295">3D 모델을 데이터로 사용 하는 공간 인식 관찰자</span><span class="sxs-lookup"><span data-stu-id="caf3c-295">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="caf3c-296">UnityInput</span><span class="sxs-lookup"><span data-stu-id="caf3c-296">UnityInput</span></span> | <span data-ttu-id="caf3c-297">Unity의 입력 API를 통해 구현된 일반적인 입력 디바이스(원통형, 마우스 등)입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-297">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="caf3c-298">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-298">MRTK/Providers</span></span> | | <span data-ttu-id="caf3c-299">플랫폼별 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-299">Platform specific data providers</span></span> |
| | <span data-ttu-id="caf3c-300">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="caf3c-300">LeapMotion</span></span> | <span data-ttu-id="caf3c-301">UltraLeap Leap Motion 컨트롤러에 대한 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-301">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="caf3c-302">OpenVR</span><span class="sxs-lookup"><span data-stu-id="caf3c-302">OpenVR</span></span> | <span data-ttu-id="caf3c-303">OpenVR 디바이스에 대한 지원.</span><span class="sxs-lookup"><span data-stu-id="caf3c-303">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="caf3c-304">Oculus</span><span class="sxs-lookup"><span data-stu-id="caf3c-304">Oculus</span></span> | <span data-ttu-id="caf3c-305">Quest와 같은 Oculus 디바이스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-305">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="caf3c-306">UnityAR</span><span class="sxs-lookup"><span data-stu-id="caf3c-306">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="caf3c-307">(실험적) 모바일 AR 디바이스에서 MRTK를 사용할 수 있도록 하는 카메라 설정 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-307">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="caf3c-308">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="caf3c-308">WindowsMixedReality</span></span> | <span data-ttu-id="caf3c-309">Microsoft HoloLens 및 몰입형 헤드셋을 포함하여 Windows Mixed Reality 디바이스에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="caf3c-309">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="caf3c-310">Windows</span><span class="sxs-lookup"><span data-stu-id="caf3c-310">Windows</span></span> | <span data-ttu-id="caf3c-311">Microsoft Windows 특정 API 지원(예: 음성 및 받아쓰기)</span><span class="sxs-lookup"><span data-stu-id="caf3c-311">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="caf3c-312">XR SDK</span><span class="sxs-lookup"><span data-stu-id="caf3c-312">XR SDK</span></span> | <span data-ttu-id="caf3c-313">(실험적) Unity 2019.3 이상에서 [Unity의 새로운 XR 프레임워크를](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-313">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="caf3c-314">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="caf3c-314">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="caf3c-315">실험적</span><span class="sxs-lookup"><span data-stu-id="caf3c-315">Experimental</span></span> | <span data-ttu-id="caf3c-316">셰이더, 사용자 인터페이스 컨트롤 및 개별 시스템 관리자를 비롯한 실험적 기능</span><span class="sxs-lookup"><span data-stu-id="caf3c-316">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="caf3c-317">기능</span><span class="sxs-lookup"><span data-stu-id="caf3c-317">Features</span></span> | <span data-ttu-id="caf3c-318">Foundation 패키지를 기반으로 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-318">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="caf3c-319">프로필</span><span class="sxs-lookup"><span data-stu-id="caf3c-319">Profiles</span></span> | <span data-ttu-id="caf3c-320">Microsoft Mixed Reality Toolkit 시스템 및 서비스에 대한 기본 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-320">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="caf3c-321">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="caf3c-321">StandardAssets</span></span> | <span data-ttu-id="caf3c-322">일반 자산; 모델, 질감, 재질 등</span><span class="sxs-lookup"><span data-stu-id="caf3c-322">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="caf3c-323">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="caf3c-323">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="caf3c-324">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-324">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="caf3c-325">VR 경계 지원을 구현 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-325">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="caf3c-326">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-326">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="caf3c-327">카메라 구성 및 관리를 구현 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-327">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="caf3c-328">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-328">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="caf3c-329">응용 프로그램 진단에서 시스템을 구현 합니다 (예: 시각적 프로파일러).</span><span class="sxs-lookup"><span data-stu-id="caf3c-329">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="caf3c-330">InputSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-330">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="caf3c-331">사용자 입력에 대 한 액세스 및 처리 지원을 제공 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-331">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="caf3c-332">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-332">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="caf3c-333">다중 장면 응용 프로그램 지원을 제공 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-333">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="caf3c-334">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-334">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="caf3c-335">사용자 환경을 인식 하기 위한 지원을 제공 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-335">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="caf3c-336">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="caf3c-336">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="caf3c-337">Teleporting에 대 한 지원을 제공 하는 시스템 (점프의 경험에 대 한 이동).</span><span class="sxs-lookup"><span data-stu-id="caf3c-337">System providing support for teleporting (moving about the experience in jumps).</span></span> |

<span data-ttu-id="caf3c-338">종속성:</span><span class="sxs-lookup"><span data-stu-id="caf3c-338">Dependencies:</span></span>

- <span data-ttu-id="caf3c-339">표준 자산 ( `com.microsoft.mixedreality.toolkit.standardassets` )</span><span class="sxs-lookup"><span data-stu-id="caf3c-339">Standard Assets (`com.microsoft.mixedreality.toolkit.standardassets`)</span></span>

### <a name="standard-assets"></a><span data-ttu-id="caf3c-340">표준 자산</span><span class="sxs-lookup"><span data-stu-id="caf3c-340">Standard Assets</span></span>

<span data-ttu-id="caf3c-341">표준 자산 패키지 ( `com.microsoft.mixedreality.toolkit.standardassets)` 은 다음을 비롯 한 모든 혼합 현실 환경에 권장 되는 구성 요소 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-341">The standard assets package (`com.microsoft.mixedreality.toolkit.standardassets)` is a collection of components that are recommended for all mixed reality experiences, including:</span></span>

- <span data-ttu-id="caf3c-342">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="caf3c-342">MRTK Standard shader</span></span>
- <span data-ttu-id="caf3c-343">MRTK 표준 셰이더를 사용 하는 기본 자료</span><span class="sxs-lookup"><span data-stu-id="caf3c-343">Basic materials using the MRTK Standard shader</span></span>
- <span data-ttu-id="caf3c-344">오디오 파일</span><span class="sxs-lookup"><span data-stu-id="caf3c-344">Audio files</span></span>
- <span data-ttu-id="caf3c-345">글꼴</span><span class="sxs-lookup"><span data-stu-id="caf3c-345">Fonts</span></span>
- <span data-ttu-id="caf3c-346">질감</span><span class="sxs-lookup"><span data-stu-id="caf3c-346">Textures</span></span>
- <span data-ttu-id="caf3c-347">아이콘</span><span class="sxs-lookup"><span data-stu-id="caf3c-347">Icons</span></span>

> [!Note]
> <span data-ttu-id="caf3c-348">어셈블리 정의에 따라 주요 변경 내용을 방지하기 위해 MRTK 표준 셰이더의 일부 기능을 제어하는 데 사용되는 스크립트는 표준 자산 패키지에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-348">To avoid breaking changes based on assembly definitions, the scripts used to control some features of the MRTK Standard shader are not included in the standard assets package.</span></span> <span data-ttu-id="caf3c-349">이러한 스크립트는 폴더의 기본 패키지에서 찾을 수 `MRTK/Core/Utilities/StandardShader` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-349">These scripts can be found in the foundation package in the `MRTK/Core/Utilities/StandardShader` folder.</span></span>

<span data-ttu-id="caf3c-350">Dependencies: none</span><span class="sxs-lookup"><span data-stu-id="caf3c-350">Dependencies: none</span></span>

### <a name="extension-packages"></a><span data-ttu-id="caf3c-351">확장 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-351">Extension packages</span></span>

<span data-ttu-id="caf3c-352">선택적 확장 `com.microsoft.mixedreality.toolkit.extensions)` 패키지(에는 MRTK의 기능을 확장하는 추가 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-352">The optional extensions package (`com.microsoft.mixedreality.toolkit.extensions)` contains additional components that expand the functionality of the MRTK.</span></span>

| <span data-ttu-id="caf3c-353">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-353">Folder</span></span> | <span data-ttu-id="caf3c-354">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-354">Component</span></span> | <span data-ttu-id="caf3c-355">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-355">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-356">MRTK/확장</span><span class="sxs-lookup"><span data-stu-id="caf3c-356">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="caf3c-357">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="caf3c-357">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="caf3c-358">굴절형 손에서 물리학 지원을 추가하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-358">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="caf3c-359">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="caf3c-359">LostTrackingService</span></span> | <span data-ttu-id="caf3c-360">Microsoft HoloLens 디바이스에서 손실 추적 전달을 간소화하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-360">Service that simplifies handing of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="caf3c-361">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="caf3c-361">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="caf3c-362">부드러운 장면 전환을 추가하는 것을 간소화하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-362">Service that simplifies adding smooth scene transitions.</span></span> |
| | <span data-ttu-id="caf3c-363">샘플~</span><span class="sxs-lookup"><span data-stu-id="caf3c-363">Samples~</span></span> | <span data-ttu-id="caf3c-364">샘플 장면 및 자산이 포함된 숨겨진(Unity 편집기) 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-364">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |

<span data-ttu-id="caf3c-365">예제 프로젝트가 포함된 패키지를 사용하는 프로세스에 대한 자세한 내용은 [Mixed Reality Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-365">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

<span data-ttu-id="caf3c-366">종속성:</span><span class="sxs-lookup"><span data-stu-id="caf3c-366">Dependencies:</span></span>

- <span data-ttu-id="caf3c-367">Foundation( `com.microsoft.mixedreality.toolkit.foundation` )</span><span class="sxs-lookup"><span data-stu-id="caf3c-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="tools-package"></a><span data-ttu-id="caf3c-368">도구 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-368">Tools package</span></span>

<span data-ttu-id="caf3c-369">선택적 도구 `com.microsoft.mixedreality.toolkit.tools)` 패키지(에는 혼합 현실 환경을 만드는 데 유용한 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-369">The optional tools package (`com.microsoft.mixedreality.toolkit.tools)` contains tools that are useful for creating mixed reality experiences.</span></span> <span data-ttu-id="caf3c-370">일반적으로 이러한 도구는 편집기 구성 요소이며 해당 코드는 애플리케이션의 일부로 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-370">In general, these tools are editor components and their code does not ship as part of an application.</span></span>

| <span data-ttu-id="caf3c-371">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-371">Folder</span></span> | <span data-ttu-id="caf3c-372">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-372">Component</span></span> | <span data-ttu-id="caf3c-373">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-373">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-374">MRTK/도구</span><span class="sxs-lookup"><span data-stu-id="caf3c-374">MRTK/Tools</span></span> | |
| | <span data-ttu-id="caf3c-375">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-375">BuildWindow</span></span> | <span data-ttu-id="caf3c-376">UWP 응용 프로그램 빌드 및 배포 프로세스를 간소화 하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-376">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="caf3c-377">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-377">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="caf3c-378">프로젝트의 자산에 대 한 종속성 그래프를 만드는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-378">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="caf3c-379">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="caf3c-379">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="caf3c-380">확장 서비스를 만드는 데 도움이 되는 마법사입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-380">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="caf3c-381">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-381">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="caf3c-382">사용 되지 않는 MRTK 구성 요소를 사용 하는 코드 업데이트에 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-382">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="caf3c-383">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-383">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="caf3c-384">Unity에서 최상의 성능을 위해 혼합 현실 프로젝트를 자동으로 구성 하는 데 도움이 되는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-384">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="caf3c-385">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="caf3c-385">ReserializeAssetsUtility</span></span> | <span data-ttu-id="caf3c-386">특정 Unity 파일을 다시 serialize 하기 위한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-386">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="caf3c-387">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="caf3c-387">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="caf3c-388">개발자가 하드웨어 컨트롤러에 대 한 Unity 매핑을 신속 하 게 결정할 수 있도록 하는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-388">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="caf3c-389">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="caf3c-389">ScreenshotUtility</span></span> | <span data-ttu-id="caf3c-390">Unity 편집기에서 응용 프로그램 이미지를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-390">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="caf3c-391">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="caf3c-391">TextureCombinerWindow</span></span> | <span data-ttu-id="caf3c-392">그래픽 질감을 결합 하는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-392">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="caf3c-393">도구 상자</span><span class="sxs-lookup"><span data-stu-id="caf3c-393">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="caf3c-394">MRTK UX 구성 요소를 쉽게 검색 하 고 사용할 수 있도록 하는 UI입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-394">UI that makes it easy to discover and use MRTK UX components.</span></span> |

<span data-ttu-id="caf3c-395">종속성:</span><span class="sxs-lookup"><span data-stu-id="caf3c-395">Dependencies:</span></span>

- <span data-ttu-id="caf3c-396">Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )</span><span class="sxs-lookup"><span data-stu-id="caf3c-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="test-utilities-package"></a><span data-ttu-id="caf3c-397">유틸리티 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="caf3c-397">Test utilities package</span></span>

<span data-ttu-id="caf3c-398">선택적 테스트 유틸리티 패키지 ()에는 `com.microsoft.mixedreality.toolkit.testutilities` 개발자가 재생 모드 테스트를 쉽게 만들 수 있도록 하는 도우미 스크립트 컬렉션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-398">The optional test utilities package (`com.microsoft.mixedreality.toolkit.testutilities`) contains a collection of helper scripts that enable developers to easily create play mode tests.</span></span> <span data-ttu-id="caf3c-399">이러한 유틸리티는 MRTK 구성 요소를 만드는 개발자에게 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-399">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="caf3c-400">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-400">Folder</span></span> | <span data-ttu-id="caf3c-401">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-401">Component</span></span> | <span data-ttu-id="caf3c-402">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-402">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-403">MRTK/테스트</span><span class="sxs-lookup"><span data-stu-id="caf3c-403">MRTK/Tests</span></span> | |
| | <span data-ttu-id="caf3c-404">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="caf3c-404">TestUtilities</span></span> | <span data-ttu-id="caf3c-405">손 시뮬레이션 유틸리티를 포함하여 재생 모드 테스트 만들기를 간소화하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-405">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

<span data-ttu-id="caf3c-406">종속성:</span><span class="sxs-lookup"><span data-stu-id="caf3c-406">Dependencies:</span></span>

- <span data-ttu-id="caf3c-407">Foundation( `com.microsoft.mixedreality.toolkit.foundation` )</span><span class="sxs-lookup"><span data-stu-id="caf3c-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="examples-package"></a><span data-ttu-id="caf3c-408">예제 패키지</span><span class="sxs-lookup"><span data-stu-id="caf3c-408">Examples package</span></span>

<span data-ttu-id="caf3c-409">예제 패키지( `com.microsoft.mixedreality.toolkit.examples` )는 개발자가 관심 있는 예제만 가져올 수 있도록 구조화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-409">The examples package (`com.microsoft.mixedreality.toolkit.examples`), is structured to allow developers to import only the examples of interest.</span></span>

<span data-ttu-id="caf3c-410">예제 프로젝트가 포함된 패키지를 사용하는 프로세스에 대한 자세한 내용은 [Mixed Reality Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-410">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

| <span data-ttu-id="caf3c-411">폴더</span><span class="sxs-lookup"><span data-stu-id="caf3c-411">Folder</span></span> | <span data-ttu-id="caf3c-412">구성 요소</span><span class="sxs-lookup"><span data-stu-id="caf3c-412">Component</span></span> | <span data-ttu-id="caf3c-413">설명</span><span class="sxs-lookup"><span data-stu-id="caf3c-413">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="caf3c-414">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="caf3c-414">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="caf3c-415">샘플~</span><span class="sxs-lookup"><span data-stu-id="caf3c-415">Samples~</span></span> | <span data-ttu-id="caf3c-416">샘플 장면 및 자산이 포함된 숨겨진(Unity 편집기) 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-416">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |
| | <span data-ttu-id="caf3c-417">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="caf3c-417">StandardAssets</span></span> | <span data-ttu-id="caf3c-418">여러 데모 장면에서 공유하는 공통 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="caf3c-418">Common assets shared by multiple demo scenes.</span></span> |

<span data-ttu-id="caf3c-419">종속성:</span><span class="sxs-lookup"><span data-stu-id="caf3c-419">Dependencies:</span></span>

- <span data-ttu-id="caf3c-420">Foundation( `com.microsoft.mixedreality.toolkit.foundation` )</span><span class="sxs-lookup"><span data-stu-id="caf3c-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>
- <span data-ttu-id="caf3c-421">확장 기능(`com.microsoft.mixedreality.toolkit.extensions`)</span><span class="sxs-lookup"><span data-stu-id="caf3c-421">Extensions (`com.microsoft.mixedreality.toolkit.extensions`)</span></span>

## <a name="see-also"></a><span data-ttu-id="caf3c-422">참고 항목</span><span class="sxs-lookup"><span data-stu-id="caf3c-422">See also</span></span>

- [<span data-ttu-id="caf3c-423">아키텍처 개요</span><span class="sxs-lookup"><span data-stu-id="caf3c-423">Architecture Overview</span></span>](../architecture/overview.md)
- [<span data-ttu-id="caf3c-424">시스템, 확장 서비스 및 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="caf3c-424">Systems, Extension Services and Data Providers</span></span>](../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="caf3c-425">Mixed Reality Toolkit 및 Unity 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="caf3c-425">Mixed Reality Toolkit and Unity Package Manager</span></span>](../configuration/usingupm.md)
