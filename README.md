# Local AI downloads

Local AI is a desktop app that starts a local model with one click, shows it running, and opens your coding agent on it. The recipes it runs come from the [Local AI registry](https://github.com/sybil-solutions/local-ai-registry).

This repository holds the app's releases and nothing else. The download page is [local.sybilsolutions.ai/download](https://local.sybilsolutions.ai/download/).

## Linux and Omarchy

```
curl -fsSL https://local.sybilsolutions.ai/install.sh | bash
```

This installs Local AI for your user as a service that keeps running. On Omarchy it also adds Local AI to the app menu. Run the line again to update.

The line downloads `local-ai-linux.tar.gz` from the newest release here, checks it against `local-ai-linux.tar.gz.sha256`, and runs the `install.sh` inside it. It needs Node.js 20 or newer and fetches its own copy when the machine has none. Starting a model also needs Docker and an NVIDIA GPU.

## Mac

`Local-AI-mac-arm64.dmg` is the app for Apple silicon (macOS 12 or later), signed with a Developer ID and notarized by Apple. Open it and drag Local AI to Applications. Starting a model needs Python 3.11 or newer.

## Files in a release

| file | what it is |
|---|---|
| `Local-AI-mac-arm64.dmg` | the Mac app |
| `local-ai-linux.tar.gz` | the Linux files |
| `local-ai-linux.tar.gz.sha256` | their checksum, which the one-line installer checks |
| `install.sh` | the one-line installer |
| `SHA256SUMS` | the SHA-256 checksum of each file |

The names carry no version, so `releases/latest/download/<name>` always gives the newest.

Copyright © 2026 Sybil Solutions.
