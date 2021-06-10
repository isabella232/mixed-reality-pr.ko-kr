---
title: Unity 권장 설정
description: 프로젝트 설정을 통해 전환할 수 있는 혼합 현실 앱과 관련한 Unity의 성능 및 게시 동작에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity, 설정, 혼합 현실, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 성능, 품질 설정, 조명 설정, 깊이 버퍼, xr, 손실 추적
ms.openlocfilehash: 7516ec89c49a12e7cb143d7e53d00efde0e44c4e
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743382"
---
# <a name="recommended-settings-for-unity"></a>Unity 권장 설정

Unity는 일반적으로 모든 플랫폼의 평균 사례인 기본 옵션 집합을 제공합니다. 그러나 Unity는 프로젝트 설정을 통해 전환할 수 있는 혼합 현실과 관련한 몇 가지 동작을 제공합니다.

## <a name="performant-environment-set-up"></a>수행 환경 설정

### <a name="low-quality-settings"></a>낮은 품질 설정

애플리케이션이 실행되고 적절한 프레임 속도, 특히 HoloLens 개발에서 잘 수행되도록 **Unity 품질 설정을** 매우 **낮음으로** 수정하는 것이 중요합니다. 몰입형 헤드셋을 개발하기 위해 VR 환경을 구동하는 데스크톱의 사양에 따라 가장 낮은 품질 매개 변수 없이도 프레임 속도도 얻을 수 있습니다.

Unity 2019 LTS+에서는 프로젝트 설정 품질 **편집으로** 이동한 후 아래쪽  >    >   화살표를 클릭하여 **기본값을** **매우 낮은 품질 수준으로 설정하여 프로젝트의 품질 수준을 설정할 수 있습니다.

### <a name="lighting-settings"></a>조명 설정

품질 장면 설정과 마찬가지로 Mixed Reality 애플리케이션에 대한 최적의 조명 설정을 설정하는 것이 중요합니다. Unity에서 일반적으로 장면에 가장 큰 성능 영향을 주는 조명 설정은 **Realtime Global Illumination** 입니다. **창** 렌더링 조명 설정 실시간 전역 조명 으로 가서 전역 조명을 끌 수  >    >    >  **있습니다.**

또 다른 조명 설정인 **굽은 전역 조명이 있습니다.** 이 설정은 몰입형 헤드셋에서 시각적으로 눈에 잘 띄는 결과를 제공할 수 있지만 HoloLens 개발에는 적용되지 않습니다. **베이킹된 글로벌 조명은** 알 수 없고 변화하는 환경의 특성으로 인해 HoloLens 장면에서 찾을 수 없는 정적 GameObjects에 대해서만 계산됩니다.

자세한 내용은 [Unity의 전역 조명을](https://docs.unity3d.com/Manual/GIIntro.html) 참조하세요. 

>[!NOTE]
> **실시간 글로벌 조명은** **장면별로** 설정되므로 개발자는 프로젝트의 모든 Unity 장면에 대해 이 속성을 저장해야 합니다.

### <a name="single-pass-instancing-rendering-path"></a>단일 패스 인탄싱 렌더링 경로

Mixed Reality 애플리케이션에서 장면은 사용자에게 각 시선에 대해 한 번씩 두 번 렌더링됩니다. 기존 3D 개발과 비교하여 계산해야 하는 작업의 양을 효과적으로 두 배로 늘린 것입니다. CPU 및 GPU 시간을 모두 절약하려면 Unity에서 가장 효율적인 렌더링 경로를 선택하는 것이 중요합니다. 단일 패스 인스턴스 렌더링은 Mixed Reality 앱에 대한 Unity 렌더링 파이프라인을 최적화하며, 모든 프로젝트에 대해 기본적으로 이 설정을 사용하도록 설정하는 것이 좋습니다.

Unity 프로젝트에서 이 기능을 사용하도록 설정하려면 다음을 수행합니다.

1)  **플레이어 XR 설정** 을 엽니다(**편집** > **프로젝트 설정** > **플레이어** > **XR 설정** 으로 차례로 이동).
2) **스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스화됨** 을 선택합니다(**가상 현실 지원됨** 확인란을 선택해야 함).

이 렌더링 접근 방식에 대한 자세한 내용은 Unity에서 다음 문서를 참조하세요.

