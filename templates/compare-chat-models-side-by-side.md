# Compare answers, speed and cost of Claude, GPT, Gemini, DeepSeek and Qwen side by side with apimodels.app

Type one prompt, pick 2 to 6 chat models, and get every answer on one page with server-measured response time, token counts and the exact amount each call cost.

## Who's it for
Developers and product managers choosing a model for a feature, prompt engineers testing a prompt across vendors, and teams that need numbers before switching models.

## How it works
- An n8n form takes the prompt, an optional system message, the models and an output limit.
- A Code node builds one chat completions request per model, and an HTTP Request node sends them all at the same time.
- Each response carries a request id. The workflow looks each one up in the billing records endpoint to get the exact charge, token usage and start and finish times.
- The result page shows a comparison table, marks the fastest and lowest-cost models, flags answers cut off by the output limit, and shows each full answer. Failed calls appear as failed and are not charged.

## How to set up
1. Create an API key at [apimodels.app](https://apimodels.app) (new accounts get $0.1 of free credit).
2. Add a Bearer Auth credential with the key and select it in the two HTTP Request nodes.
3. Activate the workflow and open the form URL. Setup takes about 3 minutes.

Step-by-step setup guide with screenshots: [Use apimodels in n8n](https://apimodels.app/docs/n8n).

## Requirements
- An apimodels.app account. A five-model comparison on a short prompt usually costs well under $0.01.

## How to customize
- Add any model id from GET /v1/models to the list in **One item per model** and to the form's options.
- Raise the output limit for reasoning models, which spend part of it on thinking.
