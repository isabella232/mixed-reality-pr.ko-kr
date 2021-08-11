---
title: MRTK에서 컨트롤러 검색
description: MRTK와 함께 다양 한 컨트롤러 사용에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 컨트롤러, HP 반향, oculus, HTC vive, 실습
ms.openlocfilehash: 04afcf75fc11c1c3b4c6fb9f244172c0960e8943bd469bc6424465b376ceaf53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226412"
---
# <a name="detecting-controllers-in-mrtk"></a>MRTK에서 컨트롤러 검색

MRTK는 다양 한 컨트롤러에 대 한 지원을 제공 합니다. HTC Vive Knuckles 및 HTC Vive 지팡이와 같은 많은 컨트롤러는 호환 되는 장치에서 MRTK로 빌드된 응용 프로그램이 시작 되 면 기본적으로 작동 합니다. Oculus 퀘스트 및 HP 반향 G2 컨트롤러에 대 한 트레일러 식 같은 다른 컨트롤러는 MRTK에서 인식 하기 전에 추가 패키지가 필요 합니다.

이 문서에서는 추가 패키지를 설치 해야 하는 일반적인 시나리오에 대해 설명 합니다. 장치에 배포 하는 방법에 대 한 지침은 [**Hololens/WMR**](./wmr-mrtk.md) 또는 [**Oculus 퀘스트**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) 배포 페이지를 참조 하세요. 컨트롤러에 대 한 자세한 내용은 [**기능 페이지**](../features/input/controllers.md)를 참조 하세요. 컨트롤러 관련 문제를 디버그 하려면 [ **컨트롤러 매핑 도구** 를 참조 하세요.](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP 반향 G2 컨트롤러

MRTK를 사용할 때 HP 반향 G2 컨트롤러를 검색 하 고 표시 하려면 다음 단계를 수행 하 여 [**MixedReality**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 패키지를 설치 합니다. 이 패키지를 설치한 후에는 컨트롤러가 HP 반향에 표시 되도록 기본 프로필에 대 한 다른 변경 작업을 수행 하지 않아도 됩니다. 

편집기에서 컨트롤러를 표시 하려면 [**OpenXR 플러그 인**](/windows/mixed-reality/develop/unity/openxr-getting-started)을 사용 하 여를 사용 하 고 있는지 확인 해야 합니다.

## <a name="oculus-controllers"></a>Oculus 컨트롤러 

Oculus 컨트롤러 모델을 시각화 하려면 Oculus 퀘스트 배포 지침을 따릅니다. 컨트롤러를 사용 하는 경우 가상 손을 표시 하려면 XR SDK Oculus 장치 관리자에서 **컨트롤러 대신 아바타 손을 렌더링** 하도록 선택 해야 합니다. 그렇지 않은 경우이 옵션을 선택 취소 합니다.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
