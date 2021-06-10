---
title: 마이그레이션 창
description: MRTK에서 업데이트로 마이그레이션하는 방법에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647120"
---
# <a name="migration-window"></a>마이그레이션 기간

MRTK가 변경되면 일부 구성 요소가 더 이상 사용되지 않을 수 있으며 교체가 도입될 예정입니다.
마이그레이션 기간은 사용자가 사용되지 않는 구성 요소의 하위 집합을 새 대체 항목으로 자동으로 마이그레이션하는 데 도움이 되는 도구입니다.

![마이그레이션 기간](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>사용

창을 열려면 **도구 키트** 유틸리티 마이그레이션 창 Mixed Reality  >    >    >  선택합니다. 마이그레이션 창이 열리면 마이그레이션 처리기의 구성 요소별 구현을 선택하여 선택 모드 탐색 탭을 사용하도록 설정할 수 있습니다.  

![마이그레이션 선택 모드](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>개체 모드

개체 탭을 선택하면 사용자가 마이그레이션할 프로젝트 폴더에서 현재 열려 있는 장면 또는 프리팹에서 Game 개체를 끌어서 놓을 수 있는 필드 개체를 사용할 수 있습니다.
나열된 개체의 오른쪽에 표시되는 *제거(-)* 단추를 누르면 선택 목록에서 개체가 제거됩니다.

원하는 모든 개체가 목록에 있으면 *마이그레이션* 단추를 누르면 선택한 마이그레이션 처리기 구현에 필요한 변경 내용이 구현과 일치하는 선택 항목의 모든 구성 요소에 적용됩니다.

![선택 마이그레이션](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>장면 모드

사용자가 마이그레이션할 개체가 포함된 장면 자산을 끌어서 놓을 수 있습니다.

![마이그레이션 장면 선택](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>프로젝트 모드

*마이그레이션* 단추를 누르면 프로젝트의 모든 프리팹 및 장면에 대한 마이그레이션 처리기 구현의 대상이 지정된 구성 요소가 업데이트됩니다.

![전체 프로젝트 마이그레이션](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>참조

- [이전 버전에서 업데이트](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality Toolkit 릴리스](../../release-notes/mrtk-26-release-notes.md)
- [MRTK 로드맵](../../roadmap.md)
