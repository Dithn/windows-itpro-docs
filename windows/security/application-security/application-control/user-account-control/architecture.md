---
title: User Account Control architecture
description: Learn about the User Account Control (UAC) architecture.
ms.topic: concept-article
ms.date: 04/15/2025
---

# UAC Architecture

The following diagram details the UAC architecture.

:::image type="content" source="images/uac-architecture.gif" alt-text="Diagram that describes the UAC architecture.":::

## User

- **User performs operation requiring privilege**: If the operation changes the file system or registry, Virtualization is called. All other operations call ShellExecute.
- **ShellExecute**: ShellExecute calls CreateProcess. ShellExecute looks for the `ERROR_ELEVATION_REQUIRED` error from CreateProcess. If it receives the error, ShellExecute calls the Application Information service to attempt to perform the requested task with the elevated prompt.
- **CreateProcess**: If the application requires elevation, CreateProcess rejects the call with `ERROR_ELEVATION_REQUIRED`.

## System

- **Application Information service**:
    - A system service that helps start apps that require one or more elevated privileges or user rights to run.
    - The Application Information service helps start such apps by creating a new process for the application with an administrative user's full access token when elevation is required.
    - Depending on the configured policies, the user might give consent.

- **Elevating an ActiveX install**:
    - If ActiveX isn't installed, the system checks the UAC slider level.
    - If ActiveX is installed, the **User Account Control: Switch to the secure desktop when prompting for elevation** Group Policy setting is checked.

- **Check UAC slider level**: UAC has a slider to select from four levels of notification:
    - **Always notify** will:
        - Notify you when programs try to install software or make changes to your computer.
        - Notify you when you make changes to Windows settings.
        - Freeze other tasks until you respond.
        - Recommended if you often install new software or visit unfamiliar websites.
    - **Notify me only when programs try to make changes to my computer** will:
        - Notify you when programs try to install software or make changes to your computer.
        - Not notify you when you make changes to Windows settings.
        - Freeze other tasks until you respond.
        - Recommended if you don't often install apps or visit unfamiliar websites.
    - **Notify me only when programs try to make changes to my computer (do not dim my desktop)** will:
        - Notify you when programs try to install software or make changes to your computer.
        - Not notify you when you make changes to Windows settings.
        - Not freeze other tasks until you respond.
        - Not recommended. Choose this option only if it takes a long time to dim the desktop on your computer.
    - **Never notify (Disable UAC prompts)** will:
        - Not notify you when programs try to install software or make changes to your computer.
        - Not notify you when you make changes to Windows settings.
        - Not freeze other tasks until you respond.
        - Not recommended due to security concerns.

- **Secure desktop enabled**: The **User Account Control: Switch to the secure desktop when prompting for elevation** policy setting is checked:
    - If the secure desktop is enabled, all elevation requests go to the secure desktop regardless of prompt behavior policy settings for administrators and standard users.
    - If the secure desktop isn't enabled, all elevation requests go to the interactive user's desktop, and the per-user settings for administrators and standard users are used.

- **CreateProcess**:
    - CreateProcess calls AppCompat, Fusion, and Installer detection to assess if the app requires elevation.
    - The file is then inspected to determine its requested execution level, which is stored in the application manifest for the file.
    - CreateProcess fails if the requested execution level specified in the manifest doesn't match the access token and returns an error (ERROR_ELEVATION_REQUIRED) to ShellExecute.

- **AppCompat**:
    - The AppCompat database stores information in the application compatibility fix entries for an application.

- **Fusion**:
    - The Fusion database stores information from application manifests that describe the applications.
    - The manifest schema is updated to add a new requested execution level field.

- **Installer detection**:
    - Installer detection detects setup files and helps prevent installations from being run without the user's knowledge and consent.

## Kernel

- **Virtualization**: Virtualization technology ensures that noncompliant apps don't silently fail to run or fail in a way that the cause can't be determined. UAC also provides file and registry virtualization and logging for applications that write to protected areas.
- **File system and registry**: The per-user file and registry virtualization redirects per-computer registry and file write requests to equivalent per-user locations. Read requests are redirected to the virtualized per-user location first and to the per-computer location second.

