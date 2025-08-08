---
title: Extended Security Updates (ESU) program for Windows 10
description: Learn about the Extended Security Updates (ESU) program for Windows 10. The ESU program gives customers the option to receive security updates for Windows 10.
ms.service: windows-client
ms.subservice: itpro-fundamentals
ms.author: mstewart
author: mestew
manager: bpardi
ms.localizationpriority: medium
ms.topic: article
ms.date: 07/14/2025
ms.collection:
  - highpri
  - tier2
appliesto:
  - ✅ <a href="https://learn.microsoft.com/windows/release-health/supported-versions-windows-client" target="_blank">Windows 10</a>
---

# Extended Security Updates (ESU) program for Windows 10
<!-- 8280171-->
> **Looking for consumer information?** For individuals or Windows 10 Home customers, more information about Extended Security Updates for Windows 10 is available in the frequently asked questions section of the [End of support for Windows 10](https://www.microsoft.com/windows/end-of-support) page. For information on how to enroll in ESU, see [Windows 10 Consumer Extended Security Updates (ESU) program](https://support.microsoft.com/windows/33e17de9-36b3-43bb-874d-6c53d2e4bf42).<!--10013381-->

The Windows 10 Extended Security Updates (ESU) program gives customers the option to receive security updates for PCs enrolled in the program. ESU is a paid program that provides individuals and organizations of all sizes with the option to extend the use of Windows 10 devices past the end of support date in a more secure manner. For more information about the Windows 10 lifecycle, see the [Windows Lifecycle FAQ](/lifecycle/faq/windows).

Individuals or organizations who elect to continue using Windows 10 after support ends on October 14, 2025, will have the option of enrolling their PCs into a paid ESU subscription. The ESU program enables PCs to continue to receive critical and important security updates through an annual subscription service after support ends. The [Microsoft Security Response Center](https://msrc.microsoft.com/) defines the [severity rating for security updates](https://www.microsoft.com/msrc/security-update-severity-rating-system).


## Device prerequisites

To be eligible to install updates from the ESU program, devices must be running Windows 10, version 22H2. For more information on prerequisites and enabling ESU in commercial environments, see [Enable Extended Security Updates (ESU)](enable-extended-security-updates.md).

## Limitations

ESUs doesn't include the following items:

- New features
- Customer-requested nonsecurity updates
- Design change requests
- General support won't be provided for Windows versions past the end of support date. The Windows 10 ESU only includes support for the license activation, installation, and possible regressions of the ESU itself. To get technical support for these issues related to the ESU, organizations must have an active [support plan](https://www.microsoft.com/microsoft-unified) in place. <!--9913216-->



## Frequently asked questions

The following are frequently asked questions about the ESU program for Windows 10:

### How much does ESU cost?

Extended Security Updates for organizations and businesses on Windows 10 can be purchased today through the Microsoft Volume Licensing Program, at $61 USD per device for Year One. For more information, see [When to use Windows 10 Extended Security Updates](https://techcommunity.microsoft.com/blog/windows-itpro-blog/when-to-use-windows-10-extended-security-updates/4102628). The price doubles every consecutive year, for a maximum of three years. ESU is available at no additional cost for Windows 10 virtual machines in the following services:

- [Windows 365](/windows-365/overview)
- [Azure Virtual Desktop](/azure/virtual-desktop/overview)
- [Azure virtual machines](/azure/virtual-machines/overview)
- [Azure Dedicated Host](/azure/virtual-machines/dedicated-hosts)
- [Azure VMware Solution](/azure/azure-vmware/introduction) (includes [Citrix](/azure/azure-vmware/azure-vmware-solution-citrix) and [Omnissa Horizon on Azure VMware Solution](/azure/azure-vmware/azure-vmware-solution-horizon))
- [Nutanix Cloud Clusters on Azure](/azure/baremetal-infrastructure/workloads/nc2-on-azure/about-nc2-on-azure)
- [Azure Local](/azure/azure-local/overview) (Azure Local is the new name for Azure Stack HCI)
- [Azure Stack Hub](/azure-stack/operator/azure-stack-overview)
- [Azure Stack Edge](/azure/databox-online/)

Additionally, Windows 10 endpoints connecting to Windows 365 Cloud PCs will be entitled to the ESU for up to three years, with an active Windows 365 subscription license. For more information about Windows 365, see [What is Windows 365?](/windows-365/overview).

For individuals or Windows 10 Home customers, Extended Security Updates for Windows 10 will be available for purchase at $30 for one year.


### Is there a minimum license purchase requirement for Windows 10 ESU?

The minimum license purchase requirement for Windows 10 ESU is one license.

### Can ESUs be purchased for a specific duration?

The Extended Security Update Program for Windows 10 must be purchased by year. Customers can't buy partial periods, for instance, only six months. Year One starts in November 2025. If you decide to purchase the program in Year Two, you have to pay for Year One too, as ESUs are cumulative.


### When will the ESU offer be available for licensing?

Windows 10 ESU licenses are available to purchase in volume licensing. However, the ESU Multiple Activation Keys displayed in the Microsoft 365 admin center volume licensing Product Details panel are not usable until the end of support date of Windows 10, which is when the defined ESU coverage period begins. For more information, see [Get the product keys for activating Extended Security Update (ESU) licenses](enable-extended-security-updates.md#get-the-product-keys-for-activating-extended-security-update-esu-licenses).

### How long can I get security updates for?

Enrolled PCs belonging to a commercial or educational organization can receive security updates for a maximum of three years after end of support for Windows 10.

### Is technical support included in ESU?

No, technical support isn't included in the ESU program. Microsoft will provide support for customers that encounter challenges related to the ESU.

### Will Windows 10 PCs stop working without the ESU offering?

Windows 10 PCs will continue to work, but we recommend customers upgrade eligible PCs to Windows 11 using Windows Autopatch, Microsoft Intune, or transition to a new Windows 11 PC for the best, most secure computing experience. Customers also have the option to migrate to the cloud and subscribe to Windows 365 to make Windows 11 available to users on any device with a Cloud PC. Beginning October 14, 2025, Microsoft will no longer provide the following for versions of Windows 10 that reach end of support on that date:

- Technical support
- Feature updates or new features
- Quality updates (including security and reliability fixes)

## Related content

For more information about enabling ESU in commercial environments, see [Enable Extended Security Updates (ESU)](enable-extended-security-updates.md).
