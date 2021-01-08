---
title: Unity의 손실 추적
description: Unity mixed reality 앱에서 수동 및 기본 추적 손실을 처리 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 손실 추적, 추적 손실 이미지, 폴링, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009853"
---
# <a name="tracking-loss-in-unity"></a>Unity의 손실 추적

장치를 세계에서 찾을 수 없는 경우 앱은 "추적 손실"을 경험 합니다. 기본적으로 Unity는 업데이트 루프를 일시 중지 하 고 추적이 손실 될 때마다 사용자에 게 시작 이미지를 표시 합니다. 추적이 회복 되 면 시작 이미지가 사라지고 업데이트 루프가 계속 됩니다.

대신 사용자가 설정에서 옵트아웃 하 여이 전환을 수동으로 처리할 수 있습니다. 모든 콘텐츠를 처리 하기 위해 아무것도 수행 하지 않은 경우 추적 손실을 추적 하는 동안 모든 콘텐츠가 본문으로 잠긴 것으로 보입니다.

## <a name="default-handling"></a>기본 처리

업데이트 루프 및 모든 메시지와 이벤트는 기본적으로 손실 된 추적 기간 동안 중지 됩니다. 이때 이미지가 사용자에 게 표시 됩니다. 편집 >설정->플레이어로 이동 하 고 시작 이미지를 클릭 한 다음 Holographic 추적 손실 이미지를 설정 하 여이 이미지를 사용자 지정할 수 있습니다.

## <a name="manual-handling"></a>수동 처리

추적 손실을 수동으로 처리 하려면 **편집**  >  **프로젝트 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 설정 탭**  >  **시작 이미지**  >  **Windows Holographic** 로 이동 하 고 "손실 일시 중지 및 이미지 표시"를 선택 취소 해야 합니다. 그런 다음 아래 지정 된 Api를 사용 하 여 변경 내용 추적을 처리 해야 합니다.

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형:** *WorldManager*

* 세계 관리자는 WorldManager 된 추적 (*OnPositionalLocatorStateChanged*) 및 현재 상태 (*WorldManager*)를 쿼리 하는 속성을 검색 하는 이벤트를 노출 합니다.
* 추적 상태가 활성화 되지 않은 경우 사용자가 변환 하는 동안에도 카메라는 가상 환경에서 변환 하는 것으로 표시 되지 않습니다. 개체는 더 이상 실제 위치에 해당 하지 않으며 모두 본문이 잠깁니다.

변경 내용 추적을 처리 하는 경우 각 프레임의 state 속성에 대해 폴링하거나 *OnPositionalLocatorStateChanged* 이벤트를 처리 해야 합니다.

### <a name="polling"></a>폴링

가장 중요 한 상태는 *Positionallocis state. 활성* 이며,이는 추적이 완전히 작동 함을 의미 합니다. 다른 모든 상태는 주 카메라에만 회전 델타를 발생 합니다. 예를 들면 다음과 같습니다.

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

더 편리 하 게 *OnPositionalLocatorStateChanged* 를 구독 하 여 전환을 처리할 수도 있습니다.

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

## <a name="see-also"></a>참조

* [DirectX에서 추적 손실 처리](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
