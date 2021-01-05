---
title: 홀로그램 디자인
description: Microsoft의 새로운 디자인 Holograms 응용 프로그램을 통해 혼합 현실에 대해 알아보세요.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, holograms, 디자인 Holograms, 학습, 샘플 앱, 혼합 현실 헤드셋, 가상 현실 헤드셋, 가상 현실 이란?
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757761"
---
# <a name="the-making-of-designing-holograms"></a>Holograms 디자인

> [!NOTE]
> 이 페이지의 모든 쿨 Gif 및 포함 된 비디오를 고려 하는 작은 로드 창에 대해 허용 하세요.

약간의 혼합 현실 디자인 방법은 항상 2D 디자인 프로세스에 잘 변환 되지 않기 때문에 어려울 수 있습니다. Microsoft의 Microsoft는이 문서에 나와 있는 Microsoft의 Microsoft에서는 혼합 현실 UX Design 어떠한 체험의 기본 사항을 배우는 데 도움이 되는 HoloLens 2 용 무료 앱을 만들었습니다. Holograms 앱 디자인의 고유한 접근 방식은 혼합 현실 동작, 팁 및 권장 사항을 제공 하 여 사용자가 직접 매력적인 HoloLens 앱을 만드는 데 도움이 됩니다. Microsoft Store에서 무료로 무료로 앱을 다운로드 하 고 Microsoft의 혼합 현실 디자인 팀에 대해 알아보세요.

