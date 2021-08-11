---
title: Unity의 키보드 입력
description: Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 TouchScreenKeyboard 클래스를 제공 합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 키보드, 입력, unity, touchscreenkeyboard, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203855"
---
# <a name="keyboard-input-in-unity"></a>Unity의 키보드 입력

**네임 스페이스:** *unityengine*<br>
 **유형**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens는 Bluetooth 키보드를 비롯 한 다양 한 형식의 입력을 지원 하지만 대부분의 응용 프로그램은 모든 사용자가 실제 키보드를 사용할 수 있다고 가정할 수 없습니다. 응용 프로그램에 텍스트 입력이 필요한 경우 화상 키보드의 일부 형식을 제공 해야 합니다.

Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 클래스를 제공 합니다.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity에서 HoloLens 시스템 키보드 동작

HoloLens에서 *TouchScreenKeyboard* 는 시스템의 화상 키보드를 활용 하 여 MR 응용 프로그램의 대규모 보기 위에 직접 오버레이 합니다. 이 환경은 HoloLens의 기본 제공 앱에서 키보드를 사용 하는 것과 비슷합니다. 시스템 키보드는 대상 플랫폼의 기능에 따라 동작 합니다. 예를 들어 HoloLens 2 키보드는 직접 상호 작용을 지원 하지만 HoloLens의 키보드 (첫 번째 gen)는 GGV (응시, 제스처 및 Voice)를 지원 합니다. 또한 편집기에서 HoloLens로 Unity 원격 기능을 수행할 때 시스템 키보드는 표시 되지 않습니다.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity 앱에서 시스템 키보드 사용

### <a name="declare-the-keyboard"></a>키보드를 선언 합니다.

클래스에서 *TouchScreenKeyboard* 를 저장 하는 변수와 키보드에서 반환 하는 문자열을 보유할 변수를 선언 합니다.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>키보드 호출

키보드 입력을 요청 하는 이벤트가 발생 하는 경우 다음을 사용 하 여 키보드를 표시 합니다.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

함수에 전달 된 추가 매개 변수 `TouchScreenKeyboard.Open` 를 사용 하 여 키보드의 동작을 제어할 수 있습니다. 예를 들어 자리 표시자 텍스트를 설정 하거나 자동 고침을 지원할 수 있습니다. 매개 변수의 전체 목록은 [Unity 설명서](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)를 참조 하세요.

### <a name="retrieve-typed-contents"></a>형식화 된 콘텐츠 검색

콘텐츠는를 호출 하 여 간단히 검색할 수 있습니다 `keyboard.text` . 프레임 당 또는 키보드를 닫은 경우에만 콘텐츠를 검색 하는 것이 좋습니다.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>대체 키보드 옵션

*TouchScreenKeyboard* 클래스를 직접 사용 하는 것 외에도 Unity의 *UI 입력 필드* 또는 *TextMeshPro 입력 필드* 를 사용 하 여 사용자 입력을 가져올 수 있습니다. 또한 [Mrtk](/windows/mixed-reality/mrtk-unity) 의 [HandInteractionExamples 장면의](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) *TouchScreenKeyboard* 을 기반으로 하는 구현이 있습니다 (왼쪽에 키보드 상호 작용 샘플이 있습니다).

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다. 여기에서 [토픽](unity-development-overview.md#3-advanced-features) 을 계속 하거나 장치 또는 에뮬레이터에서 앱을 배포 하기 위해 바로 이동할 수 있습니다.

> [!div class="nextstepaction"]
> [HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 배포](../platform-capabilities-and-apis/using-visual-studio.md)
