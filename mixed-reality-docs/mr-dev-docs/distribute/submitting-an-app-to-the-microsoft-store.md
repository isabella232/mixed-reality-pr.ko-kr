---
title: Microsoft Store에 앱 제출
description: Microsoft Store에 혼합 현실 앱을 패키징, 테스트 및 제출 하는 과정을 살펴봅니다.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, 모던 헤드셋, 앱, uwp, 제출, 제출, 필터, 메타 데이터, 시스템 요구 사항, 키워드, wack, 인증, 패키지, appx, 머천다이징, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197724"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store에 앱 제출

> [!IMPORTANT]
> Unreal 응용 프로그램을 제출 하는 경우 계속 하기 전에 **[게시 지침](../develop/unreal/unreal-publishing-to-store.md)** 을 따라야 합니다.

## <a name="prerequisites"></a>필수 조건

[HoloLens](/hololens/hololens1-hardware) 및 Windows 10 PC는 [몰입 형 헤드셋](../discover/immersive-headset-hardware-details.md) 을 켜는 유니버설 Windows 플랫폼 앱을 실행 합니다. HoloLens, PC 또는 둘 다를 지 원하는 앱을 제출 하 든, 앱 제출은 [파트너 센터](https://partner.microsoft.com/dashboard)를 통해 진행 됩니다.

파트너 센터 개발자 계정이 아직 없는 경우 계속 진행 하기 전에 [등록](https://developer.microsoft.com/store/register) 합니다. 제출 지침 및 검사 목록에 대 한 자세한 내용은이 [앱 서브 미션 문서](/windows/uwp/publish/app-submissions)에서 찾을 수 있습니다.

> [!IMPORTANT]
> 파트너 센터 개발자 계정이 고용 확인 검사에 실패 하는 경우 Microsoft Store에 응용 프로그램을 제출할 수 없습니다. 자세한 내용은 파트너 센터 [지원 팀](https://developer.microsoft.com/windows/support) 에 문의 하세요.

## <a name="packaging-a-mixed-reality-app"></a>혼합 현실 앱 패키징

다음을 포함 하 여 혼합 현실 응용 프로그램을 패키징하는 몇 가지 단계가 있습니다.

* 모든 이미지 자산을 올바르게 준비
* HoloLens 시작 메뉴에 표시 되는 타일 이미지 선택
* 앱에 대 한 대상 및 최소 Windows 버전 설정
* 앱 종속성에서 대상 장치 패밀리 설정
* 메타 데이터를 추가 하 여 앱을 Microsoft Store와 연결
* 업로드 패키지 만들기

이러한 각 제출 단계는 아래의 자체 섹션에서 설명 합니다. 첫 번째 제출 시도를 수행 하지 않고 순차적으로 진행 하는 것이 좋습니다.

### <a name="prepare-image-assets-included-in-the-appx"></a>Appx에 포함 된 이미지 자산 준비

Appx 빌드 도구에서 응용 프로그램을 Microsoft Store에 전송 하는 데 필요한 appx 패키지에 빌드하려면 다음 이미지 자산이 필요 합니다. MSDN의 [타일 및 아이콘 자산에 대 한 지침](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) 을 자세히 알아볼 수 있습니다.

| 필수 자산 | 권장 크기 조정 | 이미지 형식 | 자산이 표시 되는 위치 | 
|----------|----------|----------|------------------|
| 71x71 정사각형 로고 | 임의 |  PNG | 해당 없음 | 
| 150x150 정사각형 로고 | 150x150 (100% scale) 또는 225x225 (150% scale) | PNG | Pin 및 모든 앱 시작 (310x310이 제공 되지 않은 경우), 스토어 검색 제안, 스토어 목록 페이지, 스토어 찾아보기, 스토어 검색 | 
|  310x150 너비가 긴 로고 |  임의  |  PNG  |  해당 없음 | 
|  스토어 로고 |  75x75 (150% scale)  |  PNG  |  파트너 센터, 보고서 앱, 리뷰 작성, 내 라이브러리 | 
|  시작 화면 |  930x450 (150% scale)  |  PNG  |  2D 앱 시작 관리자 (슬레이트) | 

HoloLens를 개발 하는 경우 다음을 활용할 수 있는 다른 권장 자산이 있습니다.

| 권장 자산 | 권장 크기 조정 | 자산이 표시 되는 위치 | 
|----------|----------|----------|
|  사각형 310x310 로고 |  310x310 (150% scale) |  Pin 및 모든 앱 시작 | 

### <a name="live-tile-requirements"></a>라이브 타일 요구 사항

HoloLens의 시작 메뉴는 기본적으로 가장 큰 포함 된 정사각형 타일 이미지를 사용 합니다. Microsoft에서 게시 한 앱은 3d [앱 시작 관리자 구현](implementing-3d-app-launchers.md) 지침에 따라 앱에 추가할 수 있는 선택적 3d 시작 관리자가 있습니다.

### <a name="specifying-target-and-minimum-version-of-windows"></a>대상 및 최소 버전의 Windows 지정

혼합 현실 앱에 Windows 버전과 관련 된 기능이 포함 된 경우 지원 되는 대상 및 최소 플랫폼 버전을 지정 하는 것이 중요 합니다.

**Windows 10 Fall Creators Update 이상이 필요한 [Windows Mixed Reality 몰입 형 헤드셋](../discover/immersive-headset-hardware-details.md)을 대상으로 하는 앱에 특히 주의 하세요. (10.0; 빌드 16299)가 제대로 작동 하도록 합니다.**

Visual Studio에서 새 유니버설 Windows Project를 만들 때 Windows의 대상 및 최소 버전을 설정 하 라는 메시지가 표시 됩니다. 기존 프로젝트의 경우 드롭다운 메뉴의 아래쪽에 있는 **앱 이름> 속성<** 를 선택 하 여 **Project** 메뉴에서이 설정을 변경할 수 있습니다.

![Visual Studio 2019의 최소 및 대상 플랫폼 버전 설정](images/visual-studio-min-version-500px.png)<br>
*Visual Studio의 최소 및 대상 플랫폼 버전 설정*

### <a name="specifying-target-device-families"></a>대상 장치 패밀리 지정

Windows Mixed Reality 응용 프로그램 ( [HoloLens](/hololens/hololens1-hardware) 및 [몰입 형 헤드셋](../discover/immersive-headset-hardware-details.md))은 유니버설 Windows 플랫폼의 일부 이므로 Windows 있는 모든 앱 패키지를 포함 **합니다. 유니버설** [대상 장치 제품군](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) 은 HoloLens 또는 모던 헤드셋이 있는 pc Windows 10에서 실행할 수 있습니다. 앱 매니페스트에서 대상 장치 제품군을 지정 하지 않은 경우 의도 하지 않은 Windows 10 장치까지 실수로 앱을 열 수 있습니다. 아래 단계에 따라 원하는 Windows 10 장치 제품군을 지정 하 고, [Microsoft Store 제출을 위해 파트너 센터에서 앱 패키지를 업로드할 때 올바른 장치 제품군을 설정 했는지 두 번 확인 합니다.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Visual Studio에서이 필드를 설정 하려면 **appxmanifest.xml** 를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 를 선택한 다음 **targetdevicefamily Name** 필드를 찾습니다. 기본적으로 다음 항목과 같이 표시 됩니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* **HoloLens** 앱을 만드는 경우 대상 장치 패밀리를 Windows로 설정 하 여 HoloLens에만 설치 되도록 할 수 있습니다 **. Holographic**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* 응용 프로그램에 눈 또는 핸드 추적과 같은 **HoloLens 2** 기능이 필요한 경우 대상 장치 제품군을 Windows로 설정 하 여 Windows 버전 18362 이상을 대상으로 하는지 확인할 수 있습니다 **.** 10.0.18362.0의 **MinVersion** 를 사용 하는 Holographic:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* **Windows Mixed Reality 몰입 형 헤드셋** 에 대해 앱을 만드는 경우 대상 장치 제품군을 Windows로 설정 하 여 Windows 10 Fall Creators Update (Windows Mixed Reality에 필요)가 있는 Windows 10 pc에만 설치 되도록 할 수 있습니다 **.** 10.0.16299.0의 **MinVersion** 를 사용 하는 데스크톱:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* 마지막으로 앱이 **HoloLens** 및 **Windows Mixed Reality 모던 헤드셋** 모두에서 실행 되도록 설정 된 경우 해당 하는 두 장치 제품군 에서만 앱을 사용할 수 있는지 확인 하 고 각 대상에 각 대상 장치 제품군에 대 한 줄을 포함 하 여 각 대상에 올바른 최소 Windows 버전이 있는지 확인할 수 있습니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

[Targetdevicefamily UWP 설명서](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)를 읽어 장치 패밀리를 대상으로 지정 하는 방법에 대해 자세히 알아볼 수 있습니다.

### <a name="associate-app-with-the-store"></a>앱을 스토어에 연결

앱을 Microsoft Store와 연결 하면 현재 프로젝트 로컬 응용 프로그램 매니페스트 파일에 다음 값이 다운로드 됩니다.

* 패키지 표시 이름
* 패키지 이름
* 게시자 ID
* 게시자 표시 이름
* 버전

사용자 지정 .xml 파일을 사용 하 여 기본 appxmanifest.xml 파일을 재정의 하는 경우 응용 프로그램을 Microsoft Store에 연결할 수 없습니다. 사용자 지정 매니페스트 파일을 스토어와 연결 하면 오류 메시지가 생성 됩니다.

Visual Studio 솔루션으로 이동 하 고 **Project > 스토어** 를 선택 하 > 앱을 스토어에 연결 하 여 구매 및 알림 시나리오를 테스트할 수도 있습니다.

### <a name="creating-an-upload-package"></a>업로드 패키지 만들기

[Windows 10에 대 한 유니버설 Windows 앱 패키징](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2)의 지침을 따르세요.

업로드 패키지를 만드는 마지막 단계는 [Windows 앱 인증 키트](#windows-app-certification-kit)를 사용 하 여 패키지의 유효성을 검사 하는 것입니다.

다른 Windows 10 장치 제품군에서 사용할 수 있는 기존 제품에 HoloLens 관련 패키지를 추가 하는 경우 다음에 주의 해야 합니다. 

* [특정 고객에 게 제공 되는 패키지에 대 한 버전 번호의 영향을 받는 방법](/windows/uwp/publish/package-version-numbering)
* [다른 운영 체제에 패키지를 배포 하는 방법](/windows/uwp/publish/guidance-for-app-package-management)

일반적인 지침은 장치에 대 한 버전 번호가 가장 높은 패키지가 저장소에서 배포 하는 것입니다.

Windows 있는 시나리오 **. 범용** 패키지와 **Windows. Holographic** 패키지 및 Windows 합니다. 범용 패키지의 버전 번호가 더 높습니다. HoloLens 사용자가 더 높은 버전 번호 Windows 다운로드 합니다. Windows 대신 범용 패키지입니다. Holographic 패키지. 

위의 시나리오가 원하는 결과가 아닌 경우 다음과 같은 여러 가지 솔루션을 사용할 수 있습니다.

* Windows와 같은 플랫폼별 패키지를 확인 합니다. Holographic Windows와 같은 플랫폼에 관계 없는 패키지 보다 항상 버전 번호가 높습니다. 세계
* 앱을 Windows으로 패키지 하지 않습니다. 범용 패키지를 포함 하는 경우 범용 패키지-대신 Windows를 패키지 합니다. 사용할 수 있도록 하려는 특정 플랫폼에 대 한 범용 패키지
* 단일 Windows를 만듭니다. 모든 플랫폼에서 작동 하는 범용 패키지입니다. 지금은이 옵션에 대 한 지원을 사용할 수 없으므로 위의 해결 방법이 권장 됩니다.

>[!NOTE]
> HoloLens (첫 번째 Gen) 및 HoloLen 2 모두에서 앱을 지원 하려면 두 개의 앱 패키지를 업로드 해야 합니다. HoloLens (첫 번째 Gen) 및 HoloLens 2에 대 한 ARM 또는 ARM64을 포함 하는 x86을 포함 하는 하나입니다. 
> 
> 패키지에 ARM 및 ARM64를 모두 포함 하는 경우 ARM64 버전은 HoloLens 2에 사용 됩니다. 

>[!NOTE]
> 여러 대상 장치 패밀리에 적용 될 단일 패키지를 선언할 수 있습니다.

## <a name="testing-your-app"></a>앱 테스트

### <a name="windows-app-certification-kit"></a>Windows 앱 인증 키트

Visual Studio를 통해 파트너 센터에 제출할 앱 패키지를 만들 때 앱 패키지 만들기 마법사는 생성 된 패키지에 대해 Windows 앱 인증 키트를 실행 하 라는 메시지를 표시 합니다. 저장소에 대 한 원활한 전송 프로세스를 수행 하려면 스토어에 제출 하기 전에 앱의 로컬 복사본이 [Windows 앱 인증 키트 테스트](/previous-versions/windows/apps/jj657973(v=win.10)) 를 통과 하는지 확인 하는 것이 가장 좋습니다. 원격 HoloLens에서 Windows 앱 인증 키트를 실행 하는 것은 현재 지원 되지 않습니다.

### <a name="run-on-all-targeted-device-families"></a>모든 대상 장치 제품군에서 실행

Windows 범용 플랫폼을 사용 하 여 모든 Windows 10 장치 제품군에서 실행 되는 단일 응용 프로그램을 만들 수 있습니다. 그러나 유니버설 Windows 앱이 모든 장치 제품군 에서만 작동 하도록 보장 하지는 않습니다. 선택 된 각 장치 제품군에서 [앱을 테스트](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) 하 여 좋은 환경을 보장 하는 것이 중요 합니다.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>혼합 현실 앱을 스토어에 제출

Unity 프로젝트를 기반으로 하는 혼합 현실 앱을 제출 하는 경우 먼저이 [비디오](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 를 참조 하세요.

일반적으로 HoloLens 또는 모던 헤드셋에서 작동 하는 Windows Mixed Reality 앱을 제출 하는 것은 Microsoft Store에 UWP 앱을 제출 하는 것과 같습니다. [이름을 예약 하 여 앱을 만들었으면](/windows/uwp/publish/create-your-app-by-reserving-a-name) [UWP 제출 검사 목록](/windows/uwp/publish/app-submissions)을 따릅니다.

가장 먼저 수행할 작업 중 하나는 혼합 현실 환경에 대 한 [범주 및 하위](/windows/uwp/publish/category-and-subcategory-table) 범주를 선택 하는 것입니다. **앱에 대해 가장 정확한 범주를 선택** 하는 것이 중요 합니다. 범주를 사용 하면 올바른 저장소 범주에서 응용 프로그램을 상품 하 고 관련 검색 쿼리를 사용 하 여 표시 되도록 할 수 있습니다. **VR 타이틀을 게임으로 나열 해도 앱에 대 한 노출이 더 우수 하지 않으며, 더 잘** 맞춤 되 고 복잡 한 범주에 표시 되지 않을 수 있습니다.

그러나 제출 프로세스에는 다음과 같은 네 가지 주요 영역이 있습니다.
1. [속성](/windows/uwp/publish/enter-app-properties)의 **[제품 선언](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 섹션에서
2. **[시스템 요구 사항](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 섹션의 [속성](/windows/uwp/publish/enter-app-properties)아래에 있습니다.
3. [패키지](/windows/uwp/publish/upload-app-packages)의 **[장치 제품군 가용성](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 섹션에서
4. **[저장소 목록 페이지](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 의 여러 필드에 있습니다.

### <a name="mixed-reality-product-declarations"></a>혼합 현실 제품 선언

앱 제출 프로세스의 **[속성](/windows/uwp/publish/enter-app-properties)** 페이지에는 **[제품 선언](/windows/uwp/publish/app-declarations)** 섹션에서 혼합 현실과 관련 된 몇 가지 옵션이 있습니다.

![혼합 현실 제품 선언](images/product-declarations-900px.png)<br>
혼합 현실 제품 선언

먼저 앱에서 혼합 현실 환경을 제공 하는 장치 유형을 확인 해야 합니다. 장치 유형을 식별 하면 앱이 스토어의 Windows Mixed Reality 컬렉션에 포함 됩니다.

"이 환경은 다음에 Windows Mixed Reality 하도록 설계 되었습니다."
* 모던 헤드셋이 사용자의 PC에 연결 된 경우 앱에서 VR 환경을 제공 하는 경우 **PC** 상자를 확인 합니다. 앱이 몰입 형 헤드셋에서 독점적으로 실행 되도록 설정 되어 있는지 또는 헤드셋이 연결 된 경우 혼합 현실 모드 또는 보너스 콘텐츠를 제공 하는 표준 PC 게임 인지 아니면이 확인란을 선택 하는 것이 좋습니다.
* 앱이 HoloLens에서 실행 될 때 holographic 환경을 제공 하는 경우에만 **HoloLens** 상자를 확인 합니다.
* 앱이 두 장치 유형에 혼합 된 현실 환경을 제공 하는 경우 두 상자를 **모두** 선택 합니다.

위의 "PC"를 선택한 경우 "Mixed Reality setup" (활동 수준)을 설정 하는 것이 좋습니다. 이는 HoloLens의 혼합 현실 앱이 세계 규모가 고 사용자가 설치 중에 경계를 정의 하지 않으므로 몰입 형 헤드셋에 연결 된 pc에서 실행 되는 혼합 현실 환경에만 적용 됩니다.
* 사용자가 한 위치에 유지 되도록 앱을 디자인 한 경우에는 **장착 된 + 순위** 를 선택 합니다. 예를 들어 항공기 환경을 제어 하 고 있는 게임에서.
* 사용자가 설치 하는 동안 정의 된 경계 내에서 사용자가 탐색할 수 있도록 앱이 설계 된 경우 **모든 환경을** 선택 합니다. 예를 들어,는 공격을 회피 하기 위한 병렬 및 오리의 게임 일 수 있습니다.

### <a name="mixed-reality-system-requirements"></a>혼합 현실 시스템 요구 사항

앱 제출 프로세스의 **[속성](/windows/uwp/publish/enter-app-properties)** 페이지에는 **[시스템 요구 사항](/windows/uwp/publish/enter-app-properties#system-requirements)** 섹션에서 혼합 현실과 관련 된 몇 가지 옵션이 있습니다.

![시스템 요구 사항](images/system-reqs-800px.png)<br>
시스템 요구 사항

이 섹션에서는 혼합 현실 앱에 대 한 최소 (필수) 하드웨어 및 권장 (선택 사항) 하드웨어를 식별 합니다.

**입력 하드웨어:**

확인란을 사용 하 여 앱에서 [음성 입력](../design/voice-input.md) **을 지 원하는** 경우 잠재 고객에 게 알릴 수 있습니다), **[Xbox 컨트롤러나 게임 패드](../discover/hardware-accessories.md#bluetooth-gamepads)** 또는 **[Windows Mixed Reality 동작 컨트롤러](../design/motion-controllers.md)** 를 제공 합니다. 이 정보는 스토어의 앱 제품 세부 정보 페이지에 표시 되며 앱이 적절 한 앱/게임 컬렉션에 포함 되는 데 도움이 됩니다. 예를 들어 이동 컨트롤러를 지 원하는 모든 게임에 대해 컬렉션이 있을 수 있습니다.

"최소 하드웨어" 또는 입력 형식에 대 한 "권장 하드웨어" 확인란을 선택 하는 방법에 대해 설명 합니다. 

예를 들어: 
* 게임에 동작 컨트롤러가 필요 하지만 마이크를 통한 음성 입력이 허용 되는 경우 "Windows Mixed Reality 동작 컨트롤러" 옆에 있는 "최소 하드웨어" 확인란을 선택 하 고 "마이크" 옆에 있는 "권장 하드웨어" 확인란을 선택 합니다. 
* xbox 컨트롤러, 게임 패드 또는 동작 컨트롤러 중 하나를 사용 하 여 게임을 재생할 수 있는 경우 "xbox 컨트롤러 또는 게임 패드" 옆에 있는 "최소 하드웨어" 확인란을 선택 하 고, 동작 컨트롤러가 게임 패드의 단계별 경험을 제공할 수 있으므로 "Windows Mixed Reality 동작 컨트롤러" 옆에 있는 "권장 하드웨어" 확인란을 선택 합니다.

**Windows Mixed Reality 모던 헤드셋:**

응용 프로그램을 사용 하는 데 몰입 형 헤드셋이 필요 하거나 선택 사항 인지 여부를 나타내는 것은 고객 만족도 및 교육에 매우 중요 합니다.

앱을 몰입 형 헤드셋을 통해서만 사용할 수 있는 경우 "Windows Mixed Reality 몰입 형 헤드셋" 옆 *에 있는 "* 최소 하드웨어" 확인란을 선택 합니다. 이는 구매 단추 위에 경고로 스토어의 앱 제품 세부 정보 페이지에 표시 되며, 고객이 기존 데스크톱 앱과 같은 PC에서 작동 하는 앱을 구매 하는 것으로 생각 하지 않습니다.

앱이 기존 PC 앱과 같은 데스크톱에서 실행 되는 경우 모던 헤드셋이 연결 된 경우 (앱의 전체 콘텐츠를 사용할 수 있는지 여부에 관계 없이) VR 환경을 제공 하지만 "Windows Mixed Reality 몰입 헤드셋" 옆의 "권장 하드웨어" 확인란을 선택 합니다. 앱이 몰입 형 헤드셋이 연결 되지 않은 기존 데스크톱 앱으로 작동 하는 경우 앱의 제품 세부 정보 페이지에서 [구매] 단추 위에 경고가 표시 되지 않습니다.

**PC 사양:**

앱이 최대한 많은 Windows Mixed Reality의 모던 헤드셋 사용자에 게 도달 하 게 하려면 [통합 그래픽이 포함 된 Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)pc의 pc 사양을 [대상](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) 으로 지정 합니다.

혼합 현실 앱이 최소 Windows Mixed Reality pc 요구 사항을 대상으로 하는지 또는 [Windows Mixed Reality Ultra PC]의 전용 GPU와 같은 특정 pc 구성이 필요한 지 여부에 관계 없이 https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines "최소 하드웨어" 열에 관련 pc 사양을 추가 해야 합니다.

혼합 현실 앱이 성능 향상을 위해 설계 되었거나 특정 PC 구성 또는 그래픽 카드에서 고해상도 그래픽을 제공 하는 경우 "권장 하드웨어" 열에 관련 PC 사양을 포함 해야 합니다.

혼합 현실 앱에서 PC에 연결 된 몰입 형 헤드셋을 사용 하는 경우에만 적용 됩니다. 혼합 현실 앱이 HoloLens 에서만 실행 되는 경우 하드웨어 구성이 하나만 HoloLens PC 사양을 지정할 필요가 없습니다.

### <a name="device-family-availability"></a>디바이스 패밀리 가용성

Visual Studio에서 [앱을 올바르게 패키지](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) 한 경우 패키지 페이지에 업로드 하면 사용 가능한 장치 패밀리가 있는 테이블이 생성 됩니다.

![장치 패밀리 가용성 테이블](images/device-family-table-900px.png)<br>
장치 패밀리 가용성 테이블

혼합 현실 앱이 몰입 형 헤드셋에서 작동 하는 경우 테이블에서 "Windows 10 Desktop"을 선택 해야 합니다. 혼합 현실 앱이 HoloLens에서 작동 하는 경우 "Windows 10 Holographic" 이상을 선택 해야 합니다. 앱이 Windows Mixed Reality 헤드셋 유형 둘 다에서 실행 되는 경우 "Windows 10 Desktop" 및 "Windows 10 Holographic"를 모두 선택 해야 합니다.

>[!TIP]
>파트너 센터에서 패키지 매니페스트와 앱/게시자 계정 정보 간의 불일치와 관련 된 응용 프로그램의 패키지를 업로드할 때 많은 개발자가 오류를 실행 합니다. 이러한 오류는 Windows 개발자 계정 (파트너 센터에 로그인 하는 데 사용 하는 계정)과 연결 된 동일한 계정으로 Visual Studio에 로그인 하 여 방지할 수 있습니다. 동일한 계정을 사용 하는 경우 앱을 패키지 하기 전에 Microsoft Store에서 해당 id와 앱을 연결할 수 있습니다.

![앱을 Microsoft Store 연결](images/associate-your-app-700px.png)<br>
Visual Studio의 Microsoft Store에 앱 연결

### <a name="store-listing-page"></a>스토어 목록 페이지

앱 제출 프로세스의 [스토어 목록](/windows/uwp/publish/create-app-store-listings) 페이지에는 혼합 현실 앱에 대 한 유용한 정보를 추가할 수 있는 여러 위치가 있습니다.

>[!IMPORTANT]
>앱이 스토어에 의해 올바르게 분류 되 고 Windows Mixed Reality 고객에 대해 검색 가능 하도록 하려면 " **Windows Mixed Reality"** 를 앱에 대 한 "검색 용어" 중 하나로 추가 해야 합니다. "공유 필드" 섹션을 확장 하 여 검색 단어를 찾을 수 있습니다.

![검색 단어에 Windows Mixed Reality 추가](images/search-terms-800px.png)<br>
검색어에 "Windows Mixed Reality" 추가

## <a name="offering-a-free-trial-for-your-game-or-app"></a>게임 또는 앱에 대 한 무료 평가판 제공

대부분의 경우 고객은 Windows Mixed Reality 몰입 형 헤드셋을 구입 하기 전에 가상 현실에 대 한 경험이 없도록 제한 됩니다. 이는 강한 게임에서 발생 하는 것을 알 수 없거나 몰입 형 환경에서 자신의 편안 함 임계값에 익숙해질 수 있습니다. 많은 고객이 [Windows Mixed Reality pc](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)로 직장 배지가 달린 되지 않는 pc에서 Windows Mixed Reality 몰입 형 헤드셋을 사용해 볼 수도 있습니다. 이러한 고려 사항 때문에 유료 현실 앱 또는 게임의 [무료 평가판](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 을 제공 하는 것이 좋습니다.

## <a name="see-also"></a>추가 정보
* [혼합 현실이란?](../discover/mixed-reality.md)
* [개발 개요](../develop/development.md)
* [앱 보기](../design/app-views.md)
* [혼합 현실 성능 이해](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity의 성능 권장 사항](../develop/unity/performance-recommendations-for-unity.md)
* [HoloLens에서 앱 테스트](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)