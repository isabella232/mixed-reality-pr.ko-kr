---
title: 응시
description: MRTK의 응시 유형에 대한 누적
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 응시,
ms.openlocfilehash: a9d97ef73a7014a46001cbd42281c5ab28f6cf425dfd7605ce5b3c8c7fc45198
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208438"
---
# <a name="gaze"></a>응시

[응시는](/windows/mixed-reality/gaze) 사용자가 보고 있는 위치에 따라 세계와 상호 작용하는 입력의 한 형태입니다. 응시는 서로 다른 두 가지 지역에 존재합니다.

## <a name="head-gaze"></a>머리 응시

이 유형의 응시는 머리/카메라가 보고 있는 방향을 기반으로 하며, 머리 응시는 시선 응시를 지원하지 않는 시스템 또는 하드웨어에서 시선 응시를 지원할 수 있지만 올바른 [권한 집합 및 설정이](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) 수행되지 않은 경우 활성화됩니다.

머리 응시는 일반적으로 홀로그램 프레임의 가운데에 배치한 다음 에어 탭 제스처를 수행하여 개체를 보는 것과 관련된 HoloLens 1 스타일 상호 작용과 연결됩니다.

## <a name="eye-gaze"></a>응시

이러한 유형의 응시는 사용자의 시선이 보이는 위치에 따라 다릅니다. 시선 응시는 시선 추적을 지원하는 시스템에만 존재합니다. 시선 응시를 사용하는 방법에 대한 자세한 내용은 [시선 추적 설명서를](eye-tracking/eye-tracking-main.md) 참조하세요.

## <a name="gazeprovider"></a>GazeProvider

응시 기능(머리 및 눈 모두)은 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)에서 제공합니다. 이 공급자는 입력 시스템 프로필의 *포인터* 섹션에서 구성할 수 있습니다.

![응시 구성 진입점](../images/input/GazeConfigurationEntrypoint.png)

다른 입력 소스와 마찬가지로 응시 공급자는 포인터를 사용하여 장면의 개체와 상호 [작용합니다(포인터에 대한 자세한 내용은 이 문서 참조).](../../architecture/controllers-pointers-and-focus.md)
응시 공급자의 경우 포인터는 을 통해 `InternalGazePointer` 구현되며 프로필을 통해 구성되지 않습니다.

[IMixedRealityGazeProvider 및 IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 를 구현하는 다른 클래스를 참조하도록 *응시 공급자 형식을* 변경하여 스톡 GazeProvider를 대체 구현으로 바꿀 수 있습니다. [](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)
GazeProvider를 다시 구현하는 것은 사소하지 않을 수 있기 때문에 일반적으로 주식 GazeProvider를 사용하고 버그를 찾을 때 문제를 제출하는 것이 좋습니다.

### <a name="alternative-platform-provided-gaze-poses"></a>대체 플랫폼 제공 응시 자세

기본적으로 MRTK GazeProvider는 카메라 프레임의 중심을 응시 원점으로 사용합니다. HoloLens 2 Windows Mixed Reality 같은 일부 플랫폼에서는 대체적으로 정의된 응시 자세를 제공합니다. 응시 설정의 설정을 통해 `Use Head Gaze Override` 관리됩니다. 사용하도록 설정하면 대체 응시 재정의가 사용됩니다. 사용하지 않도록 설정하면 기본 프레임 중심 원점이 사용됩니다. 특히 HoloLens 2 경우 응시 각도는 대상 지정을 위해 헤드를 사용할 때 사용자의 편의를 고려하여 몇 도씩 높아질 수 있습니다.

## <a name="usage"></a>사용량

### <a name="how-get-the-current-gaze-target"></a>현재 응시 대상을 얻는 방법

이 샘플에서는 사용자 응시의 대상이 되는 현재 게임 개체를 얻는 방법을 보여 있습니다.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>현재 응시 방향 및 원점 얻는 방법

이 샘플에서는 사용자 응시의 방향과 원점(방향이 진행되는 지점)을 나타내는 Vector3을 얻는 방법을 보여줍니다.

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
