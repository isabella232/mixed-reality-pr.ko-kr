---
title: Microsoft Store에 게시
description: Microsoft Store에서 Unreal Mixed Reality 애플리케이션을 패키지하고, 인증하고, 게시하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 문서화, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 게시, 배포, Microsoft store
ms.openlocfilehash: 2e0e628439c187d787fe64902cbb9a17d617559623d90830ef4a57f6c7b34338
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226300"
---
# <a name="publishing-to-the-microsoft-store"></a>Microsoft Store에 게시

Unreal 앱을 전 세계에 공개할 준비가 되면 Microsoft Store에 제출하기 전에 업데이트해야 하는 몇 가지 프로젝트 설정이 있습니다. 이러한 모든 설정에는 기본값이 있지만 프로덕션에서 애플리케이션을 가장 잘 나타내도록 변경해야 합니다.

## <a name="project-settings-for-the-store-packaging"></a>스토어 패키징에 위한 프로젝트 설정

1. 먼저 **프로젝트 설정 > 설명** 을 선택하고 게임 및 게시자 정보를 업데이트합니다. 
    * **게임 이름** 은 HoloLens의 앱 타일에 표시됩니다.
    * **회사 고유 이름** 은 프로젝트 인증서를 생성할 때 사용되며 다음과 같은 형식이어야 합니다. 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:

![프로젝트 설정에서 설명 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-01.png)

2. 프로젝트 설정의 **HoloLens** 섹션을 확장하고 패키징 리소스를 업데이트합니다.  이러한 리소스 이름은 애플리케이션의 스토어 페이지에 표시됩니다.

![프로젝트 설정에서 패키징 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-02.png)

3. **이미지** 섹션을 확장하고 스토어 앱을 나타내는 텍스처로 기본 스토어 이미지를 업데이트합니다.  선택적으로 **3D 로고** 확인란을 선택하여 애플리케이션을 시작할 때 3D 라이브 큐브로 사용할 glb 파일을 업로드합니다.

![프로젝트 설정에서 이미지 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-03.png)

4. 마지막으로 **새로 생성** 을 선택하여 프로젝트 이름과 회사 고유 이름에서 서명 인증서를 생성합니다.  
    * 스토어 이미지에서 투명 픽셀 대신 표시되는 **타일 배경색** 을 설정합니다.
    * 드롭다운을 확장하고 **소매 Windows Store 환경 사용** 을 사용하도록 설정하여 개발 잠금 해제가 아닌 소매 잠금 디바이스에서 실행합니다.

![프로젝트 설정에서 인증서 생성 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>선택 사항 앱 설치 관리자

**프로젝트 설정 > HoloLens** 에서 앱 설치 관리자 파일을 만들 수 있으며, 스토어 외부에 애플리케이션을 배포하는 데 사용할 수 있습니다.  **앱 설치 관리자 만들기** 확인란을 선택하고 게임의 appxbundle을 저장할 URL 또는 네트워크 경로를 설정합니다.  

![프로젝트 설정에서 앱 설치 관리자 섹션이 확장된 Unreal 편집기의 스크린샷](images/unreal-publishing-img-05.png)

앱이 패키징될 때 appxbundle과 appinstaller가 모두 생성됩니다.  appxbundle을 설치 URL에 업로드한 다음, appinstaller를 실행하여 네트워크 위치에서 앱을 설치합니다.

## <a name="windows-app-certification-kit"></a>Windows 앱 인증 키트

Windows 10 SDK는 패키지를 스토어에 업로드하는 데 영향을 줄 수 있는 일반적인 문제를 검증하기 위해 WACK(Windows 앱 인증 키트)와 함께 제공됩니다.  일반적으로 다음 경로 아래에 있는 Windows 키트 디렉터리에서 WACK를 찾을 수 있습니다. 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. 게시를 위해 appx 파일을 패키징한 후 **appcertui.exe** 를 실행하고 프롬프트에 따라 appx를 스캔합니다.

![Windows 앱 인증 키트에서 유효성 검사를 위해 선택된 앱의 스크린샷](images/unreal-publishing-img-06.png)

2. **스토어 앱 유효성 검사** 를 선택합니다.

![Windows 앱 인증 키트에서 유효성 검사 선택의 스크린샷](images/unreal-publishing-img-07.png)

3. 상단 섹션에서 appx를 찾고 **다음** 을 선택합니다.

![Windows 앱 인증 키트에서 테스트 선택의 스크린샷](images/unreal-publishing-img-08.png)

4. **다음** 을 선택하여 테스트를 실행하고 보고서를 만듭니다.
    * 호스트 PC에서 실행할 수 있는 모든 사용 가능한 테스트는 기본적으로 사용하도록 설정됩니다.

![Windows 앱 인증 키트에서 앱 유효성 검사 진행률의 스크린샷](images/unreal-publishing-img-09.png)

5. 테스트가 완료될 때까지 기다립니다. 완료되면 마지막 창에 합격 또는 불합격 결과가 표시되며, 저장된 보고서에서 볼 수 있습니다.

![Windows 앱 인증 키트에서 최종 보고서 결과의 스크린샷](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>4\.25의 알려진 WACK 오류

Unreal 4.25의 Windows Mixed Reality 플러그 인은 HoloLens용으로 패키징하는 과정에 일부 x64 바이너리가 포함되기 때문에 WACK에 실패합니다. 오류는 다음과 같습니다.

![바이너리 분석기 및 Windows 앱 인증 키트에서 지원되는 API로 인해 실패한 결과의 스크린샷](images/unreal-publishing-img-11.png)

문제를 해결하려면 다음을 수행합니다.
1. Unreal 프로젝트를 열어 Unreal 설치 또는 소스 디렉터리 루트를 찾고 작업 표시줄에서 Unreal 아이콘을 마우스 오른쪽 단추로 클릭합니다.
2. UE4Editor를 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음, **위치** 항목에서 경로를 찾습니다.

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. **WindowsMixedRealityHMD.Build.cs** 에서 **행 32** 를 수정합니다.

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

다음과 같이 변경합니다.

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Unreal을 닫고, 프로젝트를 다시 열고, HoloLens를 다시 패키징합니다.  WACK를 다시 실행하면 오류가 사라집니다. 

## <a name="see-also"></a>참고 항목

* [Microsoft Store에 앱 제출](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Windows 앱 인증 키트](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [수동으로 앱 설치 관리자 파일 만들기](/windows/msix/app-installer/how-to-create-appinstaller-file)