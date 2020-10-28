---
title: OpenXR 문제 해결
description: OpenXR 응용 프로그램의 문제를 해결 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 문제 해결
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903096"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="446be-104">OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="446be-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="446be-105">Windows Mixed Reality OpenXR 런타임을 사용 하 여 OpenXR 앱을 개발할 때 발생 하는 몇 가지 문제 해결 팁은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="446be-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="446be-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>에 대 한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">여유 시간 #openxr 채널</a>을 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="446be-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="446be-107">현재 Windows Mixed Reality OpenXR 런타임에 x86 앱과 관련 하 여 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="446be-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="446be-108">현재 x64 용 데스크톱 OpenXR 앱을 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="446be-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="446be-109">Windows Mixed Reality를 시작 하지 않는 OpenXR 앱</span><span class="sxs-lookup"><span data-stu-id="446be-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="446be-110">OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="446be-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="446be-111">런타임을 활성화 하려면 [OpenXR For Windows Mixed Reality 헤드셋 시작](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="446be-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="446be-112">Windows mixed reality [OpenXR 개발자 도구](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) 를 실행 하 여 시스템의 Windows Mixed Reality OpenXR 런타임 상태에 대 한 추가 문제 해결 도움말을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="446be-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>