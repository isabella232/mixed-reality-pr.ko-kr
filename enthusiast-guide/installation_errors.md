---
title: 설치 오류
description: 표준 소비자 지원 설명서를 벗어나는 고급 Windows Mixed Reality 설치 오류 문제 해결
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 설치
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213191"
---
# <a name="installation-errors"></a>설치 오류

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"사용자 PC를 실행할 수 없습니다 Windows Mixed Reality"

PC가 Windows Mixed Reality를 실행 하는 데 필요한 [최소 요구 사항을](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 충족 하지 않습니다. 컴퓨터의 하드웨어 설정이 Windows Mixed Reality와 호환 되지 않거나 [Windows 최신 버전으로 업데이트](https://support.microsoft.com/help/12373/windows-update-faq)해야 할 수 있습니다. 

Windows Mixed Reality에는 최소한 WDDM 2.2을 지 원하는 그래픽 카드 드라이버가 필요 합니다. 제조업체의 최신 드라이버 업데이트가 있는지 확인 합니다. 설치 Windows Mixed Reality 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되 면 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"이 PC는 거의 있나요? Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다.

PC가 Windows Mixed Reality 최상의 환경에 필요한 [최소 요구 사항을](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 충족 하지 않습니다. PC는 몰입 형 헤드셋을 실행할 수 있지만 성능 문제를 발생 시킬 수 있으며 특정 응용 프로그램을 실행할 수 없습니다.

Windows Mixed Reality에는 최소한 WDDM 2.2을 지 원하는 그래픽 카드 드라이버가 필요 합니다. 제조업체의 최신 드라이버 업데이트가 있는지 확인 합니다. 설치 Windows Mixed Reality 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되 면 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Windows Mixed Reality 설정 하려면 먼저 관리자가 조직에 대해 사용 하도록 설정 해야 합니다. 자세히 알아보기 "

회사에서 관리 하는 네트워크를 사용 하 고 조직에서 WSUS (Windows Server Update Services)를 사용 하 고 있는 것 같습니다. 이러한 정책 및 다운로드를 차단할 수 있는 기타 정책 [Windows Mixed Reality 사용 하도록 설정](/windows/application-management/manage-windows-mixed-reality#enable)하려면 조직의 IT 부서 또는 시스템 관리자에 게 문의 하세요.

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"혼합 현실 소프트웨어를 다운로드할 수 없습니다." 또는 "다운로드 하는 동안 잠시 기다려 주세요."

* 경우에 따라 보류 중인 업데이트가 혼합 현실 소프트웨어 다운로드를 차단할 수 있습니다. **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 그런 다음 대기 중인 업데이트를 다운로드 하 여 설치 합니다. Windows 업데이트 오류가 표시 되 면 [여기](https://support.microsoft.com/help/10164/fix-windows-update-errors)에서 도움을 받으세요.
* PC가 인터넷에 연결 되어 있고 사용 가능한 저장소 공간이 2gb 이상 인지 확인 합니다. 네트워크 상태를 확인 합니다. **설정 > 네트워크 & 인터넷 > 상태** 를 확인 합니다. 인터넷에 연결할 수 없는 경우 [여기](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)에서 도움을 받으세요.  
* PC를 다시 시작 하 고 다시 시도 하세요. 

이러한 솔루션이 작동 하지 않는 경우 다음을 시도 합니다.
* Wi-Fi 네트워크 연결이 요금제로 설정 된 경우에는 [데이터](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)통신이 아닌 것으로 변경 합니다. 데이터 통신 연결을 해제 하려면 다음으로 이동 합니다. **설정 > 네트워크 & 인터넷 > 상태 > 연결 속성 변경 > 데이터 통신 연결로 설정** 하 고 "해제"를 선택 합니다.  
* 업데이트를 최근에 설치한 경우 문제가 발생할 수 있습니다. 설치 된 업데이트, 특히 PC를 안전 하 게 유지 하는 보안 업데이트를 제거 하지 않는 것이 좋습니다. 그러나 경우에 따라 최신 업데이트를 제거 하면 문제의 원인을 쉽게 파악할 수 있습니다. 
    * **설정 > 업데이트 & 보안 > 설치 된 업데이트 기록 보기 > 업데이트 제거** 로 이동 합니다.
    * 설치 된 마지막 업데이트와 "제거"를 선택 합니다.
    * "이 업데이트를 제거 하 시겠습니까?" 라는 메시지가 표시 되 면 "예"를 대답 합니다. 이러한 단계를 시도할 때 오류가 발생 하는 경우 [windows 업데이트 오류를 해결](https://support.microsoft.com//help/10164/fix-windows-update-errors)하는 방법에 대 한 자세한 내용을 확인 하세요. 
    * PC를 다시 시작 하 고 다시 시도 하세요. 
    * Windows Mixed Reality 제대로 설치 되 면 **설정 > Windows 업데이트** 에서 최신 업데이트를 다시 설치 하 > 업데이트를 확인 하 고 Windows Mixed Reality가 계속 작동 하는지 확인 합니다. 제대로 설치 되지 않으면 업데이트를 다시 설치 하 고 Windows 지원 담당자에 게 문의 하세요. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"오류가 발생 하 여 Windows Mixed Reality를 시작할 수 없습니다."
특정 오류 코드에 대 한 자세한 내용을 보려면 [여기](error-codes.md)를 확인 하세요. 다음을 시도할 수도 있습니다.

* PC에서 두 헤드셋 케이블을 분리 합니다.
* PC를 다시 시작 합니다.
* **설정 > 업데이트 & 보안 > Windows 업데이트** 로 이동 하 고 Windows 업데이트이 설정 되어 있는지 확인 합니다. 대기 중인 업데이트를 다운로드 하 여 설치 합니다.
* 헤드셋을 PC에 다시 연결한 다음 설치를 다시 시도 합니다.

이러한 단계가 작동 하지 않는 경우 Windows Mixed Reality를 제거한 후 다시 설치 합니다.
* **설정 > Mixed reality** 로 이동 하 > 제거를 선택 하 고 "제거"를 선택 합니다. 
* PC를 다시 시작 합니다. 
* 설치 프로세스를 다시 시작 하려면 헤드셋을 PC에 연결 하기만 하면 됩니다.