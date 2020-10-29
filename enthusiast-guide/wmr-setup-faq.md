---
title: Windows Mixed Reality 설치 FAQ
description: Windows Mixed Reality를 사용할 때의 일반적인 설정 질문에 대 한 대답을 확인 하세요.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 사용자 의견, 피드백 허브, 버그
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685568"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality 설치 FAQ

Windows Mixed Reality 모던 헤드셋을 설정 하는 경우 발생할 수 있는 문제를 해결 하는 데 도움이 되는 몇 가지 정보는 다음과 같습니다.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>"Windows Mixed Reality 소프트웨어를 다운로드할 수 없습니다." 라는 메시지가 표시 되 면 "다운로드 하는 동안 잠시만 기다려 주세요." 페이지가 표시 됩니다.

다음을 시도해 보세요.
* **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 그런 다음 설치 대기 중인 모든 업데이트를 다운로드 하 여 설치 합니다.
* PC가 인터넷에 연결 되어 있고 사용 가능한 저장소 공간이 2GB 이상 인지 확인 합니다.
* PC를 다시 시작 하 고 다시 시도 하세요. 보류 중인 업데이트를 제거 하려면 여러 번 반복 하거나 Windows 업데이트 문제 해결사를 실행 해야 할 수 있습니다. 

> [!NOTE]
> * 엔터프라이즈 관리 네트워크를 사용 하는 경우 관리자에 게 문의 하세요. Windows Mixed Reality를 사용 하도록 설정 해야 할 수도 있습니다. IT 전문가 지침을 찾고 있나요? **[이 문서](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** 를 참조 하세요.
> * Wi-fi 네트워크 연결이 요금제로 설정 되어 있는 경우에는 데이터 통신이 아닌 것으로 변경 합니다. **[자세한 정보](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"문제가 발생 하 여 Windows Mixed Reality를 시작할 수 없습니다." 라는 메시지를 받게 됩니다.

다음을 시도해 보세요.
1. 컴퓨터에서 헤드셋을 분리 합니다 (두 케이블 모두).
2. 컴퓨터를 다시 시작합니다.
3. Go **설정 > Update & security > Windows 업데이트** 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 그런 다음 설치 대기 중인 모든 업데이트를 다운로드 하 여 설치 합니다.
4. 컴퓨터에 헤드셋을 다시 연결 하 고 설치를 다시 시도 합니다.

위의 단계가 작동 하지 않는 경우 Windows Mixed Reality를 제거한 다음 다시 설치 해 보세요. **설정 > 혼합 현실 > 제거** 로 이동 하 고 **제거** 를 선택 합니다. 그런 후 컴퓨터를 다시 시작합니다. 설치 프로세스를 다시 시작 하려면 헤드셋을 PC에 연결 하기만 하면 됩니다.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>내 PC가 Windows Mixed Reality를 실행할 수 없다는 메시지를 받습니다.

이 메시지가 나타나면 PC가 Windows Mixed Reality를 실행 하는 데 필요한 [최소 요구 사항을](https://support.microsoft.com/help/4039260) 충족 하지 않습니다. 이는 컴퓨터의 하드웨어 설정이 Windows Mixed Reality와 호환 되지 않거나 [최신 버전의 windows로 업데이트](https://support.microsoft.com/help/12373)해야 하기 때문일 수 있습니다.

그래픽 카드에 대 한 참고 사항:

* Windows Mixed Reality 설치에서 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되는 경우 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.
* 최신 드라이버 업데이트는 그래픽 카드 제조업체에 문의 하십시오. Windows Mixed Reality에는 최소한 WDDM 2.2을 지 원하는 그래픽 카드 드라이버가 필요 합니다.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다." 라는 메시지를 받게 됩니다.

이 메시지가 표시 되 면 PC가 Windows Mixed Reality의 최상의 환경에 필요한 최소 요구 사항을 충족 하지 않습니다. PC는 몰입 형 헤드셋을 실행할 수 있지만 특정 앱을 실행 하지 못하거나 성능에 문제가 있을 수 있습니다.

## <a name="my-xbox-controller-isnt-working"></a>내 Xbox 컨트롤러가 작동 하지 않습니다.

다음을 시도해 보세요.

* 컨트롤러가 켜져 있고, 완전히 충전 되었으며, PC에 연결 되어 있는지 확인 합니다.
* 컨트롤러의 배터리를 바꿉니다.
* Bluetooth 컨트롤러를 사용 하는 경우 **설정 > 장치 > bluetooth & PC의 기타 장치** 로 이동 하 여 쌍으로 연결 되었는지 확인 합니다 (페이지에 표시 됨).

[Xbox 컨트롤러에 대 한 자세한 정보](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>내 동작 컨트롤러가 작동 하지 않습니다.
 
다음을 시도해 보세요.

* 컨트롤러가 켜져 있고 완전히 청구 되었는지 확인 합니다.
* 컨트롤러의 배터리를 교체 합니다.
* 컨트롤러를 설정 하는 동안 다시 설정 하거나 다시 설정 합니다. Windows 단추 (4 초)를 길게 눌러 컨트롤러를 해제 한 다음 2 초 동안 다시 길게 눌러 설정 합니다. 
* **설정 > 장치 > Bluetooth & PC의 기타 장치로** 이동 하 여 쌍을 이루어야 하는지 확인 합니다 (페이지에 표시 되어야 함).

[동작 컨트롤러에 대 한 자세한 정보](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>헤드셋에 연결한 경우에도 "헤드셋 연결" 이라는 메시지가 표시 됩니다.

다음을 시도해 보세요.

* 헤드셋이 컴퓨터의 올바른 포트에 연결 되어 있는지 확인 합니다. PC의 개별 그래픽 카드 및 USB 3.0 포트에 연결 해야 합니다. 올바른 포트를 확인 하는 방법은 다음과 같습니다.
    * USB 3.0 포트에는 "SS" 표시가 있는 특수 로고 ("SuperSpeed"를 나타냄)가 있습니다. 포트의 내부 부분은 일반적으로 파란색 이지만 이전 USB 2.0 포트는 일반적으로 내부에서 검정이 나 흰색입니다.
    * 컴퓨터에 두 개의 HDMI 포트가 있는 경우 컴퓨터의 마더보드가 아닌 그래픽 카드에 연결 하는 포트를 사용 합니다. 불연속 포트는 컴퓨터의 확장 슬롯에 있는 경우가 많지만 항상 명확 하지는 않습니다. 하나의 포트를 시도 했지만 작동 하지 않는 경우 다른 포트를 사용해 보세요.
* 헤드셋 제조업체의 웹 사이트로 이동 하 여 헤드셋의 드라이버 및 펌웨어를 업데이트 합니다.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>경계를 만들려고 할 때 오류 메시지가 표시 됩니다.

경계를 만들기 위한 몇 가지 지침은 다음과 같습니다.

* 벽 이나 기타 장애물에 너무 가까운 것은 아닙니다.
* Waist height에서 헤드셋을 보유 하 고 경계를 추적 하는 동안 컴퓨터를 향하도록 합니다.
* 센서가 차단 되지 않고 충분 한 빛이 있는지 확인 합니다.
* 추적 하는 공간은 3 평방 미터 보다 커야 합니다.
* 공간이 너무 크거나 복잡 하지 않아야 합니다. 트위스트 및 회전이 많은 간단한 기 하 도형입니다.
* 추적 하는 동안 자체 경로를 교차 하지 않습니다.
* 모퉁이가 멈춘 경우 다시 시작 합니다.

**"고정 된 기능만"을 선택 하는 경우 어떤 유형의 환경이 있나요?**

"고정 및 순위만" 이란 경계 없이 헤드셋을 사용 한다는 것을 의미 합니다. 물리적 장애물을 방지 하는 데 도움이 되는 경계를 갖지 않으므로 한 곳에 유지 해야 합니다. 또한 일부 앱 및 게임은 경계와 함께 사용 되도록 설계 될 수 있으므로 의도 한 대로 작동 하지 않을 수 있습니다.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>헤드셋에서 더 명확 하 게 볼 수 있는 방법은 무엇입니까?

헤드셋의 맞춤을 조정해 보세요. 위쪽 및 아래쪽 이나 왼쪽 및 오른쪽으로 이동 하 여 얼굴의 위치를 조정 하 고 straps를 조정 하 여 snug.

헤드셋에서 지 원하는 경우에는 해당 보정 설정을 조정할 수도 있습니다. 헤드셋에 조절기가 있는 경우 보정을 사용 합니다. 그렇지 않으면 **설정 > 혼합 현실 > 시각적 품질** 로 이동 하 여 보정을 조정 합니다. 특정 장치의 보정에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality에서 지원 되는 언어는 무엇 인가요?

Windows Mixed Reality는 다음 언어로 제공 됩니다. PC가 다른 언어로 설정 된 경우에도 Windows Mixed Reality를 사용할 수 있지만 인터페이스가 영어 (미국)로 표시 되며 음성 명령과 받아쓰기를 사용할 수 없습니다.

* 중국어 간체(중국)
* 영어(오스트레일리아)
* 영어(캐나다)
* 영어(영국)
* 영어(미국)
* 프랑스어(캐나다)
* 프랑스어(프랑스)
* 독일어 (독일)
* 이탈리아어(이탈리아)
* 일본어(일본)
* 스페인어(멕시코)
* 스페인어(스페인)

위에 나열 된 지원 되는 Windows Mixed Reality 언어 중 하나에서 받아쓰기를 사용할 수도 있습니다. 화면 키보드에서 **마이크**  를 선택 하면 됩니다.

Windows Mixed Reality는 음성 명령 또는 받아쓰기 기능 없이도 다음 언어로 제공 됩니다.

* 중국어 번체 (대만 및 홍콩)
* 네덜란드어(네덜란드)
* 한국어(한국)
* 러시아어(러시아)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>내 헤드셋에 연결 하는 경우 아무 일도 발생 하지 않습니다. 혼합 현실 포털은 열리지 않습니다.

혼합 현실 포털, Windows Mixed Reality 설치를 통해 이동 하는 앱은 호환 되는 헤드셋을 연결할 때 자동으로 열리도록 설계 되었습니다. 열리지 않는 경우 **시작** 으로 이동 하 여 **검색** 상자에 **Mixed Reality Portal** 을 입력 하 여 해당 위치에서 앱을 엽니다. 혼합 현실 포털을 찾을 수 없는 경우 [최신 버전의 Windows로 업데이트](https://support.microsoft.com/help/12373) 해야 하거나 헤드셋이 PC에 올바르게 연결 되지 않은 것일 수 있습니다.

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>내 헤드셋의 소리를 듣지 못합니다. 또는 소리를 내 컴퓨터를 통해 재생할 수 없습니다.

모던 헤드셋에 내장 헤드폰이 포함 되지 않은 경우 헤드셋의 오디오 잭에 헤드폰을 연결 해야 합니다. (잭이 종종 헤드셋 센터 또는 lenses 바로 뒤에 위치 하 고 있는 경우 헤드셋 제조업체에 문의 하는 것이 좋습니다.) 

일부 오디오 헤드셋에는 볼륨을 제어 하기 위한 물리적 단추가 있습니다. 오디오가 작동 하지 않는 경우 볼륨이 작동 중지 되었는지 아니면 음소거 상태 인지 확인 합니다.

Windows Mixed Reality는 오디오를 제작 하 고 헤드폰이 연결 된 경우 몰입 형 헤드셋을 통해 소리를 재생 하도록 설계 되었습니다. 헤드셋을 끄거나 이동 하면 오디오가 기본 Windows 재생 장치로 전환 됩니다. **설정 > 혼합 현실 > 오디오 및 음성** 에서이 설정을 변경할 수 있습니다.

> [!NOTE]
> * Windows Mixed Reality 공간 오디오는에 기본 제공 되거나 몰입 형 헤드셋에 직접 연결 된 헤드폰에서 가장 잘 작동 합니다. PC에 연결 된 PC 스피커 또는 헤드폰이 공간 오디오에서 제대로 작동 하지 않을 수 있습니다.
> * Windows Mixed Reality는 Bluetooth 오디오 헤드셋을 지원 하지 않습니다.

## <a name="speech-commands-arent-working"></a>음성 명령이 작동 하지 않습니다.

음성 명령을 사용 하려면 PC의 음성 및 언어 설정이 Windows Mixed Reality에서 지원 되는 [언어](#what-languages-are-supported-in-windows-mixed-reality) 중 하나로 설정 되어야 합니다. 이를 확인 하려면 **설정 > 시간 & 언어 > 지역 & 언어** 및 **설정 > 시간 & 언어 > 음성** 으로 이동 합니다.

헤드셋에 기본 제공 마이크가 없는 경우 마이크를 사용 하 여 헤드셋 또는 PC에 헤드폰을 연결 해야 합니다. 사용자가 착용 할 때 헤드셋에 mic 입력을 자동으로 전환 하려면 **설정 > 혼합 현실 > 오디오 및 음성** 으로 이동 하 고, **헤드셋을 착용 할 때 헤드셋 mic** 가 켜져 있는지 확인 합니다.

일부 오디오 헤드셋은 마이크를 음소거 및 음소거 해제 하는 실제 단추를 포함 합니다. 음성 명령이 작동 하지 않는 경우 마이크가 음소거 되어 있는지 확인 합니다.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>종료 하 고 빠른 시작을 수행한 후 헤드 탑재 디스플레이가 작동 하지 않습니다.

다음과 같이 해보세요.

* 헤드 탑재 디스플레이에서 디스플레이 케이블 및 USB 케이블을 분리 한 후 다시 연결 합니다.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Windows Mixed Reality를 사용 하는 경우 Wi-fi의 속도가 느려집니다.

2.4 g h h h h h h h h h h h h h h h h h h h h h h-를 사용 하는 경우 동작 컨트롤러에서 Wi-fi 다음 작업 중 하나를 수행하세요.

* 5 GHz Wi-fi 연결로 전환 합니다 (사용할 수 있는 경우). 자세한 정보
* 별도의 Bluetooth 어댑터를 사용 하 여 이동 컨트롤러를 PC에 연결 합니다. [권장 어댑터 참조](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 최신 헤드셋은 기본 제공 된 Bluetooth 칩을 통해 컨트롤러와 직접 연결 되며이 문제가 발생 하지 않아야 합니다. 

## <a name="see-also"></a>참조
* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원 문의](https://support.microsoft.com/contactus/)
* [문제 해결](troubleshooting-windows-mixed-reality.md)

