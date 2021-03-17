---
title: 데스크톱 앱의 Holographic 원격 기능
description: OpenXR를 사용 하 여 데스크톱 앱에서 Holographic 원격을 사용 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, holographic 원격, 데스크톱
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624326"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="65101-104">데스크톱 앱의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="65101-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="65101-105">Windows 독립 실행형 앱 원격 지원이 0.1.3 패키지 릴리스에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="65101-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="65101-106">버전 0.1.3이 기능은 UWP 빌드를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65101-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="65101-107">[Holographic 원격 설치](openxr-supported-features.md#holographic-remoting-setup) 의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="65101-107">Follow the steps in [Holographic Remoting setup](openxr-supported-features.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="65101-108">**편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="65101-109">또한 **시작 시 XR 초기화** 를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![시작 시 XR 초기화가 선택 취소 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="65101-111">**OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="65101-112">**Holographic App Remoting** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![앱 원격 기능을 사용할 수 있는 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="65101-114">다음으로, 원격 구성을 설정 하 고 XR 초기화를 트리거하는 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="65101-115">[Mixed Reality OpenXR 플러그](openxr-getting-started.md#hololens-2-samples) 인을 사용 하 여 배포 된 샘플 앱에는 런타임에 특정 IP 주소에 연결 하는 예제 시나리오를 보여 주는 AppRemoting.cs이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65101-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="65101-116">이 시점에서 로컬 컴퓨터에 샘플 앱을 배포 하면 연결 단추를 사용 하 여 IP 주소 입력 필드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65101-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="65101-117">IP 주소를 입력 하 고 연결을 클릭 하면 XR이 초기화 되 고 대상 장치에 연결을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![예제 앱 원격 UI를 표시 하는 샘플 앱 스크린샷](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="65101-119">사용자 지정 연결 코드를 작성 하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진를 사용 하 여를 호출 `RemotingConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="65101-120">샘플 앱은 검사기에서이를 노출 하 고 텍스트 필드에서 IP 주소를 채우는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65101-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="65101-121">`Connect`를 호출 하면 구성이 설정 되 고 XR가 자동으로 초기화 됩니다. 따라서 코 루틴로 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="65101-122">을 실행 하는 동안 API를 사용 하 여 현재 연결 상태를 가져오고 `AppRemoting.TryGetConnectionState` 필요에 따라를 사용 하 여 XR의 연결을 해제 하 고 초기화를 취소할 수 있습니다 `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="65101-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="65101-123">이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65101-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="65101-124">샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="65101-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="65101-125">이전 Api에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="65101-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="65101-126">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="65101-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="65101-127">[Unity의 문서](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)에 있는 샘플 코드:</span><span class="sxs-lookup"><span data-stu-id="65101-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="65101-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="65101-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="65101-129">OpenXR</span><span class="sxs-lookup"><span data-stu-id="65101-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="65101-130">[N/A:를 호출할 때 자동으로 발생 `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="65101-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="65101-131">UnityEngine WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="65101-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="65101-132">XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="65101-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="65101-133">OpenXR</span><span class="sxs-lookup"><span data-stu-id="65101-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="65101-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 및 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="65101-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="65101-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="65101-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="65101-136">`AppRemoting.Connect`구조체를 통해에 전달 됩니다. `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="65101-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`