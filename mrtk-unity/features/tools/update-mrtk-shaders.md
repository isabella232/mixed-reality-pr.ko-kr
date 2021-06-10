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
# <a name="updating-shaders"></a><span data-ttu-id="1ccf3-104">셰이더 업데이트</span><span class="sxs-lookup"><span data-stu-id="1ccf3-104">Updating Shaders</span></span>

<span data-ttu-id="1ccf3-105">버전 2.6.0부터 MRTK 셰이더가 MRTK를 통해 버전이 업데이트됩니다. Shaders.sentinel 파일.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="1ccf3-106">새 버전의 MRTK로 업그레이드할 때 다음 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![셰이더 업데이트 프롬프트](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="1ccf3-108">**예를** 선택하면 MRTK가 자산 MRTK 셰이더의 콘텐츠를 최신 버전으로 덮어쓰도록 **지시합니다.**  >    >  </span><span class="sxs-lookup"><span data-stu-id="1ccf3-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="1ccf3-109">**아니요를** 선택하면 현재 파일이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="1ccf3-110">**무시하면** `IgnoreUpdateCheck.sentinel` **자산**  >  **MRTK** 셰이더에 파일( )이 만들어지며, 향후  >  셰이더 업데이트 검사를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ccf3-111">셰이더 파일을 덮어쓰면 사용자 지정 수정 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="1ccf3-112">업그레이드하기 전에 수정된 셰이더 파일을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="1ccf3-113">프로젝트가 URP(유니버설 렌더링 파이프라인)(이전의 LWRP(Lightweight Render Pipeline))를 사용하도록 구성된 경우 **Mixed Reality** Toolkit 유틸리티를 다시 실행하여 >  >  >
>  **경량 렌더링 파이프라인용 MRTK 표준 셰이더를 업그레이드하세요.**</span><span class="sxs-lookup"><span data-stu-id="1ccf3-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="1ccf3-114">또한   >  Unity 편집기 메뉴 모음에서 Mixed Reality **Toolkit**  >  **유틸리티** 셰이더 업데이트 확인을 사용하여 언제든지  >  **셰이더 업데이트를 확인할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![셰이더 업데이트 확인](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="1ccf3-116">**셰이더 업데이트 확인은** 파일을 무시하고 `IgnoreUpdateCheck.sentinel` 주문형 셰이더 업데이트를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="1ccf3-117">MRTK .unitypackage 파일을 가져올 때는 셰이더 업데이트를 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ccf3-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
