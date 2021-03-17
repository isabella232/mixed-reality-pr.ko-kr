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
# <a name="holographic-remoting-in-desktop-app"></a>데스크톱 앱의 Holographic 원격 기능

> [!NOTE]
> Windows 독립 실행형 앱 원격 지원이 0.1.3 패키지 릴리스에 추가 되었습니다.
> 버전 0.1.3이 기능은 UWP 빌드를 지원 하지 않습니다.

1. [Holographic 원격 설치](openxr-supported-features.md#holographic-remoting-setup) 의 단계를 따릅니다.
2. **편집 > 프로젝트 설정을** 열고 **XR 플러그 인 관리** 로 이동 하 여 **Windows Mixed Reality 기능 집합** 상자를 선택 합니다. 또한 **시작 시 XR 초기화** 를 선택 취소 합니다.

    ![시작 시 XR 초기화가 선택 취소 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02-app.png)

3. **OpenXR** 아래의 **기능** 섹션을 확장 하 고 **모두 표시** 를 선택 합니다.
4. **Holographic App Remoting** 확인란을 선택 합니다.

    ![앱 원격 기능을 사용할 수 있는 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03-app.png)

5. 다음으로, 원격 구성을 설정 하 고 XR 초기화를 트리거하는 코드를 작성 합니다. [Mixed Reality OpenXR 플러그](openxr-getting-started.md#hololens-2-samples) 인을 사용 하 여 배포 된 샘플 앱에는 런타임에 특정 IP 주소에 연결 하는 예제 시나리오를 보여 주는 AppRemoting.cs이 포함 되어 있습니다. 이 시점에서 로컬 컴퓨터에 샘플 앱을 배포 하면 연결 단추를 사용 하 여 IP 주소 입력 필드가 표시 됩니다. IP 주소를 입력 하 고 연결을 클릭 하면 XR이 초기화 되 고 대상 장치에 연결을 시도 합니다.

    ![예제 앱 원격 UI를 표시 하는 샘플 앱 스크린샷](images/openxr-sample-app-remoting.png)

6. 사용자 지정 연결 코드를 작성 하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진를 사용 하 여를 호출 `RemotingConfiguration` 합니다. 샘플 앱은 검사기에서이를 노출 하 고 텍스트 필드에서 IP 주소를 채우는 방법을 보여 줍니다. `Connect`를 호출 하면 구성이 설정 되 고 XR가 자동으로 초기화 됩니다. 따라서 코 루틴로 호출 해야 합니다.

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 을 실행 하는 동안 API를 사용 하 여 현재 연결 상태를 가져오고 `AppRemoting.TryGetConnectionState` 필요에 따라를 사용 하 여 XR의 연결을 해제 하 고 초기화를 취소할 수 있습니다 `AppRemoting.Disconnect()` . 이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다. 샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.

### <a name="migration-from-previous-apis"></a>이전 Api에서 마이그레이션

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. HolographicRemoting

[Unity의 문서](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)에 있는 샘플 코드:

| XR. WSA. HolographicRemoting | OpenXR |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A:를 호출할 때 자동으로 발생 `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine WindowsMRRemoting

| XR. WindowsMR. WindowsMRRemoting | OpenXR |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 및 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | `AppRemoting.Connect`구조체를 통해에 전달 됩니다. `RemotingConfiguration` |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`