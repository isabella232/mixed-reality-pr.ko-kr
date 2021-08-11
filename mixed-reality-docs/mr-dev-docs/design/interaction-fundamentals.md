---
title: 직관적 상호 작용
description: 혼합 현실 플랫폼 전반에 얽혀 있는 간단하고 직관적인 상호 작용이라는 철학을 알아봅니다.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 응시, 응시 타깃팅, 상호 작용, 디자인, hololens, MMR, 멀티모달, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens
ms.openlocfilehash: 6fddec8b0ed9b8f2230b963d1a795b7309473d7f91e32dd8382b747b6f3655da
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222788"
---
# <a name="introducing-instinctual-interactions"></a>직관적인 상호 작용 소개

![수동으로 원거리 조작](images/04_InteractionFundamentals.png)

간단하고 직관적인 상호 작용이라는 철학은 MR(혼합 현실) 플랫폼 전반에 얽혀 있습니다. 애플리케이션 디자이너와 개발자가 고객에게 쉽고 직관적인 상호 작용을 제공할 수 있도록 하는 3단계를 살펴보았습니다. 

첫째, 센서와 입력 기술이 다중 모드 상호 작용 모델에 결합되도록 했습니다. 이러한 상호 작용 모델에는 자연어 입력과 함께 손 및 시선 추적이 포함됩니다. 연구에 따르면, 개별 입력보다는 다원적인 프레임워크 내의 설계와 개발이 직관적인 환경을 만드는 열쇠라고 합니다.

둘째, 여러 HoloLens 디바이스(HoloLens 2, HoloLens(1세대) 또는 HoloLens 및 VR)를 대상으로 하는 개발자가 많다는 점을 파악했습니다. 따라서, 상호 작용 모델이 여러 디바이스에서 작동하도록 설계하고 있습니다(입력 기술이 디바이스마다 다를 수 있음). 예를 들어 6DoF 컨트롤러 및 HoloLens 2가 있는 Windows 몰입형 헤드셋의 원거리 상호 작용은 모두 동일한 어포던스와 패턴을 사용합니다. 이렇게 하면 디바이스 간 애플리케이션을 쉽게 개발할 수 있고 자연스러운 느낌을 사용자 상호 작용에 제공합니다. 

MR에서 효과적이고 매력적이며 신비한 수천 가지의 상호 작용이 가능하다는 것을 인식하는 한편, 의도적으로 단일 상호 작용 모델을 애플리케이션에 사용하는 것이 사용자의 성공과 뛰어난 환경을 보장하는 가장 좋은 방법임을 알게 되었습니다. 따라서, 이 상호 작용 지침에는 다음 세 가지가 포함됩니다.
* 세 가지 주요 상호 작용 모델 및 각각에 필요한 구성 요소와 패턴에 대한 구체적인 지침
* 당사 플랫폼이 제공하는 기타 혜택에 대한 추가 지침
* 개발 시나리오에 적합한 상호 작용 모델을 선택하는 데 참고할 수 있는 일반 지침

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a>기본 손 추적 및 본능적 상호 작용 데모

아래의 **홀로그램 디자인 - 머리 추적 및 시선 추적** 동영상 데모를 확인한 다음 보다 구체적인 항목으로 이동합니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

*이 동영상은 "홀로그램 디자인" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드하여 즐겨 보세요.*

## <a name="multimodal-interaction-models"></a>멀티모달 상호 작용 모델

Microsoft의 연구와 고객의 피드백에 따라 세 가지 기본 상호 작용 모델이 대부분의 혼합 현실 환경에 적합하다는 것이 발견되었습니다. 여러 가지 면에서 상호 작용 모델은 워크플로를 완료하는 방법에 대한 사용자의 심리 모델입니다. 각 상호 작용 모델은 고객의 요구에 맞게 최적화되어 있으며 올바르게 사용될 때 편리하고 강력하며 유용합니다. 

아래 차트는 간략한 개요입니다. 각 상호 작용 모델 사용에 대한 자세한 정보는 아래 페이지에서 이미지와 코드 샘플로 연결됩니다. 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>모델</strong></td>
        <td><strong>예제 시나리오</strong></td>
        <td><strong>적합</strong></td>
        <td><strong>하드웨어</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></td>
        <td>3D 공간 환경(예: 공간 레이아웃 및 디자인, 콘텐츠 조작 또는 시뮬레이션).</td>
        <td>새로운 사용자에게 음성, 시선 추적 또는 헤드 게이즈(head-gaze)와 함께 사용하면 좋습니다. 학습 기간이 낮습니다. 손 추적 및 6DoF 컨트롤러에서 UX가 일관적입니다.</td>
        <td>HoloLens 2<br>몰입형 헤드셋</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">핸즈프리</a></td>
        <td>현장 학습, 유지 보수와 같이 사용자의 손을 다른 일에 사용하고 있는 상황에 맞는 환경.</td>
        <td>어느 정도 학습이 필요합니다. 손을 사용할 수 없는 경우, 디바이스가 음성 및 자연어와 조화를 잘 이룹니다.</td>
        <td>HoloLens 2<br>HoloLens(1세대)<br>몰입형 헤드셋</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">응시 및 커밋</a></td>
        <td>3D 프레젠테이션이나 데모와 같은 클릭 환경</td>
        <td>모바일이 아닌 HMD에 대한 교육이 필요합니다. 액세스 가능한 컨트롤러에 가장 적합합니다. HoloLens(1세대)에 가장 적합합니다.</td>
        <td>HoloLens 2<br>HoloLens(1세대)<br>몰입형 헤드셋<br>모바일 AR</td>
    </tr>
