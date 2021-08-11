---
ms.openlocfilehash: 555360092a65b80a1298eb779736b29360f8c6e13bd1834994f316043843b47a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198424"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>표준 WinRT API

WinRT를 사용하는 가장 일반적이고 쉬운 방법은 WinSDK에서 메서드를 호출하는 것입니다. 이렇게 하려면 YourModule.Build.cs 파일을 열고 다음 줄을 추가합니다.

```csharp
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

다음으로, 다음 WinRT 헤더를 추가해야 합니다. 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

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

WinRT 코드는 Win64 및 HoloLens 플랫폼에서만 컴파일할 수 있으므로 if 문은 WinRT 라이브러리가 다른 플랫폼에 포함되지 않도록 합니다. IUnknown 인터페이스를 갖기 위해 unknwn.h가 추가되었습니다. 


## <a name="winrt-from-a-nuget-package"></a>NuGet 패키지의 WinRT

WinRT 지원을 사용하여 NuGet 패키지를 추가해야 하는 경우 좀 더 복잡합니다. 이 경우 Visual Studio 거의 모든 작업을 수행할 수 있지만 Unreal 빌드 시스템은 수행할 수 없습니다. 다행히 그렇게 어려운 것은 아닙니다. 다음은 Microsoft.MixedReality.QR 패키지를 다운로드하는 방법의 예입니다. 다른 파일로 바꿀 수 있습니다. winmd 파일이 손실되지 않도록 하고 올바른 dll을 복사하기만 하면 됩니다. 

Windows 이전 섹션의 SDK dll은 OS에서 처리됩니다. NuGet dll은 모듈의 코드에서 관리해야 합니다. 코드를 추가하여 다운로드하고, 이진 파일 폴더에 복사하고, 모듈 시작 시 프로세스 메모리에 로드하는 것이 좋습니다.

첫 번째 단계에서는 모듈의 루트 폴더에 packages.config()를 추가해야 https://docs.microsoft.com/nuget/reference/packages-config) 합니다. 여기에서 모든 해당 의존도를 포함하여 다운로드하려는 모든 패키지를 추가해야 합니다. 여기서는 Microsoft.MixedReality.QR을 기본 페이로드로 추가하고 다른 두 페이로드를 종속성으로 추가했습니다. 해당 파일의 형식은 Visual Studio.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

이제 NuGet 필수 패키지를 다운로드하거나 NuGet [설명서를 참조할](/nuget/consume-packages/install-use-packages-nuget-cli)수 있습니다.

YourModule.Build.cs를 열고 다음 코드를 추가합니다.

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
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

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
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
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

다음과 같이 SafeCopy 메서드를 정의해야 합니다.

```csharp
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

NuGet DLL은 Win32 프로세스 메모리에 수동으로 로드해야 합니다. 모듈의 시작 메서드에 수동 로드를 추가하는 것이 좋습니다.

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

마지막으로 이전 섹션에서 설명한 대로 WinRT 헤더를 코드에 포함할 수 있습니다.

# <a name="425"></a>[4.25](#tab/425)

Unreal은 버전 4.25에서 WinRT 코드를 기본적으로 컴파일하지 않으므로 Unreal의 빌드 시스템에서 사용할 수 있는 별도의 이진 파일을 빌드하는 것이 사용자의 작업입니다. 

## <a name="objectives"></a>목표

- FileSaveDialogue를 여는 유니버설 Windows DLL 만들기
- Unreal 게임 프로젝트에 해당 DLL 연결
- 새 DLL을 사용하여 Unreal 청사진에서 HoloLens 파일 저장

## <a name="getting-started"></a>시작

