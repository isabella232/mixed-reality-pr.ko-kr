---
title: Controllers
description: MRTK에서 컨트롤러를 사용하는 방법
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 컨트롤러,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224771"
---
# <a name="controllers"></a>Controllers

컨트롤러는 입력 공급자 에 의해 자동으로 만들어지고 [**소멸됩니다.**](input-providers.md) 각 컨트롤러 형식에는 입력 값의 데이터 형식(Digital, Single Axis, Dual Axis, Six Dof, ...) 및 *입력의* 원점을 설명하는 입력 형식(Button Press, Trigger, Thumb Stick, Spatial Pointer, ...)을 알려주는 축 *형식으로* 정의된 여러 *실제* 입력이 있습니다. 실제 입력은 컨트롤러 *입력* 매핑 **프로필** 의 Mixed Reality Toolkit 구성 요소의 입력 시스템 *프로필에서* 를 통해 입력 작업에 매핑됩니다.

![컨트롤러 입력 매핑](../images/input/ControllerInputMapping.png)
