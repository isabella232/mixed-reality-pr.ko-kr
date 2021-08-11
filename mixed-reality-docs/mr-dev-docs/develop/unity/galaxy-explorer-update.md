---
title: HoloLens 2에 대 한 Galaxy 탐색기 만들기
description: 팀이 GitHub에서 HoloLens 2에 대 한 Galaxy 탐색기 오픈 소스 프로젝트를 업데이트 하는 방법에 대해 알아봅니다.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy 탐색기, 사례 연구, 프로젝트, 샘플, mrtk, 혼합 현실 Toolkit, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200507"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>HoloLens 2에 대 한 Galaxy 탐색기 만들기

![새 Galaxy 탐색기 로고](../images/GalaxyExplorer2.jpg)


HoloLens 2 응용 프로그램에 대해 업데이트 된 Galaxy 탐색기를 시작 합니다. [Galaxy 탐색기](/windows/mixed-reality/galaxy-explorer "갤럭시 익스플로러") 는 원래 아이디어 프로그램 공유를 통해 HoloLens (첫 번째 gen)를 위한 오픈 소스 응용 프로그램으로 개발 되었으며, 대부분의 사용자가 보유 하 고 있는 첫 번째 혼합 현실 환경 중 하나입니다. 이제 [HoloLens 2의 새롭고 흥미로운 기능](https://www.microsoft.com/hololens/hardware)을 위해 업데이트 하는 중입니다.

[Microsoft Mixed Reality 스튜디오](galaxy-explorer-update.md#mixed-reality-studios)중 하나로, 일반적으로 상용 성적 솔루션을 개발 하 고 창의적인 개발 프로세스 전체에서 대상 플랫폼에 대 한 테스트를 & 개발 하 고 있습니다. 우리와 커뮤니티에서 제공 되는 프레임 워크 및 도구 (예: [Mrtk](mrtk-getting-started.md))를 사용 하 여이 프로젝트에 대해 형성 하 고 있습니다.

원래 Galaxy 탐색기와 마찬가지로, [microsoft 팀](galaxy-explorer-update.md#meet-the-team) 은 커뮤니티에 모든 권한이 있는지 확인 하기 위해 [GitHub에 대 한 프로젝트 소싱을 시작](https://github.com/Microsoft/GalaxyExplorer) 합니다. mrtk v1에서 mrtk v 2로 이식 하는 방법, HoloLens 2에서 제공 하는 새로운 기능에 대 한 향상 된 기능 및 Galaxy 탐색기가 다중 플랫폼 환경을 유지 하는지 확인 하는 방법에 대 한 완전 한 투명성을 여기에서 살펴보겠습니다. HoloLens (처음 gen), HoloLens 2, Windows Mixed Reality 헤드셋 또는 Windows 10 데스크톱에서 Galaxy 탐색기를 보는 경우에는 최대한 많은 경험을 즐길 수 있습니다.

이 페이지는 프로젝트에 대 한 자세한 문서, 코드, 디자인 아티팩트 및 추가 MRTK 설명서에 대 한 링크를 사용 하 여 프로젝트를 진행 하면서 확장 되어 프로젝트에 대 한 의견을 제공 합니다.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>HoloLens 2의 Microsoft Store에서 앱 다운로드
HoloLens 2 장치가 있는 경우 장치에서 앱을 직접 다운로드 하 여 설치할 수 있습니다.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>상호 작용 고려

Creative studio로 Galaxy는 HoloLens 2 하는 데 Galaxy 탐색기를 이식할 수 있는 권한에 대 한 ecstatic 이었습니다. 처음에는 새로운 장치에 대 한 축 하 드립니다. 그리고 혼합 현실 역량은 상상력만 제한 된다는 것을 보여 줍니다.

HoloLens 2를 통해 사용자는 실제 개체와 같이 자연스럽 게 응답 하는 방식으로 holograms를 터치 하 고, 잡고, 이동할 수 있습니다. 완전 한 트레일러 식 모델은 사용자가 자연스럽 게 작업할 수 있기 때문에 놀라운 역할을 합니다. 예를 들어, 모든 사용자가 컵을 약간 다르게 선택 하 고 특정 한 방법을 적용 하는 대신, HoloLens 2 하 여 작업을 수행할 수 있습니다.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

이는 첫 번째 세대 HoloLens 장치에서 공기 탭 기반 인터페이스를 크게 변경 하는 것입니다. 사용자는 먼 거리에서 holograms와 상호 작용 하는 대신 "사용자가 가까이와 개인"을 가져올 수 있습니다. 기존 환경을 HoloLens 2 하거나 새로운 환경을 계획 하는 경우 holograms의 직접 조작을 이해 하는 것이 중요 합니다.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>직접 조작과 공간의 넓은 거리 비교

이는 전 세계에 도달 하 고 전 세계에 있는 마법 경험입니다. 이 방법의 과제는 태양계의 크기 이며 매우 다양 합니다. 사용자는 각 전 세계에 근접 하 여 상호 작용할 수 있도록 공간을 탐색 해야 합니다.

사용자가 더 멀리 떨어져 있는 개체와 상호 작용할 수 있도록 하기 위해 MRTK는 사용자의 팜 중심에서 제공 되는 손 광선을 제공 하 여 손 모양 확장으로 작동 합니다. 도넛 모양의 커서는 광선이 대상 개체와 교차 하는 위치를 나타내기 위해 광선 끝에 연결 됩니다. 그런 다음, 커서가 닿는 개체는 손에서 제스처 명령을 받을 수 있습니다. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

원래 버전의 Galaxy 탐색기에서 사용자는 응시 커서를 사용 하 여 전 세계를 대상으로 하 고, 무선 탭을 사용 하 여 더 가까이 호출 합니다. HoloLens 2 환경을 이식 하는 가장 쉬운 방법은이 동작을 수행 하 고 핸드 광선을 사용 하 여 행성을 선택 하는 것입니다. 이 기능이 작동 하는 동안 더 많은 정보를 남겨 주세요.

### <a name="back-to-the-drawing-board"></a>그리기 보드로 돌아가기

기존 상호 작용을 기반으로 구축 될 수 있는 항목을 ideate 했습니다. 그 이유는 다음과 같습니다 HoloLens 2. 사용자가 자연 스러운 실제 방법으로 holograms와 상호 작용할 수 있도록 하는 것은 아닙니다. 따라서 사용자에 대 한 상호 작용이 타당 실제 개체를 사용 하 여 상호 작용을 가능 하 게 하는 것은 중요 하지 않으며 가능 합니다.

Telekinesis을 기반으로 하는 한 가지 개념은 개체를 조작할 수 있는 강력한 기능입니다. 일반적으로는 슈퍼 영웅 영화에서 볼 수 있으며, 사람들은 자신의 마음에 도달 하 여 개체를 오픈 손 모양으로 호출 합니다. 아이디어를 자세히 살펴보고 개념의 작동 방식에 대 한 빠른 스케치를 제공 합니다.

![강제 잡기 상호 작용에 대 한 개념](images/ge-update-interactions-concept-force-grab.png)

사용자는 대상 피드백을 제공 하는 전 세계의 광선을 가리킵니다. 그런 다음 사용자가 자신의 오픈 손을 확장 하 게 되 면 전 세계에 가까이 있을 때까지 전 세계를 대상으로 합니다. 따라서 상호 작용에 대 한 이름: 강제 잡기. 사용자가 해당 지구를 사용 하 여 지구를 푸시하 면 해당 궤도로 다시 돌아옵니다.

### <a name="force-grab-prototyping"></a>강제 잡기 프로토타입

그런 다음 개념을 테스트 하기 위해 여러 프로토타입을 만들었습니다. 어떻게 전반적인 상호 작용이 어떻게 되나요? 호출 된 개체가 사용자 앞에서 중지 되거나 배치 될 때까지 손을 사용 해야 하나요? 호출 된 개체의 크기를 변경 해야 합니까? 아니면 크기를 조정 해야 하나요?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>응용 프로그램에 대 한 강제 잡기 구현

행성에 대해 강제 잡기를 시도 하면 태양계의 소수 자릿수를 변경 해야 했습니다. 사용자가 이해 하 고 탐색 하기 어려운 양력 시스템의 정확 하 고 보통 크기의 표현을 확인 하는 것은 쉽지 않습니다. 그러나 작은 크기의 표현이 너무 작아 쉽게 선택할 수 없습니다. 결과적으로 행성의 크기와 태양 개의 개체 간 간격은 상대 정확도를 유지 하면서 보통 크기의 공간 내에서 편안 하 게 설계 되었습니다.

개발 스 프린트의 이후 단계를 진행 하는 동안 동료 MSFT Mixed Reality 전문가에 게 사내를 사용 하는 것이 충분 하기 때문에 전문 테스터로 서 입력을 받고 강제로 잡기 상호 작용에 대 한 빠른 반복을 수행할 수 있습니다.

![의 Kam에서 Galaxy 탐색기의 미리 보기 빌드 테스트](images/ge-update-user-testing.png)

그림:의 Kam, 선임 디자인 리드, Galaxy 탐색기의 진행 중인 작업 테스트

### <a name="adding-affordances-for-targeting"></a>대상 지정을 위한 affordances 추가

HoloLens 2 하는 것 처럼 새로운 상호 작용이 자연스럽 고 직관적 이더라도 holograms는 가중치 또는 tactile sensations 없이 동일 하 게 유지 된다는 것을 알게 되었습니다. Holograms는 사용자가 개체와 상호 작용할 때 수신 하는 데 사용 하는 자연 스러운 피드백을 제공 하지 않으므로 만들어야 합니다.

사용자가 상호 작용의 다양 한 단계를 위해 사용자에 게 제공 되는 시각적 및 오디오 피드백 및 강제 잡기 메커니즘이 Galaxy 탐색기와 상호 작용 하는 중심 이므로 많은 반복이 발생 했습니다. 목표는 각 상호 작용 단계에 대 한 오디오 및 시각적 피드백의 적절 한 균형을 찾는 것입니다. 즉, 의도 한 개체에 초점을 맞춘 후 사용자에 게 호출 하 고 릴리스 합니다. HoloLens (첫 번째 gen)에 사용 된 것과 상호 작용을 강화 하기 위해 더 많은 오디오 및 시각적 피드백이 필요 했습니다.

![행성의 시각적 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>강제 잡기에 affordances 추가
 
Audio 및 visual affordances를 사용 하는 기본 강제 잡기 메커니즘이 있으면 사용자에 게 더 친숙 한 행성을 선택 하는 방법을 살펴보았습니다. 해결 해야 할 두 가지 주요 사항은 다음과 같습니다. 태양계는 3D 이동 인터페이스 이므로 사용자가 개체를 일관 되 게 대상으로 하는 방법을 배울 수 있는 복잡성이 추가 되었습니다. 이는 개체를 선택 하는 속도가 빠르기 때문에 사용자에 게 신속 하 게 이동 하는 것입니다.

대 접근 솔루션을 사용 하 여이에 대해 노력 했습니다. 첫 번째 방법은 매우 직관적입니다. 행성이 사용자에 게 보다 자연스럽 게 접근 하도록 선택 프로세스의 속도를 낮춥니다. 속도가 조정 되 면 오디오 및 시각적 affordances을 다시 방문 하 여 사용자에 게 추적 된 지구로 오디오 피드백을 추가 해야 했습니다.

솔루션의 두 번째 부분에서는 전체 강제 잡기 작업을 시각화 하는 방법을 소개 했습니다. 손 모양 광선이 연결 된 후 대상 개체를 향해 이동 하는 굵은 선을 시각화 하 고 개체를 사용자와 같은 올가미로 다시 가져옵니다. 

![강제 잡기를 위한 시각적 "올가미" affordances](images/ge-update-lasso-affordances.png)

마지막으로, 행성이 사용자의 응시 및 손 광선을 대상으로 하는 데 충분 한 크기를 갖도록 양력 시스템의 규모를 최적화 했습니다. 

이러한 세 가지 향상 된 기능을 통해 사용자는 정확한 선택을 하 고 직관적인 방식으로 행성을 호출할 수 있습니다. 전반적으로 최종 강제 잡기의 효과는 태양계에서 더 몰입 형이 고 대화형 환경입니다.

## <a name="spotlight-on-jupiter"></a>Jupiter의 스포트라이트

Milky 방식의 태양계를 만드는 것은 humbling 환경 이었습니다. 특히 Jupiter의 고유한 특성은 behold에 대 한 시야를 만듭니다. 가스의 가장 크고 광범위 한 조합 이며 다른 모든 행성 보다 많은 질량을 포함 합니다. Turbulence 및 클라우드 dynamics의 가장 큰 크기 및 mesmerizing 밴드는 특별 한 꾸밈 주의를 prefect 합니다.

### <a name="geometry-and-meshes"></a>기 하 도형 및 망

가스의 Jupiter 외부 셸은 gaseous 계층으로 구성 됩니다. 고속 회전 속도, 내부 열 교환 및 Coriolis의 조합으로 인해 swirling cloud 벨트 및 vortices로 형성 되는 다채로운 계층 및 스트림이 생성 됩니다. 이러한 복잡 한 장점 캡처는 태양계를 만드는 데 중요 했습니다.

사전 계산 스트림을 사용 하 여 유체 시뮬레이션 및 애니메이션 텍스처와 같은 시각화 기법을 사용 하는 것이 더 확실 하지 않습니다. 동시에 발생 하는 다른 모든 것과 함께이를 시뮬레이션 하는 데 필요한 컴퓨팅 성능은 성능에 상당한 영향을 미칠 수 있습니다. 

![Jupiter 개체 개요](images/ge-update-jupiter-shells-complete.jpg)

다음 방법은 순환 메시의 컴포지션에 컴파일된 대기 이동의 특정 측면을 처리 하는 투명 한 질감 계층으로 구성 된 ' 스모크 및 미러링 ' 솔루션 이었습니다.

아래 이미지에서는 왼쪽의 내부 셸을 볼 수 있습니다. 이 서 수 계층은 클라우드를 구성 하는 여러 계층 간의 작은 간격을 방지 하기 위해 컴포지션에 배경을 제공 했습니다. 계층의 저속 회전으로 인해 계층 전체에서 visual unity를 빌드하는 데 도움이 되도록 더 빠른 이동 밴드 간의 시각적 버퍼로도 제공 됩니다.

모델에 대 한이 앵커를 설정한 후에는 아래에 표시 된 중간 및 오른쪽 메시에서 이동 하는 클라우드 계층이 투영 됩니다.

![셸이 분리 된 Jupiter 개체 개요](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>질감

기존 질감이 세 부분으로 구성 된 질감 아틀라스로 구분 되어 있습니다. 위 세 번째는 시차 효과를 제공 하기 위해 간격이 있는 클라우드의 motionless 계층을 호스팅하고, 가운데 섹션에는 빠른 이동 외부 스트림이 포함 되 고, 세 번째는 느린 내부 기본 계층을 포함 합니다.

특성에 적합 한 빨간색도 다양 한 이동 부분으로 분리 된 다음, 다른 경우에는 질감의 보이지 않는 영역에 삽입 되었습니다. 이러한 구성 요소는 아래 이미지의 중간 섹션에서 빨간색으로 빨강으로 하여진 반사로 볼 수 있습니다.

각 밴드에는 특정 방향과 속도가 있으므로 질감이 각 메시에 개별적으로 적용되었습니다. 메시에는 공통 중심점과 피벗 점이 있어 전체 표면에 동심적으로 애니메이션을 적용할 수 있습니다.

![텍스처에 대한 개요](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>회전 및 질감 동작

표시 컴퍼지션이 설정되면 회전 및 회전 속도를 적절하게 계산하고 적용해야 했습니다. 전체 회전을 완료하는 데는 약 9시간이 걸립니다. 이는 차등 회전으로 인한 정의 문제입니다. 따라서 적도 스트림은 '마스터 스트림'으로 설정되었으며 전체 회전을 위해 3600 프레임을 차지합니다. 다른 모든 계층은 초기 위치(예: 600, 900, 1200, 1800 등)를 허용하기 위해 회전 속도를 3600의 요소로 사용해야 했습니다.

![셸 질감](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>큰 빨간색 스폿

개별적으로 회전하는 스트림은 좋은 시각적 인상을 제공했지만 가까운 범위에서 관찰될 때는 자세히 설명하지 않았습니다.

가장 눈에 잘 붙는 부분은 은조의 빨강 스폿이므로 특히 메시와 질감 세트를 만들어 보여 줍니다.
 
우리는 일련의 회전 파트가 서로 위에 구성되는 동시에 '마스터 계층' 아래에 그룹화되어 나머지가 이동하는 속도에 관계없이 위치에 유지되도록 하는 유사한 메커니즘을 사용했습니다.

메시가 설정되고 배치될 때 서로 다른 Stormy vortex 계층이 적용되고 각 디스크에 개별적으로 애니메이션이 적용되어 중심 부분이 가장 빠르게 이동하고 나머지는 바깥쪽으로 이동하면서 점진적으로 느려집니다.

![빨강 스폿 메시가 빨라진 것을 발견했습니다.](images/ge-update-great-red-spot-mesh.jpg)

또한 컴퍼지션은 다른 모든 메시와 동일한 피벗을 유지하면서 원래 y축(!)에서 기울기를 유지하여 회전에 애니메이션을 주도록 합니다. 3600 프레임은 기본 속도이며 각 계층은 회전 기간으로 이 요소의 비율을 갖습니다.

![Great Red Spot Texture](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Unity에서 바로 얻기

Unity에서 구현할 때 유의해야 할 몇 가지 주요 사항이 있습니다.

Unity는 큰 투명 계층 집합을 처리할 때 쉽게 혼동됩니다. 해결 방법은 각 메시에 대한 질감 재질을 복제하고 오름차순 Render Queue 값을 내부에서 외부로 5씩 각 재질에 점진적으로 적용하는 것이었습니다.

그 결과 내부 셸의 Render Queue 값은 3000(기본값)이고, 정적 빨간색 톤 외부는 나중에 값이 3005이며, 빠른 흰색 외부 클라우드는 3010입니다. 이 모델에서는 Great Red Spot(내부 계층에서 외부 계층으로 진행)이 3025로 완료되었습니다.

![2차 최종 개체](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>마지막 터치

처음에는 질감이 있는 텍스처된 스트루 계층이 설정되었으며, 이는 구현에 충분하지 않은 것으로 입증되었습니다.

원래 Planet Standard 셰이더와 모든 변형은 MRTK 표준 셰이더에서 지원되지 않는 스크립트 SunLightReceiver를 통해 조명 정보를 받습니다.

Planet Standard 셰이더가 transparencies가 있는 질감 맵을 지원하지 않기 때문에 셰이더를 단순히 교환하는 것은 솔루션이 아니었습니다. 이 셰이더를 편집하여 의도한 대로 채색 빌드가 작동하도록 했습니다.

마지막으로, Source Blend를 10으로 설정하고 Destination Blend를 5로 설정하여 알파 Blend를 설정해야 했습니다.

![Unity 속성](images/ge-update-jupiter-unity-render-queue.jpg)

Galaxy Explorer에서의 최종 렌더링을 볼 수 있습니다.

## <a name="meet-the-team"></a>팀 소개 

Mixed Reality 스튜디오 팀은 디자이너, 3D 디자이너, UX 전문가, 개발자, 프로그램 관리자 및 스튜디오 헤드로 구성됩니다. 우리는 전 세계에서 다음과 같이 전 세계에 걸쳐 있습니다. 즉, 캐나다, 독일, 아랍에미리트, 일본, 영국 및 미국. 우리는 다양한 배경을 가진 다분야 팀입니다. 게임 ( 기존 및 스트리밍, 디지털 마케팅, 의료 및 과학 모두).

HoloLens 2 위한 Galaxy Explorer를 만들고 HoloLens(1세대), VR 및 데스크톱 버전을 업데이트하게 되어 기쁩니다. 

![Galaxy Explorer 팀](images/ge-update-team-image.png)

왼쪽에서 오른쪽으로: Artemis Tsdou(개발자), Angie Teickner(비주얼 디자이너), David Janer(UX 디자이너), David Janer(Delivery & Production Lead), Yasushi Zonno(Creative Lead), Eline Ledent(Developer) 및 BenOu(Sr. Developer).
왼쪽에서 오른쪽으로 아래쪽: Amit Rojtblat(Technical Artist), Martin Wettig(3D Artist) 및 Dirk Sonika(Studio Head).
추천되지 않음: TimEdken(기술 리드) 및 표시자(비주얼 디자이너).

## <a name="additional-information"></a>추가 정보

### <a name="mixed-reality-studios"></a>Mixed Reality Studios

미국, 유럽 및 Asia-Pacific 위치한 Microsoft Mixed Reality Studio 팀은 사용자 환경 디자인, 홀로그램 컴퓨팅, AR/VR 기술 및 3D 개발 전문가입니다. 3D 자산 만들기, DirectX, Unity 및 Unreal 포함 고객이 조직 전체에서 측정 가능한 영향을 만들 수 있도록 하면서 원하는 미래를 구상하고, 솔루션을 설계, 빌드 및 제공할 수 있습니다. 스튜디오는 엔터프라이즈 애플리케이션 통합, 채택, 운영 및 지원을 위해 22,000명 이상의 Microsoft 서비스 전문가와 긴밀하게 협력합니다.