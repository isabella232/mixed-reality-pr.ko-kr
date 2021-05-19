---
title: MRTK 모듈화
description: MRTK의 구성 요소화에 대해 설명합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144427"
---
# <a name="mixed-reality-toolkit-componentization"></a>Mixed Reality 도구 키트 구성 요소화

Mixed Reality Toolkit v2의 새로운 기능 중 하나는 향상된 구성 요소화입니다. 가능하면 개별 구성 요소는 기초의 핵심 계층을 제외한 모든 계층에서 격리됩니다.

## <a name="minimized-dependencies"></a>최소화된 의존성

MRTK v2는 의도적으로 모듈식으로 개발되었으며 시스템 서비스 간의 의존성을 최소화하기 위해 개발되었습니다(예: 공간 인식).

일부 시스템 서비스(예: 입력 및 원격 보고)의 특성으로 인해 적은 수의 dependencies가 존재합니다.

서비스에는 하나 이상의 데이터 공급자 구성 요소가 필요하지만 서비스 사이에는 직접 링크가 없습니다. SDK 기능(예: 사용자 인터페이스 구성 요소)에도 마찬가지입니다.

## <a name="component-communication"></a>구성 요소 통신

구성 요소 간에 직접 링크가 없도록 하기 위해 MRTK v2는 인터페이스를 활용하여 서비스, 데이터 공급자 및 애플리케이션 코드 간에 통신합니다. 이러한 인터페이스는 에 정의되며 모든 통신은 Mixed Reality Toolkit 핵심 구성 요소를 통해 라우팅됩니다.

![인터페이스를 통해 공간 인식 시스템 사용](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>MRTK 가져오기 공간 최소화

현재 MRTK는 단일 기본 패키지로 가져옵니다(완전히 선택적 패키지인 예제 패키지의 존재는 잠시 무시). 가져온 파일을 수동으로 축소하여 이 공간을 줄일 수 있지만, 잘 정의된 가이드가 없는 매우 수동적인 프로세스입니다.

Foundation 패키지를 가져오는 동안 임의의 항목을 선택 취소할 수 있습니다. 그러나 기능이 중단될 수 있기 때문에 개발 초기 단계에서는 이 작업을 수행하지 않는 것이 좋습니다. 앱의 최종 기능 집합을 파악한 후에는 다음 폴더에서 필요 없는 공급자 및 서비스를 정리할 수 있습니다.

- MRTK/서비스
- MRTK/공급자
- MRTK/SDK/기능

> [!NOTE]
> MRTK v2. x에는 asset/MRTK/Core 폴더의 콘텐츠가 **_필요_** 합니다.

## <a name="upcoming-features"></a>예정된 기능

### <a name="application-architecture"></a>애플리케이션 아키텍처

MRTK는 다음과 같은 다양 한 아키텍처를 사용 하 여 응용 프로그램을 빌드할 수 있도록 지원 합니다.

- [MixedRealityToolkit 서비스 로케이터](#mixedrealitytoolkit-service-locator)
- [개별 서비스](#individual-service-components)
- [사용자 지정 서비스 로케이터](#custom-service-locator)
- [하이브리드 아키텍처](#hybrid-architecture)

응용 프로그램 아키텍처를 선택할 때는 디자인 유연성과 응용 프로그램 성능을 고려 하는 것이 중요 합니다. 여기에 설명 된 아키텍처는 모든 응용 프로그램에 적합 하지는 않습니다.

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit 서비스 로케이터

MRTK는 기본 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 서비스 로케이터 구성 요소를 사용 하도록 응용 프로그램 장면을 설정 하 고 자동으로 구성 합니다. 이 구성 요소에는 구성 검사기를 통해 MRTK 시스템 및 데이터 공급자를 구성 하 고 구성 요소 lifespans 및 핵심 동작을 관리 하는 지원이 포함 됩니다 (예: 업데이트할 경우).

프로젝트에서 사용 되는지 여부에 관계 없이 모든 시스템이 핵심 구성 검사자에 표시 됩니다. 자세한 내용은 [Mixed Reality 구성 가이드](../configuration/mixed-reality-configuration-guide.md) 를 참조 하세요.

#### <a name="individual-service-components"></a>개별 서비스 구성 요소

일부 개발자는 개별 서비스 구성 요소를 응용 프로그램 장면 계층 구조에 포함 하려는 것으로 표시 했습니다. 이 사용을 가능 하 게 하려면 사용자 지정 등록 기관에 서비스를 캡슐화 하거나 자체 등록/자동 관리 해야 합니다.

자체 등록 서비스는 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 응용 프로그램 코드가 레지스트리를 통해 서비스 인스턴스를 검색할 수 있도록를 구현 하 고 자체를 등록 합니다.

자동 관리 서비스는 장면 계층 구조에서 singleton 개체로 구현 될 수 있습니다. 이 개체는 애플리케이션 코드가 서비스 기능에 직접 액세스하는 데 사용할 수 있는 및 인스턴스 속성을 제공합니다.

#### <a name="custom-service-locator"></a>사용자 지정 서비스 로케이터

일부 개발자는 사용자 지정 서비스 로케이터 구성 요소를 만드는 기능을 요청했습니다. 사용자 지정 서비스 로케이터는 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 인터페이스를 구현하고 활성 서비스의 수명 주기 및 핵심 동작을 관리합니다.

#### <a name="hybrid-architecture"></a>하이브리드 아키텍처

MRTK는 개발자가 필요에 따라 또는 원하는 대로 이전 접근 방식을 결합할 수 있는 하이브리드 아키텍처를 지원합니다. 예를 들어 개발자는 서비스 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 로케이터로 시작하고 자체 등록 서비스를 추가할 수 있습니다.

> [!NOTE]
> 하이브리드 아키텍처를 선택할 때는 작업 중복(예: 여러 구성 요소에서 컨트롤러 데이터 획득)을 염두에 두어야 합니다.
