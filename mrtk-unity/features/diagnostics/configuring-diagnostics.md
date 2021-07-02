---
title: 진단 시스템 구성
description: MRTK에서 진단을 구성하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: d81b441cd9bcd40846eb94320f6f7de1bbd2f0a8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177253"
---
# <a name="configuring-the-diagnostics-system"></a>진단 시스템 구성

## <a name="general-settings"></a>일반 설정

![진단 일반 설정](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용

자세한 MRTK 로깅을 사용할지 여부를 나타냅니다. 이 기본값은 false이지만 MRTK 팀이 문제를 디버그/분석할 수 있도록 자세한 추적을 설정하도록 설정될 수 있습니다. 예를 들어 문제를 제출할 때 Unity 플레이어 로그(편집기 또는 플레이어에서)를 연결하면 버그 및 문제의 원인을 좁히는 데 도움이 될 수 있습니다.

이 옵션은 진단 시스템을 사용하는지 여부와는 독립적입니다. 이는 로깅 옵션이기 때문에 진단 시스템에 표시되지만 전체 MRTK 코드베이스의 로깅에 영향을 주므로 궁극적으로 더 높은 수준에서 작동합니다.

### <a name="show-diagnostics"></a>진단 표시

진단 시스템이 구성된 진단 옵션을 표시할지 여부를 나타냅니다.

사용하지 않도록 설정하면 구성된 모든 진단 옵션이 숨겨집니다.

## <a name="profiler-settings"></a>프로파일러 설정

![진단 프로파일러 설정](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>프로파일러 표시

시각적 프로파일러를 표시할지 여부를 나타냅니다.

### <a name="frame-sample-rate"></a>프레임 샘플 속도

프레임 속도 계산을 위해 프레임을 수집하는 시간(초)입니다. 범위는 0~5초입니다.

### <a name="window-anchor"></a>창 앵커

프로파일러 창이 고정되어야 하는 뷰 포트의 어떤 부분으로. 기본값은 Lower Center입니다.

### <a name="window-offset"></a>창 오프셋

보기 포트의 가운데에서 시각적 프로파일러를 배치할 오프셋입니다. 오프셋은 *Window Anchor* 속성의 방향입니다.

### <a name="window-scale"></a>창 크기 조정

프로파일러 창에 적용된 크기 승수입니다. 예를 들어 값을 2로 설정하면 창 크기가 두 배가 됩니다.

### <a name="window-follow-speed"></a>창 팔로우 속도

보기 포트 내에서 표시 여부를 유지하기 위해 프로파일러 창을 이동할 속도입니다.

## <a name="programmatically-controlling-the-diagnostics-system"></a>프로그래밍 방식으로 진단 시스템 제어

또한 런타임에 진단 시스템 및 프로파일러의 표시 여부를 전환할 수 있습니다. 예를 들어 아래 코드는 진단 시스템 및 프로파일러를 숨깁니다.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>참조

- [진단 시스템](diagnostics-system-getting-started.md)
- [Visual Profiler 사용](using-visual-profiler.md)
