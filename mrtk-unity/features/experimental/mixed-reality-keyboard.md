---
title: Mixed Reality 키보드
description: 혼합 현실 키보드를 사용 하는 방법에 대 한 설명
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143397"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="bded1-104">혼합 현실 및 HoloLens 키보드 도우미 클래스</span><span class="sxs-lookup"><span data-stu-id="bded1-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="bded1-105">MRTK는 [시스템 키보드](../ux-building-blocks/system-keyboard.md)에서 텍스트를 시작 하 고 읽는 데 도움이 되는 여러 실험적 도우미 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="bded1-106">시스템 키보드는 대상 플랫폼의 기능에 따라 동작 합니다. 예를 들어, HoloLens 2의 키보드는 직접 상호 작용을 지원 하는 반면, HoloLens의 키보드 (첫 번째 gen)는 GGV<sup>[1](/windows/mixed-reality/gaze)</sup>을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="bded1-107">또한 편집기에서 HoloLens로 [Unity 원격](../tools/holographic-remoting.md) 기능을 수행 하는 경우 시스템 키보드는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="bded1-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="bded1-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="bded1-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 는 키보드에서 입력 한 텍스트와 상호 작용 뿐만 아니라 시스템 키보드를 시작 하 고 닫는 메서드를 제공 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="bded1-110">사용 방법</span><span class="sxs-lookup"><span data-stu-id="bded1-110">How to Use</span></span>

1. <span data-ttu-id="bded1-111">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard)모든 개체에 구성 요소를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="bded1-112">을 호출 `Show()` `Hide()` 하 여 키보드를 표시 하거나 숨기고, 및 이벤트를 처리 하 여 키보드를 표시 하 고, `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` 숨긴 다음, enter 키를 누를 때 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="bded1-113">입력 필드 TMP_KeyboardInputField 및 UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="bded1-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="bded1-114">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)및 클래스는 텍스트 입력 필드에 추가 하 여 사용자가 텍스트를 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 입력할 때 자동으로 시스템 키보드를 호출 하 고 텍스트 입력 필드 내용을 업데이트할 수 있는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="bded1-115">사용 방법</span><span class="sxs-lookup"><span data-stu-id="bded1-115">How to use</span></span>

1. <span data-ttu-id="bded1-116">UnityUI 또는 TextMeshPro에 대 한 입력 필드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="bded1-117">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 입력 필드 게임 개체에 해당 또는 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="bded1-118">UnityUI 입력 필드 및 TextMeshPro (TMPro) 입력 필드에 대 한 Prefabs는 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="bded1-119">TMP_KeyboardInputField 및 UI_KeyboardInputField를 사용 하는 방법의 예는 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bded1-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>