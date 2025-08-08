---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Transport Layer Security (TLS)

Transport Layer Security (TLS) is a popular security protocol, encrypting data in transit to help provide a more secure communication channel between two endpoints. Windows enables the latest protocol versions and strong cipher suites by default and offers a full suite of extensions such as client authentication for enhanced server security, or session resumption for improved application performance. TLS 1.3 is the latest version of the protocol and is enabled by default in Windows. This version helps to eliminate obsolete cryptographic algorithms, enhance security over older versions, and aim to encrypt as much of the TLS handshake as possible. The handshake is more performant with one less round trip per connection on average and supports only strong cipher suites which provide perfect forward secrecy and less operational risk. Using TLS 1.3 provides more privacy and lower latencies for encrypted online connections. If the client or server application on either side of the connection doesn't support TLS 1.3, the connection falls back to TLS 1.2. Windows uses the latest Datagram Transport Layer Security (DTLS) 1.2 for UDP communications.

[!INCLUDE [learn-more](learn-more.md)]

- [TLS/SSL overview (Schannel SSP)](/windows-server/security/tls/tls-ssl-schannel-ssp-overview)
- [TLS 1.0 and TLS 1.1 soon to be disabled in Windows](https://techcommunity.microsoft.com/blog/windows-itpro-blog/tls-1-0-and-tls-1-1-soon-to-be-disabled-in-windows/3887947)
