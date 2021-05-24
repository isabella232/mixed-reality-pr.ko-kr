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
# <a name="holographic-remoting-in-desktop-app"></a>데스크톱 앱의 홀로그램 원격 접속

> [!NOTE]
> Windows 독립 실행형 앱 Remoting 지원이 0.1.3 패키지 릴리스에 추가되었습니다.
> 버전 0.1.3에서는 이 기능이 UWP 빌드를 지원하지 않습니다.

1. [홀로그램 Remoting 설정의](unity-play-mode.md#holographic-remoting-setup) 단계를 수행합니다.
2. **편집 -> 프로젝트 설정을** 열고 **XR 플러그 인 관리 로** 이동하여 Windows Mixed Reality 기능 **집합** 상자를 선택합니다. 또한 시작 시 **XR 초기화** 를 선택 취소합니다.

    ![시작 시 XR 초기화가 선택 취소된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02-app.png)

3. **OpenXR에서** **기능** 섹션을 확장하고 **모두 표시를 선택합니다.**
4. **홀로그램 앱 Remoting 확인란을** 선택합니다.

    ![앱 Remoting을 사용하도록 설정된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03-app.png)

5. 다음으로, 일부 코드를 작성하여 Remoting 구성을 설정하고 XR 초기화를 트리거합니다. [Mixed Reality OpenXR 플러그 인과](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) 함께 배포된 샘플 앱에는 런타임에 특정 IP 주소에 연결하기 위한 예제 시나리오를 보여주는 AppRemoting.cs가 포함되어 있습니다. 이 시점에서 샘플 앱을 로컬 머신에 배포하면 연결 단추가 있는 IP 주소 입력 필드가 표시됩니다. IP 주소를 입력하고 연결을 클릭하면 XR이 초기화되고 대상 디바이스에 연결을 시도합니다.

    ![예제 앱 Remoting UI를 표시하는 샘플 앱의 스크린샷](images/openxr-sample-app-remoting.png)

6. 사용자 지정 연결 코드를 작성하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진 를 사용하여 를 호출합니다. `RemotingConfiguration` 샘플 앱은 검사기에서 이를 노출하고 텍스트 필드에서 IP 주소를 채우는 방법을 보여줍니다. 를 `Connect` 호출하면 구성이 설정되고 XR이 자동으로 초기화됩니다. 따라서 코루틴으로 호출해야 합니다.

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 를 실행하는 동안 API를 사용하여 현재 연결 상태를 가져오고 필요에 따라 를 `AppRemoting.TryGetConnectionState` 사용하여 XR의 연결을 끊고 초기화 해제할 수 `AppRemoting.Disconnect()` 있습니다. 이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다. 샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.

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