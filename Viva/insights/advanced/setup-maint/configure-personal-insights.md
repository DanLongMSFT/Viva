---

ms.date: 06/20/2023
title: Configure personal insights defaults
description: Configuration options that Microsoft 365 administrators can make for personal insights in Microsoft Viva Insights
author: lilyolason
ms.author: v-lilyolason
ms.topic: article
ms.localizationpriority: medium 
ms.service: viva 
ms.subservice: viva-insights 
ms.collection: 
- M365-analytics
- viva-insights-personal
manager: anirudhbajaj
audience: Admin

---

# Configure personal insights defaults

![global admin](../images/applies-to-m365-admin.png)*Applies to: Microsoft 365 global admin or Exchange Online admin*

:::image type="content" source="../../advanced/images/setup-app-default-1.png" alt-text="Image alt text." lightbox="../../advanced/images/setup-app-default-1.png":::

To configure settings for personal insights, you have a few options:

* At the tenant level, you can use the [Microsoft 365 admin center](#configure-access-at-the-tenant-level-through-the-admin-center) or [PowerShell](#configure-access-at-the-tenant-level).
* At the user level (one or multiple users), you can use [PowerShell](#configure-access-at-the-user-level). 

We cover both configuration options in this article.

## Prerequisites, defaults, and privacy

### Prerequisites

#### User licenses

To access Microsoft Viva Insights, users need to have licenses that include a Viva Insights service plan, as described in [plans and environments](../../personal/Overview/plans-environments.md).

For information on how to assign a license, refer to:

* [Assign licenses to users in Microsoft 365 for business](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).
* [Assign licenses for Viva Insights](../../advanced/setup-maint/assign-licenses.md).

#### Admin permissions

You need to be a Microsoft 365 global admin or an Exchange Online (EXO) admin role to configure users for Viva Insights in PowerShell.

### Defaults 

When you set defaults at the tenant or user level, you’re setting users’ initial access to Viva Insights. However, users have the flexibility to keep the status you set or change it. Users can learn how to opt in or out of Viva Insights here: [Opt out of Viva Insights](https://support.microsoft.com/en-us/topic/opt-out-of-viva-insights-ecfd76f9-52ef-4882-9235-be1f59c25967). The exception is if a user's license with a Viva Insights service plan expires. In that case, the user can't opt in.

Defaults you can set are:

* All of Viva Insights (user-level only)
* The Viva Insights web experience
* Viva digest emails
* Meeting effectiveness surveys
* The Viva Insights Outlook add-in
* Schedule send suggestions in Outlook

### Privacy

Refer to the [Privacy guide](../../personal/Overview/privacy-guide-users.md) to understand how privacy is built into Viva Insights and to learn what you can configure to address specific privacy requirements.

## Configure access at the tenant level through the admin center

Through the Microsoft admin center, you can configure access to Viva Insights elements for all users in your organization.

>[!Important]
>You need to have a Global admin or an Exchange Online admin role to configure tenant-level settings in the admin center. Make sure you're signed in to the Microsoft admin center as a Global or Exchange Online admin before configuring settings.

### To manage availability for the Viva Insights app in Teams

1. In the Microsoft admin center, go to the [setup tab](https://admin.microsoft.com/adminportal/home#/featureexplorer) and select **Microsoft Viva**, then **Viva Insights**.
1. Under **Viva Insights in Microsoft 365**, select **Manage availability in the Teams admin center**. This option takes you directly to the Teams admin center, where you can configure the appropriate settings.

    :::image type="content" source="../../images/mya/setup/mac-teams-admin1.png" alt-text="Screenshot that shows Manage availability in Teams admin center in the Viva Insights admin page.":::
    
Go to our [Teams admin tasks](teams-admin-setup.md) doc for more information about setting up the Viva Insights app in Teams.    

### To enable access to Viva Insights features

*Use for [Default on](../../personal/setup/deployment-guide.md#default-on) and [Default off](../../personal/setup/deployment-guide.md#default-off) rollout scenarios, as explained in [Personal insights deployment guide](../../personal/setup/deployment-guide.md#choose-a-rollout-scenario)*

1. In the Microsoft admin center, go to the [setup tab](https://admin.microsoft.com/adminportal/home#/featureexplorer) and select **Microsoft Viva**, then **Viva Insights**.
1. Under **Viva Insights in Microsoft 365**, select **Manage settings for Viva Insights**.

    :::image type="content" source="../../images/mya/setup/manage-settings-insights.png" alt-text="Screenshot that shows Manage settings for Viva Insights in the Viva Insights admin page.":::
1. In the resulting pane:
    1. Select **Viva Insights web experience** to keep all Viva Insights users in your organization opted _in_ for access to the Viva Insights app on the web. Clear the selection for **Viva Insights web experience** to opt users _out_.  
    1. Select **Digest email** to keep all Viva Insights users in your organization opted _in_ for access to the [digest mails](../../personal/use/email-digests-3.md). Clear the selection for **Digest email** to opt users _out_.  
    1. Select **Insights Outlook add-in and inline suggestions** to keep all users in your organization opted _in_ for access to the add-in. Deselect it to opt users _out_. If you opt out of the Viva Insights Outlook add-in, the Productivity inline suggestions are also turned _off_ for all users. Individuals can also turn [inline suggestions](https://support.microsoft.com/en-us/topic/inline-suggestions-in-outlook-064a323e-6dc7-40e9-ab1b-199de8d39db5) *on* or *off* through their own **Settings** within the Viva Insights add-in.
    1. Select **Meeting effectiveness surveys** to keep all users in your organization opted _in_ for access to the surveys. Deselect it to opt users _out_. If you opt users out, they won't see an option for meeting effectiveness surveys in their settings.
    1. Select **Schedule send suggestions** to keep all Viva Insights users in your organization opted in for access to schedule send suggestions, and then select **Save changes**. Deselect **Schedule send suggestions** to opt users out. These will be default settings for all users. Users can change them at any time from their Viva Insights Outlook add-in and Viva Insights app settings page. It may take up to 24 hours for all changes to take effect.

    >[!Note]
    >After a new tenant is established, it can take up to 48 hours for this functionality to become available.

    :::image type="content" source="../../Images/MyA/setup/insights-settings-pane1.png" alt-text="Screenshot that shows the Microsoft Viva Insights (formerly MyAnalytics) settings pane with all selections enabled.":::

1. Select **Save**.


You can also get to these settings in from the main [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal):

1. In the left pane, expand **Settings** and then select **Org settings**.
1. On the **Services** tab, select **Microsoft Viva Insights (formerly MyAnalytics)**.

## Configure access at the tenant or user level through PowerShell

### Command sequence

For user configuration settings, you’ll use the [Set-MyAnalyticsFeatureConfig](/powershell/module/exchange/set-myanalyticsfeatureconfig) and [Get-MyAnalyticsFeatureConfig](/powershell/module/exchange/get-myanalyticsfeatureconfig) cmdlets. For tenant configuration settings, you’ll use the [Set-DefaultTenantMyAnalyticsFeatureConfig](/powershell/module/exchange/set-defaulttenantmyanalyticsfeatureconfig) and [Get-DefaultTenantMyAnalyticsFeatureConfig](/powershell/module/exchange/get-defaulttenantmyanalyticsfeatureconfig) cmdlets. Before you can use any of these cmdlets, you'll need to install a module and sign in to be authenticated. 

1. [Connect to Exchange Online](#connect-to-exchange-online) and, when prompted, sign in with your admin credentials.
2. After you've signed in, you're ready to work with user and tenant configuration settings:

   * [Set access for a tenant](#set-access-for-one-user)
   * [Confirm access for a tenant](#set-access-for-one-user)
   * [Set access for one user](#set-access-for-one-user)  
   * [Confirm access for one user](#confirm-access-for-one-user)
   * [Set access for multiple users](#set-access-for-multiple-users)

#### Connect to Exchange Online

To connect to Exchange Online, you install prerequisites and then you install the [Exchange Online PowerShell V2 module](/powershell/exchange/exchange-online-powershell-v2).

1. Open PowerShell.

2. <u>Prerequisite #1:</u> Installing packages from the [PowerShell Gallery](/powershell/scripting/gallery/getting-started) requires the latest version of the PowerShellGet module. Run these commands to install it:

   ```powershell
   Install-Module PowerShellGet –Repository PSGallery –Force
   ```

   For more information, see [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).  

3. <u>Prerequisite #2:</u> Install the Exchange Online PowerShell V2 module:

   ```powershell
   Install-Module -Name ExchangeOnlineManagement -RequiredVersion 2.0.4
   ```

   For more information, see [Install-Module](/powershell/module/powershellget/install-module).
   
4. <u>Connect to Exchange Online.</u> In PowerShell, run the command [Connect-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline).

   ```powershell
   Connect-ExchangeOnline
   ```

   This will prompt you to authenticate, which you do by entering your admin credentials.

### Configure access at the tenant level

Use PowerShell to configure access for all users in a tenant. For example, you could opt everyone out completely, which would turn off all Viva Insights functionality for all users. However, users can choose to opt back in.

Configure Viva Insights by setting the `PrivacyMode` parameter. For information about the values of `PrivacyMode`, refer to the next section, Tenant configuration settings.

#### Tenant configuration settings

|Parameter| Required| Description| Default value|
|----------|---------|---------|------|
|`PrivacyMode`| Yes| <ul><li>`Opt-out`: Viva Insights won't use any users’ data within the tenant to compute derived statistics for other users. Users won't see statistics in Viva Insights but can choose to opt in from the feature settings menu. <li> `Opt-in`: Viva Insights uses user data to compute derived statistics for other users in the tenant. Users can see statistics in Viva Insights, but can choose to opt out from the Feature settings menu.
|`Feature`| No| <ul><li>`Add-in`<li>`Dashboard`<li>`Digest-email`<li>`Meeting-effectiveness-survey`<li>`Schedule-send`
|`SamplingRate`|No|Value from `0.1` to `0.7`. The sampling rate you specify here is the percentage of meetings that get checked to receive a meeting effectiveness survey. For example, `0.1` indicates 10%.

Also refer to [Parameters: Set-DefaultTenantMyAnalyticsFeatureConfig](/powershell/module/exchange/set-defaulttenantmyanalyticsfeatureconfig#parameters).

#### Set access for a tenant

Configure access settings for a tenant with the PowerShell cmdlet [Set-DefaultTenantMyAnalyticsFeatureConfig](/powershell/module/exchange/set-defaulttenantmyanalyticsfeatureconfig).


```powershell
Set-DefaultTenantMyAnalyticsFeatureConfig
   [-PrivacyMode <String>]
   [-Feature <String>]
   [-IsEnabled <Boolean>]
   [-ResultSize <Unlimited>]
   [<CommonParameters>]
```
#### Command reference: `Set-DefaultTenantMyAnalyticsFeatureConfig`

The PowerShell command `Set-DefaultTenantMyAnalyticsFeatureConfig` can be used in three different ways:

* Set the `PrivacyMode` parameter
* Enable or disable Viva Insights features for all users in the tenant
* Set `PrivacyMode` and enable or disable features

##### Set the `PrivacyMode` parameter

For more information about `PrivacyMode`, refer to [Configure access at the tenant level](#configure-access-at-the-tenant-level).

* Command syntax - `PrivacyMode`: 

    ```powershell
    Set-DefaultTenantMyAnalyticsFeatureConfig -PrivacyMode <opt-in/opt-out>`
    ```

* Example – `PrivacyMode`: Running the following command sets the privacy mode to "opt-in" and enables all the personal insights features for all users in the tenant:

    ```powershell
    Set-DefaultTenantMyAnalyticsFeatureConfig -PrivacyMode Opt-in
    ```

##### Enable or disable Viva Insights features

* Command syntax – features on or off: 

    ```powershell
      Set-DefaultTenantMyAnalyticsFeatureConfig -Feature <dashboard/add-in/digest-email/all> -isEnabled <$true/$false>
    ```

* Example – features on or off:
Running the following command disables the digest email for all users in the tenant:

    ```powershell
       Set-DefaultTenantMyAnalyticsFeatureConfig -Feature digest-email -isEnabled $false
    ```

##### Set `PrivacyMode` and enable or disable features

*Use for the [Mixed deployment](../../personal/setup/deployment-guide.md#mixed-deployment) rollout scenario, as explained in [Personal insights deployment guide](../../personal/setup/deployment-guide.md#choose-a-rollout-scenario)*

* Command syntax – `PrivacyMode` and features: 

    ```powershell
      Set-DeafultTenantMyAnalyticsFeatureConfig -PrivacyMode <opt-in/opt-out> -Feature <dashboard/add-in/digest-email/all> -isEnabled <$true/$false>
    ```

* Example – `PrivacyMode` and features: Running the following command opts all users in the tenant in (by setting `PrivacyMode` to `Opt-in`) and enables all the personal insights features except the digest email:

    ```powershell
    Set-DefaultTenantMyAnalyticsFeatureConfig -PrivacyMode opt-in -Feature digest-email -isEnabled $false 
    ```

#### Confirm access for a tenant

Use the following command to confirm whether users in a tenant have access to Viva Insights (the value for `PrivacyMode`):

```powershell
Get-DefaultTenantMyAnalyticsFeatureConfig 
```

`Get-DefaultTenantMyAnalyticsFeatureConfig` reveals the tenant’s current configuration settings. The following is a sample output of this cmdlet. This output indicates that users in the tenant are currently opted in and that they have all Viva Insights features turned on except the digest email:

```powershell
 TenantId : x0xx10-00x0-0x01-0xxx-x0x0x01xx100
 IsDashboardEnabled : true
 IsAddInEnabled : true
 IsDigestEmailEnabled : false
 IsMeetingEffectivenessSurveyEnabled : opted-in
 IsScheduleSendEnabled : true
```

### Configure access at the user level

You can use PowerShell to configure Viva Insights access for individual users in your organization. For example, you could opt out the user completely, which would turn off all Viva Insights functionality for that user. However, the user can choose to [opt back in](https://support.microsoft.com/en-us/topic/opt-out-of-viva-insights-ecfd76f9-52ef-4882-9235-be1f59c25967). 

Configure Viva Insights by setting the `PrivacyMode` parameter. For information about the values of `PrivacyMode`, refer to the next section, [User configuration settings](#user-configuration-settings). 

>[!Important]
>The PowerShell cmdlets [Get-UserAnalyticsConfig](/powershell/module/exchange/get-useranalyticsconfig) and [Set-UserAnalyticsConfig](/powershell/module/exchange/set-useranalyticsconfig), which you might have used to configure access to Viva Insights, are no longer available. Instead, use the following new cmdlets: [Get-MyAnalyticsFeatureConfig](/powershell/module/exchange/get-myanalyticsfeatureconfig) and [Set-MyAnalyticsFeatureConfig](/powershell/module/exchange/set-myanalyticsfeatureconfig), which offer the same functionality along with some additional granular control.

### User configuration settings

#### About managing access and opt out

Viva Insights has core features and premium features. Access to features and types of data processing depends on a user's assigned service plan.

As an admin, you have the ability to configure opt in/opt out behavior for end users. For premium plans, you can also [allow](privacy-settings.md) users to control what’s included in advanced and some aggregated insights. Then, users can choose to [opt out](https://support.microsoft.com/topic/opt-out-of-viva-insights-ecfd76f9-52ef-4882-9235-be1f59c25967) through their Viva Insights app in Teams or on the web. When users opt out of Viva Insights:

* They lose access to the [Viva Insights app in Teams and web](https://support.microsoft.com/topic/viva-insights-app-in-teams-and-on-the-web-f07f80a1-177d-4541-9185-31493b74fc0f).
* Their data isn’t included in [email read rates](https://support.microsoft.com/topic/inline-suggestions-in-outlook-064a323e-6dc7-40e9-ab1b-199de8d39db5).

Also, if users have a premium plan:

* Their productivity data isn’t included in [person queries](../analyst/person-query-overview.md), if you choose. 
* Their collaboration data still feeds into aggregated insights—that is, [meeting queries](../analyst/meeting-query.md) and [organization insights](../../org-team-insights/org-insights.md).



#### Set access for one user

Configure access settings for a user with the PowerShell cmdlet [Set-MyAnalyticsFeatureConfig](#command-reference-set-myanalyticsfeatureconfig):

```powershell
Set-MyAnalyticsFeatureConfig –Identity <string> [-PrivacyMode <string[]>]
```

Parameter   |   Required   |   Description   | Default value
----------  |  ----------  |  -------------- | -------------
`Identity`   |   Yes   | User ID for the current user as stored in Azure Active Directory (AD)   |   --
`PrivacyMode`   |   Yes   | <ul><li>`Opt-out`: Viva Insights won't use the user's data to compute derived statistics for other users. The user won't see statistics in Viva Insights, but can choose to opt in from the Feature settings menu.</li><li>`Opt-in`: Viva Insights uses the user's data to compute derived statistics for other users. The user can see statistics in Viva Insights, but can choose to opt out from the Feature settings menu.</li></ul>|  Opt-in

Use `Set-MyAnalyticsFeatureConfig` to change the configuration settings of the user who is identified by the `-Identity` parameter. The following is a sample output of this cmdlet. It indicates that the user was opted in and that all of that user's Viva Insights features were turned on except the digest email:

   ```powershell
      UserId : <username>@<domain>
      `PrivacyMode` : opt-in
      IsDashboardEnabled : true
      IsAddInEnabled  : true
      IsDigestEmailEnabled : false
   ```

   Also refer to [Command reference: Set-MyAnalyticsFeatureConfig](#command-reference-set-myanalyticsfeatureconfig).

#### Confirm access for one user

Use the following to confirm whether a user has access to Viva Insights (the value for `PrivacyMode`):

```powershell
Get-MyAnalyticsFeatureConfig –Identity <string>
```

Parameter   |   Required   |    Description    |   Default value
----------- | ------------ |  ---------------  | ---------------
`Identity`    |  Yes         |    User ID for the current user as stored in Azure AD  | -

`Get-MyAnalyticsFeatureConfig` reveals the current configuration settings of the user who is identified by the -Identity parameter. The following is a sample output of this cmdlet. It indicates that the user is currently opted in and that they have all Viva Insights features turned on except the digest email:

```powershell
    UserId : <username>@<domain>
    `PrivacyMode` : opt-in
    IsDashboardEnabled : true
    IsAddInEnabled  : true
    IsDigestEmailEnabled : false
   ```

#### Set access for multiple users

Use the following steps in the [Exchange Online PowerShell V2 module](/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2) to change access to Viva Insights (the value of `PrivacyMode`) for multiple users by running a PowerShell script that iterates through the users, changing the value one user at a time.

1. Create a comma-separated value (.csv) text file that contains the UserPrincipalName field of the users you want to configure. For example:

```
   UserPrincipalName
   ClaudeL@contoso.onmicrosoft.com
   LynneB@contoso.onmicrosoft.com
   ShawnM@contoso.onmicrosoft.com
   ```

2. Specify the location of the input .csv file, the output .csv file, and the value of `PrivacyMode` that you want to set for each user:

   ```powershell
   $inFileName="<path and file name of the input .csv file that contains the users, example: C:\admin\Users2License..csv>"
   $outFileName="<path and file name of the output .csv file that records the results, example: C:\admin\Users2License-Done..csv>"
   $privacyMode = "Opt-in"

   $users=Import-Csv $inFileName
   ForEach ($user in $users)
   {
   $user.Userprincipalname
   $upn=$user.UserPrincipalName

   Set-MyAnalyticsFeatureConfig –Identity $upn -PrivacyMode $privacyMode
   Get-MyAnalyticsFeatureConfig –Identity $upn | Export-Csv $outFileName
   }
   ```

   Also see [Command reference: Set-MyAnalyticsFeatureConfig](#command-reference-set-myanalyticsfeatureconfig).

3. Run the resulting commands at the Exchange Online PowerShell V2 module command prompt. For more information about the module, refer to [Exchange Online PowerShell V2 module](/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2).

This PowerShell script:

* Shows the user principal name for each user.
* Sets the specified privacy mode for each user.
* Creates a .csv file with all the users that were processed and shows their status.

### Command reference: Set-MyAnalyticsFeatureConfig

The PowerShell command [Set-MyAnalyticsFeatureConfig](/powershell/module/exchange/set-myanalyticsfeatureconfig) can be used in three different ways:

* [Set the `PrivacyMode` parameter](#set-the-privacymode-parameter)
* [Enable or disable Viva Insights features](#enable-or-disable-viva-insights-features)
* [Set `PrivacyMode` *and* enable or disable features](#set-privacymode-and-enable-or-disable-features)

#### Set the `PrivacyMode` parameter

For more information about `PrivacyMode`, refer to [Configure access at the user level](#configure-access-at-the-user-level).

##### Command syntax - `PrivacyMode`

```powershell
Set-MyAnalyticsFeatureConfig -Identity \<string\> -PrivacyMode <opt-in/opt-out>
```

##### Example - `PrivacyMode`

Running the following command sets `PrivacyMode` to `opt-in` and enables all the personal insights features for the user:

   ```powershell
   Set-MyAnalyticsFeatureConfig -Identity <string> -PrivacyMode opt-in   
   ```

#### Enable or disable Viva Insights features

* Command syntax - features on or off:

    ```powershell
    Set-MyAnalyticsFeatureConfig -Identity \<string\> -Feature <dashboard/add-in/digest-email/all> -isEnabled <$true/$false>`
    ```

* Example - features on or off: Running the following command disables the digest email for the user:

   ```powershell
    Set-MyAnalyticsFeatureConfig -Identity <string> -Feature digest-email -isEnabled $false
   ```

#### Set `PrivacyMode` *and* enable or disable features

##### Command syntax - `PrivacyMode` and features

```powershell
Set-MyAnalyticsFeatureConfig -Identity \<string\> -PrivacyMode <opt-in/opt-out> -Feature <dashboard/add-in/digest-email/all> -isEnabled <$true/$false>`
```

##### Example - `PrivacyMode` and features

Running the following command opts the user in (by setting `PrivacyMode` to `opt-in`) and enables all the personal insights features except the digest email:

   ```powershell
Set-MyAnalyticsFeatureConfig -Identity <string> -PrivacyMode opt-in -Feature digest-email -isEnabled $false 
   ```

> [!div class="nextstepaction"]
> [Configure Teams app settings](teams-admin-setup.md)

*Applies to: Teams Service Administrator, Microsoft 365 global admin, and Exchange Online admin*