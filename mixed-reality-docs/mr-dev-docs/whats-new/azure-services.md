---
title: Azure 혼합 현실 서비스
description: Azure mixed reality 서비스를 사용 하 여 HoloLens, iOS 및 Android 장치에서 액세스할 수 있는 3D, 다중 사용자 및 공간적으로 인식 되는 응용 프로그램을 만듭니다.
author: grbury
ms.author: grbury
ms.date: 08/21/2019
ms.topic: overview
keywords: 혼합 현실, 개발, 개발, HoloLens, Azure 서비스, 공간 앵커, 음성, 비전, 원격 렌더링
ms.openlocfilehash: 74be047e31806fce97339756205b93c01af6f79b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582820"
---
# <a name="azure-mixed-reality-services"></a>Azure 혼합 현실 서비스
모든 사람이 주변의 3차원 실제 세계에서 Azure 혼합 현실 서비스를 사용하는 숙련된 전문가임을 보여 줍니다. 사용자가 디지털 정보 캡처 및 정보를 사용 하 여 보다 효율적으로 만들고, 학습 하 고, 공동 작업할 수 있도록 지원 합니다. 3D를 모바일 디바이스, 헤드셋 및 기타 테더링되지 않은 디바이스에 가져옵니다. Azure를 사용하면 가장 중요한 정보가 보호되도록 할 수 있습니다.

## <a name="multi-user-spatially-aware-applications-using-spatial-anchors"></a>공간 앵커를 사용 하는 다중 사용자, 공간적으로 인식 되는 응용 프로그램

![ Azure Spatial Anchors 이미지](../design/images/AzureSpatialAnchors.jpg)

공간 앵커를 사용 하 여 다중 사용자, 공간적으로 인식 되는 혼합 현실 응용 프로그램을 빌드합니다. HoloLens, iOS 및 Android 장치에서 액세스할 수 있는 정확한 위치를 매핑하고, 지정 하 고, 회수 하는 혼합 현실 앱을 만듭니다. 사용자가 더 효율적으로 공동 작업을 수행할 수 있도록 공간에 wayfinding를 사용 하도록 설정 합니다.

[Azure 공간 앵커 사용해 보기](/azure/spatial-anchors)


## <a name="interactive-high-quality-3d-models-using-remote-rendering"></a>원격 렌더링을 사용 하는 대화형의 고품질 3D 모델

![ 원격 렌더링 이미지](../design/images/RemoteRendering.jpg)

시나리오에서 산업 공장 관리, 트럭 엔진과 같은 자산에 대 한 설계 검토, 작동 가능한 수술 계획 등의 시나리오에서 3D 시각화는 해당 세부 정보를 제공 합니다. 디자이너, 엔지니어, 의사 및 학생이 복잡 한 정보를 이해 하 고 적절 하 게 호출 하는 데 도움이 됩니다.

현재 모바일 장치 및 혼합 현실 헤드셋에서 고품질 3D 모델을 실행 하는 경우 대상 하드웨어에서 실행할 수 있을 정도로 3D 모델을 단순화 해야 합니다. 이러한 간소화로 인해 주요 비즈니스 및 설계 결정에 필요한 중요 한 정보가 손실 될 수 있습니다.

Azure 원격 렌더링 미리 보기는 모든 세부 정보가 그대로 유지 되 고 품질 손상 없이 작업할 장치에 대화형 고품질 3D 모델을 제공 합니다.

[Azure 원격 렌더링에 대해 자세히 알아보기](https://azure.microsoft.com/services/remote-rendering)

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![빈 회색 배경의 음성 거품형 아이콘](images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](/azure/cognitive-services/speech-service/)
        Speech를 통해 음성 처리 기능을 앱 또는 서비스에 통합하는 방법을 알아봅니다. 음성 언어를 텍스트로 변환하거나, 표준(또는 사용자 지정 가능) 음성 글꼴을 사용하여 텍스트에서 자연스러운 음성을 생성합니다. 체험 서비스를 사용해 봅니다. 뒤에 나오는 기능을 사용하여 음성 지원 앱 및 서비스를 빠르게 빌드합니다.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![빈 회색 배경의 시각 시각 그래픽](images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Vision](/azure/cognitive-services/computer-vision/)
        사진, 비디오 및 디지털 잉크 콘텐츠를 인식, 식별, 캡션, 인덱싱 및 조정합니다. Vision을 통해 앱과 서비스에서 이미지, 비디오 및 디지털 잉크 내의 콘텐츠를 정확히 식별하고 분석할 수 있는 방법을 알아봅니다.
    :::column-end:::
:::row-end:::


## <a name="see-also"></a>참조

* HoloLens 2용 Azure Spatial Anchor 자습서 - [3-1 Azure Spatial Anchors 시작](../develop/unity/tutorials/mr-learning-asa-02.md)
* HoloLens 2용 Azure Speech Services 자습서 - [4-1 음성 인식/전사 통합 및 사용](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)