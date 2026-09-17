<p align="center"><strong>Nova CLI</strong></p>

Nova Code 是基于 [OpenAI Codex CLI](https://github.com/openai/codex) 二次开发的项目。

Nova Code is a fork of [OpenAI Codex CLI](https://github.com/openai/codex).

## 支持平台 / Supported platforms

Windows x64。

Windows x64.

macOS、Linux、Windows ARM64 暂未发布。

macOS, Linux and Windows ARM64 are not published.

## 安装 / Installing

### npm

```shell
npm install -g @xuanlinai/nova-code
```

### 独立安装器 / Standalone installer

Windows：

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.ps1 | iex"
```

macOS / Linux：

```shell
curl -fsSL https://raw.githubusercontent.com/xuanlinAI/nova-code/main/scripts/install/install.sh | sh
```

独立安装器从 GitHub Releases 下载安装包，目前只发布了 Windows x64 包。

The standalone installers download a package from GitHub Releases. Only the Windows x64 package is published, so they do not currently succeed on other platforms.

## License

Apache-2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
