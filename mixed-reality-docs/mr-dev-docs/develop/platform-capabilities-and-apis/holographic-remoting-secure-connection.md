---
title: Holographic Remoting에 대 한 연결 보안 사용
description: 이 페이지에서는 플레이어와 원격 앱 간에 암호화 및 인증 된 연결을 사용 하도록 Holographic Remoting을 구성 하는 방법을 설명 합니다.
author: markkeinz
ms.author: makei
ms.date: 10/29/2020
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 보안, 인증, 서버 간
ms.openlocfilehash: 4004c7534092c73fe478130b9d957461bb34bcfa
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679592"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="dccf4-104">Holographic Remoting에 대 한 연결 보안 사용</span><span class="sxs-lookup"><span data-stu-id="dccf4-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="dccf4-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="dccf4-106">이 페이지에서는 Holographic Remoting의 네트워크 보안에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="dccf4-107">다음에 대 한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-107">You'll find information about</span></span>

* <span data-ttu-id="dccf4-108">Holographic 원격 컨텍스트의 보안 및 필요할 수 있는 이유</span><span class="sxs-lookup"><span data-stu-id="dccf4-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="dccf4-109">다른 사용 사례를 기반으로 권장 되는 측정값</span><span class="sxs-lookup"><span data-stu-id="dccf4-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="dccf4-110">Holographic Remoting 솔루션에서 보안 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="overview"></a><span data-ttu-id="dccf4-111">개요</span><span class="sxs-lookup"><span data-stu-id="dccf4-111">Overview</span></span>

<span data-ttu-id="dccf4-112">Holographic 원격은 네트워크를 통해 정보를 교환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="dccf4-113">보안 조치를 수행 하지 않는 경우 동일한 네트워크에서 악의적 사용자 통신의 무결성을 손상 하거나 기밀 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="dccf4-114">Windows 스토어의 샘플 앱 및 Holographic Remoting 플레이어에는 보안이 사용 하지 않도록 설정 된 상태로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="dccf4-115">이렇게 하면 샘플을 보다 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="dccf4-116">또한 개발을 빠르게 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="dccf4-117">그러나 필드 테스트 또는 프로덕션 사용을 위해 Holographic Remoting 솔루션에서 보안을 사용 하도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-117">For field testing or production use however, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="dccf4-118">Holographic Remoting의 보안. 사용 사례에 대해 올바르게 설정 하면 다음을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="dccf4-119">**정품:** 플레이어와 원격 앱 모두 다른 쪽이 자신에 게 클레임을 요구 하는 것을 확신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="dccf4-120">**기밀성:** 타사에서 플레이어와 원격 앱 간에 교환 되는 정보를 읽을 수 없음</span><span class="sxs-lookup"><span data-stu-id="dccf4-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="dccf4-121">**무결성:** 플레이어 및 원격에서 통신에 대 한 전송 중인 모든 변경 내용을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!TIP]
><span data-ttu-id="dccf4-122">보안 기능을 사용 하려면 [사용자 지정 플레이어](holographic-remoting-create-player.md) 와 [사용자 지정 원격 앱](holographic-remoting-create-host.md)을 모두 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="dccf4-123">보안 구현 계획</span><span class="sxs-lookup"><span data-stu-id="dccf4-123">Planning the security implementation</span></span>

<span data-ttu-id="dccf4-124">Holographic Remoting에서 보안을 사용 하도록 설정 하면 원격 라이브러리에서 네트워크를 통해 교환 되는 모든 데이터에 대해 암호화 및 무결성 검사를 자동으로 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-124">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="dccf4-125">그러나 적절 한 인증을 사용 하려면 몇 가지 추가 작업이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-125">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="dccf4-126">사용 사례에 따라 수행 해야 하는 작업은 무엇 이며,이 섹션의 나머지 부분에서는 필요한 단계를 파악 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-126">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="dccf4-127">이 문서에서는 일반 지침도 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-127">This article can only provide general guidance.</span></span> <span data-ttu-id="dccf4-128">확실 하지 않은 경우 사용 사례에 대 한 지침을 제공할 수 있는 보안 전문가에 게 문의 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-128">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="dccf4-129">첫 번째 용어: 네트워크 연결을 설명 하는 경우 _클라이언트_ 및 _서버_ 라는 용어가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-129">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="dccf4-130">서버는 알려진 끝점 주소에서 들어오는 연결을 수신 대기 하는 쪽 이며, 클라이언트는 서버 끝점에 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-130">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="dccf4-131">클라이언트 및 서버 역할은 앱이 플레이어 또는 원격 역할을 하는지 여부에 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-131">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="dccf4-132">예제에는 서버 역할의 플레이어가 있지만 사용 사례에 적합 한 경우 역할을 쉽게 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-132">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="dccf4-133">서버-클라이언트 인증 계획</span><span class="sxs-lookup"><span data-stu-id="dccf4-133">Planning the server-to-client authentication</span></span>

