---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Kernel direct memory access (DMA) protection

Windows 11 protects against physical threats such as drive-by direct memory access (DMA) attacks. Peripheral Component Interconnect Express (PCIe) hot-pluggable devices, including Thunderbolt, USB4, and CFexpress, enable users to connect a wide variety of external peripherals to their PCs with the same plug-and-play convenience as USB. These devices encompass graphics cards and other PCI components. Since PCI hot-plug ports are external and easily accessible, PCs are susceptible to drive-by DMA attacks. Memory access protection (also known as Kernel DMA Protection) protects against these attacks by preventing external peripherals from gaining unauthorized access to memory. Drive-by DMA attacks typically happen quickly while the system owner isn't present. The attacks are performed using simple to moderate attacking tools created with affordable, off-the-shelf hardware and software that don't require the disassembly of the PC. For example, a PC owner might leave a device for a quick coffee break. Meanwhile, an attacker plugs an external tool into a port to steal information or inject code that gives the attacker remote control over the PCs, including the ability to bypass the lock screen. With memory access protection built in and enabled, Windows 11 is protected against physical attack wherever people work.

[!INCLUDE [learn-more](learn-more.md)]

- [Kernel direct memory access (DMA) protection](/windows/security/hardware-security/kernel-dma-protection-for-thunderbolt)
