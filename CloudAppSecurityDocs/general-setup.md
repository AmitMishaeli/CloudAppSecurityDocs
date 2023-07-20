---
title: Basic setup
description: This article explains how to provide information about your organization in Defender for Cloud Apps.
ms.date: 04/20/2023
ms.topic: how-to
---
# Basic setup for Defender for Cloud Apps

[!INCLUDE [Banner for top of topics](includes/banner.md)]

The following procedure gives you instructions for customizing your Microsoft Defender for Cloud Apps environment.

## Prerequisites

For portal access requirements, see [Portal access](network-requirements.md#portal-access).

## Set up your Defender for Cloud Apps environment

1. In the Microsoft 365 Defender portal, select **Settings**. Then choose **Cloud Apps**.

1. Under **System** -> **Organization details**, it's important that you provide an **Organization display name** for your organization. It's displayed on emails and web pages sent from the system.

1. Provide an **Environment name** (tenant). This information is especially important if you manage more than one tenant.

1. It's also possible to provide a **Logo** that is displayed in email notifications and web pages sent from the system. The logo should be a png file with a maximum size of 150 x 50 pixels on a transparent background.

1. Make sure you add a list of your **Managed domains** to identify internal users. Adding managed domains is a crucial step. Defender for Cloud Apps uses the managed domains to determine which users are internal, external, and where files should and shouldn't be shared. This information is used for reports and alerts.

    * Users in domains that aren't configured as internal are marked as external. External users aren't scanned for activities or files.

1. If you're integrating with Microsoft Purview Information Protection, see [Microsoft Purview Information Protection Integration](azip-integration.md) for information.

    * To work with Microsoft Purview Information Protection integration, you must enable the [App connector for Microsoft 365](./connect-office-365.md).

> [!NOTE]
> If you use ExpressRoute, Defender for Cloud Apps is deployed in Azure and fully integrated with [ExpressRoute](/azure/expressroute/expressroute-introduction). All interactions with the Defender for Cloud Apps apps APIs and traffic sent to Defender for Cloud Apps APIs, including upload of discovery logs, is routed via ExpressRoute for improved latency, performance, and security.
>
> Microsoft 365 Defender portal usage is not included in the ExpressRoute integration.
>
> For more information about Microsoft Peering, see [ExpressRoute circuits and routing domains](/azure/expressroute/expressroute-circuit-peerings).

## Next steps

> [!div class="nextstepaction"]
> [Set up Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
