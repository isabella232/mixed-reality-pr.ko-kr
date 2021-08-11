---
title: Unreal의 HP Reverb G2 컨트롤러
description: OpenXR에서 새로운 HP Reverb G2 컨트롤러를 사용하고 Unreal 혼합 현실 애플리케이션에 대해 SteamVR을 사용하는 방법을 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP Reverb G2, 혼합 현실, 개발, 모션 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, 홀로그램, 게임 개발, 혼합 현실 헤드셋, Windows 혼합 현실 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204211"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Unreal의 HP Reverb G2 컨트롤러 

## <a name="getting-started"></a>시작

> [!IMPORTANT]
> Unreal Engine 4.26 및 OpenXR 또는 SteamVR은 HP Reverb G2 컨트롤러로 작업해야 하는 HP Motion Controller 플러그 인에 액세스하는 데 필요합니다.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>기존 OpenXR 앱 포팅 

HP Mixed Reality 컨트롤러에 대한 게임에 컨트롤러 바인딩이 없는 경우 OpenXR 런타임은 기존 바인딩을 활성 컨트롤러에 다시 연결하려고 시도합니다.  이 경우 게임에는 Oculus Touch 바인딩이 있고 HP Mixed Reality Controller 바인딩이 없습니다.

![컨트롤러 바인딩이 없을 때 기존 바인딩 다시 매핑](images/reverb-g2-img-04.png)

이벤트는 계속 발생하지만, 게임이 오른쪽 메뉴 단추와 같은 컨트롤러별 바인딩을 사용해야 하는 경우 HP Mixed Reality 상호 작용 프로필을 사용해야 합니다.  여러 디바이스를 더 잘 지원하기 위해 작업별로 여러 컨트롤러 바인딩을 지정할 수 있습니다.
   
![여러 컨트롤러 바인딩 사용](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>입력 작업 매핑 추가 

새 작업을 정의하고 HP Mixed Reality Controller 섹션의 키 누른 키 중 하나에 매핑합니다.

![새 작업 및 매핑 정의](images/reverb-g2-img-02.png)

HP Reverb G2 컨트롤러에는 "Axis Axis" 바인딩이 있는 축 매핑에 사용할 수 있는 아날로그 그립도 있습니다.  그립 단추를 완전히 눌렀을 때 작업 매핑에 사용해야 하는 별도의 Binding 바인딩이 있습니다. 

![2차원 축 바인딩 사용](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>입력 이벤트 추가

청사진을 마우스 오른쪽 단추로 클릭하고 입력 시스템에서 새 작업 이름을 검색하여 이러한 작업에 대한 이벤트를 추가합니다.  여기서 청사진은 현재 단추 및 축 상태를 출력하는 인쇄 문자열을 사용하여 이벤트에 응답합니다.

![이벤트에 응답하고 현재 단추 및 축 상태를 출력하는 청사진](images/reverb-g2-img-06.png)

### <a name="using-input"></a>입력 사용 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>추가 정보
* [SteamVR 입력](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Windows Mixed Reality 함께 SteamVR 사용](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal 플레이어 카메라](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)