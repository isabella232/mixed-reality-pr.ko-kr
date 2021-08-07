---
title: Unity 및 Visual Studio 모범 사례
description: Unity 및 Visual Studio 혼합 현실 애플리케이션을 만드는 워크플로를 간소화하는 팁 및 요령입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, 몰입형 헤드셋, 모범 사례, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, UWP, Visual Studio Tools, Windows SDK
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186883"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity 및 Visual Studio 사용 모범 사례

Unity를 사용하여 혼합 현실 애플리케이션을 만드는 경우 Unity와 Visual Studio 전환하여 앱 패키지를 빌드하고 HoloLens 또는 몰입형 헤드셋에 배포해야 합니다. 기본적으로 unity 스크립트를 수정하는 인스턴스 하나와 디바이스에 배포하고 디버그하는 인스턴스 등 두 개의 Visual Studio 인스턴스가 필요합니다. 다음 지침을 통해 단일 Visual Studio 인스턴스를 사용하여 개발하여 Unity 프로젝트를 내보내는 빈도를 줄이고 디버깅 환경을 개선할 수 있습니다.

## <a name="improving-iteration-time"></a>반복 시간 개선

Unity의 .NET 스크립팅 백 엔드에 대한 지원은 Unity 2018에서 더 이상 사용되지 않으며 Unity 2019 이상부터 제거되므로 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)로 전환하는 것이 좋습니다. 그러나 Unity에서 Visual Studio 빌드 시간이 길어질 수 있습니다. 더 빠른 반복을 위해 개선하려면 최상의 컴파일 결과를 위해 환경을 설정합니다.

1) 매번 동일한 디렉터리에 프로젝트를 빌드하고 미리 빌드된 파일을 다시 사용하여 증분 빌드를 사용합니다.
2) 프로젝트 & 빌드 폴더에 대한 맬웨어 방지 소프트웨어 검색 사용 안 함
   - Windows 10 설정 앱에서 바이러스 & **위협 방지** 열기
   - 바이러스 & **위협 방지 설정에서 설정** **관리를** 선택합니다.
   - 제외 섹션에서 **제외 추가 또는 제거를** **선택합니다.**
   - **제외 추가를** 선택하고 Unity 프로젝트 코드 및 빌드 출력이 포함된 폴더를 선택합니다.
3) 빌드에 SSD 사용

자세한 내용은 [IL2CPP에 대한 빌드 시간 최적화를](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 검토하세요. 또한 [IL2CPP 스크립팅 백 엔드에서 디버깅을 검토합니다.](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)

[ *UnityScriptAnalyzer* Visual Studio 확장을](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)설치하는 것이 좋습니다. 이 도구는 보다 최적화된 방식으로 작성할 수 있는 코드에 대한 Unity C# 스크립트를 분석합니다.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

[다운로드 Visual Studio Tools for Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Visual Studio Tools for Unity 이점**
* 중단점을 배치하고 변수 및 복잡한 식을 평가하여 Visual Studio Unity 편집기 내 재생 모드를 디버그합니다.
* Unity Project 탐색기를 사용하여 Unity에서 표시하는 것과 동일한 계층 구조로 스크립트를 찾습니다.
* Visual Studio 내에서 직접 Unity 콘솔을 얻습니다.
* 마법사를 사용하여 신속하게 스크립트를 만들거나 탐색할 수 있습니다.

## <a name="expose-c-class-variables-for-easy-tuning"></a>쉽게 튜닝할 수 있는 C# 클래스 변수 노출

클래스 변수를 노출하는 방법에는 두 가지가 있습니다. 프라이빗 변수에 [SerializeField] 특성을 추가하는 것이 좋습니다. 직렬화된 필드는 편집기에서 액세스할 수 있지만 프로그래밍 방식으로 노출되지는 않습니다.  다른 옵션은 C# 클래스 변수를 공용으로 만들어 편집기 UI에 노출하는 것입니다. 

두 방법 모두 편집기에서 재생하는 동안 변수를 쉽게 조정할 수 있습니다. 이는 상호 작용 메커니즘 속성을 조정하는 데 특히 유용합니다.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>SDK 또는 Unity 업그레이드를 Windows 후 UWP Visual Studio 솔루션 다시 생성

새 Windows SDK 또는 Unity 엔진으로 업그레이드한 후 소스 제어에 체크 인된 UWP Visual Studio 솔루션이 최신이 될 수 있습니다. Unity에서 새 UWP 솔루션을 빌드하고 차이점을 체크 인 솔루션에 병합하여 오래된 솔루션을 해결할 수 있습니다.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>텍스트 형식 자산을 사용하여 콘텐츠 변경 내용을 쉽게 비교

자산을 텍스트 형식으로 저장하면 Visual Studio 콘텐츠 변경 diff를 더 쉽게 검토할 수 있습니다. 편집 > Project 설정 > **편집을** 선택하고 **자산 직렬화** 모드를 텍스트 강제 로 변경하여 자산을 텍스트 형식으로 저장할 수 **있습니다.** 그러나 텍스트 자산 파일 변경 내용을 병합하는 것은 오류가 발생하기 쉬우며 권장되지 않으므로 소스 제어에서 배타적 이진 체크 아웃을 사용하도록 설정하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [IL2CPP에 대한 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio 확장](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)