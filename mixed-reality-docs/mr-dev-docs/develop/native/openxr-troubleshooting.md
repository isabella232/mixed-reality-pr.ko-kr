---
title: OpenXR 문제 해결
description: OpenXR 응용 프로그램의 문제를 해결 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 문제 해결
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612937"
---
# <a name="openxr-troubleshooting"></a>OpenXR 문제 해결

Windows Mixed Reality OpenXR 런타임을 사용 하 여 OpenXR 앱을 개발할 때 발생 하는 몇 가지 문제 해결 팁은 다음과 같습니다.  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>에 대 한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">여유 시간 #openxr 채널</a>을 방문 하세요.

>[!NOTE]
>현재 Windows Mixed Reality OpenXR 런타임에 x86 앱과 관련 하 여 알려진 문제가 있습니다.  현재 x64 용 데스크톱 OpenXR 앱을 빌드해야 합니다.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality를 시작 하지 않는 OpenXR 앱

OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정 되지 않을 수 있습니다. [OpenXR For Windows Mixed Reality 헤드셋 시작](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 의 지침에 따라 문제를 해결 합니다.

[Windows mixed Reality OpenXR 개발자 도구](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) 를 실행 하 여 시스템의 Windows Mixed Reality OpenXR 런타임 상태에 대 한 문제 해결 도움말을 가져올 수도 있습니다.