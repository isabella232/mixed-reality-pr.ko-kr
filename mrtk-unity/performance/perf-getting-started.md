---
title: 성능 시작
description: MRTK의 preformance을 이해 하 고 조정 하는 설명서입니다.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 1ddc057c7f3966375d512a5e4a714dce093412e6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144868"
---
# <a name="performance"></a>성능

## <a name="getting-started"></a>시작

성능을 합리화 하는 가장 쉬운 방법은 프레임 속도를 통하거나 응용 프로그램이 초당 이미지를 렌더링할 수 있는 횟수입니다. 대상 플랫폼에 설명 된 대로 대상 프레임을 충족 하는 것이 중요 합니다 (즉, [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)등). 예를 들어 HoloLens에서 대상 프레임 속도는 60 FPS입니다. 낮은 프레임 속도 응용 프로그램은 악화 사용자 환경을 만들 수 있습니다 [. 예를 들어, 세계](../performance/hologram-stabilization.md)추적, 수동 추적 등이 있습니다. 개발자가 우수한 품질의 프레임 속도를 추적 하 고 달성할 수 있도록 혼합 현실 도구 키트는 다양 한 도구와 스크립트를 제공 합니다.

### <a name="visual-profiler"></a>시각적 프로파일러

개발 수명 동안 지속적으로 성능을 추적 하려면 응용 프로그램 디버깅 & 실행 하는 동안 항상 프레임 속도 시각적 개체를 표시 하는 것이 좋습니다. Mixed Reality Toolkit은 응용 프로그램 보기에서 현재 FPS 및 메모리 사용에 대 한 실시간 정보를 제공 하는 [Visual Profiler](../features/diagnostics/using-visual-profiler.md) 진단 도구를 제공 합니다. Visual Profiler는 [Mrtk 프로필 검사자](../configuration/mixed-reality-configuration-guide.md)의 [진단 시스템 설정을](../features/diagnostics/diagnostics-system-getting-started.md) 통해 구성할 수 있습니다.

또한 Unity 편집기 또는 에뮬레이터에서 실행 하는 것이 아니라 장치에서 실행 되는 경우 시각적 프로파일러를 활용 하 여 프레임 속도를 추적 하는 것이 특히 중요 합니다. 가장 정확한 성능 결과는 [릴리스 구성 빌드에서](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)장치에서 실행 될 때 표시 됩니다.

> [!NOTE]
> Windows Mixed Reality를 빌드하는 경우 [마스터 구성 빌드](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution) 를 사용 하 여 배포

