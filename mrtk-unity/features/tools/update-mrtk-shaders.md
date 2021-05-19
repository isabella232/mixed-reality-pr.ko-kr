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
# <a name="updating-shaders"></a><span data-ttu-id="4aa21-104">셰이더 업데이트</span><span class="sxs-lookup"><span data-stu-id="4aa21-104">Updating Shaders</span></span>

<span data-ttu-id="4aa21-105">2.6.0 버전부터 MRTK 셰이더는 MRTK를 통해 버전 관리 됩니다. 셰이더 센티널 파일.</span><span class="sxs-lookup"><span data-stu-id="4aa21-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="4aa21-106">새 버전의 MRTK로 업그레이드 하는 경우 다음 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![셰이더 업데이트 프롬프트](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="4aa21-108">**예** 를 선택 하면 mrtk가 자산의 콘텐츠를   >    >   최신 버전으로 덮어쓰도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="4aa21-109">**아니요** 를 선택 하면 현재 파일이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="4aa21-110">**Ignore** 는 `IgnoreUpdateCheck.sentinel` mrtk 셰이더에서 파일 () **을 만들며**  >    >  이후 셰이더 업데이트 검사를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4aa21-111">셰이더 파일을 덮어쓰면 사용자 지정 수정 내용이 모두 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="4aa21-112">업그레이드 하기 전에 수정 된 셰이더 파일을 백업 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="4aa21-113">프로젝트가 urp (유니버설 렌더링 파이프라인)를 사용 하도록 구성 된 경우 (이전에는 LWRP (경량 렌더링 파이프라인)) **Mixed Reality Toolkit** 유틸리티를 다시 실행 하 여 >  >
>  **경량 렌더링 파이프라인에 대 한 mrtk 표준 셰이더를 업그레이드** 하세요.</span><span class="sxs-lookup"><span data-stu-id="4aa21-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="4aa21-114">에서 모든 경우에 셰이더 업데이트를 확인 하는 것도 가능 합니다. 여기서는 **혼합 된 현실 도구 키트** 유틸리티를 사용 하 여  >    >  Unity 편집기의 메뉴 모음에서 **셰이더 업데이트를 확인** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![셰이더 업데이트 확인](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="4aa21-116">**셰이더 업데이트 확인** 은 파일을 무시 `IgnoreUpdateCheck.sentinel` 하 고 요청 시 셰이더 업데이트를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="4aa21-117">MRTK 파일을 가져올 때 셰이더 업데이트를 확인 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aa21-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
