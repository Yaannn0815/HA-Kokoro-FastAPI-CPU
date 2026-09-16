# Kokoro-FastAPI Backend for Home Assistant

This Home Assistant app runs the [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI) text-to-speech server locally on the Home Assistant host. It is essentially nothing more than a wrapper around the work the FastKoko folks did, with the goal to have the backend running inside Home Assistant.

It works well alongside the [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS).

## Usage

1. If not already done in HA, add `https://github.com/remsky/Kokoro-FastAPI` to **Settings > Apps > App store > Repositories**.
2. Install **Kokoro-FastAPI (CPU)**.
3. Start the app and wait for the model to finish loading.
4. Add and configure the [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS).

Click **Open Web UI** (above), or open `http://HOME_ASSISTANT_IP:8880/web/` to play around with the Kokoro-FastAPI backend.

The Kokoro web player is available from the app's **Open Web UI** link.

## Settings

- **API Log Level**: Choose how much detail Kokoro writes to the app log. Options are `Debug`, `Info`, `Warning`, and `Error`.
- **Default Voice**: Default Kokoro voice identifier. Use the **Open Web UI** link to browse and preview voices.
- **Enable Web UI**: Serve Kokoro's browser-based web interface at `http://HOME_ASSISTANT_IP:8880/web/`.
- **Support SSML**: Enable Speech Synthesis Markup Language, including pauses and other supported speech controls.

The app supports Home Assistant `amd64` and `aarch64` installations (CPU-only).

## Related links

- [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI)
- [Kokoro TTS HACS integration](https://github.com/beecho01/Kokoro-TTS)
