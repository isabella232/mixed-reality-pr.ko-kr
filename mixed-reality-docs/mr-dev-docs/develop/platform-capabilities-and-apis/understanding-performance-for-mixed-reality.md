---
title: Mixed Reality 성능 이해
description: Windows Mixed Reality 앱 성능을 분석하고 최적화하기 위한 고급 정보와 세부 정보를 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 성능, 최적화, CPU, GPU
ms.openlocfilehash: 394198011c40f0b90e2c5579f7e0ad8c4019b2a8cefcb1859c544afcbce47df6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193564"
---
# <a name="understanding-performance-for-mixed-reality"></a>혼합 현실의 성능 이해

이 문서에서는 Mixed Reality 앱에 대한 성능의 중요성을 이해하는 방법을 소개합니다.  애플리케이션이 최적의 프레임 속도로 실행되지 않으면 사용자 환경의 성능이 크게 저하될 수 있습니다. 홀로그램스 불안정해 보이고 환경의 헤드 추적이 부정확하여 사용자 환경이 저하됩니다. 성능은 혼합 현실 개발을 위한 첫 번째 클래스 기능으로 간주되어야 하며 폴란드어 작업이 아닙니다.

최근에 HoloLens 2 앱에 대한 일반적인 성능, 디자인 및 환경 문제 및 솔루션을 다루는 품질 기본 사항이라는 애플리케이션을 릴리스했습니다. 이 앱은 다음과 같은 콘텐츠에 대한 훌륭한 시각적 데모입니다.

