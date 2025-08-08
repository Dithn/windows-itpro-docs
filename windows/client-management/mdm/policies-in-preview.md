---
title: Configuration service provider preview policies
description: Learn more about configuration service provider (CSP) policies that are available for Windows Insider Preview.
ms.date: 07/22/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

# Configuration service provider policies in preview

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

This article lists the policies that are applicable for Windows Insider Preview builds.

## AboveLock

- [ConfigureAudioOnLockScreen](policy-csp-abovelock.md#configureaudioonlockscreen)

## AppDeviceInventory

- [TurnOffInstallTracing](policy-csp-appdeviceinventory.md#turnoffinstalltracing)
- [TurnOffAPISamping](policy-csp-appdeviceinventory.md#turnoffapisamping)
- [TurnOffApplicationFootprint](policy-csp-appdeviceinventory.md#turnoffapplicationfootprint)
- [TurnOffWin32AppBackup](policy-csp-appdeviceinventory.md#turnoffwin32appbackup)

## ApplicationManagement

- [AllowedNonAdminPackageFamilyNameRules](policy-csp-applicationmanagement.md#allowednonadminpackagefamilynamerules)
- [ConfigureMSIXAuthenticationAuthorizedDomains](policy-csp-applicationmanagement.md#configuremsixauthenticationauthorizeddomains)

## ClientCertificateInstall CSP

- [AttestPrivateKey](clientcertificateinstall-csp.md#userscepuniqueidinstallattestprivatekey)

## CloudDesktop CSP

- [EnablePhysicalDeviceAccessOnCtrlAltDel](clouddesktop-csp.md#userenablephysicaldeviceaccessonctrlaltdel)
- [EnablePhysicalDeviceAccessOnErrorScreens](clouddesktop-csp.md#userenablephysicaldeviceaccessonerrorscreens)
- [EnableBootToCloudSharedPCMode](clouddesktop-csp.md#deviceenableboottocloudsharedpcmode)

## Connectivity

- [DisableCrossDeviceResume](policy-csp-connectivity.md#disablecrossdeviceresume)
- [UseCellularWhenWiFiPoor](policy-csp-connectivity.md#usecellularwhenwifipoor)
- [DisableCellularSettingsPage](policy-csp-connectivity.md#disablecellularsettingspage)
- [DisableCellularOperatorSettingsPage](policy-csp-connectivity.md#disablecellularoperatorsettingspage)

## DeclaredConfiguration CSP

- [Document](declaredconfiguration-csp.md#hostcompletedocumentsdociddocument)
- [Abandoned](declaredconfiguration-csp.md#hostcompletedocumentsdocidpropertiesabandoned)
- [ConflictResolution](declaredconfiguration-csp.md#managementserviceconfigurationconflictresolution)

## DeviceGuard

- [MachineIdentityIsolation](policy-csp-deviceguard.md#machineidentityisolation)

## DevicePreparation CSP

- [PageEnabled](devicepreparation-csp.md#pageenabled)
- [PageStatus](devicepreparation-csp.md#pagestatus)
- [PageErrorPhase](devicepreparation-csp.md#pageerrorphase)
- [PageErrorCode](devicepreparation-csp.md#pageerrorcode)
- [PageErrorDetails](devicepreparation-csp.md#pageerrordetails)
- [PageSettings](devicepreparation-csp.md#pagesettings)
- [ExecutionContext](devicepreparation-csp.md#bootstrapperagentexecutioncontext)
- [Progress](devicepreparation-csp.md#mdmproviderprogress)
- [MdmAgentInstalled](devicepreparation-csp.md#mdmprovidermdmagentinstalled)
- [RebootRequired](devicepreparation-csp.md#mdmproviderrebootrequired)

## Display

- [ConfigureMultipleDisplayMode](policy-csp-display.md#configuremultipledisplaymode)
- [SetClonePreferredResolutionSource](policy-csp-display.md#setclonepreferredresolutionsource)

## DMClient CSP

- [DiscoveryEndpoint](dmclient-csp.md#deviceproviderprovideridlinkedenrollmentdiscoveryendpoint)

## eUICCs CSP

- [MaximumAttempts](euiccs-csp.md#euiccdownloadserversservernamemaximumattempts)
- [ICCID](euiccs-csp.md#euiccdownloadserversservernameiccid)

## FileSystem

- [ClfsAuthenticationChecking](policy-csp-filesystem.md#clfsauthenticationchecking)

## HumanPresence

- [ForceOnlookerDetection](policy-csp-humanpresence.md#forceonlookerdetection)
- [ForceOnlookerDetectionAction](policy-csp-humanpresence.md#forceonlookerdetectionaction)

## InternetExplorer

- [AllowLegacyURLFields](policy-csp-internetexplorer.md#allowlegacyurlfields)

## LanguagePackManagement CSP

- [Providers](language-pack-management-csp.md#installedlanguageslanguage-idproviders)
- [LanguageFeatures](language-pack-management-csp.md#installedlanguageslanguage-idlanguagefeatures)
- [Status](language-pack-management-csp.md#installlanguage-idstatus)
- [ErrorCode](language-pack-management-csp.md#installlanguage-iderrorcode)
- [CopyToDeviceInternationalSettings](language-pack-management-csp.md#installlanguage-idcopytodeviceinternationalsettings)
- [EnableLanguageFeatureInstallations](language-pack-management-csp.md#installlanguage-idenablelanguagefeatureinstallations)
- [StartInstallation](language-pack-management-csp.md#installlanguage-idstartinstallation)
- [SystemPreferredUILanguages](language-pack-management-csp.md#languagesettingssystempreferreduilanguages)

## LocalPoliciesSecurityOptions

- [UserAccountControl_BehaviorOfTheElevationPromptForAdministratorProtection](policy-csp-localpoliciessecurityoptions.md#useraccountcontrol_behavioroftheelevationpromptforadministratorprotection)
- [UserAccountControl_TypeOfAdminApprovalMode](policy-csp-localpoliciessecurityoptions.md#useraccountcontrol_typeofadminapprovalmode)

## MixedReality

- [AutoUnlock](policy-csp-mixedreality.md#autounlock)
- [ConfigureSharedAccount](policy-csp-mixedreality.md#configuresharedaccount)
- [ConfigureDeviceStandbyAction](policy-csp-mixedreality.md#configuredevicestandbyaction)
- [ConfigureDeviceStandbyActionTimeout](policy-csp-mixedreality.md#configuredevicestandbyactiontimeout)

## NewsAndInterests

- [DisableWidgetsOnLockScreen](policy-csp-newsandinterests.md#disablewidgetsonlockscreen)
- [DisableWidgetsBoard](policy-csp-newsandinterests.md#disablewidgetsboard)

## Power

- [EnableEnergySaver](policy-csp-power.md#enableenergysaver)

## Printers

- [ConfigureIppTlsCertificatePolicy](policy-csp-printers.md#configureipptlscertificatepolicy)

## RemoteRemediation CSP

- [EnableCloudRemediation](remoteremediation-csp.md#cloudremediationsettingsenablecloudremediation)
- [EnableAutoRemediation](remoteremediation-csp.md#cloudremediationsettingsautoremediationsettingsenableautoremediation)
- [SetTimeToReboot](remoteremediation-csp.md#cloudremediationsettingsautoremediationsettingssettimetoreboot)
- [SetRetryInterval](remoteremediation-csp.md#cloudremediationsettingsautoremediationsettingssetretryinterval)
- [NetworkSSID](remoteremediation-csp.md#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkssid)
- [NetworkPassword](remoteremediation-csp.md#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpassword)
- [NetworkPasswordEncryptionType](remoteremediation-csp.md#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpasswordencryptiontype)
- [NetworkPasswordEncryptionStore](remoteremediation-csp.md#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpasswordencryptionstore)

## SettingsSync

- [EnableWindowsBackup](policy-csp-settingssync.md#enablewindowsbackup)

## Start

- [AlwaysShowNotificationIcon](policy-csp-start.md#alwaysshownotificationicon)
- [TurnOffAbbreviatedDateTimeFormat](policy-csp-start.md#turnoffabbreviateddatetimeformat)

## TextInput

- [TouchKeyboardControllerModeAvailability](policy-csp-textinput.md#touchkeyboardcontrollermodeavailability)

## Wifi

- [AllowWFAQosManagementMSCS](policy-csp-wifi.md#allowwfaqosmanagementmscs)
- [AllowWFAQosManagementDSCPToUPMapping](policy-csp-wifi.md#allowwfaqosmanagementdscptoupmapping)

## WindowsAI

- [DisableClickToDo](policy-csp-windowsai.md#disableclicktodo)
- [AllowRecallExport](policy-csp-windowsai.md#allowrecallexport)
- [DisableSettingsAgent](policy-csp-windowsai.md#disablesettingsagent)

## WindowsBackupAndRestore CSP

- [EnableWindowsRestore](windowsbackupandrestore-csp.md#enablewindowsrestore)

## WindowsLicensing CSP

- [SubscriptionType](windowslicensing-csp.md#subscriptionssubscriptiontype)
- [SubscriptionStatus](windowslicensing-csp.md#subscriptionssubscriptionstatus)
- [SubscriptionLastError](windowslicensing-csp.md#subscriptionssubscriptionlasterror)
- [SubscriptionLastErrorDescription](windowslicensing-csp.md#subscriptionssubscriptionlasterrordescription)
- [DisableSubscription](windowslicensing-csp.md#subscriptionsdisablesubscription)
- [RemoveSubscription](windowslicensing-csp.md#subscriptionsremovesubscription)

## WirelessNetworkPreference CSP

- [IsEnabled](wirelessnetworkpreference-csp.md#isenabled)
- [PreferCellularOverWiFi](wirelessnetworkpreference-csp.md#prefercellularoverwifi)
- [eSIMprofilesCount](wirelessnetworkpreference-csp.md#statusesimprofilescount)
- [eSIMprofilesMatched](wirelessnetworkpreference-csp.md#statusesimprofilesmatched)
- [eSIMpolicyStatus](wirelessnetworkpreference-csp.md#statusesimpolicystatus)
- [NetworkDiscoveryOption](wirelessnetworkpreference-csp.md#parameterscellularparametersnetworkdiscoveryoption)
- [MaxRescanIntervalInSeconds](wirelessnetworkpreference-csp.md#parameterscellularparametersmaxrescanintervalinseconds)
- [PreferredProfileWakeConnectionTimerInSeconds](wirelessnetworkpreference-csp.md#parameterscellularparameterspreferredprofilewakeconnectiontimerinseconds)
- [ProfileRegistrationTimerInSeconds](wirelessnetworkpreference-csp.md#parameterscellularparametersprofileregistrationtimerinseconds)
- [ScreenOffDurationToTriggerNetworkDiscoveryInMinutes](wirelessnetworkpreference-csp.md#parameterscellularparametersscreenoffdurationtotriggernetworkdiscoveryinminutes)
- [Priority](wirelessnetworkpreference-csp.md#connectionprofilesconnectionprofileidpriority)
- [StayConnected](wirelessnetworkpreference-csp.md#connectionprofilesconnectionprofileidstayconnected)
- [WirelessType](wirelessnetworkpreference-csp.md#connectionprofilesconnectionprofileidwirelesstype)
- [PLMNID](wirelessnetworkpreference-csp.md#connectionprofilesconnectionprofileidcellularplmnid)

## Related articles

[Policy configuration service provider](policy-configuration-service-provider.md)
