---
keywords: Experience Platform;home;popular topics;date range
solution: Experience Platform
title: Adobe Experience Platform Observability Insights
topic: overview
description: Observability Insights is a RESTful API that allows you to expose key observability metrics in Adobe Experience Platform. These metrics provide insights into Platform usage statistics, health-checks for Platform services, historical trends, and performance indicators for various Platform functionalities.
---

# Adobe Experience Platform Observability Insights overview

[!DNL Observability Insights] allows you to monitor activities on Adobe Experience Platform through the use of statistical metrics and event notifications. This document provides an overview of the various capabilities provided by the service, along with links to further documentation for details.

## [!DNL Observability Insights] API

The [!DNL Observability Insights] API is a RESTful API that allows you to expose key observability metrics in Adobe Experience Platform. These metrics provide insights into [!DNL Platform] usage statistics, health-checks for [!DNL Platform] services, historical trends, and performance indicators for various [!DNL Platform] functionalities. 

For more information on working with the API, see the [[!DNL Observability Insights] API developer guide](./api/overview.md).

## Alerts (Alpha)

>[!IMPORTANT]
>
>Alerts in Adobe Experience Platform are not available to all users yet. This feature is in alpha and still being tested. This section is subject to change.

Experience Platform allows you to subscribe to alerts based on specific Observability metrics when a certain set of conditions in your Platform operations is reached. An alert can take the form of one-time notification, or it can repeat over a pre-defined time interval until the conditions that triggered the alert have been resolved.

By subscribing to alerts, you can set up your own downstream protocols for when a job has completed, if a certain milestone within a workflow has been reached, or if any failures occurred during the process.

See the overview on [alerts](./alerts/overview.md) for more information.

## Next steps

This document covered the various capabilities of [!DNL Observability Insights]. Refer to the documentation linked to throughout this overview to learn more about each feature.