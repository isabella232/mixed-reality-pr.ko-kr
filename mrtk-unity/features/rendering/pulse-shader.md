---
title: 펄스 셰이더
description: MRTK의 펄스 셰이더에 대 한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176311"
---
# <a name="pulse-shader"></a>펄스 셰이더

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

펄스 셰이더를 사용 하 여 표면 재구성, 트레일러 모양 메쉬 또는 기타 메시에 대 한 시각적 펄스 효과에 애니메이션 효과를 적용 합니다.

## <a name="shader-and-material"></a>셰이더 및 재질

다음 자료에서는 **SR_Triangles** 셰이더를 사용 합니다. 채우기 색, 선 색 및 펄스 색과 같은 다양 한 옵션을 구성할 수 있습니다.

- **MRTK_Pulse_SpatialMeshBlue입니다.** 
- **MRTK_Pulse_SpatialMeshPurple입니다.** 
- **MRTK_Pulse_ArticulatedHandMeshBlue입니다.** 
- **MRTK_Pulse_ArticulatedHandMeshPurple입니다.** 

## <a name="prerequisites"></a>필수 조건

공간 메시 예의 경우 MRTK 설정-> 공간 인식-> 표시 설정 표시 되는 재질에 MRTK_Pulse_ArticulatedHandMeshBlue 또는 MRTK_Pulse_ArticulatedHandMeshPurple가 할당 되어 있는지 확인 합니다.

손 모양 메시 예제에서는 MRTK_Pulse_SpatialMeshBlue prefab 또는 MRTK_Pulse_SpatialMeshPurple이에 할당 되어 있는지 확인 합니다 .이는 MRTK 설정 > 입력 > 손 추적-> 손 모양 Prefab에 할당 되어야 합니다.

## <a name="how-it-works"></a>작동 방식

손 모양 메시 셰이더는 UVs를 사용 하 여 핸드 메시를 따라 펄스를 매핑하고 손목을 페이드 아웃 합니다. 표면 재구성 셰이더는 꼭 짓 점 위치를 사용 하 여 펄스를 매핑합니다.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>공간 메시 예-PulseShaderSpatialMeshExample

HoloLens 2 셸 환경과 마찬가지로, 손 광선을 사용 하 여 마우스를 가리키고 공기 탭을 사용 하 여 공간 메시에 대해 깜박이는 효과를 생성할 수 있습니다. 예제 장면에는 Unity 게임 모드의 테스트 공간 메시 데이터 인 ExampleSpatialMesh 개체가 포함 되어 있습니다. 이 개체는 장치에서 사용 하지 않도록 설정 되 고 숨겨집니다.

**PulseShaderSpatialMeshHandler** 스크립트는가 true 인 경우 적중 지점 위치의 공간 메시에 대 한 펄스 효과를 생성 합니다 `PulseOnSelect` . `Auto Pulse`애니메이션을 반복 하기 위해 재질 자체에서 속성을 true로 설정할 수도 있습니다.  예제 장면에서이 스크립트는 PulseShaderSpatialMeshParent prefab에 연결 됩니다.  이 prefab는 런타임 공간 메시 Prefab 속성을 통해 공간 인식 프로필에서 참조 됩니다. 런타임 중에 PulseShaderSpatialMeshParent prefab 및가 인스턴스화되고 공간 메시 계층 구조에 추가 됩니다 (장치 에서만이 동작은 편집기에서 관찰 될 수 없음).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>핸드 메시 예제-PulseShaderHandMeshExample

이 예제 장면에서는 펄스 셰이더를 사용 하는 손 모양 메쉬 시각화를 보여 줍니다. HoloLens 장치에서 손을 검색 하는 경우 펄스 애니메이션은 한 번 트리거됩니다. 이 시각적 피드백은 사용자의 상호 작용 신뢰도를 높일 수 있습니다. 

**PulseShaderHandMeshHandler** 스크립트는 할당 된 재질에 대해 펄스 효과를 생성 합니다. 기본적으로 ' 직접 펄스 감지 '가 선택 되어 있습니다.
