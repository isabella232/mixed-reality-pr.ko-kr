---
title: 네이티브 개발 개요
description: Windows Mixed Reality Api를 직접 사용 하 여 DirectX 기반 혼합 현실 엔진을 빌드하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱, 플랫폼 Api, 사용자 지정 엔진, 미들웨어, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 764cbe0a37501cc176e9bb05a9a7771b03666f0c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006853"
---
# <a name="native-development-overview"></a>네이티브 개발 개요

![기본 배너 로고](../images/native_logo_banner.png)

[Unity](../unity/unity-development-overview.md) , [unreal](../unreal/unreal-development-overview.md) 등의 3d 엔진은 유일 하 게 혼합 된 현실 개발 경로를 사용자에 게 공개 하지 않습니다. DirectX 11 또는 DirectX 12를 사용 하 여 Windows Mixed Reality Api를 사용 하 여 혼합 현실 앱을 만들 수도 있습니다. 플랫폼 소스로 이동 하 여 기본적으로 고유한 미들웨어 또는 프레임 워크를 빌드합니다. 

> [!IMPORTANT]
> 유지 하려는 기존 WinRT 프로젝트가 있는 경우 주 [winrt 설명서](creating-a-holographic-directx-project.md)를 참조 하세요. 

## <a name="development-checkpoints"></a>개발 검사점

다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.

### <a name="1-getting-started"></a>1. 시작

Windows Mixed Reality는 다음과 같은 [두 가지 종류의 앱을](../../design/app-views.md)지원 합니다.
* [HOLOGRAPHICSPACE api](getting-a-holographicspace.md) 또는 [OpenXR api](openxr.md) 를 사용 하는 UWP 또는 Win32 **Mixed Reality 응용 프로그램** 은 헤드셋 표시를 채우는 [몰입 형 보기](../../design/app-views.md) 를 렌더링 합니다.
* DirectX, XAML 또는 다른 프레임 워크를 사용 하 여 Windows Mixed Reality 홈의 슬레이트에서 [2d 뷰](../../design/app-views.md#2d-views) 를 렌더링 하는 **2d 앱** (UWP)

[2d 보기 및 몰입 형 보기](../../design/app-views.md) 에 대 한 DirectX 개발 간의 차이점은 주로 holographic 렌더링 및 공간 입력에 문제가 있습니다. UWP 응용 프로그램의 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 또는 Win32 응용 프로그램의 HWND는 필수 이며 거의 동일 하 게 유지 됩니다. 앱에서 사용할 수 있는 WinRT Api의 경우에도 마찬가지입니다. 하지만 holographic 기능을 활용 하려면 이러한 Api의 다른 하위 집합을 사용 해야 합니다. 예를 들어 holographic 용 시스템 응용 프로그램은 포즈 예측 프레임 루프를 사용 하도록 설정 된이 swapchain present 및 프레임을 관리 합니다.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. 핵심 구성 요소

Windows Mixed Reality 응용 프로그램은 다음 Api를 사용 하 여 HoloLens 및 기타 몰입 형 헤드셋에 대 한 [Mixed Reality](../../discover/mixed-reality.md) 환경을 구축 합니다.

|  특징  |  기능  |
| --- | --- |
| [응시](../../design/gaze-and-commit.md) | 사용자가 홀로그램을 확인하여 대상으로 할 수 있습니다. |
| [제스처](../../design/gaze-and-commit.md#composite-gestures) | 앱에 공간 작업 추가 |
| [홀로그램 렌더링](../platform-capabilities-and-apis/rendering.md) | 사용자를 중심으로 하는 정확한 위치에서 홀로그램 그리기 |
| [동작 컨트롤러](../../design/motion-controllers.md) | 사용자가 혼합 현실 환경에서 작업을 수행 하도록 허용 |
| [공간 매핑](../../design/spatial-mapping.md) | 가상 메시 오버레이를 사용하여 실제 공간을 매핑하여 환경 경계 표시 |
| [음성](../../design/voice-input.md) | 사용자의 음성 키워드, 구 및 받아쓰기 캡처 |
 
> [!NOTE]
> OpenXR [로드맵](openxr.md#roadmap) 설명서에서 예정 및 개발 중인 핵심 기능을 찾을 수 있습니다.

### <a name="3-deploying-and-testing"></a>3. 배포 및 테스트

HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋에서 OpenXR를 사용 하 여 데스크톱에서 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 [HoloLens 2 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 또는 [Windows Mixed Reality 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 를 대신 사용할 수 있습니다.

## <a name="whats-next"></a>다음 작업

특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다. 다음 섹션에서는 이미 완료 한 초보자 수준 자료를 벗어나는 영역으로 이동할 수 있습니다. 이러한 항목과 리소스는 순차적으로 정렬 되지 않으므로 자유롭게 이동 하 여 탐색할 수 있습니다.

### <a name="additional-resources"></a>추가 자료

OpenXR 게임의 수준을 설정 하려면 아래 링크를 확인 하세요.

* [OpenXR 모범 사례](openxr-best-practices.md)
* [OpenXR 성능](openxr-performance.md)
* [OpenXR 문제 해결](openxr-troubleshooting.md)

## <a name="see-also"></a>참조
* [앱 모델](../../design/app-model.md)
* [앱 보기](../../design/app-views.md)
