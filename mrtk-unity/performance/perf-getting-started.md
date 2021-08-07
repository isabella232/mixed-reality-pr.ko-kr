---
title: 성능
description: MRTK의 전형을 이해하고 조정하는 설명서입니다.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 50128100d058b5ec3bca7eac523c78287ce657925c3ac116e4336174e34e75c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211188"
---
# <a name="performance"></a>성능

## <a name="getting-started"></a>시작

성능을 합리화하는 가장 쉬운 방법은 프레임 속도 또는 애플리케이션이 초당 이미지를 렌더링할 수 있는 횟수를 통하는 것입니다. 대상으로 지정되는 플랫폼에 설명된 대로 대상 프레임 전송률(즉, [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)등). 예를 들어 HoloLens 대상 프레임 속도는 60FPS입니다. 프레임 속도 애플리케이션이 낮으면 [홀로그램 안정화,](../performance/hologram-stabilization.md)세계 추적, 손 추적 등과 같은 사용자 환경이 저하될 수 있습니다. 개발자가 품질 프레임 속도 추적 및 달성을 돕기 위해 Mixed Reality Toolkit 다양한 도구와 스크립트를 제공합니다.

### <a name="visual-profiler"></a>시각적 프로파일러

개발 수명 동안 성능을 지속적으로 추적하려면 애플리케이션 디버깅을 & 실행하는 동안 항상 프레임 속도 시각적 개체를 표시하는 것이 좋습니다. Mixed Reality Toolkit 애플리케이션 보기에서 현재 FPS 및 메모리 사용에 대 한 실시간 정보를 제공 하는 [Visual Profiler](../features/diagnostics/using-visual-profiler.md) 진단 도구를 제공 합니다. [MRTK 프로필 검사기에서](../configuration/mixed-reality-configuration-guide.md) [진단 시스템 설정](../features/diagnostics/diagnostics-system-getting-started.md) 통해 시각적 프로파일러를 구성할 수 있습니다.

또한 Unity 편집기 또는 에뮬레이터에서 실행하는 대신 디바이스에서 실행할 때 Visual Profiler를 활용하여 프레임 전송률을 추적하는 것이 특히 중요합니다. [릴리스 구성 빌드를](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)통해 디바이스에서 실행할 때 가장 정확한 성능 결과가 표시됩니다.

