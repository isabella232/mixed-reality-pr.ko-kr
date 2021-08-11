---
title: OpenXR 문제 해결
description: Windows Mixed Reality OpenXR 애플리케이션의 일반적인 문제 해결에 대한 리소스 및 답변을 찾습니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 문제 해결
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219207"
---
# <a name="openxr-troubleshooting"></a>OpenXR 문제 해결

다음은 Windows Mixed Reality OpenXR 런타임을 사용하여 OpenXR 앱을 개발할 때의 몇 가지 문제 해결 팁입니다.  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양에</a>대한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">Slack #openxr 채널을</a>방문하세요.

>[!NOTE]
>x86 앱을 사용한 현재 Windows Mixed Reality OpenXR 런타임에는 알려진 문제가 있습니다.  현재 x64용 데스크톱 OpenXR 앱을 빌드해야 합니다.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 앱이 Windows Mixed Reality 시작되지 않음

OpenXR 앱을 실행할 때 Windows Mixed Reality 시작하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정되지 않을 수 있습니다. [Windows Mixed Reality 헤드셋용 OpenXR을 시작하기 위한 지침에](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 따라 문제를 해결합니다.

Windows Mixed Reality [OpenXR 개발자 도구](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) 실행하여 OpenXR 런타임을 Windows Mixed Reality 시스템 상태에 대한 문제 해결 도움말을 얻을 수도 있습니다.