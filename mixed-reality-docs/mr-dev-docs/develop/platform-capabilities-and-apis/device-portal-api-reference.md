---
title: 디바이스 포털 API 참조
description: Windows Device Portal API에 대 한 최신 상태를 유지 하세요.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, Windows 장치 포털, API, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: cdbe9635fc51a0d19c978b72fdc8d5db6b8e8e01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581258"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="ccf8e-104">디바이스 포털 API 참조</span><span class="sxs-lookup"><span data-stu-id="ccf8e-104">Device portal API reference</span></span>

<span data-ttu-id="ccf8e-105">[Windows 장치 포털](using-the-windows-device-portal.md) 의 모든 항목은 데이터에 액세스 하 고 프로그래밍 방식으로 장치를 제어 하는 데 사용할 수 있는 REST API의 맨 위에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="ccf8e-106">앱 배포</span><span class="sxs-lookup"><span data-stu-id="ccf8e-106">App deloyment</span></span>

<span data-ttu-id="ccf8e-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="ccf8e-108">앱을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-108">Uninstalls an app</span></span>

<span data-ttu-id="ccf8e-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-109">Parameters</span></span>
* <span data-ttu-id="ccf8e-110">package: 제거할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="ccf8e-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="ccf8e-112">앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-112">Installs an App</span></span>

<span data-ttu-id="ccf8e-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-113">Parameters</span></span>
* <span data-ttu-id="ccf8e-114">package: 설치할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="ccf8e-115">Payload</span><span class="sxs-lookup"><span data-stu-id="ccf8e-115">Payload</span></span>
* <span data-ttu-id="ccf8e-116">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="ccf8e-116">multi-part conforming http body</span></span>

<span data-ttu-id="ccf8e-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="ccf8e-118">세부 정보를 사용 하 여 시스템에 설치 된 앱 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="ccf8e-119">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-119">Return data</span></span>
* <span data-ttu-id="ccf8e-120">세부 정보가 포함 된 설치 된 패키지 목록</span><span class="sxs-lookup"><span data-stu-id="ccf8e-120">List of installed packages with details</span></span>

<span data-ttu-id="ccf8e-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="ccf8e-122">진행 중인 앱 설치의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="ccf8e-123">덤프 컬렉션</span><span class="sxs-lookup"><span data-stu-id="ccf8e-123">Dump collection</span></span>

<span data-ttu-id="ccf8e-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="ccf8e-125">테스트용으로 로드 앱에 대 한 크래시 덤프 수집 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="ccf8e-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="ccf8e-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-126">Parameters</span></span>
* <span data-ttu-id="ccf8e-127">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-127">packageFullname : package name</span></span>

<span data-ttu-id="ccf8e-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="ccf8e-129">테스트용으로 로드 apps 크래시 덤프 컬렉션에 대 한 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="ccf8e-130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-130">Parameters</span></span>
* <span data-ttu-id="ccf8e-131">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-131">packageFullname : package name</span></span>

<span data-ttu-id="ccf8e-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="ccf8e-133">테스트용으로 로드 앱에 대 한 덤프 제어 설정을 사용 하도록 설정 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="ccf8e-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-134">Parameters</span></span>
* <span data-ttu-id="ccf8e-135">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-135">packageFullname : package name</span></span>

<span data-ttu-id="ccf8e-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="ccf8e-137">테스트용으로 로드 앱에 대 한 크래시 덤프를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ccf8e-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-138">Parameters</span></span>
* <span data-ttu-id="ccf8e-139">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-139">packageFullname : package name</span></span>
* <span data-ttu-id="ccf8e-140">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-140">fileName : dump file name</span></span>

<span data-ttu-id="ccf8e-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="ccf8e-142">테스트용으로 로드 앱에 대 한 크래시 덤프를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ccf8e-143">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-143">Parameters</span></span>
* <span data-ttu-id="ccf8e-144">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-144">packageFullname : package name</span></span>
* <span data-ttu-id="ccf8e-145">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-145">fileName : dump file name</span></span>

