---
title: 품질 기본 사항
description: 혼합 현실 애플리케이션 디자인의 품질 기본 사항 에 대해 알아봅니다.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: 품질 기본 사항, 사례 연구, 프로젝트, 샘플, MRTK, Mixed Reality Toolkit, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647534"
---
# <a name="quality-fundamentals"></a>품질 기본 사항

품질 기본 사항 은 훌륭한 혼합 현실 환경을 구축하는 기본을 보여 주는 HoloLens 2 앱입니다.  혼합 현실에서 품질 문제를 학습하고 읽는 대신, 이제 앱에서 제공하는 옵션을 선택하여 일반적인 환경, 디자인 및 성능 문제 및 솔루션을 직접 경험할 수 있습니다.

앱을 다운로드하고 설치하려면 앱 다운로드 페이지로 이동합니다.

> [!div class="nextstepaction"]
> [품질 기본 사항](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![품질 기본 사항 홈페이지](images\qf-homepage.jpg)

이 샘플 앱에서는 다음을 알아봅니다.

>[!div class = "checklist"]
> * [디바이스 I/O 및 환경:](#device-io-and-environment)환경 요소가 HoloLens 성능에 미치는 영향
> * [Spatial Anchors:](#anchor-fundamentals)공간 앵커를 사용하여 홀로그램을 실제 공간에 맞추는 방법입니다.
> * [홀로그램 안정성 및 충실도:](#stability-and-fidelity)홀로그램스 안정성과 충실도를 개선하는 데 도움이 되는 기술을 살펴봅니다.
> * [3D 자산 기본 사항:](#3d-asset-fundamentals)높은 시각적 충실도를 유지하기 위해 3D 자산을 최적화하는 방법입니다. 

## <a name="device-io-and-environment"></a>디바이스 I/O 및 환경

HoloLens 품질 기본 사항 앱을 시작합니다. 앱의 홈페이지가 나타나면 **디바이스 I/O 및 환경을** 선택합니다.  HoloLens 센서와 주변 환경이 공간 매핑, 추적 및 홀로그램 배치에 어떤 영향을 주는지 살펴보겠습니다. 

### <a name="surfaces"></a>Surfaces

미러된 완료가 있는 미러 또는 표면은 개체의 모양에 대해 HoloLens 센서를 혼동할 수 있습니다.  화면에 반영된 개체는 디바이스에서 환경 변경으로 해석될 수 있으며, 이로 인해 디바이스 추적이 손실될 수 있습니다.  미러된 표면으로 인해 HoloLens 문제가 발생하는 경우 화면 또는 복제 가능한 시각 장애가 추가되는 것이 좋습니다.

자세한 내용은 환경 고려 [사항 HoloLens 공간의 표면을](/hololens/hololens-environment-considerations#surfaces-in-a-space) [참조하세요.](/hololens/hololens-environment-considerations)

### <a name="lighting"></a>조명

HoloLens 성능은 매우 낮거나 매우 밝은 조명 조건의 영향을 받을 수 있습니다.  HoloLens 추적 센서는 최적으로 작동하려면 약 500-1000개의 광원을 필요로 합니다. metmeter 또는 모바일 앱을 사용하여 공간의 광원 양을 측정할 수 있습니다.

자세한 내용은 HoloLens 환경의 [조명](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) [고려 사항을 참조하세요.](/hololens/hololens-environment-considerations)

## <a name="anchor-fundamentals"></a>앵커 기본 사항

Spatial Anchors 사용하여 홀로그램을 물리적 공간에 맞추는 방법을 알아보려면 앱 홈페이지에서 **앵커 자금** 조정을 선택합니다.

앱의 이 부분에서는 다음과 같은 사용자 시나리오를 살펴봅니다.

>[!div class = "checklist"]
> * 개체에 앵커를 적용하지 않을 때 발생하는 일입니다.
> * 개체 그룹에 여러 Spatial Anchors 사용하는 경우
> * QR 코드를 사용하여 여러 협력자 간에 Spatial Anchor 공유
> * 공간에서 매우 큰 개체에 대한 앵커 배치입니다.

자세한 내용은 [Mixed Reality](../../design/spatial-anchors.md) 설명서의 [Spatial Anchors](../../design/spatial-anchors.md) 참조하세요.

## <a name="stability-and-fidelity"></a>안정성 및 충실도

애플리케이션의 홈페이지에서 안정성 **및 충실도를** 선택하여 홀로그램 안정성을 개선하는 방법을 살펴봅니다.

다음과 같은 주요 개념을 살펴보겠습니다.

>[!div class = "checklist"]
> * [프레임 속도](#frame-rate)입니다.
> * [LSR(Late Stage reprojection)](#late-stage-reprojection-lsr).
> * [Z-fighting .](#z-fighting)
> * [앤티 앨리어싱.](#anti-aliasing)

### <a name="frame-rate"></a>프레임 속도

가능한 최상의 홀로그램 환경을 제공하려면 애플리케이션 개발자가 FPS(초당 60프레임)를 유지 관리해야 합니다.  앱의 이 부분에서는 다양한 삼각형 개수 옵션을 전환하여 다양한 프레임 속도의 차이를 경험합니다.

![삼각형 개수 최적화](images\qf-triangle-count-optimization.png)

자세한 내용은 [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md) 문서의 [프레임 속도를](../platform-capabilities-and-apis/hologram-stability.md#frame-rate) 참조하세요.

### <a name="late-stage-reprojection-lsr"></a>LSR(Late Stage reprojection)

다시 프로젝션은 사용자가 공간을 이동할 때 홀로그램을 안정화하는 데 사용됩니다.  홀로그램 품질 차이를 확인하려면 앱의 이 부분에서 제공하는 다양한 다시 프로젝션 옵션을 사용해 보세요.

![다른 다시 프로젝션 옵션을 사용하여 차이를 경험해 보세요.](images\qf-lsr-modes.jpg)

자세한 내용은 [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md) 문서의 [다시 프로젝션을](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 참조하세요.

### <a name="z-fighting"></a>z-fighting

Z-fighting은 혼합 현실 애플리케이션이 다른 개체 앞에 있는 개체를 파악할 수 없는 경우에 발생합니다.  홀로그램 개체가 동일한 z-깊이 값을 사용할 때 깜박이는 것을 볼 수 있습니다.  이 경우 자전거의 로고인 홀로그램 개체의 배치를 변경하여 앱에서 z-fighting의 효과를 경험해 보세요.

![개체 배치를 통해 z-fighting을 경험해보세요.](images\qf-z-fighting.jpg)

z-fighting에 대한 자세한 내용은 [Unity의 권장 설정](./recommended-settings-for-unity.md) 문서에서 [깊이 버퍼 공유 사용을](./recommended-settings-for-unity.md#enable-depth-buffer-sharing) 참조하세요.

### <a name="anti-aliasing"></a>앤티 앨리어싱

앤티 앨리어싱은 홀로그램의 곡선 및 대각선에서 가변 가장자리를 평활하는 데 사용되는 기술입니다.  앱의 이 부분에서는 표시된 텍스트 및 자전거 스포크에서 별칭이 미치는 영향을 경험합니다.  

## <a name="3d-asset-fundamentals"></a>3D 자산 기본 사항

애플리케이션의 홈페이지에서 **3D 자산 기본 사항을** 선택하여 높은 시각적 충실도를 유지하면서 프레임 속도 요구 사항을 충족하도록 3D 자산을 최적화하는 방법을 살펴봅니다.

다음과 같은 주요 개념을 살펴보겠습니다.

>[!div class = "checklist"]
> * [삼각형 개수입니다.](#triangle-count)
> * [셰이더가 를 전달합니다.](#shader-passes)
> * [그리기 호출](#draw-calls)입니다.
> * [을(를) 하십시오.](#finale)

### <a name="triangle-count"></a>삼각형 개수

자전거 모델의 수와 복잡성을 선택하여 FPS에 따라 시각적 차이를 경험합니다.

![프레임 속도에 미치는 영향을 보려면 다른 삼각형 개수 옵션을 선택합니다.](images\qf-3d-asset-visible-triangles.jpg)

자세한 내용은 [자산 만들기 프로세스를 참조하세요.](../../design/asset-creation-process.md)

### <a name="shader-passes"></a>셰이더 패스

자전거 수와 다양한 셰이더 옵션을 선택하여 FPS에 따라 시각적 차이를 경험합니다.

![프레임 속도에 미치는 영향을 보려면 다른 셰이더 옵션을 선택합니다.](images\qf-3d-asset-shader-complexity.jpg)

자세한 내용은 [MRTK 표준 셰이더 를 참조하세요.](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

### <a name="draw-calls"></a>그리기 호출

그리기 호출은 그래픽 카드에 대한 리소스 집약적 호출입니다.  그리기 호출 수가 FPS에 영향을 주기 때문에 앱의 이 부분에서 시각적 차이를 직접 경험해보세요.

![그리기 호출은 성능을 향상시키기 위해 최적화되어야 합니다.](images\qf-3d-asset-draw-calls.jpg)

[CPU-GPU 성능 권장 사항을 참조하세요.](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>피날레

여기서는 표시할 수 있는 완전히 최적화된 자전거의 수와 최적화 기술을 고려할 때 가능한 충실도 수준을 살펴볼 수 있습니다.

![사용되는 최적화 기술입니다.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>다음 단계

다른 혼합 현실 샘플 시나리오 살펴보기:

   > [!div class="nextstepaction"]
   > [샘플 및 기능 앱](../features-and-samples.md)