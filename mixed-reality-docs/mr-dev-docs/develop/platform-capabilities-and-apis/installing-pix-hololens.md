---
title: HoloLens 용 PIX 설치 2
description: HoloLens 2 장치에 대해 PIX를 설치 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, 캡처, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615428"
---
# <a name="installing-pix-for-hololens-2"></a>HoloLens 용 PIX 설치 2

[PIX](https://devblogs.microsoft.com/pix) 는 Windows의 DirectX 12 응용 프로그램에 대 한 성능 조정 및 디버깅 도구입니다. 

## <a name="setup"></a>설정

1. 호스트 PC에서 최신 PIX [릴리스]( https://devblogs.microsoft.com/pix/download) 를 잡고 USB 케이블을 통해 HoloLens 2를 PC에 연결 합니다.

2. HoloLens 2가 [Windows 참가자 빌드](https://insider.windows.com) 에 있거나 PIX를 중단 하는 구성을 포함 하는 경우  [장치를 다시 플래시](https://docs.microsoft.com/hololens/hololens-recovery) 하 여 모든 데이터를 지웁니다.

3. **개발자 모드** 및 **장치 포털** 을 사용 하도록 설정 합니다.

* 셸에서 **설정** 열기:

![설정 단추가 강조 표시 된 HoloLens 메뉴 스크린샷](images/pix-img-01.jpg)

* **업데이트 & 보안** 을 선택 합니다.

![업데이트 및 보안 단추가 강조 표시 된 HoloLens에서 열린 설정 창의 스크린샷](images/pix-img-02.jpg)

* **개발자를 위해를 클릭 합니다**.

![개발자 단추가 강조 표시 된 보안 및 업데이트 창의 스크린샷](images/pix-img-03.jpg)

* **개발자 기능 사용** 및 **장치 포털 사용 설정**

![장치 포털 활성화 단추가 강조 표시 된 설정에서 열린 개발자 창의 스크린샷](images/pix-img-04.jpg)

![개발 기능 사용이 강조 표시 된 설정으로 열려 있는 개발자 창의 스크린샷](images/pix-img-05.jpg)

* 장치를 계속 연결 하 고, 사용자가 로그인 한 상태에서 Visual Studio를 시작 합니다.

> [!IMPORTANT]
> 장치가 대기 모드 또는 절전 모드에 있지 않은지 확인 합니다. 이 단계에서 문제가 발생 하는 경우 [Windows 장치 포털 지침](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)을 참조 하세요.

## <a name="preparing-for-deployment"></a>배포 준비

1. Visual Studio에서 **ARM64** 를 플랫폼으로 설정 **하 고 장치를 장치로 설정** 합니다.

![플랫폼 및 장치 설정이 강조 표시 된 visual 스튜디오 솔루션 스크린샷](images/pix-img-06.png)

2. Visual Studio에서 장치의 **PIN** 을 입력 하 라는 메시지가 표시 되 면 다음을 수행 합니다.

![PIN을 요청 하는 visual studio 팝업의 스크린샷](images/pix-img-07.png)

* 셸에서 **설정** 선택
* **업데이트 & 보안** 선택
* **개발자 용** 을 클릭 하 고 **장치 검색** 아래에서 쌍을 누릅니다. 

![장치 검색이 강조 표시 된 설정에서 열린 개발자 창의 스크린샷](images/pix-img-08.jpg)

![등록 코드가 강조 표시 된 유료 장치 팝업의 스크린샷](images/pix-img-09.jpg)

* Visual Studio에서 생성 된 PIN 번호 입력

3. Visual Studio에서 연결 된 HoloLens 2에 앱을 배포 합니다. 앱에 따라 몇 분 정도 걸릴 수 있습니다.

## <a name="launching-pix"></a>PIX 시작

먼저 장치 포털을 사용 하 여 HoloLens 2에서 앱이 실행 되 고 있지 않은지 확인 합니다. 그런 다음, PIX를 시작 하 고 장치에 연결한 다음 **홈** 을 클릭 합니다.

![PIX 응용 프로그램 홈 화면의 스크린샷](images/pix-img-10.png)

* 왼쪽 메뉴에서 **연결** 을 선택 합니다.

![연결 단추가 강조 표시 된 PIX 응용 프로그램 왼쪽 메뉴의 스크린샷](images/pix-img-11.png)

2. **컴퓨터** 탭에서 **추가** 를 클릭 하 고 다음 자격 증명을 입력 합니다.
    * 별칭: 사용자의 재량
    * 호스트 이름 또는 IP 주소: 127.0.0.1

3. **컴퓨터** 탭의 오른쪽 아래에 있는 **연결** 을 클릭 합니다.

![별칭, 호스트 이름, IP 주소 및 추가 단추가 강조 표시 된 PIX 응용 프로그램 연결 창의 스크린샷](images/pix-img-12.png)

> [!NOTE]
> 이진 파일을 복사 하는 중이기 때문에 첫 번째 연결은 항상 느립니다.

4. PIX가 HoloLens 2에 연결 된 경우 UWP 시작 탭의 **대상 프로세스 선택** 섹션에서 앱을 찾고 **시작** 을 클릭 합니다.

![대상 프로세스 선택 창 및 시작 단추가 강조 표시 된 PIX 응용 프로그램의 스크린샷](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU 캡처

1. **Gpu 캡처** 섹션에서 **Photo** 를 클릭 하 여 gpu 캡처를 시작 합니다.

![GPU 캡처가 강조 표시 된 PC 연결 패널이 열려 있는 PIX 응용 프로그램의 스크린샷](images/pix-img-14.png)

2. **GPU 캡처** 패널에서 생성 된 스크린샷을 클릭 하 여 분석을 위한 캡처를 엽니다.

![Gpu 캡처 패널이 강조 표시 된 PIX 응용 프로그램의 스크린샷 강조 표시 된 gpu 캡처](images/pix-img-15.png)

3. **시작** 을 눌러 분석을 시작 합니다.

![PIX 응용 프로그램의 스크린샷 강조 표시 된 시작 단추](images/pix-img-16.png)

> [!IMPORTANT]
> GPU 캡처 후 타이밍 데이터를 수집 하는 경우 헤드셋을 다시 부팅 해야 합니다. 이는 장치를 한 번만 다시 시작 하며 타이밍 데이터 수집에 필요 합니다.

이제 PIX를 사용할 준비가 되었습니다.

## <a name="see-also"></a>참고 항목
* [PIX 홈페이지](https://devblogs.microsoft.com/pix)