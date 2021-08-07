---
title: 헤드셋 표시 FAQ
description: 표준 소비자 지원 설명서를 벗어나는 헤드셋 표시 문제에 대한 Windows Mixed Reality 문제 해결을 표시합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 문제 해결, 오류, 도움말, 지원
appliesto:
- Windows 10
ms.openlocfilehash: 811b5160c739c8b19fde737e7a61bcef84e0cf60a87927adbe21241e229f3f22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189393"
---
# <a name="headset-display-faqs"></a>헤드셋 디스플레이 FAQ

## <a name="my-headset-displays-are-black"></a>헤드셋 디스플레이가 검은색임

* PC 성능 및 안정성 확인:
    * 작업 관리자 사용하여 PC의 CPU, GPU 또는 디스크 드라이브를 최대화하고 있는 프로세스가 있는지 확인합니다.
    * **이벤트 뷰어 > Windows 로그의** "애플리케이션" 및 "시스템" 로그를 확인하여 앱이 충돌하고 WER(Windows 오류 보고) 보고서를 생성하는지 확인합니다.
    * Windows 업데이트를 확인하여 Windows 버전이 최신 버전인지 확인합니다. "업데이트 확인"을 여러 번 선택해야 할 수 있습니다.
* 앱 및 게임 안정성 확인:
    * PC가 올바르게 실행되지 않는 앱 또는 게임의 최소 시스템 요구 사항을 충족하는지 확인합니다.
    * GPU 드라이버 버전이 최신 버전인지 확인하고 새 드라이버에 대한 새로운 성능 및 호환성 문제 및 회귀를 확인합니다.
    * SteamVR 앱 및 게임을 사용하는 경우 SteamVR 및 SteamVR 구성 요소에 대한 Windows Mixed Reality 최신 상태로 있는지 확인합니다.
* HDMI 어댑터 호환성 확인:
    * HDMI 케이블이 모든 방식으로 연결되어 있는지 확인합니다.
    * HDMI 어댑터(예: HDMI 어댑터에 대한 Mini DisplayPort)를 사용하는 경우 Windows Mixed Reality 호환되는지 확인합니다. 어댑터는 HDMI 2.0을 지원해야 하며 1080p만 지원하는 오래된 어댑터가 많이 있습니다. [Windows Mixed Reality 권장 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)참조하세요.
    * 플러그 순서가 중요할 수 있습니다. 특히 USB-C-HDMI 어댑터를 사용하는 경우 헤드셋을 어댑터에 연결하기 전에 HDMI 어댑터를 PC에 커넥트.
    * 확장 케이블을 사용하는 경우 제거해 보세요.
* 그래픽 카드 및 드라이버 호환성 확인:
    * PC 모니터를 통해 PC의 HDMI 포트를 사용해 보세요. 일부 PC에는 둘 이상의 HDMI 포트가 있을 수 있으며 모든 PC가 활성 상태일 수 있는 것은 아닙니다.
    * PC에 iGPU(통합 그래픽 처리 장치)와 dGPU(불연속 그래픽 처리 장치)가 있는 경우 dGPU의 HDMI 포트에 연결되어 있는지 확인합니다.
    * GPU 드라이버 버전을 다시 확인합니다. 최신인지 확인하지만 새로운 드라이버의 새로운 성능 및 호환성 문제 및 회귀에도 주의해야 합니다.
    * 랩톱에서 Mixed Reality 사용하고 그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치한 경우 PC 제조업체의 웹 사이트 또는 Windows 업데이트에 제공된 최신 그래픽 카드 드라이버로 다운그레이드해 보세요.
    * PC에 연결된 PC 모니터가 여러 개 있는 경우 하나의 PC 모니터를 제외한 모든 모니터의 연결을 일시적으로 끊어 보세요.
    * PC 모니터에 대한 사용자 지정 새로 고침 속도를 설정한 경우 60Hz와 같은 표준 새로 고침 빈도로 일시적으로 되돌려 보세요.
    * Windows 다시 설치하지 않고 그래픽 카드를 최근에 변경한 경우 헤드셋 모니터에 올바른 드라이버가 설치되어 있는지 확인합니다. 헤드셋을 연결한 후 "Mixed Reality 헤드셋"이 디바이스 관리자의 모니터 노드 아래에 나열되어 있는지 확인합니다.
    * PC에 Nvidia 그래픽 카드가 있는 경우 Nvidia의 3D Vision 소프트웨어가 사용하지 않도록 설정되어 있는지 확인합니다.
    * 일부 그래픽 카드(특히 이전 카드)에서 HDMI 포트는 HDMI 2.0을 지원하지 않거나 Windows Mixed Reality 완전히 호환되지 않을 수 있습니다. [DisplayPort 1.2에서 HDMI 2.0 어댑터로](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)그래픽 카드의 DisplayPort를 사용해 보세요.
    * HP 제품 번호가 1RJ99EA#ED인 HP Omen PC에는 Windows Mixed Reality 호환되지 않는 HDMI 포트가 있습니다("HP 지원 도우미"를 열면 번호가 앱 아래쪽에 나열됩니다).
    * PC에 AMD R9 시리즈 그래픽 카드가 있고 Samsung Mixed Reality 헤드셋을 사용하는 경우 헤드셋의 펌웨어를 버전 1.0.8 이상으로 업데이트하여 헤드셋과 함께 그래픽 카드의 HDMI 포트를 사용합니다.
    * Surface Book 2를 사용하는 경우 [Surface USB-C-HDMI 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)를 사용하고 있는지 확인합니다.
