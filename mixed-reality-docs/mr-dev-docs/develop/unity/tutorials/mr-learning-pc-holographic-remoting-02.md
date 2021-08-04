---
title: 홀로그램 원격 PC 애플리케이션 만들기
description: 이 과정을 완료하여 혼합 현실 환경을 PC에서 HoloLens 2로 원격으로 수행하는 PC 애플리케이션을 만드는 방법을 알아봅니다.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, PC 홀로그램 원격, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 19c10ad0cdad70b38663f9da0f7d2a1f1702d94d
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757235"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. 홀로그램 원격 PC 애플리케이션 만들기

이 자습서에서는 홀로그램 원격을 사용하는 PC 앱을 만드는 방법을 학습하여 진행 중인 작업을 HoloLens로 스트리밍하여 먼저 빌드하지 않고도 볼 수 있습니다.

[홀로그램 원격의 기본 사항에 대해 알아봅니다.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>목표

* 홀로그램 원격에 대한 Unity 구성
* Visual Studio를 사용하여 애플리케이션을 빌드하고 배포하는 방법 알아보기
* 홀로그램 원격 애플리케이션 개발 및 HoloLens에 연결

## <a name="configuring-the-capabilities"></a>기능 구성

프로젝트 설정 창에서 **게시 설정** 을 확장하고 **기능** 섹션으로 스크롤하여 기존 기능 외에 아래 표시 기능 확인란을 선택합니다.

* 인터넷 클라이언트 서버
* 개인 네트워크 클라이언트 서버

![기능 사용 설정](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>PC로 애플리케이션 빌드

이제 홀로그램 원격 앱을 PC에서 빌드할 준비가 되었습니다. 아래 단계를 수행하고 이 애플리케이션을 PC에 빌드하려면 이러한 변경을 수행합니다.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>홀로그램 원격 원격 애플리케이션 테스트

PC 애플리케이션을 HoloLens 2에 연결하려면 아래 프로세스를 수행합니다.

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. HoloLens 2 디바이스에 원격 플레이어 애플리케이션 설치

* HoloLens 2에서 스토어 앱을 방문하여 "**원격 플레이어**"를 검색합니다.
* **원격 플레이어** 앱을 선택합니다.
* **설치** 를 탭하여 앱을 다운로드하고 설치합니다.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. 원격 플레이어에 홀로그램 원격 PC 앱 연결

* HoloLens에서 **원격 플레이어** 를 시작합니다.
* HoloLens **IP 주소** 를 기록해 둡니다. 시작되는 즉시 **원격 플레이어** 에서 홀로그램으로 표시됩니다.
* 홀로그램 원격 PC 애플리케이션을 PC에서 엽니다.
* 애플리케이션이 시작되면 **IP 주소** 를 입력하고 **연결** 단추를 클릭하여 연결합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 제공하여 언제든지 홀로그램 원격 원격 앱을 만들고 HoloLens 2에 연결하는 방법을 알아보았습니다. HoloLens가 홀로그램 원격 PC 애플리케이션에 연결되면 HoloLens 2 디바이스로 스트리밍되는 혼합 현실 환경이 표시됩니다.
