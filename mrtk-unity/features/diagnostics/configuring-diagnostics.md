---
title: 진단 구성
description: MRTK에서 진단 구성 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 2ff761baa728017eb011cb9105cf203e6e3a72e4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144170"
---
# <a name="configuring-the-diagnostics-system"></a>진단 시스템 구성

## <a name="general-settings"></a>일반 설정

![진단 일반 설정](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용

Verbose MRTK 로깅을 사용할지 여부를 나타냅니다. 이 기본값은 false 이지만 MRTK 팀에서 디버그/문제를 해결 하는 데 사용할 수 있는 자세한 추적을 사용 하도록 설정할 수 있습니다. 예를 들어 문제를 해결할 때 Unity 플레이어 로그 (편집기나 플레이어)를 연결 하면 버그와 문제의 원인을 좁힐 수 있습니다.

이 옵션은 진단 시스템이 사용 하도록 설정 되었는지 여부와는 독립적입니다 .이 옵션은 로깅 옵션 이지만 궁극적으로는 전체 MRTK 코드 베이스의 로깅에 영향을 주므로 더 높은 수준에서 작동 하므로 진단 시스템에 표시 됩니다.

### <a name="show-diagnostics"></a>진단 표시

진단 시스템이 구성 된 진단 옵션을 표시 하는지 여부를 나타냅니다.

사용 하지 않도록 설정 하면 구성 된 모든 진단 옵션이 숨겨집니다.

## <a name="profiler-settings"></a>프로파일러 설정

![진단 프로파일러 설정](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>프로파일러 표시

시각적 프로파일러를 표시할지 여부를 나타냅니다.

### <a name="frame-sample-rate"></a>프레임 샘플링 주기

프레임 주기 계산에 대 한 프레임을 수집 하는 시간 (초)입니다. 범위는 0 초에서 5 초입니다.

### <a name="window-anchor"></a>창 앵커

프로파일러 창이 고정 되는 뷰 포트의 부분입니다. 기본값은 아래쪽 가운데입니다.

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

## <a name="see-also"></a>참고 항목

- [진단 시스템](diagnostics-system-getting-started.md)
- [Visual Profiler 사용](using-visual-profiler.md)
