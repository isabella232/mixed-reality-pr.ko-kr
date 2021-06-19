---
title: Unity에서 OpenXR 플러그 인 지원 기능
description: Unity에서 혼합 현실 개발을 위해 OpenXR이 지원하는 기능을 검색합니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: c9d52f9529cabeaf912fffa6efc6599a9041a929
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112398056"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="86d56-104">Unity에서 OpenXR 지원 기능 Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="86d56-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="86d56-105">**Mixed Reality OpenXR 플러그 인** 패키지는 Unity **OpenXR 플러그 인의** 확장이며 HoloLens 2 및 Windows Mixed Reality 헤드셋용 기능 모음을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="86d56-106">계속하기 전에 Unity 프로젝트가 [OpenXR 에 대해 구성되어](openxr-getting-started.md)있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-106">Before continuing, make sure your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="86d56-107">지원되는 내용</span><span class="sxs-lookup"><span data-stu-id="86d56-107">What's supported</span></span>

<span data-ttu-id="86d56-108">현재 지원되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-108">The following features are currently supported:</span></span>

* <span data-ttu-id="86d56-109">HoloLens 2 UWP 애플리케이션을 지원하고 HoloLens 2 애플리케이션 모델에 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="86d56-110">최신 컨트롤러 프로필 및 홀로그램 앱 remoting을 Windows Mixed Reality 헤드셋용 Win32 VR 애플리케이션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="86d56-111">앵커 및 무제한 공간을 사용하는 세계 크기 조정 추적.</span><span class="sxs-lookup"><span data-stu-id="86d56-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="86d56-112">HoloLens 2 로컬 [스토리지에 앵커를 유지하도록 스토리지 API를 고정합니다.](spatial-anchors-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="86d56-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="86d56-113">새 HP Reverb G2 컨트롤러를 포함한 모션 컨트롤러 [및 손 상호 작용.](#motion-controller-and-hand-interactions)</span><span class="sxs-lookup"><span data-stu-id="86d56-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="86d56-114">26개의 조인트 및 조인 반경 입력을 사용하는 굴절형 손 추적</span><span class="sxs-lookup"><span data-stu-id="86d56-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="86d56-115">HoloLens 2 시선 응시 상호 작용</span><span class="sxs-lookup"><span data-stu-id="86d56-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="86d56-116">HoloLens 2 사진/비디오(PV) 카메라 찾기</span><span class="sxs-lookup"><span data-stu-id="86d56-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="86d56-117">PV 카메라를 통해 세 번째 시선 렌더링을 사용하는 혼합 현실 캡처.</span><span class="sxs-lookup"><span data-stu-id="86d56-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="86d56-118">개발자가 빌드하고 디바이스에 배포하지 않고도 스크립트를 디버그할 수 있도록 [Holographic Remoting 앱과 HoloLens 2 "Play"를](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="86d56-119">[MRTK OpenXR 공급자 지원을 통해 MRTK](openxr-getting-started.md#using-mrtk-with-openxr-support)Unity 2.5.3 이상과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="86d56-120">Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 이상과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="86d56-121">(0.1.3에 추가) 빌드되고 배포된 Windows 독립 실행형 [앱에서 데스크톱 앱 Holographic Remoting을](holographic-remoting-desktop.md) 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="86d56-122">(0.1.4에 추가) SpatialGraphNode를 통해 HoloLens2에서 [QR 코드 추적을](#qr-codes) 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>
* <span data-ttu-id="86d56-123">(0.2.0에 추가) 홀로그램 Remoting에서 **앵커** 지원</span><span class="sxs-lookup"><span data-stu-id="86d56-123">(Added in 0.2.0) Supports **Anchor** in Holographic Remoting</span></span>
* <span data-ttu-id="86d56-124">(0.2.0에 추가) **손받침 및 손 메시 추적을 모두 지원합니다.**</span><span class="sxs-lookup"><span data-stu-id="86d56-124">(Added in 0.2.0) Supports both **hand joints and hand mesh tracking**</span></span>
* <span data-ttu-id="86d56-125">(0.2.0에 추가) **ARRaycastManager를** 사용하여 평면 감지 및 홀로그램 배치를 위한 **ARPlaneSubsystems를** 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-125">(Added in 0.2.0) Supports **ARPlaneSubsystems** for plane detection and place hologram using **ARRaycastManager**.</span></span>
* <span data-ttu-id="86d56-126">(0.9.0) 공간 매핑을 위해 **XRMeshSubsystem** 및 **ARMeshManager를** 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-126">(0.9.0) Supports **XRMeshSubsystem** and **ARMeshManager** for spatial mapping.</span></span>
* <span data-ttu-id="86d56-127">(0.9.0에 추가) Windows용 Azure Spatial Anchors SDK 플러그 인을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-127">(Added in 0.9.0) Supports the Azure Spatial Anchors SDK for Windows plugin.</span></span> <span data-ttu-id="86d56-128">자세한 내용은 [GitHub의 Mixed Reality + OpenXR Azure Spatial Anchors 샘플 프로젝트를 참조하세요.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)</span><span class="sxs-lookup"><span data-stu-id="86d56-128">For more information, see the [Mixed Reality + OpenXR Azure Spatial Anchors sample project on GitHub](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample).</span></span>
* <span data-ttu-id="86d56-129">(0.9.1에 추가) 빌드되고 배포된 Windows UWP 앱에서 데스크톱 앱 Holographic Remoting을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-129">(Added in 0.9.1) Supports desktop app Holographic Remoting from a built and deployed Windows UWP app.</span></span>
* <span data-ttu-id="86d56-130">(0.9.4에 추가) HoloLens 2 애플리케이션용 ARM64 외에도 ARM 플랫폼을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-130">(Added in 0.9.4) Supports ARM platform in addition to ARM64 for HoloLens 2 application.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="86d56-131">모션 컨트롤러 및 손 상호 작용</span><span class="sxs-lookup"><span data-stu-id="86d56-131">Motion controller and hand interactions</span></span>

<span data-ttu-id="86d56-132">Unity의 혼합 현실 상호 작용에 대한 기본 사항 알아보려면 Unity [XR 입력에 대한 Unity 설명서를 참조하세요.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="86d56-132">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="86d56-133">이 Unity 설명서에서는 컨트롤러별 입력에서 보다 일반적인 **InputFeatureUsage로의** 매핑, 사용 가능한 XR 입력을 식별하고 분류하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-133">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="86d56-134">Mixed Reality OpenXR 플러그 인은 아래에 설명된 대로 표준 **InputFeatureUsage에** 매핑된 추가 입력 상호 작용 프로필을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-134">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="86d56-135">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="86d56-135">InputFeatureUsage</span></span> | <span data-ttu-id="86d56-136">HP Reverb G2 컨트롤러(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="86d56-136">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="86d56-137">HoloLens Hand(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="86d56-137">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="86d56-138">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="86d56-138">primary2DAxis</span></span> | <span data-ttu-id="86d56-139">조이스틱</span><span class="sxs-lookup"><span data-stu-id="86d56-139">Joystick</span></span> | |
| <span data-ttu-id="86d56-140">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="86d56-140">primary2DAxisClick</span></span> | <span data-ttu-id="86d56-141">운정 - 클릭</span><span class="sxs-lookup"><span data-stu-id="86d56-141">Joystick - Click</span></span> | |
| <span data-ttu-id="86d56-142">트리거</span><span class="sxs-lookup"><span data-stu-id="86d56-142">trigger</span></span> | <span data-ttu-id="86d56-143">트리거</span><span class="sxs-lookup"><span data-stu-id="86d56-143">Trigger</span></span>  | |
| <span data-ttu-id="86d56-144">그립</span><span class="sxs-lookup"><span data-stu-id="86d56-144">grip</span></span> | <span data-ttu-id="86d56-145">그립</span><span class="sxs-lookup"><span data-stu-id="86d56-145">Grip</span></span> | <span data-ttu-id="86d56-146">에어 탭 또는 에어 탭</span><span class="sxs-lookup"><span data-stu-id="86d56-146">Air tap or squeeze</span></span> |
| <span data-ttu-id="86d56-147">primaryButton</span><span class="sxs-lookup"><span data-stu-id="86d56-147">primaryButton</span></span> | <span data-ttu-id="86d56-148">[X/A] - 누르기</span><span class="sxs-lookup"><span data-stu-id="86d56-148">[X/A] - Press</span></span> | <span data-ttu-id="86d56-149">에어 탭</span><span class="sxs-lookup"><span data-stu-id="86d56-149">Air tap</span></span> |
| <span data-ttu-id="86d56-150">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="86d56-150">secondaryButton</span></span> | <span data-ttu-id="86d56-151">[Y/B] - 누르기</span><span class="sxs-lookup"><span data-stu-id="86d56-151">[Y/B] - Press</span></span> | |
| <span data-ttu-id="86d56-152">gripButton</span><span class="sxs-lookup"><span data-stu-id="86d56-152">gripButton</span></span> | <span data-ttu-id="86d56-153">그립 - 누르기</span><span class="sxs-lookup"><span data-stu-id="86d56-153">Grip - Press</span></span> | |
| <span data-ttu-id="86d56-154">triggerButton</span><span class="sxs-lookup"><span data-stu-id="86d56-154">triggerButton</span></span> | <span data-ttu-id="86d56-155">트리거 - 누르기</span><span class="sxs-lookup"><span data-stu-id="86d56-155">Trigger - Press</span></span> | |
| <span data-ttu-id="86d56-156">menuButton</span><span class="sxs-lookup"><span data-stu-id="86d56-156">menuButton</span></span> | <span data-ttu-id="86d56-157">메뉴</span><span class="sxs-lookup"><span data-stu-id="86d56-157">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="86d56-158">목표 및 그립 자세</span><span class="sxs-lookup"><span data-stu-id="86d56-158">Aim and Grip Poses</span></span>

<span data-ttu-id="86d56-159">OpenXR 입력 상호 작용을 통해 두 가지 자세 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-159">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="86d56-160">손에서 개체를 렌더링하기 위한 그립 자세</span><span class="sxs-lookup"><span data-stu-id="86d56-160">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="86d56-161">목표는 세계를 가리키는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-161">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="86d56-162">이 디자인과 두 가지 자세 간의 차이점에 대한 자세한 내용은 [OpenXR 사양 - 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-162">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="86d56-163">InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** 및 **DeviceAngularVelocity에서** 제공하는 자세는 모두 OpenXR **그립** 자세를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-163">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="86d56-164">그립 자세와 관련된 InputFeatureUsages는 Unity의 [CommonUsages 에 정의되어 있습니다.](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)</span><span class="sxs-lookup"><span data-stu-id="86d56-164">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="86d56-165">InputFeatureUsages **PointerPosition,** **PointerRotation,** PointerVelocity 및 **PointerAngularVelocity에서** 제공하는 자세는 모두 OpenXR **목표** 자세를 나타냅니다. </span><span class="sxs-lookup"><span data-stu-id="86d56-165">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="86d56-166">이러한 InputFeatureUsages는 포함된 C# 파일에 정의되지 않으므로 다음과 같이 고유한 InputFeatureUsages를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-166">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="86d56-167">햅 틱</span><span class="sxs-lookup"><span data-stu-id="86d56-167">Haptics</span></span>

<span data-ttu-id="86d56-168">Unity의 XR 입력 시스템에서 haptics 사용에 대한 자세한 내용은 Unity [XR 입력을 위한 Unity 설명서 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-168">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="86d56-169">QR 코드</span><span class="sxs-lookup"><span data-stu-id="86d56-169">QR codes</span></span>

<span data-ttu-id="86d56-170">HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-170">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="86d56-171">자세한 내용은 [QR 코드 추적](../platform-capabilities-and-apis/qr-code-tracking.md) 설명서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-171">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="86d56-172">OpenXR 플러그 인을 사용하는 경우 [ `SpatialGraphNodeId` QR API에서](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) 를 잡고 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API를 사용하여 QR 코드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-172">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="86d56-173">참고로 [GitHub에는](https://github.com/yl-msft/QRTracking) [ `SpatialGraphNode` API에](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)대한 자세한 사용 설명이 있는 QR 추적 샘플 프로젝트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-173">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="86d56-174">문제 해결</span><span class="sxs-lookup"><span data-stu-id="86d56-174">Troubleshooting</span></span>

<span data-ttu-id="86d56-175">HoloLens 2 Unity 앱을 일시 중단했다가 다시 시작하면 앱이 올바르게 다시 시작되지 않아 HoloLens 보기에서 4개의 회전 점이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-175">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="86d56-176">해결 방법으로 OpenXR 프로젝트 설정에서 **깊이 제출 모드를** **없음으로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86d56-176">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
