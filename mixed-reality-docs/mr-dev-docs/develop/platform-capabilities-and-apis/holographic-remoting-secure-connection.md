---
title: 홀로그램 Remoting에 대한 연결 보안 사용
description: 이 페이지에서는 플레이어와 원격 앱 간에 암호화되고 인증된 연결을 사용하도록 Holographic Remoting을 구성하는 방법을 설명합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, 홀로그램 Remoting, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 보안, 인증, 서버-클라이언트
ms.openlocfilehash: fa23994ff4ab49d313fe24a67974bf4d90454e511658e0663c61d7b129b10f9e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223583"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>홀로그램 Remoting에 대한 연결 보안 사용

>[!IMPORTANT]
>이 지침은 HoloLens 2 Holographic Remoting과 관련이 있습니다.

이 페이지에서는 홀로그램 Remoting의 네트워크 보안에 대한 개요를 제공합니다. 에 대한 정보를 찾을 수 있습니다.

* 홀로그램 Remoting의 컨텍스트에서 보안 및 필요한 이유
* 다양한 사용 사례에 따라 권장되는 측정값
* 홀로그램 Remoting 솔루션에서 보안 구현

## <a name="holographic-remoting-security"></a>홀로그램 Remoting 보안

홀로그램 Remoting은 네트워크를 통해 정보를 교환합니다. 보안 조치가 없으면 동일한 네트워크의 악의적 사용자들이 통신의 무결성을 손상하거나 기밀 정보에 액세스할 수 있습니다.

Windows Store의 샘플 앱 및 홀로그램 Remoting Player에는 보안이 사용하지 않도록 설정되어 있습니다. 이렇게 하면 샘플을 더 쉽게 이해할 수 있습니다. 또한 개발을 더 빠르게 시작하는 데 도움이 됩니다.

현장 테스트 또는 프로덕션의 경우 홀로그램 Remoting 솔루션에서 보안을 사용하도록 설정하는 것이 좋습니다.

Holographic Remoting의 보안은 사용 사례에 맞게 올바르게 설정된 경우 다음과 같은 보장을 제공합니다.

* **신뢰성:** 플레이어와 원격 앱은 둘 다 다른 쪽에서 클레임하는 사람인지 확인할 수 있습니다.
* **기밀성:** 타사에서 플레이어와 원격 앱 간에 교환된 정보를 읽을 수 없습니다.
* **무결성:** 플레이어 및 원격은 통신의 전송 중 변경 내용을 검색할 수 있습니다.

>[!IMPORTANT]
>보안 기능을 사용하려면 Windows Mixed Reality 또는 [OpenXR](holographic-remoting-create-remote-openxr.md) [API를](holographic-remoting-create-remote-wmr.md) 사용하여 [사용자 지정 플레이어와](holographic-remoting-create-player.md) 사용자 지정 원격 앱을 모두 구현해야 합니다.

