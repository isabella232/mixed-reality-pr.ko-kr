---
title: 공간 오디오 자습서-4. 런타임 시 공간 오디오 사용 및 사용 안 함
description: 단추를 사용 하 여 런타임에 spatialization 오디오를 사용 하거나 사용 하지 않도록 설정 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer
ms.openlocfilehash: 9239c45efa5196b94fe2e05f85a2e83df6c7789f
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578322"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="cebba-105">4. 런타임에 spatialization 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="cebba-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="cebba-106">개요</span><span class="sxs-lookup"><span data-stu-id="cebba-106">Overview</span></span>

<span data-ttu-id="cebba-107">이 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하 고 unity 편집기 및 HoloLens 2에서 테스트 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="cebba-108">목표</span><span class="sxs-lookup"><span data-stu-id="cebba-108">Objectives</span></span>

* <span data-ttu-id="cebba-109">게임 개체에서 spatialization을 제어 하는 새 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="cebba-110">단추 작업에서 spatialization 컨트롤 스크립트를 구동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="cebba-111">Spatialization 컨트롤 스크립트 추가</span><span class="sxs-lookup"><span data-stu-id="cebba-111">Add spatialization control script</span></span>

 <span data-ttu-id="cebba-112">프로젝트 창을 마우스 오른쪽 단추로 클릭 하 고   >  **c # 스크립트** 만들기를 선택 하 여 새 c # 스크립트를 만들고 스크립트에 적합 한 이름 (예: _SpatializeOnOff_)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![스크립트 만들기](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="cebba-114">프로젝트 창에서 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="cebba-115">기본 스크립트 내용을 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="cebba-116">스크립트의 여러 줄이 주석 처리 됩니다. 이러한 줄은 다음 챕터에서 주석 처리가 제거 됩니다. [즉, 반향를 사용 하 여 공간 오디오에 거리를 추가](unity-spatial-audio-ch5.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="cebba-117">Spatialization를 사용 하거나 사용 하지 않도록 설정 하기 위해 스크립트는 **spatialization** 속성을 사용 하도록 설정 된 상태로 유지 하 여 **spatialBlend** 속성만 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="cebba-118">이 모드에서 Unity는 여전히 **볼륨** 곡선을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="cebba-119">그렇지 않고 사용자가 원본에서 멀리 spatialization 사용 하지 않도록 설정 하는 경우 볼륨이 갑자기 증가 하는 것을 알리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="cebba-120">Spatialization를 완전히 사용 하지 않도록 설정 하려면 스크립트를 수정 하 여 **SourceObject** 변수의 **spatialization** 부울 속성도 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="cebba-121">스크립트를 연결 하 고 단추에서이를 구동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="cebba-122">계층 구조에서 **쿼드** 을 선택 하 고 검사기 창에서 구성 요소 추가 단추를 사용 하 여 **SpatializeOnOff (스크립트)** 을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![쿼드 스크립트 추가](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="cebba-124">계층 구조에서 **PressableButtonHoloLens2**  >  **iconandtext**  >  **TextMeshPro** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="cebba-125">계층 구조에서 **4 개의** 개체가 선택 된 상태에서 검사기 창의 **Spatialize On Off (Script)** 구성 요소를 찾아 PressableButtonHoloLens2의 **TextMeshPro** 구성 요소를 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![계층에서 PressableButtonHoloLens2 개체 찾기](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="cebba-127">단추가 릴리스될 때 **SpatializeOnOff** 스크립트를 호출 하는 단추를 설정 하려면 interactable 스크립트를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="cebba-128">계층 창에서 **PressableButtonHoloLens2** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="cebba-129">검사기 창에서 **Interactable (스크립트)** 구성 요소를 찾고 OnClick () 이벤트 아래에서 + 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="cebba-130">계층 창에서 **PressableButtonHoloLens2** 개체를 선택 하 고, 계층 창에서 **4 개의** 개체를 클릭 한 다음 방금 추가한 이벤트의 빈 **없음 (개체)** 필드로 끌어서 끌어 옵니다 .이 단추에서 단추 클릭 이벤트를 수신 대기 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="cebba-131">동일한 이벤트의 **함수 없음** 드롭다운을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="cebba-132">그런 다음 **SpatializeOnOff**  >  **SwapSpatialization ()** 를 선택 하 여 공간 오디오를 켜고 끕니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![단추 동작 설정](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="cebba-134">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-134">Congratulations</span></span>

<span data-ttu-id="cebba-135">이 자습서에서는 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하 고 HoloLens 2 또는 Unity 편집기에서 앱을 테스트 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="cebba-136">앱에서 이제 단추를 클릭 하 여 오디오의 spatialization을 활성화 하 고 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="cebba-137">다음 자습서에서는 소리에 거리를 지정 하기 위해 반향 효과를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cebba-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="cebba-138">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cebba-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cebba-139">다음 자습서: 5. 반향를 사용 하 여 공간 오디오에 거리 추가</span><span class="sxs-lookup"><span data-stu-id="cebba-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
