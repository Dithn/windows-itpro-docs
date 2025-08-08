---
title: Register devices with Autopatch groups
description: This article details how to register devices in Autopatch.
ms.date: 05/27/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: how-to
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: andredm7
ms.collection:
  - highpri
  - tier1
---

# Register devices with Autopatch groups

> [!IMPORTANT]
> If you're new to Autopatch, it might take up to 48 hours for devices to appear as Registered in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). During this 48 hour period, devices undergo the necessary onboarding processes before appearing as registered

An Autopatch group is a logical container or unit that groups several [Microsoft Entra groups](/entra/fundamentals/groups-view-azure-portal), and software update policies. For more information, see [Windows Autopatch groups](../deploy/windows-autopatch-groups-overview.md).

When you [create an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group) or [edit an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#edit-an-autopatch-group), the device-based Microsoft Entra groups you use are scanned on an ongoing basis to see if new devices need to be added to the Autopatch group.

## Detailed device registration workflow diagram

See the following detailed workflow diagram. The diagram covers the Windows Autopatch device registration process:

:::image type="content" source="../media/windows-autopatch-device-registration-workflow-diagram.png" alt-text="Diagram of the device registration workflow." lightbox="../media/windows-autopatch-device-registration-workflow-diagram.png":::

| Step | Description |
| ----- | ----- |
| **Step 1: Assign Entra Groups** | IT admin identifies the Microsoft Entra group they want to assign when they [create an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group) or [edit an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#edit-an-autopatch-group). |
| **Step 2: Discover devices** | The Windows Autopatch Discover Devices function discovers devices (hourly) that were previously added by the IT admin from Microsoft Entra groups used with Autopatch groups in **step #1**. The Microsoft Entra device ID is used by Windows Autopatch to query device attributes in both Microsoft Intune and Microsoft Entra ID when registering devices into its service.<ol><li>Once devices are discovered from the Microsoft Entra group, the same function gathers additional device attributes and saves it into its memory during the discovery operation. The following device attributes are gathered from Microsoft Entra ID in this step:</li><ol><li>**AzureADDeviceID**</li><li>**OperatingSystem**</li><li>**DisplayName (Device name)**</li><li>**AccountEnabled**</li><li>**RegistrationDateTime**</li><li>**ApproximateLastSignInDateTime**</li></ol><li>In this same step, the Windows Autopatch discover devices function calls another function, the device prerequisite check function. The device prerequisite check function evaluates software-based device-level prerequisites to comply with Windows Autopatch device readiness requirements before registration.</li></ol> |
| **Step 3: Check prerequisites** | The Windows Autopatch prerequisite function makes an Intune Graph API call to sequentially validate device readiness attributes required for the registration process. For detailed information, see the [Detailed prerequisite check workflow diagram](#detailed-prerequisite-check-workflow-diagram) section. The service checks the following device readiness attributes, and/or prerequisites:<ol><li>**If the device is Intune-managed or not.**</li><ol><li>Windows Autopatch looks to see **if the Microsoft Entra device ID has an Intune device ID associated with it**.</li><ol><li>If **yes**, it means this device is enrolled into Intune.</li><li>If **not**, it means the device isn't enrolled into Intune, hence it can't be managed by the Windows Autopatch service.</li></ol><li>**If the device is not managed by Intune**, the Windows Autopatch service can't gather device attributes such as operating system version, Intune enrollment date, device name, and other attributes. When this happens, the Windows Autopatch service uses the Microsoft Entra device attributes gathered and saved to its memory in **step 3a**.</li><ol><li>Once it has the device attributes gathered from Microsoft Entra ID in **step 3a**, the device is flagged with the **Prerequisite failed** status, and the device's Autopatch readiness status appears as **Not registered** in the [**Autopatch groups membership report**](#autopatch-groups-membership-report). The IT admin can review the reasons the device wasn't registered into Windows Autopatch. The IT admin remediates these devices. In this case, the IT admin should check why the device wasn't enrolled into Intune.</li><li>A common reason is when the Microsoft Entra device ID is stale, it doesn't have an Intune device ID associated with it anymore. To remediate, [clean up any stale Microsoft Entra device records from your tenant](windows-autopatch-register-devices.md#clean-up-dual-state-of-hybrid-azure-ad-joined-and-azure-registered-devices-in-your-azure-ad-tenant).</li></ol><li>**If the device is managed by Intune**, the Windows Autopatch prerequisite check function continues to the next prerequisite check, which evaluates whether the device checked into Intune in the last 28 days.</li></ol><li>**If the device is a Windows device or not.**</li><ol><li>Windows Autopatch looks to see if the device is a Windows and corporate-owned device.</li><ol><li>**If yes**, it means this device can be registered with the service because it's a Windows corporate-owned device.</li><li>**If not**, it means the device is a non-Windows device, or it's a Windows device but it's a personal device.</li></ol></ol><li>**Windows Autopatch checks the Windows SKU family**. The SKU must be either:</li><ol><li>**Enterprise**</li><li>**Pro**</li><li>**Pro Workstation**</li><li>**Education**</li><li>**Pro Education**</li></ol><li>**If the device meets the operating system requirements**, Windows Autopatch checks whether the device is either:</li><ol><li>**Only managed by Intune.**</li><ol><li>If the device is only managed by Intune, the device is marked as Passed all prerequisites.</li></ol><li>**Co-managed by both Configuration Manager and Intune.**</li><ol><li>If the device is co-managed by both Configuration Manager and Intune, an additional prerequisite check is evaluated to determine if the device satisfies the co-management-enabled workloads required by Windows Autopatch to manage devices in a co-managed state. The required co-management workloads evaluated in this step are:</li><ol><li>**Windows Updates Policies**</li><li>**Device Configuration**</li><li>**Office Click to Run**</li></ol><li>If Windows Autopatch determines that one of these workloads isn't enabled on the device, the service marks the device as **Prerequisite failed** and the device's Autopatch readiness status appears as **Not registered** in the **Autopatch groups membership report**.</li></ol></ol></ol>|
| **Step 4: Calculate dynamic distribution and assign devices** | Microsoft Entra Groups, which are directly assigned to a deployment ring, adds those devices to the Microsoft Entra Group that Autopatch creates for that deployment ring.<p>If you choose to use dynamic distribution, the Autopatch service distributes the devices you selected. The service takes a percentage of the devices in the dynamic pool and adds them to the relevant Microsoft Entra groups. Devices that are members of Microsoft Entra groups that are directly assigned aren't included in the dynamic pool.</p><p>If you have fewer than 100 devices in an Autopatch group, the distribution might not match your selection.</p>|
| **Step 5: Post-device registration** | If you deployed the [**Windows Autopatch Client Broker**](../deploy/windows-autopatch-post-reg-readiness-checks.md#install-the-windows-autopatch-client-broker), post-device registration actions occur. For more information, see [Post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md#post-device-registration-readiness-checks-workflow). |
| **Step 6: Review device registration status** | IT admins review the device's Autopatch readiness status. Devices are either **Registered** or **Not registered** in the **[**Autopatch groups membership report**](#autopatch-groups-membership-report)**.<ol><li>If the device was **successfully registered**, the device's Autopatch readiness status appears as **Registered** in the **Autopatch groups membership report**.</li><li>If **not**, the device's Autopatch readiness status appears as **Not registered** in the **Autopatch groups membership report**.</li></ol> |
| **Step 7: End of registration workflow** | This is the end of the Windows Autopatch device registration workflow. |

## Detailed prerequisite check workflow diagram

As described in **step #3** in the previous [Detailed device registration workflow diagram](#detailed-device-registration-workflow-diagram), the following diagram is a visual representation of the prerequisite construct for the Windows Autopatch device registration process. The prerequisite checks are sequentially performed.

:::image type="content" source="../media/windows-autopatch-prerequisite-check-workflow-diagram.png" alt-text="Diagram of the prerequisite check workflow." lightbox="../media/windows-autopatch-prerequisite-check-workflow-diagram.png":::

## Autopatch groups membership report

Windows Autopatch has an Autopatch groups membership report provides the following information:

- Autopatch group membership (only if the device is added to an Autopatch group)
- Update status
- Policies that target each device

> [!NOTE]
> You can configure custom roles to access the Autopatch groups membership report, including the various device actions.<p>To **Assign ring** the user requires a minimum of **Windows Autopatch Group/Read permissions**. Use the dropdown menu to select the deployment ring to move devices to, the menu will only display deployment rings in the users' scope. </p><p>To view the device's properties, the minimum permission required is **Manage Devices/Read**.</p><p>Scoped admins can only move devices between deployment rings in the same Autopatch group, with the same scope tags.</p><p>For more information, see [Windows Autopatch role-based access controls](../prepare/windows-autopatch-role-based-access-control.md).</p>

### View the Autopatch groups membership report

**To view the Autopatch groups membership report:**

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** in the left pane.
1. Under **Manage updates**, select **Windows updates**.
1. Select the **Monitor** tab, and then select **Autopatch devices**.

Once a device is added to an Autopatch group, a readiness status is displayed. Each readiness status helps you to determine if there are any actions to take or if the device is ready for the service.

#### Readiness statuses

| Autopatch readiness status in the Autopatch groups membership report | Substatus description |
| --- | --- |
| Registered |<ul><li>**Ready**: Devices successfully passed all prerequisite checks and successfully registered with Windows Autopatch. Additionally, Ready devices successfully passed all [post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md) and don't have any active alerts targeting them.</li><li>**Not ready**: These devices were successfully registered with Windows Autopatch. However, these devices:</li><ul><li>Failed to pass one or more [post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md).</li><li>Aren't ready to have one or more software update workloads managed by the service.</li><li>The device didn't communicate with Microsoft Intune in the last 28 days</li><li>The device has a conflict with policies or with Autopatch group membership</li></ul></ul> |
| Not registered |<ul><li>**Autopatch group conflict**: The device has a conflict with Autopatch group membership</li><li>**Prerequisites failed**: The device failed to pass one or more [post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md).</li><li>**Excluded**: Devices with this status are removed from the Windows Autopatch service only. Microsoft assumes you manage these devices yourself in some capacity.</li></ul> |

### Supported scenarios when nesting other Microsoft Entra groups

Windows Autopatch also supports the following Microsoft Entra nested group scenarios:

Microsoft Entra groups synced up from:

- On-premises Active Directory groups (Windows Server AD)
- [Configuration Manager collections](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_aadcollsync)

## Windows Autopatch on Windows 365 Enterprise Workloads

Windows 365 Enterprise gives IT admins the option to register devices with the Windows Autopatch service as part of the Windows 365 provisioning policy creation. This option provides a seamless experience for admins and users to ensure your Cloud PCs are always up to date. When IT admins decide to manage their Windows 365 Cloud PCs with Windows Autopatch, the Windows 365 provisioning policy creation process calls Windows Autopatch device registration APIs to register devices on behalf of the IT admin.

**To register new Windows 365 Cloud PC devices with Windows Autopatch from the Windows 365 Provisioning Policy:**

1. Go to the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. In the left pane, select **Devices**.
1. Navigate to Provisioning > **Windows 365**.
1. Select Provisioning policies > **Create policy**.
1. Provide a policy name and select **Join Type**. For more information, see [Device join types](/windows-365/enterprise/identity-authentication#device-join-types).
1. Select **Next**.
1. Choose the desired image and select **Next**.
1. Under the **Microsoft managed services** section, ensure **Windows Autopatch** is selected.
1. Assign your policy accordingly and select **Next**.
1. Select **Create**. Now your newly provisioned Windows 365 Enterprise Cloud PCs are automatically enrolled and managed by Windows Autopatch.

For more information, see [Create a Windows 365 Provisioning Policy](/windows-365/enterprise/create-provisioning-policy).

## Windows Autopatch on Azure Virtual Desktop workloads

Windows Autopatch is available for your Azure Virtual Desktop workloads. Enterprise admins can provision their Azure Virtual Desktop workloads to be managed by Windows Autopatch using the existing device registration process.

Windows Autopatch provides the same scope of service with virtual machines as it does with [physical devices](../deploy/windows-autopatch-device-registration-overview.md). However, Windows Autopatch defers any Azure Virtual Desktop specific support to [Azure support](#contact-support-for-autopatch-group-registration-related-incidents), unless otherwise specified.

### Prerequisites

Windows Autopatch for Azure Virtual Desktop follows the same [prerequisites](../prepare/windows-autopatch-prerequisites.md) as Windows Autopatch, and the [Azure Virtual Desktop prerequisites](/azure/virtual-desktop/prerequisites).

The service supports:

- Personal persistent virtual machines

The following Azure Virtual Desktop features aren't supported:

- Multi-session hosts
- Pooled non persistent virtual machines
- Remote app streaming

### Deploy Autopatch on Azure Virtual Desktop

Azure Virtual Desktop workloads can be registered into Windows Autopatch by using the same method as your physical devices.

For ease of deployment, we recommend nesting a dynamic device group in your Autopatch device registration group. The dynamic device group would target the **Name** prefix defined in your session host, but **exclude** any Multi-Session Session Hosts. For example:

| Group name | Dynamic membership name |
| ----- | ----- |
| Windows Autopatch - Host Pool Session Hosts | <ul><li>`(device.displayName -contains "AP")`</li><li>`(device.deviceOSType -ne "Windows 10 Enterprise for Virtual Desktops")`</li></ul> |

<a name='clean-up-dual-state-of-hybrid-azure-ad-joined-and-azure-registered-devices-in-your-azure-ad-tenant'></a>

### Clean up dual state of Microsoft Entra hybrid joined and Azure registered devices in your Microsoft Entra tenant

An [Microsoft Entra dual state](/entra/identity/devices/hybrid-join-plan#handling-devices-with-azure-ad-registered-state) occurs when a device is initially connected to Microsoft Entra ID as an [Microsoft Entra registered](/entra/identity/devices/concept-device-registration) device. However, when you enable Microsoft Entra hybrid join, the same device is connected twice to Microsoft Entra ID but as a [Hybrid Microsoft Entra device](/entra/identity/devices/concept-hybrid-join).

In the dual state, you end up having two Microsoft Entra device records with different join types for the same device. In this case, the Hybrid Microsoft Entra device record takes precedence over the Microsoft Entra registered device record for any type of authentication in Microsoft Entra ID, which makes the Microsoft Entra registered device record stale.

It's recommended to detect and clean up stale devices in Microsoft Entra ID before registering devices with Windows Autopatch, see [How To: Manage stale devices in Microsoft Entra ID](/entra/identity/devices/manage-stale-devices).

> [!WARNING]
> If you don't clean up stale devices in Microsoft Entra ID before registering devices with Windows Autopatch, you might end up seeing devices failing to meet the **Intune or Cloud-Attached (Device must be either Intune-managed or Co-managed)** prerequisite check  in the **Not ready** tab because it expects that these stale Microsoft Entra devices aren't enrolled into the Intune service anymore.

### Contact support for Autopatch group registration-related incidents

Support is available either through Windows 365, or the Windows Autopatch Service Engineering team for device registration-related incidents.

- For Windows 365 support, see [Get support](/mem/get-support).
- For Azure Virtual Desktop support, see [Get support](https://azure.microsoft.com/support/create-ticket/).
- For Windows Autopatch support, see [Submit a support request](../manage/windows-autopatch-support-request.md). You can only submit a support request if you have E3+ or F3 licenses. For more information, see [Features and capabilities](../overview/windows-autopatch-overview.md).

## Device management lifecycle scenarios

There's a few more device management lifecycle scenarios to consider when planning to register devices in an Autopatch group.

### Device refresh

If a device was previously registered into an Autopatch group, but it needs to be reimaged, you must run one of the device provisioning processes available in Microsoft Intune to reimage the device.

The device is rejoined to Microsoft Entra ID (either Hybrid or Microsoft Entra-only). Then, re-enrolled into Intune as well. No further action is required from you or the Windows Autopatch service, because the Microsoft Entra device ID record of that device remains the same.

### Device repair and hardware replacement

If you need to repair a device that was previously registered into the Windows Autopatch service, by replacing the motherboard, nonremovable network interface cards (NIC), or hard drive, you must re-register the device into the Windows Autopatch service, because a new hardware ID is generated when there are major hardware changes, such as:

- SMBIOS UUID (motherboard)
- MAC address (nonremovable NICs)
- OS hard drive's serial, model, manufacturer information

When one of these hardware changes occurs, Microsoft Entra ID creates a new device ID record for that device, even if it's technically the same device.

> [!IMPORTANT]
> If a new Microsoft Entra device ID is generated for a device that was previously registered into the Windows Autopatch service, even if it's technically same device, the new Microsoft Entra device ID must be added either through device direct membership or through nested Microsoft Entra dynamic/assigned group in the Windows Autopatch group experience. This process guarantees that the newly generated Microsoft Entra device ID is registered with Windows Autopatch and that the device continues to have its software updates managed by the service.
