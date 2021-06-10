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
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="5ec32-105">5. 반향 효과를 이용해 공간 오디오에 거리감 부여</span><span class="sxs-lookup"><span data-stu-id="5ec32-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="5ec32-106">개요</span><span class="sxs-lookup"><span data-stu-id="5ec32-106">Overview</span></span>

<span data-ttu-id="5ec32-107">이전 자습서에서는 소리에 대한 공간화를 추가하여 이 자습서에서 방향성을 부여했습니다. 반향 효과를 추가하여 소리에 거리 느낌을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="5ec32-108">목표</span><span class="sxs-lookup"><span data-stu-id="5ec32-108">Objectives</span></span>

* <span data-ttu-id="5ec32-109">반향을 추가하여 소리 소스의 인식된 거리를 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="5ec32-110">수신기의 홀로그램 거리를 사용하여 소리의 인식된 거리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="5ec32-111">혼합기 그룹 및 반향 효과 추가</span><span class="sxs-lookup"><span data-stu-id="5ec32-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="5ec32-112">[공간화 단추 상호 작용은 자습서](unity-spatial-audio-ch2.md)에서 mixer를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="5ec32-113">이 혼합기는 기본적으로 **마스터** 라는 하나의 **그룹을** 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="5ec32-114">일부 소리에만 반향 효과를 적용하려고 하므로 해당 소리에 대한 두 번째 그룹을 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="5ec32-115">그룹을 추가하려면 **오디오 혼합기에서** 마스터 그룹을 마우스 오른쪽 단추로 클릭하고 **자식 그룹 추가를** 선택하고 적절한 이름(예: _Room Effect)을_ 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![자식 그룹 추가](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

<span data-ttu-id="5ec32-117">각 **그룹에는** 고유한 효과 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="5ec32-118">새 그룹에서 **추가...를** 클릭하고 **SFX Reverb** 를 선택하여 새 그룹에 반향 효과를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX Reverb 추가](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

<span data-ttu-id="5ec32-120">오디오 용어에서 확인되지 않은 원래 오디오를 _건식 경로라고_ 하며, 반향 필터를 통해 필터링한 후의 오디오를 _습성 경로_ 라고 부립니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="5ec32-121">두 경로 모두 오디오 출력으로 전송되며, 이 혼합에서 상대적 강도는 _습/건성 조합이라고_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="5ec32-122">습/건성 혼합은 거리감에 큰 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="5ec32-123">**SFX Reverb에는** 효과 내에서 습/건성 혼합을 조정하는 컨트롤이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="5ec32-124">Microsoft **Spatializer** 플러그 인은 건식 경로를 처리하므로 습성 경로에만 **SFX Reverb를** 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="5ec32-125">**SFX Reverb** 의 검사기 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="5ec32-126">**건성 수준** 속성을 가장 낮은 설정(-10000mB)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="5ec32-127">Room **속성을** 가장 높은 설정(0mB)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX Reverb 속성](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

<span data-ttu-id="5ec32-129">다른 설정은 시뮬레이션된 공간의 느낌을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="5ec32-130">특히 **감쇠 시간은** 인식된 실내 크기와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="5ec32-131">비디오 재생에서 반향 사용</span><span class="sxs-lookup"><span data-stu-id="5ec32-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="5ec32-132">오디오 원본에서 반향을 사용하도록 설정하는 두 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="5ec32-133">오디오 **원본을** 적절한 **그룹으로** 라우팅</span><span class="sxs-lookup"><span data-stu-id="5ec32-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="5ec32-134">처리를 위해 **오디오를 그룹에** 전달하도록 **Microsoft Spatializer** 플러그 인 설정</span><span class="sxs-lookup"><span data-stu-id="5ec32-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="5ec32-135">다음 단계에서는 오디오 라우팅을 제어하도록 스크립트를 조정하고 **Microsoft Spatializer** 플러그 인과 함께 제공된 제어 스크립트를 연결하여 데이터를 반향에 공급합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="5ec32-136">[계층 구조]에서 **쿼드를** 선택한 상태로 [검사기] 창에서 **구성 요소 추가를** 클릭하고 **Room Effect Send Level(Script)** 을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![보내기 수준 스크립트 추가](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="5ec32-138">**Microsoft Spatializer** 플러그 인의 **Room Effect Send Level** 기능을 사용하도록 설정하지 않으면 효과 처리를 위해 오디오를 Unity 오디오 엔진으로 다시 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="5ec32-139">**Room Effect Send Level** 구성 요소에는 반향 처리를 위해 Unity 오디오 엔진으로 전송되는 오디오의 수준을 설정하는 그래프 컨트롤이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="5ec32-140">그래프 컨트롤을 열려면 실내 **효과 보내기 수준** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="5ec32-141">녹색 곡선을 클릭하고 아래로 끌어 수준을 약 -30dB로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![반향 곡선 조정](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

<span data-ttu-id="5ec32-143">다음으로 **SpatializeOnOff** 스크립트에서 주석 처리된 4개 줄의 주석 처리의 주석을 푼 다음,</span><span class="sxs-lookup"><span data-stu-id="5ec32-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="5ec32-144">이제 스크립트가 다음과 같이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-144">The script will now look like this:</span></span>

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

<span data-ttu-id="5ec32-145">이러한 줄의 압축을 풀면 **SpatializeOnOff 스크립트의** 검사기 에 두 개의 속성이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="5ec32-146">**쿼드** 의 **SpatializeOnOff** 구성 요소에 대한 검사기 창에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="5ec32-147">Hierarchy 에서 Quad 개체를 선택한 상태에서 검사기 창에서 **SpatializeOnOff 스크립트** 구성 요소 및 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="5ec32-148">Room **Effect Group** 속성을 새 Room Effect Mixer 그룹으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="5ec32-149">마스터 **그룹** 속성을 마스터 mixer 그룹으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-149">Set the **Master Group** property to the Master mixer group</span></span>

![확장된 공간화 해제](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="5ec32-151">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-151">Congratulations</span></span>

<span data-ttu-id="5ec32-152">Unity용 HoloLens 2 공간 오디오 자습서를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="5ec32-153">HoloLens 2 또는 Unity에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="5ec32-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="5ec32-154">앱에서 단추를 클릭하여 공간화를 활성화하면 스크립트는 비디오의 오디오를 실내 효과 그룹으로 라우팅하여 반향을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="5ec32-155">스테레오로 전환할 때 오디오를 마스터 그룹으로 라우팅하고 반향을 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec32-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="5ec32-156">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ec32-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
