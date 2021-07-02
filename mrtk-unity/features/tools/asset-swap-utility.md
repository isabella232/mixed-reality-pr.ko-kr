---
title: 자산 교환 유틸리티
description: Unity용 MRTK에서 자산 교환 유틸리티 사용에 대한 설명서입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176160"
---
# <a name="asset-swap-utility"></a>자산 교환 유틸리티

찾기 및 바꾸기는 텍스트 및 콘텐츠 만들기 도구에서 작업할 때 유비쿼터스입니다. Unity 장면 내에서 많은 자산을 교환해야 하는 경우 [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject와](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 편집기가 도움을 줄 수 있습니다. 유틸리티는 패키지에 포함되어 `Microsoft.MixedReality.Toolkit.Unity.Tools` 있습니다.

는 `AssetSwapUtility` 모든 찾기 및 바꾸기 작업을 ScriptableObject로 저장하므로 나중에 사용할 수 있도록 앞뒤로 교환하거나 교환 "테마"를 저장하는 것이 매우 중요합니다.

## <a name="swapping-assets"></a>자산 교환

을 만든 후에는 자산을 쉽게 교환할 수 `AssetSwapCollection` 있습니다. 장면에서 두 개의 빨간색 큐브를 두 개의 파란색 구로 교환하여 사용하는 것을 보여 봅시다. 먼저 기본 Unity 큐브와 재질을 사용하는 두 개의 빨간색 큐브를 장면에 `MRTK_Standard_Red` 추가합니다.

를 만들려면 `AssetSwapCollection` Mixed Reality Toolkit > 유틸리티 > Asset Swap Collection **만들기로** 이동합니다. 선택한 를 통해 `AssetSwapCollection` 아래 이미지와 같이 속성을 채웁니다.

![Unity 편집기에서 자산 교환 컬렉션](images/asset-swap-img-01.png)

다음으로"선택한 테마" 드롭다운에서 "Blue Spheres"를 선택하고 "적용"을 적중합니다. 장면 내의 모든 빨간색 큐브는 파란색 구로 대체해야 합니다.

![선택한 테마가 강조 표시된 Unity 편집기에서 자산 교환 컬렉션](images/asset-swap-img-02.png)

이 예제에서는 전체 장면 바꾸기를 수행했지만 "선택 모드"를 변경하여 장면의 일부를 바꿀 수 있습니다. "선택한 테마" 드롭다운에서 "빨간색 큐브"를 선택하고 "적용"을 다시 하여 빨간색 큐브로 다시 바꿀 수도 있습니다.

> [!NOTE]
> 오디오 파일, 글꼴, 프리팹 등과 같은 자산 형식을 교환할 수 있습니다. `AssetSwapUtility` 는 몇 가지 온전성 검사를 수행하여 유사한 형식으로 교환하는지 확인합니다.
