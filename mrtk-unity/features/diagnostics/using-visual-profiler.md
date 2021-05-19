---
title: Profiler 사용
description: MRTK에서 Visual profiler를 사용 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143716"
---
# <a name="using-the-visual-profiler"></a>시각적 프로파일러 사용

VisualProfiler는 혼합 현실 응용 프로그램의 성능에 대 한 사용 하기 쉬운 응용 프로그램 보기를 제공 합니다. 프로파일러는 다음과 같은 모든 Mixed Reality 도구 키트 플랫폼에서 지원 됩니다.

- Microsoft HoloLens (첫 번째 gen)
- Microsoft HoloLens 2
- Windows Mixed Reality 몰입형 헤드셋
- OpenVR

응용 프로그램을 개발 하는 동안 Visual Profiler가 현재 보기를 기준으로 데이터를 표시 하므로 장면의 여러 부분에 집중 합니다.

> [!IMPORTANT]
> 복합 개체, 파티클 효과 또는 활동을 사용 하 여 장면의 일부에 주목 합니다. 이러한 요소 및 기타 요소는 응용 프로그램 성능 및 이상적인 사용자 환경 감소에 영향을 주는 경우가 많습니다.

## <a name="visual-profiler-interface"></a>Visual profiler 인터페이스

![Visual Profiler 인터페이스](../images/diagnostics/VisualProfiler.png)

Visual Profiler 인터페이스에는 다음 구성 요소가 포함 되어 있습니다.

- [프레임 속도](#frame-rate)
- [프레임 시간](#frame-time)
- [프레임 그래프](#frame-graph)
- [메모리 사용률](#memory-utilization)

### <a name="frame-rate"></a>프레임 율

인터페이스의 왼쪽 위 모퉁이에는 프레임 속도로 초당 프레임 수로 측정 됩니다. 최상의 사용자 환경 및 편안 하 게이 값은 최대한 높아야 합니다.

특정 플랫폼 및 하드웨어 구성은 달성 가능한 최대 프레임 속도로 중요 한 역할을 합니다. 몇 가지 일반적인 대상 값은 다음과 같습니다.

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> 기본 [MRC가 활성 상태일 때 HoloLens의 프레임 속도 제한으로](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)인해 비디오 및 사진이 캡처되는 동안 시각적 프로파일러가 자신을 숨깁니다. 이 설정은 진단 시스템 프로필에서 재정의할 수 있습니다.

### <a name="frame-time"></a>프레임 시간

프레임 속도의 오른쪽에는 CPU에 소요된 프레임 시간(밀리초)이 있습니다. 앞에서 언급한 대상 프레임 속도를 달성하기 위해 애플리케이션은 프레임당 다음과 같은 시간을 소비할 수 있습니다.

- 60fps: 16.6ms
- 90fps: 11.1ms

GPU 시간은 향후 릴리스에서 추가될 예정입니다.

### <a name="frame-graph"></a>프레임 그래프

프레임 그래프는 애플리케이션 프레임 속도 기록을 그래픽으로 표시합니다.

![시각적 프로파일러에서 프레임 그래프 누락](../images/diagnostics/VisualProfilerMissedFrames.png)

애플리케이션을 사용하는 경우 애플리케이션이 대상 프레임 속도에 도달하지 않고 최적화 작업이 필요할 수 있음을 나타내는 누락된 프레임을 찾습니다.

### <a name="memory-utilization"></a>메모리 사용률

메모리 사용률 표시를 사용하면 현재 보기가 애플리케이션의 메모리 소비에 미치는 영향을 쉽게 이해할 수 있습니다.

![시각적 프로파일러 메모리 그래프](../images/diagnostics/VisualProfilerMemory.png)

애플리케이션을 사용하는 경우 총 메모리 사용량을 찾습니다. 핵심 지표에는 메모리 제한에 근접하고 사용량이 빠르게 변경되는 것이 포함됩니다.

## <a name="customizing-the-visual-profiler"></a>시각적 프로파일러 사용자 지정

Visual Profiler의 모양과 동작은 진단 시스템 프로필을 통해 사용자 지정할 수 있습니다. 자세한 내용은 [진단 시스템 구성을](configuring-diagnostics.md) 참조하세요.

## <a name="see-also"></a>참고 항목

- [진단 시스템](diagnostics-system-getting-started.md)
- [진단 시스템 구성](configuring-diagnostics.md)