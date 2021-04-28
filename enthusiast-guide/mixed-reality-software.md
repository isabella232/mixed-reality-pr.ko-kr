---
title: 소프트웨어 개요 및 릴리스 기록
description: Windows Mixed Reality, 모던 헤드셋 및 해당 릴리스 내역에 대 한 주요 소프트웨어 구성 요소에 대 한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 소프트웨어 구성 요소, 릴리스 기록, 릴리스 정보, 버전 기록
appliesto:
- Windows 10
ms.openlocfilehash: 5e6cdcbc7d91a6c1fadb519f94fc0339bdd39ca7
ms.sourcegitcommit: 229c33afab7c70341982f48962028aad13956356
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2021
ms.locfileid: "108069207"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>혼합 현실 소프트웨어 개요 및 릴리스 기록

## <a name="introduction-to-mixed-reality-software"></a>혼합 현실 소프트웨어 소개

Windows Mixed Reality는 다음과 같은 주요 소프트웨어 구성 요소로 구성 됩니다.

1. 기본 Windows Mixed Reality 환경을 제공 하는 **혼합 현실 포털**
    * Windows 10 버전 1709 및 1803에서 혼합 현실 포털은 Windows 업데이트를 통해 업데이트 된 Windows 10 운영 체제의 주요 구성 요소입니다.
    * Windows 10 버전 1809 이상에서 혼합 현실 포털은 Microsoft Store 앱을 통해 업데이트 됩니다.
2. 혼합 현실 포털의 첫 실행 중에는 **혼합 현실 주문형 패키지 (주문형 패키지** )가 자동으로 다운로드 및 설치 됩니다. 패키지에 대 한 자세한 내용은 여기를 참조 [하세요](/windows/application-management/manage-windows-mixed-reality) .
3. Windows mixed reality 헤드셋이 Windows Mixed Reality에서 작동할 수 있도록 하는 **혼합 현실 헤드셋 및 동작 컨트롤러 드라이버**(HoloLens 센서 드라이버 라고도 함)는 핵심 드라이버 패키지입니다. 이는 혼합 현실 헤드셋이 연결 된 경우 Windows 업데이트를 통해 자동으로 다운로드 및 설치 되며를 통해 정기적으로 업데이트 됩니다 Windows 업데이트
4. * * 혼합 현실 동작 컨트롤러 모델 드라이버는 혼합 현실 동작 컨트롤러의 3D 모델을 포함 하며 타사 혼합 현실 환경에 필요 합니다. 이는 혼합 현실 동작 컨트롤러가 PC와 쌍으로 연결 되 고 처음으로 업데이트 될 때 Windows 업데이트를 통해 자동으로 다운로드 및 설치 됩니다 Windows 업데이트
5. Windows **10, 버전 1709 (낙하 작성자의 업데이트) 이상** 에는 Windows Mixed Reality를 사용 하는 핵심 OS 구성 요소 및 기술이 포함 되어 있습니다.

SteamVR에서 Windows Mixed Reality를 사용 하려면 다음 소프트웨어가 필요 합니다.

