---
title: 플랫폼 기능 검색
description: MRTK에서 지원하는 다양한 기능에 대한 세부 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 기능,
ms.openlocfilehash: e6f5a70120b2634a4c8c75cdca3d8b369967c4b0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143863"
---
# <a name="detecting-platform-capabilities"></a>플랫폼 기능 검색

MRTK에 대한 일반적인 질문은 애플리케이션을 실행하는 데 사용되는 특정 디바이스(예: Microsoft HoloLens 2)를 파악하는 것입니다. 정확한 하드웨어를 식별하는 것은 다양한 플랫폼에서 어려울 수 있습니다. 대신 MRTK는 런타임에 특정 기능을 식별하는 방법을 제공합니다(예: 현재 디바이스 엔드포인트가 굴절된 손을 지원하는 경우).

## <a name="capabilities"></a>기능

Mixed Reality 도구 키트는 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 애플리케이션이 런타임에 쿼리할 수 있는 기능 집합을 정의하는 열거형을 제공합니다.

### <a name="input-system-capabilities"></a>입력 시스템 기능

기본 MRTK 입력 시스템은 다음 기능 쿼리를 지원합니다.

| 기능 | 설명 |
|---|---|
| ArticulatedHand | 굴절형 손 입력 |
| EyeTracking | 시선 응시 대상 지정 |
| GGVHand | 응시 제스처-음성 손 입력 |
| MotionController | 모션 컨트롤러 입력 |
| VoiceCommand | 앱 정의 키워드를 사용하는 음성 명령 |
| VoiceDictation | 음성 텍스트 받아쓰기 |

아래 예제 코드는 입력 시스템이 굴절된 손을 지원하는 데이터 공급자를 로드했는지 확인합니다.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>공간 인식 기능

기본 MRTK 공간 인식 시스템은 다음 기능 쿼리를 지원합니다.

| 기능 | 설명 |
|---|---|
| SpatialAwarenessMesh | 공간 메시 |
| SpatialAwarenessPlane | 공간 평면 |
| SpatialAwarenessPoint | 공간 지점 |

이 예제에서는 공간 인식 시스템이 공간 메시를 지원하는 데이터 공급자를 로드했는지 확인합니다.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>참고 항목

- [IMixedRealityCapabilityCheck API 설명서](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability 열거형 설명서](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
