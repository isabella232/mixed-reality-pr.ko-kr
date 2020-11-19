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
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="7a9cc-104">MaquetteScript 핵심 언어 정보</span><span class="sxs-lookup"><span data-stu-id="7a9cc-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="7a9cc-105">![Maquette 로고 ](../images/MaquetteIcon.png) MaquetteScript 핵심 언어 정보</span><span class="sxs-lookup"><span data-stu-id="7a9cc-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="7a9cc-106">`Maquette`개체 및 네임 스페이스 액세스</span><span class="sxs-lookup"><span data-stu-id="7a9cc-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="7a9cc-107">Maquette는 개체와 해당 자식을 통해 JavaScript의 내부 개체 및 인터페이스를 노출 `Maquette` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="7a9cc-108">이 기능은 [Maquette 개체 및 네임 스페이스](https://www.maquette.ms/doc_staging/objects/Maquette.html) 설명서에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="7a9cc-109">개체에는 `Maquette` Maquette 자체와 쉽게 상호 작용할 수 있도록 하 고 반복적인 문제를 해결 하기 쉽도록 하는 최상위 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="7a9cc-110">이 내용은 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)의 설명서에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="7a9cc-111">Maquette 시작 및 로드</span><span class="sxs-lookup"><span data-stu-id="7a9cc-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="7a9cc-112">Maquette는 특정 JavaScript 파일을 로드 하 고 평가 하 여 다음과 같은 시간에 구성, 설정 및 초기화를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="7a9cc-113">Maquette 시작 중:</span><span class="sxs-lookup"><span data-stu-id="7a9cc-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="7a9cc-114">프로젝트가 로드 될 때마다:</span><span class="sxs-lookup"><span data-stu-id="7a9cc-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="7a9cc-115">프로젝트는 해당 프로젝트 스크립트를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="7a9cc-116">JavaScript 구현</span><span class="sxs-lookup"><span data-stu-id="7a9cc-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="7a9cc-117">Maquette에서 사용 되는 JavaScript 인터프리터는 [Jint](https://github.com/sebastienros/jint)를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="7a9cc-118">Jint는 ECMAScript 5.1 호환 되며 [ecmascript 6의 추가 확장](https://github.com/sebastienros/jint/issues/343)을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="7a9cc-119">확장은 `.mqjs` 일반 javascript에서 Maquette javascript 파일을 구분 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9cc-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a9cc-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a9cc-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->