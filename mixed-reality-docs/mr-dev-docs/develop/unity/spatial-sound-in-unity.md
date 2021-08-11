---
title: Unity의 공간 음향
description: 예제를 사용하여 Unity 장면 내의 특정 3D 지점에서 공간 소리를 재생하고 감쇠하는 방법을 알아봅니다.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 사운드, HRTF, 실내 크기, 혼합 현실 헤드셋, Windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit, spatializer, reverb
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228229"
---
# <a name="spatial-sound-in-unity"></a>Unity의 공간 음향

이 페이지는 Unity의 공간 음향에 대한 리소스에 연결됩니다.

## <a name="spatializer-options"></a>Spatializer 옵션

혼합 현실 애플리케이션에 대한 공간화 도우미 옵션은 다음과 같습니다.
* Unity는 *Windows Mixed Reality* 선택적 패키지의 일부로 *MS HRTF Spatializer를* 제공합니다.
  * 더 높은 비용의 '단일 원본' 아키텍처에서 CPU에서 실행됩니다.
  * 원래 HoloLens 애플리케이션과의 이전 버전과의 호환성을 위해 제공됩니다.
* *Microsoft Spatializer는* Microsoft [spatializer GitHub 리포지토리에서](https://github.com/microsoft/spatialaudio-unity)사용할 수 있습니다.
  * 저렴한 '다중 원본' 아키텍처를 사용합니다.
  * HoloLens 2 하드웨어 가속기로 오프로드됩니다. 

새 애플리케이션의 경우 *Microsoft Spatializer* 를 사용하는 것이 좋습니다.

## <a name="enable-spatialization"></a>공간화 사용

[Unity용 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 사용하여 _Microsoft.SpatialAudio.Spatializer.Unity를_ 설치하고 프로젝트의 오디오 설정에서 **Microsoft Spatializer를** 선택합니다. 그렇다면
* 계층 구조의 개체에 **오디오 원본** 연결
* **공간화 사용** 확인란을 선택합니다.
* **Spatial Blend** 슬라이더를 '1'로 이동
* 개발자 워크스테이션에서 공간 오디오가 사용하도록 설정되어 있는지 확인합니다. 
    * 작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭하고 공간 소리가 "off" 이외의 다른 것으로 설정되어 있는지 확인합니다. 
    * 헤드폰용 Windows Sonic 선택하여 **HoloLens 2** 가장 잘 표현합니다.

>[!NOTE]
>Unity에서 플러그 인 Microsoft.SpatialAudio.Spatializer.Unity를 로드할 수 없다는 오류가 발생할 경우 해당 dependencies 중 하나가 누락되어 PC에 최신 버전의 [Microsoft Visual C++ 재배포 가능하도록](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 설치되어 있는지 확인합니다.

자세한 내용은 다음을 참조하세요.
* [Microsoft spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft의 spatializer 자습서](tutorials/unity-spatial-audio-ch1.md)
* [Unity의 오디오 원본 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity의 spatializer 설명서](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>거리 기반 감쇠

Unity의 기본 거리 기반 감쇠는 최소 거리 1미터, 최대 거리 500m이며 로그 롤오프가 있습니다. 이러한 설정은 시나리오에 대해 작동하거나 소스가 너무 빨리 또는 너무 느리게 감쇠되는 것을 발견할 수 있습니다. 자세한 내용은 다음을 참조하세요.
* 권장 설정에 대한 [혼합 현실의 사운드 디자인.](../../design/spatial-sound-design.md)
* 이러한 곡선 설정에 대한 지침은 [Unity의 오디오 원본 설명서입니다.](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)

## <a name="reverb"></a>반향

_Microsoft Spatializer는_ 기본적으로 공간화 후 효과를 사용하지 않도록 설정합니다. 공간화된 원본에 대해 반향 및 기타 효과를 사용하도록 설정하려면 다음을 수행합니다.
* 각 원본에 **Room Effect Send Level** 구성 요소 연결
* 효과 처리를 위해 그래프로 다시 전송된 오디오의 게인을 제어하도록 각 소스에 대한 송신 수준 곡선을 조정합니다.

자세한 내용은 [spatializer 자습서의 5장을](tutorials/unity-spatial-audio-ch5.md) 참조하세요.

## <a name="unity-spatial-sound-examples"></a>Unity 공간 사운드 예제

Unity의 공간 소리 예제는 다음을 참조하세요.
* [MRTK 데모](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer 샘플 프로젝트](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 따라가는 경우 Mixed Reality 핵심 구성 요소에 대해 알아보세요. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [혼합 현실의 사운드 디자인](../../design/spatial-sound-design.md)
* [Microsoft의 spatializer 자습서](tutorials/unity-spatial-audio-ch1.md)
