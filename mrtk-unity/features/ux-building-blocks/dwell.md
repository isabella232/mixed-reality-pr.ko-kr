---
title: 연연
description: Dwell 상호 작용
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647863"
---
# <a name="dwell"></a>연연

![Dwell Hero](../images/dwell/MRTK_UX_Dwell.png)

헤드 응시 및 번지는 사람의 손을 다른 작업으로 사용 중인 시나리오에서 유용합니다. 이 기능은 음성이 100% 안정적이지 않거나 환경 또는 소셜 제약으로 인해 사용할 수 없는 경우에도 유용합니다.
MRTK의 dwell 예제는 구성 가능한 응답 시간 및 시각적 피드백을 통해 다양한 유형의 UI 구성 요소를 보여줍니다.

디자인 권장 사항은 [헤드 응시 및 상주 지침](/windows/mixed-reality/design/gaze-and-dwell-head) 페이지를 참조하세요.

## <a name="dwell-scripts"></a>Dwell 스크립트

- **DwellHandler:** UI 대상에 유지 형식을 추가합니다.
- **DwellStateType: dwell** 처리기의 상태입니다.
- **DwellUnityEvent:** 유지 이벤트에 대한 Unity 이벤트입니다. 포인터 참조를 포함합니다.
- **BaseDwellPressableButton.cs:** PressableButtonHoloLens2 프리팹의 에서 OnClick() 이벤트를 트리거하는 `Interactable` 스크립트입니다.
- **ToggleDwellPressableButton.cs:** 이 `_BorderWidth` `dwellVisualImage` 스크립트는 MRTK 표준 셰이더를 사용하는 의 속성을 수정합니다.

## <a name="dwell-profiles"></a>Dwell 프로필
Dwell 프로필은 **Dwell 처리기에서** 다양한 임계값을 구성하는 데 사용됩니다.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>프리 팹

이러한 프리팹은 유지 상호 작용을 지원하는 추가 구성 요소가 있는 HoloLens 2 스타일 누를 수 있는 단추 프리팹의 변형입니다.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

이러한 프리팹에는 더 많은 백플레이트 구성 요소 **QuadDwellVisual이** 있습니다. **HolographicBackPlateDwellVisual.mat** 재질이 할당되어 있습니다. **ToggleDwellPressableButton.cs는** MRTK 표준 셰이더의 **_BorderWidth** 속성을 업데이트하여 dwell 입력을 시각화합니다.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>예제 장면

장면에서 예제를 찾을 수 `DwellExample` 있습니다. 예제 장면에는 볼륨이 많은 UI 예제와 Unity UI 예제가 모두 표시됩니다.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>참조

- [**단추**](button.md)
- [**상호 작용 가능**](interactable.md)
