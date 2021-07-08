---
title: Mixed Reality 키보드
description: 혼합 현실 키보드를 사용하는 방법에 대한 설명
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466233"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="c3755-104">키보드 도우미 클래스 Mixed Reality 및 HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3755-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="c3755-105">MRTK는 [시스템 키보드](../ux-building-blocks/system-keyboard.md)에서 텍스트를 시작하고 읽는 데 도움이 되는 몇 가지 실험적 도우미 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="c3755-106">시스템 키보드는 대상 플랫폼의 기능에 따라 동작합니다. 예를 들어 HoloLens 2 키보드는 직접 손 상호 작용을 지원하지만 HoloLens(1세대)의 키보드는 GGV<sup>[1을](/windows/mixed-reality/gaze)</sup>지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="c3755-107">또한 편집기에서 HoloLens [Unity Remoting을](../tools/holographic-remoting.md) 수행할 때 시스템 키보드가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="c3755-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="c3755-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="c3755-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 는 시스템 키보드를 시작하고 닫을 뿐만 아니라 키보드에서 입력한 텍스트와 상호 작용하는 메서드를 제공하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="c3755-110">사용 방법</span><span class="sxs-lookup"><span data-stu-id="c3755-110">How to Use</span></span>

1. <span data-ttu-id="c3755-111">모든 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 개체에 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="c3755-112">`ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` 를 호출하여 키보드를 표시 및 숨기고, `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` 키보드가 표시되고 숨겨질 때와 Enter 키를 누를 때 처리할 , 및 이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-112">Call `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="c3755-113">입력 필드 TMP_KeyboardInputField 및 UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="c3755-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="c3755-114">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)및 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 클래스는 클릭할 때 시스템 키보드를 자동으로 호출하고 사용자가 텍스트를 입력할 때 텍스트 입력 필드 내용을 업데이트하기 위해 텍스트 입력 필드에 추가할 수 있는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="c3755-115">사용 방법</span><span class="sxs-lookup"><span data-stu-id="c3755-115">How to use</span></span>

1. <span data-ttu-id="c3755-116">UnityUI 또는 TextMeshPro에 대한 입력 필드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="c3755-117">입력 필드 게임 개체에 해당 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 또는 구성 요소를 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="c3755-118">UnityUI 입력 필드와 TextMeshPro(TMPro) 입력 필드 모두에 대한 프리팹은 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="c3755-119">TMP_KeyboardInputField 및 UI_KeyboardInputField 사용하는 방법의 예는 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"입니다.</span><span class="sxs-lookup"><span data-stu-id="c3755-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>