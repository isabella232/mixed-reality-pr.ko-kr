---
title: Unity의 OpenXR 플러그 인 지원 기능
description: Unity에서 혼합 현실 개발에 대해 OpenXR에서 지 원하는 기능을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 1fbc03fe446d9e9619348618c6d0b9aab828fe1a
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937429"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="f33de-104">Unity의 혼합 현실 OpenXR 지원 되는 기능</span><span class="sxs-lookup"><span data-stu-id="f33de-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="f33de-105">**Mixed Reality OpenXR 플러그 인** 패키지는 Unity의 **OpenXR 플러그 인** 을 확장 한 것으로, HoloLens 2 및 Windows Mixed Reality 헤드셋의 기능 모음을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="f33de-106">계속 하기 전에 Unity 프로젝트가 [OpenXR에 대해 구성](openxr-getting-started.md)되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-106">Before continuing, make sure your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="f33de-107">지원되는 내용</span><span class="sxs-lookup"><span data-stu-id="f33de-107">What's supported</span></span>

<span data-ttu-id="f33de-108">현재 지원 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-108">The following features are currently supported:</span></span>

* <span data-ttu-id="f33de-109">HoloLens 2 용 UWP 응용 프로그램을 지원 하 고 HoloLens 2 응용 프로그램 모델을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="f33de-110">최신 컨트롤러 프로필 및 holographic app remoting과 함께 Windows Mixed Reality 헤드셋에 대해 Win32 VR 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="f33de-111">앵커와 바인딩되지 않은 공간을 사용한 세계 크기 조정 추적.</span><span class="sxs-lookup"><span data-stu-id="f33de-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="f33de-112">[저장소 API를 고정 하 여](spatial-anchors-in-unity.md) HoloLens 2 로컬 저장소에 앵커를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="f33de-113">새 HP 반향 G2 컨트롤러를 포함 하 여 [동작 컨트롤러 및 직접 상호 작용](#motion-controller-and-hand-interactions).</span><span class="sxs-lookup"><span data-stu-id="f33de-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="f33de-114">26 개의 조인트와 조인트 반지름 입력을 사용 하 여 직접 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="f33de-115">HoloLens 2의 눈 응시 상호 작용입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="f33de-116">HoloLens 2에서 사진/비디오 (PV) 카메라를 찾는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="f33de-117">혼합 현실 PV 카메라를 통한 세 번째 눈동자 렌더링을 사용 하 여 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="f33de-118">는 [Holographic Remoting 앱을 사용 하 여 HoloLens 2에 대 한 "Play"를](#holographic-remoting-in-unity-editor-play-mode)지원 하므로 개발자는 장치에 빌드 및 배포 하지 않고도 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="f33de-119">[Mrtk OpenXR 공급자 지원을](openxr-getting-started.md#using-mrtk-with-openxr-support)통해 Mrtk Unity 2.5.3 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="f33de-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="f33de-121">(0.1.3에 추가 됨) 빌드 및 배포 된 Windows 독립 실행형 앱에서 [데스크톱 앱 Holographic 원격](holographic-remoting-desktop.md) 을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="f33de-122">(0.1.4에 추가 됨) SpatialGraphNode을 통해 HoloLens2에서 [QR 코드 추적](#qr-codes) 을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>
* <span data-ttu-id="f33de-123">(0.2.0에 추가 됨) Holographic Remoting에서 **앵커** 지원</span><span class="sxs-lookup"><span data-stu-id="f33de-123">(Added in 0.2.0) Supports **Anchor** in Holographic Remoting</span></span>
* <span data-ttu-id="f33de-124">(0.2.0에 추가 됨) **손을 조인트 및 손 모양 추적을** 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-124">(Added in 0.2.0) Supports both **hand joints and hand mesh tracking**</span></span>
* <span data-ttu-id="f33de-125">(0.2.0에 추가 됨) 평면 검색을 위한 **Ar설계도 Esubsystems** 를 지원 하 고 **ARRaycastManager** 를 사용 하 여 홀로그램을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-125">(Added in 0.2.0) Supports **ARPlaneSubsystems** for plane detection and place hologram using **ARRaycastManager**.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="f33de-126">Holographic 원격 설치</span><span class="sxs-lookup"><span data-stu-id="f33de-126">Holographic Remoting setup</span></span>

1. <span data-ttu-id="f33de-127">먼저 HoloLens 2의 Microsoft Store에서 [Holographic Remoting Player 앱을 설치](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-127">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="f33de-128">HoloLens 2에서 Holographic 원격 플레이어 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-128">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="f33de-129">OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-129">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="f33de-131">Unity 편집기 재생 모드의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="f33de-131">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="f33de-132">Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 패키지 하 여 HoloLens 2 장치에 배포 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-132">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="f33de-133">한 가지 해결 방법은 Holographic Editor 원격 기능을 사용 하도록 설정 하는 것입니다 .이 기능을 사용 하면 네트워크를 통해 HoloLens 2 장치에 직접 "재생" 모드를 사용 하 여 c # 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-133">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="f33de-134">이 시나리오에서는 UWP 패키지를 빌드하여 원격 장치에 배포 하는 오버 헤드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-134">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="f33de-135">[Holographic 원격 설치](#holographic-remoting-setup) 의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-135">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="f33de-136">**편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-136">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![XR 플러그 인 관리가 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

3. <span data-ttu-id="f33de-138">**OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-138">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="f33de-139">**Holographic Editor 원격** 작업 확인란을 선택 하 고 Holographic remoting 앱에서 가져온 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-139">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![기능이 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

<span data-ttu-id="f33de-141">이제 "재생" 단추를 클릭 하 여 HoloLens의 Holographic Remoting 앱에 Unity 앱을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-141">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="f33de-142">[Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-142">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="f33de-143">버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-143">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="f33de-144">이 기능은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-144">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="f33de-145">동작 컨트롤러 및 직접 상호 작용</span><span class="sxs-lookup"><span data-stu-id="f33de-145">Motion controller and hand interactions</span></span>

<span data-ttu-id="f33de-146">Unity의 혼합 현실 상호 작용에 대 한 기본 사항을 알아보려면 unity [XR 입력](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f33de-146">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="f33de-147">이 Unity 설명서에서는 컨트롤러 특정 입력에서 보다 일반화할 수 있는 **Inputfeatureusage** s에 대 한 매핑, 사용 가능한 XR 입력을 식별 하 고 분류 하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-147">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="f33de-148">Mixed Reality OpenXR 플러그 인은 아래에 설명 된 대로 표준 **Inputfeatureusage** 에 매핑되는 추가 입력 상호 작용 프로필을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-148">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="f33de-149">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="f33de-149">InputFeatureUsage</span></span> | <span data-ttu-id="f33de-150">HP 반향 G2 컨트롤러 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="f33de-150">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="f33de-151">HoloLens 손 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="f33de-151">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="f33de-152">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="f33de-152">primary2DAxis</span></span> | <span data-ttu-id="f33de-153">조이스틱이</span><span class="sxs-lookup"><span data-stu-id="f33de-153">Joystick</span></span> | |
| <span data-ttu-id="f33de-154">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="f33de-154">primary2DAxisClick</span></span> | <span data-ttu-id="f33de-155">조이스틱-클릭</span><span class="sxs-lookup"><span data-stu-id="f33de-155">Joystick - Click</span></span> | |
| <span data-ttu-id="f33de-156">트리거</span><span class="sxs-lookup"><span data-stu-id="f33de-156">trigger</span></span> | <span data-ttu-id="f33de-157">트리거</span><span class="sxs-lookup"><span data-stu-id="f33de-157">Trigger</span></span>  | |
| <span data-ttu-id="f33de-158">그리퍼</span><span class="sxs-lookup"><span data-stu-id="f33de-158">grip</span></span> | <span data-ttu-id="f33de-159">그리퍼</span><span class="sxs-lookup"><span data-stu-id="f33de-159">Grip</span></span> | <span data-ttu-id="f33de-160">공중 탭 또는 꽉의</span><span class="sxs-lookup"><span data-stu-id="f33de-160">Air tap or squeeze</span></span> |
| <span data-ttu-id="f33de-161">primaryButton</span><span class="sxs-lookup"><span data-stu-id="f33de-161">primaryButton</span></span> | <span data-ttu-id="f33de-162">[X/A]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="f33de-162">[X/A] - Press</span></span> | <span data-ttu-id="f33de-163">에어 탭</span><span class="sxs-lookup"><span data-stu-id="f33de-163">Air tap</span></span> |
| <span data-ttu-id="f33de-164">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="f33de-164">secondaryButton</span></span> | <span data-ttu-id="f33de-165">[Y/B]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="f33de-165">[Y/B] - Press</span></span> | |
| <span data-ttu-id="f33de-166">gripButton</span><span class="sxs-lookup"><span data-stu-id="f33de-166">gripButton</span></span> | <span data-ttu-id="f33de-167">그립-누름</span><span class="sxs-lookup"><span data-stu-id="f33de-167">Grip - Press</span></span> | |
| <span data-ttu-id="f33de-168">triggerButton</span><span class="sxs-lookup"><span data-stu-id="f33de-168">triggerButton</span></span> | <span data-ttu-id="f33de-169">트리거-누르기</span><span class="sxs-lookup"><span data-stu-id="f33de-169">Trigger - Press</span></span> | |
| <span data-ttu-id="f33de-170">menuButton</span><span class="sxs-lookup"><span data-stu-id="f33de-170">menuButton</span></span> | <span data-ttu-id="f33de-171">메뉴</span><span class="sxs-lookup"><span data-stu-id="f33de-171">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="f33de-172">목표 및 그립 포즈</span><span class="sxs-lookup"><span data-stu-id="f33de-172">Aim and Grip Poses</span></span>

<span data-ttu-id="f33de-173">OpenXR 입력 상호 작용을 통해 두 가지 포즈 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-173">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="f33de-174">손으로 개체를 렌더링 하는 그립</span><span class="sxs-lookup"><span data-stu-id="f33de-174">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="f33de-175">세계를 가리키는 목표입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-175">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="f33de-176">이 디자인 및 두 포즈 간의 차이점에 대 한 자세한 내용은 [OpenXR 사양 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-176">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="f33de-177">InputFeatureUsages **Deviceposition**, **devicerDeviceAngularVelocity ation**, **Devicevelocation** 및  에서 제공 하는 포즈는 모두 OpenXR **그립** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-177">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="f33de-178">그립 포즈와 관련 된 InputFeatureUsages은 Unity의 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-178">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="f33de-179">InputFeatureUsages **Pointerposition**, **pointerposition**, **pointerposition** 에서 제공 하는 포즈는  모두 OpenXR **목표** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-179">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="f33de-180">이러한 InputFeatureUsages은 포함 된 c # 파일에 정의 되어 있지 않으므로 다음과 같이 사용자 고유의 InputFeatureUsages을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-180">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="f33de-181">Haptics</span><span class="sxs-lookup"><span data-stu-id="f33de-181">Haptics</span></span>

<span data-ttu-id="f33de-182">Unity의 XR 입력 시스템에서 haptics를 사용 하는 방법에 대 한 자세한 내용은 unity의 unity [설명서 XR haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f33de-182">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="f33de-183">QR 코드</span><span class="sxs-lookup"><span data-stu-id="f33de-183">QR codes</span></span>

<span data-ttu-id="f33de-184">HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-184">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="f33de-185">자세한 내용은 [QR 코드 추적](../platform-capabilities-and-apis/qr-code-tracking.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-185">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="f33de-186">OpenXR 플러그 인을 사용 하는 경우 [ `SpatialGraphNodeId` qr api에서](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) 를 잡고 API를 사용 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` 하 여 qr 코드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-186">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="f33de-187">참조를 위해 GitHub에는 [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)에 대 한 자세한 사용 설명이 포함 된 [QR 추적 샘플 프로젝트가](https://github.com/yl-msft/QRTracking) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-187">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="f33de-188">출시 예정</span><span class="sxs-lookup"><span data-stu-id="f33de-188">What's coming soon</span></span>

<span data-ttu-id="f33de-189">혼합 현실 OpenXR 플러그 인 **버전 0.1.0** 에는 다음과 같은 문제와 누락 된 기능이 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-189">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="f33de-190">이 작업을 수행 하 고 있으며 향후 릴리스에서 수정 사항 및 새로운 기능을 출시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-190">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="f33de-191">**Azure 공간 앵커** 지원은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-191">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="f33de-192">**ARM64** 는 HoloLens 2 앱에 대해 유일 하 게 지원 되는 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-192">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="f33de-193">**ARM** 플랫폼은 향후 릴리스에서 출시 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-193">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f33de-194">문제 해결</span><span class="sxs-lookup"><span data-stu-id="f33de-194">Troubleshooting</span></span>

<span data-ttu-id="f33de-195">HoloLens 2에서 Unity 앱을 일시 중단 하 고 다시 시작 하는 경우 앱이 올바르게 다시 시작 될 수 없습니다. 그러면 HoloLens 보기에서 4 개의 회전 점이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-195">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="f33de-196">OpenXR 프로젝트 설정에서 해결 방법으로 **깊이 전송 모드** 를 **없음** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33de-196">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
