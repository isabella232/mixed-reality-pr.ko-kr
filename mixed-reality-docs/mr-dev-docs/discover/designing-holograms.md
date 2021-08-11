---
title: 홀로그램 디자인
description: Microsoft의 새로운 디자인 홀로그램스 애플리케이션을 통해 Mixed Reality 대해 알아봅니다.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, 홀로그램, 디자인 홀로그램스, 학습, 샘플 앱, 혼합 현실 헤드셋, 가상 현실 헤드셋, 가상 현실이란?
ms.openlocfilehash: fb60dabcd03d276a7d901ee5b2f061460fbfa05acfbdf226a8aee9325f160cff
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192413"
---
# <a name="the-making-of-designing-holograms"></a>디자인 홀로그램스

> [!NOTE]
> 이 페이지의 모든 멋진 GIF 및 포함된 비디오를 설명하는 작은 로드 창을 허용하세요.

혼합 현실용으로 디자인하는 방법을 Learning 미디어가 항상 2D 디자인 프로세스로 잘 변환되지는 않기 때문에 어려울 수 있습니다. 여기서는 혼합 현실 UX 디자인의 기본 내용을 직접 학습할 수 있도록 HoloLens 2 위한 무료 앱을 Microsoft에서 만들었습니다. 디자인 홀로그램스 앱의 고유한 접근 방식은 혼합 현실 동작, 팁 및 권장 사항을 자세히 분석하여 사용자 고유의 흥미롭고 놀라운 HoloLens 앱을 만드는 데 도움이 됩니다. Microsoft Store 무료로 앱을 다운로드하고 Microsoft의 Mixed Reality 디자인 팀에서 알아보세요.

