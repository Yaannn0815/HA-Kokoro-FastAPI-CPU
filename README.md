# Kokoro-FastAPI for Home Assistant

This repo contains a Home Assistant app that runs [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI) locally on the Home Assistant host. It is essentially a wrapper around the upstream server, with the goal of running the backend inside Home Assistant.

It works well with the [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS).

## Usage

1. Add this repository (`https://github.com/remsky/Kokoro-FastAPI`) to **Settings > Apps > App store > Repositories**.
2. Install **Kokoro-FastAPI (CPU)**.
3. Start the app and wait for the model to finish loading.
4. Add and configure the [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS).

Click **Open Web UI** on the app page, or open `http://HOME_ASSISTANT_IP:8880/web/` to browse the Kokoro web interface.

## Settings

- **API Log Level**: Choose how much detail Kokoro writes to the app log. Options are `Debug`, `Info`, `Warning`, and `Error`.
- **Default Voice**: Default Kokoro voice identifier. Use the **Open Web UI** link to browse and preview voices.
- **Enable Web UI**: Serve Kokoro's browser-based web player at `/web` on port `8880`.
- **Support SSML**: Enable Speech Synthesis Markup Language, including pauses and other supported speech controls.

The app supports Home Assistant `amd64` and `aarch64` installations (CPU-only).

## Related links

- [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI)
- [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS)
- [Kokoro configuration docs](https://github.com/remsky/Kokoro-FastAPI/blob/master/docs/configuration.md)

## License

This project is licensed under the Apache License, Version 2.0.

This matches the upstream Kokoro-FastAPI project licensing choice and keeps the wrapper app consistent with the upstream server project.
