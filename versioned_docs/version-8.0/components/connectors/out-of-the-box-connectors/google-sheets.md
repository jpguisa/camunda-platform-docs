---
id: google-sheets
title: Google Sheets Connector
sidebar_label: Google Sheets Connector
description: Use the Google Sheets Connector to connect your BPMN service with Google Sheets.
---

The **Google Sheets Connector** is an outbound Connector that allows you to work with an existing or new empty
spreadsheet
on [Google Drive](https://drive.google.com/) and work with it or already existing one from your BPMN process.

## Prerequisites

To start working with the **Google Sheets Connector**, a relevant OAuth token must be configured and stored as a secret
in your cluster. The token must have permission to read/write and create a file from a desired Google Drive instance.
Follow the steps from the [appendix](#appendix--faq) to find out more about creating an OAuth token and giving relevant
permissions.

## Create a Google Sheets Connector task

Currently, the Google Sheets Connector supports next operations:

- [Add values to spreadsheet](#add-values-to-spreadsheet)
- [Create empty column or row](#create-empty-column-or-row)
- [Create row](#create-row)
- [Create spreadsheet](#create-spreadsheet)
- [Create worksheet](#create-worksheet)
- [Delete column](#delete-column)
- [Delete worksheet](#delete-worksheet)
- [Get row by index](#get-row-by-index)
- [Get spreadsheet details](#get-spreadsheet-details)
- [Get worksheet data](#get-worksheet-data)

To use a **Google Sheets Connector** in your process, either change the type of existing task by clicking on it and
using the wrench-shaped **Change type** context menu icon or create a new Connector task by using the **Append Connector
** context menu. Follow our [guide on using Connectors](/components/connectors/use-connectors/index.md) to learn more.

## Make your Google Sheets Connector executable

To make the **Google Sheets Connector** executable, fill out the mandatory fields highlighted in red in the properties
panel.

### Add values to spreadsheet

![Google Sheets Connector add values example](../img/connectors-google-sheets-add-values.png)

To add values, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Add values to Spreadsheet**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which a new
   value will be added.
4. _(optional)_ In the **Operation Details** section, set the field **Worksheet name** to the desired worksheet, in
   which a new value will be added. Keep in mind that if not specified, a new value will be added to the first available
   worksheet in the desired spreadsheet.
5. In the **Operation Details** section, set the field **Cell ID** to the desired cell, in which a new value a new value
   will be added. Use format ColumnRow (for example A1).
6. In the **Operation Details** section, set the field **Value** to the desired value, which will be added in the
   desired cell.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Add values to Spreadsheet**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**

### Create empty column or row

![Google Sheets Connector create empty column or row example](../img/connectors-google-sheets-add-empty-column-or-row.png)

To create empty column or row, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Create empty Column or Row**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which new
   columns/rows will be added.
4. In the **Operation Details** section, set the field **Worksheet ID** to the desired worksheet, in which new
   columns/rows will be added.
5. In the **Operation Details** section, select the Dimension, which will be added.
6. _(optional)_ In the **Operation Details** section, set the both of the **Start index** and **End index** fields, in
   which new columns/rows will be added. Keep in mind that **count starts from 0**. It's possible to leave these fields
   empty. In this case a new column/row will be added in the end of the desired worksheet.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Create empty Column or Row**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**

### Create Row

![Google Sheets Connector create row example](../img/connectors-google-sheets-create-row.png)

To create row, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Create Row**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which a new row
   will be added.
4. _(optional)_ In the **Operation Details** section, set the field **Worksheet name** to the desired worksheet, in
   which a new row will be added. Keep in mind that if not specified, a new row will be added to the first available
   worksheet in the desired spreadsheet.
5. In the **Operation Details** section, set the field **Row index** to the desired row index, where a new row will be
   added. See the [relevant appendix entry](#what-is-a-row-index) to find out more.
6. In the **Operation Details** section, set the field **Enter values** to the desired values, which will be added. This
   property requires FEEL input.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Create Row**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**

### Create spreadsheet

![Google Sheets Connector create spreadsheet example](../img/connectors-google-sheets-create-spreadsheet.png)

To create spreadsheet, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Create Spreadsheet**.
3. _(optional)_ In the **Operation Details** section, set the field **Parent folder ID** to the desired parent, inside
   which a new spreadsheet will be created. Keep in mind that if not specified, a new spreadsheet will be created in the
   Google Drive root folder of a user who owns the OAuth token.
4. In the **Operation Details** section, set the field **Spreadsheet name** to the desired spreadsheet name.

#### Operation response

The following fields are available in the response variable:

- `spreadsheetId` - ID of the newly created spreadsheet.
- `spreadsheetUrl` - Human-readable URL of the newly created spreadsheet.

### Create worksheet

![Google Sheets Connector create worksheet example](../img/connectors-google-sheets-create-worksheet.png)

To create worksheet, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Create Worksheet**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which a new
   worksheet will be created.
4. In the **Operation Details** section, set the field **Worksheet name** to the desired worksheet name.
5. _(optional)_ In the **Operation Details** section, set the field **Worksheet index** to the desired index, in which a
   new worksheet will be created. See the [relevant appendix entry](#what-is-a-worksheet-index) to find out more.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Create Worksheet**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**

### Delete column

![Google Sheets Connector delete column example](../img/connectors-google-sheets-delete-column.png)

To delete column, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Delete Column**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which a colum
   will be deleted.
4. In the **Operation Details** section, set the field **Worksheet ID** to the desired worksheet ID, in which column
   will be deleted.
5. In the **Operation Details** section, select **Index format** of desired index of column to be deleted. See
   the [relevant appendix entry](#how-can-i-define-which-column-will-be-deleted) to find out more.
6. In the **Operation Details** section, set the **Column letter index**, to the desired column index.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Delete Column**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**
-

### Delete worksheet

![Google Sheets Connector delete worksheet example](../img/connectors-google-sheets-delete-worksheet.png)

To delete worksheet, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Delete Worksheet**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, in which a
   worksheet will be deleted.
4. In the **Operation Details** section, set the field **Worksheet ID** to the desired worksheet ID, which will be
   deleted.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Delete Worksheet**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. In this case, it will always be **null**

### Get row by index

![Google Sheets Connector get row by index example](../img/connectors-google-sheets-get-row-by-index.png)

To get row by index, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Get Row by index**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, from which row
   will be retrieved.
4. _(optional)_ In the **Operation Details** section, set the field **Worksheet name** to the desired worksheet, from
   which row will be retrieved. Keep in mind that if not specified, row will be retrieved from the first available
   worksheet in the desired spreadsheet.
5. In the **Operation Details** section, set the field **Row index** to the desired row index. See
   the [relevant appendix entry](#what-is-a-row-index) to find out more.

#### Operation response

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Get Row by index**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. If row is empty, the response is null, else array.

### Get spreadsheet details

![Google Sheets Connector get spreadsheet details example](../img/connectors-google-sheets-get-spreadsheet-details.png)

To get spreadsheet details, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Get Spreadsheet details**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, which details will
   be returned.

#### Operation response

The response contains spreadsheet properties. To see details follow
the [official documentation](https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#spreadsheetproperties)

### Get worksheet data

![Google Sheets Connector get spreadsheet details example](../img/connectors-google-sheets-get-worksheet-data.png)

To get worksheet data, take the following steps:

1. Set the required credentials in the **Authentication** section. See
   the [relevant appendix entry](#how-can-i-authenticate-my-connector) to find out more.
2. In the **Select Operation** section, select **Get Worksheet data**.
3. In the **Operation Details** section, set the field **Spreadsheet ID** to the desired spreadsheet, from which data
   will be retrieved.
4. In the **Operation Details** section, set the field **Worksheet name** to the desired worksheet, from which data will
   be retrieved.

The following fields are available in the response variable:

- `action` - The action performed. In this case, it will always be **Get Worksheet data**
- `status` - The status of the operation. If successful, it will always be "OK". Otherwise, it will be an error message.
- `response` - The response of the operation. If worksheet is empty, the response is null, else array of rows (also
  array)

## Appendix & FAQ

### How can I authenticate my Connector?

The **Google Sheets Connector** currently supports two methods for authentication and authorization: based on
short-lived JWT bearer token, and based on refresh token.

Google supports multiple ways to obtain both. Refer to
the [official Google OAuth documentation](https://developers.google.com/identity/protocols/oauth2) to get up-to-date
instructions or see the examples below.

You also enable _Google Sheets API_ and _Google Drive API_ for every client intended to use. You can do this at
the [Google Cloud API Library](https://console.cloud.google.com/apis/library) page.

#### Example 1: Obtaining JWT bearer token with a service account

![Bearer Auth](../img/connectors-googledrive-jwt-bearer.png)

:::warning
The following code snippet is for demonstration purposes only and must not be used for real production systems due to
security concerns.
For production usage it is highly recommended to follow
the [official Google guideline](https://developers.google.com/identity/protocols/oauth2/service-account).
:::

Assuming you have created a service account and downloaded a JSON file with keys, run the following Python 3 snippet
that prints the JWT token in the terminal:

```python
import google.auth
import google.auth.transport.requests
from google.oauth2 import service_account
# Scopes required to execute 'create' endpoind with Google Sheets API
SCOPES = ['https://www.googleapis.com/auth/drive', 'https://www.googleapis.com/auth/drive.file', 'https://www.googleapis.com/auth/drive.appdata']
# File with keys
SERVICE_ACCOUNT_FILE = 'google-service-account-creds.json'
credentials = service_account.Credentials.from_service_account_file(SERVICE_ACCOUNT_FILE, scopes=SCOPES)
auth_req = google.auth.transport.requests.Request()
credentials.refresh(auth_req)
# Print token
print(credentials.token)
```

#### Example 2: Obtaining bearer and refresh tokens with OAuth client

![Refresh Auth](../img/connectors-googledrive-jwt-refresh.png)

:::warning
The following code snippet is for demonstration purposes only and must not be used for real production systems due to
security concerns.
For production usage it is highly recommended to follow
the [official Google guideline](https://developers.google.com/identity/protocols/oauth2/web-server).
:::

Assuming you have created an OAuth client, you can download key files from the
Google [Console](https://console.cloud.google.com/apis/credentials). Run the following Python 3 snippet that prints the
refresh token in the terminal:

```python
from google_auth_oauthlib.flow import InstalledAppFlow
import pprint

SCOPES = ['https://www.googleapis.com/auth/drive', 'https://www.googleapis.com/auth/spreadsheets']
OAUTH_KEYS = './oauth-keys.json' # path to your file with OAuth credentials

def main():
    flow = InstalledAppFlow.from_client_secrets_file(OAUTH_KEYS, SCOPES)
    creds = flow.run_local_server(port=54948)
    pprint.pprint(vars(creds))

if __name__ == "__main__":
    main()
```

### Where do I get a spreadsheet ID?

It is in the URL.

![Google Sheets Connector get spreadsheet ID](../img/connectors-google-sheets-get-spreadsheet-id.png)

### Where do I get a worksheet ID?

It is in the URL.

![Google Sheets Connector get worksheet ID](../img/connectors-google-sheets-get-worksheet-id.png)

### What is a Worksheet index?

You can define the place where a new worksheet will be created. By default, the new worksheet will be created in the end
of worksheet. Keep in mind, that **count starts from 0**. For instance, in order to create a new worksheet on the second
place, worksheet index should be set as 1.

### What is a Row index?

Row index is the unique identifier for each row in some worksheet, which is used both for reading and writing operations
with row. This index is defined in the left of the row.

![Google Sheets Connector get row index](../img/connectors-google-sheets-row-index.png)

### How can I define which column will be deleted?

There are two ways to define which column will be deleted: by letter index and numeric one. Numeric index can be found
at the top of the column.

![Google Sheets Connector get column letter index](../img/connectors-google-sheets-letter-column-index.png)

The other option is to use numeric index. Keep in mind that **count starts from 0**. In order to delete column A,
numeric index should be 0, B -> 1...
