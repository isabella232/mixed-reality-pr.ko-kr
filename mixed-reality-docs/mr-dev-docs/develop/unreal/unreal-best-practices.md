---
title: 일반적인 유용한 정보
description: Unreal Engine에서 혼합 현실 애플리케이션을 개발할 때 권장되는 모든 최신 모범 사례를 파악하세요.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, 편집기 확장, Unreal 편집기, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584905"
---
# <a name="general-best-practices"></a>일반적인 유용한 정보

다음은 혼합 현실용 Unreal Engine 프로젝트를 만들 때 모든 개발자에게 권장되는 몇 가지 일반적인 모범 사례입니다.

## <a name="constructors"></a>생성자

청사진에 "생성자"와 동일한 항목이 필요한 경우 Unreal의 [생성 스크립트](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)를 사용합니다. "BeginPlay" 이벤트를 사용하는 경우와 비교할 때 주요 이점은 "편집기"에서도 생성자 스크립트가 실행된다는 것입니다. 대부분의 경우에는 값을 시작 시 바로 캐시하거나 컴파일 시에도 캐시할 수 있습니다.

> [!NOTE]
> [편집기 확장 개요](unreal-editor-extensions.md#construction-scripts)에서 생성 스크립트에 대한 추가 지원 정보를 찾을 수 있습니다.

## <a name="3d-buttons-and-textures"></a>3D 단추 및 질감

혼합 현실 애플리케이션에서 3D 단추를 만드는 중이거나 사용할 계획이 있다면 성능에 대해 생각하는 것이 당연합니다. 그러나 모든 것이 메시에서 제작되어 3D로 인식될 수 있는 것은 아닙니다. 질감이 정교하게 만들어진 Paper2D를 사용하여 3D 모양을 구현하는 방법이 있습니다. 이는 3D로 "보이는" 단추에 정말 잘 맞지만 쿼드의 포토샵 이미지일 뿐입니다. 이러한 이미지의 고급 버전을 [스프라이트](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)라고 합니다.

## <a name="variants"></a>변형

런타임에 여러 개체 구성이 포함된 장면을 만드는 시나리오에서는 [Unreal 변형](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)을 사용합니다. 변형에는 재질 또는 메시 변경이 포함될 수 있습니다. 

## <a name="animation"></a>애니메이션

"상호 작용 가능한 애니메이션"을 많이 만드는 경우 [스플라인 구성 요소](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html)(스플라인 "메시" 구성 요소가 아님) 및 [타임라인 노드](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)를 활용하세요. 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>통신

개체를 동적으로 찾는 데 문제가 있거나 여러 행위자와 청사진 간에 통신하는 데 너무 많은 대역폭을 사용 중인 경우 [수준 청사진](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)을 사용합니다. Unreal Engine 4는 Unity와 달리, 모든 것이 구성 요소 내부에 있을 필요가 없습니다. 수준 청사진은 여러 행위자 간의 통신을 단순화할 때 권장되는 완벽한 방법입니다. 수준 청사진의 OnBeginPlay에서 시작 시 개체 참조를 "캐시"할 수도 있습니다.

## <a name="global-state"></a>전역 상태

점수, 수준 데이터, 플레이어 관련 정보 또는 특정 개체에 속하지 않는 다른 항목 등의 수준별 상태를 저장해야 하는 경우가 종종 있습니다. [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)를 간과하지 마세요. 대부분의 사람들은 GameMode가 존재한다는 것을 잊고 있지만 GameMode는 수준별로 생성할 수 있으며 각 수준과 관련된 데이터를 포함할 수 있습니다.

## <a name="optimizing-blueprints"></a>청사진 최적화

청사진을 찾는 데 너무 오래 걸릴 경우 Unreal에서 청사진을 "네이티브화"한 후 재정렬하여 C++로 코드를 다시 작성하도록 할 수 있습니다. 사용자 지정 솔루션을 만들기 전에 자동 [네이티브화](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)를 사용해 보세요.

![청사진 네이티브화 방법에서 포괄이 강조 표시된 청사진 설정](images/unreal-general-practices-img-01.jpg)
