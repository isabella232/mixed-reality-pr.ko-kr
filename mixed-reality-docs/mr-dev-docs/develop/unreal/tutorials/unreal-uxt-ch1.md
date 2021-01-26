---
title: 1. 시작
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 체스 앱을 만드는 자습서 시리즈 1/6부
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 자습서, 시작, mrtk, uxt, UX Tools, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: a46b9fef96f75f3d80b9ebbd5cbd724730374b41
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580566"
---
# <a name="1-getting-started"></a>1. 시작

혼합 현실을 처음 접하든 노련한 전문가이든 관계 없이 [HoloLens 2](../../../index.yml) 및 [Unreal Engine](https://www.unrealengine.com/en-US/) 과정은 여기에서 시작됩니다. 이 자습서 시리즈에서는 [Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)의 일부인 [UX Tools 플러그 인](https://github.com/microsoft/MixedReality-UXTools-Unreal)을 사용하여 대화형 체스 앱을 빌드하는 방법을 단계별로 안내합니다. 플러그 인은 코드, 청사진 및 예제를 통해 프로젝트에 일반 UX 기능을 추가하는 데 도움이 됩니다. 

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

시리즈를 마치면 다음에 대한 경험을 갖게 됩니다.
* 새 프로젝트 시작
* 혼합 현실 설정
* 사용자 입력 작업
* 단추 추가
* 에뮬레이터 또는 디바이스에서 재생

## <a name="prerequisites"></a>필수 구성 요소

진행하기 전에 다음을 설치했는지 확인합니다.
* Windows 10 1809 이상
* Windows 10 SDK 10.0.18362.0 이상
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 이상
* [개발용으로 구성된](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 디바이스 또는 [에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* Visual Studio 2019(아래 워크로드 포함)

### <a name="installing-visual-studio-2019"></a>Visual Studio 2019 설치

먼저 다음과 같은 필수 Visual Studio 패키지를 모두 사용하여 설정을 확인합니다.
1. 최신 버전의 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)를 다운로드합니다.
1. 다음 [워크로드](/visualstudio/install/modify-visual-studio#modify-workloads)를 설치합니다.
    * C++를 사용한 데스크톱 개발
    * .NET 데스크톱 개발
    * 유니버설 Windows 플랫폼 개발
1. 유니버설 Windows 플랫폼 개발을 확장하고 다음을 선택합니다. 
    * USB 디바이스 연결
    * C++(v142) 유니버설 Windows 플랫폼 도구

1. 다음 [구성 요소](/visualstudio/install/modify-visual-studio#modify-individual-components)를 설치합니다.
    * 컴파일러, 빌드 도구 및 런타임 > MSVC v142 - VS 2019 C++ ARM64 빌드 도구(최신 버전)

다음 그림을 통해 설치를 확인할 수 있습니다.

![VS 설치 관리자의 중요한 틱](images/unreal-uxt/1-install-the-tools.png)

간단하죠. 체스 프로젝트를 시작할 준비가 되었습니다.

[다음 섹션: 2. 프로젝트 및 첫 번째 애플리케이션 초기화](unreal-uxt-ch2.md)