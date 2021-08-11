---
title: Windows Mixed Reality 설정
description: Windows Mixed Reality 동작 컨트롤러, 음성 및 오디오를 설정 하 고 안전한 재생 공간에 대 한 공간 경계를 정의 하는 방법입니다.
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 시작, 설정, 동작 컨트롤러, 컨트롤러, 음성, 오디오, 장착 됨, 경계, 그래픽 드라이버, Microsoft Edge, chromium
ms.openlocfilehash: 436818ee662f9beb1c445ea5b22c5d168bb4142a7b49a116a4f5fa138e3a5595
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221056"
---
# <a name="set-up-windows-mixed-reality"></a>Windows Mixed Reality 설정

## <a name="get-ready"></a>준비

Windows Mixed Reality를 실행 하려면 다음이 필요 합니다.

* 호환 되는 혼합 현실 모던 헤드셋. [자세한 정보](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* 헤드셋에 올바른 포트를 사용 하는 [Windows Mixed Reality 준비 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* 동작 [컨트롤러](controllers-in-wmr.md), Xbox 컨트롤러 또는 마우스 및 키보드
* 마이크가 있는 헤드폰 (헤드셋에서 기본 제공 되지 않는 경우)
* 열려 있는 많은 공간

## <a name="get-set"></a>집합 가져오기

공간을 준비 합니다 (오버 헤드 공간 포함). 사용할 영역에 장애물, 위험 또는 손상 된 항목이 없는지 확인 합니다. 계단의 위쪽 이나 더 낮은 천장 팬에서 설정 하지 마세요. 영역에서 모든 거 나 장애물을 제거 하 고 모든 헤드셋 사용자가 안전 지침을 읽고 이해 하는지 확인 합니다.

공간이 준비 되 면 헤드셋에 연결 하지만 아직 배치 하지 마십시오. 먼저 PC에서 일부 설치를 수행 해야 합니다. PC 검사를 실행 하 고, 일부 소프트웨어를 다운로드 하 고, 컨트롤러를 연결 하 고, 장애물을 방지 하는 데 도움이 되는 [경계](boundary-questions.md) 를 만듭니다.

그런 다음 재미 있는 부분을 제공 합니다. Cortana는 둘러보기를 제공 하기 위해 대기 중입니다. 즐거운 시간 보내세요!

## <a name="go"></a>지금

공간이 준비 되 면 헤드셋에 연결 하지만 아직 배치 하지 마십시오. 먼저 PC에서 일부 설치를 수행 해야 합니다. PC 검사를 실행 하 고, 일부 소프트웨어를 다운로드 하 고, 컨트롤러를 연결 하 고, 장애물을 방지 하는 데 도움이 되는 [경계](boundary-questions.md) 를 만듭니다.

그런 다음 재미 있는 부분을 제공 합니다. Cortana는 둘러보기를 제공 하기 위해 대기 중입니다. 즐거운 시간 보내세요!

## <a name="get-familiar-with-your-motion-controllers"></a>동작 컨트롤러에 대해 알아보기

헤드셋에 기본 제공 된 라디오가 있는 경우 헤드셋과 함께 제공 되는 컨트롤러는 팩터리에서 페어링 됩니다. 새 컨트롤러와 헤드셋을 처음 켜면 이미 페어링 된 것입니다.

기본 제공 라디오 없이 헤드셋을 사용 하는 경우 PC에 연결 하 여 동작 컨트롤러를 설정 해야 합니다. 2018 이후 제조 된 대부분의 헤드셋에는 기본 제공 라디오가 있습니다.

Xbox 게임 패드 또는 키보드와 마우스를 사용 하려는 경우에는 컨트롤러를 페어링 하지 않아도 됩니다.  컨트롤러를 사용 하려는 경우에는 컨트롤러를 페어링 해야 합니다.

**참고**: Windows Mixed Reality 동작 컨트롤러에는 Bluetooth 4.0가 필요 합니다. PC에 기본 제공 Bluetooth 없는 경우 Bluetooth 4.0을 지 원하는 USB Bluetooth 어댑터를 연결 하 여 동작 컨트롤러를 사용 하도록 설정 해야 합니다. 헤드셋에서 기본 제공 라디오를 사용 하는 Bluetooth 어댑터가 필요 하지 않습니다.

![동작 컨트롤러에 대해 알아보기](images/get_to_know_controllers.png)

동작 컨트롤러를 쌍으로 연결 해야 하는 경우 [Windows Mixed Reality 문서의 컨트롤러](controllers-in-wmr.md) 를 검토 합니다.

## <a name="set-up-your-room-boundary"></a>대화방 경계 설정

방 규모 또는 책상 크기 조정 환경을 선택 합니다.

**옵션 1: 모든 환경 (공간 규모가 라고도 함)에 대해 설정** 하면 대화방을 탐색할 수 있으며, 가장 몰입가 혼합 된 현실 환경입니다. 혼합 현실에 대해 최소 5 피트 x 7 피트 (1.5 미터 x 2 미터)의 공간을 선택 하는 것이 좋습니다.

**옵션 2: 사용자의 책상에서 작동 하는 (책상 크기 조정 라고도 함) 환경에 대해 설정** 합니다. 공간이 크지 않은 경우 좋은 옵션입니다. 또한 경계 없이 헤드셋을 사용 하는 것을 의미 합니다. 물리적 장애물을 방지 하는 데 도움이 되는 경계를 갖지 않으므로 한 곳에 유지 해야 합니다. 일부 앱 및 게임은 경계 환경으로 설계 되지 않으므로 의도 한 대로 작동 하지 않을 수 있습니다.

![설정 선택](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>"모든 환경에 대해 설정"을 선택 하는 경우

곧 이동 하 고 상호 작용할 수 있는 가상 세계가 될 것입니다. 혼합 현실 실행을 위해 공간의 일부 공간을 확보 하 고 지웁니다. 혼합 현실에서 최소 5 피트 x 7 피트 또는 1.5 미터 x 2 미터의 공간을 선택 하는 것이 좋습니다.

![공간이 명확 한지 확인 합니다.](images/1050px-createaboundary.png)

공간이 명확 한지 확인 합니다.

![헤드셋 가운데 맞춤](images/1050px-createaboundary-2.png)

헤드셋을 가운데에 맞춥니다.

![경계 추적](images/1050px-createaboundary-3.png)

경계를 추적 합니다.

![PC를 지속적으로 유지](images/1050px-createaboundary-4.png)

헤드셋을 PC가 가리키는 상태로 유지 합니다.

![경계는 다음과 같습니다.](images/1050px-createaboundary-5.png)

경계는 다음과 같습니다.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>"시작 및 고정에 대해 설정"을 선택 하는 경우

이 옵션을 선택 하는 경우에는 추가 단계가 필요 하지 않습니다.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>경계의 최대 크기는 얼마 인가요?

Windows Mixed Reality에서 지원 되는 최대 경계 크기는 18x18ft (5.7 x 5.7 m) 또는 중간의 13 피트 (4 m) 반경입니다. 경계 크기는 앵커 지점과 경계의 안정성을 위해 이동할 수 있는 앵커 지점의 거리에 따라 달라 집니다.  Windows Mixed Reality 단계 추상화를 기반으로 하며, 단계는에서 이동 하는 공간입니다. 해당 단계는 거의 모든 앱에서 가정 하는 단일 앵커에 종속 됩니다 .이는 Vive와 Oculus가 단일 좌표계로 작동 하는 방식입니다.  이는 내부 추적을 사용 하는 경우에 중요 합니다 .이는 앵커 지점에서 더 멀리 이동할 때 헤드셋 추적이 안정적으로 경계를 유지할 수 있기 때문입니다.  경계는 물리적 장애물을 방지 하기 위해 고안 된 것 이며,이는 이동 하는 중심에서 더 많은 문제를 해결 하는 데 도움이 됩니다.  최대 경계 크기를 결정 하는 두 가지 요인이 있습니다. Windows Mixed Reality 헤드셋에서 대부분의 Windows Mixed Reality 헤드셋이 10 피트 (3 m) 인 경계와 헤드셋 케이블의 길이를 사용 하 여 최상의 공간 크기 조정 환경을 제공할 수 있는 최대 거리입니다.

## <a name="set-up-speech"></a>음성 설정

혼합 현실에서 Cortana 명령을 사용 하도록 설정할 수 있습니다. 그러면 음성 명령을 사용 하 여 앱을 텔레포트 하 고 열 수 있습니다. [Mixed Reality 학습](learn-mixed-reality.md) 장에서 이러한 작업에 대해 자세히 알아보세요.

![혼합 현실에서 음성 사용이 더 좋습니다.](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>오디오 헤드셋 설정

Ic AKG 헤드폰 및 이중 마이크 배열을 사용 하 여 Samsung HMD Odyssey를 구매한 경우를 제외 하 고 마이크와 헤드폰을 모두 사용 하 여 오디오 헤드셋을 받고 헤드셋의 3.5-mm 오디오 잭에 연결 해야 합니다. 헤드셋의 3.5-mm 오디오 잭이 헤드셋의 아래쪽에 있거나 헤드셋 모델에 따라 헤드셋 센터에 연결 된 짧은 오디오 케이블의 끝에 있습니다.

## <a name="adjusting-your-headsets-display-settings"></a>헤드셋의 디스플레이 설정 조정

Windows Mixed Reality는 PC의 하드웨어 구성에 따라 품질 및 성능의 균형을 유지 하는 표시 설정을 자동으로 선택 합니다. 이러한 설정을 조정 하려면 **설정 > Mixed Reality > 헤드셋 표시** 로 이동 합니다.

### <a name="visuals"></a>시각적 개체

이 설정은 Mixed reality 홈의 시각적 품질을 제어 합니다. 기본값은 "Automatic"입니다.

### <a name="resolution"></a>해결 방법

헤드셋의 기본 해상도는 다음과 같습니다.

고해상도 디스플레이를 사용 하 여 헤드셋을 PC에 연결 하는 경우 (예: 4320x2160이 표시 된 헤드셋) 혼합 현실 디스플레이 해상도를 조정 하는 설정이 표시 됩니다.

* 이 설정은 Windows Mixed Reality 컴퍼지션 스택이 기본적으로 렌더링 (예: 4320x2160) 하거나 더 낮은 해상도 및 upscale (예: 2880x1440, upscale에서 4320x2160으로 렌더링)를 렌더링 하도록 하는 옵션을 제공 합니다.
* 기본 설정은 헤드셋에서 가능한 최상의 시각적 품질을 제공 하기 위해 기본적으로 렌더링 하는 것입니다 (예: **4320 x 2160 (최고 품질)** 옵션).
* 다음과 같은 경우 **자동 upscaling (최상의 성능)** 옵션을 사용 합니다.
    * PC가 해상도가 높은 헤드셋의 최소 그래픽 하드웨어 요구 사항을 충족 하지 않습니다.
    * 그래픽 성능 문제가 발생 하 고 있습니다.

이 설정은 Windows 10 버전 1903 이상에서 사용할 수 있습니다.

### <a name="calibration"></a>보정

이 설정은 software IPD support가 포함 된 헤드셋의 IPD 보정을 조정 하는 것입니다.

### <a name="experience-options"></a>환경 옵션

이 고급 설정은 기본 헤드셋 디스플레이 새로 고침 빈도 환경을 재정의합니다.

* **자동(기본값)**: PC의 하드웨어 구성에 따라 60Hz 또는 90Hz 환경을 자동으로 선택합니다.
* **60Hz**
* **90Hz**

>[!Note]
>HP Reverb G2 헤드셋을 처음 설정하는 경우 환경을 90Hz로 변경하여 .best 환경을 보장합니다.  필요한 경우 다시 자동으로 변경할 수 있습니다.

### <a name="input-switching"></a>입력 전환

이 설정은 헤드셋의 현재 상태 센서에 대한 응답으로 Windows Mixed Reality 동작을 제어합니다.

* **헤드셋 상태 센서를 사용하여 자동으로** 전환(기본값): Windows 헤드셋을 사용할 때마다 입력(키보드, 마우스...)을 자동으로 Windows Mixed Reality 지시합니다. Win + Y를 사용하면 언제든지 이를 재정의할 수 있습니다.
* **Windows 로고 키 + Y를 사용하여 수동으로 전환:** Windows 헤드셋의 현재 상태 센서를 사용하여 헤드셋을 사용하는 시기를 감지하지 않습니다. Win + Y를 사용하여 PC 데스크톱과 Windows Mixed Reality 간에 입력을 전환해야 합니다.

이 설정은 Windows 10 버전 1903 이상에서 사용할 수 있습니다.

## <a name="installing-microsoft-edge"></a>Microsoft Edge 설치 

Windows Mixed Reality 홈의 새 Chromium 기반 Microsoft Edge 사용하려면 Windows Mixed Reality 홈의 Win32 애플리케이션(예: 새 Microsoft Edge)의 기본 지원을 위해 Windows 10 버전 1903 이상으로 업그레이드합니다. Windows 업데이트를 확인하거나 [최신 버전의 Windows 10 를 수동으로 설치합니다.](https://www.microsoft.com/software-download/windows10)

>[!IMPORTANT]
>새로운 Microsoft Edge VR 헤드셋을 위한 몰입형 웹 환경을 만들기 위한 새로운 표준인 WebXR을 지원하여 시작됩니다. 새 Microsoft Edge 설치하는 경우 Microsoft Edge WebVR 환경을 더 이상 재생할 수 없습니다.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Windows Mixed Reality 새 Microsoft Edge 문제

**Windows 10 버전 1903 이상에 대한 2020-01 누적 업데이트에서 해결된 알려진 문제**

- 새 Microsoft Edge 포함하여 Win32 앱을 시작하면 헤드셋 디스플레이가 잠시 중지합니다.
- Microsoft Edge 타일은 Windows Mixed Reality 시작 메뉴 사라집니다("클래식 앱" 폴더에서 찾을 수 있습니다).
- 이전 Microsoft Edge Windows 여전히 혼합 현실 홈 주위에 배치되지만 사용할 수는 없습니다. 이러한 창을 활성화하려고 시도하여 데스크톱 앱에서 Edge가 시작됩니다.
- 혼합 현실 홈 하이퍼링크를 선택하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작됩니다.
- WebVR Showcase 앱은 WebVR이 더 이상 지원되지 않는데도 혼합 현실 홈 있습니다.
- 키보드 시작 및 시각적 개체에 대한 일반적인 개선

**추가적으로 알려진 문제**

- Windows Mixed Reality 열린 웹 사이트는 Mixed Reality 포털 닫히면 손실되지만 Microsoft Edge 창은 혼합 현실 홈 배치된 위치로 유지됩니다.
- Microsoft Edge 창의 오디오는 공간화되지 않습니다.
- 360 뷰어 확장 버전 2.3.8에서 수정됨: Windows Mixed Reality YouTube에서 360 비디오를 열면 헤드셋에서 비디오가 왜곡될 수 있습니다. Edge를 다시 시작하면 이 문제를 해결하기 위해 360 뷰어 확장을 보이지 않게 업데이트해야 합니다. 주소 표시줄에 을 `edge://system/` 입력하고 "확장" 옆에 있는 "확장" 단추를 선택하여 확장의 버전을 확인할 수 있습니다.
- Windows Mixed Reality 세션 중에 가상 모니터는 **설정 > System > Display에** 일반 물리적 모니터로 표시됩니다.

## <a name="launching-mixed-reality-after-the-first-time"></a>처음으로 혼합 현실 시작

혼합 현실에 두 번째로 입력하는 것은 PC에 연결된 동안 헤드셋을 다시 켜는 것만큼 쉽습니다. 시작 메뉴 열어 Mixed Reality 포털 애플리케이션을 수동으로 시작할 수도 있습니다. 입력 및 오디오는 헤드셋을 배치할 때 자동으로 헤드셋으로 라우팅되거나 키보드에서 **Windows + Y를** 눌러 수동으로 트리거할 수 있습니다.

## <a name="see-also"></a>추가 정보

* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원을 요청합니다.](https://support.microsoft.com/contactus/)
* [설치 문제 해결](installation_errors.md)
* [설정 문제 해결](wmr-setup-faq.yml)
* [Mixed Reality 학습](learn-mixed-reality.md)
* [모션 컨트롤러](controllers-in-wmr.md)
* [내부에서 외부로 추적의 작동 방식](tracking-system.md)