* Mixed Reality 헤드셋 하드웨어 문제를 확인합니다.
    * 헤드셋의 하드웨어 문제를 확인하거나 배제하려면 Mixed Reality 헤드셋을 다른 PC에 연결합니다.
    * 증상이 유사하기 때문에 먼저 PC 호환성 및 설정 문제를 확인합니다.
* USB 케이블이 USB 3.0 이상 포트에 연결되어 있는지 확인합니다. USB 3.0 포트 옆에는 SS(슈퍼 속도)가 있으며 종종 파란색으로 표시됩니다.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>일부 사용 후 헤드셋 디스플레이가 가끔 검은색으로 바뀝니다.

* PC에서 USB 일시 중단 또는 절전 기능을 사용하지 않도록 합니다. 예를 들어 **설정 > System > Power & Sleep > [USB 선택적 일시 중단,](/windows-hardware/drivers/usbcon/usb-selective-suspend)** 디바이스 관리자의 "컴퓨터에서 이 디바이스의 전원을 끄도록 허용" 설정 및 PC의 펌웨어에 있는 USB 절전 설정이 있습니다.
* PC에 연결된 다른 USB 디바이스 및 주변 장치의 연결을 일시적으로 끊습니다.
* GPU 드라이버 버전이 최신 버전인지 확인하고 새 드라이버에 대한 새로운 성능 및 호환성 문제 및 회귀를 확인합니다.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>헤드셋에 표시되는 표시 중 하나가 검은색입니다.

* HDMI 어댑터를 사용하는 경우 HDMI 2.0을 지원하는지 확인합니다.
* 사용할 수 있는 USB 및 HDMI 확장 케이블을 제거합니다.
* 그래픽 드라이버가 최신인지 확인합니다.
* 다른 PC에서 Mixed Reality 헤드셋을 사용해 보세요.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>헤드셋이 파란색으로 표시되고 Mixed Reality 포털 다시 활성화됩니다.

이는 일반적으로 PC에서 가끔 발생하는 USB 컨트롤러 안정성 문제를 나타냅니다.

* 다른 USB 포트를 사용해 보세요. PC에 여러 USB 3.0 컨트롤러가 있을 수 있습니다.
* 확장 케이블을 제거합니다(해당하는 경우).
* PC에서 다른 모든 USB 디바이스를 분리합니다.
* 외부에서 전원이 켜진 USB 3.0 허브를 PC에 커넥트 헤드셋을 허브에 연결합니다.
* 데스크톱 PC를 사용하는 경우 USB 3.0 PCIe 카드를 구매하여 PC에 다른 USB 컨트롤러를 추가하는 것이 좋습니다.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>헤드셋으로 인해 PC가 중단되거나 시작하는 동안 검은색 화면이 표시됩니다.

일부 PC에서는 PC를 켜기 전이나 다시 부팅하는 동안 헤드셋을 연결한 상태로 두면 시작 프로세스가 방해가 될 수 있습니다. PC에서 헤드셋 표시를 "기본 모니터"로 선택하여 PC 시작 진행 상황을 표시하거나, 제대로 시작하지 않거나, "중단"하거나, 경고음 오류 코드를 생성할 수 있습니다. 동작은 PC 메이크 및 모델 또는 그래픽 카드의 메이크 및 모델에 따라 달라집니다. 이 문제를 해결하려면