>[!NOTE]
> 버전 [2.4.0부터](holographic-remoting-version-history.md#v2.4.0) [OpenXR API를](../native/openxr.md) 사용하는 원격 앱을 만들 수 있습니다. OpenXR 환경에서 보안 연결을 설정하는 방법에 대한 개요는 [아래에서](#secure-connection-using-the-openxr-api)찾을 수 있습니다.

## <a name="planning-the-security-implementation"></a>보안 구현 계획

홀로그램 Remoting에서 보안을 사용하도록 설정하면 Remoting 라이브러리는 네트워크를 통해 교환된 모든 데이터에 대해 암호화 및 무결성 검사를 자동으로 사용하도록 설정합니다.

그러나 적절한 인증을 보장하려면 몇 가지 추가 작업이 필요합니다. 정확히 수행해야 하는 것은 사용 사례에 따라 달라지고, 이 섹션의 나머지 부분은 필요한 단계를 구성하는 것입니다.

>[!IMPORTANT]
> 이 문서에서는 일반 지침만 제공할 수 있습니다. 확실하지 않은 경우 사용 사례와 관련된 지침을 제공할 수 있는 보안 전문가에게 문의하는 것이 좋습니다.

첫 번째 몇 가지 용어: 네트워크 연결을 설명할 때 _클라이언트와_ _서버라는_ 용어가 사용됩니다. 서버는 알려진 엔드포인트 주소에서 들어오는 연결을 수신 대기하는 쪽이며 클라이언트는 서버의 엔드포인트에 연결하는 쪽입니다.

>[!NOTE]
> 클라이언트 및 및 서버 역할은 앱이 플레이어 역할을 하는지 아니면 원격으로 동작하는지에 연결되지 않습니다. 샘플에는 서버 역할에 플레이어가 있지만 사용 사례에 더 잘 맞으면 역할을 되돌리는 것이 쉽습니다.

### <a name="planning-the-server-to-client-authentication"></a>서버-클라이언트 인증 계획

서버는 디지털 인증서를 사용하여 클라이언트에 대한 ID를 증명합니다. 클라이언트는 연결 핸드셰이크 단계에서 서버 인증서의 유효성을 검사합니다. 클라이언트가 서버를 신뢰하지 않으면 이 시점에서 연결이 종료됩니다.

클라이언트가 서버 인증서의 유효성을 검사하는 방법 및 사용할 수 있는 서버 인증서의 종류는 사용 사례에 따라 달라집니다.

**사용 사례 1:** 서버 호스트 이름이 고정되지 않았거나 서버의 주소가 호스트 이름으로 전혀 지정되지 않습니다.

이 사용 사례에서는 서버의 호스트 이름에 대한 인증서를 발급하는 것이 실용적이지 않습니다(또는 가능). 대신 인증서 지문의 유효성을 검사하는 것이 좋습니다. 사람의 지문처럼 지문은 인증서를 고유하게 식별합니다.

지문을 클라이언트 out-of-band에 전달하는 것이 중요합니다. 즉, Remoting에 사용되는 것과 동일한 네트워크 연결을 통해 보낼 수 없습니다. 대신 클라이언트의 구성에 수동으로 입력하거나 클라이언트가 QR 코드를 검사하도록 할 수 있습니다.

**사용 사례 2:** 안정적인 호스트 이름을 통해 서버에 연결할 수 있습니다.

이 사용 사례에서 서버에는 특정 호스트 이름이 있으며 이 이름은 변경되지 않을 수 있습니다. 그런 다음 서버의 호스트 이름에 발급된 인증서를 사용할 수 있습니다. 트러스트는 호스트 이름 및 인증서의 신뢰 체인에 따라 설정됩니다.

이 옵션을 선택하는 경우 클라이언트는 서버의 호스트 이름 및 루트 인증서를 미리 알고 있어야 합니다.

### <a name="planning-the-client-to-server-authentication"></a>클라이언트-서버 인증 계획

클라이언트는 자유 형식 토큰을 사용하여 서버에 대해 인증합니다. 이 토큰에 포함해야 하는 것은 사용 사례에 따라 달라집니다.

**사용 사례 1:** 클라이언트 앱의 ID만 확인하면 됩니다.

이 사용 사례에서는 공유 암호로 충분할 수 있습니다. 이 비밀은 추측할 수 없을 정도로 복잡해야 합니다.

좋은 공유 암호는 서버와 클라이언트의 구성 모두에 수동으로 입력되는 임의의 GUID입니다. 예를 들어 만들려면 `New-Guid` PowerShell에서 명령을 사용합니다.

이 공유 비밀이 안전하지 않은 채널을 통해 전달되지 않는지 확인합니다. Remoting 라이브러리는 공유 비밀이 항상 암호화되고 신뢰할 수 있는 피어에게만 전송되도록 합니다.

**사용 사례 2:** 또한 클라이언트 앱 사용자의 ID를 확인해야 합니다.

공유 비밀만으로는 이 사용 사례를 다룰 수 없습니다. 대신 ID 공급자가 만든 토큰을 사용할 수 있습니다. ID 공급자를 사용하는 인증 워크플로는 다음과 같습니다.

* 클라이언트는 ID 공급자에 대해 권한을 부여하고 토큰을 요청합니다.
* ID 공급자가 토큰을 생성하고 클라이언트에 보냅니다.
* 클라이언트는 홀로그램 Remoting을 통해 서버에 이 토큰을 보냅니다.
* 서버가 ID 공급자에 대해 클라이언트 토큰의 유효성을 검사합니다.

ID 공급자의 한 가지 예는 [Microsoft ID 플랫폼](/azure/active-directory/develop/)입니다.

이전 사용 사례와 마찬가지로 이러한 토큰이 안전하지 않은 채널을 통해 전송되거나 노출되지 않는지 확인합니다.

## <a name="implementing-holographic-remoting-security"></a>홀로그램 Remoting 보안 구현

연결 보안을 사용하도록 설정하려면 사용자 지정 원격 및 플레이어 앱을 구현해야 합니다. 제공된 샘플을 사용자 고유의 앱에 대한 시작점으로 사용할 수 있습니다.

보안을 사용하려면 대신 및 를 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` 호출하여 Remoting 연결을 설정합니다.

이러한 호출을 사용하려면 보안 관련 정보를 제공하고 유효성을 검사하기 위한 특정 인터페이스의 구현을 제공해야 합니다.

* 서버에서 인증서 공급자 및 인증 유효성 검사기를 구현해야 합니다.
* 클라이언트는 인증 공급자 및 인증서 유효성 검사기를 구현해야 합니다.

모든 인터페이스에는 작업을 수행하도록 요청하는 함수가 있으며, 이 함수는 콜백 개체를 매개 변수로 받습니다. 이 개체를 사용하면 요청의 비동기 처리를 쉽게 구현할 수 있습니다. 이 개체에 대한 참조를 유지하고 비동기 작업이 완료되면 완료 함수를 호출합니다. 완료 함수는 모든 스레드에서 호출할 수 있습니다.

>[!TIP]
>WinRT 인터페이스 구현은 C++/WinRT를 사용하여 쉽게 수행할 수 있습니다. [C++/WinRT를 이용한 API 작성](/windows/uwp/cpp-and-winrt-apis/author-apis) 챕터에서는 이에 대해 자세히 설명합니다.

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 패키지 내의 에는 보안 연결과 관련된 API에 대한 자세한 설명서가 포함되어 있습니다.

### <a name="implementing-a-certificate-provider"></a>인증서 공급자 구현

인증서 공급자는 서버 애플리케이션에 사용할 인증서를 제공합니다. 구현은 다음 두 부분으로 구성됩니다.

1) 인터페이스를 구현하는 인증서 `ICertificate` 개체입니다.

    * `GetCertificatePfx()` 는 인증서 저장소의 이진 콘텐츠를 반환해야 `PKCS#12` 합니다. `.pfx`파일에는 데이터가 포함되어 `PKCS#12` 있으므로 여기에서 직접 해당 내용을 사용할 수 있습니다.
    * `GetSubjectName()` 는 사용할 인증서를 식별하는 이름을 반환해야 합니다. 인증서에 이름이 할당되지 않은 경우 이 함수는 인증서의 주체 이름을 반환해야 합니다.
    * `GetPfxPassword()` 는 인증서 저장소를 여는 데 필요한 암호를 반환해야 합니다(또는 암호가 필요하지 않은 경우 빈 문자열).

2) 인터페이스를 구현하는 인증서 `ICertificateProvider` 공급자:
    * `GetCertificate()` 는 인증서 개체를 생성하고 콜백 개체에서 를 호출하여 반환해야 `CertificateReceived()` 합니다.

