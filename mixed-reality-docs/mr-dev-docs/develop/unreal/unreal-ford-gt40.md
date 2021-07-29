---
title: Ford GT40 환경
description: Unreal에서 HoloLens 2 위해 MRTK를 통해 Ford GT40 혼합 현실 애플리케이션을 만드는 것을 살펴보세요.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 디바이스에 배포, PC, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
appliesto:
- HoloLens 2
ms.openlocfilehash: e634d75af92509372209d8e7c0cde2833127c128
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757202"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Ford GT40 환경 만들기
![Ford GT40 Hero 이미지](images/ford-gt40-hero_1920.jpg)

*"모든 공간 상호 작용을 C++로 직접 코딩해야 하므로 MRTK 이전의 Unreal을 사용하여 HoloLens 2 개발하면 약간 지루했습니다. Unreal용 MRTK는 이와 동일한 작업을 많이 수행했습니다. 초기 프로토타입에 필요한 시간을 절반으로 줄인 것으로 예상합니다."* - Software Developer, Jose Jose

*"Ford GT40 환경은 약정한 예산으로 단 몇 개월 만에 HoloLens 2 앱을 완료할 수 있지만 여전히 매우 영향력 있는 결과를 제공한다는 것을 증명합니다."*  - Daniel 체etham, Happy Finish 최고 혁신 책임자

Unreal에 대한 MRTK(Mixed Reality Toolkit)를 사용하는 창의적인 프로덕션 회사 Happy HoloLens 2 Finish는 Le Mans의 24시간 동안 24시간 동안의 Le Mans!

사용자는 다양한 자연적이고 직관적인 공간 상호 작용을 사용하여 Unreal Engine에서 제공하는 높은 시각적 충실도를 활용하는 방식으로 제공되는 GT40의 장점, 성능 및 엔지니어링을 살펴볼 수 있습니다. 전체 프로젝트에 대한 소프트웨어 개발은 단일 개발자가 3개월 이내에 완료했으며, Unreal의 시각적 스크립팅 및 디자인 환경에 대한 MRTK를 통해 가능합니다.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>HoloLens 2 Microsoft Store 앱을 다운로드합니다.
HoloLens 2 디바이스가 있는 경우 앱을 직접 다운로드하여 디바이스에 설치할 수 있습니다.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>요청

Happy Finish는 Ford, Microsoft, Includes, Netflix, Vodafone 및 기타 가구 이름을 포함하는 클라이언트 기반이 있는 세계 최고의 창의적인 프로덕션 회사 중 하나입니다. 이 회사는 3D 공간 디자인 및 상호 작용을 통해 몰입형 스토리텔링의 뛰어난 분야로 확장하기 전에 영화 및 CGI로 분기하는 고급 사진 보증 기관으로 시작했습니다.

2020년 중간에 Microsoft는 Unreal Engine의 HoloLens 2 지원을 기반으로 하는 Unreal용 MRTK(새 Mixed Reality Toolkit)에서 사용할 수 있는 가능성을 보여 주는 데모 앱을 만들기 위해 Happy Finish에 접근했습니다. 이 시점에서 회사는 이미 두 개의 Unreal on-on-HoloLens 2 프로젝트를 성공적으로 수행했습니다. 둘 다 전 세계적으로 인식되는 소비자 브랜드에 대한 것이었습니다. 이 브랜드는 클라이언트 고유의 고성능 제품을 가장 잘 소개하는 데 필요한 대로 높은 시각적 충실도를 위해 내부 R&D/B2B 판매 도구에 대해 Unreal on HoloLens 2 선택했습니다.

솔루션 자체는 Happy Finish로 남겨지지만 몇 가지 주요 지침을 충족해야 했습니다. 첫째, 게임 업계 외부의 HoloLens 2 Unreal의 유틸리티를 설명하기 위해 엔터프라이즈 시나리오에 집중해야 했습니다. 둘째, 대상 프레임 속도와 시각적 품질을 얻기 위해 네트워크 연결 및 외부 처리 능력을 요구하지 않고도 독립 실행형 데모로 사용할 수 있는 디바이스 전용이어야 했습니다. 셋째, MRTK에서 지원하는 직관적인 상호 작용의 범위를 원활하고 자연스러운 환경으로 혼합해야 합니다. 마지막으로 제안된 솔루션은 고유 시각적 충실도와 Unreal Engine 자체의 기타 이점(예: 셰이더 효율성)을 보여 주어야 합니다. 

