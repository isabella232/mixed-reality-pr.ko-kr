---
title: Holographic Remoting에 대 한 연결 보안 사용
description: 이 페이지에서는 플레이어와 원격 앱 간에 암호화 및 인증 된 연결을 사용 하도록 Holographic Remoting을 구성 하는 방법을 설명 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 보안, 인증, 서버 간
ms.openlocfilehash: 6b8c26bfa32661a180f1f58acc5c4aa13529f3bb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583842"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Holographic Remoting에 대 한 연결 보안 사용

>[!IMPORTANT]
>이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

이 페이지에서는 Holographic Remoting의 네트워크 보안에 대 한 개요를 제공 합니다. 다음에 대 한 정보를 찾을 수 있습니다.

* Holographic 원격 컨텍스트의 보안 및 필요할 수 있는 이유
* 다른 사용 사례를 기반으로 권장 되는 측정값
* Holographic Remoting 솔루션에서 보안 구현

## <a name="holographic-remoting-security"></a>Holographic 원격 보안

Holographic 원격은 네트워크를 통해 정보를 교환 합니다. 보안 조치를 수행 하지 않는 경우 동일한 네트워크에서 악의적 사용자 통신의 무결성을 손상 하거나 기밀 정보에 액세스할 수 있습니다.

Windows 스토어의 샘플 앱 및 Holographic Remoting 플레이어에는 보안이 사용 하지 않도록 설정 된 상태로 제공 됩니다. 이렇게 하면 샘플을 보다 쉽게 이해할 수 있습니다. 또한 개발을 빠르게 시작할 수 있습니다.

필드 테스트 또는 프로덕션의 경우 Holographic Remoting 솔루션에서 보안을 사용 하도록 설정 하는 것이 좋습니다.

Holographic Remoting의 보안. 사용 사례에 대해 올바르게 설정 하면 다음을 보장할 수 있습니다.

* **정품:** 플레이어와 원격 앱 모두 다른 쪽이 자신에 게 클레임을 요구 하는 것을 확신할 수 있습니다.
* **기밀성:** 타사에서 플레이어와 원격 앱 간에 교환 되는 정보를 읽을 수 없음
* **무결성:** 플레이어 및 원격에서 통신에 대 한 전송 중인 모든 변경 내용을 검색할 수 있습니다.

>[!IMPORTANT]
>보안 기능을 사용 하려면 [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) 또는 [OpenXR](holographic-remoting-create-remote-openxr.md) api를 사용 하 여 [사용자 지정 플레이어](holographic-remoting-create-player.md) 와 사용자 지정 원격 앱을 모두 구현 해야 합니다.

