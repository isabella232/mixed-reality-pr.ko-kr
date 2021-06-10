---
title: 공간 오디오 자습서 - 1. 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가하여 HoloLens 2 HRTF 하드웨어 오프로드에 액세스합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, 혼합 현실 도구 키트, UWP, Windows 10, HRTF, 헤드 관련 전송 함수, reverb, Microsoft Spatializer
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403364"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Unity 프로젝트에 공간 오디오 추가

## <a name="overview"></a>개요

HoloLens2의 Unity에 대한 공간 오디오 자습서를 시작합니다. 이 자습서 시리즈를 통해 HoloLens 2 HRTF(헤드 관련 전송 함수) 오프로드를 사용하는 방법과 HRTF 오프로드를 사용할 때 반향을 사용하도록 설정하는 방법을 알아봅니다.

[Microsoft Spatializer GitHub 리포지토리에는](https://github.com/microsoft/spatialaudio-unity) 이 자습서 시퀀스의 완료된 Unity 프로젝트가 있습니다.

HRTF 기반 공간화 기술을 사용하여 소리를 공간화하는 것의 의미와 도움이 될 수 있는 경우에 대한 권장 사항을 이해하려면 [공간 음향 디자인을](/windows/mixed-reality/spatial-sound-design)참조하세요.

## <a name="what-is-hrtf-offload"></a>HRTF 오프로드란?

HRTF 기반 알고리즘을 사용하여 오디오를 처리하려면 많은 양의 특수 계산이 필요합니다. HoloLens 2 애플리케이션 프로세서의 부담을 피하기 위해 활용할 수 있는 전용 하드웨어를 포함하므로 HRTF 기반 알고리즘의 처리를 "오프로드"합니다.  Microsoft spatializer 플러그 인은 애플리케이션이 전용 HRTF 하드웨어를 활용할 수 있는 쉬운 방법을 제공하므로 애플리케이션이 공간 오디오 이외의 작업에 더 많은 애플리케이션 프로세서를 사용할 수 있습니다.

## <a name="objectives"></a>목표

* Microsoft spatializer 플러그 인 가져오기 및 사용
* 개발자 워크스테이션에서 공간 오디오 사용

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC
* 기본적인 C# 프로그래밍 지식
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity</a> 2020/2019 LTS가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 Unity Hub

계속하기 전에 [시작](mr-learning-base-01.md) 자습서 시리즈를 완료하거나 Unity 및 MRTK에 대한 기본적인 사전 경험을 갖추는 **것이 좋습니다.**

> [!Important]
> 이 자습서 시리즈는 Open XR 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)를 지원하고 레거시 WSA 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)도 지원합니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정

1. [빌드 플랫폼 전환](mr-learning-base-02.md#configuring-the-unity-project)

1. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Mixed Reality 도구 키트 가져오기 및 Unity 프로젝트 구성](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. [장면 만들기 및 구성](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름(예: *SpatialAudio)을* 지정합니다.

그런 다음 [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면에 대한 MRTK 구성 프로필이 **DefaultHoloLens2ConfigurationProfile인지** 확인하고 공간 인식 메시의 표시 옵션을 **폐색으로 변경합니다.**

## <a name="adding-microsoft-spatializer-to-the-project"></a>프로젝트에 Microsoft Spatializer 추가

Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage</a> 다운로드 및 가져오기

>[!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [자습서 자산 가져오기](mr-learning-base-02.md#importing-the-tutorial-assets) 지침을 참조할 수 있습니다.

## <a name="enable-the-microsoft-spatializer-plugin"></a>Microsoft Spatializer 플러그 인 사용

Microsoft Spatializer를 Unity 프로젝트로 가져오면 **MRTK Project Configurator** 창이 **나타나고, Audio spatializer** 드롭다운을 사용하여 **Microsoft Spatializer** 를 선택한 다음, 적용 단추를 클릭하여 설정을 적용합니다.

![MRTK 프로젝트 구성기](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

Microsoft Spatializer: **Edit -> Project Settings -> Audio를** 수동으로 사용하도록 설정하고 **Spatializer 플러그 인을** "Microsoft Spatializer"로 변경할 수도 있습니다.

![spatializer 플러그 인을 보여주는 프로젝트 설정](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>워크스테이션에서 공간 오디오 사용

데스크톱 버전의 Windows에서는 공간 오디오가 기본적으로 사용하지 않도록 설정됩니다. 작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭하여 사용하도록 설정합니다. HoloLens 2 가장 잘 표현하려면 **공간 소리 -> 헤드폰용 Windows Sonic** 를 선택합니다.

![데스크톱 공간 오디오 설정](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> 이 설정은 Unity 편집기에서 프로젝트를 테스트하려는 경우에만 필요합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Microsoft Spatializer 플러그 인을 가져오고 사용하도록 설정하고 워크스테이션에서 공간 오디오를 사용하도록 설정하는 방법을 알아봅니다.
다음 자습서에서는 Unity 프로젝트에서 공간 오디오를 추가하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 2. 단추 상호 작용 소리 공간화](unity-spatial-audio-ch2.md)
