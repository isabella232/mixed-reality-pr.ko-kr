---
title: 앱에서 바로 구매
description: 2d XAML 뷰 및 stock Windows OS popup을 사용 하 여 혼합 현실 앱에서 앱에서 바로 구매를 사용 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 앱에서 바로 구매, hololens, XAML, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196151"
---
# <a name="in-app-purchases"></a>앱에서 바로 구매

앱 내 구매는 HoloLens에서 지원 되지만 몇 가지 작업을 설정 해야 합니다.

앱 구매 기능에서을 사용 하려면 다음을 수행 해야 합니다.
* 슬레이트로 표시할 XAML [2d 뷰](../design/app-views.md) 만들기
* 이로 전환 하 여 배치를 활성화 하면 몰입 형 보기가 남습니다.
* API: wait [Currentapp. RequestProductPurchaseAsync ("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_) 를 호출 합니다.

이 API는 앱 내 구매 이름, 설명 및 가격을 표시 하는 stock Windows OS 팝업을 표시 합니다. 그러면 사용자가 구매 옵션을 선택할 수 있습니다. 작업이 완료 되 면 앱은 UI를 제공 해야 합니다 .이를 통해 사용자는 [몰입 형 보기로](../design/app-views.md)다시 전환할 수 있습니다.

데스크톱 기반 Windows Mixed Reality 모던 헤드셋을 대상으로 하는 앱의 경우 RequestProductPurchaseAsync API를 호출 하기 전에 수동으로 XAML 뷰로 전환할 필요가 없습니다.