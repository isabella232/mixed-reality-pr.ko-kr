---
title: 홀로그램 디자인
description: Microsoft의 새로운 Holograms 애플리케이션 디자인을 통해 Mixed Reality 대해 알아봅니다.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, 홀로그램, 홀로그램 디자인, 학습, 샘플 앱, 혼합 현실 헤드셋, 가상 현실 헤드셋, 가상 현실이란?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143632"
---
# <a name="the-making-of-designing-holograms"></a>홀로그램 디자인

> [!NOTE]
> 이 페이지의 모든 멋진 GIF 및 포함된 비디오를 설명하는 작은 로드 창을 허용하세요.

혼합 현실용으로 디자인하는 방법을 학습하는 것은 미디어가 항상 2D 디자인 프로세스로 잘 변환되지 않기 때문에 어려울 수 있습니다. Microsoft에서는 혼합 현실 UX 디자인의 기본 내용을 직접 학습하는 데 도움이 되는 HoloLens 2 대한 무료 앱을 만들었습니다. Holograms 앱 디자인의 고유한 접근 방식은 혼합 현실 동작, 팁 및 권장 사항을 자세히 분석하여 사용자 고유의 흥미롭고 놀라운 HoloLens 앱을 만드는 데 도움이 됩니다. Microsoft Store 무료로 앱을 다운로드하고 Microsoft의 Mixed Reality 디자인 팀에서 알아보세요.

