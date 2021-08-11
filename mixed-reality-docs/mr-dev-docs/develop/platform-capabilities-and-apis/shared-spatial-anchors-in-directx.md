---
title: DirectX의 공유 공간 앵커
description: DirectX 애플리케이션에서 로컬 및 Azure 공간 앵커를 공유하여 두 HoloLens 디바이스를 동기화하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 멀티 플레이, 보기, 시나리오, 연습, 샘플 코드, Azure, Azure Spatial Anchors, ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193547"
---
# <a name="shared-experiences-in-directx"></a>DirectX의 공유 환경

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 API와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OpenXR API](../native/openxr-getting-started.md)** 를 사용하는 것이 좋습니다.

공유 환경은 자신의 HoloLens, iOS 또는 Android 디바이스를 가진 여러 사용자가 전체적으로 동일한 홀로그램을 보고 상호 작용하는 환경입니다. 홀로그램은 공간 앵커 공유를 사용하여 공간의 고정된 지점에 배치됩니다.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 사용하여 지속형 클라우드 기반 공간 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, iOS 및 Android 디바이스에서 찾을 수 있습니다.  여러 디바이스에서 공통 공간 앵커를 공유하면 각 사용자는 동일한 물리적 위치에서 해당 앵커를 기준으로 렌더링된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

<a href="/azure/spatial-anchors/overview" target="_blank">HoloLens,</a> iOS 및 Android 디바이스에서 비동기 홀로그램 지속성을 위해 Azure Spatial Anchors 사용할 수도 있습니다.  지속형 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.

HoloLens 앱에서 공유 환경 빌드를 시작하려면 5분 Azure Spatial Anchors HoloLens <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">빠른 시작을</a>사용해 보세요.

Azure Spatial Anchors 실행하면 HoloLens <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">앵커를 만들고 찾을</a>수 있습니다.  <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS에서도</a> 연습을 사용할 수 있으므로 모든 디바이스에서 동일한 앵커를 공유할 수 있습니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure Spatial Anchors 사용할 수 없는 경우 [로컬 앵커 전송을](../../out-of-scope/local-anchor-transfers-in-directx.md) 사용하면 하나의 HoloLens 디바이스에서 두 번째 HoloLens 디바이스에서 앵커를 가져올 앵커를 내보낼 수 있습니다.  이 방법은 Azure Spatial Anchors 비해 앵커 회수를 덜 제공하며 iOS 및 Android 디바이스는 이 접근 방식에서 지원되지 않습니다.

## <a name="see-also"></a>추가 정보

* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">azure Spatial Anchors SDK for HoloLens</a>