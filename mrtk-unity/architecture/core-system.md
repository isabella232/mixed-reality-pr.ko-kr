---
title: 핵심 시스템
description: MRTK의 입력 시스템, 디바이스 관리자 및 데이터 공급자
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 이벤트
ms.openlocfilehash: 79ebd3855cd991db168233f00058ab5d42f87d83
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121601"
---
# <a name="core-system"></a>핵심 시스템

입력 시스템의 핵심은 MRTK와 관련된 모든 입력 관련 기능을 초기화하고 운영하는 서비스인 [InputSystem](../features/input/overview.md)입니다.

> [!NOTE]
> 독자는 용어 [섹션을](terminology.md) 이미 읽고 기본적으로 이해하고 있다고 가정합니다.

이 서비스는 다음을 담당합니다.

- 입력 [시스템 프로필](../configuration/mixed-reality-configuration-guide.md#input-system-settings) 읽기
- 구성된 데이터 [공급자(예:](../features/input/input-providers.md) 및 `Windows Mixed Reality Device Manager` `OpenVR Device Manager` )를 시작합니다.
- HoloLens 2 스타일 시선 응시 정보 외에도 HoloLens(1세대) 스타일 머리 응시 정보를 제공하는 구성 요소인 [GazeProvider의](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)인스턴스화입니다.
- 포커스가 있는 개체를 결정하는 구성 요소인 [FocusProvider의](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)인스턴스화입니다. 설명서의 [포인터 및 포커스](controllers-pointers-and-focus.md#pointers-and-focus) 섹션에서 자세히 설명합니다.
- 모든 입력 이벤트에 대한 등록 지점 [제공(전역 수신기로)](#global-listeners)
- 이러한 입력 이벤트에 대한 이벤트 디스패치 기능을 제공합니다.

## <a name="input-events"></a>입력 이벤트

입력 이벤트는 일반적으로 두 개의 서로 다른 채널에서 발생합니다.

### <a name="objects-in-focus"></a>포커스에 있는 개체

이벤트는 포커스가 있는 GameObject로 직접 보낼 수 있습니다. 예를 들어 개체에는 를 구현하는 스크립트가 있을 수 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 있습니다.
이 개체는 가까이 있는 손에서 포커스가 있을 때 터치 이벤트를 가져옵니다. 이러한 유형의 이벤트는 이벤트를 처리할 수 있는 GameObject를 찾을 때까지 GameObject 계층 구조를 "위로" 이동합니다.

이 작업은 기본 입력 시스템 구현 내에서 [ExecuteHierarchy를](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 사용하여 수행됩니다.

### <a name="global-listeners"></a>전역 수신기

전역 수신기로 이벤트를 보낼 수 있습니다. 입력 시스템의 인터페이스를 사용하여 모든 입력 이벤트에 등록할 수 [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) 있습니다. [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) 메서드를 사용하여 전역 이벤트를 등록하는 것이 좋습니다. 사용되지 않는 `Register` 함수를 사용하면 수신기가 특정 형식의 입력 이벤트(여기서 형식은 이벤트 인터페이스에 의해 정의됨)가 아니라 모든 입력 이벤트에 대한 알림을 받습니다.

대체 [수신기는](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) 장면의 다른 곳에서 처리되지 않은 모든 단일 입력 이벤트를 수신하기 때문에 권장되지 않는 또 다른 유형의 전역 수신기입니다.

### <a name="order-of-event-dispatch"></a>이벤트 디스패치 순서

일반적으로 이벤트는 다음과 같은 방식으로 수신기에 전송됩니다. 아래 단계 중에서 이벤트를 [처리된](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)것으로 표시하면 이벤트 디스패치 프로세스가 중지됩니다.

1. 이벤트가 전역 수신기로 전송됩니다.
2. 이벤트는 포커스가 있는 개체의 모달 대화 상자로 전송됩니다.
3. 이벤트는 포커스가 있는 개체로 전송됩니다.
4. 이벤트는 대체 수신기로 전송됩니다.

## <a name="device-managers-and-data-providers"></a>디바이스 관리자 및 데이터 공급자

이러한 엔터티는 하위 수준 API(예: Windows Mixed Reality API 또는 OpenVR API)와 상호 작용하고 해당 시스템의 데이터를 MRTK의 상위 수준 입력 추상화에 맞는 데이터로 변환하는 역할을 담당합니다. 컨트롤러의 수명을 검색, 생성 및 관리하는 업무를 [담당합니다.](controllers-pointers-and-focus.md#controllers)

디바이스 관리자의 기본 흐름에는 다음이 포함됩니다.

1. 디바이스 관리자는 입력 시스템 서비스에 의해 인스턴스화됩니다.
2. 디바이스 관리자는 기본 시스템에 등록합니다(예: Windows Mixed Reality 디바이스 관리자는 [입력](../features/input/input-events.md) 및 [제스처](../features/input/gestures.md#gesture-events) 이벤트를 등록합니다.
3. 기본 시스템에서 검색하는 컨트롤러를 만듭니다(예: 공급자가 굴절된 손의 존재를 감지할 수 있는 경우).
4. Update() 루프에서 UpdateController()를 호출하여 기본 시스템의 새 상태를 폴링하고 해당 컨트롤러 표현을 업데이트합니다.
