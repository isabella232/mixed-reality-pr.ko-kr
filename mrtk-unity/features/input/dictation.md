---
title: 받아쓰기
description: 오디오 클립을 녹음하고 MRTK에서 전사를 가져오는 방법에 대한 누적
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220010"
---
# <a name="dictation"></a>받아쓰기

받아쓰기를 사용하면 사용자가 오디오 클립을 녹음하고 전사를 가져올 수 있습니다. 이를 사용하려면 받아쓰기 시스템이 *입력 시스템 프로필* 에 등록되어 있는지 확인합니다. **Windows 받아쓰기 입력 공급자는** 바로 제공되는 받아쓰기 시스템이지만 를 구현하는 대체 받아쓰기 시스템을 만들 수 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 있습니다.

## <a name="requirements"></a>요구 사항

받아쓰기 시스템은 받아쓰기 처리에 기본 Windows 음성 API를 사용하는 Unity의 [DictationRecognizer를](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) 사용합니다. 이는 이 기능이 Windows 기반 플랫폼에만 있음을 의미합니다.

받아쓰기 시스템을 사용하려면 [PlayerSettings - Capabilities 섹션의](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)"Internet Client" 및 "Microphone" 애플리케이션 기능이 모두 필요합니다.
Unity의 음성 입력에 대한 자세한 내용은 [Windows Mixed Reality 설명서를](/windows/mixed-reality/voice-input-in-unity#dictation) 참조하세요.

## <a name="configuration"></a>구성

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

받아쓰기 서비스가 설정되면 스크립트를 사용하여 세션 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) 기록을 시작 및 중지하고 UnityEvents를 통해 전사 결과를 얻을 수 있습니다.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **받아쓰기 가설은** 사용자가 지금까지 캡처한 오디오의 초기의 대략적인 전사로 말하면 발생합니다.
- **받아쓰기 결과는** 지금까지 캡처한 오디오의 최종 전사와 함께 각 문장의 끝에서 발생합니다(즉, 사용자가 일시 중지하는 경우).
- **받아쓰기 완료는** 오디오의 전체 최종 전사를 통해 녹음 세션이 끝날 때 발생합니다.
- **받아쓰기** 서비스의 오류를 알리기 위해 받아쓰기 오류가 발생합니다. 이 경우 전사에는 오류에 대한 설명이 포함됩니다.

## <a name="example-scene"></a>예제 장면

의 **받아쓰기** 장면에는 `MRTK/Examples/Demos/Input/Scenes/Dictation` 사용 중 스크립트가 `DictationHandler` 표시됩니다. 더 많은 제어가 필요한 경우 이 스크립트를 확장하거나 직접 구현을 만들어 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) 받아쓰기 이벤트를 직접 받을 수 있습니다.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
