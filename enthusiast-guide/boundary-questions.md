---
title: 경계 FAQ
description: 표준 소비자 지원 설명서를 벗어나는 경계 질문에 대한 고급 Windows Mixed Reality 문제 해결
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 문제 해결, 오류, 도움말, 지원, 경계
appliesto:
- Windows 10
ms.openlocfilehash: c1d6a10ae6ed50f7b9088b26c78cde4ccf8386ea0603c39e107ed23910db9308
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187973"
---
# <a name="boundary-faqs"></a>경계 FAQ

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>경계란 무엇이며 경계를 만들어야 하는 이유는 무엇인가요?

경계는 Windows Mixed Reality 헤드셋을 걸 때 이동할 수 있는 영역을 정의합니다. 헤드셋에서 볼 수 없는 장애물을 방지하는 데 도움이 되는 경계를 만드는 것이 중요합니다. 경계는 혼합 현실 내부의 흰색 윤곽선처럼 보이고 가까이 오면 나타납니다. 이를 확인하면 이동 속도가 느려지거나 경계를 넘거나 그 이상으로 확장하지 않도록 방지합니다.

경계 내의 영역에는 가구, 낮음 조명 설비, 상한 팬 등이 없어야 하므로 어떤 것에도 충돌하거나 여행하지 않습니다. [Windows Mixed Reality 의 상태 및 안전성에 대해 알아봅니다.](wmr-health-safety-comfort.md)

## <a name="how-do-i-create-a-boundary"></a>경계를 만들 어떻게 할까요? 있나요?

헤드셋을 처음 설정하면 설정 앱(Mixed Reality 포털)에서 경계를 만드는 단계를 안내합니다. 하지만 언제든지 만들 수 있습니다.

1. 바탕 화면에서 **> Mixed Reality 포털 시작을** 선택합니다.
2. "메뉴"를 엽니다.
3. "공간 경계 설정"을 선택하여 새 경계를 만듭니다.

다른 사용자가 헤드셋을 사용하는 경우 경계 및 사용 방법을 이해해야 합니다. 헤드셋을 새 위치로 이동하는 경우 공간에 대한 새 경계를 설정해야 합니다.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>경계를 만들려고 할 때 오류 메시지가 표시됩니다.

* 경계를 만들 때 벽이나 기타 장애물에 너무 가까이 있지 마세요.
* 헤드셋 높이를 유지하고 경계를 추적하는 동안 컴퓨터를 향해야 합니다.
* 센서가 차단되지 않고 충분한 조명이 있는지 확인합니다.
* 추적하는 공간은 3평방미터보다 커야 합니다.
* 공간이 너무 크거나 너무 복잡하지 않아야 합니다. 변형 및 턴이 있는 간단한 기하 도형에 고정합니다.
* 추적할 때 사용자 고유의 경로를 다시 교차하지 마세요.
* 모서리에 고정된 경우 다시 시작합니다.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>시스템에서 경계를 찾을 수 없고 설치 UI가 표시됩니다.

