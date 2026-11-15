# Local AI downloads

Local AI is a desktop app that starts a local model with one click, shows it running, and opens your coding agent on it. The recipes it runs come from the [Local AI registry](https://github.com/sybil-solutions/local-ai-registry).

This repository holds the app's releases and nothing else. The download page is [local.sybilsolutions.ai/download](https://local.sybilsolutions.ai/download/).

## Linux and Omarchy

```
curl -fsSL https://local.sybilsolutions.ai/install.sh | bash
```

This installs Local AI for your user as a service that keeps running, and adds Local AI to the app menu (on Omarchy as an app window of its own, on any other desktop it opens the page in your browser). Run the line again to update.

The line downloads `local-ai-linux.tar.gz` from the newest release here, checks it against `local-ai-linux.tar.gz.sha256`, and runs the `install.sh` inside it. It needs Node.js 20 or newer and fetches its own copy when the machine has none. Starting a model also needs Docker and an NVIDIA GPU.

## Mac

Download [`Local-AI-mac-arm64.dmg`](https://local.sybilsolutions.ai/download/mac), open it and drag Local AI to Applications. It is for Apple silicon (macOS 12 or later), signed with a Developer ID and notarized by Apple. Starting a model needs Python 3.11 or newer.

## Windows

Download [`Local-AI-windows-x64.exe`](https://local.sybilsolutions.ai/download/windows) and run it. It is for 64-bit Windows 10 or 11, installs for your account (no administrator needed) and adds Local AI to the Start menu. It is not signed yet, so Windows asks before it runs: choose More info, then Run anyway. Starting a model needs Docker Desktop and an NVIDIA GPU.

## Files in a release

| file | what it is |
|---|---|
| `Local-AI-mac-arm64.dmg` | the Mac app |
| `Local-AI-windows-x64.exe` | the Windows installer |
| `local-ai-linux.tar.gz` | the Linux files |
| `local-ai-linux.tar.gz.sha256` | their checksum, which the one-line installer checks |
| `install.sh` | the one-line installer |
| `SHA256SUMS` | the SHA-256 checksum of each file |

The names carry no version, so `releases/latest/download/<name>` always gives the newest.

## How a release is checked

A new version is uploaded as a pre-release. The [Check a release](.github/workflows/check.yml) workflow then downloads its files on a Windows, a macOS and a Linux machine, checks each against `SHA256SUMS`, installs it, starts it and asks its server what it sees. Only when all three work is the version made the newest release, which is the one the download page leads to. Those machines have no GPU, so the Windows check gives the app a stand-in `nvidia-smi`; starting a model is not part of the check.

Copyright © 2026 Sybil Solutions.
