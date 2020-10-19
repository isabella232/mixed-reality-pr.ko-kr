---
title: 시작하기 전에
description: PC가 Windows Mixed Reality와 호환 되 고 준비 되었는지 확인 하는 방법입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 호환, 호환성, 시작, 설정, PC, 시스템 요구 사항
appliesto:
- Windows 10
ms.openlocfilehash: c76f670230a4a19b53b7e8f938b13e79bb7c8db7
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174449"
---
# <a name="before-you-start"></a>시작하기 전에

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Windows Mixed Reality를 실행 하는 데 필요한 사항

* Windows [Mixed Reality 헤드 (HMD) 디스플레이](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)입니다.
* Windows 10 버전 1709 이상을 실행 하는 새로운 [Windows Mixed reality READY pc](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 또는 Windows mixed REALITY 호환 pc입니다.
* 인터넷 연결
* 디스플레이, USB 및 Bluetooth 어댑터 (헤드셋 또는 컴퓨터에 내장 되지 않은 경우)
* 동작 컨트롤러, Xbox 컨트롤러 또는 마우스 및 키보드
* 마이크가 있는 헤드폰 (HMD에서 기본 제공 되지 않는 경우)
* 열려 있는 많은 공간

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>PC가 Windows Mixed Reality와 호환 되는지 확인 합니다.

PC가 Windows Mixed Reality와 호환 되는지 확인 하려면 [Windows Mixed reality 최소 pc 하드웨어 요구 사항을](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 확인 하거나 Pc에서 [Windows mixed reality 포털](install-windows-mixed-reality.md#launch-mixed-reality-portal) 을 실행 합니다.

PC 호환성 문제에 대 한 자세한 내용은 [여기](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)를 참조 하세요.

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Windows 10 버전 1709 이상이 설치 되어 있는지 확인 합니다.

Windows Mixed Reality를 사용 하려면 Windows 10 버전 1709 (사용자가 나이를 사용 하 여 업데이트) 이상을 실행 해야 합니다. 호환 되는 Windows 10 버전은 다음과 같습니다.
* Windows 10 버전 1709 (동일 구성 업데이트, 빌드 16299)
* Windows 10 버전 1803 (스프링 업데이트, 빌드 17134)
* Windows 10 버전 1809 (10 월 업데이트, 빌드 17763)

장치가 현재 실행 중인 Windows 10 버전을 확인 하려면 **시작** 단추를 선택한 다음 **설정 > 시스템 > 정보**를 선택 합니다.

PC에서 Windows 10이 최신 상태 인지 확인 하려면 **시작** 단추를 선택한 다음 **설정 > 업데이트 & 보안 > Windows 업데이트**를 선택 합니다.  **업데이트 확인**을 선택합니다. 업데이트를 사용할 수 있는 경우 설치 합니다.

PC를 최신 상태로 유지 하는 방법에 대 한 자세한 내용은 [여기](https://support.microsoft.com/en-us/help/12373/windows-update-faq) 를 참조 하세요.

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>PC가 인터넷에 연결 되어 있는지 확인 합니다.

PC가 인터넷에 연결 되어 있는지 확인 합니다. Windows Mixed Reality를 실행 하는 데 필요한 드라이버와 일부 추가 소프트웨어를 다운로드 해야 합니다.  Wi-Fi 네트워크 연결이 요금제로 설정 된 경우에는 데이터 통신 해제로 변경 합니다. [자세한 정보를 알아보세요](https://support.microsoft.com/en-us/help/4028458/windows-metered-connections-in-windows-10).

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>호환 되는 그래픽 드라이버가 있는지 확인 합니다.

혼합 현실 설치를 완료 하려면 PC에 WDDM 2.2 이상 그래픽 드라이버가 있어야 합니다. 호환 되는 그래픽 드라이버가 아직 없는 경우 다음 원본을 사용해 보세요.

* Windows 업데이트를 사용 하 여 최신 중요 드라이버 업데이트 확인 (**> 시작 Windows 설정 > 업데이트 및 보안 > 업데이트 확인**)
* 최신 선택적 드라이버 업데이트를 확인 합니다.
    1. **시작 > Device Manager**을 마우스 오른쪽 단추로 클릭 합니다.
    2. **디스플레이 어댑터**를 확장 합니다.
    3. 그래픽 카드를 마우스 오른쪽 단추로 클릭 하 고 **업데이트 드라이버 > 선택 하 여 업데이트 된 드라이버 소프트웨어에 대해 자동으로 검색**합니다.
* 웹 사이트에서 PC의 제조업체 (OEM)를 확인 합니다.
* PC에서 그래픽 카드의 제조업체에 대 한 웹 사이트 (예: AMD, Intel 또는 NVIDIA)를 확인 합니다.

## <a name="make-sure-that-you-have-any-required-adapters"></a>필요한 어댑터가 있는지 확인 합니다.

Windows Mixed Reality 호환 PC에는 몰입 형 헤드셋을 연결 하는 데 필요한 전체 크기의 HDMI 및 USB 3.0 포트가 없을 수 있습니다. 또는 혼합 현실 포털 요구 사항을 충족 하기 위해 Bluetooth 어댑터가 필요할 수 있습니다.  이 경우 헤드셋 및 동작 컨트롤러를 연결 하는 어댑터가 필요 합니다. 필요한 어댑터 유형 목록과 [여기](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)에서 특정 어댑터 모델에 대 한 몇 가지 권장 사항을 찾을 수 있습니다.

## <a name="make-sure-that-you-have-input-devices"></a>입력 장치가 있는지 확인 합니다.

Windows Mixed Reality는 Windows Mixed Reality 동작 컨트롤러에서 가장 잘 작동 하도록 설계 되었습니다 .이는 벽에 하드웨어를 설치할 필요 없이 자연스럽 고 정확한 상호 작용을 제공 합니다. 그러나 Xbox 컨트롤러나 마우스 및 키보드를 사용할 수도 있습니다.

## <a name="get-headphones-if-your-headset-didnt-come-with-them"></a>헤드셋에서 제공 하지 않은 경우 헤드폰 가져오기

Samsung HMD Odyssey, HP 반향 또는 HP 반향 G2 헤드셋 (통합 된 AKG 헤드폰 및 통합 된 이중 배열 마이크)을 구입 하지 않은 경우 HMD의 헤드 set3.5 mm 오디오 잭에 연결할 수 있는 오디오 헤드셋 쌍의 헤드폰을 가져와야 합니다.

## <a name="make-sure-that-you-have-a-large-open-space"></a>열려 있는 공간이 충분 한지 확인 합니다.

Windows Mixed Reality를 사용 하는 동안 이동 하려면 공간이 크고 열려 있어야 합니다.  설치 하는 동안 "꽂혀 있는" 또는 "모든 환경" 중에서 선택 하 라는 메시지가 표시 됩니다. "모든 환경"을 선택 하 고 이동 하려는 경우 경계를 설정 합니다.

### <a name="seated-and-standing-no-boundary"></a>꽂혀 있고 순위 (경계 없음)

"하드 및 순위"를 선택 하는 경우 경계 없이 헤드셋을 사용 합니다. 즉, 헤드셋을 사용할 때 한 곳에 유지 하 여 물리적 장애물 및 왕복 위험을 피할 수 있습니다. 다음 단계로 이동 하거나 진행할 수는 있지만 이동 해서는 안 됩니다. 일부 앱은 경계를 사용 하도록 디자인 될 수 있으므로 경계 없이 사용 하는 경우에는 사용 하지 못할 수도 있고 동일한 환경을 사용 하지 못할 수도 있습니다.

### <a name="all-experiences-boundary"></a>모든 환경 (경계)

"모든 환경"을 선택 하는 경우 경계를 설정 하 고 경계를 필요로 하지 않는 앱과 환경을 사용 하 여 작업할 수 있습니다. 사용 중인 영역에 장애물, 위험 또는 취약 한 항목이 없도록 공간을 준비 해야 합니다 (머리 위에 포함). 계단의 위쪽 이나 더 낮은 천장 팬에서 설정 하지 마세요. 영역에서 트 및 장애물을 제거 하 고, 사용자와 헤드셋을 사용 하는 모든 사용자가 [안전 지침](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)을 읽고 이해 하는지 확인 합니다.

## <a name="see-also"></a>참고 항목

* [HMD에 연결](plug-in-your-headset.md)
* [최소 PC 하드웨어 요구 사항](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [권장 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)