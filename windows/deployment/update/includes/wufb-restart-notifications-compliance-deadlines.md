---
author: mestew
ms.author: mstewart
manager: bpardi
ms.subservice: itpro-updates
ms.service: windows-client
ms.topic: include
ms.date: 03/18/2025
ms.localizationpriority: medium
---
<!--This file is shared by update/wufb-compliancedeadlines.md. It may be added to /update/waas-wufb-csp-mdm.md, /update/waas-wufb-group-policy.md, and /update/waas-restart.md articles later. Headings are driven by article context. Updated with 9091858 -->

These deadline policies also offer an option to opt out of automatic restarts until a deadline is reached by presenting an "engaged restart experience" until the deadline passes. At that point, the device automatically schedules a restart regardless of active hours.

These notifications are what the user sees depending on the settings you choose, and what operating system version their device is running. Generally, the user notifications become more noticeable as the deadline approaches. The experience described is the default and assumes there's ample time for notifications before the [effective deadline](../wufb-compliancedeadlines.md) occurs. The description doesn't account for changes to the **Display options for update notifications** policy ([Update/NoUpdateNotificationsDuringActiveHours](/windows/client-management/mdm/policy-csp-update#noupdatenotificationsduringactivehours)) or other settings that would significantly change the experience.

# [Windows 11, version 23H2 and later](#tab/w11-23h2-notifications)

The following notifications are what the user sees on Windows 11, version 23H2 and later, depending on the settings chosen by the user and the IT administrator:

When **Specify deadlines for automatic updates and restarts** is set:

While restart is pending, before the deadline occurs, users receive a toast notification in the corner of their screen. The notification includes the deadline date, and options to either restart now, pick a time to restart, or restart tonight once active hours ends.

- If the user set [the option](../waas-wufb-csp-mdm.md#user-settings-for-notifications) **Settings** > **Windows Update** > **Advanced options** > **Notify me when a restart is required to finish updating** to **On**, they immediately receive the toast notification when the device enters a restart pending state for updates. Automatic restarts for updates are blocked for 24 hours after the initial notification to give these users time to prepare.
- If the user set **Notify me when a restart is required to finish updating** to **Off** (default), they receive a toast notification that a restart is required 24 hours after the device enters a restart pending state for updates.

   :::image type="content" source="../media/9091858-11-initial-toast.png" alt-text="Screenshot of the initial toast notification displayed in Windows 11 version 23H2, or later, for a user when a restart is needed for an update but isn't past the deadline." lightbox="../media/9091858-initial-toast.png":::

Depending on settings both users and admins configure, toast notification may occur occasionally before the day of the deadline to remind the user of the update. During this time, if they're allowed, automatic restarts might be scheduled after active hours.
- If an automatic restart is scheduled or the user scheduled the restart, and the user is signed in at that time, they receive a notification 15 minutes before the scheduled time.

   :::image type="content" source="../media/9091858-11-pre-deadline-restart-imminent.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now or acknowledge the notification" lightbox="../media/9091858-pre-deadline-restart-imminent.png":::

As the device approaches the deadline time, a notification displays in the middle of the screen that contains the deadline time and options to restart now or acknowledge the notification.

:::image type="content" source="../media/9091858-11-dialog-18-hours.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now or acknowledge the notification." lightbox="../media/9091858-11-dialog-18-hours.png":::

15 minutes before the deadline, a notification displays in the middle of the screen notifying the user that a restart is going to occur. Users can either confirm the restart, reschedule, or choose to restart now.

   :::image type="content" source="../media/9091858-11-pre-deadline-restart-imminent.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now or acknowledge the notification" lightbox="../media/9091858-pre-deadline-restart-imminent.png":::

In cases where a user scheduled restart fails but there's still more time before the deadline is reached, the user receives a notification to either restart now or to reschedule the restart.

:::image type="content" source="../media/9091858-11-scheduled-restart-failed.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user if their scheduled restart fails. The notification contains the options to restart now or to reschedule the restart." lightbox="../media/9091858-11-scheduled-restart-failed.png":::

In cases where the deadline has passed, the user receives a notification that a restart is required. The only options a user can select is to restart now or confirm. The user has 15 minutes to select restart before the device is forced to restart.

:::image type="content" source="../media/9091858-11-fifteen-minutes-restart.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user if their scheduled restart fails and the deadline is passed. The notification contains the options to restart now or to reschedule the restart." lightbox="../media/9091858-11-fifteen-minutes-restart.png":::

In cases where the deadline has passed and the restart failed, the user receives a notification that a restart is required. If the device is plugged in, it will attempt to restart every 5 minutes until the device successfully restarts. The user has 5 minutes to restart before the device is forced to restart.

:::image type="content" source="../media/9091858-11-past-deadline-restart-failed.png" alt-text="Screenshot of the dialog displayed in Windows 11 version 23H2, or later, for a user if their scheduled restart fails and it's past the deadline. The user has 5 minutes to select restart before the device is forced to restart." lightbox="../media/9091858-11-past-deadline-restart-failed.png":::

# [Windows 11, version 22H2 and earlier](#tab/w11-22h2-notifications)

The following notifications are what the user sees on Windows 11, version 22H2 and earlier, depending on the settings chosen by the user and the IT administrator:

When **Specify deadlines for automatic updates and restarts** is set:

For the first few days, the user receives a toast notification in the corner of their screen. The notification includes the deadline date, and options to either restart now, pick a time to restart, or restart tonight once active hours ends.

- If the device is Windows 11, version 22H2 and the user set [the option](../waas-wufb-csp-mdm.md#user-settings-for-notifications) **Settings** > **Windows Update** > **Advanced options** > **Notify me when a restart is required to finish updating** to **On**, they immediately receive the toast notification when the device enters a restart pending state for updates. Automatic restarts for updates are blocked for 24 hours after the initial notification to give these users time to prepare.
- If the device is Windows 11, version 22H2 and the user set **Notify me when a restart is required to finish updating** to **Off** (default), they receive a toast notification that a restart is required 24 hours after the device enters a reboot pending state for updates.

   :::image type="content" source="../media/9091858-11-initial-toast.png" alt-text="Screenshot of the initial toast notification displayed in Windows 11 version 23H2, or later, for a user when a restart is needed for an update but isn't past the deadline." lightbox="../media/9091858-initial-toast.png":::

Depending on settings both users and admins configure, notifications display in the middle of the screen as the deadline gets closer.
- If there's still time for an automatic restart to occur after active hours, the dialog displays an option to let the device restart later along with options to restart now or to pick a time to schedule a restart.

- If there's not time for an automatic restart to occur after active hours, the dialog displays options to pick a time to schedule a restart, restart now, or remind the user later.



During this time before the deadline is reached, if they're allowed, automatic restarts might be scheduled after active hours. If an automatic restart is scheduled or the user scheduled the restart, and the user is signed in at that time, they receive a notification 15 minutes before the scheduled time.

:::image type="content" source="../media/9091858-11-pre-deadline-restart-imminent.png" alt-text="Screenshot of the dialog displayed for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now, schedule a restart, or acknowledge the notification. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-11-pre-deadline-restart-imminent.png":::

The day of the deadline, a notification displays that contains the deadline time and options to restart now or acknowledge the notification.

:::image type="content" source="../media/9091858-11-dialog-18-hours.png" alt-text="Screenshot of the dialog displayed for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now or acknowledge the notification. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-11-dialog-18-hours.png":::

If the restart is still pending once the deadline passes, a notification displays in the middle of the screen notifying the user that a restart is going to occur. Users can either confirm the restart or choose to restart now.

:::image type="content" source="../media/9091858-11-fifteen-minutes-restart.png" alt-text="Screenshot of the dialog displayed for a user 15 minutes before a restart is forced due to a deadline. The notification contains the options to restart now or confirm the notification. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-11-fifteen-minutes-restart.png":::

In cases where a user scheduled restart fails but there's still more time before the deadline is reached, the user receives a notification to either restart now or to reschedule the restart.

:::image type="content" source="../media/9091858-11-scheduled-restart-failed.png" alt-text="Screenshot of the dialog displayed for a user if their scheduled restart fails. The notification contains the options to restart now or to reschedule the restart. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-11-scheduled-restart-failed.png":::

In cases where the deadline has passed and the restart failed, the user receives a notification that a restart is required. The user has 5 minutes to restart before the device is forced to restart.

:::image type="content" source="../media/9091858-11-past-deadline-restart-failed.png" alt-text="Screenshot of the dialog displayed for a user if their scheduled restart fails and it's past the deadline. The user has 5 minutes to select restart before the device is forced to restart." lightbox="../media/9091858-11-past-deadline-restart-failed.png":::

# [Windows 10, version 22H2](#tab/w10-22h2-notifications)

These notifications are what the user sees on Windows 10, depending on the settings chosen by the user and the IT administrator:

When **Specify deadlines for automatic updates and restarts** is set (For Windows 10, version 1709 and later):

 - **While restart is pending, before the deadline occurs:**

   - For the first few days, the user receives a toast notification
     :::image type="content" source="../media/9091858-initial-toast.png" alt-text="Screenshot of the initial Windows 10 toast notification displayed for a user when a restart is needed for an update but the deadline isn't reached yet. This notification is displayed for Windows 11, version 22H2, and earlier devices. " lightbox="../media/9091858-initial-toast.png":::

   - After this period, the user receives this dialog:

        :::image type="content" source="../media/9091858-dialog-18-hours.png" alt-text="Screenshot of the Windows 10 notification displayed for a user when a restart is needed for an update and there's still time for an automatic restart to occur." lightbox="../media/9091858-dialog-18-hours.png":::

   - If the user scheduled a restart, or if an auto restart is scheduled, 15 minutes before the scheduled time the user receives this notification that the restart is about to occur:

     :::image type="content" source="../media/9091858-pre-deadline-restart-imminent.png" alt-text="Screenshot of the Windows 10 dialog displayed for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now, schedule a restart, or acknowledge the notification. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-pre-deadline-restart-imminent.png":::

 - **If the restart is still pending after the deadline passes:**

   - Within 12 hours before the deadline passes, the user receives this notification that the deadline is approaching:

     :::image type="content" source="../media/9091858-initial-deadline-day-dialog.png" alt-text="Screenshot of the Windows 10 dialog displayed for a user when a restart is needed for an update but the deadline isn't reached yet. The notification contains the deadline time and options to restart now or acknowledge the notification. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-initial-deadline-day-dialog.png":::

   - Once the deadline has passed, the user is forced to restart to keep their devices in compliance and receives this notification:

     :::image type="content" source="../media/9091858-scheduled-restart-failed-22h2.png" alt-text="Screenshot of the Windows 10 dialog displayed for a user if their scheduled restart fails. The notification contains the options to restart now or to reschedule the restart. This notification is displayed for Windows 11, version 22H2, and earlier devices." lightbox="../media/9091858-scheduled-restart-failed-22h2.png":::


---
