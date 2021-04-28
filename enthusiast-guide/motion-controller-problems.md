---
title: 동작 컨트롤러 Faq
description: Controllers 표준 소비자 지원 설명서를 벗어나는 Windows Mixed Reality 문제 해결을 지원 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 동작 컨트롤러
appliesto:
- Windows 10
ms.openlocfilehash: cf45794d5c5c6c790578e76be4b222d851b5a73c
ms.sourcegitcommit: 229c33afab7c70341982f48962028aad13956356
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2021
ms.locfileid: "108069197"
---
# <a name="motion-controller-faqs"></a>동작 컨트롤러 Faq

## <a name="what-do-the-vibrations-and-lights-mean"></a>Vibrations 및 조명의 의미

LED constellation 링 및 haptics은 동작 컨트롤러의 상태를 표시 합니다.

| 주    | 상태와 연결 된 동작입니다. | 상태를 가져오는 방법 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **전원 켜기**               | Led는를 켜고 컨트롤러를 한 번 vibrates 합니다. | 컨트롤러를 켜려면 2 초 동안 컨트롤러에서 Windows 단추를 길게 누릅니다.  |
| **전원 끄기**              |  Led가 해제 되 고 컨트롤러가 두 번 vibrates. | 컨트롤러를 해제 하려면 컨트롤러의 Windows 단추를 4 초 동안 누르고 계십시오.   |
| **중지 중**               |  Led는 절전 상태에서 3 초 마다 해제 되 고 깜박거립니다. | 컨트롤러는 30 초 동안 중지 된 상태로 자동으로 전환 됩니다. 장치가 호스트 PC와 연결 되지 않은 경우를 제외 하 고는 동작이 감지 되 면 컨트롤러의 절전 모드가 해제 됩니다. 이 경우 단추를 눌러 절전 모드를 해제 합니다. |
| **Pin**                |  는 페어링 모드에서 서서히 펄스를 발생 하 고 연결 모드를 종료할 때 solid로 이동 합니다. 컨트롤러는 페어링이 성공한 경우 한 번 vibrates, 연결에 실패 한 경우 시간이 초과 되 면 한 번입니다. | 배터리 케이스 내에서 3 초간 페어링 단추를 길게 누릅니다.     |
| **PC에서 컨트롤러 연결/연결 끊기** |  컨트롤러는 PC 연결 또는 연결 끊김에서 한 번 vibrates. | 컨트롤러를 켠 후 PC에 성공적으로 연결 하거나 사용 중에 PC에서 연결을 끊는 경우에 발생 합니다.|
| **배터리 부족 수준**      | 배터리가 부족 하면 Haptics 사용 하지 않도록 설정 됩니다 (LED 표시가 없음). 헤드셋의 컨트롤러 핸들에 있는 배터리 표시기 아이콘은 배터리가 부족할 때 1/4을 모두 표시 합니다. | 배터리를 교체 합니다. | 
| **배터리 위험 수준** |  컨트롤러를 켜면 세 번 vibrates 자동으로 꺼집니다. 배터리 표시기 아이콘이 빨간색으로 바뀝니다. | 배터리를 교체 합니다. 문제가 지속 되 면 [장치를 출하 시 설정으로 복원 합니다](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) .|

## <a name="my-motion-controllers-arent-working-properly"></a>내 동작 컨트롤러가 제대로 작동 하지 않습니다.

[이동 컨트롤러가](controllers-in-wmr.md) 작동 하지 않거나, 연결 하거나, 헤드셋을 사용할 때 컨트롤러의 이미지가 표시 되는 경우:

