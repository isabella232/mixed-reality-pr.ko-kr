---
title: AR Foundation 사용
description: Unity에서 ARFoundation을 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207459"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>iOS 및 Android용 MRTK를 구성하는 방법 [실험적]

## <a name="install-required-packages"></a>필요한 패키지를 설치합니다.

1. [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) 또는 Unity 패키지 관리자 **Microsoft.MixedReality.Toolkit.Unity.Foundation** 패키지를 [](../configuration/usingupm.md) 다운로드하여 가져옵니다.

1. Unity 패키지 관리자(UPM)에서 다음 패키지를 설치합니다.

    **Unity 2018.4.x**

    | **Android** | **iOS** | 의견 |
    | --- | --- | --- |
    | AR Foundation  <br/> 버전: 1.5.0 - 미리 보기 6 | AR Foundation  <br/> 버전: 1.5.0 - 미리 보기 6 | Unity 2018.4의 경우 이 패키지는 미리 보기로 포함되어 있습니다. 패키지를 보려면 다음을 수행합니다. `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 플러그 인 <br/> 버전: 2.1.2 | ARKit XR 플러그 인 <br/> 버전: 2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 버전: 2.1.8 |  AR Foundation  <br/> 버전: 2.1.8 |
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

1. **복사 및 사용자 지정을** 선택하여 MRTK 프로필 복제를 선택하여 사용자 지정 구성을 사용하도록 설정합니다.

    ![MRTK 프로필 복제](../features/images/camera-system/CloneProfileARFoundation.png)

1. 카메라 프로필 옆에 있는 **복제를** 선택합니다.

    ![MRTK 카메라 프로필 복제](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 검사기 패널을 카메라 시스템 섹션으로 이동하고 **카메라 설정 공급자 섹션을 확장합니다.**

    ![설정 공급자 확장](../features/images/camera-system/ExpandProviders.png)

1. **카메라 설정 공급자 추가를** 클릭하고 새로 추가된 새 카메라 **설정** 항목을 확장합니다.

    ![새 설정 공급자 확장](../features/images/camera-system/ExpandNewProvider.png)

1. Unity AR 카메라 설정 공급자 선택

    ![Unity AR 설정 공급자 선택](../features/images/camera-system/SelectUnityArSettings.png)

    Unity AR 카메라 설정 공급자를 구성하는 방법에 대한 자세한 내용은 [Unity AR 카메라 설정 공급자를 참조하세요.](../features/camera-system/unity-ar-camera-settings.md)

> [!NOTE]
> 이 설치는 AR Foundation 구성 요소가 장면에 있는지 확인합니다(애플리케이션이 시작될 때). 그렇지 않으면 ARCore 및 ARKit에서 작동하도록 자동으로 추가됩니다.
> 특정 동작을 설정해야 하는 경우 필요한 구성 요소를 직접 추가해야 합니다.
> AR Foundation 구성 요소 및 설치에 대한 자세한 내용은 이 [설명서를 참조하세요.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Android 및 iOS 디바이스에 대한 장면 빌드

1. UnityAR 카메라 설정 공급자를 장면에 추가했는지 확인합니다.

1. Unity 빌드 설정에서 플랫폼을 Android 또는 iOS로 전환

1. 연결된 XR 플러그 인 관리 공급자가 사용하도록 설정되어 있는지 확인합니다.

    iOS XR 플러그 인 관리:  ![ XR 플러그 인 관리 iOS](../features/images/XRManagementiOS.png)

1. 장면을 빌드하고 실행 합니다.

## <a name="see-also"></a>참고 항목

- [Unity AR 카메라 설정](../features/camera-system/unity-ar-camera-settings.md)
