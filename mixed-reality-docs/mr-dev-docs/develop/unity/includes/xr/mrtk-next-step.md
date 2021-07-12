---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603724"
---
# <a name="openxr"></a>[<span data-ttu-id="d40ad-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="d40ad-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d40ad-102">MRTK를 사용 하 여 **새 Unity 프로젝트** 를 시작 하려면 mrtk 자습서의 2 단계에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d40ad-103">MRTK를 사용 하 여 새 OpenXR 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="d40ad-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="d40ad-104">**기존 MRTK 프로젝트를 OpenXR로** 업그레이드 하는 경우에는 먼저 MRTK-Unity를 최신 버전 (버전 2.7.2 이상)으로 업그레이드 하 여 혼합 현실 OpenXR 플러그 인과의 호환성을 위한 주요 수정 사항을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="d40ad-105">[Mixed Reality 기능 도구](../../welcome-to-mr-feature-tool.md) 를 사용 하 여 최신 버전의 MRTK로 업그레이드 한 후 [아래의 수동 OpenXR 설정 단계](#manual-setup-without-mrtk)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d40ad-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="d40ad-106">[기존 mrtk 프로젝트를 OpenXR로 마이그레이션하](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)는 방법에 대 한 자세한 내용은 mrtk 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d40ad-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="d40ad-107">**2.5.3** 보다 이전 버전의 MRTK 이전 버전에서 업그레이드 하는 경우 Asset **/MixedRealityToolkit/link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="d40ad-108">이 줄은 MRTK 2.5.4 이상으로 시작한 경우 기본적으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="d40ad-109">Windows XR</span><span class="sxs-lookup"><span data-stu-id="d40ad-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="d40ad-110">MRTK를 사용 하 여 **새 Unity 프로젝트** 를 시작 하려면 mrtk 자습서의 2 단계에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d40ad-111">mrtk를 사용 하 여 새 Windows XR 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="d40ad-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="d40ad-112">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="d40ad-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="d40ad-113">MRTK를 사용 하 여 **새 Unity 프로젝트** 를 시작 하려면 mrtk 자습서의 2 단계에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d40ad-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d40ad-114">MRTK를 사용 하 여 새 레거시 XR 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="d40ad-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)