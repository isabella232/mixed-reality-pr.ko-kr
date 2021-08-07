---
title: 용어
description: MRTK의 다른 입력 시스템 용어
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 입력,
ms.openlocfilehash: 8046501fdab0a7594800a75ad0306a131adaaa6924ffa870c299571cbd4d8e13
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211162"
---
# <a name="input-system"></a>입력 시스템

입력 시스템은 MRTK에서 제공 하는 모든 기능 중에서 가장 큰 시스템 중 하나입니다.
따라서 도구 키트 내의 많은 항목이이를 기반으로 작성 됩니다 (포인터, 포커스, prefabs). 입력 시스템 내의 코드는 플랫폼 간 잡기 및 회전과 같은 자연 스러운 상호 작용을 허용 합니다.

입력 시스템에는 다음과 같은 고유한 용어를 정의할 수 있습니다.

- **데이터 공급자**

    입력 프로필의 입력 설정에는 데이터 공급자 라고 하는 엔터티에 대 한 참조가 있습니다. 이러한 항목을 설명 하는 다른 단어는 장치 관리자입니다. 이는 특정 기본 시스템과 상호 작용 하 여 MRTK 입력 시스템을 확장 하는 작업을 포함 하는 구성 요소입니다. 공급자의 예로는 Windows Mixed Reality 공급자가 있습니다 .이 공급자는 기본 Windows Mixed Reality api와 통신 하 고 해당 api의 데이터를 아래의 mrtk 관련 입력 개념으로 변환 합니다. 또 다른 예는 OpenVR 공급자 (해당 작업은 Unity로 추상화 된 OpenVR 버전의 OpenVR와 통신 하 고 해당 데이터를 MRTK 입력 개념으로 변환)입니다.

- **컨트롤러**

    실제 컨트롤러에 대 한 표현으로, 사용 하는 경우에는 사용 되는 것이 좋습니다. 즉 HoloLens, 사용 되는 것이 가장 좋습니다. 컨트롤러는 장치 관리자에 의해 생성 됩니다. 즉, WMR 장치 관리자는 컨트롤러를 생성 하 고 해당 되는 것으로 간주 되는 경우에는 해당 수명 주기를 관리 합니다.

- **포인터**

    컨트롤러는 포인터를 사용 하 여 게임 개체와 상호 작용 합니다. 예를 들어 근거리 상호 작용 포인터는 손 (컨트롤러)이 ' 근접 한 상호 작용 '을 지 원하는 것으로 광고 하는 개체와 가까운 경우를 검색 합니다. 포인터에 대 한 다른 예는 먼 raycasts를 사용 하는 teleportation 또는 far 포인터 (즉, 셸 손 광선 포인터)입니다.

    포인터는 장치 관리자에 의해 생성 된 다음 입력 소스에 연결 됩니다. 컨트롤러에 대 한 모든 포인터를 가져오려면 다음을 수행 합니다. `controller.InputSource.Pointers`

    컨트롤러는 여러 포인터와 동시에 연결할 수 있습니다. 이 작업이 비정상 상태로 미치는지를 않도록 하기 위해 활성화 될 수 있는 포인터를 제어 하는 포인터 mediator 있습니다. 예를 들어 근처의 상호 작용이 감지 되 면 mediator는 먼 상호 작용 포인터를 사용 하지 않도록 설정 합니다.

- **포커스**

    포인터 이벤트는 **포커스** 로 개체에 전송 됩니다. 포커스 선택은 포인터 유형에 따라 달라 집니다. 손 모양 포인터는 raycasts를 사용 하는 반면, poke 포인터는 spherecasts를 사용 합니다. 개체는 포커스를 받을 IMixedRealityFocusHandler을 구현 해야 합니다. 개체를 전역적으로 등록 하 여 필터링 되지 않은 포인터 이벤트를 받을 수 있지만이 방법은 사용 하지 않는 것이 좋습니다.

    포커스가 있는 개체를 업데이트 하는 구성 요소는 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **커서**

    포인터 상호 작용에 대 한 추가 시각적 신호를 제공 하는 포인터와 연결 된 엔터티입니다. 예를 들어 FingerCursor는 손가락 주위에 고리를 렌더링 하 고 손가락이 ' near interactable ' 개체에 근접 한 경우 해당 링을 회전할 수 있습니다. 포인터는 한 번에 하나의 커서와 연결할 수 있습니다.

- **상호 작용 및 조작**

    개체에는 상호 작용 또는 조작 스크립트를 사용 하 여 태그를 지정할 수 있습니다. 또는와 같은을 통해이 작업을 수행할 수 있습니다 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    예를 들어, NearInteractionGrabbable 및 NearInteractionTouchable는 특정 포인터 (특히 상호 작용 포인터 근처)에서 포커스를 받을 수 있는 개체를 알 수 있도록 허용 합니다.

    Interactable 및 ManipulationHandler는 포인터 이벤트를 수신 하 여 UI 시각적 개체를 수정 하거나 게임 개체를 이동/배율 조정/회전 하는 구성 요소의 예입니다.

아래 이미지는 MRTK 입력 스택의 상위 수준 빌드 (상향식)를 캡처합니다.

![입력 시스템 다이어그램](../features/images/input/MRTK_InputSystem.png)
