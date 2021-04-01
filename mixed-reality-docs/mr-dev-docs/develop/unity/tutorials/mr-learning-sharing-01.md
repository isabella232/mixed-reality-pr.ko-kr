---
title: 다중 사용자 기능 자습서 소개
description: 이 과정을 완료하여 HoloLens 2 애플리케이션에서 공유된 다중 사용자 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 다중 사용자 기능, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 5b7ad27d41147a57d03f4a1b5a78b92e6e1234d4
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550213"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. 다중 사용자 기능 자습서 소개

다중 사용자 기능 자습서를 시작합니다. 이 자습서 시리즈를 통해 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 네트워킹</a>(PUN)을 사용하여 다중 사용자 환경을 구축하는 기본 사항을 배우게 됩니다. PUN은 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.

이 시리즈의 자습서:

* [Photon Unity 네트워킹 설정](mr-learning-sharing-02.md)
* [여러 사용자 연결](mr-learning-sharing-03.md)
* [여러 사용자와 개체 움직임 공유](mr-learning-sharing-04.md)
* [공유 환경에 Azure Spatial Anchors 통합](mr-learning-sharing-05.md)

## <a name="objectives"></a>목표

* PUN 앱을 만들고 Unity 프로젝트를 연결하는 방법 알아보기
* 공유 환경에서 여러 사용자를 연결하는 방법 알아보기
* 개체 이동을 다른 사용자와 공유하는 방법 알아보기
* 여러 디바이스 간의 공간 맞춤을 구현하는 방법 알아보기

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 컴퓨터
* Windows 10 SDK 10.0.18362.0 이상
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* Unity 2019 LTS가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 다음 자습서의 [Spatial Anchors 리소스 만들기](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료했습니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료했습니다.
* [시작 자습서](mr-learning-base-01.md) 시리즈 또는 Unity 및 MRTK를 사용하는 몇 가지 기본 사전 경험을 완료했습니다.
* Azure Spatial Anchors 계정을 만드는 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 시리즈 또는 이전 환경을 완료했습니다.
* Android 및 HoloLens에 배포하려는 경우
  * Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스
  * Unity 2019 LTS가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* iOS 및 HoloLens에 배포하려는 경우
  * 최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터
  * macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스
  * Unity 2019 LTS가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!CAUTION]
> 이 자습서 시리즈에 권장되는 Mixed Reality Toolkit 버전은 MRTK 2.6입니다.

> [!CAUTION]
> 이 자습서 시리즈에 권장되는 Unity 버전은 Unity 2019 LTS입니다. 이 버전은 위의 링크에 연결된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.

> [!div class="nextstepaction"]
> [다음 자습서: 2. Photon Unity 네트워킹 설정](mr-learning-sharing-02.md)