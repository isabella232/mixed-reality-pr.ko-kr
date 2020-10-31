---
title: 헤드셋 표시 Faq
description: 표준 소비자 지원 설명서를 벗어나는 헤드셋 표시 문제에 대 한 Windows Mixed Reality 문제 해결을 표시 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원
appliesto:
- Windows 10
ms.openlocfilehash: df91b6d131a8c2ce0faeecc659842418ef03c7c1
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132087"
---
# <a name="headset-display-faqs"></a>헤드셋 표시 Faq

## <a name="my-headset-displays-are-black"></a>헤드셋 화면이 검게 표시 됨

* PC 성능 및 안정성을 확인 합니다.
    * 작업 관리자를 사용 하 여 PC의 CPU, GPU 및/또는 디스크 드라이브에 대 한 프로세스가 사고 인지 확인 합니다.
    * **이벤트 뷰어 > Windows 로그** 의 "응용 프로그램" 및 "시스템" 로그를 확인 하 여 WER (Windows 오류 보고) 보고서가 자주 발생 하는 앱이 있는지 확인 합니다.
    * Windows 업데이트를 확인 하 여 Windows 버전이 최신 인지 확인 합니다. "업데이트 확인"을 여러 번 선택 해야 할 수도 있습니다.
* 앱 및 게임 안정성 확인:
    * 제대로 수행 되지 않는 앱 또는 게임을 실행 하기 위한 최소 시스템 요구 사항을 충족 하는 PC 인지 확인 합니다.
    * GPU 드라이버 버전이 최신 인지 확인 하 고 새 드라이버에서 새로운 성능 및 호환성 문제 및 재발을 확인 하십시오.
    * SteamVR apps 및 게임을 사용 하는 경우 SteamVR 및 SteamVR 구성 요소에 대 한 Windows Mixed Reality가 최신 상태 인지 확인 합니다.
* HDMI 어댑터 호환성 확인:
    * HDMI 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.
    * HDMI 어댑터를 사용 하는 경우 (예: HDMI 어댑터에 대 한 미니 DisplayPort) Windows Mixed Reality와 호환 되는지 확인 합니다. 어댑터는 HDMI 2.0를 지원 해야 하며 1080p만 지 원하는 이전 어댑터가 많이 있습니다. [Windows Mixed Reality의 권장 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)참조 하세요.
    * 플러그 순서는 중요할 수 있습니다. 헤드셋 어댑터를 어댑터에 연결 하기 전에 컴퓨터에 HDMI 어댑터를 연결 합니다. 특히, USB-C에서 HDMI 어댑터를 사용 하는 경우에는 특히 그렇습니다.
    * 확장 케이블을 사용 하는 경우 제거 해 보세요.
* 그래픽 카드 및 드라이버 호환성 확인:
    * Pc 모니터로 PC의 HDMI 포트를 사용해 보세요. 일부 Pc에는 두 개 이상의 HDMI 포트가 있을 수 있으며, 일부는 활성 상태가 아닐 수 있습니다.
    * PC에 iGPU (통합 그래픽 처리 장치)와 개별 Gpu (그래픽 처리 장치)가 모두 있는 경우에는 사용자가 사용자의 컴퓨터에 연결 되어 있는지 확인 합니다.
    * GPU 드라이버 버전을 다시 확인 합니다. 최신 상태 인지 확인 하 고 새로운 성능 및 호환성 문제 및 새로운 드라이버에 대 한 재발에도 유의 하세요.
    * 노트북에서 혼합 현실를 사용 하 고 있고 그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치한 경우 PC 제조업체의 웹 사이트 또는 Windows 업데이트에서 제공 되는 최신 그래픽 카드 드라이버로 다운 그레이드 해 보세요.
    * Pc에 여러 개의 PC 모니터가 연결 되어 있는 경우 하나 이상의 PC 모니터의 연결을 일시적으로 해제 해 보세요.
    * PC 모니터에 대 한 사용자 지정 새로 고침 빈도를 설정한 경우 60Hz와 같은 표준 새로 고침 속도로 일시적으로 되돌립니다.
    * Windows를 다시 설치 하지 않고 최근에 그래픽 카드를 변경한 경우 헤드셋 모니터에 올바른 드라이버가 설치 되어 있는지 확인 합니다. 헤드셋이 연결 된 상태에서 "Mixed Reality 헤드셋"이 Device Manager의 모니터 노드 아래에 나열 되는지 확인 합니다.
    * PC에 Nvidia 그래픽 카드가 있는 경우 Nvidia의 3D 비전 소프트웨어를 사용 하지 않도록 설정 해야 합니다.
    * 일부 그래픽 카드 (특히 이전 카드)에서 hdmi 포트는 HDMI 2.0을 지원 하지 않거나 Windows Mixed Reality와 완전히 호환 되지 않을 수 있습니다. [DisplayPort 1.2에서 HDMI 2.0 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)와 함께 그래픽 카드의 DisplayPort을 사용해 보세요.
    * Hp Omen Pc HP 제품 번호 1RJ99EA # 아부다비에는 Windows Mixed Reality와 호환 되지 않는 HDMI 포트가 있습니다 ("HP 지원 길잡이"를 열고 숫자가 앱 하단에 나열 됨).
    * PC에 AMD R 9 시리즈 그래픽 카드가 있고 Samsung Mixed Reality 헤드셋을 사용 하는 경우 헤드셋의 펌웨어를 버전 1.0.8 이상으로 업데이트 하 여 헤드셋에서 그래픽 카드의 HDMI 포트를 사용 합니다.
    * Surface Book 2를 사용 하는 경우 [USB-C를 사용 하 여 HDMI 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)사용 하 고 있는지 확인 합니다.