- [고급 스테레오 렌더링을 사용하여 AR 및 VR 성능을 최대화하는 방법](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [단일 패스 인스턴스화](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 인스턴스화된 단일 패스 렌더링의 일반적인 문제 중 하나는 개발자에게 인스턴스화에 맞게 작성되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우에 발생합니다. 이 기능을 사용하도록 설정하면 개발자가 일부 GameObjects를 한쪽 눈에만 렌더링한다는 것을 알 수 있습니다. 이는 인스턴스화에 적절한 속성이 연결된 사용자 지정 셰이더에 없기 때문입니다.
>
> 이 문제를 해결하는 방법은 Unity의 [HoloLens에 대한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)을 참조하세요.

### <a name="enable-depth-buffer-sharing"></a>깊이 버퍼 공유 사용

사용자 인식에서 홀로그램 안정성을 향상하려면 Unity에서 **깊이 버퍼 공유** 속성을 사용하도록 설정하는 것이 좋습니다. 이를 켜면 Unity는 애플리케이션에서 생성된 깊이 맵을 Windows Mixed Reality 플랫폼과 공유합니다. 그러면 플랫폼은 특히 애플리케이션에서 렌더링되는 지정된 프레임의 장면에 맞게 홀로그램 안정성을 더 잘 최적화할 수 있습니다.

Unity 프로젝트에서 이 기능을 사용하도록 설정하려면 다음을 수행합니다.

1) **플레이어 XR 설정** 을 엽니다(**편집** > **프로젝트 설정** > **플레이어** > **XR 설정** 으로 차례로 이동).
2) **가상 현실 SDK** Windows Mixed Reality 확장에서 **깊이 버퍼 공유 사용**  >   확인란을 선택합니다( Virtual **Reality 지원** 확인란을 선택해야 합니다.)

또한 특히 HoloLens 개발의 경우 이 패널의 **깊이 형식** 설정에서 **16비트 깊이를** 선택하는 것이 좋습니다. 24비트와 비교하여 16비트 를 선택하면 이동/처리해야 하는 데이터가 줄어들기 때문에 대역폭 요구 사항이 크게 줄어듭니다.

Windows Mixed Reality 플랫폼이 홀로그램 안정성을 최적화하기 위해 깊이 버퍼를 사용하여 정확하고 화면에 렌더링된 홀로그램과 일치합니다. 따라서 깊이 버퍼를 공유하는 경우 색을 렌더링할 때 깊이도 렌더링하는 것이 중요합니다. Unity에서 대부분의 불투명 또는 TransparentCutout 재질은 기본적으로 깊이를 렌더링하지만 투명하고 텍스트 개체는 셰이더에 종속되어 있지만 깊이를 렌더링하지 않습니다.

[Mixed Reality 도구 키트 표준 셰이더](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)를 사용하는 경우 투명 개체의 깊이를 렌더링하려면 다음을 수행합니다.

1) MRTK 표준 셰이더를 사용하는 투명 재질을 선택하고 검사기 편집기 창을 엽니다.
2) 깊이 버퍼 공유 경고 내에서 **지금 수정** 단추를 선택합니다. **렌더링 모드를** 사용자 지정 로 설정하여 수동으로 수행할 수도 **있습니다.** 그런 다음 **모드를** **투명으로** 설정하고 마지막으로 **깊이 쓰기를** **켜기로** 설정합니다.

> [!IMPORTANT]
> 개발자는 카메라의 가까운/원거리 평면 설정과 함께 이러한 값을 변경할 때 Z-fighting을 주의해야 합니다. Z-Fighting은 두 gameobject가 동일한 픽셀로 렌더링하려고 할 때 깊이 버퍼의 충실도 제한(즉, z depth) Unity는 어떤 개체가 다른 개체 앞에 있는지 파악할 수 없습니다. 개발자는 동일한 z-깊이 값을 위해 두 게임 개체가 깜박이는 *것을* 확인할 수 있습니다. 카메라에서 z 깊이에 대해 계산할 각 개체에 대해 더 큰 값 범위가 있기 때문에 24비트 깊이 형식으로 전환하여 이 문제를 해결할 수 있습니다.
>
> 그러나 특히 HoloLens 개발의 경우 카메라의 근거리 및 원거리 평면을 더 작은 범위로 수정하고 16비트 깊이 형식을 유지하는 것이 좋습니다. z 깊이는 근거리 및 원거리 카메라 평면을 따라 값 범위에 비선형으로 매핑됩니다. 장면에서 *주 카메라를* 선택하고 **검사기에서** **근거리 & 원거리 클리핑 평면** 값을 변경하여 범위를 줄이면 수정할 수 있습니다(예: 1000m에서 100m 또는 기타 x 값 등)

