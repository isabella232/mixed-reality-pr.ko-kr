---
title: 공간 오디오 자습서-2. 공간화 단추 상호 작용 소리
description: 프로젝트에 단추를 추가 하 고 단추 상호 작용 소리를 spatialize.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer, prefabs, volume curve
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578494"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. 공간화 단추 상호 작용 소리

## <a name="overview"></a>개요

이 자습서에서는 단추 상호 작용 소리를 spatialize 하 고 오디오 클립을 사용 하 여 spatialized 단추 상호 작용을 테스트 하는 방법을 알아봅니다.  

## <a name="objectives"></a>목표

* 단추 클릭 소리를 추가 하 고 Spatialize

## <a name="add-a-button"></a>단추 추가

Prefab 단추를 추가 하려면 **프로젝트** 창에서 **자산** 을 선택 하 고 검색 표시줄에 "PressableButtonHoloLens2"을 입력 합니다.

![자산에서 prefab 단추](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

Prefab 단추는 파란색 아이콘으로 표시 되는 항목입니다. **PressableButtonHoloLens2** prefab를 클릭 하 고 계층으로 끕니다. **PressableButtonHoloLens2** 개체가 선택 된 상태에서 검사기 창에서 다음과 같이 **Transform** 구성 요소를 구성 합니다.

* **Position**: X = 0, Y =-0.4, Z = 2
* **회전**: X = 0, Y = 0, Z = 0
* **크기 조정**: X = 1, Y = 1, Z = 1

![단추 변형](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

장면의 개체에 초점을 맞추기 위해 **PressableButtonHoloLens2** 개체를 두 번 클릭 한 다음 다시 약간 확대할 수 있습니다.

## <a name="spatialize-button-feedback"></a>Spatialize 단추 피드백

이 단계에서는 단추에 대 한 오디오 피드백을 spatialize 합니다. 관련 디자인 제안 사항은 [공간 음향 디자인](../../../design/spatial-sound-design.md)을 참조 하세요.

오디오 **믹서** 창에서 오디오 **원본** 구성 요소의 오디오 재생에 대해 **믹서 그룹** 이라는 대상을 정의 합니다.

**오디오 믹서** 창을 열려면 Unity 메뉴에서 **창**  >  **오디오**  >  **오디오 믹서**: ![ 오디오 믹서 창 열기를 선택 합니다.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 **Mixers** 옆의 ' + '를 클릭 하 여 **믹서** 를 만들고, 믹서에 적절 한 이름 (예: _공간 오디오 믹서_)을 입력 합니다. 새 믹서에는 **Master** 라는 기본 **그룹이** 포함 됩니다.

![첫 번째 믹서가 있는 믹서 패널](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> 5 번째 챕터에서 반향를 사용 하도록 설정할 때까지 [: 반향를 사용 하 여 공간 오디오에 거리를 추가](unity-spatial-audio-ch5.md)하면 믹서의 볼륨 측정기에 Microsoft Spatializer를 통해 재생 된 소리의 활동이 표시 되지 않습니다.

계층 창에서 **PressableButtonHoloLens2** 를 선택 하 고 검사기 창에서 **오디오 원본** 구성 요소를 찾은 후 다음과 같이 오디오 원본 구성 요소를 구성 합니다.

1. **출력** 속성의 경우 선택기를 클릭 하 고 만든 **믹서** 를 선택 합니다.
2. **Spatialize** 확인란을 선택 합니다.
3. **공간 Blend** 슬라이더를 3d (1)로 이동 합니다.

![오디오 원본 단추](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> **Spatialize** 확인란을 선택 하지 않고 **공간 Blend** 를 1 (3d)로 이동 하는 경우 Unity는 **Microsoft spatializer** with hrtfs 대신 패닝 spatializer를 사용 합니다.

## <a name="adjust-the-volume-curve"></a>볼륨 곡선 조정

기본적으로 Unity는 수신기에서 더 멀리 경우 spatialized 소리를 표시 합니다. 이 감쇠가 상호 작용 피드백 소리에 적용 되 면 인터페이스를 사용 하기가 더 어려울 수 있습니다.

이 감쇠를 사용 하지 않도록 설정 하려면 **오디오 원본** 구성 요소에서 **볼륨** 곡선을 조정 해야 합니다.

계층 창에서 **PressableButtonHoloLens2** 를 선택 하 고 검사기 창에서 **오디오 원본**  >  **3d 소리 설정** 으로 이동한 후 다음과 같이 구성 합니다.

1. **Volume Rolloff** 속성을 Linear Rolloff로 설정 합니다.
2. Y 축의 ' 0 '에서 ' 1 '까지 **볼륨** 곡선 (빨간색 곡선)의 끝점을 끕니다.
3. **볼륨** 곡선의 모양을 평면으로 조정 하려면 흰색 곡선 셰이프 컨트롤을 X 축에 평행으로 끌어 놓습니다.

![3D 소리 설정 단추](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Spatialize 오디오 테스트

Unity 편집기에서 spatialize 오디오를 테스트 하려면 **PressableButtonHoloLens2** 개체에서 **Loop** 옵션이 체크 인 된 **오디오 원본** 구성 요소에서 오디오 클립을 추가 해야 합니다.

재생 모드에서 **PressableButtonHoloLens2** 개체를 왼쪽에서 오른쪽으로 이동 하 고, 워크스테이션에서 사용 하도록 설정 된 공간 오디오를 사용 하지 않고 비교 합니다. 또한 테스트에 대 한 오디오 원본 설정을 변경할 수 있습니다.

* 0-1 (2D 비 spatialized 및 3D spatialized 소리) 간에 **공간 Blend** 속성 이동
* **Spatialize** 속성 확인 및 선택 취소

HoloLens 2에서 앱을 사용해 보세요. 앱에서 단추를 클릭 하 고 spatialized 단추 상호 작용 소리를 들 수 있습니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 학습 단추 상호 작용 소리를 spatialize 오디오 클립을 사용 하 여 spatialized 단추 상호 작용을 테스트 합니다. 다음 자습서에서는 비디오 원본에서 오디오를 spatialize 하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 비디오에서 3. Spatializing 오디오](unity-spatial-audio-ch3.md)