* 혼합 현실 헤드셋 하드웨어 문제를 확인 합니다.
    * 헤드셋의 하드웨어 문제를 확인 하거나 규칙을 처리 하려면 혼합 현실 헤드셋을 다른 PC에 연결 합니다.
    * 증상이 매우 유사 하므로 PC 호환성 및 설정 문제를 먼저 확인 합니다.
* Usb 케이블이 USB 3.0 이상 포트에 연결 되어 있는지 확인 합니다. USB 3.0 포트 옆에 SS (Super Speed)가 있으며 종종 파란색으로 파란색으로 되어 있습니다.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>일부 사용 후 헤드셋이 검정색으로 표시 되는 경우

* PC에서 USB 일시 중단 또는 전원 절약 기능을 사용 하지 않도록 설정 해 보세요. 예를 들어 **설정 > 시스템 > 전원 & 절전 > [USB 선택적 일시 중단](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)** , "컴퓨터에서 전원 절약을 위해이 장치를 끌 수 있도록 허용" 설정, Device Manager의 모든 USB 절전 설정 및 PC의 펌웨어를 저장 합니다.
* PC에 연결 된 다른 모든 USB 장치 및 주변 장치와 일시적으로 연결을 끊습니다.
* GPU 드라이버 버전이 최신 인지 확인 하 고 새 드라이버에서 새로운 성능 및 호환성 문제 및 재발을 확인 하십시오.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>헤드셋의 디스플레이 중 하나가 검은색입니다.

* HDMI 어댑터를 사용 하는 경우 HDMI 2.0을 지원 하는지 확인 합니다.
* 사용할 수 있는 모든 USB 및 HDMI 확장 케이블을 제거 합니다.
* 그래픽 드라이버가 최신 인지 확인 합니다.
* 다른 PC에서 혼합 현실 헤드셋을 사용해 보세요.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-re-initializes"></a>헤드셋이 파란색으로 바뀌고 혼합 현실 포털이 다시 초기화 됩니다.

일반적으로 PC에서 가끔 USB 컨트롤러 안정성 문제가 있음을 나타냅니다.

* 다른 USB 포트를 사용해 보세요. PC에 USB 3.0 컨트롤러가 여러 개 있을 수 있습니다.
* 확장 케이블을 제거 합니다 (해당 하는 경우).
* PC에서 다른 모든 USB 장치를 분리 합니다.
* 외부적으로 구동 되는 USB 3.0 허브를 PC에 연결 하 고 헤드셋을 허브에 연결 합니다.
* 데스크톱 PC를 사용 하는 경우 USB 3.0 PCIe 카드를 구입 하 여 PC에 다른 USB 컨트롤러를 추가 하는 것이 좋습니다.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>내 헤드셋은 시작 하는 동안 내 PC가 중지 되거나 검은색 화면이 표시 되도록 합니다.

일부 Pc의 경우 또는 PC를 다시 부팅 하는 동안 헤드셋이 연결 된 상태를 유지 하면 시작 프로세스에 방해가 될 수 있습니다. PC가 "기본 모니터"로 표시 되는 헤드셋 표시를 선택 하 여 PC 시작 진행률, 제대로 시작 하지 않음 또는 "중단"을 표시 하 고 비프음 오류 코드를 생성할 수 있습니다. 이 동작은 PC 제조업체와 모델 및/또는 그래픽 카드의 제조업체와 모델에 따라 달라 집니다. 이 문제를 해결하려면

* 다른 포트를 사용 하려면 어댑터를 사용 해야 할 수 있는 경우에는 그래픽 카드의 다른 포트에 헤드셋을 연결 합니다.
* PC의 BIOS/UEFI 펌웨어가 최신 상태 인지 확인 합니다 (이 작업을 수행 하는 데 익숙한 경우에만 PC의 BIOS/UEFI 펌웨어를 업데이트).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Surface PC를 사용 하는 경우 내 PC 또는 헤드셋이 깜박임, 플래시 또는 검정색 상태를 유지 합니다.

* HDMI 2.0을 지 원하는 HDMI 어댑터를 사용 하 고 있는지 확인 합니다. 이전 HDMI 어댑터 대부분은 혼합 현실 헤드셋에 충분 하지 않은 1080p 해상도만 지원 합니다.
* 그래픽 드라이버가 최신 상태 인지 확인 합니다. Windows 업데이트 및 PC 제조업체의 웹 사이트에서 업데이트 된 그래픽 드라이버를 확인 합니다.
* 일부 Surface 장치는 Windows Mixed Reality와 호환 되지 않습니다. [Surface 호환성 및 요구 사항](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)에 대해 자세히 알아보세요.

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>종료 하 고 빠른 시작을 수행한 후 헤드셋 디스플레이가 작동 하지 않음

