---
title: MRTK의 컨트롤러
description: MRTK에서 다양한 컨트롤러 사용에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 컨트롤러, HP Reverb, Oculus, HTC Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145488"
---
# <a name="controllers-in-mrtk"></a>MRTK의 컨트롤러

MRTK는 다양한 컨트롤러를 지원합니다. HTC Vive Knuckles 및 HTC Vive Wands와 같은 많은 컨트롤러는 MRTK로 빌드된 애플리케이션이 호환되는 디바이스에서 시작되면 기본적으로 작동합니다. Oculus Quest 및 HP Reverb G2 컨트롤러의 굴절된 손과 같은 다른 컨트롤러는 MRTK에서 인식되기 전에 추가 패키지가 필요합니다.

이 문서에서는 추가 패키지를 설치해야 하는 일반적인 시나리오를 설명합니다. 컨트롤러에 대한 자세한 내용은 기능 페이지 를 [**방문하세요.**](../features/input/controllers.md) 컨트롤러 관련 문제를 디버그하려면 [ **컨트롤러 매핑 도구를 참조하세요.**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP Reverb G2 컨트롤러

MRTK를 사용할 때 HP Reverb G2 컨트롤러를 검색하고 표시하려면 다음 단계에 따라 [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 패키지를 설치합니다. 이 패키지가 설치되면 컨트롤러가 HP Reverb에 표시되기 위해 기본 프로필을 변경할 필요가 없습니다. 

편집기에서 컨트롤러를 표시하려면 [**OpenXR 플러그 인**](/windows/mixed-reality/develop/unity/openxr-getting-started)을 사용하여 를 사용하고 있는지 확인해야 합니다.

## <a name="oculus-controllers"></a>Oculus 컨트롤러 

Oculus 컨트롤러 모델을 시각화하려면 Oculus Quest 배포 지침을 따릅니다. 컨트롤러를 사용할 때 가상 손을 표시하려면 XR SDK Oculus 디바이스 **관리자에서 컨트롤러 대신 아바타 손 렌더링을** 선택해야 합니다. 그렇지 않으면 이 옵션을 선택 취소합니다.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
