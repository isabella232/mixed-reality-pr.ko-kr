---
title: Unreal의 WinRT
description: HoloLens 장치에 대해 진짜 혼합 현실 앱에서 사용자 지정 WinRT 기능을 작성 하 고 관리 하는 방법을 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: unreal, unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, WinRT, DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198419"
---
# <a name="winrt-in-unreal"></a>Unreal의 WinRT

HoloLens 개발 과정에서 WinRT를 사용 하 여 기능을 작성 해야 할 수 있습니다. 예를 들어 HoloLens 응용 프로그램에서 파일 대화 상자를 열려면 winrt/Windows에서 FileSavePicker가 필요 합니다. Storage. 선택. h 헤더 파일입니다. WinRT는 버전 4.26부터 시작 하는 Unreal의 빌드 시스템에서 지원 됩니다.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 Mixed Reality 플랫폼 기능 및 API를 살펴보는 중입니다. 여기에서 [토픽](unreal-development-overview.md#3-advanced-features) 을 계속 하거나 장치 또는 에뮬레이터에서 앱을 배포 하기 위해 바로 이동할 수 있습니다.

> [!div class="nextstepaction"]
> [디바이스에 배포](unreal-deploying.md)

## <a name="see-also"></a>추가 정보

* [C + +/WinRT Api](/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker 클래스](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [실제 타사 라이브러리](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)