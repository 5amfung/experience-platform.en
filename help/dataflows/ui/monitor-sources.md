---
keywords: Experience Platform;home;popular topics;monitor accounts;monitor dataflows;dataflows;sources
description: Source connectors in Adobe Experience Platform provide the ability to ingest externally sourced data on a scheduled basis. This tutorial provides steps for viewing existing dataflows from the Sources workspace.
solution: Experience Platform
title: Monitor dataflows
topic: overview
type: Tutorial
---

# Monitor dataflows for sources in the UI

Source connectors in Adobe Experience Platform provide the ability to ingest externally sourced data on a scheduled basis. This tutorial provides steps for viewing existing dataflows from the [!UICONTROL Sources] workspace.

## Getting started

This tutorial requires a working understanding of the following components of Adobe Experience Platform:

- [Sources](../../sources/home.md): [!DNL Experience Platform] allows data to be ingested from various sources while providing you with the ability to structure, label, and enhance incoming data using [!DNL Platform] services.
- [Sandboxes](../../sandboxes/home.md): [!DNL Experience Platform] provides virtual sandboxes which partition a single [!DNL Platform] instance into separate virtual environments to help develop and evolve digital experience applications.

## Monitor dataflows

Log in to the [Experience Platform UI](https://platform.adobe.com) and then select **[!UICONTROL Sources]** from the left navigation to access the [!UICONTROL Sources] workspace. Select **[!UICONTROL Dataflows]** from the top header to view existing dataflows.

![catalog-dataflows](../assets/ui/monitor-sources/catalog-dataflows.png)

A list of existing dataflows appears. On this page is a list of viewable dataflows, including information about their source, username, number of dataflows, and status.

See the following table for more information on statuses:

| Status | Description |
| ------ | ----------- |
| Enabled | The `Enabled` status indicates that a dataflow is active and is ingesting data according to the schedule it was provided. |
| Disabled | The `Disabled` status indicates that a dataflow is inactive and is not ingesting any data. |
| Processing | The `Processing` status indicates that a dataflow is not yet active. This status is often encountered immediately after a new dataflow is created. |
| Error | The `Error` status indicates that the activation process of a dataflow has been disrupted. |

 Select the funnel icon on the top left to sort.

![dataflows-list](../assets/ui/monitor-sources/dataflows-list.png)

The sorting panel appears. Select the source you wish to access from the scroll menu and select the dataflow from the list on the right. You can also select the ellipses (`...`) button to bring up more available options for your selected dataflow.

![sort-dataflows](../assets/ui/monitor-sources/dataflows-sort.png)

The **[!UICONTROL Dataflow activity]** page contains details on the number of records ingested and records failed, as well as information regarding dataflow status and processing time. Select the calendar icon above the dataflow to adjust the time frame of your ingestion records.

![datflow-activity](../assets/ui/monitor-sources/dataflow-activity.png)

The calendar allows you to view the different time frames for ingested records. You can choose to select one of the two pre-set options "[!UICONTROL Last 7 days]" or "[!UICONTROL Last 30 days]". Alternatively, you can set a custom time frame using the calendar. Select your time frame of choice and select **[!UICONTROL Apply]** to continue.

![flow-calendar](../assets/ui/monitor-sources/flow-calendar.png)

By default, the **[!UICONTROL Dataflow activity]** displays the **[!UICONTROL Properties]** panel associated with the dataflow. Select the flow run from the list to see its associated meta data, including information about its unique run ID.

Select **[!UICONTROL Dataflow run start]** to access the **[!UICONTROL Dataflow run overview]**.

![runs](../assets/ui/monitor-sources/run-metadata.png)

The **[!UICONTROL Dataflow run overview]** displays information on the dataflow including its metadata, partial ingestion status, and assigned error threshold. The upper header also includes an error summary. The **[!UICONTROL Error summary]** contains the specific top-level error that shows at which step the ingestion process encountered an error.

![dataflow-run-overview](../assets/ui/monitor-sources/dataflow-run-overview.png)

Refer to the following table for errors that can be seen in the **[!UICONTROL Error summary]**.

| Error | Description |
| ---------- | ----------- |
| `CONNECTOR-1001-500` | An error occurred while data is being copied from a source. |
| `CONNECTOR-2001-500` | An error occurred while copied data is being processed to [!DNL Platform]. This error could be regarding parsing, validating, or transforming. |

The lower half of the screen contains information on **[!UICONTROL Dataflow run errors]**. From here, you can also view the files ingested, preview and download error diagnostics, or download the file manifest.

The **[!UICONTROL Dataflow run errors]** section displays the error code, the number of records failed, and information describing the error.

Select **[!UICONTROL Preview error diagnostics]** to see more information on the ingestion error.

![Dataflow-run-errors](../assets/ui/monitor-sources/dataflow-run-errors.png)

The **[!UICONTROL Error diagnostics preview]** panel appears. This screen displays specific information regarding the ingestion failure, including the file name, error code, the name of the column in which the error occurred, and a description of the error.

This section also includes a preview of the column that contains the error.

>[!IMPORTANT]
>
>To enable **[!UICONTROL Error diagnostics preview]** you must activate **[!UICONTROL Partial ingestion]** and **[!UICONTROL Error diagnostics]** when configuring a dataflow. Doing so will allow the system to scan all of the records ingested during the flow run.

![Preview-error-diagnostics](../assets/ui/monitor-sources/preview-error-diagnostics.png)

After previewing the errors, you can select **[!UICONTROL Download]** from within the **[!UICONTROL dataflow runs overview]** panel to access full error diagnostics and download the file manifest. See the documents on [error diagnostics](../../ingestion/batch-ingestion/partial.md#retrieve-errors) and [downloading metadata](../../ingestion/batch-ingestion/partial.md#download-metadata) for more information.

![Preview-error-diagnostics](../assets/ui/monitor-sources/download.png)

For more information on monitoring dataflows and ingestion, refer to the tutorial on [monitoring streaming dataflows](../../ingestion/quality/monitor-data-ingestion.md).

## Next steps

By following this tutorial, you have successfully accessed existing accounts and dataflows from the **[!UICONTROL Sources]** workspace. Incoming data can now be used by downstream [!DNL Platform] services such as [!DNL Real-time Customer Profile] and [!DNL Data Science Workspace]. See the following documents for more details:

- [Real-time Customer Profile overview](../../profile/home.md)
- [Data Science Workspace overview](../../data-science-workspace/home.md)
