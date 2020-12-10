---
title: Unity의 공간 음향
description: Unity 장면 내의 특정 3D 점에서 공간 소리를 재생 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 대화방 크기, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit, spatializer, 반향
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010144"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="17726-104">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="17726-104">Spatial sound in Unity</span></span>

<span data-ttu-id="17726-105">이 페이지는 Unity의 공간 소리에 대 한 리소스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17726-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="17726-106">Spatializer 옵션</span><span class="sxs-lookup"><span data-stu-id="17726-106">Spatializer options</span></span>
<span data-ttu-id="17726-107">혼합 현실 응용 프로그램에 대 한 Spatializer 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="17726-108">Unity는 *Windows Mixed Reality* 선택적 패키지의 일부로 *MS hrtf Spatializer* 을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="17726-109">는 높은 비용의 단일 소스 아키텍처에서 CPU를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="17726-110">이전에 원본 HoloLens 응용 프로그램과의 호환성을 위해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17726-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="17726-111">Microsoft *Spatializer* 는 [microsoft Spatializer GitHub 리포지토리에서](https://github.com/microsoft/spatialaudio-unity)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="17726-112">는 저렴 한 ' 다중 원본 ' 아키텍처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="17726-113">HoloLens 2에서 하드웨어 가속기로 오프 로드 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="17726-114">새 응용 프로그램의 경우 *Microsoft Spatializer* 를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="17726-115">Spatialization 사용</span><span class="sxs-lookup"><span data-stu-id="17726-115">Enable spatialization</span></span>

<span data-ttu-id="17726-116">[Unity 용 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 을 사용 하 여 _SpatialAudio. Spatializer_ 을 설치 하 고 프로젝트의 오디오 설정에서 **microsoft Spatializer** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="17726-117">그런 다음:</span><span class="sxs-lookup"><span data-stu-id="17726-117">Then:</span></span>
* <span data-ttu-id="17726-118">계층의 개체에 **오디오 소스** 연결</span><span class="sxs-lookup"><span data-stu-id="17726-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="17726-119">**Spatialization 사용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="17726-120">**공간 Blend** 슬라이더를 ' 1 '로 이동</span><span class="sxs-lookup"><span data-stu-id="17726-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="17726-121">개발자 워크스테이션에서 공간 오디오를 사용 하도록 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="17726-122">작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 고 공간 사운드가 "꺼짐" 이외의 항목으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="17726-123">**Windows Sonic For 헤드폰** 을 선택 하 여 HoloLens 2에서 듣는 내용을 가장 잘 표현 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="17726-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="17726-124">종속성 중 하나가 누락 되어 SpatialAudio에서 플러그 인 Spatializer를 로드 하지 못하는 경우 Unity에 오류가 발생 하는 경우 최신 버전의 [Microsoft Visual C++ 재배포 가능 패키지가](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) PC에 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="17726-125">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17726-125">For more information, see:</span></span>
* [<span data-ttu-id="17726-126">Microsoft spatializer GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="17726-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="17726-127">Microsoft의 spatializer 자습서</span><span class="sxs-lookup"><span data-stu-id="17726-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="17726-128">Unity의 오디오 소스 설명서</span><span class="sxs-lookup"><span data-stu-id="17726-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="17726-129">Unity의 spatializer 설명서</span><span class="sxs-lookup"><span data-stu-id="17726-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="17726-130">거리 기반 감쇠</span><span class="sxs-lookup"><span data-stu-id="17726-130">Distance-based attenuation</span></span>
<span data-ttu-id="17726-131">Unity의 기본 거리 기반 감소는 로그 rolloff를 사용 하 여 최소 거리가 1 미터이 고 최대 거리가 500 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="17726-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="17726-132">이러한 설정은 시나리오에 대해 적용 될 수 있으며, 원본이 너무 빨리 또는 너무 느리게 경우 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="17726-133">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17726-133">For more information, see:</span></span>
* <span data-ttu-id="17726-134">권장 설정에 대해 [혼합 현실에서 설계](../../design/spatial-sound-design.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="17726-135">이러한 곡선을 설정 하는 방법에 대 한 지침은 [Unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17726-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="17726-136">잔</span><span class="sxs-lookup"><span data-stu-id="17726-136">Reverb</span></span>
<span data-ttu-id="17726-137">_Microsoft Spatializer_ 는 기본적으로 사후 Spatializer 효과를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="17726-138">Spatialized 원본에 대해 반향 및 기타 효과를 사용 하도록 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="17726-139">각 원본에 **대화방 효과 보내기 수준** 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="17726-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="17726-140">각 원본에 대 한 전송 수준 곡선을 조정 하 여 효과 처리를 위해 그래프로 다시 보낸 오디오의 이득을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="17726-141">자세한 내용은 [spatializer 자습서의 5 장](tutorials/unity-spatial-audio-ch5.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17726-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="17726-142">Unity 공간 음향 예</span><span class="sxs-lookup"><span data-stu-id="17726-142">Unity spatial sound examples</span></span>
<span data-ttu-id="17726-143">Unity의 공간 음향 예는 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17726-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="17726-144">MRTK 데모</span><span class="sxs-lookup"><span data-stu-id="17726-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="17726-145">[Microsoft Spatializer 샘플 프로젝트](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="17726-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="17726-146">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="17726-146">Next Development Checkpoint</span></span>

<span data-ttu-id="17726-147">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="17726-148">여기에서 다음 구성 요소를 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17726-149">Text</span><span class="sxs-lookup"><span data-stu-id="17726-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="17726-150">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="17726-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17726-151">공유 환경</span><span class="sxs-lookup"><span data-stu-id="17726-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="17726-152">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17726-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="17726-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17726-153">See also</span></span>
* [<span data-ttu-id="17726-154">혼합 현실에서의 소리 디자인</span><span class="sxs-lookup"><span data-stu-id="17726-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="17726-155">Microsoft의 spatializer 자습서</span><span class="sxs-lookup"><span data-stu-id="17726-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
