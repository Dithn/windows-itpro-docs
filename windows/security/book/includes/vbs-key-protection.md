---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/new-button-title.svg" border="false"::: VBS key protection

VBS key protection enables developers to secure cryptographic keys using Virtualization-based security (VBS). VBS uses the virtualization extension capability of the CPU to create an isolated runtime outside of the normal OS. When in use, VBS keys are isolated in a secure process, allowing key operations to occur without ever exposing the private key material outside of this space. At rest, private key material is encrypted by a TPM key, which binds VBS keys to the device. Keys protected in this way can't be dumped from process memory or exported in plain text from a user's machine, preventing exfiltration attacks by any admin-level attacker.

[!INCLUDE [learn-more](learn-more.md)]

- [Advancing key protection in Windows using VBS](https://techcommunity.microsoft.com/blog/windows-itpro-blog/advancing-key-protection-in-windows-using-vbs/4050988)
