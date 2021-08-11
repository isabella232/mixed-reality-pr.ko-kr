---
title: Unity 패키지 관리자 사용
description: Unity 패키지 관리자 MRTK 사용
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK 패키지,
ms.openlocfilehash: fb96a910b86e8ec9f6d73b8239e0ae008ea021c65f2c52edc613d2fe02719e58
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194469"
---
# <a name="using-the-unity-package-manager"></a>Unity 패키지 관리자 사용

버전 2.5.0부터는 [Mixed Reality 기능 도구를](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)사용하여 Microsoft Mixed Reality Toolkit Unity 2019.4 이상 버전을 사용하는 경우 UNITY 패키지 관리자(UPM)와 통합됩니다.

## <a name="using-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool 사용

Mixed Reality 기능 [도구 시작에서](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 설명한 대로 [이 링크를](https://aka.ms/MRFeatureTool)사용하여 도구를 다운로드할 수 있습니다.

> [!IMPORTANT]
> 프로젝트의 매니페스트에 `Microsoft Mixed Reality` 섹션에 항목이 있는 경우 `scopedRegistries` 제거하는 것이 좋습니다.
>
> 구성된 범위의 레지스트리를 제거하려면 로 `Edit`  >  `Project Settings`  >  `Package Manager` 이동하세요.
>
> ![범위가 있는 레지스트리 제거](../features/images/packaging/RemoveScopedRegistry.png)

기능을 검색할 때 MRTK 패키지가 제목 아래에 `Mixed Reality Toolkit` 표시됩니다.

![기능 검색](../features/images/packaging/DiscoverFeatures.png)

기능을 선택할 때 필수 의존성과 관련될 필요가 없습니다. 도구는 자동으로 다운로드하여 프로젝트에 통합합니다.

![필수 종속성](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Unity 패키지 관리자 Mixed Reality 기능 관리

Mixed Reality Toolkit 패키지가 패키지 매니페스트에 추가되면 Unity 패키지 관리자 사용자 인터페이스를 사용하여 관리될 수 있습니다.

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Unity 패키지 관리자 사용하여 Mixed Reality Toolkit 패키지를 제거한 경우 [이전에 설명한 단계를](#using-the-mixed-reality-feature-tool)사용하여 다시 추가해야 합니다.

### <a name="using-mixed-reality-toolkit-examples"></a>Mixed Reality Toolkit 예제 사용

자산 패키지(.unitypackage) 파일을 사용하는 경우와 달리 및 는 `com.microsoft.mixedreality.toolkit.examples` 예제 장면 및 자산을 자동으로 `com.microsoft.mixedreality.toolkit.handphysicsservice` 가져오지 않습니다.

하나 이상의 예제를 활용하려면 다음 단계를 사용하세요.

1. Unity 편집기에서 으로 이동합니다. `Window` > `Package Manager`
1. 패키지 목록에서 를 선택합니다. `Mixed Reality Toolkit Examples`
1. 목록에서 원하는 샘플을 찾습니다. `Samples`
1. `Import into Project`을 클릭합니다.

![샘플 가져오기](../features/images/packaging/MRTK_ExamplesUpm.png)

예제 패키지가 업데이트되면 Unity는 가져온 샘플을 업데이트하는 옵션을 제공합니다.

> [!NOTE]
> 가져온 샘플을 업데이트하면 해당 샘플 및 관련 자산에 대해 변경된 내용을 덮어쓰게 됩니다.

## <a name="see-also"></a>참고 항목

- [패키지 Mixed Reality Toolkit](../packages/mrtk-packages.md)