### <a name="implementing-an-authentication-validator"></a>인증 유효성 검사기 구현

인증 유효성 검사기는 클라이언트에서 보낸 인증 토큰을 수신하고 유효성 검사 결과로 응답합니다.

다음과 `IAuthenticationReceiver` 같이 인터페이스를 구현합니다.

* `GetRealm()` 는 인증 영역의 이름(Remoting 연결 핸드셰이크 중에 사용되는 HTTP 영역)을 반환해야 합니다.
* `ValidateToken()` 는 클라이언트 인증 토큰의 유효성을 검사하고 `ValidationCompleted()` 유효성 검사 결과를 사용하여 콜백 개체에서 를 호출해야 합니다.

### <a name="implementing-an-authentication-provider"></a>인증 공급자 구현

인증 공급자는 서버로 보낼 인증 토큰을 생성하거나 검색합니다.

다음과 `IAuthenticationProvider` 같이 인터페이스를 구현합니다.

* `GetToken()` 는 전송할 인증 토큰을 생성하거나 검색해야 합니다. 토큰이 준비되면 `TokenReceived()` 콜백 개체에서 메서드를 호출합니다.

### <a name="implementing-a-certificate-validator"></a>인증서 유효성 검사기 구현

인증서 유효성 검사기는 서버에서 보낸 인증서 체인을 수신하고 서버를 신뢰할 수 있는지 여부를 결정합니다.

