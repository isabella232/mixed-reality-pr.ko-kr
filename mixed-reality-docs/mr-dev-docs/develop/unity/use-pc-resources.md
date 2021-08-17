---
title: PC 리소스를 사용하여 홀로그램 Remoting으로 앱 전원 공급
description: HoloLens 온보드 처리 능력을 사용하는 대신 PC 리소스를 사용하여 홀로그램 Remoting으로 앱에 전원을 공급합니다.
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, 홀로그램 원격, 데스크톱, 미리 보기, 디버그
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203848"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>PC 리소스를 사용하여 홀로그램 Remoting으로 앱 전원 공급

이 문서에서는 홀로그램 Remoting에 대한 다음 사용 사례를 설명합니다.

-  **PC의 리소스가 HoloLens 온보드 리소스에 의존하는 대신 앱의 전원을 공급하려고** 합니다. 홀로그램 Remoting 기능이 있는 앱을 만들고 빌드할 수 있습니다. 사용자는 HoloLens 앱을 경험하지만 앱은 실제로 PC에서 실행되어 앱이 PC의 더 강력한 리소스를 활용할 수 있도록 합니다. 이는 앱에 고해상도 자산 또는 모델이 있고 프레임 속도를 저하하지 않으려는 경우에 특히 유용할 수 있습니다. 이를 _홀로그램 원격 원격 앱이라고_ 부릅니다. HoloLens 입력(응시, 제스처, 음성 및 공간 매핑)은 PC로 전송되며, 여기서 콘텐츠는 가상 몰입형 보기로 렌더링됩니다. 그러면 렌더링된 프레임이 HoloLens 전송됩니다.

이 유형의 홀로그램 Remoting은 WMR(Windows Mixed Reality) 몰입형 헤드셋에도 사용할 수 있습니다. 예를 들어 WMR 헤드셋이 스트래퍼 PC에 연결되어 있고 더 강력한 PC에서 모조 PC로 앱을 스트리밍하려는 경우에 유용할 수 있습니다.

홀로그램 Remoting에 대한 자세한 내용은 [홀로그램 Remoting 개요를 참조하세요.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

[개발 프로세스 중에 앱을 미리 보고 디버그하려는 경우에도](preview-and-debug-your-app.md)홀로그램 Remoting을 사용할 수 있습니다.

## <a name="set-up-holographic-remoting"></a>홀로그램 Remoting 설정

홀로그램 Remoting을 사용하려면 HoloLens 2 Microsoft Store [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 앱을 설치해야 합니다. 아래에 설명된 대로 앱을 다운로드하고 실행하면 연결할 버전 번호와 IP 주소가 표시됩니다. **OpenXR 플러그 인 을 사용하려면 v2.4 이상 이 필요합니다.**

홀로그램 Remoting에는 빠른 PC 및 Wi-Fi 연결이 필요합니다. 자세한 내용은 위에 링크된 홀로그램 Remoting Player 문서에서 찾을 수 있습니다.

![HoloLens 실행 중인 홀로그램 Remoting Player의 스크린샷](images/openxr-features-img-01.png)

1. 메뉴 모음에서 **> Project 설정 편집을** 선택합니다.
1. 왼쪽 열에서 **XR 플러그 인 관리를** 선택합니다.
1. **XR 플러그 인 관리** 섹션에서 **Microsoft HoloLens 기능 그룹** 및 **홀로그램 원격 원격 원격 앱 기능 그룹을** 선택합니다.
1. 시작 시 **XR 초기화** 를 선택 취소합니다.

    ![시작 시 XR 초기화가 선택 취소된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/001-openxr-features.png)

1. 일부 코드를 작성하여 Remoting 구성을 설정하고 XR 초기화를 트리거합니다. [Mixed Reality OpenXR 플러그 인과](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) 함께 배포된 샘플 앱에는 런타임에 특정 IP 주소에 연결하기 위한 예제 시나리오를 보여주는 AppRemoting.cs가 포함되어 있습니다. 이 시점에서 샘플 앱을 로컬 머신에 배포하면 연결 단추가 있는 IP 주소 입력 필드가 표시됩니다. IP 주소를 입력하고 커넥트 클릭하면 XR이 초기화되고 대상 디바이스에 연결을 시도합니다.

    ![예제 앱 Remoting UI를 표시하는 샘플 앱의 스크린샷](images/openxr-sample-app-remoting.png)

1. 사용자 지정 연결 코드를 작성하려면 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 채워진 를 사용하여 를 호출합니다. `RemotingConfiguration` 샘플 앱은 검사기에서 이를 노출하고 텍스트 필드에서 IP 주소를 채우는 방법을 보여줍니다. 를 `Connect` 호출하면 구성이 설정되고 XR이 자동으로 초기화됩니다. 따라서 코루틴으로 호출해야 합니다.

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. 실행하는 동안 API를 사용하여 현재 연결 상태를 가져오고 필요에 따라 를 `AppRemoting.TryGetConnectionState` 사용하여 XR의 연결을 끊고 초기화 해제할 수 `AppRemoting.Disconnect()` 있습니다. 동일한 앱 세션 내에서 연결을 끊고 다른 디바이스에 다시 연결하는 데 사용할 수 있습니다. 샘플 앱은 탭할 경우 Remoting 세션의 연결을 끊는 탭 가능한 큐브를 제공합니다.

## <a name="migrate-from-previous-holographic-remoting-apis"></a>이전 홀로그램 Remoting API에서 마이그레이션

홀로그램 Remoting에 대한 자세한 내용은 [홀로그램 Remoting 개요를 참조하세요.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

[Unity 문서의](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)샘플 코드에서:

| Xr. Wsa. HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [해당 없음: 를 호출할 때 자동으로 `AppRemoting.Connect` 발생합니다. ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine.XR.WindowsMR.WindowsMRRemoting

| Xr. WindowsMR.WindowsMRRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 및 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | `AppRemoting.Connect`구조체를 통해 에 전달됩니다. `RemotingConfiguration` |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>참고 항목

* [홀로그램 원격 플레이어](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [홀로그램 Remoting 및 재생 모드를 통해 앱 미리 보기 및 디버그](preview-and-debug-your-app.md)
* [자습서: PC 홀로그램 Remoting 시작](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [자습서: 홀로그램 Remoting PC 애플리케이션 만들기](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
