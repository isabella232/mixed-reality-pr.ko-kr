---
title: 소프트웨어 개요 및 릴리스 기록
description: Windows Mixed Reality, 모던 헤드셋 및 릴리스 기록을 위한 주요 소프트웨어 구성 요소에 대 한 개요입니다.
author: qianw211
ms.author: v-qianwen
ms.date: 10/5/2021
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 소프트웨어 구성 요소, 릴리스 기록, 릴리스 정보, 버전 기록
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: b27006790d48107bdb19c7afa59e9c8adbda45b1
ms.sourcegitcommit: 289cefbe479d6e0f4451a618bf926e4b08b50260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129593381"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>혼합 현실 소프트웨어 개요 및 릴리스 기록

## <a name="introduction-to-mixed-reality-software"></a>혼합 현실 소프트웨어 소개

Windows Mixed Reality는 다음과 같은 주요 소프트웨어 구성 요소로 구성 됩니다.

1. 기본 Windows Mixed Reality 환경을 제공 하는 **혼합 현실 포털**
    * Windows 10 버전 1709 및 1803에서 혼합 현실 포털은 Windows 업데이트를 통해 업데이트 된 Windows 10 운영 체제의 주요 구성 요소입니다.
    * Windows 10 버전 1809 이상에서 혼합 현실 포털은 Microsoft Store 앱을 통해 업데이트 됩니다.
    * Windows 11 버전 21h2에서 혼합 현실 포털은 Microsoft Store 앱을 통해 업데이트 됩니다.
2. 혼합 현실 포털의 첫 실행 중에는 **혼합 현실 주문형 패키지 (주문형 패키지** )가 자동으로 다운로드 및 설치 됩니다. 패키지에 대 한 자세한 내용은 여기를 참조 [하세요](/windows/application-management/manage-windows-mixed-reality) .
3. **혼합 현실 헤드셋 및 동작 컨트롤러 드라이버**(HoloLens 센서 드라이버 라고도 함)는 Windows Mixed Reality 헤드셋이 Windows Mixed Reality에서 작동할 수 있도록 하는 주요 드라이버 패키지입니다. 이는 혼합 현실 헤드셋이 연결 된 경우 Windows 업데이트를 통해 자동으로 다운로드 및 설치 되며를 통해 정기적으로 업데이트 됩니다 Windows 업데이트
4. * * 혼합 현실 동작 컨트롤러 모델 드라이버는 혼합 현실 동작 컨트롤러의 3D 모델을 포함 하며 타사 혼합 현실 환경에 필요 합니다. 이는 혼합 현실 동작 컨트롤러가 PC와 쌍으로 연결 되 고 처음으로 업데이트 될 때 Windows 업데이트를 통해 자동으로 다운로드 및 설치 됩니다 Windows 업데이트
5. **Windows 10 버전 1709 (에 지 작성자의 업데이트) 이상** 에는를 지 원하는 핵심 OS 구성 요소 및 기술이 포함 되어 Windows Mixed Reality

SteamVR에서 Windows Mixed Reality를 사용 하려면 다음 소프트웨어가 필요 합니다.