1. 컨트롤러가 켜져 있는지 확인 합니다. 설정 하려면 Windows 단추를 2 초 동안 누르고 있습니다.
2. 컨트롤러가 완전히 청구 되는지 확인 하 고 배터리가 없으면 배터리를 교체 합니다.
3. 컨트롤러를 설정 하는 동안 다시 설정 하거나 다시 설정 합니다. Windows 단추를 길게 눌러 컨트롤러를 해제 합니다. 2 초 동안 다시 길게 눌러 설정 합니다.
4. 동작 컨트롤러의 [쌍](controllers-in-wmr.md#pair-motion-controllers)이 올바른지 확인 합니다.
5. 동작 컨트롤러 Led를 확인 합니다. 밝은 lit controller는 페어링 되 고 연결 되어 있으며, dimly lit controller는 연결 되지 않습니다.
6. PC에서 **> Mixed Reality 포털 시작** 으로 이동 하 여 "메뉴"를 선택 합니다. 상태 메시지와 함께 표시 되는 동작 컨트롤러가 표시 되어야 합니다.
    * 준비 됨 – 컨트롤러가 모두 설정 됩니다.
    * 손실 추적 – 혼합 현실 포털에서 컨트롤러를 찾을 수 없습니다. 헤드셋 앞에 있는 상태에서 Windows 단추를 4 초간 누르고 2 초 동안 다시 시작 하 여 다시 시작 합니다.
    * 배터리 부족 – 컨트롤러 배터리를 교체 합니다.
7. 외부 USB Bluetooth 어댑터를 사용 하는 경우 USB 2.0 포트에 연결 되어 있는지 확인 합니다 (항상 검정색은 아니지만). 또한 헤드셋의 USB 커넥터를 비롯 하 여 다른 무선 송신기 또는 USB 플래시 드라이브에서 가능한 한 빨리 연결 해야 합니다. 
8. **장치 관리자 > bluetooth** 로 이동 하 고 하나의 어댑터를 찾아 PC에 bluetooth 라디오가 하나만 있는지 확인 합니다. 기본 제공 라디오에서 데스크톱 PC 구성을 사용 하는 경우 외부 안테나가 연결 되어 있는지 확인 합니다. 외부 안테나가 연결 되어 있지 않으면 추적 문제가 발생할 수 있습니다. 또는 외부 Bluetooth 동글을 사용 하 고, 내부 Bluetooth 기능을 사용 하지 않도록 설정 하 고, 페어링 및 연결을 다시 시도 합니다.
9. Bluetooth 설정 창이 백그라운드로 열려 있으면 Bluetooth 프로토콜에 대 한 많은 추가 호출이 수행 됩니다. 설치 미디어를 닫습니다.
10. 혼합 현실에서 컨트롤러를 켜서 배터리 아이콘을 확인 하 여 동작 컨트롤러의 가상 배터리 수준을 확인 합니다. 보고 된 수준이 컨트롤러를 연결한 직후의 실제 수준 보다 높기 때문에 수준을 읽기 전에 15 초 정도 기다립니다. 아이콘이 빨간색 이면 배터리를 교체 합니다.
11. Bluetooth 헤드폰 및 스피커를 **설정 > 장치 > bluetooth & 기타 장치** 를 제거 하 고 장치를 끕니다. 최상의 오디오 환경을 위해 혼합 현실 헤드셋의 헤드폰 잭 또는 기본 제공 스피커를 사용 합니다.
12. 헤드폰 또는 gamepads와 같이 PC와 페어링된 것일 수 있는 다른 Bluetooth 장치를 제거 합니다. **설정 > 장치 > Bluetooth & 기타 장치** 로 이동 하 고 장치를 선택한 다음 "장치 제거"를 선택 합니다.
13. 헤드셋에서 USB 케이블을 분리 하 고 PC에 다시 연결 하 여 Windows Mixed Reality를 다시 시작 합니다.
14. 컨트롤러는 펌웨어 업데이트를 진행 하는 동안 깜박입니다. 업데이트가 완료 될 때까지 기다리거나, 컨트롤러가 혼합 현실에 표시 되어야 합니다.
15. PC가 5ghz Wi-Fi 네트워크에 연결 되어 있는지 확인 합니다. 랩톱이 2.4 GHz Wi-Fi 네트워크에 연결 된 경우 일반적으로 Bluetooth 연결을 공유 합니다. 이는 제품 설계에 따라 Wi-Fi 또는 Bluetooth 성능에 부정적인 영향을 미칠 수 있습니다. 네트워크 어댑터 설정에서 기본 설정 밴드를 5ghz로 변경 합니다. 네트워크가 5ghz를 지원 하지 않는 경우 내부 Bluetooth 기능 대신 Bluetooth 동글을 사용할 수 있습니다.
16. Bluetooth 설정에 이미 페어링 된 동작 컨트롤러가 있는 경우 Windows는 제거 될 때까지 새 장치를 검색 하지 않습니다. 특정 동글을 사용 하 여 추가 된 경우 해당 동글을 제거할 수 있습니다.
17. PC가 기본 제공 블루투스를 사용 하는 경우 연결 문제가 있는 경우 USB Bluetooth 어댑터를 사용해 보세요. 이렇게 하려면 장치 관리자에서 기본 제공 Bluetooth 라디오를 끄고 다른 Bluetooth 장치를 새 어댑터와 페어링 합니다.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>혼합 현실에서 내 컨트롤러 지터, 정지 또는 깜박임

* PC가 2.4 GHz wifi에서 실행 되는 경우 5 GHz wifi로 전환 합니다. 
* 외부 Bluetooth 어댑터를 사용 하는 경우 다른 무선 송신기 또는 USB 플래시 드라이브에서 벗어나 USB 2.0 포트 (항상 그렇지는 않지만 항상 그렇지는 않음)에 연결 되어 있는지 확인 합니다.
* 설정 > bluetooth 문제 해결사를 실행 하 여 **bluetooth > 문제 해결 & 보안 > 업데이트** 합니다.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>내 컨트롤러가 무한 다시 부팅에 걸려 있습니다.

이는 중요 한 배터리 표시기입니다. 장치에 새 배터리를 넣고, 문제가 계속 되 면 컨트롤러를 [공장 설정으로 다시 설정](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)합니다.

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>혼합 현실 포털이 작동 중이지만 컨트롤러에서 잘못 된 (비행, 핸드쉐이킹 등)를 추적 하 고 있습니다.

1. 조명 조건은 추적에 영향을 줄 수 있습니다. 직접 햇빛에 노출 되지 않고 HMD (예: 크리스마스 트리와 같은 광원의 문자열)에 최소 점 광원을 표시 하는지 확인 합니다.
2. 이러한 증상은 컨트롤러와 호스트 PC 간의 통신 오류로 인해 발생 하며 Bluetooth 링크 품질 저하를 표시 합니다. [Bluetooth에 대 한 질문](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)을 참조 하세요.

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>동작 컨트롤러 Led가 켜지 지 않지만 혼합 현실 포털에서 단추와 엄지 스틱을 계속 사용할 수 있습니다.

동작 컨트롤러 보정 캐시가 손상 되었을 수 있습니다. 캐시를 삭제 하려면 관리자 명령 프롬프트에서 다음 명령을 실행 합니다.

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

이 폴더는 Windows 탐색기에서 액세스할 수 없으며 관리자 명령 프롬프트 에서만 수정할 수 있습니다. 폴더를 삭제 한 후 PC를 다시 시작 하 고 동작 컨트롤러를 다시 연결 하 여 보정 파일을 복원 합니다.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>내 컨트롤러가 다음과 같이 표시 되거나 이상한 방향이 있거나 단추가 잘못 매핑 되었습니다.

웹 사이트에 전체 동작 컨트롤러 지원이 없을 가능성이 높습니다.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>내 동작 컨트롤러가 SteamVR 앱 및 게임에 표시 되지 않습니다.

먼저 컨트롤러의 배터리가 청구 되는지 확인 합니다. 배터리가 비활성 이거나 죽을 경우 컨트롤러가 작동 하지 않습니다.

절벽에서 컨트롤러를 볼 수 있지만 SteamVR apps 및 게임이 아닌 경우에는 동작 컨트롤러 모델 드라이버가 제대로 설치 되지 않을 수 있습니다. 동작 컨트롤러 모델 드라이버가 올바르게 설치 되었는지 확인 하려면 다음을 수행 합니다.

1. 두 동작 컨트롤러를 모두 켭니다. 동작 컨트롤러의 [쌍](controllers-in-wmr.md#pair-motion-controllers)이 올바른지 확인 합니다.
2. **장치 관리자 > 휴먼 인터페이스 장치로** 이동 하 여 "동작 컨트롤러"를 찾습니다.
3. 각 "동작 컨트롤러" 장치를 두 번 클릭 하 고 "드라이버" 탭으로 이동 합니다. 나열 된 드라이버 버전이 [이러한 버전](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)중 하나에 해당 하는지 확인 합니다.
4. 드라이버 버전이 일치 하지 않거나 "동작 컨트롤러" 라는 장치를 찾을 수 없는 경우 Windows 업데이트를 실행 합니다.  그러면 드라이버가 자동으로 다운로드 되어 설치 됩니다. 엔터프라이즈 정책이 있는 PC를 만들거나 Windows 업데이트 달리 제한 된 경우에는 동작 컨트롤러 모델 드라이버를 수동으로 설치 해야 할 수 있습니다. 이렇게 하려면 [이 페이지](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) 를 방문 하 여 컨트롤러 하드웨어에 해당 하는 드라이버 버전을 확인 합니다. 설치 지침은 다운로드 페이지에서 확인할 수 있습니다.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>컨트롤러 펌웨어 업데이트는 2 분 이상 소요 됩니다.

[Bluetooth 질문 섹션](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)을 확인 하세요. Bluetooth 링크 품질이 저하 되 면 일반적으로 이러한 문제가 발생 합니다.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>새 배터리를 삽입 했지만 컨트롤러 가상 배터리 수준이 전체 수준을 표시 하지 않음

AA 배터리에 대해 모션 컨트롤러 배터리 수준이 조정 됩니다. 일부 저전압 rechargeable 배터리는 완전히 청구 되더라도 가득 찬 것으로 보고 되지 않을 수 있습니다.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>내 Samsung 모션 컨트롤러의 터치 패드가 중심 이거나 비활성 지점을 포함 합니다.

이는 하드웨어 결함 일 수 있으므로 교체 또는 교환에 대 한 소매점 또는 장비 제조업체로 다시 이동 해야 합니다.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>컨트롤러를 공장 설정으로 복원 하려면 어떻게 해야 하나요?

공장 조건으로 복원 합니다 (새 배터리가 필요 함).

1. 컨트롤러를 분리 하 고 전원 해제 합니다.
2. 배터리 덮개를 엽니다.
3. 새 배터리를 삽입 합니다.
4. 페어링 단추 (배터리 아래쪽의 탭)를 길게 누릅니다.
5. 페어링 단추를 누른 상태에서 Windows 단추를 5 초 동안 누르고 있으면 컨트롤러의 전원을 켭니다 (두 단추를 모두 누른 상태 유지).
6. 단추를 해제 하 고 컨트롤러의 전원이 켜 지는 때까지 기다립니다. 이 작업에는 최대 15 초가 걸리며, 장치 복구가 발생 하는 경우에는 지표가 표시 되지 않습니다. 장치가 단추 릴리스부터 즉시 켜지 면 복구 단추 시퀀스가 등록 되지 않아 다시 시도해 야 합니다.
7. 컨트롤러가 PC와 쌍으로 연결 된 경우 **설정 > bluetooth > 기타 장치** 로 이동 하 고 "동작 컨트롤러"를 선택 하 고 "장치 제거"를 선택 하 여 bluetooth 설정에서 컨트롤러 연결을 제거 합니다.
8. [컨트롤러를](controllers-in-wmr.md#pair-motion-controllers) 헤드셋 또는 PC와 다시 페어링 합니다.
9. 호스트 및 헤드셋과 연결한 후 장치는 사용 가능한 최신 펌웨어로 업데이트 됩니다.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Xbox 컨트롤러를 내 PC에 연결 하 여 헤드셋에서 사용할 수 있습니다.

다음 [지침](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)에 따라 Bluetooth Xbox 컨트롤러를 연결 하 여 헤드셋과 함께 사용할 수 있습니다.

유선 Xbox 컨트롤러가 있는 경우 PC에 연결 합니다.

일부 게임과 앱은 혼합 현실에서 사용 되는 것과 다른 방식으로 Xbox 컨트롤러를 사용 합니다. 게임 또는 앱에 컨트롤러를 사용 하려면 앱 바에서 "게임 프로그램으로 사용"을 선택 하거나 "게임 프로그램으로 사용" 이라고 표시 합니다. 컨트롤러를 혼합 된 현실을 다시 전환 하려면 "게임 패드로 사용"을 다시 선택 하거나 "응시와 함께 사용"을 선택 합니다. 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Windows Mixed Reality가 PC에 이미 설치 되어 있는 경우 새 컨트롤러를 어떻게 할까요? 페어링

컨트롤러를 헤드셋에 연결 하는 경우에는 부록 앱을 사용 합니다. [혼합 현실 포털](install-windows-mixed-reality.md#launch-mixed-reality-portal) 을 사용 하면 시작 하는 도우미 앱을 찾거나 선택할 수 있는 도우미 앱 목록을 제공할 수 있습니다.

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>컨트롤러를 공장 페어링으로 반환 하려면 어떻게 해야 하나요?

동작 컨트롤러를 공장 페어링으로 반환 하거나 기본 제공 블루투스 라디오를 사용 하 여 Windows Mixed Reality 헤드셋과 페어링 하려면 헤드셋의 장치 도우미 앱을 실행 하 고 동작 컨트롤러 페어링에 대 한 지침을 따르세요. 예를 들어 "Acer OJO 500" 앱 또는 "Samsung HMD Odyssey + Setup" 앱은 헤드셋이 처음 연결 될 때 자동으로 설치 됩니다.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>내 동작 컨트롤러가 내 PC와 페어링 되지 않습니다.

* 컨트롤러가 켜지 지 않으면 새 배터리를 삽입 합니다. 이 문제가 해결 되지 않으면 페어링 단추를 누른 상태에서 장치 전원을 켜는 방식으로 장치를 출하 시 설정으로 복원 합니다. 자세한 내용은 [장치 복구 단계](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)를 참조 하세요.
* 외부 Bluetooth 어댑터를 사용 하는 동안 컨트롤러가 켜지 면 다른 무선 송신기 또는 USB 플래시 드라이브에서 어댑터가 USB 2.0 포트 (항상 그렇지는 않지만 항상 그렇지는 않음)에 연결 되어 있는지 확인 합니다. 그래도 작동 하지 않는 경우 설정에서 Bluetooth 문제 해결사를 실행 하 여 Bluetooth > 문제 해결 & 보안 > > 업데이트 합니다.
* Qualcomm 어댑터를 사용 중이 고 PC가 충돌 하는 경우 PC를 다시 시작 합니다.
* 페어링 하지 않는 동작 컨트롤러를 한 번에 하나씩 다시 시작 하 고 PC를 다시 시작 하세요.
* 동작 컨트롤러 캐시가 손상 되었을 수 있습니다. 이 문제를 해결 하려면 다음 [단계](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)를 참조 하세요.
* 단계에서 문제를 해결 하는 경우 제조업체에 문의 해야 합니다.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>쌍을 이루는 컨트롤러가 혼합 현실 포털에 표시 되지 않습니다.

* 헤드셋 앞에 있는 컨트롤러를 보유 하 고 Windows 단추를 4 초간 누르고 2 초 동안 다시 시작 하 여 다시 시작 합니다.
* 컨트롤러가 연결 된 것으로 표시 되는 경우 연결 해제 하 고 [페어링 프로세스](controllers-in-wmr.md#pair-motion-controllers) 를 다시 진행 합니다.
* 컨트롤러 Led가 한 번에 하나의 조명으로 켜고 끌 수 있는 경우 펌웨어 업데이트를 진행 하는 것입니다. 업데이트가 완료 될 때까지 기다리거나, 컨트롤러가 혼합 현실에 표시 되어야 합니다.
* 외부 Bluetooth 어댑터를 사용 하는 경우 어댑터가 USB 2.0 포트 (검은색)에 연결 되어 있는지 확인 하 고 다른 무선 송신기 또는 USB 3.0 장치에서 제거 합니다.
* PC가 충돌 하 고 Qualcomm 어댑터를 사용 하는 경우 다시 설정이 작동 하지 않을 수 있습니다. 이 문제를 해결 하려면 컴퓨터의 뒷면에서 전원을 분리 하거나 (노트북의 경우 10 초 동안 전원 단추를 누른 채) PC를 다시 시작 합니다.
* 설정 > bluetooth 문제 해결사를 실행 하 여 **bluetooth > 문제 해결 & 보안 > 업데이트** 합니다.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>내 컨트롤러를 페어링 하려고 하지만 Bluetooth 설정의 "새 장치 메뉴 추가"에 표시 되지 않습니다.

컨트롤러가 이미 연결 되어 있는지 확인 하세요. 이렇게 하려면 제거 하 고 다시 시도 하세요. 문제가 지속 되 면 PC를 다시 시작 합니다. 실패 하면 [Bluetooth에 대 한 자세한 정보](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)를 참조 하세요.

참고: 다른 동작 컨트롤러 집합이 PC와 페어링된 경우 새 컨트롤러를 연결 하기 전에 해당 컨트롤러를 연결 해제 해야 합니다. 현재 PC를 사용 하 여 일련의 동작 컨트롤러를 연결 하 고 두 번째 PC와 쌍으로 연결 하는 경우 다시 사용 하기 전에 연결 해제 하 고 현재 PC와 쌍을 다시 연결 해야 합니다.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Bluetooth 기술을 사용 하 고 있는지 어떻게 알 수 있나요?

동작 컨트롤러는 많은 소비자 장치에서 발견 된 것과 동일한 Bluetooth 기술을 사용 하며, 최근 PC에 포함 된 Bluetooth 기능을 사용할 수 있도록 설계 되었습니다. 혼합 현실 호환성 검사를 통과 하면 PC에 Bluetooth 라디오가 있어야 합니다. 확인하려면 다음을 수행합니다.

* "장치 관리자"를 엽니다.
* Bluetooth 섹션을 확장 하 고 어댑터를 찾습니다.

![장치 관리자 예의 스크린샷 어댑터는 Bluetooth 송수신 장치입니다.](images/devicemanagerbtadapterpic.png)

PC에 Bluetooth가 없는 경우 플러그형 USB Bluetooth 4.0 저 에너지 마이크로 어댑터를 사용 합니다.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>이동 컨트롤러를 켜면 내 노트북에서 Wi-Fi 느려집니다.

노트북은 2.4 GHz 액세스 지점에 연결 된 경우 Bluetooth와 Wi-Fi 안테나를 공유할 수 있습니다. 대역 기본 설정을 5ghz로 전환할 수 있는 경우 장치 관리자 체크인 합니다. 5 GHz 네트워크를 사용할 수 없고 성능이 심각한 영향을 받는 경우 Bluetooth 동글을 사용 하는 것이 좋습니다.

![장치 관리자를 통해 Wifi 대역 선택 설정을 찾을 수 있습니다.](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>내 PC에 Bluetooth 기술이 있지만 내 컨트롤러에 문제가 있습니다.

동작 컨트롤러는 다른 Bluetooth 키보드, 마우스 및 게임 컨트롤러에서 작동 해야 합니다. 경험은 사용 하는 키보드, 마우스 또는 게임 컨트롤러의 모델에 따라 달라 집니다. 성능을 향상 시키기 위해 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

* 컴퓨터에 Bluetooth가 있지만 계속 해 서 동작 컨트롤러에 문제가 있는 경우에는 USB로 연결 된 플러그형 외부 Bluetooth 어댑터를 사용 하 여 Bluetooth 라디오를 교체 하는 것이 좋습니다. Bluetooth 라디오 어댑터는 한 번에 하나만 활성 상태로 만들 수 있습니다. 기존 라디오와 함께 외부 라디오를 연결 하는 경우 장치 관리자에서 기존 Bluetooth 라디오를 사용 하지 않도록 설정 해야 합니다. 어댑터를 마우스 오른쪽 단추로 클릭 하 고 "장치 사용 안 함"을 선택 하 고 이전 Bluetooth 장치를 모두 연결 해제/다시 페어링 합니다.
* USB Bluetooth 어댑터를 사용 하는 경우 USB 2.0 포트에 연결 합니다 (2.0 포트는 일반적으로 검정색 이며 "SS"로 레이블이 지정 되지 않음) (사용 가능한 경우). 포트는 다음과 같이 물리적으로 분리 되어야 합니다.
    - HMD USB 커넥터
    - 플래시 드라이브
    - 하드 드라이브
    - 키보드/마우스에 대 한 것과 같은 무선 USB 수신기는 USB Bluetooth 어댑터를 이러한 다른 커넥터에서 가능 하면 컴퓨터의 반대쪽에 연결 합니다.
* Bluetooth 설정 창이 열려 있으면 닫습니다. 백그라운드에서 열린 상태로 두면 Bluetooth 프로토콜에 대 한 많은 추가 호출이 수행 됩니다.
* 헤드셋이 PC와 쌍으로 연결 된 경우 Windows Bluetooth 드라이버 스택을 사용 하 고 타사 Bluetooth 드라이버 스택을 설치 하지 마세요. 타사 소프트웨어가 제대로 작동 하지 않을 수 있습니다.
* "Bluetooth & 기타 장치"에서 "Swift Pair를 사용 하 여 연결 하는 알림 표시" 설정을 사용 하지 않도록 설정 하 여 호스트 라디오 검색 작업을 줄입니다.
* 내부 Bluetooth 카드를 사용 하는 경우 외부 Bluetooth 안테나를 사용 하 고 있는지 확인 하 고, 문제를 추적 하는 것일 수 있습니다. 작동 하지 않는 경우 내부 Bluetooth를 사용 하지 않도록 설정한 후 외부 Bluetooth 동글을 사용 합니다.
* 장치가 Bluetooth 설정의 "마우스, 키보드 & 펜" 범주 아래에 나타납니다. "기타 장치" 아래에 있는 경우 연결 해제 하 고 장치를 페어링 합니다.
* Bluetooth 헤드폰 및 스피커를 제거 하 고, 연결 해제, 전원을 끕니다. Windows Mixed Reality에서는 지원 되지 않습니다. 최상의 오디오 환경을 위해 혼합 현실 헤드셋의 헤드폰 잭 또는 기본 제공 스피커를 사용 합니다.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>두 번째 컨트롤러를 다시 연결 하는 데 시간이 오래 걸립니다.

일부 이전 Intel 라디오에서는 동작 컨트롤러가 동시에 켜져 있는 경우이 문제가 발생 합니다. 컨트롤러의 전원을 동시에 사용 하지 마십시오.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>PC 작동이 중단 된 후에는 Qualcomm Bluetooth 라디오가 컨트롤러를 쌍으로 연결할 수 없습니다.

10.0.0.448 이전 Qualcomm (QCA) Bluetooth 라디오 드라이버는 Windows 크래시 후에 잘못 된 상태가 될 수 있습니다. 이 문제를 해결 하려면 PC 전원을 완전히 끕니다.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Marvell 라디오를 사용 하 여 잘못 된 컨트롤러 추적이 발생 함

**장치 관리자 > bluetooth > MARVELL AVASTAR Bluetooth 라디오 어댑터 > 속성 > 드라이버로** 이동 하 여 driver 15.68.9210.47 이상을 사용 중인지 확인 합니다.
