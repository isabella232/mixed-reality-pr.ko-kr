---
title: 공간 오디오 자습서-5. 반향 효과를 이용해 공간 오디오에 거리감 부여
description: 반향 효과를 추가 하 여 공간 오디오에 대 한 거리 변동의 의미를 향상 시킵니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer, 오디오 믹서, SFX 반향
ms.openlocfilehash: f7a5270d969f2e462db0244bd6c68b99347ae1a7
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590725"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="10bd6-105">5. 반향 효과를 이용해 공간 오디오에 거리감 부여</span><span class="sxs-lookup"><span data-stu-id="10bd6-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="10bd6-106">개요</span><span class="sxs-lookup"><span data-stu-id="10bd6-106">Overview</span></span>

<span data-ttu-id="10bd6-107">이전 자습서에서는 소리에 대 한 spatialization를 추가 하 여이 자습서의 지침을 제공 합니다. 소리에 거리를 지정 하는 반향 효과를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="10bd6-108">목표</span><span class="sxs-lookup"><span data-stu-id="10bd6-108">Objectives</span></span>

* <span data-ttu-id="10bd6-109">반향을 추가 하 여 사운드 소스의 인식 된 거리를 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="10bd6-110">홀로그램의 수신자 거리를 사용 하 여 사운드의 인식 거리를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="10bd6-111">믹서 그룹 및 반향 효과 추가</span><span class="sxs-lookup"><span data-stu-id="10bd6-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="10bd6-112">[Spatializing button 인터랙션 소리 자습서](unity-spatial-audio-ch2.md)에서 믹서를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="10bd6-113">믹서에는 기본적으로 **Master** 라는 **그룹** 하나가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="10bd6-114">약간의 소리에 반향 효과를 적용 하려는 경우에만 해당 소리에 대해 두 번째 그룹을 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="10bd6-115">그룹을 추가 하려면 **오디오 믹서** 에서 마스터 그룹을 마우스 오른쪽 단추로 클릭 하 고, **하위 그룹 추가** 를 선택 하 고, 적합 한 이름을 지정 _합니다. 예_:</span><span class="sxs-lookup"><span data-stu-id="10bd6-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![자식 그룹 추가](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="10bd6-117">각 **그룹** 에는 고유한 영향 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="10bd6-118">새 그룹에서 **추가 ...** 를 클릭 하 고 **SFX 반향** 를 선택 하 여 새 그룹에 반향 효과를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX 반향 추가](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="10bd6-120">오디오 용어로 원래의 unreverberated 오디오를 _마른 경로_ 라고 하며, 반향 필터를 사용 하 여 필터링 한 후의 오디오를도로 _경로_ 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="10bd6-121">두 경로는 모두 오디오 출력으로 전송 되 고, 이러한 혼합의 상대적인 강도를 고 지 _/건조_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="10bd6-122">가 중/마른 조합은 거리의 의미에 크게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="10bd6-123">**SFX 반향** 에는 효과 내에서도로/마른 조합을 조정 하는 컨트롤이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="10bd6-124">**Microsoft Spatializer** 플러그 인은 마른 경로를 처리 하기 때문에 **SFX 반향** 를 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="10bd6-125">**SFX 반향** 의 검사기 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="10bd6-126">**마른 수준** 속성을 가장 낮은 설정 (-1만 mB)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="10bd6-127">**방 속성** 을 가장 높은 설정 (0mb)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX 반향 속성](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="10bd6-129">다른 설정은 시뮬레이트된 대화방의 느낌을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="10bd6-130">특히, **감소 시간은** 인식 된 대화방 크기와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="10bd6-131">비디오 재생에서 반향 사용</span><span class="sxs-lookup"><span data-stu-id="10bd6-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="10bd6-132">오디오 원본에서 반향를 사용 하도록 설정 하는 두 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="10bd6-133">**오디오 소스** 를 해당 **그룹** 으로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="10bd6-134">처리를 위해 오디오를 **그룹** 에 전달 하도록 **Microsoft Spatializer** 플러그 인을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="10bd6-135">다음 단계에서는 오디오 라우팅을 제어 하도록 스크립트를 조정 하 고 **Microsoft Spatializer** 플러그 인과 함께 제공 된 제어 스크립트를 연결 하 여 데이터를 반향에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="10bd6-136">계층 구조에서 **4** 를 선택한 상태에서 검사기 창에서 **구성 요소 추가** 를 클릭 하 고 **방 효과 보내기 수준 (스크립트)** 을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![송신 수준 스크립트 추가](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="10bd6-138">**Microsoft Spatializer** 플러그 인의 **공간 효과 보내기 수준** 기능을 사용 하도록 설정 하지 않으면 효과 처리를 위해 오디오를 Unity 오디오 엔진으로 다시 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="10bd6-139">**대화방 효과 송신 수준** 구성 요소에는 반향 처리를 위해 Unity 오디오 엔진으로 보낸 오디오의 수준을 설정 하는 그래프 컨트롤이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="10bd6-140">그래프 컨트롤을 열려면 **방 효과 보내기 수준을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="10bd6-141">녹색 곡선을 클릭 하 여 아래쪽으로 끌어서 수준을 about-30dB로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![반향 곡선 조정](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="10bd6-143">다음으로 **SpatializeOnOff** 스크립트에서 주석 처리 된 4 줄의 주석 처리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="10bd6-144">이제 스크립트는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-144">The script will now look like this:</span></span>

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

<span data-ttu-id="10bd6-145">이러한 줄이 주석 처리가 제거 되 면 **SpatializeOnOff 스크립트** 의 검사기에 두 개의 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="10bd6-146">이를 **4** 개의 **SpatializeOnOff** 구성 요소에 대 한 검사기 창에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="10bd6-147">계층 구조에서 4 개의 개체가 선택 된 상태에서 검사기 창은 **SpatializeOnOff 스크립트** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="10bd6-148">**방 효과 그룹** 속성을 새 대화방 효과 믹서 그룹으로 설정</span><span class="sxs-lookup"><span data-stu-id="10bd6-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="10bd6-149">마스터 **그룹** 속성을 마스터 믹서 그룹으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize On Off 확장](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="10bd6-151">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-151">Congratulations</span></span>

<span data-ttu-id="10bd6-152">Unity 용 HoloLens 2 공간 오디오 자습서를 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="10bd6-153">HoloLens 2 또는 Unity에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="10bd6-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="10bd6-154">앱에서 단추를 클릭 하 여 spatialization을 활성화 하면 스크립트는 비디오의 오디오를 대화방 효과 그룹으로 라우팅하고 반향를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="10bd6-155">스테레오로 전환 하는 경우 오디오를 마스터 그룹으로 라우팅하고 반향를 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10bd6-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="10bd6-156">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10bd6-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
