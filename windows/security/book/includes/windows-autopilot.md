---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Windows Autopilot

Traditionally, IT professionals spend significant time building and customizing images that will later be deployed to devices. If you're purchasing new devices or managing device refresh cycles, you can use Windows Autopilot to set up and preconfigure new devices, getting them ready for productive use. Autopilot helps you ensure your devices are delivered locked down and compliant with corporate security policies. The solution can also be used to reset, repurpose, and recover devices with zero touch by your IT team and no infrastructure to manage, enhancing efficiency with a process that's both easy and simple.

With Windows Autopilot, there's no need to reimage or manually set-up devices before giving them to the users. Your hardware vendor can ship them, ready to go, directly to the users. From a user perspective, they turn on their device, go online, and Windows Autopilot delivers apps and settings.

Windows Autopilot enables you to:

- Automatically join devices to Microsoft Entra ID or Active Directory via Microsoft Entra hybrid join
- Autoenroll devices into a device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup> (requires a Microsoft Entra ID Premium subscription for configuration)
- Create and autoassignment of devices to configuration groups based on a device's profile
- Customize of the out-of-box experience (OOBE) content specific to your organization

Existing devices can also be quickly prepared for a new user with Windows Autopilot Reset. The reset capability is also useful in break/fix scenarios to quickly bring a device back to a business-ready state.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows Autopilot](/autopilot/overview)
- [Windows Autopilot Reset](/mem/autopilot/windows-autopilot-reset)