* 헤드셋을 그래픽 카드의 다른 포트로 커넥트(다른 포트를 사용하려면 어댑터를 사용해야 할 수도 있음)
* PC의 BIOS/UEFI 펌웨어가 최신인지 확인합니다(하지만 PC의 BIOS/UEFI 펌웨어만 업데이트합니다.)

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Surface PC를 사용할 때 내 PC 또는 헤드셋이 깜박이거나 깜박이거나 검은색으로 유지됩니다.

* HDMI 2.0을 지원하는 HDMI 어댑터를 사용하고 있는지 확인합니다. 많은 이전 HDMI 어댑터는 1080p 해상도만 지원하며 Mixed Reality 헤드셋에는 충분하지 않습니다.
* 그래픽 드라이버가 최신인지 확인합니다. 업데이트된 그래픽 드라이버에 대한 Windows 업데이트 및 PC 제조업체의 웹 사이트를 확인합니다.
* 일부 Surface 디바이스는 Windows Mixed Reality 호환되지 않습니다. [Surface 호환성 및 요구 사항에](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)대해 자세히 알아보세요.

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>종료하고 빠른 시작을 수행하면 헤드셋 디스플레이가 작동하지 않습니다.

헤드셋에서 HDMI 케이블 및 USB 케이블을 분리한 다음 다시 연결합니다.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>헤드셋 표시가 끊어졌지만 Mixed Reality 포털 미리 보기 창이 잘 표시됩니다.

* PC의 시스템 리소스(CPU, 메모리 및 하드 드라이브)를 사용할 수 있고 다른 앱 또는 프로세스에서 사용할 수 없는지 확인합니다.
* 그래픽 드라이버를 업데이트합니다.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>디바이스 관리자에서 "설치 클래스가 없거나 잘못되었습니다." 오류가 발생합니다.

디바이스 관리자에 노란색 느낌표가 있는 "HoloLens 센서"가 표시되면 추가 세부 정보를 보려면 디바이스를 선택합니다. "이 디바이스의 드라이버가 설치되지 않았습니다. (코드 28)--설치 클래스가 없거나 잘못되었습니다.", 이는 일반적으로 PC가 [N Windows 10](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)실행 중이기 때문입니다. N 버전의 Windows 10 Windows Mixed Reality 지원하지 않으며 N이 아닌 버전의 Windows 10 설치해야 합니다.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>헤드를 이동하고 이중 비전을 표시할 때 WMR 환경이 지터링되거나 더듬거림

통합 그래픽 및 Nvidia GPU가 있는 랩톱에서 이전 프레임이 다음 프레임 이후에 표시되도록 하는 일정 기간 후에 오류가 발생하여 이중 비전이 요, 피치 또는 롤 이동에서 머리 이동 속도가 빨라집니다. Nvidia Graphics Driver 436.48 이후 드라이버에 문제가 있는 것으로 나타납니다.  이 드라이버를 설치하면 Nvidia가 업데이트된 드라이버의 문제를 해결할 때까지 문제가 해결됩니다. Nvidia Graphics Driver 436.48을 직접 설치하는 경우 [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)를 방문합니다.

## <a name="im-uncomfortable-in-my-headset"></a>헤드셋을 봤는데요.

Windows Mixed Reality 편의성에 대한 일반적인 내용은 [몰입형 헤드셋 상태, 안전성 및 편의성 Windows Mixed Reality 참조하세요.](wmr-health-safety-comfort.md) 특정 헤드셋에 대한 자세한 내용은 헤드셋 제조업체에 문의하세요.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>헤드셋에서 더 명확한 보기를 얻으려면 어떻게 해야 합니까?

헤드셋의 적합도를 조정해 보세요. 얼굴에서 위아래로 이동하거나 왼쪽과 오른쪽으로 이동하고, 스너그처럼 느낄 수 있도록 자를 조정합니다.

헤드셋에 보정을 조정할 노브가 있는 경우 보정 설정을 조정합니다. 그렇지 않으면 혼합 현실 **> 시각적 품질 설정 >** 이동하여 보정을 조정합니다. 특정 디바이스의 보정에 대한 자세한 내용은 헤드셋 제조업체에 문의하세요.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>헤드셋의 보기 주위에 검은색 테두리가 자주 표시됩니다. 경우에 따라 터널을 보고 있는 것 같습니다.

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