---
title: DirectX의 키보드, 마우스 및 컨트롤러 입력
description: 키보드, 마우스 및 게임 컨트롤러를 사용하는 Windows Mixed Reality 앱을 만드는 방법을 설명합니다.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, 키보드, 마우스, 게임 컨트롤러, Xbox 컨트롤러, HoloLens, 데스크톱, 연습, 샘플 코드
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244168"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX의 키보드, 마우스 및 컨트롤러 입력

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 API와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OpenXR API](../native/openxr-getting-started.md)** 를 사용하는 것이 좋습니다.

키보드, 마우스 및 게임 컨트롤러는 모두 Windows Mixed Reality 디바이스에 유용한 입력 형태일 수 있습니다. Bluetooth 키보드와 마우스는 모두 앱 디버깅 또는 대체 입력 형식으로 사용하기 위해 HoloLens 지원됩니다. Windows Mixed Reality PC에 연결된 몰입형 헤드셋도 지원합니다. 여기서 마우스, 키보드 및 게임 컨트롤러는 지금까지 표준이었습니다.

HoloLens 키보드 입력을 사용하려면 Bluetooth 키보드를 디바이스에 페어링하거나 Windows 장치 포털 통해 가상 입력을 사용합니다. Windows Mixed Reality 몰입형 헤드셋을 사용하는 동안 키보드 입력을 사용하려면 디바이스에 배치하거나 Windows 키 + Y 키보드 조합을 사용하여 혼합 현실에 입력 포커스를 할당합니다. HoloLens 위한 앱은 이러한 디바이스가 연결되지 않은 기능을 제공해야 합니다.
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>이 문서의 코드 조각은 현재 C++ 홀로그램 프로젝트 템플릿 에서 사용되는 C++17 규격 C++/WinRT 대신 [C++/CX를](../native/creating-a-holographic-directx-project.md)사용하는 것을 보여줍니다.  개념은 C++/WinRT 프로젝트에 해당하지만 코드를 번역해야 합니다.

## <a name="subscribe-for-corewindow-input-events"></a>CoreWindow 입력 이벤트 구독

### <a name="keyboard-input"></a>키보드 입력

Windows Holographic 앱 템플릿에는 다른 UWP 앱과 마찬가지로 키보드 입력에 대한 이벤트 처리기가 포함되어 있습니다. 앱은 Windows Mixed Reality 동일한 방식으로 키보드 입력 데이터를 사용합니다.

AppView.cpp에서:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>가상 키보드 입력
몰입형 데스크톱 헤드셋의 경우 **CoreTextEditContext** 를 구현하여 몰입형 보기를 통해 Windows 렌더링된 가상 키보드를 지원할 수 있습니다. 이렇게 하면 Windows 앱 렌더링 텍스트 상자의 상태를 이해할 수 있으므로 가상 키보드가 텍스트에 올바르게 기여할 수 있습니다.

CoreTextEditContext 지원 구현에 대한 자세한 내용은 [CoreTextEditContext 샘플 를 참조하세요.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)

### <a name="mouse-input"></a>마우스 입력

UWP CoreWindow 입력 이벤트 처리기를 통해 마우스 입력을 다시 사용할 수도 있습니다. 누른 제스처와 동일한 방식으로 마우스 클릭을 지원하도록 Windows Holographic 앱 템플릿을 수정하는 방법은 다음과 같습니다. 이렇게 수정한 후 몰입형 헤드셋 디바이스를 누르는 동안 마우스를 클릭하면 큐브 위치가 변경됩니다.

