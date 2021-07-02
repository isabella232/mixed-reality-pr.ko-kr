---
title: 홀로그램 안정화
description: 다양한 환경 및 프레임 속도 조건에서 홀로그램의 성능.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 환경 추적, TMP,
ms.openlocfilehash: 7aab167f2d850a4bca88a2cc40aae4f3cc50fb4b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176485"
---
# <a name="hologram-stabilization"></a>홀로그램 안정화

## <a name="performance"></a>성능

기본 혼합 현실 플랫폼 및 디바이스가 최상의 결과를 생성하려면 프레임 속도를 달성하는 것이 중요합니다. 대상 프레임 속도(예: 60 FPS 또는 90 FPS)는 플랫폼 및 디바이스에 따라 달라집니다. 그러나 프레임 속도 충족 혼합 현실 애플리케이션에는 안정적인 홀로그램뿐만 아니라 효율적인 헤드 추적, 손 추적 등이 있습니다.  

## <a name="environment-tracking"></a>환경 추적

안정적인 홀로그램 렌더링은 플랫폼 & 디바이스의 머리 자세 추적에 크게 의존합니다. Unity는 기본 플랫폼에서 예측하고 제공하는 카메라 자세의 모든 프레임마다 장면을 렌더링합니다. 이 추적이 실제 머리 이동을 올바르게 따르지 않으면 홀로그램이 시각적으로 부정확하게 표시됩니다. 이는 사용자가 가상 홀로그램을 실제 세계와 관련할 수 있는 HoloLens 같은 AR 디바이스에 특히 분명하고 중요합니다. 성능은 신뢰할 수 있는 헤드 추적에 중요하지만 [다른 중요한 기능도](/windows/mixed-reality/environment-considerations-for-hololens)있을 수 있습니다. 사용자 환경에 영향을 미치는 환경 요소의 유형은 대상 플랫폼 세부 사항에 따라 달라집니다.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 플랫폼은 플랫폼에서 홀로그램을 안정화하기 위한 몇 가지 [참조 자료를](/windows/mixed-reality/hologram-stability) 제공합니다. 개발자가 사용자의 홀로그램 시각적 환경을 개선하는 데 활용할 수 있는 몇 가지 주요 도구가 있습니다.

### <a name="depth-buffer-sharing"></a>깊이 버퍼 공유

Unity 개발자는 플랫폼과 애플리케이션의 깊이 버퍼를 공유할 수 있습니다. 이를 통해 현재 프레임에 홀로그램이 존재하는 경우 플랫폼이 Late-Stage Reprojection이라는 하드웨어 지원 프로세스를 통해 홀로그램을 안정화하는 데 활용할 수 있는 정보를 제공합니다.

#### <a name="late-stage-reprojection"></a>대기 단계 다시 프로젝션

프레임 렌더링이 끝나면 Windows Mixed Reality 플랫폼은 애플리케이션에서 생성된 색 & 깊이 렌더링 대상을 가져와서 마지막 머리 자세 예측 이후 약간의 머리 이동을 고려하여 최종 화면 출력을 변환합니다. 애플리케이션의 게임 루프를 실행하는 데 시간이 걸립니다. 예를 들어 60 FPS에서 애플리케이션이 프레임을 렌더링하는 데 최대 16.667ms가 걸리는 것을 의미합니다. 이는 최소한의 시간처럼 보일 수 있지만, 사용자의 머리 위치와 방향이 변경되어 렌더링 시 카메라에 대한 새로운 프로젝션 행렬이 생성됩니다. 마지막 단계 다시 프로젝션은 이 새로운 큐브 뷰를 고려하도록 최종 이미지의 픽셀을 변환합니다.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>픽셀당 및 안정화 평면 LSR

