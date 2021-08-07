---
title: 제스처
description: MRTK의 제스처 및 해당 이벤트에 대한 Docummentation
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 제스처,
ms.openlocfilehash: db6be5845c11efd5bfb199db9c53c867ea315f65bff0a799cd6bf63b9c50a3d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209170"
---
# <a name="gestures"></a>제스처

제스처는 사람의 손을 기반으로 하는 입력 이벤트입니다. MRTK에서 제스처 입력 이벤트를 발생시키는 디바이스에는 두 가지 유형이 있습니다.

- HoloLens 같은 디바이스를 Windows Mixed Reality. 이는 손가락 모으기 동작("에어 탭") 및 탭 및 유지 제스처에 대해 설명합니다.

  HoloLens 제스처에 대한 자세한 내용은 [Windows Mixed Reality 제스처 설명서를 참조하세요.](/windows/mixed-reality/gestures)

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)[는 Unity XR을 래핑합니다. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) - HoloLens 디바이스에서 Unity의 제스처 이벤트를 사용합니다.

- 터치 스크린 디바이스.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 는 물리적 터치 스크린을 지원하는 [Unity Touch 클래스를](https://docs.unity3d.com/ScriptReference/Touch.html) 래핑합니다.

이러한 두 입력 소스는 _모두 제스처 설정_ 프로필을 사용하여 Unity의 Touch 및 제스처 이벤트를 각각 MRTK의 입력 작업 으로 [변환합니다.](input-actions.md) 이 프로필은 입력 _시스템 설정_ 프로필에서 찾을 수 있습니다.

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>제스처 이벤트

제스처 이벤트는 제스처 처리기 인터페이스 또는 (이벤트 처리기 표 참조) 중 하나를 구현하여 [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [수신됩니다.](input-events.md)

제스처 이벤트 처리기의 예제 구현은 [예제 장면](#example-scene) 을 참조하세요.

제네릭 버전을 구현할 때 *OnGestureCompleted* 및 *OnGestureUpdated* 이벤트는 다음 형식의 형식화된 데이터를 받을 수 있습니다.

- `Vector2` - 2D 위치 제스처입니다. 를 알리기 위해 터치 스크린에서 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 생성됩니다.
- `Vector3` - 3D 위치 제스처입니다. HoloLens 생성하여 다음을 알 수 있습니다.
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 조작 이벤트의
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 탐색 이벤트의
- `Quaternion` - 3D 회전 제스처입니다. 사용자 지정 입력 소스에 사용할 수 있지만 현재 기존 입력 소스에서 생성되지 않습니다.
- `MixedRealityPose` - 결합된 3D 위치/회전 제스처입니다. 사용자 지정 입력 소스에 사용할 수 있지만 현재 기존 입력 소스에서 생성되지 않습니다.

## <a name="order-of-events"></a>이벤트 순서

사용자 입력에 따라 다음과 같은 두 가지 주요 이벤트 체인이 있습니다.

- "Hold":
    1. 길게 탭합니다.
        - _조작_ 시작
    1. [HoldStartDuration을 탭합니다.](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - _보류_ 시작
    1. 릴리스 탭:
        - 완료 _보류_
        - 완전한 _조작_

- "이동":
    1. 길게 탭합니다.
        - _조작_ 시작
    1. [HoldStartDuration을 탭합니다.](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - _보류_ 시작
    1. [NavigationStartThreshold를](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)넘어 손을 이동합니다.
        - _보류_ 취소
        - _탐색_ 시작
    1. 릴리스 탭:
        - 완전한 _조작_
        - _탐색_ 완료

## <a name="example-scene"></a>예제 장면

HandInteractionGestureEventsExample(Assets/MRTK/Examples/Demos/HandTracking/Scenes) 장면에서 Result 포인터를 사용하여 적중 위치에서 개체를 생성하는 방법을 보여줍니다. 

`GestureTester`(Assets/MRTK/Examples/Demos/HandTracking/Script) 스크립트는 GameObjects를 통해 제스처 이벤트를 시각화하는 예제 구현입니다. 처리기 함수는 표시기 개체의 색을 변경하고 장면의 텍스트 개체에 마지막으로 기록된 이벤트를 표시합니다.