>[!NOTE]
> [OPENXR API](../native/openxr.md) 를 사용 하 여 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 버전의 원격 앱을 만들 수 있습니다. OpenXR 환경에서 보안 연결을 설정 하는 방법에 대 한 개요는 [아래](#secure-connection-using-the-openxr-api)에서 찾을 수 있습니다.

## <a name="planning-the-security-implementation"></a>보안 구현 계획

Holographic Remoting에서 보안을 사용 하도록 설정 하면 원격 라이브러리에서 네트워크를 통해 교환 되는 모든 데이터에 대해 암호화 및 무결성 검사를 자동으로 사용 하도록 설정 합니다.

그러나 적절 한 인증을 사용 하려면 몇 가지 추가 작업이 필요 합니다. 사용 사례에 따라 수행 해야 하는 작업은 무엇 이며,이 섹션의 나머지 부분에서는 필요한 단계를 파악 하는 방법에 대해 설명 합니다.

>[!IMPORTANT]
> 이 문서에서는 일반 지침도 제공할 수 있습니다. 확실 하지 않은 경우 사용 사례에 대 한 지침을 제공할 수 있는 보안 전문가에 게 문의 하는 것이 좋습니다.

첫 번째 용어: 네트워크 연결을 설명 하는 경우 _클라이언트_ 및 _서버_ 라는 용어가 사용 됩니다. 서버는 알려진 끝점 주소에서 들어오는 연결을 수신 대기 하는 쪽 이며, 클라이언트는 서버 끝점에 연결 하는 것입니다.

>[!NOTE]
> 클라이언트 및 서버 역할은 앱이 플레이어 또는 원격 역할을 하는지 여부에 연결 되지 않습니다. 예제에는 서버 역할의 플레이어가 있지만 사용 사례에 적합 한 경우 역할을 쉽게 되돌릴 수 있습니다.

### <a name="planning-the-server-to-client-authentication"></a>서버-클라이언트 인증 계획

서버는 디지털 인증서를 사용 하 여 클라이언트에 대 한 id를 증명 합니다. 클라이언트는 연결 핸드셰이크 단계에서 서버 인증서의 유효성을 검사 합니다. 클라이언트에서 서버를 신뢰 하지 않는 경우이 시점에서 연결이 종료 됩니다.

클라이언트에서 서버 인증서의 유효성을 검사 하는 방법과 사용할 수 있는 서버 인증서 종류는 사용 사례에 따라 다릅니다.

**사용 사례 1:** 서버 호스트 이름이 고정 되어 있지 않거나 서버에서 호스트 이름으로 주소가 지정 되지 않았습니다.

이 사용 사례에서는 서버 호스트 이름에 대 한 인증서를 발급 하는 것이 실용적이 지 않거나 가능 하지 않습니다. 대신 인증서의 지문을 확인 하는 것이 좋습니다. 인간 지문과 마찬가지로, 지 문은 인증서를 고유 하 게 식별 합니다.

지문을 클라이언트에 대역 외로 전달 하는 것이 중요 합니다. 즉, 원격 작업에 사용 되는 것과 동일한 네트워크 연결을 통해 메시지를 보낼 수 없습니다. 대신, 클라이언트의 구성에 수동으로 입력 하거나 클라이언트에서 QR 코드를 검색 하도록 할 수 있습니다.

**사용 사례 2:** 안정적인 호스트 이름을 통해 서버에 연결할 수 있습니다.

이 사용 사례에서 서버에는 특정 호스트 이름이 있으며이 이름은 변경 될 수 없습니다. 그런 다음 서버 호스트 이름에 발급 된 인증서를 사용할 수 있습니다. 트러스트는 호스트 이름 및 인증서의 신뢰 체인에 따라 설정 됩니다.

이 옵션을 선택 하는 경우 클라이언트는 서버의 호스트 이름 및 루트 인증서를 미리 알고 있어야 합니다.

### <a name="planning-the-client-to-server-authentication"></a>클라이언트와 서버 간 인증 계획

클라이언트는 자유 형식 토큰을 사용 하 여 서버에 대해 인증 합니다. 이 토큰에 포함 되어야 하는 항목은 사용 사례에 따라 다음과 같이 달라 집니다.

**사용 사례 1:** 클라이언트 앱의 id를 확인 하기만 하면 됩니다.

이 사용 사례에서 공유 암호는 충분할 수 있습니다. 이 비밀은 추측 하기에 충분히 복잡 해야 합니다.

적절 한 공유 암호는 임의의 GUID 이며, 서버 및 클라이언트의 구성에 수동으로 입력 합니다. 예를 들어 PowerShell에서 명령을 사용 하 여 만들 수 있습니다 `New-Guid` .

이 공유 암호는 안전 하지 않은 채널을 통해 전달 되지 않는지 확인 합니다. 원격 라이브러리는 공유 암호가 항상 암호화 된 상태로 전송 되 고 신뢰할 수 있는 피어로 전송 되도록 합니다.

**사용 사례 2:** 또한 클라이언트 앱 사용자의 id를 확인 해야 합니다.

공유 암호는이 사용 사례를 포함 하는 데 충분 하지 않습니다. 대신 id 공급자에 의해 생성 된 토큰을 사용할 수 있습니다. Id 공급자를 사용 하는 인증 워크플로는 다음과 같습니다.

* 클라이언트는 id 공급자에 대해 권한을 부여 하 고 토큰을 요청 합니다.
* Id 공급자는 토큰을 생성 하 여 클라이언트에 보냅니다.
* 클라이언트는 Holographic 원격을 통해 서버에이 토큰을 보냅니다.
* 서버는 id 공급자에 대해 클라이언트 토큰의 유효성을 검사 합니다.

Id 공급자의 한 가지 예는 [Microsoft id 플랫폼](/azure/active-directory/develop/)입니다.

이전 사용 사례와 마찬가지로 이러한 토큰은 안전 하지 않은 채널을 통해 전송 되거나 다른 방법으로 노출 되지 않아야 합니다.

## <a name="implementing-holographic-remoting-security"></a>Holographic 원격 보안 구현

연결 보안을 사용 하도록 설정 하려면 사용자 지정 원격 및 플레이어 앱을 구현 해야 합니다. 제공 된 샘플을 자신의 앱에 대 한 시작 점으로 사용할 수 있습니다.

보안을 사용 하도록 설정 하려면 대신를 호출 하 고 대신를 호출 하 여 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` 원격 연결을 설정 합니다.

이러한 호출에는 보안 관련 정보를 제공 하 고 유효성을 검사 하기 위해 특정 인터페이스의 구현을 제공 해야 합니다.

* 서버는 인증서 공급자와 인증 유효성 검사기를 구현 해야 합니다.
* 클라이언트는 인증 공급자 및 인증서 유효성 검사기를 구현 해야 합니다.

모든 인터페이스에는 콜백 개체를 매개 변수로 수신 하는 작업을 수행 하도록 요청 하는 함수가 있습니다. 이 개체를 사용 하 여 요청에 대 한 비동기 처리를 쉽게 구현할 수 있습니다. 이 개체에 대 한 참조를 유지 하 고 비동기 작업이 완료 되 면 완료 함수를 호출 합니다. 모든 스레드에서 완료 함수를 호출할 수 있습니다.

>[!TIP]
>WinRT 인터페이스 구현은 c + +/WinRT. 사용 하 여 쉽게 수행할 수 있습니다. [C + +/vb를 사용 하는 작성자 api](//windows/uwp/cpp-and-winrt-apis/author-apis) 장에서는이에 대해 자세히 설명 합니다.

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 패키지 내에는 보안 연결과 관련 된 API에 대 한 자세한 설명서가 포함 되어 있습니다.

### <a name="implementing-a-certificate-provider"></a>인증서 공급자 구현

인증서 공급자는 사용할 인증서를 서버 응용 프로그램에 제공 합니다. 구현은 다음과 같은 두 부분으로 구성 됩니다.

1) 인터페이스를 구현 하는 인증서 개체 `ICertificate` :

    * `GetCertificatePfx()` 인증서 저장소의 이진 콘텐츠를 반환 해야 합니다 `PKCS#12` . `.pfx`파일은 `PKCS#12` 데이터를 포함 하므로 여기에서 직접 콘텐츠를 사용할 수 있습니다.
    * `GetSubjectName()` 는 사용할 인증서를 식별 하는 친숙 한 이름을 반환 해야 합니다. 인증서에 지정 된 이름이 없는 경우이 함수는 인증서의 주체 이름을 반환 해야 합니다.
    * `GetPfxPassword()` 인증서 저장소를 여는 데 필요한 암호를 반환 해야 합니다. 암호를 입력 해야 하는 경우에는 빈 문자열을 반환 해야 합니다.

2) 인터페이스를 구현 하는 인증서 공급자 `ICertificateProvider` :
    * `GetCertificate()` 인증서 개체를 생성 하 고 `CertificateReceived()` 콜백 개체에 대해를 호출 하 여 반환 해야 합니다.

