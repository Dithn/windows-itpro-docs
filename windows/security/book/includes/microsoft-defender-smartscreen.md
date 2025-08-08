---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Microsoft Defender SmartScreen

Microsoft Defender SmartScreen protects against phishing, malware websites and applications, and the downloading of potentially malicious files.

SmartScreen determines whether a site is potentially malicious by:

- Analyzing visited webpages to find indications of suspicious behavior. If it determines a page is suspicious, it will show a warning page advising caution
- Checking the visited sites against a dynamic list of reported phishing sites and malicious software sites. If it finds a match, SmartScreen warns that the site might be malicious

SmartScreen also determines whether a downloaded app or app installer is potentially malicious by:

- Checking downloaded files against a list of reported malicious software sites and programs known to be unsafe. If it finds a match, SmartScreen warns that the file might be malicious
- Checking downloaded files against a list of well-known files. If the file is of a dangerous type and not well-known, SmartScreen displays a caution alert

With enhanced phishing protection in Windows 11, SmartScreen also alerts people when they're entering their Microsoft credentials into a potentially risky location, regardless of which application or browser is used. IT can customize which notifications appear through Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>. This protection runs in audit mode by default, giving IT admins full control to make decisions around policy creation and enforcement.

Because Windows 11 comes with these enhancements already built in and enabled, users have extra security from the moment they turn on their device.

[!INCLUDE [learn-more](learn-more.md)]

- [Microsoft Defender SmartScreen documentation library](/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/)