> [!NOTE]
> UWP 앱은 [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API를 사용하여 마우스에 대한 원시 XY 데이터를 얻을 수도 있습니다.

AppView.h에서 새 OnPointerPressed 처리기를 선언하여 시작합니다.

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

AppView.cpp에서 SetWindow에 다음 코드를 추가합니다.

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

그런 다음, OnPointerPressed에 대한 이 정의를 파일의 맨 아래에 배치합니다.

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

방금 추가한 이벤트 처리기는 템플릿 주 클래스에 대한 통과입니다. 이 통과를 지원하도록 main 클래스를 수정해 보겠습니다. 헤더 파일에 다음 공용 메서드 선언을 추가합니다.

```
// Handle mouse input.
       void OnPointerPressed();
```

이 프라이빗 멤버 변수도 필요합니다.

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

마지막으로 마우스 클릭을 지원하는 새 논리로 주 클래스를 업데이트합니다. 이 이벤트 처리기를 추가하여 시작합니다. 클래스 이름을 업데이트해야 합니다.

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

이제 Update 메서드에서 포인터 자세를 얻기 위한 기존 논리를 다음으로 대체합니다.

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

다시 컴파일하고 다시 배포합니다. 마우스 클릭이 몰입형 헤드셋의 큐브 위치를 변경하거나 bluetooth 마우스가 연결된 HoloLens.

### <a name="game-controller-support"></a>게임 컨트롤러 지원

게임 컨트롤러는 사용자가 몰입형 Windows Mixed Reality 환경을 제어할 수 있는 재미있고 편리한 방법이 될 수 있습니다.

 다음 프라이빗 멤버 선언을 기본 파일의 헤더 클래스에 추가합니다.

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

주 클래스의 생성자에서 게임 패드 이벤트 및 현재 연결된 모든 게임 패드를 초기화합니다.

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

이러한 이벤트 처리기를 주 클래스에 추가합니다. 클래스 이름을 업데이트해야 합니다.

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

마지막으로 컨트롤러 상태의 변경 내용을 인식하도록 입력 논리를 업데이트합니다. 여기서는 마우스 이벤트를 추가하기 위해 위의 섹션에서 설명한 것과 동일한 m_pointerPressed 변수를 사용합니다. SpatialPointerPose를 확인하는 위치 바로 앞의 Update 메서드에 이 메서드를 추가합니다.

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

주 클래스를 정리할 때 이벤트 등록을 취소해야 합니다.

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

다시 컴파일하고 다시 배포합니다. 이제 게임 컨트롤러를 연결하거나 페어링하고 이를 사용하여 회전하는 큐브의 위치를 변경할 수 있습니다.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>키보드 및 마우스 입력에 대한 중요한 지침

기본적으로 자연 사용자 입력을 사용하는 디바이스인 Microsoft HoloLens 이 코드를 사용할 수 있는 방법과 Windows Mixed Reality 지원 PC에서 사용할 수 있는 것과는 몇 가지 주요 차이점이 있습니다.
* 키보드 또는 마우스 입력을 사용할 수 없습니다. 앱의 모든 기능은 응시, 제스처 및 음성 입력에서 작동해야 합니다.
* Bluetooth 키보드가 연결되면 앱에서 요청할 수 있는 텍스트에 키보드 입력을 사용하도록 설정하는 것이 유용할 수 있습니다. 예를 들어 이는 받아쓰기에서 훌륭한 보완이 될 수 있습니다.
* 앱을 디자인할 때는 WASD 및 마우스 모양 컨트롤을 게임에 의존하지 마세요. HoloLens 사용자가 방 주변을 둘러보도록 설계되었습니다. 이 경우 사용자는 카메라를 직접 제어합니다. 이동/모양 컨트롤을 통해 실내에서 카메라를 구동하기 위한 인터페이스는 동일한 환경을 제공하지 않습니다.
* 키보드 입력은 특히 사용자가 키보드를 사용할 필요가 없으므로 앱 또는 게임 엔진 디버깅을 제어하는 훌륭한 방법입니다. CoreWindow 이벤트 API를 사용하여 기존에 사용하던 것과 동일합니다. 이 시나리오에서는 디버그 세션 중에 키보드 이벤트를 "디버그 입력 전용" 모드로 라우팅하도록 앱을 구성하는 방법을 구현하도록 선택할 수 있습니다.
* Bluetooth 컨트롤러도 작동합니다.

## <a name="see-also"></a>참고 항목
* [하드웨어 액세서리](../../discover/hardware-accessories.md)