6. 스트림에서 가상 현실 앱 및 게임을 활성화 하는 밸브가 Corporation에서 개발 하 고 유지 관리 하는 **SteamVR**. 자세한 내용은 [여기](https://go.microsoft.com/fwlink/?linkid=862788)를 참조하세요.
7. SteamVR 구성 요소 **에 대 한 Windows Mixed reality** 로, Windows mixed Reality와 SteamVR를 연결 합니다. 이 구성 요소에 대 한 자세한 내용은 [SteamVR 용 Windows Mixed Reality 페이지에서](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 찾을 수 있습니다.

Windows Mixed Reality 헤드셋 관리:

8. 각 헤드셋 제조업체에서 개발 하 고 유지 관리 하는 **장치 도우미 앱** 은 Windows Mixed Reality 헤드셋을 신속 하 게 소개 합니다. Bluetooth 기능이 기본 제공 되는 헤드셋에서 장치 도우미 앱을 사용 하면 동작 컨트롤러를 공장 Bluetooth 페어링으로 복원할 수 있습니다. 일부 헤드셋 (예: Samsung Odyssey 및 Samsung Odyssey +)은 장치 도우미 앱을 사용 하 여 헤드셋 제조업체의 헤드셋 펌웨어 업데이트를 제공 합니다. 이 앱은 헤드셋이 처음 연결 될 때 자동으로 다운로드 되 고 Windows 시작 메뉴에서 찾을 수 있습니다.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 릴리스 정보-2020 년 5 월

**Windows 10 5 월 2020 업데이트 (v2004)** 에는 혼합 현실 홈에서 Win32 응용 프로그램을 시작 하는 기능과 같은 VR (Windows mixed Reality) 헤드셋의 새로운 기능이 포함 되어 있습니다. HoloLens (첫 번째 gen)는 장기 서비스 (LTS)에서 제공 하는 서비스 업데이트가 매월 릴리스됩니다.

Windows Mixed Reality 모던 (VR) 헤드셋의 최신 PC 릴리스로 업그레이드 하 고, **설정을 열고 > 업데이트 & 보안** 을 선택 하 고, **업데이트 확인** 을 선택 합니다. Windows 10 PC에서는 [windows 미디어 만들기 도구](https://www.microsoft.com/software-download/windows10)를 사용 하 여 **Windows 10 5 월 2020 업데이트** 를 수동으로 설치할 수도 있습니다.

**데스크톱용 최신 릴리스**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 모던 헤드셋의 업데이트

#### <a name="introducing-the-new-microsoft-edge"></a>새 Microsoft Edge 소개

[이전에 발표](/windows/mixed-reality/new-microsoft-edge)한 대로 Windows Mixed Reality에서 새로운 Microsoft Edge 브라우저를 사용 하 여 더 나은 지원을 제공 했습니다. 새 Microsoft Edge는 Chromium 오픈 소스 프로젝트를 채택 하 여 고객에 게 더 나은 웹 호환성을 만들며 모든 웹 개발자가 웹의 조각화를 줄일 수 있습니다. 또한 WebVR 대신 VR 헤드셋에 대 한 몰입 형 웹 환경을 만드는 새로운 표준인 WebXR도 지원 합니다.

#### <a name="improved-settings-for-wmr"></a>WMR에 대 한 향상 된 설정

피드백을 주셔서 감사 합니다. 헤드셋 표시 페이지에서 설정을 추가 하 고 설명 했습니다.

* **내 홈의 시각적 품질이** 이 설정을 변경 하면 혼합 현실 집 환경 (절벽 집 및 Skyloft)에만 영향을 줍니다.

* **혼합 현실 홈에서 세부 효과 수준 및 효과 품질 조정** -이 변경 내용은 홈에서 사용 하는 일부 렌더링에 영향을 줍니다. 특히이 설정을 낮은 수준에서 높음으로 변경 하는 경우 다양 한 재질의 시각적 품질 (목재, 구체적 등)이 확장 됩니다.

* **앱 창 해상도 변경** -기본적으로 홈에서 시작 된 대부분의 2d 창은 720-p 해상도로 시작 됩니다. 수직 & 세로 방향으로 수동으로 크기를 조정할 수 있지만,이를 모두 1080p에서 시작 하도록 선택할 수도 있습니다. 이전에는이 옵션을 시각적 품질에서 매우 높은 (베타) 옵션으로 사용할 수 있었습니다. 이제 별도의 설정으로 적절 하 게 분할 했습니다.

* **환경 옵션** -이러한 옵션은 하드웨어에서 무제한 90 fps를 유지 해야 하는 시스템의 부하를 줄이기 위해 혼합 현실 환경을 조정 합니다. 이러한 추가 설정을 명시적으로 사용 하도록 설정 하거나 사용 하지 않도록 설정할 수 있습니다. 또는 Windows에서 결정을 선택 하 여 추론을 설정 하거나 해제 하는 시기를 계속 결정할 수 있습니다.

* **해결 방법** -HP 반향 같은 고해상도 헤드셋이 있는 경우 네이티브 해상도로 실행 하거나 성능상의 이유로 해상도를 줄이는 것이 좋습니다. Samsung Odyssey 및 Odyssey +와 같은 이전 헤드셋은 단일 해상도만 지원 하므로 해당 헤드셋에서이 설정을 변경할 수 없습니다.

* **프레임 주기** -이제 헤드셋 디스플레이의 프레임 속도로 수동으로 설정 하거나 Windows에서 추론을 사용 하 여 60 hz 또는 90 hz가 더 적절 한지 확인할 수 있습니다.

* **보정** -이전 처럼 헤드셋에서 지 원하는 경우 IPD (interpupillary distance)를 조정할 수 있습니다.

* **입력 전환** -입력 포커스 전환 (Win + Y) 동작을 자동 (현재 상태 센서 피드백에 따라) 또는 수동으로 전환 합니다.

#### <a name="new-cortana-app"></a>새 Cortana 앱

이 Windows 업데이트에는 현재 영어로만 제공 되는 Cortana 앱의 최신 버전이 포함 되어 있으며, "사진 찍기" 및 "비디오 가져오기"와 같은 특정 혼합 현실 특정 명령을 더 이상 지원 하지 않습니다. 사용자는 새로운 Cortana를 사용 하 여 앱을 시작할 수 있으며, "다음 모임이 언제 인가요?"와 같은 새로운 생산성 중심 명령도 지원 합니다. 또는 "늦게 실행 중인 것으로 전자 메일 보내기 <name> "
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546에서 제공 되는 추가 업데이트 (10 월 2020 일 출시)

이 데스크톱 월간 서비스 업데이트에는 Windows Mixed Reality 장치에 대 한 다음 변경 내용이 포함 되어 있습니다. 
* Windows Mixed Reality 헤드 탑재 디스플레이 (HMD)의 왜곡 및 aberrations 줄어듭니다. 
* 에는 예정 된 HP Windows Mixed Reality 동작 컨트롤러에 대 한 지원이 추가 되었습니다. 
* 90 Hz를 달성할 수 없는 경우 특정 경우에 Windows Mixed Reality에서 90-Hz 새로 고침 빈도 설정의 동작을 더 이상 자동으로 60 Hz로 전환 하지 않도록 변경 합니다. 

#### <a name="help-us-improve"></a>개선할 수 있도록 도와 주세요!

호환성을 지속적으로 개선 하 고 있습니다.  Windows Mixed Reality에서 즐겨 사용 하는 클래식 Win32 응용 프로그램이 제대로 작동 하지 않는 경우 [피드백 허브](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)를 통해 피드백을 제출 하세요.

### <a name="prior-release-notes"></a>이전 릴리스 정보

* [릴리스 정보-2019 년 5 월](release-notes-may-2019.md)
* [릴리스 정보 - 2018년 10월](release-notes-october-2018.md)
* [릴리스 정보-4 월 2018](release-notes-april-2018.md)
* [릴리스 정보 - 2017년 10월](release-notes-october-2017.md)
* [릴리스 정보 - 2016년 8월](release-notes-august-2016.md)
* [릴리스 정보 - 2016년 5월](release-notes-may-2016.md)
* [릴리스 정보 - 2016년 3월](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>혼합 현실 헤드셋 및 동작 컨트롤러 드라이버 릴리스 기록 ###

이 드라이버는 Windows 업데이트를 통해 자동으로 다운로드 및 설치 되지만 다운로드 링크는 인라인으로 제공 됩니다.

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, 버전 2004 (2020 업데이트 될 수 있음) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 2021년 3월 23일  | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>다른 헤드셋과 일관 되도록 HP 반향 G2에 대 한 숨겨진 영역 메시의 굴곡 순서를 업데이트 합니다.</li><li>HP 반향 G2 헤드셋의 시각적 품질 향상</li><li>Windows Mixed Reality 헤드셋 플랫폼 및 안정성 향상.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020 년 12 월 10 일  | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>일부 컨트롤러에 작동 하지 않는 트리거가 있는 문제를 해결 하기 위한 HP 컨트롤러의 새 컨트롤러 펌웨어</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020 년 10 월 8 일  | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>HP 반향 G2, HP Omnicept 및 새 HP 컨트롤러에 대 한 공식적인 지원.</li><li>HP 반향 및 Samsung Odyssey + 헤드셋의 보조 디스플레이 수정 [Os 빌드 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 이상 또는 [os 빌드 18362.1110 및 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 이상이 필요 합니다.</li><li>컴퓨터 전원 상태를 절전 모드로 전환 하는 기능이 향상 되어 SWW 1-4 오류가 줄어듭니다.</li><li>Windows Mixed Reality 헤드셋 플랫폼은 사소한 수정과 안정성을 개선 합니다.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020년 5월 7일      | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>Windows Mixed Reality 헤드셋 플랫폼은 사소한 수정과 안정성을 개선 합니다.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, 버전 1903 (2019 업데이트 될 수 있음) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019년 10월 14일      | Windows 10, 버전 1809 및 최신 버전과 호환 됩니다.<br/><ul><li>Windows Mixed Reality 헤드셋 플랫폼 사소한 수정 사항입니다.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019년 6월 24일      | Windows 10, 버전 1809 및 최신 버전과 호환 됩니다.<br/><ul><li>Windows Mixed Reality 헤드셋 플랫폼 및 절전 모드 컴퓨터와 전원 상태 전환에 대 한 안정성 향상.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 년 5 월 1일      | Windows 10, 버전 1809 및 최신 버전과 호환 됩니다.<br/><ul><li>2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo 및 Medion Windows Mixed Reality 헤드셋의 펌웨어 업데이트가 포함 되어 있습니다. 이 펌웨어 업데이트는 특정 그래픽 어댑터나 그래픽 드라이버를 사용 하 여 헤드셋 표시 호환성과 안정성을 향상 시킵니다.</li><li>Windows Mixed Reality 헤드셋 플랫폼 및 안정성 향상</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, 버전 1803 (4 월 2018 업데이트) 및 버전 1809 (10 월 2018 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019 년 1 월 2 일      | Windows 10, 버전 1803 및 최신 버전과 호환 됩니다.<br/><ul><li>헤드셋 추적 지터 및 끊길 수정</li><li>손전등 모드 안정성 수정</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018 년 10 월 1 일      | Windows 10 용 드라이버의 최초 공개 릴리스 버전 1809.<br/>Windows 10, 버전 1803 및 최신 버전과 호환 됩니다.<br/><ul><li>Windows 10, 버전 1809에서 손전등 모드와 같은 새로운 Windows Mixed Reality 기능을 사용 하도록 설정 합니다.</li><li>헤드셋 추적 및 안정성 향상</li><li>동작 컨트롤러 추적 및 성능 향상</li><li>USB 성능 및 향상 된 기능</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018년 4월 27일      | Windows 10 버전 1803 용 드라이버의 초기 공개 릴리스<br/> <ul><li>헤드셋 추적 및 안정성 향상</li><li>동작 컨트롤러 추적 및 성능 향상</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, 버전 1709 (이 하 크리에이터 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018 년 2 월 6 일    | <ul><li>3Glasses S2 S2 혼합 현실 헤드셋의 공식 지원</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017년 12월 19일   | <ul><li>일부 Pc에서 *잘못* 된 오류 코드 2181038087-7이 발생 하는 HID 문제를 해결 합니다.</li><li>다양 한 안정성 및 안정성 수정</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017년 12월 5일    | <ul><li>향상 된 헤드셋 추적</li><li>동작 컨트롤러 터치 패드 응답성 향상</li><li>드라이버 설치가 때때로 실패할 수 있는 문제를 해결 합니다.</li><li>다양 한 안정성 및 안정성 수정</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 11 월 21 일, 2017   | <ul><li>가끔씩 헤드셋을 사용 하는 동안 검정색으로 이동 하는 문제를 해결 합니다.</li><li>때때로 동작 컨트롤러의 사라짐 문제를 해결 합니다.</li><li>Dell 센터 헤드셋의 현재 상태 센서 성능 향상</li><li>다양 한 안정성 및 안정성 수정</li></ul> |
   | 10.0.16299.1036  | 2017 년 11 월 7 일    | <ul><li>정비공 개선 사항을 throw 하는 동작 컨트롤러:<ul><li>이제 위치 정확도가 근사치 인 경우 이제는 속도를 올바르게 보고 하므로 이제 헤드 뒤에를 throw 할 수 있습니다.</li><li>Throw를 위한 예제 코드는 [여기](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)의 "ThrowingStarter" unity 패키지에서 찾을 수 있습니다. 시작에 대 한 throw 장면 열기</li></ul></li><li>향상 된 이동 컨트롤러 배터리 보고</li><li>다양 한 안정성 및 안정성 수정</li></ul> |
   | 10.0.16299.1012  | 2017년 10월 17일    | 드라이버의 초기 공개 릴리스                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>혼합 현실 동작 컨트롤러 모델 드라이버 릴리스 기록 ###

또한이 드라이버는 Windows 업데이트를 통해 자동으로 다운로드 및 설치 되지만 다운로드 링크는 인라인으로 제공 됩니다.

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, 버전 2004 (2020 업데이트 될 수 있음)

| 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020 년 9 월 16 일      | 새 HP 모션 컨트롤러에 대 한 드라이버의 초기 공개 릴리스입니다. Windows 10, 버전 1903 및 최신 버전과 호환 됩니다. 이 드라이버는 새로운 HP 동작 컨트롤러와만 호환 됩니다.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, 버전 1803 (4 월 2018 업데이트) 및 버전 1809 (10 월 2018 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018 년 10 월 1 일      | Windows 10 용 드라이버의 최초 공개 릴리스 버전 1809. Windows 10, 버전 1803 및 최신 버전과 호환 됩니다.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018년 4월 17일      | Windows 10 용 드라이버의 최초 공개 릴리스 버전 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, 버전 1709 (이 하 크리에이터 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017년 10월 17일    | 드라이버의 초기 공개 릴리스                          |

### <a name="mixed-reality-portal-release-history"></a>혼합 현실 포털 릴리스 기록 ###

Windows 10 버전 1809 이상에서 [혼합 현실 포털](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 은 Microsoft Store 앱을 통해 업데이트 됩니다.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, 버전 1809 이상 ####

   | 버전            | 출시 날짜          | 주요 변경 내용                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21041.1051.0  | 2020 4 월 26 일        | <ul><li>혼합 현실 포털에 대 한 앱 아이콘을 업데이트 합니다.</li></ul>  |
   | 2000.20111.1381.0  | 2020 년 12 월 10 일        | <ul><li>혼합 현실 포털의 방문 페이지를 업데이트 합니다.</li><li>펌웨어를 업데이트 하는 동안 헤드셋 연결 오류가 줄어듭니다. </li></ul>  |
   | 2000.20071.1133.0  | 2020년 8월 5일        | <ul><li>[OpenXR](/windows/mixed-reality/openxr) 을 지원 하 여 미리 보기 창을 일시 중지 합니다.</li></ul>  | 
   | 2000.20041.1212.0  | 2020년 5월 11일          | <ul><li>일치 하지 않는 15-5 오류가 발생 한 타이밍 문제를 해결 합니다.</li><li>인터넷에 연결 되지 않은 Windows Mixed Reality 실행에 대 한 지원 향상.</li><li>**설치 컨트롤러** 를 통해 동작 컨트롤러를 페어링 하는 기능이 향상 되었습니다.</li></ul>  | 
   | 2000.20031.1202.0  | 2020년 4월 14일        | <ul><li>Windows Mixed Reality 정보, 팁 및 제안에 대 한 등록 지원.</li></ul>  | 
   | 2000.20011.1312.0  | 2020년 2월 11일     | <ul><li>2019 년 5 월 업데이트를 사용 하는 장치에서 [OpenXR](/windows/mixed-reality/openxr) 를 사용 하는 응용 프로그램에 대 한 지원 향상</li><li>접근성 및 키보드 포커스 문제를 해결 합니다.</li></ul>  | 
   | 2000.19101.1211.0  | 2019 년 11 월 11 일     | <ul><li>는 대화방 경계 시각적 개체를 전환 하지 못하도록 하는 문제를 해결 합니다.</li><li>실내 경계 설정 중 헤드셋을 가운데에 맞추지 못하게 하는 문제를 해결 합니다.</li></ul>  | 
   | 2000.19081.1301.0  | 2019년 9월 23일    | <ul><li>하드웨어 문제가 있는 헤드셋이 잘못 된 오류 메시지를 표시 하는 문제를 해결 합니다. 이전 버전에서 1-4 오류 코드를 받은 사용자는 이제 장치 상태에 대 한 보다 구체적인 오류 코드를 받을 수 있습니다.</li></ul>  |
   | 2000.19071.1302.0  | 2019년 8월 13일     | <ul><li>2019 년 5 월 업데이트를 사용 하는 장치에서 [OpenXR](/windows/mixed-reality/openxr) 를 사용 하는 응용 프로그램 지원.</li></ul>  | 
   | 2000.19061.1011.0  | 2019년 7월 16일         | <ul><li>JSON 구성 옵션을 지원 하 여 앱 동작을 사용자 지정 합니다. 자세한 내용은을 참조 https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup 하세요.</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 릴리스 기록 ###

SteamVR에 대 한 밸브의 릴리스 정보는 다음 위치에서 찾을 수 있습니다. [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 릴리스 내역에 대 한 Windows Mixed Reality ###

Windows Mixed Reality for SteamVR 구성 요소에 대 한 릴리스 정보는 다음 위치에서 찾을 수 있습니다. [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