>[!IMPORTANT]
> Unity는 16비트 깊이 형식을 사용하는 경우 [스텐실 버퍼를 만들지 않습니다.](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 따라서 8비트 스텐실 버퍼 를 만드는 24비트 깊이 형식을 선택하지 않으면 일부 Unity UI 효과 및 [기타 스텐실](https://docs.unity3d.com/Manual/SL-Stencil.html)필수 효과가 작동하지 않습니다.

### <a name="building-for-il2cpp"></a>IL2CPP용 빌드

Unity는 .NET 스크립팅 백 엔드에 대한 지원이 더 이상 사용되지 않으므로 개발자가 UWP Visual Studio 빌드에 **IL2CPP를** 활용하는 것이 좋습니다. 이렇게 하면 다양한 이점이 있지만 **IL2CPP용** Unity에서 Visual Studio 솔루션을 빌드하는 것이 이전 .NET 메서드보다 느릴 수 있습니다. 따라서 개발 반복 시간을 절약하기 위해 **IL2CPP를** 빌드하는 모범 사례를 따르는 것이 좋습니다.

1) 매번 동일한 디렉터리에 프로젝트를 빌드하고 미리 빌드된 파일을 다시 사용하여 증분 빌드 활용
2) 프로젝트 & 빌드 폴더에 대한 맬웨어 방지 소프트웨어 검색 사용 안 함
   - Windows 10 설정 앱에서 바이러스 & **위협 방지** 열기
   - 바이러스 & **위협 방지 설정에서 설정** **관리를** 선택합니다.
   - 제외 섹션에서 **제외 추가 또는 제거를** **선택합니다.**
   - **제외 추가를** 선택하고 Unity 프로젝트 코드 및 빌드 출력이 포함된 폴더를 선택합니다.
3) 빌드에 SSD 사용

자세한 내용은 [IL2CPP에 대한 빌드 시간 최적화를](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 참조하세요.

> [!NOTE]
> 또한 대용량 자산(스크립트 파일 제외) 또는 지속적으로 변화하는 장면/자산을 포함하는 Unity 프로젝트에 맞게 [캐시 서버](https://docs.unity3d.com/Manual/CacheServer.html)를 설정하는 것도 유용할 수 있습니다. 프로젝트를 열 때 Unity는 정식 자산을 개발자 컴퓨터에 내부 캐시 형식으로 저장합니다. 따라서 항목이 수정되면 다시 가져온 후 다시 처리해야 합니다. 모든 개발자가 새 변경 내용을 로컬로 다시 가져오지 않고, 이 프로세스를 한 번 수행한 후 캐시 서버에 저장하고, 이후에 다른 개발자와 공유할 수 있으므로 시간을 절약할 수 있습니다.

## <a name="publishing-properties"></a>게시 속성

### <a name="holographic-splash-screen"></a>홀로그램 시작 화면

HoloLens에는 모바일 클래스 CPU 및 GPU가 있습니다. 즉, 앱을 로드하는 데 시간이 좀 더 걸릴 수 있습니다. 앱이 로드되는 동안 사용자는 검은색만 표시되므로 어떤 일이 진행되는지 궁금할 수 있습니다. 로드하는 동안 이를 확인할 수 있도록 홀로그램 시작 화면을 추가할 수 있습니다.

홀로그램 시작 화면을 전환하려면 다음을 수행합니다.

1) 프로젝트 설정 **플레이어 편집**  >    >   페이지로 이동합니다.
2) Windows **스토어** 탭을 선택하고 **시작 이미지** 섹션을 엽니다.
3) **Windows Holographic > Holographic Splash Image** 속성 아래에 이미지를 적용합니다.
    - Unity 시작 **화면 표시** 옵션을 설정/해제하면 Unity 브랜드 시작 화면이 활성화되거나 비활성화됩니다. Unity Pro 라이선스가 없는 경우 Unity 브랜드 시작 화면이 항상 표시됩니다.
    - **홀로그램 시작 이미지가** 적용되는 경우 Unity 시작 화면 표시 확인란을 사용할지 여부를 선택하면 항상 표시됩니다. 사용자 지정 홀로그램 시작 이미지를 지정하는 것은 Unity Pro 라이선스가 있는 개발자만 사용할 수 있습니다.

