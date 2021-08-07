---
title: Unreal의 직접 추적
description: Unreal 혼합 현실 앱에서 손 추적 입력, 자세, 손 메시 및 라이브 링크 애니메이션을 사용하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, 손 추적, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 기능, 설명서, 가이드, 홀로그램, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 4c3b86c842fc875ebedbdf2527bf962fd8afd4d19cef90d168293cc85b664f70
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187267"
---
# <a name="hand-tracking-in-unreal"></a>Unreal의 직접 추적

손 추적 시스템은 사람의 손끝과 손가락을 입력으로 사용합니다. 모든 손가락, 전체 손끝 및 손 제스처의 위치 및 회전에 대한 데이터를 사용할 수 있습니다. Unreal 4.26부터 손 추적은 Unreal HeadMountedDisplay 플러그 인을 기반으로 하며 모든 XR 플랫폼 및 디바이스에서 공통 API를 사용합니다. 기능은 Windows Mixed Reality 및 OpenXR 시스템 모두에 대해 동일합니다.

## <a name="hand-pose"></a>손 자세

손 자세를 사용하면 사용자의 손과 손가락을 추적하고 입력으로 사용할 수 있으며, 청사진과 C++에서 모두 액세스할 수 있습니다. Unreal API는 Unreal 엔진과 동기화된 틱을 통해 데이터를 좌표계로 보냅니다.

