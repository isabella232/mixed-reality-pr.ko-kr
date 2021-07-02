---
title: 받아쓰기
description: Docummentation는 오디오 클립을 기록 하 고 MRTK에서 기록을 얻는 방법에 대해 설명 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176477"
---
# <a name="dictation"></a>받아쓰기

받아쓰기를 통해 사용자는 오디오 클립을 기록 하 고 기록을 가져올 수 있습니다. 이를 사용 하려면 받아쓰기 시스템이 *입력 시스템 프로필* 에 등록 되어 있는지 확인 합니다. **받아쓰기 입력 공급자** 는 즉시 제공 되는 받아쓰기 시스템 이지만 다른 받아쓰기 시스템을 구현 하 여 만들 수 있습니다 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) . Windows

## <a name="requirements"></a>요구 사항

받아쓰기 시스템은 자동으로 받아쓰기를 처리 하는 데 기본 Windows speech api를 사용 하는 Unity의 [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) 를 사용 합니다. 이 기능은 Windows 기반 플랫폼에만 포함 되어 있음을 의미 합니다.

받아쓰기 시스템을 사용 하려면 [PlayerSettings 섹션](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)에서 "인터넷 클라이언트" 및 "마이크" 응용 프로그램 기능을 모두 사용 해야 합니다.
Unity의 음성 입력에 대 한 자세한 내용은 [Windows Mixed Reality 설명서](/windows/mixed-reality/voice-input-in-unity#dictation) 를 참조 하세요.

## <a name="configuration"></a>구성

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

받아쓰기 서비스를 설정한 후에는 스크립트를 사용 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) 하 여 세션을 시작 및 중지 하 고 UnityEvents를 통해 기록 결과를 가져올 수 있습니다.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **받아쓰기 가설** 은 사용자가 지금까지 캡처된 오디오의 조기에 대략적인 오디오를 말하는 경우에 발생 합니다.
- 지금까지 캡처된 오디오의 최종 기록을 사용 하 여 각 문장의 끝에 **받아쓰기 결과가** 발생 합니다 (즉, 사용자가 일시 중지 하는 경우).
- **받아쓰기 완료** 는 오디오의 전체 최종 기록과 함께 기록 세션이 끝날 때 발생 합니다.
- 받아쓰기 서비스에서 오류를 알리기 위해 **받아쓰기 오류가** 발생 합니다. 이 경우 기록에는 오류에 대 한 설명이 포함 됩니다.

## <a name="example-scene"></a>장면 예

에서 **받아쓰기** 장면을 `MRTK/Examples/Demos/Input/Scenes/Dictation` `DictationHandler` 사용 중인 스크립트를 표시 합니다. 더 많은 제어가 필요한 경우이 스크립트를 확장 하거나 직접 구현을 만들어 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) 받아쓰기 이벤트를 직접 수신할 수 있습니다.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