6. 스트림에서 가상 현실 앱 및 게임을 활성화 하는 밸브가 Corporation에서 개발 하 고 유지 관리 하는 **SteamVR**. 자세한 내용은 [여기](https://go.microsoft.com/fwlink/?linkid=862788)를 참조하세요.
7. SteamVR 구성 요소 **에 대 한 Windows Mixed Reality** Windows Mixed Reality와 SteamVR를 연결 합니다. 이 구성 요소에 대 한 자세한 내용은 [SteamVR에 대 한 Windows Mixed Reality 페이지에서](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 찾을 수 있습니다.

Windows Mixed Reality 헤드셋 관리:

8. 각 헤드셋 제조업체에서 개발 하 고 유지 관리 하는 **장치 도우미 앱** 은 Windows Mixed Reality 헤드셋에 대 한 간략 한 소개를 제공 합니다. 기본 제공 Bluetooth 기능이 포함 된 헤드셋에서 장치 도우미 앱을 사용 하면 동작 컨트롤러를 공장 Bluetooth 페어링으로 복원할 수 있습니다. 일부 헤드셋 (예: Samsung Odyssey 및 Samsung Odyssey +)은 장치 도우미 앱을 사용 하 여 헤드셋 제조업체의 헤드셋 펌웨어 업데이트를 제공 합니다. 이 앱은 헤드셋이 처음 연결 될 때 자동으로 다운로드 되며 Windows 시작 메뉴에서 찾을 수 있습니다.

## <a name="windows-11-release-notes---october-2021"></a>Windows 11 릴리스 정보-10 월 2021

### <a name="infinite-expanse"></a>무한 Expanse

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* Windows Mixed Reality 장치에 대 한 새로운 가상 홈 환경으로, 범위와 크기를 크게 줄일 수 있으며, 더 많은 기능을 갖춘 cliffhouse 대신 단일 단계로 간소화 됩니다. 
* 성능 향상을 위해 작성 된 무한 Expanse는 고객이 게임과 경험을 최대한 활용할 수 있도록 하는 리소스를 많이 사용 하는 가상 홈 환경에 대 한 장기 고객 요청을 해결 하도록 설계 되었습니다. 
* 이 새 가상 홈 환경은 **위치** 메뉴 내의 **핀 패널** 에서 찾을 수 있습니다. 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>혼합 현실 SteamVR boot 포털 시작

* WMR가 시작 될 때 SteamVR를 자동으로 시작 하 여 WMR 홈 공간을 무시 하 고 SteamVR로 직접 이동할 수 있도록 하는 새로운 설정입니다.
   * 이 새로운 설정은 **설정** 앱의 **혼합 현실 > 시작 및 데스크톱 > 자동 시작** 에서 찾을 수 있습니다.
    
### <a name="new-startup-experience-settings"></a>새 시작 환경 설정

* 혼합 현실 포털이 시작 될 때 제어 수준을 높여 이상적인 시작 환경을 구성 하는 데 사용할 수 있는 새로운 설정입니다.
* 이제 장치가 연결 될 때 또는 상태 센서가 활성화 될 때 혼합 현실 포털을 시작할지 여부를 제어 하 고, 가상 데스크톱 앱을 여는 방법을 제어할 수 있습니다.
* 이러한 새 설정은 **설정** 앱의 **혼합 현실 > 시작 및 바탕 화면** 에서 찾을 수 있습니다.
    * HMD 플러그 인에서 MRP 시작으로 전환 합니다.
    * 현재 상태가 검색 되 면 MRP를 시작 하려면 전환 합니다.
    * 데스크톱 앱에서 오픈 데스크톱 앱 포커스를 설정 합니다.

### <a name="prior-release-notes"></a>이전 릴리스 정보

* [릴리스 정보-2020 년 5 월](release-notes-may-2020.md)
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
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020 년 10 월 8 일  | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>HP 반향 G2, HP Omnicept 및 새 HP 컨트롤러에 대 한 공식적인 지원.</li><li>HP 반향 및 Samsung Odyssey + 헤드셋의 보조 디스플레이 수정 [Os 빌드 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 이상 또는 [os 빌드 18362.1110 및 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 이상이 필요 합니다.</li><li>컴퓨터 전원 상태를 절전 모드로 전환 하는 기능이 향상 되어 SWW 1-4 오류가 줄어듭니다.</li><li>Windows Mixed Reality 헤드셋 플랫폼 사소한 수정 및 안정성 향상|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020년 5월 7일      | Windows 10, 버전 1903 및 최신 버전과 호환 됩니다.<br/><ul><li>Windows Mixed Reality 헤드셋 플랫폼 사소한 수정 및 안정성 향상</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, 버전 1903 (2019 업데이트 될 수 있음) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019년 10월 14일      | Windows 10, 버전 1809 이상 버전과 호환 됩니다.<br/><ul><li>Windows Mixed Reality 헤드셋 플랫폼의 사소한 수정 사항입니다.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019년 6월 24일      | Windows 10, 버전 1809 이상 버전과 호환 됩니다.<br/><ul><li>절전 모드의 컴퓨터 및 전원 상태 전환에 대 한 Windows Mixed Reality 헤드셋 플랫폼 및 안정성 향상</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 년 5 월 1일      | Windows 10, 버전 1809 이상 버전과 호환 됩니다.<br/><ul><li>2017 acer, Asus, Dell, Fujitsu, HP, Lenovo 및 Medion Windows Mixed Reality 헤드셋의 펌웨어 업데이트가 포함 되어 있습니다. 이 펌웨어 업데이트는 특정 그래픽 어댑터나 그래픽 드라이버를 사용 하 여 헤드셋 표시 호환성과 안정성을 향상 시킵니다.</li><li>Windows Mixed Reality 헤드셋 플랫폼 및 안정성 향상</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, 버전 1803 (4 월 2018 업데이트) 및 버전 1809 (10 월 2018 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019년 1월 2일      | Windows 10 버전 1803 이상과 호환 가능합니다.<br/><ul><li>헤드셋 추적 지터 및 스텁 수정</li><li>손전등 모드 안정성 수정</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018년 10월 1일      | Windows 10, 버전 1809 드라이버의 초기 공개 릴리스입니다.<br/>Windows 10 버전 1803 이상과 호환 가능합니다.<br/><ul><li>Windows 10, 버전 1809 손전등 모드와 같은 새로운 Windows Mixed Reality 기능을 사용하도록 설정합니다.</li><li>헤드셋 추적 및 안정성 향상</li><li>모션 컨트롤러 추적 및 성능 향상</li><li>USB 성능 및 개선</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018년 4월 27일      | Windows 10 버전 1803용 드라이버의 초기 공개 릴리스<br/> <ul><li>헤드셋 추적 및 안정성 향상</li><li>모션 컨트롤러 추적 및 성능 향상</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 버전 1709(Fall Creators Update) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018년 2월 6일    | <ul><li>3Glasses Blubur S2 Mixed Reality 헤드셋에 대한 공식 지원</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017년 12월 19일   | <ul><li>일부 PC에서 *잘못된 오류* 코드 2181038087-7로 이어지는 HID 문제를 해결합니다.</li><li>다양한 안정성 및 안정성 수정</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017년 12월 5일    | <ul><li>향상된 헤드셋 추적</li><li>모션 컨트롤러 터치 패드 응답성 향상</li><li>드라이버 설치가 때때로 실패할 수 있는 문제를 해결합니다.</li><li>다양한 안정성 및 안정성 수정</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017년 11월 21일   | <ul><li>헤드셋 디스플레이를 사용하는 동안 가끔 검은색으로 표시하는 문제를 해결합니다.</li><li>경우에 따라 모션 컨트롤러가 사라지는 문제를 해결합니다.</li><li>Dell Visor 헤드셋의 현재 상태 센서 성능 향상</li><li>다양한 안정성 및 안정성 수정</li></ul> |
   | 10.0.16299.1036  | 2017년 11월 7일    | <ul><li>동작 컨트롤러 throw 메커니즘 개선 사항:<ul><li>이제 위치 정확도가 근사치일 때 속도가 제대로 보고되므로 이제 머리 뒤에서 을 throw할 수 있습니다.</li><li>throw에 대한 예제 코드는 여기의 "ThrowingStarter" unity 패키지에서 찾을 수 [있습니다.](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/) throw하는 장면을 열어 시작합니다.</li></ul></li><li>향상된 모션 컨트롤러 배터리 보고</li><li>다양한 안정성 및 안정성 수정</li></ul> |
   | 10.0.16299.1012  | 2017년 10월 17일    | 드라이버의 초기 공개 릴리스                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Mixed Reality 모션 컨트롤러 모델 드라이버 릴리스 기록 ###

이 드라이버는 Windows 업데이트를 통해 자동으로 다운로드되고 설치되지만 다운로드 링크는 인라인으로 제공됩니다.

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 버전 2004(2020년 5월 업데이트)

| 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020년 9월 16일      | 새 HP Motion Controller에 대한 드라이버의 초기 공개 릴리스입니다. Windows 10 버전 1903 이상과 호환 가능합니다. 이 드라이버는 새 HP 모션 컨트롤러와만 호환됩니다.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, 버전 1803(2018년 4월 업데이트) 및 버전 1809(2018년 10월 업데이트) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018년 10월 1일      | Windows 10, 버전 1809 드라이버의 초기 공개 릴리스입니다. Windows 10 버전 1803 이상과 호환 가능합니다.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018년 4월 17일      | Windows 10 버전 1803용 드라이버의 초기 공개 릴리스입니다.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 버전 1709(Fall Creators Update) ####

   | 버전          | 출시 날짜          | 주요 변경 내용                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017년 10월 17일    | 드라이버의 초기 공개 릴리스                          |

### <a name="mixed-reality-portal-release-history"></a>Mixed Reality 포털 릴리스 기록 ###

Windows 10, 버전 1809 이상에서는 [Microsoft Store](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 앱을 통해 Mixed Reality 포털 업데이트됩니다.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, 버전 1809 이상 ####

   | 버전            | 출시 날짜          | 주요 변경 내용                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 2021년 6월 8일          | <ul><li>일반적인 헤드셋 오류에 대한 문제 해결 링크를 도움말 앱에 추가합니다.</li><li>초기 설정 중에 헤드셋 디바이스 도우미 앱을 건너뛸 수 있는 문제를 해결합니다.</li><li>고해상도 헤드셋에 대한 추가 정보로 시스템 요구 사항 페이지를 업데이트합니다.</li><li>시작 화면 및 방문 페이지를 새 시각적 개체로 업데이트합니다.</li></ul>  |
   | 2000.21041.1051.0  | 2021년 4월 26일        | <ul><li>Mixed Reality 포털 대한 앱 아이콘을 업데이트합니다.</li></ul>  |
   | 2000.20111.1381.0  | 2020년 12월 10일     | <ul><li>Mixed Reality 포털 방문 페이지를 업데이트합니다.</li><li>펌웨어를 업데이트 하는 동안 헤드셋 연결 오류가 줄어듭니다. </li></ul>  |
   | 2000.20071.1133.0  | 2020년 8월 5일        | <ul><li>[OpenXR](/windows/mixed-reality/openxr) 을 지원 하 여 미리 보기 창을 일시 중지 합니다.</li></ul>  | 
   | 2000.20041.1212.0  | 2020년 5월 11일          | <ul><li>일치 하지 않는 15-5 오류가 발생 한 타이밍 문제를 해결 합니다.</li><li>인터넷에 연결 되지 않은 Windows Mixed Reality 실행에 대 한 지원이 향상 되었습니다.</li><li>**설치 컨트롤러** 를 통해 동작 컨트롤러를 페어링 하는 기능이 향상 되었습니다.</li></ul>  | 
   | 2000.20031.1202.0  | 2020년 4월 14일        | <ul><li>Windows Mixed Reality에 대 한 정보, 팁 및 제안을 위한 등록 지원.</li></ul>  | 
   | 2000.20011.1312.0  | 2020년 2월 11일     | <ul><li>2019 년 5 월 업데이트를 사용 하는 장치에서 [OpenXR](/windows/mixed-reality/openxr) 를 사용 하는 응용 프로그램에 대 한 지원 향상</li><li>접근성 및 키보드 포커스 문제를 해결 합니다.</li></ul>  | 
   | 2000.19101.1211.0  | 2019년 11월 11일     | <ul><li>는 대화방 경계 시각적 개체를 전환 하지 못하도록 하는 문제를 해결 합니다.</li><li>실내 경계 설정 중 헤드셋을 가운데에 맞추지 못하게 하는 문제를 해결 합니다.</li></ul>  | 
   | 2000.19081.1301.0  | 2019년 9월 23일    | <ul><li>하드웨어 문제가 있는 헤드셋이 잘못 된 오류 메시지를 표시 하는 문제를 해결 합니다. 이전 버전에서 1-4 오류 코드를 받은 사용자는 이제 장치 상태에 대 한 보다 구체적인 오류 코드를 받을 수 있습니다.</li></ul>  |
   | 2000.19071.1302.0  | 2019년 8월 13일     | <ul><li>2019 년 5 월 업데이트를 사용 하는 장치에서 [OpenXR](/windows/mixed-reality/openxr) 를 사용 하는 응용 프로그램 지원.</li></ul>  | 
   | 2000.19061.1011.0  | 2019년 7월 16일         | <ul><li>JSON 구성 옵션을 지원 하 여 앱 동작을 사용자 지정 합니다. [Windows Mixed Reality를 사용 하 여 위치 기반 엔터테인먼트에 대 한](/windows/mixed-reality/location-based-experiences#setup)자세한 내용은 설치를 참조 하세요.</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 릴리스 기록 ###

SteamVR에 대 한 밸브의 릴리스 정보는 다음 위치에서 찾을 수 있습니다. [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 릴리스 기록에 대 한 Windows Mixed Reality ###

SteamVR 구성 요소에 대 한 Windows Mixed Reality 릴리스 정보는 다음 위치에서 찾을 수 있습니다.[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
