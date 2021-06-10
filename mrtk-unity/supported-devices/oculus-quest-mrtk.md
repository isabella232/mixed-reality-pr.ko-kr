---
title: Oculus Quest MRTK
description: MRTK에서 Oculus Quest를 구성하기 위한 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Oculus Quest,
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908390"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a>XR SDK 파이프라인을 사용하여 Oculus Quest에 MRTK 빌드 및 배포

[Oculus Quest가](https://www.oculus.com/quest/) 필요합니다.

Oculus Quest에 대한 MRTK의 지원은 Unity의 XR SDK 파이프라인과 Oculus Integration Unity 패키지의 두 가지 소스를 통해 제공됩니다. **Oculus XRSDK Data Provider** 두 소스를 모두 사용할 수 있으며 Oculus Quest에 MRTK를 배포하는 데 사용해야 합니다.

[Unity XR SDK 파이프라인을](https://docs.unity3d.com/Manual/XR.html) 사용하면 Oculus Quest를 통해 Oculus Touch 컨트롤러 및 헤드 추적을 사용할 수 있습니다.
이 파이프라인은 Unity 2019.3 이상에서 XR 애플리케이션을 개발하기 위한 표준입니다. 이 파이프라인을 사용하려면 Unity **2019.3 이상** 을 사용해야 합니다. 이는 MRTK 애플리케이션을 Oculus Quest에 배포하는 **데 필요합니다.**

[Oculus Integration Unity 패키지를 사용하면 Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) Quest에서 **손 추적을** 사용할 수 있습니다. 이 데이터 **공급자는** Unity의 **XR SDK 파이프라인** 또는 레거시 **XR 파이프라인 을** 사용하지 않습니다.

## <a name="setting-up-project-for-the-oculus-quest"></a>Oculus Quest에 대한 프로젝트 설정

1. [다음 단계에](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 따라 프로젝트가 Oculus Quest에 배포할 준비가 되었는지 확인합니다.

1. 디바이스에서 [개발자 모드가](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 사용하도록 설정되어 있는지 확인합니다. Oculus ADB 드라이버를 설치하는 것은 선택 사항입니다.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Oculus Quest용 XR SDK 파이프라인 설정

1. **Oculus XR 플러그 인이** 창 **--> 패키지 관리자** 아래에 설치되어 있는지 확인합니다.

    ![Oculus XR 플러그 인 패키지](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. **편집 --> 프로젝트 설정 --> XR 플러그 인 관리 --> 플러그 인 공급자로** 진행하여 Oculus 플러그 인 공급자가 프로젝트에 포함되어 있는지 확인합니다.

    ![Oculus 플러그 인 공급자](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>수동 추적을 사용하도록 Oculus Integration Unity 패키지 설정

1. Unity 자산 저장소에서 [Oculus Integration을](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 다운로드하고 가져옵니다. 작동하도록 테스트된 최신 버전은 20.0.0입니다. 이전 버전은 이 [보관에서](https://developer.oculus.com/downloads/package/unity-integration-archive/)찾을 수 있습니다.

1. Mixed Reality Toolkit > Utilities > Oculus > Integration Unity Modules로 이동합니다. 이렇게 하면 관련 Oculus Quest 코드가 작동하는 데 필요한 정의 및 참조를 사용하여 asmdefs가 업데이트됩니다. 또한 csc 파일을 업데이트하여 Oculus 통합 자산에서 생성된 사용되지 않는 경고를 필터링합니다. MRTK 리포지션에는 경고를 오류로 변환하는 csc 파일이 포함되어 있습니다. 이 변환은 MRTK-Quest 구성 프로세스를 중지합니다.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. 가져온 Oculus 폴더(Assets/Oculus에서 찾을 수 있음)에는 OculusProjectConfig라는 스크립팅 가능한 개체가 있습니다. 해당 구성 파일에서 HandTrackingSupport를 "컨트롤러 및 손"으로 설정해야 합니다.

    ![Oculus 통합 컨트롤러 및 손](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>장면 설정

1. 새 Unity 장면을 만들거나 HandInteractionExamples와 같은 기존 장면을 엽니다.
1. **Mixed Reality Toolkit** 장면에 추가 및 구성으로 이동하여 MRTK를  >  **장면에 추가합니다.**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Oculus XR SDK Data Provider 사용

::: moniker range=">= mrtkunity-2021-05"

1. **Oculus XR SDK Data Provider** 사용하도록 프로필 구성
    - 구성 프로필을 수정하지 않으려는 경우
        - Unity의 XR 파이프라인에서 모두 구성된 기본 MRTK 프로필을 사용합니다. 이전 DefaultXRSDKConfigurationProfile은 이제 사용되지 않음 레이블이 지정됩니다.
        - 프로젝트 [빌드 및 Oculus Quest 에 배포로](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)이동합니다.
    - 그렇지 않으면 다음을 따릅니다.
        - 계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - **입력** 구성 프로필을 선택합니다.

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - 입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - 입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.  새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager 로** 설정합니다.

        ![Oculus XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. **Oculus XR SDK Data Provider** 사용하도록 프로필 구성
    - 구성 프로필을 수정하지 않으려는 경우
        - 프로필을 DefaultXRSDKConfigurationProfile로 변경합니다.
        - 프로젝트 [빌드 및 Oculus Quest 에 배포로](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)이동합니다.
    - 그렇지 않으면 다음을 따릅니다.
        - 계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.

        ![프로필 복제](../images/cross-platform/CloneProfile.png)

        - **입력** 구성 프로필을 선택합니다.

        ![입력 구성 프로필](../images/cross-platform/InputConfigurationProfile.png)

        - 입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.

        ![입력 시스템 프로필 복제](../images/cross-platform/CloneInputSystemProfile.png)

        - 입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.  새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager 로** 설정합니다.

        ![Oculus XRSDK Data Provider 추가](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. Oculus XR SDK Data Provider 입력을 올바르게 라우팅하도록 OVR Camera Rig 및 OVR Hands를 사용하여 프로젝트를 자동으로 구성하는 OVR Camera Rig Prefab이 포함되어 있습니다. 장면에 OVR Camera Manual을 수동으로 추가하려면 설정 및 입력을 수동으로 구성해야 합니다.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>프로젝트를 빌드하고 Oculus Quest에 배포

1. USB 3.0 -> USB C 케이블을 통해 Oculus Quest 플러그 인
1. 파일 **> 빌드 설정으로** 이동합니다.
1. **배포를 Android로** 변경
1. Oculus Quest가 해당 실행 디바이스로 선택되었는지 확인합니다.

    ![Oculus 디바이스 실행](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. 빌드 및 실행 선택
    - 빌드 *및 실행을* 처음 선택하면 다음과 같은 빌드 오류 집합이 발생할 수 있습니다. *빌드 및 실행을* 다시 선택하면 성공적으로 배포할 수 있습니다.

    ![Oculus 예상 빌드 오류](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Quest 내부에서 _USB 디버깅 허용_ 프롬프트를 수락합니다.
1. Oculus Quest 내의 장면 보기

## <a name="removing-oculus-integration-from-the-project"></a>프로젝트에서 Oculus 통합 제거

1. Mixed Reality Toolkit > Oculus > 별도의 Oculus Integration Unity 모듈  ![ Oculus Separation Asmdef로 이동합니다.](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Unity를 Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef의 참조로 새로 고치도록 하고 다른 파일을 이 단계에서 수정합니다.
1. Unity 닫기
1. Visual Studio 닫습니다(열려 있는 경우).
1. 파일 탐색기 열고 MRTK Unity 프로젝트의 루트로 이동합니다.
1. UnityProjectName/Library 디렉터리 삭제
1. UnityProjectName/Assets/Oculus 디렉터리 삭제
1. UnityProjectName/Assets/Oculus.meta 파일을 삭제합니다.
1. Unity 다시 열기

## <a name="common-errors"></a>일반 오류

### <a name="quest-not-recognized-by-unity"></a>Unity에서 인식할 수 없는 Quest

Android 경로가 제대로 구성되었는지 확인합니다. 문제가 계속 발생하면 이 [가이드를](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools) 따르세요.

**Android에서 외부 도구 > > > 기본 설정 편집**

![Android 도구 구성](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
