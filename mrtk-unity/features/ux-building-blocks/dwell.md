---
title: 유지
description: 유지 조작
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: 지속, Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226912"
---
# <a name="dwell"></a>유지

![유지 영웅](../images/dwell/MRTK_UX_Dwell.png)

헤드-응시 및 유지는 사용자가 다른 작업을 사용 하는 시나리오에서 유용 합니다. 이 기능은 음성이 100% 안정적이 아니거나 환경 또는 소셜 제약 조건으로 인해 사용할 수 있는 경우에도 유용 합니다.
MRTK의 유지 예제는 구성 가능한 응답 시간 및 시각적 피드백을 포함 하는 다양 한 유형의 UI 구성 요소를 보여 줍니다.

디자인 권장 사항에 대해서는 [Head-응시 및 지속 지침](/windows/mixed-reality/design/gaze-and-dwell-head) 페이지를 참조 하세요.

## <a name="dwell-scripts"></a>유지 스크립트

- **DwellHandler**: 유지 모달을 UI 대상에 추가 합니다.
- **DwellStateType**: 유지 처리기의 상태입니다.
- **DwellUnityEvent**: 유지 이벤트에 대 한 Unity 이벤트입니다. 포인터 참조를 포함 합니다.
- **BaseDwellPressableButton** : `Interactable` PressableButtonHoloLens2 prefabs의 OnClick () 이벤트를 트리거하는 스크립트입니다.
- **ToggleDwellPressableButton** :이 스크립트는 `_BorderWidth` `dwellVisualImage` Mrtk 표준 셰이더를 사용 하는의 속성을 수정 합니다.

## <a name="dwell-profiles"></a>지속 프로필
지속 프로필은 유지 **처리기** 에서 다양 한 임계값을 구성 하는 데 사용 됩니다.
- **ButtonDwellProfile**
- **InstandDwellProfile**
- **DwellProfileWithDecay**

## <a name="prefabs"></a>Prefabs

이러한 prefabs는 유지 상호 작용을 지 원하는 추가 구성 요소가 있는 HoloLens 2 스타일 pressable button prefabs의 변형입니다.

- **PressableButtonHoloLens2_Dwell prefab**
- **PressableButtonHoloLens2_32x96_Dwell prefab**
- **PressableButtonHoloLens2ToggleDwell. prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell prefab**

이러한 **prefabs에는** 유지 입력 상태를 시각화 하는 추가 backplate 구성 요소가 있습니다. **HolographicBackPlateDwellVisual** 자료를 할당 합니다. **ToggleDwellPressableButton** 는 MRTK 표준 셰이더의 **_BorderWidth** 속성을 업데이트 하 여 유지 입력을 시각화 합니다.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>장면 예

장면에서 예제를 찾을 수 있습니다 `DwellExample` . 예제 장면에서는 대규모 UI 예제와 Unity UI 예제를 모두 보여 줍니다.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>추가 정보

- [**단추**](button.md)
- [**상호 작용 가능**](interactable.md)
