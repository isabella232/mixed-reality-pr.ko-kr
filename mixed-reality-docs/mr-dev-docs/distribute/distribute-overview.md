---
title: 앱 배포
description: 지원 되는 다양 한 플랫폼 및 게시 저장소에 대 한 다양 한 배포 옵션의 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, 혼합 현실, 모던 헤드셋, 앱, uwp, 제출, 제출, 필터, 메타 데이터, 시스템 요구 사항, 키워드, wack, 인증, 패키지, appx, 머천다이징
ms.openlocfilehash: 7d4fbc1a7a5767ad8276017c7cdc38e9bb436bc83b12a4d8caeb9a8d84f1caca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198792"
---
# <a name="distributing-your-apps"></a>앱 배포

![WMR home의 Floaty bird 3D 앱 lancher](images/distribute-hero-image.png)

앱을 사용자에 게 전달 하거나 전 세계에 세밀히 하는 것이 가장 중요 하 고 때로는 개발 활동의 일부입니다. 사용자 또는 팀에 가장 적합 한 배포 및 배포 시나리오에 따라 달라 지는 일련의 리소스에 프로세스를 간소화 했습니다.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>분포 옵션

> [!IMPORTANT]
> * 다른 파티와 앱을 공유 하는 경우 appx 파일을 빌드하고 제공 해야 합니다. 
>     * 앱 설치 관리자를 사용 하는 경우 사용자와 인증서를 공유 해야 합니다.
> 
> * 조직과 공유 하는 경우 회사 또는 학교 계정이 필요 하 고 조직 [MDM (모바일 장치 관리)](/hololens/hololens-enroll-mdm) 인프라에 대 한 액세스 권한이 필요 합니다.  
>    * 공유 파티를 사용 하는 경우 테 넌 트의 관리자 여야 하 고 [Microsoft Endpoint Manager 관리 센터](/mem/intune/apps/apps-deploy) 를 사용 하 여 앱을 사용할 수 있도록 설정 해야 합니다. 또 다른 옵션은 최종 사용자와 appx 파일 및 앱 종속성을 공유 하는 것입니다.
>    * 최종 사용자 인 경우 공유 조직의 테 넌 트에 등록 하면 앱이 자동으로 다운로드 되거나 다운로드 가능 합니다. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>시나리오</strong></td>
    <td><strong>로컬 장치 설치</strong></td>
    <td><strong>다른 사람과 공유</strong></td>
    <td><strong>조직과 공유</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>앱 설치 관리자</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM-회사 포털</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM-필수 앱 설치</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-store-business"><strong>비즈니스용 Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>프로비전 패키지</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>사용자 지정 Win32 배포</strong></a> (HoloLens 장치에는 사용할 수 없음-아래 참조)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> 현재 관리 되는 장치 또는 HoloLens (첫 번째 Gen) 장치에 대해 앱 설치 관리자를 사용할 수 없습니다.

## <a name="other-scenarios"></a>기타 시나리오

* 스트림 및 Game Pass를 포함 하 여 Win32 응용 프로그램 배포에 대 한 Unity의 PC 독립 실행형 빌드 대상을 사용 하 여 Win32 .EXE 파일을 생성할 수 있습니다. .EXE 있으면 선택한 플랫폼에 대 한 일반적인 앱을 제출할 수 있습니다. 

* 오프 라인 상태인 동안 HoloLens 2 응용 프로그램을 설치 해야 하는 경우에는 [오프 라인 보안 HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) 지침을 참조 하거나 개발자 모드를 사용 하도록 설정 하지 않고 프로 비전 패키지를 통해 앱을 설치 합니다.

* 또한 장치에 빌드를 배포 하 고 [Visual Studio를 사용 하 여 배포 및 디버깅](../develop/platform-capabilities-and-apis/using-visual-studio.md) 하거나 [장치 포털로 응용 프로그램 패키지를 설치](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)하 여 개발자 모드를 사용 하도록 설정한 다른 개발자와 공유할 수 있습니다.

## <a name="see-also"></a>추가 정보
* [Microsoft Store에서 응용 프로그램 찾기, 설치 및 제거](/hololens/holographic-store-apps)