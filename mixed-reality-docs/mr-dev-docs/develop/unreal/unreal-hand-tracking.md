---
title: Unreal의 직접 추적
description: Unreal mixed reality 앱에서 직접 추적 입력, 포즈, 손 모양 및 라이브 링크 애니메이션을 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, 직접 추적, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed reality, 개발, 기능, 설명서, 가이드, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 415a0773586ab232e925fd0f18a3a8e6f8217e88
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695807"
---
# <a name="hand-tracking-in-unreal"></a>Unreal의 직접 추적

손으로 추적 시스템은 사용자의 palms와 손가락을 입력으로 사용 합니다. 모든 손가락의 위치 및 회전에 대 한 데이터, 전체 palm 및 핸드 제스처를 사용할 수 있습니다. Unreal 4.26부터 수동 추적은 Unreal HeadMountedDisplay 플러그 인을 기반으로 하며 모든 XR 플랫폼과 장치에서 공통 API를 사용 합니다. 기능은 Windows Mixed Reality 및 OpenXR 시스템 모두에서 동일 합니다.

## <a name="hand-pose"></a>직접 포즈

직접 사용 하면 사용자의 손으로, 손가락을 입력으로 사용 하 여 청사진과 c + +에서 액세스할 수 있습니다. Unreal API는 틱이 Unreal 엔진과 동기화 된 좌표계로 데이터를 전송 합니다.

![조인트 오버레이 이미지를 사용 하는 손 ](images/hand-tracking-img-02.png)
 모양 기본 이미지 ![](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>손 모양 링크 애니메이션

손 포즈는 [라이브 링크 플러그 인](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)을 사용 하 여 애니메이션에 노출 됩니다.

Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우:
1. **창 > 라이브 링크** 를 선택 하 여 라이브 링크 편집기 창을 엽니다.
2. **원본** 선택 및 **Windows Mixed Reality 추적 원본** 사용

![라이브 링크 소스](images/unreal/live-link-source.png)

소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후에는 **장면 미리 보기** 탭에서 **애니메이션** 섹션을 확장 하 여 추가 옵션을 표시 합니다.

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)

손 모양 애니메이션 계층은에서와 동일 합니다 `EWMRHandKeypoint` . **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다.

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)

편집기에서 서브클래싱 될 수도 있습니다.

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>손 모양 메시

### <a name="hand-mesh-as-a-tracked-geometry"></a>추적 되는 기 하 도형으로 직접 메시

> [!IMPORTANT]
> OpenXR에서 추적 되는 기 하 도형으로 손 모양의 메시를 가져오려면 **활성화 된 추적 기 하 도형** 으로 **설정 된 손 모양 사용** 을 호출 해야 합니다.

해당 모드를 사용 하도록 설정 하려면 설정 된 **추적 기 하 도형을** 사용 하 여 **핸드 메시 사용** 을 호출 해야 합니다.

![설정에 연결 된 이벤트 시작 재생의 청사진 활성화 된 추적 기 하 도형 모드를 사용 하 여 설정 된 손 모양 메시 함수 사용](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> 두 모드를 동시에 사용할 수는 없습니다. 하나를 사용 하도록 설정 하면 다른 하나는 자동으로 사용 하지 않도록 설정 됩니다.

### <a name="accessing-hand-mesh-data"></a>손 모양 메시 데이터 액세스

![손 모양 메시](images/unreal/hand-mesh.png)

직접 메시 데이터에 액세스 하려면 먼저 다음을 수행 해야 합니다.
- **Arsessionconfig** 자산을 선택 하 고 **AR 설정-> 월드 매핑** 설정을 확장 하 고 **추적 된 기 하 도형에서 메시 데이터 생성** 을 선택 합니다.

기본 메시 매개 변수는 다음과 같습니다.

1.  폐색에 대 한 메시 데이터 사용
2.  메시 데이터의 충돌 생성
3.  메시 데이터의 Nav 메시 생성
4.  와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수

이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다. 모든 망상의 청사진 또는 코드에서 언제 든 지 변경할 수 있습니다.

### <a name="c-api-reference"></a>C + + API 참조
`EEARObjectClassification`를 사용 하 여 모든 추적 가능 개체에서 손 모양 값을 찾을 수 있습니다.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

다음 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다.

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

대리자 처리기가 아래 함수 시그니처를 따르는지 확인 합니다.

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

다음을 통해 메시 데이터에 액세스할 수 있습니다  `UARTrackedGeometry::GetUnderlyingMesh` .

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>청사진 API 참조

청사진에서 손 모양 망을 사용 하려면 다음을 수행 합니다.
1. 청사진 행위자에 **ARTrackableNotify** 구성 요소 추가

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)

