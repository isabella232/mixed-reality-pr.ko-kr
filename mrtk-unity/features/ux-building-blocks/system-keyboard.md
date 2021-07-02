---
title: 시스템 키보드
description: MRTK의 시스템 키 보드 개요
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 시스템 키보드,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176494"
---
# <a name="system-keyboard"></a><span data-ttu-id="6e030-104">시스템 키보드</span><span class="sxs-lookup"><span data-stu-id="6e030-104">System keyboard</span></span>

![시스템 키보드](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="6e030-106">Unity 애플리케이션은 언제든지 시스템 키보드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e030-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="6e030-107">시스템 키보드는 대상 플랫폼의 기능에 따라 동작합니다. 예를 들어 HoloLens 2 키보드는 직접 손 상호 작용을 지원하는 반면, HoloLens(1세대)의 키보드는 GGV(응시, 제스처 및 음성)<sup>[1을](/windows/mixed-reality/gaze)</sup>지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e030-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="6e030-108">또한 편집기에서 HoloLens [Unity Remoting을](../tools/holographic-remoting.md) 수행할 때 시스템 키보드가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e030-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="6e030-109">시스템 키보드를 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="6e030-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="6e030-110">입력을 읽는 방법</span><span class="sxs-lookup"><span data-stu-id="6e030-110">How to read the input</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a><span data-ttu-id="6e030-111">시스템 키보드 예제</span><span class="sxs-lookup"><span data-stu-id="6e030-111">System keyboard example</span></span>

<span data-ttu-id="6e030-112">`MixedRealityKeyboard.cs`(Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)에서 시스템 키보드를 가져오는 방법의 간단한 예제를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e030-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="6e030-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e030-113">See Also</span></span>

- [<span data-ttu-id="6e030-114">키보드 도우미 클래스 Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6e030-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
