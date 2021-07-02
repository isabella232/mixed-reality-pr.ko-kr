---
title: 진단 시스템 개요
description: MRTK에서 진단을 사용하거나 사용하지 않도록 설정하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177239"
---
# <a name="diagnostics-system-overview"></a>진단 시스템 개요

Mixed Reality Toolkit 진단 시스템은 애플리케이션 문제를 분석할 수 있도록 애플리케이션 내에서 실행되는 진단 도구를 제공합니다.

진단 시스템의 첫 번째 릴리스에는 애플리케이션을 사용하는 동안 성능 문제를 분석할 수 있는 [Visual Profiler가](using-visual-profiler.md) 포함되어 있습니다.

## <a name="getting-started"></a>시작

> [!IMPORTANT]
> 진단 시스템은 전체 제품 개발 주기 동안 사용하도록 설정되고 최종 버전을 빌드하고 릴리스하기 전에 마지막 변경으로 사용하지 않도록 설정하는 **_것이_** 좋습니다.

진단 시스템 사용을 시작하는 두 가지 주요 단계가 있습니다.

1. 진단 시스템 [사용](#enable-diagnostics)
2. 진단 옵션 [구성](#configure-diagnostic-options)

### <a name="enable-diagnostics"></a>진단 사용

진단 시스템은 MixedRealityToolkit 개체(또는 다른 [서비스 등록 기관](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)에 의해 관리됩니다.

다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다. 다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. 검사기 패널을 진단 시스템 섹션으로 이동하고 사용을 선택합니다.
1. 진단 시스템 구현 선택

    ![진단 시스템 구현 선택](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> 기본 `DefaultMixedRealityToolkitConfigurationProfile` 프로필(Assets/MRTK/SDK/Profiles)의 사용자는 개체를 사용하도록 미리 구성된 진단 시스템을 갖게 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 됩니다.

### <a name="configure-diagnostic-options"></a>진단 옵션 구성

진단 시스템은 구성 프로필을 사용하여 표시할 구성 요소를 지정하고 해당 설정을 구성합니다. 사용 가능한 구성 요소 설정과 관련된 자세한 내용은 [진단 시스템 구성을](configuring-diagnostics.md) 참조하세요.

> [!IMPORTANT]
> 빌드 및 배포 단계 없이 애플리케이션을 개발하는 동안 Unity의 재생 모드를 사용할 수 있지만 대상 하드웨어 및 플랫폼에서 실행되는 컴파일된 애플리케이션을 사용하여 진단 시스템 결과를 평가하는 것이 중요합니다.
>
> [Visual Profiler와](using-visual-profiler.md)같은 성능 진단은 편집기 내에서 실행할 때 실제 애플리케이션 성능을 정확하게 반영하지 않을 수 있습니다.

## <a name="see-also"></a>참조

- [진단 API 설명서](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [진단 시스템 구성](configuring-diagnostics.md)
- [Visual Profiler 사용](using-visual-profiler.md)
