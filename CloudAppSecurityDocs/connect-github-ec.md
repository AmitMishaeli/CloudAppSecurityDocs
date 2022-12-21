---
title: Connect GitHub Enterprise Cloud to Defender for Cloud Apps
description: This article provides information about how to connect your GitHub Enterprise Cloud app to Defender for Cloud Apps using the API connector  for visibility and control over use.
ms.date: 11/09/2021
ms.topic: how-to
---
# Connect GitHub Enterprise Cloud to Microsoft Defender for Cloud Apps

[!INCLUDE [Banner for top of topics](includes/banner.md)]

This article provides instructions for connecting Microsoft Defender for Cloud Apps to your existing GitHub Enterprise Cloud organization using the App Connector APIs. This connection gives you visibility into and control over your organization's GitHub Enterprise Cloud use. For more information about how Defender for Cloud Apps protects GitHub Enterprise Cloud, see [Protect GitHub Enterprise](protect-github.md).

## Prerequisites

- Your organization must have a GitHub Enterprise Cloud license.
- The GitHub account used for connecting to Defender for Cloud Apps must have *Owner* permissions for your organization.
- To verify owners of your organization, browse to your organization's page, select **People**, and then filter by *Owner*.

## How to connect GitHub Enterprise Cloud to Defender for Cloud Apps

### Verify your GitHub domains

Verifying your domains is optional. However, we highly recommend that you do verify your domains so that Defender for Cloud Apps can match the domain emails of your GitHub organization's members to their corresponding Azure Active Directory user.

These steps can be completed independently of the [Configure GitHub Enterprise Cloud](#configure-github-enterprise-cloud) steps and can skipped if you have already verified your domains.

1. Upgrade your organization to the [Corporate Terms of Service](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/upgrading-to-the-corporate-terms-of-service).
1. Verify [your organization's domains](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/verifying-your-organizations-domain).

    > [!NOTE]
    > Make sure to verify each of the managed domains listed in your Defender for Cloud Apps portal. To view your managed domains, in Defender for Cloud Apps, browse to **Settings** > **Organization details** > **Managed domains**.

### Configure GitHub Enterprise Cloud

1. **Find your Organization's login name**  
In GitHub, browse to your organization's page, and from the URL, make a note of your organization login name, you'll need it later.

    > [!NOTE]
    > The page will have a URL like `https://github.com/<your-organization>`. For example, if your organization's page is `https://github.com/sample-organization`, the organization's login name is *sample-organization*.

    ![Screenshot showing obtaining organization login name.](media/connect-github-org-login-name.png)

1. **Create an OAuth App for Defender for Cloud Apps to connect your GitHub organization.**  
Repeat this step for each additional connected organization.

    1. Browse to **Settings** > **Developer settings**, select  **OAuth Apps**, and then click **Register an application**. Alternatively, if you have existing OAuth apps, click **New OAuth App**.

        ![Screenshot showing creating an oauth app.](media/connect-github-create-oauth-app.png)

    1. Fill out the **Register a new OAuth app** details and then click **Register application**.
        - In the **Application name** box, enter a name for the app.
        - In the **Homepage URL** box, enter the URL for the app's homepage.
        - In the **Authorization callback URL** box, enter the following value: `https://portal.cloudappsecurity.com/api/oauth/saga`.

            > [!NOTE]
            >
            > - For US Government GCC customers, enter the following value: `https://portal.cloudappsecuritygov.com/api/oauth/saga`
            > - For US Government GCC High customers, enter the following value: `https://portal.cloudappsecurity.us/api/oauth/saga`

        ![Screenshot showing registering an oauth app.](media/connect-github-register-oauth-app.png)

    > [!NOTE]
    >
    > - Apps owned by an organization have access to the organization's apps. For more information, see [About OAuth App access restrictions](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions).

1. Browse to **Settings** > **OAuth Apps**, select the OAuth App you just created, and make note of its **Client ID** and **Client Secret**.

    ![Screenshot showing details of an oauth app.](media/connect-github-oauth-app-details.png)

### Configure Defender for Cloud Apps

1. In the C[loud App Security portal](https://portal.cloudappsecurity.com/), click **Investigate** and then **Connected apps**.

1. In the **App connectors** page, click the plus button followed by **GitHub**.

1. In the pop-up, fill out the **Client ID**, **Client Secret**, and **Organization Login Name** that you made a note of earlier, and then click **Connect in GitHub**.

    ![Screenshot showing connect github api.](media/connect-github-connect-app.png)

    The GitHub sign-in page opens. If necessary, enter your GitHub administrator credentials to allow Defender for Cloud Apps access to your team's GitHub Enterprise Cloud instance.

1. Request organization access and authorize the app to give Defender for Cloud Apps access to your GitHub organization.

    > [!NOTE]
    > Defender for Cloud Apps requires the following OAuth scopes:
    >
    > - **admin:org** - required for synchronizing your organization's audit log
    > - **read:user** and **user:email** - required for synchronizing your organization's members
    > - **repo:status** - required for synchronizing repository-related events in the audit log
    > For more information about OAuth scopes, see [Understanding scopes for OAuth Apps](https://docs.github.com/developers/apps/building-oauth-apps/scopes-for-oauth-apps).

    ![Screenshot showing authorize github oauth.](media/connect-github-authorize-app.png)

1. Back in the Defender for Cloud Apps console, you should receive a message that GitHub was successfully connected.

1. Work with your GitHub organization owner to grant organization access to the OAuth app created. The organization owner should navigate to **Organization Settings** -> **Integrations** -> **Third-party access** to grant access. 

 > [!NOTE]
 > 
 > The organization owner will find the request from the OAuth app only after connecting GitHub to Defender for Cloud Apps. 

1. Make sure the connection succeeded by clicking **Test API**.

    Testing may take a couple of minutes. After you receive a success notice, click **Close**.

After connecting GitHub Enterprise Cloud, you'll receive events for 7 days prior to connection.

If you have any problems connecting the app, see [Troubleshooting App Connectors](troubleshooting-api-connectors-using-error-messages.md).

## Next steps

> [!div class="nextstepaction"]
> [Control cloud apps with policies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
