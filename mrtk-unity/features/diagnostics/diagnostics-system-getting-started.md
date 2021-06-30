---
title: 진단 시스템 개요
description: MRTK에서 진단을 사용 및 사용 하지 않도록 설정 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121781"
---
# <a name="diagnostic-system"></a>진단 시스템

Mixed Reality Toolkit 진단 시스템은 응용 프로그램 내에서 실행 되는 진단 도구를 제공 하 여 응용 프로그램 문제를 분석할 수 있도록 합니다.

진단 시스템의 첫 번째 릴리스에는 응용 프로그램을 사용 하는 동안 성능 문제를 분석 하는 데 사용할 수 있는 [시각적 프로파일러가](using-visual-profiler.md) 포함 되어 있습니다.

## <a name="getting-started"></a>시작

> [!IMPORTANT]
> 전체 제품 개발 주기 전체에서 진단 시스템을 사용 하도록 설정 하 고 최종 버전을 빌드 및 릴리스 하기 전에 마지막 변경 내용으로 비활성화 하 **_는 것이 좋습니다._**

진단 시스템 사용을 시작 하는 데는 두 가지 주요 단계가 있습니다.

1. 진단 시스템 [사용](#enable-diagnostics)
2. 진단 옵션 [구성](#configure-diagnostic-options)

### <a name="enable-diagnostics"></a>진단 사용

진단 시스템은 MixedRealityToolkit 개체 (또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)를 통해 관리 됩니다.

다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다. 다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. 검사기 패널에서 진단 시스템 섹션으로 이동 하 고 사용을 선택 합니다.
1. 진단 시스템 구현 선택

    ![진단 시스템 구현 선택](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> 기본 프로필의 사용자 `DefaultMixedRealityToolkitConfigurationProfile` (자산/m a s v k/SDK/프로필)에는 진단 시스템이 개체를 사용 하도록 미리 구성 되어 있습니다 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) .

### <a name="configure-diagnostic-options"></a>진단 옵션 구성

진단 시스템은 구성 프로필을 사용 하 여 표시할 구성 요소를 지정 하 고 해당 설정을 구성할 수 있습니다. 사용 가능한 구성 요소 설정에 대 한 자세한 내용은 [진단 시스템 구성](configuring-diagnostics.md) 을 참조 하세요.

> [!IMPORTANT]
> 빌드 및 배포 단계를 요구 하지 않고 응용 프로그램을 개발 하는 동안 Unity의 재생 모드를 사용할 수 있지만 대상 하드웨어 및 플랫폼에서 실행 되는 컴파일된 응용 프로그램을 사용 하 여 진단 시스템 결과를 평가 하는 것이 중요 합니다.
>
> [Visual Profiler](using-visual-profiler.md)와 같은 성능 진단은 편집기 내에서 실행 될 때 실제 응용 프로그램 성능을 정확 하 게 반영 하지 않을 수 있습니다.

## <a name="see-also"></a>참조

- [진단 API 설명서](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [진단 시스템 구성](configuring-diagnostics.md)
- [시각적 프로파일러 사용](using-visual-profiler.md)
