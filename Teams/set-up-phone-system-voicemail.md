---
title: "Set up Cloud Voicemail"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jenstr
ms.topic: article
ms.assetid: 9c590873-b014-4df3-9e27-1bb97322a79d
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto:
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Phone System
description: "Learn how to set up Cloud Voicemail for your users."
---

# Set up Cloud Voicemail

This article is for Microsoft 365 administrators who want to set up Cloud Voicemail for their users.

Cloud Voicemail deposits voicemail messages in a user's Exchange mailbox. Cloud Voicemail doesn't support third-party email systems. For Exchange Online licensing requirements, see [Exchange Online service description](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description#features-available-to-all-plans). For more information about administrator roles, see [About admin roles](/microsoft-365/admin/add-users/about-admin-roles).

## Cloud Voicemail provisioning

For Teams users, Cloud Voicemail is automatically set up and provisioned. *A Microsoft Teams Phone license is not required for Cloud Voicemail.*

Provisioning for Teams users isn't the same as it was for Skype for Business Online users. For Skype for Business Online users, Cloud Voicemail was automatically set up and provisioned when the users were assigned a Phone System license and were Enterprise Voice enabled by the provisioning system.

For Skype for Business Server on-premises users, Cloud Voicemail is automatically set up and provisioned. However, you must configure the Skype for Business Server environment to route calls to Cloud Voicemail. For more information, see [Plan Cloud Voicemail service for on-premises users](/skypeforbusiness/hybrid/plan-cloud-voicemail.md).

## Cloud Voicemail storage

Voicemail messages generated by Cloud Voicemail are delivered to and stored in the user's Exchange mailbox, either in Exchange Online or in Exchange Server. There's no specific or additional storage for voicemail. The clients that access voicemail (for example, Microsoft Outlook, Microsoft Teams, or Skype for Business) do so through the Exchange mailbox and the APIs provided.

A voicemail message contains an attached audio file with the voice messages and the voicemail transcription (if enabled).

The Exchange mailbox of a user stores any custom recorded greetings. These greetings are retrieved by Cloud Voicemail as needed during an incoming call.

## Cloud Voicemail processing

The recording and transcription of Cloud Voicemail starts in Microsoft 365 at the origin of the call being routed to Cloud Voicemail. The message is then delivered to the user’s Exchange mailbox.

For example, if a call comes in to an unavailable Direct Routing user through a Session Border Controller (SBC) in Europe, the voicemail recording and transcription are done in Europe. The message is then delivered to the user’s Exchange mailbox. For another example, assume a Teams user in North America calls an unavailable Teams user in Europe. In this case, the call starts in North America, the processing occurs in North America, and then the voicemail is delivered to the user’s Exchange mailbox in Europe.

The delivery of a voicemail to an Exchange mailbox is done using Simple Mail Transport Protocol (SMTP) like any other e-mail.

## Manage Cloud Voicemail for users

To manage Cloud Voicemail features for your users, use the Teams PowerShell module as follows.

To manage Cloud Voicemail features for groups of users, use the [New-CsOnlineVoicemailPolicy](/powershell/module/skype/new-csonlinevoicemailpolicy) cmdlet.
You can configure and assign existing or new voicemail policies for features such as call answering rules, voicemail transcription, transcription profanity masking, transcription translation, and system prompt language. For more information, see [New-CsOnlineVoicemailPolicy](/powershell/module/skype/new-csonlinevoicemailpolicy).

To manage Cloud Voicemail settings for individual users, use the  [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings) cmdlet. Cloud Voicemail settings that you can apply to individual users include call answering rules, prompt language, text to speech default, and vacation greetings. For more information, see [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings).
(Note that your end users can also configure these settings in the Teams client by going to **Settings** -> **Calls** -> **Configure Voicemail**.)

You can also disable Cloud Voicemail for a user by using the [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings) cmdlet and setting the VoicemailEnabled parameter to $false. This setting will ensure that Cloud Voicemail can no longer record a voicemail for the user.

## Control routing of calls to Cloud Voicemail

The default setting for all users provisioned for Cloud Voicemail is to allow routing of calls to Cloud Voicemail, and to allow users to forward calls to Cloud Voicemail.

You can control whether routing of calls to Cloud Voicemail is allowed for Teams users by using the Set-CsTeamsCallingPolicy cmdlet with the AllowVoicemail parameter. For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy.md).

