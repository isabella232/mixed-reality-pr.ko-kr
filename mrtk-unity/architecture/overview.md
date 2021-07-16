---
title: 아키텍처 개요
description: MRTK의 아키텍처 개요입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk 아키텍처,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281919"
---
# <a name="architecture-overview"></a>아키텍처 개요

MRTK의 내용에 대 한 전반적인 소개를 위해이 문서에 포함 된 아키텍처 정보는 다음을 이해 하는 데 도움이 됩니다.

- MRTK의 많은 부분과 연결 방법
- MRTK가 소개 하는 개념은 바닐라 Unity에 없을 수 있습니다.
- 더 큰 시스템 (예: 입력)의 일부는 어떻게 작동 합니까?

이 섹션은 작업을 수행 하는 방법을 설명 하기 위한 것이 아니라 이러한 작업을 구성 하는 방법 및 이유를 설명 하기 위한 것입니다.

## <a name="many-audiences-one-toolkit"></a>여러 대상 그룹, 도구 키트 하나

MRTK에는 단일 단일 대상이 없습니다. 해커 톤 행사는 처음부터 엔터프라이즈에 대 한 복잡 하 고 공유 된 환경을 구축 하는 개인에 이르는 사용 사례를 지원 하기 위해 작성 되었습니다. 일부 코드 및 Api는 다른 하나 이상에 대해 최적화 된 것으로 작성 되었을 수 있습니다. 즉, MRTK의 일부는 "한 번 클릭 구성"에 대해 최적화 된 것 처럼 보이지만 기록 및 높아지면 이유 중 일부는 더 중요 합니다. MRTK가 진화 함에 따라 작성 되는 기능은 사용 사례의 범위를 지원 하도록 크기를 조정 하도록 설계 되어야 합니다.

MRTK에는 VR 및 AR 환경에서 원활 하 게 확장할 수 있는 요구 사항도 있습니다. HoloLens 2 또는 HoloLens 1에 배포 될 때 동작을 정상적으로 대체 하는 응용 프로그램을 쉽게 빌드할 수 있어야 합니다. openvr 및 WMR (및 기타 플랫폼)를 대상으로 하는 응용 프로그램을 빌드하는 것이 간단 합니다. 팀이 특정 시스템이 나 플랫폼에서 특정 반복에 집중할 수 있는 반면 장기적 목표는 사용자가 혼합 된 현실 환경을 구축할 때마다 광범위 한 지원을 구축 하는 것입니다.

## <a name="high-level-breakdown"></a>높은 수준의 분석

MRTK는 완전히 빠른 사용자 경험을 위한 도구 모음입니다. 또한 자체 런타임에 대 한 의견이 있는 응용 프로그램 프레임 워크, 확장 방법 및 구성 방법입니다.

상위 수준에서 MRTK는 다음과 같은 방법으로 세분화 될 수 있습니다.

![아키텍처 개요 다이어그램](../features/images/architecture/MRTK_Architecture.png)

MRTK에는 MRTK의 나머지 부분에 대 한 종속성이 거의 없는 또 다른 (빌드 도구, solvers, 오디오 영향 요인, 다듬기 유틸리티 및 선 렌더러) 집합도 포함 되어 있습니다.

아키텍처 설명서의 나머지 부분에서는 프레임 워크 및 런타임에서 시작 하 여 입력과 같이 더 흥미롭고 복잡 한 시스템으로 진행 됩니다. 아키텍처 개요를 계속 진행 하려면 목차를 참조 하세요.
