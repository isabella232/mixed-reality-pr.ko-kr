---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 몰입형 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 응시
ms.openlocfilehash: 6773bb71da7d98b1dd00d2246084d469e5e7c6ba
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600582"
---
# <a name="voice-input"></a>음성 입력

![음성 입력](images/UX_Hero_VoiceCommand.jpg)

음성은 HoloLens의 주요 입력 형태 중 하나입니다. [손 제스처를](gaze-and-commit.md#composite-gestures)사용하지 않고 홀로그램을 직접 명령할 수 있습니다. 음성 입력은 의도를 전달하는 자연스러운 방법일 수 있습니다. 음성은 사용자가 하나의 명령으로 중첩된 메뉴를 잘라낼 수 있기 때문에 복잡한 인터페이스를 트래버스하는 데 특히 적합합니다.

음성 입력은 모든 _유니버설 Windows 앱_ 에서 음성을 지원하는 동일한 [엔진에](/windows/uwp/design/input/speech-recognition) 의해 구동됩니다. HoloLens에서 음성 인식은 항상 디바이스 설정에 구성된 Windows 표시 언어로 작동합니다. 

<br>

## <a name="voice-and-gaze&quot;></a>음성 및 응시

음성 명령을 사용하는 경우 머리 또는 시선 응시는 커서를 사용하여 &quot;선택&quot;하든, 보고 있는 애플리케이션에 명령을 채널링하든 간에 일반적인 대상 지정 메커니즘입니다. 응시 커서를 표시할 필요가 없을 수도 _있습니다(&quot;see it, say it")._ 일부 음성 명령에는 "go to start" 또는 "Hey Cortana"와 같은 대상이 전혀 필요하지 않습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>음성 입력</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️(마이크 사용)</td>
    </tr>
</table>

## <a name="the-select-command"></a>"select" 명령

**HoloLens(1세대)**

앱에 음성 지원을 구체적으로 추가하지 않아도 사용자는 시스템 음성 명령 "select"를 말하여 홀로그램을 활성화할 수 있습니다. 이 동작은 HoloLens의 [에어 탭과](gaze-and-commit.md#composite-gestures) 동일하게 동작하고, [HoloLens 클릭하여](/hololens/hololens1-clicker)선택 단추를 누르거나, [Windows Mixed Reality 동작 컨트롤러에서](motion-controllers.md)트리거를 누릅니다. 소리가 들었습니다. "select"가 있는 도구 설명이 확인으로 표시됩니다. "Select"는 저전력 키워드 검색 알고리즘을 통해 사용하도록 설정됩니다. 즉, 배터리 수명 영향을 최소화하면서 언제든지 말할 수 있습니다. 손으로 "선택"을 말할 수도 있습니다.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        HoloLens 2 "select" 음성 명령을 사용하려면 먼저 포인터로 사용할 응시 커서를 가져와야 합니다. 이를 가져오는 명령은 기억하기 쉽습니다. "select"라고 말합니다.<br><br>
        모드를 종료하려면 에어 탭을 하거나 손가락으로 단추에 접근하거나 시스템 제스처를 사용하여 손을 다시 사용합니다.<br>
        <br> 
        *이미지: 선택 영역의 음성 명령을 사용하려면 "select"라고 말하세요.*
    :::column-end:::
        :::column:::
       ![사용자는 "select"라고 말하여 선택 항목에 음성 명령을 사용할 수 있습니다.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hey Cortana

언제든지 Cortana를 불러 오도록 "Hey Cortana"라고 말할 수 있습니다. 계속해서 질문을 하거나 지침을 제공하는 것처럼 보일 때까지 기다릴 필요가 없습니다. 예를 들어 "Hey Cortana, 날씨는 무엇인가요?"라고 말해 보세요. 단일 문장으로. Cortana에 대한 자세한 내용과 수행할 수 있는 작업을 알려주세요. "Hey Cortana, 무슨 말을 할 수 있나요?"라고 말하세요. 그리고 작업 및 제안된 명령 목록을 끌어올 것입니다. Cortana 앱에 이미 있는 경우 **?** 이 동일한 메뉴를 끌어오려면 사이드바에 아이콘을 표시합니다.

**HoloLens 관련 명령**
* "What can I say?"
* "Go to Start" - [시작 메뉴로](../discover/navigating-the-windows-mixed-reality-home.md#start-menu) 가는 [것을 피울](system-gesture.md#bloom) 대신
* "Launch <app> "
* <app>"여기로 이동"
* "Take a picture"
* "기록 시작"
* "Stop recording"
* "손 광선 표시"
* "손 광선 숨기기"
* "밝기 늘리기"
* "밝기 감소"
* "볼륨 늘리기"
* "볼륨 감소"
* "음소거" 또는 "음소거 해제"
* "디바이스 종료"
* "디바이스 다시 시작"
* "절전 모드로 이동"
* "What time is it?"
* "얼마나 많은 배터리가 남아 있나요?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"See it, Say It"<br>
        HoloLens에는 음성 입력을 위한 "see it, say it" 모델이 있습니다. 여기서 단추의 레이블은 사용자가 말할 수 있는 음성 명령도 알려줍니다. 예를 들어 HoloLens(1세대)에서 앱 창을 볼 때 사용자는 "조정" 명령을 말하여 전 세계에서 앱의 위치를 조정할 수 있습니다.<br>
        <br>
        *이미지: 사용자가 앱 표시줄에 표시되는 "조정" 명령을 말하여 앱의 위치를 조정할 수 있습니다.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![앱 창 또는 홀로그램을 볼 때 사용자는 앱 표시줄에 표시되는 "조정" 명령을 말하여 전 세계에서 앱의 위치를 조정할 수 있습니다.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        앱이 이 규칙을 따르는 경우 사용자는 시스템을 제어하기 위해 말하는 내용을 쉽게 이해할 수 있습니다. HoloLens(1세대)의 단추를 눌렀을 때 단추가 음성을 사용하도록 설정되어 있고 "누르기" 명령을 표시하면 1초 후에 나오는 "음성 계속" 도구 설명이 표시됩니다. HoloLens 2 음성 도구 설명에 표시하려면 "select" 또는 "What can I say"(이미지 참조)라고 말하여 음성 커서를 표시합니다. <br>
        <br>
        *이미지: 단추 아래에 "See it, say it" 명령이 표시됩니다.*
    :::column-end:::
        :::column:::
       ![이를 확인합니다. 명령이 단추 아래에 표시되면](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>빠른 홀로그램 조작을 위한 음성 명령

홀로그램에서 조작 작업을 빠르게 수행하는 동안 많은 음성 명령을 말할 수 있습니다. 이러한 음성 명령은 전 세계에 배치된 앱 창 및 3D 개체에서 작동합니다.

**홀로그램 조작 명령**
* Face me
* 더 큰 | 향상
* 작음

HoloLens 2 참조하는 내용에 대한 컨텍스트 정보를 암시적으로 제공하는 시선 응시와 함께 보다 자연스러운 상호 작용을 만들 수도 있습니다. 예를 들어 홀로그램을 보고 _"put this"라고_ 말한 다음, 배치할 위치를 살펴보고 "here "를 통해"라고 말할 수 _있습니다._
또는 복잡한 컴퓨터의 홀로그램 부분을 살펴보고 다음과 같이 말할 수 있습니다. _"이에_ 대한 자세한 정보를 제공해 주세요."

## <a name="discovering-voice-commands"></a>음성 명령 검색

위의 빠른 조작을 위한 명령과 같은 일부 명령은 숨길 수 있습니다. 사용할 수 있는 명령에 대해 알아보려면 개체를 응시하고 "무엇을 말할 수 있나요?"라고 말합니다. 가능한 명령 목록이 표시됩니다. 머리 응시 커서를 사용하여 주변을 둘러보고 앞에 있는 각 단추의 음성 도구 설명도 표시할 수 있습니다. 

전체 목록을 원하는 경우 언제든지 "모든 명령 표시"라고 말하면 됩니다. 

## <a name="dictation"></a>받아쓰기

[에어 탭으로](gaze-and-commit.md#composite-gestures)입력하는 대신 음성 받아쓰기를 사용하여 앱에 텍스트를 입력하는 것이 더 효율적일 수 있습니다. 이렇게 하면 사용자가 더 적은 노력으로 입력을 크게 가속화할 수 있습니다.

![마이크 단추를 선택하여 음성 받아쓰기 시작](images/micbuttonfordictation.png)<br>
*키보드에서 마이크 단추를 선택하여 음성 받아쓰기 시작*

홀로그램 키보드가 활성 상태일 때마다 입력하는 대신 받아쓰기 모드로 전환할 수 있습니다. 시작하려면 텍스트 입력 상자 옆에 있는 마이크를 선택합니다.

## <a name="adding-voice-commands-to-your-app"></a>앱에 음성 명령 추가

빌드하는 모든 환경에 음성 명령을 추가하는 것이 좋습니다. 음성은 시스템과 앱을 제어하는 강력한 방법입니다. 사용자는 다양한 종류의 언어와 악센트를 사용하기 때문에 적절한 음성 키워드를 선택하면 사용자의 명령이 명확하게 해석됩니다.

### <a name="best-practices"></a>모범 사례

다음은 매끄러운 음성 인식에 도움이 될 수 있는 몇 가지 사례입니다.
* **간결한 명령 사용** - 가능한 경우 두 개 이상의 음절로 이루어진 키워드를 선택합니다. 1음절 단어는 악센트가 다른 사람이 말할 경우 다른 모음 소리를 사용할 수 있습니다. 예: "비디오 재생"이 "현재 선택한 비디오 재생"보다 낫습니다.
* **간단한 어휘 사용** - 예: "메모 표시"가 "placard 표시"보다 낫습니다.
* **명령이 비파괴적인지 확인** - 음성 명령 동작이 비파괴적인지 확인하고 사용자 가까이에서 말하는 다른 사람이 실수로 명령을 트리거하는 경우 쉽게 실행 취소할 수 있습니다.
* **유사한 소리 명령 방지** - 비슷한 소리의 여러 음성 명령을 등록하지 않습니다. 예: "Show more" 및 "Show store"는 유사한 소리일 수 있습니다.
* **사용하지 않을 때 앱 등록 취소** - 앱이 특정 음성 명령이 유효한 상태가 아닌 경우 다른 명령이 혼동하지 않도록 등록 취소하는 것이 좋습니다.
* **다른 악센트로 테스트** - 다른 악센트의 사용자와 앱을 테스트합니다.
* **음성 명령 일관성 유지** - "Go back"이라고 말할 경우 이전 페이지로 이동되면 애플리케이션에서 이 동작을 유지합니다.
* **시스템 명령 사용 방지** - 다음 음성 명령은 시스템용으로 예약되므로 애플리케이션에서 사용하지 않도록 합니다.
   * "Hey Cortana"
   * "Select"
   * "Go to start"

### <a name="advantages-of-voice-input"></a>음성 입력의 이점

음성 입력은 의도를 전달하는 자연스러운 방법입니다. 음성은 사용자가 인터페이스의 여러 단계를 잘라내는 데 도움이 될 수 있으므로 인터페이스 **순회에** 특히 적합합니다. 사용자가 위로 이동하여 앱의 뒤로 단추를 누르는 대신 웹 페이지를 보는 동안 "뒤로 이동"을 말할 수 있습니다. 이 작은 시간 절약은 환경의 사용자 인식에 강력한 **감정 효과를** 주고 적은 양의 초능력을 제공합니다. 팔에 무언가를 잔뜩 들고 있거나 **멀티태스킹** 중일 때도 음성을 사용하는 것이 편리한 입력 방법입니다. 키보드에서 입력하기 어려운 디바이스에서 **음성 받아쓰기는** 텍스트를 입력하는 효율적인 대체 방법이 될 수 있습니다. 마지막으로 응시 및 제스처에 대한 **정확도 범위가** 제한된 경우 음성이 사용자의 의도를 명확하게 구분하는 데 도움이 될 수 있습니다. 

**사용자에게 도움이 될 수 있는 음성 사용 방법**
* 시간 단축 - 보다 효율적으로 최종 목표에 도달할 수 있어야 합니다.
* 최소의 노력 - 보다 유연하고 편리하게 작업할 수 있도록 해야 합니다.
* 인지 부담 감소 - 직관적이며 배우고 기억하기 쉽습니다.
* 사회적으로 허용되며, 사회적 행동 규범에 부합해야 합니다.
* 일상적임 - 음성이 습관적인 동작이 될 수 있습니다.

### <a name="challenges-for-voice-input"></a>음성 입력에 대한 과제

음성 입력은 다양한 애플리케이션에 적합하지만 몇 가지 문제에 직면합니다. 음성 입력의 장점과 과제를 모두 이해하면 앱 개발자가 음성 입력을 사용하는 방법과 시기를 더 스마트하게 선택할 수 있으며 사용자에게 훌륭한 환경을 만들 수 있습니다.

**연속 입력 제어에 대한 음성 입력** 세분화된 제어가 그 중 하나입니다. 예를 들어 사용자는 음악 앱에서 볼륨을 변경하려고 할 수 있습니다. "더 크게" 말할 수 있지만 시스템에서 볼륨을 얼마나 크게 만들어야 하는지는 명확하지 않습니다. 사용자는 "조금 더 크게 만드세요"라고 말할 수 있지만 "약간"은 수량화하기 어렵습니다. 음성으로 홀로그램을 이동하거나 크기를 조정하는 것도 비슷하게 어렵습니다. 

**음성 입력 감지의 안정성** 음성 입력 시스템은 향상되고 향상되지만 음성 명령을 잘못 듣고 해석하는 경우도 있습니다.
핵심은 애플리케이션의 과제를 해결하는 것입니다. 시스템이 수신 대기 중일 때 사용자에게 피드백을 제공하고 시스템에서 이해한 내용이 사용자의 음성을 이해하는 잠재적인 문제를 명확히 합니다.  

**공유 공간의 음성 입력** 음성은 다른 사람과 공유하는 공간에서 사회적으로 허용되지 않을 수 있습니다.
다음은 몇 가지 예입니다.
* 사용자가 다른 사용자를 방해하지 않을 수 있습니다(예: Quiet Library 또는 공유 사무실).
* 사용자는 공개적으로 자신에게 말하는 것을 보고 불편할 수 있습니다.
* 사용자는 다른 사용자가 수신 대기하는 동안 개인 또는 기밀 메시지(암호 포함)를 받아쓰는 것을 좋아할 수 있습니다.

**고유하거나 알 수 없는 단어의 음성 입력** 사용자가 애칭, 특정 속어 단어 또는 약어와 같이 시스템에서 알 수 없는 단어를 받아쓰는 경우에도 음성 입력에 대한 어려움이 있습니다. 

**음성 명령 학습** 최종 목표는 시스템과 자연스럽게 대화하는 것이지만, 앱은 여전히 미리 정의된 특정 음성 명령을 사용하는 경우가 많습니다.
중요한 음성 명령 집합과 관련된 과제는 사용자를 오버로드하지 않고 학습하는 방법과 사용자가 음성 명령을 유지하도록 돕는 방법입니다. 

<br>

---

### <a name="voice-feedback-states"></a>음성 피드백 상태

음성이 제대로 적용되면 사용자는 **말할 수 있는 사항** 을 이해하고 시스템이 **올바르게 알아 들었다는 명확한 피드백을 받게 됩니다**. 이러한 두 신호를 통해 사용자는 음성을 기본 입력으로 사용할 때 안심할 수 있습니다. 다음은 음성 입력이 인식될 때 커서에 나타나는 결과와 사용자에게 이러한 사실을 전달하는 방법을 보여 주는 다이어그램입니다.


:::row:::
    :::column:::
       ![1. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)<br>
       **1. 일반 커서 상태**<br>
    :::column-end:::
    :::column:::
       ![2. 음성 피드백을 전달한 다음 사라집니다.](images/voicefeedbackstates-voice.jpg)<br>
        **2. 음성 피드백을 전달한 다음 사라집니다.**<br>
    :::column-end:::
    :::column:::
       ![*3. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)<br>
       **3. 일반 커서 상태로 돌아갑니다.**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>혼합 현실에서 "음성"에 대해 알아야 할 주요 사항

* 단추를 대상으로 하는 동안 **"선택"을** 말합니다(단추를 선택하는 데 어디서나 사용할 수 있습니다).
* 일부 앱에서는 작업을 수행하기 위해 **label name of an app bar button** 이라고 말할 수 있습니다. 예를 들어 앱을 보는 동안 사용자는 "제거" 명령을 말하여 전 세계에서 앱을 제거할 수 있습니다(이렇게 하면 손으로 앱을 선택할 필요가 없습니다).
* **"Hey Cortana"라고** 말하여 Cortana 수신 대기를 시작할 수 있습니다. 질문을 하거나("Hey Cortana, how tall is the Eiffel tower"), 앱을 열도록 말하거나("Hey Cortana, open Netflix"), 시작 메뉴를 불러오도록 말할 수 있습니다("Hey Cortana, take me home").

## <a name="common-questions-and-concerns-users-have-about-voice"></a>음성에 대한 사용자의 일반적인 질문 및 어려움

* 어떤 말을 할 수 있나요?
* 시스템이 내 말을 제대로 알아듣는지 어떻게 알 수 있나요?
   * 시스템이 내 음성 명령을 계속 잘못 알아듣습니다.
   * 음성 명령을 받아도 반응하지 않습니다.
* 음성 명령을 제공할 때 잘못된 방식으로 반응합니다.
* 특정 앱이나 앱 명령을 대상으로 음성 명령을 내리려면 어떻게 하나요?
* 음성을 사용해서 항목을 HoloLens의 홀로그래픽 프레임 밖으로 보낼 수 있나요?

## <a name="communication"></a>통신

HoloLens에서 제공하는 사용자 지정된 오디오 입력 처리 옵션을 활용하려는 애플리케이션의 경우 앱에서 사용할 수 있는 다양한 [오디오 스트림 범주를](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) 이해하는 것이 중요합니다. Windows 10 여러 스트림 범주를 지원하며, HoloLens는 이러한 세 가지 스트림 범주를 사용하여 사용자 지정 처리를 통해 음성, 통신 및 기타에 맞게 조정된 마이크 오디오 품질을 최적화할 수 있습니다. 이 오디오 품질은 주변 환경 오디오 캡처(즉, "camcorder") 시나리오에 사용할 수 있습니다.
* AudioCategory_Communications 스트림 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정되며, 클라이언트에 사용자 음성의 16kHz 24비트 모노 오디오 스트림을 제공합니다.
* AudioCategory_Speech 스트림 범주는 HoloLens(Windows) 음성 엔진에 맞게 사용자 지정되며 사용자 음성의 16kHz 24비트 모노 스트림을 제공합니다. 이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.
* AudioCategory_Other 스트림 범주는 앰비언트 환경 오디오 녹음을 위해 사용자 지정되며 클라이언트에 48kHz 24비트 스테레오 오디오 스트림을 제공합니다.

이 모든 오디오 처리는 하드웨어 가속되므로 HoloLens CPU에서 동일한 처리가 수행된 경우보다 기능이 훨씬 더 적은 전력 소모를 의미합니다. CPU에서 다른 오디오 입력 처리를 실행하지 않도록 하여 시스템 배터리 수명을 최대화하고 오프로드된 기본 제공 오디오 입력 처리를 활용합니다.

## <a name="languages"></a>언어

HoloLens 2 여러 [언어를 지원합니다.](/hololens/hololens2-language-support) 여러 키보드가 설치되거나 앱이 다른 언어로 음성 인식기를 만들려고 하는 경우에도 음성 명령은 항상 시스템의 표시 언어로 실행됩니다.

## <a name="troubleshooting"></a>문제 해결

"select" 및 "Hey Cortana"을 사용하는 데 문제가 있는 경우 더 작은 공간으로 이동하거나, 노이즈 소스에서 벗어나거나, 더 크게 말하여 시도해 보세요. 현재 HoloLens의 모든 음성 인식은 미국 영어의 네이티브 스피커에 맞게 특별히 조정되고 최적화됩니다.

Windows Mixed Reality Developer Edition 릴리스 2017의 경우 초기 HMD 연결 후 로그아웃했다가 PC 데스크톱으로 다시 로그인한 후 오디오 엔드포인트 관리 논리가 계속 작동합니다. WMR OOBE를 통과한 후 처음으로 로그아웃/로그인 이벤트 전에 사용자는 HMD를 처음 연결하기 전에 시스템이 설정된 방식에 따라 오디오 없음에서 오디오 전환 없음까지 다양한 오디오 기능 문제를 경험할 수 있었습니다.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 음성 입력
**[MRTK를](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 사용하면 모든 개체에 음성 명령을 쉽게 할당할 수 있습니다. MRTK의 **음성 입력 프로필을** 사용하여 키워드를 정의합니다. **SpeechInputHandler** 스크립트를 할당하여 모든 개체가 Speech Input Profile에 정의된 키워드에 응답하도록 할 수 있습니다. SpeechInputHandler는 사용자의 신뢰도를 높이기 위해 음성 확인 레이블도 제공합니다.

* [MRTK - 음성 명령](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>참조

* [응시 및 커밋](gaze-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [DirectX의 음성 입력](../develop/native/voice-input-in-directx.md)
* [Unity의 음성 입력](../develop/unity/voice-input-in-unity.md)