---
keywords: Experience Platform;home;popular topics;cloud storage;Cloud storage
solution: Experience Platform
title: Explore a cLoud Storage System Using the Flow Service API
topic-legacy: overview
description: This tutorial uses the Flow Service API to explore a third-party cloud storage system.
exl-id: ba1a9bff-43a6-44fb-a4e7-e6a45b7eeebd
---
# Explore a cloud storage system using the [!DNL Flow Service] API

This tutorial uses the [[!DNL Flow Service] API](https://www.adobe.io/experience-platform-apis/references/flow-service/) to explore a third-party cloud storage system.

## Getting started

This guide requires a working understanding of the following components of Adobe Experience Platform:

* [Sources](../../../home.md): [!DNL Experience Platform] allows data to be ingested from various sources while providing you with the ability to structure, label, and enhance incoming data using [!DNL Platform] services.
* [Sandboxes](../../../../sandboxes/home.md): [!DNL Experience Platform] provides virtual sandboxes which partition a single [!DNL Platform] instance into separate virtual environments to help develop and evolve digital experience applications.

The following sections provide additional information that you will need to know in order to successfully connect to a cloud storage system using the [!DNL Flow Service] API.

### Obtain a connection ID

In order to explore a third party cloud storage using [!DNL Platform] APIs, you must possess a valid connection ID. If you do not already have a connection for the storage you wish to work with, you can create one through the following tutorials:

* [[!DNL Amazon S3]](../create/cloud-storage/s3.md)
* [[!DNL Azure Blob]](../create/cloud-storage/blob.md)
* [[!DNL Azure Data Lake Storage Gen2]](../create/cloud-storage/adls-gen2.md)
* [[!DNL Azure File Storage]](../create/cloud-storage/azure-file-storage.md)
* [[!DNL FTP]](../create/cloud-storage/ftp.md)
* [[!DNL Google Cloud Storage]](../create/cloud-storage/google.md)
* [HDFS](../create/cloud-storage/hdfs.md)
* [[!DNL Oracle Object Storage]](../create/cloud-storage/oracle-object-storage.md)
* [[!DNL SFTP]](../create/cloud-storage/sftp.md)

### Reading sample API calls

This tutorial provides example API calls to demonstrate how to format your requests. These include paths, required headers, and properly formatted request payloads. Sample JSON returned in API responses is also provided. For information on the conventions used in documentation for sample API calls, see the section on [how to read example API calls](../../../../landing/troubleshooting.md#how-do-i-format-an-api-request) in the [!DNL Experience Platform] troubleshooting guide.

### Gather values for required headers

In order to make calls to [!DNL Platform] APIs, you must first complete the [authentication tutorial](https://www.adobe.com/go/platform-api-authentication-en). Completing the authentication tutorial provides the values for each of the required headers in all [!DNL Experience Platform] API calls, as shown below:

* `Authorization: Bearer {ACCESS_TOKEN}`
* `x-api-key: {API_KEY}`
* `x-gw-ims-org-id: {IMS_ORG}`

All resources in [!DNL Experience Platform], including those belonging to [!DNL Flow Service], are isolated to specific virtual sandboxes. All requests to [!DNL Platform] APIs require a header that specifies the name of the sandbox the operation will take place in:

* `x-sandbox-name: {SANDBOX_NAME}`

All requests that contain a payload (POST, PUT, PATCH) require an additional media type header:

* `Content-Type: application/json`

## Explore your cloud storage

Using the connection ID for your cloud storage, you can explore files and directories by performing GET requests. When performing GET requests to explore your cloud storage, you must include the query parameters that are listed in the table below:

| Parameter | Description |
| --------- | ----------- |
| `objectType` | The type of object that you wish to explore. Set this value as either: <ul><li>`folder`: Explore a specific directory</li><li>`root`: Explore the root directory.</li></ul> |
| `object` | This parameter is required only when viewing a specific directory. Its value represents the path of the directory you wish to explore. |

Use the following call to find the path of the file you wish to bring into [!DNL Platform]:

**API format**

```http
GET /connections/{CONNECTION_ID}/explore?objectType=root
GET /connections/{CONNECTION_ID}/explore?objectType=folder&object={PATH}
```

| Parameter | Description |
| --- | --- |
| `{CONNECTION_ID}` | The connection ID for your cloud storage source connector. |
| `{PATH}` | The path of a directory. |

**Request**

```shell
curl -X GET \
    'http://platform.adobe.io/data/foundation/flowservice/connections/{CONNECTION_ID}/explore?objectType=folder&object=/some/path/' \
    -H 'Authorization: Bearer {ACCESS_TOKEN}' \
    -H 'x-api-key: {API_KEY}' \
    -H 'x-gw-ims-org-id: {IMS_ORG}' \
    -H 'x-sandbox-name: {SANDBOX_NAME}'
```

**Response**

A successful response returns an array of files and folders found within the queried directory. Take note of the `path` property of the file you wish you upload, as you are required to provide it in the next step to inspect its structure.

```json
[
    {
        "type": "file",
        "name": "account.csv",
        "path": "/test-connectors/testFolder-fileIngestion/account.csv",
        "canPreview": true,
        "canFetchSchema": true
    },
    {
        "type": "file",
        "name": "profileData.json",
        "path": "/test-connectors/testFolder-fileIngestion/profileData.json",
        "canPreview": true,
        "canFetchSchema": true
    },
    {
        "type": "file",
        "name": "sampleprofile--3.parquet",
        "path": "/test-connectors/testFolder-fileIngestion/sampleprofile--3.parquet",
        "canPreview": true,
        "canFetchSchema": true
    }
]
```

## Inspect the structure of a file

To inspect the structure of data file from your cloud storage, perform a GET request while providing the file's path and type as a query parameter.

You can inspect the structure of a data file from your cloud storage source by performing a GET request while providing the file's path and type. You can also inspect different file types such as CSV, TSV, or compressed JSON and delimited files by specifying their file types as part of the query parameters.

**API format**

```http
GET /connections/{CONNECTION_ID}/explore?objectType=file&object={FILE_PATH}&fileType={FILE_TYPE}&{QUERY_PARAMS}&preview=true
GET /connections/{CONNECTION_ID}/explore?objectType=file&object={FILE_PATH}&preview=true&fileType=delimited&columnDelimiter=\t
GET /connections/{CONNECTION_ID}/explore?objectType=file&object={FILE_PATH}&preview=true&fileType=delimited&compressionType=gzip;
```

| Parameter | Description |
| --------- | ----------- |
| `{CONNECTION_ID}` | The connection ID of your cloud storage source connector. |
| `{FILE_PATH}` | The path to the file you want to inspect. |
| `{FILE_TYPE}` | The type of the file. Supported file types include:<ul><li><code>DELIMITED</code>: Delimiter-separated value. DSV files must be comma-separated.</li><li><code>JSON</code>: JavaScript Object Notation. JSON files must be XDM compliant</li><li><code>PARQUET</code>: Apache Parquet. Parquet files must be XDM compliant.</li></ul> |
| `{QUERY_PARAMS}` | Optional query parameters that can be used to filter results. See the section on [query parameters](#query) for more information. |

**Request**

```shell
curl -X GET \
    'http://platform.adobe.io/data/foundation/flowservice/connections/{CONNECTION_ID}/explore?objectType=file&object=/aep-bootcamp/Adobe%20Pets%20Customer%2020190801%20EXP.json&fileType=json&preview=true' \
    -H 'Authorization: Bearer {ACCESS_TOKEN}' \
    -H 'x-api-key: {API_KEY}' \
    -H 'x-gw-ims-org-id: {IMS_ORG}' \
    -H 'x-sandbox-name: {SANDBOX_NAME}'
```

**Response**

A successful response returns the structure of the queried file including table names and data types.

```json
[
    {
        "name": "Id",
        "type": "String"
    },
    {
        "name": "FirstName",
        "type": "String"
    },
    {
        "name": "LastName",
        "type": "String"
    },
    {
        "name": "Email",
        "type": "String"
    },
    {
        "name": "Phone",
        "type": "String"
    }
]
```

## Using query parameters {#query}

The [[!DNL Flow Service] API](https://www.adobe.io/experience-platform-apis/references/flow-service/) supports the use of query parameters to preview and inspect different file types.

| Parameter | Description |
| --------- | ----------- |
| `columnDelimiter` | The single character value you specified as a column delimiter to inspect CSV or TSV files. If the parameter is unprovided, the value defaults to a comma `(,)`. |
| `compressionType` | A required query parameter for previewing a compressed delimited or JSON file. The supported compressed files are: <ul><li>`bzip2`</li><li>`gzip`</li><li>`deflate`</li><li>`zipDeflate`</li><li>`tarGzip`</li><li>`tar`</li></ul> |

## Next steps

By following this tutorial, you have explored your cloud storage system, found the path of the file you wish to bring in to [!DNL Platform], and viewed its structure. You can use this information in the next tutorial to [collect data from your cloud storage and bring it into Platform](../collect/cloud-storage.md).
