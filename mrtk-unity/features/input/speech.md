---
title: 음성
description: MRTK에서 음성 입력 구성
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, Speech,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228418"
---
# <a name="speech"></a>음성

![Near 메뉴](../images/input/MRTK_Input_Speech.png)

음성 입력 *Windows* 같은 음성 입력 공급자는 컨트롤러를 만들지 않고 인식 될 때 음성 입력 이벤트를 발생 시키는 키워드를 정의할 수 있습니다. *입력 시스템 프로필* 의 **음성 명령 프로필** 은 인식할 키워드를 구성 하는 위치입니다. 각 명령에 대해 다음을 수행할 수도 있습니다.

- 매핑할 **입력 작업** 을 선택 합니다. 이러한 방식으로 예를 들어 *Select* 키워드를 사용 하 여 두 마우스를 동일한 동작으로 매핑하여 마우스 왼쪽 단추를 클릭 하는 것과 동일한 효과를 적용할 수 있습니다.
- 누를 때 동일한 음성 이벤트를 생성 하는 **키 코드** 를 지정 합니다.
- 앱 리소스에서 지역화 된 키워드를 가져오기 위해 UWP 앱에서 사용 되는 **지역화 키** 를 추가 합니다.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>음성 입력 처리

[**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler)GameObject에 스크립트를 추가 하 여 [**Unityevents**](https://docs.unity3d.com/Manual/UnityEvents.html)를 사용 하는 음성 명령을 처리할 수 있습니다. **음성 명령 프로필** 에서 정의 된 키워드 목록을 자동으로 표시 합니다.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

**SpeechConfirmationTooltip** (선택 사항)을 할당 하 여 인식에 애니메이션을 적용 하는 확인 도구 설명 레이블을 표시 합니다.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

또는 개발자가 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 사용자 지정 스크립트 구성 요소에서 인터페이스를 구현 하 여 [음성 입력 이벤트를 처리할](input-events.md#input-event-interface-example)수 있습니다.

## <a name="example-scene"></a>장면 예

에서 **SpeechInputExample** 장면은 `MRTK/Examples/Demos/Input/Scenes/Speech` 음성을 사용 하는 방법을 보여 줍니다. 을 구현 하 여 직접 스크립트에서 음성 명령 이벤트를 직접 수신할 수도 있습니다 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) ( [이벤트 처리기](input-events.md)테이블 참조).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
