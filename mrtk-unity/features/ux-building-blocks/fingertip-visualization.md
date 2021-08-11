---
title: 손끝 시각화
description: MRTK의 FingerTip 시각화 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, Fingertip
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193306"
---
# <a name="fingertip-visualization"></a>손끝 시각화

![Fingertip 시각화 기본](../images/fingertip/MRTK_FingertipVisualization_Main.png)

Fingertip affordance를 사용 하면 사용자가 대상 개체 로부터의 거리를 인식할 수 있습니다. 링 모양 시각적 개체는 fingertip에서 개체로의 거리를 기준으로 크기를 조정 합니다. Fingertip 시각화는 기본적으로 `FingerCursor` *Pokepointer* 의 커서 prefab로 생성 되는 (ASSET/MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor) (및 스크립트)에 의해 제어 됩니다. 시각화의 다른 구성 요소에는 *ProximityLight* 스크립트와 *MixedRealityStandard* 셰이더가 있습니다.

## <a name="how-to-use-the-fingertip-visualization"></a>Fingertip 시각화를 사용 하는 방법

기본적으로 fingertip 시각화는 FingerCursor를 생성 하도록 구성 된 모든 Unity 장면에서 작동 합니다. FingerCursor의 생성은 다음 *DefaultMixedRealityToolkitConfigurationProfile* 에 발생 합니다.

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

높은 수준에서 fingertip 시각화는 근접 조명을 사용 하 여 근접 조명을 허용 하는 주변 표면에서 색이 지정 된 그라데이션을 프로젝션 하는 방식으로 작동 합니다. 그러면 손가락 커서는 부모에 의해 결정 되는 주변의 interactable 표면을 검색 하 여 `IMixedRealityNearPointer(s)` 손가락이 화면으로 이동 하는 것 처럼 손가락 링을 표면과 맞춥니다. 손가락이 표면에 가까워지면 손가락 링은 MixedRealityStandard 셰이더의 둥근 모퉁이 속성을 사용 하 여 동적으로 애니메이션을 적용 합니다.

## <a name="example-scene"></a>장면 예

Fingertip 시각화 예제는 트레일러 식에서 작동 하는 거의 모든 장면에서 볼 수 있지만 [HandInteractionExample 장면](../example-scenes/hand-interaction-examples.md)에서 볼 수 있습니다.

![Fingertip 시각화 상태](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Inspector 속성

**FingerCursor** 대부분의 손가락 커서 속성은 기본 커서 클래스에서 상속 됩니다. 중요 한 속성에는 MixedRealityStandard 셰이더에 손가락 링 애니메이션을 구동 하는 멀리 떨어져 있는 표면 여백 및 너비가 포함 됩니다. 다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** 근접 조명 설정은 화면 가까이와 멀리 떨어져 있는 경우 조명이 표시 되는 방식을 제어 합니다. 가운데, 가운데 및 외부 색은 조명의 그라데이션 모양을 제어 하며 응용 프로그램의 색상표에 맞게 사용자 지정이 가능 합니다. 색은 사용자가 근접 한 조명을 위의 값으로 밝게 할 수 있도록 하는 HDR (높은 동적 범위)입니다. 다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.

**MixedRealityStandard 셰이더** MixedRealityStandard 셰이더는 MRTK의 많은 효과에 사용 됩니다. Fingertip 시각화에 중요 한 두 가지 설정은 "근거리 페이드" 및 "근접 조명"입니다. 가까이 페이드를 사용 하면 개체를 카메라 또는 빛으로 페이드 인 하거나 빛을 희미하게 할 수 있습니다. 근접 조명이 카메라 대신 페이드를 구동 하도록 하려면 "Light"를 선택 해야 합니다. "페이드 Begin" 및 "페이드 완료" 값을 반대로 바꿔 페이드를 되돌릴 수 있습니다. 근접 조명을 밝게 하려는 모든 표면에 대해 "근접 조명"을 선택 합니다. 다른 속성의 경우 검사기 도구 설명을 마우스로 가리킵니다.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
