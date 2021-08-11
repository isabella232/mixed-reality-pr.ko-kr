---
title: OpenXR 모범 사례
description: OpenXR 애플리케이션의 시각적 품질, 안정성 및 성능에 대한 모범 사례를 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 모범 사례, 성능, 품질, 안정성
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207851"
---
# <a name="openxr-app-best-practices"></a>OpenXR 앱 모범 사례

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp의</a>OpenXRProgram.cpp 파일에서 아래 모범 사례의 예를 볼 수 있습니다. 시작 부분에 있는 Run() 함수는 초기화에서 이벤트 및 렌더링 루프까지 일반적인 OpenXR 앱 코드 흐름을 캡처합니다.

## <a name="best-practices-for-visual-quality-and-stability"></a>시각적 품질 및 안정성에 대한 모범 사례

이 섹션의 모범 사례에서는 OpenXR 애플리케이션에서 최상의 시각적 품질과 안정성을 얻는 방법을 설명합니다.

HoloLens 2 관련 추가 성능 권장 사항은 아래 HoloLens 2 [성능 모범 사례 섹션을](#best-practices-for-performance-on-hololens-2) 참조하세요.

### <a name="gamma-correct-rendering"></a>감마 올바른 렌더링

렌더링 파이프라인이 감마 올바른지 확인하려면 주의해야 합니다. 스왑 체인으로 렌더링할 때 렌더링 대상 뷰 형식은 스왑 체인 형식과 일치해야 합니다. 예를 들어 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 스왑 체인 형식과 렌더링 대상 뷰 모두에 대해 입니다.
앱의 렌더링 파이프라인이 셰이더 코드에서 수동 sRGB 변환을 수행하는 경우 예외가 있습니다. 앱은 sRGB 스왑 체인 형식을 요청해야 하지만 렌더링 대상 보기에 선형 형식을 사용합니다. 예를 들어 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 를 스왑 체인 형식으로 요청하지만 를 렌더링 대상 보기로 사용하여 `DXGI_FORMAT_B8G8R8A8_UNORM` 콘텐츠가 이중 감마로 수정되지 않도록 합니다.

### <a name="submit-depth-buffer-for-projection-layers"></a>프로젝션 계층에 대한 깊이 버퍼 제출

프레임을 에 제출할 때는 항상 확장을 사용하고 `XR_KHR_composition_layer_depth` 깊이 버퍼를 프로젝션 계층과 함께 `xrEndFrame` 제출합니다.
HoloLens 2 하드웨어 깊이 다시 프로젝션을 사용하도록 설정하면 홀로그램 안정성이 향상됩니다.

### <a name="choose-a-reasonable-depth-range"></a>적절한 깊이 범위 선택

HoloLens 홀로그램 안정성을 위해 가상 콘텐츠의 범위를 좁히려면 더 좁은 깊이 범위를 선호합니다.
예를 들어 OpenXrProgram.cpp 샘플은 0.1m~20m를 사용하고 있습니다.
더 균일한 깊이 해상도를 위해 [역동기-Z를](https://developer.nvidia.com/content/depth-precision-visualized) 사용합니다.
16비트 깊이 `DXGI_FORMAT_D16_UNORM` 버퍼는 24비트 깊이 버퍼보다 깊이 해상도가 낮지만 HoloLens 2 기본 설정 깊이 형식을 사용하면 프레임 속도와 성능을 향상하는 데 도움이 됩니다.
깊이 해상도를 최대한 활용하기 위해 이러한 모범 사례를 따르는 것이 더 중요합니다.

### <a name="prepare-for-different-environment-blend-modes"></a>다양한 환경 혼합 모드 준비

애플리케이션이 전 세계를 완전히 차단하는 몰입형 헤드셋에서도 실행되는 경우 API를 사용하여 지원되는 환경 혼합 모드를 `xrEnumerateEnvironmentBlendModes` 열거하고 렌더링 콘텐츠를 올바르게 준비해야 합니다.
예를 들어 HoloLens 같은 시스템을 사용하는 경우 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 앱은 투명한 색으로 사용해야 하고, 가 있는 시스템의 경우 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` 앱은 불투명 색 또는 일부 가상 공간을 배경에 렌더링해야 합니다.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>애플리케이션의 루트 공간으로 무제한 참조 공간 선택

애플리케이션은 일반적으로 보기, 작업 및 홀로그램을 함께 연결하는 일부 루트 세계 좌표 공간을 설정합니다.
확장이 지원되는 경우 를 사용하여 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` [세계적 좌표계를](../../design/coordinate-systems.md#building-a-world-scale-experience)설정함으로써 앱이 시작되는 위치에서 사용자가 멀리 이동할 때 원치 않는 홀로그램 드리프트를 방지할 수 있습니다(예: 5미터).
`XR_REFERENCE_SPACE_TYPE_LOCAL`무제한 공간 확장이 없는 경우 대체(fallback)로 사용합니다.

### <a name="associate-hologram-with-spatial-anchor"></a>홀로그램을 공간 앵커와 연결

제한 없는 참조 공간을 사용하는 경우 해당 참조 공간에 직접 배치하는 홀로그램은 [사용자가 멀리 떨어진 방으로 이동한 다음 다시 돌아올 때 드리프트될 수 있습니다.](../../design/coordinate-systems.md#building-a-world-scale-experience)
홀로그램 사용자가 전 세계의 개별 위치에 배치하는 경우 확장 함수를 사용하여 [공간 앵커를 만들고](../../design/spatial-anchors.md#best-practices) `xrCreateSpatialAnchorSpaceMSFT` 홀로그램을 원점 위치에 배치합니다. 시간이 지남에 따라 홀로그램을 독립적으로 안정적으로 유지합니다.

### <a name="support-mixed-reality-capture"></a>혼합 현실 캡처 지원

HoloLens 2 기본 디스플레이는 가감 환경 혼합을 사용하지만 사용자가 [혼합 현실 캡처를](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)시작할 때 앱의 렌더링 콘텐츠는 환경 비디오 스트림과 알파 혼합됩니다.
혼합 현실 캡처 비디오에서 최상의 시각적 품질을 얻으려면 프로젝션 계층의 에서 를 설정하는 것이 가장 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` `layerFlags` 좋습니다.

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 성능에 대한 모범 사례

하드웨어 다시 프로젝션을 지원하는 모바일 디바이스인 HoloLens 2 최적의 성능을 위해 더 엄격한 요구 사항이 있습니다.  컴퍼지션 데이터를 제출하는 방법에는 여러 가지가 있으며, 이로 인해 성능 저하가 두드러진 후처리가 발생합니다.

### <a name="select-a-swapchain-format"></a>스왑 체인 형식 선택

항상 를 사용하여 지원되는 픽셀 형식을 `xrEnumerateSwapchainFormats` 열거하고 앱이 지원하는 런타임에서 첫 번째 색 및 깊이 픽셀 형식을 선택합니다. 런타임에서 최적의 성능을 위해 선호하기 때문입니다. HoloLens 2 및 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 는 일반적으로 `DXGI_FORMAT_D16_UNORM` 렌더링 성능을 향상하기 위한 첫 번째 선택입니다. 이 기본 설정은 24비트 깊이 버퍼가 성능에 미치는 영향이 적은 데스크톱 PC에서 실행되는 VR 헤드셋에서 다를 수 있습니다.
  
**성능 경고:** 기본 스왑 체인 색 형식 이외의 형식을 사용하면 런타임 후처리가 발생하며, 이로 인해 성능이 크게 저하됩니다.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>권장 렌더링 매개 변수 및 프레임 타이밍을 통해 렌더링

항상 권장 보기 구성 너비/높이( `recommendedImageRectWidth` 및 `recommendedImageRectHeight` )를 `XrViewConfigurationView` 사용하여 렌더링하고 항상 `xrLocateViews` API를 사용하여 렌더링하기 전에 권장되는 보기 자세, FOV 및 기타 렌더링 매개 변수를 쿼리합니다.
`XrFrameEndInfo.predictedDisplayTime`자세 및 보기를 쿼리할 때는 항상 최신 `xrWaitFrame` 호출의 를 사용합니다.
이렇게 하면 HoloLens 렌더링을 조정하고 HoloLens 않은 사람의 시각적 품질을 최적화할 수 있습니다.

### <a name="use-a-single-projection-layer"></a>단일 프로젝션 계층 사용

HoloLens 2 콘텐츠 렌더링을 위한 GPU 성능과 단일 프로젝션 계층에 최적화된 하드웨어 Compositor가 있습니다.
항상 단일 프로젝션 계층을 사용하면 애플리케이션의 프레임 속도, 홀로그램 안정성 및 시각적 품질에 도움이 될 수 있습니다.  
  
**성능 경고:** 단일 보호 계층을 제외한 모든 것을 제출하면 런타임 후처리가 발생하며, 이로 인해 성능이 크게 저하됩니다.

### <a name="render-with-texture-array-and-vprt"></a>질감 배열 및 VPRT를 통해 렌더링

색 `xrSwapchain` 교환 체인에 을 사용하고 깊이를 위해 하나를 사용하여 왼쪽 및 오른쪽 눈 둘 `arraySize=2` 다에 대해 하나를 만듭니다.
왼쪽 눈은 조각 0으로, 오른쪽 눈은 조각 1로 렌더링합니다.
VPRT와 함께 셰이더를 사용하고 스테레오 범위 렌더링을 위해 인스턴스화된 그리기 호출을 사용하여 GPU 부하를 최소화합니다.
이렇게 하면 런타임의 최적화를 통해 HoloLens 2 최상의 성능을 얻을 수 있습니다.
이중 와이드 렌더링 또는 눈당 별도의 스왑 체인과 같은 질감 배열을 사용하는 대신 런타임 후처리가 발생하여 성능이 크게 저하됩니다.

### <a name="avoid-quad-layers"></a>쿼드 계층 방지

를 사용하여 쿼드 계층을 컴퍼지션 계층으로 제출하는 대신 `XrCompositionLayerQuad` 쿼드 콘텐츠를 프로젝션 스왑 체인에 직접 렌더링합니다.

**성능 경고:** 쿼드 계층과 같은 단일 프로젝션 계층을 초과하는 추가 계층을 제공하면 런타임 후처리가 발생하며 이로 인해 성능이 크게 저하됩니다.