---
title: 홀로그램 안정화
description: 다른 환경 및 프레임 속도 조건에서 holograms의 성능
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 환경 추적, TMP,
ms.openlocfilehash: 338ae2719764b84b7c58c1422e08fe02176eccf0
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333435"
---
# <a name="hologram-stabilization"></a>홀로그램 안정화

## <a name="performance"></a>성능

기본 혼합 현실 플랫폼과 장치에서 최상의 결과를 얻으려면 프레임 속도를 수행 하는 것이 중요 합니다. 대상 프레임 속도 (예: 60 FPS 또는 90 FPS)는 플랫폼과 장치에 따라 다릅니다. 그러나 프레임 속도를 충족 하는 혼합 현실 응용 프로그램은 안정적인 holograms 뿐만 아니라 효율적인 헤드 추적, 수동 추적 등을 포함 합니다.  

## <a name="environment-tracking"></a>환경 추적

안정적인 holographic 렌더링은 플랫폼 & 장치에의 한 헤드 포즈 추적에 크게 의존 합니다. Unity는 카메라의 모든 프레임을 예상 하 고 기본 플랫폼에서 제공 하는 장면으로 렌더링 합니다. 이 추적이 실제 헤드 이동을 올바르게 따르지 않으면 holograms가 시각적으로 부정확 하 게 표시 됩니다. 이는 사용자가 가상 holograms를 실제 세계와 연결할 수 있는 HoloLens와 같은 AR 장치에서 특히 명확 하 고 중요 합니다. 안정적인 헤드 추적에는 성능이 중요 하지만 [다른 중요 한 기능도](/windows/mixed-reality/environment-considerations-for-hololens)있을 수 있습니다. 사용자 환경에 영향을 주는 환경 요소의 형식은 대상 플랫폼 세부 사항에 따라 달라 집니다.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 플랫폼은 플랫폼에서 holograms를 안정화 하기 위한 [참조 자료](/windows/mixed-reality/hologram-stability) 를 제공 합니다. 개발자가 사용자를 위한 홀로그램 시각적 환경을 개선 하는 데 활용할 수 있는 몇 가지 주요 도구가 있습니다.

### <a name="depth-buffer-sharing"></a>깊이 버퍼 공유

Unity 개발자에 게는 응용 프로그램의 깊이 버퍼를 플랫폼과 공유할 수 있는 옵션이 있습니다. 이는 holograms가 현재 프레임에 대 한 정보를 제공 하 고, 플랫폼은 Late-Stage Reprojection 이라는 하드웨어 기반 프로세스를 통해 안정화 holograms을 활용할 수 있습니다.

#### <a name="late-stage-reprojection"></a>후반 단계 다시 프로젝션

프레임 렌더링이 끝나면 Windows Mixed Reality 플랫폼은 애플리케이션에서 생성된 색 & 깊이 렌더링 대상을 가져와서 마지막 머리 자세 예측 이후 약간의 머리 이동을 고려하여 최종 화면 출력을 변환합니다. 애플리케이션의 게임 루프를 실행하는 데 시간이 걸립니다. 예를 들어 60 FPS에서 애플리케이션이 프레임을 렌더링하는 데 최대 16.667ms가 걸리는 것을 의미합니다. 이는 최소한의 시간처럼 보일 수 있지만, 사용자의 머리 위치와 방향이 변경되어 렌더링에서 카메라에 대한 새로운 프로젝션 행렬이 생성됩니다. 마지막 단계 다시 프로젝션은 이 새로운 큐브 뷰를 고려하도록 최종 이미지의 픽셀을 변환합니다.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>픽셀당 및 안정화 평면 LSR

