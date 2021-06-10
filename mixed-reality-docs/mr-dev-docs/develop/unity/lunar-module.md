---
title: 달착륙선
description: 양손 추적 및 Xbox 컨트롤러 입력으로 HoloLens의 기본 제스처를 확장하고, 반응형 개체를 만들고, 메뉴 시스템을 구현하는 방법을 알아봅니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 샘플 앱, 디자인, MRTK, Mixed Reality 도구 키트, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: ebac2c5680524b408d6dde8635d2585236fa0b08
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743516"
---
# <a name="lunar-module"></a>달착륙선

>[!NOTE]
>이 문서에서는 혼합 현실 앱 개발에 대한 학습 및 제안을 공유하는 [Mixed Reality Design Labs에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플을 설명합니다. 디자인 관련 문서와 코드는 새로운 검색을 통해 발전할 것입니다.

[달 모듈은](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) Microsoft Mixed Reality Design Labs의 오픈 소스 샘플 앱입니다. 양손 추적 및 Xbox 컨트롤러 입력으로 HoloLens의 기본 제스처를 확장하고, 표면 매핑 및 평면 찾기에 반응하는 개체를 만들고, 간단한 메뉴 시스템을 구현하는 방법을 알아봅니다. 프로젝트의 모든 구성 요소는 사용자 고유의 혼합 현실 앱 경험에서 사용할 수 있습니다.

## <a name="demo-video"></a>데모 동영상 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

혼합 현실 캡처 사용하여 HoloLens 2 기록

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Windows Mixed Reality 클래식 환경 재고

대기권에서 높은 위치에 있는 Apollo 모듈의 작은 배는 아래의 가변 지형을 체계적으로 조사합니다. 무시무시한 파일럿은 적절한 랜딩 영역을 발견합니다. 하강은 엄격하지만 다행히 이 여정은 이전에 여러 번 이루어졌습니다...

![Atari의 1979년 달 로아의 원래 인터페이스](images/640px-atari-lunar-lander.png)<br>
*Atari의 1979년 달 로아의 원래 인터페이스*

[달의 아키데](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) 클래식으로, 플레이어가 달 지형의 평지 지점으로 달 을 파일럿하려고 합니다. 1970년에 출생한 사람은 아마도 하늘에서 벡터 배에 시선이 붙는 아케이드에서 몇 시간을 보냈을 것입니다. 플레이어가 우주선을 랜딩 영역으로 이동하면 지형이 확장하여 점진적으로 더 자세한 정보를 표시합니다. 성공이란 수평 및 수직 속도의 안전 임계값 내에 도달한다는 것을 의미합니다. 방문 영역의 크기에 따라 승수를 통해 방문 및 남은 연료에 소요된 시간에 대한 포인트가 부여됩니다.

게임 플레이 외에도 게임의 아케이드 시대는 제어 체계의 지속적인 혁신을 가져왔습니다. 가장 간단한 4방향 원스틱 및 단추 구성(파격적인 [Pac-Man에](https://en.wikipedia.org/wiki/Pac-Man)표시됨)부터 90대 후반과 00대(예: 경도 시뮬레이터 및 레일 레일에 있는 체계)에서 볼 수 있는 매우 구체적이고 복잡한 체계까지. 달의 로아 머신에서 사용되는 입력 체계는 두 가지 이유, 즉 운석과 몰입이라는 두 가지 이유로 인해 난해합니다.

![Atari의 달의 아케이드 콘솔](images/atariconsole.png)<br>
*Atari의 Lunar 한 아케이드 콘솔*

Atari와 다른 많은 게임 회사가 입력을 재고하기로 결정한 이유는 무엇인가요?

아케이드를 따라 탐색하는 어린이는 자연스럽게 최신 플래시 플래시 머신에 의해 깜빡입니다. 하지만 달의 아로나이는 새로운 입력 역학을 갖추고 있습니다.

달의 은 왼쪽 및 오른쪽으로 배 회전에 두 개의 단추를 사용하고, 배에서 생성하는 배의 양을 제어하는 **승용차를** 사용합니다. 이 레버를 통해 사용자는 일반 중틱을 제공할 수 없는 특정 수준의 미세한 정보를 얻을 수 있습니다. 또한 현대식 항공기에 공통적인 구성 요소이기도 합니다. Atari는 달 로아가 실제로 달 모듈을 시험하고 있다는 느낌에 사용자를 몰입시키기를 원했습니다. 이 개념을 **tactile 몰입이라고 하며,**

Tactile 몰입은 반복적인 작업을 수행하는 센서 피드백의 환경입니다. 이 경우 눈과 코가 들은 스로틀 레버 및 회전을 조정하는 반복적인 동작은 플레이어를 달 표면의 배 착륙 동작에 연결하는 데 도움이 됩니다. 이 개념은 "흐름"의 개념에 연결될 수 있습니다. 사용자가 과제와 보상이 올바르게 혼합된 작업에 완전히 흡수되거나 더 간단하게 말하면 "영역"에 있습니다.

혼합 현실에서 가장 두드러진 유형의 몰입은 공간 몰입입니다. 혼합 현실의 핵심은 이러한 디지털 개체가 실제 세계에 존재하게 하는 것입니다. 전체 환경과 환경에 공간적으로 몰입된 환경에서 홀로그램을 합성하고 있습니다. 이것은 Atari가 달 로아의 타일 몰입에서 했던 것처럼 다른 유형의 몰입을 경험에서 계속 사용할 수 없다는 의미는 아닙니다.

## <a name="designing-with-immersion"></a>몰입형 디자인

Atari 클래식에 업데이트된 대량의 압축에 타일 몰입을 적용하려면 어떻게 해야 할까요? 입력 체계를 처리하기 전에 3차원 공간에 대한 게임 구문을 해결해야 합니다.

![HoloLens에서 표면 매핑 시각화](images/surfacemapping.png)<br>
*HoloLens에서 공간 매핑 시각화*

사용자의 주변을 활용하여 달 모듈을 방문하기 위한 무한 지형 옵션을 효과적으로 사용할 수 있습니다. 게임을 원래 타이틀과 가장 비슷하게 만들기 위해 사용자는 환경에서 다양한 난이도의 랜딩 패드를 잠재적으로 조작하고 배치할 수 있습니다.

![달 모듈 비행](images/640px-lm-hero.jpg)<br>
*달 모듈 비행*

사용자가 입력 체계를 배우고, 배송을 제어하고, 소형 대상을 착륙하도록 요구하는 것은 많은 요청입니다. 성공적인 게임 환경은 과제와 보상의 적절한 조합을 제공합니다. 사용자는 사용자가 HoloLens에서 스캔한 표면의 사용자 정의 영역에 성공적으로 도달하도록 요구하는 가장 쉬운 모드로 난이도를 선택할 수 있습니다. 사용자가 게임 중단을 가져오면 적합해 보이는 난이도를 높일 수 있습니다.

### <a name="adding-input-for-hand-gestures"></a>손 제스처에 대한 입력 추가

HoloLens 기본 입력에는 두 개의 [제스처(Air Tap 및 Bloom)만](../../design/gaze-and-commit.md#composite-gestures)있습니다. 사용자는 플랫폼의 인터페이스를 다재다능하고 쉽게 학습할 수 있도록 하는 상황에 맞는 미묘한 차이 또는 특정 제스처의 놀라운 목록을 기억할 필요가 없습니다. 시스템은 이러한 두 제스처만 노출할 수 있지만, 디바이스인 HoloLens는 한 번에 두 손을 추적할 수 있습니다. 달의 아로나에 대한 운도는 [몰입형 앱입니다. 즉, 기본 제스처 세트를 확장하여 두 손을 활용하고 달 모듈 탐색을 위한 고유한 능선 수단을 추가할 수 있습니다.

원래 제어 체계를 **되돌아보면 회전 및 회전에 대해 해결해야 했습니다.** 주의할 점은 새 컨텍스트에서 회전이 추가 축을 추가하는 것입니다(기술적으로는 2개이지만 Y축은 랜딩에 덜 중요함). 두 가지 고유한 배 이동은 자연스럽게 각 손과 매핑됩니다.

![제스처를 탭하고 끌어 세 축에서 모두 회전](images/module-handdrag.gif)<br>
*제스처를 탭하고 끌어 세 축에서 모두 회전*

**추력**

값의 배율에 매핑된 원래 아케이드 머신의 레버가 높을수록 더 많은 화물이 배에 적용되었습니다. 여기서 유의해야 할 중요한 미묘한 차이는 사용자가 컨트롤에서 손을 떼고 원하는 값을 유지 관리하는 방법입니다. 탭 및 끌기 동작을 효과적으로 사용하여 동일한 결과를 얻을 수 있습니다. 이 값은 0부터 시작합니다. 사용자가 탭하고 끌어 값을 늘입니다. 이때 유지 관리하도록 할 수 있습니다. 탭 및 끌기 제스처 값 변경은 원래 값의 델타입니다.

**회전**

이 방법은 좀 더 까다롭습니다. 홀로그램 "회전" 단추를 탭하면 능동적인 경험을 할 수 있습니다. 활용할 물리적 컨트롤이 없으므로 동작은 하게 나타내는 개체의 조작 또는 자체 으로 수행해야 합니다. 사용자가 원하는 방향으로 효과적으로 "밀어넣고 끌어올" 수 있도록 탭 및 끌기를 사용하는 메서드를 사용했습니다. 사용자가 탭하고 보유할 때마다 제스처가 시작된 공간의 지점이 회전의 원점이 됩니다. 원점에서 끌어 오면 손의 변환 델타(X,Y,Z)가 변환되고 이 델타가 로그 회전 값의 델타에 적용됩니다. 또는 더 간단하게 왼쪽 < > 오른쪽으로 끌어서 < > 아래로 끌어서 *< > 뒤로 돌려서 그에 따라 을 회전합니다.*

HoloLens는 두 손을 추적할 수 있기 때문에 왼쪽에 의해 제어되는 동안 오른쪽에 회전을 할당할 수 있습니다. Finesse는 이 게임에서 성공을 위한 추진 요인입니다. 이러한 상호 작용의 *느낌은* 절대적인 가장 높은 우선 순위입니다. 특히 tactile 몰입의 컨텍스트에서. 너무 빠르게 반응하는 배는 조정하기가 어려울 수 있지만, 너무 느리면 사용자가 너무 오랜 시간 동안 배에서 "밀어넣고 끌어오기"해야 합니다.

### <a name="adding-input-for-game-controllers"></a>게임 컨트롤러에 대한 입력 추가

HoloLens의 손 제스처는 세분화된 제어의 새로운 방법을 제공하지만 아날로그 컨트롤에서 얻을 수 있는 'true' 타일 피드백이 여전히 부족합니다. Xbox 게임 컨트롤러를 연결하면 컨트롤을 활용하여 세분화된 제어를 유지하면서 이러한 물리적 느낌을 되돌릴 수 있습니다.

Xbox 컨트롤러에 상대적으로 직선 제어 체계를 적용하는 방법에는 여러 가지가 있습니다. 원래 아케이드 설정에 최대한 가깝게 유지하려고 하기 **때문에, 스트링이** 트리거 단추에 가장 잘 매핑됩니다. 이러한 단추는 아날로그 컨트롤입니다. 즉, *켜기 및 끄기* 상태보다 더 많은 상태를 가지며 실제로 가중의 정도에 응답합니다. 이렇게 하면 스트래버와 유사한 구문을 제공합니다. 원래 게임 및 손 제스처와 달리, 이 컨트롤은 사용자가 트리거에 대한 압력을 중지하면 배의 난간을 잘라냅니다. 여전히 사용자에게 원래 아케이드 게임과 동일한 수준의 정밀도를 제공합니다.

![왼쪽 엄지스틱이 Yaw 및 Roll에 매핑되고 오른쪽 엄지스틱이 피치 및 롤에 매핑됩니다.](images/thumbsticksidebyside.gif)<br>
*왼쪽 엄지스틱은 yaw 및 roll에 매핑됩니다. 오른쪽 엄지스틱이 피치 및 롤에 매핑됩니다.*

이중 엄지스틱은 자연스럽게 배 회전을 제어할 수 있습니다. 아쉽게도 우주선이 회전할 수 있는 축 3개와 두 축을 모두 지원하는 2개의 엄지스틱이 있습니다. 이러한 불일치는 하나의 엄지 스틱 컨트롤 하나를 의미 합니다. 또는 thumbsticks에 대 한 축이 겹칩니다. Thumbsticks는 기본적으로 로컬 X 및 Y 값을 혼합 하므로 이전 솔루션이 "중단" 된 느낌을 종료 했습니다. 후자 솔루션은 어떤 중복 축을 가장 자연스럽 게 파악 하는 테스트를 필요로 했습니다. 최종 샘플에서는 왼쪽 엄지 스틱에 *요* 및 *roll* (Y 및 x 축)를 사용 하 고 오른쪽 엄지 스틱에 *피치* 및 *롤* (Z 및 x 축)을 사용 합니다. 이는 *요* 및 *피치* 와 독립적으로 쌍으로 연결 되는 것 처럼 보이지만 가장 자연스럽 *게 생각 합니다* . 참고로, thumbsticks에 대 한 두 가지 *모두를 사용* 하 여 회전 값을 두 배로 만듭니다. lander do 루프를 사용할 때 매우 재미 있습니다.

이 샘플 앱은 공간 인식 및 tactile 집중 교육 Windows Mixed Reality의 확장 가능 입력 소프트웨어나 덕분에 환경을 크게 변경 하는 방법을 보여 줍니다. 음력은 Lander에 40 년 동안 사용할 수 있지만 작은 팔각형를 사용 하 여 노출 되는 개념은 영원히 지속 됩니다. 미래를 발견 때 과거를 확인 하지 않는 이유는 무엇 인가요?

## <a name="technical-details"></a>기술 세부 정보

[Mixed Reality 디자인 실험 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)에서 음력 모듈 샘플 앱에 대 한 스크립트 및 prefabs를 찾을 수 있습니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조

* [MRTK 예제 허브](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [원소의 주기율표 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [갤럭시 익스플로러 2.0](galaxy-explorer-update.md)