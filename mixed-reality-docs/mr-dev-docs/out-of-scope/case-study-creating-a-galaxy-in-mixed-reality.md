---
title: 사례 연구 - 혼합 현실에서 북극 만들기
description: 커뮤니티 개발자가 24시간 동안 Twitter를 폴링한 후 "Galaxy Explorer" 애플리케이션 및 Microsft HoloLens 위해 빌드된 방법에 대해 알아봅니다.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, 아이디어 공유, 사례 연구
ms.openlocfilehash: 5891fbc052c52cd90176214d1eff8ef019a2bcfc80dbd5264489deced0fb1664
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208086"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>사례 연구 - 혼합 현실에서 북극 만들기

Microsoft HoloLens 출시되기 전에 개발자 커뮤니티에 새 디바이스에 대한 숙련된 내부 팀 빌드를 보고 싶은 앱의 종류를 문의했습니다. 5,000개가 넘는 아이디어를 공유했으며, 24시간 동안 Twitter 설문 조사 후에는 [Galaxy Explorer라는](../develop/unity/galaxy-explorer.md)아이디어를 받았습니다.

프로젝트의 아트 리더이자 팀의 그래픽 엔지니어인 Andy Zibits와 팀의 그래픽 엔지니어인 Luccin은 Galaxy Explorer에서 Galaxy Way galaxy의 정확한 대화형 표현을 만드는 데 영향을 주는 아트와 엔지니어링 간의 공동 활동에 대해 이야기합니다.

## <a name="the-tech"></a>The Tech

