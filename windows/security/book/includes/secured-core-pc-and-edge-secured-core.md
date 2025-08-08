---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Secured-core PC and Edge Secured-Core

The March 2021 Security Signals report found that more than 80% of enterprises have experienced at least one firmware attack in the past two years. For customers in data-sensitive industries like financial services, government, and healthcare, Microsoft has worked with OEM partners to offer a special category of devices called Secured-core PCs (SCPCs), and an equivalent category of embedded IoT devices called Edge Secured-Core (ESc). The devices ship with more security measures enabled at the firmware layer, or device core, that underpins Windows.

Secured-core PCs and edge devices help prevent malware attacks and minimize firmware vulnerabilities by launching into a clean and trusted state at startup with a hardware-enforced root-of-trust. Virtualization-based security comes enabled by default. Built-in hypervisor-protected code integrity (HVCI) shield system memory, ensuring that all kernel executable code is signed only by known and approved authorities. Secured-core PCs and edge devices also protect against physical threats such as drive-by direct memory access (DMA) attacks with kernel DMA protection.

Secured-core PCs and edge devices provide multiple layers of robust protection against hardware and firmware attacks. Sophisticated malware attacks commonly attempt to install *bootkits* or *rootkits* on the system to evade detection and achieve persistence. This malicious software may run at the firmware level prior to Windows being loaded or during the Windows boot process itself, enabling the system to start with the highest level of privilege. Because critical subsystems in Windows use Virtualization-based security, protecting the hypervisor becomes increasingly important. To ensure that no unauthorized firmware or software can start before the Windows bootloader, Windows PCs rely on the Unified Extensible Firmware Interface (UEFI) Secure Boot standard, a baseline security feature of all Windows 11 PCs. Secure Boot helps ensure that only authorized firmware and software with trusted digital signatures can execute. In addition, measurements of all boot components are securely stored in the TPM to help establish a nonrepudiable audit log of the boot called the Static Root of Trust for Measurement (SRTM).

Thousands of OEM vendors produce numerous device models with diverse UEFI firmware components, which in turn creates an incredibly large number of SRTM signatures and measurements at bootup. Because these signatures and measurements are inherently trusted by Secure Boot, it can be challenging to constrain trust to only what is needed to boot on any specific device. Traditionally, blocklists and allowlists were the two main techniques used to constrain trust, and they continue to expand if devices rely only on SRTM measurements.

### Dynamic Root of Trust for Measurement (DRTM)

In secured-core PCs and edge devices, System Guard Secure Launch protects bootup with a technology known as the *Dynamic Root of Trust for Measurement (DRTM)*. With DRTM, the system initially follows the normal UEFI Secure Boot process. However, before launching, the system enters a hardware-controlled trusted state that forces the CPU down a hardware-secured code path. If a malware rootkit or bootkit bypasses UEFI Secure Boot and resides in memory, DRTM prevents it from accessing secrets and critical code protected by the Virtualization-based security environment. Firmware Attack Surface Reduction (FASR) technology can be used instead of DRTM on supported devices, such as Microsoft Surface.

System Management Mode (SMM) isolation is an execution mode in x86-based processors that runs at a higher effective privilege than the hypervisor. SMM complements the protections provided by DRTM by helping to reduce the attack surface. Relying on capabilities provided by silicon providers like Intel and AMD, SMM isolation enforces policies that implement restrictions such as preventing SMM code from accessing OS memory. The SMM isolation policy is included as part of the DRTM measurements that can be sent to a verifier like Microsoft Azure Remote Attestation.

:::image type="content" source="../images/secure-launch.png" alt-text="Diagram of secure launch components." lightbox="../images/secure-launch.png" border="false":::

[!INCLUDE [learn-more](learn-more.md)]

- [System Guard Secure Launch](/windows/security/hardware-security/system-guard-secure-launch-and-smm-protection)
- [Firmware Attack Surface Reduction](/windows-hardware/drivers/bringup/firmware-attack-surface-reduction)
- [Windows 11 secured-core PCs](/windows-hardware/design/device-experiences/oem-highly-secure-11)
- [Edge Secured-Core](/azure/certification/overview)

### Configuration lock

In many organizations, IT administrators enforce policies on their corporate devices to protect the OS and keep devices in a compliant state by preventing users from changing configurations and creating configuration drift. Configuration drift occurs when users with local admin rights change settings and put the device out of sync with security policies. Devices in a noncompliant state can be vulnerable until the next sync, when configuration is reset with the device management solution.

Configuration lock is a secured-core PC and edge device feature that prevents users from making unwanted changes to security settings. With configuration lock, Windows monitors supported registry keys and reverts to the IT-desired state in seconds after detecting a drift.

[!INCLUDE [learn-more](learn-more.md)]

- [Secured-core PC configuration lock](/windows/client-management/mdm/config-lock)
