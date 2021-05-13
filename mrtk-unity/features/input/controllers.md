---
title: Controllers
description: MRTK에서 컨트롤러를 사용하는 방법
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 컨트롤러,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850339"
---
# <a name="controllers"></a>Controllers

컨트롤러는 입력 공급자 에 의해 자동으로 만들어지고 [**소멸됩니다.**](input-providers.md) 각 컨트롤러 형식에는 입력 값의 데이터 형식(Digital, Single Axis, Dual Axis, Six Dof, ...) 및 입력의 원점을 설명하는 *입력 형식(Button* Press, Trigger, Thumb Stick, Spatial Pointer, ...)을 알려주는 축 *형식으로* 정의된 여러 *실제* 입력이 있습니다. 물리적 입력은 Mixed Reality 도구 키트 구성 요소의 입력 시스템 프로필 아래에 있는 **컨트롤러 입력 매핑 프로필의** 를 통해 *입력* *작업에* 매핑됩니다.

MRTK는 [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 패키지가 설치될 때 WMR 컨트롤러를 자동으로 검색하고 표시합니다. 컨트롤러 모델은 OpenXR 파이프라인을 사용하는 경우에만 편집기에 표시됩니다. Oculus 컨트롤러 모델을 시각화하려면 [Oculus Quest 배포 지침을 따릅니다.](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![컨트롤러 입력 매핑](../images/input/ControllerInputMapping.png)