<span data-ttu-id="ccf8e-146">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-146">Return data</span></span>
* <span data-ttu-id="ccf8e-147">덤프 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-147">Dump file.</span></span> <span data-ttu-id="ccf8e-148">WinDbg 또는 Visual Studio를 사용 하 여 검사</span><span class="sxs-lookup"><span data-stu-id="ccf8e-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="ccf8e-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="ccf8e-150">테스트용으로 로드 apps에 대 한 모든 크래시 덤프 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="ccf8e-151">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-151">Return data</span></span>
* <span data-ttu-id="ccf8e-152">테스트용으로 로드 된 앱 당 크래시 덤프 목록</span><span class="sxs-lookup"><span data-stu-id="ccf8e-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="ccf8e-153">ETW</span><span class="sxs-lookup"><span data-stu-id="ccf8e-153">ETW</span></span>

<span data-ttu-id="ccf8e-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="ccf8e-155">등록 된 공급자를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-155">Enumerates registered providers</span></span>

<span data-ttu-id="ccf8e-156">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-156">Return data</span></span>
* <span data-ttu-id="ccf8e-157">공급자 목록, 이름 및 GUID</span><span class="sxs-lookup"><span data-stu-id="ccf8e-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="ccf8e-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="ccf8e-159">실시간 ETW 세션을 만듭니다. websocket을 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="ccf8e-160">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-160">Return data</span></span>
* <span data-ttu-id="ccf8e-161">활성화 된 공급자의 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="ccf8e-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="ccf8e-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="ccf8e-162">Holographic OS</span></span>

<span data-ttu-id="ccf8e-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="ccf8e-164">시스템에 등록 되지 않은 HoloLens 특정 ETW 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="ccf8e-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="ccf8e-166">실행 중인 모든 서비스의 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-166">Returns the states of all services running.</span></span>

<span data-ttu-id="ccf8e-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="ccf8e-168">저장 된 IPD (Interpupillary distance)를 밀리미터 단위로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="ccf8e-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="ccf8e-170">IPD를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-170">Sets the IPD</span></span>

<span data-ttu-id="ccf8e-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-171">Parameters</span></span>
* <span data-ttu-id="ccf8e-172">ipd: 밀리미터로 지정할 New IPD 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="ccf8e-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="ccf8e-174">장치 포털에 대 한 HTTPS 요구 사항 가져오기</span><span class="sxs-lookup"><span data-stu-id="ccf8e-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ccf8e-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="ccf8e-176">장치 포털에 대 한 HTTPS 요구 사항을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ccf8e-177">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-177">Parameters</span></span>
* <span data-ttu-id="ccf8e-178">필수: 예, 아니요 또는 기본값</span><span class="sxs-lookup"><span data-stu-id="ccf8e-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="ccf8e-179">Holographic 인식</span><span class="sxs-lookup"><span data-stu-id="ccf8e-179">Holographic Perception</span></span>

<span data-ttu-id="ccf8e-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="ccf8e-181">Websocket 업그레이드를 수락 하 고 30fps로 업데이트를 전송 하는 인식 클라이언트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="ccf8e-182">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-182">Parameters</span></span>
* <span data-ttu-id="ccf8e-183">clientmode: "활성"은 동적으로 설정할 수 없는 경우 시각적 추적 모드를 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="ccf8e-184">Holographic 열</span><span class="sxs-lookup"><span data-stu-id="ccf8e-184">Holographic Thermal</span></span>

<span data-ttu-id="ccf8e-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="ccf8e-186">장치의 열 단계 가져오기 (0 보통, 1 웜, 2 개 위험)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="ccf8e-187">맵 관리자</span><span class="sxs-lookup"><span data-stu-id="ccf8e-187">Map Manager</span></span>

<span data-ttu-id="ccf8e-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="ccf8e-189">사용 가능한 맵 파일 (mapx) 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="ccf8e-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="ccf8e-191">사용 가능한 앵커 파일 (.. x x x) 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="ccf8e-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="ccf8e-193">사용 가능한 공간 재구성 데이터베이스 파일 (srdb) 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="ccf8e-194">**/api/holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="ccf8e-195">현재 사용자에 대해 지속형 앵커 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="ccf8e-196">파일 다운로드/업로드/삭제</span><span class="sxs-lookup"><span data-stu-id="ccf8e-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="ccf8e-197">**/api/holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="ccf8e-198">지도, 앵커 또는 공간 재구성 데이터베이스 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ccf8e-199">이 파일은 이전에 업로드 하거나 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ccf8e-200">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-200">Parameters</span></span>
* <span data-ttu-id="ccf8e-201">파일 이름: 다운로드할 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="ccf8e-202">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="ccf8e-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="ccf8e-204">지도, 앵커 또는 공간 재구성 데이터베이스 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ccf8e-205">파일이 업로드 되 면 나중에 시스템에서 사용 하기 위해 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="ccf8e-206">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-206">Parameters</span></span>
* <span data-ttu-id="ccf8e-207">file: 업로드할 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="ccf8e-208">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="ccf8e-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="ccf8e-210">지도, 앵커 또는 공간 재구성 데이터베이스 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ccf8e-211">이 파일은 이전에 업로드 하거나 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ccf8e-212">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-212">Parameters</span></span>
* <span data-ttu-id="ccf8e-213">FileName: 삭제할 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="ccf8e-214">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="ccf8e-215">내보내기</span><span class="sxs-lookup"><span data-stu-id="ccf8e-215">Export</span></span>

