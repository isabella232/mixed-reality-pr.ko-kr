---
title: 공간 오디오 자습서-3. 비디오에서 공간화 오디오
description: 비디오 자산을 Unity 프로젝트로 가져오고 비디오에서 오디오를 spatialize.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer, 비디오 가져오기, 비디오 플레이어
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712919"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. 비디오에서 공간화 오디오

## <a name="overview"></a>개요

이 자습서에서는 비디오 원본에서 오디오를 spatialize unity 편집기 및 HoloLens 2에서이를 테스트 하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* 비디오 가져오기 및 비디오 플레이어 추가
* Quadrangle 비디오 재생
* 비디오에서 quadrangle로 오디오 라우팅 및 오디오 spatialize

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>비디오 가져오기 및 장면에 비디오 플레이어 추가

이 자습서에서는 공간 오디오 샘플 프로젝트에서 [이 비디오](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 를 사용할 수 있습니다.

Unity 프로젝트에 비디오를 가져오려면 Unity 메뉴에서 **자산**  >  **가져오기 새 자산 가져오기** 
 ![ 자산을 선택 합니다.](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

**새 자산 가져오기** ... 창에서 다운로드 한 **Microsoft HoloLens-공간 PTPvx7mDon4** 파일을 선택 하 고 **열기** 단추를 클릭 하 여 자산을 프로젝트로 가져옵니다.

![자산 선택](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

비디오 클립의 품질 설정을 조정 하면 HoloLens 2에서 부드러운 재생을 보장할 수 있습니다. **프로젝트** 창에서 비디오 파일을 선택 하 고 비디오 파일의 검사기 창에서 **Windows 스토어 앱** 에 대 한 설정을 **재정의** 하 고 다음을 수행 합니다.

* **트랜스 코딩** 사용
* **코덱을** H264로 설정
* **비트 전송률 모드** 를 낮음으로 설정
* **공간 품질** 을 보통 공간 품질로 설정

이러한 조정 후에 적용을 클릭 하 여 비디오 클립의 품질 설정을 변경 합니다.

![비디오 속성 변경](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

계층을 마우스 오른쪽 단추로 클릭 하 고 비디오  >  플레이어 구성 요소를 추가 하려면 비디오 **비디오 플레이어** 를 선택 합니다.

![비디오 플레이어 추가](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Quadrangle 비디오 재생

비디오 **플레이어** 개체는 비디오를 렌더링 하기 위한 질감 게임 개체가 필요 합니다.

계층을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체**  >  **쿼드** 을 선택 하 여 다음과 같이 쿼드를 만들고 해당 **변환** 구성 요소를 구성 합니다.

* **Position**: X = 0, Y = 0, Z = 2
* **회전**: X = 0, Y = 0, Z = 0
* **크기 조정**: X = 1.28, Y = 0.72, Z = 1

![쿼드 추가](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

이제 비디오를 사용 하 여 **쿼드** 의 질감을 선택 하 고, **프로젝트** 창에서 마우스 오른쪽 단추를 클릭 하 고, 렌더링 질감 **만들기** 를 선택 하 여 렌더링  >   텍스처 구성 요소를 만들려면, _공간 오디오 텍스처_ 와 같이 렌더링 질감에 적합 한 이름을 입력 합니다.

![렌더링 질감 만들기](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

**렌더링 질감** 을 선택 하 고 검사기 창에서 **Size** 속성을 비디오의 1280x720에 대 한 기본 해상도와 일치 하도록 설정 합니다. 그러면 HoloLens 2에서 최적의 렌더링 성능을 보장 하기 위해 **깊이 버퍼** 속성을 **16 비트** 수준 이상으로 설정 합니다.

![질감 속성 렌더링](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

그런 다음 생성 된 렌더링 질감 **공간 오디오 텍스처** 를 **쿼드** 의 질감으로 사용 합니다.

1. **프로젝트** 창의 **공간 오디오 텍스처** 를 계층 구조에서 **쿼드** 로 끌어 렌더링 질감을 쿼드에 추가 합니다.
2. HoloLens 2의 성능을 보장 하려면 계층에서 쿼드를 선택 하 고 셰이더에 대 한 검사기 창에서 **Mixed Reality Toolkit**  >  **Standard** 셰이더를 선택 합니다.

![쿼드 질감 속성](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

비디오 **플레이어** 를 설정 하 고 **질감을 렌더링** 하 여 비디오 클립을 재생 하려면 **계층 구조** 및 **검사기** 창에서 **비디오 플레이어** 를 선택 합니다.

* **비디오 클립** 속성을 다운로드 한 비디오 파일 ' Microsoft HoloLens-PTPvx7mDon4 '로 설정 합니다.
* **루프** 확인란을 선택 합니다.
* **대상 질감** 을 새 렌더링 질감 **공간 오디오 질감** 으로 설정 합니다.

![비디오 플레이어 속성](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>비디오에서 오디오 Spatialize

계층 창에서 **쿼드** 개체를 선택한 다음 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 비디오에서 오디오를 라우팅할 **오디오 원본을** 추가 합니다.

**오디오 원본** 에서:

* **출력** 을 **공간 오디오 믹서** 로 설정 합니다.
* **Spatialize** 상자를 선택 합니다.
* **공간 Blend** 슬라이더를 1 (3d)로 이동

![쿼드 오디오 원본 검사기](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

오디오 **원본** 으로 오디오를 라우팅하도록 비디오 플레이어를 설정 하려면 계층 창에서 **비디오 플레이어** 를 선택 하 고 검사기의 비디오 플레이어 개체에서 다음과 같이 변경 합니다.

* 오디오 **출력 모드** 를 **오디오 원본** 으로 설정
* **오디오 원본** 속성을 **쿼드** 로 설정 합니다.

![비디오 플레이어에서 오디오 원본 설정](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 비디오 원본에서 오디오를 spatialize 하는 방법을 알아보았습니다. HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요. 비디오를 보고 듣고 비디오에서 오디오가 spatialized 됩니다.

다음 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하는 방법에 대해 설명 합니다.

> [!div class="nextstepaction"]
> [다음 자습서: 4. 런타임에 spatialization 사용 및 사용 안 함](unity-spatial-audio-ch4.md)
