---
title: 장면 시스템 장면 유형
description: MRTK의 다양한 장면 유형에 대한 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: be34110c693c749535f6bfcd0411ecbd0bafc3bb48ab2392b3635c2e86a4dfb1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203333"
---
# <a name="scene-types"></a>장면 유형

장면에는 세 가지 형식으로 나뉘어져 있으며, 각 형식에는 다른 함수가 있습니다.

![계층 구조의 장면 시스템](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>콘텐츠 장면

다음은 처리하는 데 익숙한 장면입니다. 모든 종류의 콘텐츠를 저장할 수 있으며 어떤 조합으로든 로드하거나 언로드할 수 있습니다.

콘텐츠 씬은 기본적으로 사용하도록 설정됩니다. 프로필의 배열에 포함된 모든 장면을 `Content Scenes` 서비스에서 로드/언로드할 수 있습니다.

___

## <a name="manager-scenes"></a>관리자 장면

필요한 MixedRealityToolkit 인스턴스가 있는 단일 장면입니다. 이 장면은 시작 시 먼저 로드되며 앱의 수명 동안 로드된 상태로 유지됩니다. 또한 관리자 장면에서는 절대 소멸해서는 안 되는 다른 개체를 호스트할 수 있습니다. DontDestroyOnLoad 대신 사용할 수 있습니다.

이 기능을 사용하도록 설정하려면 프로필을 체크 `Use Manager Scene` 인하고 장면 개체를 필드로 끌어 `Manager Scene` 줍니다.

___

## <a name="lighting-scenes"></a>조명 장면

조명 정보 및 조명 개체를 저장하는 장면 세트입니다. 한 번에 하나만 로드할 수 있으며, 부드러운 조명 전환을 위해 로드 중에 해당 설정을 혼합할 수 있습니다.

Unity의 조명 설정(앰비언트 조명, skyboxes 등)은 개별 장면에 연결되고 동작을 재정의하는 것이 간단하지 않으므로 가감 로드를 사용할 때 관리하기 어려울 수 있습니다. 실제로 이로 인해 런타임에 얻을 수 없는 조명 조건에서 자산을 작성할 때 혼동이 발생할 수 있습니다.

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
