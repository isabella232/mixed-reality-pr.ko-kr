---
title: 입력 작업
description: MRTK에서 입력 작업을 만드는 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, InputActions,
ms.openlocfilehash: ffa8f201097c8d85b1ea19613b608487529412f3686ddf077f1acc1c34e93c1f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211247"
---
# <a name="input-actions"></a>입력 작업

[**입력 작업은**](input-actions.md) 입력을 생성하는 특정 입력 소스에서 애플리케이션 논리를 격리하는 데 도움이 되는 원시 입력에 대한 추상화입니다. 예를 들어 *선택* 작업을 정의하고 마우스 왼쪽 단추, 게임 패드의 단추 및 6 DOF 컨트롤러의 트리거에 매핑하는 것이 유용할 수 있습니다. 그런 다음 애플리케이션 논리가 생성할 수 있는 모든 다른 입력을 인식하는 대신 입력 *선택* 작업 이벤트를 수신 대기하도록 할 수 있습니다.

## <a name="creating-an-input-action"></a>입력 작업 만들기

입력 작업은 **입력 작업 프로필에서** 구성되며, Mixed Reality Toolkit 구성 요소의 *입력 시스템 프로필* 내에서 작업 이름과 매핑할 수 있는 입력 형식(축 *제약 조건)을* 지정합니다.

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

축 **제약** 조건 에 가장 일반적으로 사용되는 값입니다.

축 제약 조건 | Description
--- | ---
디지털 | 게임 패드 또는 마우스의 이진 단추와 같은 입력 켜기/끄기
단일 축 | 게임 패드의 아날로그 트리거와 같은 단일 축 아날로그 입력입니다.
이중 축 | 엄지스틱과 같은 이중 축 아날로그 입력입니다.
Six Dof | 3D는 6개의 DOF 컨트롤러에서 생성된 것과 같이 변환 및 회전이 있는 자세를 취합니다.

에서 전체 목록을 찾을 수 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 있습니다.

## <a name="mapping-input-to-actions"></a>작업에 입력 매핑

입력을 및 작업에 매핑하는 방법은 입력 원본의 형식에 따라 달라집니다.

### <a name="controller-input"></a>컨트롤러 입력

입력 시스템 프로필 에서 **컨트롤러 입력 매핑** *프로필* 로 이동합니다. 지원되는 모든 컨트롤러 목록을 찾을 수 있습니다.

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

구성하려는 컨트롤러를 선택하면 모든 컨트롤러 입력과 함께 대화 상자 창이 표시되어 각 컨트롤러에 대한 작업을 설정할 수 있습니다.

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>음성 입력

음성 **명령 프로필의** *입력 시스템 프로필* 에서 현재 정의된 음성 명령 목록을 찾을 수 있습니다. 작업 중 하나를 작업에 매핑하려면 작업 *드롭다운에서* 선택합니다.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>제스처 입력

입력 시스템 **프로필 아래의 제스처** *프로필에는* 정의된 모든 제스처가 포함됩니다. 작업 드롭다운에서 선택하여 각 *작업을 작업에* 매핑할 수 있습니다.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>입력 작업 처리

> [!WARNING]
> 현재 *디지털* 형식의 입력 작업만 이 섹션에 설명된 메서드를 사용하여 처리할 수 있습니다. 다른 작업 유형의 경우 해당 입력에 대한 이벤트를 직접 처리해야 합니다. 예를 들어 컨트롤러 입력에 매핑된 6개의 DOF 작업을 처리하려면 T = 와 함께 를 사용해야 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 합니다.

입력 작업을 처리하는 가장 쉬운 방법은 스크립트를 사용하는 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 것입니다. 이를 통해 수신 대기하려는 작업을 정의하고 Unity 이벤트를 사용하여 시작된 작업 및 종료된 이벤트에 대응할 수 있습니다.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

더 많은 제어를 원하는 경우 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 스크립트에서 직접 인터페이스를 구현할 수 있습니다. 처리기 인터페이스를 통한 이벤트 처리에 대한 자세한 내용은 [**입력**](input-events.md) 이벤트 섹션을 참조하세요.

## <a name="examples"></a>예제

`MRTK/Examples/Demos/Input/Scenes/InputActions`작업을 만들고, 컨트롤러, 음성 및 제스처 입력에 매핑하고, 명령에서 개체를 회전하는 데 사용하는 방법을 보여주는 예제 장면을 참조하세요.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
