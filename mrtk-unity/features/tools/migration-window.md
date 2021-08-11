---
title: 마이그레이션 기간
description: MRTK의 업데이트로 마이그레이션하는 방법에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 9e657e0b90f8087670b72c993ab1dcf78ae9e6680873139c6867d7c551a41895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220051"
---
# <a name="migration-window"></a>마이그레이션 기간

MRTK가 변경 되 면 일부 구성 요소가 더 이상 사용 되지 않을 수 있으며 대체가 도입 됩니다.
마이그레이션 창은 사용자가 더 이상 사용 되지 않는 구성 요소의 하위 집합을 새 대체 항목으로 자동으로 마이그레이션하는 데 도움이 되는 도구입니다.

![마이그레이션 기간](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>사용량

창을 열려면 **Mixed Reality**  >  **Toolkit**  >  **유틸리티**  >  **마이그레이션 창** 을 선택 합니다. 마이그레이션 창이 열리면 마이그레이션 처리기의 구성 요소별 구현을 선택 하 여 선택 모드 탐색 탭을 사용 하도록 설정할 수 있습니다.  

![마이그레이션 선택 모드](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>개체 모드

개체 탭을 선택 하면 개체 필드에서 사용자가 현재 열려 있는 장면 또는 prefabs 프로젝트 폴더에 있는 게임 개체를 끌어서 놓을 수 있습니다.
나열 된 개체의 오른쪽에 표시 된 제거 *(-)* 단추를 누르면 선택 목록에서 해당 개체가 제거 됩니다.

원하는 모든 개체가 목록에 있으면 *마이그레이션* 단추를 누르면 선택한 마이그레이션 처리기 구현에 필요한 변경 내용이 구현에 일치 하는 선택 항목의 모든 구성 요소에 적용 됩니다.

![선택 마이그레이션](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>장면 모드

사용자가 마이그레이션할 개체가 포함 된 장면 자산을 끌어서 놓을 수 있도록 허용 합니다.

![마이그레이션에 대 한 장면 선택](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project 모드

*마이그레이션 단추를* 누르면 마이그레이션 처리기 구현에서 대상으로 지정 된 구성 요소가 프로젝트의 모든 prefabs 및 장면에 대해 업데이트 됩니다.

![전체 프로젝트 마이그레이션](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>추가 정보

- [이전 버전에서 업데이트](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality Toolkit 릴리스](../../release-notes/mrtk-26-release-notes.md)
- [MRTK 로드맵](../../roadmap.md)
