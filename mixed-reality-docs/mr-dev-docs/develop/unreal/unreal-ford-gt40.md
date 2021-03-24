---
title: Ford GT40 환경
description: Ford GT40 mixed reality 응용 프로그램을 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 장치에 배포, PC, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
appliesto:
- HoloLens 2
ms.openlocfilehash: d610907123898471e92598da134e9c4d77a195e9
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909142"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Ford GT40 환경 만들기

MRTK (Mixed Reality Toolkit)를 사용 하면 독창적인 프로덕션 회사의 행복 한 완료는 Ford GT40에 대 한 새로운 큐브 뷰를 제공 하는 HoloLens 2 환경을 제공 하며,이는 24 시간 Le Mans에서 Ferrari를 갱신 하는 전설의 레이스 자동차입니다.

사용자는 다양 한 자연스럽 고 직관적인 공간 상호 작용을 사용 하 여, Unreal 엔진에서 제공 하는 높은 시각적 충실도를 활용 하는 방식으로 제공 되는 GT40's의 장점, 성능 및 엔지니어링을 탐색할 수 있습니다. 전체 프로젝트에 대 한 소프트웨어 개발이 3 개월 이내에 단일 개발자에 의해 완료 되었습니다 .이는 MRTK에서 Unreal의 시각적 스크립팅 및 디자인 환경에 사용할 수 있게 되었습니다.

