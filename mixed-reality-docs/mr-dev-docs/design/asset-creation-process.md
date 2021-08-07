---
title: 자산 생성 프로세스
description: 혼합 현실 환경을 위한 자산을 만들고, 구매하고, 이식하는 방법을 알아봅니다.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 자산, 생성, 프로세스, 예산, 다각형, 질감, 셰이더, 성능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 자산
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214114"
---
# <a name="asset-creation-process"></a>자산 생성 프로세스

Windows Mixed Reality Microsoft가 DirectX에 투자한 수십 년 동안의 투자를 기반으로 합니다. 개발자가 3D 그래픽을 빌드하는 데 보유한 모든 환경과 기술은 HoloLens 계속 중요합니다.

프로젝트에 대해 만드는 자산은 다양한 모양과 형태로 제공됩니다. 일련의 질감/이미지, 오디오, 비디오, 3D 모델 및 애니메이션으로 구성될 수 있습니다. 프로젝트에서 사용되는 다양한 유형의 자산을 만드는 데 사용할 수 있는 모든 도구를 다룰 수는 없습니다. 이 문서에서는 3D 자산 생성 방법을 중점으로 살펴보겠습니다.

![개념, 생성, 통합 및 반복 흐름](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*개념, 생성, 통합 및 반복 흐름*

## <a name="things-to-consider"></a>고려할 사항

환경을 살펴볼 때는 환경을 만들려는 경우 최상의 환경을 만들기 위해 사용할 수 있는 **예산으로** 간주합니다. 자산에서 사용할 수 있는 **다각형** 또는 **재질 형식의** 수에 대한 하드 제한이 반드시 있는 것은 아닙니다. 예산이 정해진 절충안으로 더 생각해 보세요.

다음은 경험에 대한 예제 예산입니다. 성능은 단일 실패 지점이 아니라 천 개의 절단으로 인한 사망입니다.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Assets</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 메모리</th>
</tr><tr>
<td> 다각형</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 텍스처</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 셰이더</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Physics</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 실시간 조명</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> 미디어(오디오/비디오)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 스크립트/논리</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 일반 오버헤드</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>합계</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**총 자산 수**
* 장면에서 활성 상태인 자산은 몇 개입니까?

**자산의 복잡성**
* 삼각형/다각형은 몇 개입니까?
* 셰이더가 얼마나 복잡한가요? Mixed Reality Toolkit 사용하는 경우 [Mixed Reality Toolkit 표준 셰이더를](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 사용하여 셰이더 복잡성을 줄이는 것이 좋습니다.

개발자와 유명인은 모두 디바이스와 그래픽 엔진의 기능을 고려해야 합니다. Microsoft HoloLens 디바이스에 기본 제공되는 모든 계산 및 그래픽이 있습니다. 개발자가 모바일 플랫폼에서 찾을 수 있는 기능을 공유합니다.

자산 생성 프로세스는 환경이 [홀로그램 디바이스 또는 몰입형 디바이스](../discover/mixed-reality.md#the-mixed-reality-spectrum)를 대상으로 하는지 여부에 관계없이 동일합니다. 가장 중요한 점은 디바이스 기능 및 크기 조정입니다. 혼합 현실에서 실제 세계를 볼 수 있으므로 경험에 따라 올바른 규모를 유지 관리하려고 합니다.

## <a name="authoring-assets"></a>자산 작성

프로젝트의 자산을 얻는 방법부터 시작하겠습니다.
1. 자산 만들기(제작 도구 및 개체 캡처)
2. 자산 구매(온라인으로 자산 구입)
3. 자산 포팅(기존 자산 활용)
4. 자산 아웃소싱(타사에서 자산 가져오기)

### <a name="creating-assets"></a>자산 만들기

**제작 도구**<br>
먼저 여러 가지 방법으로 고유한 자산을 만들 수 있습니다. 3D 아티스트는 다양한 애플리케이션과 도구를 사용하여 **메시,** **질감** 및 **재질로** 구성된 모델을 만듭니다. 그런 다음, 앱에서 사용하는 그래픽 엔진(예: )에서 가져오거나 사용할 수 있는 파일 형식으로 **저장됩니다. FBX** 또는 **입니다. OBJ**. 선택한 그래픽 엔진에서 지원하는 모델을 생성하는 모든 도구는 **HoloLens** 작동합니다. 3D 아티스트 중에는 HoloLens 사용하여 자산을 만드는 방식을 변환할 [수 있기 때문에 Autodesk의 Maya를 사용하는](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 경우가 많습니다. 빠르게 원하는 것을 얻으려면 [Windows](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 함께 제공되는 3D Builder 사용하여 를 내보낼 수도 있습니다. 애플리케이션에서 사용할 OBJ입니다.

**개체 캡처**<br>
개체를 3D로 캡처하는 옵션도 있습니다. 3D에서 애니메이션이 없는 개체를 캡처하고 디지털 콘텐츠 만들기 소프트웨어로 편집하는 것은 3D 인쇄의 증가에 따라 점점 더 인기를 끌고 있습니다. Kinect **2** 센서 및 [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 사용하여 캡처 기능을 사용하여 실제 개체에서 자산을 만들 수 있습니다. 또한 여러 이미지를 처리하여 메시와 질감을 함께 연결함으로써 **사진 측량으로** 동일한 작업을 수행할 수 있는 [도구 모음이기도](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) 합니다.

### <a name="purchasing-assets"></a>자산 구매

또 다른 훌륭한 옵션은 사용자 경험을 위해 자산을 구매하는 것입니다. Unity 자산 저장소 또는 [TurboSquid와](https://www.turbosquid.com/) 같은 서비스를 통해 사용할 수 있는 많은 [자산이](https://www.assetstore.unity3d.com/) 있습니다.

타사에서 자산을 구매하는 경우 항상 다음 속성을 확인하려고 합니다.
* **poly 개수는 무엇인가요?**
  * 예산 내에 맞는가요?
* **모델에 대한 세부 정보(LOD) 수준이 있나요?**
  * 모델 수준의 세부 정보를 사용하면 성능을 위해 모델의 세부 정보를 확장할 수 있습니다.
* **원본 파일을 사용할 수 있나요?**
  * [Unity 자산 저장소에는](https://www.assetstore.unity3d.com/) 포함되지 않지만 항상 [TurboSquid](https://www.turbosquid.com/)와 같은 서비스에 포함됩니다.
  * 원본 파일이 없으면 자산을 수정할 수 없습니다.
  * 제공 된 소스 파일을 3D 도구에서 가져올 수 있는지 확인 합니다.
* **수신 하는 내용 파악**
  * 애니메이션이 제공 되나요?
  * 구매 중인 자산의 콘텐츠 목록을 확인 하세요.

### <a name="porting-assets"></a>자산 포팅

일부 경우에는 원래 다른 장치와 다른 앱을 위해 빌드된 기존 자산을 전달 하 게 됩니다. 대부분의 경우 이러한 자산은 앱에서 사용 하는 그래픽 엔진과 호환 되는 형식으로 변환할 수 있습니다.

HoloLens 응용 프로그램에서 사용할 자산을 이식 하는 경우 다음과 같은 질문을 할 수 있습니다.
* **직접 가져올 수도 있고 다른 형식으로 변환 해야 하나요?** 사용 중인 그래픽 엔진을 사용 하 여 가져오는 형식을 확인 합니다.
* **호환 되는 형식으로 변환 하는 것이 손실 되는 경우** 경우에 따라 세부 정보를 분실 하거나 가져오면 3D authoring tool에서 정리 해야 하는 아티팩트가 발생할 수 있습니다.
* **자산의 삼각형/다각형 수는 무엇 인가요?** 응용 프로그램의 예산에 따라 [Simplygon](https://www.simplygon.com/) 또는 유사한 도구를 사용 하 여 원래 자산의 decimate (procedurally 또는 수동 감소)를 응용 프로그램 예산에 맞게 설정할 수 있습니다.

### <a name="outsourcing-assets"></a>자산 아웃소싱

팀에서 만드는 것 보다 더 많은 자산이 필요한 대규모 프로젝트의 또 다른 옵션은 자산 생성을 아웃소싱 하는 것입니다. 아웃소싱 프로세스에는 자산을 전문적으로 활용 하는 올바른 스튜디오 또는 에이전시를 찾는 과정이 포함 됩니다. 이 옵션은 비용이 가장 많이 드는 옵션 일 수 있지만 가장 유연 하 게 얻을 수 있습니다.
* **요청 하는 내용을 명확 하 게 정의**
  * 최대한 많은 세부 정보 제공
  * Front, side 및 back 개념 이미지
  * 컨텍스트에서 자산을 보여 주는 참조 아트
  * 개체의 눈금 (일반적으로 센티미터 단위로 지정)
* **예산 제공**
  * Poly count 범위
  * 질감 수
  * 셰이더 유형 (Unity 및 HoloLens 항상 먼저 모바일 셰이더로 기본 지정 해야 함)
* **비용 이해**
  * 변경 요청에 대 한 아웃소싱 정책은 무엇 인가요?

아웃소싱은 프로젝트 타임 라인을 기반으로 잘 작동 하지만, 처음으로 필요한 자산을 얻을 수 있도록 더 많은 감독이 필요 합니다.
