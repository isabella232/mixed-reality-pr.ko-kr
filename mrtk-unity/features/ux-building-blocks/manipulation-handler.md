---
title: 조작 처리기
description: MRTK의 조작 처리기에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 조작,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176634"
---
# <a name="manipulation-handler"></a>조작 처리기

![조작 처리기](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ManipulationHandler* 스크립트를 사용하면 한 손 또는 두 손을 사용하여 개체를 이동 가능하고 확장 가능하며 회전 가능하게 만들 수 있습니다. 조작은 특정 종류의 변환만 허용하도록 제한할 수 있습니다. 스크립트는 HoloLens 2 연결 손 입력, 손 광선, HoloLens(1세대) 제스처 입력 및 몰입형 헤드셋 모션 컨트롤러 입력을 비롯한 다양한 유형의 입력에서 작동합니다.

## <a name="how-to-use-the-manipulation-handler"></a>조작 처리기를 사용하는 방법

`ManipulationHandler`GameObject에 스크립트 구성 요소를 추가합니다. 또한 잡기 가능한 범위와 일치하는 충돌체를 개체에 추가해야 합니다.

개체가 연결이 가까운 손 입력에 응답하도록 `NearInteractionGrabbable` 하려면 스크립트도 추가합니다.

![Unity 편집기에서 조작 처리기 사용](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>검사기 속성

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**호스트 변환** 끌어 올 변환입니다. 기본값은 구성 요소의 개체입니다.

**조작 유형** 한 손, 두 손 또는 둘 다 사용하여 개체를 조작할 수 있는지 여부를 지정합니다.

* *한 손으로만*
* *양손만*
* *1과 2손*

**양손 조작 유형**

* *크기 조정:* 크기 조정만 허용됩니다.
* *회전:* 회전만 허용됩니다.
* *크기 조정 이동:* 이동 및 크기 조정이 허용됩니다.
* *Move Rotate:* 이동 및 회전이 허용됩니다.
* *배율 회전:* 회전 및 크기 조정이 허용됩니다.
* *회전 배율 이동:* 이동, 회전 및 크기 조정이 허용됩니다.

![조작 처리기](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**원거리 조작 허용** 포인터와의 원거리 상호 작용을 사용하여 조작을 수행할 수 있는지 여부를 지정합니다.

**한 손 회전 모드 가까이** 개체가 한 손/컨트롤러 가까이에서 잡을 때 동작하는 방법을 지정합니다.

**원 핸드 회전 모드 원거리** 한 손/컨트롤러를 멀리서 잡고 있을 때 개체가 동작하는 방식을 지정합니다.

**한 손 회전 모드 옵션** 한 손으로 잡고 있을 때 개체가 회전하는 방법을 지정합니다.

* *원래 회전 유지 관리:* 이동 중인 개체를 회전하지 않습니다.
* *사용자에 대한 회전 유지 관리:* X/Y축에 대한 개체의 원래 회전을 사용자에게 유지 관리합니다.
* *사용자에 대한 회전을 유지 관리하는 무게* 조정: 사용자에 대한 개체의 원래 회전을 유지 관리하지만 개체를 세로로 만듭니다. 경계 컨트롤이 있는 개체에 유용합니다.
* *Face 사용자:* 개체가 항상 사용자를 향하도록 합니다. 슬레이트/패널에 유용합니다.
* *사용자와 얼굴 분리:* 개체가 항상 사용자와 떨어져 있는지 확인합니다. 뒤로 구성된 슬레이트/패널에 유용합니다.
* *개체 중심 회전:* 굴절형 손/컨트롤러에 대해서만 작동합니다. 손/컨트롤러의 회전을 사용하지만 개체 중심점을 사용하여 개체를 회전합니다. 원거리에서 검사하는 데 유용합니다.
* *잡기 지점 회전:* 굴절형 손/컨트롤러에 대해서만 작동합니다. 개체를 손/컨트롤러가 보유하고 있는 것처럼 회전합니다. 검사에 유용합니다.

**릴리스 동작** 개체가 해제되면 개체의 물리적 이동 동작을 지정합니다. 고정된 구성 요소가 해당 개체에 있어야 합니다.

* *Nothing*
* *모두*
* *속도 유지*
* *Angular 속도 유지*

**회전에 대한 제약 조건** 상호 작용할 때 개체가 회전할 축을 지정합니다.

* *없음*
* *X축만*
* *Y축만*
* *Z축만*

**제약 조건에 로컬 공간 사용** 세계 공간 축 또는 로컬 공간 축과 관련하여 제약 조건을 적용하는 사이를 전환하는 토글입니다.

**이동에 대한 제약 조건**

* *없음*
* *헤드로부터의 거리 수정*

**활성 다듬기** 다듬기 가 활성 상태인지 여부를 지정합니다.

**한 손 다량 다듬기** 이동, 배율, 회전에 적용할 다듬기 양입니다. 0의 다듬기란 다듬기 없음을 의미합니다. 최대값은 값이 변경되지 않는 것을 의미합니다.

## <a name="events"></a>이벤트

조작 처리기는 다음 이벤트를 제공합니다.

* *OnManipulationStarted:* 조작이 시작될 때 발생합니다.
* *OnManipulationEnded:* 조작이 종료될 때 발생합니다.
* *OnHoverStarted:* 손/컨트롤러가 조작 가능한 마우스를 근거리 또는 멀리 가리키면 발생합니다.
* *OnHoverEnded:* 손/컨트롤러가 조작 가능한 가리키기를 거의 또는 멀리 가리키면 발생합니다.
