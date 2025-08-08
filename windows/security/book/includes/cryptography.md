---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Cryptography

Cryptography is designed to protect user and system data. The cryptography stack in Windows 11 extends from the chip to the cloud, enabling Windows, applications, and services to protect system and user secrets. For example, data can be encrypted so that only a specific reader with a unique key can read it. As a basis for data security, cryptography helps prevent anyone except the intended recipient from reading data, performs integrity checks to ensure data is free of tampering, and authenticates identity to ensure that communication is secure. Windows 11 cryptography is certified to meet the Federal Information Processing Standard (FIPS) 140. FIPS 140 certification ensures that US government-approved algorithms are correctly implemented.

[!INCLUDE [learn-more](learn-more.md)]

- FIPS 140 validation

Windows cryptographic modules provide low-level primitives such as:

- Random number generators (RNG)
- Support for AES 128/256 with XTS, ECB, CBC, CFB, CCM, and GCM modes of operation; RSA and DSA 2048, 3072, and 4,096 key sizes; ECDSA over curves P-256, P-384, P-521
- Hashing (support for SHA1, SHA-256, SHA-384, and SHA-512)
- Signing and verification (padding support for OAEP, PSS, and PKCS1)
- Key agreement and key derivation (support for ECDH over NIST-standard prime curves P-256, P-384, P-521 and HKDF)

Application developers can use these cryptographic modules to perform low-level cryptographic operations (Bcrypt), key storage operations (NCrypt), protect static data (DPAPI), and securely share secrets (DPAPI-NG).

[!INCLUDE [learn-more](learn-more.md)]

- Cryptography and certificate management

Developers can access the modules on Windows through the Cryptography Next Generation API (CNG), which is powered by Microsoft's open-source cryptographic library, SymCrypt. SymCrypt supports complete transparency through its open-source code. In addition, SymCrypt offers performance optimization for cryptographic operations by taking advantage of assembly and hardware acceleration when available.

SymCrypt is part of Microsoft's commitment to transparency, which includes the global Microsoft Government Security Program that aims to provide the confidential security information and resources people need to trust Microsoft's products and services. The program offers controlled access to source code, threat and vulnerability information
exchange, opportunities to engage with technical content about Microsoft's products and services, and access to five globally distributed Transparency Centers.
