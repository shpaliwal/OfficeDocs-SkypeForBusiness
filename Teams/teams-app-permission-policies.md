---
title: Manage app permission policies in Microsoft Teams
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.reviewer: rarang
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about app permission policies in Microsoft Teams and how to use them to control what apps are available for users in your organization.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.apppermspolicies.overview
  - ms.teamsadmincenter.appsetuppolicies.addpinnedapp.permissions
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - ms.teamsadmincenter.appsetuppolicies.overview
---

# Manage app permission policies in Microsoft Teams

As an admin, you can use app permission policies to control what apps are available to Microsoft Teams users in your organization. You can allow or block all apps or specific apps published by Microsoft, third-parties, and your organization. When you block an app, users who have the policy are unable to install it from the Teams app store. You must be a global admin or Teams service admin to manage these policies.

You manage app permission policies in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy. After you edit or assign a policy, it can take a few hours for changes to take effect.

![Screenshot of app permission policy.](media/app-permission-policies.png)

> [!NOTE]
> Org-wide app settings override the global policy and any custom policies that you create and assign to users.

If your organization is already on Teams, the app settings you configured in **Tenant-wide settings** in the Microsoft 365 admin center are reflected in org-wide app settings on the [Manage apps](manage-apps.md) page. If you're new to Teams and just getting started, by default, all apps are allowed in the global policy. This includes apps published by Microsoft, third-parties, and your organization.

Say, for example, you want to block all third-party apps and allow specific apps from Microsoft for the HR team in your organization. First, you would go to the [Manage apps](manage-apps.md) page and make sure that the apps that you want to allow for the HR team are allowed at the org level. Then, create a custom policy named HR App Permission Policy, set it to block and allow the apps that you want, and assign it to users on the HR team.

> [!NOTE]
> If you deployed Teams in a Microsoft 365 Government Community Cloud High (GCCH) and Department of Defense (DoD) environment, see [Manage org-wide app settings for Microsoft 365 Government](#manage-org-wide-app-settings-for-microsoft-365-government) to learn more about third-party app settings that are unique to GCCH and DoD.

## Create a custom app permission policy

If you want to control the apps that are available for different groups of users in your organization, create and assign one or more custom app permission policies. You can create and assign separate custom policies based on whether apps are published by Microsoft, third-parties, or your organization. It's important to know that after you create a custom policy, you can't change it if third-party apps are disabled in org-wide app settings.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Permission policies**.
2. Click **Add**. <br>
    ![Screenshot of new app permission policy.](media/app-permission-policies-new-policy.png)
3. Enter a name and description for the policy.
4. Under **Microsoft apps**, **Third-party apps**, and **Custom apps**, select one of the following:

    - **Allow all apps**
    - **Allow specific apps and block all others**
    - **Block specific apps and allow all others**
    - **Block all apps**

5. If you selected **Allow specific apps and block others**, add the apps that you want to allow:

    1. Select **Allow apps**.
    1. Search for the apps that you want to allow, and then click **Add**. The search results are filtered to the app publisher (**Microsoft apps**, **Third-party apps**, or **Custom apps**).
    1. When you've chosen the list of apps, click **Allow**. 

6. Similarly, if you selected **Block specific apps and allow all others**, search for and add the apps that you want to block, and then click **Block**.
7. Click **Save**.

## Edit an app permission policy

You can use the Microsoft Teams admin center to edit a policy, including the global policy and custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Permission policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. From here, make the changes that you want. You can manage settings based on the app publisher and add and remove apps based on the allow/block setting.
4. Click **Save**.

## Assign a custom app permission policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Manage org-wide app settings for Microsoft 365 Government  

In a Microsoft 365 Government - GCCH and DoD deployment of Teams, it's important to know the following about third-party app settings, which are unique to GCCH and DoD.

In GCCH and DoD, all third-party apps are blocked by default. Additionally, you'll see the following note about managing third-party apps on the app permission policies page in the Microsoft Teams admin center.

![Screenshot of app permission policy in GCCH and DoD.](media/app-permission-policies-gcc.png)

Use org-wide app settings to control whether users can install third-party apps. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

1. On the **Permission policies** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.

    ![Screenshot of org-wide app settings.](media/app-permission-policies-gcc-org-wide.png)
    
2. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    - **Allow third-party apps**: This controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, this setting is off by default.
    - **Allow any new third-party apps published to the store by default**: This controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

3. Under **Blocked apps**, add the apps you want to block across your organization. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, all third-party apps are added to this list by default. For any third-party app you want to allow in your organization, remove the app from this blocked apps list. When you block an app org-wide, the app is automatically blocked for all your users, regardless of whether it's allowed in any app permission policies
4. Click **Save** for org-wide app settings to take effect.

As mentioned earlier, to allow third-party apps, you can either edit and use the global (Org-wide default) policy or create and assign custom policies.

## FAQ

### Working with app permission policies

#### What app interactions do permission policies affect?
Permission policies govern app usage by controlling installation, discovery, and interaction for end users. Admins can still manage apps in the Microsoft Teams admin center regardless of the permission policies assigned to them.

#### Can I control line of business (LOB) apps?
Yes, you can use app permission policies to control the rollout and distribution of custom (LOB) apps. You can create a custom policy or edit the global policy to allow or block custom apps based on the needs of your organization.

#### How do app permission policies relate to pinned apps and app setup policies?

You can use app setup policies together with app permission policies. Pre-pinned apps are selected from the set of enabled apps for a user. Additionally, if a user has an app permission policy that blocks an app in their app setup policy, that app won't appear in Teams.

#### Can I use app permission policies to restrict uploading custom apps?

You can use org-wide settings on the **Manage apps** page, or app setup policies to restrict uploading custom apps for your organization.  

To restrict specific users from uploading custom apps, use custom app policies. To learn more, see [Manage custom app policies and settings in Teams](teams-custom-app-policies-and-settings.md).

#### Does blocking an app apply to Teams mobile clients?

Yes, when you block an app, that app is blocked across all Teams clients.  

### User experience

#### What does a user experience when an app is blocked?

Users can't interact with a blocked app or its capabilities, such bots, tabs, and messaging extensions. In a shared context, such as a team or group chat, bots can still send messages to all participants of that context. Teams indicates to the user when an app is blocked.

For example, when an app is blocked, users can't do any of the following:

- Add the app personally or to a chat or team
- Send messages to the app’s bot
- Perform button actions that send information back to the app, such as actionable messages  
- View the app’s tab
- Set up connectors to receive notifications
- Use the app’s messaging extension

The legacy portal allowed controlling apps at the organization level, which means when an app is blocked, it's blocked for all users in the organization. Blocking an app on the [Manage apps](manage-apps.md) page works exactly the same way.

For app permission policies assigned to specific users, if an app with bot or connector capability was allowed and then blocked, and if the app is then allowed only for some users in a shared context, members of a group chat or channel that don't have permission to that app can see the message history and messages that were posted by the bot or connector, but can't interact with it.

## Related topics

[Admin settings for apps in Teams](admin-settings.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)
