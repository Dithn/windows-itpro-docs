---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Microsoft Pluton security processor

The Microsoft Pluton security processor is the result of Microsoft's close partnership with silicon partners. Pluton enhances the protection of Windows 11 devices with a hardware security processor that provides extra protection for cryptographic keys and other secrets. Pluton is designed to reduce the attack surface by integrating the security chip directly into the processor. It can be used as a TPM 2.0 or as a standalone security processor. When a security processor is located on a separate, discrete chip on the motherboard, the communication path between the hardware root-of-trust and the CPU can be vulnerable to physical attack. Embedding Pluton into the CPU makes it harder to exploit the communication path.

Pluton supports the TPM 2.0 industry standard, allowing customers to immediately benefit from enhanced security for Windows features that rely on TPMs, including BitLocker, Windows Hello, and System Guard. Pluton can also support other security functionality beyond what is possible with the TPM 2.0 specification. This extensibility allows for more Pluton firmware and OS features to be delivered over time via Windows Update.

As with other TPMs, credentials, encryption keys, and other sensitive information can't be easily extracted from Pluton even if an attacker installed malware or has physical possession of the PC. Storing sensitive data like encryption keys securely within the Pluton processor, which is isolated from the rest of the system, helps ensure that attackers can't access sensitive data - even if attackers use emerging techniques like speculative execution.

Pluton also solves the major security challenge of keeping its own security processor firmware up to date across the entire PC ecosystem. Today customers receive security firmware updates from different sources, which might make it difficult to get alerts about security updates, and keeping systems in a vulnerable state. Pluton provides a flexible, updateable platform for its firmware that implements end-to-end security functionality authored, maintained, and updated by Microsoft. Pluton is integrated with the Windows Update service, benefiting from over a decade of operational experience in reliably delivering updates across over a billion endpoint systems. Microsoft Pluton is available with select new Windows PCs.

Pluton aims to ensure long-term security resilience. With the rising threat landscape influenced by artificial intelligence, memory safety will become ever more critical. To meet these demands, in addition to facilitating reliable updates to security processor firmware, we chose the open-source Tock system as the Rust-based foundation to develop the Pluton security processor firmware and actively contribute back to the Tock community. This collaboration with an open community ensures rigorous security scrutiny, and using Rust mitigates memory safety threats.

Ultimately, Pluton establishes the security backbone for Copilot + PC, thanks to tight partnerships with our silicon collaborators and OEMs. The Qualcomm Snapdragon X, AMD Ryzen AI, and Intel Core Ultra 200V mobile processors (codenamed Lunar Lake) processor platforms all incorporate Pluton as their security subsystem .

[!INCLUDE [learn-more](learn-more.md)]

- [Microsoft Pluton processor - The security chip designed for the future of Windows PCs](https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/)
- [Microsoft Pluton security processor](/windows/security/hardware-security/pluton/microsoft-pluton-security-processor)
