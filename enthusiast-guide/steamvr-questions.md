---
title: SteamVR Faq
description: SteamVR Windows Mixed Reality 문제 해결은 표준 소비자 지원 설명서를 벗어나는 것입니다.
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, SteamVR
ms.openlocfilehash: 0fb9c07dda8fe354966403bc9c6a21acb600e61cb943c270eb9c87f5ec2fb89a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199499"
---
# <a name="steamvr-faqs"></a>SteamVR Faq

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Windows Mixed Reality 헤드셋에서 SteamVR 게임을 재생 하려면 어떻게 해야 하나요?

1. [SteamVR를 다운로드 하 여 설치](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)합니다. SteamVR 자습서는 SteamVR를 시작할 때 자동으로 시작 됩니다.
2. 헤드셋을 PC에 커넥트 하 고 동작 컨트롤러를 켭니다.
3. Windows Mixed Reality 홈이 로드 되 고 컨트롤러가 표시 되 면 바탕 화면에서 스트림 앱을 엽니다.
4. 스트림 앱을 사용 하 여 스트림 라이브러리에서 SteamVR 게임을 시작 합니다. 헤드셋을 사용 하지 않고 SteamVR 게임을 시작 하려면 Windows Mixed Reality의 **시작 > 모든 앱** 에서 찾아 시작 합니다.

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>"Windows Mixed Reality에서 SteamVR을 사용 하려면 최신 Windows 업데이트를 설치 해야 합니다." 또는 "Windows 개발자 모드가 필요 합니다." 라는 메시지가 표시 됩니다.

1. PC에서 최신 버전의 Windows 10를 실행 하 고 있는지 확인 합니다. **설정 > System > 정보** 로 이동 하 고 "Windows 사양"에서 "OS 빌드"가 16299.64 이상 인지 확인 합니다.
2. 다운로드 또는 설치를 기다리는 업데이트가 없는지 확인 합니다. **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 "업데이트 확인"을 선택 합니다. 더 이상 업데이트를 사용할 수 없을 때까지 여러 번 확인 하 고 PC를 다시 시작할 수 있습니다.

## <a name="steamvr-is-crashing-after-updating-windows"></a>업데이트 후 SteamVR가 충돌 Windows

SteamVR에 대 한 Windows Mixed Reality의 일부 이전 버전은 더 이상 Windows와 호환 되지 않습니다. SteamVR에 대 한 Windows Mixed Reality 버전이 최신 인지 확인 하려면 다음을 수행 합니다.

1. 스트림 라이브러리에서 **SteamVR에 대 한 Software > Windows Mixed Reality** 로 이동 합니다.
2. 마우스 오른쪽 단추로 클릭 하 고 "속성"으로 이동 합니다.
3. "업데이트" 탭 및 "항상이 응용 프로그램을 최신 상태로 유지"를 선택 합니다.
4. "로컬 파일" 탭으로 이동 하 고 "응용 프로그램 파일의 무결성 확인"을 선택 하 여 업데이트를 강제로 적용 합니다.
5. 스트림 및 SteamVR를 다시 시작 합니다.

업데이트 후 SteamVR 계속 충돌 하는 경우 컴퓨터에 SteamVR에 대 한 두 개의 Windows Mixed Reality 설치가 있을 수 있습니다. 확인 하려면 다음을 수행 합니다.

1. ```%localappdata%\openvr\openvrpaths.vrpath```메모장에서 찾아서 엽니다.
2. "외부 드라이버" 섹션에서 "MixedRealityVRDriver"에 대 한 여러 항목을 찾습니다.
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 여러 항목이 표시 되는 경우 두 항목의 이전 항목을 제거 합니다. 항목이 하나만 있는 경우에는 줄의 끝에 더 이상 쉼표가 없어야 합니다. 예를 들어:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. 파일을 저장하고 닫습니다.
5. 스트림 및 SteamVR를 다시 시작 합니다.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>내 컨트롤러가 SteamVR에서 예상 대로 작동 하지 않습니다.

