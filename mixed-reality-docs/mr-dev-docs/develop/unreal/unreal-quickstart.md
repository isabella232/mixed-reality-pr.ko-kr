---
title: 첫 번째 HoloLens Unreal 애플리케이션 만들기
description: HoloLens 혼합 현실 개발을 위해 장면 개체 및 입력 상호 작용을 사용하여 Unreal 프로젝트를 올바르게 구성하는 방법을 알아봅니다.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal 편집기, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99421432"
---
# <a name="creating-your-first-hololens-unreal-application"></a>첫 번째 HoloLens Unreal 애플리케이션 만들기

이 가이드는 Unreal Engine의 HoloLens에서 첫 번째 혼합 현실 앱을 실행하는 과정을 안내합니다. 화면에 큐브를 표시하는 간단한 앱을 만듭니다("Hello World"와 유사함). 유용성을 높이기 위해 큐브를 돌리고 애플리케이션을 종료하는 첫 번째 제스처도 만듭니다. 

## <a name="objectives"></a>목표

* HoloLens 프로젝트 시작
* 올바른 플러그 인 사용
* ARSessionConfig 데이터 자산 만들기
* 제스처 입력 설정
* 기본 수준 빌드
* 손가락 모으기 제스처 구현

## <a name="creating-a-new-project"></a>새 프로젝트 만들기

가장 먼저 필요한 것은 작업할 프로젝트입니다. 초보 Unreal 개발자라면 Epic Launcher에서 [지원 파일을 다운로드](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)해야 합니다.

1. Unreal Engine 실행
2. **New Project Categories(새 프로젝트 범주)** 에서 **Games(게임)** 를 선택하고 **Next(다음)** 를 클릭합니다.

![Games(게임)가 강조 표시된 상태로 열려 있는 최근 프로젝트 창](images/unreal-quickstart-img-01.png)

3. **Blank(빈)** 템플릿을 선택하고 **Next(다음)** 를 클릭합니다.

![Blank(빈) 템플릿이 강조 표시된 Unreal 프로젝트 브라우저 창](images/unreal-quickstart-img-02.png)

4. **Project Settings(프로젝트 설정)** 에서 **C++, Scalable 3D or 2D(확장 가능한 3D 또는 2D), Mobile/Tablet(모바일/태블릿)** , **No Starter Content(시작 콘텐츠 없음)** 를 설정한 후 **Create Project(프로젝트 만들기)** 를 클릭합니다.

> [!NOTE] 
> 나중에 OpenXR 플러그 인을 사용할 수 있도록 청사진 프로젝트가 아닌 C++를 사용하는 것입니다. 이 빠른 시작에서는 Unreal Engine과 함께 제공되는 기본 OpenXR 플러그 인을 사용합니다. 하지만 공식 Microsoft OpenXR 플러그 인을 다운로드하여 사용하는 것이 좋습니다. 이렇게 하려면 프로젝트가 C++ 프로젝트여야 합니다.

![프로젝트, 성능, 대상 플랫폼 및 시작 콘텐츠 선택 항목이 강조 표시된 프로젝트 설정 창](images/unreal-quickstart-img-03.png)

Unreal 편집기에서 새 프로젝트가 자동으로 열리므로, 다음 섹션에 대한 준비가 완료되었습니다.

## <a name="enabling-required-plugins"></a>필수 플러그 인 사용

장면에 개체를 추가하기 전에 두 플러그 인을 사용하도록 설정해야 합니다.

1. **편집 > 플러그 인** 을 열고 기본 제공 옵션 목록에서 **증강 현실** 을 선택합니다.
* **HoloLens** 까지 아래로 스크롤하고 **Enabled(사용)** 를 선택합니다.

![증강 현실 섹션이 열려 있고 HoloLens가 강조 표시된 플러그 인 창](images/unreal-quickstart-img-04.png)

2. 오른쪽 상단의 검색창에 **OpenXR** 을 입력하고 **OpenXR** 및 **OpenXRMsftHandInteraction** 플러그 인을 사용하도록 설정합니다.

![OpenXR이 사용하도록 설정된 플러그 인 창](images/unreal-quickstart-img-05.jpg)

![Open XR Msft Hand Interaction이 사용하도록 설정된 플러그 인 창](images/unreal-quickstart-img-06.jpg)

3. 편집기 다시 시작

