<p align="center"><strong>Nova CLI</strong> is a coding agent that runs locally on your computer.</p>
<p align="center">
  <img src="https://github.com/xuanlinAI/nova-code/blob/main/.github/nova-cli-splash.png" alt="Nova CLI splash" width="80%" />
</p>
</br>

Nova Code is a fork of [OpenAI Codex CLI](https://github.com/openai/codex). It is developed on top of Codex; the changes made in this fork are listed below.

---

## Changes from Codex

### Model providers

- Provider setup is a guided flow: enter the endpoint URL, enter the API key, Nova tests connectivity, fetches the model list from the provider's `/models` endpoint, and the user picks a default model (`nova-rs/cli/src/setup.rs`).
- Model selection is not limited to a bundled catalog. Any provider exposing an OpenAI-compatible `/models` endpoint can be configured, and the picker shows the list returned by that provider (`nova-rs/nova-api/src/endpoint/models.rs`, `nova-rs/models-manager/src/manager.rs`).
- Added a `Chat` wire API alongside `Responses`, selected automatically when the provider does not serve `/responses` (`nova-rs/model-provider-info/src/lib.rs`).
- The first interactive run without a configured provider enters the setup flow instead of an account sign-in menu (`nova-rs/cli/src/main.rs`).
- Reasoning-effort levels are probed against the provider before being applied. A level the provider rejects falls back to `High` and reports the rejection (`nova-rs/model-provider/src/reasoning_probe.rs`).
- Models discovered from a provider expose a seven-level effort ladder: `None`, `Low`, `Medium`, `High`, `Extra high`, `Max`, `Ultra` (`nova-rs/tui/src/chatwidget/model_popups.rs`).
- Removed the `update` and `cloud` subcommands. No subcommands were added.

### System prompt

- Replaced with nine modular templates under `nova-rs/prompts/templates/system/` (`identity`, `personality`, `execution`, `capabilities`, `delegation`, `memory_policy`, `scratchpad_policy`, `quality_speed`, `guardrails`), assembled per session (`nova-rs/prompts/src/system_prompt.rs`, version `3.1.0`).
- The `{{nova_system_prompt}}` placeholder is substituted into model instruction templates (`nova-rs/core/src/system_prompt.rs`).

### Tools added under the `nova` namespace

| Tool | Purpose |
| --- | --- |
| `nova.worker_call` | Invoke an external worker process |
| `nova.worker_status` | Report worker state |
| `nova.worker_stop` | Stop a worker |
| `nova.scratchpad` | Global scratchpad shared across the session |
| `nova.ctc` | Context trash can: archive and retrieve large tool outputs |
| `nova.fleet_run` | Run N sub-agent tasks in parallel with an optional output JSON Schema |
| `nova.ps` | Unified process view over agents and workers |
| `nova.mind` | Per-thread persistent working-state file |
| `nova.memory` | Read and write the on-disk memory store |
| `nova.save_skill` | Write a reusable workflow into `NOVA_HOME/skills` |

### Workers

- New `nova-workers` crate (`nova-rs/workers/`) holding worker processes that outlive the turn that started them.
- New `[workers.<id>]` config table (`nova-rs/config/src/config_toml.rs`).

### Context and memory

- Context trash can: tool output over 8 KB is archived to `~/.nova/compaction/<thread-id>/entries.jsonl` with an index in `ctc-index.md` (`nova-rs/core/src/context_trash_can.rs`).
- Auto-memory: markdown memory files with YAML frontmatter and a per-scope `MEMORY.md` index, injected into the session (`nova-rs/core/src/session/auto_memory.rs`).
- Context window handling: warning at 85% used, forced compaction at 95%, `NOVA_DISABLE_AUTO_COMPACT` disables automatic compaction (`nova-rs/core/src/session/turn.rs`).
- `tools.repeat_tool_reminder` config: detects repeated identical tool calls and issues a reminder (`nova-rs/core/src/tools/repeat_tool_reminder.rs`).

### Other

- Home directory is `~/.nova` instead of `~/.codex`.
- All crates renamed from `codex-*` to `nova-*`; `codex-rs/` renamed to `nova-rs/`.
- Config and telemetry keys renamed: `codex_git_commit` → `nova_git_commit`, `codex.feature.state` → `nova.feature.state`.
- TUI strings and frames renamed to Nova Code.

## Supported platforms

Windows x64.

macOS, Linux, and Windows ARM64 builds are not published. Building from source is possible; see [Installing & building](./docs/install.md).

## Installing

### npm

```shell
npm install -g @xuanlinai/nova-code
```

### Standalone installer

Windows:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.ps1 | iex"
```

macOS / Linux:

```shell
curl -fsSL https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.sh | sh
```

The standalone installers download a package from GitHub Releases. Only the Windows x64 package is published, so these installers do not currently succeed on other platforms.

## First run

Nova walks through a guided setup:

1. Enter the provider API URL (for example `https://api.deepseek.com`)
2. Enter the API key
3. Nova tests connectivity and fetches the provider's model list
4. Pick the default model

Models can be changed later with `/model` in the TUI. Reasoning effort can be changed in the same picker, or stepped with `Alt+,` and `Alt+.`.

## Docs

- [**Contributing**](./docs/contributing.md)
- [**Installing & building**](./docs/install.md)
- [**Configuration**](./docs/config.md)
- [**Slash commands**](./docs/slash_commands.md)

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
