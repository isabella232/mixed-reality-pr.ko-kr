---
title: 장면 시스템 콘텐츠 로드 중
description: MRTK를 통해 장면 시스템을 로드하는 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: df4437a0640637328c3f8f0d78be63a492d4bba15acb8a37bdf2dd3c32d89a59
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223044"
---
# <a name="scene-system-content-loading"></a>장면 시스템 콘텐츠 로드 중

모든 콘텐츠 로드 작업은 비동기적이며 기본적으로 모든 콘텐츠 로드는 가산적입니다. 관리자 및 조명 장면에는 콘텐츠 로드 작업의 영향을 받지 않습니다. 부하 진행률 및 장면 활성화 모니터링에 대한 자세한 내용은 [콘텐츠 로드 모니터링을 참조하세요.](scene-system-load-progress.md)

## <a name="loading-content"></a>콘텐츠 로드

콘텐츠 장면을 로드하려면 메서드를 사용합니다. `LoadContent`

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>단일 장면 로드

단일 장면 로드에 해당하는 는 선택적 인수를 통해 달성할 수 `mode` 있습니다. `LoadSceneMode.Single` 는 로드를 계속하기 전에 먼저 로드된 모든 콘텐츠 장면을 언로드합니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a>다음/이전 장면 로드

콘텐츠는 빌드 인덱스 순서대로 로드될 수 있습니다. 이는 사용자가 일련의 데모 장면을 하나씩 안내하는 애플리케이션을 소개하는 데 유용합니다.

![플레이어 설정에서 빌드의 현재 장면](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

next/prev 콘텐츠 로드는 기본적으로 LoadSceneMode.Single를 사용하여 이전 콘텐츠가 언로드되었는지 확인합니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

`PrevContentExists` 는 현재 로드된 가장 낮은 빌드 인덱스보다 낮은 빌드 인덱스 를 가진 콘텐츠 장면이 하나 이상 있는 경우 true를 반환합니다. `NextContentExists` 는 현재 로드된 가장 높은 빌드 인덱스보다 높은 빌드 인덱스 를 가진 콘텐츠 장면이 하나 이상 있는 경우 true를 반환합니다.

`wrap`인수가 true이면 콘텐츠가 첫 번째/마지막 빌드 인덱스로 다시 반복됩니다. 이렇게 하면 다음/이전 콘텐츠를 확인할 필요가 없습니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a>태그로 로드

![태그로 콘텐츠 장면 로드](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

콘텐츠 장면을 그룹으로 로드하는 것이 바람직한 경우가 있습니다. 예를 들어 환경의 단계는 여러 장면으로 구성될 수 있으며, 이 모든 단계는 작동하기 위해 동시에 로드되어야 합니다. 이를 용이하게 하기 위해 장면에 태그를 적용한 다음 로드하거나 해당 태그를 사용하여 언로드할 수 있습니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

태그로 로드하는 것은 스크립트를 수정하지 않고도 경험에서 요소를 통합/제거하려는 경우에도 유용할 수 있습니다. 예를 들어 다음 두 태그 집합을 사용하여 이 스크립트를 실행하면 다른 결과가 생성됩니다.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>콘텐츠 테스트

장면 이름 | 장면 태그 | 스크립트로 로드
---|---|---
DebugTerrainPhysics | 지형 | •
StructureTesting | 구조체 | •
VegetationTools | 식물 | •
Mountain | 지형 | •
Cabin | 구조체 | •
Trees | 식물 | •

### <a name="final-content"></a>최종 콘텐츠

장면 이름 | 장면 태그 | 스크립트로 로드
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
VegetationTools | DoNotInclude |
Mountain | 지형 | •
Cabin | 구조체 | •
Trees | 식물 | •

---

## <a name="editor-behavior"></a>편집기 동작

장면 시스템의 [서비스 검사기를](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용하여 편집기 및 재생 모드에서 이러한 모든 작업을 수행할 수 있습니다. 편집 모드에서는 장면 로드가 즉시 진행되지만 재생 모드에서는 로드 진행 상황을 관찰하고 [활성화 토큰을](scene-system-load-progress.md) 사용할 수 있습니다.

![콘텐츠 로드가 강조 표시된 검사기에서 장면 시스템](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
