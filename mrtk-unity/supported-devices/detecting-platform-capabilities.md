---
title: 플랫폼 기능 검색
description: MRTK가 지 원하는 다양 한 기능에 대 한 세부 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 기능,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175518"
---
# <a name="detecting-platform-capabilities"></a>플랫폼 기능 검색

mrtk에 대 한 일반적인 질문은 응용 프로그램을 실행 하는 데 사용 되는 특정 장치 (예: Microsoft HoloLens 2)를 파악 하는 것입니다. 정확한 하드웨어를 식별 하는 것은 다양 한 플랫폼에서 어려울 수 있습니다. 대신, MRTK는 런타임에 특정 기능을 식별 하는 방법을 제공 합니다 (예: 현재 장치 끝점이 트레일러 식을 지 원하는 경우).

## <a name="capabilities"></a>기능

혼합 현실 Toolkit는 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 응용 프로그램이 런타임에 쿼리할 수 있는 기능 집합을 정의 하는 열거형을 제공 합니다.

### <a name="input-system-capabilities"></a>입력 시스템 기능

기본 MRTK 입력 시스템은 다음 기능에 대 한 쿼리를 지원 합니다.

| 기능 | Description |
|---|---|
| ArticulatedHand | 트레일러 식 입력 |
| EyeTracking | 아이 응시 대상 |
| GGVHand | 응시-제스처-음성 입력 |
| MotionController | 동작 컨트롤러 입력 |
| VoiceCommand | 앱에서 정의한 키워드를 사용 하는 음성 명령 |
| VoiceDictation | 음성 텍스트 받아쓰기 |

아래 예제 코드에서는 입력 시스템에서 트레일러 식에 대 한 지원을 포함 하는 데이터 공급자를 로드 했는지 확인 합니다.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>공간 인식 기능

기본 MRTK 공간 인식 시스템은 다음 기능에 대 한 쿼리를 지원 합니다.

| 기능 | Description |
|---|---|
| SpatialAwarenessMesh | 공간 메시 |
| SpatialAwarenessPlane | 공간 평면 |
| SpatialAwarenessPoint | 공간 점수 |

이 예제에서는 공간 인식 시스템이 공간 메시를 지 원하는 데이터 공급자를 로드 했는지 확인 합니다.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>참조

- [IMixedRealityCapabilityCheck API 설명서](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability enum 설명서](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
