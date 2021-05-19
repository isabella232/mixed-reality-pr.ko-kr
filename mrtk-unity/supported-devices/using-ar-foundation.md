---
title: AR Foundation 사용
description: Unity에서 ARFoundation 사용에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 코어, AR 키트
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143945"
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

    **Unity 2020.1.x(현재 공식적으로 지원되지 않음, 정보 제공 목적으로만 포함됨)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 버전: 3.1.3 |  AR Foundation  <br/> 버전: 3.1.3 |
    | ARCore XR 플러그 인 <br/> 버전: 3.1.4 | ARKit XR 플러그 인 <br/> 버전: 3.1.3 |

1. 메뉴 항목을 호출하여 MRTK UnityAR 스크립팅 정의 업데이트: **Mixed Reality Toolkit > Utilities > UnityAR > 업데이트 스크립팅 정의**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Unity AR 카메라 설정 공급자 사용

다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다. 다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.

    ![MRTK 구성 장면 계층 구조](../features/images/MRTK_ConfiguredHierarchy.png)

1. **복사 및 사용자 지정을** 선택하여 MRTK 프로필 복제를 선택하여 사용자 지정 구성을 사용하도록 설정합니다.

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

    플랫폼을 전환할 때 선택한 플랫폼에 대 한 설정이 포함 된 MRTK 프로젝트 구성 기 창이 표시 됩니다.  플랫폼 특정 설정을 사용 하려면 적용을 클릭 합니다.

    iOS 프로젝트 구성자 설정

    ![iOS 프로젝트 구성기](../features/images/camera-system/MRTKProjectConfigurator.png)

1. Android용 플랫폼을 전환한 후에는 추가 단계가 없습니다.

1. 플랫폼이 iOS인 경우 최적화 헤더에서 플레이어 > 기타 설정 > 프로젝트 설정 > 편집에서 엔진 코드 **제거를 선택 취소합니다.**

    ![iOS 설정](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > 줄무늬 엔진 코드의 선택을 취소하는 것은 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)오류에 대한 단기 솔루션입니다.  장기 솔루션에 대해 작업하고 있습니다.

1. 장면 빌드 및 실행

## <a name="see-also"></a>참고 항목

- [Unity AR 카메라 설정](../features/camera-system/unity-ar-camera-settings.md)
