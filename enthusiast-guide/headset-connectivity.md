---
title: 헤드셋 연결 Faq
description: 헤드셋 연결 Windows Mixed Reality 헤드셋 연결 문제 해결 설명서를 참조 하세요.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 헤드셋
appliesto:
- Windows 10
ms.openlocfilehash: 25b42377d92273573da909ab52d67578eb6469ec
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132077"
---
# <a name="headset-connectivity-faqs"></a>헤드셋 연결 Faq

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>내 컴퓨터에 HDMI 및/또는 디스플레이 포트가 없습니다.

어댑터를 사용 해야 할 수도 있습니다. 지원 되는 어댑터 목록을 보려면 [여기](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 로 이동 하세요.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋에서 USB 또는 HDMI 및/또는 DisplayPort 확장 케이블을 사용할 수 있나요?

Windows Mixed Reality 헤드셋은 USB, HDMI 또는 DisplayPort 확장 케이블의 사용을 공식적으로 지원 하지 않습니다. 이러한 케이블을 사용 하면 PC의 USB 컨트롤러와 혼합 현실 헤드셋 사이에 발생 하는 신호 무결성 및 버스 전력의 차이 때문에 혼합 현실 환경에 큰 영향을 줄 수 있습니다. 헤드셋에 파란색 화면이 잠깐 표시 되 면 블랙 및 Mixed Reality 포털을 사용 중에 다시 시작 하거나 완전히 제거 하거나 헤드셋 오디오가 glitchy 되거나 헤드셋 오디오가 검정색으로 깜박이는 경우에는 확장 케이블 없이 헤드셋을 사용해 보세요.

## <a name="i-am-getting-a-check-your-display-cable-error"></a>"디스플레이 케이블 확인" 오류가 표시 됩니다.

* 모든 어댑터를 사용 하 여 헤드셋을 PC에 연결 하는 경우 Windows Mixed Reality를 지원 하는지 확인 합니다 (어댑터는 4K 가능 해야 함). 또한 헤드셋을 어댑터에 연결 하기 전에 어댑터를 PC에 연결 해 봅니다.
* 다른 HDMI 및/또는 DisplayPort 포트를 사용해 보세요.
* 헤드셋을 DisplayPort 1.2 이상 또는 HDMI 1.4 이상에 연결 합니다. 포트가 PC의 고급 그래픽 카드와 일치 하는지 확인 합니다.
* PC에 통합 그래픽과 개별 그래픽이 모두 있는 경우 활성 그래픽 카드에서 HDMI 및/또는 DisplayPort 포트를 사용 하 고 있는지 확인 합니다. 이것은 PC 디스플레이를 비 HDMI 포트에 연결 해야 한다는 의미입니다.
* PC에 통합 된 그래픽과 개별 그래픽이 모두 있고 통합 그래픽이 오래 되어 Windows Mixed Reality를 지원 하지 않는 경우 통합 GPU를 사용 하지 않도록 설정 해 보세요.
* Pc 모니터를 PC의 HDMI 및/또는 DisplayPort 포트에 연결 합니다. 그래픽 드라이버가 최신 상태 인지 확인 합니다. AMD, Nvidia 또는 Intel에서 Windows 업데이트에 게시 된 것 보다 최신 버전으로 직접 다운로드 하 여 설치 합니다.
* 외부 모니터가 HDMI 포트에 연결 된 경우 DisplayPort에 연결 하 고 헤드셋에 대해 HDMI 포트를 사용 하세요.
* 헤드셋의 HDMI 케이블을 PC의 "hdmi 아웃" 포트에 연결 했는지 확인 합니다. "HDMI in" 포트는 아닙니다.
* Windows에서 디스플레이 케이블 연결을 검색 하지 못할 수 있습니다. Device Manager를 열고 헤드셋이 "모니터" 아래에 표시 되는지 확인 합니다. 그렇지 않은 경우 **작업 > 하드웨어 변경 내용 검색** 을 선택 합니다. 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>"헤드셋에 배치" 라는 메시지가 표시 되지만 헤드셋은

헤드셋에 배치 하는 경우 공간을 다시 로드 하는 데 몇 초 정도 걸릴 수 있습니다. 이 메시지가 나타나지 않으면 lenses 사이에 있는 헤드셋 내부의 근접 센서에서 보호 스티커가 제거 되었는지 확인 합니다. 그래도 문제가 해결 되지 않으면 헤드셋 제조업체에 문의 하십시오.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>"헤드셋 연결" 메시지를 표시 하지만 내가 헤드셋에 연결 했습니다.

- 헤드셋의 USB 및 HDMI 및/또는 DisplayPort 케이블이 PC의 올바른 포트에 연결 되어 있는지 확인 하세요. 올바른 포트를 식별 하는 방법은 다음과 같습니다.

    - USB 3.0 포트에는 "SS" 표시가 있는 특수 로고 ("SuperSpeed"를 나타냄)가 있습니다. 포트의 내부 부분은 일반적으로 파란색 이지만 이전 USB 2.0 포트는 일반적으로 내부에서 검정이 나 흰색입니다.
    - 컴퓨터에 두 개의 HDMI 및/또는 DisplayPort 포트가 있는 경우 컴퓨터의 마더보드가 아닌 그래픽 카드에 연결 하는 포트를 사용 합니다. 불연속 포트는 컴퓨터의 확장 슬롯에 있는 경우가 많지만 항상 명확 하지는 않습니다. 하나의 포트를 시도 했지만 작동 하지 않는 경우 다른 포트를 사용해 보세요.

- 컴퓨터를 분리 하 고 헤드셋에서 USB 및 HDMI 및/또는 DisplayPort 케이블을 연결 하 여 안전 하 게 연결 하세요. USB 케이블을 연결 하는 경우 USB 케이블을 삽입 하는 동안 일시 중지 하지 마십시오.
- 헤드셋의 부분 열거를 표시 하는 경우 (일련의 USB 장치가 열거 하지만 Device Manager의 "Mixed Reality 헤드셋"에 아무것도 표시 되지 않음) 외부에서 제공 되는 USB 3.0 허브를 사용해 보세요.
- 헤드셋 제조업체의 웹 사이트로 이동 하 여 헤드셋의 드라이버 및 펌웨어를 업데이트 합니다.
- 헤드셋을 다른 PC에 연결 하 고 Device Manager를 엽니다. 해당 PC가 Windows Mixed Reality와 완전히 호환 되지 않더라도 헤드셋이를 열거 하는지 확인할 수 있습니다. 헤드셋에서 여러 Pc를 열거 하지 않는 경우 하드웨어 문제가 있을 수 있습니다.

Surface 사용자에 대 한 참고 사항: 이전 버전의 Surface Dock 및 Surface Book USB 허브 펌웨어 업데이트 소프트웨어는 혼합 현실 헤드셋과 호환 되지 않습니다. Surface PC에서 "헤드셋 연결" 메시지가 표시 되는 경우 장치가 Device Manager에서 "코드 10: 장치를 시작할 수 없습니다" 오류를 보고 하는지 확인 합니다. 그렇다면 충돌 하 [는 드라이버를 제거](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)합니다. 이 작업은 한 번만 수행 해야 합니다.

Windows 10 N 사용자의 경우: PC에서 Windows 10 N을 실행 하는 경우 혼합 현실 헤드셋을 연결한 후 Device Manager에 "코드 28: 설치 클래스가 없거나 잘못 되었습니다" 오류가 표시 됩니다. N 버전의 Windows 10은 Windows Mixed Reality에서 지원 되지 않습니다. 자세한 내용은 다음 [지침](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 을 따르세요.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>"USB 케이블 확인" 또는 "USB 속도 부족" 메시지가 표시 됨

* PC에서 지원 되는 USB 3.0 포트를 사용 하 고 있는지 확인 합니다.

    * 헤드셋의 USB 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.
    * [Windows Mixed Reality 포털](install-windows-mixed-reality.md#launch-mixed-reality-portal) 을 실행 하 여 PC의 USB 3.0 컨트롤러가 지원 되는지 확인 합니다.
    * 헤드셋을 PC의 다른 USB 3.0 포트에 연결 합니다. 일부 Pc에는 두 개 이상의 USB 3.0 컨트롤러가 있습니다.
    * PC에 연결 된 모든 USB 장치를 일시적으로 분리 하 고 헤드셋만 연결 합니다.
    * 사용자가 빌드한 Pc에서는 포트가 USB 3.0 포트로 표시 될 수 있지만 USB 2.0 컨트롤러에 연결 될 수 있습니다. 헤드셋이 연결 된 상태에서 Device Manager을 열고, 헤드셋에서 열거 된 장치를 찾아 한 번 클릭 한 다음, **연결로 > 장치 보기** 로 이동 합니다.
* 다른 PC에서 헤드셋을 사용해 보세요. 다른 PC가 Windows Mixed Reality와 완전히 호환 되지 않는 경우 Device Manager를 확인 하 여 "USB 속도 부족" 메시지가 표시 되는지 확인 합니다. 여러 Pc에서 제대로 열거 되지 않으면 헤드셋에 결함이 있을 수 있습니다.
* 헤드셋과 컴퓨터 간에 extender 또는 허브를 제거 합니다.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>혼합 현실 포털이 내 헤드셋에 연결한 후 시작 되지 않았습니다.

기본 문제로 인해 헤드셋이 제대로 검색 되지 않았을 수 있습니다. 혼합 현실 포털을 수동으로 시작 하 고 표시 되는 오류 메시지를 찾습니다.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>내 컴퓨터가 절전 모드 또는 최대 절전 모드로 전환 되거나 내 헤드셋이 연결 된 PC를 다시 시작 하는 경우 내 헤드셋의 작동이 중지 됨

1. Device Manager를 열고 헤드셋이 "Mixed Reality 장치" 아래에 표시 되는지 확인 합니다.
2. "혼합 현실 장치"에서 헤드셋을 선택 하 고 장치 상태가 "이 장치가 제대로 작동 하 고 있음을 나타냅니다."가 표시 되는지 확인 합니다.
3. 장치가 작동을 중지 했음을 나타내는 "코드 43" 오류가 표시 되는 경우 또는 헤드셋의 USB 케이블에서 분리 하 고 replug는 "Mixed Reality 장치" 아래에 표시 되지 않는 경우입니다. Microsoft는이 오류가 발생할 수 있는 잠재적인 소프트웨어/드라이버 상호 운용성 문제를 조사 하 고 있습니다. 이 문제는 적은 수의 Pc에 영향을 주므로 혼합 현실 헤드셋 드라이버에 대 한 향후 업데이트에서 해결 될 것으로 예상 됩니다.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>내 헤드셋은 PC를 절전 모드 또는 최대 절전 모드로 전환할 때 내 PC에서 버그 확인 (블루 스크린)을 생성 하도록 합니다.

10.0.19041.2034 드라이버 또는 최신 버전 인지 확인 합니다.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>헤드셋 드라이버가 헤드셋에 연결 될 때 자동으로 설치 되지 않았습니다.

새 Pc 또는 Windows 10의 새로 설치 된 복사본을 사용 하는 Pc에서는 헤드셋 드라이버가 다른 Windows 업데이트 뒤에 대기 될 수 있으며 즉시 설치 되지 않을 수도 있습니다.

1. **시작 > Device Manager** 로 이동 하 여 헤드셋의 "Mixed Reality 장치" 아래에서 확인 합니다. 장치 상태에 "장치가 제대로 작동 하 고 있습니다."가 표시 되어야 합니다.
2. 장치를 마우스 오른쪽 단추로 클릭 하 고 "드라이버 업데이트"를 선택 합니다.

작동 하지 않는 경우 드라이버를 제거 해 보세요.

1. **시작 > Device Manager** 로 이동 하 여 헤드셋의 "Mixed Reality 장치" 아래에서 확인 합니다. 장치 상태에 "장치가 제대로 작동 하 고 있습니다."가 표시 되어야 합니다.
2. 장치를 마우스 오른쪽 단추로 클릭 하 고 "장치 제거"를 선택 합니다.
3. 표시 되는 새 팝업에서 "이 장치에 대 한 드라이버 소프트웨어 삭제" 확인란을 선택 하 고 "제거"를 선택 합니다.
4. 이 작업이 완료 되 면 PC에서 헤드셋을 분리 하 고 다시 연결 합니다. 이제 Windows 업데이트 새 드라이버를 다운로드 하 여 설치 합니다.

참고: N 버전의 Windows를 사용 하는 경우 windows Mixed Reality를 사용 하려면 windows 10의 일반 버전으로 전환 해야 합니다.