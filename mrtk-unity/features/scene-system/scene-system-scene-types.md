---
title: 장면 시스템 장면 유형
description: MRTK의 여러 장면 유형에 대 한 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144570"
---
# <a name="scene-types"></a>장면 유형

장면은 세 가지 형식으로 나뉘어 있으며 각 형식에는 다른 함수가 있습니다.

![계층의 장면 시스템](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>콘텐츠 장면

이는를 처리 하는 데 사용 하는 배경입니다. 모든 종류의 콘텐츠를 저장 하 고 모든 조합에서 로드 하거나 언로드할 수 있습니다.

콘텐츠 장면을 기본적으로 사용할 수 있습니다. 프로필의 배열에 포함 된 모든 장면을 `Content Scenes` 서비스에서 로드/언로드할 수 있습니다.

___

## <a name="manager-scenes"></a>관리자 장면

필수 MixedRealityToolkit 인스턴스가 있는 단일 장면. 이 장면은 처음 시작할 때 로드 되 고 앱의 수명 동안 로드 된 상태로 유지 됩니다. 또한 관리자 장면은 제거 되지 않아야 하는 다른 개체를 호스트할 수 있습니다. 이는 DontDestroyOnLoad에 대 한 기본 설정 대안입니다.

이 기능을 사용 하도록 설정 하려면 프로필을 체크 인하고 `Use Manager Scene` 장면 개체를 필드로 끕니다 `Manager Scene` .

___

## <a name="lighting-scenes"></a>조명 장면

조명 정보 및 조명 개체를 저장 하는 장면 집합입니다. 한 번에 하나만 로드할 수 있으며 부드러운 조명 전환을 위해 로드 하는 동안 해당 설정을 혼합할 수 있습니다.

Unity의 조명 설정-앰비언트 광원, skyboxes 등은 개별 장면에 연결 되 고 재정의 동작이 간단 하지 않으므로 추가 로드를 사용 하는 경우 관리 하기가 어려울 수 있습니다. 실제로는 자산이 런타임에 가져오지 않는 조명 조건에서 작성 될 때 혼동을 일으킬 수 있습니다.

![장면 시스템 조명 설정](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

장면 시스템은 조명 장면을 사용하여 편집 모드와 재생 모드 모두에서 로드되거나 활성 상태인 장면에 관계없이 이러한 설정이 일관되게 유지되도록 합니다.

이 기능을 사용하도록 설정하려면 프로필을 체크 `Use Lighting Scene` 인하고 배열을 채웁 수 `Lighting Scenes` 있습니다.

### <a name="cached-lighting-settings"></a>캐시된 조명 설정

프로필은 조명 장면에 보관된 조명 설정의 캐시된 복사본을 저장합니다. 조명 장면에서 이러한 설정이 변경되면 재생 모드에서 조명이 예상대로 표시되도록 캐시를 업데이트해야 합니다. 캐시된 설정이 만료된 것으로 의심되는 프로필에 경고가 표시됩니다. 클릭하면 `Update Cached Lighting Settings` 각 조명 장면을 로드하고, 설정을 추출한 다음, 프로필에 저장합니다.

![장면 시스템 캐시 조명 설정](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>편집기 동작

조명 장면을 사용할 경우의 이점 중 하나는 편집하는 동안 콘텐츠가 올바르게 켜져 있다는 것입니다. 이를 위해 장면 서비스는 항상 조명 장면을 로드하고 해당 장면의 조명 설정을 현재 활성 장면에 복사합니다.\*

장면 시스템의 [서비스 검사기](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 열어 로드되는 조명 장면을 변경할 수 있습니다. 편집 모드에서는 조명 장면 간에 즉시 전환할 수 있습니다. 재생 모드에서는 전환을 미리 볼 수 있습니다.

![장면 시스템 검사기](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**참고: 일반적으로 활성 장면에 따라 편집기에서 조명 설정이 결정됩니다. 그러나 활성 장면도 새로 만든 개체가 기본적으로 배치되고 조명 장면에 조명 구성 요소만 포함할 수 있으므로 이 기능을 사용하여 조명 설정을 적용하지 않도록 선택합니다. 대신 현재 조명 장면의 설정이 활성 장면의 설정에 자동으로 복사됩니다. 이렇게 하면 콘텐츠 장면의 조명 설정이 덮어쓰여집니다.*
