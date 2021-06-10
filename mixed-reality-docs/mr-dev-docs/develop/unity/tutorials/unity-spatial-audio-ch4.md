---
title: 공간 오디오 자습서-4. 런타임 시 공간 오디오 사용 및 사용 안 함
description: 단추를 사용 하 여 런타임에 spatialization 오디오를 사용 하거나 사용 하지 않도록 설정 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712758"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. 런타임에 spatialization 사용 및 사용 안 함

## <a name="overview"></a>개요

이 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하 고 unity 편집기 및 HoloLens 2에서 테스트 하는 방법에 대해 설명 합니다.

## <a name="objectives"></a>목표

* 게임 개체에서 spatialization을 제어 하는 새 스크립트를 추가 합니다.
* 단추 작업에서 spatialization 컨트롤 스크립트를 구동 합니다.

## <a name="add-spatialization-control-script"></a>Spatialization 컨트롤 스크립트 추가

 프로젝트 창을 마우스 오른쪽 단추로 클릭 하 고   >  **c # 스크립트** 만들기를 선택 하 여 새 c # 스크립트를 만들고 스크립트에 적합 한 이름 (예: _SpatializeOnOff_)을 입력 합니다.

![Create 스크립트](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

프로젝트 창에서 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다. 기본 스크립트 내용을 다음과 같이 바꿉니다.

> [!NOTE]
> 스크립트의 여러 줄이 주석 처리 됩니다. 이러한 줄은 다음 챕터에서 주석 처리가 제거 됩니다. [즉, 반향를 사용 하 여 공간 오디오에 거리를 추가](unity-spatial-audio-ch5.md)합니다.

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
> Spatialization를 사용 하거나 사용 하지 않도록 설정 하기 위해 스크립트는 **spatialization** 속성을 사용 하도록 설정 된 상태로 유지 하 여 **spatialBlend** 속성만 조정 합니다. 이 모드에서 Unity는 여전히 **볼륨** 곡선을 적용 합니다. 그렇지 않고 사용자가 원본에서 멀리 spatialization 사용 하지 않도록 설정 하는 경우 볼륨이 갑자기 증가 하는 것을 알리는 것입니다.
> Spatialization를 완전히 사용 하지 않도록 설정 하려면 스크립트를 수정 하 여 **SourceObject** 변수의 **spatialization** 부울 속성도 조정 합니다.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>스크립트를 연결 하 고 단추에서이를 구동 합니다.

계층 구조에서 **쿼드** 을 선택 하 고 검사기 창에서 구성 요소 추가 단추를 사용 하 여 **SpatializeOnOff (스크립트)** 을 추가 합니다.

![쿼드 스크립트 추가](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

계층 구조에서 **PressableButtonHoloLens2**  >  **iconandtext**  >  **TextMeshPro** 를 찾습니다.

계층 구조에서 **4 개의** 개체가 선택 된 상태에서 검사기 창의 **Spatialize On Off (Script)** 구성 요소를 찾아 PressableButtonHoloLens2의 **TextMeshPro** 구성 요소를 끌어서 놓습니다.

![계층에서 PressableButtonHoloLens2 개체 찾기](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

단추가 릴리스될 때 **SpatializeOnOff** 스크립트를 호출 하는 단추를 설정 하려면 interactable 스크립트를 구성 해야 합니다.

계층 창에서 **PressableButtonHoloLens2** 를 선택 합니다. 검사기 창에서 **Interactable (스크립트)** 구성 요소를 찾고 OnClick () 이벤트 아래에서 + 아이콘을 클릭 합니다.

* 계층 창에서 **PressableButtonHoloLens2** 개체를 선택 하 고, 계층 창에서 **4 개의** 개체를 클릭 한 다음 방금 추가한 이벤트의 빈 **없음 (개체)** 필드로 끌어서 끌어 옵니다 .이 단추에서 단추 클릭 이벤트를 수신 대기 하도록 합니다.

* 동일한 이벤트의 **함수 없음** 드롭다운을 클릭합니다. 그런 다음 **SpatializeOnOff**  >  **SwapSpatialization ()** 를 선택 하 여 공간 오디오를 켜고 끕니다.

![단추 동작 설정](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하 고 HoloLens 2 또는 Unity 편집기에서 앱을 테스트 하는 방법을 배웠습니다. 앱에서 이제 단추를 클릭 하 여 오디오의 spatialization을 활성화 하 고 비활성화할 수 있습니다.

다음 자습서에서는 소리에 거리를 지정 하기 위해 반향 효과를 추가 합니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

> [!div class="nextstepaction"]
> [다음 자습서: 5. 반향를 사용 하 여 공간 오디오에 거리 추가](unity-spatial-audio-ch5.md)
