---
title: 셰이더 업데이트 도구
description: MRTK 표준 셰이더를 업데이트하는 방법에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647098"
---
# <a name="updating-shaders"></a>셰이더 업데이트

버전 2.6.0부터 MRTK 셰이더가 MRTK를 통해 버전이 업데이트됩니다. Shaders.sentinel 파일. 새 버전의 MRTK로 업그레이드할 때 다음 메시지가 나타날 수 있습니다.

![셰이더 업데이트 프롬프트](../images/tools/UpdateShaderPrompt.png)

**예를** 선택하면 MRTK가 자산 MRTK 셰이더의 콘텐츠를 최신 버전으로 덮어쓰도록 **지시합니다.**  >    >   **아니요를** 선택하면 현재 파일이 유지됩니다. **무시하면** `IgnoreUpdateCheck.sentinel` **자산**  >  **MRTK** 셰이더에 파일( )이 만들어지며, 향후  >  셰이더 업데이트 검사를 표시하지 않습니다.

> [!IMPORTANT]
> 셰이더 파일을 덮어쓰면 사용자 지정 수정 내용이 손실됩니다. 업그레이드하기 전에 수정된 셰이더 파일을 백업해야 합니다.
>
> 프로젝트가 URP(유니버설 렌더링 파이프라인)(이전의 LWRP(Lightweight Render Pipeline))를 사용하도록 구성된 경우 **Mixed Reality** Toolkit 유틸리티를 다시 실행하여 >  >  >
>  **경량 렌더링 파이프라인용 MRTK 표준 셰이더를 업그레이드하세요.**

또한   >  Unity 편집기 메뉴 모음에서 Mixed Reality **Toolkit**  >  **유틸리티** 셰이더 업데이트 확인을 사용하여 언제든지  >  **셰이더 업데이트를 확인할** 수 있습니다.

![셰이더 업데이트 확인](../images/tools/ShaderUpdateMenu.png)

**셰이더 업데이트 확인은** 파일을 무시하고 `IgnoreUpdateCheck.sentinel` 주문형 셰이더 업데이트를 허용합니다.

> [!NOTE]
> MRTK .unitypackage 파일을 가져올 때는 셰이더 업데이트를 확인할 필요가 없습니다.
