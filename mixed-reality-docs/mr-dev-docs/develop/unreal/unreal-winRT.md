---
title: Unreal의 WinRT
description: HoloLens 장치에 대 한 Unreal mixed reality 앱에서 사용자 지정 WinRT 기능을 작성 하 고 관리 하는 방법을 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격 기능, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, WinRT, DLL
ms.openlocfilehash: 0d181d1eff644de0512c40a140474612a1540b40
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247756"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="f5a91-104">Unreal의 WinRT</span><span class="sxs-lookup"><span data-stu-id="f5a91-104">WinRT in Unreal</span></span>

<span data-ttu-id="f5a91-105">HoloLens 개발 과정에서 WinRT를 사용 하 여 기능을 작성 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a91-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="f5a91-106">예를 들어 HoloLens 응용 프로그램에서 파일 대화 상자를 열려면 winrt/FileSavePicker 헤더 파일에 해당 파일이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5a91-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="f5a91-107">WinRT는 버전 4.26부터 시작 하는 Unreal의 빌드 시스템에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5a91-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="f5a91-108">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="f5a91-108">Next Development Checkpoint</span></span>

<span data-ttu-id="f5a91-109">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 Mixed Reality 플랫폼 기능 및 API를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="f5a91-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="f5a91-110">여기에서 [토픽](unreal-development-overview.md#3-advanced-features) 을 계속 하거나 장치 또는 에뮬레이터에서 앱을 배포 하기 위해 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a91-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5a91-111">디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="f5a91-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="f5a91-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5a91-112">See also</span></span>

* [<span data-ttu-id="f5a91-113">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="f5a91-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="f5a91-114">FileSavePicker 클래스</span><span class="sxs-lookup"><span data-stu-id="f5a91-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="f5a91-115">실제 타사 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f5a91-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
