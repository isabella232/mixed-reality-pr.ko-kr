---
title: Android 및 iOS MRTK 구성 (ARFoundation)
description: Unity에서 MRTK for Android 및 iOS (ARFoundation)를 구성 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 코어, AR 키트, iOS, IOS, Android, AR
ms.openlocfilehash: 9f621008db76e3f8e443545b795db442d7c17dda
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345136"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>IOS 및 Android 용 MRTK를 구성 하는 방법 [실험적]

## <a name="install-required-packages"></a>필요한 패키지를 설치합니다.

1. [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) 또는 [Unity 패키지 관리자](../configuration/usingupm.md) 에서 **MixedReality** 패키지를 다운로드 하 여 가져옵니다.

1. UPM (Unity 패키지 관리자)에서 다음 패키지를 설치 합니다.

    **Unity 2018.4.x**

    | **Android** | **iOS** | 의견 |
    | --- | --- | --- |
    | AR  <br/> 버전: 1.5.0-preview 6 | AR  <br/> 버전: 1.5.0-preview 6 | Unity 2018.4의 경우이 패키지는 미리 보기로 포함 되어 있습니다. 패키지를 보려면 다음을 수행 합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 플러그 인 <br/> 버전: 2.1.2 | ARKit XR 플러그 인 <br/> 버전: 2.1.2 | |

    **Unity 2019.4**

    | **Android** | **iOS** |
    | --- | --- |
    | AR  <br/> 버전: 2.1.8 |  AR  <br/> 버전: 2.1.8 |
    | ARCore XR 플러그 인 <br/> 버전: 2.1.11 | ARKit XR 플러그 인 <br/> 버전: 2.1.9 |

    **Unity 2020.1 (현재 공식적으로 지원 되지 않음, 정보 제공 목적 으로만 포함)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR  <br/> 버전: 3.1.3 |  AR  <br/> 버전: 3.1.3 |
    | ARCore XR 플러그 인 <br/> 버전: 3.1.4 | ARKit XR 플러그 인 <br/> 버전: 3.1.3 |

1. 메뉴 항목을 호출 하 여 MRTK UnityAR scripting를 업데이트 합니다. **혼합 현실 > Toolkit > 유틸리티 > UnityAR > 업데이트 스크립팅 정의**

    ![업데이트 스크립팅 정의](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Unity AR 카메라 설정 공급자 사용

다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다. 다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. **복사 및 사용자** 지정을 선택 하 여 MRTK 프로필을 복제 하 고 사용자 지정 구성을 사용 하도록 설정 합니다.

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. 카메라 프로필 옆의 **복제** 를 선택 합니다.

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 설정 공급자** 섹션을 확장 합니다.

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. **카메라 설정 공급자 추가** 를 클릭 하 고 새로 추가 된 **새 카메라 설정** 항목을 확장 합니다.

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. Unity AR 카메라 설정 공급자를 선택 합니다.

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    Unity AR 카메라 설정 공급자를 구성 하는 방법에 대 한 자세한 내용은 [UNITY ar 카메라 설정 공급자를 제공](../features/camera-system/unity-ar-camera-settings.md)합니다.

> [!NOTE]
> AR 구성 요소가 장면에 있는 경우이 설치는 응용 프로그램이 시작 될 때를 확인 합니다. 그렇지 않은 경우 ARCore 및 Arcore에서 사용할 수 있도록 자동으로 추가 됩니다.
> 특정 동작을 설정 해야 하는 경우에는 필요한 구성 요소를 직접 추가 해야 합니다.
> AR 기반 구성 요소 및 설치에 대 한 자세한 내용은이 [설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)를 참조 하세요.

## <a name="building-a-scene-for-android-and-ios-devices"></a>Android 및 iOS 장치에 대 한 장면 빌드

1. 장면에 UnityAR 카메라 설정 공급자를 추가 했는지 확인 합니다.

1. Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환 합니다.

1. 연결 된 XR 플러그 인 관리 공급자가 사용 하도록 설정 되어 있는지 확인 합니다.

    iOS XR 플러그 인 관리:  ![ XR 플러그 인 관리 iOS](../features/images/XRManagementiOS.png)

1. 장면을 빌드하고 실행 합니다.

## <a name="see-also"></a>참조

- [Unity AR 카메라 설정](../features/camera-system/unity-ar-camera-settings.md)