<span data-ttu-id="ccf8e-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="ccf8e-217">시스템에서 현재 사용 중인 맵을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ccf8e-218">내보낸 후에는 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="ccf8e-219">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="ccf8e-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="ccf8e-221">시스템에서 현재 사용 중인 맵을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ccf8e-222">내보낸 후에는 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="ccf8e-223">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="ccf8e-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="ccf8e-225">시스템에서 현재 사용 중인 맵과 앵커를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="ccf8e-226">내보낸 후에는 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="ccf8e-227">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="ccf8e-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ccf8e-229">시스템에서 현재 사용 중인 맵 및 공간 재구성 데이터베이스를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="ccf8e-230">내보낸 후에는 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="ccf8e-231">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="ccf8e-232">가져오기</span><span class="sxs-lookup"><span data-stu-id="ccf8e-232">Import</span></span>

<span data-ttu-id="ccf8e-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="ccf8e-234">현재 사용 해야 하는 맵을 시스템에 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="ccf8e-235">내보내거나 업로드 한 파일에 대해를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ccf8e-236">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-236">Parameters</span></span>
* <span data-ttu-id="ccf8e-237">FileName: 사용할 맵의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="ccf8e-238">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ccf8e-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="ccf8e-240">현재 사용 해야 하는 앵커를 시스템에 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="ccf8e-241">내보내거나 업로드 한 파일에 대해를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ccf8e-242">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-242">Parameters</span></span>
* <span data-ttu-id="ccf8e-243">FileName: 사용할 앵커의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="ccf8e-244">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ccf8e-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ccf8e-246">현재 사용 되는 공간 재구성 데이터베이스를 시스템에 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="ccf8e-247">내보내거나 업로드 한 파일에 대해를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ccf8e-248">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-248">Parameters</span></span>
* <span data-ttu-id="ccf8e-249">FileName: 사용할 공간 매핑 db의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="ccf8e-250">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="ccf8e-251">기타</span><span class="sxs-lookup"><span data-stu-id="ccf8e-251">Other</span></span>

<span data-ttu-id="ccf8e-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="ccf8e-253">시스템을 맵, 앵커 및 공간 재구성 데이터베이스로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="ccf8e-254">예제:</span><span class="sxs-lookup"><span data-stu-id="ccf8e-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="ccf8e-255">**/api/holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="ccf8e-256">마지막으로 가져온 맵, 앵커 및 공간 재구성 데이터베이스 파일을 포함 하 여 시스템의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="ccf8e-257">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="ccf8e-257">Mixed Reality Capture</span></span>

<span data-ttu-id="ccf8e-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="ccf8e-259">장치에서 혼합 된 현실 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="ccf8e-260">스트리밍을 위해 op = stream 쿼리 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="ccf8e-261">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-261">Parameters</span></span>
* <span data-ttu-id="ccf8e-262">filename: hex64로 인코딩된 비디오 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="ccf8e-263">op: stream</span><span class="sxs-lookup"><span data-stu-id="ccf8e-263">op : stream</span></span>