</table>
<br>

사용자 상호 작용 환경의 차이를 방지하려면 단일 모델에 대한 지침을 처음부터 끝까지 따르는 것이 가장 좋습니다.

아래 섹션에서는 이러한 상호 작용 모델 중 하나를 선택하고 구현하는 단계를 설명합니다.  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a>이 페이지를 끝까지 마치면 다음에 대한 지침을 이해할 수 있습니다.
 
* 고객을 위한 상호 작용 모델 선택
* 상호 작용 모델 구현
* 상호 작용 모델 간 전환
* 다음 단계 디자인


## <a name="choose-an-interaction-model-for-your-customer"></a>고객을 위한 상호 작용 모델 선택

일반적으로 개발자와 작성자는 고객이 가질 수 있는 상호 작용 유형에 대해 충분히 생각합니다. 고객 중심의 설계 방식을 권장하기 위해, 아래 지침에 따라 고객에게 최적화된 상호 작용 모델을 선택하는 것이 좋습니다.

### <a name="why-follow-this-guidance"></a>이 지침을 따르는 이유

* 신체적/인지적 노력, 직관성 및 학습 가능성을 포함하여 객관적이고 주관적인 기준에 따라 상호 작용 모델을 테스트합니다. 
* 상호 작용이 다르기 때문에, 시각/오디오 어포던스 및 개체 동작 역시 상호 작용 모델마다 다를 수 있습니다.  
* 여러 상호 작용 모델의 일부를 결합하면 어포던스 사이에 경쟁(예: 동시 손 광선과 헤드 게이즈(head-gaze) 커서)이 발생할 위험이 있습니다. 그러면 사용자의 불편과 혼동을 초래할 수 있습니다.

다음은 각 상호 작용 모델에 대해 어포던스 및 동작을 최적화하는 방법에 대한 몇 가지 예입니다. 새로운 사용자가 _"시스템이 작동하는지 어떻게 알 수 있나요?"_ , _"내가 무엇을 할 수 있는지 어떻게 알 수 있나요?"_ , _"내가 방금 한 일이 이해되었는지 어떻게 알 수 있나요?"_ 등과 유사한 질문을 하는 경우가 종종 있습니다.

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>모델</strong></td>
        <td><strong>작동하는지 어떻게 알 수 있나요?</strong></td>
        <td><strong>내가 무엇을 할 수 있는지 어떻게 알 수 있나요?</strong></td>
        <td><strong>내가 방금 한 일을 어떻게 알 수 있나요?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></td>
        <td>손 메시, 손가락 끝 어포던스 또는 손/컨트롤러 광선이 보입니다.</td>
        <td>내 손이 개체 가까이 있으면 잡을 수 있는 핸들이나 경계 상자가 나타납니다.</td>
        <td>가청음이 들리고 잡았다 놓을 수 있는 애니메이션이 보입니다.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">헤드 게이즈 및 커밋</a></td>
        <td>내 시야의 가운데에 커서가 있습니다.</td>
        <td>커서가 특정 개체 위에 있으면 상태가 변경됩니다.</td>
        <td>내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">핸즈프리(헤드 게이즈(head-gaze) 및 드웰(dwell))</a></td>
        <td>내 시야의 가운데에 커서가 있습니다.</td>
        <td>상호 작용이 가능한 개체에 드웰(dwell)하면 진행률 표시기가 보입니다.</td>
        <td>내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">핸즈프리(음성 명령)</a></td>
        <td>시스템이 무엇을 들었는지 보여주는 듣기 표시기와 자막이 보입니다.</td>
        <td>음성 프롬프트와 힌트가 제공됩니다. 다음과 같이 말하는 경우: "이렇게 말 하세요~" 피드백이 보입니다.</td>
        <td>명령을 하면 시각 및 청각 확인이 보이고 들리거나 필요할 때 명확성 UX가 제공됩니다.</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>다음은 상호 작용 모델을 선택하는 데 도움이 되는 질문입니다.
 
