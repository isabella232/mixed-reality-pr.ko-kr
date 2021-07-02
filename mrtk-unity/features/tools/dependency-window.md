---
title: 종속성 창
description: MRTK의 종속성 창 사용에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176660"
---
# <a name="dependency-window"></a>종속성 창

Unity에서 사용 되는 자산 및 참조 하는 항목을 gleam 하는 것이 어려운 경우가 종종 있습니다. "장면에서 참조 찾기" 옵션은 현재 장면에만 관심이 있는 경우와 전체 Unity 프로젝트에 대 한 내용에 대해 잘 작동 하나요? 여기에서 **종속성 창** (asset/MRTK/Tools/DependencyWindow)이 유용할 수 있습니다.

종속성 창에는 자산이 서로를 참조 하 고 종속 되는 방식이 표시 됩니다. 종속성은 project YAML 파일 내의 guid를 구문 분석 하 여 계산 됩니다 (참고, 스크립트 종속성에 대 한 스크립트는 고려 되지 않음).

## <a name="usage"></a>사용

창을 열려면 **Mixed Reality**  >  **Toolkit**  >  **유틸리티**  >  **종속성 창** 을 선택 합니다. 그러면 창이 열리고 프로젝트의 종속성 그래프를 자동으로 빌드하기 시작 합니다. 종속성 그래프가 작성 되 면 프로젝트 탭에서 자산을 선택 하 여 해당 종속성을 검사할 수 있습니다.

![종속성 창](../images/dependency-window/MRTK_Dependency_Window.png)

창에는 현재 선택 된 자산이 종속 된 자산 목록과 해당 자산이 종속 된 자산의 계층적 목록이 표시 됩니다. 현재 선택 된 자산에 종속 되지 않는 경우 프로젝트에서 삭제 하는 것을 고려할 수 있습니다. 일부 자산은 셰이더와 같은 Api를 통해 프로그래밍 방식으로 로드 됩니다. Find ()는 종속성 추적기에 의해 catch 되지 않을 수도 있습니다.

이 창에는 다른 자산에서 참조 하지 않으며 삭제로 간주할 수 있는 모든 자산 목록만 표시 될 수도 있습니다.

![참조 되지 않은 자산을 보여 주는 종속성 창](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> 종속성 창이 사용 되는 동안 자산을 수정, 추가 또는 제거 하는 경우 가장 "최신" 결과에 대 한 종속성 그래프를 새로 고치는 것이 좋습니다.
