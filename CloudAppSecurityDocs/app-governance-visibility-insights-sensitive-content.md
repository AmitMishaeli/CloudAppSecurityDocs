---
title: Get insights on and regulate access to sensitive content 
ms.date: 10/19/2022
ms.topic: how-to
description: Learn how to get insights on and regulate access to sensitive content in app governance.
---

# Get insights on and regulate access to sensitive content

App governance lets you quickly identify the Microsoft 365 services apps have accessed and if these apps have accessed content with sensitivity labels.

## View apps

To view apps that have accessed data across Microsoft 365 services, select **View apps** from the overview.
> [!div class="mx-imgBorder"]
>![Apps that have accessed data across Microsoft 365 services](media/app-governance-visibility-insights-sensitive-content/image7.png)

Alternatively, select any of the labels listed under **Sensitivity labels access** in the apps page.

> [!div class="mx-imgBorder"]
>![Under each service type, app governance shows the number of times the app has accessed the corresponding label name in the last 30 days.](media/app-governance-visibility-insights-sensitive-content/sensitive-labels-details.png)

To view details on what sensitive content the app has accessed in the last 30 days, select the app and then select **Sensitive labels**. Under each service type, app governance shows the number of times the app has accessed the corresponding label name in the last 30 days. For example, in the screenshot below, the app has accessed content with the sensitivity label *Highly confidential* 7 times on SharePoint, 15 times on OneDrive, and 25 times on Exchange Online in the last 30 days.
## Regulate access to sensitive content
By default, the predefined policy **Access to sensitive data** triggers alerts after an app accesses sensitive content.

You can customize the predefined policy by:

- Selecting **Disable app** as the policy action to automatically deactivate apps that trigger alerts.
- Modifying the policy scope to apply the policy to specific apps or exclude specific apps.

For even more customization options, create a custom policy using the condition **Sensitivity labels accessed** in combination with [other policy conditions](app-governance-app-policies-create.md#custom).

## Next step

[Get detailed insights on a specific app](app-governance-visibility-insights-view-apps.md).




