---
title: PC 호환성에 대한 도움말 보기
description: Windows Mixed Reality 응용 프로그램 및 장치로 작업할 때 PC 호환성 문제를 해결 하기 위한 리소스를 최신 상태로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 사용자 의견, 피드백 허브, 버그
appliesto:
- Windows 10
ms.openlocfilehash: e3d150544c3bce99d1aa808229d282b3d2fe1dd0
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007483"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Windows Mixed Reality의 PC 호환성에 대 한 도움말 보기

Windows Mixed Reality를 설정 하거나 [Mixed Reality 포털](install-windows-mixed-reality.md)을 사용 하는 경우 PC가 작업에 있는지 여부에 대 한 보고서를 받게 됩니다. 아래 섹션에서 볼 수 있는 내용에 대 한 구체적인 정보를 자세히 설명 했습니다.

좀 더 진행 하기 전에 아래에서 가장 일반적인 수정 사항을 시도해 보세요. 

> [!div class="checklist"]
> * 컴퓨터가 [최소 PC 하드웨어 호환성 요구 사항을](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 충족 하는지 확인 합니다.
> * [그래픽 카드 및 프로세서가](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 호환 되는지 확인 합니다.
> * [권장 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 목록 확인
> * **시작 > 설정 > 업데이트 & 보안 > 업데이트 확인을** 선택 하 여 그래픽 드라이버를 업데이트 합니다. 

연락처를 받으려면 [커뮤니티에 요청](https://answers.microsoft.com)하거나 [지원 담당자](https://support.microsoft.com/contactus/)에 게 문의 하거나 [문제 해결](troubleshooting-windows-mixed-reality.md) 정보를 확인할 수 있습니다.

## <a name="youre-good-to-go"></a>이동 하는 것이 좋습니다.

좋은 소식입니다. **바로 가기** 메시지가 표시 되 면 PC에서 Windows Mixed Reality를 실행할 수 있습니다. 컴퓨터 하드웨어와 구성 사이에 여전히 변형이 있으므로 혼합 현실 환경은 모든 PC에서 동일 하지 않을 수 있습니다.

## <a name="supports-some-features"></a>일부 기능 지원

에서 **일부 기능을 지원** 합니다. 메시지가 표시 되는 경우 PC에서 일부 Windows Mixed Reality 환경을 실행할 수 있지만 가능한 최상의 환경을 제공 하지 못할 수 있습니다. 가능한 단점이에는 지연 그래픽, 성능 적중 횟수, 일부 응용 프로그램 및 게임을 실행할 수 없습니다. 표시 될 수 있는 메시지 및 다음에 대해 수행할 작업을 나열 했습니다.

* [이 PC에는 단일 채널 RAM이 있는 통합 그래픽 카드가 있습니다.](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [이 PC에는 호환 되지 않는 PCIe 링크로 하이브리드 그래픽 구성이 있습니다.](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [이 PC의 프로세서는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [이 PC에는 호환 되는 USB 구성이 없을 수 있습니다.](#this-pc-might-not-have-a-compatible-usb-configuration)
* [이 PC에는 컨트롤러에 대 한 Bluetooth 4.0가 없습니다.](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [헤드셋에 따라 동작 컨트롤러를 사용 하려면 Bluetooth 어댑터가 필요할 수 있습니다.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [이 PC에는 자체 기반 USB 포트가 없습니다.](#this-pc-doesnt-have-a-self-powered-usb-port)
* [이 PC의 그래픽 카드는 Windows Mixed Reality에서 작동 하지 않습니다.](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 작동 하지 않습니다.](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [이 PC의 프로세서는 Windows Mixed Reality에서 작동 하지 않습니다.](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [이 PC에는 Windows Mixed Reality를 실행 하는 데 사용 가능한 디스크 공간이 충분 하지 않습니다.](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [이 PC는 Windows Mixed Reality를 지원 하지 않는 Windows 버전을 실행 하 고 있습니다.](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [이 PC는 최신 버전의 Windows 10을 실행 하지 않습니다.](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [이 PC에는 USB 3.0 포트가 없습니다.](#this-pc-has-no-usb-30-port)
* [원격 데스크톱을 통해이 앱을 실행할 수 없습니다.](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>이 PC에는 단일 채널 RAM이 있는 통합 그래픽 카드가 있습니다.

통합 그래픽 카드는 이중 채널 RAM이 있는 Pc에서 최상의 Windows Mixed Reality 환경을 제공 합니다. 성능 문제가 발생 하면 다음을 수행 합니다.

> [!div class="checklist"]
> * [호환 되는 개별 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 설치
> * 추가 RAM 스틱을 설치 하 여 이중 채널 RAM 만들기
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>이 PC에는 호환 되지 않는 PCIe 링크로 하이브리드 그래픽 구성이 있습니다.

PCIe는 PC가 그래픽 카드와 통신 하는 데 사용 하는 연결 인 *주변 장치 구성 요소 상호 연결 Express* 를 나타냅니다. 구성이 작동할 수 있지만 문제가 발생 하는 경우 [호환 되는 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)로 전환 해야 합니다.

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.

Windows 업데이트를 사용 하 여 새 그래픽 드라이버를 다운로드 해 보세요.

> [!div class="checklist"]
> * **시작 > 설정 선택 > 업데이트 & 업데이트 > 업데이트 확인** 또는 PC 또는 그래픽 카드 제조업체의 웹 사이트로 이동
> * [업데이트 확인](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

작동 하지 않는 경우 다음을 수행 해야 합니다.

> [!div class="checklist"]
> * [호환 되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 프로세서는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.

PC의 프로세서는 코어가 충분 하지 않기 때문에 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다. Windows Mixed Reality가 제대로 실행 되지 않는 경우:

> [!div class="checklist"]
> * 프로세서를 [호환 되는 것](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 으로 바꿉니다. 
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>이 PC에는 호환 되는 USB 구성이 없을 수 있습니다.

Windows Mixed Reality를 실행 하는 문제:

> [!div class="checklist"]
> * 일반적인 호환성 문제에 대 한 해결 [방법은 권장 어댑터 설명서](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 를 참조 하세요.
> * [외부 기반 USB 허브](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) 를 사용 하는 것이 좋습니다.

문제가 지속 되 면 다음을 수행 합니다.

> [!div class="checklist"]
> * 사용 가능한 경우 헤드셋을 다른 USB 포트에 연결 합니다.
> * 그래도 작동 하지 않으면 PC의 현재 USB 드라이버를 제거 하 고 Microsoft 드라이버를 다시 설치 합니다.

1. **시작** 을 선택한 다음 **검색** 상자에 "장치 관리자"를 입력 합니다.
2. 결과에서 **Device Manager** 를 선택 합니다.
3. 범용 직렬 버스 컨트롤러의 범주를 확장 하 고 나열 된 장치를 확인 한 다음 호환 되지 않는 드라이버를 모두 제거 합니다.
    * 장치 이름 끝에 "Microsoft"가 없는 "확장 가능 호스트 컨트롤러" 항목이 목록에 포함 되어 있으면 해당 드라이버는 Windows Mixed Reality와 호환 되지 않습니다. 제거 해야 합니다. 드라이버를 제거 하려면 목록에서 장치를 마우스 오른쪽 단추로 클릭 하 고 **장치 제거** 를 선택 합니다. **이 장치에 대 한 드라이버 소프트웨어 삭제** 확인란을 선택 하 고 **제거** 를 선택 합니다.
    * 이름에 "Etron"가 포함 된 "확장 가능한 호스트 컨트롤러" 항목이 목록에 포함 되어 있으면 해당 USB 컨트롤러는 Windows Mixed Reality와 호환 되지 않습니다. PC에서 다른 USB 포트를 사용 하거나 다른 USB 3.0 호스트 컨트롤러를 구입 해야 합니다.
4. PC를 다시 시작 합니다.
5. Device Manager로 돌아가서 확장 가능한 호스트 컨트롤러 항목을 다시 찾습니다. 이제 장치 이름 끝에 "Microsoft"가 표시 되 면 이동 하는 것이 좋습니다. 그렇지 않은 경우 제거 단계를 반복 하 여 Microsoft 이외의 다른 버전의 드라이버를 제거 합니다.

> [!div class="checklist"]
> * 그래도 작동 하지 않으면 컴퓨터에 PCIe USB 카드를 추가 합니다.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>이 PC에는 컨트롤러에 대 한 Bluetooth 4.0가 없습니다.

2018 이상 Windows Mixed Reality 헤드셋에는 기본 제공 블루투스가 이미 있지만 이전 헤드셋이 있는 경우 혼합 현실 동작 컨트롤러에는 bluetooth 4.0이 필요 합니다. [Windows Mixed Reality를 Xbox 컨트롤러](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), [마우스 및 키보드](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)또는 [USB Bluetooth 어댑터](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) 와 함께 사용 하 여 이동 컨트롤러를 PC에 연결할 수 있습니다. [권장 어댑터 참조](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>헤드셋에 따라 동작 컨트롤러를 사용 하려면 Bluetooth 어댑터가 필요할 수 있습니다.

일부 헤드셋에는 Bluetooth가 내장 되어 있으므로 컨트롤러는 헤드셋에 직접 연결할 수 있습니다. 다른 사용자는 움직임 컨트롤러를 사용 하기 위해 PC의 Bluetooth 라디오 (또는 별도의 동글을 필요 함)가 필요 합니다. 자세한 내용은 [권장 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) 페이지를 참조 하세요.

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>이 PC에는 자체 기반 USB 포트가 없습니다.

Windows Mixed Reality 헤드셋을 연결 하려면 셀프 기반 USB 3.0 포트가 필요 합니다. [전원이 켜진 USB 3.0 허브](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) 를 PC에 연결 하 고이를 사용 하 여 헤드셋을 연결 합니다.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>이 PC의 그래픽 카드는 Windows Mixed Reality에서 작동 하지 않습니다.

이 PC의 그래픽 카드는 Windows Mixed Reality와 호환 되지 않습니다. 다음 작업을 수행 해야 합니다.

> [!div class="checklist"]
> * [호환 되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 작동 하지 않습니다.

이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 작동 하지 않습니다. Windows 업데이트를 사용 하 여 새 그래픽 드라이버를 다운로드 해 보세요.

> [!div class="checklist"]
> * **시작 > 설정 선택 > 업데이트 & 업데이트 > 업데이트 확인** 또는 PC 또는 그래픽 카드 제조업체의 웹 사이트로 이동
> * [업데이트 확인](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

작동 하지 않는 경우 다음을 수행 해야 합니다.

> [!div class="checklist"]
> * [호환 되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>이 PC의 프로세서는 Windows Mixed Reality에서 작동 하지 않습니다.

이 PC의 프로세서는 AVX/Popcnt 명령을 지원 하지 않습니다. Windows Mixed Reality를 실행 하려면 다음을 수행 해야 합니다.

> [!div class="checklist"]
> * [호환 되는 그래픽 카드로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 바꿉니다. 
> * [호환 되는 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 로 전환

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>이 PC에는 Windows Mixed Reality를 실행 하는 데 사용 가능한 디스크 공간이 충분 하지 않습니다.

Windows Mixed Reality에는 설치 및 최상의 성능을 위해 10gb의 사용 가능한 디스크 공간이 필요 합니다. 드라이브의 공간을 확보 한 다음 처음부터 다시 설정 해 봅니다.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>이 PC는 Windows Mixed Reality를 지원 하지 않는 Windows 버전을 실행 하 고 있습니다.

Windows Mixed Reality는 [windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) 및 [windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)에서 작동 합니다. Windows Mixed Reality를 사용 하려면 이러한 버전 중 하나를 설치 해야 합니다.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>이 PC는 최신 버전의 Windows 10을 실행 하지 않습니다.

Windows Mixed Reality를 사용 하려면 Windows 10 인 생성기를 업데이트 해야 합니다. [PC를 업데이트](https://support.microsoft.com/help/4028685) 하 고 다시 시도 하세요.

### <a name="this-pc-has-no-usb-30-port"></a>이 PC에는 USB 3.0 포트가 없습니다.

Windows Mixed Reality 헤드셋을 연결 하려면 USB 3.0 포트가 필요 합니다. 데스크톱 PC를 사용 하 고 있는 경우 PCIe USB 카드를 추가 합니다. 노트북의 경우 [호환 되는 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)로 전환 해야 합니다.

### <a name="you-cant-run-this-app-via-remote-desktop"></a>원격 데스크톱을 통해이 앱을 실행할 수 없습니다.

Windows Mixed Reality를 사용 하려면 모니터가 연결 된 PC가 필요 합니다. 가상 컴퓨터를 사용 하 고 있거나 모니터가 없는 경우 가상 표시 어댑터를 사용해 보세요. PC의 DisplayPort에 연결 하 고 컴퓨터 디스플레이를 에뮬레이트하는 장치입니다.

## <a name="getting-the-best-performance"></a>최상의 성능 얻기

일부 하드웨어 구성은 Windows Mixed Reality의 성능 문제를 일으킬 수 있습니다. 느린 로드, 고르지 않은 시각적 개체 또는 시각적 품질 저하와 같은 문제가 발생 하는 경우 다음과 같은 일반적인 수정 작업을 수행해 보세요.

* PC 데스크톱에서 실행 중인 모든 오픈 앱 닫기
* USB-C를 사용 하거나 HDMI 어댑터에 DisplayPort를 사용 하는 경우 다른 것을 시도 합니다. 권장 어댑터 참조
* PC의 그래픽 카드에 추가 모니터가 연결 되어 있는 경우 연결을 끊습니다.
* Windows 스토어에서 다른 혼합 현실 앱을 다운로드 해 보세요. 일부 앱은 컴퓨터 설치에서 더 잘 작동할 수 있습니다.
* [성능 질문 설명서](performance-questions.md) 를 확인 하세요.

성능 문제가 여전히 발생 하는 경우 최적의 사용자 환경에 대해 다음과 같은 [Windows Mixed Reality](set-up-windows-mixed-reality.md) 설정을 업데이트 합니다.

* 환경
* 해결 방법
* 프레임-요율
* 보정

> [!NOTE]
> "이 하드웨어 구성은 Windows Mixed Reality에서 작동할 수 있지만 아직 테스트 되지 않았습니다." 라는 메시지가 표시 되 면 긴 세션에 대해 Windows Mixed Reality를 실행할 때 몇 가지 성능 문제가 발생할 수 있습니다.

## <a name="working-with-steamvr"></a>SteamVR 사용

SteamVR에서 게임을 제공 하는 것은 VR이 제공 해야 하는 모든 것을 경험 하는 좋은 방법입니다. 그러나 모던 장치에서 [최상의 성능을 얻을](performance-questions.md) 수 있는지 확인 하는 것이 좋습니다. [스트림](https://store.steampowered.com/about)를 설치한 후:

* [Windows Mixed Reality에서 SteamVR 사용](using-steamvr-with-windows-mixed-reality.md) 에 대 한 지침을 따르세요.
* [SteamVR 성능 테스트](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 앱 설치

## <a name="next-vr-checkpoint"></a>다음 VR 검사점

앞에서 설명한 VR 경험을 팔 트 하는 경우 장치를 구매할 준비가 거의 준비 된 것입니다. 여기에서 검사점을 구입 하기 전에 마지막으로 계속할 수 있습니다.

> [!div class="nextstepaction"]
> [구매 Faq](before-you-buy-faqs.md)

또는 시작 섹션으로 바로 이동 합니다.

> [!div class="nextstepaction"]
> [Windows Mixed Reality 설정](set-up-windows-mixed-reality.md)

언제 든 지 [VR 여행](vr-journey.md) 으로 돌아갈 수 있습니다.