![Visual Profiler 인터페이스](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>최적화 창

[Mrtk Optimize 창은](../features/tools/optimize-window.md) 혼합 현실 개발자가 최상의 결과를 위해 환경을 설정 하 고 장면 & 자산에서 잠재적 병목 상태를 식별 하는 데 도움이 되는 정보 및 자동화 도구를 제공 합니다. Unity의 특정 키 구성은 혼합 현실 프로젝트에 대해 훨씬 더 최적화 된 결과를 제공 하는 데 도움이 될 수 있습니다.

일반적으로 이러한 설정에는 혼합 현실에 이상적인 렌더링 구성이 포함 됩니다. 혼합 현실 응용 프로그램은 두 개의 화면 (즉, 두 개의 눈)에서 전체 장면에 대해 렌더링 합니다.

아래에서 참조 하는 권장 설정은 MRTK Optimize 창을 활용 하 여 Unity 프로젝트에서 자동으로 구성할 수 있습니다.

![MRTK 창 설정 최적화](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity 프로파일러

[Unity 프로파일러](https://docs.unity3d.com/Manual/ProfilerWindow.html) 는 프레임 수준 수준에서 응용 프로그램 성능에 대 한 세부 정보를 조사 하는 데 유용한 도구입니다.

#### <a name="time-spent-on-the-cpu"></a>CPU에 소요 된 시간

![예제 Unity 프로파일러 그래프](../features/images/performance/UnityProfilerGraph.png)

편안한 프레임 속도 (일반적으로 초당 60 프레임)를 유지 하기 위해 응용 프로그램은 최대 프레임 시간 (16.6 밀리초)의 CPU 시간을 획득 해야 합니다. MRTK 기능의 비용을 파악 하는 데 도움이 되도록 Microsoft Mixed Reality Toolkit에는 내부 루프 (프레임 당) 코드 경로에 대 한 표식이 포함 되어 있습니다. 이러한 마커는 다음 형식을 사용 하 여 사용 되는 특정 기능을 이해 하는 데 도움을 줍니다.

```
[MRTK] className.methodName
```

> [!Note]
> 메서드 이름 뒤에 추가 데이터가 있을 수 있습니다. 이는 응용 프로그램 코드를 약간만 변경 하 여 방지할 수 있는 조건부로 실행 되는 잠재적으로 비용이 많이 드는 기능을 식별 하는 데 사용 됩니다.

![예제 Unity 프로파일러 계층 구조](../features/images/performance/UnityProfilerHierarchy.png)

이 예제에서는 WindowsMixedRealityArticulatedHand 클래스의 UpdateHandData 메서드가 분석 중인 프레임 동안 0.44 밀리초의 CPU 시간을 소비 함을 보여 주기 위해 계층이 확장 되었습니다. 이 데이터를 사용 하 여 성능 문제가 응용 프로그램 코드와 관련 된 것인지 아니면 시스템의 다른 위치에 있는지 확인할 수 있습니다.

개발자는 응용 프로그램 코드를 비슷한 방식으로 계측 하는 것이 좋습니다. 응용 프로그램 코드 계측에 대 한 주요 포커스가 이벤트 처리기 내에 있습니다. 이러한 메서드는 이벤트가 발생할 때 MRTK 업데이트 루프로 청구 됩니다. MRTK 업데이트 루프 내의 높은 프레임 시간은 이벤트 처리기 메서드에서 비용이 많이 드는 코드를 의미할 수 있습니다.

## <a name="recommended-settings-for-unity"></a>Unity 권장 설정

### <a name="single-pass-instanced-rendering"></a>Single-Pass 인스턴스화된 렌더링

Unity의 XR에 대 한 기본 렌더링 구성은 [다중 패스](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)입니다. 이 설정은 각 눈 마다 한 번씩 전체 렌더링 파이프라인을 두 번 실행 하도록 Unity에 지시 합니다. 이는 대신 [단일 패스 인스턴스화된 렌더링](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 을 선택 하 여 최적화할 수 있습니다. 이 구성은 [렌더링 대상 배열을](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 활용 하 여 각 눈동자에 대해 해당 인스턴스를 적절 한 [렌더링 대상](https://en.wikipedia.org/wiki/Render_Target) 으로 단일 그리기 호출을 수행할 수 있도록 합니다. 또한이 모드를 사용 하면 렌더링 파이프라인의 단일 실행에서 모든 렌더링을 수행할 수 있습니다. 따라서 혼합 현실 응용 프로그램의 렌더링 경로로 단일 패스 인스턴스화된 렌더링을 선택 하면 [CPU & GPU에서 상당한 시간을 절약할](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) 수 있으며 권장 되는 렌더링 구성입니다.

그러나 각 메시에 대해 단일 그리기 호출을 실행 하려면 모든 셰이더가 [GPU 인스턴스](https://docs.unity3d.com/Manual/GPUInstancing.html) 를 지원 해야 합니다. 인스턴스를 사용 하면 GPU에서 두 눈에 멀티플렉싱 그리기 호출을 수행할 수 있습니다. Unity 기본 제공 셰이더 뿐만 아니라 [Mrtk 표준 셰이더](../features/rendering/mrtk-standard-shader.md) 는 기본적으로 셰이더 코드에 필요한 인스턴스화 지침을 포함 합니다. Unity의 경우에만 사용자 지정 셰이더를 작성 하는 경우에는 단일 패스 인스턴스화된 렌더링을 지원 하도록 이러한 셰이더를 업데이트 해야 할 수 있습니다.

#### <a name="example-code-for-custom-shader"></a>[사용자 지정 셰이더에 대 한 예제 코드](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

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

Unity는 각 플랫폼 끝점의 렌더링 [품질을 제어 하는 사전 설정을](https://docs.unity3d.com/Manual/class-QualitySettings.html) 제공 합니다. 이러한 사전 설정은 그림자, 앤티앨리어싱, 전 세계 조명 등과 같이 사용할 수 있는 그래픽 기능을 제어 합니다. 이러한 설정을 낮추고 렌더링 중에 수행 되는 계산의 수를 최적화 하는 것이 좋습니다.

*1 단계:* *낮은 품질* 수준 설정을 사용 하도록 Mixed reality Unity 프로젝트를 업데이트 합니다.  
**편집**  >  그런 다음 **프로젝트 설정** 에서 **품질** 범주를 선택 하 > UWP 플랫폼의 저품질 *품질* 을 선택 합니다.

*2 단계:* 모든 Unity 장면 파일의 경우 [실시간 글로벌 조명을](https://docs.unity3d.com/Manual/LightMode-Realtime.html) 사용 하지 않도록 설정  
**창**  >  **렌더링**  >  **조명 설정**  >  [ *실시간 글로벌 조명* 선택 취소](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>HoloLens (깊이 버퍼 공유)

Windows Mixed Reality 플랫폼과 특정 HoloLens를 개발 하는 경우 *XR 설정* 에서 *깊이 버퍼 공유* 를 사용 하도록 설정 하면 [홀로그램 안정화](../performance/hologram-stabilization.md)에 도움이 될 수 있습니다. 그러나 깊이 버퍼를 처리 하면 성능이 저하 될 수 있으며, 특히 [24 비트 깊이 형식을](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)사용할 경우에는 성능이 저하 될 수 있습니다. 따라서 깊이 버퍼를 16 비트 정밀도로 구성 하는 것이 *좋습니다* .

더 낮은 비트 형식으로 인해 [z를 싸우는](https://en.wikipedia.org/wiki/Z-fighting) 경우 모든 카메라의 [먼 클립 평면이](https://docs.unity3d.com/Manual/class-Camera.html) 응용 프로그램에 대해 가능한 가장 낮은 값으로 설정 되었는지 확인 합니다. Unity는 기본적으로 원거리 클립 평면을 1000m으로 설정 합니다. HoloLens에서 5천만 개의 먼 클립 평면은 일반적으로 대부분의 응용 프로그램 시나리오에서 충분 합니다.

> [!NOTE]
> *16 비트 깊이 형식을* 사용 하는 경우 Unity에서이 설정에 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 스텐실 버퍼 필요 효과가 작동 하지 않습니다. 이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 해당 하는 경우 8 비트 스텐실 버퍼가 생성 됩니다.
>
> 스텐실 버퍼가 필요한 [마스크 구성 요소](https://docs.unity3d.com/Manual/script-Mask.html) 를 사용 하는 경우 스텐실 버퍼를 요구 하지 않으므로 *16 비트 깊이 형식과* 함께 사용할 수 있는 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) 를 대신 사용 하는 것이 좋습니다.

> [!NOTE]
> 장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 신속 하 게 확인 하기 위해 MRTK 구성 프로필의 *편집기 설정* 에서 [ *렌더링 수준 버퍼* 유틸리티](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 사용할 수 있습니다.

### <a name="optimize-mesh-data"></a>메시 데이터 최적화

[메시 데이터 최적화](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) 설정은 응용 프로그램 내에서 사용 되지 않는 꼭 짓 점 특성을 제거 하려고 합니다. 이 설정은 빌드의 모든 메시에 서 모든 재질의 모든 셰이더 패스를 실행 하 여이를 수행 합니다. 이는 게임 데이터 크기 및 런타임 성능에 적합 하지만 빌드 시간을 크게 저하 시킬 수 있습니다.

개발 중에 이 설정을 사용하지 않도록 설정하고 "마스터" 빌드를 만드는 동안 다시 사용하도록 설정하는 것이 좋습니다. 이 설정은 프로젝트 설정 **편집**  >    >  **플레이어**  >  **기타 설정** 메시 데이터 최적화에서 찾을 수  >  **있습니다.**

## <a name="general-recommendations"></a>일반 권장 사항

성능은 혼합 현실 개발자에게 모호하고 지속적으로 변화하는 과제일 수 있으며 성능을 합리화하는 지식 스펙트럼은 방대합니다. 그러나 애플리케이션의 성능에 접근하는 방법을 이해하기 위한 몇 가지 일반적인 권장 사항이 있습니다.

*CPU* 또는 *GPU에서* 실행되는 구성 요소로 애플리케이션 실행을 간소화하여 앱이 어느 구성 요소에 의해 제한되는지 여부를 식별하는 것이 유용합니다.  처리 단위와 신중하게 조사해야 하는 몇 가지 고유한 시나리오에 걸쳐 있는 병목 현상이 있을 수 있습니다. 그러나 시작하려면 애플리케이션이 가장 많은 시간 동안 실행되는 위치를 파악하는 것이 좋습니다.

### <a name="gpu-bounded"></a>GPU 경계

혼합 현실 애플리케이션에 대한 대부분의 플랫폼은 [스테레오 범위 렌더링을](https://en.wikipedia.org/wiki/Stereoscopy)활용하기 때문에 "이중 너비" 화면을 렌더링하는 특성으로 인해 GPU에 바인딩되는 것이 매우 일반적입니다. 또한 HoloLens 또는 Oculus Quest와 같은 모바일 혼합 현실 플랫폼은 모바일 클래스 CPU & GPU 처리 능력으로 제한됩니다.

GPU에 집중할 때 일반적으로 애플리케이션이 모든 프레임을 완료해야 하는 두 가지 중요한 단계가 있습니다.

1. [꼭짓점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) 실행
2. 픽셀 [셰이더(조각 셰이더라고도](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 함)를 실행합니다.

렌더링 [파이프라인을](https://en.wikipedia.org/wiki/Graphics_pipeline)& 컴퓨터 그래픽의 복잡한 필드를 심도 있게 분석하지 않고 각 셰이더 단계는 GPU에서 실행되어 다음을 생성하는 프로그램입니다.

1. 꼭짓점 셰이더가 메시 꼭짓점을 화면 공간의 좌표로 변환(즉, 꼭짓점당 실행된 코드)
2. 픽셀 셰이더가 지정된 픽셀 및 메시 조각(즉, 픽셀당 코드 실행)

성능 조정과 관련 하 여 일반적으로 픽셀 셰이더의 작업 최적화에 집중 하는 것이 더 높여. 응용 프로그램에서 꼭 짓 점 8 개만 되는 큐브를 그려야 할 수 있습니다. 그러나 큐브가 차지 하는 화면 공간은 수백만 픽셀의 순서에 따라 다를 수 있습니다. 따라서 10 개의 작업을 통해 셰이더 코드를 줄이면 꼭 짓 점 셰이더 보다 픽셀 셰이더에 감소할 경우 훨씬 더 많은 작업을 저장할 수 있습니다.

이 셰이더가 일반적으로 [Mrtk 표준 셰이더](../features/rendering/mrtk-standard-shader.md) 를 활용 하는 주된 이유 중 하나는 미적 결과를 달성 하는 동안 Unity 표준 셰이더에 비해 픽셀 & 꼭 짓 점 마다 더 많은 명령을 실행 하는 것입니다.

|    CPU 최적화      |             GPU 최적화              |
|---------------------------|--------------------------------------------|
| 앱 시뮬레이션 논리      | 렌더링 작업 |
| 물리학 단순화          | 조명 계산 줄이기 |
| 애니메이션 간소화       | 그릴 수 있는 개체 수 & polygon 수 줄이기 |
| 가비지 수집 관리 | 투명 개체의 개수 줄이기 |
| 캐시 참조          | 사후 처리/전체 화면 효과 방지  |

### <a name="draw-call-instancing"></a>호출 인스턴스 그리기

Unity에서 성능을 줄이는 가장 일반적인 실수 중 하나는 런타임에 대 한 복제 자료입니다. Gameobject가 동일한 재질 및/또는 동일한 메시를 공유 하는 경우 *[정적 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[동적 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[GPU 인스턴스](https://docs.unity3d.com/Manual/GPUInstancing.html)* 등의 기술을 통해 단일 그리기 호출로 최적화 될 수 있습니다. 그러나 개발자가 런타임에 [렌더러 재질](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 의 속성을 수정 하는 경우 Unity는 할당 된 자료의 클론 복사본을 만듭니다.

예를 들어 장면에 100 큐브가 있는 경우 개발자는 런타임에 각각에 고유한 색을 할당 하는 것이 좋습니다. C #에서 [*렌더러에*](https://docs.unity3d.com/ScriptReference/Material-color.html) 대 한 액세스를 통해 Unity는이 특정 렌더러/GameObject에 대해 메모리에 새 자료를 만듭니다. 각 100 큐브는 고유한 자료를 포함 하므로 하나의 그리기 호출로 결합 될 수는 없으며, 대신 CPU에서 GPU로의 100 그리기 호출 요청이 됩니다.

이러한 장애물을 극복 하 고 큐브 별로 고유한 색을 할당 하려면 개발자가 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)를 활용 해야 합니다.

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

Unity는 편집기에 기본 제공 되는 뛰어난 성능 도구를 제공 합니다.

- [Unity 프로파일러](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)

하나의 셰이더와 다른 셰이더 간의 대략적인 성능 균형을 예측 하는 경우 각 셰이더를 컴파일하고 셰이더 단계 당 작업 수를 확인 하는 것이 유용 합니다. [셰이더 자산](https://docs.unity3d.com/Manual/class-Shader.html) 을 선택 하 고 *컴파일 및 코드 표시* 단추를 클릭 하 여이 작업을 수행할 수 있습니다. 그러면 모든 셰이더 변형이 컴파일되고 결과가 포함 된 visual studio가 열립니다. 참고: 생성 된 통계 결과는 지정 된 셰이더를 활용 하는 자료에서 사용 하도록 설정 된 기능에 따라 달라질 수 있습니다. Unity는 현재 프로젝트에서 직접 사용 되는 셰이더 변형만 컴파일합니다.

Unity 표준 셰이더 통계 예제

![Unity 표준 셰이더 통계 1](../features/images/performance/UnityStandardShader-Stats.PNG)

MRTK 표준 셰이더 통계 예제

![MRTK 표준 셰이더 통계 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>참고 항목

### <a name="unity"></a>Unity

- [초보자를 위한 Unity 성능 최적화](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Unity 성능 최적화 자습서](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Unity 최적화 모범 사례](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [그래픽 성능 최적화](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [모바일 최적화 실용 가이드](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Unity에 대한 권장 설정](/windows/mixed-reality/recommended-settings-for-unity)
- [Mixed Reality 성능 이해](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Unity의 권장 성능](/windows/mixed-reality/performance-recommendations-for-unity)
- [ETW(Windows용 이벤트 추적) Unity 가이드](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [성능 지침](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [성능 도구](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>메시 최적화

- [3D 모델 최적화](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [실시간 3D 모델 변환 및 최적화 모범 사례](/dynamics365/mixed-reality/import-tool/best-practices)