---
title: 공간 메시 시각화
description: MRTK의 공간 메시 시각화를 사용 하 여 디자인 지침 및 물리적 환경 이해에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 혼합 현실, HoloLens, UI 컨트롤, 상호 작용, ui, ux, UX 디자인, 공간 UI, 공간 상호 작용, 3D UI, 3D UX, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5e8ffbb90b1143cd4e11bf45a889c11c233232df
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759809"
---
# <a name="spatial-mesh"></a>공간 메시

![공간 메시](images/MRTK_PulseShader_SpatialMesh.gif)

사용자는 장치에서 공간 메시 시각화를 통해 물리적 환경을 인식 하 고 이해 하는 방법을 알아봅니다. 적절 한 공간 메시 시각화는 공간 컨텍스트를 제공 하는 동시에 매력적인 및 마법 환경을 만들 수 있습니다.  

## <a name="design-guideline"></a>디자인 지침

사용자가 콘텐츠를 집중적으로 사용 하 고 상호 작용할 수 있도록 하는 것이 중요 합니다. 배경에서 공간 메시의 연속 시각화는 혼란을 수 있습니다. 초기 실행에서 한 번만 또는 사용자가 공간을 대상으로 하 여 환경 메시를 표시 하려는 경우에만 환경을 시각화 하는 것이 좋습니다. 혼합 현실 포털에서이 동작을 관찰할 수 있습니다.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 공간 메시 시각화

MRTK는 공간 메시 시각화에 대 한 여러 자료를 제공 합니다.

- **MRTK_Wireframe, MRTK_Wireframe**: 기본 정적 공간 메시 재질: 애니메이션 없이 메시 윤곽선을 표시 합니다. 이 자료는 전체 공간 메시 기 하 도형을 표시 하기 때문에 디버깅 목적으로 유용 합니다. 그러나 프로덕션에는 권장 되지 않습니다.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.** 대만:이 자료는 공간 메시에 애니메이션 된 펄스 효과를 제공 합니다. 이 자료를 사용 하 여 특정 순간 이나 사용자의 공중 탭 입력에서 환경을 시각화할 수 있습니다. 예제는 **PulseShaderExamples** 을 참조 하세요.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 자세한 내용은 [Mrtk-공간 인식](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) 및 [Mrtk-펄스 셰이더](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md)를 참조 하세요.

<br>

---

## <a name="see-also"></a>참고 항목

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
