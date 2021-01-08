---
title: 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가 하 여 HoloLens 2 HRTF 하드웨어 오프 로드에 액세스 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007473"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Unity 프로젝트에 공간 오디오 추가

HoloLens2의 Unity 용 공간 오디오 자습서를 시작 합니다. 이 자습서 시퀀스는 다음을 보여 줍니다.
* Unity에서 HoloLens 2의 HRTF (head 관련 전송 함수) 오프 로드를 사용 하는 방법
* HRTF 오프 로드를 사용할 때 반향 기능을 사용 하도록 설정 하는 방법

[Microsoft Spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity) 는이 자습서 시퀀스의 완료 된 Unity 프로젝트를 포함 합니다. 

유용 하 게 사용할 수 있는 경우에 대 한 HRTF 기반 spatialization 기술과 권장 사항을 사용 하 여 소리를 spatialize 하는 것에 대 한 자세한 내용은 [공간 음향 디자인](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)을 참조 하세요.

## <a name="what-is-hrtf-offload"></a>HRTF 오프 로드 란?

HRTF 기반 알고리즘을 사용 하 여 오디오를 처리 하려면 많은 양의 특수 한 계산을 수행 해야 합니다. HoloLens 2에는 응용 프로그램 프로세서의 부담을 방지 하기 위해 활용할 수 있는 전용 하드웨어가 포함 되어 있습니다. 따라서 HRTF 기반 알고리즘의 처리를 "오프 로딩" 합니다.  Microsoft spatializer 플러그 인을 사용 하면 응용 프로그램이 공간 오디오 이외의 작업에 더 많은 응용 프로그램 프로세서를 사용할 수 있도록 응용 프로그램에서 전용 HRTF 하드웨어를 활용할 수 있는 쉬운 방법을 제공 합니다.

## <a name="objectives"></a>목표

이 첫 번째 장에서는 다음을 수행 합니다.
* Unity 프로젝트 만들기 및 MRTK 가져오기
* Microsoft spatializer 플러그 인 가져오기
* Microsoft spatializer 플러그 인 사용
* 개발자 워크스테이션에서 공간 오디오 사용

## <a name="create-a-project-and-add-nuget-for-unity"></a>프로젝트 만들기 및 Unity 용 NuGet 추가

빈 Unity 프로젝트로 시작한 다음 Unity에 대해 NuGet을 추가 하 고 구성 합니다.
1. 최신 NuGetForUnity를 다운로드 [합니다. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. Unity 메뉴 모음에서 **자산-> 가져오기 패키지-> 사용자 지정 패키지** ...를 클릭 하 고 NuGetForUnity 패키지를 설치 합니다.

![사용자 지정 패키지 가져오기](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Windows Mixed Reality 패키지 추가

Unity 2019 이상에서 Windows Mixed Reality 지원은 선택적 패키지에 포함 되어 있습니다. 프로젝트에 추가 하려면 Unity 메뉴 모음에서 **창 > 패키지 관리자** 를 엽니다.

![패키지 관리자 메뉴](images/spatial-audio/package-manager-menu.png)

그런 다음 **Windows Mixed Reality** 패키지를 찾아서 설치 합니다.

![패키지 관리자 창](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>MRTK 및 Microsoft Spatializer 설치

Unity에 NuGet을 사용 하 여 MRTK 및 Microsoft Spatializer 플러그 인을 설치 합니다.
1. Unity 메뉴 모음에서 **nuget > Nuget 패키지 관리** 를 클릭 합니다.

![NuGet 패키지 관리](images/spatial-audio/manage-nuget-packages.png)

2. **검색** 상자에 "MixedReality"를 입력 하 고 MRTK 핵심 패키지: **MixedReality** 를 설치 합니다.

![MRTK NuGet 패키지](images/spatial-audio/mrtk-nuget-package.png)

[Mrtk NuGet 패키지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) 에는 추가 컨텍스트 및 세부 정보가 있습니다.

4. **검색** 상자에 "SpatialAudio"를 입력 하 고 microsoft Spatializer Package: SpatialAudio를 설치 합니다. **Spatializer**

![Spatializer 플러그 인 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>프로젝트에서 MRTK 설정

1. **파일 > 빌드 설정** 으로 이동 하 여 빌드 설정 창을 엽니다.

2. _유니버설 Windows 플랫폼_ 를 선택 하 고 **플랫폼 전환** 을 클릭 합니다.

3. **빌드 창** 에서 **플레이어 설정** 을 클릭 하 여 **검사기** 창에서 **플레이어 설정** 속성을 엽니다.
    * **XR 설정** 에서 **가상 현실 지원** 확인란을 선택 합니다.
    * **XR 설정** 에서 **스테레오 렌더링 모드** 를 **인스턴스 하나로** 변경 합니다.
    * **게시 설정** 에서 **기능** 섹션의 **공간 인식** 확인란을 선택 합니다.

4. 메뉴 모음에서 **혼합 현실 도구 키트-장면에 추가 및 구성 >를 클릭 합니다.** 장면에 MRTK를 추가 합니다.

앱을 빌드하고 HoloLens 2에 배포 하는 방법을 비롯 한 추가 지침은 [MR 학습 기본 모듈의 1 장](../../../mrlearning-base-ch1.md)을 참조 하세요.

## <a name="enable-the-microsoft-spatializer-plugin"></a>Microsoft Spatializer 플러그 인 사용

**Microsoft Spatializer** 플러그 인을 사용 하도록 설정 합니다. **편집 > 프로젝트 설정-오디오 >** 열고 **Spatializer 플러그 인** 을 "Microsoft Spatializer"로 변경 합니다. 이제 **프로젝트 설정** 의 **Audio** 섹션이 다음과 같이 표시 됩니다.

![Spatializer 플러그 인을 보여 주는 프로젝트 설정](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>워크스테이션에서 공간 오디오 사용

데스크톱 버전의 Windows에서는 공간 오디오가 기본적으로 사용 하지 않도록 설정 되어 있습니다. 작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 여 사용 하도록 설정 합니다. HoloLens 2에서 제공 하는 내용을 가장 잘 표시 하려면 **공간 사운드-헤드폰 용 Windows Sonic >** 선택 합니다.

![데스크톱 공간 오디오 설정](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> 이 설정은 Unity 편집기에서 프로젝트를 테스트 하려는 경우에만 필요 합니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Unity 공간 오디오 챕터 2](unity-spatial-audio-ch2.md)

