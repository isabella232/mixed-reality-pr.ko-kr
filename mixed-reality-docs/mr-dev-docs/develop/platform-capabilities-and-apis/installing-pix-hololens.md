---
title: HoloLens 2용 PIX 설치
description: HoloLens 2 디바이스용 PIX를 설치하는 방법을 알아봅니다.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, 캡처, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217315"
---
# <a name="installing-pix-for-hololens-2"></a>HoloLens 2용 PIX 설치

[PIX는](https://devblogs.microsoft.com/pix) Windows DirectX 12 애플리케이션에 대한 성능 조정 및 디버깅 도구입니다. 

## <a name="setup"></a>설치 프로그램

1. 호스트 PC에서 최신 PIX [릴리스를]( https://devblogs.microsoft.com/pix/download) 받아 USB 케이블을 통해 HoloLens 2 PC에 연결합니다.

2. HoloLens 2 [Windows 참가자 빌드에](https://insider.windows.com) 있거나 PIX를 중단하는 구성이 있는 경우 [디바이스를 반사하여](/hololens/hololens-recovery) 모든 데이터를 지웁습니다.

3. **개발자 모드를** 사용하도록 설정하고 **를 장치 포털.**

* **Mixed Reality** Home에서 설정 엽니다.

![설정 단추가 강조 표시된 HoloLens 메뉴의 스크린샷](images/pix-img-01.jpg)

* **& 보안 업데이트를 선택합니다.**

![업데이트 및 보안 단추가 강조 표시된 HoloLens 열린 설정 창의 스크린샷](images/pix-img-02.jpg)

* **개발자용 을 선택합니다.**

![개발자용 단추가 강조 표시된 보안 및 업데이트 창이 열려 있는 스크린샷](images/pix-img-03.jpg)

* 개발자 **기능 사용** 및 **장치 포털 사용** 설정

![디바이스 포털 사용 단추가 강조 표시된 설정에서 열린 개발자용 창의 스크린샷](images/pix-img-04.jpg)

![개발 기능 사용 토글이 강조 표시된 설정에서 열린 개발자 창의 스크린샷](images/pix-img-05.jpg)

* 디바이스가 계속 연결되어 있고, 잠기고, 사용자가 로그인한 상태에서 Visual Studio 시작합니다.

> [!IMPORTANT]
> 디바이스가 대기 모드 또는 절전 모드에 있지 않은지 확인합니다. 이 단계에 문제가 있는 경우 [Windows 장치 포털 지침을 참조합니다.](./using-the-windows-device-portal.md)

## <a name="preparing-for-deployment"></a>배포 준비

1. Visual Studio **ARM64를** 플랫폼으로 설정하고 **디바이스를** 디바이스로 설정합니다.

![플랫폼 및 디바이스 설정이 강조 표시된 Visual Studios 솔루션의 스크린샷](images/pix-img-06.png)

2. Visual Studio 디바이스에서 **PIN을** 입력하라는 메시지가 표시되면 다음을 수행합니다.

![PIN을 요청하는 Visual Studio 팝업의 스크린샷](images/pix-img-07.png)

* 셸에서 **설정** 선택
* **& 보안 업데이트를 선택합니다.**
* **개발자용 을** 선택하고 디바이스 검색에서 페어링을 **누릅니다.** 

![디바이스 검색이 강조 표시된 설정에서 열린 개발자 창의 스크린샷](images/pix-img-08.jpg)

![등록 코드가 강조 표시된 유료 디바이스 팝업의 스크린샷](images/pix-img-09.jpg)

* 생성된 PIN 번호를 Visual Studio 입력합니다.

3. Visual Studio 연결된 HoloLens 2 앱을 배포하며, 앱에 따라 몇 분 정도 걸릴 수 있습니다.

## <a name="launching-pix"></a>PIX 시작

먼저 장치 포털 사용하여 앱이 HoloLens 2 실행되고 있지 않은지 확인합니다. 그런 다음, PIX를 시작하고, 디바이스에 연결하고, **홈을** 선택합니다.

![PIX 애플리케이션 홈 화면의 스크린샷](images/pix-img-10.png)

* 왼쪽 메뉴에서 **커넥트** 선택합니다.

![연결 단추가 강조 표시된 PIX 애플리케이션 왼쪽 메뉴의 스크린샷](images/pix-img-11.png)

2. **컴퓨터** 탭에서 **추가를** 선택하고 다음 자격 증명을 입력합니다.
    * 별칭: 사용자의 판단에 따라
    * 호스트 이름 또는 IP 주소: 127.0.0.1

3. **컴퓨터** 탭의 오른쪽 아래에서 **커넥트** 선택합니다.

![별칭, 호스트 이름, IP 주소 및 추가 단추가 강조 표시된 PIX 애플리케이션 연결 창의 스크린샷](images/pix-img-12.png)

> [!NOTE]
> 이진이 복사되기 때문에 첫 번째 연결은 항상 느립니다.

4. PIX가 HoloLens 2 연결된 경우 UWP 시작 탭의 **대상 프로세스 선택** 섹션에서 앱을 찾고 시작 을 선택합니다. 

![대상 프로세스 선택 창과 시작 단추가 강조 표시된 PIX 애플리케이션의 스크린샷](images/pix-img-13.png)

## <a name="gpu-captured"></a>캡처된 GPU

1. GPU 캡처 섹션에서 **사진을** 클릭하여 **GPU 캡처를** 시작합니다.

![GPU 캡처가 강조 표시된 PC 연결 패널이 열려 있는 PIX 애플리케이션의 스크린샷](images/pix-img-14.png)

2. GPU 캡처 패널에서 생성된 스크린샷을 클릭하여 분석용 **캡처를** 엽니다.

![GPU 캡처 패널이 강조 표시된 GPU 캡처 섹션이 열려 있는 PIX 애플리케이션의 스크린샷](images/pix-img-15.png)

3. **시작을** 눌러 분석을 시작합니다.

![시작 단추가 강조 표시된 PIX 애플리케이션의 스크린샷](images/pix-img-16.png)

> [!IMPORTANT]
> GPU 캡처를 받은 후 타이밍 데이터를 수집하는 경우 헤드셋을 다시 부팅해야 합니다. 이는 디바이스를 일회성으로 다시 시작하는 것이며 타이밍 데이터 수집에 필요합니다.

이제 PIX를 사용할 준비가 되었습니다.

## <a name="see-also"></a>추가 정보
* [PIX 홈페이지](https://devblogs.microsoft.com/pix)