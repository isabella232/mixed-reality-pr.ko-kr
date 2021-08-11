---
title: Unity의 응시
description: 사용자가 혼합 현실에서 앱이 만드는 홀로그램을 대상으로 지정하는 기본 방법으로 응시 입력을 사용하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 시선 응시, 헤드 게이즈, unity, 홀로그램, 혼합 현실, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c6a435e958a92adeed6cd965bebd0b8829e00da735bd193ca72a68acb9e0d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200118"
---
# <a name="head-gaze-in-unity"></a>Unity의 헤드 응시

[응시는](../../design/gaze-and-commit.md) 사용자가 앱이 [Mixed Reality](../../discover/mixed-reality.md)만드는 [홀로그램을](../../discover/hologram.md) 대상으로 지정하는 기본 방법입니다.

## <a name="implementing-head-gaze"></a>헤드 응시 구현

개념적으로 사용자의 헤드셋에서 광선을 앞으로 프로젝팅하여 [헤드 게이즈(head-gaze)를](../../design/gaze-and-commit.md) 결정하여 적중되는 것을 확인합니다. Unity에서 사용자의 머리 위치와 방향은 [카메라,](camera-in-unity.md)특히 [UnityEngine.Camera.main 을](https://docs.unity3d.com/ScriptReference/Camera-main.html)통해 노출됩니다. [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

[Physics.RayCast를](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 호출하면 3D 충돌 지점 및 헤드 응시 광선 적중을 포함한 다른 GameObject를 포함하여 충돌에 대한 정보가 포함된 [RaycastHit가](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 있습니다.

### <a name="example-implement-head-gaze"></a>예제: 헤드 응시 구현

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>모범 사례

위의 예제에서는 업데이트 루프에서 단일 광선 캐스팅을 발생하여 사용자의 헤드포인트가 가리키는 대상을 찾는 동안 단일 개체를 사용하여 모든 헤드 응시 프로세스를 관리하는 것이 좋습니다. 헤드 게이즈 논리를 결합하면 앱의 처리 능력이 절약되고 광선 캐스팅이 프레임당 하나로 제한됩니다.

## <a name="visualizing-head-gaze"></a>머리 응시 시각화

컴퓨터의 마우스 포인터와 마찬가지로 사용자의 머리 응시를 나타내는 [커서를](../../design/cursors.md) 구현해야 합니다. 사용자가 대상으로 하는 콘텐츠를 알면 상호 작용하려는 내용에 대한 신뢰도가 높아질 수 있습니다.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 머리 응시

MRTK의 [입력 관리자에서](/windows/mixed-reality/mrtk-unity/features/input/overview) 헤드 응시에 액세스할 수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 따라가는 경우 MRTK 핵심 구성 요소에 대해 알아보세요. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [모션 컨트롤러](motion-controllers-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [카메라](camera-in-unity.md)
* [커서](../../design/cursors.md)
* [헤드 게이즈 및 커밋](../../design/gaze-and-commit.md)