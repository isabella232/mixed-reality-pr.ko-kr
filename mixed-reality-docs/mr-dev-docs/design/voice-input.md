---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 응시
ms.openlocfilehash: 3f178442d892e284ed3e3454d2d54ed68c732313
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300298"
---
# <a name="voice-input"></a><span data-ttu-id="16c06-105">음성 입력</span><span class="sxs-lookup"><span data-stu-id="16c06-105">Voice input</span></span>

![음성 입력](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="16c06-107">음성은 HoloLens의 주요 입력 형태 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="16c06-108">직접 [제스처](gaze-and-commit.md#composite-gestures)를 사용 하지 않고도 홀로그램을 직접 명령을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="16c06-109">음성 입력은 의도를 전달하는 자연스러운 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="16c06-110">음성은 복잡 한 인터페이스를 트래버스하는 데 특히 유용 합니다 .이를 통해 사용자는 단일 명령을 사용 하 여 중첩 된 메뉴를 잘라낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="16c06-111">음성 입력은 모든 _유니버설 Windows 앱_ 에서 음성을 지 원하는 [동일한 엔진](/windows/uwp/design/input/speech-recognition) 에 의해 구동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-111">Voice input is powered by the [same engine](/windows/uwp/design/input/speech-recognition) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="16c06-112">HoloLens에서 음성 인식은 항상 장치 설정에서 구성 된 Windows 표시 언어로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="16c06-113">음성 및 응시</span><span class="sxs-lookup"><span data-stu-id="16c06-113">Voice and gaze</span></span>

<span data-ttu-id="16c06-114">음성 명령을 사용 하는 경우 head 또는 eye 응시는 커서를 사용 하 여 사용자가 원하는 응용 프로그램에 명령을 사용 하는지 여부에 관계 없이 일반적인 대상 지정 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="16c06-115">모든 응시 커서를 표시 하는 데 필요 하지 않을 수도 있습니다 _("참조" 라고 표시)_.</span><span class="sxs-lookup"><span data-stu-id="16c06-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="16c06-116">일부 음성 명령은 대상이 전혀 필요 하지 않습니다 (예: "시작으로 이동" 또는 "안녕하세요 Cortana").</span><span class="sxs-lookup"><span data-stu-id="16c06-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="16c06-117">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="16c06-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="16c06-118"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="16c06-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="16c06-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="16c06-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="16c06-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="16c06-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="16c06-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="16c06-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="16c06-122">음성 입력</span><span class="sxs-lookup"><span data-stu-id="16c06-122">Voice input</span></span></td>
        <td><span data-ttu-id="16c06-123">✔️</span><span class="sxs-lookup"><span data-stu-id="16c06-123">✔️</span></span></td>
        <td><span data-ttu-id="16c06-124">✔️</span><span class="sxs-lookup"><span data-stu-id="16c06-124">✔️</span></span></td>
        <td><span data-ttu-id="16c06-125">✔️ (마이크 포함)</span><span class="sxs-lookup"><span data-stu-id="16c06-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="16c06-126">"Select" 명령</span><span class="sxs-lookup"><span data-stu-id="16c06-126">The "select" command</span></span>

<span data-ttu-id="16c06-127">**HoloLens(1세대)**</span><span class="sxs-lookup"><span data-stu-id="16c06-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="16c06-128">앱에 음성 지원을 특별히 추가 하지 않은 경우에도 사용자는 시스템 음성 명령 "select"를 통해 holograms을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="16c06-129">이는 HoloLens의 [공기 탭](gaze-and-commit.md#composite-gestures) , [hololens clicker](/hololens/hololens1-clicker)의 선택 단추 누르기 또는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 트리거 누르기와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="16c06-130">소리가 들리고 "선택"이 확인으로 표시 된 도구 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="16c06-131">"Select"는 저전원 키워드 검색 알고리즘에서 사용 하도록 설정 됩니다. 즉, 배터리 수명에 영향을 주지 않고 언제 든 지 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="16c06-132">사용자 측의 손을 통해 "선택" 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="16c06-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="16c06-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="16c06-134">HoloLens 2에서 "select" 음성 명령을 사용 하려면 먼저 응시 커서를 포인터로 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="16c06-135">이를 가져오는 명령은 쉽게 기억할 수 있습니다. 예를 들어 "선택" 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="16c06-136">이 모드를 종료 하려면 마우스를 사용 하 여 손가락을 다시 사용 하 여 손가락으로 단추에 근접 하거나 시스템 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="16c06-137">*이미지: 선택 영역에 음성 명령을 사용 하려면 "선택"*</span><span class="sxs-lookup"><span data-stu-id="16c06-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![사용자는 선택에 대해 음성 명령을 사용 하기 위해 "선택" 이라고 말할 수 있습니다.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="16c06-139">안녕하세요. Cortana</span><span class="sxs-lookup"><span data-stu-id="16c06-139">Hey Cortana</span></span>

<span data-ttu-id="16c06-140">언제 든 지 Cortana를 표시 하는 "안녕하세요 Cortana" 라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="16c06-141">사용자의 질문을 계속 하거나 사용자에 게 지침을 제공 하기 위해 사용자가 표시 될 때까지 기다릴 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="16c06-142">예를 들어, "안녕하세요?" 라고 말하여</span><span class="sxs-lookup"><span data-stu-id="16c06-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="16c06-143">단일 문장으로</span><span class="sxs-lookup"><span data-stu-id="16c06-143">as a single sentence.</span></span> <span data-ttu-id="16c06-144">Cortana 및 사용자가 수행할 수 있는 작업에 대 한 자세한 내용은 다음을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="16c06-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="16c06-145">"안녕하세요?" 라고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="16c06-146">그리고 작업 및 제안 된 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="16c06-147">Cortana 앱에 이미 있는 경우 **?** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="16c06-148">동일한 메뉴를 끌어올 수 있는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="16c06-149">**HoloLens 관련 명령**</span><span class="sxs-lookup"><span data-stu-id="16c06-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="16c06-150">"무엇을 할 수 있나요?"</span><span class="sxs-lookup"><span data-stu-id="16c06-150">"What can I say?"</span></span>
* <span data-ttu-id="16c06-151">[시작 메뉴로](../discover/navigating-the-windows-mixed-reality-home.md#start-menu) 이동 하려면 [블 룸](system-gesture.md#bloom) 대신 "시작으로 이동"을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="16c06-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="16c06-152">"Launch <app> "</span><span class="sxs-lookup"><span data-stu-id="16c06-152">"Launch <app>"</span></span>
* <span data-ttu-id="16c06-153">" <app> 여기로 이동"</span><span class="sxs-lookup"><span data-stu-id="16c06-153">"Move <app> here"</span></span>
* <span data-ttu-id="16c06-154">"사진 찍기"</span><span class="sxs-lookup"><span data-stu-id="16c06-154">"Take a picture"</span></span>
* <span data-ttu-id="16c06-155">"기록 시작"</span><span class="sxs-lookup"><span data-stu-id="16c06-155">"Start recording"</span></span>
* <span data-ttu-id="16c06-156">"기록 중지"</span><span class="sxs-lookup"><span data-stu-id="16c06-156">"Stop recording"</span></span>
* <span data-ttu-id="16c06-157">"손 모양 표시"</span><span class="sxs-lookup"><span data-stu-id="16c06-157">"Show hand ray"</span></span>
* <span data-ttu-id="16c06-158">"손 모양 숨기기"</span><span class="sxs-lookup"><span data-stu-id="16c06-158">"Hide hand ray"</span></span>
* <span data-ttu-id="16c06-159">"밝기 늘리기"</span><span class="sxs-lookup"><span data-stu-id="16c06-159">"Increase the brightness"</span></span>
* <span data-ttu-id="16c06-160">"밝기 낮추기"</span><span class="sxs-lookup"><span data-stu-id="16c06-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="16c06-161">"볼륨 증가"</span><span class="sxs-lookup"><span data-stu-id="16c06-161">"Increase the volume"</span></span>
* <span data-ttu-id="16c06-162">"볼륨 낮추기"</span><span class="sxs-lookup"><span data-stu-id="16c06-162">"Decrease the volume"</span></span>
* <span data-ttu-id="16c06-163">"음소거" 또는 "음소거 해제"</span><span class="sxs-lookup"><span data-stu-id="16c06-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="16c06-164">"장치 종료"</span><span class="sxs-lookup"><span data-stu-id="16c06-164">"Shut down the device"</span></span>
* <span data-ttu-id="16c06-165">"장치 다시 시작"</span><span class="sxs-lookup"><span data-stu-id="16c06-165">"Restart the device"</span></span>
* <span data-ttu-id="16c06-166">"절전 모드로 전환"</span><span class="sxs-lookup"><span data-stu-id="16c06-166">"Go to sleep"</span></span>
* <span data-ttu-id="16c06-167">"시간 이란?"</span><span class="sxs-lookup"><span data-stu-id="16c06-167">"What time is it?"</span></span>
* <span data-ttu-id="16c06-168">"얼마나 많은 배터리가 남아 있나요?"</span><span class="sxs-lookup"><span data-stu-id="16c06-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="16c06-169">"이 항목을 참조 하세요."</span><span class="sxs-lookup"><span data-stu-id="16c06-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="16c06-170">HoloLens에는 음성 입력에 대 한 "이를 확인 하는 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="16c06-171">예를 들어 HoloLens (첫 번째 gen)에서 앱 창을 볼 때 사용자는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="16c06-172">*이미지: 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 앱의 위치를 조정할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="16c06-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="16c06-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="16c06-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="16c06-174">![앱 창이 나 홀로그램을 볼 때 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="16c06-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="16c06-175">앱이이 규칙을 준수 하는 경우 사용자는 시스템을 제어 하는 내용을 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="16c06-176">Gazing (첫 번째 gen)의 단추를 사용 하는 동안 단추가 음성으로 사용 되는 경우 초 후에 표시 되는 "음성 유지" 도구 설명이 표시 되 고이를 통해 "press"로 말하는 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="16c06-177">HoloLens 2에서 음성 도구 설명을 표시 하려면 "선택" 또는 "설명 가능한 내용" (이미지 참조)을 설명 하 여 음성 커서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="16c06-178">*이미지: 단추 아래에 "표시 됩니다." 라고 표시 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="16c06-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![단추 아래에 표시 되는 것을 확인 하세요.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="16c06-180">빠른 홀로그램 조작을 위한 음성 명령</span><span class="sxs-lookup"><span data-stu-id="16c06-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="16c06-181">한 번의 조작 작업을 빠르게 수행 하기 위해 홀로그램에서 gazing 하는 동안 많은 음성 명령을 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="16c06-182">이러한 음성 명령은 전 세계에 배치한 앱 창과 3D 개체에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="16c06-183">**홀로그램 조작 명령**</span><span class="sxs-lookup"><span data-stu-id="16c06-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="16c06-184">얼굴 얼굴</span><span class="sxs-lookup"><span data-stu-id="16c06-184">Face me</span></span>
* <span data-ttu-id="16c06-185">크게 | 보강</span><span class="sxs-lookup"><span data-stu-id="16c06-185">Bigger | Enhance</span></span>
* <span data-ttu-id="16c06-186">짧은</span><span class="sxs-lookup"><span data-stu-id="16c06-186">Smaller</span></span>

<span data-ttu-id="16c06-187">HoloLens 2에서는 참조 하는 내용에 대 한 상황에 맞는 정보를 암시적으로 제공 하는 눈에 잘 맞는 상호 작용을 함께 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="16c06-188">예를 들어 홀로그램을 확인 하 고 " _이_ 위치"를 확인 한 다음, 배치 하려는 위치를 확인 하 고 " _여기_ 에" 라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="16c06-189">또는 복잡 한 컴퓨터에서 holographic 파트를 살펴볼 수 있습니다. " _이_ 에 대 한 자세한 정보를 제공 합니다." 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="16c06-190">음성 명령 검색</span><span class="sxs-lookup"><span data-stu-id="16c06-190">Discovering voice commands</span></span>

<span data-ttu-id="16c06-191">위의 빠른 조작을 위한 명령과 같은 일부 명령은 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="16c06-192">사용할 수 있는 명령에 대 한 자세한 내용은 개체를 응시 하 고 "무엇을 할 수 있나요?" 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="16c06-193">가능한 명령 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-193">A list of possible commands pops up.</span></span> <span data-ttu-id="16c06-194">헤드 응시 커서를 사용 하 여 앞의 각 단추에 대 한 음성 도구 설명을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="16c06-195">전체 목록을 원하는 경우 언제 든 지 "모든 명령 표시" 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="16c06-196">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="16c06-196">Dictation</span></span>

<span data-ttu-id="16c06-197">음성 받아쓰기는 [공기 탭](gaze-and-commit.md#composite-gestures)을 사용 하 여 입력 하는 대신 앱에 텍스트를 입력 하는 것이 더 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="16c06-198">이렇게 하면 사용자에 대해 더 짧은 노력으로 입력 속도를 크게 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="16c06-199">![음성 받아쓰기는 마이크 단추를 선택 하 여 시작 합니다.](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="16c06-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="16c06-200">*음성 받아쓰기는 키보드에서 마이크 단추를 선택 하 여 시작 합니다.*</span><span class="sxs-lookup"><span data-stu-id="16c06-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="16c06-201">Holographic 키보드가 활성화 될 때마다 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="16c06-202">텍스트 입력 상자의 측면에서 마이크를 선택 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="16c06-203">앱에 음성 명령 추가</span><span class="sxs-lookup"><span data-stu-id="16c06-203">Adding voice commands to your app</span></span>

<span data-ttu-id="16c06-204">빌드하는 모든 환경에 음성 명령을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="16c06-205">음성은 시스템과 앱을 제어 하는 강력한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="16c06-206">사용자는 다양 한 종류의 언어와 악센트를 사용 하기 때문에 음성 키워드를 적절히 선택 하면 사용자의 명령이 명확 하 게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="16c06-207">모범 사례</span><span class="sxs-lookup"><span data-stu-id="16c06-207">Best practices</span></span>

<span data-ttu-id="16c06-208">다음은 매끄러운 음성 인식에 도움이 될 수 있는 몇 가지 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="16c06-209">**간결한 명령 사용** - 가능한 경우 두 개 이상의 음절로 이루어진 키워드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="16c06-210">1음절 단어는 악센트가 다른 사람이 말할 경우 다른 모음 소리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="16c06-211">예: "비디오 재생"은 "현재 선택한 비디오 재생" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="16c06-212">**간단한 어휘 사용** -예: "show note"는 "show 카드" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="16c06-213">**명령이 소거식이 아닌지** 확인 합니다. 음성 명령 작업이 비 소거식 인지 확인 하 고, 사용자 가까이를 말하는 다른 사람이 실수로 명령을 트리거하는 경우 쉽게 실행 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="16c06-214">**비슷한 음의 명령을 방지** 합니다. 여러 음성 명령을 비슷한 방식으로 등록 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="16c06-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="16c06-215">예: "자세히 표시" 및 "저장소 표시"는 비슷한 소리가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="16c06-216">**사용 하지 않을 때 앱 등록 취소** -앱이 특정 음성 명령이 유효한 상태가 아닌 경우에는 다른 명령이 혼동 하지 않도록 앱의 등록을 취소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="16c06-217">**다른 악센트로 테스트** - 다른 악센트의 사용자와 앱을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="16c06-218">**음성 명령 일관성 유지** - "Go back"이라고 말할 경우 이전 페이지로 이동되면 애플리케이션에서 이 동작을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="16c06-219">**시스템 명령을 사용 하지 않습니다** . 다음 음성 명령은 시스템용으로 예약 되어 있으므로 응용 프로그램에서 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="16c06-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="16c06-220">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="16c06-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="16c06-221">"Select"</span><span class="sxs-lookup"><span data-stu-id="16c06-221">"Select"</span></span>
   * <span data-ttu-id="16c06-222">"시작으로 이동"</span><span class="sxs-lookup"><span data-stu-id="16c06-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="16c06-223">음성 입력의 장점</span><span class="sxs-lookup"><span data-stu-id="16c06-223">Advantages of voice input</span></span>

<span data-ttu-id="16c06-224">음성 입력은 의도를 전달하는 자연스러운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="16c06-225">음성은 인터페이스 탐색에 특히 유용 합니다. 사용자가 인터페이스의 여러 단계를 잘라내는 데 도움이 될 수 **있기 때문입니다** .</span><span class="sxs-lookup"><span data-stu-id="16c06-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="16c06-226">사용자는 웹 페이지를 보면서 앱에서 뒤로 단추를 누르면 "뒤로 이동" 이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="16c06-227">이러한 시간 절약은 사용자의 경험에 대 한 강력한 **감정적 효과** 를 제공 하 고 작은 양의 슈퍼 능력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="16c06-228">팔에 무언가를 잔뜩 들고 있거나 **멀티태스킹** 중일 때도 음성을 사용하는 것이 편리한 입력 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="16c06-229">키보드에 입력 하는 것이 어려운 장치에서 **음성 받아쓰기** 는 텍스트를 입력 하는 효율적인 대체 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="16c06-230">마지막으로, 응시 및 제스처에 대 한 **정확도 범위가** 제한 되는 경우 음성은 사용자의 의도를 명확 하 게 구분 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="16c06-231">**사용자에게 도움이 될 수 있는 음성 사용 방법**</span><span class="sxs-lookup"><span data-stu-id="16c06-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="16c06-232">시간 단축 - 보다 효율적으로 최종 목표에 도달할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="16c06-233">최소의 노력 - 보다 유연하고 편리하게 작업할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="16c06-234">인지 부담 감소 - 직관적이며 배우고 기억하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="16c06-235">사회 공학적는 사용할 수 있습니다 .이는 표준의 동작에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="16c06-236">일상적임 - 음성이 습관적인 동작이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="16c06-237">음성 입력에 대 한 문제</span><span class="sxs-lookup"><span data-stu-id="16c06-237">Challenges for voice input</span></span>

<span data-ttu-id="16c06-238">음성 입력은 다양 한 응용 프로그램에 유용 하지만 몇 가지 문제도 직면 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="16c06-239">음성 입력의 장점과 문제를 모두 이해 하면 앱 개발자가 음성 입력을 사용 하는 방법 및 시기를 보다 효율적으로 선택 하 고 사용자에 게 훌륭한 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="16c06-240">**연속 입력 컨트롤에 대 한 음성 입력** 세밀 한 제어가 그 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="16c06-241">예를 들어 사용자가 음악 앱에서 볼륨을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="16c06-242">"큰" 것은 아니지만 시스템에서 볼륨을 만드는 것이 얼마나 큰 지는 확실 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="16c06-243">사용자는 "약간 더 크게 만들기" 라고 말할 수 있지만 "약간의"는 수량화 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="16c06-244">음성으로 holograms을 이동 하거나 크기를 조정 하는 것은 비슷하게 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="16c06-245">**음성 입력 검색의 안정성** 음성 입력 시스템은 더 효과적이 고 더 나은 반면 음성 명령을 잘못 듣고 해석 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="16c06-246">핵심은 응용 프로그램에서 챌린지를 해결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="16c06-247">시스템이 수신 대기 하는 경우 사용자에 게 피드백을 제공 하 고 시스템에서 사용자의 음성을 이해 하는 잠재적인 문제를 명확 하 게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="16c06-248">**공유 공간의 음성 입력** 음성은 다른 사용자와 공유 하는 공간에서 사회 공학적 허용 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="16c06-249">다음은 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-249">Here are a few examples:</span></span>
* <span data-ttu-id="16c06-250">사용자가 다른 사용자의 방해를 원하지 않을 수 있습니다 (예: 자동 라이브러리나 공유 사무실).</span><span class="sxs-lookup"><span data-stu-id="16c06-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="16c06-251">사용자가 공개를 통해 자신에 게 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="16c06-252">사용자가 암호를 포함 하 여 개인 또는 기밀 메시지를 수신 하는 불편을 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="16c06-253">**고유 하거나 알 수 없는 단어의 음성 입력** 음성 입력의 어려움은 사용자가 시스템에서 알 수 없는 단어 (예: 애칭, 특정은 어 단어 또는 약어)를 받아쓰게 하는 경우에도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="16c06-254">**음성 명령 학습** 최종 목표는 시스템과 자연스럽 게 사용 되는 것이 아니라 앱이 미리 정의 된 특정 음성 명령을 계속 사용 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="16c06-255">중요 한 음성 명령 집합과 관련 된 과제는 사용자를 오버 로드 하지 않고 사용자를 유지 하는 데 도움이 되는 방법을 설명 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="16c06-256">음성 피드백 상태</span><span class="sxs-lookup"><span data-stu-id="16c06-256">Voice feedback states</span></span>

<span data-ttu-id="16c06-257">음성이 제대로 적용되면 사용자는 **말할 수 있는 사항** 을 이해하고 시스템이 **올바르게 알아 들었다는 명확한 피드백을 받게 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="16c06-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="16c06-258">이러한 두 신호를 통해 사용자는 음성을 기본 입력으로 사용할 때 안심할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="16c06-259">다음은 음성 입력이 인식될 때 커서에 나타나는 결과와 사용자에게 이러한 사실을 전달하는 방법을 보여 주는 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="16c06-260">![1. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="16c06-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="16c06-261">**1. 일반 커서 상태**</span><span class="sxs-lookup"><span data-stu-id="16c06-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="16c06-262">![2. 음성 피드백을 전달 하 고 사라집니다.](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="16c06-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="16c06-263">**2. 음성 피드백을 전달 하 고 사라집니다.**</span><span class="sxs-lookup"><span data-stu-id="16c06-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="16c06-264">![3.</span><span class="sxs-lookup"><span data-stu-id="16c06-264">![\*3.</span></span> <span data-ttu-id="16c06-265">일반 커서 상태](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="16c06-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="16c06-266">**3. 일반 커서 상태로 돌아갑니다.**</span><span class="sxs-lookup"><span data-stu-id="16c06-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="16c06-267">혼합 현실에서 "음성"에 대해 알아야 할 주요 사항</span><span class="sxs-lookup"><span data-stu-id="16c06-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="16c06-268">단추를 대상으로 하는 동안 **"선택"** 이라고 말할 수 있습니다 .이 단추를 사용 하 여 단추를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="16c06-269">일부 앱에서는 작업을 수행하기 위해 **label name of an app bar button** 이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="16c06-270">예를 들어 앱을 확인 하는 동안 사용자는 "제거" 명령을 사용 하 여 전 세계에서 앱을 제거할 수 있습니다. 이렇게 하면 사용자가 손을 선택 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="16c06-271">Cortana 수신 대기를 시작할 수 있습니다 **.**</span><span class="sxs-lookup"><span data-stu-id="16c06-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="16c06-272">질문을 하거나("Hey Cortana, how tall is the Eiffel tower"), 앱을 열도록 말하거나("Hey Cortana, open Netflix"), 시작 메뉴를 불러오도록 말할 수 있습니다("Hey Cortana, take me home").</span><span class="sxs-lookup"><span data-stu-id="16c06-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="16c06-273">음성에 대한 사용자의 일반적인 질문 및 어려움</span><span class="sxs-lookup"><span data-stu-id="16c06-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="16c06-274">어떤 말을 할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="16c06-274">What can I say?</span></span>
* <span data-ttu-id="16c06-275">시스템이 내 말을 제대로 알아듣는지 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="16c06-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="16c06-276">시스템이 내 음성 명령을 계속 잘못 알아듣습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="16c06-277">음성 명령을 받아도 반응하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="16c06-278">음성 명령을 제공할 때 잘못된 방식으로 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="16c06-279">특정 앱이나 앱 명령을 대상으로 음성 명령을 내리려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="16c06-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="16c06-280">음성을 사용해서 항목을 HoloLens의 홀로그래픽 프레임 밖으로 보낼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="16c06-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="16c06-281">통신</span><span class="sxs-lookup"><span data-stu-id="16c06-281">Communication</span></span>

<span data-ttu-id="16c06-282">HoloLens에서 제공 하는 사용자 지정 된 오디오 입력 처리 옵션을 활용 하려는 응용 프로그램의 경우 앱에서 사용할 수 있는 다양 한 [오디오 스트림 범주](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) 를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) your app can consume.</span></span> <span data-ttu-id="16c06-283">Windows 10은 다양 한 스트림 범주를 지원 하 고, HoloLens는 이러한 세 가지를 사용 하 여 주변 환경 오디오 캡처 (즉, "캠코더") 시나리오에 사용할 수 있는 음성, 통신 등에 맞게 조정 된 마이크 오디오 품질을 최적화할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="16c06-284">AudioCategory_Communications stream 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정 되며 클라이언트에 사용자 음성의 16Khz 24 비트 mono 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="16c06-285">AudioCategory_Speech stream 범주는 HoloLens (Windows) 음성 엔진에 맞게 사용자 지정 되며 사용자 음성의 16Khz 24 비트 mono 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="16c06-286">이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="16c06-287">AudioCategory_Other stream 범주는 주변 환경 오디오 녹음에 맞게 사용자 지정 되며 클라이언트에 48-kHz 24 비트 스테레오 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="16c06-288">이러한 오디오 처리는 모두 하드웨어 가속입니다. 즉, HoloLens CPU에서 동일한 처리가 수행 된 경우 보다 기능이 훨씬 더 많은 전력을 소모 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="16c06-289">시스템 배터리 수명을 최대화 하 고 오프 로드 된 기본 제공 오디오 입력 처리 기능을 활용 하기 위해 CPU에서 기타 오디오 입력 처리를 실행 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="16c06-290">언어</span><span class="sxs-lookup"><span data-stu-id="16c06-290">Languages</span></span>

<span data-ttu-id="16c06-291">HoloLens 2는 [여러 언어를 지원](/hololens/hololens2-language-support)합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-291">HoloLens 2 [supports multiple languages](/hololens/hololens2-language-support).</span></span> <span data-ttu-id="16c06-292">음성 명령은 여러 키보드가 설치 되어 있거나 앱이 다른 언어로 음성 인식기를 만들려고 하는 경우에도 항상 시스템의 표시 언어로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="16c06-293">문제 해결</span><span class="sxs-lookup"><span data-stu-id="16c06-293">Troubleshooting</span></span>

<span data-ttu-id="16c06-294">"Select" 및 "안녕하세요 Cortana"를 사용 하는 데 문제가 있는 경우 더 조용한 공간으로 이동 하거나, 소음의 원본에서 떨어진 곳으로 이동 하거나, 더 크게 말해 보세요.</span><span class="sxs-lookup"><span data-stu-id="16c06-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="16c06-295">지금은 HoloLens의 모든 음성 인식이 특별히 미국 영어의 기본 스피커로 조정 되 고 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="16c06-296">Windows Mixed Reality Developer Edition 릴리스 2017에서는 초기 HMD 연결 후 PC 데스크톱에 로그 아웃 했다가 다시 로그인 한 후 오디오 끝점 관리 논리가 정상적으로 작동 합니다 (계속).</span><span class="sxs-lookup"><span data-stu-id="16c06-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="16c06-297">WMR OOBE를 통과 한 후 첫 번째 로그 아웃 이벤트 이전에는 사용자가 HMD를 처음으로 연결 하기 전에 시스템이 설정 된 방법에 따라 오디오 없음에서 오디오 전환 없이 다양 한 오디오 기능 문제를 겪을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="16c06-298">Unity 용 MRTK (Mixed Reality Toolkit)의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="16c06-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="16c06-299">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 하면 개체에 음성 명령을 쉽게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="16c06-300">MRTK의 **음성 입력 프로필** 을 사용 하 여 키워드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="16c06-301">**SpeechInputHandler** 스크립트를 할당 하 여 음성 입력 프로필에 정의 된 키워드에 대 한 모든 개체 응답을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="16c06-302">또한 SpeechInputHandler는 사용자의 신뢰도를 높이기 위해 음성 확인 레이블을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16c06-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="16c06-303">MRTK-음성 명령</span><span class="sxs-lookup"><span data-stu-id="16c06-303">MRTK - Voice command</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a><span data-ttu-id="16c06-304">참조</span><span class="sxs-lookup"><span data-stu-id="16c06-304">See also</span></span>

* [<span data-ttu-id="16c06-305">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="16c06-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="16c06-306">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="16c06-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="16c06-307">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="16c06-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="16c06-308">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="16c06-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)