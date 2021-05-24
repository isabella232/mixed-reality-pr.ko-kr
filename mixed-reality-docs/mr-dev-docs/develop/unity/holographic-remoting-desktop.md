---
title: 데스크톱 앱의 홀로그램 원격 접속
description: OpenXR을 사용하여 데스크톱 앱에서 홀로그램 원격을 사용하는 방법을 검색합니다.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, 홀로그램 원격, 데스크톱
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333417"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="02172-104">데스크톱 앱의 홀로그램 원격 접속</span><span class="sxs-lookup"><span data-stu-id="02172-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="02172-105">Windows 독립 실행형 앱 Remoting 지원이 0.1.3 패키지 릴리스에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="02172-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="02172-106">버전 0.1.3에서는 이 기능이 UWP 빌드를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="02172-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="02172-107">[홀로그램 Remoting 설정의](unity-play-mode.md#holographic-remoting-setup) 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="02172-108">**편집 -> 프로젝트 설정을** 열고 **XR 플러그 인 관리 로** 이동하여 Windows Mixed Reality 기능 **집합** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="02172-109">또한 시작 시 **XR 초기화** 를 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![시작 시 XR 초기화가 선택 취소된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="02172-111">**OpenXR에서** **기능** 섹션을 확장하고 **모두 표시를 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="02172-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="02172-112">**홀로그램 앱 Remoting 확인란을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![앱 Remoting을 사용하도록 설정된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="02172-114">다음으로, 일부 코드를 작성하여 Remoting 구성을 설정하고 XR 초기화를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="02172-115">[Mixed Reality OpenXR 플러그 인과](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) 함께 배포된 샘플 앱에는 런타임에 특정 IP 주소에 연결하기 위한 예제 시나리오를 보여주는 AppRemoting.cs가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02172-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="02172-116">이 시점에서 샘플 앱을 로컬 머신에 배포하면 연결 단추가 있는 IP 주소 입력 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="02172-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="02172-117">IP 주소를 입력하고 연결을 클릭하면 XR이 초기화되고 대상 디바이스에 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![예제 앱 Remoting UI를 표시하는 샘플 앱의 스크린샷](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="02172-119">사용자 지정 연결 코드를 작성하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진 를 사용하여 를 호출합니다. `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="02172-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="02172-120">샘플 앱은 검사기에서 이를 노출하고 텍스트 필드에서 IP 주소를 채우는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="02172-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="02172-121">를 `Connect` 호출하면 구성이 설정되고 XR이 자동으로 초기화됩니다. 따라서 코루틴으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="02172-122">를 실행하는 동안 API를 사용하여 현재 연결 상태를 가져오고 필요에 따라 를 `AppRemoting.TryGetConnectionState` 사용하여 XR의 연결을 끊고 초기화 해제할 수 `AppRemoting.Disconnect()` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02172-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="02172-123">이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02172-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="02172-124">샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="02172-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="02172-125">이전 Api에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="02172-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="02172-126">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="02172-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="02172-127">[Unity의 문서](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)에 있는 샘플 코드:</span><span class="sxs-lookup"><span data-stu-id="02172-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="02172-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="02172-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="02172-129">OpenXR</span><span class="sxs-lookup"><span data-stu-id="02172-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="02172-130">[N/A:를 호출할 때 자동으로 발생 `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="02172-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="02172-131">UnityEngine WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="02172-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="02172-132">XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="02172-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="02172-133">OpenXR</span><span class="sxs-lookup"><span data-stu-id="02172-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="02172-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 및 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="02172-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="02172-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="02172-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="02172-136">`AppRemoting.Connect`구조체를 통해에 전달 됩니다. `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="02172-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`