인증서의 유효성을 검사하려면 기본 시스템의 유효성 검사 논리를 사용할 수 있습니다. 이 시스템 유효성 검사는 사용자 고유의 유효성 검사 논리를 지원하거나 완전히 바꿀 수 있습니다. 보안 연결을 요청할 때 사용자 고유의 인증서 유효성 검사기를 전달하지 않으면 시스템 유효성 검사가 자동으로 사용됩니다.

Windows 시스템 유효성 검사는 다음을 확인합니다.

* 인증서 체인의 무결성: 인증서는 신뢰할 수 있는 루트 인증서에서 끝나는 일관된 체인을 형성합니다.
* 인증서 유효성: 서버의 인증서가 유효 시간 범위 내에 있으며 서버 인증을 위해 발급됩니다.
* 해지: 인증서가 해지되지 않았습니다.
* 이름 일치: 서버의 호스트 이름이 인증서가 발급된 호스트 이름 중 하나와 일치합니다.

다음과 `ICertificateValidator` 같이 인터페이스를 구현합니다.

 * `PerformSystemValidation()` 는 `true` 위에서 설명한 대로 시스템 유효성 검사를 수행해야 하는 경우 를 반환해야 합니다. 이 경우 시스템 유효성 검사 결과가 메서드에 입력으로 `ValidateCertificate()` 전달됩니다.
* `ValidateCertificate()` 는 인증서 체인의 유효성을 검사한 다음 `CertificateValidated()` 최종 유효성 검사 결과와 함께 전달된 콜백에서 를 호출해야 합니다. 이 메서드는 인증서 체인, 연결이 설정되는 서버의 이름 및 해지 확인을 강제 적용해야 하는지 여부를 허용합니다. 인증서 체인에 여러 인증서가 포함된 경우 첫 번째 인증서는 주체 인증서입니다.

>[!NOTE]
>사용 사례에 다른 형식의 유효성 검사가 필요한 경우(위의 #1 인증서 사용 사례 참조) 시스템 유효성 검사를 완전히 무시합니다. 대신 DER로 인코딩된 X.509 인증서를 처리할 수 있는 API 또는 라이브러리를 사용하여 인증서 체인을 디코딩하고 사용 사례에 필요한 검사를 수행합니다.

## <a name="secure-connection-using-the-openxr-api"></a>OpenXR API를 사용하여 연결 보호

[OpenXR API를](../native/openxr.md) 사용하는 경우 모든 보안 연결 관련 API를 OpenXR 확장의 일부로 사용할 수 `XR_MSFT_holographic_remoting` 있습니다.

>[!IMPORTANT]
>홀로그램 Remoting OpenXR 확장 API에 대해 알아보려면 [홀로그램 Remoting 샘플 github 리포지토리에서](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)찾을 수 있는 [사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) 확인하세요.

OpenXR 확장을 사용하는 보안 연결의 주요 요소는 `XR_MSFT_holographic_remoting` 다음과 같은 콜백입니다.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`은 전송할 인증 토큰을 생성하거나 검색합니다.
- `xrRemotingValidateServerCertificateCallbackMSFT`- 인증서 체인의 유효성을 검사합니다.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`는 클라이언트 인증 토큰의 유효성을 검사합니다.
- `xrRemotingRequestServerCertificateCallbackMSFT`- 서버 애플리케이션에 사용할 인증서를 제공하세요.

이러한 콜백은 및 을 통해 Remoting OpenXR 런타임에 제공할 수 `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` 있습니다. 또한 또는 를 `XrRemotingConnectInfoMSFT` 사용하는지 여부에 따라 구조체 또는 구조의 secureConnection 매개 변수를 통해 보안 연결을 사용하도록 설정해야 `XrRemotingListenInfoMSFT` `xrRemotingConnectMSFT` `xrRemotingListenMSFT` 합니다.

이 API는 [홀로그램 Remoting 보안 구현에](#implementing-holographic-remoting-security)설명된 IDL 기반 API와 비슷합니다. 그러나 인터페이스를 구현하는 대신 콜백 구현을 제공해야 합니다. 자세한 예제는 [OpenXR 샘플 앱](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목
* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [홀로그램 Remoting 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)