이러한 지침에 따라 Happy Finish는 가능성을 브레인스토밍하기 시작했으며, 공간 상호 작용을 사용하여 브랜드 이름, 높은 가치의 제품을 전달하는 혼합 현실 경험에 대한 아이디어를 제시했습니다. 시계, 카메라, 자동차 및 프라이빗 자동차를 포함하는 다양한 개체를 고려한 후 Happy Finish는 2019년 영화 Ford vs. 표시줄에 표시된 것처럼 1966년 Ford가 Le Mans의 24시간 동안 Ford가 24시간 동안 브이너를 꺾을 때 널리 알려진 자동차 범례인 Ford GT40을 결정했습니다. 

기존 Happy Finish 클라이언트인 Ford에서 구매를 얻은 회사는 클래식 자동차 아이콘에 대한 새로운 관점을 제공하기로 했습니다.

## <a name="the-solution"></a>솔루션

이 작업은 2020년 5월 7일에 시작되었습니다. GT40 모델 파일을 가져온 후 3D 유명인은 다각형 모델, UV 매핑, 질감 맵 다시 그리기 및 해당 맵을 가능한 한 적은 수의 질감으로 압축하는 데 3주가 소요되었습니다. 한 기술가가 병렬로 작업하여 3D 아티스트의 출력을 벤치마킹하고, 지정된 대상 프레임 속도에 따라 최적의 질감 크기를 결정하고, Unreal에서 사용자 지정 셰이더를 적용하는 가장 좋은 방법을 파악했습니다. 이 모든 사전 프로덕션 작업은 디바이스 내 환경을 최적화하기 위해 수행되었습니다.

사전 프로덕션 작업이 완료된 후 Creative Director Alex 램버트가 사진을 입력했습니다. 그는 Ford와 을 시청하면서 시나리오 및 상호 작용에 대한 이야기를 함께 묶는 방법을 생각하면서 시작했습니다. 또한 LE Mans 경합의 시각적 개체 및 GT40 대시보드의 이미지와 같은 UI 디자이너에 대한 시각적 참조를 수집하고 사운드 디자이너를 위해 작동하는 GT40의 오디오 녹음을 수집했습니다.

설명이 정의되고 최적화된 사전 프로덕션 자산이 준비되면서, 동료 소프트웨어 개발자인인 요제프 브러가 참여하여 이 모든 것을 결합했습니다. Unreal용 MRTK가 릴리스되기 전에 Happy Finish가 수행한 이전 두 Unreal on-on-HoloLens 2 프로젝트의 개발자였습니다.

Unreal용 MRTK에서 제공하는 값은 초기에 분명하게 드러났으며, 1주일 만에 초기 프로토타입을 제공하는 데 도움이 되었습니다. 그는 램버트가 식별한 GT40의 주요 측면 각각에 대해 하나씩 세 가지 고유한 시나리오인 뛰어난 성능 및 엔지니어링을 구현했습니다. 각 시나리오에 대해, 은 MRTK를 사용하여 사전 프로덕션 단계의 최적화된 3D 자산을 다양한 공간 상호 작용에 통합했습니다. 

Unreal용 MRTK를 사용하면, C++에서 모든 것을 구현할 필요 없이 Visual Unreal Motion Graphics(UMG) UI 디자이너를 사용하여 각 시나리오를 빌드했습니다. MRTK 내의 UX 구성 요소 및 구성 요소를 포함하는 플러그 인인 [Unreal용 UX 도구는](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)코드 없는 끌어서 놓기 디자인 환경 내에서 입력 시뮬레이션, 시각적으로 손 조작 스크립팅, 누를 수 있는 단추, 3D 이미지 조작, 표면 자성 등을 위한 [Unreal Blueprints를](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) 제공했습니다.

"MrTK 이전에서는 Unreal을 사용하여 HoloLens 2 개발했습니다. 모든 공간 상호 작용을 C++로 직접 코딩해야 했기 때문입니다. "Unreal용 MRTK는 동일한 작업을 많이 수행했습니다. 초기 프로토타입에 필요한 시간을 절반으로 줄인 것으로 예상합니다."

