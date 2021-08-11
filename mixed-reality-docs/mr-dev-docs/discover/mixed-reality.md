---
title: 혼합 현실이란?
description: Mixed Reality에 대한 토론, Mixed Reality 스펙트럼에서 AR 및 VR 디바이스 사용 시연.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Mixed Reality, 홀로그래픽, AR, VR, MR, XR, 증강 현실, 가상 현실, 설명, 사례 연구, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 가상 현실이란, 증강 현실이란
ms.localizationpriority: high
ms.openlocfilehash: fc2686c409883e948f1e5f3a631060a66cd55849f998f94a201801ac10b65808
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205046"
---
# <a name="what-is-mixed-reality"></a>혼합 현실이란?

혼합 현실은 메인프레임, PC 및 스마트폰을 뒤잇는 컴퓨팅의 새로운 물결입니다. 혼합 현실은 소비자와 비즈니스에서 일반화되고 있습니다.  이를 통해 우리가 살고 있는 공간에서, 사물 간에, 친구들과 함께 데이터를 통해 직관적인 상호 작업을 제공함으로써 화면을 사용하는 환경에서 벗어나게 됩니다.  전 세계 수억 명의 온라인 탐험가는 휴대용 디바이스를 통해 혼합 현실을 경험했습니다.  모바일 AR은 현재 소셜 미디어에서 가장 일반화된 혼합 현실 솔루션을 제공합니다. 사람들은 Instagram에서 사용하는 AR 필터가 Mixed Reality 환경이라는 점을 아직 모를 수 있습니다.  Microsoft Mixed Reality는 굉장히 놀라운 사람의 홀로그램 표현, 충실도가 높은 홀로그램 3D 모델 및 주변의 실제 세계를 결합하여 이러한 모든 사용자 환경을 한 단계 발전시킵니다.

