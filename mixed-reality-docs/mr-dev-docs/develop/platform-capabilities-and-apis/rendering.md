---
title: 렌더링
description: 홀로그램 렌더링을 통해 앱이 사용자 주변의 정확한 위치에 홀로그램을 그리는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 렌더링, 홀로그램
ms.openlocfilehash: d01a5911ad8b479197bd38e8ed7825feef1f69dc51d2c2dc2f8e500e93880955
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193669"
---
# <a name="rendering"></a>렌더링

홀로그램 렌더링을 사용하면 애플리케이션이 실제 세계 또는 사용자가 만든 가상 영역에 정확하게 배치되었는지 여부에 관계없이 사용자 주변의 정확한 위치에 홀로그램을 그릴 수 있습니다. [홀로그램스](../../discover/hologram.md) 소리와 광원으로 이루어진 개체입니다. 렌더링을 사용하면 애플리케이션에서 조명을 추가할 수 있습니다.

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>렌더링</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>홀로그램 렌더링

홀로그램 렌더링의 핵심은 사용 중인 디바이스의 종류를 아는 것입니다. HoloLens 등과 [같이](/hololens/hololens1-hardware) **디스플레이가 있는** 디바이스는 전 세계에 조명을 추가합니다. 검은색 픽셀은 완전히 투명하지만 더 밝은 픽셀은 점점 불투명해집니다. 디스플레이의 광원은 실제 세계의 광원에 추가되므로 흰색 픽셀은 반투명합니다.

스테레오 범위 렌더링은 홀로그램에 대한 하나의 깊이 신호를 [제공하지만, 접지 효과를](../../design/interaction-fundamentals.md) 추가하면 홀로그램이 가까이 있는 표면을 보다 쉽게 볼 수 있습니다. 한 가지 접지 기술은 주변 표면의 홀로그램 주위에 후광을 추가한 다음, 이 광선에 그림자를 렌더링하는 것입니다. 이러한 방식으로 그림자는 환경에서 조명을 빼는 것처럼 보입니다. [공간 소리는](../../design/spatial-sound.md) 사용자가 홀로그램의 거리와 상대 위치를 추론할 수 있는 또 다른 중요한 깊이 큐입니다.

불투명 **디스플레이가** 있는 디바이스는 [Windows Mixed Reality 몰입형 헤드셋과](../../discover/immersive-headset-hardware-details.md)같이 전 세계를 차단합니다. 검은색 픽셀은 검은색이며 다른 색은 사용자에게 해당 색으로 표시됩니다. 애플리케이션은 사용자에게 표시되는 모든 것을 렌더링해야 합니다. 따라서 사용자가 편안한 환경을 갖도록 일정한 새로 고침 빈도를 유지하는 것이 훨씬 더 중요합니다.

## <a name="predicted-rendering-parameters"></a>예측된 렌더링 매개 변수

혼합 현실 헤드셋(HoloLens 및 몰입형 헤드셋 모두)은 주변을 기준으로 사용자의 머리 위치와 방향을 지속적으로 추적합니다. 애플리케이션이 다음 프레임 준비를 시작할 때 시스템은 프레임이 디스플레이에 표시되는 정확한 시점에 사용자의 헤드가 미래의 위치를 예측합니다. 이 예측을 기반으로 시스템은 해당 프레임에 사용할 뷰 및 프로젝션 변환을 계산합니다. 애플리케이션은 **올바른 결과를 생성하기 위해 이러한 변환을 사용해야 합니다.** 시스템 제공 변환을 사용하지 않으면 결과 이미지가 실제 세계와 일치하지 않아 사용자 불편이 발생합니다.

> [!NOTE]
> 새 프레임이 디스플레이에 도달하는 시기를 정확하게 예측하기 위해 시스템은 애플리케이션 렌더링 파이프라인의 효과적인 엔드투엔드 대기 시간을 지속적으로 측정하고 있습니다. 시스템이 렌더링 파이프라인의 길이에 맞게 조정되는 동안 해당 파이프라인을 최대한 짧게 유지하여 홀로그램 안정성을 향상시킬 수 있습니다.

고급 기술을 사용하여 시스템 예측을 보강하는 애플리케이션은 시스템 뷰 및 프로젝션 변환을 재정의할 수 있습니다. 이러한 애플리케이션은 의미 있는 결과를 생성하기 위해 사용자 지정 변환의 기준으로 시스템 제공 변환을 계속 사용해야 합니다.