> [!div class="nextstepaction"]
> [Ford GT40 앱 다운로드](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Ford GT40 주인공 이미지](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>Ask

행복 한 완료는 Ford, Microsoft, Nike, Netflix, Vodafone 및 기타 가사 이름을 포함 하는 클라이언트 베이스를 사용 하는 세계 최고의 창작 프로덕션 회사 중 하나입니다. 이 회사는 최고 수준의 사진 재손질 기관으로 시작 하 고, 3D 공간 디자인 및 상호 작용을 통해 공헌를 모던 스토리텔링 확장 하기 전에 필름이 나 CGI로 분기 합니다.

중부-2020에서 Microsoft는 unreal의 새 Mixed Reality Toolkit (MRTK)에서 사용 하도록 설정 된 가능성을 보여 주는 데모 앱을 생성 하는 데 도움이 될 것입니다 .이는 Unreal 엔진에서 HoloLens 2에 대 한 지원을 기반으로 합니다. 이 시점에서 회사는 이미 두 개의 성공적인 실시간 HoloLens 2 프로젝트를 분리 하 고 있습니다. 두 가지 모두 전역으로 인식 되는 소비자 브랜드에 대 한 것 이었습니다 .이는 클라이언트의 고유한 고급 제품을 최대한 활용 하는 데 필요한 내부 R&D/B2B 판매 도구용 내부 R D/B2B 판매 도구입니다.

솔루션 자체는 완료 될 때까지 남은 것은 아니지만 몇 가지 주요 지침을 충족 해야 했습니다. 먼저, 게임 업계 외부에서 HoloLens 2에서 Unreal의 유틸리티를 설명 하는 엔터프라이즈 시나리오에 집중 해야 했습니다. 둘째, 장치 전용 이어야 합니다. 즉, 대상 프레임 속도와 시각적 품질을 얻기 위해 네트워크 연결 및 외부 처리 기능을 요구 하지 않고도 독립 실행형 데모로 사용할 수 있습니다. 셋째, MRTK에서 지 원하는 직관적인 상호 작용의 범위를 원활 하 고 자연 스러운 환경으로 혼합 해야 합니다. 마지막으로, 제안 된 솔루션은 셰이더 효율성과 같이, Unreal 엔진 자체의 내재 된 시각적 충실도 및 기타 이점을 보여 줍니다. 

이러한 지침을 고려 하 여이에 대 한 의견을 작성 하기 시작 하 고, 공간 상호 작용을 사용 하 여 브랜드 이름, 높은 가치 제품의 가치를 전달 하는 혼합 현실 환경의 아이디어를 제공 합니다. Watch, 카메라, 자동차 및 개인 젯을 포함 하는 다양 한 개체를 고려한 후에는 2019 Ferrari 필름이 Mans 및 Blockbuster에 표시 된 것 처럼 24 시간 Ford의 24 시간 Ford Ferrari에서 1966의 notoriety를 달성 하는 자동차 범례 인 Ford GT40이 궁극적으로 결정 됩니다. 

기존 행복 한 마무리 클라이언트 인 Ford에서 구매할 때 회사는 클래식 자동차 아이콘에 새로운 큐브 뷰를 제공 하도록 설정 했습니다.

## <a name="the-solution"></a>솔루션

5 월 7 일에 시작 되는 작업은 2020입니다. GT40 모델 파일을 가져온 후 3D 음악가는 3 주가 다각형 모델을 최적화 하 고, UV 매핑을 다시 그리고, 질감 맵을 다시 그리고, 이러한 지도를 가능한 한 적은 질감으로 압축 했습니다. 기술 음악가는 3D 음악가의 출력을 벤치 마크 하 고, 대상 프레임 속도를 지정 하 여 최적의 질감 크기를 결정 하 고, Unreal에서 사용자 지정 셰이더를 적용 하는 가장 좋은 방법을 파악 하기 위해 병렬로 작동 했습니다. 이러한 사전 프로덕션 작업은 모두 장치 환경을 최적화 하기 위해 수행 되었습니다.

Creative Director Alex 램버트는 사전 프로덕션 작업이 완료 된 후에 사진을 입력 했습니다. Ford와 Ferrari을 감시 하 여 시나리오와 상호 작용에 대 한 설명을 함께 활용 하는 방법을 고려 하 여 시작 했습니다. 또한 GT40 대시보드의 이미지 및 Le Mans 트랙의 시각적 개체와 같은 UI 음악가의 시각적 참조를 수집 하 고, 사운드 디자이너에 대 한 작동 중인 GT40 오디오 녹음을 수집 했습니다.

Freelance software developer Jose Rodriguez는 잘 정의 되 고 최적화 된 사전 프로덕션 자산을 포함 하도록 등록 되었습니다. Unreal의 MRTK가 해제 되기 전에 완료 된 이전 두 개의 Rodriguez 2 프로젝트에서 개발자가 왔습니다.

Unreal에 대해 MRTK에서 제공 하는 값은 초기에 Rodriguez을 제공 하는 데 도움이 됩니다. 램버트의 장점, 성능 및 엔지니어링 이라는 GT40의 주요 측면 각각에 대해 세 가지 고유한 시나리오를 구현 했습니다. 각 시나리오에 대해 Rodriguez는 MRTK를 사용 하 여 사전 프로덕션 단계의 최적화 된 3D 자산을 공간 상호 작용의 범위에 통합 했습니다. 

Unreal의 경우 MRTK를 사용 하 여 c + +에서 모든 항목을 구현 하지 않고 시각적 Rodriguez UMG (실제 동작 그래픽) UI 디자이너를 사용 하 여 각 시나리오를 구축 했습니다. [Unreal 용 Ux 도구](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), MRTK 내에서 ux 구성 요소 및 구성 요소를 포함 하는 플러그 인은 입력 시뮬레이션에 대 한 [실제 청사진](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) 을 제공 하지 않으며, 시각적 스크립팅 상호 작용, pressable 단추, 3d 이미지 조작, 표면 자기 등은 코드 없는 끌어서 놓기 디자인 환경에서 모두 제공 합니다.

"프리 MRTK, Unreal을 사용 하 여 HoloLens 2를 개발 하는 것은 모든 공간 상호 작용이 직접 코딩 되어야 하 고 c + +에서" Rodriguez "라고 했기 때문에 다소 지루한 였습니다. "Unrtk for Real은 매우 간단한 동일한 작업을 수행 했습니다. 초기 프로토타입에 필요한 시간을 절반으로 줄일 수 있습니다. "

직접 프로토타입을 사용 하는 경우 팀에서 매주 반복을 시작 하 여 환경을 구체화 했습니다. "이는 혼합 현실 캡처 기능 및 Windows 장치 포털이 실제로 도움이 되는 경우입니다." 리콜 램버트. "필자는이를 사용 하 여 내 디자인 리뷰를 캡처하고 사용자 의견을 다른 사용자에 게 브로드캐스트합니다. 이러한 도구 없이는 불가능 한 것 처럼 격리 작업을 수행 합니다. "

![순환 구성 요소를 순서 대로 배치 하 여 실행 되는 unreal editor Ford GT40 app](images/ford-gt40-img-04.JPG)

UI 요소의 위치를 변경 하거나 단추의 동작을 변경 하는 것과 같이 램버트 요청 된 변경으로 구현 Rodriguez 구현 했습니다. 약간의 변경으로 인해 작은 코드를 조정 해야 하는 경우 대부분의 경우 대부분의 visual 디자이너에서 처리 됩니다. "정말 빨리 반복 될 수 있습니다." 라고 Rodriguez. "시간을 낭비 하지 않았습니다. 디자이너에서 변경한 다음 play를 눌러 장치에서 바로 볼 수 있습니다. MRTK는 정말로 작업을 간소화 했습니다. "

또한 Rodriguez는 프로덕션이 모든 개발 도구를 준비 하는 방법에 따라 결정 됩니다. "우리는 코드에서 작업을 다시 구현 하거나 최적화 하지 않고도 초기 프로토타입에서 최종 프로덕션을 통해 원활 하 게 진행 되었습니다." 라는 메시지가 표시 됩니다.  

## <a name="the-final-build"></a>최종 빌드

2020 년 7 월 28 일에 Ford GT40 환경의 최신 큐브 뷰를 완료 하 여 전설의 레이스 자동차에 대 한 새로운 관점을 제공 합니다. 이 환경은 시작 화면으로 시작 하 고, Ford 로고를 사용 하 여 테이블 또는 데스크톱과 같은 평면에 배치 하 여 앵커를 설정 하도록 안내 합니다. 

### <a name="beauty"></a>장점은

이에 대 한 **장점** 세그먼트는 GT40 구성 기를 제공 합니다 .이 구성 기는 자동차 표시에서 실제 자동차를 표시 하는 방법과 유사 하 게 회전 페데스탈에 GT40을 표시 합니다. 사용자는 다양 한 휠 옵션을 적용 하 고, 다양 한 색 구성표를 선택 하 고, 사용자가 영국에서 호출 하는 문과 트렁크를 열거나 닫을 수 있습니다. 사용자는 모든 경험 경험을 통해 자동차를 선택 하 여 더 자세히 살펴볼 수 있습니다.

![장치에서 실행 되는 GT40 configurator의 애니메이션 GIF](images/ford-gt40-img-05.gif)

### <a name="performance"></a>성능

**성능** 세그먼트는 GT40's 속도 및 내구성을 보여 줍니다. Voiceover은 자동차를 개발한 방법을 설명 하 고, Ford의 킹 속도로에서 애리조나를 증명 하는 grounds에 배치 하 고, 테스트 트랙에서 움직임을 GT40 하는 3D 시각적 개체를 사용 하 여 시작 합니다. 성능 세그먼트가 소개 될 때 voiceover은 "Le Mans 단추를 눌러 트랙에 도달 했습니다." 라는 메시지를 표시 합니다.

![장치에서 실행 되는 GT40 속도 및 내구성 앱의 애니메이션 GIF](images/ford-gt40-img-06.gif)

성능 세그먼트의 두 번째 부분은 GT40를 소개 합니다 .이는 24 시간 Le Mans에서 발생할 수 있으며,이는 회로 de la Sarthe near Le Mans, 프랑스에서 매년 보유 합니다. 3D 보기는 자동차를 더 빠르거나 더 느리게 만들기 위해 제공 되는 단추를 사용 하 여 Le Mans track의 움직임을 표시 합니다. GT40's 아날로그 속도계 및 tachometer float의 이미지는 배경 화면에 더 많은 경합 원격 분석이 표시 됩니다. 사용자는 일과 야간 보기 사이를 전환 하 고, 켄은 마일 및 기타 GT40 드라이버의 실제 경합에 대 한 현실적인 관점을 제공 합니다.

### <a name="engineering"></a>공학

Ford GT40 환경에 대 한 **엔지니어링** 부문에서는 다른 모든 팀에서 요구 하는 20-30 분에 비해 브레이크 rotors를 변경 하 고 1 분 이내에 pad 하는 기능을 제공 하는 엔지니어링 혁신 중 하나를 소개 합니다. 직관적인 제스처를 사용 하면 사용자가 GT40 휠 및 브레이크 어셈블리의 자세한 3D 모델을 조작할 수 있습니다. 어셈블리를 확장 하기 위해 사용자는 들고 렌치를 선택 하 고, 색상환의 중심 잠금에 맞추고, 시계 반대 방향으로 전환 하 고 나 서 휠 밖으로 끌어옵니다. 다른 제스처는 마모 된 브레이크 rotors 및 패드를 제거 하 고, 새 항목으로 대체 하 고, 어셈블리를 축소 하 고, 가운데 잠금을 시작 하는 데 사용 됩니다. 백그라운드에서 타이머는 경과 된 시간을 표시 하 여 사용자가 Le Mans에서 pit crew 만큼 신속 하 게 프로세스를 완료할 수 있는지 확인 합니다.

![장치에서 실행 되는 GT40 엔지니어링 환경의 애니메이션 GIF](images/ford-gt40-img-07.gif)

Ford GT40 환경은 [Microsoft store에서 다운로드할](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)수 있으며 HoloLens 2를 사용 하는 모든 사용자가 전설의 레이스 자동차에 대 한 새로운 관점을 만드는 방법을 살펴볼 수 있습니다.

### <a name="getting-impressive-visual-fidelity"></a>인상적인 시각적 충실도 얻기

Ford GT40 환경에서 지원 되는 공간 상호 작용의 범위는 매우 인상적 이지만 경험을 통해 효과를 제공 하는 것은 무엇을 의미 하는 것입니다. 3D 모델을 최적화 하 고, Unreal 사용자 지정 셰이더를 사용 하 여, 앱의 성능 세그먼트가 크기의 315000에 근접 하는 경우에도 초당 60 프레임의 목표에 도달 하는 것을 완료 합니다. 

"저는 유체의 집합을 일관 되 고 유용한 설명으로 사용 하는 방법에 대해 매우 만족 하 고 있습니다." 라고 램버트. "HoloLens 2에서 Unreal Engine의 강력한 기능을 통해 더욱 놀라운이 고 흥미로운 현실 경험을 얻을 수 있는 기회를 누릴 수 있습니다. 손상 되지 않은 시각적 충실도는 HoloLens 2의 엔터프라이즈 응용 프로그램에 대 한 최종 목표가 아닐 수 있습니다. 그러나이 경우에는 HoloLens 2에서 Unreal의 지원이 매우 중요 합니다. "

### <a name="rapid-solution-delivery"></a>신속한 솔루션 제공

최종 사용자 Ford GT40 환경에서는 최종 사용자에 게 전체 프로젝트 (사전 프로덕션에서 최종 배달까지)가 12 주 이내에 완료 될 때까지 얼마나 빨리 배달 됩니다. 요약 하자면, 프로젝트는 1088 시간의 노력을 사용 합니다. 독창적인 감독 (80 시간), UX 디자이너 (56 시간), UI 디자이너 (40 시간), 사운드 디자이너 (40 시간), 3D/기술 음악가 (328 시간), 소프트웨어 개발자 (408 시간), 기술 담당 이사 (40 시간), 생산자 (56 시간) 및 품질 보증 (40 시간)으로 분류 됩니다.

"우리는 전반적으로 원래 프로젝트 추정치와 긴밀 하 게 Daniel Cheetham, 고객의 대화형 부서를 담당 하는 행복 한 마무리에서 최고 혁신 책임자를 제공 하 고 있습니다. "Ford GT40 환경은 최고 수준의 예산으로 한 달만에 최고 품질의 HoloLens 2 앱을 완료할 수 있지만 여전히 매우 뛰어난 결과를 제공 합니다." 

이전에는 HoloLens 2를 사용 하 여 이전 경험을 기반으로 하는 개발 관점에서, Rodriguez는 해당 부분에 필요한 총 시간과 노력을 계산 하지 않는 것으로 예상 합니다. 또한 MRTK를 사용 하 여 HoloLens 2로 작업 한 적이 없는 개발자에 게 도움을 주는 방법을 설명 합니다. "다른 개발자가 혼합 현실에 관심이 있다고 생각 하는 경우, 지금 바로 이동 하 여 HoloLens 2 development stack 및 MRTK를 설치 하 고이에 대해 이동 하는 것이 좋습니다. MRTK를 사용 하면 쉽고 간편 하 게 앱을 빌드할 수 있으며, 실제 사용 하지 않는 visual editor는 시작 하기 위해 HoloLens 2 장치가 필요 하지 않습니다. 모든 것은 복잡 하지 않습니다.

### <a name="potential-azure-service-enhancements"></a>잠재적 Azure 서비스 향상

램버트는 azure mixed reality 서비스를 사용 하 여 실제 환경에 고정 된 다중 사용자 환경을 제공 하기 위해 Azure 공간 앵커를 사용 하는 등의 Ford GT40 환경을 개선 하는 여러 가지 방법을 볼 수 있습니다. "독창적인 관점에서 볼 때 Azure 공간 고정은 제공 하는 기능을 통해 실제 세계 내에서 3D 콘텐츠나 관심 영역을 매핑하고, 유지 하 고, 복원 하는 기능을 통해 완전히 새로운 범위를 개방 했습니다."

또한 램버트는 azure 원격 렌더링 또는 Azure에서 앱 스트리밍을 사용 하 여 보다 자세 하 고 복잡 한 3D 모델로 작업 하는 동안 원하는 프레임 속도를 달성할 수 있는 방법을에서는 합니다. "우리는이에 대해 설명 하는 60 프레임의 장치 목표를 충족 하기 위해 Unreal에서 매우 최적화 된 사용자 지정 셰이더를 구현 해야 했습니다. "Azure 원격 렌더링을 사용 하면 훨씬 더 많은 작업을 수행할 수 있으며, 다각형 모델을 최적화 하 고 텍스처 지도를 다시 그리는 데 필요한 만큼의 작업을 수행 하지 않고 훨씬 더 쉽게 수행할 수 있습니다."

### <a name="endless-new-possibilities"></a>무한 한 새 가능성

그렇다면 행복 한 마무리는 어떻게 되나요? Ford GT40 환경에 대 한 Ford의 피드백은 대다수 긍정적인로, 향후 HoloLens 2 프로젝트에서 행복 한 마무리와 Ford 간의 추가 토론이 제공 됩니다. Ford와의 관계 이외에는 이미 HoloLens 2에서 새 프로젝트를 시작 하 고 있습니다. 여기서는 Unreal의 MRTK가 대부분의 사용자 환경에 대 한 기본 구성 블록이 됩니다. 

"우리는 항상 각 새 프로젝트에 대해 기술 독립적인 방법을 유지 관리 하 고, 클라이언트에서 원하는 결과를 얻기 위해 가장 적합 한 도구 집합을 제안 합니다." 라고 Cheetham. "즉, HoloLens 2는 혼합 현실에 대 한 비 사실상 골드 표준으로 등장 했습니다. 특히 기업에서는 장치 기능과 지원 에코 시스템의 단순성 측면에서 다른 모든 옵션을 접근."

Cheetham에 따르면 전 세계 전염병는 잠재적 고객 간에 다양 하 게 혼합 된 현실에서 새로운 관심사를 때 엄청난 합니다. "50%가 혼합 현실 옵션을 논의 하기 위해 열리는 잠재적 클라이언트의 약%가 되었습니다. "사용자가 시험해 볼 수 있도록 하는 것이 중요 합니다. 모든 경우에는 혼합 현실에 대 한 정보를 볼 수 있지만, HoloLens 2를 직접 경험해 볼 수 있습니다. HoloLens 2에서 Unreal Engine에 대 한 지원에는 제공 되는 값만 증가할수록 가장 까다로운 클라이언트를 충족 하는 시각적으로 매력적인 환경을 제공할 수 있습니다. "

## <a name="try-it-out"></a>기능 직접 사용해 보기

> [!div class="nextstepaction"]
> [Ford GT40 앱 다운로드](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

GitHub에서 [Unreal의 경우 HoloLens 2 또는 Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unreal) 에 대 한 [혼합 현실 개발 소개를](../development.md) 확인 하세요.

## <a name="what-people-are-saying"></a>사용자 의견

*C + +에서 모든 공간 상호 작용을 직접 코딩 해야 하기 때문에 "이전 MRTK는 Unreal을 사용 하 여 HoloLens 2를 개발 하는 것이 다소 지루한 였습니다. Unreal의 MRTK는 이와 동일한 많은 작업을 간단 하 게 만들었습니다. 초기 프로토타입에 필요한 시간을 절반으로 줄일 수 있습니다. "*
- Jose Rodriguez, 소프트웨어 개발자

*"Ford GT40 환경은 최고 수준의 예산으로 한 달만에 최고 품질의 HoloLens 2 앱을 완료할 수 있지만 여전히 매우 뛰어난 결과를 제공 합니다."*  
- Daniel Cheetham, 최고 혁신 책임자, 행복 한 마무리

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