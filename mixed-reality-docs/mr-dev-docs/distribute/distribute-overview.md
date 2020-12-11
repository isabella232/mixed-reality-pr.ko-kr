---
title: 앱 배포
description: 지원 되는 다양 한 플랫폼 및 게시 저장소에 대 한 다양 한 배포 옵션의 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, 혼합 현실, 모던 헤드셋, 앱, uwp, 제출, 제출, 필터, 메타 데이터, 시스템 요구 사항, 키워드, wack, 인증, 패키지, appx, 머천다이징
ms.openlocfilehash: b4b82557ba274852ebb3f97058017fa2e5db1c02
ms.sourcegitcommit: 9e9d58de4513655c7daa71ff4b5b2c2b115ab959
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97034584"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="38ced-104">앱 배포</span><span class="sxs-lookup"><span data-stu-id="38ced-104">Distributing your apps</span></span>

![WMR home의 Floaty bird 3D 앱 lancher](images/distribute-hero-image.png)

<span data-ttu-id="38ced-106">앱을 사용자에 게 전달 하거나 전 세계에 세밀히 하는 것이 가장 중요 하 고 때로는 개발 활동의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="38ced-107">아래에 나열 된 일련의 리소스에 대 한 프로세스를 간소화 했습니다. 모든는 사용자 또는 팀에 가장 적합 한 배포 및 배포 시나리오에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="38ced-108">분포 옵션</span><span class="sxs-lookup"><span data-stu-id="38ced-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="38ced-109">다른 파티와 앱을 공유 하는 경우 appx 파일을 빌드하고 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="38ced-110">앱 설치 관리자를 사용 하는 경우 사용자와 인증서를 공유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="38ced-111">조직과 공유 하는 경우 회사 또는 학교 계정이 필요 하 고 조직 [MDM (모바일 장치 관리)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) 인프라에 대 한 액세스 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="38ced-112">공유 당사자 인 경우 테 넌 트의 관리자 여야 하며 [Microsoft Endpoint Manager 관리 센터](https://docs.microsoft.com/mem/intune/apps/apps-deploy) 를 사용 하 여 앱을 사용할 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="38ced-113">또 다른 옵션은 최종 사용자와 appx 파일 및 앱 종속성을 공유 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="38ced-114">최종 사용자 인 경우 공유 조직의 테 넌 트에 등록 하면 앱이 자동으로 다운로드 되거나 다운로드 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="38ced-115"><strong>시나리오</strong></span><span class="sxs-lookup"><span data-stu-id="38ced-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="38ced-116"><strong>로컬 장치 설치</strong></span><span class="sxs-lookup"><span data-stu-id="38ced-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="38ced-117"><strong>다른 사람과 공유</strong></span><span class="sxs-lookup"><span data-stu-id="38ced-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="38ced-118"><strong>조직과 공유</strong></span><span class="sxs-lookup"><span data-stu-id="38ced-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>앱 설치 관리자</strong></span><span class="sxs-lookup"><span data-stu-id="38ced-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="38ced-120">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-120">✔️</span></span></td>
    <td><span data-ttu-id="38ced-121">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-회사 포털</strong></a></span><span class="sxs-lookup"><span data-stu-id="38ced-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="38ced-123">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-필수 앱 설치</strong></a></span><span class="sxs-lookup"><span data-stu-id="38ced-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="38ced-125">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="38ced-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="38ced-127">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-127">✔️</span></span></td>
    <td><span data-ttu-id="38ced-128">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-128">✔️</span></span></td><span data-ttu-id="38ced-129">초</span><span class="sxs-lookup"><span data-stu-id="38ced-129">s</span></span>
</tr>
<tr>
    <td><span data-ttu-id="38ced-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>비즈니스용 Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="38ced-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="38ced-131">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-131">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>프로 비전 패키지</strong></a></span><span class="sxs-lookup"><span data-stu-id="38ced-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="38ced-133">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-133">✔️</span></span></td>
    <td><span data-ttu-id="38ced-134">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-134">✔️</span></span></td>
    <td><span data-ttu-id="38ced-135">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-135">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="38ced-136"><a href="#additional-scenarios"><strong>사용자 지정 Win32 배포</strong></a> (HoloLens 장치에는 사용할 수 없음-아래 참조)</span><span class="sxs-lookup"><span data-stu-id="38ced-136"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="38ced-137">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-137">✔️</span></span></td>
    <td><span data-ttu-id="38ced-138">✔️</span><span class="sxs-lookup"><span data-stu-id="38ced-138">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="38ced-139">현재는 관리 되는 장치 또는 HoloLens (첫 번째 Gen) 장치에 대해 앱 설치 관리자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-139">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="38ced-140">추가 시나리오</span><span class="sxs-lookup"><span data-stu-id="38ced-140">Additional scenarios</span></span>

* <span data-ttu-id="38ced-141">스트림 및 Game Pass를 포함 하는 Win32 응용 프로그램 배포의 경우 Win32를 생성할 수 있습니다. EXE 파일을 사용 하 여 Unity의 PC 독립 실행형 빌드 대상을 사용 하 고 선택한 플랫폼에 대 한 일반적인 앱을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-141">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="38ced-142">오프 라인 상태인 동안 HoloLens 2 응용 프로그램을 설치 해야 하는 경우 [오프 라인 보안 HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) 지침을 참조 하거나 개발자 모드를 사용 하도록 설정 하지 않고 프로 비전 패키지를 통해 앱을 설치할.</span><span class="sxs-lookup"><span data-stu-id="38ced-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="38ced-143">빌드를 장치에 배포 하 고 [Visual Studio를 사용 하 여 배포 및 디버깅](../develop/platform-capabilities-and-apis/using-visual-studio.md) 하거나 [장치 포털로 응용 프로그램 패키지를 설치](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal)하 여 개발자 모드를 사용 하는 다른 개발자와 공유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ced-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="38ced-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38ced-144">See also</span></span>
* [<span data-ttu-id="38ced-145">Microsoft Store에서 응용 프로그램 찾기, 설치 및 제거</span><span class="sxs-lookup"><span data-stu-id="38ced-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

