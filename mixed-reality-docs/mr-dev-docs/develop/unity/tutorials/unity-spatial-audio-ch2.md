---
title: 공간 오디오 자습서 - 2. 공간화 단추 상호 작용 소리
description: 프로젝트에 단추를 추가하고 단추 상호 작용 소리를 공간화합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer, 프리팹, 볼륨 곡선
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209840"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. 공간화 단추 상호 작용 소리

## <a name="overview"></a>개요

이 자습서에서는 단추 상호 작용 소리를 공간화하는 방법과 오디오 클립을 사용하여 공간화된 단추 상호 작용을 테스트하는 방법을 알아봅니다.  

## <a name="objectives"></a>목표

* 단추 클릭 소리 추가 및 공간화

## <a name="add-a-button"></a>단추 추가

단추 프리팹을 추가하려면 **Project** 창에서 **패키지를** 선택하고 검색 창에 "PressableButtonHoloLens2"를 입력합니다.

![자산의 단추 프리팹](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

단추 프리팹은 파란색 아이콘으로 표시되는 항목입니다. **PressableButtonHoloLens2 프리팹을** 클릭하고 계층 구조로 끕니다. **PressableButtonHoloLens2** 개체를 선택한 상태에서 검사기 창에서 **다음과** 같이 변환 구성 요소를 구성합니다.

* **위치**: X = 0, Y = -0.4, Z = 2
* **회전**: X = 0, Y = 0, Z = 0
* **크기 조정**: X = 1, Y = 1, Z = 1

![단추 변환](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

장면의 개체에 초점을 맞추려면 **PressableButtonHoloLens2** 개체를 두 번 클릭한 다음, 약간 다시 확대하면 됩니다.

## <a name="spatialize-button-feedback"></a>공간화 단추 피드백

이 단계에서는 단추에 대한 오디오 피드백을 공간화합니다. 관련 디자인 제안은 [공간 음향 디자인](../../../design/spatial-sound-design.md)를 참조하세요.

오디오 **Mixer** 창에서 오디오 **원본** 구성 요소에서 오디오 재생을 위해 **Mixer 그룹** 이라는 대상을 정의합니다.

**오디오 Mixer** 창을 열려면 Unity 메뉴에서 **창**  >  **오디오 오디오**  >  **Mixer:** 오디오 Mixer 창 ![ 열기를 선택합니다.](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 **Mixers** 옆에 있는 '+'를 클릭하여 **Mixer** 만들고 Mixer 적절한 이름(예: 공간 오디오 _Mixer)을_ 입력합니다. 새 mixer에는 **Master라는** 기본 **그룹이** 포함됩니다.

![첫 번째 mixer가 있는 Mixer 패널](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> 5장에서 반향을 사용하도록 설정할 [때까지: 반향을 사용하여 공간 오디오에 거리를 추가하면,](unity-spatial-audio-ch5.md)혼합기 볼륨 미터는 Microsoft Spatializer를 통해 재생되는 소리에 대한 활동을 표시하지 않습니다.

계층 구조 창에서 **PressableButtonHoloLens2를** 선택한 다음, 검사기 창에서 **오디오 원본** 구성 요소를 찾고 다음과 같이 오디오 원본 구성 요소를 구성합니다.

1. **Output** 속성에 대해 선택기를 클릭하고 만든 **Mixer** 선택합니다.
2. **공간화** 확인란을 선택합니다.
3. **Spatial Blend** 슬라이더를 3D(1)로 이동합니다.

![단추 오디오 원본](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> 공간화 확인란을 선택하지 않고 **Spatial Blend를**  1(3D)로 이동하는 경우 Unity는 HRTF가 있는 **Microsoft Spatializer** 대신 해당 이동 공간화기를 사용합니다.

## <a name="adjust-the-volume-curve"></a>볼륨 곡선 조정

기본적으로 Unity는 수신기에서 더 멀리 떨어져 있을 때 공간화된 소리를 감쇠합니다. 이 감쇠가 상호 작용 피드백 소리에 적용되면 인터페이스를 사용하기가 더 어려워질 수 있습니다.

이 감쇠를 사용하지 않도록 설정하려면 **오디오 원본** 구성 요소에서 **볼륨** 곡선을 조정해야 합니다.

계층 구조 창에서 **PressableButtonHoloLens2를** 선택한 다음, 검사기 창에서 **오디오 원본**  >  **3D 소리 설정,** 다음과 같이 구성으로 이동합니다.

1. 볼륨 **롤오프** 속성을 선형 롤오프로 설정
2. **볼륨** 곡선(빨간색 곡선)의 엔드포인트를 y축의 '0'에서 '1'까지 끕
3. **볼륨** 곡선의 모양을 평면으로 조정하려면 흰색 곡선 모양 컨트롤을 X축과 병렬로 끌어서

![단추 3D 소리 설정](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>공간화 오디오 테스트

Unity 편집기에서 공간화 오디오를 테스트하려면 **PressableButtonHoloLens2** 개체에서 루프 **옵션을** 선택한 **오디오 원본** 구성 요소에 오디오 클립을 추가해야 합니다.

재생 모드에서 **PressableButtonHoloLens2** 개체를 왼쪽에서 오른쪽으로 이동하고 워크스테이션에서 공간 오디오를 사용하는 경우와 비교합니다. 다음을 수행하여 테스트할 오디오 원본 설정을 변경할 수도 있습니다.

* **Spatial Blend** 속성을 0에서 1 사이로 이동(2D 공간화가 아닌 소리와 3D 공간화된 소리)
* **Spatialize** 속성 확인 및 선택 취소

HoloLens 2 앱을 사용해 보세요. 앱에서 단추를 클릭하고 공간화된 단추 상호 작용 소리를 들 수 있습니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 단추 상호 작용 소리를 공간화하고 오디오 클립을 사용하여 공간화된 단추 상호 작용을 테스트하는 방법을 알아봅니다. 다음 자습서에서는 비디오 원본에서 오디오를 공간화하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 3. 비디오에서 오디오 공간화](unity-spatial-audio-ch3.md)
