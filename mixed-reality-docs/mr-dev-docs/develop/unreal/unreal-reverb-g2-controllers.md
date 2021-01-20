---
title: 진짜의 HP 반향 G2 컨트롤러
description: OpenXR 및 SteamVR에서 새로운 HP 반향 G2 컨트롤러를 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582679"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>진짜의 HP 반향 G2 컨트롤러 

## <a name="getting-started"></a>시작

> [!IMPORTANT]
> Hp 동작 컨트롤러 플러그 인에 액세스 하려면 unreal Engine 4.26 및 OpenXR 또는 SteamVR가 필요 합니다. HP 반향 G2 컨트롤러를 사용 하 여 작업 해야 합니다.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>기존 OpenXR 앱 포팅 

HP Mixed Reality 컨트롤러의 게임에 컨트롤러 바인딩이 없으면 OpenXR 런타임은 기존 바인딩을 활성 컨트롤러로 다시 매핑하려는 것입니다.  이 경우 게임에는 Microsoft의 터치 바인딩과 HP 혼합 현실 컨트롤러 바인딩이 없습니다.

![컨트롤러 바인딩이 없을 때 기존 바인딩 다시 매핑](images/reverb-g2-img-04.png)

이벤트는 계속 발생 하지만, 게임에서 오른쪽 메뉴 단추와 같은 컨트롤러 특정 바인딩을 사용 해야 하는 경우 HP 혼합 현실 상호 작용 프로필을 사용 해야 합니다.  여러 장치를 보다 효율적으로 지원 하기 위해 작업 마다 여러 컨트롤러 바인딩을 지정할 수 있습니다.
   
![여러 컨트롤러 바인딩 사용](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>입력 작업 매핑 추가 

새 작업을 정의 하 고 HP Mixed Reality 컨트롤러 섹션의 키 누름 중 하나에 매핑합니다.

![새 작업 및 매핑 정의](images/reverb-g2-img-02.png)

HP 반향 G2 컨트롤러에는 "아웃 축" 바인딩을 사용 하는 축 매핑에서 사용할 수 있는 아날로그 그립도 있습니다.  그립 단추가 완전히 눌린 상태에서 작업 매핑에 사용 해야 하는 별도의 꽉 binding이 있습니다. 

![아웃 축 바인딩 사용](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>입력 이벤트 추가

청사진을 마우스 오른쪽 단추로 클릭 하 고 입력 시스템에서 새 작업 이름을 검색 하 여 이러한 동작에 대 한 이벤트를 추가 합니다.  여기서 청사진은 현재 단추 및 축 상태를 출력 하는 인쇄 문자열이 있는 이벤트에 응답 합니다.

![청사진 이벤트에 응답 하 고 현재 단추 및 축 상태를 출력 합니다.](images/reverb-g2-img-06.png)

### <a name="using-input"></a>입력 사용 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>참고 항목
* [SteamVR 입력](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Windows Mixed Reality에서 SteamVR 사용](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player 카메라](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)