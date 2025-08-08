---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Attack surface reduction rules

Attack surface reduction rules help prevent actions and applications or scripts that are often abused to compromise devices and networks. By controlling when and how executables and/or script can run, thereby reducing the attack surface, you can reduce the overall vulnerability of your organization. Administrators can configure specific attack surface reduction rules to help block certain behaviors, such as:

- Launching executable files and scripts that attempt to download or run files
- Running obfuscated or otherwise suspicious scripts
- Performing behaviors that apps don't usually initiate during normal day-to-day work

For example, an attacker might try to run an unsigned script from a USB drive or have a macro in an Office document make calls directly to the Win32 API. Attack surface reduction rules can constrain these kinds of risky behaviors and improve the defensive posture of the device. For comprehensive protection, follow steps for enabling hardware-based isolation

[!INCLUDE [learn-more](learn-more.md)]

- [Attack surface reduction](/defender-endpoint/overview-attack-surface-reduction)