![HoloLens 2를 착용하고 손으로 가리키고 커밋](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality는 실제 세계와 디지털 세계가 혼합되어 자연스러우면서 직관적인 3D 인간, 컴퓨터 및 환경 상호 작용을 넓힙니다. 이러한 새로운 현실은 컴퓨터 비전, 그래픽 처리, 표시 기술, 입력 시스템 및 클라우드 컴퓨팅의 발전을 기반으로 합니다. 혼합 현실이라는 용어는 Paul Milgram 및 Fumio Kishino가 1994년에 발표한 "[A Taxonomy of Mixed Reality Visual Displays(혼합 현실 시각적 표시 분류)](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)"라는 논문에서 소개되었습니다. 이 논문에서는 *가상 연속체* 개념과 시각적 표시 분류를 연구했습니다. 그 이후로 Mixed Reality는 표시뿐만 아니라 다음과 같은 영역에도 적용되었습니다.

* 환경 이해: 공간 매핑 및 앵커
* 인간 이해: 손 추적, 시선 추적 및 음성 입력
* 공간 음향
* 실제 공간과 가상 공간 모두에서 위치 및 위치 지정
* 혼합 현실 공간의 3D 자산에 대한 협업

![Mixed Reality 스펙트럼 이미지](images/mixedrealityspectrum-worlds.png)<br>
*이미지: Mixed Reality - 실제 세계와 디지털 세계를 혼합한 결과*

<br>

---

## <a name="environmental-input-and-perception"></a>환경 입력 및 인식

지난 수십 년 동안 인간과 컴퓨터 간의 관계는 입력 방법을 통해 계속 진화해 왔습니다.  HCI(인간-컴퓨터 상호 작용)라고 하는 새로운 분야가 등장했습니다. 이제 인간 입력에는 키보드, 마우스, 터치, 잉크, 음성 및 Kinect 뼈대 추적이 포함될 수 있습니다.

센서 및 처리 능력의 발전으로 고급 입력 방법에 따라 환경에 대한 새로운 컴퓨터 인식이 생성되고 있습니다. 이점이 바로 환경 정보를 표시하는 Windows의 API 이름을 [인식 API](/uwp/api/Windows.Perception)라고 하는 이유입니다. 환경 입력은 다음을 캡처할 수 있습니다. 

* 실제 세계에서 사람 신체 위치([머리 추적](../design/coordinate-systems.md)) 
* 물체, 표면 및 경계([공간 매핑](../design/spatial-mapping.md) 및 [장면 이해](../design/scene-understanding.md)) 
* 주변 조명 및 소리
* 물체 인식
* 실제 위치

<br>

![컴퓨터, 인간 및 환경 간의 상호 작용을 보여주는 벤 다이어그램](images/mixed-reality-venn-diagram-300px.png)<br> 
*이미지: 컴퓨터, 인간 및 환경 간의 상호 작용*

<br>

세 가지 필수 요소를 조합하면 진정한 Mixed Reality 환경을 만들 수 있습니다.

* 클라우드에서 지원하는 컴퓨터 처리
* 고급 입력 방법
* 환경 인식

우리가 실제 세계를 통해 이동하면 이동은 디지털 현실에 매핑됩니다. 물리적 경계는 게임이나 제조 시설의 작업 기반 지침과 같은 디지털 세계의 혼합 현실 환경에 영향을 미칩니다. 환경적 입력과 인식을 통해 환경은 실제 현실과 디지털 현실 사이에서 혼합되기 시작합니다.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>Mixed Reality 스펙트럼

Mixed Reality는 실제 세계와 디지털 세계를 혼합합니다.  이러한 두 가지 현실은 *가상 연속체* 라고 하는 스펙트럼의 극단을 표시합니다. 이러한 현실의 스펙트럼을 *Mixed Reality 스펙트럼* 이라고 합니다.  스펙트럼 끝에는 인간이 존재하는 실제 현실이 있고 스펙트럼의 반대 쪽 끝에는 해당 디지털 현실이 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>증강 현실과 가상 현실 비교

현재 시중에서 판매 중인 대부분의 휴대폰에는 환경 인식 기능이 거의 없거나 아예 없습니다. 이러한 휴대폰에서 제공하는 환경은 실제 현실과 디지털 현실을 혼합할 수 없습니다. 

실제 세계의 그래픽, 비디오 스트림 또는 홀로그램을 겹치는 환경을 증강 현실이라고 합니다. 사용자 시야를 가리고 완전한 몰입형 디지털 환경을 제공하는 환경은 가상 현실입니다. 증강 현실과 가상 현실 간에 전환할 수 있는 환경은 Mixed Reality를 만들었으며 여기서 다음을 수행할 수 있습니다.

* 홀로그램과 같은 디지털 개체를 물리적으로 존재하는 것처럼 실제 세계에 배치합니다.
* 서로 다른 시점에 다른 사용자와 비동기적으로 협업할 수 있도록 아바타 형식으로 실제 세계에 개인적이면서 디지털 방식으로 존재합니다.
* 가상 현실에서 벽 및 가구와 같은 물리적 경계는 실제 장애물이 되지 않도록 사용자의 환경 내에서 디지털 방식으로 나타납니다.

<br>

![Mixed Reality 스펙트럼](images/mixedrealityspectrum.png)<br>
*이미지: Mixed Reality 스펙트럼*

<br>

오늘날 사용할 수 있는 대부분의 증강 현실과 가상 현실 환경은 더 큰 Mixed Reality 스펙트럼의 작은 하위 집합으로 간주됩니다. Windows 10은 전체 스펙트럼을 염두에 두고 제작되었으며 실제 세계의 사람, 장소 및 사물의 디지털 표현을 혼합할 수 있습니다.

## <a name="devices-and-experiences"></a>디바이스 및 환경

Windows Mixed Reality 환경을 제공하는 두 가지 주요 디바이스가 있습니다.
1. **홀로그램 디바이스** 는 디지털 콘텐츠를 마치 실제로 있는 것처럼 현실 세계에 배치하는 기능을 특징으로 하는 디바이스입니다.
2. **몰입형 VR 디바이스** 는 실제 세계를 차단하고 완전한 몰입형 디지털 환경으로 바꿔 현실감을 만드는 기능이 특징인 디바이스입니다.

<table>
<tr>
<th width="30%"> 특성</th><th width="35%"> 홀로그램 디바이스</th><th width="35%"> 몰입형 디바이스</th>
</tr><tr>
<td><strong>디바이스 예</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>표시</strong></td><td> 시스루 디스플레이. 사용자가 헤드셋을 착용하고 있는 동안 실제 환경을 볼 수 있습니다.</td><td> 불투명 디스플레이. 사용자가 헤드셋을 착용하고 있는 동안 실제 환경을 가립니다.</td>
</tr><tr>
<td><strong>이동</strong></td><td> 회전 및 변환 모두 완전한 6 자유도 운동.</td><td> 회전 및 변환 모두 완전한 6 자유도 운동.</td>
</tr>
</table> 

> [!NOTE]
> 디바이스가 USB 케이블이나 Wi-Fi를 통해 별도의 PC에 테더링되어 있거나 테더링되지 않은지 여부는 홀로그램 디바이스나 몰입형 디바이스인지를 반영하지 않습니다. 이동성을 개선하는 기능은 종종 더 나은 환경을 제공합니다. 홀로그램 및 몰입형 디바이스는 테더링되거나 테더링되지 않을 수 있습니다.

Mixed Reality 환경은 기술 발전의 결과물입니다. 현재 전체 스펙트럼에서 환경을 실행할 수 있는 디바이스는 없습니다. Windows 10은 디바이스 제조업체와 개발자 모두에게 공통적인 Mixed Reality 플랫폼을 제공합니다. 현재 지정된 디바이스에서 Mixed Reality 스펙트럼 내 특정 범위를 지원할 수 있습니다. 향후 더욱 다양한 새 디바이스가 예상됩니다. 홀로그램 디바이스는 점점 몰입형 디바이스가 되고 몰입형 디바이스는 점점 홀로그램 디바이스가 될 것입니다.

<br>

![Mixed Reality 스펙트럼의 디바이스 유형](images/Final_WhatIsMixedReality07.png)<br>
*이미지: Mixed Reality 스펙트럼 내에서의 디바이스 위치*

애플리케이션이나 게임 개발자로서 어떤 유형의 환경을 만들고 싶나요? 이 환경은 일반적으로 이 스펙트럼의 특정 지점이나 부분을 대상으로 합니다. 대상으로 지정할 디바이스의 기능을 고려해야 합니다. 실제 세계에 종속된 환경은 HoloLens에서 가장 효율적으로 실행됩니다.

* **왼쪽 방향(실제 현실에 가까움).** 사용자가 실제 현실에 그대로 있으며 해당 현실을 떠났다는 믿음을 갖지 않게 합니다.
* **중간(완전한 Mixed Reality).** 실제 세계와 디지털 세계를 혼합한 환경입니다. 예를 들어 [쥬만지](https://en.wikipedia.org/wiki/Jumanji) 영화에서는 이야기가 시작된 집의 실제 구조가 정글 환경과 혼합되었습니다.
* **오른쪽 방향(디지털 현실에 가까움).** 사용자는 디지털 현실을 경험하고 주변의 실제 현실을 인식하지 못합니다.

## <a name="next-discovery-checkpoint"></a>다음 검색 검사점

Microsoft가 사용자를 위해 준비해 놓은 [검색 과정](get-started-with-mr.md)을 시작하고 Mixed Reality의 기본 사항을 살펴봅니다. 이제 다음 기본 항목으로 계속 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [홀로그램이란?](hologram.md)