> [!NOTE]
> 이 자습서에서는 OpenXR을 사용하지만 위에서 설치한 두 플러그 인은 현재 HoloLens 개발을 위한 전체 기능 집합을 제공하지 않습니다. HandInteraction 플러그 인은 나중에 사용할 "손가락 모으기" 제스처에 충분하지만 기본 이상을 원한다면 [OpenXR 플러그 인을 다운로드](https://github.com/microsoft/Microsoft-OpenXR-Unreal)해야 합니다.

이러한 플러그 인을 사용하도록 설정하면 콘텐츠로 채우는 데 집중할 수 있습니다.

## <a name="creating-a-level"></a>수준 만들기

다음 작업은 참조 및 규모에 대한 시작 지점과 큐브를 사용하여 플레이어 설정을 만드는 것입니다.

1. **파일 > 새 수준** 을 선택하고 **빈 수준** 을 선택합니다. 이제 뷰포트의 기본 장면이 비어 있습니다.
2. **Modes(모드)** 탭에서 **Basic(기본)** 을 선택하고 장면으로 **PlayerStart** 를 끌어옵니다.
* **Details(세부 정보)** 탭에서 **Location(위치)** 을 **X = 0, Y = 0** 및 **Z = 0** 으로 설정하고 앱이 시작될 때 사용자를 장면의 중앙에 배치합니다.

![위치 및 플레이어 시작이 추가된 Unreal 편집기 장면](images/unreal-quickstart-img-07.png)

3. **Basic(기본)** 탭에서 **Cube(큐브)** 를 장면으로 끌어옵니다.
* 큐브의 **Location(위치)** 을 **X = 50, Y = 0** 및 **Z = 0** 으로 설정하여 시작 시 플레이어에서 50cm 거리에 큐브를 배치합니다.
* 큐브의 **Scale(눈금)** 을 **X = 0.2, Y = 0.2** 및 **Z = 0.2** 로 변경합니다. 

장면을 테스트하기 전에 마지막으로 장면에 조명을 추가하지 않으면 큐브를 볼 수 없습니다.

4. **Modes(모드)** 패널에서 **Lights(조명)** 탭으로 전환하고 **Directional Light(방향성 광원)** 을 장면으로 끌어옵니다.
* **PlayerStart** 위에 조명을 배치하면 볼 수 있습니다.

![큐브 및 방향성 광원이 추가된 Unreal 편집기 장면](images/unreal-quickstart-img-08.png)

5. **File(파일) > Save Current(현재 저장)** 로 이동하고, 수준 이름을 **Main(기본)** 으로 지정한 후 **Save(저장)** 를 선택합니다.

장면 집합에서 도구 모음의 **재생** 을 눌러 큐브의 작동을 확인합니다. 작업을 감상한 후 Esc를 눌러 애플리케이션을 중지합니다.

![큐브가 화면 중앙에 위치한 재생 모드의 장면](images/unreal-quickstart-img-09.png)

장면이 설정되었으므로 이제 AR에서 몇 가지 기본적인 상호 작용을 준비하도록 할 수 있습니다. 먼저 AR 세션을 만들고 청사진을 추가하여 손 조작을 사용하도록 설정해야 합니다.

## <a name="adding-a-session-asset"></a>세션 자산 추가

Unreal의 AR 세션은 스스로 발생하지 않습니다. 세션을 사용하려면 다음 작업을 위한 ARSessionConfig 데이터 자산이 필요합니다.

1. **Content Browser(콘텐츠 브라우저)** 에서 **새로 추가(Add New) > Miscellaneous(기타) > Data Asset(데이터 자산)** 을 선택하고 루트 콘텐츠 폴더 수준에 있는지 확인합니다.
2. **ARSessionConfig** 를 선택하고 **Select(선택)** 를 클릭한 다음, 자산의 이름을 **ARSessionConfig** 로 지정합니다.

![AR 세션 구성 자산이 강조 표시된 상태로 열려 있는 데이터 자산 클래스 선택 창](images/unreal-quickstart-img-10.png)

2. **ARSessionConfig** 를 두 번 클릭하여 열고 모든 기본 설정을 그대로 둔 다음, **Save(저장)** 를 눌러 주 창으로 돌아갑니다.

![AR 세션 구성 자산 세부 정보 창](images/unreal-quickstart-img-11.png)

작업이 완료되면 다음 단계는 수준이 로드되고 종료될 때 AR 세션이 시작되고 중지되도록 하는 것입니다. 다행히 Unreal에는 수준 전체 글로벌 이벤트 그래프 역할을 하는 **수준 청사진** 이라는 특수 청사진이 있습니다. 수준 청사진에서 ARSessionConfig 자산을 연결하면 게임 재생이 시작될 때 AR 세션이 즉시 실행됩니다.

3. 편집기 도구 모음에서 **Blueprints(청사진) > Open Level Blueprint(수준 청사진 열기)** 를 선택합니다.

![수준 청사진 옵션이 강조 표시된 상태로 열려 있는 청사진 메뉴](images/unreal-quickstart-img-12.png)

4. 실행 노드(왼쪽 화살표 아이콘)를 **Event BeginPlay(이벤트 BeginPlay)** 에 끌어다 놓습니다.
* **Start AR Session node(AR 세션 시작 노드)** 를 검색하고 Enter 키를 누릅니다.
* **Session Config(세션 구성)** 에서 **Select Asset(자산 선택)** 드롭다운을 클릭하고 **ARSessionConfig** 자산을 선택합니다.

![이벤트 시작 재생이 AR 세션 시작 기능에 연결된 청사진 그래프](images/unreal-quickstart-img-13.png)

5. 마우스 오른쪽 단추로 EventGraph의 아무 곳을 클릭하고, 새 **Event EndPlay** 노드를 만듭니다. 
* 실행 핀을 끌어 놓은 다음, **Stop AR Session(AR 세션 중지)** 노드를 검색하고 Enter 키를 누릅니다. 
* **Compile(컴파일)** 을 누른 다음, **Save(저장)** 하고 주 창으로 돌아갑니다.

> [!IMPORTANT]
> 수준이 종료될 때 AR 세션이 계속 실행 중이면 헤드셋으로 스트리밍하는 동안 앱을 다시 시작할 때 특정 기능이 작동하지 않을 수 있습니다.

![AR 세션 중지 기능에 연결된 이벤트 종료 재생 노드](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>입력 설정

1. **Edit(편집) > Project Settings(프로젝트 설정)** 를 선택하고 **Engine(엔진) > Input(입력)** 으로 이동합니다.
2. **Action Mappings(작업 매핑)** 옆에 있는 **+** 아이콘을 선택하고 **RightPinch** 및 **LeftPinch** 작업을 만듭니다.

![오른쪽 손가락 모으기 및 왼쪽 손가락 모으기 작업 매핑이 강조 표시된 바인딩 입력 설정](images/unreal-quickstart-img-15.jpg)

3. **RightPinch** 및 **LeftPinch** 작업을 각 **OpenXR Msft Hand Interaction** 작업에 매핑합니다.

![OpenXR Msft Hand Interaction 옵션이 강조 표시된 작업 매핑](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>제스처 설정

이제 입력을 설정했으므로 흥미로운 부분으로 넘어가 보겠습니다. 바로 제스처를 추가하는 겁니다. 오른쪽 손가락을 모아서 큐브를 돌리고 왼쪽 손가락을 모아서 애플리케이션을 종료해 보겠습니다.

1. **Level Blueprint(수준 청사진)** 를 열고 **InputAction RightPinch** 및 **InputAction LeftPinch** 를 추가합니다.
* **Cube(큐브)** 를 대상으로 사용하고 **Delta Rotation(델타 회전)** 을 **X = 0, Y = 0** 및 **Z = 20** 으로 설정하여 오른쪽 손가락 모으기 이벤트를 **AddActorLocalRotation** 에 연결합니다. 이제 손가락을 모을 때마다 큐브가 20도 회전합니다.
* 왼쪽 손가락 모으기 이벤트를 **Quit Game(게임 종료)** 에 연결합니다.

![오른쪽 및 왼쪽 손가락 모으기 이벤트에 대한 입력 작업을 사용하여 열린 수준 청사진](images/unreal-quickstart-img-17.jpg)

2. 큐브의 **Transform(변환)** 설정에서 **Mobility(이동성)** 를 **Movable(이동 가능)** 로 설정하여 동적으로 이동할 수 있도록 합니다.

![이동성 속성이 강조 표시된 변환 설정](images/unreal-quickstart-img-18.jpg)

이제 애플리케이션을 배포하고 테스트할 준비가 되었습니다.