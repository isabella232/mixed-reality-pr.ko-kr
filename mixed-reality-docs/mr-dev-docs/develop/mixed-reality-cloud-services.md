---
layout: LandingPage
title: Azure Cloud Services
description: 혼합 현실 클라우드 서비스 리소스
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 개발, 개발, HoloLens, 클라우드 서비스, Azure, remote rendering, spatial anchors, cognitive services, 인식, unity, 기계 학습, 음성 번역, 컴퓨터 비전, Microsoft Graph
ms.openlocfilehash: 640e99637f9cfa1786e1e78ed5cec396748b2f47
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679692"
---
# <a name="azure-cloud-services"></a>Azure Cloud Services

![ Azure Spatial Anchors 이미지](../design/images/AzureSpatialAnchors.jpg)

모든 사람이 주변의 3차원 실제 세계에서 Azure 혼합 현실 서비스를 사용하는 숙련된 전문가임을 보여 줍니다. 사용자가 자신의 작업과 세계의 컨텍스트 내에서 디지털 정보를 캡처하고 표시하여 더 효과적으로 만들고, 학습하고, 협업할 수 있도록 지원합니다. 3D를 모바일 디바이스, 헤드셋 및 기타 테더링되지 않은 디바이스에 가져옵니다. Azure를 사용하면 가장 중요한 정보가 보호되도록 할 수 있습니다.

## <a name="mixed-reality-services"></a>Mixed Reality 서비스

**Azure Remote Rendering** 및 **Azure Spatial Anchors** 와 같은 Mixed Reality 클라우드 서비스는 개발자가 다양한 플랫폼에서 매력적인 몰입형 경험을 빌드할 수 있도록 도와줍니다. 이러한 서비스를 사용하면 사용자 환경의 컨텍스트에서 3D 학습, 예측 장비 유지 관리 및 디자인 검토를 위한 애플리케이션을 만들 때 공간 인식을 프로젝트에 통합할 수 있습니다.

### <a name="azure-remote-rendering"></a>Azure Remote Rendering
ARR(Azure Remote Rendering)은 매우 복잡한 3D 모델을 실시간으로 렌더링하고 디바이스로 스트리밍할 수 있는 서비스입니다. ARR은 현재 공개 미리 보기 상태이며, HoloLens 2 또는 Windows 데스크톱 PC를 대상으로 하는 Unity 또는 네이티브 C++ 프로젝트에 추가할 수 있습니다.

![ 원격 렌더링 이미지](../design/images/RemoteRendering.jpg)

계산 렌더링 성능이 낮으므로 ARR은 테더링되지 않은 디바이스에서 실행되는 모든 Mixed Reality 애플리케이션의 필수 구성 요소입니다. 다음과 같은 병렬 엔진 모델 비교를 예로 들어 보겠습니다. 왼쪽의 고화질 모델에는 1,800만 개가 넘는 삼각형이 있지만, 오른쪽의 축소된 모델에는 약 20만 개가 있습니다. 산업 공장 관리, 트럭 엔진과 같은 자산에 대한 설계 검토, 수술 전 수술 계획 등과 같은 모든 세부 정보가 중요한 시나리오에서 3D 시각화는 이러한 세부 정보에 생명을 불어 넣습니다. 디자이너, 엔지니어, 의사 및 학생이 복잡한 정보를 더 잘 이해하고 올바른 결정을 내리는 데 도움이 됩니다. 그러나 이렇게 간소화하면 주요 비즈니스 및 설계 결정에 필요한 중요한 세부 정보가 손실될 수 있습니다.

![Unity 쇼케이스 앱에서 Azure Remote Rendering의 예](images/arr-engine.png)

ARR은 렌더링 워크로드를 클라우드의 고급 GPU로 이동하여 이 문제를 해결합니다. 그런 다음, 클라우드에서 호스팅되는 그래픽 엔진에서 이미지를 인계받아서 렌더링하고, 비디오 스트림으로 인코딩하고, 모델을 대상 디바이스로 직접 스트리밍합니다. 

