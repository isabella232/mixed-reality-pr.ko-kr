---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110631142"
---
# <a name="mrtk"></a>[<span data-ttu-id="40165-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="40165-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40165-102">[Mrtk의 구성 대화 상자](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 는 XR SDK 및 레거시 WSA에 대해 깊이 버퍼 설정을 설정 하려고 하지만 해당 탭을 확인 하 고 Unity에서 설정을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-102">[MRTK's configuration dialog](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) will attempt to set depth buffer settings for both XR SDK and legacy WSA, but it's good to check those tabs and verify the settings in Unity.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="40165-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="40165-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40165-104">Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-104">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="40165-105">프로젝트 설정 **편집** XR 플러그 인 관리로 이동 하 여  >    >   메뉴 항목이 확장 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-105">Go to **Edit** > **Project Settings** > **XR Plug-in Management** and ensure the menu item is expanded.</span></span>
2. <span data-ttu-id="40165-106">선택한 XR 런타임에 해당 하는 메뉴 항목을 클릭 합니다 (Windows Mixed Reality 또는 OpenXR).</span><span class="sxs-lookup"><span data-stu-id="40165-106">Click on the menu item corresponding to the XR runtime you've chosen, either Windows Mixed Reality or OpenXR.</span></span> <span data-ttu-id="40165-107">또한 Windows 독립 실행형 및 유니버설 Windows 플랫폼에 대 한 탭을 사용할 수 있으므로 올바른 빌드 플랫폼이 선택 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-107">Additionally, ensure the correct build platform is selected, as tabs for both Windows Standalone and Universal Windows Platform are available.</span></span>
3. <span data-ttu-id="40165-108">을 사용 하도록 설정 하 고 구성 하려면:</span><span class="sxs-lookup"><span data-stu-id="40165-108">To enable and configure:</span></span>
    1. <span data-ttu-id="40165-109">OpenXR의 경우 **깊이 제출 모드** 드롭다운에서 깊이 형식 또는 "없음"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-109">For OpenXR, select either a depth format or "None" in the **Depth Submission Mode** dropdown.</span></span>
    2. <span data-ttu-id="40165-110">Windows Mixed Reality의 경우 **공유 깊이 버퍼** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-110">For Windows Mixed Reality, check or uncheck the **Shared Depth Buffer** check box.</span></span> <span data-ttu-id="40165-111">그런 다음 **깊이 버퍼 형식** 드롭다운에서 형식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-111">Then, select a format from the **Depth Buffer Format** dropdown.</span></span>

<span data-ttu-id="40165-112">![Windows XR 플러그 인 깊이 설정 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 깊이 설정](../../images/xrsdk-openxr-depth.png)</span><span class="sxs-lookup"><span data-stu-id="40165-112">![Windows XR Plugin depth settings](../../images/xrsdk-winxr-depth.png)
![OpenXR depth settings](../../images/xrsdk-openxr-depth.png)</span></span>

> [!NOTE]
> <span data-ttu-id="40165-113">성능 향상을 위해 일반적으로 16 비트 깊이 버퍼를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-113">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="40165-114">그러나 16 비트 깊이 형식을 사용 하는 경우 Unity가이 설정에서 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 일부 unity UI 스크롤 패널과 같이 스텐실 버퍼에 필요한 효과는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-114">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="40165-115">이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 적용 되는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html) 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40165-115">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="40165-116">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="40165-116">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40165-117">Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-117">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="40165-118">**편집**  >  **프로젝트 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 탭**  >  **XR 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-118">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="40165-119">**Windows Mixed REALITY SDK** 항목을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-119">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="40165-120">**깊이 버퍼 공유 사용** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="40165-120">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span> <span data-ttu-id="40165-121">새 프로젝트에서 깊이 버퍼 공유 사용은 기본적으로 선택 되어 있지만 이전 프로젝트에서는 기본적으로 선택 취소 되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-121">Enable Depth Buffer Sharing is checked by default in new projects, but may have been unchecked by default in older projects.</span></span>

![레거시 XR 깊이 설정](../../images/wmr-depth.png)

<span data-ttu-id="40165-123">깊이 버퍼를 사용 하면 Windows에서 기본 카메라의 Unity에 설정 된 근처 및 far 비행기를 사용 하 여 깊이 버퍼의 정규화 된 픽셀 당 깊이 값을 측정 단위로 다시 정확히 매핑할 수 있으므로 시각적 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-123">A depth buffer can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span> <span data-ttu-id="40165-124">렌더링 과정에서 일반적인 방법으로 깊이 값이 처리 되는 경우에는 일반적으로 여기에 자세히 설명 해야 합니다 .이는 기존 색 픽셀을 통해 표시 되는 동안 깊이 버퍼에 쓰는 반투명 렌더링 패스가 다시 프로젝션을 혼동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40165-124">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="40165-125">렌더링 패스에서 깊이 값이 정확 하지 않은 최종 깊이 픽셀을 많이 사용 하는 경우 "깊이 버퍼 공유 사용"을 선택을 취소 하면 시각적 품질이 향상 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-125">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

> [!NOTE]
> <span data-ttu-id="40165-126">성능 향상을 위해 일반적으로 16 비트 깊이 버퍼를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-126">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="40165-127">그러나 16 비트 깊이 형식을 사용 하는 경우 Unity가이 설정에서 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 일부 unity UI 스크롤 패널과 같이 스텐실 버퍼에 필요한 효과는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40165-127">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="40165-128">이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 적용 되는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html) 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40165-128">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>