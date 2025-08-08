---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/universal-print.svg" border="false"::: Universal Print

Universal Print eliminates the need for on-premises print servers. It also eliminates the need for print drivers from the users' Windows devices and makes the devices secure, reducing the malware attacks that typically exploit vulnerabilities in driver model. It enables Universal Print-ready printers (with native support) to connect directly to the Microsoft Cloud. All major printer OEMs have these [models][LINK-23]. It also supports existing printers by using the connector software that comes with Universal Print.

Unlike traditional print solutions that rely on Windows print servers, Universal Print is a Microsoft-hosted cloud subscription service that supports a Zero Trust security model when using the Universal Print-ready printers. Customers can enable network isolation of printers, including the Universal Print connector software, from the rest of the organization's resources. Users and their devices don't need to be on the same local network as the printers or the Universal Print connector.

Universal Print supports Zero Trust security by requiring that:

- Each connection and API call to Universal Print cloud service requires authentication validated by Microsoft Entra ID<sup>[\[4\]](../conclusion.md#footnote4)</sup>. A hacker would have to have knowledge of the right credentials to successfully connect to the Universal Print service
- Every connection established by the user's device (client), the printer, or another cloud service to the Universal Print cloud service uses SSL with TLS 1.2 protection. This protects network snooping of traffic to gain access to sensitive data
- Each printer registered with Universal Print is created as a device object in the customer's Microsoft Entra ID tenant and issued its own device certificate. Every connection from the printer is authenticated using this certificate. The printer can access only its own data and no other device's data
- Applications can connect to Universal Print using either user, device, or application authentication. To ensure data security, it's highly recommended that only cloud applications use application authentication
- Each acting application must register with Microsoft Entra ID and specify the set of permission scopes it requires. Microsoft's own acting applications - for example, the Universal Print connector - are registered with the Microsoft Entra ID service. Customer administrators need to provide their consent to the required permission scopes as part of onboarding the application to their tenant
- Each authentication with Microsoft Entra ID from an acting application can't extend the permission scope as defined by the acting client app. This prevents the app from requesting additional permissions if the app is breached

Additionally, Windows 11 includes device management support to simplify printer setup for users. With support from Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, admins can now configure policy settings to provision specific printers onto the user's Windows devices.

Universal Print stores the print data in cloud securely in Office Storage, the same storage used by other Microsoft 365 products.

More information about handling of Microsoft 365 data (this includes Universal Print data) can be found [here][LINK-24].

The Universal Print secure release platform ensures user privacy, secures organizational data, and reduces print wastage. It eliminates the need for people to rush to a shared printer as soon as they send a print job to ensure that no one sees the private or confidential content. Sometimes, printed documents are picked up by another person or not picked up at all and discarded. Detailed support and configuration information can be found [here][LINK-25].

Universal Print supports Administrative Units in Microsoft Entra ID to enable the assignments of a *Printer Administrator* role to specific teams in the organization. The assigned team can configure only the printers that are part of the same Administrative Unit.

For customers who want to stay on print servers, we recommend using the Microsoft IPP Print driver. For features beyond what's covered in the standard IPP driver, use Print Support Applications (PSA) for Windows from the respective printer OEM.

[!INCLUDE [learn-more](learn-more.md)]

- [Universal Print][LINK-26]
- [Data handling in Universal Print][LINK-27]
- [Delegate Printer Administration with Administrative Units][LINK-28]
- [Print support app design guide][LINK-29]

<!--links-->

[LINK-23]: /universal-print/fundamentals/universal-print-partner-integrations
[LINK-24]: /microsoft-365/enterprise/m365-dr-overview
[LINK-25]: /universal-print/fundamentals/universal-print-qrcode
[LINK-26]: https://www.microsoft.com/microsoft-365/windows/universal-print
[LINK-27]: /universal-print/data-handling
[LINK-28]: /universal-print/portal/delegated-admin
[LINK-29]: /windows-hardware/drivers/devapps/print-support-app-design-guide
