---
title: Microsoft Store에 게시
description: ''
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 문서화, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 게시, 배포, Microsoft store
ms.openlocfilehash: 37a17ba4a691ca8db6ce447abd485293454b8ae3
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96583950"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="cd11f-103">Microsoft Store에 게시</span><span class="sxs-lookup"><span data-stu-id="cd11f-103">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="cd11f-104">Unreal 앱을 전 세계에 공개할 준비가 되면 Microsoft Store에 제출하기 전에 업데이트해야 하는 몇 가지 프로젝트 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-104">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="cd11f-105">이러한 모든 설정에는 기본값이 있지만 프로덕션에서 애플리케이션을 가장 잘 나타내도록 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-105">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="cd11f-106">스토어 패키징에 위한 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="cd11f-106">Project settings for the store packaging</span></span>

1. <span data-ttu-id="cd11f-107">먼저 **프로젝트 설정 > 설명** 을 선택하고 게임 및 게시자 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-107">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="cd11f-108">**게임 이름** 은 HoloLens의 앱 타일에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-108">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="cd11f-109">**회사 고유 이름** 은 프로젝트 인증서를 생성할 때 사용되며 다음과 같은 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-109">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="cd11f-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="cd11f-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![프로젝트 설정에서 설명 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="cd11f-112">프로젝트 설정의 **HoloLens** 섹션을 확장하고 패키징 리소스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-112">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="cd11f-113">이러한 리소스 이름은 애플리케이션의 스토어 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-113">These resource names will be shown on the application’s store page:</span></span>

![프로젝트 설정에서 패키징 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="cd11f-115">**이미지** 섹션을 확장하고 스토어 앱을 나타내는 텍스처로 기본 스토어 이미지를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-115">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="cd11f-116">선택적으로 **3D 로고** 확인란을 선택하여 애플리케이션을 시작할 때 3D 라이브 큐브로 사용할 glb 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-116">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![프로젝트 설정에서 이미지 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="cd11f-118">마지막으로 **새로 생성** 을 선택하여 프로젝트 이름과 회사 고유 이름에서 서명 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-118">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="cd11f-119">스토어 이미지에서 투명 픽셀 대신 표시되는 **타일 배경색** 을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-119">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="cd11f-120">드롭다운을 확장하고 **소매 Windows Store 환경 사용** 을 사용하도록 설정하여 개발 잠금 해제가 아닌 소매 잠금 디바이스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-120">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![프로젝트 설정에서 인증서 생성 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="cd11f-122">선택 사항 앱 설치 관리자</span><span class="sxs-lookup"><span data-stu-id="cd11f-122">Optional App Installer</span></span>

<span data-ttu-id="cd11f-123">**프로젝트 설정 > HoloLens** 에서 앱 설치 관리자 파일을 만들 수 있으며, 스토어 외부에 애플리케이션을 배포하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-123">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="cd11f-124">**앱 설치 관리자 만들기** 확인란을 선택하고 게임의 appxbundle을 저장할 URL 또는 네트워크 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-124">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![프로젝트 설정에서 앱 설치 관리자 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-05.png)

<span data-ttu-id="cd11f-126">앱이 패키징될 때 appxbundle과 appinstaller가 모두 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-126">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="cd11f-127">appxbundle을 설치 URL에 업로드한 다음, appinstaller를 실행하여 네트워크 위치에서 앱을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-127">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="cd11f-128">Windows 앱 인증 키트</span><span class="sxs-lookup"><span data-stu-id="cd11f-128">Windows App Certification Kit</span></span>

<span data-ttu-id="cd11f-129">Windows 10 SDK는 패키지를 스토어에 업로드하는 데 영향을 줄 수 있는 일반적인 문제를 검증하기 위해 WACK(Windows 앱 인증 키트)와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-129">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="cd11f-130">일반적으로 다음 경로 아래에 있는 Windows 키트 디렉터리에서 WACK를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-130">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="cd11f-131">게시를 위해 appx 파일을 패키징한 후 **appcertui.exe** 를 실행하고 프롬프트에 따라 appx를 스캔합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-131">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Windows 앱 인증 키트에서 유효성 검사를 위해 선택된 앱의 스크린샷](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="cd11f-133">**스토어 앱 유효성 검사** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-133">Select **Validate Store App**:</span></span>

![Windows 앱 인증 키트에서 유효성 검사 선택의 스크린샷](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="cd11f-135">상단 섹션에서 appx를 찾고 **다음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-135">Browse for the appx in the top section and select **Next**:</span></span>

![Windows 앱 인증 키트에서 테스트 선택의 스크린샷](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="cd11f-137">**다음** 을 선택하여 테스트를 실행하고 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-137">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="cd11f-138">호스트 PC에서 실행할 수 있는 모든 사용 가능한 테스트는 기본적으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-138">All available tests that can be run on the host PC will be enabled by default</span></span>

![Windows 앱 인증 키트에서 앱 유효성 검사 진행률의 스크린샷](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="cd11f-140">테스트가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-140">Wait for the tests to finish.</span></span> <span data-ttu-id="cd11f-141">완료되면 마지막 창에 합격 또는 불합격 결과가 표시되며, 저장된 보고서에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-141">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Windows 앱 인증 키트에서 최종 보고서 결과의 스크린샷](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="cd11f-143">4\.25의 알려진 WACK 오류</span><span class="sxs-lookup"><span data-stu-id="cd11f-143">Known WACK failure with 4.25</span></span>

<span data-ttu-id="cd11f-144">Unreal 4.25의 Windows Mixed Reality 플러그 인은 HoloLens용으로 패키징하는 과정에 일부 x64 바이너리가 포함되기 때문에 WACK에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-144">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="cd11f-145">오류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-145">The failure will look like this:</span></span>

![바이너리 분석기 및 Windows 앱 인증 키트에서 지원되는 API로 인해 실패한 결과의 스크린샷](images/unreal-publishing-img-11.png)

<span data-ttu-id="cd11f-147">문제를 해결하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-147">To fix the issue:</span></span>
1. <span data-ttu-id="cd11f-148">Unreal 프로젝트를 열어 Unreal 설치 또는 소스 디렉터리 루트를 찾고 작업 표시줄에서 Unreal 아이콘을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-148">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="cd11f-149">UE4Editor를 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음, **위치** 항목에서 경로를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-149">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="cd11f-150">**WindowsMixedRealityHMD.Build.cs** 에서 **행 32** 를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-150">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="cd11f-151">다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-151">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="cd11f-152">Unreal을 닫고, 프로젝트를 다시 열고, HoloLens를 다시 패키징합니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-152">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="cd11f-153">WACK를 다시 실행하면 오류가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="cd11f-153">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="cd11f-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd11f-154">See also</span></span>
* [<span data-ttu-id="cd11f-155">Microsoft Store에 앱 제출</span><span class="sxs-lookup"><span data-stu-id="cd11f-155">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="cd11f-156">Windows 앱 인증 키트</span><span class="sxs-lookup"><span data-stu-id="cd11f-156">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="cd11f-157">수동으로 앱 설치 관리자 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="cd11f-157">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)