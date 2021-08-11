---
title: 입력 애니메이션 파일 형식
description: MRTK의 입력 애니메이션 이진 파일 형식 사양에 대 한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: bf77d976c9c894e6cf455a3a6b0e0c538912af2a9e8f8e2c7e847ba6e4657140
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222765"
---
# <a name="input-animation-file-format"></a>입력 애니메이션 파일 형식

## <a name="overall-structure"></a>전체 구조

입력 애니메이션 이진 파일은 64 비트 정수 매직 숫자로 시작 합니다. 이 숫자의 16 진수 표기법 값은 이며 `0x6a8faf6e0f9e42c6` 유효한 입력 애니메이션 파일을 식별 하는 데 사용할 수 있습니다.

다음 8 바이트는 파일의 주 버전 번호와 부 버전 번호를 선언 하는 두 개의 Int32 값입니다.

파일의 나머지 부분은 애니메이션 데이터에 의해 수행 되며 버전 번호 사이에서 변경 될 수 있습니다.

| 섹션 | 형식 |
|---------|------|
| 매직 넘버 | Int64 |
| 주 버전 번호 | Int32 |
| 부 버전 번호 | Int32 |
| 애니메이션 데이터 | _버전 섹션 참조_ |

## <a name="version-11"></a>버전 1.1

입력 애니메이션 데이터는 애니메이션에 카메라, 손 모양 및 눈에 맞는 데이터를 포함 하 고 그 다음에 애니메이션 곡선의 시퀀스를 포함할지 여부를 나타내는 세 개의 부울 값으로 구성 됩니다. 표시 되는 곡선은 이러한 부울 값에 따라 달라 집니다. 각 곡선의 키 프레임 수는 다를 수 있습니다.

