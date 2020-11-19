---
title: 핵심 언어
description: Maquette의 핵심 언어에 대해 자세히 알아보세요.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935629"
---
# <a name="maquettescript-core-language-details"></a>MaquetteScript 핵심 언어 정보

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette 로고 ](../images/MaquetteIcon.png) MaquetteScript 핵심 언어 정보

## <a name="accessing-maquette-object-and-namespace"></a>`Maquette`개체 및 네임 스페이스 액세스

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette는 개체와 해당 자식을 통해 JavaScript의 내부 개체 및 인터페이스를 노출 `Maquette` 합니다. 이 기능은 [Maquette 개체 및 네임 스페이스](https://www.maquette.ms/doc_staging/objects/Maquette.html) 설명서에 설명 되어 있습니다. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
개체에는 `Maquette` Maquette 자체와 쉽게 상호 작용할 수 있도록 하 고 반복적인 문제를 해결 하기 쉽도록 하는 최상위 함수가 있습니다. 이 내용은 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)의 설명서에 설명 되어 있습니다.

## <a name="maquette-startup-and-loading"></a>Maquette 시작 및 로드

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette는 특정 JavaScript 파일을 로드 하 고 평가 하 여 다음과 같은 시간에 구성, 설정 및 초기화를 사용 하도록 설정 합니다.

Maquette 시작 중:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

프로젝트가 로드 될 때마다:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

프로젝트는 해당 프로젝트 스크립트를 로드 합니다.
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript 구현

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Maquette에서 사용 되는 JavaScript 인터프리터는 [Jint](https://github.com/sebastienros/jint)를 기반으로 합니다. Jint는 ECMAScript 5.1 호환 되며 [ecmascript 6의 추가 확장](https://github.com/sebastienros/jint/issues/343)을 지원 합니다. 

확장은 `.mqjs` 일반 javascript에서 Maquette javascript 파일을 구분 하는 데 사용 됩니다.

## <a name="see-also"></a>참고 항목 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->