---
title: MRTK 자습서 소개
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 처음부터 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, solvers, 시선 추적, 음성 명령
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224789"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. MRTK 자습서 소개

초보자를 위한 자습서 시리즈를 시작합니다. 이러한 자습서의 과정을 통해 MRTK(Mixed Reality Toolkit) 및 제공해야 하는 기능 중 일부에 대해 알아봅니다. 또한 사용자가 NASA의 Mars Curiosity Rover 이후에 모델링된 홀로그램을 탐색할 수 있는 혼합 현실 환경을 구축합니다. 이 시리즈의 끝 부분에서는 MRTK를 이해하고 개발 프로세스의 속도를 높이는 방법을 배웁니다.

이 시리즈의 자습서는 순차적이므로 올바른 순서로 진행하세요.

1. [소개](mr-learning-base-01.md)(이미 여기에 있음)
2. [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)
3. [MRTK 프로필 구성](mr-learning-base-03.md)
4. [장면에서 개체 위치 지정](mr-learning-base-04.md)
5. [해결기를 사용하여 동적 콘텐츠 만들기](mr-learning-base-05.md)
6. [사용자 인터페이스 만들기](mr-learning-base-06.md)
7. [3D 개체와 상호 작용](mr-learning-base-07.md)
8. [시선 추적 사용](mr-learning-base-08.md)
9. [음성 명령 사용](mr-learning-base-09.md)

## <a name="objectives"></a>목표

* MRTK에 대한 Unity를 구성하는 방법 알아보기
* 빌드하고 디바이스에 배포하는 방법 알아보기
* MRTK의 주요 기능 중 일부를 사용하는 방법 알아보기
* 완전한 혼합 현실 환경 만들기

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 이상
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스

* Unity 2020.3 LTS 또는 Unity 2019.4 LTS가 설치된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(**OpenXR은 버그 방지를 위해 2020.3.8 이상 필요**)

Unity를 설치할 때는 **'Platforms'('플랫폼')** 아래에서 다음 구성 요소를 확인하세요.

* **유니버설 Windows 플랫폼 빌드 지원**
* **Windows 빌드 지원(IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'Add Modules'('모듈 추가')** 메뉴를 통해 추가할 수 있습니다.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> 이 자습서 시리즈에 추천되는 MRTK 버전은 MRTK 2.7.2입니다.

> [!Important]
> 이 자습서 시리즈는 Open XR 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)와 레거시 WSA 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)를 지원합니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.

> [!div class="nextstepaction"]
> [다음 자습서: 2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)
