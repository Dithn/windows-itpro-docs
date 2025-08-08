---
author: paolomatarazzo
ms.author: paoloma
ms.date: 08/04/2025
ms.topic: include
---

## Trusted Boot (Secure Boot + Measured Boot)

Windows 11 requires all PCs to use Unified Extensible Firmware Interface (UEFI)'s Secure Boot feature. When a Windows 11 device starts, Secure Boot and Trusted Boot work together to prevent malware and corrupted components from loading. Secure Boot provides initial protection, then Trusted Boot picks up the process.

Secure Boot makes a safe and trusted path from the Unified Extensible Firmware Interface (UEFI) through the Windows kernel's Trusted Boot sequence. Malware attacks on the Windows boot sequence are blocked by the signature-enforcement handshakes throughout the boot sequence between the UEFI, bootloader, kernel, and application environments.

To mitigate the risk of firmware rootkits, the PC verifies the digital signature of the firmware at the start of the boot process. Secure Boot then checks the digital signature of the OS bootloader and all code that runs before the operating system starts, ensuring that the signature and code are uncompromised and trusted according to the Secure Boot policy.

Trusted Boot picks up the process that begins with Secure Boot. The Windows bootloader verifies the digital signature of the Windows kernel before loading it. The Windows kernel, in turn, verifies every other component of the Windows startup process, including boot drivers, startup files, and any anti-malware product's early-launch anti-malware (ELAM) driver. If any of these files have been tampered with, the bootloader detects the problem and refuses to load the corrupted component. Often, Windows can automatically repair the corrupted component, restoring the integrity of Windows and allowing the PC to start normally.

[!INCLUDE [learn-more](learn-more.md)]

- [Secure the Windows boot process](/windows/security/operating-system-security/system-security/secure-the-windows-10-boot-process)
- [Secure Boot and Trusted Boot](/windows/security/operating-system-security/system-security/trusted-boot)
