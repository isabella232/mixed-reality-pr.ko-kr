---
title: Unity의 OpenXR 플러그 인 지원 기능
description: Unity에서 혼합 현실 개발에 대해 OpenXR에서 지 원하는 기능을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496152"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="b1a62-104">Unity의 혼합 현실 OpenXR 지원 되는 기능</span><span class="sxs-lookup"><span data-stu-id="b1a62-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="b1a62-105">**Mixed Reality OpenXR 플러그 인** 패키지는 Unity의 **OpenXR 플러그 인** 을 확장 한 것으로, HoloLens 2 및 Windows Mixed Reality 헤드셋의 기능 모음을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="b1a62-106">계속 하기 전에 **unity 2020.2** 이상, **OpenXR 플러그 인 버전 0.1.3** 이상을 설치 했는지 확인 하 고 unity 프로젝트가 [OpenXR에 대해 구성](openxr-getting-started.md)되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="b1a62-107">지원되는 내용</span><span class="sxs-lookup"><span data-stu-id="b1a62-107">What's supported</span></span>

<span data-ttu-id="b1a62-108">현재 지원 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-108">The following features are currently supported:</span></span>

* <span data-ttu-id="b1a62-109">HoloLens 2 용 UWP 응용 프로그램을 지원 하 고 HoloLens 2 응용 프로그램 모델을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="b1a62-110">최신 컨트롤러 프로필 및 holographic app remoting과 함께 Windows Mixed Reality 헤드셋에 대해 Win32 VR 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="b1a62-111">앵커와 바인딩되지 않은 공간을 사용한 세계 크기 조정 추적.</span><span class="sxs-lookup"><span data-stu-id="b1a62-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="b1a62-112">[저장소 API를 고정 하 여](#anchors-and-anchor-persistence) HoloLens 2 로컬 저장소에 앵커를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="b1a62-113">새 HP 반향 G2 컨트롤러를 포함 하 여 [동작 컨트롤러 및 직접 상호 작용](#motion-controller-and-hand-interactions).</span><span class="sxs-lookup"><span data-stu-id="b1a62-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="b1a62-114">26 개의 조인트와 조인트 반지름 입력을 사용 하 여 직접 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="b1a62-115">HoloLens 2의 눈 응시 상호 작용입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="b1a62-116">HoloLens 2에서 사진/비디오 (PV) 카메라를 찾는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="b1a62-117">혼합 현실 PV 카메라를 통한 세 번째 눈동자 렌더링을 사용 하 여 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="b1a62-118">는 [Holographic Remoting 앱을 사용 하 여 HoloLens 2에 대 한 "Play"를](#holographic-remoting-in-unity-editor-play-mode)지원 하므로 개발자는 장치에 빌드 및 배포 하지 않고도 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="b1a62-119">[Mrtk OpenXR 공급자 지원을](openxr-getting-started.md#using-mrtk-with-openxr-support)통해 Mrtk Unity 2.5.3 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="b1a62-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 이상 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="b1a62-121">(0.1.3에 추가 됨) 빌드 및 배포 된 Windows 독립 실행형 앱에서 [데스크톱 앱 Holographic 원격](#holographic-remoting-in-desktop-app) 을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="b1a62-122">Holographic 원격 설치</span><span class="sxs-lookup"><span data-stu-id="b1a62-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="b1a62-123">먼저 HoloLens 2의 Microsoft Store에서 [Holographic Remoting Player 앱을 설치](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="b1a62-124">HoloLens 2에서 Holographic 원격 플레이어 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="b1a62-125">OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="b1a62-127">Unity 편집기 재생 모드의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="b1a62-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="b1a62-128">Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 패키지 하 여 HoloLens 2 장치에 배포 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="b1a62-129">한 가지 해결 방법은 Holographic Editor 원격 기능을 사용 하도록 설정 하는 것입니다 .이 기능을 사용 하면 네트워크를 통해 HoloLens 2 장치에 직접 "재생" 모드를 사용 하 여 c # 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="b1a62-130">이 시나리오에서는 UWP 패키지를 빌드하여 원격 장치에 배포 하는 오버 헤드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="b1a62-131">[Holographic 원격 설치](#holographic-remoting-setup) 의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b1a62-132">**편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![XR 플러그 인 관리가 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

3. <span data-ttu-id="b1a62-134">**OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b1a62-135">**Holographic Editor 원격** 작업 확인란을 선택 하 고 Holographic remoting 앱에서 가져온 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![기능이 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

<span data-ttu-id="b1a62-137">이제 "재생" 단추를 클릭 하 여 HoloLens의 Holographic Remoting 앱에 Unity 앱을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="b1a62-138">[Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b1a62-139">버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="b1a62-140">이 기능은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="b1a62-141">데스크톱 앱의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="b1a62-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="b1a62-142">Windows 독립 실행형 앱 원격 지원이 0.1.3 패키지 릴리스에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="b1a62-143">버전 0.1.3이 기능은 UWP 빌드를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="b1a62-144">[Holographic 원격 설치](#holographic-remoting-setup) 의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b1a62-145">**편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="b1a62-146">또한 **시작 시 XR 초기화** 를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![시작 시 XR 초기화가 선택 취소 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="b1a62-148">**OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b1a62-149">**Holographic App Remoting** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![앱 원격 기능을 사용할 수 있는 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="b1a62-151">다음으로, 원격 구성을 설정 하 고 XR 초기화를 트리거하는 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="b1a62-152">[Mixed Reality OpenXR 플러그](openxr-getting-started.md#hololens-2-samples) 인을 사용 하 여 배포 된 샘플 앱에는 런타임에 특정 IP 주소에 연결 하는 예제 시나리오를 보여 주는 AppRemoting.cs이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="b1a62-153">이 시점에서 로컬 컴퓨터에 샘플 앱을 배포 하면 연결 단추를 사용 하 여 IP 주소 입력 필드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="b1a62-154">IP 주소를 입력 하 고 연결을 클릭 하면 XR이 초기화 되 고 대상 장치에 연결을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![예제 앱 원격 UI를 표시 하는 샘플 앱 스크린샷](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="b1a62-156">사용자 지정 연결 코드를 작성 하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진를 사용 하 여를 호출 `RemotingConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="b1a62-157">샘플 앱은 검사기에서이를 노출 하 고 텍스트 필드에서 IP 주소를 채우는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="b1a62-158">`Connect`를 호출 하면 구성이 설정 되 고 XR가 자동으로 초기화 됩니다. 따라서 코 루틴로 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="b1a62-159">을 실행 하는 동안 API를 사용 하 여 현재 연결 상태를 가져오고 `AppRemoting.TryGetConnectionState` 필요에 따라를 사용 하 여 XR의 연결을 해제 하 고 초기화를 취소할 수 있습니다 `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="b1a62-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="b1a62-160">이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="b1a62-161">샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="b1a62-162">이전 Api에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="b1a62-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="b1a62-163">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b1a62-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="b1a62-164">[Unity의 문서](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)에 있는 샘플 코드:</span><span class="sxs-lookup"><span data-stu-id="b1a62-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="b1a62-165">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b1a62-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="b1a62-166">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b1a62-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="b1a62-167">[N/A:를 호출할 때 자동으로 발생 `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="b1a62-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="b1a62-168">UnityEngine WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b1a62-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="b1a62-169">XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b1a62-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="b1a62-170">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b1a62-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="b1a62-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 및 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="b1a62-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="b1a62-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="b1a62-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="b1a62-173">`AppRemoting.Connect`구조체를 통해에 전달 됩니다. `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="b1a62-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="b1a62-174">앵커 및 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="b1a62-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="b1a62-175">Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="b1a62-176">Aranchor의 **Aranchor** 에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 aranchor 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1a62-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="b1a62-177">버전 0.1.0이 플러그 인은 평면에 연결 된 앵커 만들기를 제외한 모든 ARAnchorManager 기능을 지원 하며,이는 이후 릴리스에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="b1a62-178">앵커 지 속성 및 XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b1a62-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="b1a62-179">**XRAnchorStore** 이라는 추가 API를 사용 하면 세션 간에 앵커가 지속 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="b1a62-180">XRAnchorStore는 장치에 저장 된 앵커를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="b1a62-181">Unity 장면의 **Aranchors** 에서 앵커를 유지 하거나, 저장소에서 새 **aranchors** 로 로드 하거나, 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="b1a62-182">이러한 앵커는 동일한 장치에 저장 되 고 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="b1a62-183">장치 간 앵커 저장소는 향후 릴리스에서 Azure 공간 앵커를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="b1a62-184">XRAnchorStore를 로드 하기 위해 플러그 인은 ARAnchorManager의 하위 시스템인 XRAnchorSubsystem에 확장 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="b1a62-185">이 확장 메서드를 사용 하려면 다음과 같이 ARAnchorManager의 하위 시스템에서 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="b1a62-186">앵커 지속/유지 안 됨의 전체 예를 보려면 [Mixed Reality OpenXR Plugin 샘플 장면의](openxr-getting-started.md#hololens-2-samples)앵커-> 앵커 샘플 GameObject 및 AnchorsSample.cs 스크립트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1a62-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![앵커 샘플이 강조 표시 된 Unity 편집기에서 열린 계층 패널의 스크린샷](images/openxr-features-img-04.png)

![앵커 샘플 스크립트가 강조 표시 된 상태로 Unity 편집기에서 열리는 검사기 패널의 스크린샷](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="b1a62-189">동작 컨트롤러 및 직접 상호 작용</span><span class="sxs-lookup"><span data-stu-id="b1a62-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="b1a62-190">Unity의 혼합 현실 상호 작용에 대 한 기본 사항을 알아보려면 unity [XR 입력](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1a62-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="b1a62-191">이 Unity 설명서에서는 컨트롤러 특정 입력에서 보다 일반화할 수 있는 **Inputfeatureusage** s에 대 한 매핑, 사용 가능한 XR 입력을 식별 하 고 분류 하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="b1a62-192">Mixed Reality OpenXR 플러그 인은 아래에 설명 된 대로 표준 **Inputfeatureusage** 에 매핑되는 추가 입력 상호 작용 프로필을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="b1a62-193">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="b1a62-193">InputFeatureUsage</span></span> | <span data-ttu-id="b1a62-194">HP 반향 G2 컨트롤러 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="b1a62-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="b1a62-195">HoloLens 손 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="b1a62-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="b1a62-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="b1a62-196">primary2DAxis</span></span> | <span data-ttu-id="b1a62-197">조이스틱이</span><span class="sxs-lookup"><span data-stu-id="b1a62-197">Joystick</span></span> | |
| <span data-ttu-id="b1a62-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="b1a62-198">primary2DAxisClick</span></span> | <span data-ttu-id="b1a62-199">조이스틱-클릭</span><span class="sxs-lookup"><span data-stu-id="b1a62-199">Joystick - Click</span></span> | |
| <span data-ttu-id="b1a62-200">트리거</span><span class="sxs-lookup"><span data-stu-id="b1a62-200">trigger</span></span> | <span data-ttu-id="b1a62-201">트리거</span><span class="sxs-lookup"><span data-stu-id="b1a62-201">Trigger</span></span>  | |
| <span data-ttu-id="b1a62-202">그리퍼</span><span class="sxs-lookup"><span data-stu-id="b1a62-202">grip</span></span> | <span data-ttu-id="b1a62-203">그리퍼</span><span class="sxs-lookup"><span data-stu-id="b1a62-203">Grip</span></span> | <span data-ttu-id="b1a62-204">공중 탭 또는 꽉의</span><span class="sxs-lookup"><span data-stu-id="b1a62-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="b1a62-205">primaryButton</span><span class="sxs-lookup"><span data-stu-id="b1a62-205">primaryButton</span></span> | <span data-ttu-id="b1a62-206">[X/A]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="b1a62-206">[X/A] - Press</span></span> | <span data-ttu-id="b1a62-207">에어 탭</span><span class="sxs-lookup"><span data-stu-id="b1a62-207">Air tap</span></span> |
| <span data-ttu-id="b1a62-208">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="b1a62-208">secondaryButton</span></span> | <span data-ttu-id="b1a62-209">[Y/B]-키 누르기</span><span class="sxs-lookup"><span data-stu-id="b1a62-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="b1a62-210">gripButton</span><span class="sxs-lookup"><span data-stu-id="b1a62-210">gripButton</span></span> | <span data-ttu-id="b1a62-211">그립-누름</span><span class="sxs-lookup"><span data-stu-id="b1a62-211">Grip - Press</span></span> | |
| <span data-ttu-id="b1a62-212">triggerButton</span><span class="sxs-lookup"><span data-stu-id="b1a62-212">triggerButton</span></span> | <span data-ttu-id="b1a62-213">트리거-누르기</span><span class="sxs-lookup"><span data-stu-id="b1a62-213">Trigger - Press</span></span> | |
| <span data-ttu-id="b1a62-214">menuButton</span><span class="sxs-lookup"><span data-stu-id="b1a62-214">menuButton</span></span> | <span data-ttu-id="b1a62-215">메뉴</span><span class="sxs-lookup"><span data-stu-id="b1a62-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="b1a62-216">목표 및 그립 포즈</span><span class="sxs-lookup"><span data-stu-id="b1a62-216">Aim and Grip Poses</span></span>

<span data-ttu-id="b1a62-217">OpenXR 입력 상호 작용을 통해 두 가지 포즈 집합에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="b1a62-218">손으로 개체를 렌더링 하는 그립</span><span class="sxs-lookup"><span data-stu-id="b1a62-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="b1a62-219">세계를 가리키는 목표입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="b1a62-220">이 디자인 및 두 포즈 간의 차이점에 대 한 자세한 내용은 [OpenXR 사양 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="b1a62-221">InputFeatureUsages **Deviceposition**, **devicerDeviceAngularVelocity ation**, **Devicevelocation** 및  에서 제공 하는 포즈는 모두 OpenXR **그립** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="b1a62-222">그립 포즈와 관련 된 InputFeatureUsages은 Unity의 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="b1a62-223">InputFeatureUsages **Pointerposition**, **pointerposition**, **pointerposition** 에서 제공 하는 포즈는  모두 OpenXR **목표** 포즈를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="b1a62-224">이러한 InputFeatureUsages은 포함 된 c # 파일에 정의 되어 있지 않으므로 다음과 같이 사용자 고유의 InputFeatureUsages을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="b1a62-225">Haptics</span><span class="sxs-lookup"><span data-stu-id="b1a62-225">Haptics</span></span>

<span data-ttu-id="b1a62-226">Unity의 XR 입력 시스템에서 haptics를 사용 하는 방법에 대 한 자세한 내용은 unity의 unity [설명서 XR haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1a62-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="b1a62-227">출시 예정</span><span class="sxs-lookup"><span data-stu-id="b1a62-227">What's coming soon</span></span>

<span data-ttu-id="b1a62-228">혼합 현실 OpenXR 플러그 인 **버전 0.1.0** 에는 다음과 같은 문제와 누락 된 기능이 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="b1a62-229">이 작업을 수행 하 고 있으며 향후 릴리스에서 수정 사항 및 새로운 기능을 출시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="b1a62-230">**Ar설계도 Esubsystem** 은 아직 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="b1a62-231">**ARAnchorManager. AttachAnchor** 와 같은 **ar설계도 emanager**, **ARRaycastManager** 및 관련 API도 HoloLens 2에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="b1a62-232">**앵커** 는 Holographic Remoting에서 아직 지원 되지 않지만 가까운 장래에 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="b1a62-233">**손 모양 메시** 추적, **QR 코드** 및 **XRMeshSubsystem** 아직 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="b1a62-234">**Azure 공간 앵커** 지원은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="b1a62-235">**ARM64** 는 HoloLens 2 앱에 대해 유일 하 게 지원 되는 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="b1a62-236">**ARM** 플랫폼은 향후 릴리스에서 출시 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b1a62-237">문제 해결</span><span class="sxs-lookup"><span data-stu-id="b1a62-237">Troubleshooting</span></span>

<span data-ttu-id="b1a62-238">HoloLens 2에서 Unity 앱을 일시 중단 하 고 다시 시작 하는 경우 앱이 올바르게 다시 시작 될 수 없습니다. 그러면 HoloLens 보기에서 4 개의 회전 점이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="b1a62-239">OpenXR 프로젝트 설정에서 해결 방법으로 **깊이 전송 모드** 를 **없음** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1a62-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
