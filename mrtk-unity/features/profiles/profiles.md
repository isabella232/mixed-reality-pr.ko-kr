---
title: 프로필
description: MRTK의 문서 프로필
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Profiles,
ms.openlocfilehash: 384614f27c099af197ea8a9aedc72c711f0c099e
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881230"
---
# <a name="profiles"></a>프로필

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

MRTK가 구성되는 주요 방법 중 하나는 Foundation 패키지에서 사용할 수 있는 프로필을 사용하는 것입니다. 장면의 주 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체에는 액티브 프로필(ScriptableObject)이 포함됩니다. 최상위 MRTK 구성 프로필에는 기본 코어 시스템의 각 코어에 대한 하위 프로필 데이터가 포함되어 있으며, 각각은 해당 하위 시스템의 동작을 구성하도록 설계되었습니다. 또한 이러한 하위 프로필은 ScriptableObjects이며, 따라서 한 수준 아래의 다른 프로필 개체에 대한 참조를 포함할 수 있습니다. 기본적으로 MRTK 하위 시스템과 기능을 초기화하는 방법에 대한 구성 정보를 구성하는 연결된 프로필로 이루어진 전체 트리가 있습니다.

예를 들어 입력 시스템의 동작은 `DefaultMixedRealityInputSystemProfile`(자산/MRTK/SDK/프로필)과 같은 입력 시스템 프로필에 의해 제어됩니다.

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>프로필 검사기</sup>

## <a name="background"></a>배경

프로필은 주로 데이터 공급자를 통해 처리되는 여러 디바이스에서 특정 시나리오를 지원하기 위한 것입니다. 이런 식으로 앱은 가능한 한 디바이스에 구애받지 않고 설계할 수 있으며 MRTK 및 프로필의 데이터 공급자가 플랫폼 간 지원을 처리하도록 할 수 있습니다.

GGV 스타일 상호 작용을 기본으로 하는 HoloLens 1 프로필과 같은 특정 디바이스의 입력 기능을 중심으로 구축된 프로필도 있습니다.

## <a name="xr-sdk"></a>XR SDK

현재 XR SDK에 대해 두 개의 프로필(`DefaultXRSDKConfigurationProfile` 및 `DefaultHoloLens2XRSDKConfigurationProfile`)이 제공됩니다. 따라서 장면 및 시나리오별 구성으로 인해 모든 샘플 장면이 완전히 지원되는 것은 아닙니다. `DefaultMixedRealityToolkitConfigurationProfile` 및 `DefaultHoloLens2ConfigurationProfile`을 사용하는 모든 샘플은 해당 XR SDK 프로필로 교환 _할 수 있습니다_. XR SDK와 함께 OpenXR을 사용하는 경우 `DefaultOpenXRConfigurationProfile`을 대신 사용합니다.

기존 XR 및 XR SDK를 나란히 구성할 수 있도록 구성을 쉽게 하고 모든 샘플 장면을 지원하기 위한 추가 작업이 진행되고 있습니다. 추적은 문제 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419)를 참조하세요.

레거시 XR 및 XR SDK 간의 프로필 변환에 대한 자세한 내용은 [XR SDK 파이프라인에 대한 MRTK 구성](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline)을 참조하세요.

## <a name="default-profile"></a>기본 프로필

MRTK는 MRTK가 지원하는 대부분의 플랫폼과 시나리오를 포괄하는 기본 프로필 세트를 제공합니다. 예를 들어 `DefaultMixedRealityToolkitConfigurationProfile`(자산/MRTK/SDK/프로필)을 선택하면 VR(OpenVR, WMR) 및 HoloLens(1 및 2)에서 시나리오를 시험해 볼 수 있습니다.

이 프로필은 일반 사용 프로필이기 때문에 특정 사용 사례에 최적화되어 있지 않습니다. 다른 플랫폼에서 더 나은 성능/특정 설정을 지정하려면, 각 플랫폼에서 더 나은 성능을 발휘하도록 약간 조정되어 있는 다른 프로필을 참조하세요.

## <a name="hololens-2-profile"></a>HoloLens 2 프로필

MRTK는 또한 HoloLens 2: `DefaultHoloLens2ConfigurationProfile`(자산/MRTK/SDK/프로필/HoloLens2)에서 배포 및 테스트에 최적화된 기본 프로필을 제공합니다.

MixedRealityToolkit 개체에 대한 프로필을 선택하라는 메시지가 표시되면 기본 선택된 프로필 대신 이 프로필을 사용합니다.

HoloLens2 프로필과 기본 프로필의 주요 차이점은 다음과 같습니다.

**사용할 수 없는** 기능:

- [경계 시스템](../boundary/boundary-system-getting-started.md)
- [시스템 텔레포트](../teleport-system/teleport-system.md)
- [공간 인식 시스템](../spatial-awareness/spatial-awareness-getting-started.md)
- [손 메시 시각화](../input/hand-tracking.md)(성능 오버헤드 때문)

**사용할 수 있는** 시스템:

- [시선 추적 공급자](../input/eye-tracking/eye-tracking-main.md)
- 시선 입력 시뮬레이션

카메라 프로필 설정은 편집기 품질 및 플레이어 품질이 동일하게 일치하도록 설정됩니다. 이는 불투명 디스플레이가 더 높은 품질로 설정된 기본 카메라 프로필과 다릅니다. 이 변경 사항은 편집기 내 품질이 낮아져 디바이스에서 렌더링되는 것과 더 가깝게 일치함을 의미합니다.

> [!NOTE]
> 공간 인식 시스템은 클라이언트 피드백에 따라 기본적으로 꺼져 있습니다. 얼핏 흥미롭게 보일 수 있지만, 일반적으로 시각적 산만함과 추가 성능 저하를 피하기 위해 꺼져 있습니다. 시스템은 [여기의 지침](../spatial-awareness/spatial-awareness-getting-started.md)에 따라 다시 사용할 수 있습니다.
