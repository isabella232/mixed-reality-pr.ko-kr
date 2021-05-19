---
title: 경계 시각화 구성
description: MRTK에서 경계 시스템을 구성하는 세부 정보
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144498"
---
# <a name="configuring-the-boundary-visualization"></a>경계 시각화 구성

*경계 시각화 프로필은 경계* 시스템에 대한 시각적 개체 및 기타 관련 매개 변수를 구성하기 위한 옵션을 제공합니다. 경계 시각화는 장면의 Mixed Reality Playspace 개체에 연결되고 사용자와 원격 전송됩니다.

## <a name="general-settings"></a>일반 설정

![경계 시각화 일반 설정](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>경계 높이

경계 높이는 경계 상한이 렌더링되어야 하는 바닥 평면 위의 거리를 나타냅니다. 기본값은 3미터입니다.

## <a name="floor-settings"></a>바닥 설정

![경계 시각화 바닥 설정](../images/boundary/BoundaryVisualizationFloorSettings.png)

**표시**

평면을 만들고 장면에 추가할지 여부를 나타냅니다. 기본값은 true입니다.

**재질**

평면을 만들 때 사용해야 하는 재질을 나타냅니다.

**규모**

만들 평면의 크기(미터)를 나타냅니다. 기본 배율 3 미터 x 3 미터 제곱입니다.

**물리학 계층**

평면을 설정해야 하는 계층입니다. 기본값은 *기본* 계층입니다.

## <a name="play-area-settings"></a>재생 영역 설정

![경계 시각화 재생 영역 설정](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**표시**

재생 영역 사각형을 만들고 장면에 추가할지 여부를 나타냅니다. 기본값은 true입니다.

**재질**

재생 영역 개체를 만들 때 사용 해야 하는 자료를 나타냅니다.

**물리 계층**

재생 영역을 설정 해야 하는 계층입니다. 기본값은 *Raycast 계층 무시* 계층입니다.

## <a name="tracked-area-settings"></a>추적 영역 설정

![경계 시각화 추적 영역 설정](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**표시**

추적 영역의 개요를 만들어 장면에 추가할지 여부를 나타냅니다. 기본값은 true입니다.

**재질**

추적 된 영역 개요를 만들 때 사용 해야 하는 자료를 나타냅니다.

**물리 계층**

추적 된 영역을 설정할 계층입니다. 기본값은 *Raycast 계층 무시* 계층입니다.

## <a name="boundary-wall-settings"></a>경계 벽 설정

![경계 시각화 경계 벽 설정](../images/boundary/BoundaryVisualizationWallSettings.png)

**표시**

경계 벽 평면을 만들고 장면에 추가할지 여부를 나타냅니다. 기본값은 false입니다.

**재질**

경계 벽 평면을 만들 때 사용 해야 하는 재질을 나타냅니다.

**물리 계층**

경계 벽을 설정 해야 하는 계층입니다. 기본값은 *Raycast 계층 무시* 계층입니다.

> [!NOTE]
> 경계 벽 구성 요소를 *Raycast 무시* 이외의 물리 계층으로 설정 하면 사용자가 장면 내의 개체와 상호 작용 하지 못할 수 있습니다.

## <a name="boundary-ceiling-settings"></a>경계 상한 설정

![경계 시각화 경계 상한 설정](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**표시**

경계 최대 평면을 만들어 장면에 추가할지 여부를 나타냅니다. 기본값은 false입니다.

**재질**

경계 상한 평면을 만들 때 사용해야 하는 재질을 나타냅니다.

**물리학 계층**

경계 벽이 설정되어야 하는 계층입니다. 기본값은 *Raycast 무시* 계층입니다.

> [!NOTE]
> 경계 최대값 구성 요소를 *Raycast 무시* 이외의 물리학 계층으로 설정하면 사용자가 장면 내의 개체와 상호 작용하지 못할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [경계 API 설명서](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [경계 시스템](boundary-system-getting-started.md)
