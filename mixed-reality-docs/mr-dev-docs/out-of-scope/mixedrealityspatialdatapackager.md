---
title: Mixed Reality 공간 데이터 패키지 설명서
description: Mixed Reality 공간 데이터 패키지 도구는 이제 더 이상 사용되지 않으며 어떤 플랫폼에서도 작동하지 않습니다. 대신 맵 관리자 도구를 권장합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 914e22c4e80385c93696ebd978000978e1e03f57706d466bdbb3cfcd5843f69e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213168"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Mixed Reality 공간 데이터 패키지 설명서

>[!NOTE]
> 사용되지 않음 
> 
> 2020년 8월 1일 현재 이 도구는 더 이상 사용되지 않으며 어떤 플랫폼에서도 더 이상 작동하지 않습니다. 대신 장치 포털 [맵 관리자](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) 도구를 사용하는 것이 좋습니다. 
> 
> 이 도구와 해당 작업은 있는 그대로 제공됩니다. 알림 없이 변경될 수 있으며 향후 Windows 또는 Windows Mixed Reality HMD 릴리스와 호환되지 않을 수 있습니다. 


## <a name="download"></a>다운로드
 [여기에서 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip) 다운로드

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>공간 데이터 패키지 Mixed Reality</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>빠른 시작

Mixed Reality 공간 데이터 패키지 도구는 2단계 내보내기 및 가져오기 프로세스를 통해 대상 앱의 공간 데이터를 한 PC에서 다른 PC로 복사합니다. 도구는 관리자 권한으로 실행되어야 하며 가져올 때 기존 공간 데이터를 삭제합니다. 내보내기 는 기존 공간 데이터를 그대로 둡니다.

주요 요구 사항 및 제한 사항:

1. 도구는 관리자 권한으로 실행해야 합니다. 
2. 도구를 실행한 후 Mixed Reality 포털 불안정한 경우 PC를 다시 시작해야 할 수 있습니다.
3. 공간 데이터 버전 불일치 또는 비호환성이 발생하는 경우 도구가 실행되지 않습니다.
4. 도구가 가져올 때 기존 공간 데이터를 지웁
5. 가져오기 프로세스가 실패하면 이전에 내보내 백업하지 않은 경우 이전 데이터를 복원할 수 없습니다.
6. 공간 맵 데이터에 대한 "읽기 전용" 모드에 따라 가져오기 기능 품질이 제한됩니다.
***

## <a name="mapping-best-practices"></a>매핑 모범 사례

1. 제어판 기존 맵 지우기(설정 -> Mixed Reality -> 환경 -> 환경 데이터 지우기)
2. 적절한 추적을 위한 충분한 조명을 확인하고 잠긴 지도 모드를 실행하는 경우 동일한 조명을 유지 관리합니다.
3. 가능하면 어둡고 그림자가 있는 영역 옆의 높은 조명 영역을 방지하여 조명 동적 범위를 낮게 유지합니다.
4. 비어 있는 질감 없는 표면 최소화(예: 흰색 벽 위에 다양한 포스터 배치)
5. 장면에 동적 개체 없이 공간 매핑(예: 사람 이동)
6. 가져오기 시 맵 잠금(Insider Preview를 통해 사용 가능)
7. 품질 저하 및/또는 환경의 변경 내용(개체 레이아웃의 조명 또는 변경)을 추적할 때 맵 잠금을 해제하고 환경을 다시 검색합니다.
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>도우미 스크립트를 사용하여 Mixed Reality 공간 데이터 패키지 실행

맵 패키지 도구를 실행하는 MRSpatialPackagerHelperScript.ps1 제공했습니다. 


스크립트 매개 변수는 아래에 정의되어 있습니다.

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell 스크립트 예제 사용 및 출력

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>MixedRealitySpatialDataPackager.exe 사용하여 내보내는 방법
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

디바이스에서 맵을 내보내면 het.mapx 및 sa.mapx의 두 mapx 파일이 생성됩니다. 내보내기 프로세스 중에 지정된 앱 및 사용자가 만든 경계(있는 경우)를 제외한 모든 공간 앵커가 제거됩니다. 원본 패키지 제품군 이름은 기존 설치된 앱과 일치해야 합니다. 그렇지 않은 경우 exe가 실패합니다.

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>MixedRealitySpatialDataPackager.exe 사용하여 가져오는 방법
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
가져오기는 기존 공간 데이터를 삭제하고 지정된 디렉터리에서 데이터로 대체합니다. 앱 이름 입력은 공간 앵커와 같은 대상 앱의 패키지 이름을 지정하며, 대상 사용자 SID는 가져온 공간 앵커에 액세스할 수 있어야 하는 사용자를 지정합니다. 대상 패키지 패밀리 이름 및 사용자 SID는 PC의 기존 값과 일치해야 합니다. 그렇지 않을 경우 exe가 실패합니다.


***
## <a name="error-messages"></a>오류 메시지
또한 오류 아래의 오류 메시지는 HRESULT와 함께 제공됩니다.

### <a name="if-there-was-an-error-invalid-arguments"></a>잘못된 인수 오류가 있는 경우
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>실행 파일을 관리자 모드로 실행하지 않은 경우
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>드라이버를 사용하거나 사용하지 않도록 설정하는 동안 오류가 있는 경우
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>공간 데이터베이스 버전의 유효성을 검사하는 동안 오류가 발생한 경우
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>대상 가져오기/내보내기 앱에 제공된 패키지 패밀리 이름의 유효성을 검사하는 동안 오류가 있는 경우
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>사용자 SID의 유효성을 검사하는 동안 오류가 있는 경우
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>대상 또는 원본 공간 데이터 파일과 관련된 오류가 발생한 경우
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Spectrum/SharedRealitySvc 시작 및 중지와 관련된 오류가 있는 경우
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```