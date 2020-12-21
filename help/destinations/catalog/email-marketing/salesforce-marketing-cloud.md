---
keywords: email;Email;e-mail;email destinations;salesforce;salesforce destination
title: Salesforce Marketing Cloud
seo-title: Salesforce Marketing Cloud
description: Salesforce Marketing Cloud is a digital marketing suite formerly known as ExactTarget that allows you to build and customize journeys for visitors and customers to personalize their experience.
seo-description: Salesforce Marketing Cloud is a digital marketing suite formerly known as ExactTarget that allows you to build and customize journeys for visitors and customers to personalize their experience.
---

# [!DNL Salesforce Marketing Cloud]

## Overview

[[!DNL Salesforce Marketing Cloud]](https://www.salesforce.com/products/marketing-cloud/email-marketing/) is a digital marketing suite formerly known as ExactTarget that allows you to build and customize journeys for visitors and customers to personalize their experience.

To send segment data to [!DNL Salesforce Marketing Cloud], you must first [connect the destination](#connect-destination) in Platform, and then [set up a data import](#import-data-into-salesforce) from your storage location into [!DNL Salesforce Marketing Cloud].

## Export Type {#export-type}

**Profile-based** - you are exporting all members of a segment, together with the desired schema fields (for example: email address, phone number, last name), as chosen from the select attributes screen of the [destination activation workflow](../../ui/activate-destinations.md#select-attributes).

## Connect destination {#connect-destination}

In **[!UICONTROL Connections]** > **[!UICONTROL Destinations]**, select [!DNL Salesforce Marketing Cloud], then select **[!UICONTROL Connect destination]**.

![Connect to Salesforce](../../assets/catalog/email-marketing/salesforce/catalog.png)

In the **[!UICONTROL Authentication]** step, if you had previously set up a connection to your cloud storage destination, select **[!UICONTROL Existing Account]** and select one of your existing connections. Or, you can select **[!UICONTROL New Account]** to set up a new connection. Fill in your account authentication credentials and select **[!UICONTROL Connect to destination]**. For [!DNL Salesforce Marketing Cloud], you can select between **[!UICONTROL SFTP with Password]** and **[!UICONTROL SFTP with SSH Key]**. Fill in the information below, depending on your connection type, and select **[!UICONTROL Connect to destination]**.

For **[!UICONTROL SFTP with Password]** connections, you must provide Domain, Port, Username, and Password.

For **[!UICONTROL SFTP with SSH Key]** connections, you must provide Domain, Port, Username, and SSH Key.

![Fill in Salesforce information](../../assets/catalog/email-marketing/salesforce/account-info.png)

In the **[!UICONTROL Setup]** step, fill in the relevant information for your destination as shown below:
- **[!UICONTROL Name]**: Pick a relevant name for your destination.
- **[!UICONTROL Description]**: Enter a description for your destination.
- **[!UICONTROL Folder Path]**: Provide the path in your storage location where Platform will deposit your export data as CSV or tab-delimited files.
- **[!UICONTROL File Format]**: **[!UICONTROL CSV]** or **[!UICONTROL TAB_DELIMITED]**. Select which file format to export to your storage location.

![Salesforce basic information](../../assets/catalog/email-marketing/salesforce/basic-information.png)

Click **[!UICONTROL Create destination]** after filling in the fields above. Your destination is now connected and you can [activate segments](../../ui/activate-destinations.md) to the destination.

## Activate segments {#activate-segments}

See [Activate profiles and segments to a destination](../../ui/activate-destinations.md) for information about the segment activation workflow.

## Destination attributes {#destination-attributes}

When [activating segments](../../ui/activate-destinations.md) to the [!DNL Salesforce Marketing Cloud] destination, we recommend that you select a unique identifier from your [union schema](../../../profile/home.md#profile-fragments-and-union-schemas). Select the unique identifier and any other XDM fields that you want to export to the destination. For more information, see [Select which schema fields to use as destination attributes in your exported files](./overview.md#destination-attributes) in Email Marketing Destinations.

## Exported data {#exported-data}

For [!DNL Salesforce Marketing Cloud] destinations, Platform creates a tab-delimited `.txt` or `.csv` file in the storage location that you provided. For more information about the files, see [Email Marketing destinations and Cloud storage destinations](../../ui/activate-destinations.md#esp-and-cloud-storage) in the segment activation tutorial. 

## Set up data import into [!DNL Salesforce Marketing Cloud] {#import-data-into-salesforce}

After connecting Platform to your [!DNL Amazon S3] or SFTP storage, you must set up the data import from your storage location into [!DNL Salesforce Marketing Cloud]. To learn how to accomplish this, see [Importing Subscribers into Marketing Cloud from a File](https://help.salesforce.com/articleView?id=mc_es_import_subscribers_from_file.htm&type=5) in the [!DNL Salesforce Help Center].