* 하나의 고성능 GPU에서 처리하기에는 너무 많은 복잡한 모델의 경우 ARR은 워크로드를 여러 GPU에 분산하고 결과를 단일 이미지에 병합하여 프로세스를 사용자에게 완전히 투명하게 만듭니다. 

이에 더하여 ARR은 앱에서 사용할 수 있는 사용자 인터페이스의 종류를 제한하지 않습니다. 프레임이 끝나면 로컬로 렌더링된 콘텐츠는 아래 이미지와 같이 원격 이미지와 자동으로 결합됩니다.

![Unity 쇼케이스 앱에서 Azure Remote Rendering의 예](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors
ASA(Azure Spatial Anchors)는 공간 인식 혼합 현실 애플리케이션을 빌드할 수 있는 플랫폼 간 서비스입니다. Azure Spatial Anchors를 사용하면 여러 디바이스에서 홀로그램 콘텐츠를 현실 세계 규모로 매핑, 유지 및 공유할 수 있습니다. 

ASA는 다음을 포함하여 Mixed Reality의 일반적인 사용 사례를 위한 고유한 맞춤형 솔루션입니다.
* **경로 찾기**: 둘 이상의 공간 앵커를 연결하여 사용자가 상호 작용해야 하는 작업 목록 또는 관심 지점을 만들 수 있습니다.
* **다중 사용자 환경**: 사용자가 동일한 가상 공간에서 개체와 상호 작용하여 앞뒤로 이동할 수 있습니다.
* **현실 세계에서 가상 콘텐츠 유지**: 사용자가 지원되는 다른 디바이스에서 볼 수 있는 가상 개체를 현실 세계에 배치할 수 있습니다.

![Azure Spatial Anchors의 예](images/persistence.gif)

서비스는 다양한 환경에서 개발될 수 있으며, 대규모 디바이스 및 플랫폼 그룹에 배포할 수 있습니다. 이를 통해 다음과 같은 사용 가능한 플랫폼 목록에 대해 특별히 허가됩니다.
* HoloLens용 Unity
* iOS용 Unity
* Android용 Unity
* 네이티브 iOS
* 네이티브 Android
* C++/WinRT 및 HoloLens용 DirectX
* iOS용 Xamarin
* Android용 Xamarin

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![음성](../whats-new/images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
        Speech를 통해 음성 처리 기능을 앱 또는 서비스에 통합하는 방법을 알아봅니다. 음성 언어를 텍스트로 변환하거나, 표준(또는 사용자 지정 가능) 음성 글꼴을 사용하여 텍스트에서 자연스러운 음성을 생성합니다. 체험 서비스를 사용해 봅니다. 뒤에 나오는 기능을 사용하여 음성 지원 앱 및 서비스를 빠르게 빌드합니다.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Vision](../whats-new/images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Vision](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
        사진, 비디오 및 디지털 잉크 콘텐츠를 인식, 식별, 캡션, 인덱싱 및 조정합니다. Vision을 통해 앱과 서비스에서 이미지, 비디오 및 디지털 잉크 내의 콘텐츠를 정확히 식별하고 분석할 수 있는 방법을 알아봅니다.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>독립 실행형 Unity 서비스

아래에 나열된 독립 실행형 서비스는 Mixed Reality에 적용되지 않지만, 다양한 개발 컨텍스트에서 유용할 수 있습니다. Unity에서 개발하는 경우 이러한 각 서비스를 새 프로젝트 또는 기존 프로젝트에 통합할 수 있습니다.

### <a name="device-support"></a>디바이스 지원
<table>
    <tr>
        <td><strong>Azure Cloud Service</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens 1세대</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">언어 번역</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">컴퓨터 비전</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">사용자 지정 비전</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">디바이스 간 알림</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">얼굴 인식</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">함수 및 스토리지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">비디오 스트리밍</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">기계 학습</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">함수 및 스토리지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">애플리케이션 인사이트</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">개체 감지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">봇 통합</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>참조

* HoloLens 2용 Azure Spatial Anchor 자습서 - [3-1 Azure Spatial Anchors 시작](../mrlearning-asa-ch1.md)
* HoloLens 2용 Azure Speech Services 자습서 - [4-1 음성 인식/전사 통합 및 사용](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
