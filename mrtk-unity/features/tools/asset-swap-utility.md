---
title: 자산 교환 유틸리티
description: Unity 용 MRTK에서 asset swap 유틸리티를 사용 하는 방법에 대 한 설명서입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk
ms.openlocfilehash: 3322087f9027f46b39be07f5368cd8ae4ca875f206984fb823f9b1c8590f86f6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196276"
---
# <a name="asset-swap-utility"></a>자산 교환 유틸리티

찾기 및 바꾸기는 텍스트 및 콘텐츠 생성 도구에서 작업할 때 사용 됩니다. Unity 장면 내에서 많은 자산을 교환 해야 하는 경우이는 [Assetswaputility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) 인 [tabletableobject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 및 editor가 손 모양으로 할 수 있는 위치입니다. 유틸리티는 패키지에 포함 되어 `Microsoft.MixedReality.Toolkit.Unity.Tools` 있습니다.

은 `AssetSwapUtility` 모든 찾기 및 바꾸기 작업을 Tritableobject로 저장 하 여 앞뒤로 교환 하거나 나중에 사용할 수 있도록 스왑 "테마"를 저장 합니다.

## <a name="swapping-assets"></a>자산 교환

을 만들면 자산을 쉽게 교체할 수 있습니다 `AssetSwapCollection` . 장면에서 두 개의 파란 구를 사용 하 여 두 개의 빨간색 큐브를 바꿔 사용 하는 방법을 살펴보겠습니다. 먼저 기본 Unity 큐브와 재질을 사용 하는 두 개의 빨간색 큐브를 장면에 추가 `MRTK_Standard_Red` 합니다.

`AssetSwapCollection`을 만들려면 **혼합 현실 Toolkit > 유틸리티 > 자산 교환 컬렉션 만들기** 로 이동 합니다. 선택한을 사용 하 여 `AssetSwapCollection` 아래 이미지에 표시 된 대로 속성을 입력 합니다.

![Unity 편집기의 자산 교환 컬렉션](images/asset-swap-img-01.png)

그런 다음 "선택한 테마" 드롭다운에서 "파란색 구"를 선택 하 고 "적용"을 누릅니다. 장면 내의 모든 빨간색 큐브는 파란색 구로 바꾸어야 합니다.

![선택한 테마가 강조 표시 된 Unity 편집기의 자산 교환 컬렉션](images/asset-swap-img-02.png)

이 예제에서는 전체 장면 바꾸기를 수행 했지만 "선택 모드"를 변경 하 여 장면의 일부를 바꿀 수 있습니다. "선택한 테마" 드롭다운에서 "Red 큐브"를 선택 하 고 "적용"을 다시 선택 하 여 빨간색 큐브로 다시 바꿀 수도 있습니다.

> [!NOTE]
> 오디오 파일, 글꼴, prefabs 등의 자산 유형을 교환할 수 있습니다. 는 `AssetSwapUtility` 비슷한 형식으로 스와핑 되도록 몇 가지 온전성 검사를 수행 합니다.
