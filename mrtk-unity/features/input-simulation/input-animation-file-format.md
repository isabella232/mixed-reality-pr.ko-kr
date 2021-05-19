---
title: 입력 애니메이션 파일 형식
description: MRTK의 입력 애니메이션 이진 파일 형식 사양에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145123"
---
# <a name="input-animation-binary-file-format-specification"></a>입력 애니메이션 이진 파일 형식 사양

## <a name="overall-structure"></a>전체 구조

입력 애니메이션 이진 파일은 64비트 정수 매직 넘버로 시작합니다. 16진수 표기에서 이 숫자의 값은 `0x6a8faf6e0f9e42c6` 이며 유효한 입력 애니메이션 파일을 식별하는 데 사용할 수 있습니다.

다음 8바이트는 파일의 주 버전 및 부 버전 번호를 선언하는 두 개의 Int32 값입니다.

파일의 나머지 부분은 버전 번호 간에 변경 될 수 있는 애니메이션 데이터에 의해 수행됩니다.

| 섹션 | 유형 |
|---------|------|
| 매직 넘버 | Int64 |
| 주 버전 번호 | Int32 |
| 부 버전 번호 | Int32 |
| 애니메이션 데이터 | _버전 섹션 참조_ |

## <a name="version-11"></a>버전 1.1

입력 애니메이션 데이터는 애니메이션에 카메라, 손 및 시선 응시 데이터와 애니메이션 곡선 시퀀스가 포함되는지 여부를 나타내는 세 개의 부울 값으로 구성됩니다. 존재하는 곡선은 이러한 부울의 값에 따라 달라집니다. 각 곡선에는 서로 다른 수의 키 프레임이 있을 수 있습니다.

