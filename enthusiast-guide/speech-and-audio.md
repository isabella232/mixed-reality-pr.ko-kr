---
title: 음성 및 오디오 Faq
description: 표준 소비자 지원 설명서를 벗어나는 음성 및 오디오 Windows 혼합 현실 문제 해결.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 오디오 문제, 음성 문제
ms.openlocfilehash: d685190248dd17792f941cf53e3a57499cd3e662
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725894"
---
# <a name="speech-and-audio-faqs"></a>음성 및 오디오 Faq

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>헤드셋의 소리를 듣지 못할 수 있거나, 내 헤드셋 대신 내 컴퓨터를 통해 사운드가 재생 되 고 있습니다.

* 모던 헤드셋에 내장 헤드폰이 포함 되지 않은 경우 헤드셋의 오디오 잭에 헤드폰을 연결 합니다. 잭이 헤드셋 센터 또는 lenses 바로 뒤에 위치 하는 경우가 많습니다. 찾을 수 없는 경우 헤드셋 제조업체에 문의 하세요.
* 일부 오디오 헤드셋에는 볼륨을 제어 하기 위한 물리적 단추가 있습니다. 오디오가 작동 하지 않는 경우 볼륨이 작동 중지 되었는지 아니면 음소거 상태 인지 확인 합니다.
* 오디오가 기본 Windows 재생 장치로 전환 됩니다. 
    * 헤드셋을 사용 하지 않는 경우
    * 센터를 위로 대칭 이동
    * 혼합 현실 포털 앱을 닫습니다.
    * 앱이 15 분 동안 사용 되지 않은 경우 
    * **설정 > 혼합 현실 > 오디오 및 음성** 에서이 설정을 변경할 수 있습니다.
* 오디오 헤드셋이 오디오 잭에 꽂혀 있는지 확인 합니다. 특히 Acer 헤드셋은 오디오 헤드셋이 연결 되어 있는지 확인 하는 데 더 많은 주의가 필요할 수 있습니다.
* 오디오 헤드셋/마이크가 PC가 아닌 헤드셋에 꽂혀 있는지 확인 합니다.
* **설정 > 시스템 > 사운드** 의 사운드 제어판은 사용 하도록 설정 된 끝점이 아니라 사용 하도록 설정 된 오디오 끝점만 표시 합니다. 헤드셋을 입고 있지 않으면 헤드셋 오디오 장치를 사용할 수 없습니다. 이를 확인 하려면 사운드 제어판을 마우스 오른쪽 단추로 클릭 하 고 "사용 하지 않도록 설정 된 장치 표시"를 선택 합니다. 장치 이름은 "Realtek USB 2.0 Audio" 이며 "속성" 페이지에서 이름을 바꿀 수 있습니다. 재생 및 기록 탭 모두에 대해이 작업을 수행할 수 있습니다.
* 오디오가 혼합 현실 앱에서 작동 하지 않는 경우 (예: Netflix 앱). Windows Mixed Reality가 OS 버전과 일치 하도록 자동으로 업데이트 되지 않는 알려진 문제가 원인일 수 있습니다. 이 문제를 해결 하 고 가장 혼합 된 현실 경험을 얻으려면 **설정 > 업데이트 & 보안 > Windows 업데이트 > 업데이트 확인** 으로 이동 합니다.

> [!NOTE]
> * Windows Mixed Reality 공간 오디오는에 기본 제공 되거나 몰입 형 헤드셋에 직접 연결 된 헤드폰에서 가장 잘 작동 합니다. PC에 연결 된 PC 스피커 또는 헤드폰이 공간 오디오에서 제대로 작동 하지 않을 수 있습니다.
> * Windows Mixed Reality는 Bluetooth 오디오 헤드셋을 지원 하지 않습니다.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>갑작스러운 볼륨 변경, 오디오 분실 또는 고주파음이 발생 함

