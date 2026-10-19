# Chat with your CSV and Excel data using Claude and a free Cradler database

Upload a CSV or Excel file and ask questions about it in plain words. The file is loaded into a free [Cradler](https://cradler.ai) database with no schema to design, and an AI agent running [Claude Sonnet 5.5](https://apimodels.app/models/claude-sonnet-5-5) finds the right table, queries it and does the math.

## Who's it for
Founders, operators and analysts who want quick answers from exports (orders, leads, support tickets, survey results) without setting up a database or writing SQL.

## How it works
- The upload form takes a file and a table name. Headers become snake_case columns and each column gets one type: number, true/false or text.
- Rows are inserted in batches of 500, and the table is recorded in a `data_tables` list with its columns and row count.
- In n8n's hosted chat, the agent calls list_tables, then get_table_schema, then query_table with filters, sorting and exact counts, and uses the calculator for sums and averages.
- The chat tools are read-only, and table names are sanitised before they go into a URL.

## How to set up
1. Create a free project at cradler.ai and add its service key as a Bearer Auth credential named "Cradler service key".
2. Create an [apimodels.app](https://apimodels.app) API key and add an OpenAI credential with Base URL https://api.apimodels.app/v1.
3. In Settings, replace YOUR_PROJECT_ID with your Cradler project id, activate, upload a file and open the chat. Setup takes about 5 minutes.

Step-by-step setup guide with screenshots: [Use apimodels in n8n](https://apimodels.app/docs/n8n).

## Requirements
- Cradler free plan and an apimodels.app account. In our test on a 400-row orders file, four questions were all answered correctly in 22 to 95 seconds each.

Disclosure: Cradler and apimodels.app are built by the same team.

## How to customize
- Swap the chat model id (for example deepseek-v4.1-flash for lower cost).
- One query returns up to 1,000 rows, so sums and averages are exact up to that many matching rows; counts are always exact.