<span data-ttu-id="dccf4-134">서버는 디지털 인증서를 사용 하 여 클라이언트에 대 한 id를 증명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-134">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="dccf4-135">클라이언트는 연결 핸드셰이크 단계에서 서버 인증서의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-135">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="dccf4-136">클라이언트에서 서버를 신뢰 하지 않는 경우이 시점에서 연결이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-136">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="dccf4-137">클라이언트에서 서버 인증서의 유효성을 검사 하는 방법과 사용할 수 있는 서버 인증서 종류는 사용 사례에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-137">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="dccf4-138">**사용 사례 1:** 서버 호스트 이름이 고정 되어 있지 않거나 서버에서 호스트 이름으로 주소가 지정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-138">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="dccf4-139">이 사용 사례에서는 서버 호스트 이름에 대 한 인증서를 발급 하는 것이 실용적이 지 않거나 가능 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-139">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="dccf4-140">여기서 권장 사항은 대신 인증서의 지문을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-140">The recommendation here is to validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="dccf4-141">인간 지문과 마찬가지로, 지 문은 인증서를 고유 하 게 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-141">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="dccf4-142">지문을 클라이언트에 대역 외로 전달 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-142">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="dccf4-143">즉, 원격 작업에 사용 되는 것과 동일한 네트워크 연결을 통해 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-143">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="dccf4-144">대신, 클라이언트의 구성에 수동으로 입력 하거나 클라이언트에서 QR 코드를 검색 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-144">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="dccf4-145">**사용 사례 2:** 안정적인 호스트 이름을 통해 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-145">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="dccf4-146">이 사용 사례에서 서버에는 특정 호스트 이름이 있으며이 이름은 변경 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-146">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="dccf4-147">그런 다음 서버 호스트 이름에 발급 된 인증서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-147">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="dccf4-148">트러스트는 호스트 이름 및 인증서의 신뢰 체인에 따라 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-148">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="dccf4-149">이 옵션을 선택 하는 경우 클라이언트는 서버의 호스트 이름 및 루트 인증서를 미리 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-149">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="dccf4-150">클라이언트와 서버 간 인증 계획</span><span class="sxs-lookup"><span data-stu-id="dccf4-150">Planning the client-to-server authentication</span></span>

<span data-ttu-id="dccf4-151">클라이언트는 자유 형식 토큰을 사용 하 여 서버에 대해 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-151">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="dccf4-152">이 토큰에 포함 되어야 하는 항목은 사용 사례에 따라 다음과 같이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-152">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="dccf4-153">**사용 사례 1:** 클라이언트 앱의 id를 확인 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-153">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="dccf4-154">이 사용 사례에서 공유 암호는 충분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-154">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="dccf4-155">이 비밀은 추측 하기에 충분히 복잡 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-155">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="dccf4-156">적절 한 공유 암호는 임의의 GUID 이며, 서버 및 클라이언트의 구성에 수동으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-156">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="dccf4-157">예를 들어 PowerShell에서 명령을 사용 하 여 만들 수 있습니다 `New-Guid` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-157">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="dccf4-158">이 공유 암호는 안전 하지 않은 채널을 통해 전달 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-158">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="dccf4-159">원격 라이브러리는 공유 암호가 항상 암호화 된 상태로 전송 되 고 신뢰할 수 있는 피어로 전송 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-159">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="dccf4-160">**사용 사례 2:** 또한 클라이언트 앱 사용자의 id를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-160">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="dccf4-161">공유 암호는이 사용 사례를 포함 하는 데 충분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-161">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="dccf4-162">대신 id 공급자에 의해 생성 된 토큰을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-162">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="dccf4-163">Id 공급자를 사용 하는 인증 워크플로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-163">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="dccf4-164">클라이언트는 id 공급자에 대해 권한을 부여 하 고 토큰을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-164">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="dccf4-165">Id 공급자는 토큰을 생성 하 여 클라이언트에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-165">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="dccf4-166">클라이언트는 Holographic 원격을 통해 서버에이 토큰을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-166">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="dccf4-167">서버는 id 공급자에 대해 클라이언트 토큰의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-167">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="dccf4-168">Id 공급자의 한 가지 예는 [Microsoft id 플랫폼](https://docs.microsoft.com/azure/active-directory/develop/)입니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-168">One example of an identity provider is the [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/).</span></span>

