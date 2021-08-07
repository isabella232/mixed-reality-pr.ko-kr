---
title: OpenXR 시작
description: Windows Mixed Reality 및 HoloLens 2 헤드셋에서 이식 가능한 OpenXR API 표준 사용을 시작합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR 개발자 도구, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 시작, 101, 미리 보기 확장, OpenXR 런타임 버전, 시스템 상태
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189158"
---
# <a name="getting-started-with-openxr"></a>OpenXR 시작

데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 Emulator 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="getting-started-with-openxr-for-hololens-2"></a>openXR for HoloLens 2 시작

HoloLens 2 OpenXR 애플리케이션 개발을 시작하려면 다음을 수행합니다.

1. HoloLens 2 설정하거나 지침에 따라 [HoloLens 2 에뮬레이터의 최신 버전을 설치합니다.](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 최근 에뮬레이터 이미지를 사용하거나 디바이스가 해당 OS를 업데이트한 경우 OpenXR 1.0을 사용할 준비가 이미 되어 있어야 합니다.
2. 디바이스 또는 에뮬레이터에서 **스토어** 앱을 시작하여 모든 [확장이](openxr.md#roadmap) 있는 최신 OpenXR 런타임이 있는지 확인합니다.
    * 오른쪽 위에서 메뉴를 열고 다운로드 **및 업데이트를** 선택한 다음, **업데이트 받기를 선택합니다.**  

> [!NOTE]
> 에뮬레이터를 사용하는 경우 에뮬레이터 이미지를 시작할 때마다 에뮬레이터 이미지가 다시 설정되므로 최신 버전의 [HoloLens 2 에뮬레이터 이미지가](../platform-capabilities-and-apis/using-the-hololens-emulator.md)있는지 확인하는 것이 가장 좋습니다.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋용 OpenXR 시작

몰입형 Windows Mixed Reality 헤드셋용 OpenXR 애플리케이션 개발을 시작하려면 다음을 수행합니다.

1. Windows Mixed Reality 최종 사용자가 OpenXR 애플리케이션을 실행하기 위한 최소 요구 사항인 Windows 10 2019년 5월 업데이트(1903) 이상을 실행하고 있는지 확인합니다.  이전 버전의 Windows 10 경우 Windows 10 <a href="https://www.microsoft.com/software-download/windows10" target="_blank">업데이트 도우미</a>를 사용하여 업그레이드할 수 있습니다.
2. Windows Mixed Reality 헤드셋을 설정하거나 지침에 따라 [Windows Mixed Reality 시뮬레이터를 사용하도록 설정합니다.](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

이것으로 끝입니다.  Windows Mixed Reality OpenXR 런타임이 설치되고 모든 Windows Mixed Reality 사용자에 대해 자동으로 활성화됩니다.  그런 다음 Microsoft Store 런타임을 최신 상태로 유지합니다.

Windows Mixed Reality OpenXR 런타임을 다시 활성화하려면 시작 메뉴 Mixed Reality 포털 시작하고 창 위쪽에서 "수정"을 선택합니다.  해당 단추가 없으면 OpenXR 런타임이 이미 활성 상태입니다.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>openXR for 개발자 도구 Windows Mixed Reality

Windows Mixed Reality OpenXR 런타임을 사용해보려면 Windows Mixed Reality <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">앱용 OpenXR 개발자 도구</a>설치하면 됩니다.  이 앱은 활성 런타임 및 현재 헤드셋에 대한 주요 정보가 있는 시스템 상태 페이지와 함께 다양한 OpenXR 기능의 데모를 제공합니다.

HoloLens 2 에뮬레이터를 사용하는 경우 Windows Mixed Reality 대한 OpenXR 개발자 도구 설치하는 가장 쉬운 방법은 [Windows 장치 포털](../platform-capabilities-and-apis/using-the-windows-device-portal.md)통해서입니다. "OpenXR" 페이지로 이동한 다음 , 물리적 HoloLens 2 디바이스에서도 작동하는 "개발자 기능" 아래의 "설치" 단추를 클릭합니다.

![Windows Mixed Reality 앱용 OpenXR 개발자 도구](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

OpenXR 개발에 필요한 [도구를 아직 설치하지](../install-the-tools.md) 않은 경우 설치해야 합니다.

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 프로젝트는 Visual Studio Win32 및 UWP HoloLens 2 프로젝트 파일이 있는 간단한 OpenXR 샘플을 보여줍니다. 솔루션에는 HoloLens UWP 프로젝트가 포함되어 있으므로 완전히 열려면 [Visual Studio 유니버설 Windows Platform 개발 워크로드가](../install-the-tools.md#installation-checklist) 설치되어 있어야 합니다.

Win32 및 UWP 프로젝트 파일은 패키징 및 배포의 차이로 인해 별개이지만 각 프로젝트 내의 앱 코드는 거의 동일합니다.

OpenXR Win32 데스크톱 .EXE 빌드한 후 헤드셋 유형에 관계없이 OpenXR을 지원하는 모든 데스크톱 VR 플랫폼에서 VR 헤드셋과 함께 사용할 수 있습니다.

OpenXR UWP 앱 패키지를 빌드한 후 해당 패키지를 HoloLens 2 디바이스 또는 HoloLens 2 Emulator [배포할](../platform-capabilities-and-apis/using-visual-studio.md) 수 있습니다.

## <a name="learning-the-openxr-api"></a>OpenXR API Learning

OpenXR API 둘러보기의 경우 Visual Studio <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 샘플의 60분 분량의 비디오를 확인하세요.  이 비디오에서는 OpenXR API의 각 주요 구성 요소를 사용자 고유의 엔진에서 사용할 수 있는 방법을 보여 줍니다. 또한 현재 OpenXR을 기반으로 빌드된 애플리케이션 중 일부를 보여 줍니다.

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>OpenXR 로더를 프로젝트에 통합

기존 프로젝트에서 OpenXR을 시작하려면 OpenXR 로더를 포함합니다.  로더는 디바이스에서 활성 OpenXR 런타임을 검색하고 구현하는 핵심 함수 및 확장 함수에 대한 액세스를 제공합니다.

Visual Studio 프로젝트에서 [공식 OpenXR NuGet 패키지를 참조하거나](#reference-official-openxr-nuget-package) Khronos GitHub 리포지토리의 [공식 OpenXR 로더 원본을 포함할](#include-official-openxr-loader-source) 수 있습니다.  두 방법 중 하나를 사용하면 OpenXR 1.0 핵심 기능과 게시된 및 확장에 액세스할 수 `KHR` `EXT` `MSFT` 있습니다.

확장을 실험하려는 경우 `MSFT_preview` Mixed Reality GitHub 리포지션에서 [미리 보기 OpenXR 헤더를 복사할](#using-preview-extensions) 수 있습니다.

### <a name="reference-official-openxr-nuget-package"></a>공식 OpenXR NuGet 패키지 참조

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR.Loader** NuGet 패키지는 Visual Studio</a> C++ 솔루션에서 미리 .DLL OpenXR 로더를 참조하는 가장 쉬운 방법입니다.  이렇게 하면 OpenXR 1.0 핵심 기능과 게시된 및 확장에 액세스할 수 `KHR` `EXT` `MSFT` 있습니다.

OpenXR.Loader NuGet 패키지 참조를 Visual Studio C++ 솔루션에 추가하려면 다음을 수행합니다.
1. **솔루션 탐색기** OpenXR을 사용할 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...를** 선택합니다.
2. **찾아보기** 탭으로 전환하고 **OpenXR.Loader 를 검색합니다.**
3. **OpenXR.Loader** 패키지를 선택하고 오른쪽의 세부 정보 창에서 설치를 선택합니다.
4. 확인을 선택하여 프로젝트의 변경 내용을 적용합니다.
5. `#include <openxr/openxr.h>`를 소스 파일에 추가하여 OpenXR API 사용을 시작합니다.

작동하는 OpenXR API의 예를 보려면 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 샘플 앱을 확인하세요.

### <a name="include-official-openxr-loader-source"></a>공식 OpenXR 로더 원본 포함

로더를 직접 빌드하려는 경우(예: 추가 로더 .DLL 방지하기 위해) 공식 Khronos OpenXR 로더 원본을 프로젝트로 끌어올 수 있습니다.  이렇게 하면 OpenXR 1.0 핵심 기능과 게시된 및 확장에 액세스할 수 `KHR` `EXT` `MSFT` 있습니다.

여기서 시작하려면 <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub 의 Khronos OpenXR-SDK 리포지토리에 있는</a>지침을 따르세요.  프로젝트가 CMake를 사용하여 빌드하도록 설정됩니다. MSBuild 사용하는 경우 코드를 사용자 고유의 프로젝트에 복사해야 합니다.

## <a name="using-preview-extensions"></a>미리 보기 확장 사용

`MSFT_preview` [확장 로드맵에](openxr.md#roadmap) 나열된 확장은 피드백을 수집하기 위해 미리 보기 중인 실험적 공급업체 확장입니다.  이러한 확장은 개발자 디바이스 전용이며 실제 확장이 배송될 때 제거됩니다.

사용 가능한 확장을 사용해 보려는 경우 `MSFT_preview` 다음 단계를 수행하여 프로젝트를 업데이트합니다.
1. 위의 방법 중 하나에 따라 OpenXR 로더를 프로젝트에 통합합니다.
2. 프로젝트의 표준 OpenXR 헤더를 GitHub Mixed Reality <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">OpenXR 리포지점의 미리 보기 헤더로</a>대체합니다.

그런 다음 대상 HoloLens 2 또는 데스크톱 PC에서 미리 보기 확장 지원을 활성화하려면 다음을 수행합니다.
  1. 모든 [확장이](openxr.md#roadmap) 있는 최신 OpenXR 런타임이 있는지 확인하려면 대상 디바이스 또는 에뮬레이터 내에서 **스토어** 앱을 시작하고, 오른쪽 위에 있는 메뉴를 열고, **다운로드 및 업데이트를** 선택하고, **업데이트 받기를** 선택합니다.
  2. Microsoft Store Windows Mixed Reality <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">앱용 OpenXR 개발자 도구</a> 대상 디바이스에 설치하고 실행합니다.
  3. **개발자 설정** 탭으로 이동하여 최신 미리 **보기 OpenXR 런타임 사용을** 사용하도록 설정합니다.  이렇게 하면 미리 보기 확장이 활성화된 디바이스에서 미리 보기 런타임이 활성화됩니다.
     ![Windows Mixed Reality 앱용 OpenXR 개발자 도구 개발자 설정 탭](images/mixed-reality-openxr-developer-tools-settings.png)
  4. [Windows Mixed Reality 대한 OpenXR 개발자 도구](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) 시스템 **상태** 탭에 표시된 **런타임** 버전이 시도하려는 미리 보기 확장의 필수 버전과 일치하는지 확인합니다.  이 경우 **확장** 목록에 확장이 표시됩니다.  안정적인 확장을 사용할 수 있게 되면 미리 보기 확장이 제거됩니다.<br />
     ![Windows Mixed Reality 앱용 OpenXR 개발자 도구 시스템 상태 탭](images/mixed-reality-openxr-developer-tools-status.png)

이러한 미리 보기 확장에 대한 설명서 및 사용 방법에 대한 샘플은 <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality OpenXR 리포지션을</a> 참조하세요.

## <a name="troubleshooting"></a>문제 해결

OpenXR 개발을 시작하고 실행하는 데 문제가 있는 경우 [문제 해결 팁](openxr-troubleshooting.md)를 확인하세요.