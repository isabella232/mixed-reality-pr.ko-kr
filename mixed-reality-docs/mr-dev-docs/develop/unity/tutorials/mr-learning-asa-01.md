---
title: Azure Spatial Anchors 자습서 소개
description: 이 과정을 완료하여 혼합 현실 애플리케이션에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, ios, android, Windows 10, ARCore, macOS, Android 빌드 지원, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 4d753546fd8fd0779e7614ca11e4668e359d8f9dcdc8db9d62e95267747471db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197363"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Azure Spatial Anchors 자습서 소개

Azure Spatial Anchors 자습서를 시작합니다. 이 자습서 시리즈를 통해 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a>(ASA)의 기본 사항과 실제 환경에서 완벽하게 혼합된 현실 경험을 고정하는 방법을 알아봅니다. Android 및 iOS에 프로젝트를 배포하는 방법에 대해서도 알아봅니다.

이 시리즈의 자습서:

1. [소개](mr-learning-asa-01.md)(이미 여기에 있음)
2. [Azure Spatial Anchors 시작](mr-learning-asa-02.md)
3. [Azure Spatial Anchors 저장, 검색 및 공유](mr-learning-asa-03.md)
4. [Azure Spatial Anchor 피드백 표시](mr-learning-asa-04.md)
5. [Android 및 iOS용 Azure Spatial Anchors](mr-learning-asa-05.md)

## <a name="objectives"></a>목표

* 공간 앵커를 만들고 Azure에서 가져오는 방법 알아보기
* 앱 세션 간에 공간 맞춤을 달성하는 방법 알아보기
* 여러 디바이스 간의 공간 맞춤을 구현하는 방법 알아보기
* Android 및 iOS에 대한 프로젝트를 준비, 빌드 및 배포하는 방법 알아보기

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 컴퓨터
* Windows 10 SDK(10.0.18362.0 이상 버전)
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* Unity 2020/2019 LTS가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 다음 자습서의 [Spatial Anchors 리소스 만들기](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료했습니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료했습니다.
* [시작 자습서](mr-learning-base-01.md) 시리즈 또는 Unity 및 MRTK를 사용하는 몇 가지 기본 사전 경험을 마쳤습니다.
* Android 및 HoloLens에 배포하려는 경우
  * Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스
  * Unity 2020/2019 LTS가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* iOS 및 HoloLens에 배포하려는 경우
  * 최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터
  * macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스
  * Unity 2020/2019 LTS가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!Important]
> 이 자습서 시리즈는 Open XR 또는 Windows XR 플러그 인을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)를 지원하고 레거시 WSA를 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)도 지원합니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.

> [!div class="nextstepaction"]
> [다음 자습서: 2. Azure Spatial Anchors를 사용하여 시작](mr-learning-asa-02.md)
