# Create short videos from a photo and a prompt with Seedance 2.0 and apimodels.app

Describe a shot, optionally upload a photo as the first frame, and get a 5 to 15 second video with native sound from ByteDance [Seedance 2.0](https://apimodels.app/models/seedance-2.0), all from an n8n form.

## Who's it for
Marketers, e-commerce teams and creators who want product teasers, social clips or storyboard shots without editing software.

## How it works
- An n8n form collects the prompt, an optional first-frame photo, the Seedance tier (Mini, Fast or standard), resolution, length and aspect ratio.
- If a photo is uploaded, it goes to [apimodels.app](https://apimodels.app) once and is passed on by URL; without one, the video is made from the prompt alone.
- A Code node maps the form to the API fields and only sends 1080p to the tier that supports it.
- The video task runs asynchronously; the workflow checks it every 20 seconds for up to 30 minutes.
- The result page plays the video and shows the real charge. Refusals (for example photos of real people) show the model's own message, and failed tasks are not charged.

## How to set up
1. Create an API key at apimodels.app (new accounts get $0.1 of free credit).
2. Add a Bearer Auth credential with the key and select it in the three HTTP Request nodes.
3. Activate the workflow and open the form URL. Setup takes about 5 minutes.

Step-by-step setup guide with screenshots: [Use apimodels in n8n](https://apimodels.app/docs/n8n).

## Requirements
- An apimodels.app account. Seedance 2.0 is billed per second, from $0.044/s (Mini, 480p).

## How to customize
- Rename tiers or change defaults in **Build request**.
- Change the polling interval or time limit in **Settings**.
- Turn on Basic Auth in the form trigger before sharing the link.
