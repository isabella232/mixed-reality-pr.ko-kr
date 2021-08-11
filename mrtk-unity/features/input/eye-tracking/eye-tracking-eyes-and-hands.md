---
title: 눈 및 손
description: MRTK의 손 동작과 함께 시선 대상 지정을 기본 포인터로 사용하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: 37411eb344b4efae03a00bb06a31ce56182cc724d96b2cdcc008f10a66d56011
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224770"
---
# <a name="eyes-and-hands"></a>눈 및 손

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>_모양 + 손 동작(시선_ 응시 & 손 제스처)을 지원하는 방법

이 페이지에서는 손 동작과 함께 시선 대상 지정을 기본 포인터로 사용하는 방법을 설명합니다.
[MRTK 시선 추적 데모에서는](../../example-scenes/eye-tracking-examples-overview.md)눈 + 손을 사용하는 몇 가지 예를 설명합니다. 예를 들면 다음과 같습니다.

- [선택:](eye-tracking-target-selection.md)먼 홀로그램 단추를 보고 손가락 모으기 제스처를 수행하여 빠르게 선택합니다.
- **위치(이 문서)**: 홀로그램을 보고, 인덱스 손가락과 엄지 손가락으로 묶어 잡고, 손을 사용하여 주변으로 이동하여 홀로그램을 장면 전체로 Fluently 이동합니다.
- [탐색:](eye-tracking-navigation.md)확대하려는 위치를 살펴보고, 인덱스 손가락과 엄지 손가락을 묶고, 손을 _끌어와_ 확대합니다.

MRTK는 현재 원거리 손 광선이 우선 순위가 있는 포커스 포인터 역할을 하는 방식으로 설계되었습니다.
즉, 손을 감지하면 머리 및 시선 응시 포인터가 자동으로 표시되지 않으며 "선택"이라고 말하면 다시 표시됩니다.
그러나 이 방법은 멀리서 상호 작용하려는 방식이 아니고 보기에서 손의 존재와는 별개로 간단한 _'응시 및 커밋'_ 상호 작용을 선호할 수 있습니다.

### <a name="how-to-disable-the-hand-ray"></a>손 광선을 사용하지 않도록 설정하는 방법

손 광선 포인터를 사용하지 않도록 설정하려면 _입력 -> 포인터_ MRTK 구성 설정에서 _'DefaultControllerPointer'를_ 제거하면 됩니다.
앱에서 위에서 설명한 대로 눈과 손을 사용하려면 [시선 추적을 사용하기 위한](eye-tracking-basic-setup.md)모든 요구 사항을 충족하는지 확인하세요.

![손 광선을 제거하는 방법](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

시선 추적 샘플 패키지의 입력 프로필 _EyeTrackingDemoPointerProfile이_ 참조로 설정되는 방법을 확인할 수도 있습니다.

### <a name="how-to-keep-gaze-pointer-always-on"></a>응시 포인터를 항상 켜진 상태로 유지하는 방법

손을 감지한 후 머리 또는 시선 응시 포인터를 자동으로 표시하지 않도록 하기 위해 응시를 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 지정하여 설정 또는 해제 여부를 제어할 수 있습니다.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

[`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md) 참조

---
["MixedRealityToolkit의 시선 추적"으로 돌아가기](eye-tracking-main.md)