Windows Mixed Reality 디바이스에서 실행되는 디바이스 엔드포인트 및 OS 버전에 따라 Late-Stage 다시 프로젝션 알고리즘은 픽셀당 또는 안정화 [평면을](/windows/mixed-reality/hologram-stability#stabilization-plane)통해 수행됩니다.

##### <a name="per-pixel-depth-based"></a>픽셀당 깊이 기반

픽셀별 깊이 기반 다시 프로젝션에는 깊이 버퍼를 활용하여 픽셀당 이미지 출력을 수정하여 다양한 거리에 있는 홀로그램을 안정화하는 작업이 포함됩니다. 예를 들어 1m 떨어진 구는 10m 떨어진 핵심 요소 앞에 있을 수 있습니다. 구를 나타내는 픽셀은 사용자가 헤드를 약간 기울인 경우 핵심을 나타내는 멀리 떨어진 픽셀과 다른 변환을 갖습니다. 픽셀당 다시 프로젝션은 보다 정확한 다시 프로젝션을 위해 모든 픽셀에서 이 거리 차이를 고려합니다.

##### <a name="stabilization-plane"></a>안정화 평면

플랫폼과 공유할 정확한 깊이 버퍼를 만들 수 없는 경우 또 다른 형태의 LSR은 안정화 평면을 활용합니다. 장면의 모든 홀로그램은 일부 안정화를 받지만 원하는 평면에 있는 홀로그램은 최대 하드웨어 안정화를 받습니다. 평면의 점과 표준은 Unity에서 제공하는 *HolographicSettings.SetFocusPointForFrame* [API를](/windows/mixed-reality/focus-point-in-unity)통해 플랫폼에 제공할 수 있습니다.

#### <a name="depth-buffer-format"></a>깊이 버퍼 형식

개발을 위한 HoloLens 대상으로 지정하는 경우 24비트 대비 16비트 깊이 버퍼 형식을 활용하는 것이 좋습니다. 깊이 값의 정밀도가 낮아지더라도 성능이 크게 저하될 수 있습니다. 낮은 정밀도를 보정하고 [z-fighting을](https://en.wikipedia.org/wiki/Z-fighting)방지하려면 Unity에서 설정한 1000m 기본값에서 [원거리 클립 평면을](https://docs.unity3d.com/Manual/class-Camera.html) 줄이는 것이 좋습니다.

> [!NOTE]
> *16비트 깊이 형식을* 사용하는 경우 Unity가 이 설정에서 [스텐실 버퍼를 만들지 않으므로 스텐실 버퍼에](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 필요한 효과가 작동하지 않습니다. *24비트 깊이 형식을* 선택하면 일반적으로 엔드포인트 그래픽 플랫폼에 해당하는 경우 [8비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html)가 생성됩니다.

#### <a name="depth-buffer-sharing-in-unity"></a>Unity의 깊이 버퍼 공유

깊이 기반 LSR을 활용하려면 개발자가 수행해야 하는 두 가지 중요한 단계가 있습니다.

1. Project 설정   >    >  **Player**  >  **XR 설정** Virtual Reality  >  **SDK** 편집 > 깊이 **버퍼 공유** 사용
    1. HoloLens 대상으로 하는 경우 **16비트 깊이 형식도** 선택하는 것이 좋습니다.
1. 화면에서 색을 렌더링하는 경우 렌더링 깊이도

Unity의 [불투명 GameObjects는](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) 일반적으로 깊이에 자동으로 기록됩니다. 그러나 투명 & 텍스트 개체는 일반적으로 기본적으로 깊이로 작성되지 않습니다. MRTK 표준 셰이더 또는 텍스트 메시 Pro 활용하는 경우 쉽게 해결할 수 있습니다.

> [!NOTE]
> 장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 빠르게 확인하려면 MRTK 구성 프로필의 *편집기 설정* 아래에 [ *있는 렌더링 깊이 버퍼* 유틸리티를](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용할 수 있습니다.

##### <a name="transparent-mrtk-standard-shader"></a>투명한 MRTK 표준 셰이더

[MRTK 표준 셰이더를](../features/rendering/MRTK-standard-shader.md)사용하는 투명 재질의 경우 *검사기* 창에서 볼 재질을 선택합니다. 그런 다음 *지금 수정* 단추를 클릭하여 재질을 깊이에 쓰도록 변환합니다(즉, Z-Write On).

이전

![MRTK 표준 셰이더를 수정하기 전의 깊이 버퍼](../features/images/performance/DepthBufferFixNow_Before.PNG)

After

![깊이 버퍼 고정 MRTK 표준 셰이더](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>텍스트 메시 Pro

Text Mesh Pro 개체의 경우 TMP GameObject를 선택하여 검사기에서 봅니다. 재질 구성 요소 아래에서 할당된 재질의 셰이더를 전환하여 MRTK TextMeshPro 셰이더를 사용합니다.

![텍스트 메시 Pro 깊이 버퍼 수정](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

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

HoloLens 같은 디바이스는 지속적으로 환경을 검색하고 학습합니다. 따라서 HoloLens 공간에서 이동 & 위치를 추적하므로 해당 예상치가 업데이트되고 Unity [좌표계가 조정됩니다.](/windows/mixed-reality/coordinate-systems-in-unity) 예를 들어 GameObject가 시작 시 카메라에서 1m 정도 배치되는 경우 HoloLens 환경을 추적할 때 GameObject가 있는 물리적 지점이 실제로 1.1m 떨어져 있음을 알 수 있습니다. 이로 인해 홀로그램이 드리프트될 수 있습니다. GameObject에 WorldAnchor를 적용하면 앵커가 개체의 변환을 제어하여 개체가 올바른 물리적 위치(즉, 을 런타임에 1m이 아닌 1.1m 으로 업데이트합니다. 앱 세션 간에 [WorldAnchors를](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 유지하려면 개발자가 [WorldAnchorStore를 사용하여 WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 를 [저장하고 로드할](/windows/mixed-reality/persistence-in-unity)수 있습니다.

> [!NOTE]
> WorldAnchor 구성 요소가 GameObject에 추가되면 해당 GameObject의 변환(즉, transform.position = x). 개발자는 변환을 편집하려면 WorldAnchor를 제거해야 합니다.

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

앵커를 수동으로 작업하는 대신 사용하려면 Microsoft World Locking Tools를 확인하세요. 

> [!div class="nextstepaction"]
> [MR 기능 도구를 사용하여 설치](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>참고 항목

- [성능](../performance/perf-getting-started.md)
- [HoloLens 대한 환경 고려 사항](/windows/mixed-reality/environment-considerations-for-hololens)
- [홀로그램 안정성 Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Unity의 포커스 포인트](/windows/mixed-reality/focus-point-in-unity)
- [Unity의 좌표계](/windows/mixed-reality/coordinate-systems-in-unity)
- [Unity의 지속성](/windows/mixed-reality/persistence-in-unity)
- [Mixed Reality 성능 이해](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Unity의 권장 성능](/windows/mixed-reality/performance-recommendations-for-unity)
