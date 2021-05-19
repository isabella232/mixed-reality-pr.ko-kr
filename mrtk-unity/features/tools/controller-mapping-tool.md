---
title: 컨트롤러 매핑 도구
description: MRTK의 컨트롤러 매핑 도구에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144088"
---
# <a name="controller-mapping-tool"></a>컨트롤러 매핑 도구

컨트롤러 매핑 도구는 개발자가 하드웨어 컨트롤러(예: 모션 컨트롤러)에 대한 Unity 입력 축 및 단추 매핑을 신속하게 확인할 수 있는 런타임(디바이스 또는 편집기) 도구입니다.

이 도구는 새 하드웨어 컨트롤러에 대한 지원을 개발할 때 매우 유용합니다. 또한 기존 컨트롤러에 대한 지원 클래스에서 의심되는 컨트롤 매핑 문제를 확인하는 데 도움이 될 수 있습니다.

![컨트롤러 매핑 도구](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>컨트롤러 매핑 도구 사용

컨트롤러 매핑 도구를 시작하려면 **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool로** 이동하여 **ControllerMappingTool** 장면을 엽니다. 장면이 로드되면 프로젝트를 편집기에서 실행하거나, 재생 모드를 사용하거나, 디바이스에서 빌드 및 실행할 수 있습니다.

컨트롤러에 대한 Unity의 매핑을 검사하려면 다음을 수행합니다.

- 컨트롤러 연결
- 각 단추를 누르고 각 축 이동
- 디스플레이의 매핑을 기록해 둡니다.
- 컨트롤러에 대한 입력 시스템 데이터 공급자의 컨트롤 매핑 업데이트

> [!NOTE]
> 컨트롤러 매핑 도구는 Microsoft Mixed Reality 도구 키트 구성 요소를 사용하지 않습니다. Unity와 직접 통신하여 컨트롤 매핑을 확인하고 표시합니다.

### <a name="all-controls-display"></a>모든 컨트롤 표시

큰 디스플레이 패널은 정의된 모든 Unity 입력 축 및 단추의 상태를 보고합니다(예: 축 10, 단추 3). 이 패널은 컨트롤러의 상태에 대한 전체 보기를 제공합니다.

![모든 컨트롤 표시](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>활성 컨트롤 표시

더 작은 좁은 디스플레이 패널에는 Unity 입력 axed 및 활성 상태의 단추가 표시 됩니다 (예: 단추가 누름). 활성 컨트롤 표시를 통해 컨트롤러의 상태에 대 한 요약 보기를 쉽게 읽을 수 있습니다.

![활성 컨트롤 표시](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>참고 항목

- [입력 시스템 데이터 공급자 만들기](../input/create-data-provider.md)
- [InputFeatureUsage 도구](input-feature-usage-tool.md)