<span data-ttu-id="ccf8e-264">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="ccf8e-265">장치에서 혼합 된 현실 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="ccf8e-266">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-266">Parameters</span></span>
* <span data-ttu-id="ccf8e-267">filename: 삭제할 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="ccf8e-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="ccf8e-269">장치에 저장 된 혼합 현실 파일의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="ccf8e-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="ccf8e-271">혼합 현실 사진을 사용 하 고 장치에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="ccf8e-272">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-272">Parameters</span></span>
* <span data-ttu-id="ccf8e-273">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-274">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-275">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="ccf8e-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="ccf8e-277">기본 혼합 현실 캡처 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="ccf8e-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="ccf8e-279">기본 혼합 현실 캡처 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="ccf8e-280">이러한 설정 중 일부는 시스템의 MRC 사진 및 비디오 캡처에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="ccf8e-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="ccf8e-282">Windows 장치 포털 내 혼합 현실 캡처의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="ccf8e-283">\**_응답_* _</span><span class="sxs-lookup"><span data-stu-id="ccf8e-283">\**_Response_* _</span></span>

<span data-ttu-id="ccf8e-284">응답에는 Windows 장치 포털이 비디오를 기록 하 고 있는지 여부를 나타내는 JSON 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="ccf8e-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span><span class="sxs-lookup"><span data-stu-id="ccf8e-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="ccf8e-286">지정 된 파일에 대 한 미리 보기 이미지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="ccf8e-287">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-287">Parameters</span></span>
* <span data-ttu-id="ccf8e-288">파일 이름: 미리 보기를 요청 하는 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="ccf8e-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="ccf8e-290">혼합 현실 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="ccf8e-291">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-291">Parameters</span></span>
* <span data-ttu-id="ccf8e-292">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-293">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-294">mic: 마이크 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-295">루프백: 응용 프로그램 오디오 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-296">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ccf8e-297">vstab: (HoloLens 2만 해당) 비디오 안정화 사용: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="ccf8e-298">vstabbuffer: (HoloLens 2만 해당) 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ccf8e-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="ccf8e-300">현재 혼합 된 현실 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="ccf8e-301">혼합 현실 스트리밍</span><span class="sxs-lookup"><span data-stu-id="ccf8e-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="ccf8e-302">루프백 격리로 인해 장치의 앱 내에서 혼합 현실 스트리밍에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="ccf8e-303">HoloLens는 조각화 된 mp4의 청크 다운로드를 통해 혼합 현실의 실시간 미리 보기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="ccf8e-304">혼합 현실 스트림은 동일한 매개 변수 집합을 공유 하 여 캡처할 항목을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="ccf8e-305">holo: capture holograms: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="ccf8e-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="ccf8e-306">pv: PV 카메라 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="ccf8e-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="ccf8e-307">mic: 마이크 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="ccf8e-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="ccf8e-308">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="ccf8e-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="ccf8e-309">이러한 항목이 지정 되지 않은 경우 holograms, photo/video 카메라 및 앱 오디오가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="ccf8e-310">지정 된 경우: 지정 되지 않은 매개 변수는 기본적으로 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="ccf8e-311">선택적 매개 변수 (HoloLens 2에만 해당)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="ccf8e-312">RenderFromCamera: photo/video 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ccf8e-313">vstab: 비디오 안정화 사용: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="ccf8e-314">vstabbuffer: 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ccf8e-315">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="ccf8e-316">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ccf8e-317">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="ccf8e-318">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ccf8e-319">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="ccf8e-320">854x480p 30fps 2.5 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="ccf8e-321">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="ccf8e-322">428x240p 15fps 0.6 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="ccf8e-323">네트워킹</span><span class="sxs-lookup"><span data-stu-id="ccf8e-323">Networking</span></span>

<span data-ttu-id="ccf8e-324">**/sh/svring/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="ccf8e-325">현재 ip 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="ccf8e-326">OS 정보</span><span class="sxs-lookup"><span data-stu-id="ccf8e-326">OS Information</span></span>

<span data-ttu-id="ccf8e-327">**///s/정보 (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="ccf8e-328">운영 체제 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-328">Gets operating system information</span></span>

