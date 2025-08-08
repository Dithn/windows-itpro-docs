---
title: Predefined key combinations
description: Predefined key combinations
ms.date: 03/20/2025
ms.topic: reference
---

# Predefined key combinations

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

This topic lists a set of key combinations that are predefined by a keyboard filter.  You can list the value of the WEKF_PredefinedKey.Id to get a complete list of key combinations defined by a keyboard filter.

You can use the values in the WEKF_PredefinedKey.Id column to configure the Windows Management Instrumentation (WMI) class [WEKF_PredefinedKey](wekf-predefinedkey.md).

## Accessibility keys

The following table contains predefined key combinations for accessibility:

| Key combination                      | WEKF_PredefinedKey.Id     | Blocked behavior            |
|:-------------------------------------|:--------------------------|:----------------------------|
| Left Alt + Left Shift + Print Screen | **LShift+LAlt+PrintScrn** | Open High Contrast.         |
| Left Alt + Left Shift + Num Lock     | **LShift+LAlt+NumLock**   | Open Mouse Keys.            |
| Windows key + U                 | **Win+U**                 | Open Ease of Access Center. |

## Application keys

The following table contains predefined key combinations for controlling application state:

| Key combination       | WEKF_PredefinedKey.Id | Blocked behavior   |
|:----------------------|:----------------------|:-------------------|
| Alt + F4              | **Alt+F4**            | Close application. |
| Ctrl + F4             | **Ctrl+F4**           | Close window.      |
| Windows key + F1 | **Win+F1**            | Open Windows Help. |

## Shell keys

The following table contains predefined key combinations for general UI control:

