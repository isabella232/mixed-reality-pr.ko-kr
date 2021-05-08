---
title: 대화 상자
description: 대화 상자 컨트롤에 대한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489193"
---
# <a name="dialog"></a>대화 상자

![대화 상자](../images/dialog/MRTK_UX_Dialog_Main.png)

대화 상자 컨트롤은 상황에 맞는 앱 정보를 제공하는 UI 오버레이입니다. 종종 사용자의 작업을 요청하기도 합니다. 대화 상자를 사용하여 사용자에게 중요한 정보를 알리거나 확인 또는 추가 정보를 요청한 후에 작업을 완료할 수 있습니다.

## <a name="example-scene"></a>예제 장면

**DialogExample** 장면의 [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog) 아래에서 예제를 찾을 수 있습니다.

## <a name="how-to-use-dialog-control"></a>대화 상자 컨트롤을 사용하는 방법

MRTK는 다음과 같은 세 가지 대화 프리팹을 제공합니다.

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Dialog.Open()을 사용하여 새 대화 상자를 엽니다. 대화 상자 프리팹, 단추 수, 제목 텍스트, 메시지 텍스트, 배치 거리(근거리 또는 거리), 추가 변수)를 지정합니다. 대화 상자는 '확인(단일 단추)' 및 '선택(두 단추)' 대화 상자 옵션을 제공합니다.

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>원거리 상호 작용 범위(응시, 손 광선, 모션 컨트롤러)에 배치된 단일 '확인' 단추가 있는 큰 대화 상자를 여는 예제

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>근거리 상호 작용 범위(직접 손 상호 작용)에 배치된 사용자에 대한 선택 메시지가 포함된 작은 대화 상자를 여는 예제

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

자세한 내용은 `DialogExampleController.cs` DialogExample.unity 장면에서 를 참조하세요.
