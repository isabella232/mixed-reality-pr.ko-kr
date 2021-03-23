---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855887"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="315b2-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="315b2-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="315b2-102">옵션</span><span class="sxs-lookup"><span data-stu-id="315b2-102">Option</span></span> | <span data-ttu-id="315b2-103">설명</span><span class="sxs-lookup"><span data-stu-id="315b2-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="315b2-104">연결할 HoloLens 2 디바이스의 IP 주소(및 옵션 포트)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="315b2-105">포트를 제공하지 않으면 기본값은 8265입니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="315b2-106">(선택 사항) 기본값은 8000입니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-106">(optional) Default 8000.</span></span> <span data-ttu-id="315b2-107">최대 네트워크 전송 속도(kb/s)입니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="315b2-108">(선택 사항) 수신 대기 서버 시작</span><span class="sxs-lookup"><span data-stu-id="315b2-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="315b2-109">(선택 사항) 수신할 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="315b2-110">HoloLens 디바이스에서 PC 또는 VM에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="315b2-111">(4.26에서는 사용되지 않음)연결할 HoloLens 1 디바이스의 IP 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="315b2-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="315b2-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="315b2-113">옵션</span><span class="sxs-lookup"><span data-stu-id="315b2-113">Option</span></span> | <span data-ttu-id="315b2-114">설명</span><span class="sxs-lookup"><span data-stu-id="315b2-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="315b2-115">연결할 HoloLens 2 디바이스의 IP 주소(및 선택적 포트, 기본값 8265) 또는 앱이 연결에 대해 수신 대기해야 하는 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="315b2-116">(선택 사항) 원격의 경우 PC 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="315b2-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="315b2-117">(선택 사항) 수신 대기 서버 시작</span><span class="sxs-lookup"><span data-stu-id="315b2-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="315b2-118">(선택 사항) 기본값은 8000입니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-118">(optional) Default 8000.</span></span> <span data-ttu-id="315b2-119">최대 네트워크 전송 속도(kb/s)입니다.</span><span class="sxs-lookup"><span data-stu-id="315b2-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="315b2-120">(선택 사항) 연결 코덱</span><span class="sxs-lookup"><span data-stu-id="315b2-120">(optional) Connection codec</span></span>  |