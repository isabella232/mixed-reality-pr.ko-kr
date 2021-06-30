---
title: 컨트롤러, 포인터 및 포커스
description: 컨트롤러, 포인터 및 포커스와 상호 작용
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 포인터, 컨트롤러
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121621"
---
# <a name="controllers-pointers-and-focus"></a>컨트롤러, 포인터 및 포커스

컨트롤러, 포인터 및 초점은 핵심 입력 시스템에 의해 설정 된 기반을 기반으로 구축 되는 상위 수준 개념입니다. 이와 함께 장면의 개체와 상호 작용 하는 메커니즘의 많은 부분을 제공 합니다.

## <a name="controllers"></a>Controllers

컨트롤러는 물리적 컨트롤러 (자유도, 트레일러 식 등의 6도)를 표현 합니다. 이러한 장치는 장치 관리자에 의해 생성 되며 해당 하는 기본 시스템과 통신 하 고 해당 데이터를 MRTK 모양의 데이터 및 이벤트로 변환 합니다.

예를 들어 Windows Mixed Reality 플랫폼에서는 [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 기본 Windows [직접 추적 api](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 와 상호 작용 하 여 손, 포즈 및 기타 속성에 대 한 정보를 가져오기 위한 역할을 담당 하는 컨트롤러입니다. RaisePoseInputChanged 또는 RaiseHandJointsUpdated를 호출 하 여이 데이터를 관련 MRTK 이벤트로 전환 하 고,에 대 한 쿼리가 올바른 데이터를 반환 하도록 자체 내부 상태를 업데이트 하는 일을 담당 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) 합니다.

일반적으로 컨트롤러의 수명 주기에는 다음이 포함 됩니다.

1. 컨트롤러는 새 원본을 검색할 때 장치 관리자에 의해 생성 됩니다. 예를 들어 장치 관리자는 직접 추적을 검색 하 고 시작 합니다.

2. 컨트롤러의 Update () 루프에서는 기본 API 시스템을 호출 합니다.

3. 동일한 업데이트 루프에서 핵심 입력 시스템 자체 (예: HandMeshUpdated 또는 HandJointsUpdated)를 직접 호출 하 여 입력 이벤트 변경을 발생 시킵니다.

## <a name="pointers-and-focus"></a>포인터 및 포커스

포인터는 게임 개체와 상호 작용 하는 데 사용 됩니다. 이 섹션에서는 포인터를 만드는 방법, 업데이트 되는 방법 및 포커스에 있는 개체를 결정 하는 방법에 대해 설명 합니다. 또한 존재 하는 다양 한 유형의 포인터와 활성 상태의 시나리오를 다룹니다.

### <a name="pointer-categories"></a>포인터 범주

포인터는 일반적으로 다음 범주 중 하나에 속합니다.

- **먼 포인터**

  이러한 종류의 포인터는 사용자의 멀리 떨어져 있는 개체와 상호 작용 하는 데 사용 됩니다 (멀리 떨어져 있는 것은 단순히 "가까이 있지 않음"으로 정의 됨). 이러한 형식의 포인터는 일반적으로 전 세계에 있을 수 있는 선을 캐스트 하 고 사용자가 바로 다음에 있지 않은 개체와 상호 작용 하 고 조작할 수 있도록 합니다.

- **가까운 포인터**

  이러한 형식의 포인터를 사용 하 여 사용자가 잡아 이동 하 고 조작할 수 있을 만큼 가까운 개체와 상호 작용할 수 있습니다. 일반적으로 이러한 종류의 포인터는 가까운 주변 주변에서 개체를 검색 하 여 개체와 상호 작용 합니다. 예를 들어 작은 거리에서 raycasting를 수행 하거나 주변에서 개체를 찾는 구면 캐스트를 수행 하거나 grabbable/touchable로 간주 되는 개체 목록을 열거 합니다.

- **텔레포트 포인터**

  이러한 포인터 형식은 teleportation 시스템에 연결 하 여 포인터의 대상 위치로 사용자를 이동 하는 것을 처리 합니다.

## <a name="pointer-mediation"></a>포인터 중재

단일 컨트롤러에는 여러 개의 포인터가 있을 수 있으므로 (예를 들어, 두 번째는 근접 하 고 먼 상호 작용 포인터를 사용할 수 있음) 어떤 포인터가 활성 상태 여야 mediating를 담당 하는 구성 요소가 있습니다.

예를 들어, 사용자가 pressable 단추를 사용 하는 경우가 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 표시를 중지 하 고가 사용 됩니다 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) .

