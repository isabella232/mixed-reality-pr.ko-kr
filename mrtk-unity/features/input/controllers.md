---
title: Controllers
description: MRTK에서 컨트롤러를 사용 하는 방법
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 컨트롤러,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176927"
---
# <a name="controllers"></a><span data-ttu-id="76d14-104">Controllers</span><span class="sxs-lookup"><span data-stu-id="76d14-104">Controllers</span></span>

<span data-ttu-id="76d14-105">컨트롤러는 [**입력 공급자**](input-providers.md)에 의해 자동으로 생성 되 고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d14-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="76d14-106">각 컨트롤러 유형에는 *축 유형에* 의해 정의 된 여러 개의 *물리적 입력* 이 있으며 입력 값의 데이터 형식 (디지털, 단일 축, 이중 축, 6 개의 Dof, ...) 및 입력의 출처를 설명 하는 *입력 형식* (단추 누름, 트리거, 엄지 스틱, 공간 포인터, ...)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d14-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="76d14-107">물리적 입력은 혼합 현실 Toolkit 구성 요소의 *입력 시스템 프로필* 아래 **컨트롤러 입력 매핑 프로필** 에서를 통해 *입력 작업* 에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d14-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![컨트롤러 입력 매핑](../images/input/ControllerInputMapping.png)