프로토타입을 사용하여 팀은 환경을 구체화하기 위해 매주 반복을 시작했습니다. 램버트는 "이때 혼합 현실 캡처 기능과 Windows 장치 포털 도움이 되었습니다. "디자인 검토를 캡처하고, 피드백을 다른 사람에게 브로드캐스트하고, 변경 내용에 대해 공동 작업하는 데 사용했습니다. 이와 같이 격리된 상태에서 작업하는 것은 이러한 도구 없이는 불가능했을 것입니다."

![휠 구성 요소가 순서대로 배치된 Unreal 편집기 Ford GT40 앱 실행](images/ford-gt40-img-04.JPG)

램버트가 UI 요소의 위치 변경 또는 단추 동작 변경과 같은 변경 내용을 요청했을 때, 표시는 이를 구현했습니다. 일부 변경에는 작은 코드 조정이 필요했지만 대부분은 Unreal 비주얼 디자이너에서 처리되었습니다. "반복할 수 있는 속도가 얼마나 빠른지 에 대해 놀라워했습니다. "시간을 낭비하지 않았습니다. 디자이너를 변경한 다음, 재생을 눌러 디바이스에서 즉시 봅니다. MRTK가 작업을 간소화했습니다."

또한 이때는 모든 개발 도구가 프로덕션에 얼마나 준비되어 있었는지에 깊은 인상을 받았습니다. "코드에서 다시 구현하거나 최적화할 필요 없이 초기 프로토타입에서 최종 프로덕션까지 원활하게 진행했습니다.  

## <a name="the-final-build"></a>최종 빌드

Happy Finish는 2020년 7월 28일에 HoloLens 2 Ford GT40 Experience의 프로덕션을 완료하여 gt;경합차에 대한 새로운 관점을 제공했습니다. 환경은 시작 화면으로 시작한 다음, Ford 로고를 잡고 테이블이나 데스크톱과 같은 평면 화면에 배치하여 앵커를 설정하도록 사용자를 안내합니다. 

### <a name="beauty"></a>아름다움

**이 세그먼트는** 사용자에게 GT40 구성기를 제공합니다. 이 구성기는 자동차 디스플레이에서 실제 자동차를 표시하는 방법과 비슷하게 회전 받음으로 GT40을 표시합니다. 사용자는 다양한 휠 옵션을 적용하고, 다른 색 구성표 중에서 선택하고, 문과 트렁크를 열고 닫을 수 있습니다(또는 부팅은 UK에서 호출할 때). 모든 경험을 통해 사용자는 자동차를 픽업하고 더 자세히 보기 위해 자유롭게 조작할 수 있습니다.

![디바이스에서 실행되는 GT40 구성기의 애니메이션 GIF](images/ford-gt40-img-05.gif)

### <a name="performance"></a>성능

**성능** 세그먼트는 GT40의 속도와 내구성을 보여줍니다. 음성 검색은 자동차 개발 방법을 설명하고, 테스트 트랙에서 GT40의 동작을 보여주는 3D 시각적 개체와 함께 Ford's Kingman,구호에서 속도를 내는 것으로 시작합니다. 성능 세그먼트 소개가 끝나면 음성을 통해 사용자에게 "Le Mans 단추를 눌러 경합을 적중"하라는 메시지가 표시됩니다.

![디바이스에서 실행되는 GT40 속도 및 내구성 앱의 애니메이션 GIF](images/ford-gt40-img-06.gif)

성능 세그먼트의 두 번째 부분에서는 매년 프랑스 Le Mans 근처의 Circuit de la Sarthe에서 열리는 Le Mans 24시간에서 드라이버가 경험할 수 있는 조건 범위 아래의 GT40을 보여 주며, 3D 보기는 Le Mans 트랙에서 움직이는 자동차를 보여 줍니다. 단추를 통해 자동차를 더 빠르거나 느리게 만들 수 있습니다. GT40의 아날로그 속도계 및 tachometer 이미지는 백그라운드에 더 많은 경합 원격 분석이 표시되어 있는 경합 보기 위에 떠 있습니다. 사용자는 낮과 야간 보기 사이를 전환하고 건성 및 습한 주행 상태 사이를 전환하여 Ken Miles와 다른 GT40 드라이버가 실제 경합에서 경험했던 사실적이고 실제적인 관점을 제공합니다.

### <a name="engineering"></a>공학