- If you set AllowVoicemail to AlwaysDisabled, calls are never routed to voicemail--regardless of the call forward or unanswered settings for a user. Voicemail isn't available as a call forwarding or unanswered setting in Teams.

- If you set AllowVoicemail to AlwaysEnabled, calls are always forwarded to voicemail on unanswered after ringing for thirty seconds--regardless of the unanswered call forward setting for a user.

- If you set AllowVoicemail to UserOverride, calls are forwarded to voicemail based on the call forwarding and/or unanswered settings for a user.

## Set up Cloud Voicemail to work with on-premises users

You can use Cloud Voicemail to provide voice mail functionality for users who have mailboxes on your Exchange Servers, or for users who are using Skype for Business Server.

This section describes how to set up Cloud Voicemail for Exchange Server mailbox users. For information about how to configure Cloud Voicemail for Skype for Business Server users, see [Plan Cloud Voicemail service for on-premises users](/skypeforbusiness/hybrid/plan-cloud-voicemail).

### Set up Cloud Voicemail for Exchange Server mailbox users

The following information is about configuring Cloud Voicemail to work with Teams  users who have their mailbox on Exchange Server.

1. Voicemail messages are delivered to a user's Exchange mailbox through SMTP routed through Exchange Online Protection. To enable successful delivery of these messages, be sure that Exchange Connectors are configured correctly between your Exchange servers and Exchange Online Protection. For more information, see [Use Connectors to Configure Mail Flow](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

2. To enable Voicemail features such as customizing greetings and visual voicemail in Teams clients, you must set up connectivity between Microsoft 365 and the Exchange Server mailbox. To enable this connectivity, you must configure the new Exchange Oauth authentication protocol described in [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help), or run the Exchange Hybrid Wizard from Exchange 2013 CU5 or greater. You must also configure integration and Oauth between Teams and Exchange Server described in [Configure Integration and OAuth between Teams and Exchange Server](/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises).

## Enable protected voicemail in your organization

When someone leaves a voicemail message for a user in your organization, the voicemail is delivered to the user's mailbox as an email message attachment. 

Using Microsoft Information Protection, you can encrypt the voicemail messages left by both internal and external callers. You can also prevent the user from  forwarding these messages. This feature is supported for users with Exchange Online mailboxes.

To encrypt the voicemail message, you can create a sensitivity label. With the auto-labeling feature, you can ensure that the label will be applied automatically to incoming voicemail messages. 

When you enable protected voicemail, users can listen to protected voicemail messages by calling into their voicemail mailbox or by opening the message in Outlook, Outlook on the web, or Outlook for Android or iOS. Protected voicemail messages can't be opened in Microsoft Teams or Skype for Busimess.

To create a sensitivity label for voicemail, see [Use sensitivity labels](/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions). Select **In Outlook, enforce one of the following restrictions**, and then select the **Do Not Forward** option.

To create the auto-labelling policy to apply a sensitivity label to voicemail, see [How to configure auto-labeling policies](/microsoft-365/compliance/apply-sensitivity-label-automatically?view=o365-worldwide#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange), and specify the following specific settings:

-	For **Choose info you want this label applied to**, select **Custom policy**.

-	For **Choose locations where you want to apply the label**, select **Locations: Exchange for all users**.

-	For  **Set up common or advanced rules**,  select **Advanced rules**.

- Exchange rules:
    - Conditions:<br>
        - **Header matches pattern:**<br>
              Content-Class = Voice-CA
       -  **Sender IP address is:**<br>
               13.107.64.0/18, 52.112.0.0/14, 52.120.0.0/14, 52.238.119.141/32, 52.244.160.207/32

- For **Choose a label to auto-apply**, select the sensitivity label you created for voicemail in the step above.

- For **additional settings for email**, select **Apply encryption to email received from outside your organization**, and specify the Rights Management owner.

The IP V4 ranges specified in Sender IP address is based on the list in ID 12 in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#skype-for-business-online-and-microsoft-teams).

For more information about message encryption, see [Define mail flow rules to encrypt email messages](/microsoft-365/compliance/define-mail-flow-rules-to-encrypt-email).

## Help your users learn about Cloud Voicemail features

To help your users learn about how to use and manage Cloud Voicemail features, you can recommend the following articles:

- [Check your voicemail in Teams](https://support.microsoft.com/office/check-your-voicemail-in-teams-f8d568ce-7329-4fe2-a6a2-325ec2e2b419)
- [Manage your call settings in Teams](https://support.microsoft.com/office/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f)
