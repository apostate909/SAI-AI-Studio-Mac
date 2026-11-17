# SAI AI Studio · Mac

这是独立的 Mac 公开仓库，与 Windows 工程分开。完整工程以源码压缩包提供。

[下载完整 Mac 工程源码包](https://github.com/apostate909/SAI-AI-Studio-Mac/raw/refs/heads/main/SAI-AI-Studio-Mac-Source-20261117-111203.zip)

[SHA-256 校验文件](SAI-AI-Studio-Mac-Source-20261117-111203.zip.sha256)

包含 Mac 客户端、现有授权协议与生产授权引导公钥、Mac Photoshop UXP 插件、测试和打包脚本。未包含服务器私钥、邀请码、API Key 或用户资料。

## 在 Mac 上编译

1. 下载上面的源码 ZIP，解压整个 SAI-AI-Studio-Mac 文件夹。
2. 安装 .NET 8 SDK，以及 Apple 命令行工具（终端运行 xcode-select --install）。
3. 在解压后的工程根目录运行：

```bash
bash macOS/build-mac.sh
```

完整说明在源码包内的 START-HERE.md 和 macOS/README.md。脚本生成带运行时的 .app、ZIP 和 DMG，并包含 Photoshop 插件安装文件；首次使用仍需有效授权。正式跨 Mac 分发需要自己的 Developer ID 签名和 Apple 公证。

## 已验证范围

C# Release 编译通过，0 警告、0 错误；Mac 核心测试 52/52 通过。当前发布物是工程源码，尚未包含在真实 Mac 上编译、签名和公证的 .app 成品。Swift、Keychain、WebKit 及实际 Mac Photoshop 闭环仍需在 Mac 上验证。

源码 ZIP 的 SHA-256：

```text
119B36B451311E9504E58BA87EFFDE5CE7E7652DD683C99F7D22D7D4B1960088
```
