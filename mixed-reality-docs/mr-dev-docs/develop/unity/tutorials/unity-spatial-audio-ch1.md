---
title: 공간 오디오 자습서-1. 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가 하 여 HoloLens 2 HRTF 하드웨어 오프 로드에 액세스 합니다.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head 관련 전송 함수, 반향, Microsoft Spatializer
ms.openlocfilehash: 1eb2913f1953e334cfe75b786f96bb51a9852fc5
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578456"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Unity 프로젝트에 공간 오디오 추가

## <a name="overview"></a>개요

HoloLens2의 Unity 용 공간 오디오 자습서를 시작 합니다. 이 자습서 시리즈를 통해 HoloLens 2에서 HRTF (head 관련 전송 함수) 오프 로드를 사용 하는 방법과 HRTF 오프 로드를 사용할 때 반향를 사용 하도록 설정 하는 방법에 대해 알아봅니다.

[Microsoft Spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity) 는이 자습서 시퀀스의 완료 된 Unity 프로젝트를 포함 합니다.

유용 하 게 사용할 수 있는 경우 HRTF 기반 spatialization 기술과 권장 사항을 사용 하 여 소리를 spatialize 소리를 이해 하려면 [공간 음향 디자인](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)을 참조 하세요.

## <a name="what-is-hrtf-offload"></a>HRTF 오프 로드 란?

HRTF 기반 알고리즘을 사용 하 여 오디오를 처리 하려면 많은 양의 특수 한 계산을 수행 해야 합니다. HoloLens 2에는 응용 프로그램 프로세서의 부담을 방지 하기 위해 활용할 수 있는 전용 하드웨어가 포함 되어 있습니다. 따라서 HRTF 기반 알고리즘의 처리를 "오프 로딩" 합니다.  Microsoft spatializer 플러그 인을 사용 하면 응용 프로그램이 공간 오디오 이외의 작업에 더 많은 응용 프로그램 프로세서를 사용할 수 있도록 응용 프로그램에서 전용 HRTF 하드웨어를 활용할 수 있는 쉬운 방법을 제공 합니다.

## <a name="objectives"></a>목표

* Microsoft spatializer 플러그 인 가져오기 및 사용
* 개발자 워크스테이션에서 공간 오디오 사용

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC
* 기본적인 C# 프로그래밍 지식
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2019 LTS가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가되어 있음)

계속 하기 전에 [초보자](mr-learning-base-01.md) 를 위한 자습서 시리즈를 완료 하거나 Unity 및 MRTK를 사용 하 여 몇 가지 기본 사전 경험을 사용 하는 **것이 좋습니다** .

> [!IMPORTANT]
>
> * 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019 LTS입니다. 이는 위에서 연결된 필수 구성 요소에서 설명하는 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정

1. [빌드 플랫폼 전환](mr-learning-base-02.md#configuring-the-unity-project)

1. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project)

1. [장면을 만들고 설정](mr-learning-base-02.md#creating-and-configuring-the-scene) 하 고 장면에 적절 한 이름 (예: *SpatialAudio* )을 제공 합니다.

그런 다음 [공간 인식 디스플레이 변경 옵션](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필이 **DefaultXRSDKConfigurationProfile** 고 공간 인식 메시의 표시 옵션을 **폐색** 로 변경 합니다.

## <a name="adding-microsoft-spatializer-to-the-project"></a>프로젝트에 Microsoft Spatializer 추가

Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio Spatializer</a> 를 다운로드 하 여 가져옵니다. 1.0.18. unitypackage

>[!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

## <a name="enable-the-microsoft-spatializer-plugin"></a>Microsoft Spatializer 플러그 인 사용

**Microsoft Spatializer** 를 가져온 후에는 사용 하도록 설정 해야 합니다. **편집 > 프로젝트 설정-오디오 >** 열고 **Spatializer 플러그 인** 을 "Microsoft Spatializer"로 변경 합니다.

![Spatializer 플러그 인을 보여 주는 프로젝트 설정](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>워크스테이션에서 공간 오디오 사용

데스크톱 버전의 Windows에서는 공간 오디오가 기본적으로 사용 하지 않도록 설정 되어 있습니다. 작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 여 사용 하도록 설정 합니다. HoloLens 2에서 제공 하는 내용을 가장 잘 표시 하려면 **공간 사운드-헤드폰 용 Windows Sonic >** 선택 합니다.

![데스크톱 공간 오디오 설정](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> 이 설정은 Unity 편집기에서 프로젝트를 테스트 하려는 경우에만 필요 합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Microsoft Spatializer 플러그 인을 가져오고 사용 하도록 설정 하는 방법 및 워크스테이션에서 공간 오디오를 사용 하도록 설정 하는 방법을 학습.
다음 자습서에서는 unity 프로젝트에서 공간 오디오를 추가 하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 2. Spatializing button 상호 작용 소리](unity-spatial-audio-ch2.md)
