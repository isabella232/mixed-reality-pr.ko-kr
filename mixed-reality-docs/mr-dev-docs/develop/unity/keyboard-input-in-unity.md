---
title: Unity의 키보드 입력
description: Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 TouchScreenKeyboard 클래스를 제공 합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 키보드, 입력, unity, touchscreenkeyboard, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098275"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="bf471-104">Unity의 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="bf471-104">Keyboard input in Unity</span></span>

<span data-ttu-id="bf471-105">**네임 스페이스:** *unityengine*</span><span class="sxs-lookup"><span data-stu-id="bf471-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="bf471-106">**유형**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="bf471-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="bf471-107">HoloLens는 Bluetooth 키보드를 비롯 한 다양 한 형태의 입력을 지원 하지만 대부분의 응용 프로그램은 모든 사용자가 실제 키보드를 사용할 수 있다고 간주할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="bf471-108">응용 프로그램에 텍스트 입력이 필요한 경우 화상 키보드의 일부 형식을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="bf471-109">Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="bf471-110">Unity의 HoloLens 시스템 키보드 동작</span><span class="sxs-lookup"><span data-stu-id="bf471-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="bf471-111">HoloLens에서 *TouchScreenKeyboard* 는 시스템의 화상 키보드를 활용 하 여 MR 응용 프로그램의 대규모 보기 위에 직접 오버레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="bf471-112">이 환경은 HoloLens의 기본 제공 앱에서 키보드를 사용 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="bf471-113">시스템 키보드는 대상 플랫폼의 기능에 따라 동작 합니다. 예를 들어, HoloLens 2의 키보드는 직접 상호 작용을 지원 하는 반면, HoloLens의 키보드 (첫 번째 gen)는 GGV (응시, 제스처 및 음성)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="bf471-114">또한 편집기에서 HoloLens로 Unity 원격 기능을 수행 하는 경우 시스템 키보드는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="bf471-115">Unity 앱에서 시스템 키보드 사용</span><span class="sxs-lookup"><span data-stu-id="bf471-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="bf471-116">키보드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-116">Declare the keyboard</span></span>

<span data-ttu-id="bf471-117">클래스에서 *TouchScreenKeyboard* 를 저장 하는 변수와 키보드에서 반환 하는 문자열을 보유할 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="bf471-118">키보드 호출</span><span class="sxs-lookup"><span data-stu-id="bf471-118">Invoke the keyboard</span></span>

<span data-ttu-id="bf471-119">키보드 입력을 요청 하는 이벤트가 발생 하는 경우 다음을 사용 하 여 키보드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="bf471-120">함수에 전달 된 추가 매개 변수 `TouchScreenKeyboard.Open` 를 사용 하 여 키보드의 동작을 제어할 수 있습니다. 예를 들어 자리 표시자 텍스트를 설정 하거나 자동 고침을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="bf471-121">매개 변수의 전체 목록은 [Unity 설명서](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf471-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="bf471-122">형식화 된 콘텐츠 검색</span><span class="sxs-lookup"><span data-stu-id="bf471-122">Retrieve typed contents</span></span>

<span data-ttu-id="bf471-123">콘텐츠는를 호출 하 여 간단히 검색할 수 있습니다 `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="bf471-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="bf471-124">프레임 당 또는 키보드를 닫은 경우에만 콘텐츠를 검색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="bf471-125">대체 키보드 옵션</span><span class="sxs-lookup"><span data-stu-id="bf471-125">Alternative keyboard options</span></span>

<span data-ttu-id="bf471-126">*TouchScreenKeyboard* 클래스를 직접 사용 하는 것 외에도 Unity의 *UI 입력 필드* 또는 *TextMeshPro 입력 필드* 를 사용 하 여 사용자 입력을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="bf471-127">또한 [Mrtk](/windows/mixed-reality/mrtk-unity) 의 [HandInteractionExamples 장면의](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) *TouchScreenKeyboard* 을 기반으로 하는 구현이 있습니다 (왼쪽에 키보드 상호 작용 샘플이 있습니다).</span><span class="sxs-lookup"><span data-stu-id="bf471-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="bf471-128">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="bf471-128">Next Development Checkpoint</span></span>

<span data-ttu-id="bf471-129">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="bf471-130">여기에서 [토픽](unity-development-overview.md#3-advanced-features) 을 계속 하거나 장치 또는 에뮬레이터에서 앱을 배포 하기 위해 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf471-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bf471-131">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="bf471-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