### <a name="implementing-an-authentication-validator"></a>인증 유효성 검사기 구현

인증 유효성 검사기는 클라이언트에서 보낸 인증 토큰을 수신 하 고 유효성 검사 결과를 사용 하 여 다시 응답 합니다.

다음과 같이 인터페이스를 구현 합니다 `IAuthenticationReceiver` .

* `GetRealm()` 는 인증 영역 (원격 연결 핸드셰이크 중에 사용 되는 HTTP 영역)의 이름을 반환 해야 합니다.
* `ValidateToken()` 는 클라이언트 인증 토큰의 유효성을 검사 하 고 `ValidationCompleted()` 유효성 검사 결과를 사용 하 여 콜백 개체에 대해를 호출 해야 합니다.

### <a name="implementing-an-authentication-provider"></a>인증 공급자 구현

인증 공급자는 서버로 전송 되는 인증 토큰을 생성 하거나 검색 합니다.

다음과 같이 인터페이스를 구현 합니다 `IAuthenticationProvider` .

* `GetToken()` 전송할 인증 토큰을 생성 하거나 검색 해야 합니다. 토큰이 준비 되 면 `TokenReceived()` 콜백 개체에서 메서드를 호출 합니다.

### <a name="implementing-a-certificate-validator"></a>인증서 유효성 검사기 구현