1. SteamVR를 닫습니다.
2. Windows Mixed Reality 홈으로 돌아가서 컨트롤러가 작동 하는지 확인 합니다.
3. SteamVR 환경을 다시 시작 하 고 컨트롤러를 정상적으로 다시 시작 해야 합니다.
4. 문제가 지속 되 면 혼합 현실 범주 아래 [Windows 피드백 허브](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) 를 사용 하 여 피드백을 제공 하 고 요약에 SteamVR를 포함 합니다.

다른 게임에서 동작 컨트롤러를 다르게 사용 합니다. 시작 하는 데 도움이 되는 몇 가지 기본 사항은 다음과 같습니다.
* 스트림 대시보드를 열려면 왼쪽 엄지 스틱을 바로 누릅니다.
* SteamVR 게임을 종료 하 고 Windows Mixed Reality 홈으로 돌아가려면 Windows 단추를 누릅니다. 그런 다음 화면에 표시 되는 혼합 현실 홈 단추를 선택 합니다.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>왼쪽 및 오른쪽 컨트롤러가 SteamVR에서 반전 됩니다.

컨트롤러와 함께 게임을 시작 하 고 왼쪽 컨트롤러를 켠 다음 오른쪽 컨트롤러를 켭니다.

## <a name="my-games-are-running-slowly"></a>내 게임이 느리게 실행 되 고 있습니다.

1. PC가 Windows Mixed Reality의 SteamVR에 대 한 사양과 게임 중인 게임을 충족 하는지 확인 합니다.
2. 바탕 화면의 혼합 현실 포털에서 "일시 중지"를 선택 하 여 데스크톱 미리 보기를 중지 합니다.
3. **설정 > 시스템 >** "Windows 사양"으로 이동 하 여 "OS 빌드"가 16299.64 이상 인지 확인 합니다.
4. PC에 최신 그래픽 드라이버가 있는지 확인 합니다 ("업데이트 확인" Windows 업데이트).
5. "작업 관리자"를 선택 하 여 PC에서 리소스를 사용 하 고 있는 다른 프로세스를 확인 합니다.
6. 스트림에서 리소스를 사용 하 고 게임을 제대로 실행 하는 백그라운드에서 게임을 다운로드 하 고 있는지 확인 합니다.
7. 표시 된 창 (예: SteamVR Home)이 없는 작은 앱 클래스에는 알려진 성능 문제가 있습니다. 대부분의 앱은이 범주에 속하지 않으며 향후 업데이트에서 수정할 수 있습니다.

예기치 않은 성능 문제가 계속 발생 하는 경우 [Windows 피드백 허브](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)를 사용 하 여 피드백을 보내 주세요. 지침에 따라 [SteamVR 성능 추적을 포함](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)해야 합니다.

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR는 compositor 오류 (예: "Shared IPC Compositor 커넥트 Failed (400)")를 표시 합니다.

헤드셋 및 기본 모니터가 서로 다른 두 비디오 어댑터에 있는 경우이 문제가 발생할 수 있습니다. 모니터를 헤드셋과 동일한 어댑터에 연결 하 고 **설정 app > System > 디스플레이** 에서 기본 모니터로 구성 합니다.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR 콘텐츠가 잘못 된 장소에 표시 됩니다 (예: 밑면 또는 위쪽 헤드).

사용자의 위치를 다시 설정 합니다.

1. 왼쪽 컨트롤러의 엄지 스틱을 선택 하 여 "SteamVR 대시보드"를 표시 합니다.
2. "설정" 단추를 선택 합니다.
3. "꽂혀 있는 위치 다시 설정"을 선택 합니다.

## <a name="my-steam-app-closed-unexpectedly"></a>스트림 앱이 예기치 않게 닫혔습니다.

스트림 앱은 다음과 같은 경우 닫힙니다.

* PC 화면을 잠급니다.
* 헤드셋 제거
* 사용자 전환
* PC가 절전 모드로 전환 됨