<span data-ttu-id="dccf4-169">이전 사용 사례와 마찬가지로 이러한 토큰은 안전 하지 않은 채널을 통해 전송 되거나 다른 방법으로 노출 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-169">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="dccf4-170">Holographic 원격 보안 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-170">Implementing holographic remoting security</span></span>

<span data-ttu-id="dccf4-171">연결 보안을 사용 하도록 설정 하려면 사용자 지정 원격 및 플레이어 앱을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-171">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="dccf4-172">제공 된 샘플을 자신의 앱에 대 한 시작 점으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-172">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="dccf4-173">보안을 사용 하도록 설정 하려면 대신를 호출 하 고 대신를 호출 하 여 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-173">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="dccf4-174">이러한 호출에는 보안 관련 정보를 제공 하 고 유효성을 검사 하기 위해 특정 인터페이스의 구현을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-174">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="dccf4-175">서버는 인증서 공급자와 인증 유효성 검사기를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-175">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="dccf4-176">클라이언트는 인증 공급자 및 인증서 유효성 검사기를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-176">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="dccf4-177">모든 인터페이스에는 콜백 개체를 매개 변수로 수신 하는 작업을 수행 하도록 요청 하는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-177">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="dccf4-178">이 개체를 사용 하 여 요청에 대 한 비동기 처리를 쉽게 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-178">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="dccf4-179">이 개체에 대 한 참조를 유지 하 고 비동기 작업이 완료 되 면 완료 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-179">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="dccf4-180">모든 스레드에서 완료 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-180">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="dccf4-181">WinRT 인터페이스 구현은 c + +/WinRT. 사용 하 여 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-181">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="dccf4-182">[C + +/vb를 사용 하는 작성자 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 장에서는이에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-182">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="dccf4-183">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 패키지 내에는 보안 연결과 관련 된 API에 대 한 자세한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-183">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="dccf4-184">인증서 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-184">Implementing a certificate provider</span></span>

<span data-ttu-id="dccf4-185">인증서 공급자는 사용할 인증서를 서버 응용 프로그램에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-185">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="dccf4-186">구현은 다음과 같은 두 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-186">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="dccf4-187">인터페이스를 구현 하는 인증서 개체 `ICertificate` :</span><span class="sxs-lookup"><span data-stu-id="dccf4-187">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="dccf4-188">`GetCertificatePfx()` 인증서 저장소의 이진 콘텐츠를 반환 해야 합니다 `PKCS#12` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-188">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="dccf4-189">`.pfx`파일은 `PKCS#12` 데이터를 포함 하므로 여기에서 직접 콘텐츠를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-189">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="dccf4-190">`GetSubjectName()` 는 사용할 인증서를 식별 하는 친숙 한 이름을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-190">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="dccf4-191">인증서에 지정 된 이름이 없는 경우이 함수는 인증서의 주체 이름을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-191">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="dccf4-192">`GetPfxPassword()` 인증서 저장소를 여는 데 필요한 암호를 반환 해야 합니다. 암호를 입력 해야 하는 경우에는 빈 문자열을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-192">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="dccf4-193">인터페이스를 구현 하는 인증서 공급자 `ICertificateProvider` :</span><span class="sxs-lookup"><span data-stu-id="dccf4-193">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="dccf4-194">`GetCertificate()` 인증서 개체를 생성 하 고 `CertificateReceived()` 콜백 개체에 대해를 호출 하 여 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-194">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="dccf4-195">인증 유효성 검사기 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-195">Implementing an authentication validator</span></span>