| Key combination                        | WEKF_PredefinedKey.Id | Blocked behavior                                                                                                                     |
|:---------------------------------------|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| Alt + Spacebar                         | **Alt+Space**         | Open shortcut menu for the active window.                                                                                            |
| Ctrl + Esc                             | **Ctrl+Esc**          | Open the Start screen.                                                                                                               |
| Ctrl + Windows key + F            | **Ctrl+Win+F**        | Open Find Computers.                                                                                                                 |
| Windows key + Break               | **Win+Break**         | Open System dialog box.                                                                                                              |
| Windows key + E                   | **Win+E**             | Open Windows Explorer.                                                                                                               |
| Windows + F                            | **Win+F**             | Open Search.                                                                                                                         |
| Windows key + P                   | **Win+P**             | Cycle through Presentation Mode. Also blocks the Windows key + Shift + P and the Windows key + Ctrl + P key combinations.  |
| Windows key + R                   | **Win+R**             | Open Run dialog box.                                                                                                                 |
| Alt + Tab                              | **Alt+Tab**           | Switch task. Also blocks the Alt + Shift + Tab key combination.                                                                      |
| Ctrl + Tab                             | **Ctrl+Tab**          | Switch window.                                                                                                                       |
| Windows key + Tab                 | **Win+Tab**           | Cycle through Microsoft Store apps. Also blocks the Windows key + Ctrl + Tab and Windows key + Shift + Tab key combinations. |
| Windows key + D                   | **Win+D**             | Show desktop.                                                                                                                        |
| Windows key + M                   | **Win+M**             | Minimize all windows.                                                                                                                |
| Windows key + Home                | **Win+Home**          | Minimize or restore all inactive windows.                                                                                            |
| Windows key + T                   | **Win+T**             | Set focus on taskbar and cycle through programs.                                                                                     |
| Windows key + B                   | **Win+B**             | Set focus in the notification area.                                                                                                  |
| Windows key + Minus Sign          | **Win+-**             | Zoom out.                                                                                                                            |
| Windows key + Plus Sign           | **Win++**             | Zoom in.                                                                                                                             |
| Windows key + Esc                 | **Win+Esc**           | Close Magnifier application.                                                                                                         |
| Windows key + Up Arrow            | **Win+Up**            | Maximize the active window.                                                                                                          |
| Windows key + Down Arrow          | **Win+Down**          | Minimize the active window.                                                                                                          |
| Windows key + Left Arrow          | **Win+Left**          | Snap the active window to the left half of screen.                                                                                   |
| Windows key + Right Arrow         | **Win+Right**         | Snap the active window to the right half of screen.                                                                                  |
| Windows key + Shift + Up Arrow    | **Win+Shift+Up**      | Maximize the active window vertically.                                                                                               |
| Windows key + Shift + Down Arrow  | **Win+Shift+Down**    | Minimize the active window.                                                                                                          |
| Windows key + Shift + Left Arrow  | **Win+Shift+Left**    | Move the active window to left monitor.                                                                                              |
| Windows key + Shift + Right Arrow | **Win+Shift+Right**   | Move the active window to right monitor.                                                                                             |
| Windows key + Spacebar            | **Win+Space**         | Switch layout.                                                                                                                       |
| Windows key + O                   | **Win+O**             | Lock device orientation.                                                                                                             |
| Windows key + Page Up             | **Win+PageUp**        | Move a Microsoft Store app to the left monitor.                                                                                        |
| Windows key + Page Down           | **Win+PageDown**      | Move a Microsoft Store app to right monitor.                                                                                           |
| Windows key + Period              | **Win+.**             | Snap the current screen to the left or right gutter. Also blocks the Windows key + Shift + Period key combination.              |
| Windows key + C                   | **Win+C**             | Activate Cortana in listening mode (after user has enabled the shortcut through the UI).                                                                                                                         |
| Windows key + I                   | **Win+I**             | Open Settings charm.                                                                                                                 |
| Windows key + K                   | **Win+K**             | Open Connect charm.                                                                                                                  |
| Windows key + H                   | **Win+H**             | Start dictation.                                                                                                                  |
| Windows key + Q                   | **Win+Q**             | Open Search charm.                                                                                                                   |
| Windows key + W                   | **Win+W**             | Open Windows Ink workspace.                                                                                                         |
| Windows key + Z                   | **Win+Z**             | Open app bar.                                                                                                                        |
| Windows key + /                   | **Win+/**             | Open input method editor (IME).                                                                                                      |
| Windows key + J                   | **Win+J**             | Swap between snapped and filled applications.                                                                                        |
| Windows key + Comma               | **Win+,**             | Peek at the desktop.                                                                                                                 |
| Windows key + V                   | **Win+V**             | Cycle through toasts in reverse order.                                                                                               |

## Modifier keys

The following table contains predefined key combinations for modifier keys (such as Shift and Ctrl):

| Key combination  | WEKF_PredefinedKey.Id | Blocked key            |
|:-----------------|:----------------------|:-----------------------|
| Alt              | **Alt**               | Both Alt keys          |
| Application      | **Application**       | Application key        |
| Ctrl             | **Ctrl**              | Both Ctrl keys         |
| Shift            | **Shift**             | Both Shift keys        |
| Windows key | **Windows**           | Both Windows keys |

## Security keys

The following table contains predefined key combinations for OS security:

| Key combination        | WEKF_PredefinedKey.Id | Blocked behavior                  |
|:-----------------------|:----------------------|:----------------------------------|
| Ctrl + Alt + Delete    | **Ctrl+Alt+Del**      | Open the Windows Security screen. |
| Ctrl + Shift + Esc     | **Shift+Ctrl+Esc**    | Open Task Manager.                |
| Windows key + L   | **Win+L**             | Lock the device.                  |

## Extended shell keys

The following table contains predefined key combinations for extended shell functions (such as automatically opening certain apps):

| Key combination     | WEKF_PredefinedKey.Id | Blocked key             |
|:--------------------|:----------------------|:------------------------|
| LaunchMail          | **LaunchMail**        | Start Mail key          |
| LaunchMediaSelect   | **LaunchMediaSelect** | Select Media key        |
| LaunchApp1          | **LaunchApp1**        | Start Application 1 key |
| LaunchApp2          | **LaunchApp2**        | Start Application 2 key |

## Browser keys

The following table contains predefined key combinations for controlling the browser:

| Key combination  | WEKF_PredefinedKey.Id | Blocked key                |
|:-----------------|:----------------------|:---------------------------|
| BrowserBack      | **BrowserBack**       | Browser Back key           |
| BrowserForward   | **BrowserForward**    | Browser Forward key        |
| BrowserRefresh   | **BrowserRefresh**    | Browser Refresh key        |
| BrowserStop      | **BrowserStop**       | Browser Stop key           |
| BrowserSearch    | **BrowserSearch**     | Browser Search key         |
| BrowserFavorites | **BrowserFavorites**  | Browser Favorites key      |
| BrowserHome      | **BrowserHome**       | Browser Start and Home key |

## Media keys

The following table contains predefined key combinations for controlling media playback:

| Key combination | WEKF_PredefinedKey.Id | Blocked key          |
|:----------------|:----------------------|:---------------------|
| VolumeMute      | **VolumeMute**        | Volume Mute key      |
| VolumeDown      | **VolumeDown**        | Volume Down key      |
| VolumeUp        | **VolumeUp**          | Volume Up key        |
| MediaNext       | **MediaNext**         | Next Track key       |
| MediaPrev       | **MediaPrev**         | Previous Track key   |
| MediaStop       | **MediaStop**         | Stop Media key       |
| MediaPlayPause  | **MediaPlayPause**    | Play/Pause Media key |

## Microsoft Surface keyboard keys

The following table contains predefined key combinations for Microsoft Surface devices:

| Key combination               | WEKF_PredefinedKey.Id | Blocked key  |
|:------------------------------|:----------------------|:-------------|
| Left Alt + Windows key   | **AltWin**            | Share key    |
| Left Ctrl + Windows key  | **CtrlWin**           | Devices key  |
| Left Shift + Windows key | **ShiftWin**          | Search key   |
| F21                           | **F21**               | Settings key |

## Related topics

[Keyboard filter](index.md)
