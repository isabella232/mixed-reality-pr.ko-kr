---
title: 헤드셋 표시 Faq
description: 표준 소비자 지원 설명서를 벗어나는 헤드셋 표시 문제에 대 한 Windows Mixed Reality 문제 해결을 표시 합니다.
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 5a7c7979c9d93d917633cbfed23dc82597368a43
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436684"
---
# <a name="headset-display-faqs"></a>헤드셋 표시 Faq

## <a name="my-headset-displays-are-black"></a>헤드셋 화면이 검게 표시 됨

* PC 성능 및 안정성을 확인 합니다.
    * 작업 관리자를 사용 하 여 PC의 CPU, GPU 또는 디스크 드라이브에 대 한 프로세스가 사고 인지 확인 합니다.
    * **이벤트 뷰어 > Windows 로그** 의 "응용 프로그램" 및 "시스템" 로그를 확인 하 여 앱이 충돌 하 고 WER (Windows 오류 보고) 보고서를 생성 하 고 있는지 확인 합니다.
    * Windows 업데이트를 확인 하 여 Windows 버전이 최신 인지 확인 합니다. "업데이트 확인"을 여러 번 선택 해야 할 수도 있습니다.
* 앱 및 게임 안정성 확인:
    * PC가 제대로 실행 되지 않는 앱 또는 게임의 최소 시스템 요구 사항을 충족 하는지 확인 합니다.
    * GPU 드라이버 버전이 최신 인지 확인 하 고 새 드라이버에서 새로운 성능 및 호환성 문제 및 재발을 확인 하십시오.
    * SteamVR apps 및 게임을 사용 하는 경우 SteamVR 및 SteamVR 구성 요소에 대 한 Windows Mixed Reality 최신 상태 인지 확인 합니다.
* HDMI 어댑터 호환성 확인:
    * HDMI 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.
    * HDMI 어댑터를 사용 하는 경우 (예: HDMI 어댑터에 대 한 미니 DisplayPort) Windows Mixed Reality와 호환 되는지 확인 합니다. 어댑터는 HDMI 2.0를 지원 해야 하며 1080p만 지 원하는 이전 어댑터가 많이 있습니다. [Windows Mixed Reality에 대 한 권장 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)참조 하세요.
    * 플러그 순서는 중요할 수 있습니다. 헤드셋 어댑터를 어댑터에 연결 하기 전에 컴퓨터에 HDMI 어댑터를 커넥트 합니다. 특히, USB-C를 사용 하 여 HDMI 어댑터를 사용 하는 경우에 해당 합니다.
    * 확장 케이블을 사용 하는 경우 제거 해 보세요.
