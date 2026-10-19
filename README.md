# n8n templates for apimodels.app

Ready-to-import [n8n](https://n8n.io) workflows that generate images, video, speech and chat with one API key from [apimodels.app](https://apimodels.app), an OpenAI-compatible API for 150+ image, video, audio and language models. Each workflow uses only core n8n nodes (no community nodes), includes sticky-note instructions, and was run end to end before publishing.

Maintained by the apimodels.app team.

| Template | What it does | Models | Typical run |
|---|---|---|---|
| [Product photo to ad image](templates/product-photo-to-ad-image-gpt-image-2.md) | n8n form: upload a product photo, pick a scene, get an ad-ready image with the product unchanged | GPT Image 2 | 1K about 30 s, 2K about 2 min |
| [Photo to short video](templates/photo-to-short-video-seedance-2.md) | n8n form: prompt plus optional first-frame photo to a 5–15 s video with sound | Seedance 2.0 Mini / Fast / standard | 5 s Mini 480p about 2–3 min |
| [Blog post to podcast](templates/blog-post-to-podcast-claude-elevenlabs.md) | n8n form: article URL or text to a narrated MP3 episode | Claude Sonnet 5.5 + ElevenLabs v4 | 1-minute episode about 40 s |
| [Chat agent with image tool](templates/chat-agent-with-image-generation.md) | Hosted chat: an AI agent that answers and draws on request | Claude Haiku 5.5 + GPT Image 2 | Image reply about 1–2 min |

Timings come from our own test runs on n8n 2.43.8 on 2026-10-19. Prices are on each model's page at apimodels.app; failed generations are not charged.

## Import a template

1. Download a `.json` file from [`templates/`](templates).
2. In n8n, open a new workflow, click the `...` menu and choose **Import from File** (or paste the JSON onto the canvas).
3. Add your credential (below), select it in the nodes marked with a credential warning, and activate the workflow.

## Credentials

Create an API key in the [apimodels console](https://apimodels.app/console/api-keys). New accounts get $0.1 of free credit.

- **Form templates** (image, video, podcast) use a **Bearer Auth** credential: paste the key as the token.
- **Chat agent** uses an **OpenAI** credential: paste the key and set **Base URL** to `https://api.apimodels.app/v1`. The same credential works in any OpenAI Chat Model or AI Agent node, so you can run Claude, GPT, Gemini, DeepSeek or Qwen in n8n by changing the model id.

## Screenshots

**Product photo to ad image**: workflow, form and result page

![Product photo to ad image workflow](images/product-photo-to-ad-image-workflow.png)

<img src="images/product-photo-to-ad-image-form.png" alt="Form for the product photo template" width="420"> <img src="images/product-photo-to-ad-image-result.png" alt="Result page with the generated ad image and the charged amount" width="420">

**Photo to short video**

![Photo to short video workflow](images/photo-to-short-video-workflow.png)

**Blog post to podcast**

![Blog post to podcast workflow](images/blog-post-to-podcast-workflow.png)

<img src="images/blog-post-to-podcast-result.png" alt="Result page with the audio player, costs and script" width="420">

**Chat agent with image tool**

![Chat agent workflow](images/chat-agent-image-tool-workflow.png)

<img src="images/chat-agent-image-tool-chat.png" alt="n8n hosted chat showing a generated poster inline" width="420">

## How the media workflows handle async jobs

Image and video models run as tasks. The form templates create a task, then loop through **Wait → Check task status → Route by status** until the task is `completed` or `failed`, with a limit in **Settings**. The result page reads the charge from the task itself (`data.credits`), and `GET /v1/records/{task_id}` returns the same amount later for bookkeeping. For a single request that returns the image directly, as the chat agent's tool does, send an OpenAI-style `size` without `callback_url` to `POST /v1/images/generations`.

More: [API docs](https://apimodels.app/docs) · [n8n guide](https://apimodels.app/docs/n8n) · [All models](https://apimodels.app/models)

## License

MIT
