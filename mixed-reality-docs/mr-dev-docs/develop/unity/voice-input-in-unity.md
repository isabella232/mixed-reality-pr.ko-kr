---
title: Unity의 음성 입력
description: Unity가 음성 입력, 음성 인식 및 받아쓰기를 Windows Mixed Reality 애플리케이션에 추가하는 세 가지 방법을 노출하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 음성 입력, KeywordRecognizer, GrammarRecognizer, 마이크, 받아쓰기, 음성, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: e436c320a2f4393eeae86a7a936a6afa8e8a15f91ba803e95e6a318b117ee81c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216409"
---
# <a name="voice-input-in-unity"></a>Unity의 음성 입력

> [!CAUTION]
> 시작하기 전에 Cognitive Speech Services SDK에 Unity 플러그 인을 사용하는 것이 좋습니다. 플러그 인은 더 나은 음성 정확도 결과 및 음성-텍스트 디코딩에 쉽게 액세스할 수 있으며 대화 상자, 의도 기반 상호 작용, 번역, 텍스트 음성 변환 및 자연어 음성 인식과 같은 고급 음성 기능을 제공합니다. 시작하려면 [샘플 및 설명서를 확인하세요.](/azure/cognitive-services/speech-service/quickstart-csharp-unity)

Unity는 Unity 애플리케이션에 [음성 입력을](../../design/voice-input.md) 추가하는 세 가지 방법을 노출하며, 그 중 처음 두 가지는 PhraseRecognizer 형식입니다.
* 는 `KeywordRecognizer` 수신 대기할 문자열 명령 배열을 앱에 제공합니다.
* 는 `GrammarRecognizer` 수신 대기할 특정 문법을 정의하는 SRGS 파일을 앱에 제공합니다.
* `DictationRecognizer`을 사용하면 앱이 단어를 수신 대기하고 사용자에게 음성의 메모 또는 기타 표시를 제공할 수 있습니다.

> [!NOTE]
> 받아쓰기 및 구 인식은 동시에 처리할 수 없습니다. GrammarRecognizer 또는 KeywordRecognizer가 활성 상태인 경우 DictationRecognizer는 활성 상태일 수 없으며 그 반대의 경우도 마찬가지입니다.

## <a name="enabling-the-capability-for-voice"></a>음성 기능 사용

**앱에서** 음성 입력을 사용하려면 마이크 기능을 선언해야 합니다.
1. Unity 편집기에서 **> Project 설정 > 플레이어 편집으로** 이동합니다.
2. Windows **스토어** 탭 선택
3. 게시 **설정 > 기능** 섹션에서 **마이크** 기능을 확인합니다.
4. HoloLens 디바이스에서 마이크 액세스 권한을 앱에 부여합니다.
    * 디바이스 시작 시 이 작업을 수행하라는 메시지가 표시되지만 실수로 "아니요"를 클릭한 경우 디바이스 설정에서 사용 권한을 변경할 수 있습니다.

## <a name="phrase-recognition"></a>구 인식

앱이 사용자가 말하는 특정 구를 수신 대기한 다음, 일부 작업을 수행하도록 하려면 다음을 수행해야 합니다.
1. 또는 을 사용하여 수신 대기할 구를 지정합니다. `KeywordRecognizer``GrammarRecognizer`
2. 이벤트를 `OnPhraseRecognized` 처리하고 인식된 구에 해당하는 작업을 수행합니다.

### <a name="keywordrecognizer"></a>KeywordRecognizer

**네임스페이스:** *UnityEngine.Windows. 음성*<br>
**형식:** *KeywordRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError*, *SpeechSystemStatus*

몇 가지 키 입력을 저장하려면 몇 가지 using 문이 필요합니다.

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

그런 다음, 클래스에 몇 가지 필드를 추가하여 인식기 및 키워드 >동작 사전을 저장해 보겠습니다.

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

이제 사전에 키워드를 추가합니다(예: `Start()` 메서드의 ). 이 예제에서는 "activate" 키워드를 추가합니다.

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

키워드 인식기를 만들고 인식할 내용을 알려줍니다.

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

이제 이벤트에 등록합니다. `OnPhraseRecognized`

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

예제 처리기는 다음과 같습니다.

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

마지막으로, 인식하기 시작합니다.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**네임스페이스:** *UnityEngine.Windows. 음성*<br>
**형식:** *GrammarRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer는 SRGS를 사용하여 인식 문법을 지정하는 경우에 사용됩니다. 앱에 키워드가 몇 개 이상 있거나, 더 복잡한 구를 인식하려는 경우 또는 명령 집합을 쉽게 설정 및 해제하려는 경우에 유용할 수 있습니다. 참조: 파일 형식 정보에 대 한 [SRGS XML을 사용 하 여 문법 만들기합니다.](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14))