* 그래픽 카드 및 드라이버 호환성 확인:
    * Pc 모니터로 PC의 HDMI 포트를 사용해 보세요. 일부 Pc에는 두 개 이상의 HDMI 포트가 있을 수 있으며, 일부는 활성 상태가 아닐 수 있습니다.
    * PC에 iGPU (그래픽 처리 장치)와 불연속 Gpu (그래픽 처리 장치)가 있는 경우에는 사용자가 사용자의 장치를 사용자의 컴퓨터에 연결 하 고 있는지 확인 합니다.
    * GPU 드라이버 버전을 다시 확인 합니다. 최신 상태 인지 확인 하 고 새로운 성능 및 호환성 문제 및 새로운 드라이버에 대 한 재발에도 유의 하세요.
    * 노트북에서 혼합 현실를 사용 하 고 있고 그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치한 경우 PC 제조업체의 웹 사이트 또는 Windows 업데이트에서 제공 되는 최신 그래픽 카드 드라이버로 다운 그레이드 해 보세요.
    * PC에 여러 Pc 모니터가 연결 되어 있는 경우 하나 이상의 PC 모니터의 연결을 일시적으로 해제 해 보세요.
    * PC 모니터에 대 한 사용자 지정 새로 고침 빈도를 설정한 경우 60 Hz와 같은 표준 새로 고침 속도로 일시적으로 되돌립니다.
    * Windows를 다시 설치 하지 않고 최근에 그래픽 카드를 변경한 경우 헤드셋 모니터에 올바른 드라이버가 설치 되어 있는지 확인 합니다. 헤드셋이 연결 된 상태에서 "Mixed Reality 헤드셋"이 장치 관리자의 모니터 노드 아래에 나열 되는지 확인 합니다.
    * PC에 Nvidia 그래픽 카드가 있는 경우 Nvidia의 3D 비전 소프트웨어를 사용 하지 않도록 설정 해야 합니다.
    * 일부 그래픽 카드 (특히 이전 카드)에서 HDMI 포트는 HDMI 2.0을 지원 하지 않거나 Windows Mixed Reality와 완전히 호환 되지 않을 수 있습니다. [DisplayPort 1.2에서 HDMI 2.0 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)와 함께 그래픽 카드의 DisplayPort을 사용해 보세요.
    * hp omen pc에서 hp 제품 번호 1rj99ea # 아부다비에는 Windows Mixed Reality와 호환 되지 않는 HDMI 포트가 있습니다 ("HP 지원 길잡이"를 열고 숫자가 앱 하단에 나열 됨).
    * PC에 AMD R 9 시리즈 그래픽 카드가 있고 Samsung Mixed Reality 헤드셋을 사용 하는 경우 헤드셋의 펌웨어를 버전 1.0.8 이상으로 업데이트 하 여 헤드셋에서 그래픽 카드의 HDMI 포트를 사용 합니다.
    * Surface Book 2를 사용 하는 경우 [USB-C를 사용 하 여 HDMI 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)사용 하 고 있는지 확인 합니다.
* 혼합 현실 헤드셋 하드웨어 문제를 확인 합니다.
    * 헤드셋의 하드웨어 문제를 확인 하거나 규칙을 처리 하려면 혼합 현실 헤드셋을 다른 PC에 연결 합니다.
    * 증상이 유사 하므로 PC 호환성 및 설정 문제를 먼저 확인 합니다.
* Usb 케이블이 USB 3.0 이상 포트에 연결 되어 있는지 확인 합니다. USB 3.0 포트 옆에 SS (Super Speed)가 있으며 종종 파란색으로 파란색으로 되어 있습니다.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>일부 사용 후 헤드셋이 검정색으로 표시 되는 경우

* PC에서 USB 일시 중단 또는 전원 절약 기능을 사용 하지 않도록 설정 해 보세요. 예를 들어 **설정 >에서 전원 & 절전 모드를 > 하 고, [usb 선택적 일시 중단](/windows-hardware/drivers/usbcon/usb-selective-suspend)을 >** 하 고, 장치 관리자에서 "컴퓨터를 사용 하 여 전원을 절약할 수 있도록 허용" 설정을 선택 하 고, PC의 펌웨어에서 usb 전원 저장 설정을 사용할 수 있습니다.
* PC에 연결 된 다른 모든 USB 장치 및 주변 장치와 일시적으로 연결을 끊습니다.
* GPU 드라이버 버전이 최신 인지 확인 하 고 새 드라이버에서 새로운 성능 및 호환성 문제 및 재발을 확인 하십시오.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>헤드셋의 디스플레이 중 하나가 검은색입니다.

* HDMI 어댑터를 사용 하는 경우 HDMI 2.0을 지원 하는지 확인 합니다.
* 사용할 수 있는 모든 USB 및 HDMI 확장 케이블을 제거 합니다.
* 그래픽 드라이버가 최신 인지 확인 합니다.
* 다른 PC에서 혼합 현실 헤드셋을 사용해 보세요.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>헤드셋이 파란색으로 바뀌고 혼합 현실 포털 다시 초기화가 표시 됩니다.

