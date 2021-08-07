---
title: 집에서 3D 모델의 배치 사용
description: 웹 사이트 또는 애플리케이션의 3D 모델을 Windows Mixed Reality 홈에 배치하는 방법을 알아봅니다.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 모델, 집, 장소, 세계, 모델링, 혼합 현실 홈, 웹, 앱, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186799"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>혼합 현실 홈에서 3D 모델 배치 사용

> [!NOTE]
> 이 기능은 [Windows 10 2018년 4월 업데이트의](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)일부로 추가되었습니다. 이전 버전의 Windows 이 기능과 호환되지 않습니다.

[Windows Mixed Reality 홈은](../discover/navigating-the-windows-mixed-reality-home.md) 애플리케이션을 시작하기 전에 사용자가 시작하는 시작점입니다. 일부 시나리오에서 2D 앱(예: 홀로그램스 앱)을 사용하면 3D 모델을 혼합 현실 홈 직접 장식으로 배치하거나 전체 3D로 추가로 검사할 수 있습니다. *모델 추가 프로토콜을* 사용하면 웹 사이트 또는 애플리케이션에서 직접 3D 모델을 Windows Mixed Reality 홈으로 보낼 수 있습니다. 여기서 [3D 앱 시작 관리자,](3d-app-launcher-design-guidance.md)2D 앱 및 홀로그램처럼 유지됩니다. 

예를 들어 공간을 디자인하기 위해 3D 가구 카탈로그를 표면화할 애플리케이션을 개발하는 경우 *모델 추가 프로토콜을* 사용하여 사용자가 카탈로그에서 해당 3D 가구 모델을 배치할 수 있도록 합니다. 세계에 배치되면 사용자는 홈의 다른 홀로그램과 마찬가지로 이러한 3D 모델을 이동, 크기 조정 및 제거할 수 있습니다. 이 문서에서는 사용자가 앱 또는 웹에서 3D 개체로 세계를 데코레이트할 수 있도록 *모델 추가 프로토콜을* 구현하는 개요를 제공합니다.

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>모델 프로토콜 추가</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>기본 사항

Windows Mixed Reality 홈에 3D 모델을 배치할 수 있도록 설정하는 두 단계는 다음과 같습니다.
1. [3D 모델이 Windows Mixed Reality 홈 과 호환되는지 확인합니다.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
2. 애플리케이션 또는 웹 페이지에서 *모델 추가 프로토콜을* 구현합니다(이 문서).

## <a name="implementing-the-add-model-protocol"></a>*모델 추가 프로토콜* 구현

[호환되는 3D 모델이](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)있으면 웹 페이지 또는 애플리케이션에서 다음 URI를 활성화하여 *모델 추가 프로토콜을* 구현할 수 있습니다.

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

URI가 원격 리소스를 가리키는 경우 자동으로 다운로드되어 홈에 배치됩니다. 로컬 리소스는 홈에 배치되기 전에 혼합 현실 홈 앱 데이터 폴더에 복사됩니다. 사용자가 단추를 숨기거나 가능하면 사용하지 않도록 하여 이 기능을 지원하지 않는 이전 버전의 Windows 실행할 수 있는 시나리오를 고려하도록 환경을 디자인하는 것이 좋습니다. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>유니버설 Windows 플랫폼 앱에서 *모델 추가 프로토콜 호출:*

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>웹 페이지에서 *모델 추가 프로토콜 호출:*

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>몰입형(VR) 헤드셋에 대한 고려 사항

* 몰입형(VR) 헤드셋의 경우 *모델 추가 프로토콜* 를 호출하기 전에 Mixed Reality 포털 실행할 필요가 없습니다. 이 경우 *모델 추가 프로토콜은* Mixed Reality 포털 시작하고 혼합 현실 홈 도착하면 헤드셋이 보고 있는 위치에 개체를 직접 배치합니다. 
* Mixed Reality 포털 이미 실행 중인 데스크톱에서 *모델 추가 프로토콜을* 호출할 때 헤드셋이 "깨워져" 있는지 확인합니다. 그렇지 않으면 배치가 성공하지 못합니다. 

## <a name="see-also"></a>참고 항목

* [Windows Mixed Reality 홈에 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Windows Mixed Reality 홈 탐색](../discover/navigating-the-windows-mixed-reality-home.md)