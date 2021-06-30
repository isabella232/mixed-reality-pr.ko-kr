---
title: 실험적 기능
description: MRTK의 실험적 기능과 관련 된 문서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121381"
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

실험적 폴더 이외의 폴더에는 0으로 변경 하는 것을 목표로 합니다. 다음은 실험적 변경을 수행할 수 있는 폴더 목록입니다.

- MRTK/SDK/실험적
- MRTK/SDK/검사기/실험적
- MRTK/예제/실험적

이러한 폴더의 외부에 있는 변경 내용은 매우 신중 하 게 처리 해야 합니다. 실험적 기능에 MRTK core 코드에 대 한 변경 내용을 포함 해야 하는 경우 테스트 및 설명서를 포함 하는 별도의 끌어오기 요청으로 MRTK 변경 내용을 분할 하는 것이 좋습니다.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>실험적 기능을 사용 하면 사용자의 핵심 컨트롤 사용 능력에 영향을 주지 않습니다.

대부분의 사람들은 ManipulationHandler 및 Interactable 단추와 같은 핵심 UX 구성 요소를 매우 자주 사용 합니다. 사용자가 단추를 사용 하지 못하도록 하는 경우 실험적 기능을 사용 하지 않을 가능성이 높습니다.

구성 요소를 사용 하는 경우 ManipulationHandler, BoundingBox 또는 interactable 단추가 중단 되어서는 안 됩니다.

예를 들어 [이 SCROLLABLEOBJECTCOLLECTION PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)에서 ScrollableObjectCollection를 추가 하면 사용자가 HoloLens 단추 prefabs를 사용할 수 없습니다. PR의 버그로 인해 발생 하는 것은 아니지만 기존 버그를 노출 하는 경우에도 PR을 체크 인할 수 없습니다.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>기능을 사용 하는 방법을 보여 주는 예제 장면을 제공 합니다.

사용자는 기능을 사용 하는 방법 및 테스트 하는 방법을 확인 해야 합니다.

MRTK/example/실험적/YOUR_FEATURE 아래에 예제를 제공 합니다.

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>실험적 기능에서 사용자에 게 보이는 결함 최소화

다른 사용자는 실험적 기능을 사용 하지 않는 경우 해당 기능을 사용 하지 않습니다.

대상 플랫폼에서 예제 장면을 테스트 하 고 예상 대로 작동 하는지 확인 합니다. 기능이 편집기에서 작동 하는지 확인 하 여 대상 플랫폼이 없더라도 사용자가 신속 하 게 반복 하 고 기능을 볼 수 있도록 합니다.

## <a name="graduating-experimental-code-into-mrtk-code"></a>MRTK 코드에 실험적 코드 졸업

기능이 매우 많은 사용을 표시 하는 경우에는 핵심 MRTK 코드를 졸업 해야 합니다. 이렇게 하려면 기능에 테스트, 설명서 및 예제 장면이 있어야 합니다.

MRTK 기능을 졸업 할 준비가 되 면 PR에 대해 확인 하는 문제를 만듭니다. PR은이를 핵심 기능으로 만드는 데 필요한 모든 항목을 포함 해야 합니다. 테스트, 설명서 및 사용법을 보여 주는 예제 장면.

또한 "실험적" 하위 공간을 제거 하려면 네임 스페이스를 업데이트 해야 합니다.