일반적으로 PC에서 가끔 USB 컨트롤러 안정성 문제가 있음을 나타냅니다.

* 다른 USB 포트를 사용해 보세요. PC에 USB 3.0 컨트롤러가 여러 개 있을 수 있습니다.
* 확장 케이블을 제거 합니다 (해당 하는 경우).
* PC에서 다른 모든 USB 장치를 분리 합니다.
* 외부에서 전원이 공급 되는 USB 3.0 허브를 PC에 커넥트 하 고 헤드셋을 허브에 연결 합니다.
* 데스크톱 PC를 사용 하는 경우 USB 3.0 PCIe 카드를 구입 하 여 PC에 다른 USB 컨트롤러를 추가 하는 것이 좋습니다.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>내 헤드셋은 시작 하는 동안 내 PC가 중지 되거나 검은색 화면이 표시 되도록 합니다.

일부 Pc의 경우 또는 PC를 다시 부팅 하는 동안 헤드셋이 연결 된 상태를 유지 하면 시작 프로세스에 방해가 될 수 있습니다. PC가 "기본 모니터"로 표시 되는 헤드셋 표시를 선택 하 여 PC 시작 진행률, 제대로 시작 되지 않음 또는 "중단"을 표시 하거나 비프음 오류 코드를 생성할 수 있습니다. 이 동작은 PC 제조업체와 모델 또는 그래픽 카드의 제조업체와 모델에 따라 달라 집니다. 이 문제를 해결하려면

* 다른 포트를 사용 하려면 어댑터를 사용 해야 할 수 있습니다 (다른 포트를 사용 하려면 어댑터를 사용 해야 할 수 있음). 커넥트
* PC의 BIOS/UEFI 펌웨어가 최신 상태 인지 확인 하세요 (이 작업을 수행 하는 데 익숙한 경우에만 PC의 BIOS/UEFI 펌웨어를 업데이트).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Surface PC를 사용 하는 경우 내 PC 또는 헤드셋이 깜박임, 플래시 또는 검정색 상태를 유지 합니다.

* HDMI 2.0을 지 원하는 HDMI 어댑터를 사용 하 고 있는지 확인 합니다. 이전 HDMI 어댑터 대부분은 혼합 현실 헤드셋에 충분 하지 않은 1080p 해상도만 지원 합니다.
* 그래픽 드라이버가 최신 상태 인지 확인 합니다. Windows 업데이트 및 PC 제조업체의 웹 사이트에서 업데이트 된 그래픽 드라이버를 확인 합니다.
* 일부 Surface 장치는 Windows Mixed Reality 호환 되지 않습니다. [Surface 호환성 및 요구 사항](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)에 대해 자세히 알아보세요.

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>종료 하 고 빠른 시작을 수행한 후 헤드셋 디스플레이가 작동 하지 않음

헤드셋 케이블 및 USB 케이블을 헤드셋에서 분리 한 후 다시 연결 합니다.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>내 헤드셋 디스플레이는 고르지 않지만 혼합 현실 포털의 미리 보기 창이 제대로 표시 됩니다.

* PC의 시스템 리소스 (CPU, 메모리 및 하드 드라이브)가 사용 가능 하 고 다른 앱 또는 프로세스에서 사용 되 고 있지 않은지 확인 합니다.
* 그래픽 드라이버를 업데이트 합니다.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>장치 관리자에 "설치 클래스가 없거나 잘못 되었습니다" 오류가 발생 합니다.

장치 관리자에 노란색 느낌표가 표시 된 "HoloLens 센서"가 표시 되는 경우 추가 정보는 장치를 선택 합니다. "이 장치의 드라이버가 설치 되어 있지 않습니다. 라는 메시지가 표시 되 면 (코드 28)--설치 클래스가 없거나 잘못 되었습니다. "는 PC가 [N을 Windows 10](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)실행 하 고 있기 때문입니다. n 버전의 Windows 10 및 Windows 11은 Windows Mixed Reality을 지원 하지 않으며 Windows 10 또는 Windows 11의 n이 아닌 버전을 설치 해야 합니다.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>내 헤드를 이동 하 여 이중 비전을 표시 하는 경우 내 WMR 환경이 떨림 또는 stutters

