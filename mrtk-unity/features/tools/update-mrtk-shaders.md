---
title: 셰이더 업데이트 도구
description: MRTK 표준 셰이더를 업데이트 하는 방법에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145132"
---
# <a name="updating-shaders"></a>셰이더 업데이트

2.6.0 버전부터 MRTK 셰이더는 MRTK를 통해 버전 관리 됩니다. 셰이더 센티널 파일. 새 버전의 MRTK로 업그레이드 하는 경우 다음 메시지가 표시 될 수 있습니다.

![셰이더 업데이트 프롬프트](../images/tools/UpdateShaderPrompt.png)

**예** 를 선택 하면 mrtk가 자산의 콘텐츠를   >    >   최신 버전으로 덮어쓰도록 합니다. **아니요** 를 선택 하면 현재 파일이 유지 됩니다. **Ignore** 는 `IgnoreUpdateCheck.sentinel` mrtk 셰이더에서 파일 () **을 만들며**  >    >  이후 셰이더 업데이트 검사를 표시 하지 않습니다.

> [!IMPORTANT]
> 셰이더 파일을 덮어쓰면 사용자 지정 수정 내용이 모두 손실 됩니다. 업그레이드 하기 전에 수정 된 셰이더 파일을 백업 해야 합니다.
>
> 프로젝트가 urp (유니버설 렌더링 파이프라인)를 사용 하도록 구성 된 경우 (이전에는 LWRP (경량 렌더링 파이프라인)) **Mixed Reality Toolkit** 유틸리티를 다시 실행 하 여 >  >
>  **경량 렌더링 파이프라인에 대 한 mrtk 표준 셰이더를 업그레이드** 하세요.

에서 모든 경우에 셰이더 업데이트를 확인 하는 것도 가능 합니다. 여기서는 **혼합 된 현실 도구 키트** 유틸리티를 사용 하 여  >    >  Unity 편집기의 메뉴 모음에서 **셰이더 업데이트를 확인** 합니다.

![셰이더 업데이트 확인](../images/tools/ShaderUpdateMenu.png)

**셰이더 업데이트 확인** 은 파일을 무시 `IgnoreUpdateCheck.sentinel` 하 고 요청 시 셰이더 업데이트를 허용 합니다.

> [!NOTE]
> MRTK 파일을 가져올 때 셰이더 업데이트를 확인 하지 않아도 됩니다.
