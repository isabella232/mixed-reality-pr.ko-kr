---
title: 공간 오디오 자습서 - 4. 런타임 시 공간 오디오 사용 및 사용 안 함
description: 런타임에 오디오 공간화를 사용하거나 사용하지 않도록 설정하려면 단추를 사용합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer
ms.openlocfilehash: 2599e2f360afa4518102ab9535608e9d378264ae87f84a36823d460f934d6a05
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213227"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. 런타임에 공간화 사용 및 사용 안 됨

## <a name="overview"></a>개요

이 자습서에서는 런타임에 공간화를 사용하거나 사용하지 않도록 설정하고 Unity 편집기 및 HoloLens 2 이를 테스트하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* 게임 개체의 공간화를 제어하는 새 스크립트 추가
* 단추 작업에서 공간화 제어 스크립트 구동

## <a name="add-spatialization-control-script"></a>공간화 컨트롤 스크립트 추가

 Project 창을 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를** 선택하여 새  >  **C#** 스크립트를 만들고 스크립트에 적합한 이름(예: _SpatializeOnOff)을_ 입력합니다.

![Create 스크립트](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Project 창에서 스크립트를 두 번 클릭하여 Visual Studio 엽니다. 기본 스크립트 내용을 다음으로 대체합니다.

> [!NOTE]
> 스크립트의 여러 줄이 주석으로 표시됩니다. 이러한 줄은 [다음 챕터: reverb를 사용하여 공간 오디오에 거리 추가에서](unity-spatial-audio-ch5.md)처리되지 않습니다.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> 공간화를 사용하거나 사용하지 않도록 설정하기 위해 스크립트는 **spatialBlend** 속성만 조정하여 **공간화** 속성을 사용하도록 설정합니다. 이 모드에서는 Unity가 **볼륨** 곡선을 계속 적용합니다. 그렇지 않은 경우 사용자가 원본에서 멀리 떨어져 있을 때 공간화를 사용하지 않도록 설정하면 볼륨이 갑자기 증가하는 것을 들었습니다.
> 공간화를 완전히 사용하지 않도록 설정하려면 스크립트를 수정하여 **SourceObject** 변수의 **공간화** 부울 속성도 조정합니다.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>스크립트를 연결하고 단추에서 드라이브

계층 구조에서 **쿼드를** 선택하고 검사기 창에서 구성 요소 추가 단추를 사용하여 **SpatializeOnOff(스크립트)를** 추가합니다.

![쿼드에 스크립트 추가](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

계층 구조에서 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro** 를 찾습니다.

Hierarchy에서 **Quad** 개체를 선택한 상태에서 Inspector 창에서 **Spatialize On Off(스크립트)** 구성 요소를 찾고 PressableButtonHoloLens2의 **TextMeshPro** 구성 요소를 끌어서 놓습니다.

![계층 구조에서 PressableButtonHoloLens2 개체 찾기](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

단추가 해제될 때 **SpatializeOnOff** 스크립트를 호출하도록 단추를 설정하려면 상호 작용 가능한 스크립트를 구성해야 합니다.

계층 구조 창에서 **PressableButtonHoloLens2를** 선택합니다. 검사기 창에서 **Interactable(스크립트)** 구성 요소를 찾고 OnClick() 이벤트 아래에서 + 아이콘을 클릭합니다.

* Hierarchy 창에서 **PressableButtonHoloLens2** 개체를 선택한 상태에서 Hierarchy 창에서 **Quad** 개체를 클릭하고 방금 추가한 이벤트의 빈 **없음(개체)** 필드로 끌어서 ButtonParent 개체가 이 단추에서 단추 클릭 이벤트를 수신 대기하도록 합니다.

* 동일한 이벤트의 **함수 없음** 드롭다운을 클릭합니다. 그런 다음 **SpatializeOnOff**  >  **SwapSpatialization()을** 선택하여 공간 오디오를 켜고 끕니다.

![단추 작업 설정](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 런타임에 공간화를 사용하거나 사용하지 않도록 설정하고, HoloLens 2 또는 Unity 편집기에서 앱을 테스트하는 방법을 배웠습니다. 이제 앱에서 단추를 클릭하여 오디오의 공간화를 활성화하고 비활성화할 수 있습니다.

다음 자습서에서는 반향 효과를 추가하여 소리에 거리 느낌을 줍니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

> [!div class="nextstepaction"]
> [다음 자습서: 5. reverb를 사용하여 공간 오디오에 거리 추가](unity-spatial-audio-ch5.md)