통합 된 그래픽 및 Nvidia GPU를 사용 하는 랩톱에서 다음 프레임 후 이전 프레임을 표시 하는 데 걸리는 시간이 지나면 오류가 발생 합니다. 그러면 요, 피치 또는 롤 이동에서 헤드를 더 빨리 이동 하 게 됩니다. Nvidia 그래픽 드라이버 436.48 후 드라이버에 문제가 있는 것 같습니다.  이 드라이버를 설치 하면 Nvidia에서 업데이트 된 드라이버의 문제를 해결할 때까지 문제가 해결 됩니다. Nvidia 그래픽 드라이버 436.48을 직접 설치 하려면 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)를 방문 하십시오.

## <a name="im-uncomfortable-in-my-headset"></a>헤드셋의 불편 함

Windows Mixed Reality에서 편안 하 게 보호 하는 방법에 대 한 일반적인 정보는 [몰입 형 헤드셋 상태, 안전 및 편안 Windows Mixed Reality](wmr-health-safety-comfort.md)을 참조 하세요. 특정 헤드셋에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>내 헤드셋에서 명확 하 게 볼 수 있는 방법

헤드셋의 맞춤을 조정해 보세요. 얼굴에서 위/아래로 이동 하거나 왼쪽 및 오른쪽으로 이동 하 고 straps를 조정 하 여 snug 수 있도록 합니다.

헤드셋에 노브가 있는 경우 보정 설정을 조정 합니다. 그렇지 않으면 **설정 > Mixed reality > 시각적 품질** 으로 이동 하 여 보정을 조정 합니다. 특정 장치의 보정에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>헤드셋에서 보기 주위에 검정색 테두리가 자주 표시 됩니다. 경우에 따라 터널을 보고 있는 것 같습니다.

즉, 애플리케이션이 PC에서 프레임 속도에 도달할 수 없으며 시스템에서 이전 프레임을 사용하여 헤드셋에서 보기를 렌더링합니다. 애플리케이션은 보고 있는 세계의 일부만 렌더링하기 때문에 프레임 속도에 일관되게 도달하지 않으면 시스템은 이전 관점에서 세계를 렌더링하려고 시도하고 누락된 세부 정보를 검은색으로 채웁니다. 이 경우가 자주 발생하는 경우:

1. 메모리 및 CPU를 확보하려면 모든 무인 프로그램을 닫거나 중지합니다.
2. 애플리케이션에서 세부 정보 설정을 줄입니다.
3. 설정 > Mixed Reality > **헤드셋 디스플레이로** 이동하여 Windows Mixed Reality 홈에 표시되는 세부 정보를 줄입니다.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>헤드셋의 보기가 지터링되고 더듬거림이 많습니다.

시스템에서 헤드셋에 콘텐츠를 렌더링할 수 없거나 추적 시스템에 문제가 발생할 수 있습니다.

1. 작업 관리자 열어 PC에 충분한 컴퓨팅 리소스가 있는지 확인합니다. CPU 사용 가능의 80%, RAM 400MB, 디스크 IO가 80% 미만이어야 합니다.
2. 하드웨어에 대한 최신 그래픽 드라이버가 있는지 확인합니다. 그래픽 [드라이버 섹션을](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver)참조하세요.
3. 실내에 충분한 조명이 있는지 확인합니다.
4. 디바이스를 분리하고, Windows Mixed Reality 닫고, 다시 연결합니다.
5. PC를 다시 시작합니다.
6. 문제가 지속되면 고객 [지원](https://support.microsoft.com/)에 문의합니다.