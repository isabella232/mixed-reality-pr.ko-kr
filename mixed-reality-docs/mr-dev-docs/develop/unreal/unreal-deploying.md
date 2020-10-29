---
title: Unreal의 디바이스에 배포
description: 장치를 장치에 배포 하는 방법에 대 한 가이드 2 개
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 장치에 배포, PC, 설명서
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684792"
---
# <a name="deploy-to-device-in-unreal"></a>Unreal의 디바이스에 배포

## <a name="overview"></a>개요
다음 두 가지 방법으로 HoloLens 2에 Unreal 응용 프로그램을 배포할 수 있습니다.
* Unreal 편집기에서 직접
* 장치 포털을 통해 업로드 된 패키지

두 옵션 모두 개발용으로 [장치 포털](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 을 사용 하도록 HoloLens를 설정 해야 합니다.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Unreal 편집기에서 장치에 배포

1. **시작** 단추 옆에 있는 드롭다운 화살표를 클릭 합니다. 처음에는 HoloLens 장치 옵션이 회색으로 표시 됩니다.

![시작 드롭다운 옵션](images/unreal/launch-dropdown.png)

2. **Device Manager** 를 엽니다. HoloLens는 장치 목록에 자동으로 표시 되지 않습니다.

3. 나열 되지 **않은 장치 추가** 섹션을 확장 합니다.

4. **플랫폼** 으로 **HoloLens** 를 선택 합니다.

5. 장치의 IP 주소와 포트 정보를 콜론으로 구분 하 여 장치 식별자로 입력 합니다. 예를 들면 "127.0.0.1:10080" (USB를 통해 연결 된 경우)입니다. 장치 포털 사용자 이름 및 암호 자격 증명을 사용 합니다.

6. **추가** 를 누르고 장치 관리자를 닫습니다.
    * 오류가 발생 하는 경우 (예: 잘못 된 주소, 사용자 이름 또는 암호) 출력 로그에 메시지가 인쇄 됩니다.

![나열 되지 않은 장치 추가](images/unreal/add-unlisted-device.png)

7. **시작** 단추 옆에 있는 드롭다운 화살표를 다시 클릭 합니다. 이번에는 방금 추가한 HoloLens 장치가 표시 되어야 합니다. Hololens에 빌드 및 배포할 HoloLens 장치를 선택 합니다.

>[!NOTE]
>장치를 빌드하기 위해 셰이더를 다시 컴파일하는 작업이 포함 될 수 있습니다 (특히 첫 번째 실행의 경우) .이는 다소 시간이 걸릴 수 있습니다. 앱이 실행 될 때까지 장치가 절전 모드로 전환 되지 않도록 합니다 (앱을 사용 해야 할 수 있음). 그렇지 않으면 셰이더 컴파일이 실패 합니다.

## <a name="deploying-to-device-via-device-portal"></a>장치 포털을 통해 장치에 배포

[앱 패키징 및 배포](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) 에 대 한 자세한 지침은 unreal 자습서 시리즈 시작의 마지막 섹션에서 찾을 수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 실제 개발 검사점 경험을 수행 하는 경우 배포 단계를 진행 하 게 됩니다. 여기에서 고급 서비스 추가를 계속할 수 있습니다.

> [!div class="nextstepaction"]
> [고급 서비스](unreal-development-overview.md#5-adding-services)

언제 든 지 [실제 개발 검사점](unreal-development-overview.md#4-deploying-to-a-device) 으로 돌아갈 수 있습니다.