두 명의 디자이너, 3명의 개발자, 4명의 디자이너, 4명의 제작자, 1명의 테스터로 구성된 [팀은](../develop/unity/galaxy-explorer.md#meet-the-team) 6주 동안 모든 기능을 갖춘 앱을 빌드했습니다. 이 앱을 통해 사람들이 밀키 Way Galaxy의 방대한 내용과 지식을 배우고 탐색할 수 있습니다.

우리는 HoloLens 기능을 활용하여 3D 개체를 실제 공간에서 직접 렌더링하려고 했으므로 사람들이 각각 자신의 고유의 별을 가까이 확대하고 개별 별을 볼 수 있는 현실적인 찾고 있는 우주를 만들기로 결정했습니다.

개발 첫 주에는Galaxyy Way Galaxy를 표현하기 위한 몇 가지 목표를 마련했습니다. 즉, 북극의 모양을 만드는 데 도움이 되는 별으로 가득 찬 깊이, 이동 및 볼륨이 필요했습니다.

수십억 개의 별을 가진 애니메이션된 북극을 만들 때의 문제는 업데이트해야 하는 단일 요소 수가 프레임당 너무 커서 HoloLens CPU를 사용하여 애니메이션 효과를 줄 수 없다는 것이었습니다. 이 솔루션에는 복잡한 아트와 과학 혼합이 포함되었습니다.

## <a name="behind-the-scenes"></a>배후 상황

사람들이 개별 별을 탐색할 수 있도록 하기 위해 첫 번째 단계는 한 번에 렌더링할 수 있는 파티클의 개수를 파악하는 것이었습니다.

### <a name="rendering-particles"></a>파티클 렌더링

현재 CPU는 직렬 작업 및 최대 몇 개의 병렬 작업을 한 번에 처리하는 데 적합하지만(코어 수에 따라) GPU는 수천 개의 작업을 병렬로 처리하는 데 훨씬 더 효과적입니다. 그러나 일반적으로 CPU와 동일한 메모리를 공유하지 않으므로 CPU<>GPU 간에 데이터를 교환하면 신속하게 병목 상태가 될 수 있습니다. 이 솔루션은 GPU에서 북극을 만드는 것이었습니다. GPU에서 완전히 라이브로 만들어야 했습니다.

다양한 패턴으로 수천 개의 포인트 파티클로 스트레스 테스트를 시작했습니다. 이를 통해 HoloLens 작동한 내용과 수행되지 않은 작업을 확인할 수 있습니다.

### <a name="creating-the-position-of-the-stars"></a>별의 위치 만들기

팀 멤버 중 한 명이 초기 위치에 별을 생성하는 C# 코드를 이미 작성했습니다. 별은 타원에 있으며, 해당 위치는 (**curveOffset**, **ellipseSize**, **elevation**)로 설명할 수 있습니다. 여기서 **curveOffset은** 타원을 따라 별의 각도이고, **ellipseSize는** X 및 Z를 따라 타원의 차원이며, galaxy 내에서 별의 적절한 상승을 승격합니다. 따라서 각 별 특성으로 초기화되는[버퍼(Unity의 ComputeBuffer)를](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)만들고 나머지 환경의 경우 GPU에 보낼 수 있습니다. 이 버퍼를 그리려면 [Unity의 DrawProcedural을](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) 사용합니다. 이 그리기를 사용하면 실제 메시 없이도 임의의 점 집합에서 셰이더(GPU의 코드)를 실행할 수 있습니다.

**Cpu:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

수천 개의 파티클이 있는 원시 원형 패턴으로 시작했습니다. 이렇게 하면 많은 입자를 관리하고 성능이 좋은 속도로 실행할 수 있다는 증명이 필요했지만, 전체적인 양자 모양은 만족스럽지 못했습니다. 모양을 개선하기 위해 회전을 사용하여 다양한 패턴 및 파티클 시스템을 시도했습니다. 처음에는 파티클 수와 성능이 일관되게 유지되었지만 모양이 중심 부근에서 중단되고 별들이 바깥쪽으로 내보내고 있어 현실적이지 않았기 때문에 처음에는 기대가 있었습니다. 시간을 조작하고 파티클을 사실적으로 이동하면서 북극의 중심에 더 가깝게 반복할 수 있는 배출물이 필요했습니다.

![이와 같이 회전된 다양한 패턴과 파티클 시스템을 시도했습니다.](images/galaxy-patterns-500px.png)

이와 같이 회전된 다양한 패턴과 파티클 시스템을 시도했습니다.

우리 팀은 프록시가 작동하는 방식에 대해 몇 가지 연구를 했고,["밀도 파동](https://en.wikipedia.org/wiki/Density_wave_theory)이론"을 기반으로 타원에 입자를 이동할 수 있도록 특별히 우주를 위한 사용자 지정 입자 시스템을 만들었습니다. 이 시스템은 우주의 암석이 밀도가 높지만 트래픽 맵과 같이 일정한 유동 영역이라고 이론화합니다. 안정적이고 단색으로 보이지만 별은 각각의 타원을 따라 이동할 때 실제로 암 안팎으로 이동하고 있습니다. 시스템에서 파티클은 CPU에 존재하지 않습니다. 카드를 생성하고 GPU에서 모두 방향을 정하기 때문에 전체 시스템은 단순히 초기 상태 + 시간입니다. 다음과 같이 진행되었습니다.

![GPU 렌더링을 통해 파티클 시스템의 진행](images/spiral-galaxy-arms-500px.jpg)

GPU 렌더링을 통해 파티클 시스템의 진행


충분한 타원이 추가되고 회전하도록 설정되면 별의 이동이 수렴되는 "암"을 형성하기 시작합니다. 각 타원 경로를 따라 별의 간격에 약간의 임의성이 부여되었고 각 별은 약간의 위치 임의성을 추가했습니다. 이로 인해 별 모양과 암 모양이 훨씬 더 자연스럽게 분포되었습니다. 마지막으로 중심에서의 거리를 기준으로 색을 구동하는 기능을 추가했습니다.

### <a name="creating-the-motion-of-the-stars"></a>별의 동작 만들기

일반적인 별 동작에 애니메이션을 적용하려면 각 프레임에 대한 상수 각도를 추가하고 별들이 일정한 방사형 속도로 타원을 따라 이동하도록 해야 했습니다. **이는 curveOffset** 를 사용하는 주된 이유입니다. 별표가 타원의 긴 측면을 따라 더 빠르게 이동하지만 일반적인 동작이 좋은 느낌을 주기 때문에 기술적으로는 올바르지 않습니다.

![별은 긴 호에서 더 빠르게 이동하고 가장자리에서는 더 느립니다.](images/ellipse-movement.jpg)

별은 긴 호에서 더 빠르게 이동하고 가장자리에서는 더 느립니다.


이를 통해 각 별은 (**curveOffset**, **ellipseSize**, **elevation**, **Age**)로 완전히 설명됩니다. 여기서 **Age는** 장면 로드 이후 경과된 총 시간의 누적입니다.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

이렇게 하면 애플리케이션을 시작할 때 수만 개의 별을 한 번 생성한 다음, 설정된 곡선을 따라 단일 별 집합에 애니메이션 효과를 주었습니다. 모든 것이 GPU에 있기 때문에 시스템은 CPU에 대한 비용 없이 모든 별에 병렬로 애니메이션을 적용할 수 있습니다.

![흰색 쿼드를 그릴 때의 모양은 다음과 같습니다.](images/drawing-white-quads-300px.jpg)

흰색 쿼드를 그릴 때의 모양은 다음과 같습니다.



각 쿼드가 카메라를 향하도록 하기 위해 기하 도형 셰이더를 사용하여 각 별 위치를 별 질감을 포함하는 화면의 2D 사각형으로 변환했습니다.

![쿼드 대신 다이아몬드입니다.](images/drawing-white-quads-300px.jpg)

쿼드 대신 다이아몬드입니다.


오버드로(픽셀이 처리되는 횟수)를 최대한 제한하려고 했으므로 겹침을 줄이도록 쿼드를 회전했습니다.

### <a name="adding-clouds"></a>클라우드 추가

볼륨 내부의 광선에서 클라우드를 시뮬레이트하기 위해 가능한 한 많은 파티클을 그리는 것까지, 파티클을 사용하여 볼륨 느낌을 얻는 여러 가지 방법이 있습니다. 실시간 광선행진은 비용이 너무 많이 들고 작성하기 어려웠기 때문에 먼저 게임에서 포리스트를 렌더링하는 방법을 사용하여 카메라를 향하여 2D 이미지의 트리를 많이 사용하여 Imposter 시스템을 빌드하려고 했습니다. 게임에서 이 작업을 수행할 때 회전하는 카메라에서 렌더링된 트리 질감을 가질 수 있으며, 해당 이미지를 모두 저장하고 런타임에 각 조정 카드에 대해 보기 방향과 일치하는 이미지를 선택할 수 있습니다. 이는 이미지가 홀로그램인 경우에도 작동하지 않습니다. 왼쪽 눈과 오른쪽 눈의 차이로 인해 훨씬 더 높은 해상도가 필요하거나 평면적이거나 별칭이 있거나 반복적으로 보입니다.

두 번째 시도에서는 가능한 한 많은 파티클을 만들려고 했습니다. 최상의 시각적 개체는 장면에 추가하기 전에 파티클을 가감하고 흐리게 표시했을 때 달성되었습니다. 이 접근 방식의 일반적인 문제는 한 번에 그릴 수 있는 파티클 수와 60fps를 유지하면서 적용된 화면 영역의 양과 관련이 있습니다. 이 클라우드 느낌을 얻기 위해 결과 이미지를 흐리게 하는 것은 일반적으로 매우 비용이 많이 드는 작업이었습니다.

![질감이 없으면 클라우드는 불투명도가 2%인 모양입니다.](images/clouds-without-texture-300px.jpg)

질감이 없으면 클라우드는 불투명도가 2%인 모양입니다.



가감이 많고 많은 경우 여러 쿼드가 서로 위에 있고 동일한 픽셀을 반복적으로 음영으로 표시한다는 것을 의미합니다. 북극의 가운데에 있는 동일한 픽셀에는 수백 개의 쿼드가 서로 위에 있으며 전체 화면을 완료할 때 비용이 많이 들었습니다.

전체 화면 클라우드를 수행하고 클라우드를 흐리게 표시하려는 것은 잘못된 생각이었습니다. 따라서 대신 하드웨어가 작업을 수행하도록 하기로 결정했습니다.

### <a name="a-bit-of-context-first"></a>먼저 컨텍스트의 비트

게임에서 질감을 사용하는 경우 질감 크기는 사용하려는 영역과 거의 일치하지 않지만 다양한 종류의 질감 필터링을 사용하여 그래픽 카드를 사용하여 질감의[픽셀(질감 필터링)에서](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)원하는 색을 보간할 수 있습니다. 관심 있는 필터링은 가장 인접한 4개의 인접을 사용하여 모든 픽셀의 값을 계산하는 [쌍선형 필터링입니다.](/windows/win32/direct3d9/bilinear-texture-filtering)

![필터링 전 원본](images/texture-1.png)

![필터링 후 결과](images/texture-2.png)

이 속성을 사용하면 질감을 두 배 큰 영역으로 그리려고 할 때마다 결과가 흐리게 표시됩니다.

전체 화면으로 렌더링하고 다른 것에 소비할 수 있는 귀중한 밀리초가 손실되는 대신, 작은 버전의 화면으로 렌더링합니다. 그런 다음, 이 질감을 복사하고 2배씩 늘여 프로세스의 콘텐츠를 흐리게 하는 동안 전체 화면으로 돌아갑니다.

![x3 전체 해상도로 다시 스케일 업스케일합니다.](images/galaxy-resolutions-300px.png)

x3 전체 해상도로 다시 스케일 업스케일합니다.



이렇게 하면 원래 비용의 일부만 사용하여 클라우드 부분을 얻을 수 있습니다. 전체 해상도에 클라우드를 추가하는 대신 픽셀의 1/64만 칠하고 질감을 다시 전체 해상도로 늘립니다.

![왼쪽, 1/8에서 전체 해상도로 크기가 조정됩니다. 및 오른쪽, 2의 전원을 사용하는 3개 업스케일.](images/stars-upscaled-300px.jpg)

왼쪽, 1/8에서 전체 해상도로 크기가 조정됩니다. 및 오른쪽, 2의 전원을 사용하는 3개 업스케일.


그래픽 카드는 설정에서 여전히 4픽셀을 사용하여 더 큰 영역을 음영 처리하고 아티팩트 표시를 시작하기 때문에 크기의 1/64에서 전체 크기로 이동하려고 하면 완전히 다르게 보입니다.

그런 다음, 작은 카드가 있는 전체 해상도 별표를 추가하면 전체 galaxy를 얻게 될 것입니다.

![전체 해상도 별을 사용하여 galaxy 렌더링의 거의 최종 결과](images/full-galaxy-500px.png)

셰이프가 올바른 트랙에 있으면 클라우드 계층을 추가하고, 임시 점을 Photoshop에서 그린 점과 교환하고, 색을 추가했습니다. 그 결과, 우리 아트 및 엔지니어링 팀은 모두 좋은 느낌을 주며, CPU에 대한 부담 없이 깊이, 볼륨 및 동작의 목표를 충족했습니다.

![3D의 최종 밀키 방법 Galaxy.](images/final-galaxy-500px.jpg)

3D의 최종 밀키 방법 Galaxy.


### <a name="more-to-explore"></a>자세히 알아보기

Galaxy Explorer 앱에 대한 코드를 오픈 소스로 제공하고 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 개발자가 빌드할 수 있도록 했습니다.

Galaxy Explorer의 개발 프로세스에 대해 자세히 알아보고 싶으신가요? [Microsoft HoloLens YouTube 채널](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)에서 모든 과거 프로젝트 업데이트를 확인합니다.

## <a name="about-the-authors"></a>작성자 정보

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Luccin은</b> 소프트웨어 엔지니어이자 멋진 시각적 개체를 좋아합니다. 그는 Galaxy Explorer용 그래픽 엔지니어였습니다.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits는</b> Galaxy Explorer용 3D 모델링 팀을 관리하고 더 많은 파티클에 대해 익히게 하는 아트 리드이자 우주 마인드입니다.</td>
</tr>
</table>


## <a name="see-also"></a>추가 정보
* [GitHub Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube의 Galaxy Explorer 프로젝트 업데이트](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)