2. **세부 정보** 패널로 이동 하 여 **이벤트** 섹션을 확장 합니다.

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)

3. 이벤트 그래프의 다음 노드로 추적 된 Geometry 추가/업데이트/제거를 덮어씁니다.

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>OpenXR의 핸드 메시 시각화

손 메시를 시각화 하는 권장 방법은 [Microsoft OpenXR 플러그 인과](https://github.com/microsoft/Microsoft-OpenXR-Unreal)함께 대규모의 XRVisualization 플러그 인을 사용 하는 것입니다. 

그런 다음 청사진 편집기에서 사용 하도록 설정 된 **XRVisualization** 를 매개 변수로 사용 하 여 [Microsoft OpenXR 플러그 인](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 에서 **Set use 손 메시** 함수를 사용 해야 합니다.

![설정에 연결 된 이벤트 시작 재생의 청사진 사용 하도록 설정 된 손 모양 메시 함수를 사용 하는 xrvisualization 모드](images/unreal-hand-tracking-img-05.png)

렌더링 프로세스를 관리 하려면 XRVisualization에서 **렌더링 동작 컨트롤러** 를 사용 해야 합니다.

![렌더링 동작 컨트롤러 함수에 연결 된 get 모션 컨트롤러 데이터 함수의 청사진](images/unreal-hand-tracking-img-06.png)

결과:

![실제 인간 오버레이할의 디지털 핸드 이미지 이미지](images/unreal-hand-tracking-img-07.png) 

사용자 지정 셰이더를 사용 하 여 손을 메시를 그리는 등 더 복잡 한 작업이 필요한 경우 메시를 추적 된 기 하 도형으로 가져와야 합니다. 

## <a name="hand-rays"></a>손 광선

개체를 가져오거나 단추를 누르는 것과 같은 닫기 작업에 대해 작업을 수행 하는 것이 가능 합니다. 그러나 사용자에 게 멀리 떨어져 있는 holograms 작업 해야 하는 경우도 있습니다. 이는 c + + 및 청사진 모두를 가리키는 장치로 사용할 수 있는 직접 광선을 사용 하 여 수행할 수 있습니다. 손 모양에서 먼 점으로 광선을 그릴 수 있으며, Unreal 레이 추적에서 몇 가지 도움을 받을 수 있습니다. 그렇지 않은 경우에는 연결 되지 않은 홀로그램을 선택 합니다. 

> [!IMPORTANT]
> 모든 함수 결과는 프레임 마다 변경 되므로 모두 호출할 수 있습니다. Pure 및 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [함수](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)에 대 한 청사진 사용자 guid를 참조 하세요.

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>제스처

HoloLens 2는 공간 제스처를 추적 합니다. 즉, 이러한 제스처를 입력으로 캡처할 수 있습니다. 제스처 추적은 구독 모델을 기반으로 합니다. "제스처 구성" 함수를 사용 하 여 추적 하려는 제스처를 장치에 알려야 합니다.  제스처에 대 한 자세한 내용은 [HoloLens 2 기본 사용](/hololens/hololens2-basic-usage) 문서에 나와 있습니다.

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [로컬 Spatial Anchors](unreal-spatial-anchors.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.