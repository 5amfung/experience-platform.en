---
keywords: Experience Platform;home;popular topics;Snowflake;snowflake
solution: Experience Platform
title: Create a Snowflake Base Connection Using the Flow Service API
topic-legacy: overview
type: Tutorial
description: Learn how to connect Adobe Experience Platform to Snowflake using the Flow Service API.
---
# Create a [!DNL Snowflake] base connection using the [!DNL Flow Service] API

A base connection represents the authenticated connection between a source and Adobe Experience Platform.

This tutorial walks you through the steps to create a base connection for [!DNL Snowflake] using the [[!DNL Flow Service] API](https://www.adobe.io/experience-platform-apis/references/flow-service/).

## Getting started

This guide requires a working understanding of the following components of Adobe Experience Platform:

* [Sources](../../../../home.md): [!DNL Experience Platform] allows data to be ingested from various sources while providing you with the ability to structure, label, and enhance incoming data using [!DNL Platform] services.
* [Sandboxes](../../../../../sandboxes/home.md): [!DNL Experience Platform] provides virtual sandboxes which partition a single [!DNL Platform] instance into separate virtual environments to help develop and evolve digital experience applications.

### Using Platform APIs

For information on how to successfully make calls to Platform APIs, see the guide on [getting started with Platform APIs](../../../../../landing/api-guide.md).

The following section provides additional information that you will need to know in order to successfully connect to [!DNL Snowflake] using the [!DNL Flow Service] API.

### Gather required credentials

In order for [!DNL Flow Service] to connect with [!DNL Snowflake], you must provide the following connection properties:

| Credential | Description |
| --- | --- |
| `account` | The [!DNL Snowflake] account you want to connect to Platform. |
| `warehouse` | The [!DNL Snowflake] warehouse manages the query execution process for the application. Each [!DNL Snowflake] warehouse is independent from one another and must be accessed individually when bringing data over to Platform. |
| `database` | The [!DNL Snowflake] contains the data you want to bring the Platform. |
| `username` | The username for the [!DNL Snowflake] account. |
| `password` | The password for the [!DNL Snowflake] user account. |
| `connectionString` | The connection string used to connect to your [!DNL Snowflake] instance. The connection string pattern for [!DNL Snowflake] is `jdbc:snowflake://{ACCOUNT_NAME}.snowflakecomputing.com/?user={USERNAME}&password={PASSWORD}&db={DATABASE}&warehouse={WAREHOUSE}`. |
| `connectionSpec.id` | The connection specification returns a source’s connector properties, including authentication specifications related to creating the base and source connections. The connection specification ID for [!DNL Snowflake] is `b2e08744-4f1a-40ce-af30-7abac3e23cf3`. |

For more information about getting started, refer to this [[!DNL Snowflake] document](https://docs.snowflake.com/en/user-guide/oauth-custom.html).

## Create a base connection

A base connection retains information between your source and Platform, including your source's authentication credentials, the current state of the connection, and your unique base connection ID. The base connection ID allows you to explore and navigate files from within your source and identify the specific items that you want to ingest, including information regarding their data types and formats.

To create a base connection ID, make a POST request to the `/connections` endpoint while providing your [!DNL Snowflake] authentication credentials as part of the request body.

**API format**

```https
POST /connections
```

**Request**

The following request creates a base connection for [!DNL Snowflake]:

```shell
curl -X POST \
    'https://platform.adobe.io/data/foundation/flowservice/connections' \
    -H 'Authorization: Bearer {ACCESS_TOKEN}' \
    -H 'x-api-key: {API_KEY}' \
    -H 'x-gw-ims-org-id: {IMS_ORG}' \
    -H 'x-sandbox-name: {SANDBOX_NAME}' \
    -H 'Content-Type: application/json' \
    -d '{
        "name": "Snowflake base connection",
        "description": "Snowflake base connection",
        "auth": {
            "specName": "Basic Authentication for Snowflake,
            "params": {
                "connectionString": "{CONNECTION_STRING}"
            }
        },
        "connectionSpec": {
            "id": "b2e08744-4f1a-40ce-af30-7abac3e23cf3",
            "version": "1.0"
        }
    }'
```

| Property | Description |
| -------- | ----------- |
| `auth.params.connectionString` | The connection string used to connect to your [!DNL Snowflake] instance. The connection string pattern for [!DNL Snowflake] is `jdbc:snowflake://{ACCOUNT_NAME}.snowflakecomputing.com/?user={USERNAME}&password={PASSWORD}&db={DATABASE}&warehouse={WAREHOUSE}`. |
| `connectionSpec.id` | The [!DNL Snowflake] connection specification ID: `b2e08744-4f1a-40ce-af30-7abac3e23cf3`. |

**Response**

A successful response returns the newly created connection, including its unique connection identifier (`id`). This ID is required to explore your data in the next tutorial.

```json
{
    "id": "2fce94c1-9a93-4971-8e94-c19a93097129",
    "etag": "\"d403848a-0000-0200-0000-5e978f7b0000\""
}
```

By following this tutorial, you have created a [!DNL Snowflake] connection using the [!DNL Flow Service] API, and have obtained the connection's unique ID value. You can use this connection ID in the next tutorial as you learn how to [explore databases using the Flow Service API](../../explore/database-nosql.md).