즉, 추적 시스템에서 환경을 인식할 수 없습니다. 새 환경에 있는 경우 [경계를](set-up-windows-mixed-reality.md#set-up-your-room-boundary)설정해야 합니다.
이전에 이 환경에서 디바이스를 사용하고 경계를 설정한 경우:

* 실내에 충분한 조명이 있는지 확인합니다.
* 디바이스를 찾은 후 방 주변을 둘러봤는지 확인합니다. 디바이스는 환경을 관찰하여 위치를 알아야 합니다. 데스크 또는 테이블에 있는 경우 경계를 찾을 수 없습니다.
* 디바이스를 분리하고, Windows Mixed Reality 닫고, 다시 연결합니다.
* 환경의 변경된 내용이 있으면 디바이스에서 더 이상 인식하지 못할 수 있습니다. 새 경계를 설정합니다.

이러한 단계를 수행해도 문제가 해결되지 않으면 환경 데이터를 삭제하고 경계를 다시 설정합니다.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>시스템에서 모든 환경 또는 착석/대기에 대한 설정을 선택하라는 UI를 제공합니다. 내 경계가 표시됩니다.

디바이스가 범위를 찾는 데 너무 오래 걸리고 있습니다. 경계를 사용하는 옵션을 선택하여 이 메시지를 무시할 수 있으며 경계가 있는 Windows Mixed Reality 홈으로 이동됩니다.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>"경계가 손실되었습니다."라는 메시지가 표시되는 경우가 많습니다.

추적 시스템에는 환경을 추적하고 식별하는 데 어려움이 있습니다. 이 상태에서 디바이스는 더 이상 경계를 표시할 수 없습니다. 헤드셋은 3DOF로 전환하여 경계를 다시 찾을 때까지 실제 세계의 사물로 이동하지 않도록 합니다. 다음 단계를 시도하여 문제를 해결합니다.

1. 실내에 충분한 조명이 있는지 확인합니다.
2. 최근에 공간을 다시 장식하거나 리모델링한 경우 설정을 다시 실행합니다.
3. 디바이스를 분리하고, Windows Mixed Reality 닫고, 다시 연결합니다.
4. 환경 데이터를 지우고 디바이스를 다시 설정합니다.
5. 메시지가 지속되면 고객 지원에 문의하세요.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>내 경계를 찾을 수 없다는 메시지가 표시됩니다.   어떻게 해야 합니까?

Windows Mixed Reality 기존 경계를 식별하는 데 문제가 있을 수 있습니다. 새 경계를 만들거나 디바이스를 "좌식 및 서" 모드에서 사용할 수 있습니다.

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>"추적 손실" 또는 "이 공간에 대한 경계가 없습니다."라는 메시지가 표시됩니다.

새 경계를 만듭니다.

1. **> Mixed Reality 포털 시작을** 선택합니다.
2. "메뉴"를 엽니다.
3. "공간 경계 설정"을 선택합니다.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>경계는 항상 표시됩니다. 어떻게 하면 사라지나요?

경계가 가까이 있으면 나타납니다. 경계에 좁거나 불규칙한 모양의 섹션이 포함되어 있으면 경계에 가까워지게 될 수 있습니다. 경계가 원하는 것보다 더 자주 나타날 수 있습니다. 더 크고 일반적인 셰이프를 사용하여 경계를 다시 만들어 문제를 해결해 보세요.

1. **> Mixed Reality 포털 시작을** 선택합니다.
2. "메뉴"를 엽니다.
3. "공간 경계 설정"을 선택합니다.

## <a name="can-i-turn-off-the-boundary-temporarily"></a>경계를 일시적으로 해제할 수 있나요?

* **> Mixed Reality 포털 시작을** 선택합니다.
* "메뉴"를 엽니다.
* "경계"를 "끄기"로 설정합니다. 경계가 해제되어 있는 동안 한 곳에 있어야 합니다.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>"좌표 및 서" 및 "모든 환경" 중에서 선택할 어떻게 할까요? 있나요?

헤드셋을 설치하는 동안 또는 나중에 "착석 및 서"를 선택하는 경우 경계 없이 헤드셋을 사용합니다. 헤드셋을 사용할 때는 물리적 장애물과 위험 위험을 방지하기 위해 한 지점에 있어야 합니다. 낮거나 일어설 수 있지만 이동할 수는 없습니다. 장애물은 오버헤드와 주변일 수 있습니다.

일부 앱은 경계에서 작동하도록 설계될 수 있습니다. 경계 없이 사용하는 경우 작동하지 않거나 동일한 환경을 제공할 수 있습니다.

"모든 환경"을 선택하는 경우 경계를 설정하고 경계를 사용 및 사용하지 않고 작동하는 앱과 환경을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원을 요청합니다.](https://support.microsoft.com/contactus/)