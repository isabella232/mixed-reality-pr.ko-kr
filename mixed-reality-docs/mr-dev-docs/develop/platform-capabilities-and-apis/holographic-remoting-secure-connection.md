---
title: 홀로그램 원격을 사용하여 보안 연결 설정
description: 이 페이지에서는 Holographic Remoting을 사용할 때 암호화 된 보안 연결을 설정 하는 방법을 설명 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683648"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>홀로그램 원격을 사용하여 보안 연결 설정

>[!IMPORTANT]
>이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

이 페이지에서는 Holographic Remoting을 사용할 때 암호화 된 보안 연결을 설정 하는 방법을 설명 합니다.

개방형 WiFi 또는 인터넷과 같은 안전 하지 않은 네트워크를 통해 HoloLens 2로 콘텐츠를 스트리밍하는 경우 암호화 된 연결을 사용 하는 것이 좋습니다.

>[!IMPORTANT]
>암호화 된 연결을 사용 하는 신뢰할 수 있는 로컬 WiFi를 사용 하는 경우에도 고려해 야 합니다.

암호화 된 연결을 사용할 수 있으려면 [사용자 지정 플레이어](holographic-remoting-create-player.md) 와 [사용자 지정 원격 앱](holographic-remoting-create-host.md)을 모두 구현 해야 합니다.

기본 플랫폼 TLS 구현을 사용 하 여 암호화를 구현 합니다.

## <a name="basics-of-an-encrypted-connection"></a>암호화 된 연결의 기본 사항

인증서 교환을 허용 하려면 다음 개체를 구현 해야 합니다.

>[!TIP]
>WinRT 인터페이스 구현은 c + +/WinRT. 사용 하 여 쉽게 수행할 수 있습니다. [C + +/vb를 사용 하는 작성자 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 장에서는이에 대해 자세히 설명 합니다.

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 패키지 내에는 보안 연결과 관련 된 API에 대 한 자세한 설명서가 포함 되어 있습니다.

1) 인터페이스를 구현 해야 하는 인증서 개체 ```ICertificate``` 입니다.

    * 메서드를 통해 pfx 인증서의 이진 콘텐츠를 반환 합니다 ```GetCertificatePfx``` . .Pfx 파일의 이진 콘텐츠와 동일 합니다.
    * 를 통해 인증서 주체 이름을 반환 합니다 ```GetSubjectName``` .
    * 를 통해 pfx 암호를 반환 ```GetPfxPassword``` 합니다. 보호 되지 않는 pfx에 대해 빈 문자열을 반환 합니다.

2) ```ICertificateProvider```메서드를 통해 요청 될 때 인증서를 제공 하는 인터페이스를 구현 하는 인증서 공급자 ```GetCertificate``` 입니다.

3) 인터페이스를 구현 하는 인증서 유효성 검사기 ```ICertificateValidator``` 입니다. 해당 작업은 들어오는 인증서를 확인 하는 것입니다.
    * ```PerformSystemValidation``` ```true``` 기본 플랫폼에서 들어오는 인증서 체인의 유효성을 검사 해야 하는 경우 메서드는을 반환 하 고 그렇지 않으면를 반환 해야 ```false``` 합니다.
    * ```ValidateCertificate``` 는 인증서의 유효성 검사를 요청 하기 위해 클라이언트 컨텍스트에서 호출 됩니다. 이 메서드는 인증서 체인 (주체 인증서가 있는 첫 번째 인증서 포함), 연결이 설정 되는 서버의 이름 및 해지 검사 강제 적용 여부를 수락 합니다. 기본 시스템에서 유효성 검사를 요청한 경우 시스템 유효성 검사 결과가 제공 됩니다. ```CertificateValidated```적절 한 결과를 사용 하거나 유효성 검사를 취소 하 여 처리를 계속 하려면 ```Cancel``` 전달 된에 대해를 호출 해야 합니다 ```ICertificateValidationCallback``` .

또한 보안 토큰을 교환할 수 있도록 다음 개체를 구현 해야 합니다.

1) 인터페이스를 구현 하는 인증 공급자 ```IAuthenticationProvider``` 입니다. 클라이언트 ```GetToken``` 인증에 대 한 토큰을 요청 하기 위해 클라이언트 컨텍스트에서 해당 메서드를 호출 합니다. ```TokenReceived```인증 토큰을 제공 하 고 연결 프로세스를 계속 하거나 취소 하려면 전달 된에서 프로세스를 호출 해야 합니다 ```Cancel``` ```IAuthenticationProviderCallback``` .
2) 인터페이스를 구현 하는 인증 수신자 ```IAuthenticationReceiver``` 입니다. 해당 작업은 들어오는 토큰의 유효성을 검사 하는 것입니다.
    * ```GetRealm```메서드는 인증 영역 이름을 반환 해야 합니다.
    * ```ValidateToken```메서드는 클라이언트 인증 토큰의 유효성 검사를 요청 하기 위해 서버 네트워크 컨텍스트에서 호출 됩니다. ```ValidationCompleted```유효성 검사의 신호 완료를 계속 하거나 ```Cancel``` 클라이언트 연결을 거부 하려면를 호출 합니다. 에 전달 된 유효성 검사 결과에 따라 클라이언트 연결이 허가 되거나 거부 됩니다 ```ValidationCompleted``` . 

이러한 개체를 구현한 후에는 ```ListenSecure``` ```Listen``` ```ConnectSecure``` ```Connect``` 각각 원격 컨텍스트 및 플레이어 컨텍스트 대신 및 대신를 호출 해야 합니다. ```ListenSecure``` 에는 추가 인증서 공급자 및 인증 수신기가 필요 ```Listen``` 합니다. ```ConnectSecure``` 에는 추가 인증 공급자 및 인증서 유효성 검사기가 필요 ```Connect``` 합니다.

## <a name="see-also"></a>참고 항목
* [홀로그램 원격 원격 앱 작성](holographic-remoting-create-host.md)
* [사용자 지정 홀로그램 원격 플레이어 앱 작성](holographic-remoting-create-player.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)
