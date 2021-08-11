---
title: 릴리스 정보 - 2016년 8월
description: 2016에 대 한 Windows 10 기념일 릴리스에 대 한 HoloLens 릴리스 정보를 최신 상태로 유지 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 릴리스 정보, os, 플랫폼, 기능, 상용 제품군
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202468"
---
# <a name="release-notes---august-2016"></a>릴리스 정보 - 2016년 8월

HoloLens 팀은 Windows Insider Program의 개발자가 작업의 우선 순위를 지정 하는 피드백을 수신 대기 합니다. 피드백 허브, [개발자 포럼](https://forums.hololens.com) [ @HoloLens 및 Twitter ](https://twitter.com/hololens)를 통해 피드백을 계속 해 서 [보내 주세요](/windows/mixed-reality/give-us-feedback) . 기념일 업데이트를 수용 하는 Windows 10 HoloLens 팀은 holographic 환경에 대 한 향상 된 기능을 제공 합니다. 이 업데이트에서는 중요 한 수정 사항, 개선 사항 및 비즈니스에서 요청 하 고 Microsoft HoloLens Commercial Suite에서 제공 하는 기능 소개에 초점을 맞추고 있습니다.

**최신 릴리스:** Windows Holographic 8 월 2016 업데이트 (**10.0.14393.0**, Windows 10 기념일 릴리스)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

[현재 릴리스로 업데이트](/windows/mixed-reality/updating-hololens)하려면 *설정* 앱을 열고 *업데이트 & 보안* 으로 이동한 후 *업데이트 확인* 단추를 선택 합니다.

## <a name="new-features"></a>새로운 기능

프로세스 **디버깅에 연결** HoloLens 이제 프로세스 간 디버깅을 지원 합니다. Visual Studio 2015 업데이트 3을 사용 하 여 HoloLens에서 실행 중인 앱에 연결 하 고 [디버깅을 시작할](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app)수 있습니다. 이는 Visual Studio 프로젝트에서 배포할 필요 없이 작동 합니다.

**업데이트 된 HoloLens Emulator** 업데이트 된 버전의 HoloLens Emulator도 릴리스 했습니다.

**게임 패드 지원** 이제 HoloLens를 사용 하 여 Bluetooth gamepads를 페어링 하 고 사용할 수 있습니다. 새로 릴리스된 Xbox 무선 컨트롤러는 Bluetooth 기능을 제공 하며, 즐겨 사용 하는 게임 패드를 사용 하는 게임 및 앱을 재생 하는 데 사용할 수 있습니다. Xbox 무선 컨트롤러 S를 HoloLens 연결 하려면 먼저 [컨트롤러 업데이트](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 를 적용 해야 합니다. Xbox 무선 컨트롤러는 [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) 및 Windows에서 지원 됩니다 [. 게임. 입력](/uwp/api/Windows.Gaming.Input) api. Windows를 통해 더 많은 Bluetooth 컨트롤러 모델에 액세스할 수 있습니다 [. 게이밍. 입력](/uwp/api/Windows.Gaming.Input) API.

## <a name="improvements-and-fixes"></a>향상된 기능 및 수정 프로그램

microsoft는 Windows 10 기념일 업데이트의 나머지 부분과 동기화 하 고 있으므로 HoloLens 특정 수정 사항 외에도 Windows 업데이트에서 제공 하는 모든 것을 받아 플랫폼 안정성과 성능을 향상 시킬 수 있습니다. 사용자 의견은 매우 중요 하며 릴리스에 대 한 수정 사항의 우선 순위를 지정 합니다.

다음 환경이 개선 되었습니다.
* 로그인 환경.
* 작업 영역 등에 join.
* 장치 전원 상태 전환에 대 한 전원 효율성.
* 혼합 현실 캡처의 안정성.
* Bluetooth 연결에 대 한 안정성
* 다중 앱 시나리오에서 홀로그램 지 속성

다음 문제를 해결 했습니다.
* Visual Studio 프로파일러 및 그래픽 디버거가 연결 되지 않습니다.
* 사진 & 문서는 장치 포털의 파일 탐색기에 표시 되지 않습니다.
* 조정 모드에서 커서를 위에 배치 하면 앱 바를 깜박일 수 있습니다.
* 조정 모드에 있을 때 눈에 주목 하는 커서 커서가 4 화살표 커서로 변경 됩니다.
* "Cortana 음악 재생"은 Groove을 시작 하지 않습니다.
* 이전 업데이트 후에 "이동 홈"은 핀 패널을 올바르게 표시 하지 않습니다.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens Commercial Suite 소개

Microsoft HoloLens Commercial Suite 엔터프라이즈 배포용으로 준비 됩니다. 초기 비즈니스 파트너 로부터 요청 된 [상업적 기능](/windows/mixed-reality/commercial-features) 을 몇 개 추가 했습니다.

Microsoft HoloLens Commercial Suite를 구매 하려면 로컬 Microsoft 계정 관리자에 게 문의 하세요.

### <a name="key-commercial-features"></a>주요 상업용 기능 

* **키오스크 모드.** HoloLens 키오스크 모드에서는 데모 또는 전시 환경을 사용 하기 위해 실행할 앱을 제한할 수 있습니다.<br>
  ![키오스크 모드를 사용 하면 선택한 앱으로 직접 HoloLens를 시작할.](images/201608-kioskmode-400px.png)
* **HoloLens용 MDM(모바일 장치 관리).** IT 부서에서 Microsoft Intune 같은 솔루션을 사용 하 여 여러 HoloLens 장치를 동시에 관리할 수 있습니다. 설정을 관리 하 고, 설치할 앱을 선택 하 고, 조직의 요구에 맞게 조정 된 보안 구성을 설정할 수 있습니다.<br>
  ![HoloLens의 모바일 장치 관리는 여러 장치에서 엔터프라이즈급 장치 관리를 제공 합니다.](images/201608-enterprisemanagement-400px.png)
* **비즈니스용 Windows 업데이트.** 장치에 대 한 제어 된 운영 체제 업데이트 및 장기 서비스 분기에 대 한 지원.
* **데이터 보안.** 다른 Windows 장치와 동일한 수준의 보안 보호 기능을 제공하도록 HoloLens에서 BitLocker 데이터 암호화가 사용됩니다.
* **작업 액세스.** 조직의 모든 사용자가 HoloLens의 가상 개인 네트워크를 통해 회사 네트워크에 원격으로 연결할 수 있습니다. HoloLens는 자격 증명이 필요한 Wi-Fi 네트워크에도 액세스할 수 있습니다.
* **비즈니스용 Microsoft Store.** IT 부서에서는 특정 HoloLens 사용에 대 한 회사 앱만 포함 하는 엔터프라이즈 개인 저장소를 설정할 수도 있습니다. 선택한 엔터프라이즈 사용자 그룹에 엔터프라이즈 소프트웨어를 안전하게 배포합니다.

### <a name="development-edition-vs-commercial-suite"></a>개발 버전 및 상용 제품군

<table>
<tr>
<th>기능</th><th>Development Edition</th><th>상용 제품군</th>
</tr><tr>
<td>장치 암호화 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>VPN(가상 사설망)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">키오스크 모드</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 관리 및 배포</th>
</tr><tr>
<td>MDM(모바일 디바이스 관리)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>등록 해제 차단 기능</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>인증서 기반 회사 Wi-Fi 액세스</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store(소비자)</td><td style="text-align: center;">소비자</td><td style="text-align: center;">MDM을 통해 필터링</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">비즈니스 Store 포털</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 보안 및 ID</th>
</tr><tr>
<td>AAD (Azure Active Directory를 사용 하 여 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft 계정 (MSA)으로 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>PIN 잠금 해제를 사용하는 차세대 자격 증명</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">보안 부팅</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 서비스 및 지원</th>
</tr><tr>
<td>도착 시 자동 시스템 업데이트</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>장기 서비스 분기</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>이전 릴리스 정보
* [릴리스 정보 - 2016년 5월](release-notes-may-2016.md)
* [릴리스 정보 - 2016년 3월](release-notes-march-2016.md)

## <a name="see-also"></a>추가 정보
* [HoloLens 알려진 문제](/windows/mixed-reality/hololens-known-issues)
* [상용 기능](/windows/mixed-reality/commercial-features)
* [도구 설치](/windows/mixed-reality/develop/install-the-tools)
* [HoloLens 에뮬레이터 사용](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)