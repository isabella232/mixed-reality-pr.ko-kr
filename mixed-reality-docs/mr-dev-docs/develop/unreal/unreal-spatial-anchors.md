---
title: Unreal의 로컬 Spatial Anchors
description: Unreal 혼합 현실 애플리케이션에서 공간 앵커를 만들고, 저장하고, 관리하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 기능, 설명서, 가이드, 홀로그램, spatial anchors, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98009983"
---
# <a name="local-spatial-anchors-in-unreal"></a>Unreal의 로컬 Spatial Anchors

Spatial Anchors는 애플리케이션 세션 간의 실제 공간에 홀로그램을 **ARPin** 으로 저장합니다. HoloLens의 앵커 저장소에 저장되면 ARPin은 향후 세션에 로드될 수 있으며 인터넷 연결이 없을 때 이상적인 대체 옵션입니다.

> [!NOTE]
> UE 4.25의 앵커 함수는 4.26에서 사용되지 않으며 새 함수로 바꿔야 합니다. 

> [!IMPORTANT]
> 로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다. Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](unreal-azure-spatial-anchors.md) 통합 과정을 안내하는 문서를 참조하세요. 로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.

## <a name="checking-the-anchor-store"></a>앵커 저장소 확인

앵커를 저장하거나 로드하기 전에 먼저 앵커 저장소가 준비되었는지 확인해야 합니다.  앵커 저장소가 준비되기 전에는 HoloLens 앵커 함수의 호출에 성공하지 못합니다.  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>앵커 저장

세계에 고정해야 하는 구성 요소가 애플리케이션에 있으면 다음 순서에 따라 앵커 저장소에 저장할 수 있습니다. 

[!INCLUDE[](includes/tabs-sa-2.md)]

상세 구분:
1. 알려진 위치에 행위자를 생성합니다.
2. 행위자의 클래스를 기준으로 해당 위치와 이름을 사용하여 **ARPin** 을 만듭니다. 
3. **ARPin** 에 행위자를 추가하고 HoloLens 앵커 저장소에 핀을 저장합니다.  
    * 선택한 앵커 이름은 고유해야 하며 이 예제에서는 현재 타임스탬프를 추가합니다. 

4. 앵커가 앵커 저장소에 성공적으로 저장된 경우, **시스템 > 맵 관리자 > 디바이스에 저장된 앵커 파일** 에서 해당 항목을 HoloLens 디바이스 포털에서 볼 수 있습니다. 

## <a name="loading-anchors"></a>앵커 로드

애플리케이션이 시작되면 다음 청사진을 사용하여 구성 요소를 앵커 위치에 복원할 수 있습니다.

[!INCLUDE[](includes/tabs-sa-3.md)]

상세 구분:
1. 앵커 저장소의 모든 앵커에 대해 반복합니다. 
2. ID에서 행위자를 생성합니다.
3. 해당 행위자를 앵커 저장소에서 **ARPin** 에 고정합니다.  

    * 앵커는 홀로그램이 저장된 위치를 기준으로 홀로그램 위치를 다시 설정하는 것을 담당하므로 행위자를 ID에 생성하는 것이 중요합니다. 여기에 추가된 변환은 앵커에 오프셋을 추가합니다. 

앵커 ID는 앵커의 저장된 이름에 따라 다른 행위자가 생성될 수 있도록 쿼리되기도 합니다. 

## <a name="removing-anchors"></a>앵커 제거 

앵커 작업을 마치면 **WMRAnchor 저장소에서 ARPin 제거** 및 **WMRAnchor 저장소 모든 ARPin 제거** 구성 요소를 통해 개별 앵커 또는 전체 앵커 저장소를 지울 수 있습니다.

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> Spatial Anchors가 아직 베타 버전이므로 업데이트된 정보 및 기능을 다시 확인해야 합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [좌표계](../../design/coordinate-systems.md)
