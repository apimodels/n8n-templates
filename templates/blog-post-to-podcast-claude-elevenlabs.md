# Convert blog posts into podcast audio with Claude and ElevenLabs via apimodels.app

Paste an article link or its text and get a narrated podcast episode as an MP3. Claude Sonnet 5.5 rewrites the article as a spoken script and ElevenLabs v4 reads it, both through one API key.

## Who's it for
Bloggers, newsletter writers and content teams who want an audio version of each post without recording it.

## How it works
- An n8n form takes an article URL or pasted text, a voice, a style and a target length (about 1, 3 or 5 minutes).
- If only a URL is given, the page is fetched and the main article text is extracted. The fetch sends no credentials.
- Claude writes a script for one host that stays faithful to the source.
- ElevenLabs v4 turns the script into speech, and the MP3 is uploaded to get a shareable link.
- The result page plays the episode and shows the script, the charged cost of the script and an estimate for the voice. Errors show the provider's own message.

## How to set up
1. Create an API key at apimodels.app (new accounts get $0.1 of free credit).
2. Add a Bearer Auth credential with the key and select it in the three apimodels HTTP Request nodes.
3. Activate the workflow and open the form URL. Setup takes about 5 minutes.

## Requirements
- An apimodels.app account. ElevenLabs v4 costs $0.08 per 1,000 characters; a 1-minute episode is about $0.08 in total.

## How to customize
- Change the script model, voice model or estimate price in **Settings**.
- Edit voices, styles and lengths in **Prepare input**. Any voice id from GET /v1/voices works.
