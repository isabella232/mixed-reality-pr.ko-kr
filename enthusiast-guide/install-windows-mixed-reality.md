---
title: Windows Mixed Reality 소프트웨어 설치
description: Windows Mixed Reality 헤드셋을 연결한 후 혼합 현실 포털 앱을 사용 하 여 Windows Mixed Reality 기능을 시작 하 고 다운로드 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, 가상 현실, VR, MR, 시작 하기, 설정, 혼합 현실 포털
appliesto:
- Windows 10
ms.openlocfilehash: 5e04f29f834b2220f51f1748aa59e4188d8ad38d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686529"
---
# <a name="install-windows-mixed-reality-software"></a>Windows Mixed Reality 소프트웨어 설치

## <a name="launch-mixed-reality-portal"></a>혼합 현실 시작 포털

Windows Mixed Reality 헤드셋을 연결 하 고 드라이버를 성공적으로 설치한 후에는 혼합 현실 포털 (MRP)이 바탕 화면에서 자동으로 시작 됩니다. 자동으로 발생 하지 않는 경우 시작 메뉴 ( **혼합 현실 포털 시작 >** )에서 항상 mixed reality 포털을 시작할 수 있습니다. 포털이 시작 되 면 **시작** 을 클릭 합니다.

![혼합 현실 시작](images/1050px-mixedrealityportal.png)

혼합 현실 포털에서 다음을 수행할 수 있습니다.

* 헤드셋에서 보기의 라이브 스트림 표시 합니다 (Windows Mixed Reality Ultra만). 이 기능을 설정 및 해제 하려면 "미리 보기 중지" 또는 "미리 보기 시작"을 선택 합니다. 혼합 현실 시작 메뉴에서 미리 보기를 켜고 끌 수도 있습니다.
* 헤드셋 및 컨트롤러의 상태를 확인 합니다. 모든 정보를 보려면 "메뉴"를 선택 합니다.
* 새 컨트롤러를 설정 합니다. **메뉴 > 컨트롤러 설정** 을 선택 합니다.
* 경계를 설정 하거나 해제 합니다. **메뉴 > 경계 설정/해제** 를 선택 합니다. (이 기능을 해제 하는 경우 안전을 위해 한 곳에 유지 해야 합니다.)
* 새 경계를 만듭니다. 메뉴를 선택 하 **> 설치를 실행** 합니다.
* 혼합 현실 사진을 보세요. **메뉴 > 혼합 현실 사진을 참조** 하세요.
* 혼합 현실 앱과 게임을 받으세요. **메뉴 > 혼합 현실 앱 가져오기** 를 선택 합니다.

## <a name="download-windows-mixed-reality"></a>Windows Mixed Reality 다운로드

Windows Mixed Reality의 크기는 약 1GB 이며, 다운로드 시간은 인터넷 연결에 따라 달라 집니다. "Mixed Reality 소프트웨어를 다운로드할 수 없습니다." 라는 메시지가 나타나면 [문제 해결 단계](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading)를 확인 하세요.

## <a name="general-troubleshooting"></a>일반적인 문제 해결

혼합 현실 포털을 사용 하는 동안 문제가 발생 하거나 오류 메시지가 표시 되는 경우이 솔루션을 사용해 보세요.

**Windows Mixed Reality 다시 시작**

1. PC에서 헤드셋의 연결을 끊습니다 (두 케이블 모두).
2. PC를 다시 시작 하 고 헤드셋을 다시 연결 합니다.

**PC가 헤드셋을 인식 하는지 확인**

다시 시작이 작동 하지 않으면 PC에서 헤드셋을 인식 하는지 확인 합니다. 시작을 선택 하 고 검색 상자에 장치 관리자를 입력 한 다음 목록에서 선택 합니다. 혼합 현실 장치를 확장 하 고 헤드셋이 나열 되는지 확인 합니다. 

나열 되지 않은 경우 다음을 시도 합니다.
* 사용 가능한 경우 헤드셋을 PC의 다른 포트에 연결 합니다.
* [Windows 업데이트](https://support.microsoft.com/help/12373)에서 최신 소프트웨어 업데이트를 확인 합니다.
* Windows Mixed Reality 제거 및 다시 설치:
    1. PC에서 헤드셋의 연결을 끊습니다 (두 케이블 모두).
    2. **설정 > 혼합 현실 > 제거** 를 선택 합니다.
    3. 동작 컨트롤러 연결 해제: **설정 > 장치 > Bluetooth & 기타 장치** 를 선택 합니다. 각 컨트롤러를 선택 하 고 **장치 제거** 를 선택 합니다.
    4. Windows Mixed Reality를 다시 설치 하려면 헤드셋을 PC에 다시 연결 합니다.

## <a name="common-error-messages"></a>일반적인 오류 메시지

다음은 표시 될 수 있는 [오류 메시지](error-codes.md) 에 대 한 몇 가지 사항입니다.

| 이 메시지가 표시 되는 경우 | 사용 방법 |
| --- | --- |
| USB 케이블 확인 | 헤드셋을 다른 USB 포트에 연결 합니다 (SuperSpeed USB 3.0 인지 확인). 또한 헤드셋과 컴퓨터 간에 extender 나 허브를 제거해 보세요. |
| 디스플레이 케이블 확인 | 다음을 시도해 보세요. <ul><li>헤드셋을 DisplayPort 1.2 이상 또는 HDMI 1.4 이상에 연결 합니다. 포트가 PC의 고급 그래픽 카드와 일치 하는지 확인 합니다.</li><li>어댑터를 사용 하는 경우 4K 가능 인지 확인 합니다.</li><li>다른 HDMI 포트를 사용해 보세요.</li><li>외부 모니터가 HDMI 포트에 연결 되어 있는 경우 대신 DisplayPort에 연결 하 고 헤드셋에 대해 HDMI 포트를 사용 하세요.</li></ul> |
| 문제가 발생한 경우 | 위의 일반적인 문제 해결 단계를 따릅니다. |

## <a name="review-and-accept-terms-and-conditions"></a>사용 약관 검토 및 동의

설치를 계속 하려면 PC에 2GB의 사용 가능한 공간이 있어야 합니다. 검토 하 고 사용 약관에 **동의 함** 을 눌러 계속 합니다.

![사용 약관에 동의](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>호환성 검사

다음으로는 호환 되는 검사입니다. 혼합 현실 포털은 PC가 혼합 현실와 호환 되는지 확인 합니다. **녹색** 확인은 PC가 필요한 항목을 통과 했음을 의미 합니다. **주황색** 삼각형은 지정 된 요구 사항에 대 한 PC에 문제가 있을 수 있음을 의미 합니다. 문제가 발생 하는 경우 PC의 문제를 해결 하거나 업그레이드 해야 할 수 있습니다. **빨강** X는 지정 된 항목의 요구 사항을 충족 하는 PC가 없음을 의미 합니다.

![호환성 검사](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>준비

회전 아이콘을 사용 하 여 화면에 "설정 준비 중" 메시지가 표시 됩니다. 몇 분 정도 소요 됩니다.

![설정 준비](images/1050px-gettingsetup.png)

## <a name="see-also"></a>참조
* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원 문의](https://support.microsoft.com/contactus/)
* [설치 문제 해결](installation_errors.md)
* [설치 문제 해결](set-up-questions.md)
* [Windows Mixed Reality 설정](set-up-windows-mixed-reality.md)
