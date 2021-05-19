---
title: 실험적 기능
description: MRTK의 실험적 기능과 관련 된 문서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 705b7ab96d22c5c94c04476de30e5524095c1ce2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144782"
---
# <a name="experimental-features"></a>실험적 기능

MRTK 팀에서 작업 하는 일부 기능은 세부 정보를 완전히 갖춰진 않는 경우에도 많은 초기 값이 있는 것 처럼 보입니다. 이러한 유형의 기능을 위해 커뮤니티에서 일찍 볼 수 있는 기회를 원합니다. 주기 초기에 있기 때문에 실험으로 표시 하 여 계속 진화 하 고 있으며 시간이 지남에 따라 변경 될 수 있습니다.

## <a name="what-to-expect-from-an-experimental-feature"></a>실험적 기능에서 예측할 수 있는 사항

구성 요소가 실험적으로 표시 되어 있는 경우 다음을 예측할 수 있습니다.

- 하위 폴더에 있는 사용법을 보여 주는 예제 장면 `MRTK/Examples/Experimental`
- 실험적 기능에 문서를 사용할 수 없습니다.
- 테스트는 없을 수 있습니다.
- 실험적 기능은 변경 될 수 있습니다.

## <a name="experimental-feature-guidelines"></a>실험적 기능 지침

### <a name="experimental-code-should-live-in-a-separate-folder"></a>실험적 코드는 별도의 폴더에 있어야 합니다.

실험적 코드는 최고 수준의 실험적 폴더와 실험적 기능 이름을 차례로 이동 해야 합니다. 예를 들어 새 기능 FooBar를 적용 하려는 경우 코드를 다음과 같이 입력 합니다.

- 예제 장면, 스크립트 이동 `MRTK/Examples/Experimental/FooBar/`
- 구성 요소 스크립트, prefabs으로 이동 `MRTK/SDK/Experimental/FooBar/`
- 구성 요소 검사기 이동 `MRTK/SDK/Inspectors/Experimental/FooBar`

실험적 기능 이름 아래의 하위 폴더를 사용 하는 경우 MRTK의 동일한 폴더 구조를 미러링합니다.

예를 들어, solvers는 다음과 같이 진행 됩니다. `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

위쪽 근처의 장면 폴더에 장면 유지: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> 단일 실험적 루트 폴더가 없고 대신 실험을 만드는 것으로 간주 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 됩니다. 실험 기능을 보다 쉽게 검색할 수 있도록 기준으로 폴더를 사용 하기로 결정 했습니다.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>실험적 코드는 특수 네임 스페이스에 있어야 합니다.

실험적 코드가 실험적이 아닌 위치와 일치 하는 실험적 네임 스페이스에 상주 하는지 확인 합니다. 예를 들어 구성 요소가 solvers의 일부인 경우 `Microsoft.MixedReality.Toolkit.Utilities.Solvers` 해당 네임 스페이스는 여야 합니다 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

예제는 [이 PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 을 참조 하세요.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>실험적 기능에는 [실험적] 특성이 있어야 합니다.

필드 중 `[Experimental]` 하나에 특성을 추가 하 여 기능을 실험적 이라고 표시 하 고 중요 한 변경 내용을 적용 하는 작은 대화 상자를 구성 요소 편집기에 표시 합니다.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>실험적 기능에 대 한 메뉴는 "실험적" 하위 메뉴 아래에 있어야 합니다.

편집기에서 메뉴에 명령을 추가할 때 실험적 기능이 "실험적" 하위 메뉴 아래에 있는지 확인 합니다. 다음은 몇 가지 예입니다.

최상위 메뉴 명령 추가:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

구성 요소 메뉴 추가:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>설명서

실험적 기능에 대 한 설명서를 추가 하려면 다음 단계를 따르세요.

1. 실험적 기능에 대 한 설명서는 `readme.md` 실험적 폴더의 파일로 이동 해야 합니다. 예: MRTK/SDK/실험적/PulseShader/추가 정보.

1. *기능 개요* 아래에서 *실험적* 섹션의 링크를 추가 [`Documentation/toc.yml`](../toc.yml) 합니다.

### <a name="minimize-impact-to-mrtk-code"></a>MRTK 코드에 대 한 영향 최소화

MRTK가 변경 되 면 실험에서 작업을 수행할 수 있지만 예상치 못한 방식으로 다른 사용자에 게 영향을 줄 수 있습니다.
MRTK core 코드에 대 한 모든 재발으로 인해 끌어오기 요청이 되돌려집니다.

실험적 폴더 이외의 폴더에는 0으로 변경 하는 것을 목표로 합니다. 실험적 변경이 있을 수 있는 폴더 목록은 다음과 같습니다.

- MRTK/SDK/실험적
- MRTK/SDK/Inspectors/Experimental
- MRTK/예제/실험적

이러한 폴더 외부의 변경 내용은 매우 신중하게 처리해야 합니다. 실험적 기능에 MRTK 핵심 코드 변경 내용이 포함되어야 하는 경우 MRTK 변경 내용을 테스트 및 설명서를 포함하는 별도의 끌어오기 요청으로 분할하는 것이 좋습니다.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>실험적 기능을 사용하는 것은 핵심 컨트롤을 사용하는 사용자의 기능에 영향을 미치지 않아야 합니다.

대부분의 사람들은 Button, ManipulationHandler 및 Interactable과 같은 핵심 UX 구성 요소를 매우 자주 사용합니다. 단추를 사용할 수 없는 경우 실험적 기능을 사용하지 못할 수 있습니다.

구성 요소를 사용하면 단추, ManipulationHandler, BoundingBox 또는 상호 작용이 중단되지 않아야 합니다.

예를 들어 [이 ScrollableObjectCollection PR에서](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)ScrollableObjectCollection을 추가하면 사람들이 HoloLens 단추 프리팹을 사용할 수 없습니다. PR의 버그로 인한 것이 아니라 기존 버그를 노출했지만 PR이 체크 인되지 않았습니다.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>기능을 사용하는 방법을 보여 주는 예제 장면 제공

사람들은 기능을 사용하는 방법과 테스트하는 방법을 확인해야 합니다.

MRTK/Examples/Experimental/YOUR_FEATURE 아래에 예제를 제공합니다.

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>실험적 기능에서 사용자 표시 결함 최소화

실험적 기능이 작동하지 않는 경우 다른 사람은 실험적 기능을 사용하지 않고 기능을 사용하지 않습니다.

대상 플랫폼에서 예제 장면을 테스트하고 예상대로 작동하는지 확인합니다. 편집기에서도 기능이 작동하는지 확인합니다. 따라서 사용자는 대상 플랫폼이 없어도 신속하게 반복하고 기능을 볼 수 있습니다.

## <a name="graduating-experimental-code-into-mrtk-code"></a>실험적 코드를 MRTK 코드로 다시 변환

기능이 매우 많은 사용을 표시 하는 경우에는 핵심 MRTK 코드를 졸업 해야 합니다. 이렇게 하려면 기능에 테스트, 설명서 및 예제 장면이 있어야 합니다.

MRTK 기능을 졸업 할 준비가 되 면 PR에 대해 확인 하는 문제를 만듭니다. PR은이를 핵심 기능으로 만드는 데 필요한 모든 항목을 포함 해야 합니다. 테스트, 설명서 및 사용법을 보여 주는 예제 장면.

또한 "실험적" 하위 공간을 제거 하려면 네임 스페이스를 업데이트 해야 합니다.