> [!div class="nextstepaction"]
> [홀로그램 디자인 앱 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![디자인 홀로그램 데모실의 머리 추적 장면에 대한 애니메이션 GIF](images/designing-holograms/demo-room.gif)

*Hologram의 데모실 디자인(마스어하우스라고도 함)*

## <a name="designing-for-mixed-reality"></a>혼합 현실 디자인

많은 사용자와 마찬가지로 모바일 앱을 디자인하는 데 사용했습니다. 2D 디자인 세계에서 들어오는 공간 컴퓨팅은 이제 모든 것이 전 세계에 있는 전체 공간 컴퓨팅으로 전환하는 것이 상당한 변화였습니다. 혼합 현실에서 앱은 더 이상 2D 화면으로 제한되지 않습니다. 실제로 거의 무료이며 실제 세계에 배치되고 실제 개체와 상호 작용합니다.

3D 환경을 기존 2D 디자인 프로세스에 연결하는 것은 혼합 현실 개발에서 가장 어려운 측면입니다. 고객과의 대화에서 "포함할 기능과 기능을 시작하고 실행하는 방법을 알고 있습니다. 코드입니다. 문서와 자습서를 따를 수 있지만 사용자 환경은 무엇인가요? 많은 기능, 다양한 입력 옵션, 다양한 시나리오 및 물리적 환경이 너무 많아서 너무 많습니다."

![Hololens 2의 hololens 2 디자인 워크숍의 이미지-샌프란시스코 ](images/designing-holograms/workshop.jpeg)
 *2 디자인 워크숍* 의 샌프란시스코 이미지

## <a name="an-opportunity-to-teach"></a>학습 기회

처음에는 분명히 알 수 없지만 혼합 현실를 미디어로 사용 하 여 학습 하는 것이 뛰어난 기회를 제공 했습니다.

Holograms 디자인은 혼합 현실 디자인 개념 및 권장 사항을 설명 하는 시각적 환경입니다. 단지 사용자와 혼합 현실 설계 개념을 보여 주는 가상 교사입니다. 모든 것은 사용자의 고유한 공간에서 환경을 확실 하 게 제공 하는 세 번째 사용자 관점에서 제공 됩니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Holograms 트레일러 비디오 디자인*

## <a name="exploring-the-doll-house"></a>인형 집 탐색

인형 회사는 앱 전체에서 사용 하는 가상 환경입니다. 환경은 벽, 전구, 가구, 테이블, TV 등 대부분의 방에 공통적으로 포함 하는 기본 요소를 포함 하는 80 x 60 x 40-cm 소형 공간입니다. 인형 회사는 앱 환경의 주요 protagonist 모든 환경에서 잘 작동 하는지 확인 해야 합니다. 모든 종류의 혼합 현실 개념을 시각화할 수 있는 작은 데모 공간 이라고 생각 하면 됩니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Dollhouse 조정 동작 비디오*

### <a name="11-vs-110-prototypes"></a>1:1 vs 1:10 프로토타입

처음에는 실제 교사와 거의 유사 하 게 1:1 데모를 사용할 수 있다고 가정 했습니다. 사용자는 선생님이 실제 규모에서 볼 수 있는 모든 것을 볼 수 있습니다. 그러나 다음과 같은 몇 가지 문제가 있다는 것을 즉시 알 수 있습니다.

- 대부분의 개발자는 사무실에서 앱을 실행 하거나, 데모 공간 보다 작은 방에서 앱을 실행 하므로 적합 하지 않습니다.
- 표시는 추가 가능 합니다. 즉, 전체 가상 환경이 사용자의 방에 걸쳐 중첩 됩니다. 두 테이블, 즉 두 개의 테이블을 사용 하면 혼동을 couches 수 있습니다.
- 그리고 모든 가상 환경이 보기 필드로 크게 제한되는 최악의 경우입니다.

미니 1:10 배율로 시도한 결과는 사실적인 방의 멋진 조감도였습니다. 모든 각도에서 동시에 진행되는 모든 것을 볼 수 있습니다. 가장 놀라운 점은 대부분의 테스터가 작은 버전을 보기 위해 훨씬 더 몰입형을 찾은 다음, 1:1 규모로 다시 전환하지 않는다는 것입니다. 따라서 실제로 1:1 버전을 폐기하고 UI 및 앱의 다른 측면을 조정하는 데 필요한 추가 작업을 방지하기로 결정했습니다.

![1:1 배율의 ](images/designing-holograms/1-1-scale.png)
 *필드1:1 배율의 보기 필드*

![1:10 배율의 ](images/designing-holograms/1-10-scale.png)
 *필드1:10 배율의 보기 필드*

## <a name="using-mixed-reality-capture"></a>혼합 현실 캡처 사용

이 앱의 가장 특징적인 기능 중 하나는 혼합 현실 캡처 사용하여 혼합 현실 디자인 개념을 교육하고 시연하는 것입니다.

Microsoft는 샌프란시스코에 혼합 현실 캡처 Studio를 보유하고 있습니다. 또한 Microsoft는 이 기술을 워싱턴 D.C.의 아바타 차원, 로스앤젤레스의 메타 스테이지, 런던 차원 스튜디오, Sk Telecom inAngeles 및필로의 Volucap을 비롯한 다른 스튜디오에 라이선스를 부여합니다. [혼합 현실 캡처 Studio에](https://www.microsoft.com/mixed-reality/capture-studios)대한 자세한 내용은 여기에서 확인할 수 있습니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*샌프란시스코의 혼합 현실 캡처 Studio에 있는 106대의 카메라 중 하나에서 나온 Daniel Escudero의 원시 장면입니다.*

캡처 프로세스는 추가 프로덕션 후를 위해 OBJ/PNG 파일로 배달되거나 H.264 압축 MP4 파일로 재생할 준비가 될 수 있는 키 프레임 메시, 기본 및 질감을 생성합니다. 이러한 파일을 Unity, Unreal, Native 및 WebXR 프로젝트로 가져올 수 있습니다. 파일은 Windows, iOS, Mac, Android, Magic Leap 및 Playstation VR에서 실행할 수 있습니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*오디오 및 포함된 메시가 있는 비디오가 포함된 mp4를 분석하기 위해 제공된 캡처 플레이어입니다.*

## <a name="manipulating-captures-and-virtual-objects"></a>캡처 및 가상 개체 조작

Mixed Reality 캡처는 사람 또는 동물에 대한 가상 표현을 생성하지만, 때로는 다른 가상 개체와 상호 작용하기 위해 해당 문자가 필요할 수 있습니다. 다음 두 예제에서는 이러한 효과를 얻기 위해 장면을 조작 하는 다양 한 방법을 보여 줍니다.

### <a name="head-gaze-adjustment"></a>헤드 응시 조정

헤드 응시 조정을 사용 하면 캡처된 사람의 헤드를 런타임에 이동할 수 있습니다. 즉, 사용자에 대 한 캡처 얼굴을 가질 수 있습니다. 여기서는이를 사용 하 여 보기 필드와 관심 있는 필드를 표시 했습니다. 아래에서 볼 수 있는 것은 헤드 응시에서 볼 수 있는 대상의 역할을 하는 이동 gameobject입니다. 대상을 측에서 쪽으로 이동 하는 경우 캡처의 헤드는 다음과 같습니다.

이 트릭을 사용 하 여 유휴 캡처가 항상 인형의 서로 다른 부분에 배치 된 holograms에 직면 하 고 있는지 확인 했습니다. 

![Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처 헤드입니다.](images/designing-holograms/head-adjustment.gif)

*Unity의 대상 gameobject를 따라 런타임에 이동 하는 캡처의 헤드입니다.*

### <a name="syncing-animated-objects"></a>애니메이션 개체 동기화

두 번째는 개체에서 캡처 이동과의 동기화에 애니메이션을 적용 하는 것입니다. 앱의 여러 부분에서 5 개 프레임 마다 특정 캡처의 순차적 Obj을 가져왔습니다. 그런 다음 Obj는이 캡처의 해당 프레임과 일치 하는지 확인 하기 위해 장면에 애니메이션을 적용 했습니다. 애니메이션 및 프레임을 적용 하는 지루한 작업 이지만 결과는 매우 유용 합니다. 이제 캡처되지 않은 개체와 상호 작용 하는 혼합 현실 캡처가 표시 될 수 있습니다.

![혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션](images/designing-holograms/synced-objects.gif)

*혼합 현실 캡처 및 UI 패널 간의 동기화 된 애니메이션*

### <a name="ui-creative-process"></a>UI 창작 프로세스

UI 디자인을 시작할 때 holograms에서 제공 해야 하는 몇 가지 매직 및 가능성을 보여 원했습니다. 단순히 정적 2D 창과 텍스트 상자를 표시 하는 것은 3D 세계에서 적절 하지 않습니다. 많은 가능성이 표시되지 않으므로 처음부터 바로 이를 벗어나 홀로그램 3D 공간을 최대한 활용하기로 결정했습니다.

처음에는 패널, 아이콘 및 텍스트 정보에 일부 두께를 추가하는 것으로 시작했습니다. 그래도 사용자가 볼 수 있는 것은 텍스트 상자입니다. 이미지가 있는 입력란이지만, 아직 없습니다. MRTK(Mixed Reality Toolkit) 셰이더를 사용하여 더 발전했습니다. MRTK 셰이더가 강력한 도구가 되었으며, 스텐실 기능을 사용하여 패널에 음의 깊이를 추가했습니다. 즉, 텍스트 상자 앞에 요소를 추가하는 대신 이제 아이콘이 투명 패널 뒤에 표시됩니다. 이제 사용자로 볼 수 있는 것은 실제 세계에서 더 이상 복제할 수 없는 것이며, 홀로그램 매직이 발생하기 시작했습니다. 또한 실제로 읽고 싶지 않은 사용자로서 실제 세계에서 이미 많은 작업을 수행합니다.

물론 아이콘은 간단한 텍스트보다 훨씬 더 잘 작동합니다. 훨씬 더 강력한 지침을 제공하기 위해 애니메이션 개체 및 아바타 집합을 만들기 시작했습니다. 각 아이콘은 각 시나리오에서 수행되는 작업과 사용 방법에 대한 작은 스토리를 제공하기 시작했습니다.

![대화형 홀로그램 메뉴 시스템의 애니메이션 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>핵심 개념

**헤드 추적 및 시선 추적**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**손 추적**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**공간 인식**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**홀로그램 프레임**

![홀로그램 프레임이 강조 표시된 톨로지 주변을 둘러보는 사용자의 애니메이션 GIF](images/designing-holograms/FOVandFOI.gif)

**좌표계**

![좌표계가 강조 표시된 좌표집을 둘러보는 사용자의 애니메이션 GIF](images/designing-holograms/CoordinateSystems.gif)

**시선 추적**

![시선 응시 광선이 강조 표시된 고정 홀로그램을 보는 사용자의 애니메이션 GIF](images/designing-holograms/EyeTracking.gif)

**공간 검색 시각화 및 공간 매핑**

![매핑되는 히어하우스 내의 모든 표면의 애니메이션 GIF](images/designing-holograms/SpatialMapping.gif)

**장면 이해**

![인식되는 달하우스의 개체에 대한 애니메이션 GIF](images/designing-holograms/SceneUnderstanding.gif)

**직접 광선을 사용 하 여 점 및 커밋**

![손으로 강조 표시 된 손으로 그린 사용자의 애니메이션 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"시험 사용해 보기" 분

Holograms을 디자인 하는 것은 혼합 현실 개념 이지만 방에서 사용해 볼 수도 있습니다. 이러한 설명 중 일부를 일시 중지 하 고 대화형으로 이동 하 고 있습니다. 이러한 대화형 순간의 몇 가지 예는 다음과 같습니다.

![손이 검색 된 시간과 보기 필드를 입력 하는 시점을 보여 주는 손 추적 프레임의 애니메이션 GIF](images/designing-holograms/try-out-1.gif)

*손 모양 추적 프레임은 손을 검색 하는 시기와 보기 필드를 입력 하는 시간을 보여 줍니다.*

![먼 상호 작용을 통해 충돌 하는 crystals와 상호 작용 하는 애니메이션 GIF](images/designing-holograms/try-out-2.gif)

*먼 상호 작용을 통해 충돌 하는 crystals 상호 작용*

![거의 상호 작용 affordances를 탐색 하는 애니메이션 GIF](images/designing-holograms/try-out-3.gif)

*거의 상호 작용 affordances 탐색*

## <a name="about-the-team"></a>팀 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>선임 기술 디자이너</i><br>Dan은 Holograms 디자인에 대 한 독창적인 담당 이사 이며 현재는 샌프란시스코의 Microsoft Mixed Reality 아카데미를 위한 디자인 리드로 작동 하며, 이전에는 런던의 Microsoft Mixed Reality 스튜디오 중 하나인 디자이너 였습니다.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>선임 3D 음악가</i><br>Martin는 Holograms 디자인에 3D 아트 및 UI 디자인을 선도 하며, 이전에는 베를린의 Microsoft Mixed Reality 스튜디오 중 하나에서 선임 3D 음악가 였습니다.</td>
</tr>
</table>

매우 많은 정보를 공유 하 고, [개체 이론](https://objecttheory.com/) 에서 프로젝트의 모든 단계를 통해 필수적인 팀으로 서 많은 정보를 공유 하기 위해 혼합 현실 설계 팀에 감사 합니다. 디자인에 대한 열정을 가지고 뛰어난 시각을 발휘해 주셔서 감사합니다.

> [!div class="nextstepaction"]
> [홀로그램 디자인 앱 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)