| 섹션 | Type | 참고 |
|---------|------|------|
| 카메라 자세가 있습니다. | 부울 | |
| 손 데이터 사용 | 부울 | |
| 시선 응시| 부울 | |
| 카메라 | [자세 곡선](#pose-curves) | 카메라 자세가 true인 경우에만 |
| 왼쪽 추적 | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 직접 추적 권한 | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 손 집기 Left | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 손 집기 Right | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 왼쪽 조인트 | [조인트 포즈 곡선](#joint-pose-curves) | 가 손 데이터를 만족 하는 경우에만 |
| 직접 조인트 | [조인트 포즈 곡선](#joint-pose-curves) | 가 손 데이터를 만족 하는 경우에만 |
| 아이 응시 | [광선 곡선](#ray-curves)] | 시선 응시가 true인 경우에만 |

## <a name="version-10"></a>버전 1.0

입력 애니메이션 데이터는 애니메이션 곡선 시퀀스로 구성됩니다. 애니메이션 곡선의 수와 의미는 고정되어 있지만 각 곡선에는 서로 다른 수의 키 프레임이 있을 수 있습니다.

| 섹션 | 유형 |
|---------|------|
| 카메라 | [자세 곡선](#pose-curves) |
| 왼쪽에서 손 추적 | [부울 곡선](#boolean-curve) |
| 직접 추적 오른쪽 | [부울 곡선](#boolean-curve) |
| 왼쪽 손가락 모으기 | [부울 곡선](#boolean-curve) |
| 오른쪽 손가락 모으기 | [부울 곡선](#boolean-curve) |
| 왼쪽 손 조인트 | [공동 자세 곡선](#joint-pose-curves) |
| 손 조인트 오른쪽 | [공동 자세 곡선](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>공동 자세 곡선

각 손의 경우 일련의 조인 애니메이션 곡선이 저장됩니다. 조인 수가 고정되고 각 조인에 대해 자세 곡선 집합이 저장됩니다.

| 섹션 | 유형 |
|---------|------|
| 없음 | [자세 곡선](#pose-curves) |
| 손목 | [포즈 곡선](#pose-curves) |
| Palm | [포즈 곡선](#pose-curves) |
| ThumbMetacarpalJoint | [포즈 곡선](#pose-curves) |
| ThumbProximalJoint | [포즈 곡선](#pose-curves) |
| ThumbDistalJoint | [포즈 곡선](#pose-curves) |
| ThumbTip | [포즈 곡선](#pose-curves) |
| IndexMetacarpal | [포즈 곡선](#pose-curves) |
| IndexKnuckle | [포즈 곡선](#pose-curves) |
| IndexMiddleJoint | [포즈 곡선](#pose-curves) |
| IndexDistalJoint | [포즈 곡선](#pose-curves) |
| IndexTip | [자세 곡선](#pose-curves) |
| MiddleMetacarpal | [자세 곡선](#pose-curves) |
| MiddleKnuckle | [자세 곡선](#pose-curves) |
| MiddleMiddleJoint | [자세 곡선](#pose-curves) |
| MiddleDistalJoint | [자세 곡선](#pose-curves) |
| MiddleTip | [자세 곡선](#pose-curves) |
| RingMetacarpal | [자세 곡선](#pose-curves) |
| RingKnuckle | [자세 곡선](#pose-curves) |
| RingMiddleJoint | [자세 곡선](#pose-curves) |
| RingDistalJoint | [자세 곡선](#pose-curves) |
| RingTip | [포즈 곡선](#pose-curves) |
| PinkyMetacarpal | [포즈 곡선](#pose-curves) |
| PinkyKnuckle | [포즈 곡선](#pose-curves) |
| PinkyMiddleJoint | [포즈 곡선](#pose-curves) |
| PinkyDistalJoint | [포즈 곡선](#pose-curves) |
| PinkyTip | [포즈 곡선](#pose-curves) |

### <a name="pose-curves"></a>포즈 곡선

포즈 곡선은 회전 4 원수에 대 한 4 개의 애니메이션 곡선 뒤에 위치 벡터에 대 한 3 개의 애니메이션 곡선의 시퀀스입니다.

| 섹션 | 유형 |
|---------|------|
| X 위치 | [Float 곡선](#float-curve) |
| Y 위치 | [Float 곡선](#float-curve) |
| Z 위치 | [Float 곡선](#float-curve) |
| 회전 X | [Float 곡선](#float-curve) |
| 회전 Y | [Float 곡선](#float-curve) |
| 회전 Z | [Float 곡선](#float-curve) |
| 회전 W | [Float 곡선](#float-curve) |

### <a name="ray-curves"></a>광선 곡선

광선 곡선은 원점 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 방향 벡터에 대해 3개의 애니메이션 곡선이 잇는 시퀀스입니다.

| 섹션 | 유형 |
|---------|------|
| 원본 X | [Float 곡선](#float-curve) |
| 원본 Y | [Float 곡선](#float-curve) |
| 원본 Z | [Float 곡선](#float-curve) |
| Direction X | [Float 곡선](#float-curve) |
| Direction Y | [Float 곡선](#float-curve) |
| 방향 Z | [Float 곡선](#float-curve) |

### <a name="float-curve"></a>Float 곡선

부동 소수점 곡선은 여러 개의 키 프레임을 사용 하는 완벽 한 베 지 어 곡선입니다. 각 키프레임에는 시간과 곡선 값 뿐만 아니라 각 키 프레임의 왼쪽과 오른쪽에 접선 및 가중치가 저장 됩니다.

| 섹션 | 유형 |
|---------|------|
| 래핑 전 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 줄 바꿈 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 키 프레임 수 | Int32 |
| 키 프레임 | [Float 키 프레임](#float-keyframe) |

### <a name="float-keyframe"></a>Float 키 프레임

Float 키프레임은 기본 시간 및 값과 함께 탄젠트 및 가중치 값을 저장 합니다.

| 섹션 | 유형 |
|---------|------|
| Time | Float32 |
| 값 | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [가중치가 적용 모드](#weighted-mode) |

### <a name="boolean-curve"></a>부울 곡선

부울 곡선은 설정/해제 값의 단순 시퀀스입니다. 모든 키 프레임에서 곡선의 값이 즉시 대칭 이동 합니다.

| 섹션 | 유형 |
|---------|------|
| 래핑 전 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 줄 바꿈 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 키 프레임 수 | Int32 |
| 키 프레임 | [부울 키 프레임](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>부울 키 프레임

부울 키프레임은 시간 및 값만 저장 합니다.

| 섹션 | 유형 |
|---------|------|
| Time | Float32 |
| 값 | Float32 |

### <a name="wrap-mode"></a>줄 바꿈 모드

사전 및 사후 줄 바꿈 모드의 의미 체계는 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 정의를 따릅니다. 다음 비트의 조합입니다.

| 값 | 의미 |
|-------|---------|
| 0 | 기본값: 높게 설정 된 기본 반복 모드를 읽습니다. |
| 1 | 한 번: 시간이 애니메이션 클립의 끝에 도달 하면 클립이 자동으로 재생을 중지 하 고 시간이 클립의 시작 부분으로 다시 설정 됩니다. |
| 2 | Loop: 시간이 애니메이션 클립의 끝에 도달 하면 시작 시 시간이 계속 됩니다. |
| 4 | PingPong: 시간이 애니메이션 클립의 끝에 도달 하면 time은 시작과 끝 사이에 ping를 다시 ping 합니다. |
| 8 | ClampForever: 애니메이션을 재생 합니다. 끝에 도달 하면 마지막 프레임을 계속 재생 하 고 재생을 중지 하지 않습니다. |

### <a name="weighted-mode"></a>가 중 모드

가중치가 적용 되는 모드의 의미 체계는 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 정의를 따릅니다.

| 값 | 의미 |
|-------|---------|
| 0 | 없음: 곡선 세그먼트를 계산할 때 inWeight 또는 outWeight를 모두 제외합니다. |
| 1 | In: 이전 곡선 세그먼트를 계산할 때 inWeight를 포함합니다. |
| 2 | Out: 다음 곡선 세그먼트를 계산할 때 outWeight를 포함합니다. |
| 3 | 둘 다: 곡선 세그먼트를 계산할 때 inWeight 및 outWeight를 포함합니다. |
