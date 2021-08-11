---
title: 앱 바
description: MRTK의 앱 바에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 앱 바,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198280"
---
# <a name="app-bar"></a>앱 바

![앱 바](../images/app-bar/MRTK_AppBar_Main.png)

앱 바는 [경계 제어](bounds-control.md) 스크립트와 함께 사용 되는 UI 구성 요소입니다. 컨트롤을 조작 하기 위해 개체에 button 컨트롤을 추가 합니다. ' 조정 ' 단추를 사용 하 여 개체에 대 한 경계 컨트롤 인터페이스를 활성화/비활성화할 수 있습니다. "제거" 단추는 장면에서 개체를 제거 해야 합니다.

## <a name="how-to-use-app-bar"></a>앱 바를 사용 하는 방법

`AppBar`장면 계층에 (asset/MRTK/SDK/Features/UX/Prefabs/AppBar/appbar. prefab)를 끌어서 놓습니다. 구성 요소의 검사기 패널에서 범위 컨트롤을 포함 하는 개체를 *대상 경계 상자로* 할당 하 여 앱 바를 추가 합니다.

**중요:** 대상 개체에 대 한 범위 제어 활성화 옵션은 ' 수동으로 활성화 ' 해야 합니다.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