![조인트 오버레이 ](images/hand-tracking-img-02.png)
 ![ 손 스켈레톤이 있는 손 구조 이미지](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>손 라이브 링크 애니메이션

손 자세는 Live Link [플러그 인](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)를 사용하여 애니메이션에 노출됩니다.

Windows Mixed Reality 및 Live Link 플러그 인을 사용하는 경우:
1. **창 > Live Link를** 선택하여 Live Link 편집기 창을 엽니다.
2. **원본을** 선택하고 **Windows Mixed Reality 손 추적 원본을** 사용하도록 설정합니다.

![Live Link 원본](images/unreal/live-link-source.png)

원본을 사용하도록 설정하고 애니메이션 자산을 연 후 장면 **미리 보기** 탭에서 **애니메이션** 섹션을 확장합니다. 추가 옵션도 볼 수 있습니다.

![Live Link 애니메이션](images/unreal/live-link-animation.png)

손 애니메이션 계층 구조는 의 경우와 `EWMRHandKeypoint` 동일합니다. **애니메이션은 WindowsMixedRealityHandTrackingLiveLinkRemapAsset를** 사용하여 대상을 변경할 수 있습니다.

![Live Link 애니메이션 2](images/unreal/live-link-animation2.png)

편집기에서 서브클래스할 수도 있습니다.

![Live Link 다시맵](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>손 메시

### <a name="hand-mesh-as-a-tracked-geometry"></a>추적된 기하 도형인 손 메시

> [!IMPORTANT]
> OpenXR에서 손 메시를 추적된 기하 도형으로 가져오려면 Set **Use Hand Mesh** with **Enabled Tracking Geometry** 를 호출해야 합니다.

해당 모드를 사용하도록 설정하려면 Set **Use Hand Mesh** with **Enabled Tracking Geometry** 를 호출해야 합니다.

![설정된 추적 기하 도형 모드에서 손 메시 함수 사용을 설정하기 위해 연결된 이벤트 시작 재생의 청사진](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> 두 모드를 동시에 사용하도록 설정할 수 없습니다. 하나를 사용하도록 설정하면 다른 하나는 자동으로 비활성화됩니다.

### <a name="accessing-hand-mesh-data"></a>손 메시 데이터 액세스

![손 메시](images/unreal/hand-mesh.png)

손 메시 데이터에 액세스하려면 다음을 수행해야 합니다.
- **ARSessionConfig** 자산을 선택하고 **AR 설정 -> World 매핑** 설정을 확장하고 **추적된 기하 도형에서 메시 데이터 생성을** 선택합니다.

기본 메시 매개 변수는 다음과 같습니다.

1.  폐색에 메시 데이터 사용
2.  메시 데이터에 대한 충돌 생성
3.  Mesh 데이터에 대한 탐색 메시 생성
4.  Wireframe에서 메시 데이터 렌더링 – 생성된 메시를 보여 주는 디버그 매개 변수

이러한 매개 변수 값은 공간 매핑 메시 및 손 메시 기본값으로 사용됩니다. 청사진 또는 모든 메시에 대한 코드에서 언제든지 변경할 수 있습니다.

### <a name="c-api-reference"></a>C++ API 참조
를 사용하여 `EEARObjectClassification` 추적 가능한 모든 개체에서 손 메시 값을 찾습니다.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

다음 대리자는 시스템이 손 메시를 포함하여 추적 가능한 개체를 검색할 때 호출됩니다.

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

대리자 처리기가 아래 함수 시그니처를 따르는지 확인합니다.

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

를 통해 메시 데이터에 액세스할 수  `UARTrackedGeometry::GetUnderlyingMesh` 있습니다.

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>청사진 API 참조

청사진에서 손 메시를 작업하려면 다음을 수행합니다.
1. 청사진 행위자로 **ARTrackableNotify** 구성 요소 추가

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)

2. **세부 정보** 패널로 이동하여 이벤트 섹션을 **확장합니다.**

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)

3. 이벤트 Graph 다음 노드로 추적된 기하 도형 추가/업데이트/제거 시 덮어쓰기:

![ARTrackable 알림에서](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>OpenXR의 손 메시 시각화

손 메시를 시각화하는 권장 방법은 [Microsoft OpenXR 플러그](https://github.com/microsoft/Microsoft-OpenXR-Unreal)인 과 함께 에픽의 XRVisualization 플러그 인을 사용하는 것입니다. 

그런 다음 청사진 편집기에서 **Enabled XRVisualization을** 매개 변수로 사용하여 [Microsoft OpenXR 플러그 인에서](https://github.com/microsoft/Microsoft-OpenXR-Unreal) **손 메시 사용 설정** 함수를 사용해야 합니다.

![활성화된 xrvisualization 모드로 손 메시 함수 사용을 설정하기 위해 연결된 이벤트 시작 재생의 청사진](images/unreal-hand-tracking-img-05.png)

렌더링 프로세스를 관리하려면 XRVisualization에서 **렌더링 모션 컨트롤러를** 사용해야 합니다.

![렌더링 모션 컨트롤러 함수에 연결된 get motion controller data 함수의 청사진](images/unreal-hand-tracking-img-06.png)

결과:

![실제 사람의 손 위에 겹침 디지털 손 이미지](images/unreal-hand-tracking-img-07.png) 

사용자 지정 셰이더를 사용하여 손 메시를 그리는 것과 같이 더 복잡한 것이 필요한 경우 메시를 추적된 기하 도형으로 받아야 합니다. 

## <a name="hand-rays"></a>손 광선

손 자세를 얻는 것은 개체를 잡거나 단추를 누르는 것과 같은 가까운 상호 작용에 적합합니다. 그러나 사용자와 멀리 떨어져 있는 홀로그램으로 작업해야 하는 경우도 있습니다. 이는 C++ 및 Blueprints 모두에서 포인팅 디바이스로 사용할 수 있는 손 광선으로 수행할 수 있습니다. 손에서 원거리 지점까지 광선을 그리고 Unreal 광선 추적의 도움을 받아 도달할 수 없는 홀로그램을 선택할 수 있습니다. 

> [!IMPORTANT]
> 모든 함수 결과는 프레임마다 변경되므로 모두 호출할 수 있습니다. 순수 함수 및 불순한 함수 또는 호출 가능 함수에 대한 자세한 내용은 함수에 대한 청사진 사용자 [GUID를 참조하세요.](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>제스처

HoloLens 2 공간 제스처를 추적합니다. 즉, 이러한 제스처를 입력으로 캡처할 수 있습니다. 제스처 추적은 구독 모델을 기반으로 합니다. "제스처 구성" 함수를 사용하여 추적하려는 제스처를 디바이스에 알려야 합니다.  제스처에 대한 자세한 내용은 [HoloLens 2 기본 사용 문서를](/hololens/hololens2-basic-usage) 찾을 수 있습니다.

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [로컬 Spatial Anchors](unreal-spatial-anchors.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.