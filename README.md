# SAI AI Studio · Mac

独立的 macOS 客户端仓库，与 Windows 工程分开。包含现有授权功能、Photoshop UXP 插件和 Mac 打包脚本。

## 下载 Mac 构建包

[打开本次 GitHub Actions 构建与下载页面](https://github.com/apostate909/SAI-AI-Studio-Mac/actions/runs/44012402398)

成功的构建产物在页面底部 **Artifacts**：

- `SAI-AI-Studio-Mac-osx-arm64`：Apple Silicon（M 系列芯片）。
- `SAI-AI-Studio-Mac-osx-x64`：Intel 芯片。

每份产物包含带 .NET 运行时的应用 ZIP、DMG、Photoshop Bridge CCX、安装脚本和 SHA-256 校验文件；运行应用不需要安装 .NET SDK。Actions 产物保留 7 天，下载需要登录 GitHub。

当前为 **ad-hoc 临时签名测试包，未通过 Apple 公证**。正式跨 Mac 分发需要自己的 Developer ID 签名和 Apple 公证；CI 构建不能替代实际 Photoshop 交互测试。首次使用仍需有效授权。

## 下载完整 Mac 工程源码

[下载当前 Mac 工程 ZIP](https://github.com/apostate909/SAI-AI-Studio-Mac/raw/refs/heads/main/SAI-AI-Studio-Mac-Source-20261117-114407.zip)

[源码 ZIP 的 SHA-256 校验文件](SAI-AI-Studio-Mac-Source-20261117-114407.zip.sha256)

当前源码修正了 .NET 程序集发布布局及 Intel Mac 内部库签名顺序。早期源码 ZIP 保留为历史版本，编译请使用上面的当前版本。

```text
0BF0FF77A14BEAC48E54A98EA0E90D5D66204453E18FBB8DA89D3D49067CF09C
```

在 Mac 上解压整个 `SAI-AI-Studio-Mac` 文件夹，安装 .NET 8 SDK 和 Apple 命令行工具（`xcode-select --install`），然后在解压后的工程根目录运行：

```bash
bash macOS/build-mac.sh
```

详细的配置和使用说明在源码包内的 `START-HERE.md`、`macOS/README.md`。源码包不包含服务器私钥、邀请码、API Key、用户资料或 Apple 签名证书。

## GitHub Actions 构建流程

工作流分别在 `macos-15`（Apple Silicon）和 `macos-15-intel`（Intel）运行，校验并解压源码、执行 52 项核心测试、发布 .NET 应用、使用 Apple SDK 编译 Swift 原生桥接库、验证内置授权引导和真实 Keychain，再签名并生成 ZIP / DMG / PS 插件。每个任务使用独立的临时 Keychain；设备私钥不会打进应用或下载产物。

[构建工作流](.github/workflows/build-macos.yml) 支持手动重新运行：打开 Actions → Build macOS app → Run workflow。这里只使用公开仓库的标准 GitHub 托管 runner。