헤드셋 케이블 및 USB 케이블을 헤드셋에서 분리 한 후 다시 연결 합니다.

## <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>내 헤드셋은 매우 고르지 않지만 혼합 현실 포털의 미리 보기 창이 표시 됩니다.

* PC의 시스템 리소스 (CPU, 메모리 및 하드 드라이브)가 사용 가능 하 고 다른 앱 또는 프로세스에서 사용 되 고 있지 않은지 확인 합니다.
* 그래픽 드라이버를 업데이트 합니다.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Device Manager에 "설치 클래스가 없거나 잘못 되었습니다" 오류가 발생 합니다.

Device Manager에 노란색 느낌표가 표시 된 "HoloLens 센서"가 표시 되는 경우 추가 정보를 보려면 장치를 선택 합니다. "이 장치의 드라이버가 설치 되어 있지 않습니다. 라는 메시지가 표시 되 면 (코드 28)--설치 클래스가 없거나 잘못 되었습니다. "는 PC에서 [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)을 실행 하 고 있기 때문입니다. N 버전의 Windows 10은 Windows Mixed Reality를 지원 하지 않으므로 N이 아닌 Windows 10 버전을 설치 해야 합니다.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>내 헤드를 이동 하 여 이중 비전을 표시 하는 경우 내 WMR 환경이 떨림 또는 stutters

통합 된 그래픽 및 Nvidia GPU를 사용 하는 랩톱에서 다음 프레임 후 이전 프레임을 표시 하는 데 걸리는 시간이 지나면 오류가 발생 합니다. 그러면 요, 피치 또는 롤 이동에서 헤드를 더 빨리 이동 하 게 됩니다. Nvidia 그래픽 드라이버 436.48 후 드라이버에 문제가 있는 것 같습니다.  이 드라이버를 설치 하면 Nvidia에서 업데이트 된 드라이버의 문제를 해결할 때까지 문제가 해결 됩니다. Nvidia 그래픽 드라이버 436.48을 직접 설치 하려면 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)를 방문 하십시오.

## <a name="im-uncomfortable-in-my-headset"></a>헤드셋의 불편 함

Windows Mixed Reality에서 편안 하 게 보호 하는 방법에 대 한 일반적인 정보는 [Windows Mixed reality 모던 헤드셋 상태, 안전 및 편안](wmr-health-safety-comfort.md)을 참조 하세요. 특정 헤드셋에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>내 헤드셋에서 명확 하 게 볼 수 있는 방법

헤드셋의 맞춤을 조정해 보세요. 얼굴에서 위/아래로 이동 하거나 왼쪽 및 오른쪽으로 이동 하 고 straps를 조정 하 여 snug 수 있도록 합니다.

헤드셋에 노브가 있는 경우 보정 설정을 조정 합니다. 그렇지 않으면 **설정 > 혼합 현실 > 시각적 품질** 로 이동 하 여 보정을 조정 합니다. 특정 장치의 보정에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>헤드셋에서 보기 주위에 검정색 테두리가 자주 표시 됩니다. 경우에 따라 터널을 조회 하는 것과 같습니다.

이는 응용 프로그램이 PC에서 프레임 속도로 적중 할 수 없고 시스템에서 이전 프레임을 사용 하 여 헤드셋에서 보기를 렌더링 하는 것을 의미 합니다. 응용 프로그램은 원하는 전 세계 부분만 렌더링 하므로 프레임 속도에 지속적으로 도달 하지 않으면 시스템은 이전 관점에서 전 세계를 렌더링 하려고 시도 하 고 누락 된 세부 정보를 검정으로 채웁니다. 자주 발생 하는 경우:

1. 모든 불필요 한 프로그램을 닫거나 종료 하 여 메모리와 CPU를 확보 합니다.
2. 응용 프로그램에서 세부 설정을 줄입니다.
3. Windows Mixed Reality 홈에 표시 되는 세부 정보 양을 줄이려면 **설정 > 혼합 현실 > 헤드셋 표시** 로 이동 합니다.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>헤드셋의 보기는 jittering 일지 매우 많습니다.

시스템이 헤드셋에 콘텐츠를 렌더링 하지 못하거나 추적 시스템에 문제가 있을 수 있습니다. 다음 사항을 확인합니다.

1. 작업 관리자를 열어 PC에 계산 리소스가 충분 한지 확인 합니다. 80%의 CPU 사용 가능, 400MB RAM, 디스크 IO는 80% 미만 이어야 합니다.
2. 하드웨어에 대 한 최신 그래픽 드라이버가 있는지 확인 합니다. [그래픽 드라이버 섹션](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver)을 참조 하세요.
3. 대화방에 충분 한 조명이 있는지 확인 합니다.
4. 장치를 분리 하 고 Windows Mixed Reality를 닫은 다음 다시 연결 합니다.
5. PC를 다시 시작 합니다.
6. 문제가 지속 되 면 [고객 지원](https://support.microsoft.com/)에 문의 하세요.