1. [모든 필수 도구가](../tutorials/unreal-uxt-ch1.md) 설치되어 있는지 확인합니다.
2. [새 Unreal 프로젝트를 만들고](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) 이름을 **Consumewinrt로** 지정합니다.
3. HoloLens 개발에 [필요한 플러그 인](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) 사용
4. 디바이스 또는 에뮬레이터에 [배포하기 위한 설정](../tutorials/unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>WinRT DLL 만들기 

1. 새 Visual Studio 프로젝트를 열고 Unreal 게임의 **uproject** 파일과 동일한 디렉터리에 **DLL(유니버설 Windows)** 프로젝트를 만듭니다. 

![DLL 만들기](../images/unreal-winrt-img-01.png)

2. 프로젝트 이름을 **HoloLensWinrtDLL로** 지정하고 위치를 **ThirdParty** 하위 디렉토리로 Unreal 게임의 uproject 파일로 설정합니다. 
    * 솔루션 **및 프로젝트를 동일한 디렉터리에 배치를** 선택하여 나중에 경로를 간단하게 찾습니다. 

![DLL 구성](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 새 프로젝트가 컴파일된 후 각각 **HoloLensWinrtDLL.cpp** 및 **HoloLensWinrtDLL.h라는** 빈 cpp 및 헤더 파일에 특히 주의해야 합니다. 헤더는 Unreal에서 DLL을 사용하는 포함 파일이며, cpp는 내보내는 모든 함수의 본문을 포함하고 Unreal이 컴파일할 수 없는 WinRT 코드를 포함합니다. 

3. 코드를 추가하기 전에 필요한 WinRT 코드를 컴파일할 수 있도록 프로젝트 속성을 업데이트해야 합니다. 
    * HoloLensWinrtDLL 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성을** 선택합니다.  
    * **구성** 드롭다운을 **모든 구성으로** 변경하고 **플랫폼** 드롭다운을 **모든 플랫폼으로 변경합니다.**  
    * **구성 속성> C/C++에서 모든 옵션을>.**
        * **추가 옵션에** **await를** 추가하여 비동기 작업을 기다릴 수 있는지 확인합니다.  
        * WinRT 코드를 포함하도록 **C++ 언어 표준을** **ISO C++17 표준(/std:c++17)으로** 변경

![프로젝트 속성 업그레이드](../images/unreal-winrt-img-03.png)

프로젝트는 파일 대화가 열리고 파일을 HoloLens 디스크에 저장하는 WinRT 코드로 DLL의 소스를 업데이트할 준비가 된 것입니다.  

## <a name="adding-the-dll-code"></a>DLL 코드 추가

1. **HoloLensWinrtDLL.h를** 열고 Unreal에서 사용할 dll 내보낸 함수를 추가합니다. 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. **HoloLensWinrtDLL.cpp를** 열고 클래스에서 사용할 모든 헤더를 추가합니다.  

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
> 모든 WinRT 코드는 **HoloLensWinrtDLL.cpp에** 저장되므로 Unreal은 헤더를 참조할 때 WinRT 코드를 포함하지 않습니다. 

3. 여전히 **HoloLensWinrtDLL.cpp에서** OpenFileDialogue() 및 지원되는 모든 코드에 대한 함수 본문을 추가합니다. 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. SaveGameManager 클래스를 **HoloLensWinrtDLL.cpp에** 추가하여 파일 대화형을 처리하고 파일을 저장합니다. 

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

5. Release > **ARM64** 솔루션을 빌드하여 DLL 솔루션에서 자식 디렉터리 ARM64/Release/HoloLensWinrtDLL에 DLL을 빌드합니다. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Unreal에 WinRT 이진 파일 추가 
Unreal에서 DLL을 연결하고 사용하려면 C++ 프로젝트가 필요합니다. Blueprint 프로젝트를 사용하는 경우 C++ 클래스를 추가하여 C++ 프로젝트로 쉽게 변환할 수 있습니다.  

1. Unreal 편집기에서 **파일 > 새 C++ 클래스...** 를 엽니다. **WinrtActor라는** 새 **행위자** 를 만들어 DLL에서 코드를 실행합니다. 

![새 행위자 만들기](../images/unreal-winrt-img-04.png)

> [!NOTE]
> 이제 솔루션이 Source/ConsumeWinRT/ConsumeWinRT.Build.cs라는 새 빌드 스크립트와 함께 uproject 파일과 동일한 디렉터리에 만들어졌습니다.

2. 솔루션을 열고 **Games/ConsumeWinRT/Source/ConsumeWinRT** 폴더를 찾은 다음, **ConsumeWinRT.build.cs를** 엽니다.

![ConsumeWinRT.build.cs 파일 열기](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>DLL 연결
1. **ConsumeWinRT.build.cs에서** 속성을 추가하여 DLL의 포함 경로(HoloLensWinrtDLL.h를 포함하는 디렉터리)를 찾습니다. DLL은 포함 경로의 자식 디렉터리에 있으므로 이 속성은 이진 루트 디렉터리로 사용됩니다.

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

2. 클래스 생성자에서 다음 코드를 추가하여 포함 경로를 업데이트하고, 새 lib를 연결하고, DLL을 지연 로드하고, 패키지된 appx 위치에 복사합니다.

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

3. **WinrtActor.h를** 열고 청사진이 호출하는 함수 정의를 하나 추가합니다. 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. **WinrtActor.cpp를** 열고 BeginPlay를 업데이트하여 DLL을 로드합니다. 

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
> 해당 함수를 호출하기 전에 DLL을 로드해야 합니다.

### <a name="building-the-game"></a>게임 빌드
1. 게임 솔루션을 빌드하여 게임 프로젝트에 열린 Unreal 편집기를 시작합니다. 
    * **행위자 배치** 탭에서 새 **WinrtActor를** 검색하여 장면으로 끌어 놓습니다. 
    * 수준 청사진을 열어 **WinrtActor에서** 청사진 호출 가능 함수를 실행합니다. 

![장면에 WinrtActor 배치](../images/unreal-winrt-img-06.png)

2. World **Outliner에서** 이전에 장면에 삭제된 **WindrtActor를** 찾아서 수준 청사진으로 끌어 끕다. 

![WinrtActor를 수준 청사진으로 끌기](../images/unreal-winrt-img-07.png)

3. 수준 청사진에서 WinrtActor에서 출력 노드를 끌어서 **파일 열기 대화 를** 검색한 다음, 사용자 입력에서 노드를 라우팅합니다.  이 경우 파일 열기 대화는 음성 이벤트에서 호출됩니다. 

![수준 청사진에서 노드 구성](../images/unreal-winrt-img-08.png)

4. [HoloLens 이 게임을 패키지하고,](../tutorials/unreal-uxt-ch6.md)배포하고, 실행합니다.  

Unreal이 OpenFileDialogue를 호출하면 .txt 파일 이름을 묻는 HoloLens 파일 대화가 열립니다.  파일이 저장되면 디바이스 포털의 **파일 탐색기** 탭으로 이동하여 "Hello WinRT" 콘텐츠를 확인합니다. 

## <a name="summary"></a>요약 

Windows 동일한 파일 대화상자를 사용하여 파일을 HoloLens 디스크에 저장해야 하는 경우 Unreal에서 WinRT 코드를 사용하기 위한 시작점으로 이 자습서를 사용하는 것이 좋습니다.  동일한 프로세스가 HoloLensWinrtDLL 헤더에서 추가 함수를 내보내고 Unreal에서 사용되는 경우에도 적용됩니다.  백그라운드 MTA 스레드에서 비동기 WinRT 코드를 대기하는 DLL 코드에 특히 주의하여 Unreal 게임 스레드의 교착 상태를 방지합니다.