Ford GT40 Experience의 **엔지니어링** 세그먼트는 다른 모든 팀이 필요로 하는 20-30분과 비교하여 Ford가 경합에서 이기는 데 도움이 되는 엔지니어링 혁신 중 하나인 제방 로터와 패드를 1분 이내에 변경하는 기능을 보여 줍니다. 직관적인 제스처를 사용하여 사용자는 GT40 휠 및 브레이크 어셈블리의 자세한 3D 모델을 조작할 수 있습니다. 어셈블리를 확장하기 위해 사용자는 lug wrench를 선택하고, 휠의 가운데 잠금에 맞추고, 시계 반대 방향으로 바꾼 다음, 휠에서 끌어 냅니다. 다른 제스처는 쇠를 벗은 로터와 패드를 제거하고, 새 제스처로 바꾸고, 어셈블리를 축소하고, 가운데 잠금을 다시 보안하는 데 사용됩니다. 백그라운드에서 타이머는 경과된 시간을 표시하여 Le Mans의 Pit 팀만큼 빠르게 프로세스를 완료할 수 있는지 확인합니다.

![디바이스에서 실행되는 GT40 엔지니어링 환경의 애니메이션 GIF](images/ford-gt40-img-07.gif)

Ford GT40 환경은 [Microsoft 스토어에서 다운로드할](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)수 있으며, HoloLens 2 있는 모든 사용자가 Happy Finish가 어떻게 경합용 자동차의 새로운 관점을 가져왔는지 살펴볼 수 있습니다.

### <a name="getting-impressive-visual-fidelity"></a>뛰어난 시각적 충실도 얻기

Ford GT40 Experience에서 지원하는 공간 상호 작용의 범위는 그 자체로는 인상적이지만, 경험에서 제공하는 독창성과 시각적 충실도는 정말 뛰어난 요소입니다. 3D 모델을 최적화하고 Unreal 사용자 지정 셰이더를 사용하여 Happy Finish는 앱의 성능 세그먼트 크기가 315,000개에 근접하더라도 초당 60프레임 목표를 달성했습니다. 

램버트는 "유동적이고 직관적인 상호 작용 세트를 일관되고 매력적인 스토리로 결합할 수 있었던 것에 매우 만족합니다" 라고 말합니다. "분명히 HoloLens 2 Unreal Engine의 강력한 성능은 더 흥미롭고 흥미로운 혼합 현실 환경을 위한 새로운 기회의 세계를 엽니다. 호환되지 않는 시각적 충실도가 항상 HoloLens 2 엔터프라이즈 애플리케이션의 최종 목표는 아니지만, 이 경우 HoloLens 2 Unreal에 대한 지원이 매우 중요해집니다."

### <a name="rapid-solution-delivery"></a>신속한 솔루션 제공

최종 사용자 Ford GT40 Experience는 12주 이내에 완료된 전체 프로젝트(사전 프로덕션에서 최종 배달까지)를 통해 Happy Finish가 얼마나 빨리 배달했는지를 매우 중요합니다. 요약하자면, 프로젝트는 1088시간의 노력을 소비했으며, 다음과 같이 세분화되었습니다. 즉, Creative Director(80시간), UX 디자이너(56시간), UI 디자이너(40시간), 사운드 디자이너(40시간), 3D/기술 과학자(328시간), 소프트웨어 개발자(408시간), 기술 디렉터(40시간), 생산자(56시간) 및 품질 보증(40시간)이 있습니다.

"전반적으로 원래 프로젝트 예상치에 매우 근접했습니다." 회사의 대화형 사업부를 앞장서고 있는 Happy Finish의 최고 혁신 책임자인 Daniel Cheetham은 말합니다. "Ford GT40 환경은 약정한 예산으로 단 몇 개월 만에 HoloLens 2 앱을 완료할 수 있지만 여전히 매우 영향력 있는 결과를 제공한다는 것을 증명합니다." 

