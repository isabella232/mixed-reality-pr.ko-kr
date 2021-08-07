---
title: 헤드셋 연결 FAQ
description: 헤드셋 연결 Windows Mixed Reality 헤드셋 연결 문제 해결은 표준 소비자 지원 설명서를 초과합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 문제 해결, 오류, 도움말, 지원, 헤드셋
appliesto:
- Windows 10
ms.openlocfilehash: ed8708d39953e79d445f3794d335d9a9451c9bf9fe8c2fca1feb792ee3f9b2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189225"
---
# <a name="headset-connectivity-faqs"></a>헤드셋 연결 FAQ

## <a name="my-headset-will-not-wake-up"></a>헤드셋이 절전 모드를 깨우지 않음

헤드셋이 절전 모드이고 절전 모드에서 절전 모드를 클릭하여 작동하지 않는 경우 PC를 다시 시작합니다.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>컴퓨터에 HDMI 및/또는 디스플레이 포트가 없습니다.

어댑터를 사용해야 할 수도 있습니다. 지원되는 어댑터 목록은 [여기로](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 이동하세요.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋과 함께 USB 또는 HDMI 및/또는 DisplayPort 확장 케이블을 사용할 수 있나요?

Windows Mixed Reality 헤드셋은 공식적으로 USB, HDMI 또는 DisplayPort 확장 케이블 사용을 지원하지 않습니다. 이러한 케이블을 사용하는 경우 PC의 USB 컨트롤러와 Mixed Reality 헤드셋 간의 신호 무결성 및 버스 전원 차이로 인해 Mixed Reality 환경이 영향을 받을 수 있습니다. 다음과 같은 경우 확장 케이블 없이 헤드셋을 사용해 보세요.

* 헤드셋 디스플레이는 파란색 화면을 간략하게 표시한 다음 검은색으로 바뀌고 Mixed Reality 포털 다시 시작하거나 사용 중에 완전히 열거를 해제합니다.
* 헤드셋 오디오가 잘리거나 결함이 있습니다.
* 헤드셋이 검은색과 올바른 디스플레이 사이를 깜박임

## <a name="i-am-getting-a-check-your-display-cable-error"></a>"디스플레이 케이블 확인" 오류가 발생합니다.

* 어댑터를 사용하여 헤드셋을 PC에 연결하는 경우 Windows Mixed Reality 지원하며 4K가 지원되는지 확인합니다. 또한 헤드셋을 어댑터에 연결하기 전에 어댑터를 PC에 연결해 보세요.
* 다른 HDMI 또는 DisplayPort 포트를 사용해 보세요.
* 헤드셋을 DisplayPort 1.2 이상 또는 HDMI 1.4 이상에 커넥트. 포트가 PC에서 가장 고급 그래픽 카드와 일치하는지 확인합니다.
* PC에 통합 그래픽과 불연속 그래픽이 모두 있는 경우 활성 그래픽 카드에서 HDMI 또는 DisplayPort 포트를 사용하고 있는지 확인합니다. 이는 PC 디스플레이를 비 HDMI 포트에 연결해야 한다는 의미일 수 있습니다.
* PC에 통합 그래픽과 불연속 그래픽이 모두 있고 통합 그래픽이 오래되어 Windows Mixed Reality 지원하지 않는 경우 통합 GPU를 사용하지 않도록 설정을 시도합니다.
* PC 모니터를 PC의 HDMI 또는 DisplayPort 포트에 커넥트. 그래픽 드라이버가 최신인지 확인합니다. AMD, Nvidia 또는 Intel에서 직접 드라이버를 다운로드하여 설치합니다. Windows 업데이트에 게시된 것보다 최신일 가능성이 높습니다.
* HDMI 포트에 연결된 외부 모니터가 있는 경우 대신 DisplayPort에 연결하고 헤드셋에 HDMI 포트를 사용합니다.
* 헤드셋의 HDMI 케이블을 "HDMI in" 포트가 아닌 PC의 "HDMI 아웃" 포트에 연결했는지 확인합니다.
* Windows 디스플레이 케이블 연결을 검색하지 못할 수 있습니다. 디바이스 관리자를 열고 헤드셋이 "모니터" 아래에 나열되는지 확인합니다. 그렇지 않은 경우 **작업 > 하드웨어 변경 내용 검색을** 선택합니다.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>"헤드셋에 넣기"라는 메시지가 있지만 헤드셋이 있습니다.

헤드셋을 Windows Mixed Reality 공간을 다시 로드하는 데 몇 초 정도가 필요할 수 있습니다. 이 메시지가 사라지지 않으면 렌즈 사이의 헤드셋 내부에 있는 근접 센서에서 보호 스티커가 제거되었는지 확인합니다. 문제가 지속되면 헤드셋 제조업체에 문의하세요.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>"헤드셋을 커넥트"라는 메시지가 있지만 헤드셋을 연결했습니다.

- 헤드셋의 USB 및 HDMI 또는 DisplayPort 케이블이 PC의 올바른 포트에 연결되어 있는지 확인합니다. 올바른 포트를 식별하는 방법은 다음과 같습니다.

    - USB 3.0 포트에는 "SS" 표시("SuperSpeed"를 나타낸다)가 있는 특수 로고가 있습니다. 포트 내부 부분은 일반적으로 파란색이지만 이전 USB 2.0 포트는 일반적으로 내부에 검은색 또는 흰색입니다.
    - 컴퓨터에 두 개의 HDMI 또는 DisplayPort 포트가 있는 경우 컴퓨터의 마더보드가 아닌 그래픽 카드에 연결하는 포트를 사용합니다. 불연속 포트가 컴퓨터의 확장 슬롯에 있는 경우가 많지만 항상 명확하지는 않습니다. 한 포트를 시도해도 작동하지 않는 경우 다른 포트를 사용해 보세요.

- 헤드셋에서 USB 및 HDMI 또는 DisplayPort 케이블을 분리하고 연결하여 안전하게 연결되었는지 확인합니다. USB 케이블을 연결할 때 USB 케이블을 삽입하는 동안 일시 중지하지 않도록 합니다.
- 헤드셋의 부분 열거형이 표시되는 경우 외부에서 전원이 켜진 USB 3.0 허브를 사용해 보세요. 예를 들어 일련의 USB 디바이스가 열거되지만 Device Manager의 "Mixed Reality 헤드셋" 아래에는 아무 것도 없습니다.
- 헤드셋 제조업체의 웹 사이트로 이동하여 헤드셋의 드라이버 및 펌웨어를 업데이트합니다.
- 헤드셋을 다른 PC로 커넥트 디바이스 관리자를 엽니다. PC가 Windows Mixed Reality 완전히 호환되지 않더라도 헤드셋이 열거되는지 확인할 수 있습니다. 헤드셋이 여러 PC에 열거되지 않으면 하드웨어 문제가 발생할 수 있습니다.

> [!NOTE]
> Surface 사용자의 경우: 이전 버전의 Surface Dock 및 Surface Book USB Hub 펌웨어 업데이트 소프트웨어는 Mixed Reality 헤드셋과 호환되지 않습니다. Surface PC에서 "헤드셋 커넥트" 메시지가 발생하는 경우 디바이스 관리자에서 "코드 10: 디바이스를 시작할 수 없습니다" 오류를 보고하는 디바이스가 있는지 확인합니다. 그렇다면 [충돌하는 드라이버 를 제거합니다.](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book) 이 작업을 한 번만 수행하면 됩니다.

Windows 10-N 사용자에 대한 참고: PC가 Windows 10 N을 실행하는 경우 Mixed Reality 헤드셋을 연결한 후 디바이스 관리자에 "코드 28: 설치 클래스가 없거나 잘못되었습니다." 오류가 표시됩니다. N 버전의 Windows 10 Windows Mixed Reality 지원되지 않습니다. 자세한 내용은 다음 [지침을](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 따르세요.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>"USB 케이블 확인" 또는 "USB 속도 부족" 메시지가 표시됩니다.

* PC에서 지원되는 USB 3.0 포트를 사용하고 있는지 확인합니다.

    * 헤드셋의 USB 케이블이 모든 방식으로 연결되어 있는지 확인합니다.
    * Windows Mixed Reality [Portal을](install-windows-mixed-reality.md#launch-mixed-reality-portal) 실행하여 PC의 USB 3.0 컨트롤러가 지원되는지 확인합니다.
    * 헤드셋을 PC의 다른 USB 3.0 포트로 커넥트. 일부 PC에는 USB 3.0 컨트롤러가 두 개 이상 있습니다.
    * PC에 연결된 모든 USB 디바이스의 연결을 일시적으로 끊고 헤드셋만 연결합니다.
    * 사용자 지정 빌드 PC에서는 포트가 USB 3.0 포트로 표시될 수 있지만 USB 2.0 컨트롤러에 연결될 수 있습니다. 헤드셋이 연결되면 디바이스 관리자를 열고 헤드셋에서 열거된 디바이스를 찾아서 한 번 클릭한 다음 연결로 **> 디바이스 보기로** 이동합니다.
* 다른 PC에서 헤드셋을 사용해 보세요. 다른 PC가 Windows Mixed Reality 완전히 호환되지 않는 경우 디바이스 관리자를 확인하여 "USB 속도 부족" 메시지가 표시되는지 확인합니다. 여러 PC에서 제대로 열거되지 않으면 헤드셋에 결함이 있을 수 있습니다.
* 헤드셋과 컴퓨터 간에 모든 Extenders 또는 Hubs를 제거합니다.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>헤드셋을 연결한 후 Mixed Reality 포털 시작되지 않았습니다.

헤드셋이 기본 문제로 인해 제대로 검색되지 않았을 수 있습니다. Mixed Reality 포털 수동으로 시작하고 표시되는 오류 메시지를 찾습니다.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>PC가 절전 모드 또는 최대 절전 모드로 전환되거나 헤드셋이 연결된 PC를 다시 시작할 때 헤드셋 작동이 중지되었습니다.

1. 디바이스 관리자를 열고 헤드셋이 "Mixed Reality 디바이스" 아래에 나열되어 있는지 확인합니다.
2. "Mixed Reality 디바이스" 아래에서 헤드셋을 선택하고 디바이스 상태가 "이 디바이스가 제대로 작동 중"으로 표시되어 있는지 확인합니다.
3. 디바이스 작동이 중지되었다는 "코드 43" 오류가 표시되거나 헤드셋이 "Mixed Reality 디바이스" 아래에 나열되지 않으면 헤드셋의 USB 케이블을 분리하고 다시 하십시오. Microsoft는 잠재적인 소프트웨어/드라이버 상호 운용성 문제를 조사하고 있으며 이로 인해 이 오류가 발생할 수 있습니다. 이 문제는 소수의 PC에 영향을 미치며, Mixed Reality 헤드셋 드라이버에 대한 향후 업데이트에서 해결될 예정입니다.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>헤드셋을 누르면 PC를 절전 모드로 전환하거나 최대 절전 모드에 있을 때 PC에서 버그 검사(파란색 화면)가 생성됩니다.

10.0.19041.2034 드라이버 이상에 있는지 확인합니다.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>헤드셋을 연결했을 때 헤드셋 드라이버가 자동으로 설치되지 않음

새 PC 또는 새로 설치된 Windows 10 복사본이 있는 PC에서 헤드셋 드라이버는 다른 Windows 업데이트 뒤에 큐에 대기할 수 있으며 즉시 설치되지 않을 수 있습니다.

1. 디바이스 **관리자 시작 >** 이동하여 헤드셋의 "Mixed Reality 디바이스"를 찾습니다. 디바이스 상태는 "디바이스가 제대로 작동 중"을 나타내야 합니다.
2. 디바이스를 마우스 오른쪽 단추로 클릭하고 "드라이버 업데이트"를 선택합니다.

작동하지 않는 경우 드라이버를 제거해 보세요.

1. 디바이스 **관리자 시작 >** 이동하여 헤드셋의 "Mixed Reality 디바이스"를 찾습니다. 디바이스 상태는 "디바이스가 제대로 작동 중"을 나타내야 합니다.
2. 디바이스를 마우스 오른쪽 단추로 클릭하고 "디바이스 제거"를 선택합니다.
3. 표시되는 새 팝업에서 "이 디바이스에 대한 드라이버 소프트웨어 삭제" 확인란을 선택한 다음, "제거"를 선택합니다.
4. 완료되면 PC에서 헤드셋을 분리하고 다시 연결합니다. Windows 이제 업데이트에서 새 드라이버를 다운로드하고 설치합니다.

참고: N 버전의 Windows 있는 경우 Windows Mixed Reality 사용하려면 Windows 10 정규 버전으로 전환해야 합니다.