<span data-ttu-id="ccf8e-329">**/api/oss (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="ccf8e-330">컴퓨터 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-330">Gets the machine name</span></span>

<span data-ttu-id="ccf8e-331">**/api/oss (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="ccf8e-332">컴퓨터 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-332">Sets the machine name</span></span>

<span data-ttu-id="ccf8e-333">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-333">Parameters</span></span>
* <span data-ttu-id="ccf8e-334">이름: 새 컴퓨터 이름, hex64 인코딩,를로 설정</span><span class="sxs-lookup"><span data-stu-id="ccf8e-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="ccf8e-335">인식 시뮬레이션 컨트롤</span><span class="sxs-lookup"><span data-stu-id="ccf8e-335">Perception Simulation Control</span></span>

<span data-ttu-id="ccf8e-336">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="ccf8e-337">시뮬레이션 모드 가져오기</span><span class="sxs-lookup"><span data-stu-id="ccf8e-337">Get the simulation mode</span></span>

<span data-ttu-id="ccf8e-338">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="ccf8e-339">시뮬레이션 모드 설정</span><span class="sxs-lookup"><span data-stu-id="ccf8e-339">Set the simulation mode</span></span>

<span data-ttu-id="ccf8e-340">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-340">Parameters</span></span>
* <span data-ttu-id="ccf8e-341">모드: 시뮬레이션 모드: 기본값, 시뮬레이션, 원격, 레거시</span><span class="sxs-lookup"><span data-stu-id="ccf8e-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="ccf8e-342">**/api/holographic/simulation/control/stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="ccf8e-343">컨트롤 스트림을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-343">Delete a control stream.</span></span>

<span data-ttu-id="ccf8e-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ccf8e-345">컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="ccf8e-346">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="ccf8e-347">컨트롤 스트림 (우선 순위는 필수)을 만들거나 만든 스트림에 데이터를 게시 합니다 (streamId 필요).</span><span class="sxs-lookup"><span data-stu-id="ccf8e-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="ccf8e-348">게시 된 데이터는 ' 응용 프로그램/8 진수 스트림 ' 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="ccf8e-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ccf8e-350">' 시뮬레이션 ' 모드일 때 시스템 디스플레이에 렌더링 된 콘텐츠가 포함 된 시뮬레이션 비디오 스트림을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="ccf8e-351">단순 형식 설명자 헤더는 처음에 전송 되 고, 그 뒤에는 각각 눈 인덱스와 질감 크기를 나타내는 헤더가 앞에 오는, 각각에는 h.264로 인코딩된 질감이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="ccf8e-352">인식 시뮬레이션 재생</span><span class="sxs-lookup"><span data-stu-id="ccf8e-352">Perception Simulation Playback</span></span>

<span data-ttu-id="ccf8e-353">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="ccf8e-354">기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-354">Delete a recording.</span></span>

<span data-ttu-id="ccf8e-355">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-355">Parameters</span></span>
* <span data-ttu-id="ccf8e-356">녹음/녹화: 삭제할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="ccf8e-357">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="ccf8e-358">기록을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-358">Upload a recording.</span></span>

<span data-ttu-id="ccf8e-359">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="ccf8e-360">모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-360">Get all recordings.</span></span>

<span data-ttu-id="ccf8e-361">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="ccf8e-362">기록의 현재 재생 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="ccf8e-363">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-363">Parameters</span></span>
* <span data-ttu-id="ccf8e-364">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-364">recording : Name of recording.</span></span>

<span data-ttu-id="ccf8e-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="ccf8e-366">기록을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-366">Unload a recording.</span></span>

<span data-ttu-id="ccf8e-367">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-367">Parameters</span></span>
* <span data-ttu-id="ccf8e-368">녹음/녹화: 언로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="ccf8e-369">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="ccf8e-370">기록을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-370">Load a recording.</span></span>

<span data-ttu-id="ccf8e-371">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-371">Parameters</span></span>
* <span data-ttu-id="ccf8e-372">기록: 로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="ccf8e-373">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="ccf8e-374">로드 된 모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-374">Get all loaded recordings.</span></span>

<span data-ttu-id="ccf8e-375">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="ccf8e-376">기록을 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-376">Pause a recording.</span></span>

<span data-ttu-id="ccf8e-377">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-377">Parameters</span></span>
* <span data-ttu-id="ccf8e-378">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-378">recording : Name of recording.</span></span>

<span data-ttu-id="ccf8e-379">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="ccf8e-380">기록을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-380">Play a recording.</span></span>

<span data-ttu-id="ccf8e-381">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-381">Parameters</span></span>
* <span data-ttu-id="ccf8e-382">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-382">recording : Name of recording.</span></span>

<span data-ttu-id="ccf8e-383">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="ccf8e-384">기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-384">Stop a recording.</span></span>

<span data-ttu-id="ccf8e-385">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-385">Parameters</span></span>
* <span data-ttu-id="ccf8e-386">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-386">recording : Name of recording.</span></span>

<span data-ttu-id="ccf8e-387">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="ccf8e-388">로드 된 기록에서 데이터의 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="ccf8e-389">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-389">Parameters</span></span>
* <span data-ttu-id="ccf8e-390">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="ccf8e-391">인식 시뮬레이션 기록</span><span class="sxs-lookup"><span data-stu-id="ccf8e-391">Perception Simulation Recording</span></span>

<span data-ttu-id="ccf8e-392">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="ccf8e-393">기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-393">Start a recording.</span></span> <span data-ttu-id="ccf8e-394">한 번에 하나의 기록만 활성화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="ccf8e-395">헤드, 손, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="ccf8e-396">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-396">Parameters</span></span>
* <span data-ttu-id="ccf8e-397">head: 1로 설정 하 여 헤드 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="ccf8e-398">실습: 1로 설정 하 여 손으로 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="ccf8e-399">spatialMapping: 1로 설정 하 여 공간 매핑을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="ccf8e-400">환경: 환경 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="ccf8e-401">이름: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-401">name : Name of the recording.</span></span>
* <span data-ttu-id="ccf8e-402">singleSpatialMappingFrame: 단일 공간 매핑 프레임만 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="ccf8e-403">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="ccf8e-404">기록 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-404">Get recording state.</span></span>

<span data-ttu-id="ccf8e-405">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="ccf8e-406">현재 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-406">Stop the current recording.</span></span> <span data-ttu-id="ccf8e-407">기록이 파일로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="ccf8e-408">성능 데이터</span><span class="sxs-lookup"><span data-stu-id="ccf8e-408">Performance data</span></span>

<span data-ttu-id="ccf8e-409">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="ccf8e-410">세부 정보를 사용 하 여 실행 중인 프로세스의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="ccf8e-411">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-411">Return data</span></span>
* <span data-ttu-id="ccf8e-412">프로세스 목록 및 각 프로세스에 대 한 세부 정보를 포함 하는 JSON</span><span class="sxs-lookup"><span data-stu-id="ccf8e-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="ccf8e-413">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="ccf8e-414">시스템 성능 통계 (i/o 읽기/쓰기, 메모리 통계 등)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="ccf8e-415">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-415">Return data</span></span>
* <span data-ttu-id="ccf8e-416">시스템 정보를 포함 하는 JSON: CPU, GPU, 메모리, 네트워크, IO</span><span class="sxs-lookup"><span data-stu-id="ccf8e-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="ccf8e-417">고급</span><span class="sxs-lookup"><span data-stu-id="ccf8e-417">Power</span></span>

<span data-ttu-id="ccf8e-418">**/sh/svhhhhhs (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="ccf8e-419">현재 배터리 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-419">Gets the current battery state</span></span>

<span data-ttu-id="ccf8e-420">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="ccf8e-421">시스템이 저전원 상태 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="ccf8e-422">원격 제어</span><span class="sxs-lookup"><span data-stu-id="ccf8e-422">Remote Control</span></span>

<span data-ttu-id="ccf8e-423">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="ccf8e-424">대상 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-424">Restarts the target device</span></span>

<span data-ttu-id="ccf8e-425">**/sh/svcontroli (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="ccf8e-426">대상 장치를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="ccf8e-427">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="ccf8e-427">Task Manager</span></span>

<span data-ttu-id="ccf8e-428">**/api/taskmanager/app/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="ccf8e-429">최신 앱을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-429">Stops a modern app</span></span>

<span data-ttu-id="ccf8e-430">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-430">Parameters</span></span>
* <span data-ttu-id="ccf8e-431">패키지: 앱 패키지의 전체 이름, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="ccf8e-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="ccf8e-432">forcestop: 모든 프로세스를 강제로 중지 합니다 (= 예).</span><span class="sxs-lookup"><span data-stu-id="ccf8e-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="ccf8e-433">**/sh/svaryer/ps (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="ccf8e-434">최신 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-434">Starts a modern app</span></span>

<span data-ttu-id="ccf8e-435">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-435">Parameters</span></span>
* <span data-ttu-id="ccf8e-436">appid: 시작 하는 앱의 PRAID, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="ccf8e-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="ccf8e-437">패키지: 앱 패키지의 전체 이름, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="ccf8e-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="ccf8e-438">WiFi 관리</span><span class="sxs-lookup"><span data-stu-id="ccf8e-438">WiFi Management</span></span>

<span data-ttu-id="ccf8e-439">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="ccf8e-440">무선 네트워크 인터페이스를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="ccf8e-441">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-441">Return data</span></span>
* <span data-ttu-id="ccf8e-442">세부 정보를 포함 하는 무선 인터페이스 목록 (GUID, 설명 등)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="ccf8e-443">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="ccf8e-444">지정 된 인터페이스에서 네트워크와 연결 된 프로필을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="ccf8e-445">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-445">Parameters</span></span>
* <span data-ttu-id="ccf8e-446">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="ccf8e-446">interface : network interface guid</span></span>
* <span data-ttu-id="ccf8e-447">프로필: 프로필 이름</span><span class="sxs-lookup"><span data-stu-id="ccf8e-447">profile : profile name</span></span>

<span data-ttu-id="ccf8e-448">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="ccf8e-449">지정 된 네트워크 인터페이스의 무선 네트워크를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="ccf8e-450">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-450">Parameters</span></span>
* <span data-ttu-id="ccf8e-451">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="ccf8e-451">interface : network interface guid</span></span>

<span data-ttu-id="ccf8e-452">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-452">Return data</span></span>
* <span data-ttu-id="ccf8e-453">네트워크 인터페이스에서 찾을 수 있는 무선 네트워크 목록 (세부 정보 포함)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="ccf8e-454">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="ccf8e-455">지정 된 인터페이스의 네트워크에 연결 하거나 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="ccf8e-456">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-456">Parameters</span></span>
* <span data-ttu-id="ccf8e-457">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="ccf8e-457">interface : network interface guid</span></span>
* <span data-ttu-id="ccf8e-458">ssid: ssid, hex64 인코딩, 연결</span><span class="sxs-lookup"><span data-stu-id="ccf8e-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="ccf8e-459">op: 연결 또는 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ccf8e-459">op : connect or disconnect</span></span>
* <span data-ttu-id="ccf8e-460">createprofile: 예 또는 아니요</span><span class="sxs-lookup"><span data-stu-id="ccf8e-460">createprofile : yes or no</span></span>
* <span data-ttu-id="ccf8e-461">키: shared key, hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="ccf8e-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="ccf8e-462">Windows 성능 레코더</span><span class="sxs-lookup"><span data-stu-id="ccf8e-462">Windows Performance Recorder</span></span>

<span data-ttu-id="ccf8e-463">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="ccf8e-464">WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="ccf8e-465">Payload</span><span class="sxs-lookup"><span data-stu-id="ccf8e-465">Payload</span></span>
* <span data-ttu-id="ccf8e-466">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="ccf8e-466">multi-part conforming http body</span></span>

<span data-ttu-id="ccf8e-467">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-467">Return data</span></span>
* <span data-ttu-id="ccf8e-468">WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-468">Returns the WPR session status.</span></span>

<span data-ttu-id="ccf8e-469">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="ccf8e-470">WPR 세션의 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="ccf8e-471">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-471">Return data</span></span>
* <span data-ttu-id="ccf8e-472">WPR 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-472">WPR session status.</span></span>

<span data-ttu-id="ccf8e-473">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="ccf8e-474">WPR (성능) 추적 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="ccf8e-475">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-475">Return data</span></span>
* <span data-ttu-id="ccf8e-476">추적 ETL 파일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-476">Returns the trace ETL file</span></span>

<span data-ttu-id="ccf8e-477">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="ccf8e-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="ccf8e-478">WPR (성능) 추적 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="ccf8e-479">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf8e-479">Parameters</span></span>
* <span data-ttu-id="ccf8e-480">프로필: 프로필 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-480">profile : Profile name.</span></span> <span data-ttu-id="ccf8e-481">사용 가능한 프로필은 perfprofiles/profiles.js에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="ccf8e-482">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="ccf8e-482">Return data</span></span>
* <span data-ttu-id="ccf8e-483">시작 시 WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf8e-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccf8e-484">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccf8e-484">See also</span></span>
* [<span data-ttu-id="ccf8e-485">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="ccf8e-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="ccf8e-486">장치 포털 핵심 API 참조 (UWP)</span><span class="sxs-lookup"><span data-stu-id="ccf8e-486">Device Portal core API reference (UWP)</span></span>](/windows/uwp/debug-test-perf/device-portal-api-core)