개발 관점에서 볼 때, HoloLens 2 Unreal에 대한 이전 경험을 기반으로 하여, Unreal용 MRTK가 자신의 부분에 필요한 총 시간과 노력을 절반으로 줄인 것으로 추정합니다. 또한 MRTK를 통해 HoloLens 2 작업한 적이 없는 개발자가 어떻게 시작할 수 있는지도 설명합니다. "다른 개발자가 혼합 현실에 관심이 있다고 말할 때 바로 이동하여 HoloLens 2 개발 스택 및 MRTK를 설치하고, 이를 위해 이동하는 것이 좋습니다. MRTK를 사용하면 앱을 빠르고 쉽게 빌드할 수 있으며, Unreal 시각적 편집기가 잘 작동하므로 HoloLens 2 디바이스를 시작할 필요가 없습니다. 전혀 복잡하지 않습니다. 모든 것이 작동합니다."

### <a name="potential-azure-service-enhancements"></a>잠재적인 Azure 서비스 개선 사항

램버트는 Azure 혼합 현실 서비스를 사용하여 Ford GT40 환경을 개선할 수 있는 여러 가지 방법을 볼 수 있습니다. 예를 들어 Azure Spatial Anchors 사용하여 실제 세계에 고정된 다중 사용자 환경을 제공합니다. "독창적인 관점에서 볼 때 Azure 공간 고정은 제공 하는 기능을 통해 실제 세계 내에서 3D 콘텐츠나 관심 영역을 매핑하고, 유지 하 고, 복원 하는 기능을 통해 완전히 새로운 범위를 개방 했습니다."

또한 램버트는 azure 원격 렌더링 또는 Azure에서 앱 스트리밍을 사용 하 여 보다 자세 하 고 복잡 한 3D 모델로 작업 하는 동안 원하는 프레임 속도를 달성할 수 있는 방법을에서는 합니다. "우리는이에 대해 설명 하는 60 프레임의 장치 목표를 충족 하기 위해 Unreal에서 매우 최적화 된 사용자 지정 셰이더를 구현 해야 했습니다. "Azure 원격 렌더링을 사용 하면 훨씬 더 많은 작업을 수행할 수 있으며, 다각형 모델을 최적화 하 고 텍스처 지도를 다시 그리는 데 필요한 만큼의 작업을 수행 하지 않고 훨씬 더 쉽게 수행할 수 있습니다."

### <a name="endless-new-possibilities"></a>무한 한 새 가능성

그렇다면 행복 한 마무리는 어떻게 되나요? Ford GT40 환경에 대 한 Ford의 피드백은 대다수 긍정적인로, 향후 HoloLens 2 프로젝트에서 행복 한 마무리와 Ford 간의 추가 토론이 제공 됩니다. Ford와의 관계 이외에는 이미 HoloLens 2에서 새 프로젝트를 시작 하 고 있습니다. 여기서는 unreal의 mrtk가 대부분의 사용자 환경에 대 한 기본 구성 블록이 됩니다. 

"우리는 항상 각 새 프로젝트에 대해 기술 독립적인 방법을 유지 관리 하 고, 클라이언트에서 원하는 결과를 얻기 위해 가장 적합 한 도구 집합을 제안 합니다." 라고 Cheetham. "즉, HoloLens 2는 혼합 현실에 대 한 비 사실상 골드 표준으로 등장 했습니다. 특히 기업에서는 장치 기능과 지원 에코 시스템의 단순성 측면에서 다른 모든 옵션을 접근."

Cheetham에 따르면 전 세계 전염병는 잠재적 고객 간에 다양 하 게 혼합 된 현실에서 새로운 관심사를 때 엄청난 합니다. "50%가 혼합 현실 옵션을 논의 하기 위해 열리는 잠재적 클라이언트의 약%가 되었습니다. "사용자가 시험해 볼 수 있도록 하는 것이 중요 합니다. 모든 경우에 혼합 현실에 대 한 정보를 제공할 수 있지만, 자신에 대 한 경험을 제공 하는 HoloLens 2을 제공 하는 즉시 게임 교환기가 될 수 있습니다. HoloLens 2에서 unreal Engine에 대 한 지원은 제공할 수 있는 값만 늘리기 때문에 가장 까다로운 클라이언트를 충족 하는 시각적으로 매력적인 환경을 제공할 수 있습니다. "

## <a name="try-it-out"></a>기능 직접 사용해 보기

> [!div class="nextstepaction"]
> [Ford GT40 앱 다운로드](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

GitHub에 [대 한 HoloLens 2 또는 mrtk](https://github.com/microsoft/MixedRealityToolkit-Unreal) 의 [혼합 현실 개발 소개를](../development.md) 확인 하세요.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->