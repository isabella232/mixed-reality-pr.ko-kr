---
title: 핸드 코치
description: 직접 coach에 대 한 설명 및 예제입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f6042fce7c95c106de9c72adc854e2b7112da63c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177150"
---
# <a name="hand-coach"></a>핸드 코치

![손 Coach 메뉴](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

핸드 coach는 시스템에서 사용자의 손을 감지 하지 못하는 경우 트리거되는 3D 모델링 된 손을 갖습니다. 이 구성 요소는 제스처를 학습 하지 않았을 때 사용자에 게 안내 하는 데 도움이 되는 "교육" 구성 요소로 구현 됩니다. 사용자가 지정 된 기간 동안 지정 된 제스처를 수행 하지 않은 경우에는 손으로 지연 됩니다. 핸드 coach는 단추를 누르거나 홀로그램을 선택 하는 데 사용할 수 있습니다.

현재 상호 작용 모델은 스크롤, 먼 선택 및 가까운 탭과 같은 다양 한 제스처 컨트롤을 나타냅니다. 다음은 기존 손 모양 coach 예제에 대 한 전체 목록입니다.

- 근거리 탭 – 단추에 사용 되거나 interactable 개체를 닫습니다.
- Far select – 멀리 떨어져 있는 개체에 사용 됩니다.
- Move – 홀로그램을 공간으로 이동 하는 데 사용 됩니다.
- 회전 – holograms 또는 개체를 회전 하는 방법을 보여 주는 데 사용 됩니다.
- Scale – holograms를 더 크거나 작게 조작 하는 방법을 보여 주는 데 사용 됩니다.
- 핸드 대칭 이동 – UI 시작 패널 또는 손 모양 메뉴를 가져오는 데 사용 됩니다.
- 팜 위로-기본 환경에서 hummingbird 순간에 사용 됩니다. 또 다른 제안 사항은 UI 시작 패널을 가져오는 것입니다.
- Scroll – 목록 또는 긴 문서 스크롤에 사용 됩니다.

## <a name="example-scene"></a>장면 예

[MixedRealityToolkit/실험적/HandCoach/장면을](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes) 통해 **수동 공동 작업 예제** 장면에서 예제를 찾을 수 있습니다.

## <a name="hand-3d-assets"></a>수동 3D 자산

다음에서 자산을 찾을 수 있습니다. [MixedRealityToolkit/실험적/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>품질

스킨 메시에 왜곡이 있는 경우 프로젝트에서 적절 한 수의 조인트를 사용 하 고 있는지 확인 해야 합니다.
Unity의 편집 > Project 설정 > 품질 > 기타 > 혼합 가중치로 이동 합니다. 부드러운 조인트를 보려면 "4 뼈"가 선택 되어 있는지 확인 합니다.
![Project 설정](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>스크립트

### <a name="interaction-hint"></a>상호 작용 힌트

`InteractionHint.cs`스크립트는 애니메이션을 트리거하는 래퍼 기능을 제공 하 고 손 모양에 대해 페이드를 제공 합니다.

#### <a name="how-to-set-up-an-interaction-hint"></a>상호 작용 힌트를 설정 하는 방법

상호 작용 힌트를 설정 하려면 제공 된 prefabs "StaticHandCoachRoot_L. prefab" 및 StaticHandCoachRoot_R "prefab"를 사용 하는 것이 좋습니다. 이 prefab에는 제공 된 힌트 애니메이션이 의도 한 대로 작동 하도록 적절 한 계층 뿐만 아니라 InteractionHint 스크립트 및 손 (영문)이 포함 되어 있습니다.
그렇지 않으면 애니메이터를 사용 하 여 gameObject 한 부모 수준에서 한 부모 수준으로 스크립트를 저장 해야 합니다.

#### <a name="inspector-properties"></a>Inspector 속성

- **HideIfHandTracked** 이 부울은 사용자의 손을 추적할 때 시각적 추적 상태를 사용 하 여 시각적 개체를 숨길지 여부를 지정 합니다. False로 설정 하면 "customShouldHideVisuals" 스크립팅 속성만 힌트를 숨길지 여부를 결정 하는 데 사용 됩니다.

- **Mindelay** 이 속성은 시각적 개체 표시에 대 한 최소 지연을 지정 합니다. 사용자의 손을 추적 하지 않는 경우 기본적으로이 몇 초 후에 손 모양에 대 한 시각적 개체가 표시 됩니다.

- **Maxdelay** 이 속성은 시각적 개체 표시에 대 한 최대 지연을 지정 합니다. 기본적으로 사용자의 손을 추적 하는 경우에도이 몇 초 후에 손 모양에 대 한 시각적 개체가 표시 됩니다.

- **UseMaxTimer** 이 부울 값이 false로 설정 된 경우 최대 타이머를 사용 하지 않도록 설정 하 고 사용자의 손을 볼 수 없거나 사용자 지정 조건이 false를 반환 하는 경우에만 손 힌트가 표시 되도록 합니다.

- **반복** 이 속성은 min 또는 max 타이머가 통과 했을 때 힌트 애니메이션을 재생 하는 횟수를 제어 합니다. 그런 다음 힌트를 숨기고 지연을 다시 기다립니다.

- **Autoactivate** 이 부울 값을 true로 설정 하면 스크립트의 GameObject가 계층에서 활성 상태이 고 스크립트를 사용 하도록 설정한 경우에는 타이머 논리를 통해 힌트가 자동으로 실행 됩니다. 힌트 모양 및 코드를 통해 disappearance 수동으로 제어 하려는 경우에만 false로 설정 해야 합니다.

- **애니메이션 상태** 힌트가 활성화 될 때 재생 해야 하는 애니메이션 상태의 이름입니다. 이는 StartHintLoop () 함수를 호출 하기 전에 설정 해야 합니다 (AutoActivate를 선택 하는 경우 OnEnable을 선택 하는 동안).

#### <a name="controlling-interactionhint-via-script"></a>스크립트를 통해 InteractionHint 제어

- **Starthintloop** 이 함수는 AutoActivate 플래그가 true로 설정 된 경우 표시/숨기기 루프를 시작 합니다. 그렇지 않으면 OnEnable이 시작 됩니다.
- **Stophintloop** 이 함수는 현재 재생 되 고 있지 않은 경우 페이드 아웃 애니메이션 상태를 호출 합니다. 그러면 표시/숨기기 루프를 비활성화 하 고 계층에서이를 비활성으로 설정 합니다.
- **애니메이션 상태** 이 문자열은 루프 중에 재생 되는 애니메이션 상태를 결정 합니다. 이 문자열을 변경 하 여 재생 되는 상태를 변경할 수 있지만 StopHintLoop를 호출한 후이 작업을 수행 해야 하며 상태를 변경한 후에는 StartHintLoop를 다시 호출 해야 합니다.
- **CustomShouldHideVisuals** 사용자 고유의 함수를 사용 하 여이를 설정할 수 있습니다. 시각적 개체를 숨기려면 true를 반환 해야 합니다. MinMaxTimer, 특히 max 매개 변수를 염두에 두어야 합니다.

#### <a name="custom-animation-considerations"></a>사용자 지정 애니메이션 고려 사항

페이드는 기본값인 0.5 초 이므로, rig와 함께 사용 하기 위해 만든 모든 사용자 지정 애니메이션은 의미 있는 정보를 전달 하기 위해 최소 1.5 초 여야 합니다.

제공 된 기본 페이드 인 및 페이드 아웃 상태, Fade_In 및 Fade_Out는 페이드 길이를 설정 하기 위해 두 번째 키프레임의 타임 스탬프를 변경 하 여 조정할 수 있습니다.

애니메이터 및 스크립트는 가능한 한 간단 하 게 설치 하는 방식으로 설정 되었습니다. 새 애니메이션 상태를 추가 하려면 fbx를 가져온 후 애니메이션 이름이 고유한 이름으로 설정 되어 있는지 확인 하 고 해당 애니메이션을 애니메이터로 끌어 놓습니다.

### <a name="movetotarget"></a>MoveToTarget

MoveToTarget 스크립트는 시간에 따라 추적 위치에서 대상 위치로 손 힌트를 이동 하는 기능을 제공 합니다.

#### <a name="how-to-set-up-movetotarget"></a>MoveToTarget를 설정 하는 방법

제공 된 prefabs "MovingHandCoachRoot_L. prefab" 및 MovingHandCoachRoot_R "prefab"의 계층에는 MoveToTarget가 포함 되어 있습니다. 사용자의 설정에 따라이 스크립트를 사용 하려는 경우에는 rig의 애니메이터를 포함 하는 루트 gameobject에이 스크립트를 저장 해야 합니다.

#### <a name="inspector-properties"></a>Inspector 속성

- **Trackingobject** 작업을 시작 하기 전에 rig에서 따라야 하는 개체를 사용 하 여이를 설정 합니다. 빈 GameObject을 만들어 특정 위치로 이동 하 여 추적을 쉽게 파악할 수 있도록 하는 것이 좋습니다.
- **TargetObject** 이동 하는 동안 rig를 이동 하려는 개체를 사용 하 여이를 설정 합니다. 빈 GameObject을 만들어 특정 위치로 이동 하 여 추적을 쉽게 파악할 수 있도록 하는 것이 좋습니다.
- **Rootobject** 상대 위치를 정확 하 게 계산할 수 있도록 추적 및 대상 개체 간의 공유 부모로 설정 합니다. 포함 된 prefab에는 계층 구조에 추적 및 대상 개체가 모두 있지만 대상 개체를 prefab 외부의 gameObject로 설정 하 고 루트 개체를 공유 부모로 변경할 수 있습니다.
- **기간** 몇 초 안에 TrackingObject에서 TargetObject로 이동 하는 데 소요 되는 시간 (초)입니다.
- **Targetoffset** 올바른 대상 위치에 도달할 GameObject을 가져오기 위한 조정 가능한 오프셋입니다. 애니메이션에 애니메이션을 포함 하는 위치 오프셋이 포함 된 경우에 유용 합니다.
- **애니메이션 곡선** 이는 기본적으로 선형 곡선으로 설정 되지만 동작 패스를 시작 하 고 중지할 때 감속/가속을 제공 하도록 곡선을 변경할 수 있습니다.

#### <a name="controlling-movetotarget-via-script"></a>스크립트를 통해 MoveToTarget 제어

사용자 지정 스크립트에서 MoveToTargetPosition ()를 호출 하 고, 손 rig를 TrackingObject 뒤에 표시 하려는 경우에는 다음을 호출 하 여 손 (TargetObject)에 대 한 움직임을 시작 하려는 경우에 호출을 수행 합니다.

#### <a name="controlling-movetotarget-via-animations"></a>애니메이션을 통해 MoveToTarget 제어

이동 해야 하는 애니메이션에서 두 이벤트를 설정 합니다. 하나는 Follow () 호출을 사용 하 고 다른 하나는 MoveToTargetPosition ()를 호출 합니다. 팔로가 TrackingObject를 따르기 때문에 첫 번째 키 프레임에 대해 다음을 설정 해야 합니다. MoveToTargetPosition은 대상으로 이동 하기 시작 하려는 키 프레임에서 설정 해야 합니다. 이는 제공 된 prefabs 스크립트 기능을 사용 하는 방법입니다.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

RotateAroundPoint 스크립트는 시간에 따라 피벗 점을 중심으로 손 모양 힌트를 회전 하는 기능을 제공 합니다.

#### <a name="how-to-set-up-rotatearoundpoint"></a>RotateAroundPoint를 설정 하는 방법

제공 된 prefabs "RotatingHandCoachRoot_L. prefab" 및 RotatingHandCoachRoot_R "prefab"의 계층에는 RotateAroundPoint가 포함 되어 있습니다. 사용자의 설정에 따라이 스크립트를 사용 하려는 경우에는 rig의 애니메이터를 포함 하는 루트 gameobject에이 스크립트를 저장 해야 합니다.

#### <a name="inspector-properties"></a>Inspector 속성

- **가운데 Edparent** 이를 rig를 피벗할 부모 개체에 설정 합니다.
- **InverseParent** 방향을 동일 하 게 유지 하기 위해 부모를 사용 하 여이를 설정 하 여 반대로 회전 합니다. 일반적으로이 개체는 InteractionHint 스크립트를 사용 하는 부모 개체입니다.
- **PivotPosition** 힌트를 시작 하려는 지점으로 설정 합니다.
- **기간** 가운데 Edparent를 중심으로 회전 하는 데 소요 되는 시간 (초)입니다.
- **애니메이션 곡선** 이는 기본적으로 선형 곡선으로 설정 되지만 동작 패스를 시작 하 고 중지할 때 감속/가속을 제공 하도록 곡선을 변경할 수 있습니다.
- **RotationVector** 각 축을 따라 회전할 각도입니다.

#### <a name="controlling-rotatearoundpoint-via-script"></a>스크립트를 통해 RotateAroundPoint 제어

사용자 지정 스크립트에서 RotateToTarget ()를 호출 하 여 수동으로 가운데 Edparent를 중심으로 회전을 시작 합니다. 위치를 원래 PivotPosition 다시 설정 하려면 ResetAndDeterminePivot ()를 호출 합니다.

#### <a name="controlling-rotatearoundpoint-via-animations"></a>애니메이션을 통해 RotateAroundPoint 제어

이동 해야 하는 애니메이션에서 두 이벤트를 설정 합니다. 하나는 ResetAndDeterminePivot () 호출을 사용 하 고 다른 하나는 RotateToTarget ()를 호출 합니다. ResetAndDeterminePivot는 PivotPosition로 다시 설정 되기 때문에 첫 번째 키 프레임에서 설정 해야 합니다. RotateToTarget는 rig를 중심으로 회전을 시작 하려는 키 프레임에서 설정 해야 합니다. 이는 제공 된 prefabs 스크립트 기능을 사용 하는 방법입니다.
