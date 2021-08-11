---
title: 입력 개요
description: MRTK의 입력 시스템 개요
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219766"
---
# <a name="input-overview"></a>입력 개요

MRTK의 입력 시스템을 사용하여 다음을 수행할 수 있습니다.

- 입력 이벤트를 통해 6개의 DOF 컨트롤러, 굴절된 손 또는 음성과 같은 다양한 입력 소스의 입력을 사용합니다.
- *선택* 또는 *메뉴* 와 같은 추상 작업을 정의하고 다른 입력에 연결합니다.
- 포커스 및 포인터 이벤트를 통해 UI 구성 요소를 구동하기 위해 컨트롤러에 연결된 포인터를 설치합니다.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>MRTK 입력 시스템 개요</sup>

입력은 [**입력 데이터 공급자(디바이스 관리자)에서 생성됩니다.**](input-providers.md) 각 공급자는 Open VR, WMR(Windows Mixed Reality), UnityStick, Windows Speech 등의 특정 입력 원본에 해당합니다. 공급자는 *Mixed Reality Toolkit* 구성 요소의 **등록된 서비스 공급자 프로필을** 통해 프로젝트에 추가되며 해당 입력 소스를 사용할 수 있을 때(예: WMR 컨트롤러가 검색되거나 게임 패드가 연결된 경우) 입력 [**이벤트를**](input-events.md) 자동으로 생성합니다.

[**입력 작업은**](input-actions.md) 입력을 생성하는 특정 입력 소스에서 애플리케이션 논리를 격리하는 데 도움이 되는 원시 입력에 대한 추상화입니다. 예를 들어 *선택* 작업을 정의하고 마우스 왼쪽 단추, 게임 패드의 단추 및 6 DOF 컨트롤러의 트리거에 매핑하는 것이 유용할 수 있습니다. 그런 다음 애플리케이션 논리가 생성할 수 있는 모든 다른 입력을 인식하는 대신 입력 *선택* 작업 이벤트를 수신 대기하도록 할 수 있습니다. 입력 작업은 Mixed Reality Toolkit *구성* 요소의 입력 시스템 프로필 내에 있는 입력 **작업** *프로필* 에 정의됩니다.

[**컨트롤러는**](controllers.md) 입력 디바이스가 손실되거나 연결이 끊어지면 입력 디바이스가 검색되고 소멸될 때 입력 *공급자에* 의해 생성됩니다. 예를 들어 WMR 입력 공급자는 6개의 DOF 디바이스용 *WMR 컨트롤러와* 연결된 손을 위한 *WMR 연결된 손 컨트롤러를* 만듭니다. 컨트롤러 입력은 입력 시스템 **프로필 내의 컨트롤러 매핑 프로필을** 통해 *입력* 작업에 매핑할 수 있습니다. 컨트롤러에서 발생하는 입력 이벤트에는 연결된 입력 작업(있는 경우)이 포함됩니다.

컨트롤러는 장면을 [](pointers.md) 쿼리하여 포커스가 있는 게임 개체를 확인하고 포인터 이벤트를 발생시키는 [**포인터를**](pointers.md#pointer-event-interfaces) 연결할 수 있습니다. 예를 들어 *선 포인터는* 컨트롤러 자세를 사용하여 광선의 원점과 방향을 계산하는 장면에 대해 광선 캐스팅을 수행합니다. 각 컨트롤러에 대해 생성된 포인터는 **포인터 프로필** 의 *입력 시스템 프로필* 아래에 설정됩니다.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>이벤트 흐름.</sup>

[UI 구성 요소에서 직접 입력 이벤트를](input-events.md)처리할 수 있지만 [포인터 이벤트를](pointers.md#pointer-event-interfaces) 사용하여 구현 디바이스를 독립적으로 유지하는 것이 좋습니다.

또한 MRTK는 디바이스 독립적 방식으로 입력 상태를 직접 쿼리하는 몇 가지 편리한 메서드를 제공합니다. 자세한 내용은 [MRTK의 입력 상태 액세스를](input-state.md) 참조하세요.
