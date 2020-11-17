---
title: 혼합 현실이란?
description: 이 문서에서는 Mixed Reality를 정의하고, AR 및 VR 디바이스가 Mixed Reality 스펙트럼을 따라 배치되는 위치를 보여 줍니다.
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Mixed Reality, 홀로그램, AR, VR, MR, XR, 증강 현실, 가상 현실, 설명
ms.localizationpriority: high
ms.openlocfilehash: 44914decd9530a11d11127b43af527d995f6c252
ms.sourcegitcommit: cc27d31f0cebaf9fc4221a3300a9e3d73230b367
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631491"
---
# <a name="what-is-mixed-reality"></a>혼합 현실이란?

![HoloLens 2를 착용하고 손으로 가리키고 커밋](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality는 실제 세계와 디지털 세계가 혼합되어 인간, 컴퓨터 및 환경 상호 작용 간의 연결을 보여 줍니다. 이 새로운 현실은 컴퓨터 비전, 그래픽 처리 능력, 표시 기술 및 입력 시스템의 발전을 기반으로 합니다. 그러나 *Mixed Reality(혼합 현실)* 라는 용어는 Paul Milgram 및 Fumio Kishino가 1994년에 발표한 "[A Taxonomy of Mixed Reality Visual Displays(혼합 현실 시각적 표시 분류)](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)"라는 논문에서 소개되었습니다. 이 논문에서는 *가상 연속체* 의 개념과 표시에 적용되는 분류의 범주화를 연구했습니다. 그 이후로 Mixed Reality는 표시뿐만 아니라 다음과 같은 영역에도 적용되었습니다.
* 환경 입력
* 공간 음향
* 현실 공간 및 가상 공간 모두에서의 위치 및 위치 지정

![Mixed Reality 스펙트럼 이미지](images/mixedrealityspectrum-worlds.png)<br>
*이미지: Mixed Reality - 실제 세계와 디지털 세계를 혼합한 결과*

<br>

---

## <a name="environmental-input-and-perception"></a>환경 입력 및 인식

지난 수십 년 동안 인간과 컴퓨터 입력 간의 관계에 대한 연구가 계속되어 *HCI(인간 컴퓨터 상호 작용)* 로 알려진 분야로 이어졌습니다. 사용자 입력은 키보드, 마우스, 터치, 잉크, 음성, 심지어 Kinect 골격 추적을 포함하여 다양한 방법을 통해 수행됩니다.

센서 및 처리 기술의 발전 덕분에 환경에서 새로운 컴퓨터 입력 영역이 탄생하고 있습니다. 컴퓨터와 환경 간의 상호 작용은 효과적인 환경 이해 또는 *인식* 이므로 환경 정보를 표시하는 Windows의 API 이름을 [인식 API](https://docs.microsoft.com/uwp/api/Windows.Perception)라고 합니다. 환경 입력은 세계에서 사람의 위치([머리 추적](../design/coordinate-systems.md)), 표면 및 경계([공간 매핑](../design/spatial-mapping.md) 및 [장면 이해](../design/scene-understanding.md)), 주변 조명, 환경 소리, 개체 인식 및 위치와 같은 항목을 캡처합니다.

<br>

![컴퓨터, 인간 및 환경 간의 상호 작용을 보여주는 벤 다이어그램](images/mixed-reality-venn-diagram-300px.png)<br> 
*이미지: 컴퓨터, 인간 및 환경 간의 상호 작용*

<br>

**컴퓨터 처리, 사용자 입력 및 환경 입력** 모두의 세 가지 조합은 진정한 Mixed Reality 환경을 만들기 위한 단계를 설정합니다. 실제 세계에서의 움직임은 디지털 세계에서의 움직임으로 변환될 수 있습니다. 실제 세계의 경계는 디지털 세계의 게임 플레이와 같은 애플리케이션 환경에 영향을 줄 수 있습니다. 환경 입력이 없으면 실제 현실과 디지털 현실을 혼합할 수 없습니다.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Mixed Reality 스펙트럼

Mixed Reality는 실제 세계와 디지털 세계를 모두 혼합하므로 이러한 두 현실은 가상 연속체라는 스펙트럼의 극좌표형 끝을 정의합니다. 현실의 배열을 *Mixed Reality 스펙트럼* 이라고 합니다. 왼쪽에는 인간이 존재하는 실제 현실이 있으며, 오른쪽에는 이에 해당하는 디지털 현실이 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>증강 현실과 가상 현실 비교

현재 시중에 나와 있는 대부분의 휴대폰에는 환경 이해 기능이 거의 없거나 아예 없습니다. 이러한 휴대폰에서 제공하는 환경은 실제 현실과 디지털 현실을 혼합할 수 없습니다. 실제 세계의 비디오 스트림에 그래픽을 오버레이하는 환경은 *증강 현실* 입니다. 사용자의 시야를 가리고 디지털 환경을 제공하는 환경은 *가상 현실* 입니다. 증강 현실과 가상 현실 양식 사이에서 사용하도록 설정되는 환경(*Mixed Reality*)은 다음과 같습니다.
* 실제 세계에서 시작하여 홀로그램과 같은 디지털 개체를 마치 실제로 있는 것처럼 배치합니다.
* 실제 세계로 시작하고 다른 사람(아바타)을 디지털로 표현하여 메모를 남길 때 서 있던 위치를 보여줍니다. 즉, 서로 다른 시점의 비동기 협업을 나타내는 환경입니다.
* 디지털 세계로 시작하고 사용자가 실제 개체를 피할 수 있도록 벽, 가구 등 실제 세계의 물리적 경계가 환경에 디지털 방식으로 표시됩니다.


<br>

![Mixed Reality 스펙트럼](images/mixedrealityspectrum.png)<br>
*이미지: Mixed Reality 스펙트럼*

<br>

오늘날 사용할 수 있는 대부분의 증강 현실 및 가상 현실 제품은 이 스펙트럼의 작은 부분을 나타내며, 더 큰 Mixed Reality 스펙트럼의 하위 집합으로 간주됩니다. Windows 10은 전체 스펙트럼을 염두에 두고 제작되었으며 실제 세계의 사람, 장소 및 사물의 디지털 표현을 혼합할 수 있습니다.


## <a name="devices-and-experiences"></a>디바이스 및 환경

Windows Mixed Reality 환경을 제공하는 두 가지 주요 디바이스가 있습니다.
1. **홀로그램 디바이스** 는 디지털 콘텐츠를 마치 실제로 있는 것처럼 현실 세계에 배치하는 기능을 특징으로 하는 디바이스입니다.
2. **몰입형 디바이스** 는 실제 세계를 숨기고 디지털 환경으로 바꿔 "현재 상태"의 인상을 만드는 기능을 특징으로 하는 디바이스입니다.

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
> 디바이스가 USB 케이블 또는 Wi-Fi를 통해 별도의 PC에 연결되거나 테더링되어 있는지, 아니면 자체 포함되어 있는지(테더링되지 않음) 여부는 홀로그램 디바이스 또는 몰입형 디바이스인지를 반영하지 않습니다. 이동성을 향상시키는 기능은 더 나은 환경을 제공하고, 홀로그램 디바이스와 몰입형 디바이스는 모두 테더링되거나 테더링되지 않을 수 있습니다.

기술 발전에 따라 Mixed Reality 환경을 사용할 수 있게 되었습니다. 현재 전체 스펙트럼의 환경을 실행할 수 있는 디바이스는 없습니다. Windows 10은 디바이스 제조업체와 개발자 모두에게 공통적인 Mixed Reality 플랫폼을 제공합니다. 현재 디바이스는 Mixed Reality 스펙트럼 내의 특정 범위를 지원할 수 있으며, 새 디바이스는 이러한 범위를 확장하고 있습니다. 향후 홀로그램 디바이스는 더 많은 몰입감을, 몰입형 디바이스는 더 많은 홀로그램을 제공할 것입니다.

<br>

![Mixed Reality 스펙트럼의 디바이스 유형](images/Final_WhatIsMixedReality07.png)<br>
*이미지: Mixed Reality 스펙트럼 내에서의 디바이스 위치*

애플리케이션 또는 게임 개발자가 만들려고 하는 환경의 유형을 고려하는 것이 가장 좋습니다. 이 환경은 일반적으로 이 스펙트럼의 특정 지점이나 부분을 대상으로 합니다. 개발자는 대상으로 하는 디바이스의 기능을 고려해야 합니다. 실제 세계에 종속된 환경은 HoloLens에서 가장 효율적으로 실행됩니다.
* **왼쪽 방향(실제 현실에 가까움).** 사용자가 실제 환경에 그대로 있으며 해당 환경을 떠났다는 생각이 들게 하지 않습니다.
* **중간(완전한 Mixed Reality).** 실제 세계와 디지털 세계를 혼합한 환경입니다. [쥬만지](https://en.wikipedia.org/wiki/Jumanji)라는 영화를 본 시청자는 이야기가 시작된 집의 실제 구조가 정글 환경과 어떻게 조화를 이뤘는지 납득할 수 있습니다.
* **오른쪽 방향(디지털 현실에 가까움).** 사용자가 디지털 환경을 경험하고 주변의 실제 환경에서 발생하는 상황을 인식하지 못합니다.

## <a name="next-discovery-checkpoint"></a>다음 검색 검사점

준비된 [검색 과정](get-started-with-mr.md)을 수행하는 경우 Mixed Reality에 대한 기본 사항을 살펴보게 됩니다. 이제 다음 기본 항목을 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [홀로그램이란?](hologram.md)


