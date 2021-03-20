---
title: ScreenshotUtility
description: MRTK에서 스크린샷 도구를 사용하는 방법에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4fbd5457dd0af502ddedf30a10482690cd8e1a1d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693070"
---
# <a name="screenshot-utility"></a>스크린샷 유틸리티

Unity에서 문서화 및 판촉 이미지를 위해 스크린샷을 찍는 것은 부담스러울 수 있으며, 출력도 종종 바람직하지 않게 보입니다. 여기에서 `ScreenshotUtility`(xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) 클래스가 실행됩니다.

ScreenshotUtility 클래스는 Unity 편집기 내의 메뉴 항목 및 공용 API를 통해 스크린샷을 촬영하는 데 도움을 줍니다. 스크린샷은 다양한 해상도와 투명하고 선명한 색상으로 캡처하여 쉽게 이미지를 합성할 수 있습니다. 독립 실행형 빌드에서 스크린샷을 찍는 것은 이 도구에서 지원되지 않습니다.

## <a name="taking-screenshots"></a>스크린샷 찍기

편집기에서 *Mixed Reality Toolkit->Utilities->Take Screenshot* 을 선택하고 원하는 옵션을 선택하면 스크린샷을 쉽게 캡처할 수 있습니다. 게임을 플레이하지 않고 캡처하는 경우 게임 창 탭이 표시되는지 확인하세요. 스크린샷이 저장되지 않을 수 있습니다.

기본적으로 모든 스크린샷은 [임시 캐시 경로](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)에 저장되며 스크린샷 경로는 Unity 콘솔에 표시됩니다.

![스크린샷 유틸리티 메뉴 항목](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>스크린샷 캡처 예

아래 스크린샷은 *"4x 해상도(투명 배경)"* 옵션으로 캡처되었습니다. 이렇게 하면 일반적으로 투명 픽셀로 저장된 투명 색상으로 표시되는 모든 픽셀이 고해상도 이미지를 출력합니다. 이 기법을 사용하면 개발자가 이 이미지를 다른 이미지 위에 겹쳐서 스토어 또는 기타 언론 매체에 애플리케이션을 소개할 수 있습니다.

![스크린샷 유틸리티 캡처 예](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
