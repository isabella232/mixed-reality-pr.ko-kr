---
title: Unity의 음성 입력
description: Unity가 음성 입력, 음성 인식 및 받아쓰기를 Windows Mixed Reality 애플리케이션에 추가하는 세 가지 방법을 노출하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 음성 입력, KeywordRecognizer, GrammarRecognizer, 마이크, 받아쓰기, 음성, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 6b040443606e05843f85b2f74f5ea812daafba31
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489203"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="094c6-104">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="094c6-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="094c6-105">시작하기 전에 Cognitive Speech Services SDK에 Unity 플러그 인을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="094c6-106">플러그 인은 더 나은 음성 정확도 결과 및 음성-텍스트 디코딩에 쉽게 액세스할 수 있으며 대화 상자, 의도 기반 상호 작용, 번역, 텍스트 음성 변환 및 자연어 음성 인식과 같은 고급 음성 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="094c6-107">시작하려면 [샘플 및 설명서를 확인하세요.](/azure/cognitive-services/speech-service/quickstart-csharp-unity)</span><span class="sxs-lookup"><span data-stu-id="094c6-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="094c6-108">Unity는 Unity 애플리케이션에 [음성 입력을](../../design/voice-input.md) 추가하는 세 가지 방법을 노출하며, 그 중 처음 두 가지는 PhraseRecognizer 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="094c6-109">는 `KeywordRecognizer` 수신 대기할 문자열 명령 배열을 앱에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="094c6-110">는 `GrammarRecognizer` 수신 대기할 특정 문법을 정의하는 SRGS 파일을 앱에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="094c6-111">`DictationRecognizer`을 사용하면 앱이 단어를 수신 대기하고 사용자에게 음성의 메모 또는 기타 표시를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="094c6-112">받아쓰기 및 구 인식은 동시에 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="094c6-113">GrammarRecognizer 또는 KeywordRecognizer가 활성 상태인 경우 DictationRecognizer는 활성 상태일 수 없으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="094c6-114">음성에 기능 사용</span><span class="sxs-lookup"><span data-stu-id="094c6-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="094c6-115">**앱에서** 음성 입력을 사용하려면 마이크 기능을 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="094c6-116">Unity 편집기에서 **프로젝트 설정 > 플레이어 > 편집으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="094c6-117">Windows **스토어** 탭 선택</span><span class="sxs-lookup"><span data-stu-id="094c6-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="094c6-118">게시 **설정 > 기능** 섹션에서 **마이크** 기능을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="094c6-119">HoloLens 디바이스에서 마이크 액세스 권한을 앱에 부여</span><span class="sxs-lookup"><span data-stu-id="094c6-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="094c6-120">디바이스 시작 시 이 작업을 수행하라는 메시지가 표시되지만 실수로 "아니요"를 클릭한 경우 디바이스 설정에서 사용 권한을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="094c6-121">구 인식</span><span class="sxs-lookup"><span data-stu-id="094c6-121">Phrase Recognition</span></span>

