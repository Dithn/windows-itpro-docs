---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Secured kernel

To secure the kernel, we have two key features: Virtualization-based security (VBS) and hypervisor-protected code integrity (HVCI). All Windows 11 devices support HVCI and come with VBS and HVCI protection turned on by default on most/all devices.

### Virtualization-based security (VBS)

:::row:::
    :::column:::
        Virtualization-based security (VBS), also known as core isolation, is a critical building block in a secure system. VBS uses hardware virtualization features to host a secure kernel separated from the operating system. This means that even if the operating system is compromised, the secure kernel is still protected. The isolated VBS environment protects processes, such as security solutions and credential managers, from other processes running in memory. Even if malware gains access to the main OS kernel, the hypervisor and virtualization hardware help prevent the malware from executing unauthorized code or accessing platform secrets in the VBS environment. VBS implements virtual trust level 1 (VTL1), which has higher privilege than the virtual trust level 0 (VTL0) implemented in the main kernel.
    :::column-end:::
    :::column:::
:::image type="content" source="../images/vbs-diagram.png" alt-text="Diagram of VBS architecture." lightbox="../images/vbs-diagram.png" border="false":::
    :::column-end:::
:::row-end:::

Since more privileged virtual trust levels (VTLs) can enforce their own memory protections, higher VTLs can effectively protect areas of memory from lower VTLs. In practice, this allows a lower VTL to protect isolated memory regions by securing them with a higher VTL. For example, VTL0 could store a secret in VTL1, at which point only VTL1 could access it. Even if VTL0 is compromised, the secret would be safe.

[!INCLUDE [learn-more](learn-more.md)]

- [Virtualization-based security (VBS)](/windows-hardware/design/device-experiences/oem-vbs)

### Hypervisor-protected code integrity (HVCI)

Hypervisor-protected code integrity (HVCI), also called memory integrity, uses VBS to run Kernel Mode Code Integrity (KMCI) inside the secure VBS environment instead of the main Windows kernel. This helps prevent attacks that attempt to modify kernel-mode code for things like drivers. The KMCI checks that all kernel code is properly signed and hasn't been tampered with before it's allowed to run. HVCI ensures that only validated code can be executed in kernel mode. The hypervisor uses processor virtualization extensions to enforce memory protections that prevent kernel-mode software from executing code that hasn't been first validated by the code integrity subsystem. HVCI protects against common attacks like WannaCry that rely on the ability to inject malicious code into the kernel. HVCI can prevent injection of malicious kernel-mode code even when drivers and other kernel-mode software have bugs.

With new installs of Windows 11, OS support for VBS and HVCI is turned on by default for all devices that meet prerequisites.

[!INCLUDE [learn-more](learn-more.md)]

- [Enable virtualization-based protection of code integrity](/windows/security/hardware-security/enable-virtualization-based-protection-of-code-integrity)

### :::image type="icon" source="../images/new-button-title.svg" border="false"::: Hypervisor-enforced Paging Translation (HVPT)

Hypervisor-enforced Paging Translation (HVPT) is a security enhancement to enforce the integrity of guest virtual address to guest physical address translations. HVPT helps protect critical system data from write-what-where attacks where the attacker can write an arbitrary value to an arbitrary location often as the result of a buffer overflow. HVPT helps to protect page tables that configure critical system data structures.

### Hardware-enforced stack protection

Hardware-enforced stack protection integrates software and hardware for a modern defense against cyberthreats like memory corruption and zero-day exploits. Based on Control-flow Enforcement Technology (CET) from Intel and AMD Shadow Stacks, hardware-enforced stack protection is designed to protect against exploit techniques that try to hijack return addresses on the stack.

Application code includes a program processing stack that hackers seek to corrupt or disrupt in a type of attack called *stack smashing*. When defenses like executable space protection began thwarting such attacks, hackers turned to new methods like return-oriented programming. Return-oriented programming, a form of advanced stack smashing, can bypass defenses, hijack the data stack, and ultimately force a device to perform harmful operations. To guard against these control-flow hijacking attacks, the Windows kernel creates a separate *shadow stack* for return addresses. Windows 11 extends stack protection capabilities to provide both user mode and kernel mode support.

[!INCLUDE [learn-more](learn-more.md)]

- [Understanding Hardware-enforced Stack Protection](https://techcommunity.microsoft.com/blog/windowsosplatform/understanding-hardware-enforced-stack-protection/1247815)
- [Developer Guidance for hardware-enforced stack protection](https://techcommunity.microsoft.com/blog/windowsosplatform/developer-guidance-for-hardware-enforced-stack-protection/2163340)
