---
title: Unity의 키보드 입력
description: Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 TouchScreenKeyboard 클래스를 제공 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 키보드, 입력, unity, touchscreenkeyboard, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: aa9bb3059a8d0cc5b829bf14d92928511259b7f9
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677422"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="faac2-104">Unity의 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="faac2-104">Keyboard input in Unity</span></span>

<span data-ttu-id="faac2-105">**네임 스페이스:** *unityengine*</span><span class="sxs-lookup"><span data-stu-id="faac2-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="faac2-106">**유형**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="faac2-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="faac2-107">HoloLens는 Bluetooth 키보드를 비롯 한 다양 한 형태의 입력을 지원 하지만 대부분의 응용 프로그램에서는 모든 사용자가 실제 키보드를 사용할 수 있다고 간주할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="faac2-108">응용 프로그램에 텍스트 입력이 필요한 경우 화면 키보드의 일부 형식을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="faac2-109">Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="faac2-110">Unity의 HoloLens 시스템 키보드 동작</span><span class="sxs-lookup"><span data-stu-id="faac2-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="faac2-111">HoloLens에서 *TouchScreenKeyboard* 는 시스템의 화면 키보드를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="faac2-112">시스템의 화면 키보드는 대규모 보기 위에 오버레이 할 수 없기 때문에 Unity에서 키보드를 표시 하는 보조 2D XAML 뷰를 만든 다음 입력이 제출 되 면 대규모 보기로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="faac2-113">사용자 흐름은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="faac2-114">사용자가 응용 프로그램 코드에서 *TouchScreenKeyboard* 를 호출 하는 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="faac2-115">앱은 *TouchScreenKeyboard* 를 호출 하기 전에 앱 상태를 일시 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="faac2-116">앱이 대규모 보기로 다시 전환 하기 전에 종료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="faac2-117">Unity는 전 세계에 자동 배치 되는 2D XAML 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="faac2-118">사용자가 시스템 키보드를 사용 하 여 텍스트를 입력 하 고 제출 하거나 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="faac2-119">Unity에서 다시 대규모 보기로 전환</span><span class="sxs-lookup"><span data-stu-id="faac2-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="faac2-120">앱은 *TouchScreenKeyboard* 완료 될 때 앱 상태를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="faac2-121">제출 된 텍스트는 *TouchScreenKeyboard* 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="faac2-122">사용 가능한 키보드 보기</span><span class="sxs-lookup"><span data-stu-id="faac2-122">Available keyboard views</span></span>

<span data-ttu-id="faac2-123">사용할 수 있는 6 가지 키보드 보기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="faac2-124">한 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-124">Single-line textbox</span></span>
* <span data-ttu-id="faac2-125">제목이 있는 한 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-125">Single-line textbox with title</span></span>
* <span data-ttu-id="faac2-126">여러 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-126">Multi-line textbox</span></span>
* <span data-ttu-id="faac2-127">제목이 있는 여러 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="faac2-128">한 줄 암호 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-128">Single-line password box</span></span>
* <span data-ttu-id="faac2-129">제목이 있는 한 줄 암호 상자</span><span class="sxs-lookup"><span data-stu-id="faac2-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="faac2-130">Unity에서 시스템 키보드를 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="faac2-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="faac2-131">HoloLens 시스템 키보드는 "UWP 빌드 형식"을 "XAML"로 설정 하 여 내보낸 Unity 응용 프로그램 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="faac2-132">"D3D"를 통해 "XAML"을 "UWP 빌드 형식"으로 선택 하는 경우에는 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="faac2-133">이러한 절충에 익숙하지 않은 경우 시스템 키보드에 대 한 [대체 입력 솔루션](#alternative-keyboard-options) 을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="faac2-134">**파일** 메뉴를 열고 **빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="faac2-135">**플랫폼이** **Windows 스토어** 로 설정 되 고 **SDK** 가 **유니버설 10** 으로 설정 되었는지 확인 하 고 **UWP 빌드 형식을** **XAML** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="faac2-136">**빌드 설정** 대화 상자에서 **플레이어 설정 ...** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="faac2-137">**Windows 스토어에 대 한 설정 탭을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="faac2-138">**기타 설정** 그룹 확장</span><span class="sxs-lookup"><span data-stu-id="faac2-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="faac2-139">**렌더링** 섹션에서 **가상 현실 지원** 확인란을 선택 하 여 새 **가상 현실 장치** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="faac2-140">가상 현실 Sdk 목록에 **Windows Holographic** 가 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="faac2-141">빌드를 HoloLens 장치에서 지원 되는 가상 현실로 표시 하지 않으면 프로젝트는 2D XAML 앱으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="faac2-142">Unity 앱에서 시스템 키보드 사용</span><span class="sxs-lookup"><span data-stu-id="faac2-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="faac2-143">키보드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-143">Declare the keyboard</span></span>

<span data-ttu-id="faac2-144">클래스에서 *TouchScreenKeyboard* 를 저장 하는 변수와 키보드에서 반환 하는 문자열을 보유할 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="faac2-145">키보드 호출</span><span class="sxs-lookup"><span data-stu-id="faac2-145">Invoke the keyboard</span></span>

<span data-ttu-id="faac2-146">키보드 입력을 요청 하는 이벤트가 발생 하는 경우 원하는 입력 형식에 따라 이러한 함수 중 하나를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="faac2-147">제목은 textPlaceholder 매개 변수에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="faac2-148">형식화 된 콘텐츠 검색</span><span class="sxs-lookup"><span data-stu-id="faac2-148">Retrieve typed contents</span></span>

<span data-ttu-id="faac2-149">업데이트 루프에서 키보드에서 새 입력을 받았는지 확인 하 고 다른 곳에서 사용할 수 있도록 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.status == TouchScreenKeyboard.Status.Done)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="faac2-150">대체 키보드 옵션</span><span class="sxs-lookup"><span data-stu-id="faac2-150">Alternative keyboard options</span></span>

<span data-ttu-id="faac2-151">대규모 보기에서 2D 뷰로 전환 하는 것은 사용자 로부터 텍스트 입력을 가져오는 이상적인 방법이 아님을 이해 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="faac2-152">Unity를 통한 시스템 키보드 활용에 대 한 현재 대안은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="faac2-153">입력에 음성 받아쓰기 사용 (<b>참고:</b> 사전에 없는 단어에는 오류가 발생 하기 쉬우며 암호 입력에 적합 하지 않음)</span><span class="sxs-lookup"><span data-stu-id="faac2-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="faac2-154">응용 프로그램 전용 보기에서 작동 하는 키보드 만들기</span><span class="sxs-lookup"><span data-stu-id="faac2-154">Create a keyboard that works in your applications exclusive view</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="faac2-155">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="faac2-155">Next Development Checkpoint</span></span>

<span data-ttu-id="faac2-156">앞서 소개한 Unity 개발 검사점 경험을 팔로 하는 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 과정을 진행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-156">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="faac2-157">여기에서 [토픽](unity-development-overview.md#3-platform-capabilities-and-apis) 을 계속 진행 하거나 장치 또는 에뮬레이터에서 앱을 배포 하기 위해 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faac2-157">From here, you can proceed to any [topic](unity-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="faac2-158">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="faac2-158">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