<span data-ttu-id="094c6-122">앱이 사용자가 말하는 특정 구를 수신 대기한 다음, 일부 작업을 수행하도록 하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="094c6-123">또는을 사용 하 여 수신 대기할 문구 지정 `KeywordRecognizer``GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="094c6-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="094c6-124">이벤트를 처리 `OnPhraseRecognized` 하 고 인식 된 구에 해당 하는 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="094c6-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="094c6-125">KeywordRecognizer</span></span>

<span data-ttu-id="094c6-126">**네임 스페이스:** *Unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="094c6-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="094c6-127">**유형:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="094c6-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="094c6-128">몇 가지 using 문을 사용 하 여 몇 가지 키 입력을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="094c6-129">그런 다음 클래스에 몇 개의 필드를 추가 하 여 인식기 및 키워드 >동작 사전을 저장 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="094c6-130">이제 메서드의 등에서 키워드를 사전에 추가 합니다 `Start()` .</span><span class="sxs-lookup"><span data-stu-id="094c6-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="094c6-131">이 예에서는 "activate" 키워드를 추가 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="094c6-132">키워드 인식기를 만들고 인식 하려는 항목을 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="094c6-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="094c6-133">이제 `OnPhraseRecognized` 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="094c6-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="094c6-134">예제 처리기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-134">An example handler is:</span></span>

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

<span data-ttu-id="094c6-135">마지막으로 인식을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="094c6-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="094c6-136">GrammarRecognizer</span></span>

<span data-ttu-id="094c6-137">**네임 스페이스:** *Unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="094c6-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="094c6-138">**유형**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="094c6-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="094c6-139">GrammarRecognizer는 SRGS를 사용 하 여 인식 문법을 지정 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="094c6-140">이는 앱에 몇 개의 키워드 이상이 있거나 더 복잡 한 구를 인식 하거나 명령 집합을 쉽게 설정 하 고 해제 하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="094c6-141">참조: 파일 형식 정보는 [SRGS XML을 사용 하 여 문법 만들기](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="094c6-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="094c6-142">SRGS 문법이 있고 [Streamingassets 폴더](https://docs.unity3d.com/Manual/StreamingAssets.html)의 프로젝트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="094c6-143">를 만들고 `GrammarRecognizer` SRGS 파일에 경로를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="094c6-144">이제 이벤트에 등록합니다. `OnPhraseRecognized`</span><span class="sxs-lookup"><span data-stu-id="094c6-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="094c6-145">적절하게 처리할 수 있는 SRGS 문법에 지정된 정보가 포함된 콜백이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="094c6-146">대부분의 중요한 정보는 `semanticMeanings` 배열에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="094c6-147">마지막으로, 인식하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="094c6-148">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="094c6-148">Dictation</span></span>

<span data-ttu-id="094c6-149">**네임스페이스:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="094c6-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="094c6-150">**형식:** *DictationRecognizer,* *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="094c6-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="094c6-151">를 사용하여 `DictationRecognizer` 사용자의 음성을 텍스트로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="094c6-152">DictationRecognizer는 [받아쓰기](../../design/voice-input.md#dictation) 기능을 노출하고 가설 및 구가 완료된 이벤트의 등록 및 수신 대기를 지원하므로 사용자가 말하는 동안 및 나중에 사용자에게 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="094c6-153">`Start()` 및 `Stop()` 메서드는 각각 받아쓰기 인식을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="094c6-154">인식기를 사용하여 완료되면 를 사용하여 삭제하여 `Dispose()` 사용하는 리소스를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="094c6-155">이전에 릴리스되지 않은 경우 추가 성능 비용으로 가비지 수집 중에 이러한 리소스를 자동으로 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="094c6-156">받아쓰기를 시작하는 데 필요한 몇 가지 단계만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="094c6-157">새 만들기 `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="094c6-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="094c6-158">받아쓰기 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="094c6-158">Handle Dictation events</span></span>
3. <span data-ttu-id="094c6-159">DictationRecognizer 시작</span><span class="sxs-lookup"><span data-stu-id="094c6-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="094c6-160">받아쓰기 기능 사용</span><span class="sxs-lookup"><span data-stu-id="094c6-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="094c6-161">앱에서 받아쓰기를 사용하려면 **인터넷 클라이언트** 및 **마이크** 기능을 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="094c6-162">Unity 편집기에서 **프로젝트 설정 > 플레이어 > 편집으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="094c6-163">**Windows 스토어** 탭에서 선택</span><span class="sxs-lookup"><span data-stu-id="094c6-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="094c6-164">**게시 설정 > 기능** 섹션에서 **internetclient** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="094c6-165">필요에 따라 마이크를 아직 사용 하도록 설정 하지 않은 경우 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="094c6-166">HoloLens 장치에서 마이크 액세스 권한을 앱에 부여 합니다 (아직 없는 경우).</span><span class="sxs-lookup"><span data-stu-id="094c6-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="094c6-167">장치를 시작할 때이 작업을 수행 하 라는 메시지가 표시 됩니다. 하지만 실수로 "아니요"를 클릭 한 경우 장치 설정에서 사용 권한을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="094c6-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="094c6-168">DictationRecognizer</span></span>

<span data-ttu-id="094c6-169">다음과 같이 DictationRecognizer를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="094c6-170">받아쓰기 동작을 구현 하기 위해 구독 하 고 처리할 수 있는 받아쓰기 이벤트는 네 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="094c6-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="094c6-171">**DictationResult**</span></span>

