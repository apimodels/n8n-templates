# Turn product photos into ad images with GPT Image 2 and apimodels.app

Turn one plain product photo into an ad-ready image in about a minute. Upload the photo in an n8n form, pick a scene, and GPT Image 2 places the product in that scene while keeping its shape, colors, logo and printed text unchanged.

## Who's it for
Online store owners, marketers and agencies who need catalog, lifestyle or social images without a photo shoot.

## How it works
- An n8n form collects the photo, product name, scene, aspect ratio, resolution and optional instructions.
- The photo is uploaded to apimodels.app once and passed on by URL.
- A Code node turns the scene into a prompt that tells the model to keep the product as it is.
- GPT Image 2 runs as an async task; the workflow checks it every 15 seconds.
- The result page shows the image, a download link and the amount actually charged. If the model refuses or fails, its own message is shown, and failed tasks are not charged.

## How to set up
1. Create an API key at apimodels.app (new accounts get $0.1 of free credit).
2. Add a Bearer Auth credential with the key and select it in the three HTTP Request nodes.
3. Activate the workflow and open the form URL. Setup takes about 5 minutes.

## Requirements
- An apimodels.app account. GPT Image 2 costs $0.025 / $0.03 / $0.05 per image at 1K / 2K / 4K.

## How to customize
- Add scenes in **Build prompt** and in the form's Scene list.
- Change the model, polling interval or time limit in **Settings**.
- Turn on Basic Auth in the form trigger before sharing the link.
