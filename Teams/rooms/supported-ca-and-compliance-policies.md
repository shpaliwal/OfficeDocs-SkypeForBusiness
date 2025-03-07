---
title: "Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms"
ms.author: czawideh
author: cazawideh
ms.reviewer: kspiess
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
description: Learn about supported and recommended Conditional Access and Intune device compliance policies for Microsoft Teams Rooms.
---

# Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms

This article provides supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms. For best practices and example policies, see [Conditional Access and Intune compliance best practices for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md).

> [!NOTE]
> Teams Rooms must already be deployed on the devices you want to assign
Conditional Access policies to. If you haven’t deployed Teams Rooms yet,
see [Deploy Microsoft Teams Rooms with Office 365](with-office-365.md)
and [Deploy Microsoft Teams Rooms on Android](../devices/collab-bar-deploy.md)
for more information.

## Supported Conditional Access policies  

The following list includes the supported Conditional Access policies for Teams Rooms on Windows and on Android:

| Assignment | Windows | Android |
|------------|---------|---------|
| User or workload identities |Supported | Supported |
|Cloud apps or actions | Supported <br><br> Teams Rooms needs to access the following three Cloud apps when in Teams only mode: Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft Teams | Supported <br><br> Teams Rooms needs to access the following three Cloud apps when in Teams only mode: Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft Teams |
|**Conditions**| --- | --- |
| User risk | Supported | Supported |
| Sign-in risk | Supported | Supported |
| Device platforms | Supported | Supported |
| Locations | Supported | Supported |
|Client apps |Not supported| Not supported |
|Filter for devices | Supported | Supported |
|**Grant**| --- | --- |
| Block access | Supported | Supported |
| Grant access | Supported | Supported | 
| Require multi-factor authentication | Not supported | Not supported |
| Require device to be marked as compliant | Supported | Supported |
|Require Hybrid Azure AD joined device | Not supported | Not supported |
|Require approved client app | Not supported | Not supported |
| Require app protection policy | Not supported |Not supported |
| Require password change | Not supported | Not supported |

> [!NOTE]
> Skype for Business Online is retired and not supported. Skype for
Business Online cloud app is not supported for device compliance based
Conditional Access policies.

> [!NOTE]
> Microsoft Teams Rooms on Windows must meet the following
requirements to support device compliance grant controls:
>
> - Microsoft Teams Rooms application 4.8.19.0 or above
> - Windows 10 version 20H2 and above (10.0.19042)

## Supported device compliance policies 

Microsoft Teams Rooms on Windows and Teams Rooms on Android support
different device compliance policies.

#### [Teams Rooms on Windows](#tab/mtr-w)

Below is a table of device compliance settings and recommendations for
their use with Teams Rooms.  

|Policy | Availability | Notes|
|---------|-------------|-------|
| [**Device health**](/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-health) | -- | -- |
|Require BitLocker| Supported | Only use if you have first enabled BitLocker on Teams Rooms. |
|Require Secure Boot to be enabled on the device |Supported |Secure Boot is  a requirement for Teams Rooms. |
|Require code integrity |Supported  | Code integrity is already a requirement for Teams Rooms. |
| [**Device Properties**](/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-properties) | -- | -- |
|Operating System Version (minimum, maximum) |Not supported | Teams Rooms automatically updates to newer versions of Windows and setting values here could prevent successful sign in after an OS update.|
|OS version for mobile devices (minimum, maximum) | Not supported. | N/A |
| Valid operating system builds | Not supported | N/A |
| [**Configuration Manager Compliance**](/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-properties) | -- | -- |
| Require device compliance from Configuration Manager | Supported |  N/A |
| [**System security**](/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22system-security) | -- | -- |
| All password policies | Not supported | Password policies can prevent the local Skype account from automatically signing in. |
| Require encryption of data storage on device. | Supported  | Only use if you have first enabled encryption of data storage on Teams Rooms. |
| Firewall | Supported | Firewall is already a requirement for Teams Rooms |
| Trusted Platform Module (TPM) | Supported | Trusted Platform Module (TPM) is already a requirement for Teams Rooms. |
| Antivirus | Supported | Antivirus (Windows Defender) is already a requirement for Teams Rooms. |
| Antispyware | Supported | Antispyware (Windows Defender) is already a requirement for Teams Rooms. |
| Microsoft Defender Antimalware | Supported | Microsoft Defender Antimalware is already a requirement for Teams Rooms. |
| Microsoft Defender Antimalware minimum version | Not supported. | Teams Rooms automatically updates this component so there’s no need to set compliance policies.|
| Microsoft Defender Antimalware security intelligence
up-to-date | Supported | Validate that Microsoft Defender Antimalware is already a requirement for Teams Rooms. |
| Real-time protection | Supported | Real-time protections are already a requirement for Teams Rooms. |
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22microsoft-defender-for-endpointws) | -- | -- |
| Require the device to be at or under the machine risk score. | Supported |  N/A |

#### [Teams Rooms on Android](#tab/mtr-a)

Below is a table of device compliance settings and recommendations for
their use with Teams Rooms.  

| Policy | Availability | Notes |
|---------|-------------|-------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint) | -- | -- |
| Require the device to be at or under the machine risk score | Not supported |  N/A |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android%22%20/l%20%22device-health) | -- | -- |
| Device managed with device administrator | Not supported. | Teams Android devices are managed with device
administrator. |
| Rooted devices | Supported |  N/A |
| Require the device to be at or under the device threat level | Not supported |  N/A |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health) | -- | -- |
| Google Play Services is configured | Not supported | Google play isn't installed on Teams Android devices. |
| Up-to-date security provider | Not supported | Google play isn't installed on Teams Android devices. |
| Threat scan on apps | Not supported | Google play isn't installed on Teams Android devices. |
| SafetyNet device attestation | Not supported | Google play isn't installed on Teams Android devices.|
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties) | -- | -- |
| Operating System Version (minimum, maximum) | Supported |  N/A |
[**System security**](/mem/intune/protect/compliance-policy-create-android#system-security) | -- | -- |
| Require encryption of data storage on device. |Supported |  N/A |
[**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security) | -- | -- |
| Block apps from unknown sources | Not supported | Only Teams admins install apps or OEM tools |
| Company Portal app runtime integrity | Supported |  N/A|
| Restricted apps | Not supported |  N/A |
| Block USB debugging on device | Supported |  N/A|
[**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices) | -- | -- |
|Maximum minutes of inactivity before password are required | Not supported |  N/A |
| Require a password to unlock mobile devices | Not supported | N/A |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later) | -- | -- |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | -- | -- |
|Required password type |Not supported | N/A|

---