<span data-ttu-id="dccf4-196">인증 유효성 검사기는 클라이언트에서 보낸 인증 토큰을 수신 하 고 유효성 검사 결과를 사용 하 여 다시 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-196">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="dccf4-197">다음과 같이 인터페이스를 구현 합니다 `IAuthenticationReceiver` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-197">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="dccf4-198">`GetRealm()` 는 인증 영역 (원격 연결 핸드셰이크 중에 사용 되는 HTTP 영역)의 이름을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-198">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="dccf4-199">`ValidateToken()` 는 클라이언트 인증 토큰의 유효성을 검사 하 고 `ValidationCompleted()` 유효성 검사 결과를 사용 하 여 콜백 개체에 대해를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-199">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="dccf4-200">인증 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-200">Implementing an authentication provider</span></span>

<span data-ttu-id="dccf4-201">인증 공급자는 서버로 전송 되는 인증 토큰을 생성 하거나 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-201">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="dccf4-202">다음과 같이 인터페이스를 구현 합니다 `IAuthenticationProvider` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-202">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="dccf4-203">`GetToken()` 전송할 인증 토큰을 생성 하거나 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-203">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="dccf4-204">토큰이 준비 되 면 `TokenReceived()` 콜백 개체에서 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-204">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="dccf4-205">인증서 유효성 검사기 구현</span><span class="sxs-lookup"><span data-stu-id="dccf4-205">Implementing a certificate validator</span></span>

<span data-ttu-id="dccf4-206">인증서 유효성 검사기는 서버에서 보낸 인증서 체인을 받고 서버를 신뢰할 수 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-206">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="dccf4-207">인증서의 유효성을 검사 하려면 기본 시스템의 유효성 검사 논리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-207">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="dccf4-208">이 시스템 유효성 검사는 사용자 고유의 유효성 검사 논리를 지원 하거나 완전히 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-208">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="dccf4-209">보안 연결을 요청할 때 자체 인증서 유효성 검사기를 전달 하지 않으면 시스템 유효성 검사가 자동으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-209">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="dccf4-210">Windows에서 시스템 유효성 검사는 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-210">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="dccf4-211">인증서 체인의 무결성: 인증서는 신뢰할 수 있는 루트 인증서에서 끝나는 일관 된 체인을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-211">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="dccf4-212">인증서 유효성: 서버 인증서가 유효 기간 내에 있으며 서버 인증을 위해 발급 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-212">Certificate validity: the server's certificate is within its validity timespan, and is issued for the purpose of server authentication</span></span>
* <span data-ttu-id="dccf4-213">해지: 인증서가 해지 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-213">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="dccf4-214">이름 일치: 서버의 호스트 이름이 인증서가 발급 된 호스트 이름 중 하 나와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-214">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="dccf4-215">다음과 같이 인터페이스를 구현 합니다 `ICertificateValidator` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-215">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="dccf4-216">`PerformSystemValidation()``true`위에서 설명한 대로 시스템 유효성 검사를 수행 해야 하는 경우를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-216">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="dccf4-217">이 경우 시스템 유효성 검사 결과는 메서드에 입력으로 전달 됩니다 `ValidateCertificate()` .</span><span class="sxs-lookup"><span data-stu-id="dccf4-217">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="dccf4-218">`ValidateCertificate()` 인증서 체인의 유효성을 검사 한 다음 `CertificateValidated()` 최종 유효성 검사 결과를 사용 하 여 전달 된 콜백에서를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-218">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="dccf4-219">이 메서드는 인증서 체인, 연결이 설정 되는 서버의 이름 및 해지 검사 강제 적용 여부를 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-219">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="dccf4-220">인증서 체인에 여러 인증서가 포함 된 경우 첫 번째 인증서는 주체 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-220">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="dccf4-221">사용 사례에 다른 형식의 유효성 검사가 필요한 경우 (위의 #1 인증서 사용 사례 참조) 시스템 유효성 검사를 완전히 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-221">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="dccf4-222">대신, DER로 인코딩된 x.509 인증서를 처리할 수 있는 API 또는 라이브러리를 사용 하 여 인증서 체인을 디코딩하고 사용 사례에 필요한 검사를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dccf4-222">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="see-also"></a><span data-ttu-id="dccf4-223">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dccf4-223">See Also</span></span>
* [<span data-ttu-id="dccf4-224">홀로그램 원격 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="dccf4-224">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="dccf4-225">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="dccf4-225">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="dccf4-226">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="dccf4-226">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="dccf4-227">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="dccf4-227">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="dccf4-228">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="dccf4-228">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