> [!NOTE]
> Windows Mixed Reality 위해 빌드하는 경우 [MASTER 구성 빌드를 통해 배포합니다.](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Visual Profiler 인터페이스](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>최적화 창

[MRTK 최적화 창은](../features/tools/optimize-window.md) 혼합 현실 개발자가 최상의 결과를 위해 환경을 설정하고 장면 & 자산의 잠재적 병목 현상을 식별하는 데 도움이 되는 정보 및 자동화 도구를 제공합니다. Unity의 특정 주요 구성은 혼합 현실 프로젝트에 대해 훨씬 더 최적화된 결과를 제공하는 데 도움이 될 수 있습니다.

일반적으로 이러한 설정에는 혼합 현실에 이상적인 렌더링 구성이 포함됩니다. 혼합 현실 애플리케이션은 두 개의 화면(즉, 두 눈)을 사용하여 전체 장면에 대해 렌더링합니다.

아래에서 참조하는 권장 설정은 MRTK 최적화 창을 활용하여 Unity 프로젝트에서 자동으로 구성할 수 있습니다.

![MRTK 최적화 창 설정](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler는](https://docs.unity3d.com/Manual/ProfilerWindow.html) 프레임 단위 수준에서 애플리케이션 성능의 세부 정보를 조사하는 데 유용한 도구입니다.

#### <a name="time-spent-on-the-cpu"></a>CPU에 소요된 시간

![Unity Profiler Graph 예제](../features/images/performance/UnityProfilerGraph.png)

편한 프레임 속도(일반적으로 초당 60프레임)를 유지하려면 애플리케이션에서 최대 16.6밀리초의 CPU 시간을 달성해야 합니다. MRTK 기능의 비용을 식별하기 위해 Microsoft Mixed Reality Toolkit 내부 루프(프레임당) 코드 경로에 대한 표식이 포함되어 있습니다. 이러한 표식은 사용 중인 특정 기능을 이해하는 데 도움이 하려면 다음 형식을 사용합니다.

```
[MRTK] className.methodName
```

> [!Note]
> 메서드 이름 다음에 추가 데이터가 있을 수 있습니다. 이 기능은 애플리케이션 코드를 작게 변경하여 방지할 수 있는 조건부로 실행되고 비용이 많이 들 수 있는 기능을 식별하는 데 사용됩니다.

![Unity Profiler 계층 구조 예제](../features/images/performance/UnityProfilerHierarchy.png)

이 예제에서는 계층 구조가 확장되어 WindowsMixedRealityArticulatedHand 클래스의 UpdateHandData 메서드가 분석되는 프레임 동안 0.44ms의 CPU 시간을 사용함을 보여 했습니다. 이 데이터는 성능 문제가 애플리케이션 코드 또는 시스템의 다른 위치에서 관련되어 있는지 확인하는 데 사용할 수 있습니다.

개발자는 비슷한 방식으로 애플리케이션 코드를 계측하는 것이 좋습니다. 애플리케이션 코드 계측에 대한 주요 영역은 이벤트가 발생할 때 이러한 메서드가 MRTK 업데이트 루프에 청구되기 때문에 이벤트 처리기 내에 있습니다. MRTK 업데이트 루프 내에서 프레임 시간이 높으면 이벤트 처리기 메서드에서 비용이 많이 드는 코드를 나타낼 수 있습니다.

## <a name="recommended-settings-for-unity"></a>Unity 권장 설정

### <a name="single-pass-instanced-rendering"></a>인스턴스 렌더링 Single-Pass

Unity의 XR에 대한 기본 렌더링 구성은 [다중 패스](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)입니다. 이 설정은 전체 렌더링 파이프라인을 각 시선에 대해 한 번씩 두 번 실행하도록 Unity에 지시합니다. 대신 단일 패스 인스턴스 [렌더링을](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 선택하여 최적화할 수 있습니다. 이 구성은 [렌더링 대상 배열을](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 활용하여 각 눈의 적절한 렌더링 [대상에](https://en.wikipedia.org/wiki/Render_Target) 인스턴스가 있는 단일 그리기 호출을 수행할 수 있습니다. 또한 이 모드를 사용하면 렌더링 파이프라인의 단일 실행에서 모든 렌더링을 수행할 수 있습니다. 따라서 단일 패스 인스턴스 렌더링을 혼합 현실 애플리케이션의 렌더링 경로로 선택하면 [CPU & GPU에서 상당한 시간을 절약할](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) 수 있으며 권장되는 렌더링 구성입니다.

그러나 각 눈에 각 메시에 대해 단일 그리기 호출을 발급하려면 모든 [셰이더에서 GPU 인탄싱을](https://docs.unity3d.com/Manual/GPUInstancing.html) 지원해야 합니다. 인스턴싱을 사용하면 GPU가 양쪽 눈에서 호출을 멀티플렉싱할 수 있습니다. 기본적으로 Unity 기본 제공 셰이더와 [MRTK 표준 셰이더에는](../features/rendering/mrtk-standard-shader.md) 셰이더 코드에 필요한 인탄싱 명령이 포함되어 있습니다. Unity에 대해 사용자 지정 셰이더를 작성하는 경우 단일 패스 인스턴스 렌더링을 지원하도록 이러한 셰이더를 업데이트해야 할 수 있습니다.

#### <a name="example-code-for-custom-shader"></a>[사용자 지정 셰이더에 대한 예제 코드](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>품질 설정

Unity는 각 플랫폼 엔드포인트에 대한 렌더링 [품질을 제어하기](https://docs.unity3d.com/Manual/class-QualitySettings.html) 위한 사전 설정을 제공합니다. 이러한 사전 설정은 그림자, 앤티 앨리어싱, 전역 조명 등과 같이 사용할 수 있는 그래픽 기능을 제어합니다. 이러한 설정을 낮추고 렌더링하는 동안 수행되는 계산 수를 최적화하는 것이 좋습니다.

*1단계:* *낮은 품질* 수준 설정을 사용하도록 혼합 현실 Unity 프로젝트 업데이트  
**편집**  >  **Project 설정** 품질 **범주** > UWP 플랫폼에 낮은 *품질* 선택

*2단계:* 모든 Unity 장면 파일에 대해 [실시간 글로벌 조명을](https://docs.unity3d.com/Manual/LightMode-Realtime.html) 사용하지 않도록 설정합니다.  
**창**  >  **렌더링**  >  **조명 설정**  >  [ *실시간 전역 조명* 선택 취소](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>깊이 버퍼 공유(HoloLens)

Windows Mixed Reality 플랫폼 및 특히 HoloLens 대해 개발하는 경우 *XR 설정* 따라 *깊이 버퍼 공유를* 사용하도록 설정하면 [홀로그램 안정화에](../performance/hologram-stabilization.md)도움이 될 수 있습니다. 그러나 깊이 버퍼를 처리하면 특히 [24비트 깊이 형식 를](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)사용하는 경우 성능 비용이 발생할 수 있습니다. 따라서 깊이 버퍼를 16비트 전체 자릿수로 구성하는 *것이 좋습니다.*

낮은 비트 형식으로 인해 [z-fighting이](https://en.wikipedia.org/wiki/Z-fighting) 발생하는 경우 모든 카메라의 [원거리 클립 평면이](https://docs.unity3d.com/Manual/class-Camera.html) 애플리케이션에 대해 가능한 가장 낮은 값으로 설정되어 있는지 확인합니다. Unity는 기본적으로 1000m의 원거리 클립 평면을 설정합니다. HoloLens 50m의 원거리 클립 평면은 일반적으로 대부분의 애플리케이션 시나리오에서 충분한 것보다 더 큽니다.

> [!NOTE]
> *16비트 깊이 형식을* 사용하는 경우 Unity가 이 설정에서 [스텐실 버퍼를 만들지 않으므로 스텐실 버퍼에](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 필요한 효과가 작동하지 않습니다. *24비트 깊이 형식을* 선택하면 일반적으로 엔드포인트 그래픽 플랫폼에 해당하는 경우 8비트 스텐실 버퍼가 생성됩니다.
>
> 스텐실 버퍼가 필요한 [마스크 구성 요소를](https://docs.unity3d.com/Manual/script-Mask.html) 사용하는 경우 스텐실 버퍼가 필요하지 않으므로 *16비트 깊이 형식* 과 함께 사용할 수 있는 [RectMask2D를](https://docs.unity3d.com/Manual/script-RectMask2D.html) 대신 사용하는 것이 좋습니다.

> [!NOTE]
> 장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 빠르게 확인하려면 MRTK 구성 프로필의 *편집기 설정* 아래에 [ *있는 렌더링 깊이 버퍼* 유틸리티를](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용할 수 있습니다.

### <a name="optimize-mesh-data"></a>Mesh 데이터 최적화

[Mesh 데이터 최적화](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) 설정은 애플리케이션 내에서 사용되지 않는 꼭짓점 특성을 제거하려고 시도합니다. 설정은 빌드의 모든 메시에 있는 모든 재질의 모든 셰이더 패스에 대해 를 실행하여 이를 수행합니다. 이는 게임 데이터 크기 및 런타임 성능에 적합하지만 빌드 시간을 크게 저하할 수 있습니다.

개발 중에 이 설정을 사용하지 않도록 설정하고 "마스터" 빌드를 만드는 동안 다시 사용하도록 설정하는 것이 좋습니다. 설정은 Project 설정 플레이어 **편집**  >    >    >  **기타 설정** 메시 데이터 최적화에서 찾을 수  >  **있습니다.**

## <a name="general-recommendations"></a>일반 권장 사항

성능은 혼합 현실 개발자에게 모호하고 지속적으로 변화하는 과제일 수 있으며 성능을 합리화하기 위한 지식 스펙트럼은 방대합니다. 그러나 애플리케이션의 성능에 접근하는 방법을 이해하기 위한 몇 가지 일반적인 권장 사항이 있습니다.

*CPU* 또는 *GPU에서* 실행되는 구성 요소로 애플리케이션 실행을 간소화하여 앱이 어느 구성 요소에 의해 제한되는지 여부를 식별하는 것이 유용합니다.  처리 단위와 신중하게 조사해야 하는 몇 가지 고유한 시나리오에 걸쳐 있는 병목 현상이 있을 수 있습니다. 그러나 시작하려면 애플리케이션이 가장 많은 시간 동안 실행되는 위치를 파악하는 것이 좋습니다.

### <a name="gpu-bounded"></a>GPU 경계

혼합 현실 애플리케이션에 대한 대부분의 플랫폼은 [입체 렌더링을](https://en.wikipedia.org/wiki/Stereoscopy)활용하기 때문에 "이중 너비" 화면을 렌더링하는 특성으로 인해 GPU에 바인딩되는 것이 매우 일반적입니다. 또한 HoloLens 또는 Oculus Quest와 같은 모바일 혼합 현실 플랫폼은 모바일 클래스 CPU & GPU 처리 능력으로 제한됩니다.

GPU에 집중할 때 일반적으로 애플리케이션이 모든 프레임을 완료해야 하는 두 가지 중요한 단계가 있습니다.

1. [꼭짓점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) 실행
2. 픽셀 [셰이더(조각 셰이더라고도](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 함)를 실행합니다.

렌더링 [파이프라인을](https://en.wikipedia.org/wiki/Graphics_pipeline)& 컴퓨터 그래픽의 복잡한 필드를 심도 있게 분석하지 않으면 각 셰이더 단계는 GPU에서 실행되어 다음을 생성하는 프로그램입니다.

1. 꼭짓점 셰이더가 메시 꼭짓점을 화면 공간의 좌표로 변환(즉, 꼭짓점당 실행된 코드)
2. 픽셀 셰이더가 지정된 픽셀 및 메시 조각(즉, 픽셀당 코드 실행)

성능 튜닝과 관련하여 일반적으로 픽셀 셰이더에서 작업을 최적화하는 데 집중하는 것이 더 좋은 일입니다. 애플리케이션은 꼭짓점이 8개뿐인 큐브를 그리기만 하면 됩니다. 그러나 큐브가 차지하는 화면 공간은 수백만 픽셀 순서로 표시할 수 있습니다. 따라서 10개 연산을 통해 셰이더 코드를 줄이면 꼭짓점 셰이더보다 픽셀 셰이더에서 감소하는 경우 훨씬 더 많은 작업을 절약할 수 있습니다.

이는 일반적으로 이 셰이더가 Unity 표준 [셰이더보다](../features/rendering/mrtk-standard-shader.md) 픽셀 & 꼭짓점당 더 적은 명령을 실행하면서 비교 가능한 미적 결과를 달성하기 때문에 MRTK 표준 셰이더를 활용하는 주된 이유 중 하나입니다.

|    CPU 최적화      |             GPU 최적화              |
|---------------------------|--------------------------------------------|
| 앱 시뮬레이션 논리      | 렌더링 작업 |
| 물리학 단순화          | 조명 계산 줄이기 |
| 애니메이션 단순화       | 그리기 가능한 개체의 다각형 개수 & 감소 |
| 가비지 수집 관리 | 투명 개체 수 줄이기 |
| 캐시 참조          | 후처리/전체 화면 효과 방지  |

### <a name="draw-call-instancing"></a>그리기 호출 인탄싱

Unity에서 성능을 저하시키는 가장 일반적인 실수 중 하나는 런타임에 재질을 복제하는 것입니다. GameObjects가 동일한 재질 및/또는 를 공유하는 경우 *[정적 일괄 처리,](https://docs.unity3d.com/Manual/DrawCallBatching.html)* *[동적 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 및 *[GPU 인탄싱과](https://docs.unity3d.com/Manual/GPUInstancing.html)* 같은 기술을 통해 단일 그리기 호출로 최적화할 수 있습니다. 그러나 개발자가 런타임에 [렌더러 재질의](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 속성을 수정하는 경우 Unity는 할당된 재질의 복제 복사본을 만듭니다.

예를 들어 장면에 100개의 큐브가 있는 경우 개발자는 런타임에 각각에 고유한 색을 할당하려고 할 수 있습니다. C#에서 [*renderer.material.color에*](https://docs.unity3d.com/ScriptReference/Material-color.html) 액세스하면 Unity에서 이 특정 렌더러/GameObject에 대한 새 재질을 메모리에 만들 수 있습니다. 각 100개 큐브에는 자체 재질이 있으므로 하나의 그리기 호출로 병합할 수 없지만, 대신 CPU에서 GPU로의 100개 그리기 호출 요청이 됩니다.

이러한 장애물을 극복하고 큐브당 고유한 색을 할당하려면 개발자는 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)를 활용해야 합니다.

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Unity 성능 도구

Unity는 편집기에서 기본 제공되는 뛰어난 성능 도구를 제공합니다.

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)

한 셰이더와 다른 셰이더 간의 대략적인 성능 절충을 예측하는 경우 각 셰이더를 컴파일하고 셰이더 단계당 작업 수를 보는 것이 유용합니다. 이 작업은 [셰이더 자산을](https://docs.unity3d.com/Manual/class-Shader.html) 선택하고 컴파일 및 *코드 표시* 단추를 클릭하여 수행할 수 있습니다. 그러면 모든 셰이더 변형이 컴파일되고 결과와 함께 Visual Studio가 열립니다. 참고: 생성된 통계 결과는 지정된 셰이더를 활용하는 재질에서 사용하도록 설정된 기능에 따라 달라질 수 있습니다. Unity는 현재 프로젝트에서 직접 사용되는 셰이더 변형만 컴파일합니다.

Unity 표준 셰이더 통계 예제

![Unity 표준 셰이더 통계 1](../features/images/performance/UnityStandardShader-Stats.PNG)

MRTK 표준 셰이더 통계 예제

![MRTK 표준 셰이더 통계 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>추가 정보

### <a name="unity"></a>Unity

- [초보자를 위한 Unity 성능 최적화](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Unity 성능 최적화 자습서](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Unity 최적화 모범 사례](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [그래픽 성능 최적화](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [모바일 최적화 실용 가이드](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Unity에 권장되는 설정](/windows/mixed-reality/recommended-settings-for-unity)
- [Mixed Reality 성능 이해](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Unity의 권장 성능](/windows/mixed-reality/performance-recommendations-for-unity)
- [Windows Unity용 이벤트 추적 가이드](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [성능 지침](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [성능 도구](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>메시 최적화

- [3D 모델 최적화](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [실시간 3D 모델 변환 및 최적화 모범 사례](/dynamics365/mixed-reality/import-tool/best-practices)
