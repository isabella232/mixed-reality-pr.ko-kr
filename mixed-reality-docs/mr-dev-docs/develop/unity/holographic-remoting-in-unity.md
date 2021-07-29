---
title: Unity의 Holographic 원격 기능
description: OpenXR를 사용 하 여 데스크톱 앱 및 Unity 재생 모드에서 Holographic 원격을 사용 하는 방법을 알아봅니다.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, mrtk, mixed reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, holographic 원격, 데스크톱
ms.openlocfilehash: 51244a94fb7e54f2eee41d9d1b7f65b0ba373138
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757422"
---
# <a name="holographic-remoting-in-unity"></a>Unity의 Holographic 원격 기능

> [!NOTE]
> Windows 독립 실행형 앱 원격 지원이 0.1.3 패키지 릴리스에 추가 되었습니다.
> 버전 0.1.3이 기능은 UWP 빌드를 지원 하지 않습니다.

[Holographic Remoting의 기본 사항에 대해 알아봅니다.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Holographic 원격을 사용 하 여 실시간으로 HoloLens 2 Holographic 콘텐츠를 스트리밍할 수 있습니다. 이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다. 

시작 하기 전에 Unity의 두 가지 주요 옵션을 이해 하는 것이 중요 합니다.
* **Unity 재생 모드에서의 Holographic 원격** 작업: PC의 unity 편집기에서 로컬로 앱을 실행 하 여 HoloLens 2에서 콘텐츠를 빠르게 미리 볼 수 있는 방법을 제공 합니다. 재생 모드는 개발 PC에 연결 된 Windows Mixed Reality 헤드셋에도 사용할 수 있습니다.
* **Unity 빌드 파일에서 원격 Holographic**: 데스크톱으로 내보낸 Unity Holographic Remoting 원격 응용 프로그램에서 HoloLens 2로 앱을 실행 합니다. 이는 앱에 고해상도 자산 또는 모델이 있는 경우에 유용 합니다. 데스크톱 GPU는 HoloLens 2 하기 전에 렌더링을 처리 합니다.

## <a name="holographic-remoting-setup"></a>Holographic 원격 설치

Holographic 원격을 사용 하 여 수행 하는 경로와 상관 없이 HoloLens 2 Microsoft Store에서 [Holographic remoting Player 앱을 설치](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 해야 합니다.

다운로드 되 면 HoloLens 2에서 Holographic Remoting Player 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다. **OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요** 합니다.

![HoloLens에서 실행 되는 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Holographic 원격을 사용 하는 Unity 재생 모드

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다. 자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.

최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다. 이렇게 하면 Holographic 원격으로 무선 연결의 대기 시간에 장면을 조정할 수 있습니다.

## <a name="holographic-remoting-from-a-remote-application"></a>원격 응용 프로그램에서 원격 Holographic

1. 메뉴 모음에서 **편집 > Project 설정** 를 선택 합니다.
1. 왼쪽 열에서 **XR 플러그 인 관리** 를 선택 합니다.
1. **XR 플러그 인 관리** 섹션에서 **Microsoft HoloLens 기능 그룹** 및 **Holographic Remoting 원격 앱 기능 그룹** 을 선택 합니다.
1. **시작 시 XR 초기화를** 선택 취소 합니다.

    ![시작 시 XR 초기화가 선택 취소 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/001-openxr-features.png)

1. 원격 구성을 설정 하 고 XR 초기화를 트리거하는 코드를 작성 합니다. [Mixed Reality OpenXR 플러그](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) 인을 사용 하 여 배포 된 샘플 앱에는 런타임에 특정 IP 주소에 연결 하기 위한 예제 시나리오를 보여 주는 appremoting. cs가 포함 되어 있습니다. 이 시점에서 로컬 컴퓨터에 샘플 앱을 배포 하면 연결 단추를 사용 하 여 IP 주소 입력 필드가 표시 됩니다. IP 주소를 입력 하 고 커넥트를 클릭 하면 XR가 초기화 되 고 대상 장치에 연결을 시도 합니다.

    ![예제 앱 원격 UI를 표시 하는 샘플 앱 스크린샷](images/openxr-sample-app-remoting.png)

1. 사용자 지정 연결 코드를 작성 하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진를 사용 하 여를 호출 `RemotingConfiguration` 합니다. 샘플 앱은 검사기에서이를 노출 하 고 텍스트 필드에서 IP 주소를 채우는 방법을 보여 줍니다. `Connect`를 호출 하면 구성이 설정 되 고 XR가 자동으로 초기화 됩니다. 따라서 코 루틴로 호출 해야 합니다.

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. 을 실행 하는 동안 API를 사용 하 여 현재 연결 상태를 가져오고 `AppRemoting.TryGetConnectionState` 필요에 따라를 사용 하 여 XR의 연결을 해제 하 고 초기화를 취소할 수 있습니다 `AppRemoting.Disconnect()` . 이는 동일한 앱 세션 내에서 다른 장치에 대 한 연결을 끊고 다시 연결 하는 데 사용할 수 있습니다. 샘플 앱은 원격 세션을 탭 할 경우 연결을 끊을 tappable 큐브를 제공 합니다.

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

## <a name="see-also"></a>참고 항목

* [홀로그램 원격 플레이어](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [자습서: PC Holographic 원격 작업 시작](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [자습서: Holographic Remoting PC 응용 프로그램 만들기](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
