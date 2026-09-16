<p align="center"><strong>Nova CLI</strong> is a coding agent that runs locally on your computer, powered by any OpenAI-compatible model provider (DeepSeek, Moonshot, Ollama, ...).</p>
<p align="center">
  <img src="https://github.com/xuanlinAI/nova-code/blob/main/.github/nova-cli-splash.png" alt="Nova CLI splash" width="80%" />
</p>
</br>

---

## Quickstart

### Installing Nova CLI

Run the following on Windows to install Nova CLI:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.ps1 | iex"
```

On macOS or Linux:

```shell
curl -fsSL https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.sh | sh
```

The installers download from GitHub Releases and install to a per-user location (no admin rights needed).

> **Platform status** — v0.1.0 ships Windows x64 binaries. macOS / Linux / Windows ARM64 packages are not published yet; build from source in the meantime (see [Installing & building](./docs/install.md)).

### First run

No interactive menus. Nova walks you through a guided setup:

1. Enter your provider API URL (e.g. `https://api.deepseek.com`)
2. Enter your API key
3. Nova tests connectivity and fetches the provider's available model list automatically
4. Pick your default model — done

Nova works with any provider exposing an OpenAI-compatible `/models` endpoint and a Responses or Chat Completions wire API. Switch models anytime with `/model` in the TUI; the picker always shows your provider's live model list, not a hardcoded catalog.

Then simply run `nova` to get started.

## Docs

- [**Contributing**](./docs/contributing.md)
- [**Installing & building**](./docs/install.md)
- [**Configuration**](./docs/config.md)
- [**Slash commands**](./docs/slash_commands.md)

This repository is licensed under the [Apache-2.0 License](LICENSE).
