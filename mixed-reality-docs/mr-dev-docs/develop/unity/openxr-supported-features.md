---
title: Unity의 OpenXR 플러그 인 지원 기능
description: Unity에서 혼합 현실 개발에 대해 OpenXR에서 지 원하는 기능을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: d65bab65bcb06f7ccba522461e04062458e7400c
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108846"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="96930-104">Unity의 혼합 현실 OpenXR 지원 되는 기능</span><span class="sxs-lookup"><span data-stu-id="96930-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="96930-105">**Mixed Reality OpenXR 플러그 인** 패키지는 Unity의 **OpenXR 플러그 인** 을 확장 한 것으로, HoloLens 2 및 Windows Mixed Reality 헤드셋의 기능 모음을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="96930-106">계속 하기 전에 **unity 2020.2** 이상, **OpenXR 플러그 인 버전 0.1.2** 이상을 설치 했는지 확인 하 고 unity 프로젝트가 [OpenXR에 대해 구성](openxr-getting-started.md)되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.2** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="96930-107">지원되는 내용</span><span class="sxs-lookup"><span data-stu-id="96930-107">What's supported</span></span>

<span data-ttu-id="96930-108">현재 지원 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-108">The following features are currently supported:</span></span>

* <span data-ttu-id="96930-109">HoloLens 2 용 UWP 응용 프로그램을 지원 하 고 HoloLens 2 응용 프로그램 모델을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="96930-110">최신 컨트롤러 프로필 및 holographic app remoting과 함께 Windows Mixed Reality 헤드셋에 대해 Win32 VR 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="96930-111">앵커와 바인딩되지 않은 공간을 사용한 세계 크기 조정 추적.</span><span class="sxs-lookup"><span data-stu-id="96930-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="96930-112">[저장소 API를 고정 하 여](#anchors-and-anchor-persistence) HoloLens 2 로컬 저장소에 앵커를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="96930-113">새 HP 반향 G2 컨트롤러를 포함 하 여 [동작 컨트롤러 및 직접 상호 작용](#motion-controller-and-hand-interactions).</span><span class="sxs-lookup"><span data-stu-id="96930-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="96930-114">26 개의 조인트와 조인트 반지름 입력을 사용 하 여 직접 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="96930-115">HoloLens 2의 눈 응시 상호 작용입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="96930-116">HoloLens 2에서 사진/비디오 (PV) 카메라를 찾는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="96930-117">혼합 현실 PV 카메라를 통한 세 번째 눈동자 렌더링을 사용 하 여 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="96930-118">는 [Holographic Remoting 앱을 사용 하 여 HoloLens 2에 대 한 "Play"를](#holographic-remoting-in-unity-editor-play-mode)지원 하므로 개발자는 장치에 빌드 및 배포 하지 않고도 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="96930-119">[Mrtk OpenXR 공급자 지원을](openxr-getting-started.md#using-mrtk-with-openxr-support)통해 Mrtk Unity 2.5.3 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="96930-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="96930-121">Unity 편집기 재생 모드의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="96930-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="96930-122">Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 패키지 하 여 HoloLens 2 장치에 배포 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="96930-123">한 가지 해결 방법은 Holographic Editor 원격 기능을 사용 하도록 설정 하는 것입니다 .이를 통해 네트워크를 통해 HoloLens 2 장치에 직접 "재생" 모드를 사용 하 여 c # 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="96930-124">이 시나리오에서는 UWP 패키지를 빌드하여 원격 장치에 배포 하는 오버 헤드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="96930-125">먼저 HoloLens 2의 스토어에서 [Holographic Remoting Player 앱을 설치 해야 합니다](https://www.microsoft.com/store/productId/9NBLGGH4SV40) .</span><span class="sxs-lookup"><span data-stu-id="96930-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="96930-126">HoloLens 2에서 Holographic 원격 플레이어 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="96930-127">OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

3. <span data-ttu-id="96930-129">**편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![XR 플러그 인 관리가 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

4. <span data-ttu-id="96930-131">**OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="96930-132">**Holographic Editor 원격** 작업 확인란을 선택 하 고 Holographic remoting 앱에서 가져온 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![기능이 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

<span data-ttu-id="96930-134">이제 "재생" 단추를 클릭 하 여 HoloLens의 Holographic Remoting 앱에 Unity 앱을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="96930-135">[Visual Studio를 Unity에 연결](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="96930-136">버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-136">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="96930-137">이 기능은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="96930-138">앵커 및 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="96930-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="96930-139">Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="96930-140">Aranchor의 **Aranchor** 에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 aranchor 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="96930-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="96930-141">버전 0.1.0이 플러그 인은 평면에 연결 된 앵커 만들기를 제외한 모든 ARAnchorManager 기능을 지원 하며,이는 이후 릴리스에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="96930-142">앵커 지 속성 및 XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="96930-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="96930-143">**XRAnchorStore** 이라는 추가 API를 사용 하면 세션 간에 앵커가 지속 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="96930-144">XRAnchorStore는 장치에 저장 된 앵커를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96930-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="96930-145">Unity 장면의 **Aranchors** 에서 앵커를 유지 하거나, 저장소에서 새 **aranchors** 로 로드 하거나, 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="96930-146">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="96930-147">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="96930-148">XRAnchorStore를 로드 하기 위해 플러그 인은 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="96930-149">이 확장 메서드를 사용 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="96930-150">앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR Plugin 샘플 장면의](openxr-getting-started.md#hololens-2-samples)앵커-> 앵커 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="96930-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="96930-153">동작 컨트롤러 및 직접 상호 작용</span><span class="sxs-lookup"><span data-stu-id="96930-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="96930-154">Unity의 혼합 현실 상호 작용에 대 한 기본 사항을 알아보려면 unity [XR 입력](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="96930-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="96930-155">이 Unity 설명서에서는 컨트롤러 특정 입력에서 보다 일반화할 수 있는 **Inputfeatureusage** s에 대 한 매핑, 사용 가능한 XR 입력을 식별 하 고 분류 하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="96930-156">Mixed Reality OpenXR 플러그 인은 아래에 설명 된 대로 표준 **Inputfeatureusage** 에 매핑되는 추가 입력 상호 작용 프로필을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="96930-157">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="96930-157">InputFeatureUsage</span></span> | <span data-ttu-id="96930-158">HP 반향 G2 컨트롤러 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="96930-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="96930-159">HoloLens 손 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="96930-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="96930-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="96930-160">primary2DAxis</span></span> | <span data-ttu-id="96930-161">조이스틱이</span><span class="sxs-lookup"><span data-stu-id="96930-161">Joystick</span></span> | |
| <span data-ttu-id="96930-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="96930-162">primary2DAxisClick</span></span> | <span data-ttu-id="96930-163">조이스틱-클릭</span><span class="sxs-lookup"><span data-stu-id="96930-163">Joystick - Click</span></span> | |
| <span data-ttu-id="96930-164">트리거</span><span class="sxs-lookup"><span data-stu-id="96930-164">trigger</span></span> | <span data-ttu-id="96930-165">트리거</span><span class="sxs-lookup"><span data-stu-id="96930-165">Trigger</span></span>  | |
| <span data-ttu-id="96930-166">그리퍼</span><span class="sxs-lookup"><span data-stu-id="96930-166">grip</span></span> | <span data-ttu-id="96930-167">그리퍼</span><span class="sxs-lookup"><span data-stu-id="96930-167">Grip</span></span> | <span data-ttu-id="96930-168">공중 탭 또는 꽉의</span><span class="sxs-lookup"><span data-stu-id="96930-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="96930-169">primaryButton</span><span class="sxs-lookup"><span data-stu-id="96930-169">primaryButton</span></span> | <span data-ttu-id="96930-170">[X/A]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="96930-170">[X/A] - Press</span></span> | <span data-ttu-id="96930-171">에어 탭</span><span class="sxs-lookup"><span data-stu-id="96930-171">Air tap</span></span> |
| <span data-ttu-id="96930-172">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="96930-172">secondaryButton</span></span> | <span data-ttu-id="96930-173">[Y/B]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="96930-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="96930-174">gripButton</span><span class="sxs-lookup"><span data-stu-id="96930-174">gripButton</span></span> | <span data-ttu-id="96930-175">그립-누름</span><span class="sxs-lookup"><span data-stu-id="96930-175">Grip - Press</span></span> | |
| <span data-ttu-id="96930-176">triggerButton</span><span class="sxs-lookup"><span data-stu-id="96930-176">triggerButton</span></span> | <span data-ttu-id="96930-177">트리거-누르기</span><span class="sxs-lookup"><span data-stu-id="96930-177">Trigger - Press</span></span> | |
| <span data-ttu-id="96930-178">menuButton</span><span class="sxs-lookup"><span data-stu-id="96930-178">menuButton</span></span> | <span data-ttu-id="96930-179">메뉴</span><span class="sxs-lookup"><span data-stu-id="96930-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="96930-180">목표 및 그립 포즈</span><span class="sxs-lookup"><span data-stu-id="96930-180">Aim and Grip Poses</span></span>

<span data-ttu-id="96930-181">OpenXR 입력 상호 작용을 통해 두 가지 포즈 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-181">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="96930-182">손으로 개체를 렌더링 하는 그립</span><span class="sxs-lookup"><span data-stu-id="96930-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="96930-183">세계를 가리키는 목표입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-183">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="96930-184">이 디자인 및 두 포즈 간의 차이점에 대 한 자세한 내용은 [OpenXR 사양 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="96930-185">InputFeatureUsages **Deviceposition**, **devicerDeviceAngularVelocity ation**, **Devicevelocation** 및  에서 제공 하는 포즈는 모두 OpenXR **그립** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96930-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="96930-186">그립 포즈와 관련 된 InputFeatureUsages은 Unity의 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96930-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="96930-187">InputFeatureUsages **Pointerposition**, **pointerposition**, **pointerposition** 에서 제공 하는 포즈는  모두 OpenXR **목표** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96930-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="96930-188">이러한 InputFeatureUsages은 포함 된 c # 파일에 정의 되어 있지 않으므로 다음과 같이 사용자 고유의 InputFeatureUsages을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="96930-189">Haptics</span><span class="sxs-lookup"><span data-stu-id="96930-189">Haptics</span></span>

<span data-ttu-id="96930-190">Unity의 XR 입력 시스템에서 haptics를 사용 하는 방법에 대 한 자세한 내용은 unity의 unity [설명서 XR haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="96930-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="96930-191">출시 예정</span><span class="sxs-lookup"><span data-stu-id="96930-191">What's coming soon</span></span>

<span data-ttu-id="96930-192">혼합 현실 OpenXR 플러그 인 **버전 0.1.0** 에는 다음과 같은 문제와 누락 된 기능이 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="96930-193">이 작업을 수행 하 고 있으며 향후 릴리스에서 수정 사항 및 새로운 기능을 출시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="96930-194">**Ar설계도 Esubsystem** 은 아직 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="96930-195">**ARAnchorManager. AttachAnchor** 와 같은 **ar설계도 emanager**, **ARRaycastManager** 및 관련 API도 HoloLens 2에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="96930-196">**앵커** 는 Holographic Remoting에서 아직 지원 되지 않지만 가까운 장래에 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="96930-197">**손 모양 메시** 추적, **QR 코드** 및 **XRMeshSubsystem** 아직 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96930-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="96930-198">**Azure 공간 앵커** 지원은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="96930-199">**ARM64** 는 HoloLens 2 앱에 대해 유일 하 게 지원 되는 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="96930-200">**ARM** 플랫폼은 향후 릴리스에서 출시 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="96930-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="96930-201">문제 해결</span><span class="sxs-lookup"><span data-stu-id="96930-201">Troubleshooting</span></span>

<span data-ttu-id="96930-202">HoloLens 2에서 Unity 앱을 일시 중단 하 고 다시 시작 하는 경우 앱이 올바르게 다시 시작 될 수 없습니다. 그러면 HoloLens 보기에서 4 개의 회전 점이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="96930-203">OpenXR 프로젝트 설정에서 해결 방법으로 **깊이 전송 모드** 를 **없음** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96930-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
