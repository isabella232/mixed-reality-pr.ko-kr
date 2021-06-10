---
title: Unity 패키지 관리자 사용
description: Unity 패키지 관리자에서 MRTK 사용
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK 패키지,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345076"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Mixed Reality Toolkit 및 Unity 패키지 관리자

2.5.0 버전부터, [혼합 현실 기능 도구](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)를 사용 하 여 Microsoft Mixed reality Toolkit은 unity 2019.4 이상 버전을 사용 하는 경우에는 UPM (Unity 패키지 관리자)와 통합 됩니다.

## <a name="using-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool 사용

[Mixed Reality 기능 도구 시작](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 에 설명 된 대로 [이 링크](https://aka.ms/MRFeatureTool)를 사용 하 여 도구를 다운로드할 수 있습니다.

> [!IMPORTANT]
> 프로젝트의 매니페스트에 `Microsoft Mixed Reality` 섹션에 항목이 있는 경우 `scopedRegistries` 제거 하는 것이 좋습니다.
>
> 구성 된 범위가 지정 된 레지스트리를 제거 하려면을 (를) 참조 하세요 `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![범위가 지정 된 레지스트리 제거](../features/images/packaging/RemoveScopedRegistry.png)

MRTK 패키지는 기능을 검색할 때 제목 아래에 나타납니다 `Mixed Reality Toolkit` .

![검색 기능](../features/images/packaging/DiscoverFeatures.png)

기능을 선택 하는 경우 필요한 종속성을 걱정 하지 않아도 되며, 도구가 자동으로 다운로드 되어 프로젝트에 통합 됩니다.

![필수 종속성](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Unity 패키지 관리자를 사용 하 여 혼합 현실 기능 관리

혼합 현실 도구 키트 패키지는 패키지 매니페스트에 추가 된 후 Unity 패키지 관리자 사용자 인터페이스를 사용 하 여 관리할 수 있습니다.

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Unity 패키지 관리자를 사용 하 여 혼합 현실 도구 키트 패키지를 제거 하는 경우 [앞에서 설명한 단계](#using-the-mixed-reality-feature-tool)를 사용 하 여 다시 추가 해야 합니다.

### <a name="using-mixed-reality-toolkit-examples"></a>Mixed Reality Toolkit 예 사용

자산 패키지 (. unitypackage) 파일을 사용 하는 경우와 달리 `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` 예제 장면 및 자산을 자동으로 가져오지 않습니다.

하나 이상의 예제를 활용 하려면 다음 단계를 사용 하세요.

1. Unity 편집기에서로 이동 합니다. `Window` > `Package Manager`
1. 패키지 목록에서 다음을 선택 합니다. `Mixed Reality Toolkit Examples`
1. 목록에서 원하는 샘플 찾기 `Samples`
1. `Import into Project`을 클릭합니다.

![샘플 가져오기](../features/images/packaging/MRTK_ExamplesUpm.png)

예제 패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.

> [!NOTE]
> 가져온 샘플을 업데이트 하면 해당 샘플과 연결 된 자산에 대 한 변경 내용이 모두 덮어쓰여집니다.

## <a name="see-also"></a>참고 항목

- [혼합 현실 도구 키트 패키지](../packages/mrtk-packages.md)