<span data-ttu-id="094c6-172">이 이벤트는 일반적으로 문장의 끝에 사용자가 일시 중지 한 후에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="094c6-173">여기에는 전체 인식 된 문자열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="094c6-174">먼저 이벤트를 구독 합니다 `DictationResult` .</span><span class="sxs-lookup"><span data-stu-id="094c6-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="094c6-175">그런 다음 DictationResult 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="094c6-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="094c6-176">**DictationHypothesis**</span></span>

<span data-ttu-id="094c6-177">이 이벤트는 사용자가 통신 하는 동안 지속적으로 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="094c6-178">인식기는 수신 대기 하는 동안 지금까지 수신 하는 내용에 대 한 텍스트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="094c6-179">먼저 이벤트를 구독 합니다 `DictationHypothesis` .</span><span class="sxs-lookup"><span data-stu-id="094c6-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="094c6-180">그런 다음 DictationHypothesis 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="094c6-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="094c6-181">**DictationComplete**</span></span>

<span data-ttu-id="094c6-182">이 이벤트는 인식기가 중지 될 때 발생 합니다. 중지 ()를 호출할 때 발생 하는 시간 초과 또는 다른 오류가 발생 했는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="094c6-183">먼저 이벤트를 구독 합니다 `DictationComplete` .</span><span class="sxs-lookup"><span data-stu-id="094c6-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="094c6-184">그런 다음, DictationComplete 콜백을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="094c6-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="094c6-185">**DictationError**</span></span>

<span data-ttu-id="094c6-186">이 이벤트는 오류가 발생할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="094c6-187">먼저 이벤트를 구독합니다. `DictationError`</span><span class="sxs-lookup"><span data-stu-id="094c6-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="094c6-188">그런 다음, DictationError 콜백을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="094c6-189">관심 있는 받아쓰기 이벤트를 구독하고 처리한 후에는 받아쓰기 인식기를 시작하여 이벤트 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="094c6-190">DictationRecognizer를 더 이상 유지하지 않으려는 경우 이벤트 구독을 취소하고 DictationRecognizer를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="094c6-191">**팁**</span><span class="sxs-lookup"><span data-stu-id="094c6-191">**Tips**</span></span>
* <span data-ttu-id="094c6-192">`Start()` 및 `Stop()` 메서드는 각각 받아쓰기 인식을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="094c6-193">인식기를 사용하여 작업을 완료한 후에는 를 사용하여 삭제하여 `Dispose()` 사용하는 리소스를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="094c6-194">이전에 릴리스되지 않은 경우 추가 성능 비용으로 가비지 수집 중에 이러한 리소스를 자동으로 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="094c6-195">시간 제한은 설정된 기간 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="094c6-196">이벤트에서 이러한 시간 초과를 확인할 수 `DictationComplete` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="094c6-197">다음 두 가지 시간 제한에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="094c6-198">인식기 시작 하 고 처음 5 초 동안 오디오를 하지 않으면 시간 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="094c6-199">인식기에서 결과를 제공했지만 20초 동안 묵음이 들은 경우 시간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="094c6-200">구 인식 및 받아쓰기 사용</span><span class="sxs-lookup"><span data-stu-id="094c6-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="094c6-201">앱에서 구 인식과 받아쓰기를 모두 사용하려면 한 구를 완전히 종료해야 다른 구문을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="094c6-202">여러 KeywordRecognizer를 실행하는 경우 다음을 통해 한 번에 모두 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="094c6-203">`Restart()`를 호출하여 DictationRecognizer가 중지된 후 모든 인식기를 이전 상태로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="094c6-204">KeywordRecognizer를 시작하면 PhraseRecognitionSystem도 다시 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="094c6-205">Mixed Reality Toolkit의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="094c6-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="094c6-206">다음 데모 장면에서 음성 입력에 대 한 MRTK 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="094c6-207">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="094c6-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="094c6-208">Speech</span><span class="sxs-lookup"><span data-stu-id="094c6-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="094c6-209">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="094c6-209">Next Development Checkpoint</span></span>

<span data-ttu-id="094c6-210">앞서 설명한 Unity 개발 검사점 경험을 팔로 하는 경우 다음 작업은 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="094c6-211">공유 환경</span><span class="sxs-lookup"><span data-stu-id="094c6-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="094c6-212">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="094c6-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>