> [!div class="nextstepaction"]
> [Holograms 앱 디자인 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![홀로그램의 데모 객실 디자인에서 헤드 추적 장면의 애니메이션 GIF](images/designing-holograms/demo-room.gif)

*홀로그램의 데모 실 디자인 (인형 집이 라고도 함)*

## <a name="designing-for-mixed-reality"></a>혼합 현실 디자인

많은 사용자와 마찬가지로 모바일 앱을 설계 하는 데 사용 했습니다. 2D 디자인 환경에서 제공 되는 모든 것이 세계에 있는 공간 컴퓨팅에서 전체로 이동 하는 것이 중요 합니다. 혼합 현실에서 앱은 더 이상 2D 화면으로 제한 되지 않습니다. 실제로는 거의 무료 이며 실제 개체와 상호 작용할 수 있습니다.

기존 2D 디자인 프로세스에 3D 환경을 연결 하는 것은 혼합 현실 개발의 가장 어려운 측면입니다. 고객과 대화 하는 경우 "포함할 기능 및 다운로드 및 실행 방법에 대해 알고 싶습니다. 코드입니다. 문서와 자습서를 따를 수 있지만 사용자 경험을 따를 수 있나요? 따라서 다양 한 기능, 다양 한 입력 옵션, 다양 한 시나리오 및 물리적 환경을 제공 합니다. "

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
- 그리고 모든 가상 환경의 최악의 경우 보기의 필드에 의해 과도 하 게 제한 됩니다.

미니 1:10 규모를 사용해 볼 때 그 결과는 현실적인 공간에 대 한 훌륭한 상의 눈에 보기 였습니다. 모든 각도에서 동시에 진행 된 모든 항목을 볼 수 있습니다. 가장 놀라운 일은 대부분의 테스터가 작은 버전을 보기 위해 훨씬 더 몰입 형을 발견 하는 것입니다. 즉, 1:1 배율로 다시 전환 하지 않습니다. 따라서 실제로 1:1 버전을 스크랩 하 고 UI 및 앱의 다른 측면을 조정 하는 데 필요한 추가 작업을 방지 하기로 결정 했습니다.

![](images/designing-holograms/1-1-scale.png)
*1:1 소수 자릿수가 있는* 보기의 1:1 눈금 필드가 있는 보기 필드

![](images/designing-holograms/1-10-scale.png)
*1:10 소수 자릿수가 있는* 보기의 1:10 눈금 필드가 있는 보기 필드

## <a name="using-mixed-reality-capture"></a>혼합 현실 캡처 사용

이 앱의 특징 중 하나는 혼합 현실 캡처를 사용 하 여 혼합 현실 디자인 개념을 학습 하 고 시연 하는 것입니다.

Microsoft에는 샌프란시스코의 혼합 현실 캡처 스튜디오가 있습니다. Microsoft는 워싱턴 D.C, Metastage의 스튜디오, 런던의 Dimension 스튜디오, 서울의, 서울의, 서울의 Vol텔레콤 및 베를린의 Volap와 같은 다른에이 기술을 라이선스 합니다. [여기에서 혼합 현실 캡처 스튜디오](https://www.microsoft.com/mixed-reality/capture-studios)에 대 한 자세한 내용을 확인할 수 있습니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Daniel Escudero의 원시 푸티지는 샌프란시스코의 혼합 현실 캡처 스튜디오에서 106 카메라 중 하나에서 시작 합니다.*

캡처 프로세스는 keyframed 메시, 법선 및 질감을 생성 합니다 .이는 추가 사후 프로덕션을 위해 OBJ/PNG 파일로 전달 하거나, h.264 압축 MP4 파일로 재생할 준비를 할 수 있습니다. 이러한 파일은 Unity, Unreal, Native 및 WebXR 프로젝트로 가져올 수 있습니다. 파일은 Windows, iOS, Mac, Android, 매직 Leap 및 Playstation VR에서 실행할 수 있습니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*오디오 및 포함 된 메시를 사용 하 여 비디오를 포함 하는 mp4를 분석 하기 위해 제공 된 캡처 플레이어입니다.*

## <a name="manipulating-captures-and-virtual-objects"></a>캡처 및 가상 개체 조작

혼합 현실 캡처는 사람이 나 동물의 가상 표현을 생성 하지만, 때때로 다른 가상 개체와 상호 작용 하는 문자를 필요로 할 수 있습니다. 다음 두 예제에서는 이러한 효과를 얻기 위해 장면을 조작 하는 다양 한 방법을 보여 줍니다.

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

UI 디자인을 시작할 때 holograms에서 제공 해야 하는 몇 가지 매직 및 가능성을 보여 원했습니다. 단순히 정적 2D 창과 텍스트 상자를 표시 하는 것은 3D 세계에서 적절 하지 않습니다. 그 외에도 대부분의 가능성은 표시 되지 않으므로 처음부터 그 밖으로 이동 하 여 holographic 3D 공간을 모두 사용 하도록 결정 했습니다.

처음에는 패널, 아이콘 및 텍스트 정보에 일부 두께를 추가 하는 작업을 시작 했습니다. 사용자로 서는 텍스트 상자를 표시 합니다. 이미지가 있는 텍스트 상자에는 포함 되어 있지 않습니다. 이제 MRTK (Mixed Reality Toolkit) 셰이더를 사용 하 여 추가 했습니다. MRTK 셰이더는 강력한 도구가 되었으며 스텐실 기능을 사용 하 여 패널에 음수 깊이를 추가 했습니다. 즉, 입력란 앞에 요소를 추가 하는 대신 아이콘이 투명 패널 뒤에 표시 됩니다. 사용자로 서 이제는 더 이상 실제 지역에서 복제할 수 없는 것으로 표시 되며,이는 holographic magic이 시작 되는 위치입니다. 또한 실제로 읽을 필요가 없는 사용자는 이미 실제 세계에 있는 많은 작업을 수행 합니다.

분명히 아이콘은 간단한 텍스트 보다 훨씬 더 효율적으로 작동 하므로 훨씬 더 강력한 지침을 제공 하 고, 애니메이션 개체 및 아바타 집합을 만들기 시작 하 고 각각의 시나리오에서 수행 되는 작업 및 사용 방법에 대 한 간단한 스토리를 알려 줍니다.

![대화형 holographic 메뉴 시스템의 애니메이션 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>핵심 개념

**홀로그램 프레임**

![Holographic 프레임이 강조 표시 된 상태에서 dollhouse를 찾는 사용자의 애니메이션 GIF](images/designing-holograms/FOVandFOI.gif)

**좌표계**

![좌표계가 강조 표시 된 상태로 dollhouse를 찾는 사용자의 애니메이션 GIF](images/designing-holograms/CoordinateSystems.gif)

**시선 추적**

![눈에 보이는 응시 빛이 강조 표시 된 고정 된 holograms를 확인 하는 사용자의 애니메이션 GIF](images/designing-holograms/EyeTracking.gif)

**대화방 스캔 시각화 및 공간 매핑**

![매핑되는 dollhouse 내 모든 표면의 애니메이션 GIF](images/designing-holograms/SpatialMapping.gif)

**장면 이해**

![인식 되는 dollhouse의 개체에 대 한 애니메이션 GIF](images/designing-holograms/SceneUnderstanding.gif)

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

매우 많은 정보를 공유 하 고, [개체 이론](https://objecttheory.com/) 에서 프로젝트의 모든 단계를 통해 필수적인 팀으로 서 많은 정보를 공유 하기 위해 혼합 현실 설계 팀에 감사 합니다. 열정과 디자인의 뛰어난 눈에 대해 놀라운 인재을 주셔서 감사 합니다.

> [!div class="nextstepaction"]
> [Holograms 앱 디자인 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)