> [!div class="nextstepaction"]
> [품질 기본 사항 앱 다운로드](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

각 대상 플랫폼에 대한 목표 프레임 속도 값은 다음과 같습니다.

| 플랫폼 | 대상 프레임 속도 |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60FPS |
| [Windows Mixed Reality Ultra Pc](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](../../discover/immersive-headset-hardware-details.md) | 60FPS |

아래 프레임워크는 대상 프레임 속도에 도달하기 위한 모범 사례를 간략하게 설명합니다. Unity 환경에서 프레임 속도 측정 및 향상에 대한 팁은 Unity에 [대한 성능 권장 사항 문서를](../unity/performance-recommendations-for-unity.md) 읽어보는 것이 좋습니다.

## <a name="understanding-performance-bottlenecks"></a>성능 병목 현상 이해

앱의 프레임 속도 성능이 부족한 경우 첫 번째 단계는 애플리케이션이 계산 집약적인 위치를 분석하고 이해하는 것입니다. 장면을 렌더링하는 작업을 담당하는 두 가지 기본 프로세서가 있습니다. CPU와 GPU는 각각 Mixed Reality 앱의 다양한 측면을 처리합니다. 병목 현상이 발생할 수 있는 세 가지 주요 위치는 다음과 같습니다. 

1. **앱 스레드 - CPU** -
    입력, 애니메이션, 물리학 및 기타 앱 논리 처리를 포함하여 앱 논리를 담당합니다.
2. **렌더링 스레드 - CPU에서 GPU로** - 그리기 호출을 GPU에 제출하는 것을 담당합니다. 앱이 큐브 또는 모델과 같은 개체를 렌더링하려는 경우 이 스레드는 GPU에 작업을 수행하라는 요청을 보냅니다.
3. **GPU** - 가장 일반적으로 애플리케이션의 그래픽 파이프라인을 처리하여 3D 데이터(모델, 질감 등)를 픽셀로 변환합니다. 궁극적으로 디바이스의 화면에 제출할 2D 이미지를 생성합니다.

![프레임의 수명](images/lifetime-of-a-frame.png)

일반적으로 HoloLens 애플리케이션은 GPU에 바인딩되지만 항상 그렇지는 않습니다. 아래 도구와 기술을 사용하여 특정 앱의 병목 현상이 있는 위치를 파악합니다.

## <a name="how-to-analyze-your-application"></a>애플리케이션을 분석하는 방법

혼합 현실 애플리케이션의 성능 프로필 및 잠재적 병목 현상을 이해할 수 있는 많은 도구가 있습니다. 

다음은 애플리케이션에 대한 심도 있는 프로파일링 정보를 수집하는 데 도움이 되는 몇 가지 일반적인 도구입니다.
- [Intel 그래픽 성능 분석기](https://software.intel.com/gpa)
- [Visual Studio 그래픽 디버거](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [Unreal의 GPU Pofiling](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>모든 환경에서 프로파일링하는 방법

앱이 GPU 또는 CPU 바인딩인지 확인하는 한 가지 방법은 렌더링 대상 출력의 해상도를 낮추는 것입니다. 계산할 픽셀 수를 줄이면 GPU 부하가 줄어듭니다. 디바이스는 더 작은 질감으로 렌더링된 다음, 최종 이미지를 표시하는 up-sample로 렌더링됩니다.

렌더링 해상도를 낮추면 다음이 수행됩니다.
1) 애플리케이션 프레임 전송률이 **증가하면** **GPU에 바인딩된** 것일 수 있습니다.
1) 애플리케이션 프레임 **속도는 변경되지 않고** **CPU 바인딩된** 것일 수 있습니다.

>[!NOTE]
>Unity는 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해 런타임에 애플리케이션의 렌더링 대상 해상도를 쉽게 수정할 수 있는 기능을 제공합니다. 디바이스에 제공된 최종 이미지의 해상도는 고정되어 있습니다. 플랫폼은 더 낮은 해상도 출력을 샘플링하여 디스플레이에서 렌더링하기 위한 고해상도 이미지를 빌드합니다. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>애플리케이션을 개선하는 방법

### <a name="cpu-performance-recommendations"></a>CPU 성능 추천 사항

일반적으로 CPU의 혼합 현실 애플리케이션에서 대부분의 작업에는 장면의 "시뮬레이션"을 수행하고 애플리케이션 논리를 처리하는 작업이 포함됩니다. 최적화 대상으로 지정된 영역은 다음과 같습니다.

- 애니메이션
- Physics
- 메모리 할당
- 복잡한 알고리즘(즉, 역 kinematics, 경로 찾기)

### <a name="gpu-performance-recommendations"></a>GPU 성능 추천 사항

#### <a name="understanding-bandwidth-vs-fill-rate"></a>대역폭 대 채우기 비율 이해
GPU에서 프레임을 렌더링할 때 애플리케이션은 메모리 대역폭 또는 채우기 속도에 의해 바인딩됩니다.

- **메모리 대역폭은** GPU가 메모리에서 수행할 수 있는 읽기 및 쓰기 비율입니다.
    - 대역폭 제한을 식별하려면 질감 품질을 줄이고 프레임 속도 향상 여부를 확인합니다.
    - Unity에서 **편집** Project 설정 **품질** 설정 질감  >    >  **[품질을](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 변경합니다.
- **채우기 비율은** GPU에서 초당 그릴 수 있는 픽셀을 나타냅니다.
    - 채우기 속도 제한을 식별하려면 디스플레이 해상도를 낮추고 프레임 속도가 향상되었는지 확인합니다. 
    - Unity에서  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 사용합니다.

메모리 대역폭은 일반적으로 다음 중 하나에 대한 최적화를 포함합니다.
1) 낮은 질감 해상도
2) 더 적은 질감(보통, 반사 등) 사용

채우기 비율은 다음을 포함하여 최종 렌더링된 픽셀에 대해 계산해야 하는 작업 수를 줄이는 데 중점을 두고 있습니다.
1) 렌더링/처리할 개체 수
2) 셰이더당 작업 수
3) 최종 결과에 대한 GPU 단계 수(기하 도형 셰이더, 후처리 효과 등)
4) 렌더링할 픽셀 수(디스플레이 해상도)

#### <a name="reduce-polygon-count"></a>다각형 개수 줄이기

