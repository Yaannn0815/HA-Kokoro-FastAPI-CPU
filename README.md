# Kokoro-FastAPI for Home Assistant

This repo contains a Home Assistant app that runs [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI) locally on the Home Assistant host. It is essentially nothing more than a wrapper around the work the FastKoko folks did, with the goal to have the backend running inside Home Assistant.

It works well with the [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS).

## Overview

- Runs the Kokoro-FastAPI CPU image in a Home Assistant app
- Exposes the OpenAI-compatible API on port 8880
- Includes the optional web interface at `/web`
- Maps Home Assistant app options into Kokoro environment variables

## App structure

- [kokoro_fastapi](kokoro_fastapi) — Home Assistant app source
- [repository.yaml](repository.yaml) — repository metadata for Home Assistant
- [LICENSE](LICENSE) — project license

## Installation

1. Open Home Assistant.
2. Go to Settings > Apps > App store.
3. Add this repository as a custom app repository.
4. Install the app and start it.
5. Wait for the model to finish loading.

Once running, the app exposes:

- API: http://HOME_ASSISTANT_IP:8880
- Web UI: http://HOME_ASSISTANT_IP:8880/web
- Docs: http://HOME_ASSISTANT_IP:8880/docs
- Health: http://HOME_ASSISTANT_IP:8880/health

## Example API call

```bash
curl -X POST "http://HOME_ASSISTANT_IP:8880/v1/audio/speech" \
  -H "Content-Type: application/json" \
  -d '{"model":"kokoro","voice":"am_fenrir","input":"Hello from Kokoro","response_format":"mp3"}' \
  --output test.mp3
```

Note: opening `/v1/audio/speech` directly in a browser performs a GET request and returns `Method Not Allowed`. Use the API docs or send a POST request from a tool or script.

## Configuration options

The app supports these Home Assistant options:

- `api_log_level`: Log verbosity (`Debug`, `Info`, `Warning`, `Error`)
- `default_voice`: Default voice used when a request does not specify one
- `enable_web_player`: Enables the Kokoro web interface
- `enable_ssml`: Enables SSML support when set to true

## Local development notes

When testing a manually copied local app, replace the entire `kokoro_fastapi` directory, reload the local app repository, and use Rebuild before starting it again.

The app source in [kokoro_fastapi](kokoro_fastapi) uses the official `ghcr.io/remsky/kokoro-fastapi-cpu:v0.9.0` image for both `amd64` and `aarch64` targets, with a small wrapper that maps Home Assistant app options into Kokoro environment variables.

## Related links

- [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI)
- [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS)
- [Kokoro configuration docs](https://github.com/remsky/Kokoro-FastAPI/blob/master/docs/configuration.md)

## License

This project is licensed under the Apache License, Version 2.0.

This matches the upstream Kokoro-FastAPI project licensing choice and keeps the wrapper app consistent with the upstream server project.
