---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Software bill of materials (SBOM)

In the Windows ecosystem, ensuring the integrity and authenticity of software components is paramount. To achieve this, we utilize Software Bill of Materials (SBOMs) and COSE (CBOR Object Signing and Encryption) sign all evidence. SBOMs provide a comprehensive inventory of software components, including their dependencies and associated metadata. Transparency is crucial for vulnerability management and compliance with security standards.

The COSE signing process enhances the trustworthiness of SBOMs by providing cryptographic signatures that verify the integrity and authenticity of the SBOM content. The CoseSignTool, a platform-agnostic command line application, is employed to apply and verify these digital signatures. This tool ensures that all SBOMs and other build evidence are signed and validated, maintaining a high level of security within the software supply chain.

By integrating SBOMs and COSE signing evidence, we offer stakeholders visibility into the components they use, ensuring that all software artifacts are trustworthy and secure. This approach aligns with our commitment to end-to-end supply chain security, providing a robust framework for managing and verifying software components across the Windows ecosystem.

[!INCLUDE [learn-more](learn-more.md)]

- [SBOM tool](https://github.com/microsoft/sbom-tool)
- [Code Sign Tool](https://github.com/microsoft/CoseSignTool)
