---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354448"
---
# <a name="425"></a>[<span data-ttu-id="76ad8-101">4.25</span><span class="sxs-lookup"><span data-stu-id="76ad8-101">4.25</span></span>](#tab/425)

<span data-ttu-id="76ad8-102">Unreal은 버전 4.25에서 WinRT 코드를 고유 하 게 컴파일하지 않으므로 별도의 이진 파일을 작성 하 고, Unreal의 빌드 시스템에서 사용할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="76ad8-103">이 자습서에서는 이러한 시나리오를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-103">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="76ad8-104">목표</span><span class="sxs-lookup"><span data-stu-id="76ad8-104">Objectives</span></span>
- <span data-ttu-id="76ad8-105">FileSaveDialogue를 여는 유니버설 Windows DLL 만들기</span><span class="sxs-lookup"><span data-stu-id="76ad8-105">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="76ad8-106">해당 DLL을 Unreal 게임 프로젝트에 연결</span><span class="sxs-lookup"><span data-stu-id="76ad8-106">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="76ad8-107">새 DLL을 사용 하 여 실제 청사진에서 HoloLens에 파일 저장</span><span class="sxs-lookup"><span data-stu-id="76ad8-107">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="76ad8-108">시작</span><span class="sxs-lookup"><span data-stu-id="76ad8-108">Getting started</span></span>
1. <span data-ttu-id="76ad8-109">[필요한 모든 도구가](../tutorials/unreal-uxt-ch1.md) 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-109">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="76ad8-110">[새 Unreal 프로젝트를 만들고](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) 이름을 **Consumewinrt** 로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-110">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="76ad8-111">HoloLens 개발에 [필요한 플러그 인](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) 사용</span><span class="sxs-lookup"><span data-stu-id="76ad8-111">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="76ad8-112">장치 또는 에뮬레이터에 [배포 설정](../tutorials/unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="76ad8-112">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="76ad8-113">WinRT DLL 만들기</span><span class="sxs-lookup"><span data-stu-id="76ad8-113">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="76ad8-114">새 Visual Studio 프로젝트를 열고, Unreal 게임의 **uproject** 파일과 동일한 디렉터리에 **DLL (유니버설 Windows)** 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-114">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![DLL 만들기](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="76ad8-116">프로젝트 이름을 **HoloLensWinrtDLL** 로 설정 하 고 위치를 **thirdparty (** 하위 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-116">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="76ad8-117">나중에 경로를 찾기 쉽도록 **동일한 디렉터리에 솔루션 및 프로젝트 두기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-117">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![DLL 구성](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="76ad8-119">새 프로젝트를 컴파일한 후에는 각각 **HoloLensWinrtDLL** 및 **HoloLensWinrtDLL** 라는 빈 cpp 및 헤더 파일에 특별히 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-119">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="76ad8-120">헤더는 Unreal에서 DLL을 사용 하는 포함 파일이 고, cpp는 내보내기 함수의 본문을 포함 하 고 그렇지 않으면 컴파일할 수 없는 모든 WinRT 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-120">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="76ad8-121">코드를 추가 하기 전에 필요한 WinRT 코드를 컴파일할 수 있도록 프로젝트 속성을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-121">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="76ad8-122">HoloLensWinrtDLL 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-122">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="76ad8-123">모든 구성 및 **플랫폼** 드롭다운으로 **구성** **드롭다운을** **모든 플랫폼** 으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-123">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="76ad8-124">**구성 속성에서 C/c + +> 모든 옵션>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-124">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="76ad8-125">비동기 작업을 기다릴 수 있도록 **추가 옵션** 에 **wait** 추가</span><span class="sxs-lookup"><span data-stu-id="76ad8-125">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="76ad8-126">**C + + 언어 표준** 을 **ISO c + + 17 Standard (/std: c + + 17)** 로 변경 하 여 WinRT 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-126">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![프로젝트 속성 업그레이드](../images/unreal-winrt-img-03.png)

<span data-ttu-id="76ad8-128">프로젝트에서 파일 대화 상자를 열고 HoloLens 디스크에 파일을 저장 하는 WinRT 코드를 사용 하 여 DLL의 소스를 업데이트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-128">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="76ad8-129">DLL 코드 추가</span><span class="sxs-lookup"><span data-stu-id="76ad8-129">Adding the DLL code</span></span>
1. <span data-ttu-id="76ad8-130">HoloLensWinrtDLL를 열고, Unreal에 사용할 dll 내보내기 함수를 추가 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="76ad8-130">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="76ad8-131">HoloLensWinrtDLL를 열고 클래스에서 사용할 모든 헤더를 추가 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="76ad8-131">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="76ad8-132">모든 WinRT 코드는 **HoloLensWinrtDLL** 에 저장 되므로 실제는 헤더를 참조할 때 winrt 코드를 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-132">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="76ad8-133">여전히 HoloLensWinrtDLL에서 OpenFileDialogue () 및 지원 되는 모든 코드에 대 한 함수 본문을 추가 **합니다**.</span><span class="sxs-lookup"><span data-stu-id="76ad8-133">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="76ad8-134">**HoloLensWinrtDLL** 에 SaveGameManager 클래스를 추가 하 여 파일 대화 상자를 처리 하 고 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-134">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="76ad8-135">Dll 솔루션에서 자식 디렉터리 ARM64/Release/HoloLensWinrtDLL에 대 한 DLL을 빌드하기 위해 **Release > ARM64** 솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-135">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="76ad8-136">Unreal에 WinRT 이진 추가</span><span class="sxs-lookup"><span data-stu-id="76ad8-136">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="76ad8-137">Unreal에서 DLL을 연결 하 고 사용 하려면 c + + 프로젝트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-137">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="76ad8-138">청사진 프로젝트를 사용 하는 경우 c + + 클래스를 추가 하 여 c + + 프로젝트로 쉽게 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-138">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="76ad8-139">Unreal 편집기에서 **파일 > 새 c + + 클래스** ...를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-139">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="76ad8-140">그리고 DLL에서 코드를 실행 하기 위해 **Winrtactor** 라는 새 **행위자** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-140">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![새 작업자 만들기](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="76ad8-142">이제 uproject 파일과 동일한 디렉터리에 Source/ConsumeWinRT/ConsumeWinRT 라는 새 빌드 스크립트와 함께 솔루션이 생성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-142">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="76ad8-143">솔루션을 열고, **게임/ConsumeWinRT/Source/ConsumeWinRT** 폴더를 찾아보고, **ConsumeWinRT.build.cs** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-143">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![ConsumeWinRT.build.cs 파일 열기](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="76ad8-145">DLL 연결</span><span class="sxs-lookup"><span data-stu-id="76ad8-145">Linking the DLL</span></span>
1. <span data-ttu-id="76ad8-146">**ConsumeWinRT.build.cs** 에서 속성을 추가 하 여 DLL (HoloLensWinrtDLL이 포함 된 디렉터리)에 대 한 포함 경로를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-146">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="76ad8-147">DLL이 포함 경로에 대 한 자식 디렉터리에 있으므로이 속성은 이진 루트 디렉터리로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-147">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="76ad8-148">클래스 생성자에서 다음 코드를 추가 하 여 포함 경로를 업데이트 하 고, 새 lib를 연결 하 고, DLL을 지연 로드 하 고 패키지 된 appx 위치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-148">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="76ad8-149">**Winrtactor .h** 를 열고 청사진에서 호출 하는 함수 정의 하나를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-149">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="76ad8-150">**Winrtactor .cpp** 를 열고 beginplay를 업데이트 하 여 DLL을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-150">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="76ad8-151">DLL은 해당 함수를 호출 하기 전에 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-151">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="76ad8-152">게임 빌드</span><span class="sxs-lookup"><span data-stu-id="76ad8-152">Building the game</span></span>
1. <span data-ttu-id="76ad8-153">게임 솔루션을 빌드하여 게임 프로젝트에 열려 있는 실제이 아닌 편집기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-153">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="76ad8-154">**행위자 입력** 탭에서 새 **winrtactor** 를 검색 하 여 장면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-154">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="76ad8-155">수준 청사진을 열고 **Winrtactor** 에서 청사진 호출 가능 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-155">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![장면에 WinrtActor 배치](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="76ad8-157">**세계 Outliner** 에서 이전에 장면에 놓인 **Windrtactor** 를 찾아 수준 청사진으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-157">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![WinrtActor를 수준 청사진으로 끌기](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="76ad8-159">수준 청사진에서 WinrtActor의 출력 노드를 끌어서 **파일 열기 대화 상자** 를 검색 한 다음 사용자 입력에서 노드를 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-159">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="76ad8-160">이 경우 음성 이벤트에서 파일 열기 대화 상자가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-160">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![수준 청사진의 노드 구성](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="76ad8-162">[HoloLens에 대해이 게임을 패키지](../tutorials/unreal-uxt-ch6.md)하 고 배포 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-162">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="76ad8-163">Unreal에서 OpenFileDialogue을 호출 하면 .txt 파일 이름에 대 한 HoloLens 프롬프트에서 파일 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-163">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="76ad8-164">파일이 저장 되 면 장치 포털의 **파일 탐색기** 탭으로 이동 하 여 "Hello WinRT" 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-164">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="76ad8-165">요약</span><span class="sxs-lookup"><span data-stu-id="76ad8-165">Summary</span></span> 

<span data-ttu-id="76ad8-166">이 자습서의 코드는 Unreal에서 WinRT 코드를 사용 하기 위한 시작 점으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-166">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="76ad8-167">이를 통해 사용자는 Windows와 동일한 파일 대화 상자를 사용 하 여 HoloLens 디스크에 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-167">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="76ad8-168">동일한 프로세스를 따라 HoloLensWinrtDLL 헤더에서 추가 함수를 내보내고 Unreal에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-168">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="76ad8-169">백그라운드 MTA 스레드에서 비동기 WinRT 코드를 대기 하는 DLL 코드를 확인 합니다 .이는 Unreal 게임 스레드의 교착 상태를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-169">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="76ad8-170">4.26</span><span class="sxs-lookup"><span data-stu-id="76ad8-170">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="76ad8-171">표준 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="76ad8-171">The standard WinRT APIs</span></span>

<span data-ttu-id="76ad8-172">WinRT를 사용 하는 가장 일반적이 고 쉬운 방법은 WinSDK에서 메서드를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-172">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="76ad8-173">이렇게 하려면 YourModule.Build.cs 파일을 열고 다음 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-173">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

<span data-ttu-id="76ad8-174">다음으로 다음 WinRT 헤더를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-174">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

<span data-ttu-id="76ad8-175">WinRT 코드는 Win64 및 HoloLens 플랫폼 에서만 컴파일될 수 있으므로 if 문은 WinRT 라이브러리가 다른 플랫폼에 포함 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-175">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="76ad8-176">IUnknown 인터페이스를 포함 하는 unknwn이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-176">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="76ad8-177">코드를 작성 하기 전에 다음을 사용 하 여 WinRT 헤더에서 일반적인 경고를 사용 하지 않도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-177">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="76ad8-178">NuGet 패키지의 WinRT</span><span class="sxs-lookup"><span data-stu-id="76ad8-178">WinRT from a NuGet package</span></span>

<span data-ttu-id="76ad8-179">WinRT를 지 원하는 nuget 패키지를 추가 해야 하는 경우에는 좀 더 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-179">It’s a little more complicated if you need to add a nuget package with WinRT support.</span></span> <span data-ttu-id="76ad8-180">이 경우 Visual Studio는 실제로 모든 작업을 수행할 수 있지만, Unreal 빌드 시스템은 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-180">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="76ad8-181">다행히 너무 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-181">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="76ad8-182">다음은 MixedReality 패키지를 다운로드 하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-182">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="76ad8-183">이를 다른 것으로 바꿀 수 있으며, winmd 파일이 손실 되지 않도록 하 고 올바른 dll을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-183">You can replace it with another, just make sure that you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="76ad8-184">이전 섹션의 Windows SDK dll은 OS에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-184">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="76ad8-185">Nuget의 dll은 모듈의 코드를 통해 관리 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-185">Nuget’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="76ad8-186">코드를 다운로드 하 고, 이진 파일 폴더에 복사 하 고, 모듈을 시작할 때 프로세스 메모리에 로드 하는 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-186">You should add code to download them, copy into binaries folder and load into the process memory at the module startup.</span></span>

<span data-ttu-id="76ad8-187">첫 번째 단계에서는 https://docs.microsoft.com/nuget/reference/packages-config) 모듈의 루트 폴더에 packages.config를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-187">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="76ad8-188">여기에서 모든 종속성을 포함 하 여 다운로드 하려는 모든 패키지를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-188">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="76ad8-189">여기에서 MixedReality을 기본 페이로드로 추가 하 고 다른 두 개의 항목을 종속성으로 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-189">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="76ad8-190">이 파일의 형식은 Visual Studio와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-190">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="76ad8-191">이제 NuGet 또는 필수 패키지를 다운로드 하거나 NuGet [설명서](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-191">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="76ad8-192">YourModule.Build.cs를 열고 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-192">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
                                myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);

    }
    else
    {
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }
```

<span data-ttu-id="76ad8-193">다음과 같이 SafeCopy 메서드를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-193">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

<span data-ttu-id="76ad8-194">Nuget Dll은 Win32 프로세스 메모리에 수동으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-194">Nuget DLLs needs to load into your Win32 process memory manually.</span></span> <span data-ttu-id="76ad8-195">모듈의 startup 메서드에 수동 로드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-195">You should add manual loading into the startup method of your module:</span></span>

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

<span data-ttu-id="76ad8-196">마지막으로 이전 섹션에서 설명한 대로 WinRT 헤더를 코드에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ad8-196">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>