---
title: 홀로그램 원격 PC 애플리케이션 만들기
description: 이 과정을 완료하여 혼합 현실 환경을 PC에서 HoloLens 2로 원격으로 수행하는 PC 애플리케이션을 만드는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, PC 홀로그램 원격, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: fd357b0b487b948afb6ae15c9e84362e2bc1ef90
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007333"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. 홀로그램 원격 PC 애플리케이션 만들기

이 자습서에서는 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 제공하여 언제든지 홀로그램 원격을 위한 PC 앱을 만들고 HoloLens 2에 연결하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* 홀로그램 원격에 대한 Unity 구성
* Visual Studio를 사용하여 애플리케이션을 빌드하고 배포하는 방법 알아보기
* 홀로그램 원격 애플리케이션 개발 및 HoloLens에 연결

## <a name="configuring-your-scene-for-holographic-remoting"></a>홀로그램 원격에 대한 장면 구성

이 섹션에서는 Wi-Fi 연결을 통해 실시간으로 PC에서 HoloLens 2 디바이스로 혼합 현실 환경을 스트리밍하는 프로젝트를 구성합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** 폴더로 이동하고,**HolographicRemoting** 프리팹을 클릭하여 장면으로 끕니다.

![새로 추가한 HolographicRemoting 프리팹이 여전히 선택된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>PC로 애플리케이션 빌드

이제 홀로그램 원격 앱을 PC에서 빌드할 준비가 되었습니다. 아래 단계를 수행하고 이 애플리케이션을 PC에 빌드하려면 이러한 변경을 수행합니다.

### <a name="1-set-the-player-settings"></a>1. 플레이어 설정 지정

Unity 메뉴에서 편집 >프로젝트 설정을 차례로 선택하여 플레이어 설정 창을 엽니다.

프로젝트 설정 창에서 **게시 설정** 을 확장하고 **기능** 섹션으로 스크롤하여 기존 기능 외에 아래 표시 기능 확인란을 선택합니다.

* 인터넷 클라이언트 서버
* 개인 네트워크 클라이언트 서버

**XR 설정** 섹션에서 **WSA 홀로그램 원격 지원** 확인란을 선택하고 홀로그램 원격을 사용하도록 설정합니다.

![WSA 홀로그램 원격 지원이 사용되도록 설정된 Unity XR 설정 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Unity 프로젝트 빌드

Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.

Build Settings(빌드 설정) 창에서 **_Add Open Scenes_* _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다. Build(빌드) 목록에서 _*_Build 단추_*_ 를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.

![장면이 추가된 Unity Build Settings 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

빌드 유니버설 Windows 플랫폼 창에서 빌드를 저장할 적합한 위치(예: Documents\MixedRealityLearning)를 선택합니다. 새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다. 그런 다음, _*_Select Folder(폴더 선택)_*_ 단추를 클릭하여 빌드 프로세스를 시작합니다.

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![진행 중인 Unity 빌드 프로세스](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. 애플리케이션 빌드 및 배포

빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다. 폴더 내부를 탐색하고 .sln 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 도구 설치 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

릴리스 구성, x64 아키텍처 및 로컬 머신을 대상으로 선택하여 PC에 대해 Visual Studio를 구성합니다.

![로컬 컴퓨터에 대해 구성된 Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

_*_로컬 컴퓨터_*_ 라고 표시된 단추를 클릭합니다. 애플리케이션을 빌드하고 PC에 배포하기 시작합니다. 애플리케이션은 기본적으로 PC에 설치됩니다.

## <a name="testing-holographic-remoting-remote-application"></a>홀로그램 원격 원격 애플리케이션 테스트

PC 애플리케이션을 HoloLens 2에 연결하려면 아래 프로세스를 수행합니다.

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. HoloLens 2 디바이스에 원격 플레이어 애플리케이션 설치

HoloLens 2에서 스토어 앱을 방문하여 "**원격 플레이어**"를 검색합니다.
* **원격 플레이어** 앱을 선택합니다.
* **설치** 를 탭하여 앱을 다운로드하고 설치합니다.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. 원격 플레이어에 홀로그램 원격 PC 앱 연결

* HoloLens에서 **원격 플레이어** 를 시작합니다.
* HoloLens **IP 주소** 를 기록해 둡니다. 시작되는 즉시 **원격 플레이어** 에서 홀로그램으로 표시됩니다.
* 홀로그램 원격 PC 애플리케이션을 PC에서 엽니다.
* 애플리케이션이 시작되면 **IP 주소** 를 입력하고 **연결** 단추를 클릭하여 연결합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 제공하여 언제든지 홀로그램 원격 원격 앱을 만들고 HoloLens 2에 연결하는 방법을 알아보았습니다. HoloLens가 홀로그램 원격 PC 애플리케이션에 연결되면 HoloLens 2 디바이스로 스트리밍되는 혼합 현실 환경이 표시됩니다.
