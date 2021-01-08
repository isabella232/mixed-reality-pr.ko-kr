---
title: OpenXR 문제 해결
description: Windows Mixed Reality OpenXR 응용 프로그램에서 일반적으로 발생 하는 문제 해결에 대 한 리소스 및 답변을 찾아보세요.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 문제 해결
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006733"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="096f7-104">OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="096f7-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="096f7-105">Windows Mixed Reality OpenXR 런타임을 사용 하 여 OpenXR 앱을 개발할 때 발생 하는 몇 가지 문제 해결 팁은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="096f7-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>에 대 한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">여유 시간 #openxr 채널</a>을 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="096f7-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="096f7-107">현재 Windows Mixed Reality OpenXR 런타임에 x86 앱과 관련 하 여 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="096f7-108">현재 x64 용 데스크톱 OpenXR 앱을 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="096f7-109">Windows Mixed Reality를 시작 하지 않는 OpenXR 앱</span><span class="sxs-lookup"><span data-stu-id="096f7-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="096f7-110">OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="096f7-111">[OpenXR For Windows Mixed Reality 헤드셋 시작](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 의 지침에 따라 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="096f7-112">[Windows mixed Reality OpenXR 개발자 도구](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) 를 실행 하 여 시스템의 Windows Mixed Reality OpenXR 런타임 상태에 대 한 문제 해결 도움말을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="096f7-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>