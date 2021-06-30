---
title: 시각적 프로파일러 사용
description: MRTK에서 Visual profiler를 사용 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121651"
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
- [메모리 사용량](#memory-utilization)

### <a name="frame-rate"></a>프레임 율

인터페이스의 왼쪽 위 모퉁이에는 프레임 속도로 초당 프레임 수로 측정 됩니다. 최상의 사용자 환경 및 편안 하 게이 값은 최대한 높아야 합니다.

특정 플랫폼 및 하드웨어 구성은 달성 가능한 최대 프레임 속도로 중요 한 역할을 합니다. 몇 가지 일반적인 대상 값은 다음과 같습니다.

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> [기본 MRC가 활성 상태인 경우 HoloLens에서 프레임 속도로 제한](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)되기 때문에, 비디오와 사진을 캡처하는 동안에는 시각적 프로파일러가 자신을 숨깁니다. 이 설정은 진단 시스템 프로필에서 재정의할 수 있습니다.

### <a name="frame-time"></a>프레임 시간

프레임 주기 오른쪽은 CPU에 소요 된 프레임 시간 (밀리초)입니다. 이전에 언급 한 대상 프레임 속도를 얻기 위해 응용 프로그램은 프레임당 다음과 같은 시간을 소비할 수 있습니다.

- 60 fps: 16.6 밀리초
- 90 fps: 11.1 밀리초

GPU 시간은 이후 릴리스에 추가 될 예정입니다.

### <a name="frame-graph"></a>프레임 그래프

프레임 그래프는 응용 프로그램 프레임 요금 기록의 그래픽 표시를 제공 합니다.

![시각적 프로파일러 누락 프레임 그래프](../images/diagnostics/VisualProfilerMissedFrames.png)

응용 프로그램을 사용 하는 경우 응용 프로그램이 대상 프레임 속도로 적중 하지 않으며 최적화 작업이 필요할 수 있음을 나타내는 누락 된 프레임을 찾습니다.

### <a name="memory-utilization"></a>메모리 사용률

메모리 사용률 표시를 사용 하면 현재 뷰가 응용 프로그램의 메모리 사용에 영향을 주는 방법을 쉽게 이해할 수 있습니다.

![Visual Profiler 메모리 그래프](../images/diagnostics/VisualProfilerMemory.png)

응용 프로그램을 사용 하는 경우 총 메모리 사용량을 찾습니다. 키 표시기에는 메모리 제한과 사용량에 대 한 빠른 변경 내용이 포함 됩니다.

## <a name="customizing-the-visual-profiler"></a>시각적 프로파일러 사용자 지정

진단 시스템 프로필을 통해 Visual Profiler의 모양과 동작을 사용자 지정할 수 있습니다. 자세한 내용은 [진단 시스템 구성](configuring-diagnostics.md) 을 참조 하세요.

## <a name="see-also"></a>참조

- [진단 시스템](diagnostics-system-getting-started.md)
- [진단 시스템 구성](configuring-diagnostics.md)