> [!div class="nextstepaction"]
> [디자인 홀로그램스 앱 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![디자인 홀로그램 데모실의 머리 추적 장면에 대한 애니메이션 GIF](images/designing-holograms/demo-room.gif)

*Hologram의 데모실 디자인(은집이라고도 함)*

## <a name="designing-for-mixed-reality"></a>혼합 현실 디자인

많은 사용자와 마찬가지로 모바일 앱을 디자인하는 데 사용했습니다. 2D 디자인 세계에서 들어오는 공간 컴퓨팅은 이제 모든 것이 전 세계에 있는 전체 공간 컴퓨팅으로 전환하는 것이 상당한 변화였습니다. 혼합 현실에서 앱은 더 이상 2D 화면으로 제한되지 않습니다. 실제로 거의 무료이며 실제 세계에 배치되고 실제 개체와 상호 작용합니다.

3D 환경을 기존 2D 디자인 프로세스에 연결하는 것은 혼합 현실 개발에서 가장 어려운 측면입니다. 고객과의 대화에서 "포함할 기능과 기능을 시작하고 실행하는 방법을 알고 있습니다. 코드입니다. 문서와 자습서를 따를 수 있지만 사용자 환경은 무엇인가요? 많은 기능, 다양한 입력 옵션, 다양한 시나리오 및 물리적 환경이 너무 많아서 너무 많습니다."

![샌프란시스코의 HoloLens 2 Design Workshop ](images/designing-holograms/workshop.jpeg)
 *이미지의 HoloLens 2 Design Workshop 이미지*

## <a name="an-opportunity-to-teach"></a>교육할 기회

처음에는 명확하지 않았지만 혼합 현실을 매체로 사용하여 학습할 수 있는 좋은 기회가 제공되었습니다.

홀로그램스 디자인은 혼합 현실 디자인 개념 및 권장 사항을 설명하는 시각적 환경입니다. 혼합 현실 디자인 개념을 보여주는 것은 여러분과 가상 교사뿐입니다. 모든 것은 자신의 공간에서 환경을 쌓은 3인칭 관점에서 볼 수 있습니다.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*홀로그램스 트레일러 비디오 디자인*

## <a name="exploring-the-doll-house"></a>채집 탐색

은 앱 전체에서 사용하는 가상 환경입니다. 환경은 벽, 가로등, 가구, 테이블 및 TV와 같이 대부분의 방이 공통적으로 갖는 기본 요소를 포함하는 80 x 60 x 40cm 방입니다. 집집은 앱 환경의 주요 요소이므로 모든 환경에서 제대로 작동하는지 확인해야 했습니다. 모든 종류의 혼합 현실 개념을 시각화하기 위한 작은 데모 공간이라고 생각하면됩니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*히로하우스 조정 동작의 비디오*

### <a name="11-vs-110-prototypes"></a>1:1 및 1:10 프로토타입

처음에는 실제 교사를 보는 것과 거의 비슷하게 1:1 데모가 놀라운 것이라고 가정했습니다. 사용자는 교사에게 보이는 모든 것을 실제 규모로 볼 수 있습니다. 그러나 몇 가지 문제가 있다는 것을 즉시 알게 됩니다.

- 대부분의 개발자는 사무실 또는 데모실보다 작은 회의실에서 앱을 실행하므로 적합하지 않습니다.
- 디스플레이는 가감되므로 전체 가상 환경이 사용자의 방 위에 오버레이됩니다. 두 개의 테이블( 이중 안치) 및 벽이 정렬되지 않아 혼동을 줄 수 있습니다.
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

Mixed Reality 캡처는 사람 또는 동물에 대한 가상 표현을 생성하지만, 때로는 다른 가상 개체와 상호 작용하기 위해 해당 문자가 필요할 수 있습니다. 다음 두 예제에서는 이 효과를 얻기 위해 장면을 조작한 다양한 방법을 보여 드립니다.

### <a name="head-gaze-adjustment"></a>헤드 응시 조정

헤드게이즈 조정을 사용하면 런타임에 캡처된 사람의 헤드를 이동할 수 있습니다. 즉, 사용자에 대한 캡처 얼굴을 가질 수 있습니다. 이 경우 보기 필드와 관심 필드를 표시하는 데 사용했습니다. 아래에서 볼 수 있는 것은 머리 응시가 살펴볼 대상 역할을 하는 움직이는 gameobject입니다. 대상을 좌우로 이동하면 캡처 헤드가 뒤따릅니다.

이 트릭을 사용하여 유휴 캡처가 항상 집 안의 다른 부분에 배치된 홀로그램을 향하도록 했습니다. 

![Unity에서 대상 gameobject를 따라 런타임에 이동되는 캡처의 머리](images/designing-holograms/head-adjustment.gif)

*Unity에서 대상 gameobject를 따라 런타임에 캡처의 헤드가 이동됩니다.*

### <a name="syncing-animated-objects"></a>애니메이션 개체 동기화

두 번째는 캡처의 이동과 동기화하도록 개체에 애니메이션을 지정하는 것이었습니다. 앱의 여러 부분에서 5프레임마다 특정 캡처의 순차적OBJ를 가져옵니다. 그런 다음, 장면에 애니메이션 효과를 주어 캡처의 해당 프레임과 일치하는지 확인합니다. 애니메이션을 지정하고 키 프레임을 지정하는 지루한 프로세스이지만 결과는 매우 좋습니다. 이제 캡처되지 않은 개체와 상호 작용하는 혼합 현실 캡처 볼 수 있습니다.

![혼합 현실 캡처 패널과 UI 패널 간의 동기화된 애니메이션](images/designing-holograms/synced-objects.gif)

*혼합 현실 캡처 패널과 UI 패널 간의 동기화된 애니메이션*

### <a name="ui-creative-process"></a>UI 창작 프로세스

UI 디자인을 시작할 때 홀로그램이 제공해야 하는 몇 가지 매직과 가능성을 보여 주려고 했습니다. 정적 2D 창 및 텍스트 상자를 표시하는 것만으로는 3D 세계에서는 적합하지 않습니다. 많은 가능성이 표시되지 않으므로 처음부터 바로 이를 벗어나 홀로그램 3D 공간을 최대한 활용하기로 결정했습니다.

처음에는 패널, 아이콘 및 텍스트 정보에 일부 두께를 추가하기 시작했습니다. 그래도 사용자가 볼 수 있는 것은 텍스트 상자입니다. 이미지가 있는 입력란이지만, 아직 없습니다. MRTK(Mixed Reality Toolkit) 셰이더를 사용하여 더 발전했습니다. MRTK 셰이더가 강력한 도구가 되었으며, 스텐실 기능을 사용하여 패널에 음의 깊이를 추가했습니다. 즉, 텍스트 상자 앞에 요소를 추가하는 대신 이제 아이콘이 투명 패널 뒤에 표시됩니다. 이제 사용자로 볼 수 있는 것은 실제 세계에서 더 이상 복제할 수 없는 것이며, 홀로그램 매직이 발생하기 시작했습니다. 또한 실제로 읽고 싶지 않은 사용자로서 실제 세계에서 이미 많은 작업을 수행합니다.

물론 아이콘은 간단한 텍스트보다 훨씬 더 잘 작동합니다. 훨씬 더 강력한 지침을 제공하기 위해 애니메이션 개체 및 아바타 집합을 만들기 시작했습니다. 각 아이콘은 각 시나리오에서 수행되는 작업과 사용 방법에 대한 작은 스토리를 제공합니다.

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

**대화방 스캔 시각화 및 공간 매핑**

![매핑되는 dollhouse 내 모든 표면의 애니메이션 GIF](images/designing-holograms/SpatialMapping.gif)

**장면 이해**

![인식 되는 dollhouse의 개체에 대 한 애니메이션 GIF](images/designing-holograms/SceneUnderstanding.gif)

**직접 광선을 사용 하 여 점 및 커밋**

![손으로 강조 표시 된 손으로 그린 사용자의 애니메이션 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"시험 사용해 보기" 분

홀로그램스를 디자인 하는 것은 혼합 현실 개념을 설명 하지만,이를 통해 방에서 사용해 볼 수도 있습니다. 이러한 설명 중 일부를 일시 중지 하 고 대화형으로 이동 하 고 있습니다. 이러한 대화형 순간의 몇 가지 예는 다음과 같습니다.

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
<td style="border-style: none"><b>Daniel Escudero</b><br><i>선임 기술 디자이너</i><br>Dan은 홀로그램스 설계에 대 한 독창적인 담당 이사 이며 현재는 샌프란시스코의 microsoft mixed reality 아카데미를 위한 디자인 리드로 작동 하며, 이전에는 런던의 microsoft mixed reality 스튜디오 중 하나에 있는 디자이너 였습니다.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>선임 3D 음악가</i><br>Martin는 홀로그램스 설계에 3d 아트 및 UI 디자인을 선도 하 고 있으며,이는 베를린의 Microsoft Mixed Reality 스튜디오 중 하나에서 이전에는 상급 3d 음악가 였습니다.</td>
</tr>
</table>

매우 많은 정보를 공유 하 고, [개체 이론](https://objecttheory.com/) 에서 프로젝트의 모든 단계를 통해 필수적인 팀으로 서 많은 정보를 공유 하기 위해 혼합 현실 설계 팀에 감사 합니다. 열정과 디자인의 뛰어난 눈에 대해 놀라운 인재을 주셔서 감사 합니다.

> [!div class="nextstepaction"]
> [디자인 홀로그램스 앱 다운로드](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)