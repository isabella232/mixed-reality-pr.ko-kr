---
title: PC 호환성에 대한 도움말 보기
description: Windows Mixed Reality 애플리케이션 및 디바이스로 작업할 때 PC 호환성 문제를 해결하기 위한 리소스를 최신 상태로 유지합니다.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 피드백, 피드백 허브, 버그
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 1a07326da871eead6b13fe8350f37a22f8d27c23
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436565"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Windows Mixed Reality PC 호환성에 대한 도움말 얻기

Windows Mixed Reality 설정하거나 [Mixed Reality 포털](install-windows-mixed-reality.md)를 사용하는 경우 PC가 작업에 달려 있는지 여부에 대한 보고서를 받게 됩니다. 아래 섹션에서 볼 수 있는 내용에 대한 구체적인 세부 정보를 알아보았습니다.

계속 진행하기 전에 아래의 가장 일반적인 수정 사항을 시도해 보세요. 

> [!div class="checklist"]
> * 컴퓨터가 최소 PC [하드웨어 호환성 요구 사항을](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 충족하는지 확인합니다.
> * [그래픽 카드와 프로세서가](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 호환 가능한지 확인합니다.
> * 권장 [어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 목록 확인
> * 업데이트 시작 > 설정 > 업데이트 & 보안 > 업데이트 확인을 선택하여 그래픽 드라이버를 **업데이트합니다.** 

연락하려는 경우 [커뮤니티에 문의하거나,](https://answers.microsoft.com)지원 [담당자에게 문의하거나,](https://support.microsoft.com/contactus/) [문제 해결](troubleshooting-windows-mixed-reality.md) 정보를 확인할 수 있습니다.

## <a name="youre-good-to-go"></a>이동해도 좋습니다.

좋은 소식을 전합니다. **You're good to go** 메시지가 표시되면 PC를 Windows Mixed Reality 실행할 수 있습니다. 컴퓨터 하드웨어와 구성 간에는 여전히 차이가 있으므로 Mixed Reality 환경이 모든 PC에서 동일하지 않을 수 있습니다.

## <a name="supports-some-features"></a>일부 기능 지원

**일부 기능 지원** 메시지가 표시되면 PC에서 몇 가지 Windows Mixed Reality 환경을 실행할 수 있지만 가능한 최상의 환경을 제공하지 못할 수 있습니다. 가능한 단점으로는 그래픽 지연, 성능 적중, 실행할 수 없는 일부 애플리케이션 및 게임 등이 있습니다. 아래에 표시될 수 있는 메시지와 관련한 작업을 나열했습니다.

* [이 PC에는 단일 채널 RAM이 있는 통합 그래픽 카드가 있습니다.](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [이 PC에는 호환되지 않는 PCIe 링크가 있는 하이브리드 그래픽 구성이 있습니다.](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [이 PC의 그래픽 드라이버가 Windows Mixed Reality 잘 작동하지 않을 수 있습니다.](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [이 PC의 프로세서는 Windows Mixed Reality 잘 작동하지 않을 수 있습니다.](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [이 PC에는 호환되는 USB 구성이 없을 수 있습니다.](#this-pc-might-not-have-a-compatible-usb-configuration)
* [이 PC에는 컨트롤러에 대한 Bluetooth 4.0이 없습니다.](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [헤드셋에 따라 모션 컨트롤러를 사용하려면 Bluetooth 어댑터가 필요할 수 있습니다.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [이 PC에는 자체 구동 USB 포트가 없습니다.](#this-pc-doesnt-have-a-self-powered-usb-port)
* [이 PC의 그래픽 카드는 Windows Mixed Reality 작동하지 않습니다.](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [이 PC의 그래픽 드라이버는 Windows Mixed Reality 작동하지 않습니다.](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [이 PC의 프로세서는 Windows Mixed Reality 작동하지 않습니다.](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [이 PC에는 Windows Mixed Reality 실행하는 데 충분한 여유 디스크 공간이 없습니다.](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [이 PC는 Windows Mixed Reality 지원하지 않는 Windows 버전을 실행합니다.](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [이 PC는 최신 버전의 Windows 10 실행하지 않습니다.](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [이 PC는 최신 버전의 Windows 11을 실행하지 않습니다.](#this-pc-isnt-running-the-latest-version-of-windows-11)
* [이 PC에는 USB 3.0 포트가 없습니다.](#this-pc-has-no-usb-30-port)
* [원격 데스크톱을 통해 이 앱을 실행할 수 없습니다.](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>이 PC에는 단일 채널 RAM이 있는 통합 그래픽 카드가 있습니다.

통합 그래픽 카드는 이중 채널 RAM이 있는 PC에서 최상의 Windows Mixed Reality 환경을 제공합니다. 성능 문제가 발생하면 다음을 수행합니다.

> [!div class="checklist"]
> * [호환되는 불연속 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 설치
> * 추가 RAM 스티커를 설치하여 이중 채널 RAM 만들기
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>이 PC에는 호환되지 않는 PCIe 링크가 있는 하이브리드 그래픽 구성이 있습니다.

PCIe는 PC가 그래픽 카드와 통신하는 데 사용하는 연결인 주변 장치 구성 요소 상호 연결 *Express를* 의미합니다. 구성이 작동할 수 있지만 문제가 발생하면 [호환되는 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)로 전환해야 합니다.

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 그래픽 드라이버는 Windows Mixed Reality 잘 작동하지 않을 수 있습니다.

다음을 수행하여 Windows 업데이트를 사용하여 새 그래픽 드라이버를 다운로드해 보세요.

> [!div class="checklist"]
> * > 설정 > **업데이트 시작 & 보안 > 업데이트를 확인하거나** PC 또는 그래픽 카드 제조업체의 웹 사이트로 가기를 선택합니다.
> * [업데이트 확인](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

작동하지 않는 경우 다음을 수행해야 합니다.

> [!div class="checklist"]
> * [호환되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 프로세서는 Windows Mixed Reality 잘 작동하지 않을 수 있습니다.

PC의 프로세서는 코어가 충분하지 않기 때문에 Windows Mixed Reality 잘 작동하지 않을 수 있습니다. Windows Mixed Reality 잘 실행되지 않는 경우:

> [!div class="checklist"]
> * 프로세서를 [호환되는](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 프로세서로 바꾸기 
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>이 PC에 호환되는 USB 구성이 없을 수 있습니다.

Windows Mixed Reality 실행하는 문제:

> [!div class="checklist"]
> * 일반적인 호환성 문제에 대한 해결 방법은 [권장 어댑터 설명서를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 확인하세요.
> * [외부 전원 USB 허브를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) 사용하는 것이 좋습니다.

문제가 지속되면 다음을 수행합니다.

> [!div class="checklist"]
> * 헤드셋을 사용할 수 있는 경우 다른 USB 포트에 연결합니다.
> * 작동하지 않는 경우 PC의 현재 USB 드라이버를 제거한 다음, Microsoft 드라이버를 다시 설치합니다.

1. **시작을** 선택한 다음 **검색** 상자에 "디바이스 관리자"를 입력합니다.
2. 결과에서 **디바이스 관리자를** 선택합니다.
3. 유니버설 Serial Bus 컨트롤러의 범주를 확장하고, 나열된 디바이스를 살펴보고, 호환되지 않는 드라이버를 제거합니다.
    * 목록에 디바이스 이름 끝에 "Microsoft"가 없는 "eXtensible Host Controller" 항목이 포함된 경우 해당 드라이버는 Windows Mixed Reality 호환되지 않습니다. 제거해야 합니다. 드라이버를 제거하려면 목록에서 디바이스를 마우스 오른쪽 단추로 클릭하고 **디바이스 제거를** 선택합니다. 이 **디바이스에 대한 드라이버 소프트웨어 삭제** 확인란을 선택한 다음, **제거를** 선택합니다.
    * 목록에 이름에 "Etron"이 포함된 "eXtensible Host Controller" 항목이 포함된 경우 해당 USB 컨트롤러는 Windows Mixed Reality 호환되지 않습니다. PC에서 다른 USB 포트를 사용하거나 다른 USB 3.0 호스트 컨트롤러를 구입해야 합니다.
4. PC를 다시 시작합니다.
5. 디바이스 관리자로 돌아가서 eXtensible 호스트 컨트롤러 항목을 다시 찾습니다. 이제 디바이스 이름 끝에 "Microsoft"가 표시되면 이동하는 것이 좋습니다. 그렇지 않은 경우 제거 단계를 반복하여 추가 비 Microsoft 버전의 드라이버를 제거합니다.

> [!div class="checklist"]
> * 그래도 작동하지 않는 경우 PCIe USB 카드를 PC에 추가합니다.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>이 PC에는 컨트롤러에 대한 Bluetooth 4.0이 없습니다.

2018 이상 Windows Mixed Reality 헤드셋에는 이미 기본 제공 Bluetooth 있지만, 이전 헤드셋이 있는 경우 혼합 현실 모션 컨트롤러에는 bluetooth 4.0이 필요합니다. [Xbox 컨트롤러,](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)마우스 및 키보드 또는 USB Bluetooth [어댑터와 함께 Windows Mixed Reality 사용하여 모션 컨트롤러를 PC에 연결할](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) 수 있습니다. [](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse) [권장 어댑터 참조](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>헤드셋에 따라 모션 컨트롤러를 사용하려면 Bluetooth 어댑터가 필요할 수 있습니다.

일부 헤드셋에는 Bluetooth 기본 제공되므로 컨트롤러가 헤드셋에 직접 페어링할 수 있습니다. 다른 경우에는 모션 컨트롤러를 사용하려면 PC(또는 별도의 동글)에 Bluetooth 라디오가 필요합니다. 자세한 내용은 권장 [어댑터 페이지를 참조하세요.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>이 PC에는 자체 구동 USB 포트가 없습니다.

Windows Mixed Reality 헤드셋을 연결하려면 자체 구동 USB 3.0 포트가 필요합니다. [전원이 공급된 USB 3.0 허브를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) PC에 커넥트 헤드셋을 연결하는 데 사용합니다.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>이 PC의 그래픽 카드는 Windows Mixed Reality 작동하지 않습니다.

이 PC의 그래픽 카드는 Windows Mixed Reality 호환되지 않습니다. 다음 작업이 필요합니다.

> [!div class="checklist"]
> * [호환되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>이 PC의 그래픽 드라이버는 Windows Mixed Reality 작동하지 않습니다.

이 PC의 그래픽 드라이버는 Windows Mixed Reality 작동하지 않습니다. 다음을 수행하여 Windows 업데이트를 사용하여 새 그래픽 드라이버를 다운로드해 보세요.

> [!div class="checklist"]
> * > 설정 > **업데이트 시작 & 보안 > 업데이트를 확인하거나** PC 또는 그래픽 카드 제조업체의 웹 사이트로 가기를 선택합니다.
> * [업데이트 확인](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

작동하지 않는 경우 다음을 수행해야 합니다.

> [!div class="checklist"]
> * [호환되는 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 추가 
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>이 PC의 프로세서는 Windows Mixed Reality 작동하지 않습니다.

이 PC의 프로세서는 AVX/Popcnt 명령을 지원하지 않습니다. Windows Mixed Reality 실행하려면 다음을 수행해야 합니다.

> [!div class="checklist"]
> * [호환되는 그래픽 카드로 바꾸기](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * [호환되는 PC로](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 전환

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>이 PC에는 Windows Mixed Reality 실행하는 데 충분한 여유 디스크 공간이 없습니다.

Windows Mixed Reality 설치 및 최상의 성능을 위해 10GB의 사용 가능한 디스크 공간이 필요합니다. 드라이브의 공간을 지운 다음 처음부터 다시 설정을 시도합니다.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>이 PC는 Windows Mixed Reality 지원하지 않는 Windows 버전을 실행합니다.

Windows Mixed Reality Windows 10 Home , [Windows 10 Pro](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab)및 [Windows](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab) [11에서](https://www.microsoft.com/software-download/windows11)작동합니다. Windows Mixed Reality 사용하려면 해당 버전 중 하나를 설치해야 합니다.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>이 PC는 최신 버전의 Windows 10 실행하지 않습니다.

Windows Mixed Reality Windows 10 Fall Creators Update 필요합니다. [PC를 업데이트하고 다시 시도하세요.](https://support.microsoft.com/help/4028685)

### <a name="this-pc-isnt-running-the-latest-version-of-windows-11"></a>이 PC는 최신 버전의 Windows 11을 실행하지 않습니다.

Windows Mixed Reality Windows 11 최신 릴리스가 필요합니다. [PC를 업데이트하고 다시 시도하세요.](https://www.microsoft.com/software-download/windows11)

### <a name="this-pc-has-no-usb-30-port"></a>이 PC에는 USB 3.0 포트가 없습니다.

Windows Mixed Reality 헤드셋을 연결하려면 USB 3.0 포트가 필요합니다. 데스크톱 PC를 사용하는 경우 PCIe USB 카드를 추가합니다. 랩톱의 경우 [호환되는 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)로 전환해야 합니다.

### <a name="you-cant-run-this-app-via-remote-desktop"></a>원격 데스크톱을 통해 이 앱을 실행할 수 없습니다.

Windows Mixed Reality 사용하려면 모니터가 연결된 PC가 필요합니다. 가상 머신을 사용하거나 모니터가 없는 경우 가상 디스플레이 어댑터를 사용해 보세요. PC의 DisplayPort에 연결하고 컴퓨터 디스플레이를 에뮬레이트하는 디바이스입니다.

## <a name="getting-the-best-performance"></a>최상의 성능 얻기

일부 하드웨어 구성으로 인해 Windows Mixed Reality 성능 문제가 발생할 수 있습니다. 느린 로드, 느린 시각적 개체 또는 낮은 시각적 개체 품질과 같은 문제의 경우 다음과 같은 일반적인 수정을 시도합니다.

* PC 데스크톱에서 실행 중인 열려 있는 앱을 닫습니다.
* HDMI 어댑터에 USB-C 또는 DisplayPort를 사용하는 경우 다른 어댑터를 사용해 보세요. 권장 어댑터 참조
* PC의 그래픽 카드에 연결된 추가 모니터가 있는 경우 연결을 끊습니다.
* Windows 스토어에서 다른 혼합 현실 앱을 다운로드해 보세요. 일부는 컴퓨터 설정에서 더 잘 작동할 수 있습니다.
* [성능 질문 설명서를 확인하세요.](performance-questions.md)

여전히 성능 문제가 있는 경우 최적의 사용자 환경을 위해 다음 [Windows Mixed Reality](set-up-windows-mixed-reality.md) 설정을 업데이트합니다.

* 환경
* 해결 방법
* 프레임 속도
* 보정

> [!NOTE]
> "이 하드웨어 구성은 Windows Mixed Reality 작동할 수 있지만 아직 테스트되지 않았습니다."라는 메시지가 표시되면 긴 세션에 대해 Windows Mixed Reality 실행할 때 몇 가지 성능 문제가 발생할 수 있습니다.

## <a name="working-with-steamvr"></a>SteamVR 작업

Vr이 제공해야 하는 모든 것을 경험할 수 있는 좋은 방법은 SteamVR에서 게임을 즐겨보세요. 그러나 몰입형 디바이스에서 최상의 성능을 얻을 [수](performance-questions.md) 있도록 해야 합니다. [Steam을](https://store.steampowered.com/about)설치한 후:

* Windows Mixed Reality [함께 SteamVR을 사용하기](using-steamvr-with-windows-mixed-reality.md) 위한 지침을 따릅니다.
* [SteamVR 성능 테스트](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 앱 설치

## <a name="next-vr-checkpoint"></a>다음 VR 검사점

우리가 배치한 VR 여정을 따르는 경우 디바이스를 구입할 준비가 거의 된 것입니다. 여기에서 검사점 구입 전에 마지막까지 계속할 수 있습니다.

> [!div class="nextstepaction"]
> [구매 FAQ](before-you-buy-faqs.md)

또는 시작 섹션으로 바로 이동합니다.

> [!div class="nextstepaction"]
> [Windows Mixed Reality 설정](set-up-windows-mixed-reality.md)

언제든지 [VR](vr-journey.md) 여정으로 돌아갈 수 있습니다.