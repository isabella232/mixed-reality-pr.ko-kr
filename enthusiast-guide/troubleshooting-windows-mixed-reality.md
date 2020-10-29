---
title: Windows Mixed Reality 문제 해결
description: 표준 소비자 지원 설명서를 벗어나는 고급 Windows 혼합 현실 문제 해결.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685712"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Windows Mixed Reality 문제 해결 (Faq)

## <a name="understanding-common-installation-error-messages"></a>일반적인 설치 오류 메시지 이해

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"PC가 Windows Mixed Reality를 실행할 수 없습니다."

PC가 Windows Mixed Reality를 실행 하는 데 필요한 [최소 요구 사항을](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 충족 하지 않습니다. 이는 컴퓨터의 하드웨어 설정이 Windows Mixed Reality와 호환 되지 않거나 [최신 버전의 windows로 업데이트](https://support.microsoft.com/en-us/help/12373/windows-update-faq)해야 하기 때문일 수 있습니다. 

Windows Mixed Reality에는 최소한 WDDM 2.2을 지 원하는 그래픽 카드 드라이버가 필요 하므로 제조업체의 최신 드라이버 업데이트가 설치 되어 있는지 확인 하세요. Windows Mixed Reality 설치에서 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되는 경우 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다."

PC가 Windows Mixed Reality의 최상의 환경에 필요한 [최소 요구 사항을](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 충족 하지 않습니다. PC는 몰입 형 헤드셋을 실행할 수 있지만 특정 응용 프로그램을 실행 하지 못하거나 성능에 문제가 있을 수 있습니다.

Windows Mixed Reality에는 최소한 WDDM 2.2을 지 원하는 그래픽 카드 드라이버가 필요 하므로 제조업체의 최신 드라이버 업데이트가 설치 되어 있는지 확인 하세요. Windows Mixed Reality 설치에서 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되는 경우 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Windows Mixed Reality를 설정 하기 전에 관리자가 조직에 대해 사용 하도록 설정 해야 합니다. 자세히 알아보기 "

조직에서 관리 되는 네트워크를 사용 하 고 있거나 조직에서 Windows Server Update Services (WSUS)를 사용 하거나 다운로드를 차단할 수 있는 다른 정책을 사용 하 고 있는 것 같습니다. [Windows Mixed Reality를 사용](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)하려면 조직의 IT 부서 또는 시스템 관리자에 게 문의 하세요.

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"혼합 현실 소프트웨어를 다운로드할 수 없습니다." 또는 "다운로드 하는 동안 잠시 기다려 주세요."

* 경우에 따라 보류 중인 업데이트가 혼합 현실 소프트웨어 다운로드를 차단할 수 있습니다. **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 그런 다음 설치 대기 중인 모든 업데이트를 다운로드 하 여 설치 합니다. 이러한 단계를 시도할 때 Windows 업데이트 오류가 발생 하면 [여기](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)로 이동 하세요.
* PC가 인터넷에 연결 되어 있고 사용 가능한 저장소 공간이 2GB 이상 인지 확인 합니다. 네트워크 상태 확인: **설정 > 네트워크 & 인터넷 > 상태** 를 확인 합니다. 인터넷에 연결할 수 없는 경우 [여기](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) 로 이동 하 여 도움을 확인할 수 있습니다.  
* PC를 다시 시작 하 고 다시 시도 하세요. 

이전 솔루션이 작동 하지 않는 경우 다음을 시도 합니다.
* Wi-fi 네트워크 연결이 요금제로 설정 되어 있는 경우에는 [데이터](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq)통신이 아닌 것으로 변경 합니다. 데이터 통신 연결을 해제 하려면 **설정 > 네트워크 & 인터넷 > 상태 > 연결 속성 변경 > 요금제 연결로 설정** 하 고 "해제"를 선택 합니다.  
* 업데이트를 최근에 설치한 경우 문제가 발생할 수 있습니다. 설치 된 업데이트, 특히 PC를 안전 하 게 유지 하는 보안 업데이트를 제거 하지 않는 것이 좋지만, 최신 업데이트를 제거 하는 것이 문제의 원인을 확인 하는 데 도움이 될 수 있습니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면 
    * **설정 > 업데이트 & 보안 > 설치 된 업데이트 기록 보기 > 업데이트 제거** 로 이동 합니다.
    * 설치 된 마지막 업데이트와 "제거"를 선택 합니다.
    * "이 업데이트를 제거 하 시겠습니까?" 라는 메시지가 표시 되 면 "예"를 대답 합니다. 이러한 단계를 시도 하는 동안 오류가 발생 하면 [여기](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)로 이동 하세요. 
    * PC를 다시 시작 하 고 다시 시도 하세요. 
    * Windows Mixed Reality가 올바르게 설치 되 면 **설정 > Windows 업데이트** 에서 최신 업데이트를 다시 설치 > 업데이트를 확인 하 고 Windows mixed reality가 계속 작동 하는지 확인 합니다. 제대로 설치 되지 않으면 최신 업데이트를 다시 설치 하 고 Windows 지원에 문의 하십시오. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"문제가 발생 하 여 Windows Mixed Reality를 시작할 수 없습니다."
* PC에서 헤드셋의 두 케이블을 분리 합니다.
* PC를 다시 시작 합니다.
* **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 그런 다음 대기 중인 업데이트를 다운로드 하 여 설치 합니다.
* 헤드셋을 PC에 다시 연결한 다음 설치를 다시 시도 합니다.

위의 단계가 작동 하지 않는 경우 Windows Mixed Reality를 제거한 다음 다시 설치 해 보세요.
* **설정 > 혼합 현실 > 제거** 로 이동 하 고 "제거"를 선택 합니다. 
* PC를 다시 시작 합니다. 
* 설치 프로세스를 다시 시작 하려면 헤드셋을 PC에 연결 하기만 하면 됩니다.
    

## <a name="troubleshooting-setup-questions"></a>설정 질문 문제 해결 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Xbox 컨트롤러가 Windows Mixed Reality에서 작동 하지 않습니다.

* 컨트롤러가 켜져 있고, 완전히 충전 되었으며, PC에 연결 되어 있는지 확인 합니다.
* 컨트롤러의 배터리를 바꿉니다.
* Bluetooth 컨트롤러를 사용 하는 경우 **설정 > 장치 > bluetooth & PC의 기타 장치** 로 이동 하 여 페어링 되었는지 확인 합니다 (페이지에 표시 되어야 함).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>입력 (컨트롤러, 게임 패드, 마우스/키보드)을 Windows Mixed Reality에 직접 연결할 수 없습니다.

헤드셋에 배치 하는 경우 헤드셋의 현재 상태 센서를 통해 혼합 현실 환경으로 입력이 자동으로 전환 됩니다. 바탕 화면에 파란색 막대가 표시 됩니다.

![입력이 헤드셋으로 전달 되는 Windows 데스크톱](images/1050px-windowsy.png)

입력이 자동으로 전환 되지 않는 경우에는 수동으로 입력을 헤드셋으로 전환 해야 합니다. 키보드에서 **Windows 키 + Y** 를 입력 하 여이 작업을 수행할 수 있습니다 (그리고 동일한 경우 입력을 바탕 화면으로 다시 전환).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>내 헤드셋을 꽂을 때 아무 일도 발생 하지 않습니다. 혼합 현실 포털이 열리지 않습니다.
혼합 현실 포털, Windows Mixed Reality 설치를 통해 이동 하는 앱은 호환 되는 헤드셋을 연결할 때 자동으로 열리도록 설계 되었습니다. 열리지 않는 경우 시작으로 이동 하 여 검색 상자에 "Mixed Reality Portal"을 입력 하 여 앱을 엽니다. 혼합 현실 포털을 찾을 수 없는 경우 [최신 버전의 Windows로 업데이트](https://support.microsoft.com/en-us/help/12373/windows-update-faq)해야 하는 것일 수 있습니다.

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>"꽂혀 있는" 및 "모든 환경" 중에서 선택 어떻게 할까요??

헤드셋을 설치 하는 동안 또는 나중에 "꽂혀 있는"를 선택 하는 경우 경계 없이 헤드셋을 사용 합니다. 이에 대 한 추가 작업을 수행할 수 있지만, 그렇지 않은 경우에는 물리적 장애물을 방지 하는 데 도움이 되는 경계가 없기 때문에이 작업을 한 곳에 유지 해야 합니다. 일부 앱은 경계를 사용 하도록 디자인 될 수 있으므로 사용 하지 못할 수도 있고, 경계 없이 사용 하는 경우 동일한 환경을 사용 하지 못할 수도 있습니다. "경계는 무엇 이며 왜 만들어야 하나요?"를 참조 하세요. 자세한 내용은 아래를 참조 하세요.

"모든 환경"을 선택 하는 경우 경계를 설정 하 고 경계를 필요로 하지 않는 앱과 환경을 사용할 수 있습니다. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>혼합 현실에 대 한 자세한 내용은 처음 시작할 때 실행 되지 않았으며 Windows Mixed Reality 홈으로 바로 이동 했습니다.

[다시 실행 단계](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)를 수행 하 여 학습 환경을 다시 실행할 수 있습니다. 


## <a name="boundary-setup-and-other-questions"></a>경계 설정 및 기타 질문

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>경계는 무엇 이며이를 만들어야 하는 이유는 무엇 인가요?

경계는 Windows Mixed Reality 모던 헤드셋을 입고 있는 동안 이동할 수 있는 영역을 정의 합니다. 헤드셋을 사용 하는 동안에는 주변을 볼 수 없으므로 장애물을 방지 하는 데 도움이 되는 경계를 만드는 것이 중요 합니다. 경계는 혼합 현실 안에서 흰색 윤곽선 처럼 보이고 가까이 있을 때 나타납니다. 표시 되 면 이동 속도가 느려지고, 경계를 벗어나 limbs 확장 하지 않도록 합니다.

경계 내의 영역은 가구, 낮은 조명 설비, 천장 팬 등을 사용 하지 않아야 하므로 아무것도 이동 하거나 이동 하지 않습니다. [Windows Mixed Reality의 상태 및 보안에 대해 알아봅니다](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>경계를 만들 어떻게 할까요? 있나요?

헤드셋을 처음 설정 하는 경우 설치 앱 (혼합 현실 포털)에서 경계를 만드는 단계를 안내 합니다. 하지만 언제 든 지 만들 수 있습니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면
1. 바탕 화면에서 **> 혼합 현실 포털 시작** 을 선택 합니다. 
2. "메뉴"를 엽니다.
3. "설치 실행"을 선택 하 여 새 경계를 만듭니다.

다른 사용자가 헤드셋을 사용 하는 경우 경계와 사용 방법을 이해 해야 합니다. 헤드셋을 새 위치로 이동 하는 경우 해당 공간에 대해 작동 하는 새 경계를 설정 해야 합니다.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>경계를 만들려고 할 때 오류 메시지가 표시 됩니다.

* 경계를 만들 때 벽 또는 기타 장애물에 너무 가까이 두지 마십시오.
* Waist 높이로 헤드셋을 보유 하 고 경계를 추적 하는 동안 컴퓨터를 계속 사용 해야 합니다.
* 센서가 차단 되지 않고 충분 한 빛이 있는지 확인 합니다.
* 추적 하는 공간은 3 평방 미터 보다 커야 합니다.
* 공간이 너무 크거나 복잡 하지 않아야 합니다. 트위스트 및 회전이 없는 간단한 기 하 도형에 스틱을 사용 합니다.
* 추적 하는 동안 자체 경로를 교차 하지 않습니다.
* 모퉁이가 멈춘 경우 다시 시작 합니다.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>혼합 현실를 시작 하는 동안에는 "헤드를 쪽으로, 그 다음 층으로 전환" 하는 단계에서 중단 됩니다.

이 단계를 통해 헤드셋은 공간을 인식 하 고 기존 가상 바닥 및 경계를 복원 합니다. 헤드셋에 배치 하는 경우이 검색 프로세스는 최대 10 초까지 걸릴 수 있습니다. 완료 되 면 혼합 현실 홈에 있거나 경계를 다시 설정 하 라는 메시지가 표시 됩니다.

검색 프로세스가 10 초 보다 오래 걸리면 헤드셋에서 근접 센서에 문제가 있을 수 있습니다.
1. 근접 센서에서 스티커가 제거 되었는지 확인 합니다. 근접 센서는 거의 forehead의 중심이 되는 헤드셋 내부에 있습니다.
2. 근접 센서가 헤드셋에 입력을 전환 하 고 있는지 확인 합니다. 손가락을 사용 하 여 입력이 헤드셋으로 전환 되는 것을 확인 하기 위해 근접 센서를 몇 번 커버 하 고 확인 합니다. PC 위쪽에 **Windows 키 + Y** 배너가 표시 됩니다. 키보드에서 **Windows 키 + Y** 를 입력 하 여 언제 든 지 입력을 헤드셋으로 수동으로 전환할 수 있습니다.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>내 경계를 찾을 수 없다는 메시지가 표시 됩니다.   어떻게 해야 합니까?

Windows Mixed Reality는 기존 경계를 식별 하는 데 문제가 있을 수 있습니다. 새 경계를 만들거나 장치를 "장착 및 고정" 모드로 사용할 수 있습니다. 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>"추적 끊김" 또는 "이 공간을 위한 경계가 없습니다." 라는 메시지가 표시 됩니다.

새 경계를 만들어야 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면
* **시작 > 혼합 현실 포털** 을 선택 합니다.
* "설치 실행"을 선택 합니다.

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>경계는 항상 표시 됩니다. 어떻게 할 수 있나요?

경계는 가까이 있을 때 나타납니다. 범위에 좁은 모양이 나 불규칙 한 셰이프가 있는 섹션이 포함 된 경우 해당 경계에 근접 하 여 원하는 것 보다 더 자주 표시 되도록 할 수 있습니다. 이 문제를 해결 하려면 더 크고 더 많은 일반 셰이프를 사용 하 여 경계를 다시 만들어 보세요. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면
* **시작 > 혼합 현실 포털** 을 선택 합니다.
* "설치 실행"을 선택 합니다.

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>경계를 일시적으로 해제 하려면 어떻게 해야 하나요?

* **시작 > 혼합 현실 포털** 을 선택 합니다.
* "메뉴"를 엽니다. 
* "경계"를 "해제"로 설정 합니다. 경계가 꺼진 상태에서 한 곳으로 유지 해야 합니다.


## <a name="problems-in-windows-mixed-reality-home"></a>Windows Mixed Reality 홈의 문제

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>내 컨트롤러가 Windows Mixed Reality 홈에 표시 되지 않습니다.

컨트롤러에 전체 배터리가 있는지 확인 하 고 Bluetooth를 사용 하 여 올바르게 쌍을 이루어야 합니다. Windows 단추를 사용 하 여 컨트롤러를 켜고 켭니다. 그래도 컨트롤러를 볼 수 없는 경우 연결을 시도 하 고 **장치 > Bluetooth** 의 설정 메뉴에서 각 컨트롤러를 다시 페어링 합니다.

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>Windows Mixed Reality 홈의 높이가 올바른 높이가 아니거나 비스듬하게 표시 되지 않습니다.

응용 프로그램을 전 세계에 배치한 후 시작 하는 **시작 > 대화방 조정** 을 선택 하 여 헤드셋을 작성 하는 동안 변경 합니다. 이 앱에서 touch pad (동작 컨트롤러) 또는 방향 패드 (게임 패드)를 사용 하 여 층 높이를 조정 하도록 지정 합니다. 느낌이 올바르면 Windows 단추를 사용 하 여 홈으로 돌아갑니다.

### <a name="my-headset-has-stopped-tracking"></a>내 헤드셋에서 추적을 중지 했습니다.

표시등이 켜져 있고 헤드셋의 전면에 내부 추적 카메라를 방해 하지 않는지 아무것도 없는지 확인 합니다. 추적이 손실 된 경우 다시 시작 하는 데 몇 초 정도 걸릴 수 있습니다. 추적이 다시 시작 되지 않으면 Windows Mixed Reality 포털을 다시 시작 해 보세요. 자세한 내용은 [문제 해결 추적](tracking.md) 을 참조 하세요.

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>바탕 화면 화면의 헤드셋에서 보이는 항목의 미리 보기를 표시할 수 없습니다.

혼합 현실 포털에는 화면 아래쪽의 **재생** 단추가 있습니다 .이 단추를 사용 하면 데스크톱 화면에서 헤드셋에 표시 되는 항목의 미리 보기를 볼 수 있습니다. 그러나 성능상의 이유로이 기능은 Windows Mixed Reality Ultra (90Hz)에서 실행 되는 Pc 에서만 사용할 수 있습니다.

## <a name="headset-connectivity-issues"></a>헤드셋 연결 문제

### <a name="my-computer-does-not-have-an-hdmi-port"></a>내 컴퓨터에 HDMI 포트가 없습니다.
컴퓨터에 HDMI 포트가 없지만 비디오를 출력 하기 위한 DisplayPort (DP), mini DisplayPort (miniDP) 또는 USB 종류-C (USB) 포트를 사용 하는 경우 [지원 되는 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)를 사용 해야 할 수 있습니다.

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋에서 USB 또는 HDMI 확장 케이블을 사용할 수 있나요?
Windows Mixed Reality 헤드셋은 USB 또는 HDMI 확장 케이블의 사용을 공식적으로 지원 하지 않습니다. 이러한 케이블을 사용 하면 PC의 USB 컨트롤러와 혼합 현실 헤드셋 사이에 발생 하는 신호 무결성 및 버스 전력의 차이 때문에 혼합 현실 환경에 큰 영향을 줄 수 있습니다. 헤드셋에 파란색 화면이 잠깐 표시 되 고 블랙 및 Mixed Reality 포털을 사용 중에 다시 시작 하거나 완전히 제거 하는 경우 또는 헤드셋 오디오가 glitchy 되거나 헤드셋 오디오가 검정색으로 깜박이는 경우에는 확장 케이블 없이 헤드셋을 사용해 보세요.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>"디스플레이 케이블 확인" 오류가 발생 합니다.

* 모든 어댑터를 사용 하 여 헤드셋을 PC에 연결 하는 경우 Windows Mixed Reality를 지원 하는지 확인 합니다. 또한 어댑터에 HMD를 연결 하기 전에 어댑터를 PC에 연결 해 봅니다.
* PC에 통합 그래픽과 개별 그래픽이 모두 있는 경우 활성 그래픽 카드에서 HDMI 포트를 사용 하 고 있는지 확인 합니다. 경우에 따라 PC 디스플레이를 비 HDMI 포트에 연결 해야 할 수 있습니다.
* PC에 통합 된 그래픽과 개별 그래픽이 모두 있고 통합 그래픽이 오래 되어 Windows Mixed Reality를 지원 하지 않는 경우 통합 GPU를 사용 하지 않도록 설정 해 보세요.
* Pc 모니터를 PC의 HDMI 포트에 연결 합니다. 그래픽 드라이버가 최신 상태 인지 확인 합니다. AMD, Nvidia 또는 Intel에서 Windows 업데이트에 게시 된 것 보다 최신 버전으로 직접 다운로드 하 여 설치 합니다.
* 헤드셋의 hdmi 케이블을 PC의 hdmi **아웃** 포트에 연결 했는지 확인 하 고 포트에서 hdmi를 사용 하지 마십시오.
* Windows에서 디스플레이 케이블 연결을 검색 하지 못할 수 있습니다. Device Manager를 열고 헤드셋이 "모니터" 아래에 표시 되는지 확인 합니다. 그렇지 않은 경우 **작업 > 하드웨어 변경 내용 검색** 을 선택 합니다. 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>헤드셋이 있는 경우에도 "헤드셋에 배치" 라는 메시지가 표시 됩니다.

헤드셋에 배치 하는 경우 공간을 다시 로드 하는 데 몇 초 정도 걸릴 수 있습니다. 이 메시지가 나타나지 않으면 lenses 사이에 있는 헤드셋 내부의 근접 센서에서 보호 스티커가 제거 되었는지 확인 합니다. 그래도 문제가 해결 되지 않으면 헤드셋 제조업체에 문의 하십시오.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>헤드셋에 연결한 경우에도 "헤드셋 연결" 이라는 메시지가 표시 됩니다.

1. 헤드셋의 USB 및 HDMI 케이블이 PC의 올바른 포트에 연결 되어 있는지 확인 합니다. 올바른 포트를 식별 하는 방법은 다음과 같습니다.
    * USB 3.0 포트에는 "SS" 표시가 있는 특수 로고 ("SuperSpeed"를 나타냄)가 있습니다. 포트의 내부 부분은 일반적으로 파란색 이지만 이전 USB 2.0 포트는 일반적으로 내부에서 검정이 나 흰색입니다.
    * 컴퓨터에 두 개의 HDMI 포트가 있는 경우 컴퓨터의 마더보드가 아닌 그래픽 카드에 연결 하는 포트를 사용 합니다. 불연속 포트는 컴퓨터의 확장 슬롯에 있는 경우가 많지만 항상 명확 하지는 않습니다. 하나의 포트를 시도 했지만 작동 하지 않는 경우 다른 포트를 사용해 보세요.
2. 헤드셋에서 USB 및 HDMI 케이블을 분리 하 고 연결 하 여 안전 하 게 연결 하세요. USB 케이블을 연결 하는 경우 USB 케이블을 삽입 하는 동안 일시 중지 하지 마십시오.
3. Device Manager를 열고 헤드셋이 "Mixed Reality 장치" 아래에 표시 되는지 확인 합니다. "혼합 현실 장치"에서 헤드셋을 두 번 클릭 하 고 장치 상태가 "이 장치가 제대로 작동 하 고 있음을 나타냅니다."가 표시 되는지 확인 합니다. Device Manager에 나열 된 장치의 노란색 느낌표는 PC에 연결 된 장치에서 보고 하는 오류를 나타냅니다.
    * Device Manager에서 "Hololens 센서"가 노란색 느낌표가 표시 되 면 장치를 두 번 클릭 합니다. **"코드 10:이 장치에 대 한 드라이버가 설치 되어 있지 않습니다. 이 장치에 호환 되는 드라이버가 없습니다. "에 대 한** [지침](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) 에 따라 헤드셋 드라이버를 수동으로 설치 합니다.
    * PC에서 혼합 현실 헤드셋을 여러 개 사용 하 고 이전에 혼합 현실 헤드셋 드라이버를 수동으로 설치한 경우에는 일부 상황에서 수동 드라이버 업데이트가 다른 헤드셋이 아닌 시간에 연결 된 헤드셋에만 적용 될 수 있습니다. 이 경우 **"코드 31:이 장치에 필요한 드라이버를 Windows에서 로드할 수 없기 때문에이 장치가 제대로 작동 하지 않습니다. (코드 31). 요청 된 ALPC 메시지는 Device Manager에서 더 이상 사용할 수 없습니다** . Device Manager에서 "Mixed Reality 장치" 아래의 헤드셋을 마우스 오른쪽 단추로 클릭 하 고 "장치 제거"를 선택 합니다. "확인"을 선택 하 여 헤드셋을 확인 한 다음 분리 하 고 replug.
4. 헤드셋의 부분 열거를 표시 하는 경우 (일련의 USB 장치가 열거 하지만 Device Manager의 "Mixed Reality 헤드셋"에 아무것도 표시 되지 않음) 외부에서 제공 되는 USB 3.0 허브를 사용해 보세요.
5. 헤드셋 제조업체의 웹 사이트로 이동 하 여 헤드셋의 드라이버 및 펌웨어를 업데이트 합니다.
6. 헤드셋을 다른 PC에 연결 하 고 Device Manager를 엽니다. 해당 PC가 Windows Mixed Reality와 완전히 호환 되지 않더라도 헤드셋이를 열거 하는지 확인할 수 있습니다. 헤드셋에서 여러 Pc를 열거 하지 않는 경우 하드웨어 문제가 있을 수 있습니다.

**Surface 사용자에 대 한 참고 사항:** 이전 버전의 Surface Dock 및 Surface Book USB Hub 펌웨어 업데이트 소프트웨어는 혼합 현실 헤드셋과 호환 되지 않습니다. Surface PC에서 "헤드셋 연결" 메시지가 표시 되는 경우 장치가 Device Manager에서 **"코드 10: 장치를 시작할 수 없습니다" 오류** 를 보고 하는지 확인 합니다. 그렇다면 충돌 하 [는 드라이버를 제거](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)합니다. 이 작업은 한 번만 수행 해야 합니다.

**Windows 10 N 사용자에 대 한 참고 사항:** PC에서 Windows 10 N을 실행 하는 경우 혼합 현실 헤드셋을 연결한 후 Device Manager에서 **"코드 28: 설치 클래스가 없거나 잘못 되었습니다" 오류가** 표시 됩니다. N-windows 10 버전은 Windows Mixed Reality에서 지원 되지 않습니다. 자세한 내용은 다음 [지침](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 을 따르세요.

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>"USB 케이블을 확인 하십시오." 또는 "USB 속도가 충분 하지 않습니다" 라는 메시지가 표시 됩니다.

* PC에서 지원 되는 USB 3.0 포트를 사용 하 고 있는지 확인 합니다.
    * 헤드셋의 USB 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.
    * [Windows Mixed REALITY Pc 검사](https://aka.ms/pccheckapp) 앱을 실행 하 여 PC의 USB 3.0 컨트롤러가 지원 되는지 확인 합니다.
    * PC에서 각 USB 3.0 포트를 사용해 보세요. 일부 Pc에는 두 개 이상의 USB 3.0 컨트롤러가 있습니다.
    * PC에 연결 된 모든 USB 장치를 일시적으로 분리 하 고 헤드셋만 연결 합니다.
    * 사용자가 빌드한 Pc에서는 포트가 USB 3.0 포트로 표시 될 수 있지만 USB 2.0 컨트롤러에 연결 될 수 있습니다. 헤드셋이 연결 된 상태에서 Device Manager을 열고, 헤드셋에서 열거 된 장치를 찾아 한 번 클릭 한 다음, **연결로 > 장치 보기** 로 이동 합니다.
* 다른 PC에서 헤드셋을 사용해 보세요. 다른 PC가 Windows Mixed Reality와 완전히 호환 되지 않는 경우 Device Manager를 확인 하 여 "USB 속도 부족" 메시지가 표시 되는지 확인 합니다. 헤드셋이 여러 Pc에서 제대로 열거 되지 않으면 헤드셋에 결함이 있을 수 있습니다.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>혼합 현실 포털은 내 헤드셋에 연결한 후 자동으로 시작 되지 않습니다.

기본 문제로 인해 헤드셋이 제대로 검색 되지 않았을 수 있습니다. 혼합 현실 포털을 수동으로 시작 하 고 표시 되는 오류 메시지를 확인 하세요. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>내 헤드셋이 절전 모드에서 절전 모드 또는 절전 모드로 전환 되는 경우 또는 내 헤드셋이 연결 된 PC를 다시 시작할 때 내 헤드셋의 작동이 중지 되었습니다.

1. Device Manager를 열고 헤드셋이 "Mixed Reality 장치" 아래에 표시 되는지 확인 합니다.
2. "혼합 현실 장치"에서 헤드셋을 두 번 클릭 하 고 장치 상태가 "이 장치가 제대로 작동 하 고 있음을 나타냅니다."가 표시 되는지 확인 합니다.
3. 장치가 작동을 중지 했음을 나타내는 "코드 43" 오류가 표시 되는 경우 또는 헤드셋의 USB 케이블에서 분리 하 고 replug는 "Mixed Reality 장치" 아래에 표시 되지 않는 경우입니다. Microsoft는이 오류가 발생할 수 있는 잠재적인 소프트웨어/드라이버 상호 운용성 문제를 조사 하 고 있습니다. 이 문제는 적은 수의 Pc에 영향을 주므로 혼합 현실 헤드셋 드라이버에 대 한 향후 업데이트에서 해결 될 것으로 예상 됩니다.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>내 헤드셋은 PC를 절전 모드 또는 최대 절전 모드로 전환할 때 내 PC에서 버그 확인 (블루 스크린)을 생성 하도록 합니다.

Microsoft는 잠재적 소프트웨어/드라이버 상호 운용성 문제를 조사 하 고 있으며,이로 인해 PC가 절전 모드로 전환 되거나 헤드셋이 연결 된 최대 절전 모드로 전환 될 때 작은 수의 Pc가 "9F" 버그 검사 (블루 스크린)를 생성할 수 있습니다. 이 문제는 혼합 현실 헤드셋 드라이버에 대 한 향후 업데이트에서 해결 될 예정입니다.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>헤드셋 드라이버는 헤드셋에 연결 될 때 자동으로 설치 되지 않습니다.

새 Pc 또는 Windows 10의 새로 설치 된 복사본을 사용 하는 Pc에서는 헤드셋 드라이버가 다른 Windows 업데이트 뒤에 대기 될 수 있으며 즉시 설치 되지 않을 수도 있습니다. "N"-Windows 버전을 사용 하는 경우 windows Mixed Reality를 사용 하려면 Windows 10의 일반 버전으로 전환 해야 합니다. 수동으로 설치 하려면:

1. **시작 > Device Manager** 으로 이동 하 여 노란색 느낌표를 사용 하는 "hololens 센서" 장치에 대 한 "기타 장치" 아래에서 노란색 느낌표: ![ Device Manager HoloLens 센서 보기를 확인 합니다.](images/hololenssensors.png)
2. 장치를 마우스 오른쪽 단추로 클릭 하 고 속성을 선택 합니다. 이 장치의 드라이버를 읽는 장치 속성이 **설치 되지 않은 경우 (코드 28)** 창을 닫고 계속 진행 합니다. 다른 메시지가 있으면이 페이지의 나머지 부분에 대 한 문제 해결 단계를 수행 합니다.
![Device Manager에서 HoloLens 센서의 코드 28](images/code28.png)
3. 장치를 다시 마우스 오른쪽 단추로 클릭 하 고 "드라이버 업데이트 ..."를 선택 합니다. 그런 다음 "업데이트 된 드라이버 소프트웨어를 자동으로 검색" 합니다. 그러면 장치가 업데이트 된 후 Device Manager의 "혼합 현실 장치" 아래에 해당 하는 헤드셋이 표시 됩니다. ![ 혼합 현실 장치는에 표시 됩니다 Device Manager](images/mixedrealitydevices.png)

수동 설치가 작동 하지 않거나 다른 장치에서 드라이버를 찾을 수 없는 경우 기존 드라이버를 제거 하 고 다시 설치 해야 합니다. 이러한 작업을 하려면 다음을 수행합니다.
1. **시작 > Device Manager** 로 이동 하 여 헤드셋의 "Mixed Reality 장치" 아래에서 확인 합니다. 장치 상태에 "장치가 제대로 작동 하 고 있습니다."가 표시 되어야 합니다.
2. 장치를 마우스 오른쪽 단추로 클릭 하 고 "장치 제거"를 선택 합니다.
3. 표시 되는 새 팝업에서 "이 장치에 대 한 드라이버 소프트웨어 삭제" 확인란을 선택 하 고 "제거"를 선택 합니다.
4. 이 작업이 완료 되 면 PC에서 헤드셋을 분리 하 고 다시 연결 합니다. 이제 Windows 업데이트 새 드라이버를 다운로드 하 여 설치 합니다.

### <a name="troubleshooting-flowchart"></a>문제 해결 순서도

![헤드셋 연결/USB 케이블 확인](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>혼합 현실 헤드셋 표시 문제 ##

### <a name="my-headset-displays-are-black"></a>헤드셋 디스플레이는 검정색입니다.

* PC 성능 및 안정성을 확인 합니다.
    * 작업 관리자를 사용 하 여 PC의 CPU, GPU 및/또는 디스크 드라이브에 대 한 프로세스가 사고 인지 확인 합니다.
    * Windows의 응용 프로그램 및 시스템 이벤트 로그 (이벤트 뷰어 사용)에서 자주 Windows 오류 보고 (WER) 보고서를 생성 하는 앱이 있는지 확인 합니다.
    * Windows 업데이트를 확인 하 여 Windows 버전이 최신 인지 확인 합니다. "업데이트 확인"을 여러 번 선택 해야 할 수도 있습니다.
* 앱 및 게임 안정성 확인:
    * 제대로 수행 되지 않는 앱/게임을 실행 하기 위한 최소 시스템 요구 사항을 충족 하는 PC를 확인 합니다.    
    * GPU 드라이버 버전이 최신 인지 확인 하 고 새 드라이버에서 새로운 성능 및 호환성 문제 및 재발을 확인 하십시오.
    * SteamVR apps 및 게임을 사용 하는 경우 SteamVR 및 SteamVR 구성 요소에 대 한 Windows Mixed Reality가 최신 상태 인지 확인 합니다.
* HDMI 어댑터 호환성 확인:
    * HDMI 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.
    * HDMI 어댑터를 사용 하는 경우 (예: HDMI 어댑터에 대 한 미니 DisplayPort) Windows Mixed Reality와 호환 되는지 확인 합니다. 어댑터는 HDMI 2.0를 지원 해야 하며 1080p만 지 원하는 이전 어댑터가 많이 있습니다. [Windows Mixed Reality의 권장 어댑터를](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)참조 하세요.
    * 플러그 순서는 중요할 수 있습니다. 헤드셋 어댑터를 어댑터에 연결 하기 전에 컴퓨터에 HDMI 어댑터를 연결 합니다. 특히, USB-C에서 HDMI 어댑터를 사용 하는 경우에는 특히 그렇습니다. 
    * 확장 케이블을 사용 하는 경우 제거 해 보세요.
* 그래픽 카드 및 드라이버 호환성 확인:
    * Pc 모니터로 PC의 HDMI 포트를 사용해 보세요. 일부 Pc에는 두 개 이상의 HDMI 포트가 있을 수 있으며, 일부는 활성 상태가 아닐 수 있습니다.
    * PC에 iGPU (통합 그래픽 처리 장치)와 개별 Gpu (그래픽 처리 장치)가 모두 있는 경우에는 사용자가 사용자의 컴퓨터에 연결 되어 있는지 확인 합니다.<br> ![HDMI 포트](images/HP_HDMI_Ports_s.png)
    * GPU 드라이버 버전을 다시 확인 합니다. 최신 상태 인지 확인 하 고 새로운 성능 및 호환성 문제 및 새로운 드라이버에 대 한 재발에도 유의 하세요.
    * 노트북에서 혼합 현실를 사용 하 고 있고 그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치한 경우 PC 제조업체의 웹 사이트 또는 Windows 업데이트에서 제공 되는 최신 그래픽 카드 드라이버로 다운 그레이드 해 보세요.
    * Pc에 여러 개의 PC 모니터가 연결 되어 있는 경우 하나 이상의 PC 모니터의 연결을 일시적으로 해제 해 보세요.
    * PC 모니터에 대 한 사용자 지정 새로 고침 빈도를 설정한 경우 60Hz와 같은 표준 새로 고침 속도로 일시적으로 되돌립니다.
    * Windows를 다시 설치 하지 않고 최근에 그래픽 카드를 변경한 경우 헤드셋 모니터에 올바른 드라이버가 설치 되어 있는지 확인 합니다. 헤드셋이 연결 된 상태에서 "Mixed Reality 헤드셋"이 Device Manager의 모니터 노드 아래에 나열 되는지 확인 합니다.
    * PC에 Nvidia 그래픽 카드가 있는 경우 Nvidia의 3D 비전 소프트웨어를 사용 하지 않도록 설정 해야 합니다.
    * 일부 그래픽 카드 (특히 이전 그래픽 카드)에서 hdmi 포트는 HDMI 2.0을 지원 하지 않거나 Windows Mixed Reality와 완전히 호환 되지 않을 수 있습니다. [HDMI 2.0 어댑터에 활성 DisplayPort 1.2를](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) 사용 하 여 그래픽 카드의 DisplayPort 포트를 사용해 보세요.
    * HP 제품 번호 1RJ99EA # 아부다비를 포함 하는 HP Omen Pc에는 Windows Mixed Reality와 호환 되지 않는 HDMI 포트가 있습니다. 이를 확인 하려면 "HP 지원 길잡이"를 열고 제품 번호가 앱의 아래쪽에 표시 됩니다.
    * PC에 AMD R 9 시리즈 그래픽 카드가 있고 Samsung Mixed Reality 헤드셋을 사용 중인 경우 헤드셋에서 그래픽 카드의 HDMI 포트를 사용 하려면 헤드셋의 펌웨어를 버전 1.0.8 이상으로 업데이트 해야 합니다.
    * Surface Book 2를 사용 하는 경우 [USB-C를 사용 하 여 HDMI 어댑터를](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)사용 하 고 있는지 확인 하세요.
* 혼합 현실 헤드셋 하드웨어 문제를 확인 합니다.
    * 혼합 현실 헤드셋에서 하드웨어 문제를 확인 하거나 규칙을 처리 하려면 혼합 현실 헤드셋을 다른 PC에 연결 해 보세요. 
    * 증상이 매우 유사 하므로 PC 호환성 및 설정 문제를 먼저 확인 합니다.
* USB 케이블이 USB 3.0 이상 포트에 연결 되어 있는지 확인 합니다. USB 3.0 포트 옆에 SS (Super Speed)가 기록 됩니다. 이러한 색은 종종 파란색 (항상 그렇지는 않음)입니다.        

도움이 되는 경우 아래의 헤드셋 검은색 화면 문제 해결 순서도를 참조 하세요.

![검정 화면/모든 항목을 볼 수 없음](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>일부 사용 후 헤드셋이 검정색으로 표시 되는 경우도 있습니다.

* PC에 있을 수 있는 USB 일시 중단 또는 절전 기능을 사용 하지 않도록 설정 해 보세요. 예를 들어 Windows 전원 옵션의 [usb 선택적 일시 중단](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) , "컴퓨터에서 전원 절약을 위해이 장치를 끌 수 있도록 허용" 설정 DEVICE MANAGER 및 PC의 펌웨어에 있는 모든 usb 전원 저장 설정입니다.
* PC에 연결 된 다른 모든 USB 장치 및 주변 장치와 일시적으로 연결을 끊습니다.
* GPU 드라이버 버전을 다시 확인 합니다. 최신 상태 인지 확인 하 고 새로운 성능 및 호환성 문제 및 새로운 드라이버에 대 한 재발에도 유의 하세요.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>헤드셋의 디스플레이 중 하나가 검은색입니다.

* HDMI 어댑터를 사용 하는 경우 HDMI 2.0을 지원 하는지 확인 합니다.
* 사용할 수 있는 모든 USB 및 HDMI 확장 케이블을 제거 합니다.
* 그래픽 드라이버가 최신 상태 인지 확인 합니다.
* 다른 PC에서 혼합 현실 헤드셋을 사용해 보세요.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>헤드셋은 잠시 파란를 표시 한 다음 혼합 현실 포털 다시 초기화를 표시 합니다.

일반적으로 PC에서 가끔 USB 컨트롤러 안정성 문제가 있음을 나타냅니다.
* 다른 USB 포트를 사용해 보세요. PC에 USB 3.0 컨트롤러가 여러 개 있을 수 있습니다.
* 확장 케이블을 제거 합니다 (해당 하는 경우).
* PC에서 다른 모든 USB 장치를 분리 해 보세요.
* 외부적으로 구동 되는 USB 3.0 허브를 PC에 연결 하 고 헤드셋을 허브에 연결 해 보세요.
* 데스크톱 PC를 사용 하는 경우 USB 3.0 PCIe 카드를 구입 하 여 PC에 다른 USB 컨트롤러를 추가 하는 것이 좋습니다.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>내 헤드셋은 PC를 중지 하거나 시작 하는 동안 검정색 화면을 표시 합니다.

일부 Pc의 경우 또는 PC를 다시 부팅 하는 동안 헤드셋이 연결 된 상태를 유지 하면 시작 프로세스에 방해가 될 수 있습니다. PC가 "기본 모니터"로 표시 되는 헤드셋 표시를 선택 하 여 PC 시작 진행률을 표시 하거나, 제대로 시작 되지 않아 "중단" 하거나, 비프음 오류 코드를 생성할 수 있습니다. 이 동작은 PC 제조업체와 모델 및/또는 그래픽 카드의 제조업체와 모델에 따라 크게 달라 집니다. 이 문제를 해결하려면
* 다른 포트를 사용 하려면 어댑터를 사용 해야 할 수 있는 경우에는 그래픽 카드의 다른 포트에 헤드셋을 연결 합니다.
* PC의 BIOS/UEFI 펌웨어가 최신 상태 인지 확인 합니다 (이 작업을 수행 하는 데 익숙한 경우에만 PC의 BIOS/UEFI 펌웨어를 업데이트).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Surface PC를 사용 하는 경우 내 PC 또는 헤드셋은 깜박임, 플래시 또는 검정색 상태를 표시 합니다.

* HDMI 2.0을 지 원하는 HDMI 어댑터를 사용 하 고 있는지 확인 합니다. 이전 HDMI 어댑터 대부분은 혼합 현실 헤드셋에 충분 하지 않은 1080p 해상도만 지원 합니다.
* 그래픽 드라이버가 최신 상태 인지 확인 합니다. Windows 업데이트를 확인 하는 것 외에도 PC 제조업체의 웹 사이트에서 업데이트 된 그래픽 드라이버를 확인할 수 있습니다.
* 일부 Surface 장치는 Windows Mixed Reality와 호환 되지 않습니다. [Surface 호환성 및 요구 사항](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)에 대해 자세히 알아보세요.

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>종료 하 고 빠른 시작을 수행한 후에는 헤드셋 디스플레이가 작동 하지 않습니다.

헤드셋 케이블 및 USB 케이블을 헤드셋에서 분리 한 후 다시 연결 합니다.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>내 헤드셋은 매우 고르지 않지만 혼합 현실 포털의 미리 보기 창에는 잘 표시 됩니다.

* PC의 시스템 리소스 (CPU, 메모리 및 하드 드라이브)를 사용할 수 있고 다른 앱 또는 프로세스에서 해석 또는 최대값를 사용할 수 있는지 확인 합니다.
* 그래픽 드라이버를 업데이트 합니다.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Device Manager에서 "설치 클래스가 없거나 잘못 되었습니다." 오류가 발생 합니다.

Device Manager에 노란색 느낌표가 있는 "HoloLens 센서"가 표시 되 면 장치를 두 번 클릭 하 여 추가 세부 정보를 확인 합니다. "이 장치의 드라이버가 설치 되어 있지 않습니다. 라는 메시지가 표시 되 면 (코드 28)--설치 클래스가 없거나 잘못 되었습니다. "는 PC에서 [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)을 실행 하 고 있기 때문입니다. Windows 10의 N-버전은 Windows Mixed Reality를 지원 하지 않으므로 N이 아닌 Windows 10 버전을 설치 해야 합니다.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>내 WMR 환경은 헤드를 이동 하 고 이중 비전을 표시 하는 경우 stutters.

통합 된 그래픽 및 Nvidia GPU를 사용 하는 랩톱에서 다음 프레임 후 이전 프레임을 표시 하는 데 걸리는 시간이 지나면 오류가 발생 합니다. 그러면 요, 피치 또는 롤 이동에서 헤드를 더 빨리 이동 하 게 됩니다. Nvidia 그래픽 드라이버 436.48 후 드라이버에 문제가 있는 것 같습니다.  이 드라이버를 설치 하면 Nvidia에서 업데이트 된 드라이버의 문제를 해결할 때까지 문제가 해결 됩니다. Nvidia 그래픽 드라이버 436.48을 직접 설치 하려면 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)를 방문 하십시오.

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>내 헤드셋을 사용 하는 경우 discomfort 발생 합니다.
Windows Mixed Reality에서 편안 하 게 보호 하는 방법에 대 한 일반적인 정보는 [Windows Mixed reality 모던 헤드셋 상태, 안전 및 편안](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)을 참조 하세요. 특정 헤드셋에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>헤드셋에서 더 명확 하 게 볼 수 있는 방법은 무엇입니까?
헤드셋의 맞춤을 조정해 보세요. 위쪽 및 아래쪽 이나 왼쪽 및 오른쪽으로 이동 하 여 얼굴의 위치를 조정 하 고 straps를 조정 하 여 snug.

헤드셋에서 지 원하는 경우에는 해당 보정 설정을 조정할 수도 있습니다. 헤드셋에 조절기가 있는 경우 보정을 사용 합니다. 그렇지 않으면 **설정 > 혼합 현실 > 시각적 품질** 로 이동 하 여 보정을 조정 합니다. 특정 장치의 보정에 대 한 자세한 내용은 헤드셋 제조업체에 문의 하세요.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>혼합 현실 포털 오류 메시지 및 문제

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>"문제가 발생 했습니다." 오류 메시지가 발생 하거나 혼합 현실 포털에서 문제가 발생 했습니다.

Windows Mixed Reality를 다시 시작 합니다.
1. PC에서 두 헤드셋 케이블의 연결을 끊습니다.
2. PC를 다시 시작 합니다.
3. 헤드셋을 다시 연결 합니다.

그래도 작동 하지 않으면 PC가 헤드셋을 인식 하는지 확인 합니다.
1. 시작을 선택합니다.
2. 검색 상자에 "장치 관리자"를 입력 하 고 목록에서 선택 합니다. 
3. "혼합 현실 장치"를 확장 하 고 헤드셋이 나열 되는지 확인 합니다. 

나열 되지 않은 경우 다음을 시도 합니다.
1. 사용 가능한 경우 헤드셋을 PC의 다른 포트에 연결 합니다.
2. Windows 업데이트에서 최신 소프트웨어 업데이트를 확인 합니다.
3. Windows Mixed Reality 제거 및 다시 설치:
    1. PC에서 두 헤드셋 케이블의 연결을 끊습니다.
    2. **설정 > 혼합 현실 > 제거** 를 선택 합니다.
    3. **설정 > 장치 > Bluetooth & 기타 장치** 를 선택 하 여 동작 컨트롤러를 연결 해제 합니다. 각 컨트롤러를 선택한 다음 "장치 제거"를 선택 합니다.
    4. 헤드셋을 PC에 다시 연결 하 여 Windows Mixed Reality를 다시 설치 합니다.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>"USB 케이블 확인" 오류 메시지를 받고 있습니다.

헤드셋을 다른 USB 포트에 연결 합니다 (SuperSpeed USB 3.0 인지 확인). 또한 헤드셋과 컴퓨터 간에 extender 나 허브를 제거해 보세요.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>"디스플레이 케이블 확인" 오류 메시지를 받고 있습니다.

다음을 시도해 보세요.
* 헤드셋을 DisplayPort 1.2 이상 또는 HDMI 1.4 이상에 연결 합니다. 포트가 PC의 고급 그래픽 카드와 일치 하는지 확인 합니다.
* 어댑터를 사용 하는 경우 4K 가능 인지 확인 합니다.
* 다른 HDMI 포트를 사용해 보세요.
* 외부 모니터가 HDMI 포트에 연결 된 경우 DisplayPort에 연결 하 고 헤드셋에 대해 HDMI 포트를 사용 하세요.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>"문제가 발생 했습니다." 오류 코드 및 해결 방법

| **Windows 10 오류 코드** (버전 1809/버전 1709, 1803) | **오류 메시지 및 문제 해결 제안**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **디스플레이 케이블 확인: 헤드셋의 디스플레이 케이블이 올바르게 연결 되어 있는지 확인 합니다.** <br/><br/><ol start="1"><li>헤드셋의 USB 및 HDMI 케이블을 모두 분리 하 고 다시 연결 합니다.</li><li>Device Manager를 확인 하 고 "모니터" 아래에 "혼합 현실 헤드셋" 모니터가 있는지 확인 합니다.</li><li>그래픽 드라이버가 최신 상태 인지 확인 합니다 (그래픽 카드 제조업체의 웹 사이트에서).</li><li>어댑터를 사용 하 여 헤드셋에 연결 하는 경우 [Windows Mixed Reality를 지원](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)하는지 확인 합니다.</li><li>그래픽 카드에 DisplayPort 및 HDMI 포트가 둘 다 있는 경우 그래픽 카드의 DisplayPort 포트를 사용 하 고 지원 되는 혼합 현실 DisplayPort-HDMI 어댑터를 사용 합니다.</li><li>PC에서 다른 USB 3.0 포트를 사용해 보세요.</li></ol> |
|   1-5 / 2197815297-5  | **디스플레이 케이블 확인: 헤드셋이 올바르게 초기화 되지 못했음을 표시 합니다. PC를 다시 시작 하 고 헤드셋을 다시 연결 해 보세요.**<br/><br/>Windows에서 헤드셋 모니터를 볼 수 있지만 Windows Mixed Reality는 혼합 현실 헤드셋의 디스플레이와 통신 하는 데 문제가 있습니다. 이 문제를 해결하려면<br/><ol start="1"><li>그래픽 드라이버가 최신 상태 인지 확인 합니다 (그래픽 카드 제조업체의 웹 사이트에서).</li><li>어댑터를 사용 하 여 헤드셋에 연결 하는 경우 [Windows Mixed Reality를 지원](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)하는지 확인 합니다.</li><li>그래픽 카드에 DisplayPort 및 HDMI 포트가 둘 다 있는 경우 그래픽 카드의 DisplayPort 포트를 사용 하 고 지원 되는 혼합 현실 DisplayPort-HDMI 어댑터를 사용 합니다.</li><li>PC를 다시 시작 해 보세요.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **Windows Mixed Reality는 헤드셋에 연결 하는 데 문제가 있습니다. 헤드셋을 분리 하 고 다시 연결 해 보세요.**<br/><br/>혼합 현실 헤드셋을 완전히 초기화 하지 못했습니다. 이는 일시적인 오류일 가능성이 높습니다. 헤드셋을 분리 하 고 다시 연결 하 여이 문제를 해결 합니다.
|   7-4 / 2181038087-4  | **Windows Mixed Reality는 헤드셋에 연결 하는 데 문제가 있습니다. 헤드셋을 분리 하 고 다시 연결 해 보세요.**<br/><br/>혼합 현실 헤드셋 드라이버가 헤드셋에서 추적 카메라를 초기화 하지 못했습니다. 이는 일시적인 오류일 가능성이 높습니다. 헤드셋을 분리 하 고 다시 연결 하 여이 문제를 해결 합니다.
|   7-5 / 2181038087-5  | **Windows Mixed Reality는 헤드셋에 연결 하는 데 문제가 있습니다. 헤드셋을 다른 USB 포트에 연결 하 고 PC에 연결 된 다른 모든 USB 장치를 일시적으로 분리 해 보세요.**<br/><br/>Windows Mixed Reality는 혼합 현실 카메라 프레임 타임 스탬프와 PC 타임 스탬프 간의 동기화가 끊어졌습니다. 일시적인 오류 이거나 USB 신호 무결성 문제를 나타낼 수 있습니다. 이 문제를 해결하려면</li><li>모든 USB 장치 및 주변 장치를 일시적으로 분리 하 고, 모든 확장 케이블을 제거 하 고, 헤드셋만 연결 합니다.</li><li>Windows 전원 옵션의 선택적 일시 중단, "컴퓨터에서 전원 절약을 위해이 장치를 끌 수 있도록 허용" 설정, Device Manager의 모든 USB 절전 설정, PC의 펌웨어에 있는 모든 usb 절전 설정을 사용 하 여 PC에서 USB 일시 중단/전원 저장 기능을 사용 하지 않도록 설정 합니다.</li></ul>
|   7-6 / 2181038087-6  | **헤드셋 펌웨어에 문제가 있습니다. 헤드셋을 분리 하 고 다시 연결 해 보세요.** <br/><br/>일시적인 오류일 수 있습니다. 헤드셋에서 분리 하 고 다시 연결 해 보세요. 그렇지 않으면 다음을 수행 합니다.</li><li>Windows 업데이트를 확인 하 여 사용 가능한 최신 헤드셋 드라이버를 실행 하 고 있는지 확인 합니다.</li><li>다른 PC에서 헤드셋을 사용해 보세요. 동일한 오류 메시지가 표시 되는 경우 헤드셋을 서비스 해야 합니다.</li></ul>
|   7-7 / 2181038087-7  | **Windows Mixed Reality는 헤드셋에 연결 하는 데 문제가 있습니다. 헤드셋을 다른 USB 포트에 연결 하 고 PC에 연결 된 다른 모든 USB 장치를 일시적으로 분리 해 보세요.**<br/><br/>혼합 현실 헤드셋 드라이버가 헤드셋의 펌웨어를 초기화 하지 못했습니다. 일시적인 오류일 수 있습니다. 헤드셋에서 분리 하 고 다시 연결 해 보세요. 그렇지 않으면 다음을 수행 합니다.<li>Windows Mixed Reality를 실행 하지 않아도 되는 USB 장치 및 주변 장치를 일시적으로 분리 합니다.</li><li>Windows 업데이트를 확인 하 여 사용 가능한 최신 헤드셋 드라이버를 실행 하 고 있는지 확인 합니다.</li></ul>
|   7-11 / 2181038087-11 | **CPU가 너무 오래 되어 Windows Mixed Reality와 호환 되지 않습니다.**<br/><br/>CPU에 혼합 현실 동작 컨트롤러에 필요한 AVX 명령 집합이 없기 때문에 PC에서 호환성 검사에 실패 합니다. [Windows Mixed Reality 호환 PC](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons)가 필요 합니다.
|   7-12 / 2181038087-12 | **헤드셋이 호환 되지 않는 USB 컨트롤러에 연결 되어 있습니다. 사용 가능한 경우 헤드셋을 다른 USB 포트에 연결 해 보세요. 또는 호환 되지 않는 드라이버 대신 Microsoft USB 드라이버를 설치 해 보십시오.**<br/><br/>헤드셋은 호환 되지 않는 타사 USB 컨트롤러 드라이버에 연결 된 USB 포트에 연결 되어 있을 수 있습니다. 이러한 USB 3.0 컨트롤러 드라이버에는 일반적으로 혼합 현실 헤드셋의 서로 다른 부분을 결합 된 단위로 집계 하는 [ContainerID 설명자](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows)를 읽고 처리 하는 기능이 없습니다. 즉, 올바른 헤드폰에서 오디오를 재생 하 고 올바른 디스플레이를 비디오로 출력 하 고 올바른 센서에서 추적 데이터를 가져옵니다. USB 컨트롤러 드라이버를 변경 하려면: <ol start="1"><li>Device Manager를 시작 합니다.</li><li>범용 직렬 버스 컨트롤러의 범주를 확장 하 고 마우스 오른쪽 단추를 클릭 하 여 "확장 가능한 호스트 컨트롤러" 라는 텍스트가 포함 된 각 항목에 대 한 드라이버를 제거 **하 고 이름** 에 "Microsoft"가 없습니다.</li><li>이전 드라이버가 제거 되었는지 확인 하려면 "이 장치에 대 한 드라이버 소프트웨어 삭제"를 선택 합니다.</li><li>"확장 가능한 호스트 컨트롤러" 텍스트를 포함 하는 각 항목의 끝에 "Microsoft"가 있는지 확인 합니다.</li><li>HMD를 연결 합니다.</li></ol>문제가 간헐적으로 발생 하는 경우 HMD가 HMD 드라이버에서 명령에 제대로 응답 하지 않을 수 있습니다. 문제를 해결 하려면 30 초 이상 HMD를 분리 한 다음 다시 연결 하세요. | 
|   7-13 / 2181038087-13 | **헤드셋이 호환 되지 않는 USB 컨트롤러에 연결 되어 있습니다. 사용 가능한 경우 헤드셋을 다른 USB 포트에 연결 해 보세요. 그렇지 않은 경우 새 USB 3.0 컨트롤러를 설치 해야 합니다.**<br/><br/>Windows Mixed Reality는 혼합 현실 카메라 프레임 타임 스탬프를 PC 타임 스탬프와 동기화 할 수 없습니다. 이 문제는 ITP (등시 타임 스탬프 패킷)를 지원 하지 않는 호환 되지 않는 USB 3.0 호스트 컨트롤러에 의해 발생할 수 있습니다. PC 제조업체에 문의 하 여 ITP를 사용할 수 있는지 확인 하거나 ITP 지원을 통해 다른 USB 호스트 컨트롤러로 전환 합니다. |
|   7-14 / 2181038087-14 | **Windows Mixed Reality는 헤드셋에 연결 하는 데 문제가 있습니다. 헤드셋을 분리 하 고 다시 연결 해 보세요.**<br/><br/>Windows Mixed Reality는 혼합 현실 헤드셋에서 현재 상태 센서를 초기화 하는 데 문제가 있습니다. Device Manager 헤드셋은 "PoseThread가 상태 센서를 초기화 하지 못했습니다." 라는 오류 메시지를 표시 합니다. 이 문제를 해결하려면<br/><ol start="1"><li>헤드셋을 분리 하 고 다시 연결 합니다. USB 케이블이 모든 방식으로 연결 되어 있는지 확인 합니다.</li><li>PC에서 다른 USB 포트를 사용해 보세요.</li><li>다른 PC의 헤드셋을 사용해 서 헤드셋이 해당 PC의 Device Manager 완전히 열거 되는지 확인 합니다.</li><li>키보드 또는 마우스와 같이 충돌 하는 다른 HID 드라이버가 PC에 설치 되어 있는지 확인 합니다. (물음표 로고를 사용 하 여 Device Manager에서 HID 장치를 찾습니다.)</li><li>Windows 10 버전 1709 또는 1803 버전을 실행 하는 Samsung Mixed Reality 헤드셋을 사용 하는 경우 오류 코드 2181038087-12에 대 한 지침에 따라 USB 3.0 컨트롤러가 타사 USB 컨트롤러 드라이버를 실행 하 고 있는지 확인 합니다.</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality에서 호환 되지 않는 WinUSB 드라이버를 설치 했습니다.**<br/><br/><ol start="1"><li>PC에서 WinUSB 드라이버가 Windows와 함께 제공 되는 것이 고 타사 USB 드라이버가 PC에서 WinUSB 사본을 덮어쓰지 않았는지 확인 합니다.</li><li>문제가 지속 되 면 Windows 설치를 복구 하거나 다시 설치 해야 할 수 있습니다.</li></ol> |
|   13-11/-            | 혼합 현실 포털에서 Windows의 앱 등록 문제가 발생 했습니다. 응용 프로그램 이벤트 로그 (이벤트 뷰어 사용)를 확인 하 여 추가 정보가 있는지 확인 합니다. |
|   14-1/-            | 혼합 현실 포털에서 그래픽 및 컴퍼지션 스택을 초기화 하는 데 문제가 있습니다. 이 문제를 해결하려면<ul><li>바탕 화면 창 관리자 (Windows Graphics stack의 주요 구성 요소인 DWM)가 충돌 하는 것일 수 있습니다. 이벤트 뷰어를 사용 하 여 응용 프로그램 이벤트 로그를 확인 하 여이 문제가 발생 하는지 확인 합니다.</li><li>그래픽 드라이버를 새로 제거한 다음 그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치 하십시오.</li></ul> |
|   14-2/C0001160-101  | **헤드셋에 연결 하는 데 문제가 발생 했습니다. 사용할 수 있는 모든 확장 케이블을 제거 하 고, 헤드셋을 그래픽 카드의 올바른 포트에 연결 했는지 확인 하세요. 어댑터를 사용 하는 경우 혼합 현실과 호환 되는지 확인 합니다. 여전히 문제가 발생 하는 경우 그래픽 드라이버를 업데이트 해 보세요.**<br/><br/>혼합 현실 표시 및 컴퍼지션 스택을 초기화 하지 못했습니다. PC의 그래픽 카드 또는 그래픽 카드 드라이버가 Windows Mixed Reality와 호환 되지 않을 수 있습니다. 이를 확인 하려면: <ul><li>PC가 Windows Mixed Reality의 최소 시스템 요구 사항을 충족 하는지 확인 합니다.</li><li>Windows 10, 버전 1809 또는 최신 버전에서 Dell Inspiron 5577 Pc를 사용 하는 경우 Dell의 TrueColor 그래픽 후 처리 기능과 충돌 하기 때문에이 오류가 표시 될 수 있습니다. 이 문제를 해결 하려면 Dell의 TrueColor 앱을 사용 하 여 TrueColor 기능을 해제 한 다음 Mixed Reality 포털을 다시 실행 해 보세요.</li><li>데스크톱 PC의 그래픽 카드 제조업체 웹 사이트에서 최신 그래픽 드라이버를 설치 합니다. 랩톱에서 노트북 제조업체의 웹 사이트에서 제조업체 및 모델용 최신 그래픽 드라이버를 설치 합니다.</li><li>타사 그래픽이 있거나 소프트웨어/액세서리를 표시 하는 경우 이러한 앱 및 드라이버를 일시적으로 제거 합니다.</li><li>"다시 시도"를 선택 하 여 일시적인 문제 인지 확인 합니다.</li></ul> |
|   14-3/-             | **헤드셋에 연결 하는 데 문제가 발생 했습니다. 사용할 수 있는 모든 확장 케이블을 제거 하 고, 헤드셋을 그래픽 카드의 올바른 포트에 연결 했는지 확인 하세요. 어댑터를 사용 하는 경우 혼합 현실과 호환 되는지 확인 합니다. 여전히 문제가 발생 하는 경우 그래픽 드라이버를 업데이트 해 보세요.** <br/><br/><ul><li>PC 모니터에서 사용자 지정 모드 또는 새로 고침 빈도를 사용 하는 경우 새로 고침 빈도를 60Hz로 설정 해 보세요.</li><li>사용 중인 어댑터가 Windows Mixed Reality를 지원 하는지 확인 합니다.</li><li>그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치 해 보세요.</li><li>"다시 시도"를 클릭 하 여 일시적인 문제 인지 확인 합니다.</li></ul> |
| 14-4/-             | **헤드셋에 연결 하는 데 문제가 발생 했습니다. 사용할 수 있는 모든 확장 케이블을 제거 하 고, 헤드셋을 그래픽 카드의 올바른 포트에 연결 했는지 확인 하세요. 어댑터를 사용 하는 경우 혼합 현실과 호환 되는지 확인 합니다. 여전히 문제가 발생 하는 경우 그래픽 드라이버를 업데이트 해 보세요.** <br/><br/><ul><li>PC에는 그래픽 어댑터에서 지원할 수 있는 것 보다 더 많은 PC 모니터가 연결 되어 있을 수 있습니다. 기본 PC 모니터를 제외 하 고 모두 연결을 끊습니다.</li><li>사용 중인 어댑터가 Windows Mixed Reality를 지원 하는지 확인 합니다.</li><li>그래픽 카드 제조업체의 웹 사이트에서 최신 그래픽 드라이버를 설치 합니다.</li><li>"다시 시도"를 클릭 하 여 일시적인 문제 인지 확인 합니다.</li></ul> |
|   15-5/-             | **혼합 현실 포털은 코어 혼합 현실 및 Windows 구성 요소가 종속 된 Windows 구성 요소와 동기화가 끊어졌습니다.**<br/><br/><ul><li>PC의 성능 문제로 인해 발생할 수 있습니다. 작업 관리자에서 CPU, GPU 및 HDD가 해석 되지 않았는지 확인 합니다.</li><li>PC에서 다른 모든 USB 장치를 일시적으로 분리 합니다.</li><li>PC를 다시 시작 합니다.</li></ul> |
|   -/H0002000-0    | **Windows Mixed Reality의 PC 운영 체제가 일치 하지 않는 상태로 전환 되었습니다.**<br/><br/>업데이트에 대 한 Windows 업데이트를 확인 합니다. |
|   -/S0002261-101, S0002361 | **혼합 현실 셸 구성 요소에 문제가 있어 혼합 현실 포털이 제대로 시작 되지 않습니다.**<br/><br/><ul><li>PC에서 이벤트 뷰어를 사용 하 여 응용 프로그램 로그를 열어 Windows Mixed Reality를 시작 하려고 시도 하는 동안 응용 프로그램 작동 중단을 확인 합니다.</li><li>그래픽 드라이버가 최신 상태 인지 확인 합니다.</li><li>사용 중인 HDMI 어댑터는 Windows Mixed Reality와 호환 되지 않습니다. [여기](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)에서 지원 및 권장 되는 HDMI를 미니 디스플레이 포트 (DP) 동글을 참조 하세요.</li></ul> |


## <a name="motion-controller-problems"></a>동작 컨트롤러 문제

### <a name="my-motion-controllers-arent-working-properly"></a>내 동작 컨트롤러가 제대로 작동 하지 않습니다.

[동작 컨트롤러가](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) 작동 하지 않거나 연결 하지 않거나 헤드셋을 사용할 때 컨트롤러 이미지가 표시 되지 않는 경우 다음을 시도 합니다.
1. 컨트롤러가 켜져 있는지 확인 합니다. 설정 하려면 Windows 단추를 2 초 동안 누르고 있습니다.
2. 컨트롤러가 완전히 청구 되는지 확인 하 고 배터리가 없는 경우 교체 합니다.
3. 컨트롤러를 설정 하는 동안 다시 설정 하거나 다시 설정 합니다. Windows 단추 (4 초)를 누르고 컨트롤러를 해제 한 다음 2 초 동안 다시 길게 눌러 설정 합니다. 
4. PC에서 **Bluetooth & 기타 장치를 >는 설정 > 장치** 를 선택 하 고 컨트롤러가 페어링된 것으로 표시 되는지 확인 합니다. 그렇지 않은 경우 [쌍](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality)으로 연결 해야 합니다. 
5. 동작 컨트롤러가 "연결 됨"으로 표시 되는지 확인 합니다. "페어링"은 반드시 컨트롤러를 PC에 연결 하는 것을 의미 하지는 않습니다. 컨트롤러는 "마우스, 키보드 & 펜" 범주 아래에 나타납니다. "기타 장치"의 동작 컨트롤러에서 페어링 프로세스가 실패 하 여 작동 하지 않습니다. 동작 컨트롤러 Led를 확인 합니다. 밝은 lit controller는 페어링 되 고 연결 되어 있으며, dimly lit controller는 연결 되지 않습니다.
6. PC에서 **> Mixed Reality 포털 시작** 으로 이동 하 여 "메뉴"를 선택 합니다. 상태 메시지와 함께 표시 되는 동작 컨트롤러가 표시 되어야 합니다.
    * 준비 됨 – 컨트롤러가 모두 설정 됩니다.
    * 손실 추적 – 혼합 현실 포털에서 컨트롤러를 찾을 수 없습니다. 헤드셋 앞에서 누른 후 Windows 단추 (4 초)를 눌러 다시 시작 하 고 2 초 동안 다시 시작 합니다.
    * 배터리 부족 – 컨트롤러 배터리를 교체 합니다.
7. 외부 USB Bluetooth 어댑터를 사용 하는 경우 검은색 USB 2.0 포트에 연결 되어 있는지 확인 합니다. 또한 헤드셋의 USB 커넥터를 비롯 하 여 다른 무선 송신기 또는 USB 플래시 드라이브에서 가능한 한 멀리 떨어져 연결 해야 합니다. 
8. Windows 시작 메뉴를 마우스 오른쪽 단추로 클릭 하 고 Device Manager를 선택 하 여 PC에 Bluetooth 라디오가 하나만 있는지 확인 합니다. Bluetooth 섹션을 확장 하 고 어댑터 하나를 찾습니다. 기본 제공 라디오에서 데스크톱 PC 구성을 사용 하는 경우 외부 안테나가 연결 되어 있는지 확인 합니다. 외부 안테나가 연결 되어 있지 않으면 추적 문제가 발생할 수 있습니다. 또는 외부 bluetooth 동글을 사용 하 고, 내부 Bluetooth 기능을 사용 하지 않도록 설정 하 고, 페어링 및 연결을 다시 시도 합니다.
9. Bluetooth 설정 창이 열려 있으면 닫습니다. 백그라운드에서 열린 경우 Bluetooth 프로토콜에 대 한 많은 추가 호출이 수행 됩니다.
10. 동작 컨트롤러의 가상 배터리 수준을 확인 하십시오. 혼합 현실에서는 컨트롤러를 설정 하 고 배터리 아이콘을 볼 수 있습니다. 빨간색 이면 배터리를 교체 합니다. 일반적으로 배터리 보고는 컨트롤러를 연결한 직후 실제 수준 보다 높은 보고서를 보고 합니다. 15 초 정도 기다린 후 배터리 수준을 안정화 한 후 수준을 읽습니다.
11. **설정 > 장치 > bluetooth & 기타 장치** 에서 bluetooth 헤드폰 및 스피커를 제거 하 고 장치를 끕니다. 최상의 오디오 환경을 위해 혼합 현실 헤드셋의 헤드폰 잭 또는 기본 제공 스피커를 사용 합니다.
12. 헤드폰 또는 gamepads와 같이 PC와 쌍으로 연결 된 다른 Bluetooth 장치가 있는 경우 그 중 일부를 제거 합니다. **설정 > 장치 > Bluetooth & PC에서 기타 장치** 를 선택 하 고 장치를 선택한 다음 "장치 제거"를 선택 합니다.
13. 헤드셋에서 USB 케이블을 분리 하 고 PC에 다시 연결 하 여 PC에서 컨트롤러 기능을 다시 시작 합니다.
14. 컨트롤러는 펌웨어 업데이트를 할 때 깜박입니다. 펌웨어 업데이트가 완료 될 때까지 기다리거나, 컨트롤러가 혼합 현실에 표시 되어야 합니다.
15. PC가 5GHz Wi-fi 네트워크에 연결 되어 있는지 확인 합니다. 랩톱이 2.4 GHz Wifi 네트워크에 연결 된 경우 일반적으로 Bluetooth 연결을 공유 합니다. 이는 제품 설계에 따라 Wifi 또는 Bluetooth 성능에 부정적인 영향을 미칠 수 있습니다. 네트워크 어댑터 설정에서 기본 설정 밴드를 5Ghz로 변경 합니다. 네트워크에서 5GHz를 지원 하지 않는 경우 내부 Bluetooth 기능 대신 Bluetooth 동글을 사용할 수 있습니다.
16. Bluetooth 설정에 이미 페어링 된 동작 컨트롤러가 있는 경우 Windows는 제거 될 때까지 새 장치를 검색 하지 않습니다. 특정 동글을 사용 하 여 추가 된 경우 해당 동글을 제거할 수 있습니다.
17. PC가 기본 제공 블루투스를 사용 하는 경우 연결 문제가 있는 경우 대신 USB Bluetooth 어댑터를 사용해 보세요. 이렇게 하려면 Device Manager에서 기본 제공 되는 Bluetooth 라디오를 끄고 다른 Bluetooth 장치를 새 어댑터와 연결 해야 합니다.

### <a name="motion-controller-troubleshooting-flowchart"></a>동작 컨트롤러 문제 해결 순서도

![동작 컨트롤러용 흐름도 흐름도](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>내 컨트롤러가 무한 재부팅 (Led 이후 주기 주기)에 걸려 있습니다.

이는 중요 한 배터리 표시기 이므로 장치에 새 배터리가 있는지 확인 합니다. 문제가 지속 되 면 [장치 복구](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) 를 수행 하 여 컨트롤러를 공장 설정으로 다시 설정 합니다.

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>내 컨트롤러를 페어링 하려고 하지만 Bluetooth 설정의 "새 장치 메뉴 추가"에 표시 되지 않습니다.

컨트롤러가 이미 연결 되어 있는지 확인 하 고 제거 하 고 다시 시도 하세요. 문제가 지속 되 면 PC를 다시 시작 하 고 다시 시도 하세요. 실패 하면 [Bluetooth faq](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)를 참조 하세요.

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>이동 컨트롤러를 켜면 내 노트북에서 wi-fi 속도가 느릴 수 있습니다.

사용자의 노트북은 2.4 g h z 액세스 지점에 연결 될 때 Bluetooth와 Wi-fi 안테나를 공유할 수 있습니다. 대역 기본 설정을 5GHz로 전환할 수 있는 경우 장치 관리자에서 확인 합니다. 5GHz 네트워크를 사용할 수 없고 성능이 심각한 영향을 받는 경우 Bluetooth 동글을 사용 하는 것이 좋습니다.

![장치 관리자를 통해 Wifi 대역 선택 설정을 찾을 수 있습니다.](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>두 번째 컨트롤러를 다시 연결 하는 데 시간이 오래 걸립니다.

일부 이전 Intel 라디오에서는 동작 컨트롤러가 동시에 켜져 있는 경우이 문제가 발생 합니다. 컨트롤러의 전원을 동시에 사용 하지 마십시오.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>PC가 충돌 한 후에는 Qualcomm Bluetooth 라디오가 컨트롤러를 쌍으로 연결할 수 없습니다.

10.0.0.448 이전의 Qualcomm (QCA) Bluetooth 라디오 드라이버가 Windows 크래시 후에 잘못 된 상태로 종료 될 수 있습니다. 이 문제를 해결 하려면 PC 전원을 완전히 끕니다. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Marvell 라디오를 사용 하 여 잘못 된 컨트롤러 추적이 발생 합니다.

**Device Manager > bluetooth > MARVELL AVASTAR Bluetooth 라디오 어댑터 > 속성 > 드라이버로** 이동 하 여 드라이버 15.68.9210.47 이상을 사용 중인지 확인 합니다.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>혼합 현실 포털은 작동 하지만 내 동작 컨트롤러는 제대로 추적 되지 않습니다 (컨트롤러는 비행, 핸드쉐이킹 등).

1. 일부 조명 조건은 추적에 영향을 줄 수 있습니다. 직접 햇빛에 노출 되지 않고 HMD에 표시 되는 점 광원의 양이 많지 않은지 확인 합니다 (예: 크리스마스 트리와 같은 광원의 문자열). 
2. [Bluetooth faq](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)를 확인 하세요. 이러한 증상은 일반적으로 컨트롤러와 호스트 PC 간의 통신 오류로 인해 발생 하며 Bluetooth 링크 품질 저하를 표시 합니다.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>동작 컨트롤러 Led가 켜지 지 않지만 혼합 현실 포털에서 단추와 엄지 스틱을 계속 사용할 수 있습니다.

동작 컨트롤러 보정 캐시가 손상 되었을 수 있습니다. 캐시를 삭제 하려면 관리자 명령 프롬프트에서 다음 명령을 실행 합니다.

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

이 폴더는 Windows 탐색기에서 액세스할 수 없으며 관리자 명령 프롬프트 에서만 수정할 수 있습니다. 폴더를 삭제 한 후 PC를 다시 시작 하 고 동작 컨트롤러를 다시 연결 하 여 보정 파일을 복원 합니다.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>SteamVR apps 및 게임에는 동작 컨트롤러가 나타나지 않습니다.

SteamVR apps 및 게임이 아닌 절벽 집에서 동작 컨트롤러를 볼 수 있는 경우에는 동작 컨트롤러 모델 드라이버가 제대로 설치 되지 않을 수 있습니다. 이 드라이버는 Windows 업데이트를 통해 자동으로 다운로드 및 설치 되지만 엔터프라이즈 정책이 있는 PC를 사용할 경우 또는 Windows 업데이트 제한 된 경우에는 수동으로 설치 해야 할 수 있습니다. 동작 컨트롤러 모델 드라이버가 올바르게 설치 되었는지 확인 하려면 다음을 수행 합니다.
1. 두 동작 컨트롤러를 모두 켜고, **장치 > Bluetooth & 기타 장치** 에서 설정 앱에 "연결 됨"으로 표시 되는지 확인 합니다. "페어링 됨"으로 표시 되지 않거나 표시 되지 않으면 [쌍](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality)으로 연결 합니다.
2. Device Manager를 열고 "Bluetooth" 아래에서 "동작 컨트롤러 왼쪽" 및 "동작 컨트롤러 오른쪽"을 찾습니다.
3. 장치 중 하나를 선택 하 고 **연결을 통해 > 장치 보기** 로 이동 합니다.
4. 이제 이동 컨트롤러 Bluetooth 장치가 Bluetooth 라디오에 롤업되는 것을 볼 수 있습니다. 두 동작 컨트롤러가 동일한 노드 아래에 두 개의 "Bluetooth HID 장치" 장치가 있어야 하 고 각 Bluetooth HID 장치 아래에 "동작 컨트롤러" (회색 아이콘 포함) 라는 장치가 있어야 합니다.
5. "동작 컨트롤러" 장치를 각각 두 번 클릭 하 고 **드라이버** 탭으로 이동 합니다. 나열 된 드라이버 버전이 [이러한 동작 컨트롤러 모델 드라이버 버전](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)중 하나에 해당 하는지 확인 합니다.

동작 컨트롤러 모델 드라이버를 수동으로 다운로드 하 여 설치 하려면 [이 페이지](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) 를 방문 하 여 Windows 10 버전에 해당 하는 드라이버 버전을 확인 합니다. 설치 지침은 다운로드 페이지에서 확인할 수 있습니다.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>모션 컨트롤러 펌웨어 업데이트는 2 분 이상 소요 됩니다.

[Bluetooth faq](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)를 확인 하세요. Bluetooth 링크 품질이 저하 되는 것은 일반적으로 이러한 문제의 원인입니다.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>새 배터리를 삽입 했지만 컨트롤러 가상 배터리 수준이 전체 수준을 표시 하지 않습니다.

AA 배터리에 대해 모션 컨트롤러 배터리 수준이 조정 됩니다. 일부 저전압 rechargeable 배터리는 완전히 청구 되더라도 전체로 보고 되지 않을 수 있습니다.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>배터리가 부족할 때 컨트롤러는 진동 하지 않습니다.

배터리 레벨이 낮으면 Haptics을 사용할 수 없습니다. 배터리를 교체 합니다.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>장치를 세 번 vibrated 후 종료 합니다.

배터리가 부족 하 여 중단 임계값에 도달 했습니다. 배터리를 교체 합니다.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Samsung 모션 컨트롤러의 터치 패드가 가운데에 있거나 데드가 있습니다.

이는 하드웨어 결함 일 수 있으므로 교체 또는 교환에 대 한 소매점 또는 장비 제조업체로 다시 이동 해야 합니다.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>컨트롤러가 제대로 작동 하지 않으며 장치를 업데이트할 수 없습니다.

공장 조건으로 복원 합니다 (새 배터리가 필요).
1. 컨트롤러를 분리 하 고 전원 해제 합니다.
2. 배터리 덮개를 엽니다.
3. 새 배터리를 삽입 합니다.
4. 페어링 단추 (배터리 아래쪽의 탭)를 길게 누릅니다.
5. 페어링 단추를 누른 상태에서 Windows 단추를 5 초 동안 누르고 있으면 컨트롤러의 전원을 켭니다 (두 단추를 모두 누른 상태 유지).
6. 단추를 해제 하 고 컨트롤러의 전원이 켜 지는 때까지 기다립니다. 이 작업에는 최대 15 초가 걸리며, 장치 복구가 발생 하는 경우에는 지표가 표시 되지 않습니다. 장치가 단추 릴리스부터 즉시 켜지 면 복구 단추 시퀀스가 등록 되지 않아 다시 시도해 야 합니다.
7. **설정 > bluetooth > 기타 장치** 로 이동 하 고 "동작 컨트롤러-왼쪽" 또는 "동작 컨트롤러-오른쪽" 및 "장치 제거"를 선택 하 여 bluetooth 설정에서 이전 컨트롤러 연결을 제거 합니다. 
8. 컨트롤러와 PC를 다시 페어링 합니다.
9. 호스트 및 HMD에 연결한 후 장치는 사용 가능한 최신 펌웨어로 업데이트 됩니다.

### <a name="lights-and-indicators"></a>조명 및 표시기

LED constellation 링 및 haptics은 동작 컨트롤러의 상태를 표시 합니다.

| 시스템 상태    | 상태를 발생 시키는 원인 | 상태와 연결 된 광원 및 진동 동작 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **전원 켜기**               | 컨트롤러를 켜려면 2 초 동안 컨트롤러에서 Windows 단추를 길게 누릅니다.       | Led는를 켜고 컨트롤러를 한 번 vibrates 합니다. |
| **전원 끄기**              | 컨트롤러를 해제 하려면 컨트롤러의 Windows 단추를 4 초 동안 길게 누릅니다.      | Led가 해제 되 고 컨트롤러가 두 번 vibrates. |
| **중지 중**               | 컨트롤러는 30 초 동안 중지 된 상태로 자동으로 전환 됩니다. 컨트롤러가 호스트 PC와 연결 되지 않은 경우를 제외 하 고는 동작이 감지 되 면 자동으로 절전 모드가 해제 됩니다. 이 경우 절전 모드를 해제 하는 데 단추 누르기를 수행 해야 합니다. | Led는 절전 상태에서 3 초 마다 해제 되 고 깜박거립니다. |
| **Pin**                | 배터리 케이스 내에서 3 초 동안 페어링 단추를 길게 누릅니다.     | 는 페어링 모드에서 서서히 펄스를 발생 하 고 연결 모드를 종료할 때 solid로 이동 합니다. 페어링이 성공 하면 컨트롤러는 한 번 vibrates, 연결이 실패 하 고 시간이 초과 되는 경우에는 3 번입니다. |
| **PC에서 컨트롤러 연결/연결 끊기** | 컨트롤러를 켠 후에 PC에 성공적으로 연결 하거나, 어떤 이유로 사용 하는 동안 컨트롤러가 PC에서 연결을 끊습니다.| 컨트롤러는 PC 연결 또는 연결 끊김에서 한 번 vibrates. |
| **배터리 부족 수준**      | 배터리 레벨이 낮습니다.| 배터리가 부족할 때 LED 또는 진동 표시가 없습니다. 헤드셋의 컨트롤러 표시 핸들에는 배터리 표시기 아이콘이 있습니다. 배터리가 적으면 표시기 아이콘에 1/4 전체가 표시 됩니다. |
| **배터리 위험 수준** | 전원 켜기 중 배터리 수준이 "위험" 인 경우 "위험" 배터리 수준은 전원이 충분 하지 않으며 컨트롤러는 자동으로 꺼집니다.| 컨트롤러를 켜면 세 번 vibrates 자동으로 꺼집니다. 이 상태를 사용 하는 경우 배터리 표시기 아이콘이 빨강으로 표시 됩니다. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Bluetooth 기술을 사용 하 고 있는지 어떻게 알 수 있나요?

동작 컨트롤러는 많은 소비자 장치에서 발견 된 것과 동일한 Bluetooth 기술을 사용 하며, 최근 PC에 포함 된 Bluetooth 기능을 사용할 수 있도록 설계 되었습니다. PC에 Bluetooth 라디오가 있는지 확인 하려면 (장치에서 혼합 현실 호환성 검사를 통과 한 경우): 
* Windows 시작 메뉴를 마우스 오른쪽 단추로 클릭 하 고 "Device Manager"를 선택 합니다. 
* Bluetooth 섹션을 확장 하 고 어댑터를 찾습니다. 
* PC에 Bluetooth가 없는 경우 하나의 권장 동글이 [PLUGABLE USB Bluetooth 4.0 저 에너지 마이크로 어댑터](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)입니다.
![Device Manager 예의 스크린샷 어댑터는 Bluetooth 송수신 장치입니다.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>PC에 Bluetooth 기술이 있지만 내 동작 컨트롤러에 문제가 있습니다.

동작 컨트롤러는 다른 Bluetooth 키보드, 마우스 및 게임 컨트롤러에서 작동 해야 하지만 사용 하는 키보드, 마우스 또는 게임 컨트롤러의 모델에 따라 환경이 달라 집니다. 성능을 향상 시키기 위해 수행할 수 있는 몇 가지 작업은 다음과 같습니다.
* 컴퓨터에 Bluetooth가 있지만 여전히 동작 컨트롤러에 문제가 있는 경우 Bluetooth 라디오를 USB에 연결 된 Plugable 외부 Bluetooth 어댑터로 교체 하는 것이 좋습니다. Bluetooth 라디오 어댑터는 한 번에 하나만 활성 상태로 만들 수 있습니다. 기존 라디오 외에 외부 라디오를 연결 하는 경우에는 Device Manager에서 기존 Bluetooth 라디오를 사용 하지 않도록 설정 해야 합니다 (어댑터를 마우스 오른쪽 단추로 클릭 하 고 "장치 사용 안 함"을 선택).
* USB Bluetooth 어댑터를 사용 하는 경우 USB 2.0 포트에 연결 합니다 (2.0 포트는 검정색 이며 "SS"로 레이블이 지정 되지 않음) (사용 가능한 경우). 포트는 다음과 같이 물리적으로 분리 되어야 합니다.
    - HMD USB 커넥터
    - 플래시 드라이브
    - 하드 드라이브
    - 키보드/마우스에 대 한 것과 같은 무선 USB 수신기는 USB Bluetooth 어댑터를 이러한 다른 커넥터에서 가능 하면 컴퓨터의 반대쪽에 연결 합니다.
* 타사 소프트웨어를 설치 하지 마십시오.
* Bluetooth 설정 창이 열려 있으면 닫습니다. 백그라운드에서 열린 상태로 두면 Bluetooth 프로토콜에 대 한 많은 추가 호출이 수행 됩니다.
* Bluetooth & 다른 장치에서 "Swift Pair를 사용 하 여 연결 하는 알림 표시" 설정을 사용 하지 않도록 설정 하 여 호스트 라디오 검색 작업을 줄입니다.
* 내부 Bluetooth 카드를 사용 하는 경우 외부 Bluetooth 안테나를 사용 하 고 있는지 확인 하세요. 
  * 이 경우 외부 Bluetooth 안테나가 부족 하 여 추적 문제가 발생 하는 것으로 알려져 있습니다. 
  * 작동 하지 않는 경우 내부 Bluetooth를 사용 하지 않도록 설정한 후 외부 Bluetooth 동글을 사용 하세요.
* 장치가 Bluetooth 설정의 "마우스, 키보드 & 펜" 범주 아래에 표시 되는 것이 중요 합니다. "기타 장치" 아래에 있는 경우 연결 해제 하 고 장치를 페어링 합니다.
* Bluetooth 헤드폰 및 스피커를 제거, 페어링 및 해제 합니다. 이러한 기능은 Windows Mixed Reality에서 지원 되지 않습니다. 최상의 오디오 환경을 위해 혼합 현실 헤드셋에서 헤드폰 잭 또는 기본 제공 스피커를 사용할 수 있습니다.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>기본 제공 블루투스 라디오를 사용 하 여 이동 컨트롤러를 Windows Mixed Reality 헤드셋에 연결 하거나 공장 페어링에 반환 하려면 어떻게 해야 하나요?

Acer OJO 500 및 Samsung Odyssey +를 비롯 한 일부 Windows Mixed Reality 헤드셋에는 동작 컨트롤러에서 사용할 수 있는 Bluetooth 송수신 장치를 기본 제공 합니다. 이러한 헤드셋과 함께 제공 되는 동작 컨트롤러는 팩터리의 헤드셋에 미리 페어링 되며 PC에 별도의 Bluetooth 라디오가 필요 하지 않습니다. 이러한 동작 컨트롤러를 PC의 Bluetooth 송수신 장치에 수동으로 연결할 수 있습니다. 예를 들어 Windows Mixed Reality 헤드셋과 함께 사용 하 여 기본 제공 되는 Bluetooth 라디오를 사용 하지 않을 _수 있습니다_ . 동작 컨트롤러를 공장 페어링으로 반환 하거나 기본 제공 블루투스 라디오를 사용 하 여 Windows Mixed Reality 헤드셋과 페어링 하려면 헤드셋의 장치 도우미 앱 (예: "Acer OJO 500" 앱 또는 "Samsung HMD Odyssey + Setup" 앱)을 실행 하 고, 헤드셋이 처음 연결 될 때 자동으로 설치 되 고, 동작 컨트롤러 페어링에 대 한 지침을 따르세요.


## <a name="performance-questions"></a>성능 질문

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>Windows Mixed Reality 헤드셋이 60Hz 또는 90Hz 프레임 속도에서 렌더링 되는지 어떻게 알 수 있나요?

**장치 포털 > 성능** 탭을 선택 합니다. 

**참고** : HDMI 2.0 포트와 4 개 이상의 실제 코어가 있는 CPU가 있는 불연속 GPU를 사용 하는 경우에는 90 Hz를 가져와야 합니다. GPU에 HDMI 1.4 출력만 있는 경우 DisplayPort를 사용 [2.0](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) 하 여 문제를 해결할 수 있습니다. 

**참고** : **시각적 품질 설정 > 헤드셋 디스플레이** 는 Windows Mixed Reality 홈 환경의 렌더링에만 영향을 줍니다.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>PC가 느리게 실행 되는 것으로 나타나는 경우 어떻게 해야 하나요?

시스템은 여러 가지 이유로 인해 느려지거나 대부분의 경우 몇 초 후에 감소 됩니다. 오랜 기간 동안이 문제가 발생 하는 경우:
1. 바탕 화면에서 사용 하지 않는 응용 프로그램을 모두 닫습니다.
2. 랩톱이 전원에 연결 되어 있는지 확인 합니다.
3. PC가 준비 중이 아닌지 확인 합니다.
4. Windows Mixed Reality 홈의 시각적 품질을 낮춥니다.
5. PC에 최신 그래픽 드라이버가 있는지 확인 합니다 (그래픽 드라이버 섹션 참조).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>혼합 현실 환경을 실행할 때 PC가 준비 중입니다. 어떻게 할까요? 멋진 가요?

1. 배터리가 청구 되 고 전원 공급 장치가 연결 되어 있는지 확인 합니다.
2. PC에 대 한 공기를 차단 하는 팬이 차단 되지 않았는지 확인 합니다.
3. 비교적 쿨 환경에서 PC를 사용 합니다.
4. PC를 가리키는 열 원본 (예: sun 또는 열 통풍구)이 없는지 확인 합니다.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>시각적 개체는 고르지 않거나, 느리게 로드 되거나, 좋지 않습니다.
* 헤드셋이 PC의 올바른 그래픽 카드에 꽂혀 있는지 확인 합니다. 일부 Pc에는 통합 및 분리 된 그래픽 카드가 모두 있습니다. 일반적으로 불연속 카드는 최상의 성능을 제공 합니다. [PC 하드웨어에 대해 자세히 알아보세요](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* 바탕 화면에서 사용 하지 않는 응용 프로그램을 닫습니다.
* 헤드셋이 snugly에 맞게 조정 되었는지 확인 합니다 (조정 하려면 더 낮거나 왼쪽 및 오른쪽으로 이동).
* **설정 > 혼합 현실 > 헤드셋 디스플레이** 에서 헤드셋의 시각적 설정을 조정 합니다. "시각적 품질"을 "자동"으로 설정 하면 PC에 대해 가장 잘 혼합 된 현실 환경을 선택 하 게 됩니다. 시각적 효과에 대 한 자세한 내용은 "시각적 품질"을 "높음"으로 설정 합니다. 시각적 개체가 고르지 않으면 낮은 설정을 선택 하는 것이 좋습니다.
* 헤드셋의 보정을 조정해 보세요. Lenses는 pupils 사이의 거리로 IPD (interpupillary distance)와 일치 하도록 조정 해야 합니다. IPD를 모르는 경우 optometrist는이를 측정할 수 있어야 합니다. IPD을 측정 하도록 디자인 된 웹 사이트도 있습니다. IPD을 확인 한 후에는 헤드셋의 보정 노브를 사용 하 여 조정을 수행 합니다. 헤드셋에 보정 노브가 없는 경우 **설정 > 혼합 현실 > 헤드셋 표시** 를 선택 하 고 "보정 제어"를 조정 합니다.


## <a name="tracking-system-problems"></a>시스템 문제 추적

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>시스템이 경계를 찾을 수 없으며 설치 UI가 표시 됩니다.

즉, 추적 시스템에서 사용자 환경을 인식할 수 없습니다. 새 환경에 있는 경우 [경계](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)를 설정 해야 합니다. 이전에이 환경에서 장치를 사용 하 고 경계를 설정한 경우:
* 대화방에 충분 한 조명이 있는지 확인 합니다.
* 장치를 마모 하 고 공간을 확인 해야 합니다. 장치에서 사용자 환경을 관찰 하 여 어디 인지 확인 해야 합니다. 책상 이나 테이블에 있는 경우에는 범위를 찾지 못합니다.
* 장치를 분리 하 고, Windows Mixed Reality를 닫고, 장치를 다시 연결 합니다.
* 환경에서 변경 된 내용이 있으며 장치에서 더 이상 인식 하지 못할 수 있습니다. 새 경계를 설정 해 보세요.

이러한 단계를 수행 해도 문제가 해결 되지 않으면 환경 데이터를 삭제 하 고 경계를 다시 설정 합니다.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>시스템에는 모든 환경에 대 한 설치를 선택 하도록 요청 하는 UI와 함께 표시 되 고 내 경계를 표시 합니다.

장치에서 범위를 찾는 데 시간이 너무 오래 걸립니다. 경계를 사용 하는 옵션을 선택 하 여이 메시지를 무시할 수 있으며, 범위가 있는 Windows Mixed Reality 홈으로 이동 됩니다.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>"내 경계를 잃어 버렸습니다." 라는 메시지가 자주 표시 됩니다.

추적 시스템은 하드 시간을 추적 하 고 환경을 식별 합니다. 이 상태에서 장치는 더 이상 범위를 표시할 수 없으며 헤드셋은 이상으로 전환 하 여 범위를 다시 찾을 때까지 실제 환경에 bumping 수 있습니다. 이 문제를 해결하려면
1. 대화방에 충분 한 조명이 있는지 확인 합니다.
2. 최근 다시 데코 레이트 하거나 리 모델링 하는 경우 설치 프로그램을 다시 실행 합니다.
3. 장치를 분리 하 고 Windows Mixed Reality를 닫은 다음 다시 연결 합니다.
4. 환경 데이터를 지우고 장치를 다시 설정 합니다.
5. 메시지가 계속 발생 하면 고객 지원에 문의 하세요.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>이를 살펴볼 수는 있지만 번역할 수 없습니다.

즉, 추적 시스템에서 포즈를 생성할 수 없거나 응용 프로그램에서 새 포즈 데이터를 사용 하 여 렌더링할 수 없습니다. 다음 사항을 확인합니다.
* 대화방에 충분 한 조명이 있는지 확인 합니다.
* 공간에 추적할 충분 한 세부 정보가 있는지 확인 합니다.
* 장치를 분리 하 고, Windows Mixed Reality를 닫고, 장치를 다시 연결 합니다.
* 메시지가 계속 발생 하면 고객 지원 서비스에 문의 하십시오.

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>HMD의 뷰는 완전히 고정 되어 있습니다.

이는 일반적으로 응용 프로그램 또는 시스템 수준 구성 요소가 실패 했음을 의미 합니다. 다음을 시도 합니다.
1. "홈" 단추를 눌러 응용 프로그램을 종료 합니다.
2. 장치를 분리 하 고 MRP를 닫은 후 장치를 다시 연결 합니다.
3. PC를 다시 부팅 합니다.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>HMD 뷰의 가장자리 주위에 검정색 테두리가 자주 표시 됩니다. 경우에 따라 터널을 조회 하는 것 처럼 보입니다.

이는 응용 프로그램이 PC에서 프레임 속도로 적중 할 수 없고 시스템에서 이전 프레임을 사용 하 여 HMD에서 뷰를 렌더링 하는 것을 의미 합니다. 응용 프로그램은 원하는 전 세계 부분만 렌더링 하므로 프레임 속도에 지속적으로 도달 하지 않으면 시스템은 이전 관점에서 계속 해 서이를 렌더링 하려고 시도 하 고 누락 된 세부 정보를 검정으로 채웁니다. 자주 발생 하는 경우:
1. 모든 불필요 한 프로그램을 닫거나 종료 하 여 메모리와 CPU를 확보 합니다.
2. 응용 프로그램에서 세부 설정을 줄입니다.
3. Windows Mixed Reality 설정에서 세부 정보 설정을 줄입니다.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>HMD 뷰는 jittering 및 일지입니다.

이는 여러 가지 이유로 발생할 수 있습니다. 주된 원인은 시스템이 헤드셋에 콘텐츠를 렌더링 하지 못하거나 추적 시스템에 문제가 발생 한 것입니다. 다음 사항을 확인합니다.
1. PC가 리소스 경합 상태에 있지 않은지 확인 합니다. 작업 관리자를 열고 계산 리소스가 사용 가능한 지 확인 합니다 (예: 80% CPU free, 400MB ram 및 디스크 IO는 80% 미만).
2. 하드웨어에 대 한 최신 그래픽 드라이버가 있는지 확인 합니다. 자세한 내용은 그래픽 드라이버 섹션을 참조 하세요.
3. 대화방에 충분 한 조명이 있는지 확인 합니다.
4. 장치를 분리 하 고, Windows Mixed Reality를 닫고, 장치를 다시 연결 합니다.
5. PC를 다시 부팅합니다.
6. 문제가 지속 되 면 고객 지원에 문의 하세요.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>전 세계에서 잠깐 돌아가서 정상적으로 반환 하기 전에 거꾸로 또는 대칭 이동 합니다.

이는 응용 프로그램 또는 시스템 수준 구성 요소에서 오류가 발생 하거나 일시적으로 메모리 나 CPU 리소스가 부족 한 경우에 발생할 수 있습니다. 다음 사항을 확인합니다.
1. "작업 관리자"를 열고 최소 20%의 CPU 사용 가능 및 400MB의 메모리가 사용 가능한 지 확인 합니다 (예: 80% CPU free, 400MB, ram 및 디스크 IO는 80% 미만).
2. "이벤트 뷰어"를 열고 **Windows 로그 > 응용 프로그램 및** 중지 시간에 대 한 오류 이벤트 항목으로 이동 합니다. 프로세스가 충돌 하는지 확인 하십시오.
3. 이 문제가 지속 되 면 PC를 다시 부팅 합니다.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>일시적으로 대칭 이동 하 여 정상으로 전환 되었습니다.

일반적으로이 오류는 추적 알고리즘에 알리기 위해 헤드셋에서 센서 데이터를 가져오는 동안 발생 합니다. 자주 발생 하는 경우:
1. 다른 USB 3.0 포트에 헤드셋을 연결 합니다.
2. USB 3.0 허브가 아닌 PC에 직접 헤드셋을 연결 합니다.
3. 문제가 지속 되 면 고객 지원에 문의 하세요.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>세계는 기울어짐 이지만 Windows Mixed Reality에서 탐색 하 고 살펴볼 수 있습니다.

이 문제는 일반적으로 PC에 저장 된 환경 데이터에 센서 데이터 오류가 기록 되기 때문에 발생 합니다. 이로 인해 Windows Mixed Reality가 기울임으로 표시 되는 경우도 있습니다. 다음을 시도해 보세요.
1. HMD를 분리 하 고, Windows Mixed Reality를 닫고, 헤드셋을 다시 연결 합니다.
2. PC를 다시 부팅 합니다.
3. 환경 데이터를 지웁니다.

## <a name="webvr-questions"></a>WebVR 질문

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Edge에서 VR 콘텐츠를 볼 때 컨트롤러가 표시 되지 않는 이유는 무엇 인가요?

모든 WebVR 내용이 동작 컨트롤러를 지원 하도록 작성 된 것은 아닙니다. WebVR를 사용 하면 콘텐츠 개발자가 게임 컨트롤러나 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다. 사이트에 컨트롤러가 표시 되지 않으면 동작 컨트롤러를 지원 하지 않는 것일 가능성이 높습니다.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>몰입 형 WebVR 뷰에서 마우스를 사용할 수 없는 이유는 무엇입니까?

이는 WebVR 사양의 선택적 기능입니다. 모든 브라우저에서이 기능을 지원 하지는 않지만 마우스 입력을 지원 하도록 모든 WebVR 콘텐츠를 작성 하는 것은 아닙니다. WebVR를 사용 하면 콘텐츠 개발자가 마우스, 키보드, 게임 컨트롤러 또는 동작 컨트롤러와 같은 다양 한 유형의 입력을 지원할 수 있습니다. 마우스 입력 동작은 브라우저 마다 다릅니다. Microsoft Edge 내에서 웹 사이트 작성자는 마우스 입력이 작동 하기 위해 헤드셋에 프레젠테이션할 때 ' pointerlock '를 사용 하도록 해야 합니다.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>컨트롤러가 어디에 나 이상한 방향이 있거나 단추가 잘못 매핑되어 있는 이유는 무엇 인가요?

웹 사이트에 전체 동작 컨트롤러 지원이 없을 가능성이 높습니다.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>VR의 Edge에서 Youtube/Facebook/Vimeo/가디언/뉴욕 시간 등에서 360도 비디오를 볼 수 없는 이유는 무엇 인가요?

다른 웹 사양 또는 표준과 마찬가지로 작성자는이를 구현 하도록 선택할 수 있습니다. 웹 사이트가 브라우저에서 직접 VR 환경을 시작 하 고 이러한 웹 사이트의 작성자가 현재이 사양을 구현 하지 않은 WebVR 사양이 있습니다. 이러한 공급 업체의 VR 콘텐츠를 볼 수 있는 일부 플랫폼에서 다운로드 가능한 앱이 있을 수 있습니다.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Firefox 또는 Chrome에서 VR를 입력할 수 없는 이유는 무엇입니까?

WebVR는 현재 Edge의 Windows Mixed Reality 장치 에서만 지원 됩니다.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>웹 사이트에서 VR를 입력 하는 경우 헤드셋에 빈 화면이 표시 되는 이유는 무엇 인가요?

웹 사이트에서 다중 GPU 컴퓨터 (하이브리드 GPU 랩톱 포함)에 대 한 지원을 구현 하지 않았을 수 있습니다. 다음을 시도 합니다.
* 페이지를 다시 로드합니다.
* 데스크톱 컴퓨터에서 Microsoft Edge를 표시 하는 모니터와 동일한 그래픽 어댑터에 헤드셋을 연결 합니다. 통합 그래픽 어댑터가 아닌 더 높은 전원이 켜진 그래픽 카드에 모두 연결 합니다.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Edge에서 비디오를 시청할 때 VR를 끝내 면 소리는 계속 재생 되지만 가장자리 창은 회색으로 표시 됩니다.

혼합 현실 cliffhouse의 Edge에서 WebVR를 실행 하는 경우 알려진 문제입니다. 이 문제를 해결 하려면 windows 단추를 누르지 않고 키보드에서 esc 키를 눌러 WebVR 환경을 종료 하거나 선택 하 여 회색으로 표시 된 가장자리 창을 활성화 한 다음 비디오를 중지 합니다.

### <a name="can-i-use-webvr-on-the-hololens"></a>HoloLens에서 WebVR을 사용할 수 있나요?

Microsoft는이 시점에서 HoloLens WebVR에 대 한 어떠한 정보도 발표 하지 않았습니다.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Edge에서 WebVR 콘텐츠를 볼 때 평면도가 바닥에 표시 되는 이유는 무엇 인가요?

웹 사이트에서 Windows Mixed Reality 헤드셋을 제대로 지원 하지 않습니다. 이 문제의 해결 방법:
1. 헤드셋을 공간 바닥에 놓습니다.
2. 바탕 화면에서 Microsoft Edge를 사용 하 여 WebVR 페이지로 이동 합니다 (혼합 현실에 있지 않음).
3. 웹 페이지의 단추를 클릭 하 여 VR을 입력 합니다.
4. 환경이 몰입 형 모드로 완전히 전환 될 때까지 5-10 초 정도 기다립니다.
5. 헤드셋을 선택 하 여 헤드에 넣습니다.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>일부 WebVR 환경에서는 디스플레이가 매우 낮은 해상도입니다.

Websites에서 고해상도 헤드셋을 제대로 지원 하지 않습니다. 이 문제를 해결 하려면 다음을 수행 하십시오.
* 혼합 현실 cliffhouse이 아닌 데스크톱에서 WebVR를 시작 하는 경우에는 VR를 입력 하기 전에 창이 최대화 되어 있는지 확인 합니다.
* VR를 입력 한 후에 Microsoft Edge 창의 크기를 조정 하지 마십시오.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>브라우저 탭을 변경할 때 WebVR 몰입 보기가 종료 되는 이유는 무엇 인가요?

이는 정상적인 동작입니다. 보안상의 이유로 활성 브라우저 탭만 연결 된 헤드셋에 액세스할 수 있습니다.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>특정 WebVR 환경에서 오디오를 듣지 못한 이유는 무엇 인가요?

이 웹 사이트는 Microsoft Edge에서 현재 지원 하지 않는 OGG 오디오 파일 형식을 사용 하 고 있을 수 있습니다.

[문제 추적기](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)에서 또는 [#EdgeBug 해시 태그](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)를 사용 하 여 Twitter를 통해 Microsoft Edge 브라우저 팀에 직접 끊어진 사이트를 보고할 수 있습니다.

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>햅 피드백이 동작 컨트롤러가 있는 WebVR에서 작동 하지 않는 이유는 무엇 인가요?

Microsoft Edge는 현재 WebVR 게임 프로그램 API 확장에 대 한 haptics을 지원 하지 않습니다.


## <a name="steamvr-questions"></a>SteamVR 질문

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality 몰입 형 헤드셋에서 SteamVR 게임을 재생 하려면 어떻게 해야 하나요?

PC에 SteamVR에 대 한 Windows Mixed Reality를 설치 하 고 SteamVR를 설정 해야 합니다.
* [SteamVR를 다운로드 하 여 설치](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)합니다.
* SteamVR을 시작 합니다. SteamVR 자습서가 자동으로 시작 됩니다.
* 헤드셋을 PC에 연결 하 고 동작 컨트롤러를 켭니다.
* Windows Mixed Reality 홈이 로드 되 고 컨트롤러가 표시 되 면 바탕 화면에서 스트림 앱을 엽니다.
* 스트림 앱을 사용 하 여 스트림 라이브러리에서 SteamVR 게임을 시작 합니다. 헤드셋을 사용 하지 않고 SteamVR 게임을 시작 하려면 Windows Mixed Reality의 **시작 > 모든 앱** 에서 검색 하 여 시작할 수 있습니다. 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>"Windows Mixed Reality에서 SteamVR를 사용 하려면 최신 Windows 업데이트" 또는 "Windows 개발자 모드 필요"를 설치 해야 한다는 메시지가 표시 됩니다.

1. PC에서 최신 버전의 Windows 10을 실행 하 고 있는지 확인 합니다. 이를 확인 하려면 **설정 > 시스템 > 정보** 로 이동 합니다. "Windows 사양"에서 "OS 빌드"가 16299.64 이상 인지 확인 합니다.
2. 다운로드 또는 설치를 기다리는 업데이트가 없는지 확인 합니다. **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 "업데이트 확인"을 선택 합니다. 업데이트를 여러 번 확인 하 여 더 이상 업데이트를 사용할 수 없을 때까지 업데이트를 확인 하 고 PC를 다시 시작 해야 할 수 있습니다.

### <a name="steamvr-is-crashing-after-updating-windows"></a>Windows를 업데이트 한 후 SteamVR가 충돌 합니다.

SteamVR에 대 한 Windows Mixed Reality의 일부 이전 버전은 Windows와 더 이상 호환 되지 않습니다. SteamVR에 대 한 이전 버전의 Windows Mixed Reality가 있을 수 있습니다. 최신 상태를 유지 하려면 다음을 수행 합니다.
1. 스트림 library에서 **Software > SteamVR에 대 한 Windows Mixed Reality** 로 이동 합니다.
2. 마우스 오른쪽 단추로 클릭 하 고 "속성"으로 이동 합니다.
3. "업데이트" 탭을 선택 하 고 "항상이 응용 프로그램을 최신 상태로 유지"를 선택 합니다.
4. "로컬 파일" 탭으로 이동 하 고 "응용 프로그램 파일의 무결성 확인"을 선택 하 여 업데이트를 강제로 적용 합니다.
5. 스트림 및 SteamVR를 다시 시작 합니다.

업데이트 후 SteamVR 계속 충돌 하는 경우 컴퓨터에 SteamVR에 대 한 Windows Mixed Reality를 두 번 설치 했을 수 있습니다. 이 경우를 확인 하려면 다음을 수행 합니다.
1. %Localappdata%\openvr\openvrpaths.vrpath을 찾아서 메모장에서 엽니다.
2. "외부 드라이버" 섹션에서 "MixedRealityVRDriver"에 대 한 여러 항목을 찾습니다. 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 여러 항목이 표시 되는 경우 두 항목의 이전 항목을 제거 합니다. 항목이 하나만 있는 경우에는 줄의 끝에서 더 이상 쉼표를 사용할 수 없습니다. 예를 들면 다음과 같습니다.
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. 파일을 저장하고 닫습니다.
5. 스트림 및 SteamVR를 다시 시작 합니다.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>내 컨트롤러가 SteamVR에서 예상 대로 작동 하지 않습니다.

1. SteamVR를 닫습니다.
2. Mixed Reality 홈으로 돌아가서 컨트롤러가 예상 대로 작동 하는지 확인 합니다.
3. SteamVR 환경을 다시 시작 하 고 컨트롤러를 정상적으로 다시 시작 해야 합니다.
4. 문제가 지속 되는 경우 혼합 현실 범주 아래의 [Windows 피드백 허브](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) 를 사용 하 여 피드백을 파일에 저장 하 고 요약에 SteamVR을 포함 하세요.

다른 게임에서는 동작 컨트롤러를 다르게 사용 합니다. 시작 하는 데 도움이 되는 몇 가지 기본 사항은 다음과 같습니다.
* 스트림 대시보드를 열려면 왼쪽 엄지 스틱을 바로 누릅니다.
* SteamVR 게임을 종료 하 고 Windows Mixed Reality 홈으로 돌아가려면 Windows 단추를 누릅니다. 그런 다음 화면에 표시 되는 혼합 현실 홈 단추를 선택 합니다.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>왼쪽 및 오른쪽 컨트롤러가 SteamVR에서 반대로 바뀝니다.

컨트롤러와 함께 게임을 시작 하 고 왼쪽을 켠 다음 오른쪽으로 설정 합니다.

### <a name="my-games-are-running-slowly"></a>게임이 느리게 실행 되 고 있습니다.

1. PC가 Windows Mixed Reality의 SteamVR 사양을 충족 하는지 확인 합니다.
2. PC가 게임 중인 SteamVR 게임의 사양을 충족 하는지 확인 합니다.
2. 바탕 화면의 혼합 현실 포털에서 "일시 중지"를 선택 하 여 데스크톱 미리 보기를 중지 합니다.
3. 위의 지침에 따라 Windows 10 빌드 16299.64 이상을 실행 하 고 있는지 확인 합니다.
4. PC에 최신 그래픽 드라이버가 있는지 확인 합니다.
5. 작업 관리자를 확인 하 여 PC에서 실행 중이 고 리소스를 사용 하 고 있는 다른 프로세스를 확인 합니다.
6. 스트림가 백그라운드에서 게임을 다운로드 하 고 있는지 확인 합니다. 이렇게 하면 리소스를 사용 하 고 게임을 제대로 실행할 수 없습니다.
7. 표시 되는 창 (예: SteamVR Home)이 없는 작은 앱 클래스에 영향을 주는 알려진 성능 문제가 있습니다. 대다수의 앱은이 범주에 속하지 않으며 향후 업데이트에서 수정할 수 있습니다.

예기치 않은 성능 문제가 계속 발생 하는 경우 Windows 피드백 허브를 사용 하 여 피드백을 보내 주세요. 지침에 따라 [SteamVR 성능 추적을 포함](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)해야 합니다. 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR는 compositor 오류 (예: "Shared IPC Compositor Connect Failed (400)")를 표시 합니다.

헤드셋 및 기본 모니터가 서로 다른 두 비디오 어댑터에 있는 경우 발생할 수 있는 알려진 문제가 있습니다. 모니터를 헤드셋과 동일한 어댑터에 연결 하 고 **설정 앱 > 시스템 > 디스플레이** 에서 모니터가 기본 모니터가 되도록 구성 합니다.

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR 콘텐츠가 잘못 된 장소에 표시 됩니다 (예: 바닥 또는 위 헤드 아래).

사용자의 위치를 다시 설정 합니다. 
1. 왼쪽 컨트롤러의 엄지 스틱을 클릭 하 여 "SteamVR 대시보드"를 표시 합니다.
2. "설정" 단추를 선택 합니다.
3. "꽂혀 있는 위치 다시 설정"을 선택 합니다.

### <a name="my-steam-app-closed-unexpectedly"></a>내 스트림 앱이 예기치 않게 닫혔습니다.

PC 화면을 잠그거나, 헤드셋을 제거 하거나, 사용자를 전환 하거나, PC가 절전 모드로 전환 되는 경우 스트림 앱이 닫힙니다.


## <a name="speech-and-audio-problems"></a>음성 및 오디오 문제

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>헤드셋의 소리를 듣지 못할 수 있거나 사운드가 내 컴퓨터를 통해 재생 되 고 있습니다.

* 모던 헤드셋에 내장 헤드폰이 포함 되지 않은 경우 헤드셋의 오디오 잭에 헤드폰을 연결 해야 합니다. 잭이 헤드셋 센터 또는 lenses 바로 뒤에 위치 하는 경우가 많습니다. 찾을 수 없는 경우 헤드셋 제조업체에 문의 하세요.
* 일부 오디오 헤드셋에는 볼륨을 제어 하기 위한 물리적 단추가 있습니다. 오디오가 작동 하지 않는 경우 볼륨이 작동 중지 되었는지 아니면 음소거 상태 인지 확인 합니다.
* Windows Mixed Reality는 혼합 현실 포털이 실행 중이 고 헤드폰이 연결 된 경우 몰입 형 헤드셋을 통해 소리를 재생 하도록 설계 되었습니다. 헤드셋을 끄거나 대칭 이동 하거나, 혼합 현실 포털 응용 프로그램을 닫거나, 해당 앱이 15 분 동안 사용 되지 않은 경우 오디오가 기본 Windows 재생 장치로 전환 됩니다. **설정 > 혼합 현실 > 오디오 및 음성** 에서이 설정을 변경할 수 있습니다.
* 오디오 헤드셋이 오디오 잭에 완전히 연결 되어 있는지 확인 합니다. 특히 Acer 헤드셋은 오디오 헤드셋이 모든 방식으로 연결 되었는지 확인 하는 데 더 많은 주의가 필요할 수 있습니다.
* 오디오 헤드셋/마이크가 PC가 아닌 헤드셋에 꽂혀 있는지 확인 합니다.
* Windows 사운드 제어판은 사용 하도록 설정 된 끝점이 아니라 사용 하도록 설정 된 오디오 끝점만 표시 합니다. 헤드셋을 입고 있지 않으면 헤드셋 오디오 장치를 사용할 수 없게 됩니다. 따라서 사운드 제어판을 마우스 오른쪽 단추로 클릭 하 고 "사용 하지 않도록 설정 된 장치 표시"를 선택 하 여 확인 해야 합니다. 장치 이름은 "Realtek USB 2.0 오디오"입니다. 이렇게 하면 "속성" 페이지의 이름을 더 쉽게 인식할 수 있는 항목으로 변경할 수 있습니다. 재생 및 기록 탭 모두에 대해이 작업을 수행할 수 있습니다.
* 오디오가 혼합 현실 앱에서 작동 하지 않는 경우 (예: Netflix) Windows Mixed Reality가 OS 버전과 일치 하도록 자동으로 업데이트 되지 않는 알려진 문제가 원인일 수 있습니다. 이 문제를 해결 하 고 가장 혼합 된 현실 경험을 얻으려면 **설정 > 업데이트 & 보안 > Windows 업데이트 > 업데이트 확인** 으로 이동 합니다.

**참고:** Windows Mixed Reality 공간 오디오는에 기본 제공 되거나 몰입 형 헤드셋에 직접 연결 된 헤드폰에서 가장 잘 작동 합니다. PC에 연결 된 PC 스피커 또는 헤드폰이 공간 오디오에서 제대로 작동 하지 않을 수 있습니다.

**참고:** Windows Mixed Reality는 Bluetooth 오디오 헤드셋을 지원 하지 않습니다.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>갑작스러운 볼륨 변경, 오디오 분실 또는 고주파음이 발생 합니다.

* SteamVR를 통해 시작 되는 대부분의 응용 프로그램은 혼합 현실 포털을 시작 하거나 중지할 때 오디오 장치가 변경 될 때 오디오 또는 중단이 손실 될 수 있습니다. 이를 해결 하려면 Mixed Reality 포털 앱을 연 후 앱을 다시 시작 합니다.
* 다른 멀티미디어 USB 장치 (예: 웹 cam)가 Windows Mixed Reality 헤드셋과 동일한 내부 또는 외부 USB 허브를 공유 하는 경우 헤드셋의 오디오 잭/헤드폰에는 때때로 소리가 나 오디오가 없을 수 있습니다. 다른 허브를 사용 하는 USB 포트에 헤드셋을 꽂거나 다른 USB 멀티미디어 장치를 분리/사용 하지 않도록 설정 합니다.
* 헤드셋에 연결 된 헤드폰에서 큰 양의 소음이 발생 하는 경우 PC의 USB 허브가 Windows Mixed Reality 헤드셋에 충분 한 전원을 제공 하지 못할 수 있습니다. 이 경우 [피드백 허브](https://docs.microsoft.com/hololens/hololens-feedback) 버그를 즉시 파일로 작성 합니다. 확장 케이블을 사용 하지 않거나, 전용 외부 USB 3.0 허브를 사용 하거나, PC에서 다른 USB 포트를 사용해 서는 안 되는 해결 방법입니다.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Bluetooth 오디오 헤드셋이 예상 대로 작동 하지 않습니다.

Microsoft는 Windows Mixed Reality에서 Bluetooth 오디오 헤드셋을 사용 하지 않는 것이 좋습니다. Bluetooth 오디오 주변 장치는 Windows Mixed Reality 음성 및 공간 음향 환경에서 제대로 작동 하지 않으며, Bluetooth 오디오 헤드셋은 마이크 입력 및 스테레오 출력을 동시에 지원 하지 않으므로 gamechat 또는 기타 음성 입력에 사용할 때 스테레오 또는 spatialized 소리가 들리지 않습니다. 또한 Bluetooth 오디오 헤드셋은 동작 컨트롤러 환경에 부정적인 영향을 줄 수 있습니다. 

### <a name="sound-isnt-coming-from-expected-directions"></a>소리는 예상 되는 방향이 아닙니다.

Windows Mixed Reality 홈에는 공간 소리 (홈에 있는 앱에서와 같이 소리를 들면 오디오)가 포함 됩니다. 각 앱에서 가까이 나 더 가깝게 이동 하는 경우에는 현실감의 의미에 맞게 소리 방향 및 수준이 변경 됩니다. 다음은 예기치 않은 소리 방향에 대 한 몇 가지 이유입니다. 
* 홈의 배경 지원 음악 앱 (예: 그루브 음악)에서 음악을 열고 재생 한 다음 몰입 형 VR 환경 (예: 게임)을 열면 음악 앱의 사운드가 공간 사운드에서 스테레오로의 영향을 받습니다. 사용자와 소리 사이에 더 이상 거리가 없으므로 이전 보다 크게 보일 수 있습니다.
* Windows Mixed Reality 헤드셋을 사용 하기 전에 호스트 PC에서 Cortana를 사용 하도록 설정한 경우 Windows Mixed Reality 홈의 앱에 적용 되는 공간 사운드가 손실 될 수 있습니다. 이 문제를 해결 하려면 windows Mixed reality를 시작 하기 전에 바탕 화면에서 cortana에 게 "cortana에 응답 해 주세요. **>** "를 해제 하거나 Windows mixed reality 홈의 데스크톱 앱 창에서 "헤드폰 용 Windows Sonic"을 사용 하도록 설정 합니다.
    1. 바탕 화면 작업 표시줄에서 스피커 아이콘을 마우스 왼쪽 단추를 클릭 하 고 오디오 장치 목록에서 선택 합니다.
    2. 바탕 화면 작업 표시줄에서 스피커 아이콘을 마우스 오른쪽 단추로 클릭 하 고 "스피커 설정" 메뉴에서 "헤드폰 용 Windows Sonic"을 선택 합니다.
    3. 모든 오디오 장치 (끝점)에 대해이 단계를 반복 합니다.

### <a name="speech-commands-are-not-working-as-expected"></a>음성 명령이 예상 대로 작동 하지 않습니다.

* 음성 명령을 사용 하려면 PC의 음성 및 언어 설정이 [Windows Mixed Reality에서 지원 되는 언어로](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages)설정 되어 있어야 합니다. Windows 음성 및 언어 설정을 확인 하려면 **설정 > 시간 & 언어 > 지역 & 언어** 및 **설정 > 시간 & 언어 > 음성** 을 선택 합니다.
* 헤드셋에 기본 제공 마이크가 없는 경우 헤드셋 또는 PC에 마이크와 헤드폰을 연결 해야 합니다. 사용자가 착용 할 때 헤드셋에 마이크 입력을 자동으로 전환 하려면 **설정 > 혼합 현실 > 오디오 및 음성** 으로 이동 하 고 "헤드셋을 사용 하지 않는 경우 헤드셋 mic로 전환 합니다."로 이동 합니다.
* 일부 오디오 헤드셋은 마이크를 음소거 및 음소거 해제 하는 실제 단추를 포함 합니다. 음성 명령이 작동 하지 않는 경우 마이크가 음소거 되어 있는지 확인 합니다.
* Dangles 마이크를 사용 하는 마이크가 있는 오디오 헤드셋은 주변 노이즈가 있는 환경의 음성 명령에 대해 잘 작동 하지 않습니다.
* Cortana는 혼합 현실 포털 세션에서 처음 호출 될 때 느릴 수 있습니다. **설정 > cortana로 이동 하 > cortana에 게 문의** 하 고 "cortana에 게 응답 합니다."가 사용 하도록 설정 되어 있는지 확인 합니다.
* 일부 Pc에서는 헤드셋 연결 마이크의 기본 음성 캡처 이득이 너무 낮게 설정 되어 있을 수 있습니다. 불안정 한 음성 명령 또는 받아쓰기가 발생 하는 경우 마이크 설정 문제 해결사를 실행 해 볼 수 있습니다. **설정 > 시간 & 언어 > 음성** 을 통해이 문제 해결사에 연결한 다음 "마이크" 섹션에서 "시작 하기"를 선택할 수 있습니다. Windows mixed reality 홈의 데스크톱 앱을 통해이 작업을 수행 하 고, Windows Mixed Reality에 사용 하는 마이크에 영향을 주는 헤드셋을 입고 합니다. 문제 해결사 마법사에서 적절 한 끝점을 선택 합니다.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>하나의 오디오 헤드셋만 있으며 데스크톱 및 내 헤드셋 모두에 사용 하려고 합니다.

오디오 헤드셋이 하나 뿐 이며 내장 헤드폰이 포함 된 헤드셋이 없는 경우 헤드셋 대신 오디오 헤드셋을 호스트 PC에 연결 합니다. 그런 다음 MRP 설정에서 "헤드셋 오디오로 전환"을 해제 합니다.

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>헤드폰에 대 한 돌비 Atmos 전환 하려고 합니다.

Windows Mixed Reality 환경 및 해당 응용 프로그램은 혼합 현실 환경에 맞게 사용자 지정 된 헤드폰 공간 오디오 기술용 Windows Sonic을 사용 합니다. 다른 공간 오디오 기술 (예: 헤드폰 용 돌비 Atmos)은 SteamVR 게임과 같은 전체 화면 응용 프로그램에 적용할 수 있지만, Windows Mixed Reality 셸 환경 및 응용 프로그램 (예: 절벽의 벽에 웹 브라우저 배치 또는)을 사용 하 여 설계 된 헤드폰 공간 사운드 및 acoustics를 사용 하 여 설계 되었습니다.


## <a name="questions-about-desktop-in-mixed-reality"></a>Mixed Reality의 데스크톱에 대 한 질문

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>혼합 현실에서 내 PC 데스크톱에 액세스 어떻게 할까요??
데스크톱 앱을 사용 하 여 혼합 현실에서 PC 데스크톱에 액세스할 수 있습니다. Windows에서 헤드셋 단추를 클릭 하 여 **모든 앱 > 데스크톱 >** 합니다. 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>혼합 현실에서 여러 모니터를 확인 하려면 어떻게 해야 하나요?
기본적으로 데스크톱 앱은 자동으로 전환 하 여 포커스가 있는 모니터를 표시 합니다. 혼합 현실에서 모든 모니터를 보려면 다음을 수행 합니다. 
* 앱의 왼쪽 위 모서리에 있는 모니터 아이콘을 클릭 합니다.
* "모니터 자동 전환" 사용 안 함
* 보려는 모니터를 선택 합니다.
* 데스크톱 응용 프로그램의 다른 인스턴스를 시작 합니다.
* 해당 인스턴스에 대해 보려는 모니터를 선택 합니다. 
* 모든 물리적 모니터를 반복 합니다. 혼합 현실를 다시 시작할 때마다 각 데스크톱 앱에 표시할 모니터를 다시 선택 해야 합니다. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>내 데스크톱 앱에는 검은색 화면만 표시 됩니다.
PC에 Nvidia 하이브리드 GPU가 있는 경우이 문제는 통합 된 GPU가 아닌 개별 GPU에서 runtimebroker.exe를 실행 하는 Nvidia 장치에 의해 발생할 수 있습니다. 이 문제를 해결 하려면[어떻게 할까요? "새 프로그램에 대 한 Optimus 설정 만들기"의](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)지침을 따르세요. C:\windows\system32\runtimebroker.exe 추가 하 고 "통합 그래픽" 프로세서에서 강제로 실행 하도록 합니다. 


## <a name="other-questions"></a>기타 질문

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>내 Samsung Odyssey 또는 Odyssey + 헤드셋 펌웨어 업데이트가 중단 됩니다.

Samsung는 "Samsung HMD Odyssey Setup" 및 "Samsung HMD Odyssey + Setup" 장치 도우미 앱을 통해 제공 되는 헤드셋 펌웨어 업데이트를 소유 하 고 게시 합니다. Samsung 펌웨어 업데이트 문제에 대 한 자세한 내용 및 도움을 보려면 Samsung 고객 서비스에 문의 하세요.

펌웨어 업데이트 프로세스가 중단 되 고 5 분 이상 진행 되지 않은 경우:
* 다른 모든 USB 장치를 일시적으로 분리 하 고 펌웨어 업데이트를 다시 시도 합니다.
* Samsung 헤드셋을 PC의 다른 USB 3.0 포트에 연결 합니다.
* Gb의 AORUS App Center와 같은 펌웨어 업데이트를 방해할 수 있는 설치 된 소프트웨어를 사용 하지 않도록 설정 하거나 제거 합니다.
* 다른 PC를 사용 하 여 Samsung 헤드셋 펌웨어 업데이트를 수행 합니다.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Windows Mixed Reality를 사용 하는 경우 Wi-fi의 속도가 느려집니다.

2.4 g h z Wi-fi 연결을 사용 하는 경우 동작 컨트롤러에서 Wi-fi 속도가 느려질 수 있습니다. 다음 작업 중 하나를 수행하세요.
* 5GHz Wi-fi 연결 (있는 경우)으로 전환 합니다. [자세히 알아보기](https://support.microsoft.com/en-us/help/4000461).
* 별도의 Bluetooth 어댑터를 사용 하 여 이동 컨트롤러를 PC에 연결 합니다. [권장 어댑터](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)를 참조 하세요.

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>PC를 연결 하 고 요금을 청구 하는 메시지를 받았습니다. 그 이유는

노트북을 사용 하는 경우 Windows Mixed Reality는 PC가 완전히 충전 되 고 연결 된 경우에 가장 잘 작동 합니다. 

### <a name="what-is-the-experience-options-setting"></a>환경 옵션 설정은 무엇 인가요?

환경 옵션 설정 ( **설정 > 혼합 현실 > 헤드셋에서 > 환경 옵션 표시** )을 사용 하 여 Windows Mixed reality 성능 설정을 변경할 수 있습니다. 이렇게 하면 다양 한 콘텐츠를 통해 하드웨어 구성에 대 한 최상의 환경을 선택할 수 있습니다. 모든 시스템에서 90Hz 환경을 사용할 수 있지만 원하는 설정을 확인 하기 위해 자동으로 시도할 수 있습니다. 옵션은 다음과 같습니다.
* 자동: Windows Mixed Reality는 하드웨어 구성에 대 한 최상의 환경을 결정 합니다. 대부분의 사용자는이 옵션을 사용 하 여 시작 하는 것이 가장 좋습니다.
* 60Hz: 새로 고침 빈도를 60Hz로 설정 하 고 혼합 현실 포털에서 비디오 캡처 및 미리 보기와 같은 특정 기능을 끕니다.
* 90Hz: 새로 고침 빈도를 90Hz로 설정 합니다.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality에서 지원 되는 언어는 무엇 인가요?

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

Windows Mixed Reality 화면 키보드는 영어 (미국)만 해당 합니다. 텍스트를 다른 언어로 입력 하려면 PC에 연결 된 실제 키보드를 사용 합니다. 위에 나열 된 지원 되는 Windows Mixed Reality 언어 중 하나에서 받아쓰기를 사용할 수도 있습니다. 화면 키보드에서 마이크를 선택 하면 됩니다.

Windows Mixed Reality는 음성 명령 또는 받아쓰기 기능 없이도 다음 언어로 제공 됩니다.

* 중국어 번체 (대만 및 홍콩)
* 네덜란드어(네덜란드)
* 한국어(한국)
* 러시아어(러시아)

### <a name="i-have-questions-about-my-headset-hardware"></a>내 헤드셋 하드웨어에 대 한 질문이 있습니다.

헤드셋에 대 한 자세한 내용은 제조업체에서 확인 하세요. 상자에 제품 가이드가 있거나 제조업체의 웹 사이트를 사용해 볼 수 있습니다.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Windows Mixed Reality를 제거 하는 방법

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Windows Mixed Reality를 제거할 어떻게 할까요? 있나요?

1. PC에서 헤드셋의 연결을 끊습니다.
2. Mixed Reality 포털을 닫습니다.
2. **시작 > 설정 > 혼합 현실** 로 이동 하 고 "제거"를 선택 합니다.

헤드셋을 다시 사용할 준비가 되 면 플러그 인을 시작 하 고 혼합 현실 포털에서 설치를 진행 합니다.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>"Windows Mixed Reality 제거를 완료할 수 없습니다." 라는 메시지가 나타났습니다.

이는 사용자 환경에 대 한 정보를 포함 하 여 일부 파일이 컴퓨터에 남아 있을 수 있음을 의미 합니다. 나중에 Windows Mixed Reality를 다시 설치 하려는 경우 문제가 발생할 수 있습니다. 레지스트리를 수정 하 고 Windows PowerShell을 사용 하 여 명령을 실행 하 여 PC에서 남아 있는 Windows 혼합 현실 정보를 수동으로 제거할 수 있습니다. _레지스트리를 잘못 수정 하면 심각한 문제가 발생할 수 있습니다. 이러한 단계를 신중 하 게 수행 해야 합니다. 추가 된 보호를 위해 수정 하기 전에 레지스트리를 백업 하 여 문제가는 때 복원할 수 있도록 합니다._ 자세한 내용은 [Windows에서 레지스트리를 백업 하 고 다시 작성 하는 방법](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)을 참조 하세요. 

다음 명령을 사용 하 여 Windows mixed reality를 제거 합니다.
1. PC를 다시 시작 합니다.
2. **검색** 상자에 "regedit"를 입력 하 고 **예** 를 선택 합니다.
3. 다음 레지스트리 값을 제거 합니다.
   <ul>
    <li><b>\Software\microsoft\windows\currentversion\holographic을 HKEY_CURRENT_USER</b>한 다음 <b>FirstRunSucceeded</b>를 삭제 합니다.</li> 
    <li><b>\Software\microsoft\windows\currentversion\holographic\speechandaudio를 HKEY_CURRENT_USER</b>하 고 <b>PreferDesktopSpeaker</b> 및 <b>PreferDesktopMic</b>를 삭제 합니다.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b> <b>DisableSpeechInput</b>를 삭제 합니다. 참고: Windows Mixed Reality를 사용 하는 PC의 모든 사용자 계정에 대해 HHKEY_CURRENT_USER의 레지스트리 항목을 삭제 해야 합니다.</li> 
    <li><b>\Software\microsoft\windows\currentversion\perceptionsimulationextensions를 HKEY_LOCAL_MACHINE</b>하 고 <b>DeviceID</b> 및 <b>모드</b>를 삭제 합니다.</li> 
    <li><b>\Software\microsoft\windows\currentversion\holographic을 HKEY_CURRENT_USER</b>한 다음 <b>OnDeviceLearningCompleted</b>를 삭제 합니다.</li> 
   </ul>
4. 다음 레지스트리 키를 제거 합니다. <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. 레지스트리 편집기를 닫습니다.
6.**C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \LocalState** 로 이동한 다음 **에서RoomBounds.js** 을 삭제 합니다. Windows Mixed Reality를 사용 하는 각 사용자에 대해이를 반복 합니다.
7. 관리자 cmd 프롬프트를 열고 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 로 이동 합니다. 그런 다음 **헤드 추적 데이터** 폴더의 콘텐츠를 삭제 합니다 (폴더 자체는 아님).
8.**검색 상자** 에 "powershell"을 입력 하 고 **Windows powershell** 을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 선택 합니다.
9. Windows PowerShell에서 다음을 수행 합니다. <ul>
   <li>명령 프롬프트에서 다음을 복사 하 여 붙여넣고 Enter 키를 누릅니다. <b>Dism/Online/Get-Capabilities</b></li> 
   <li>Holographic로 시작 하는 기능 Id를 복사 합니다. (&#39;해당 항목이 없는 경우이 항목은 설치&#39;되지 않습니다. 이 경우에는 10 단계로 건너뜁니다.</li> 
   <li>다음 명령 프롬프트를 복사 하 여 붙여넣고 Enter 키를 누릅니다. <b>Dism/Online/Remove-Capability/CapabilityName: 마지막 단계에서 복사 된 기능 id</b></li>
   </ul>
10. PC를 다시 시작 합니다.