The slider never turns off UAC completely. If you set it to **Never notify**, it will:

- Keep the UAC service running
- Cause all elevation request initiated by administrators to be autoapproved without showing a UAC prompt
- Automatically deny all elevation requests for standard users

> [!IMPORTANT]
> In order to fully disable UAC, you must disable the policy **User Account Control: Run all administrators in Admin Approval Mode**. Some Universal Windows Platform apps might not work when UAC is disabled.

## Virtualization

Because system administrators in enterprise environments attempt to secure systems, many line-of-business (LOB) applications are designed to use only a standard user access token. As a result, you don't need to replace most apps when UAC is turned on.

Windows includes file and registry virtualization technology for apps that aren't UAC-compliant and that requires an administrator's access token to run correctly. When an administrative app that isn't UAC-compliant attempts to write to a protected folder, such as *Program Files*, UAC gives the app its own virtualized view of the resource it's attempting to change. The virtualized copy is maintained in the user's profile. This strategy creates a separate copy of the virtualized file for each user that runs the noncompliant app.

Most app tasks operate properly by using virtualization features. Although virtualization allows most applications to run, it's a short-term fix and not a long-term solution. App developers should modify their apps to be compliant as soon as possible, rather than relying on file, folder, and registry virtualization.

Virtualization isn't an option in the following scenarios:

- Virtualization doesn't apply to apps that are elevated and run with a full administrative access token
- Virtualization supports only 32-bit apps. Nonelevated 64-bit apps receive an access denied message when they attempt to acquire a handle (a unique identifier) to a Windows object. Native Windows 64-bit apps are required to be compatible with UAC and to write data into the correct locations
- Virtualization is disabled if the app includes an app manifest with a requested execution level attribute

## Request execution levels

An app manifest is an XML file that describes and identifies the shared and private side-by-side assemblies that an app should bind to at run time. The app manifest includes entries for UAC app compatibility purposes. Administrative apps that include an entry in the app manifest prompt the user for permission to access the user's access token. Although they lack an entry in the app manifest, most administrative app can run without modification by using app compatibility fixes. App compatibility fixes are database entries that enable applications that aren't UAC-compliant to work properly.

All UAC-compliant apps should have a requested execution level added to the application manifest. If the application requires administrative access to the system, marking the app with a requested execution level of *require administrator* ensures that the system identifies this program as an administrative app, and performs the necessary elevation steps. Requested execution levels specify the privileges required for an app.

## Installer detection technology

Installation programs are apps designed to deploy software. Most installation programs write to system directories and registry keys. These protected system locations are typically writeable only by an administrator in Installer detection technology, which means that standard users don't have sufficient access to install programs. Windows heuristically detects installation programs and requests administrator credentials or approval from the administrator user in order to run with access privileges. Windows also heuristically detects updates and programs that uninstall applications. One of the design goals of UAC is to prevent installations from being run without the user's knowledge and consent because installation programs write to protected areas of the file system and registry.

Installer detection only applies to:

- 32-bit executable files
- Applications without a requested execution level attribute
- Interactive processes running as a standard user with UAC enabled

Before a 32-bit process is created, the following attributes are checked to determine whether it's an installer:

- File name includes keywords such as "install," "setup," or "update."
- Versioning Resource fields contain the following keywords: Vendor, Company Name, Product Name, File Description, Original Filename, Internal Name, and Export Name.
- Keywords in the side-by-side manifest are embedded in the executable file.
- Keywords in specific StringTable entries are linked in the executable file.
- Key attributes in the resource script data are linked in the executable file.
- Executable file contains targeted sequences of bytes.

> [!NOTE]
> The keywords and sequences of bytes were derived from common characteristics observed from various installer technologies.

> [!NOTE]
> The *User Account Control: Detect application installations and prompt for elevation* policy must be enabled for installer detection to detect installation programs. For more information, see [User Account Control settings list](settings-and-configuration.md#user-account-control-settings-list).