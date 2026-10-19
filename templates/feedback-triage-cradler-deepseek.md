# Classify customer feedback with DeepSeek, store it in a free Cradler database and get AI reports

A feedback form for your users and a report page for your team. Every message is classified by an LLM and saved to a free [Cradler](https://cradler.ai) database; the report page has Claude summarise the last 7 or 30 days into themes, urgent issues and suggested actions.

## Who's it for
Product managers, founders and support or community teams who collect feedback and want it sorted and summarised without a spreadsheet or a paid tool.

## How it works
- The feedback form collects the message, product area and an optional email.
- [DeepSeek V4.1 Flash](https://apimodels.app/models/deepseek-v4.1-flash) returns category, sentiment, urgency, a one-line summary, tags and language as JSON.
- The row is saved to a `feedback` table in Cradler, which creates the table and columns on the first write.
- The report form loads the chosen period, counts messages by category, sentiment, urgency and area, and [Claude Sonnet 5.5](https://apimodels.app/models/claude-sonnet-5-5) writes the report, which is shown on the page with its cost.

## How to set up
1. Create an [apimodels.app](https://apimodels.app) API key and add it as a Bearer Auth credential named "apimodels API key".
2. Create a free project at cradler.ai and add its service key as a Bearer Auth credential named "Cradler service key".
3. In Settings, replace YOUR_PROJECT_ID with your Cradler project id, then activate. Setup takes about 5 minutes.

Step-by-step setup guide with screenshots: [Use apimodels in n8n](https://apimodels.app/docs/n8n).

## Requirements
- apimodels.app account (classification costs about $0.0001 per message; a report on a week of feedback was $0.006 in our test).
- Cradler free plan (one project, 300 MB database).

Disclosure: Cradler and apimodels.app are built by the same team.

## How to customize
- Edit categories and urgency rules in Classify feedback, and report sections in Write report.
- Add Slack or email after Save to Cradler for high-urgency alerts, or a Schedule Trigger for weekly reports.
