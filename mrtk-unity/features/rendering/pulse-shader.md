---
title: 펄스 셰이더
description: MRTK의 펄스 셰이더에 대한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: add3aaa2a98ca2ddc1f60b0307a3defed3236d9a2c09aa70ea2d12b2d9638eba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228390"
---
# <a name="pulse-shader"></a>펄스 셰이더

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

펄스 셰이더를 사용하여 표면 재설계, 굴절형 손 메시 또는 다른 메시에 대한 시각적 펄스 효과에 애니메이션 효과를 주세요.

## <a name="shader-and-material"></a>셰이더 및 재질

다음 재질에서는 **SR_Triangles** 셰이더를 사용합니다. 채우기 색, 선 색 및 펄스 색과 같은 다양한 옵션을 구성할 수 있습니다.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>필수 조건

공간 메시 예제의 경우 mixedRealityToolkit 개체 -> Spatial Awareness Profile -> Display 설정 -> Visible Material 아래에 MRTK_Pulse_SpatialMeshBlue.mat 또는 MRTK_Pulse_SpatialMeshPurple.mat이 할당되어 있는지 확인합니다.

손 메시 예제의 경우 MRTK_Pulse_ArticulatedHandMeshBlue.mat 또는 MRTK_Pulse_ArticulatedHandMeshPurple.mat가 MrTK 설정 -> Input -> 손 추적 -> 손 메시 프리팹에 할당되어야 하는 ArticulatedHandMesh.prefab에 할당되어 있는지 확인합니다.

## <a name="how-it-works"></a>작동 방식

손 메시 셰이더에서는 IV를 사용하여 손 메시를 따라 펄스를 매핑하고, 손으로 펄스를 페이드 아웃합니다. 표면 음영 셰이더에서는 꼭짓점 위치를 사용하여 펄스를 매핑합니다.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>공간 메시 예제 - PulseShaderSpatialMeshExample.unity

HoloLens 2 셸 환경과 마찬가지로 손 광선을 가리키고 에어 탭하여 공간 메시에 펄스 효과를 생성할 수 있습니다. 예제 장면에는 Unity의 게임 모드에 대한 테스트 공간 메시 데이터인 ExampleSpatialMesh 개체가 포함되어 있습니다. 이 개체는 사용하지 않도록 설정되고 디바이스에서 숨겨집니다.

이 true인 경우 **PulseShaderSpatialMeshHandler.cs** 스크립트는 적중 지점 위치에서 공간 메시에 대한 펄스 효과를 `PulseOnSelect` 생성합니다. `Auto Pulse`속성은 재질 자체에서 반복 애니메이션에 대해 true로 설정할 수도 있습니다.  예제 장면에서 이 스크립트는 PulseShaderSpatialMeshParent 프리팹에 연결됩니다.  이 프리팹은 런타임 공간 메시 프리팹 속성을 통해 공간 인식 프로필에서 참조됩니다. 런타임 중에 PulseShaderSpatialMeshParent 프리팹이 인스턴스화되어 공간 메시 계층 구조에 추가됩니다(디바이스에서만 이 동작을 편집기에서 관찰할 수 없음).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>손 메시 예제 - PulseShaderHandMeshExample.unity

이 예제 장면에서는 펄스 셰이더를 사용하여 손 메시 시각화를 보여줍니다. HoloLens 디바이스에서 손을 감지하면 펄스 애니메이션이 한 번 트리거됩니다. 이 시각적 피드백은 사용자의 상호 작용 신뢰도를 높일 수 있습니다. 

**PulseShaderHandMeshHandler.cs 스크립트는** 할당된 재질에 대한 펄스 효과를 생성합니다. 기본적으로 'Pulse On Hand Detected'가 선택되어 있습니다.