* SteamVR을 통해 시작 된 앱과 같은 일부 앱은 혼합 현실 포털을 시작 하거나 중지할 때 오디오 장치가 변경 될 때 오디오를 잃어 버릴 수 있습니다. 이를 해결 하려면 Mixed Reality 포털을 다시 열고 앱을 다시 시작 합니다.
* 다른 멀티미디어 USB 장치 (예: 웹 cam)가 Windows Mixed Reality 헤드셋과 동일한 내부 또는 외부 USB 허브를 공유 하는 경우 헤드셋 오디오 잭 또는 헤드폰에는 때때로 소리가 나 오디오가 없을 수 있습니다. 다른 허브를 사용 하는 USB 포트에 헤드셋을 꽂거나 다른 USB 멀티미디어 장치를 분리/사용 하지 않도록 설정 합니다.
* 연결 된 헤드폰에서 큰 양의 소음이 발생 하는 경우 PC의 USB 허브가 Windows Mixed Reality 헤드셋에 충분 한 전원을 제공 하지 못할 수 있습니다. 이 경우 [피드백 허브](https://docs.microsoft.com/hololens/hololens-feedback) 버그로 파일을 작성 하 고 다음을 시도 합니다.
    * 확장 케이블 제거
    * 전용 외부 기반 USB 3.0 허브 사용
    * PC의 다른 USB 포트

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Bluetooth 오디오 헤드셋이 예상 대로 작동 하지 않음

Microsoft는 Windows Mixed Reality에서 Bluetooth 오디오 헤드셋을 사용 하지 않는 것이 좋습니다. Bluetooth 오디오 주변 장치는 Windows Mixed Reality 음성 및 공간 음향 환경에서 제대로 작동 하지 않습니다. Bluetooth 오디오 헤드셋은 마이크 입력 및 스테레오 출력을 동시에 지원 하지 않으므로 gamechat 또는 기타 음성 입력에 사용할 때 스테레오 또는 spatialized 소리가 들리지 않습니다. 또한 Bluetooth 오디오 헤드셋은 동작 컨트롤러 환경에 부정적인 영향을 줄 수 있습니다.

## <a name="sound-isnt-coming-from-expected-directions"></a>소리는 예상 되는 방향에서 제공 되지 않습니다.

Windows Mixed Reality 홈에는 공간 소리 (홈에 있는 응용 프로그램에서와 같이 소리를 들면 오디오)가 포함 되어 있습니다. 각 앱에서 가까이 나 더 가까운 곳으로 이동 하면 현실감의 의미를 높이기 위해 소리 방향 및 수준이 변경 됩니다. 다음은 예기치 않은 소리 방향에 대 한 몇 가지 잠재적인 원인입니다.

* 홈의 배경 지원 음악 앱 (예: 그루브 음악)에서 음악을 열고 재생 한 후 게임과 같은 몰입 형 VR 환경을 열면 음악 앱의 사운드가 공간 소리에서 스테레오로 페이드 인 됩니다. 사용자와 소리 사이에 더 이상 거리가 없으므로 크게 보일 수 있습니다.
* Windows Mixed Reality 헤드셋을 사용 하기 전에 PC에서 Cortana를 사용 하도록 설정한 경우 Windows Mixed Reality 홈의 앱에 적용 되는 공간 사운드가 손실 될 수 있습니다. 이 문제를 해결 하려면 Windows Mixed Reality를 시작 하기 전에 바탕 화면에서 cortana가 "cortana에 응답 하도록 허용 **>** "을 해제 하거나 "windows Sonic for 헤드폰"을 사용 하도록 설정 합니다.
    1. Windows Mixed Reality 홈에서 데스크톱 앱 창으로 이동 합니다.
    2. 바탕 화면 작업 표시줄에서 스피커 아이콘을 마우스 왼쪽 단추를 클릭 하 고 오디오 장치 목록에서 선택 합니다.
    3. 바탕 화면 작업 표시줄에서 스피커 아이콘을 마우스 오른쪽 단추로 클릭 하 고 "스피커 설정" 메뉴에서 "헤드폰 용 Windows Sonic"을 선택 합니다.
    4. 모든 오디오 장치 (끝점)에 대해이 단계를 반복 합니다.

## <a name="speech-commands-are-not-working-as-expected"></a>음성 명령이 예상 대로 작동 하지 않습니다.

* 음성 명령을 사용 하려면 PC의 음성 및 언어 설정이 [Windows Mixed Reality에서 지원 되는 언어로](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages)설정 되어 있어야 합니다. Windows 음성 및 언어 설정을 확인 하려면 **설정 > 시간 & 언어 > 지역 & 언어** 및 **설정 > 시간 & 언어 > 음성** 을 선택 합니다.
* 헤드셋에 기본 제공 마이크가 없는 경우 헤드셋 또는 PC에 마이크와 헤드폰을 연결 해야 합니다. 사용자가 착용 할 때 헤드셋에 마이크 입력을 자동으로 전환 하려면 **설정 > 혼합 현실 > 오디오 및 음성** 으로 이동 하 고 "헤드셋을 사용 하지 않는 경우 헤드셋 mic로 전환 합니다."로 이동 합니다.
* 일부 오디오 헤드셋은 마이크를 음소거 및 음소거 해제 하는 실제 단추를 포함 합니다. 음성 명령이 작동 하지 않는 경우 마이크가 음소거 되어 있는지 확인 합니다.
* 마이크를 사용 하는 오디오 헤드셋은 dangles 케이블을 사용 하지 않는 환경에서 음성 명령에 적합 하지 않습니다.
* Cortana는 혼합 현실 포털 세션에서 처음 호출 될 때 느릴 수 있습니다. **설정 > cortana로 이동 하 > cortana에 게 문의** 하 고 "cortana에 게 응답 합니다."가 사용 하도록 설정 되어 있는지 확인 합니다.
* 일부 Pc에서는 헤드셋 연결 마이크의 기본 음성 캡처 이득이 너무 낮게 설정 되어 있을 수 있습니다. 불안정 한 음성 명령 또는 받아쓰기가 발생 하는 경우 마이크 설정 문제 해결사를 실행 합니다.
    1. Windows mixed Reality 홈의 데스크톱 앱으로 이동 합니다 (Windows Mixed Reality에 사용 하는 마이크에 영향을 주는 헤드셋).
    2. **설정 > 시간 & 언어 > 음성** 으로 이동 합니다.
    3. "마이크" 섹션에서 "시작"을 선택 합니다.
    4. 문제 해결사 마법사에서 적절 한 끝점을 선택 합니다.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>하나의 오디오 헤드셋만 있으며 데스크톱 및 내 헤드셋 모두에 사용 하려고 합니다.

하나의 오디오 헤드셋만 있고 기본 제공 헤드폰이 있는 헤드셋이 없는 경우 헤드셋 대신 오디오 헤드셋을 PC에 연결 합니다. 그런 다음 혼합 현실 포털 설정에서 "헤드셋 오디오로 전환"을 해제 합니다.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>헤드폰에 대 한 돌비 Atmos 전환 하려고 합니다.

Windows Mixed Reality 환경 및 해당 앱은 혼합 현실 환경에 맞게 사용자 지정 된 헤드폰 공간 오디오 기술용 Windows Sonic을 사용 합니다. 헤드폰에 대 한 돌비 Atmos 같은 다른 공간 오디오 기술은 SteamVR 게임과 같은 전체 화면 앱에 적용 될 수 있지만, Windows Mixed Reality 셸 환경 및 앱 (예: 절벽의 벽에 웹 브라우저 배치 또는 비디오를 사용 하는 경우), 헤드폰 공간 사운드 및 acoustics에 대해 Windows Sonic을 사용 하 여 설계 되었습니다.