SRGS 문법이 있고 [StreamingAssets 폴더의](https://docs.unity3d.com/Manual/StreamingAssets.html)프로젝트에 있으면 입니다.

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

를 만들고 `GrammarRecognizer` SRGS 파일에 경로를 전달합니다.

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

이제 이벤트에 등록합니다. `OnPhraseRecognized`

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

적절하게 처리할 수 있는 SRGS 문법에 지정된 정보가 포함된 콜백이 표시됩니다. 대부분의 중요한 정보는 `semanticMeanings` 배열에 제공됩니다.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

마지막으로, 인식하기 시작합니다.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>받아쓰기

**네임스페이스:** *UnityEngine.Windows. 음성*<br>
**형식:** *DictationRecognizer,* *SpeechError*, *SpeechSystemStatus*

를 사용하여 `DictationRecognizer` 사용자의 음성을 텍스트로 변환합니다. DictationRecognizer는 [받아쓰기](../../design/voice-input.md#dictation) 기능을 노출하고 가설 및 구가 완료된 이벤트의 등록 및 수신 대기를 지원하므로 사용자가 말하는 동안 및 나중에 사용자에게 피드백을 제공할 수 있습니다. `Start()` 및 `Stop()` 메서드는 각각 받아쓰기 인식을 사용하거나 사용하지 않도록 설정합니다. 인식기를 사용하여 완료되면 를 사용하여 삭제하여 `Dispose()` 사용하는 리소스를 해제해야 합니다. 이전에 릴리스되지 않은 경우 추가 성능 비용으로 가비지 수집 중에 이러한 리소스를 자동으로 해제합니다.

받아쓰기를 시작하는 데 필요한 몇 가지 단계만 있습니다.
1. 새 만들기 `DictationRecognizer`
2. 받아쓰기 이벤트 처리
3. DictationRecognizer 시작

### <a name="enabling-the-capability-for-dictation"></a>받아쓰기 기능 사용

앱에서 받아쓰기를 사용하려면 **인터넷 클라이언트** 및 **마이크** 기능을 선언해야 합니다.
1. Unity 편집기에서 **> Project 설정 > 플레이어 편집으로** 이동합니다.
2. **Windows 스토어** 탭에서 선택
3. 게시 **설정 > 기능** 섹션에서 **InternetClient** 기능을 확인합니다.
    * 필요에 따라 마이크를 사용하도록 설정하지 않은 경우 **마이크** 기능을 확인합니다.
4. HoloLens 디바이스에서 마이크 액세스 권한을 앱에 부여합니다(아직 없는 경우).
    * 디바이스 시작 시 이 작업을 수행하라는 메시지가 표시되지만 실수로 "아니요"를 클릭한 경우 디바이스 설정에서 사용 권한을 변경할 수 있습니다.

### <a name="dictationrecognizer"></a>DictationRecognizer

다음과 같이 DictationRecognizer를 만듭니다.

```
dictationRecognizer = new DictationRecognizer();
```

받아쓰기 동작을 구현하기 위해 구독하고 처리할 수 있는 4개의 받아쓰기 이벤트가 있습니다.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

이 이벤트는 일반적으로 문장 끝에서 사용자가 일시 중지한 후에 발생합니다. 인식된 전체 문자열이 여기에 반환됩니다.

먼저 이벤트를 구독합니다. `DictationResult`

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

그런 다음, DictationResult 콜백을 처리합니다.

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

이 이벤트는 사용자가 대화하는 동안 지속적으로 발생합니다. 인식기는 수신 대기하면서 지금까지 들은 내용의 텍스트를 제공합니다.

먼저 이벤트를 구독합니다. `DictationHypothesis`

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

그런 다음, DictationHypothesis 콜백을 처리합니다.

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

이 이벤트는 호출 중인 Stop()에서, 시간 제한 발생 또는 기타 오류 등 인식기 중지 시 발생합니다.

먼저 이벤트를 구독합니다. `DictationComplete`

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

그런 다음, DictationComplete 콜백을 처리합니다.

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

이 이벤트는 오류가 발생할 때 발생합니다.

먼저 이벤트를 구독합니다. `DictationError`

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

그런 다음, DictationError 콜백을 처리합니다.

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

관심 있는 받아쓰기 이벤트를 구독하고 처리한 후에는 받아쓰기 인식기를 시작하여 이벤트 수신을 시작합니다.

```
dictationRecognizer.Start();
```

DictationRecognizer를 더 이상 유지하지 않으려는 경우 이벤트 구독을 취소하고 DictationRecognizer를 삭제해야 합니다.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**팁**
* `Start()` 및 `Stop()` 메서드는 각각 받아쓰기 인식을 사용하거나 사용하지 않도록 설정합니다.
* 인식기를 사용하여 작업을 완료한 후에는 를 사용하여 삭제하여 `Dispose()` 사용하는 리소스를 해제해야 합니다. 이전에 릴리스되지 않은 경우 추가 성능 비용으로 가비지 수집 중에 이러한 리소스를 자동으로 해제합니다.
* 시간 제한은 설정된 기간 후에 발생합니다. 이벤트에서 이러한 시간 초과를 확인할 수 `DictationComplete` 있습니다. 다음 두 가지 시간 제한에 유의해야 합니다.
   1. 인식기 시작 하 고 처음 5 초 동안 오디오를 하지 않는 경우 시간 부족 합니다.
   2. 인식기에서 결과를 제공했지만 20초 동안 묵음이 들은 경우 시간이 부족합니다.

## <a name="using-both-phrase-recognition-and-dictation"></a>구 인식 및 받아쓰기 사용

앱에서 구 인식과 받아쓰기를 모두 사용하려면 한 구를 완전히 종료해야 다른 구문을 시작할 수 있습니다. 여러 KeywordRecognizer를 실행하는 경우 다음을 통해 한 번에 모두 종료할 수 있습니다.

```
PhraseRecognitionSystem.Shutdown();
```

`Restart()`를 호출하여 DictationRecognizer가 중지된 후 모든 인식기를 이전 상태로 복원할 수 있습니다.

```
PhraseRecognitionSystem.Restart();
```

KeywordRecognizer를 시작하면 PhraseRecognitionSystem도 다시 시작될 수 있습니다.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit 음성 입력

다음 데모 장면에서 음성 입력에 대한 MRTK 예제를 찾을 수 있습니다.
* [받아쓰기](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Speech](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

설명한 Unity 개발 검사점 여정을 수행하는 경우 다음 작업은 Mixed Reality 플랫폼 기능 및 API를 탐색하는 것입니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.