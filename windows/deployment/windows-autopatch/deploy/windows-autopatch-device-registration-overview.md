---
title: Autopatch group registration overview
description: This article provides an overview on how to register devices in Autopatch.
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: concept-article
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: andredm7
ms.collection:
  - highpri
  - tier1
---

# Autopatch group registration overview

> [!IMPORTANT]
> If you're new to Autopatch, it might take up to 48 hours for devices to appear as Registered in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). During this 48 hour period, devices undergo the necessary onboarding processes before appearing as registered.

When you assign a Microsoft Entra Group to an Autopatch policy or [create an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), the device is registered with the Autopatch Service.

## Prerequisites for device registration

### Built-in roles required for device registration

A role defines the set of permissions granted to users assigned to that role. You can use the Intune Service Administrator role to register devices. For more information, see [Required Intune permissions](../prepare/windows-autopatch-prerequisites.md#required-intune-permissions).

### Software prerequisites

To be eligible for Windows Autopatch management, devices must meet a minimum set of required software-based prerequisites. For more information, see [Windows Autopatch prerequisites](../prepare/windows-autopatch-prerequisites.md).

The Windows Autopatch device registration process is transparent for end-users because it doesn't require devices to be reset.

The overall Autopatch group registration process is as follows:

:::image type="content" source="../media/windows-autopatch-device-registration-overview.png" alt-text="Screenshot showing an overview of the device registration process." lightbox="../media/windows-autopatch-device-registration-overview.png":::

1. IT admin identifies and adds devices, or nests other Microsoft Entra device groups when you [create an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), or [edit an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#edit-an-autopatch-group).

2. Windows Autopatch then:
    1. Performs device readiness prior registration (prerequisite checks).
    2. Calculates the deployment ring distribution.
    3. Assigns devices to one of the deployment rings based on the previous calculation.
    4. Assigns devices to other Microsoft Entra groups required for management.

For more information about the device registration workflow, see the [Detailed device registration workflow diagram](../deploy/windows-autopatch-register-devices.md#detailed-device-registration-workflow-diagram) section for more technical details behind the Windows Autopatch device registration process.