Windows Mixed Reality 디바이스에서 실행되는 디바이스 엔드포인트 및 OS 버전에 따라 Late-Stage 다시 프로젝션 알고리즘은 픽셀당 또는 [안정화 평면을](/windows/mixed-reality/hologram-stability#stabilization-plane)통해 수행됩니다.

##### <a name="per-pixel-depth-based"></a>픽셀당 깊이 기반

픽셀별 깊이 기반 다시 프로젝션에는 깊이 버퍼를 활용하여 픽셀당 이미지 출력을 수정하여 다양한 거리에 있는 홀로그램을 안정화하는 작업이 포함됩니다. 예를 들어 1m 떨어진 구는 10m 떨어진 핵심 요소 앞에 있을 수 있습니다. 구를 나타내는 픽셀은 사용자가 헤드를 약간 기울인 경우 핵심을 나타내는 멀리 떨어진 픽셀과 다른 변환을 갖습니다. 픽셀당 다시 프로젝션은 보다 정확한 다시 프로젝션을 위해 모든 픽셀에서 이 거리 차이를 고려합니다.

##### <a name="stabilization-plane"></a>안정화 평면

플랫폼과 공유할 정확한 깊이 버퍼를 만들 수 없는 경우 또 다른 형태의 LSR은 안정화 평면을 활용합니다. 장면의 모든 홀로그램은 일부 안정화를 받지만 원하는 평면에 있는 홀로그램은 최대 하드웨어 안정화를 받습니다. 평면의 점과 표준은 Unity에서 제공하는 *HolographicSettings.SetFocusPointForFrame* [API를](/windows/mixed-reality/focus-point-in-unity)통해 플랫폼에 제공할 수 있습니다.

#### <a name="depth-buffer-format"></a>깊이 버퍼 형식

개발을 위해 HoloLens를 대상으로 지정 하는 경우 24 비트와 비교 하 여 16 비트 깊이 버퍼 형식을 활용 하는 것이 좋습니다. 이 경우 깊이 값의 정밀도가 크게 성능이 저하 될 수 있습니다. 더 낮은 정밀도를 보정 하 고 [z를 사용](https://en.wikipedia.org/wiki/Z-fighting)하지 않도록 하려면 Unity에 설정 된 1000m 기본값에서 [먼 클립 평면](https://docs.unity3d.com/Manual/class-Camera.html) 을 줄이는 것이 좋습니다.

> [!NOTE]
> *16 비트 깊이 형식을* 사용 하는 경우 Unity에서이 설정에 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 스텐실 버퍼 필요 효과가 작동 하지 않습니다. 이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 해당 하는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html)생성 됩니다.

#### <a name="depth-buffer-sharing-in-unity"></a>Unity의 깊이 버퍼 공유

깊이 기반 LSR를 활용 하기 위해 개발자가 수행 해야 하는 두 가지 중요 한 단계가 있습니다.

1.   >  **프로젝트 설정** 편집에서  >  **플레이어**  >  **XR 설정**  >  **가상 현실 sdk** > **깊이 버퍼 공유** 사용
    1. HoloLens를 대상으로 하는 경우 **16 비트 깊이 형식만** 선택 하는 것이 좋습니다.
1. 화면에서 색을 렌더링할 때 깊이도 렌더링 합니다.

Unity의 [불투명 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) 일반적으로 깊이에 자동으로 기록 됩니다. 그러나 투명 & 텍스트 개체는 일반적으로 기본적으로 깊이에 기록 되지 않습니다. MRTK 표준 셰이더 또는 텍스트 메시 Pro를 활용 하는 경우이를 쉽게 해결할 수 있습니다.

> [!NOTE]
> 장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 신속 하 게 확인 하기 위해 MRTK 구성 프로필의 *편집기 설정* 에서 [ *렌더링 수준 버퍼* 유틸리티](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 사용할 수 있습니다.

##### <a name="transparent-mrtk-standard-shader"></a>투명 MRTK 표준 셰이더

[Mrtk 표준 셰이더](../features/rendering/MRTK-standard-shader.md)를 사용 하는 투명 재질의 경우 *검사기* 창에서 볼 자료를 선택 합니다. 그런 다음 [ *지금 수정* ] 단추를 클릭 하 여 자료를 자세히 (즉, Z-쓰기).

이전

![MRTK 표준 셰이더 수정 전 깊이 버퍼](../features/images/performance/DepthBufferFixNow_Before.PNG)

After

![깊이 버퍼 고정 MRTK 표준 셰이더](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Text Mesh Pro

Text Mesh Pro 개체의 경우 TMP GameObject를 선택하여 검사기에서 확인합니다. 재질 구성 요소 아래에서 할당된 재질의 셰이더를 전환하여 MRTK TextMeshPro 셰이더를 사용합니다.

![Text Mesh Pro Depth 버퍼 수정](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>사용자 지정 셰이더

사용자 지정 셰이더를 작성하는 경우 *Pass* 블록 정의의 맨 위에 [ZWrite 플래그를](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 추가하여 깊이 버퍼에 쓰도록 셰이더를 구성합니다.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>불투명 지원

위의 메서드가 지정된 시나리오에서 작동하지 않는 경우(즉, Unity UI를 사용하여 깊이 버퍼에 다른 개체를 쓸 수 있습니다. 일반적인 예는 장면의 부동 패널에서 Unity UI 텍스트를 사용하는 것입니다. 패널을 불투명하게 만들거나 최소한 깊이에 쓰면 패널의 텍스트 & z-값이 서로 너무 가깝기 때문에 플랫폼에 의해 안정화됩니다.

### <a name="worldanchors-hololens"></a>WorldAnchors(HoloLens)

시각적 안정성을 보장하기 위해 올바른 구성을 충족하는지 확인하는 것 외에 홀로그램이 올바른 물리적 위치에서 안정적으로 유지되도록 하는 것이 중요합니다. 물리적 공간의 중요한 위치에 대해 플랫폼에 알리기 위해 개발자는 한 곳에 유지해야 하는 GameObjects에서 [WorldAnchors를](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 활용할 수 있습니다. [WorldAnchor는](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 해당 개체의 변환을 절대 제어하는 GameObject에 추가된 구성 요소입니다.

HoloLens와 같은 디바이스는 지속적으로 환경을 검색하고 학습합니다. 따라서 HoloLens는 공간에서 이동 & 위치를 추적하므로 예상값이 업데이트되고 [Unity 좌표계가 조정됩니다.](/windows/mixed-reality/coordinate-systems-in-unity) 예를 들어, GameObject가 시작 시 카메라에서 1m 정도 배치되는 경우 HoloLens가 환경을 추적할 때 GameObject가 있는 물리적 지점이 실제로 1.1m 떨어져 있음을 알 수 있습니다. 이로 인해 홀로그램이 드리프트될 수 있습니다. GameObject에 WorldAnchor를 적용하면 앵커가 개체의 변환을 제어하여 개체가 올바른 물리적 위치(즉, 런타임에 1m 대신 1.1 m 자리까지 업데이트 합니다. 응용 프로그램 세션 간에 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 을 유지 하기 위해 개발자는 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 를 사용 하 여 [WorldAnchors을 저장 하 고 로드할](/windows/mixed-reality/persistence-in-unity)수 있습니다.

> [!NOTE]
> GameObject에 WorldAnchor 구성 요소를 추가한 후에는 해당 GameObject의 변환을 수정할 수 없습니다 (즉, transform. position = x). 개발자는 변환을 편집 하려면 WorldAnchor를 제거 해야 합니다.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

수동으로 앵커를 사용 하는 방법에 대 한 대안을 원하는 경우 Microsoft 세계 잠금 도구를 확인 하세요. 

> [!div class="nextstepaction"]
> [MR 기능 도구를 사용 하 여 설치](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>참고 항목

- [성능](../performance/perf-getting-started.md)
- [HoloLens 환경 고려 사항](/windows/mixed-reality/environment-considerations-for-hololens)
- [홀로그램 안정성 Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Unity의 포커스 포인트](/windows/mixed-reality/focus-point-in-unity)
- [Unity의 좌표계](/windows/mixed-reality/coordinate-systems-in-unity)
- [Unity의 지속성](/windows/mixed-reality/persistence-in-unity)
- [혼합 현실 성능 이해](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Unity의 권장 성능](/windows/mixed-reality/performance-recommendations-for-unity)