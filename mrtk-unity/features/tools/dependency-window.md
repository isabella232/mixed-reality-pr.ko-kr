---
title: 종속성 창
description: MRTK의 종속성 기간 사용에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647029"
---
# <a name="dependency-window"></a>종속성 창

Unity에서는 어떤 자산이 사용되고 있는지, 어떤 자산이 참조되고 있는지를 익히는 것이 어려운 경우가 많습니다. "장면에서 참조 찾기" 옵션은 현재 장면에만 관심이 있을 때 잘 작동하지만 전체 Unity 프로젝트는 어떤가요? 이 경우 **종속성** 창(자산/MRTK/도구/DependencyWindow)이 유용할 수 있습니다.

종속성 창에는 자산이 서로 참조하고 종속하는 방식이 표시됩니다. 프로젝트 YAML 파일 내에서 GUID를 구문 분석하여 Dependencies를 계산합니다(참고: 스크립트-스크립트 의존성 고려 안 함).

## <a name="usage"></a>사용

창을 열려면 **Mixed Reality**  >  **도구 키트**  >  **유틸리티**  >  **종속성 창을** 선택하면 창이 열리고 프로젝트의 종속성 그래프 빌드가 자동으로 시작됩니다. 종속성 그래프가 빌드되면 프로젝트 탭에서 자산을 선택하여 종속성을 검사할 수 있습니다.

![종속성 창](../images/dependency-window/MRTK_Dependency_Window.png)

창에는 현재 선택한 자산이 의존하는 자산 목록과 해당 자산에 의존하는 자산의 계층적 목록이 표시됩니다. 현재 선택한 자산에 종속되지 않는 경우 프로젝트에서 삭제하는 것을 고려할 수 있습니다(일부 자산은 Shader.Find()와 같은 API를 통해 프로그래밍 방식으로 로드되고 종속성 추적기에서 포착되지 않을 수 있음).

창에는 다른 자산에서 참조하지 않고 삭제로 간주될 수 있는 모든 자산의 목록만 표시될 수도 있습니다.

![유추되지 않은 자산을 표시하는 종속성 창](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> 종속성 창을 사용하는 동안 자산을 수정, 추가 또는 제거하는 경우 가장 "최신" 결과에 대한 종속성 그래프를 새로 고치는 것이 좋습니다.