## <a name="other-rendering-parameters"></a>기타 렌더링 매개 변수

프레임을 렌더링할 때 시스템은 애플리케이션이 그려야 하는 백 버퍼 뷰포트를 지정합니다. 이 뷰포트는 프레임 버퍼의 전체 크기보다 작은 경우가 많습니다. 뷰포트 크기에 관계없이 프레임이 애플리케이션에 의해 렌더링되면 시스템은 이미지의 크기를 조정하여 전체 디스플레이를 채웁니다.

필요한 새로 고침 빈도로 렌더링할 수 없는 애플리케이션의 경우 픽셀 별칭을 증가시키는 비용으로 메모리 부족 및 렌더링 비용을 줄이기 위해 [시스템 렌더링 매개 변수를 구성할 수 있습니다.](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 일부 앱의 경우 메모리 대역폭 및 픽셀 처리량을 개선하는 데 도움이 될 수 있는 백 버퍼 형식도 변경할 수 있습니다.

앱이 렌더링하도록 요청되는 렌더링 frustum, resolution 및 framerate도 프레임에서 프레임으로 변경될 수 있으며 왼쪽과 오른쪽 눈에서 다를 수 있습니다. 예를 들어 [MRC(혼합 현실 캡처)가](/hololens/holographic-photos-and-videos) 활성화되어 있고 [사진/비디오 카메라 보기 구성이](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 옵트인되지 않은 경우 한 눈에 더 큰 FOV 또는 해상도로 렌더링될 수 있습니다.

지정된 프레임의 경우 앱은 시스템에서 제공하는 뷰 변환, 프로젝션 변환 및 뷰포트 해상도를 사용하여 *렌더링해야 합니다.* 또한 애플리케이션에서는 렌더링 또는 뷰 매개 변수가 프레임에서 프레임으로 고정된 상태로 유지된다고 가정해서는 안 됩니다. Unity와 같은 엔진은 사용자의 물리적 이동과 시스템 상태를 항상 준수할 수 있도록 자체 카메라 개체에서 이러한 모든 변환을 처리합니다. 애플리케이션에서 전 세계에서 사용자의 가상 이동이 허용되는 경우(예: 게임 패드에서 엄지스틱 사용) 카메라 위에 부모 조작 개체를 추가하여 주변을 이동할 수 있습니다. 이렇게 하면 카메라는 사용자의 가상 동작과 실제 동작을 모두 반영합니다. 애플리케이션이 시스템에서 제공하는 뷰 변환, 프로젝션 변환 또는 뷰포트 차원을 수정하는 경우 적절한 [재정의 API](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)를 호출하여 시스템에 알려야 합니다.

홀로그램 렌더링의 안정성을 향상하려면 앱이 렌더링에 사용된 깊이 버퍼를 각 프레임에 Windows 위해 를 제공해야 합니다. 앱이 깊이 버퍼를 제공하는 경우 카메라에서 미터로 표현된 깊이와 일관된 깊이 값이 있어야 합니다. 이렇게 하면 사용자의 헤드가 예측된 위치에서 약간 오프셋되는 경우 시스템에서 픽셀당 깊이 데이터를 사용하여 콘텐츠를 더 잘 안정화할 수 있습니다. 깊이 버퍼를 제공할 수 없는 경우 포커스 지점과 정상을 제공하여 대부분의 콘텐츠를 통과하는 평면을 정의할 수 있습니다. 깊이 버퍼와 포커스 평면이 둘 다 제공되면 시스템에서 둘 다 사용할 수 있습니다. 특히 애플리케이션이 동작 중인 홀로그램을 표시할 때 속도 벡터를 포함하는 깊이 버퍼와 포커스 지점을 모두 제공하는 것이 유용합니다.

이 항목에 대한 자세한 내용은 [DirectX의 렌더링](../native/rendering-in-directx.md) 문서를 참조하세요.

## <a name="holographic-cameras"></a>홀로그램 카메라

Windows Mixed Reality **홀로그램 카메라** 의 개념을 소개합니다. 홀로그램 카메라는 3D 그래픽 텍스트에 있는 기존 카메라와 비슷합니다. 내장(위치 및 방향) 및 내장 카메라 속성을 모두 정의합니다. (예를 들어 보기의 필드는 가상 3D 장면을 보는 데 사용됩니다.) 기존 3D 카메라와 달리 애플리케이션은 카메라의 위치, 방향 및 내장 속성을 제어하지 않습니다. 대신 홀로그램 카메라의 위치와 방향은 사용자의 이동에 의해 암시적으로 제어됩니다. 사용자의 이동은 보기 변환을 통해 프레임 단위로 애플리케이션에 릴레이됩니다. 마찬가지로 카메라의 내장 속성은 프로젝션 변환을 통해 디바이스의 보정된 광학 및 릴레이된 프레임별로 정의됩니다.

일반적으로 애플리케이션은 단일 스테레오 카메라를 렌더링합니다. 강력한 렌더링 루프는 여러 카메라를 지원하며 모노 및 스테레오 카메라를 모두 지원합니다. 예를 들어 시스템은 사용자가 헤드셋 모양에 따라 MRC(혼합 [현실 캡처)와](/hololens/holographic-photos-and-videos) 같은 기능을 활성화할 때 대체 관점에서 렌더링하도록 애플리케이션에 요청할 수 있습니다. 여러 카메라를 지원할 수 있는 애플리케이션은 지원할 수 있는 카메라 [종류에](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) [옵트인하여](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 카메라를 얻습니다.

## <a name="volume-rendering"></a>볼륨 렌더링

의료 MRI 또는 엔지니어링 볼륨을 3D로 [렌더링할](volume-rendering.md) 때 볼륨 렌더링 기술이 자주 사용됩니다. 이러한 기술은 혼합 현실에서 흥미로울 수 있습니다. 여기서 사용자는 단순히 머리만 이동하여 키 각도에서 이러한 볼륨을 자연스럽게 볼 수 있습니다.

## <a name="supported-resolutions-on-hololens-first-gen"></a>HoloLens 지원되는 해결 방법(1세대)

* 최대 뷰포트 크기는 [HolographicDisplay](/uwp/api/windows.graphics.holographic.holographicdisplay)의 속성입니다. HoloLens 최대 뷰포트 크기(기본적으로 720p(1268x720)로 설정됩니다.
* HolographicCamera에서 ViewportScaleFactor를 설정하여 뷰포트 크기를 변경할 수 있습니다. 이 배율 범위는 0에서 1까지입니다.
* HoloLens 지원되는 가장 낮은 뷰포트 크기(1세대)는 720p의 50%로, 360p(634x360)입니다. ViewportScaleFactor 0.5입니다.
* 540p보다 낮은 것은 시각적 성능 저하로 인해 권장되지 않지만 픽셀 채우기 속도의 병목 현상을 식별하는 데 사용할 수 있습니다.

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 지원되는 해결 방법

* 현재 및 최대 지원 렌더링 대상 크기는 [보기 구성](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)의 속성입니다. HoloLens 2 최대 렌더링 대상 크기(기본적으로 1440x936)로 설정됩니다.
* 앱은 RequestRenderTargetSize 메서드를 호출하여 새 렌더링 대상 크기를 요청하여 렌더링 대상 버퍼의 크기를 변경할 수 있습니다. 요청된 렌더링 대상 크기를 충족하거나 초과하는 새 렌더링 대상 크기가 선택됩니다. 이 API는 렌더링 대상 버퍼의 크기를 변경하므로 GPU에서 메모리를 다시 할당해야 합니다. 이 경우의 의미는 다음과 같습니다. 렌더링 대상 크기를 축소하여 GPU의 메모리 압력을 줄일 수 있으며, 이 메서드는 높은 빈도로 호출해서는 안 됩니다.
* 앱은 HoloLens 1과 동일한 방식으로 뷰포트 크기를 변경할 수 있습니다. GPU에 추가된 메모리 재할당이 없으므로 높은 빈도로 변경할 수 있지만 GPU의 메모리 압력을 줄이는 데 사용할 수는 없습니다.
* HoloLens 2 지원되는 가장 낮은 뷰포트 크기는 634x412이며, 기본 렌더링 대상 크기를 사용하는 경우 ViewportScaleFactor는 약 0.44입니다.
* 지원되는 가장 낮은 뷰포트 크기보다 작은 렌더링 대상 크기가 제공되면 뷰포트 배율 비율은 무시됩니다.
* 540p보다 낮은 것은 시각적 성능 저하로 인해 권장되지 않지만 픽셀 채우기 속도의 병목 현상을 식별하는 데 사용할 수 있습니다.



## <a name="see-also"></a>추가 정보
* [홀로그램 안정성](hologram-stability.md)
* [DirectX의 렌더링](../native/rendering-in-directx.md)