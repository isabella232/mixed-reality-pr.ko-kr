---
title: MRTK 구성 대화 상자
description: Unity 프로젝트에서 MRTK 구성
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144833"
---
# <a name="mrtk-project-configuration-dialog"></a>MRTK 프로젝트 구성 대화 상자

UNITY에서 프로젝트를 로드할 때 MRTK 구성 대화 상자가 표시되고 하나 이상의 구성 옵션에 개발자의 주의가 필요한 것으로 확인됩니다.

![나중에 적용 무시](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

변경 내용을 적용하려면 **적용** 단추를 클릭합니다. **이후** 단추는 나중에 프로젝트가 다시 로드될 때까지 변경 내용을 연기합니다.

> [!NOTE]
> 권장 설정 중 하나 이상을 선택하지 않은 상태로 두면 구성 대화 상자가 다시 나타납니다. 이 문제가 발생하지 않도록 하려면 원하는 옵션을 적용한 다음 Mixed Reality **Toolkit** 유틸리티 Unity 프로젝트 구성을 통해 대화 상자를 다시 시작하고  >    >   **무시를** 클릭합니다. 이렇게 하면 구성 대화 상자가 자동으로 다시 나타나지 않습니다.

## <a name="common-settings"></a>일반 설정

모든 빌드 대상은 공통 옵션 컬렉션을 공유합니다.

![일반 설정](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>텍스트 자산 직렬화 강제 적용 및 표시되는 메타 파일 사용

이러한 설정은 Unity 프로젝트 및 소스 제어 시스템(예: Git) 작업을 간소화하는 데 도움이 됩니다.

### <a name="enable-vr-supported"></a>VR 지원 사용

**Unity 2018**

**플레이어 설정**  >  **XR 설정** 에서 Virtual Reality Supported 및 Virtual Reality SDK 옵션을 구성합니다.

### <a name="set-single-pass-instanced-rendering-path"></a>단일 패스 인스턴스 렌더링 경로 설정

**플레이어 설정**  >  **XR 설정**  >  **스테레오 렌더링 모드를** 단일 패스 **인스턴스화로 구성합니다.**

### <a name="set-default-spatial-awareness-layer"></a>기본 공간 인식 계층 설정

공간 인식을 레이어 31로 등록하여 광선 캐스트 및 물리학 옵션을 쉽고 일관되게 구성할 수 있도록 합니다.

### <a name="audio-spatializer"></a>오디오 spatializer

Audio spatializers는 혼합 현실 경험을 위해 공간 사운드 및 위치 오디오의 강력한 기능을 해제 하는 구성 요소입니다.

> [!NOTE]
> 오디오 spatializer를 없음으로 설정 하면 위치 오디오 기능이 사용 되지 않습니다.

#### <a name="common-spatializers"></a>일반 spatializers

- Microsoft Spatializer

Microsoft에서 HoloLens 2에서 하드웨어 가속의 사용률을 지 원하는 spatializer을 제공 했습니다.

이 spatializer는 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 및 [GitHub](https://github.com/microsoft/spatialaudio-unity)를 통해 사용할 수 있습니다.

Microsoft Spatializer에 대 한 자세한 내용은 [공간 사운드 설명서](/windows/mixed-reality/spatial-sound-in-unity)에서 찾을 수 있습니다.

- MS HRTF Spatializer

Windows Mixed Reality 및 Windows XR 플랫폼 패키지의 일부로 Unity에서 제공 하는 Microsoft Windows spatializer입니다.

- Resonance 오디오

Unity를 통해 제공 되는 Google의 플랫폼 간 spatializer.

자세한 내용은 [Resonance Audio 설명서](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 사이트에서 찾을 수 있습니다.

## <a name="universal-windows-platform-settings"></a>유니버설 Windows 플랫폼 설정

![UWP 설정](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP 기능

유니버설 Windows 플랫폼 응용 프로그램에 대 한 특정 응용 프로그램 기능을 사용 하도록 설정 합니다. 이러한 기능을 통해 플랫폼은 특정 기능을 사용할 수 있는 권한을 알리고 요청할 수 있습니다.

- 마이크

  마이크를 통해 소리를 캡처할 수 있습니다.

- 인터넷 클라이언트

  인터넷에서 리소스에 액세스할 수 있도록 지원합니다.

- 공간 인식

  실제 환경 사용을 지원합니다.

- 시선 응시

  **Unity 2019.3 이상**

  사용자의 시선 응시 추적을 지원합니다.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Unity 'PlayerSettings.graphicsJob' 충돌 방지

**Unity 2019.3 이상**

최신 버전의 Unity 2019에서 "그래픽 작업"을 사용하도록 설정하면 HoloLens 2 배포할 때 앱이 충돌합니다.
이 설정은 Unity에서 기본적으로 사용하도록 설정됩니다. 이 버그가 있는 [동안(Unity 버그](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)참조) 구성기는 기본적으로 그래픽 작업을 'false'로 설정하므로 에 배포된 앱이 충돌하지 HoloLens 2 허용합니다.

## <a name="android-settings"></a>Android 설정

Android 지원 디바이스에서 AR 애플리케이션을 지원하기 위한 구성 설정입니다.

![Android 설정](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>다중 스레드 렌더링 사용 안 함

Android의 AR 지원에서 요구하는 대로 **플레이어 설정**  >  **기타 설정** 다중 스레드  >  **렌더링을** 사용하지 않도록 설정합니다.

### <a name="set-minimum-api-level"></a>최소 API 수준 설정

**AR**  >  애플리케이션에 대한 운영 체제 요구 사항을 적용하도록 플레이어 설정 기타 **설정**  >  **최소 API 수준** 값을 설정합니다.

## <a name="ios-settings"></a>iOS 설정

iOS 지원 디바이스에서 AR 애플리케이션을 지원하기 위한 구성 설정입니다.

![iOS 설정](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>필수 OS 버전 설정

**AR**  >  애플리케이션에 대한 운영 체제 요구 사항을 적용하도록 플레이어 설정 기타 **설정** 대상  >  **최소 iOS 버전** 값을 설정합니다.

### <a name="set-required-architecture"></a>필수 아키텍처 설정

**플레이어 설정**  >  **기타 설정** 아키텍처의 값을 설정  >   하 여 AR 응용 프로그램에 대 한 플랫폼 요구 사항을 적용 합니다.

### <a name="set-camera-usage-descriptions"></a>카메라 사용 설명 설정

**플레이어 설정** 의 값을 설정 합니다  >  .**다른 설정**  >  **카메라 사용 설명은** 장치의 카메라 사용 권한을 요청 하는 데 사용 됩니다.