| 섹션 | 형식 | 참고 |
|---------|------|------|
| 카메라 포즈 있음 | 부울 | |
| 직접 데이터 있음 | 부울 | |
| 아이 응시 있음| 부울 | |
| 카메라 | [포즈 곡선](#pose-curves) | 가 카메라 포즈 인 경우에만 |
| 왼쪽 추적 | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 직접 추적 권한 | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 손 집기 Left | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 손 집기 Right | [부울 곡선](#boolean-curve) | 가 손 데이터를 만족 하는 경우에만 |
| 왼쪽 조인트 | [조인트 포즈 곡선](#joint-pose-curves) | 가 손 데이터를 만족 하는 경우에만 |
| 직접 조인트 | [조인트 포즈 곡선](#joint-pose-curves) | 가 손 데이터를 만족 하는 경우에만 |
| 아이 응시 | [광선 곡선](#ray-curves)] | 이 true 인 경우에만 true |

## <a name="version-10"></a>버전 1.0

입력 애니메이션 데이터는 애니메이션 곡선의 시퀀스로 구성 됩니다. 애니메이션 곡선의 수와 의미가 고정 되어 있지만 각 곡선의 키 프레임 수는 다를 수 있습니다.

| 섹션 | 형식 |
|---------|------|
| 카메라 | [포즈 곡선](#pose-curves) |
| 왼쪽 추적 | [부울 곡선](#boolean-curve) |
| 직접 추적 권한 | [부울 곡선](#boolean-curve) |
| 손 집기 Left | [부울 곡선](#boolean-curve) |
| 손 집기 Right | [부울 곡선](#boolean-curve) |
| 왼쪽 조인트 | [조인트 포즈 곡선](#joint-pose-curves) |
| 직접 조인트 | [조인트 포즈 곡선](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>조인트 포즈 곡선

각 손에 대해 조인트 애니메이션 곡선의 시퀀스가 저장 됩니다. 조인트 수가 고정 되 고 각 조인트에 대해 포즈 곡선 집합이 저장 됩니다.

| 섹션 | 형식 |
|---------|------|
| 없음 | [포즈 곡선](#pose-curves) |
| 손목 | [포즈 곡선](#pose-curves) |
| Palm | [포즈 곡선](#pose-curves) |
| ThumbMetacarpalJoint | [포즈 곡선](#pose-curves) |
| ThumbProximalJoint | [포즈 곡선](#pose-curves) |
| ThumbDistalJoint | [포즈 곡선](#pose-curves) |
| ThumbTip | [포즈 곡선](#pose-curves) |
| IndexMetacarpal | [포즈 곡선](#pose-curves) |
| IndexKnuckle | [포즈 곡선](#pose-curves) |
| IndexMiddleJoint | [포즈 곡선](#pose-curves) |
| IndexDistalJoint | [자세 곡선](#pose-curves) |
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
| RingTip | [자세 곡선](#pose-curves) |
| PinkyMetacarpal | [자세 곡선](#pose-curves) |
| PinkyKnuckle | [자세 곡선](#pose-curves) |
| PinkyMiddleJoint | [자세 곡선](#pose-curves) |
| PinkyDistalJoint | [자세 곡선](#pose-curves) |
| PinkyTip | [자세 곡선](#pose-curves) |

### <a name="pose-curves"></a>자세 곡선

자세 곡선은 위치 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 회전 쿼터니언에 대해 4개의 애니메이션 곡선이 잇는 시퀀스입니다.

| 섹션 | 형식 |
|---------|------|
| 위치 X | [Float 곡선](#float-curve) |
| 위치 Y | [Float 곡선](#float-curve) |
| 위치 Z | [Float 곡선](#float-curve) |
| 회전 X | [Float 곡선](#float-curve) |
| 회전 Y | [Float 곡선](#float-curve) |
| 회전 Z | [Float 곡선](#float-curve) |
| 회전 W | [Float 곡선](#float-curve) |

### <a name="ray-curves"></a>광선 곡선

광선 곡선은 원점 벡터에 대한 3개의 애니메이션 곡선 시퀀스로, 방향 벡터에 대해 3개의 애니메이션 곡선이 잇는 시퀀스입니다.

| 섹션 | 형식 |
|---------|------|
| 원본 X | [Float 곡선](#float-curve) |
| 원본 Y | [Float 곡선](#float-curve) |
| 원본 Z | [Float 곡선](#float-curve) |
| Direction X | [Float 곡선](#float-curve) |
| Direction Y | [Float 곡선](#float-curve) |
| 방향 Z | [Float 곡선](#float-curve) |

### <a name="float-curve"></a>Float 곡선

부동 소수점 곡선은 가변 개수의 키 프레임이 있는 완전 3차원 곡선입니다. 각 키 프레임은 시간 및 곡선 값뿐만 아니라 각 키 프레임의 왼쪽과 오른쪽에 탄젠트 및 가중치를 저장합니다.

| 섹션 | 형식 |
|---------|------|
| 사전 래핑 모드 | Int32, [래핑 모드](#wrap-mode) |
| 사후 래핑 모드 | Int32, [래핑 모드](#wrap-mode) |
| 키 프레임 수 | Int32 |
| 키 프레임 | [Float 키 프레임](#float-keyframe) |

### <a name="float-keyframe"></a>Float 키 프레임

float 키 프레임은 탄젠트 및 가중치 값을 기본 시간 및 값과 함께 저장합니다.

| 섹션 | 형식 |
|---------|------|
| 시간 | Float32 |
| 값 | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [가중 모드](#weighted-mode) |

### <a name="boolean-curve"></a>부울 곡선

부울 곡선은 설정/해제 값의 단순 시퀀스입니다. 모든 키 프레임에서 곡선의 값이 즉시 대칭 이동 합니다.

| 섹션 | 형식 |
|---------|------|
| 래핑 전 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 줄 바꿈 모드 | Int32, [Wrap 모드](#wrap-mode) |
| 키 프레임 수 | Int32 |
| 키 프레임 | [부울 키 프레임](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>부울 키 프레임

부울 키프레임은 시간 및 값만 저장 합니다.

| 섹션 | 형식 |
|---------|------|
| 시간 | Float32 |
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
| 0 | None: 곡선 세그먼트를 계산할 때 inWeight 또는 outWeight를 모두 제외 합니다. |
| 1 | In: 이전 곡선 세그먼트를 계산할 때 inWeight를 포함 합니다. |
| 2 | Out: 다음 곡선 세그먼트를 계산할 때 outWeight를 포함 합니다. |
| 3 | Both: 곡선 세그먼트를 계산할 때 inWeight와 outWeight를 포함 합니다. |
