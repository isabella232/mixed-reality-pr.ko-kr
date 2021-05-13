---
title: DetectingPlatformCapabilities
description: MRTK에서 지원하는 다양한 기능에 대한 세부 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 기능,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852439"
---
# <a name="detecting-platform-capabilities"></a>플랫폼 기능 검색

MRTK에 대한 일반적인 질문은 애플리케이션을 실행하는 데 사용되는 특정 디바이스(예: Microsoft HoloLens 2)를 아는 것과 관련이 있습니다. 정확한 하드웨어를 식별하는 것은 다양한 플랫폼에서 어려울 수 있습니다. 대신 MRTK는 런타임에 특정 기능을 식별하는 방법을 제공합니다(예: 현재 디바이스 엔드포인트가 굴절된 손을 지원하는 경우).

## <a name="capabilities"></a>기능

Mixed Reality 도구 키트는 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 애플리케이션이 런타임에 쿼리할 수 있는 기능 집합을 정의하는 열거형을 제공합니다.

### <a name="input-system-capabilities"></a>입력 시스템 기능

기본 MRTK 입력 시스템은 다음 기능 쿼리를 지원합니다.

| 기능 | Description |
|---|---|
| ArticulatedHand | 굴절형 손 입력 |
| EyeTracking | 시선 응시 대상 지정 |
| GGVHand | 응시 제스처-음성 손 입력 |
| MotionController | 모션 컨트롤러 입력 |
| VoiceCommand | 앱 정의 키워드를 사용하는 음성 명령 |
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