|  Unity 시작 화면 표시  |  홀로그램 시작 이미지  |  동작 |
|----------|----------|----------|
|  켜기  |  없음  |  5초 동안 또는 앱이 로드될 때까지(더 긴 경우) 기본 Unity 시작 화면을 표시합니다. |
|  켜기  |  사용자 지정  |  5초 동안 또는 앱이 로드될 때까지(어느 것이 더 긴지) 사용자 지정 시작 화면을 표시합니다. |
|  끄기  |  없음  |  앱이 로드 될 때까지 투명 한 검정색 (없음)을 표시 합니다. |
|  끄기  |  사용자 지정  |  5 초 동안 또는 앱이 로드 될 때까지 사용자 지정 시작 화면을 표시 합니다. |

자세한 내용은 [Unity의 시작 화면 설명서](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) 를 참조 하세요.

### <a name="tracking-loss"></a>추적 손실

혼합 현실 헤드셋은 [전 세계에서 잠긴 좌표계](coordinate-systems-in-unity.md)를 구성 하는 환경에 따라 holograms 위치를 유지할 수 있습니다. 헤드셋이 세계에서 자신을 찾을 수 없는 경우 헤드셋은 *추적을 잃어버린* 것으로 간주 됩니다. 이러한 경우 공간 단계, 공간 앵커 및 공간 매핑과 같은 세계에서 잠긴 좌표계에 의존 하는 기능은 작동 하지 않습니다.

추적 손실이 발생 하는 경우 Unity의 기본 동작은 holograms 렌더링을 중지 하 고, [게임 루프](https://docs.unity3d.com/Manual/ExecutionOrder.html)를 일시 중지 하 고, 사용자가 응시 하는 추적 손실 알림을 표시 하는 것입니다. 사용자 지정 알림은 추적 손실 이미지 형식으로 제공 될 수도 있습니다. 전체 환경에 대 한 추적에 의존 하는 앱의 경우에는 추적이 다시 확보 될 때까지 Unity에서이를 완전히 처리할 수 있습니다. 개발자는 추적 손실을 추적 하는 동안 표시할 사용자 지정 이미지를 제공할 수 있습니다.

손실 된 추적 이미지를 사용자 지정 하려면:

1)   >  **프로젝트 설정** 편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭에서을 선택 하 고 **시작 이미지** 섹션을 엽니다.
3) **Windows Holographic > 추적 손실 이미지** 속성 아래에 이미지를 적용 합니다.

#### <a name="opt-out-of-automatic-pause"></a>자동 일시 중지 옵트아웃

일부 앱은 추적을 요구 하지 않을 수 있습니다 (예: 360도 비디오 뷰어 등의 [방향 전용 앱](coordinate-systems-in-unity.md) ). 추적이 손실 되는 동안 중단 없이 처리를 계속 해야 할 수도 있습니다. 추적 동작의 기본 손실을 옵트아웃 (opt out) 할 수 있지만 추적 손실 시나리오에서 제대로 렌더링 되지 않는 개체를 숨기 거 나 비활성화할 책임이 있습니다. 대부분의 경우이 경우에 렌더링 하는 데 권장 되는 콘텐츠는 주 카메라를 중심으로 하는 본문 잠금 콘텐츠입니다.

자동 일시 중지 동작을 옵트아웃 하려면:

1)   >  **프로젝트 설정** 편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 선택 하 고 **시작 이미지** 섹션을 엽니다.
3) **Holographic 일시 중지 및 이미지 표시** 확인란을 선택 하 여 Windows >를 수정 합니다.

#### <a name="tracking-loss-events"></a>손실 이벤트 추적

추적이 손실 될 때 사용자 지정 동작을 정의 하려면 전역 [추적 손실 이벤트](tracking-loss-in-unity.md)를 처리 합니다.

### <a name="capabilities"></a>기능

앱이 특정 기능을 활용 하려면 해당 매니페스트에 적절 한 기능을 선언 해야 합니다. 매니페스트 선언은 Unity에서 수행할 수 있으므로 이후의 모든 프로젝트 내보내기에 포함 됩니다.

다음을 수행 하 여 혼합 현실 응용 프로그램에 기능을 사용 하도록 설정할 수 있습니다.

1)   >  **프로젝트 설정** 편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 선택 하 고, **게시 설정** 섹션을 열고, **기능** 목록을 찾습니다.

Holographic apps에 일반적으로 사용 되는 Api를 사용 하도록 설정 하는 데 적용 되는 기능은 다음과 같습니다.
<br>

|  기능  |  기능을 필요로 하는 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  웹캠  |  사진 캡처 및 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우) |
|  마이크  |  VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (및 Unity 프로파일러를 사용 하려면) |

## <a name="see-also"></a>참조

* [Unity 개발 개요](unity-development-overview.md)
* [혼합 현실의 성능 이해](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)