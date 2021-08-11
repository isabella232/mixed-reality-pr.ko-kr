---
title: 대화 상자
description: 대화 상자 컨트롤에 대 한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 5d63fcfe79a1c3b09c78f435cec3c2155b403795993f46628cf0f5743bfd42a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203682"
---
# <a name="dialog"></a>대화 상자

![대화 상자](../images/dialog/MRTK_UX_Dialog_Main.png)

대화 상자 컨트롤은 상황별 앱 정보를 제공 하는 UI 오버레이입니다. 종종 사용자의 작업을 요청하기도 합니다. 대화 상자를 사용하여 사용자에게 중요한 정보를 알리거나 확인 또는 추가 정보를 요청한 후에 작업을 완료할 수 있습니다.

## <a name="example-scene"></a>장면 예

다음의 **Dialogexample** 장면에서 예제를 찾을 수 있습니다. [mrtk/예제/데모/UX/대화 상자](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>대화 상자 컨트롤을 사용 하는 방법

MRTK는 세 개의 대화 prefabs을 제공 합니다.

- DialogSmall_192x96 prefab
- DialogMedium_192x128 prefab
- DialogLarge_192x192 prefab

Dialog ()를 사용 하 여 새 대화 상자를 엽니다. 대화 상자 prefab, 단추 수, 제목 텍스트, 메시지 텍스트, 배치 거리 (near 또는 far), 추가 변수를 지정 합니다. 대화 상자는 ' 확인 (단일 단추) ' 및 ' 선택 (두 단추) ' 대화 상자 옵션을 제공 합니다.

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>단일 ' 확인 ' 단추를 사용 하 여 매우 많은 대화 상자를 여는 경우의 예는 먼 상호 작용 범위 (응시, 손 모양, 동작 컨트롤러)에 배치 됩니다.

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>사용자에 대 한 choice 메시지를 포함 하는 작은 대화 상자를 여는 데 가까운 상호 작용 범위 (직접 상호 작용)에 배치 된 예

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

자세한 내용은 `DialogExampleController.cs` DialogExample. unity 장면에서을 참조 하세요.