인증서 유효성 검사기는 서버에서 보낸 인증서 체인을 받고 서버를 신뢰할 수 있는지 여부를 확인 합니다.

인증서의 유효성을 검사 하려면 기본 시스템의 유효성 검사 논리를 사용할 수 있습니다. 이 시스템 유효성 검사는 사용자 고유의 유효성 검사 논리를 지원 하거나 완전히 바꿀 수 있습니다. 보안 연결을 요청할 때 자체 인증서 유효성 검사기를 전달 하지 않으면 시스템 유효성 검사가 자동으로 사용 됩니다.

Windows에서 시스템 유효성 검사는 다음을 확인 합니다.

* 인증서 체인의 무결성: 인증서는 신뢰할 수 있는 루트 인증서에서 끝나는 일관 된 체인을 형성 합니다.
* 인증서 유효성: 서버 인증서가 유효 기간 내에 있으며 서버 인증을 위해 발급 됩니다.
* 해지: 인증서가 해지 되지 않았습니다.
* 이름 일치: 서버의 호스트 이름이 인증서가 발급 된 호스트 이름 중 하 나와 일치 합니다.

다음과 같이 인터페이스를 구현 합니다 `ICertificateValidator` .

 * `PerformSystemValidation()``true`위에서 설명한 대로 시스템 유효성 검사를 수행 해야 하는 경우를 반환 해야 합니다. 이 경우 시스템 유효성 검사 결과는 메서드에 입력으로 전달 됩니다 `ValidateCertificate()` .
* `ValidateCertificate()` 인증서 체인의 유효성을 검사 한 다음 `CertificateValidated()` 최종 유효성 검사 결과를 사용 하 여 전달 된 콜백에서를 호출 해야 합니다. 이 메서드는 인증서 체인, 연결이 설정 되는 서버의 이름 및 해지 검사 강제 적용 여부를 수락 합니다. 인증서 체인에 여러 인증서가 포함 된 경우 첫 번째 인증서는 주체 인증서입니다.

>[!NOTE]
>사용 사례에 다른 형식의 유효성 검사가 필요한 경우 (위의 #1 인증서 사용 사례 참조) 시스템 유효성 검사를 완전히 무시 합니다. 대신, DER로 인코딩된 x.509 인증서를 처리할 수 있는 API 또는 라이브러리를 사용 하 여 인증서 체인을 디코딩하고 사용 사례에 필요한 검사를 수행 합니다.

## <a name="secure-connection-using-the-openxr-api"></a>OpenXR API를 사용 하 여 연결 보안

[OPENXR api](../native/openxr.md) 를 사용 하는 경우 모든 보안 연결 관련 API는 OpenXR 확장의 일부로 사용할 수 있습니다 `XR_MSFT_holographic_remoting` .

>[!IMPORTANT]
>Holographic Remoting OpenXR extension API에 대 한 자세한 내용은 [Holographic remoting 샘플 github 리포지토리에서](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)찾을 수 있는 [사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) 확인 하세요.

OpenXR 확장을 사용 하는 보안 연결의 주요 요소는 `XR_MSFT_holographic_remoting` 다음과 같은 콜백입니다.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`는 전송할 인증 토큰을 생성 하거나 검색 합니다.
- `xrRemotingValidateServerCertificateCallbackMSFT`인증서 체인의 유효성을 검사 합니다.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`는 클라이언트 인증 토큰의 유효성을 검사 합니다.
- `xrRemotingRequestServerCertificateCallbackMSFT`에서 사용할 인증서를 서버 응용 프로그램에 제공 합니다.

이러한 콜백은 및를 통해 remoting OpenXR 런타임에 제공할 수 있습니다 `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` . 또한 `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` 또는를 사용 하는지 여부에 따라 구조 또는 구조에서 secureconnection 매개 변수를 통해 보안 연결을 설정 해야 합니다 `xrRemotingConnectMSFT` `xrRemotingListenMSFT` .

이 API는 [holographic remoting Security 구현](#implementing-holographic-remoting-security)에 설명 된 IDL 기반 api와 비슷합니다. 그러나 인터페이스를 구현 하는 대신 콜백 구현을 제공 해야 합니다. [OpenXR 샘플 앱](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 자세한 예제를 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목
* [Windows Mixed Reality Api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)