<p align="center"><strong>Nova CLI</strong> is a coding agent that runs locally on your computer.
<p align="center">
  <img src="https://github.com/xuanlinAI/nova-code/blob/main/.github/nova-cli-splash.png" alt="Nova CLI splash" width="80%" />
</p>
</br>
If you want Nova in your code editor (VS Code, Cursor, Windsurf), <a href="https://developers.openai.com/codex/ide">install in your IDE.</a>
</br>If you want the desktop app experience, run <code>nova app</code> or visit <a href="https://chatgpt.com/codex?app-landing-page=true">the Nova App page</a>.
</p>

---

## Quickstart

### Installing and running Nova CLI

Run the following on Mac or Linux to install Nova CLI:

```shell
curl -fsSL https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.sh | sh
```

Run the following on Windows to install Nova CLI:

```shell
powershell -ExecutionPolicy ByPass -c "irm https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.ps1 | iex"
```

The standalone installers download from GitHub Releases by default. The legacy `releases.openai.com/codex` source is only used when explicitly enabled with `NOVA_INSTALLER_USE_LEGACY_RELEASES_OPENAI_COM=true`.

Nova CLI can also be installed via the following package managers:

```shell
# Install using npm
npm install -g @nova-code/nova
```

```shell
# Install using Homebrew
brew install --cask nova
```

Then simply run `nova` to get started.

<details>
<summary>You can also go to the <a href="https://github.com/xuanlinAI/nova-code/releases/latest">latest GitHub Release</a> and download the appropriate binary for your platform.</summary>

Each GitHub Release contains many executables, but in practice, you likely want one of these:

- macOS
  - Apple Silicon/arm64: `nova-aarch64-apple-darwin.tar.gz`
  - x86_64 (older Mac hardware): `nova-x86_64-apple-darwin.tar.gz`
- Linux
  - x86_64: `nova-x86_64-unknown-linux-musl.tar.gz`
  - arm64: `nova-aarch64-unknown-linux-musl.tar.gz`

Each archive contains a single entry with the platform baked into the name (e.g., `nova-x86_64-unknown-linux-musl`), so you likely want to rename it to `nova` after extracting it.

</details>

### Using Nova with your ChatGPT plan

Run `nova` and select **Sign in with ChatGPT**. We recommend signing into your ChatGPT account to use Nova as part of your Plus, Pro, Business, Edu, or Enterprise plan. [Learn more about what's included in your ChatGPT plan](https://help.openai.com/en/articles/11369540-codex-in-chatgpt).

You can also use Nova with an API key, but this requires [additional setup](https://developers.openai.com/codex/auth#sign-in-with-an-api-key).

## Docs

- [**Nova Documentation**](https://developers.openai.com/codex)
- [**Contributing**](./docs/contributing.md)
- [**Installing & building**](./docs/install.md)
- [**Open source fund**](./docs/open-source-fund.md)

This repository is licensed under the [Apache-2.0 License](LICENSE).