1.  Q:  사용자가 홀로그램을 터치하고 정밀한 홀로그램 조작을 수행하기를 원하나요?<br><br>
A:  만약 그렇다면, 정밀 타기팅 및 조작을 위한 손과 모션 컨트롤러 상호 작용 모델을 확인하세요.
 
2.  Q:  사용자가 실제 업무에서 손이 자유로워야 하나요?<br><br>
A:  만약 그렇다면, 응시 및 음성 기반 상호 작용을 통해 유용한 핸즈프리 환경을 제공하는 핸즈프리 상호 작용 모델을 살펴보세요.
 
3.  Q:  사용자가 MR 애플리케이션의 상호 작용을 학습할 시간이 있나요? 또는 가장 낮은 학습 곡선과의 상호 작용이 사용자에게 필요한가요?<br><br>
A:  가장 낮은 학습 곡선과 가장 직관적인 상호 작용을 위해 사용자가 손을 상호 작용에 사용할 수 있는 한 손 및 모션 컨트롤러 모델을 사용하는 것이 좋습니다.
 
4.  Q:  사용자가 가리키기 및 조작을 위해 모션 컨트롤러를 사용하나요?<br><br>
A:  손 및 모션 컨트롤러 모델에는 모션 컨트롤러를 사용하는 유용한 환경을 위한 모든 지침이 포함됩니다.
 
5.  Q:  사용자가 접근성 컨트롤러나 일반적인 Bluetooth 컨트롤러(예: 클리커)를 사용하나요?<br><br>
A:  모든 비 추적 컨트롤러에 대해서는 헤드 게이즈(head-gaze) 및 커밋 모델을 사용하는 것이 좋습니다. 사용자가 간단한 “대상 및 커밋” 기법으로 전체 환경을 탐색할 수 있도록 설계되었습니다. 
 
6.  Q: 사용자가 UI 컨트롤의 밀집된 레이아웃을 탐색하는 것과는 대조적으로, “클릭”(예: 3D 슬라이드 쇼와 같은 환경)을 통한 환경에서 작업을 수행하나요?<br><br>
A:  사용자가 많은 UI를 제어할 필요가 없는 경우 머리 응시 및 커밋에서 사용자가 대상 지정을 염려할 필요가 없는 학습 가능한 옵션을 제공합니다. 
 
7.  Q:  사용자가 HoloLens(1세대)와 HoloLens 2/Windows Mixed Reality 몰입형 헤드셋(VR)을 둘 다 사용하나요?<br><br>
A:  머리 응시 및 커밋은 HoloLens(1세대)용 상호 작용 모델이므로 HoloLens(1세대)를 지원하는 작성자는 머리 응시 및 커밋을 사용자가 HoloLens(1세대) 헤드셋에서 경험하는 모든 기능 또는 모드에 사용하는 것이 좋습니다. 여러 HoloLens 세대를 위한 훌륭한 환경을 만드는 방법에 대한 자세한 내용은 다음에 나오는 *상호 작용 모델 전환* 섹션을 참조하세요.
 
8.  Q: 많은 공간을 사용하거나 공간 사이를 이동하는 모바일 사용자와 단일 공간에서 작업하는 경향이 있는 사용자는 어떤가요?<br><br>
A:  이러한 사용자에게는 모든 사용자 상호 작용 모델이 적합합니다.  

> [!NOTE]
> 앱 디자인에 관련된 자세한 지침은 [서비스 예정](../out-of-scope/news.md)입니다.


## <a name="transitioning-interaction-models"></a>상호 작용 모델 전환
둘 이상의 상호 작용 모델을 사용해야 할 수도 있는 사용 사례도 있습니다. 예를 들어 애플리케이션의 만들기 흐름에는 _"손 및 모션 컨트롤러"_ 상호 작용 모델이 사용되지만, 현장 기술자를 위해 핸즈프리 모드를 사용하려고 합니다. 여러 상호 작용 모델이 환경에 필요한 경우, 특히 혼합 현실을 처음 접하는 경우 사용자는 한 모델에서 다른 모델로 전환하는 데 어려움을 겪을 수 있습니다.

> [!Note]
> 개발자와 디자이너에게 더 많은 지침을 제공하기 위해 지속적으로 노력하고 있으며, 이를 통해 여러 MR 상호 작용 모델을 사용하는 방법, 시기 및 이유를 알려드리겠습니다.
 

## <a name="see-also"></a>참고 항목
* [편안함](comfort.md)
* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](eye-tracking.md)
* [응시 및 커밋](gaze-and-commit.md)
* [응시 및 유지](gaze-and-dwell.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [모션 컨트롤러](motion-controllers.md)
* [공간 매핑](spatial-mapping.md)
* [공간 음향 디자인](spatial-sound-design.md)
* [음성 입력 ](voice-input.md)


