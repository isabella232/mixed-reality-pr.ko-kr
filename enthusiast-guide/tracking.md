---
title: Faq 추적
description: 표준 소비자 지원 설명서를 벗어나는 Windows Mixed Reality 문제 해결을 추적 합니다.
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 추적
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199479"
---
# <a name="tracking-faqs"></a>Faq 추적

## <a name="my-headset-has-stopped-tracking"></a>내 헤드셋에서 추적을 중지 했습니다.

표시등이 켜져 있는지 확인 하 고 헤드셋의 전면에 내부 추적 카메라를 방해 하지 않는지 아무것도 없는지 확인 합니다. 추적이 손실 된 경우 다시 시작 하는 데 몇 초 정도 걸릴 수 있습니다. 추적을 다시 시작 하지 Windows Mixed Reality 포털을 다시 시작 합니다.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>찾을 수는 있지만 번역할 수 없습니다.

즉, 추적 시스템에서 포즈를 생성할 수 없거나 응용 프로그램에서 새 포즈 데이터를 사용 하 여 렌더링할 수 없습니다. 문제를 해결하려면 다음을 수행합니다.

* 대화방에 충분 한 조명이 있는지 확인 합니다.
* 공간에 추적할 충분 한 세부 정보가 있는지 확인 합니다.
* 장치를 분리 하 고 Windows Mixed Reality를 닫은 후 장치를 다시 연결 합니다.
* 메시지가 계속 발생 하면 [고객 지원](https://support.microsoft.com/) 서비스에 문의 하십시오.

## <a name="the-view-in-the-hmd-is-frozen"></a>HMD의 뷰가 고정 되어 있습니다.

이는 일반적으로 응용 프로그램 또는 시스템 수준 구성 요소가 실패 했음을 의미 합니다. 다음을 시도 합니다.

1. "홈" 단추를 눌러 응용 프로그램을 종료 합니다.
2. 장치를 분리 하 고 MRP를 닫은 후 장치를 다시 연결 합니다.
3. PC를 다시 시작 합니다.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>표준으로 되돌리기 전에 잠시 후에는 잠시 후에만 잠깐 회전 하 고 기울이거나 대칭 이동 합니다.

이는 응용 프로그램 또는 시스템 수준 구성 요소에서 오류가 발생 하거나 일시적으로 메모리 또는 CPU 리소스가 부족 한 경우에 발생할 수 있습니다. 확인 하려면 다음을 수행 합니다.

1. 작업 관리자를 열고 CPU의 20% 이상이 사용 가능한 지 확인 하 고, 400 메모리를 사용할 수 있으며, 디스크 IO가 80% 미만 이어야 합니다.
2. **이벤트 뷰어 > Windows Logs > 응용 프로그램** 으로 이동 하 여 중지 시점에 발생 한 오류를 찾습니다. 해당 시간 동안 실행 중인 응용 프로그램 또는 HoloLens 센서, 혼합 현실 또는 응용 프로그램을 참조 하는 모든 항목을 찾습니다. 이러한 로그에서 오류의 원인을 설명할 수 있습니다.
3. 문제가 지속 되 면 PC를 다시 시작 합니다.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>일시적으로 대칭 이동 하 여 정상으로 전환 된 세계

일반적으로이 오류는 추적 알고리즘에 알리기 위해 헤드셋에서 센서 데이터를 가져오는 동안 발생 합니다. 자주 발생 하는 경우:

1. 다른 USB 3.0 포트에 헤드셋을 연결 합니다.
2. USB 3.0 허브가 아닌 PC에 직접 헤드셋을 연결 합니다.
3. 문제가 지속 되 면 [고객 지원](https://support.microsoft.com/)에 문의 하세요.

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>전 세계는 기울어짐 이지만 탐색 하 고 Windows Mixed Reality 수 있습니다.

센서 데이터 오류가 PC의 환경 데이터에 기록 되는 경우에는 Windows Mixed Reality 수 있습니다. 이 문제를 해결하려면

1. 헤드셋을 분리 하 고, Windows Mixed Reality를 닫고, 헤드셋을 다시 연결 합니다.
2. PC를 다시 시작 합니다.
3. 환경 데이터를 지웁니다.