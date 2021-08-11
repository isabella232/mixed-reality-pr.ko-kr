---
title: Android 및 iOS용 Azure Spatial Anchors
description: 이 과정을 완료하면 MRTK(Mixed Reality Toolkit) 및 Azure Spatial Anchors가 포함된 Unity 프로젝트를 Android 및 iOS에 배포하는 방법을 알아볼 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, android, ios, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215882"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Android 및 iOS용 Azure Spatial Anchors

이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* Unity AR Foundation 및 ARCore XR 플러그 인을 사용하여 Android 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.
* Unity AR Foundation 및 ARKit XR 플러그 인을 사용하여 iOS 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.

## <a name="installing-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 설치

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>AR Foundation Camera에 대한 MRTK 구성

이 섹션에서는 모바일 디바이스에 배포하기 위해 MRTK를 구성하는 방법을 알아봅니다.

Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택합니다. 그런 다음, Inspector(인스펙터) 창에서 **Camera** 탭을 선택하고 카메라 프로필을 복제한 다음, 적절한 이름(예: **AzureSpatialAnchors_ARCameraProfile**)을 지정합니다.

![새로 만든 ARCameraProfile이 선택된 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제하는 방법은 [Mixed Reality Toolkit 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.

검사기 창에서 **카메라** 탭을 선택한 상태에서 **카메라 설정 공급자** 를 확장하고 "-"를 클릭하여 **Windows Mixed Reality 카메라 설정** 또는 **XR SDK Windows Mixed Reality 카메라 설정** 을 제거합니다.

![새 데이터 공급자가 추가된 Unity ARCameraProfile ](images/mr-learning-asa/asa-05-section2-step1-2.png)

**+ 카메라 설정 공급자 추가** 단추를 클릭한 다음 새로 추가된 **새 데이터 공급자** 를 확장합니다.

![Android에 대해 추가된 AR 카메라](images/mr-learning-asa/asa-05-section2-step1-3.png)

**유형** 드롭다운을 사용하여 유형을 **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** 로 변경합니다.

![데이터 공급자 유형 선택 경로가 있는 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-4.png)

메뉴 항목을 호출하여 MRTK UnityAR 스크립팅 정의를 업데이트합니다. **Mixed Reality** > **Toolkit** > **유틸리티** > **UnityAR** > 스크립팅 정의 업데이트

## <a name="building-your-application-to-your-android-device"></a>Android 디바이스에 애플리케이션 빌드

이 섹션에서는 프로젝트를 구성하고 빌드하여 Android 디바이스에 배포하는 방법을 알아봅니다.

Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 연 다음, 플랫폼을 Android로 전환합니다.

![Android 플랫폼이 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> 빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.

빌드 설정 창을 닫습니다.

Unity 메뉴에서 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![Unity MRTK Project Configurator 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Vulkan** 을 선택하고 **"-"** 기호를 클릭하여 제거합니다.

![Vulcan이 선택된 Unity Other Settings](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다. 그런 다음, USB 케이블을 사용하여 Android 디바이스를 컴퓨터에 연결하고 **Run Device**(디바이스 실행) 드롭다운 목록에서 선택합니다.

![장면이 추가되고 Run Device가 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Run Device(디바이스 실행) 드롭다운 목록에 디바이스가 보이지 않으면 드롭다운 목록 옆에 있는 새로 고침 단추를 눌러야 할 수도 있습니다.

빌드 설정 창에서 **빌드 및 실행** 단추를 클릭하여 Build Android(Android 빌드) 창을 엽니다.

빌드를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택한 다음, apk에 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정하고 **저장** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![Save 프롬프트 창이 있는 Unity Build Settings 창 Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Android SDK, NDK 및 JDK 모듈과 관련된 Unity 콘솔 창에 오류가 발생하면 Unity Hub를 열고 Android 빌드 지원 모듈과 관련된 Android 빌드 지원 모듈을 설치해야 합니다.

빌드 프로세스가 완료되면 앱이 Android 디바이스에 자동으로 로드됩니다.

## <a name="building-your-application-to-your-ios-device"></a>iOS 디바이스에 애플리케이션 빌드

이 섹션에서는 프로젝트를 구성하고 빌드하여 iOS 디바이스에 배포하는 방법을 알아봅니다.

Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 열고 플랫폼을 iOS로 전환합니다.

![iOS가 선택된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> 빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.

빌드 설정 창을 닫습니다.

Unity 메뉴에서 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 을 선택하여 **MRTK Project Configurator** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![Unity MRTK Project Configurator 창 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Strip Engine Code**(엔진 코드 스트립) 확인란 선택을 취소하여 사용하지 않도록 설정합니다.

![스트립 엔진 코드가 비활성화된 Unity Other Settings](images/mr-learning-asa/asa-05-section4-step1-3.png)

플레이어 설정 창을 닫고 **빌드** 설정 창을 다시 엽니다.

빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다.

![장면이 추가된 Unity Build Settings 창](images/mr-learning-asa/asa-05-section4-step1-4.png)

빌드 설정 창에서 **빌드** 단추를 클릭하여 Build iOS(iOS 빌드) 창을 엽니다.

Xcode 프로젝트를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어서 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정한 다음, **폴더 선택** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![저장 프롬프트 창이 있는 Unity Build Settings 창 iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

빌드 프로세스가 완료되면 [Xcode 프로젝트 내보내기](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) 지침에 따라 Xcode 프로젝트를 iOS 디바이스에 배포하는 방법을 알아봅니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아보았습니다.
