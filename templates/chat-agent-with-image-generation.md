# Build an AI chat agent that generates images with Claude, GPT Image 2 and apimodels.app

A chat assistant in n8n's hosted chat that answers questions and draws pictures on request. Claude Haiku 5.5 runs the conversation and a GPT Image 2 tool makes the images, both through one OpenAI-compatible credential.

## Who's it for
Teams and makers who want a single assistant for text and images, and n8n users who want to try many chat and image models without separate accounts.

## How it works
- The Chat node receives messages; a window memory keeps the last 10 turns.
- The AI Agent decides whether to reply in text or call the generate_image tool.
- The tool makes one HTTP request to the image endpoint and gets the image URL back in the same response, so no polling is needed.
- The agent replies with the image inline and a short caption.

## How to set up
1. Create an API key at apimodels.app (new accounts get $0.1 of free credit).
2. Create an OpenAI credential with the key and set Base URL to https://api.apimodels.app/v1.
3. Select it in the Chat model and generate_image nodes, activate, and open the chat URL. Setup takes about 3 minutes.

## Requirements
- An apimodels.app account. Claude Haiku 5.5 is billed per token; GPT Image 2 is $0.025 per 1K image.

## How to customize
- Put any chat model id from GET /v1/models (Claude, GPT, Gemini, DeepSeek, Qwen) in Chat model.
- Change the image model or sizes in generate_image, and the assistant's behaviour in the system message.
