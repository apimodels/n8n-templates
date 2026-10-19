# Turn YouTube and Bilibili videos into a blog post, X thread and LinkedIn post with Claude via apimodels.app

Paste a YouTube or Bilibili link and get a blog post, an X thread, a LinkedIn post, a newsletter blurb and an optional 16:9 cover, all written from the video's own subtitles. Subtitles, writing and the cover image come from one API key, so there is no separate transcript service.

## Who's it for
Creators, marketers and founders who publish videos and want written versions for their blog, newsletter and social accounts without retyping.

## How it works
- An n8n form takes the video link, output language, tone and whether to make a cover.
- The workflow lists the video's caption tracks, prefers human captions in the spoken language, then downloads and cleans them into plain text.
- Claude Sonnet 5.5 writes every format in one call and returns JSON; it is told to stay faithful to the transcript.
- If requested, GPT Image 2 draws a 16:9 cover with a short headline.
- The result page shows copy-ready boxes, character counts for each post in the thread, and the exact cost of the run. Errors show the provider's own message.

## How to set up
1. Create an API key at apimodels.app (new accounts get $0.1 of free credit).
2. Add a Bearer Auth credential with the key and select it in the three apimodels HTTP Request nodes.
3. Activate the workflow and open the form URL. Setup takes about 5 minutes.

## Requirements
- An apimodels.app account. In our test, a 19-minute video cost $0.063 with a cover (subtitles $0.004, writing $0.031, cover $0.029).
- The video must have subtitles; most YouTube videos have auto-generated ones.

## How to customize
- Change the writing model or transcript limit in **Settings**.
- Edit formats and lengths in the system message of **Write posts**.
