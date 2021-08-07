---
title: Unity의 손실 추적
description: Unity 혼합 현실 앱 내에서 수동 및 기본 추적 손실을 처리하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 손실 추적, 손실 이미지 추적, 폴링, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211355"
---
# <a name="tracking-loss-in-unity"></a>Unity의 손실 추적

디바이스가 전 세계에서 자신을 찾을 수 없는 경우 앱은 "손실 추적"을 경험합니다. 기본적으로 Unity는 업데이트 루프를 일시 중지하고 추적이 손실될 때마다 사용자에게 시작 이미지를 표시합니다. 추적이 다시 완료되면 시작 이미지가 사라지고 업데이트 루프가 계속됩니다.

또는 사용자가 설정을 옵트아웃하여 이 전환을 수동으로 처리할 수 있습니다. 아무 것도 처리하지 않으면 추적 손실 중에 모든 콘텐츠가 본문이 잠긴 것처럼 보입니다.

## <a name="default-handling"></a>기본 처리

업데이트 루프 및 모든 메시지 및 이벤트는 기본적으로 손실 추적 기간 동안 중지됩니다. 동시에 이미지가 사용자에게 표시됩니다. 편집 >설정->플레이어로 차례로 가서 시작 이미지를 클릭하고 홀로그램 추적 손실 이미지를 설정하여 이 이미지를 사용자 지정할 수 있습니다.

## <a name="manual-handling"></a>수동 처리

추적 손실을 수동으로 처리하려면   >  **홀로그램에서 Project 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 설정 편집 탭**  >  **시작 이미지**  >  **Windows** 이동한 후 "추적 손실 일시 중지 및 이미지 표시" 선택을 취소해야 합니다. 그런 다음, 아래에 지정된 API를 사용하여 변경 내용 추적을 처리해야 합니다.

**네임스페이스:** *UnityEngine.XR.WSA*<br>
**유형:** *WorldManager*

* World Manager는 손실/획득한 추적을 검색하는 이벤트(*WorldManager.OnPositionalLocatorStateChanged)* 및 현재 상태를 쿼리하는 속성(WorldManager.state)을 노출합니다.
* 추적 상태가 활성 상태가 아닌 경우 사용자가 번역하는 경우에도 가상 세계에서 카메라가 번역되지 않습니다. 개체는 더 이상 물리적 위치에 해당하지 않으며 모두 본문이 잠긴 것으로 표시됩니다.

자체적으로 변경 내용 추적을 처리할 때 각 프레임의 상태 속성에 대해 폴링하거나 *OnPositionalLocatorStateChanged* 이벤트를 처리해야 합니다.

### <a name="polling"></a>폴링

가장 중요한 상태는 *PositionalLocatorState.Active* 입니다. 즉, 추적이 완벽하게 작동합니다. 다른 모든 상태는 주 카메라에 대한 회전 델타만 발생합니다. 예를 들어:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>OnPositionalLocatorStateChanged 이벤트 처리

보다 편리하게 *OnPositionalLocatorStateChanged를* 구독하여 전환을 처리할 수도 있습니다.

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>추가 정보

* [DirectX에서 추적 손실 처리](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
