---
title: 핵심 언어
description: Maquette의 핵심 언어 세부 정보를 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타이핑, Mixed Reality, Virtual Reality, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197403"
---
# <a name="maquettescript-core-language-details"></a>MaquetteScript 핵심 언어 세부 정보

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette 로고 ](../images/MaquetteIcon.png) MaquetteScript 핵심 언어 세부 정보

## <a name="accessing-maquette-object-and-namespace"></a>개체 `Maquette` 및 네임스페이스 액세스

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette는 개체 및 해당 자식을 통해 JavaScript의 내부 `Maquette` 개체 및 인터페이스를 노출합니다. 이 기능은 [Maquette 개체 및 네임스페이스](https://www.maquette.ms/doc_staging/objects/Maquette.html) 설명서에 설명되어 있습니다. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
`Maquette`개체에는 Maquette 자체와 쉽게 상호 작용하고 반복적인 문제를 더 쉽게 해결할 수 있도록 하는 최상위 함수가 있습니다. 이는 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)설명서에 설명되어 있습니다.

## <a name="maquette-startup-and-loading"></a>Maquette 시작 및 로드

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette는 특정 JavaScript 파일을 로드하고 평가하여 다음과 같은 시간에 구성, 설정 및 초기화를 사용하도록 설정합니다.

Maquette 시작 중:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

프로젝트가 로드될 때마다:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

프로젝트는 해당 프로젝트 스크립트를 로드합니다.
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript 구현

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Maquette에서 사용되는 JavaScript 인터프리터는 [Jint](https://github.com/sebastienros/jint)를 기반으로 하며, Jint는 ECMAScript 5.1과 호환되며 [ECMAScript 6의 추가 확장을 지원합니다.](https://github.com/sebastienros/jint/issues/343) 

확장은 `.mqjs` Maquette javascript 파일과 일반 JavaScript를 구분하는 데 사용됩니다.

## <a name="see-also"></a>참고 항목 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->