이는 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 모든 포인터의 상태에 따라 활성 상태인 포인터를 결정 하는에 의해 처리 됩니다. 이 작업을 수행 하는 주요 작업 중 하나는 가까운 포인터가 개체에 가까이 있을 때 먼 포인터를 사용 하지 않도록 설정 하는 것입니다 .를 참조 하십시오 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) .

포인터 프로필의 속성을 변경 하 여 포인터 mediator의 대체 구현을 제공할 수 있습니다 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) .

### <a name="how-to-disable-pointers"></a>포인터를 사용 하지 않도록 설정 하는 방법

포인터 mediator은 모든 프레임을 실행 하므로 모든 포인터의 활성/비활성 상태를 제어 합니다. 따라서 코드에서 포인터의 IsInteractionEnabled 속성을 설정 하면 모든 프레임 mediator 포인터로 덮어쓰여집니다. 대신, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 직접 포인터를 설정 하거나 해제할지 여부를 제어 하는를 지정할 수 있습니다. 이는 기본값 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 및 MRTK를 사용 하는 경우에만 작동 합니다 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) .

#### <a name="example-disable-hand-rays-in-mrtk"></a>예: MRTK에서 손 광선 사용 안 함

다음 코드는 MRTK에서 손 광선을 해제 합니다.

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

다음 코드는 MRTK의 기본 동작에 손 광선을 반환 합니다.

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

다음 코드는 grabbable 가까이에 있든 관계 없이 핸드 광선을 강제로 설정 합니다.

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 더 많은 예제는 및를 참조 하세요.

### <a name="focusprovider"></a>FocusProvider

는 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 모든 포인터 목록을 반복 하 고 각 포인터에 대 한 포커스가 있는 개체를 파악 하는 작업을 담당 합니다.

각 `Update()` 호출에서 다음 작업을 수행 합니다.

1. SphereOverlap raycastMode를 지정 하는 등의 방법으로 포인터 자체에서 구성 된 대로 모든 포인터를 업데이트 하 고, 포인터 자체에서 구성 된 대로 적중 검색을 수행 합니다. 예를 들어, FocusProvider는 구 기반 충돌을 발생 시킬 수 있습니다.

2. 포인터 단위로 포커스가 있는 개체를 업데이트 합니다. 즉, 개체가 포커스를 얻은 경우 해당 개체에 대 한 이벤트를 트리거합니다. 즉, 개체가 포커스를 잃어 잃은 경우 포커스가 손실 될 수도 있습니다.

### <a name="pointer-configuration-and-lifecycle"></a>포인터 구성 및 수명 주기

포인터는 입력 시스템 프로필의 *포인터* 섹션에서 [구성할 수 있습니다](../features/input/pointers.md) .

포인터의 수명은 일반적으로 다음과 같습니다.

1. 장치 관리자가 컨트롤러의 존재를 검색 합니다. 그런 다음이 장치 관리자는에 대 한 호출을 통해 컨트롤러와 연결 된 포인터 집합을 만듭니다 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. 해당 Update () 루프에서 FocusProvider는 모든 유효한 포인터를 반복 하 고, 연결 된 raycast 또는 적중 검색 논리를 수행 합니다. 이는 각 특정 포인터가 가리키는 개체를 확인 하는 데 사용 됩니다.

    - 한 번에 여러 개의 입력을 활성화 하는 것이 가능 하기 때문에 동시에 포커스가 있는 여러 개체를 사용할 수 있습니다.

3. 장치 관리자가 컨트롤러 원본이 손실 된 것을 발견 하면 손실 된 컨트롤러와 연결 된 포인터를 삭제 합니다.