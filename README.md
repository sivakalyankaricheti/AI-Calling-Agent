# AI Calling Agent

AI Calling Agent is a browser-based calling workspace with an outbound dialer, incoming call handling, call controls, monitoring, noise cancellation, and an AI voice assistant.

## Features

- Make and receive browser calls
- Transfer, hold, mute, and manage conference participants
- Monitor call quality and errors
- Connect an outbound caller to an OpenAI-powered voice assistant
- Enable RNNoise or Krisp noise cancellation

## Local setup

1. Install Node.js 22 or later.
2. Run `npm ci`.
3. Copy `example.env` to `.env` and set every value. Keep `.env` out of Git.
4. Run `npm start`, then open [http://localhost:3030](http://localhost:3030).

## Deploy to Render

This repository includes `render.yaml` and a Dockerfile. In Render, select **New +** → **Blueprint**, connect the `sivakalyankaricheti/AI-Calling-Agent` repository, and create the service. Set all requested secret environment variables during setup.

After Render assigns a public HTTPS host:

1. Set `CALLBACK_BASE_URL` to the host only, for example `ai-calling-agent.onrender.com` (without `https://`).
2. In the telephony provider console, set your Voice Request URL to the feature endpoint you will use, for example `https://your-host/twilio-voice-ai-conversation/twiml`.
3. Redeploy after changing `CALLBACK_BASE_URL`.

The service health endpoint is `/health`; the live homepage lists the available tools.

## Required environment variables

`ACCOUNT_SID`, `API_KEY_SID`, `API_KEY_SECRET`, `APP_SID`, `AUTH_TOKEN`, `CALLER_ID`, `CALLBACK_BASE_URL`, `DEFAULT_IDENTITY`, and `OPENAI_API_KEY`.

The Krisp option requires its proprietary SDK files and models in `src/components/twilio-voice-krisp-noise-cancellation/public/krisp/`; see that folder's README.
