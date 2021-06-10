---
title: 공간 오디오 자습서 - 5. 반향 효과를 이용해 공간 오디오에 거리감 부여
description: 공간 오디오에 대한 거리 변형의 느낌을 향상시키기 위해 반향 효과를 추가합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer, 오디오 mixer, SFX reverb
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712690"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. 반향 효과를 이용해 공간 오디오에 거리감 부여

## <a name="overview"></a>개요

이전 자습서에서는 소리에 대한 공간화를 추가하여 이 자습서에서 방향성을 부여했습니다. 반향 효과를 추가하여 소리에 거리 느낌을 줍니다.

## <a name="objectives"></a>목표

* 반향을 추가하여 소리 소스의 인식된 거리를 개선합니다.
* 수신기의 홀로그램 거리를 사용하여 소리의 인식된 거리를 제어합니다.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>혼합기 그룹 및 반향 효과 추가

[공간화 단추 상호 작용은 자습서](unity-spatial-audio-ch2.md)에서 mixer를 추가했습니다. 이 혼합기는 기본적으로 **마스터** 라는 하나의 **그룹을** 포함합니다. 일부 소리에만 반향 효과를 적용하려고 하므로 해당 소리에 대한 두 번째 그룹을 추가해 보겠습니다. 그룹을 추가하려면 **오디오 혼합기에서** 마스터 그룹을 마우스 오른쪽 단추로 클릭하고 **자식 그룹 추가를** 선택하고 적절한 이름(예: _Room Effect)을_ 지정합니다.

![자식 그룹 추가](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

각 **그룹에는** 고유한 효과 집합이 있습니다. 새 그룹에서 **추가...를** 클릭하고 **SFX Reverb** 를 선택하여 새 그룹에 반향 효과를 추가합니다.

![SFX Reverb 추가](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

오디오 용어에서 확인되지 않은 원래 오디오를 _건식 경로라고_ 하며, 반향 필터를 통해 필터링한 후의 오디오를 _습성 경로_ 라고 부립니다. 두 경로 모두 오디오 출력으로 전송되며, 이 혼합에서 상대적 강도는 _습/건성 조합이라고_ 합니다. 습/건성 혼합은 거리감에 큰 영향을 미칩니다.

**SFX Reverb에는** 효과 내에서 습/건성 혼합을 조정하는 컨트롤이 포함되어 있습니다. Microsoft **Spatializer** 플러그 인은 건식 경로를 처리하므로 습성 경로에만 **SFX Reverb를** 사용할 것입니다. **SFX Reverb** 의 검사기 창에서 다음을 수행합니다.

* **건성 수준** 속성을 가장 낮은 설정(-10000mB)으로 설정합니다.
* Room **속성을** 가장 높은 설정(0mB)으로 설정합니다.

![SFX Reverb 속성](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

다른 설정은 시뮬레이션된 공간의 느낌을 제어합니다. 특히 **감쇠 시간은** 인식된 실내 크기와 관련이 있습니다.

## <a name="enable-reverb-on-the-video-playback"></a>비디오 재생에서 반향 사용

오디오 원본에서 반향을 사용하도록 설정하는 두 단계는 다음과 같습니다.

* 오디오 **원본을** 적절한 **그룹으로** 라우팅
* 처리를 위해 **오디오를 그룹에** 전달하도록 **Microsoft Spatializer** 플러그 인 설정

다음 단계에서는 오디오 라우팅을 제어하도록 스크립트를 조정하고 **Microsoft Spatializer** 플러그 인과 함께 제공된 제어 스크립트를 연결하여 데이터를 반향에 공급합니다.

[계층 구조]에서 **쿼드를** 선택한 상태로 [검사기] 창에서 **구성 요소 추가를** 클릭하고 **Room Effect Send Level(Script)** 을 추가합니다.

![보내기 수준 스크립트 추가](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> **Microsoft Spatializer** 플러그 인의 **Room Effect Send Level** 기능을 사용하도록 설정하지 않으면 효과 처리를 위해 오디오를 Unity 오디오 엔진으로 다시 보내지 않습니다.

**Room Effect Send Level** 구성 요소에는 반향 처리를 위해 Unity 오디오 엔진으로 전송되는 오디오의 수준을 설정하는 그래프 컨트롤이 포함되어 있습니다. 그래프 컨트롤을 열려면 실내 **효과 보내기 수준** 을 클릭합니다.  녹색 곡선을 클릭하고 아래로 끌어 수준을 약 -30dB로 설정합니다.

![반향 곡선 조정](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

다음으로 **SpatializeOnOff** 스크립트에서 주석 처리된 4개 줄의 주석 처리의 주석을 푼 다음, 이제 스크립트가 다음과 같이 보입니다.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

이러한 줄의 압축을 풀면 **SpatializeOnOff 스크립트의** 검사기 에 두 개의 속성이 추가됩니다. **쿼드** 의 **SpatializeOnOff** 구성 요소에 대한 검사기 창에 할당합니다.

Hierarchy 에서 Quad 개체를 선택한 상태에서 검사기 창에서 **SpatializeOnOff 스크립트** 구성 요소 및 를 찾습니다.

* Room **Effect Group** 속성을 새 Room Effect Mixer 그룹으로 설정합니다.
* 마스터 **그룹** 속성을 마스터 mixer 그룹으로 설정합니다.

![확장된 공간화 해제](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>축하합니다.

Unity용 HoloLens 2 공간 오디오 자습서를 완료했습니다. HoloLens 2 또는 Unity에서 앱을 사용해 보세요. 앱에서 단추를 클릭하여 공간화를 활성화하면 스크립트는 비디오의 오디오를 실내 효과 그룹으로 라우팅하여 반향을 추가합니다. 스테레오로 전환할 때 오디오를 마스터 그룹으로 라우팅하고 반향을 추가하지 않습니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.
