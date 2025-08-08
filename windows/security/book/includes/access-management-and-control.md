---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Access management and control

Access control in Windows ensures that shared resources are available to users and groups other than the resource's owner and are protected from unauthorized use. IT administrators can manage the access of users, groups, and computers to objects and assets on a network or computer. After a user is authenticated, Windows implements the second phase of protecting resources with built-in authorization and access control technologies. These technologies determine if an authenticated user has the correct permissions.

Access Control Lists (ACLs) describe the permissions for a specific object and can also contain System Access Control Lists (SACLs). SACLs provide a way to audit specific system level events, such as when a user attempts to access file system objects. These events are essential for tracking activity for objects that are sensitive or valuable and require extra monitoring. Being able to audit when a resource attempts to read or write part of the operating system is critical to understanding a potential attack.

IT administrators can refine the application and management of access to:

- Protect a greater number and variety of network resources from misuse
- Provision users to access resources in a manner that is consistent with organizational policies and the requirements of their jobs. Organizations can implement the principle of least-privilege access, which asserts that users should be granted access only to the data and operations they require to perform their jobs
- Update users' ability to access resources regularly, as an organization's policies change or as users' jobs change
- Support evolving workplace needs, including access from hybrid or remote locations, or from a rapidly expanding array of devices, including tablets and phones
- Identify and resolve access issues when legitimate users are unable to access resources that they need to perform their jobs

[!INCLUDE [learn-more](learn-more.md)]

- [Access control](/windows/security/identity-protection/access-control/access-control)
