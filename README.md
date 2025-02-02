# bigquery-jupyter-integration

## Overview
This Python script provides functionality to authenticate a Google Cloud service account, interact with Google BigQuery, and execute a query on a specified dataset. It retrieves data from a BigQuery table, converts the results into a Pandas DataFrame, and displays the first 10 rows.

## Prerequisites

Before running this script, ensure you have the following:

1. **Python 3.x**: The script is written in Python.
2. **Required Libraries**:
   The following libraries are necessary for the script to function:
   - `google-auth`
   - `google-auth-oauthlib`
   - `google-auth-httplib2`
   - `google-api-python-client`
   - `google-cloud-bigquery`
   - `db-dtypes`
   - `pandas`

   You can install these dependencies by running the following command:
   ```bash
   pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client google-cloud-bigquery db-dtypes pandas
   ```

3. **Google Cloud Project**: You need a Google Cloud Project with BigQuery access and the appropriate service account credentials.

4. **Service Account JSON Key**: Ensure you have a Google Cloud service account key in JSON format to authenticate the script.

## Setup

1. **Service Account Key**:
   Download your service account credentials as a JSON file and place it on your local machine. Update the `KEY_PATH` variable in the script to point to your credentials file:
   ```python
   KEY_PATH = r"C:\path\to\your\service-account-file.json"
   ```

2. **BigQuery Dataset**:
   Modify the `dataset_id` variable to point to the desired dataset in your Google Cloud BigQuery project:
   ```python
   dataset_id = 'your_project_id.your_dataset_name'
   ```

3. **SQL Query**:
   The script is set to query a table named `sachin ODI` in the dataset. If you need to change the table or query, modify the `query` variable:
   ```python
   query = """
   SELECT *
   FROM `your_project_id.your_dataset_name.your_table_name`
   LIMIT 10
   """
   ```

## How it Works

1. **Authentication**: The script uses the `service_account.Credentials` class to authenticate your service account and obtain the credentials.
2. **BigQuery Client**: It initializes a BigQuery client using the authenticated credentials.
3. **Dataset Reference**: It fetches a reference to the dataset specified in the `dataset_id` variable.
4. **List Tables**: It lists all tables available in the specified dataset and prints their names.
5. **Execute Query**: A query is run on the specified table (default: `sachin ODI`), and the results are retrieved.
6. **Display Results**: The results are converted into a Pandas DataFrame and the first 10 rows are displayed.

## Example Output

Once the script runs successfully, it will display the table names from your dataset and print the first 10 rows of the query result.

```text
Table name: sachin ODI
Table name: another_table
...
   column1 column2 column3
0   value1 value2 value3
1   value4 value5 value6
...
```

## Troubleshooting

- **Invalid Credentials**: Ensure your service account JSON file is correctly located at `KEY_PATH` and that the credentials are valid.
- **Access Issues**: Ensure your Google Cloud project has the necessary permissions to access BigQuery and that the service account has the appropriate roles assigned.