다각형 수가 많을수록 GPU에 대한 작업이 늘어나므로 장면에서 [다각형 수를 줄이면](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 렌더링 시간이 줄어듭니다. 기하 도형 음영을 비용이 많이 드는 다른 요인이 있지만 다각형 개수는 장면을 렌더링하는 데 걸리는 작업을 결정하는 가장 간단한 메트릭입니다.

#### <a name="limit-overdraw"></a>과도한 그리기 제한

여러 개체가 렌더링되지만 폐색 개체에 의해 숨겨져 있기 때문에 화면에 표시되지 않을 때 높은 오버드로가 발생합니다. Imagine 뒤에 개체가 있는 벽이 보입니다. 모든 기하 도형은 렌더링을 위해 처리되지만 불투명 벽만 렌더링해야 하며, 이로 인해 불필요한 작업이 발생합니다.

#### <a name="shaders"></a>셰이더

셰이더 는 GPU에서 실행되며 렌더링에서 두 가지 중요한 단계를 수행하는 작은 프로그램입니다.
1) 그려야 하는 꼭짓점 및 화면 공간의 위치 결정(꼭짓점 셰이더)
    - 꼭짓점 셰이더가 모든 메시에 대해 꼭짓점별로 실행됩니다.
2) 각 픽셀의 색 확인(픽셀 셰이더)
    - 픽셀 셰이더가 픽셀당 실행되고 기하 도형에 의해 대상 렌더링 질감으로 렌더링됩니다.

일반적으로 셰이더에서는 여러 변환 및 조명 계산을 수행합니다. 복잡한 조명 모델, 그림자 및 기타 작업은 뛰어난 결과를 생성할 수 있지만 가격도 함께 제공됩니다. 셰이더에서 계산되는 작업 수를 줄이면 프레임당 GPU에 필요한 작업을 크게 줄일 수 있습니다.

##### <a name="shader-coding-recommendations"></a>셰이더 코딩 권장 사항

- 가능하면 쌍선형 필터링 사용
- 곱하기 및 추가를 동시에 수행하도록 MAD 내재체를 사용하도록 식 다시 정렬
- CPU에서 가능한 한 많이 미리 계산하고 재질에 상수로 전달합니다.
- **픽셀 셰이더에서 꼭짓점 셰이더로 작업 이동 선호**
    - 일반적으로 꼭짓점 수는 픽셀 수보다 훨씬 작습니다(720p는 921,600픽셀, 1080p는 2,073,600픽셀 등).

#### <a name="remove-gpu-stages"></a>GPU 단계 제거

사후 처리 효과는 비용이 많이 들고 MSAA와 같은 앤티 앨리어싱 기술을 포함하여 애플리케이션의 채우기 속도를 높일 수 있습니다. HoloLens 이러한 기술과 기하 도형, 구조체 및 컴퓨팅 셰이더와 같은 추가 셰이더 단계를 사용하지 않는 것이 좋습니다.

## <a name="memory-recommendations"></a>메모리 추천 사항

과도한 메모리 할당 및 할당 취소 작업으로 인해 일관되지 않은 성능, 고정된 프레임 및 기타 유해한 동작이 발생할 수 있습니다. 메모리 관리는 가비지 수집기에서 제어되므로 Unity에서 개발할 때 메모리 고려 사항을 이해하는 것이 특히 중요합니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링 은 개체의 지속적인 할당 및 할당 취소 비용을 줄이는 인기 있는 기술입니다. 이 작업을 수행하려면 시간이 지남에 따라 개체를 지속적으로 만들고 삭제하는 대신, 동일한 개체의 대량 풀을 할당하고 이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용합니다. 개체 풀은 앱 중에 수명이 가변적인 다시 사용할 수 있는 구성 요소에 적합합니다.

## <a name="see-also"></a>추가 정보
- [Unity의 권장 성능](../unity/performance-recommendations-for-unity.md)
- [Unity 권장 설정](../unity/recommended-settings-for-unity.md)
- [Unreal을 사용하기 위한 권장 성능](../unreal/performance-recommendations-for-unreal.md)
- [Unreal의 재질 권장 사항](../unreal/unreal-materials.md)
- [3D 모델 최적화](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [실시간 3D 모델 변환 및 최적화 모범 사례](/dynamics365/mixed-reality/import-tool/best-practices)
- [Unreal의 디자이너 및 디자이너에 대한 성능 지침](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Unreal에 대한 VR 모범 사례](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)